---
name: codex-exec
description: "Use this skill to delegate tasks to OpenAI Codex CLI as a sub-agent. Triggers on: 'ask codex', 'run it with codex', 'codex exec', or when the user explicitly wants to use the Codex CLI for a task."
---

# Codex CLI Sub-Agent

A skill for invoking the OpenAI Codex CLI as a sub-agent in non-interactive mode (`codex exec`).

## Prerequisites

- Installed via `npm install -g @openai/codex` (verified against `codex-cli 0.139.0`)
- Authenticated — either `codex login` (ChatGPT sign-in) or an `OPENAI_API_KEY` environment variable

## How to run

`codex exec` runs Codex non-interactively via the Bash tool. Choose the sandbox by what the task needs — there is no `--full-auto`/`--quiet`/`--ephemeral` flag (those were removed; `exec` is already headless and stateless).

```bash
# Read-only analysis / review (safe default — Codex cannot modify files)
codex exec -s read-only "<task>"

# Task that must edit files in the current workspace
codex exec -s workspace-write "<task>"
```

Pass the prompt as the positional argument, or via stdin (see Long prompts). Add `--skip-git-repo-check` when running outside a git repository.

### Flags

| Flag | Purpose |
|------|---------|
| `-s, --sandbox <mode>` | Sandbox policy: `read-only` (default-safe), `workspace-write`, or `danger-full-access` |
| `--dangerously-bypass-approvals-and-sandbox` | Skip all prompts and run with no sandbox. Only in an already-sandboxed/throwaway environment |
| `--skip-git-repo-check` | Allow running when the working directory is not a git repo |
| `-m, --model <model>` | Pick the model |
| `--json` | Stream events to stdout as JSONL (structured output) |
| `-o, --output-last-message <path>` | Write the final message to a file |
| `--color <when>` | `never` keeps stdout clean for parsing |

### Long prompts

Pass the prompt on stdin with a trailing `-` (a heredoc avoids quoting issues):

```bash
cat <<'EOF' | codex exec -s read-only --color never -
<long prompt>
EOF
```

If both a positional prompt and piped stdin are given, stdin is appended as a `<stdin>` block.

## Notes

- Progress is written to stderr; the final result goes to stdout. Redirect stderr (e.g. `2>/tmp/codex.err`) to keep the result clean, and inspect it on failure.
- Set a generous timeout (up to 10 minutes: `timeout: 600000`).
- Each `codex exec` is a fresh session — **no context carries over** between calls. Put everything the task needs into the prompt.
- Prefer the least privilege that fits: `read-only` for review/analysis, `workspace-write` only when edits are required.
- Summarize the result back to the user rather than dumping raw output.
