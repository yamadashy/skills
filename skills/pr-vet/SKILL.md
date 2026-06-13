---
name: pr-vet
description: "Vet a GitHub pull request and its author for supply-chain risk before reviewing or merging. Investigates the author's account reputation, scans the PR diff for malicious patterns (obfuscation, install hooks, Trojan Source, hidden network egress), and checks the change against current supply-chain attack techniques. Triggers on: 'vet this PR', 'vet this contributor', 'check this PR author', 'is this PR safe', 'supply chain risk', 'can we trust this PR', or before merging a fork PR from an unfamiliar author."
allowed-tools: Bash(gh api:*),Bash(gh pr view:*),Bash(gh pr diff:*),Bash(gh pr list:*),Bash(gh repo view:*),Bash(grep:*),Bash(wc:*),Bash(sort:*),WebSearch,Read,Grep
---

# Vet a Pull Request & Its Author

Vet a GitHub **pull request and its author** before review/merge, focused on **supply-chain risk**. Produces an evidence-based verdict across three axes: who the author is, what the diff actually does, and how the change measures against current attack techniques.

Use this when a fork PR comes from an unfamiliar author, when a change touches sensitive surfaces (dependencies, CI, build, install scripts), or whenever the user asks whether a PR or its author can be trusted.

This skill **investigates and reports** — it does not approve, merge, or modify anything.

## Inputs

Resolve up front:
- `OWNER/REPO` — the base repository (`gh repo view --json owner,name --jq '.owner.login + "/" + .name'`).
- `PR` — the pull request number.
- `LOGIN` — the PR author (`gh pr view <PR> --repo <OWNER/REPO> --json author --jq '.author.login'`).

## Step 1 — Author reputation

Gather identity and track-record signals. None is conclusive alone; weigh them together.

```bash
# Profile: account age, real name, bio, repo/follower counts
gh api users/$LOGIN --jq '{login, name, company, blog, location, bio, public_repos, followers, following, created_at, type, hireable}'

# Track record in THIS repo — prior merged PRs are the strongest positive signal
gh pr list --repo $OWNER/$REPO --author $LOGIN --state all --json number,title,state,createdAt,mergedAt

# Commit author identity — is the email consistent across all commits? (varying/forged = flag)
gh pr view $PR --repo $OWNER/$REPO --json commits --jq '.commits[] | {oid: .oid[0:8], author: .authors[0].name, email: .authors[0].email, msg: .messageHeadline}'

# Are their other repos real projects or empty/spam/mass-forks?
gh api "users/$LOGIN/repos?sort=pushed&per_page=12" --jq '.[] | {name, fork, lang: .language, stars: .stargazers_count, pushed: .pushed_at[0:10], desc: (.description // "")[0:50]}'
```

Read the signals:
- **Positive:** account age measured in years; consistent real identity and commit email; a prior PR **merged into this same repo**; other repos that are genuine, self-authored projects (bonus if they reference real-world services that are hard to fake).
- **Caution (not proof of malice):** account created days/weeks ago; throwaway-looking name; commit email that varies between commits or differs from the account; a portfolio that is almost entirely recent forks of trendy projects; zero prior contribution history anywhere.

## Step 2 — Technical scan of the PR diff

What the code *does* matters more than who wrote it. Pull the diff once, then scan **added lines only**. The added-line matcher is `^\+($|[^+])` (a `+` followed by end-of-line or a non-`+` char) — a plain `^\+` also matches the `+++ b/file` diff header and produces false positives. Most commands are ERE with POSIX classes (`[[:space:]]`, `[[:xdigit:]]`) and avoid `\b`/`\s` (GNU-only); the Trojan-Source scan (2d) needs a PCRE-capable grep — GNU `grep -P`, ripgrep, or ugrep (the grep Claude Code ships). On bare macOS BSD grep, run 2d under one of those.

