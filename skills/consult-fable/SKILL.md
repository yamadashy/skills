---
name: consult-fable
description: "Consult Fable (claude-fable-5, the tier above Opus) as an advisor — a second opinion on a hard design decision, a stuck debugging session, or a close review call. From Claude Code, spawn a subagent on model fable; from any other harness, call the Claude Code CLI. A consultation, not an implementation hand-off. Triggers on: 'consult fable', 'ask fable', 'get fable's opinion', 'second opinion from fable', or when a judgment call is too close to make alone."
---

# Consult Fable

Ask Fable — the frontier tier above Opus — for judgment. This is a consultation,
not a delegation: Fable reads and advises, it does not edit. For implementation
hand-offs, use `claude-exec` instead.

## When to use

- A design decision with real trade-offs, where you want a frontier-tier verdict.
- A debugging dead end: present the symptoms and your hypotheses, ask what you're missing.
- A close review call (ship or hold, is this finding real, is this API shape right).

Not for lookups, mechanical work, or anything a cheaper model answers just as
well — Fable is the most expensive tier (a trivial round trip already costs ~$0.5).

## How to run

**If you are running inside Claude Code** (the Agent/Task tool is available):
spawn one subagent with `model: "fable"` and the consultation question as its
prompt. No CLI round trip needed.

**Otherwise** (Codex, other harnesses, plain shell): call the Claude Code CLI.
Read-only tools (Read, Grep, Glob) stay available, so Fable can inspect the code
it is advising on — name the relevant paths in the prompt.

```bash
claude -p --no-session-persistence --model fable --permission-mode default \
  --disallowedTools Bash,Edit,Write -- "<question>"
```

For long prompts, pipe via stdin and omit the prompt argument:

```bash
echo "<long question>" | claude -p --no-session-persistence --model fable \
  --permission-mode default --disallowedTools Bash,Edit,Write
```

## Writing the question

Context is not carried over — the prompt must stand alone, in either mode:

1. Background: what is being built, and the constraints that matter.
2. The question: one decision, stated precisely.
3. The options considered, with your current lean and why.
4. Ask for a recommendation with reasoning, and what evidence would change it.

## Notes

- One consultation per decision. If the answer raises a follow-up, fold it into
  a single second round — don't turn Fable into a chat partner.
- CLI mode: leave `--effort` at its default (deep reasoning is the point) and
  set a generous timeout (up to 10 minutes: `timeout: 600000`).
- The reply is advice, not an order. Weigh it against what you know, decide,
  and tell the user what Fable said and which parts you adopted.
