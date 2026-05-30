---
name: antigravity-exec
description: "Use this skill to delegate tasks to the Antigravity CLI (agy) as a sub-agent. Triggers on: 'ask antigravity', 'run it with antigravity', 'agy -p', or when the user explicitly wants to use the Antigravity CLI for a task."
---

# Antigravity CLI Sub-Agent

A skill for invoking the Antigravity CLI (`agy`) as a sub-agent in non-interactive mode (`-p` / `--print`).

## Prerequisites

- `agy` is installed and on `PATH` (check with `agy --version`).

## How to run

Run non-interactively with `agy -p` via the Bash tool. The prompt is passed as the flag's argument.

### Basic command

```bash
agy -p "<task>"
```

The response is printed to stdout. Example:

```bash
agy -p "Reply with exactly one sentence: what is the capital of Japan?"
# -> The capital of Japan is Tokyo.
```

### Flags

| Flag | Purpose |
|------|---------|
| `-p` / `--print` / `--prompt` | Run a single prompt non-interactively and print the response |
| `--print-timeout <dur>` | Timeout for print mode (default `5m0s`; raise for long tasks, e.g. `10m`) |
| `--dangerously-skip-permissions` | Auto-approve all tool permission requests without prompting |
| `--add-dir <path>` | Add a directory to the workspace (repeatable) |
| `--sandbox` | Run in a sandbox with terminal restrictions enabled |
| `-c` / `--continue` | Continue the most recent conversation |
| `--conversation <id>` | Resume a previous conversation by ID |
| `--log-file <path>` | Override the CLI log file path |

### Long prompts

`-p` requires its value as an argument (it does not read the prompt from stdin). For a long prompt, pass it via command substitution:

```bash
agy -p "$(cat prompt.md)"
```

## Notes

- The prompt must be supplied as the `-p` argument — piping into a bare `agy -p` fails with "flag needs an argument: -p".
- The default print timeout is 5 minutes. For longer tasks raise it with `--print-timeout` and set a generous Bash timeout (up to 10 minutes: `timeout: 600000`).
- Tool actions may prompt for permission. For unattended automation that needs to write/run, add `--dangerously-skip-permissions` (and prefer `--sandbox` to limit the blast radius).
- The current conversation context is not carried over. Include any required information in the prompt, or use `-c` / `--conversation` to resume a prior session.
- Summarize the result back to the user.