```bash
gh pr diff $PR --repo $OWNER/$REPO > /tmp/pr.diff
wc -l /tmp/pr.diff

# 2a. Sensitive files touched — deps, CI, build, install config, native/minified blobs.
#     Use the paginated REST list; `gh pr view --json files` truncates on large PRs.
gh api --paginate "repos/$OWNER/$REPO/pulls/$PR/files?per_page=100" --jq '.[].filename' \
  | grep -iE '(^|/)(package(-lock)?\.json|npm-shrinkwrap\.json|yarn\.lock|pnpm-lock\.yaml|bun\.lockb?|deno\.lock|Cargo\.(toml|lock)|go\.(mod|sum)|pyproject\.toml|requirements[^/]*\.txt|Gemfile(\.lock)?|composer\.(json|lock)|\.npmrc|\.yarnrc[^/]*|build\.rs|Makefile|Dockerfile|action\.ya?ml)$|\.github/(workflows|actions)/|(^|/)(scripts?|bin)/|\.(min\.(js|css)|wasm|node|exe|dll|so|dylib)$' \
  || echo "→ no dependency/CI/build/config/binary changes"

# 2b. Install-time execution and curl|sh — the #1 npm-malware delivery path.
grep -nE '^\+($|[^+])' /tmp/pr.diff \
  | grep -iE '"(preinstall|install|postinstall|prepublish|prepublishOnly|prepare|prepack|postpack)"[[:space:]]*:|(curl|wget)[[:space:]].*\|[[:space:]]*(sh|bash|node)' \
  || echo "→ no install hooks or curl-pipe-shell added"

# 2c. Obfuscation / dynamic exec / shell / network primitives.
grep -nE '^\+($|[^+])' /tmp/pr.diff \
  | grep -iE '(^|[^[:alnum:]_])(eval|Function|atob|btoa|child_process|exec|execSync|execFile|spawn|spawnSync|fork)[[:space:]]*\(|fromCharCode|\\x[[:xdigit:]]{2}|\\u[[:xdigit:]]{4}|base64|/dev/tcp|[[:space:]](curl|wget|nc)[[:space:]]|bash[[:space:]]+-c|powershell|Invoke-WebRequest|axios' \
  || echo "→ no dynamic-exec / obfuscation / shell / network primitives"

# 2d. Trojan Source — bidi-reorder + zero-width controls, matched by Unicode codepoint.
#     Needs a PCRE-capable grep: GNU `grep -P`, ripgrep, or ugrep (the grep Claude Code ships).
grep -nP '^\+($|[^+]).*[\x{202A}-\x{202E}\x{2066}-\x{2069}\x{200B}-\x{200D}\x{FEFF}]' /tmp/pr.diff \
  || echo "→ no bidi/zero-width control characters added"

# 2e. Network egress targets — every URL the change introduces.
#     (Assigned to a var first: `grep | sort` always exits 0, so a trailing `|| echo` never fires.)
urls=$(grep -nE '^\+($|[^+])' /tmp/pr.diff | grep -Eio "https?://[^[:space:]<>'\"\`)]+")
if [ -n "$urls" ]; then printf '%s\n' "$urls" | sort -u; else echo "→ no URLs added"; fi

# 2f. Diff metadata — symlinks, exec bit, submodule pointers, binary blobs slip past line review.
grep -nE '^((old|new) mode [0-9]+|new file mode (100755|120000|160000)|[+-]Subproject commit|Binary files )' /tmp/pr.diff \
  || echo "→ no symlink/exec-bit/submodule/binary metadata"
```

