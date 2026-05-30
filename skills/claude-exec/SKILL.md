---
name: claude-exec
description: "Use this skill to delegate tasks to Claude Code CLI as a sub-agent. Triggers on: 'ask claude', 'run it with claude', 'claude -p', or when the user explicitly wants to spawn a separate Claude Code session for a task."
---

# Claude Code CLI Sub-Agent

A skill for invoking the Claude Code CLI as a sub-agent in non-interactive mode (`-p` / `--print`).

## When to use

- You want to hand off an investigation or task to a separate Claude session and only receive the result.
- You want to run a side task in parallel without polluting the current conversation's context.
- You want structured output (JSON) so the result can be processed in a pipeline.

## How to run

Run non-interactively with `claude -p` via the Bash tool.

### Basic command (read / investigation use)

```bash
claude -p --no-session-persistence --permission-mode default \
  --disallowedTools Bash,Edit,Write -- "<task>"
```

For tasks that write files, explicitly allow only the tools you need via `--allowedTools`:

```bash
claude -p --no-session-persistence --permission-mode acceptEdits \
  --allowedTools Read,Edit,Write -- "<task>"
```

### Common flags

| Flag | Purpose |
|------|---------|
| `-p` / `--print` | Run in non-interactive mode and exit |
| `--output-format json` | Return the result as JSON (`stream-json` is also available) |
| `--model <name>` | Select the model (`opus` / `sonnet` / `haiku`, etc.) |
| `--permission-mode <mode>` | `default` / `acceptEdits` / `plan` / `bypassPermissions` |
| `--no-session-persistence` | Do not persist the session to disk (requires `-p`) |
| `--allowedTools <list>` | Restrict to a comma-separated allowlist of tools (e.g. `Read,Edit`) |
| `--disallowedTools <list>` | Specify a comma-separated denylist of tools |
| `--append-system-prompt <text>` | Append to the system prompt |
| `--add-dir <path>` | Grant access to an additional directory |
| `--max-budget-usd <amount>` | Set a cost ceiling |
| `--bare` | Minimal mode (disables hooks, auto-memory, automatic CLAUDE.md loading, etc.) |

### Long prompts

Pipe the prompt via stdin (the prompt argument can then be omitted):

```bash
echo "<long prompt>" | claude -p --no-session-persistence \
  --permission-mode default --disallowedTools Bash,Edit,Write
```

### Structured output

```bash
claude -p --output-format json --no-session-persistence \
  --permission-mode default --disallowedTools Bash,Edit,Write \
  -- "<task>" | jq -r '.result'
```

The JSON includes `result` / `total_cost_usd` / `session_id` / `duration_ms` / `modelUsage`, among others.

## Notes

- **`--permission-mode bypassPermissions` can be rejected by the auto-mode classifier** (a safeguard against runaway sub-agents). For sub-agent use, prefer `default` + `--disallowedTools` or `acceptEdits` + `--allowedTools` first.
- **Put `--` before the prompt.** Variadic flags such as `--allowedTools` / `--disallowedTools` also accept space-separated values, so without the separator they can swallow the following prompt argument as a flag value and produce an "Input must be provided..." error. A comma-separated list plus the `--` separator is the safe form.
- Set a generous timeout (up to 10 minutes: `timeout: 600000`).
- The current conversation context is not carried over. Include any required information in the prompt.
- Summarize the result back to the user.
