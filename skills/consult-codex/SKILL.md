---
name: consult-codex
description: "Consult OpenAI Codex as an advisor via `codex exec` — a cross-model second opinion on a hard design decision, a stuck debugging session, or a close review call. A consultation, not an implementation hand-off. Triggers on: 'consult codex', 'ask codex for advice', 'get codex's opinion', 'second opinion from codex', or when a judgment call is too close to make alone."
---

# Consult Codex

Ask Codex for judgment. This is a consultation, not a delegation: Codex runs
read-only and advises, it does not edit. Because Codex is a different model
family, it can catch blind spots that every Claude-side check shares.

For implementation hand-offs and the full CLI mechanics (prerequisites, flags,
image generation), see the `codex-exec` skill — this skill only fixes the
consultation shape.

## When to use

- A design decision with real trade-offs, where you want an independent verdict.
- A debugging dead end: present the symptoms and your hypotheses, ask what you're missing.
- A close review call (ship or hold, is this finding real, is this API shape right).

Not for lookups or mechanical work — for those, delegate with `codex-exec` instead.

## How to run

Always the CLI, in the read-only sandbox so Codex can inspect the code it is
advising on but cannot change it:

```bash
codex exec -s read-only --color never "<question>"
```

For long prompts, use stdin with a trailing `-` (heredoc form — see `codex-exec`):

```bash
cat <<'EOF' | codex exec -s read-only --color never -
<long question>
EOF
```

## Writing the question

Context is not carried over — the prompt must stand alone:

1. Background: what is being built, and the constraints that matter.
2. The question: one decision, stated precisely.
3. The options considered, with your current lean and why.
4. Ask for a recommendation with reasoning, and what evidence would change it.

## Notes

- One consultation per decision. If the answer raises a follow-up, fold it into
  a single second round — don't turn Codex into a chat partner.
- Progress goes to stderr, the answer to stdout; set a generous timeout
  (up to 10 minutes: `timeout: 600000`).
- The reply is advice, not an order. Weigh it against what you know, decide,
  and tell the user what Codex said and which parts you adopted.
