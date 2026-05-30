---
name: codex-exec
description: "Use this skill to delegate tasks to OpenAI Codex CLI as a sub-agent. Triggers on: 'ask codex', 'run it with codex', 'codex exec', or when the user explicitly wants to use the Codex CLI for a task."
---

# Codex CLI Sub-Agent

A skill for invoking the OpenAI Codex CLI as a sub-agent in non-interactive mode.

## Prerequisites

- Installed via `npm install -g @openai/codex`
- The `OPENAI_API_KEY` environment variable is set

## How to run

Run non-interactively with `codex exec` via the Bash tool.

### Basic command

```bash
codex exec --full-auto --quiet --ephemeral "<task>"
```

### Flags

| Flag | Purpose |
|------|---------|
| `--full-auto` | Run automatically without approval prompts |
| `--quiet` | Disable the interactive UI |
| `--ephemeral` | Do not persist the session |
| `--json` | Structured output in JSONL format |
| `-o <path>` | Write the result to a file |

### Long prompts

Pipe the prompt via stdin:

```bash
echo "<long prompt>" | codex exec --full-auto --quiet --ephemeral -
```

## Notes

- Progress is written to stderr; the final result goes to stdout.
- Set a generous timeout (up to 10 minutes: `timeout: 600000`).
- Summarize the result back to the user.
- On errors, also check the contents of stderr.
