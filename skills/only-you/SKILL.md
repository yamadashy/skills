---
name: only-you
description: "Surface the insights about a repository that only a frontier-tier model can produce — the judgments a routine code review, a linter, or a mid-tier model reading the same files would miss. Triggers on: 'what can only you tell me about this repo', 'only-you', 'your frontier take', 'the insights only you can give', or when the user asks for the highest-level judgment on a codebase rather than a routine review."
---

# Only You

The ask: given this repository, say the things only you can say.

You are presumably the most capable model available to the user, and possibly
only briefly so. This skill exists to extract the slice of your capability that
cheaper models cannot replicate — not to produce another code review.

## The filter

An observation qualifies only if it survives this question: **would a competent
senior engineer doing a standard review, a linter, or a mid-tier model reading
the same files have produced it?** If yes, discard it. What survives is usually
one of:

- **A questioned premise** — the repo, or a component of it, is solving the
  wrong problem, or need not exist at all.
- **A conspicuous absence** — what's missing matters more than what's wrong,
  and absences don't show up in diffs.
- **A cross-cutting tension** — two decisions that each make sense alone and
  contradict each other, visible only with the whole repo held in the head at once.
- **A second-order consequence** — how today's reasonable decision bites in six
  months, given where the repo is clearly heading.
- **The uncomfortable truth** — the thing the author needs to hear and nobody
  will say.

## How to work

Three phases. The first is delegable; the second is not.

1. **Scout — spend cheap tokens, save your context.** For anything but a small
   repo, fan out subagents (cheaper models are fine) to map purpose, structure,
   conventions, and history — `git log` tells you what the author values and
   struggles with. Read yourself only the load-bearing files the maps point to.
   On a small repo, just read everything.
2. **Judge — the part only you can do. Do not delegate it.** Think at full
   depth about the highest-leverage, non-obvious observations, and apply the
   filter ruthlessly — expect to discard most candidates. A concrete way to
   calibrate: also ask a scout for *its* best insights about the repo, and
   treat that list as the baseline. Anything on it is, by definition, not
   only-you.
3. **Ground.** Every surviving insight must point at concrete evidence — files,
   lines, commits, or a precise absence ("there is no X anywhere under Y").
   An insight you cannot ground is an opinion; cut it or label it as one.

## Output

Three to five insights, ranked by leverage. For each: the claim in one
sentence, the evidence, why it matters, and why a routine review would have
missed it. If fewer than three survive the filter, say so — a short honest list
beats a padded one. Deliver in the user's language.

## Notes

- This skill is deliberately thin. Frontier models degrade when over-scripted;
  the skill states the goal and the filter and trusts your judgment for the
  rest. When maintaining it, resist adding steps.
- If you are *not* the most capable model available to the user, say so and
  suggest running this where the frontier is.
- The deliverable is your assessment. Don't fix anything unless asked.