Interpreting the scans:
- **2a/2b/2f:** dependency, lockfile, CI-workflow, `*install`-script, symlink, exec-bit, and submodule changes are the highest-leverage attack surfaces. If present, read every line by hand and do not rely on the summary.
- **2c:** any hit needs a human read. `eval`/`Function`/`atob`/`fromCharCode`/`\x..` escapes are how payloads hide; `curl`/`/dev/tcp`/`bash -c` are how they exfiltrate or stage. (`execFile('git', [..arg array..])` with no shell is normal; a shelled-out `execSync(\`...${var}...\`)` is not.)
- **2d:** a hit means the diff hides bidi-reordered or zero-width-concealed code from the reviewer (Trojan Source, CVE-2021-42574) — treat as hostile until proven otherwise. To also see benign non-ASCII (em dashes, accents) and identify codepoints, widen with `grep -nP '^\+($|[^+]).*[^\x00-\x7F]' /tmp/pr.diff`.
- **2e:** confirm every host is expected. A hardcoded, single, well-known host (e.g. `https://github.com/`) is fine; an unexpected domain, an IP, or a URL built from a variable is a red flag.

Also exercise the change end-to-end when feasible (build and run it on a throwaway input) — runtime behavior catches what static reading misses.

## Step 3 — Check against current supply-chain techniques

The threat landscape shifts; do not rely on memory. **Web-search the latest techniques** and test the diff against them.

```
WebSearch: "npm supply chain attack techniques <current year> malicious pull request open source"
```

Map the PR onto the dominant TTPs. As of this writing, many high-blast-radius attacks concentrate in **CI/CD, dependency resolution, and the publish pipeline** — so a PR touching none of these is **risk-reduced, not risk-free**. Application and test code can still carry a runtime backdoor, credential exfiltration, or dependency-confusion import, so finish Step 2's line-by-line read regardless:

| Technique | What to check in the PR |
| --- | --- |
| **Pwn Request** (`pull_request_target` abuse, Actions cache poisoning, OIDC token theft) | Any `.github/workflows/` change? Does the PR rely on a privileged workflow running against fork-controlled code? |
| **Self-replicating worms** (Shai-Hulud family) | Install hooks, token/secret access, anything reading `~/.npmrc` / `GITHUB_TOKEN` / env credentials |
| **Install-time exec + obfuscation** (Red Hat / Miasma style) | `pre/postinstall` scripts, large obfuscated JS, `eval`/ROT decoders (Step 2b/2c) |
| **Mass malicious PRs** (credential exfil via CI logs) | Is the author spraying many near-identical PRs across repos? Does the PR add steps that echo secrets? |
| **Scrutiny-evasion via large/auto-generated diffs** | Oversized diff, lockfile-only changes, generated files hiding a payload |

Note: `pull_request_target` exposure is a property of **the repository's own CI config**, not of this diff. If the repo runs privileged workflows on fork PRs, flag it as a separate hygiene item to audit — independent of this author's trustworthiness.

## Step 4 — Verdict

Report evidence, then a calibrated conclusion. **Do not overstate certainty.** State the result as a level (low / moderate / high trust — i.e. high / moderate / low risk) with the reasons, and always list residual risks.

Suggested shape:

```
## Vet result: <LOGIN> / PR #<PR>

### Author signals
<account age, identity/email consistency, prior merged PRs, repo authenticity>

### Diff scan
<deps / CI / install hooks / obfuscation / Trojan Source / egress — each ✓ or ⚠ with detail>

### Vs. current TTPs
<which dominant techniques the diff does or does not touch>

### Verdict: <low | moderate | high> trust
<the 2–3 strongest reasons>

### Residual risks
- Account compromise is always possible for any contributor; note whether THIS diff
  would carry a payload even so (small, readable, no deps/CI = benign even if pushed
  by a compromised account).
- Separate repo-level hygiene to verify (e.g. fork-PR CI handling), if any.
```

## Principles

- **Evidence over vibes.** Every claim ties to a command output. If you assert "malicious," show the line; if you retract, say so.
- **Two axes, not one.** A trusted-looking author with a dangerous diff is dangerous; an unknown author with a tiny, clean, dependency-free diff is low-risk. Weigh both.
- **The diff is the ground truth.** Reputation can be faked or hijacked; obfuscation, install hooks, and hidden egress cannot hide from a line-by-line read.
- **Report, don't act.** This skill never merges, approves, or edits. It hands the maintainer a calibrated verdict to decide on.
