---
name: carnet
description: |
  Persistent file-based notebook (.carnet/<category>/<slug>.md, auto-expiring after 30 days of disuse) for AI agents and humans.

  Use whenever saving, recalling, or organizing notes across sessions — IMPLICIT cues include the user recapping a tricky fix worth not redoing, asking 'what did we decide about X', handing off mid-task state, or setting something aside for now.

  Use PROACTIVELY when you discover something a future agent would otherwise re-derive from scratch — a non-obvious library gotcha, a hard-won fix, a rejected design alternative likely to be re-proposed, an in-progress state worth resuming.

  SKIP for: time-bound TODOs that need to nag (TodoWrite/Issues surface back, carnet does not), credentials/secrets (don't put them on disk), context already in a commit/PR/ADR (no double-bookkeeping).

  When in doubt, prefer a brief note over losing context: unused notes expire automatically.
---

# Agent Carnet

A tiny CLI that gives you a shared markdown notebook on disk under `.carnet/<category>/<slug>.md`. Notes have a 30-day default lifespan that resets every time they are read or applied; useful ones survive, stale ones drift to `.trash/` automatically.

## Quick reference

```bash
# Save (always pass --summary and --agent claude-code)
echo "body content" | agent-carnet save deps/iconv-issue \
  --summary "iconv-esm v0.7 types broken — pin to v0.6" \
  --agent claude-code \
  --tags compat,esm

# Recall
agent-carnet find iconv               # search summaries (does NOT bump lifespan)
agent-carnet list                     # category-grouped overview, sorted by last_used
agent-carnet list --sort use_count    # most-applied notes first
agent-carnet read deps/iconv-issue    # read full content (bumps last_used; weak use signal)

# Mark as actually applied (strong use signal — bumps last_used + use_count)
agent-carnet used deps/iconv-issue

# Maintain
agent-carnet move <from> <to>
agent-carnet rm <path> --yes
```

`save` reads body content from **stdin** (pipe via `echo`, heredoc, or `<` redirection). The `--summary` flag is the standalone-readable headline; the piped stdin is the full body.

When unsure of a subcommand's full flag set, run `agent-carnet <command> -h` (e.g.
`agent-carnet save -h`, `agent-carnet used -h`). Each subcommand prints its own
focused help — required arguments, options, and examples — without invoking
filesystem operations.

## When to save

Treat carnet as an agent notebook, not a strict archive. If you think a note may help a future agent (or future-you) resume work, dodge a rethink, remember a temporary state, or preserve a useful hunch — save it. Provisional notes are welcome; the 30-day lifespan is the safety valve (notes that keep getting read or applied stay alive, the rest expire automatically).

Examples worth keeping in mind (not an exhaustive list):
- "We tried X. It didn't work because Y. Don't waste time retrying without Z changing."
- "The library does A, but only if you also call B beforehand. Not in their docs."
- "Chose approach P over Q. Q would have been faster but breaks our R constraint."

These are guidelines, not gates. If grep / read / git log already gets a future reader to the same conclusion, you can skip it — but when in doubt, prefer saving a small, well-summarized note over losing context.

## When to recall

Before starting related work or when context might exist:
- `agent-carnet find <topic>` — quick scan of summaries
- `agent-carnet list <category>` — browse a folder. Each entry's tail shows `(last_used: …, use_count: N)` — a high `use_count` means the note has been load-bearing across past sessions
- `agent-carnet read <path>` — actually read (bumps `last_used`; only use when the content matters)

Use `use_count` as one importance signal among several: combine with the summary, tags, and `last_used` before deciding what to read. A high-count note is not always relevant to the current question, and a freshly-saved load-bearing note starts at `use_count: 0`. `agent-carnet list --sort use_count` surfaces the most-applied notes when that ranking is the right lens.

## When to call `used`

Call `agent-carnet used <path>` after a carnet **actually shaped your work**:
- You applied the recorded fix and it solved the bug.
- You consulted the carnet before retrying a hypothesis and skipped a dead-end.
- You used the canonical name from a `vocab` carnet in new code instead of inventing your own.

Each `used` call bumps `last_used` AND increments `use_count` by one — a durable importance signal that survives across sessions and lets future readers (and `agent-carnet list --sort use_count`) surface load-bearing notes. Repeated calls each increment, so call once per real application event, not per session.

Reading a carnet does NOT count. `read` already keeps it alive (weak signal: bumps `last_used` only); `used` records that the note was worth keeping for a real reason (strong signal: bumps both, and `+1`s the `use_count` that future agents see in `list` output).

## Hard rules

- `--summary` is required. Make it decisive — reading the summary in isolation tells the next reader (or the next agent) whether to read further.
- `--agent claude-code` is required.
- `find` does NOT bump anything. `read` bumps `last_used`. `used` bumps `last_used` AND increments `use_count`.
- `updated` tracks content modification only (`save`, `save --update`). It is independent of `last_used` and is not the lifespan driver.
- The 30-day expiry is automatic — do not manually clean up. `keep: true` pins permanent notes.
- Auto-prune runs on every CLI invocation; deleted carnets land in `.carnet/.trash/` for 7 days before hard delete.

## Path conventions

- `<category>/<slug>` — kebab-case, no leading slash, no `..`.
- Categories are folders; create new ones freely as needed.
- Subcategories are allowed: `deps/esm/iconv-issue` works.

## When to read references/

This SKILL.md is enough for everyday note-keeping. Open the references/ files **only** when one of these specific cases applies — they are not always-on context, so do not load them speculatively.

| Read this file | When |
|---|---|
| `references/cookbook.md` | You are about to use (or are being asked about) a tag-based pattern such as `tags: [vocab]` for project terminology or `tags: [hypothesis]` for debugging dead-ends. The file shows the full pattern, including how to structure the body and `meta:` for that pattern. |
| `references/frontmatter.md` | You need to write or read the `meta:` extension namespace, set a non-trivial `lifespan` / `keep`, or understand why an unfamiliar frontmatter field is or is not preserved on save. |

If neither case applies, **do not read references/**. The base of this file already covers daily save/find/read/used/move/rm flows.
