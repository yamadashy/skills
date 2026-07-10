---
name: codex-exec
description: "Use this skill to delegate tasks to OpenAI Codex CLI as a sub-agent, including image generation/editing with GPT-Image-2. Triggers on: 'ask codex', 'run it with codex', 'codex exec', 'generate an image with codex', or when the user explicitly wants to use the Codex CLI for a task."
---

# Codex CLI Sub-Agent

A skill for invoking the OpenAI Codex CLI as a sub-agent in non-interactive mode (`codex exec`).

## Prerequisites

- Installed via `npm install -g @openai/codex` (verified against `codex-cli 0.144.1`)
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
| `-i, --image <FILE>...` | Attach image(s) to the prompt (variadic — see Image generation) |
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

## Image generation (GPT-Image-2)

Codex has a built-in `image_gen` tool backed by GPT-Image-2 (feature `image_generation`, enabled by default). It works with the ChatGPT sign-in — no `OPENAI_API_KEY` required. Use `-s workspace-write`: Codex generates under `$CODEX_HOME/generated_images/` and then copies the file into the workspace.

```bash
# Generate a new image
codex exec -s workspace-write "Generate an image of <subject> and save it as assets/hero.png in the current directory."

# Edit an existing image: attach it with -i and terminate the flag with --
# (-i is variadic; without -- it swallows the prompt as another file path and
#  codex falls through to "Reading prompt from stdin..." and exits 1)
codex exec -s workspace-write -i input.png -- "Edit the attached image: <change>. Keep everything else unchanged. Save the result as input-edited.png."
```

How to instruct it (all verified):

- **Always name the destination file in the prompt** — otherwise the output may stay under `$CODEX_HOME/generated_images/` instead of the workspace.
- **State the size in the prompt** and it is honored, e.g. "Output size 1024x1024". GPT-Image-2 accepts edges up to 3840px (multiples of 16, aspect ratio ≤ 3:1); common sizes: `1024x1024`, `1536x1024` landscape, `1024x1536` portrait, `3840x2160` 4K.
- **Structure the prompt**: subject → style/medium → composition/framing → lighting/mood → constraints ("no text, no watermark"). Quote any text to render verbatim.
- **For edits, spell out invariants** ("change only X; keep the background and composition identical") — Codex passes the attached image to the edit flow.
- **Transparent backgrounds work by asking for them** ("with a transparent background"): GPT-Image-2 has no native transparency, but Codex generates on a chroma-key background and removes it locally, producing an alpha PNG.

## Notes

- Progress is written to stderr; the final result goes to stdout. Redirect stderr (e.g. `2>/tmp/codex.err`) to keep the result clean, and inspect it on failure.
- Set a generous timeout (up to 10 minutes: `timeout: 600000`).
- Each `codex exec` is a fresh session — **no context carries over** between calls. Put everything the task needs into the prompt.
- Prefer the least privilege that fits: `read-only` for review/analysis, `workspace-write` only when edits are required.
- Summarize the result back to the user rather than dumping raw output.
