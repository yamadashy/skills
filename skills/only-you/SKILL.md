---
name: only-you
description: "Propose the tasks on a repository that only a frontier-tier model can execute — the work the model one tier below or a routine engineer would fail at or do shallowly. The deliverable is a numbered pitch list ('I can do this here, and nothing cheaper can') for the human to greenlight. Triggers on: 'what could only you do in this repo', 'only-you', 'find frontier-worthy tasks', 'what work is worth handing to you', or when the user wants to know what to give the most capable model available."
---

# Only You

The ask: given this repository, propose the work only you can do — pitched so
the human can pick one and hand it back to you.

This is not a review and not an insight list. The deliverable is a set of
task pitches, each one a claim: "I can do this here, and nothing cheaper
can." The human decides which to greenlight; you execute nothing until they
do.

## The filter

A task qualifies only if it survives this question: **would the model one
tier below you, or a competent engineer with enough time, have delivered
essentially the same result?** If yes, discard it — that is delegation
fodder, not a pitch. What
survives usually looks like:

- **Resolving a cross-cutting tension** — two decisions that each make sense
  alone but contradict each other, fixed everywhere at once with the whole
  repo held in the head.
- **Rebuilding on a corrected premise** — a component is solving the wrong
  problem; redesign it from the premise up rather than patch it in place.
- **Designing the conspicuous absence** — the thing the repo needs and nobody
  has built, where the hard part is the design, not the typing.
- **Pre-empting the second-order consequence** — restructure now for where
  the repo is clearly heading, before today's reasonable decision bites.

Noticing is raw material here, not the product: an observation with no task
attached is trivia. Convert what only you can see into what only you can do,
or drop it.

## How to work

1. **Scout — spend cheap tokens, save your context.** For anything but a
   small repo, fan out subagents (the model one tier below you) to map purpose,
   structure, conventions, and history — `git log` tells you what the author
   values and struggles with. Read yourself only the load-bearing files the
   maps point to. On a small repo, just read everything.
2. **Judge — the part only you can do. Do not delegate it.** Generate
   candidate tasks and apply the filter ruthlessly — expect to discard most.
   Do not trust self-assessment: mid-read, every candidate feels
   frontier-worthy. The baseline is mandatory — launch several scouts in
   parallel (the model one tier below you), each asked what tasks *it* would
   propose and
   could carry out on this repo; the union of their lists is the baseline,
   and anything on it — or anything they could plainly execute — is
   discarded. One scout is one noisy sample; several make the baseline
   strong and the surviving delta honest.
3. **Ground.** Every surviving task must point at concrete evidence that the
   repo needs it — files, lines, commits, or a precise absence ("there is no
   X anywhere under Y") — plus a concrete reason the execution needs the
   frontier. A task you cannot ground is an ambition; cut it.

## Output

Three to five task pitches, ranked by leverage. For each: what you would do
in one sentence, the evidence the repo needs it, why nothing cheaper could
deliver it, and what "done" looks like. Number them so greenlighting costs
the human one word ("do 2"). If fewer than three survive the filter, say so —
a short honest list beats a padded one. Deliver in the user's language.

## Notes

- This skill is deliberately thin. Frontier models degrade when
  over-scripted; the skill states the goal and the filter and trusts your
  judgment for the rest. When maintaining it, resist adding steps.
- If you are *not* the most capable model available to the user, say so and
  suggest running this where the frontier is.
- Execute nothing until the human picks. If mid-execution a task turns out
  to be delegable after all, say so instead of burning frontier tokens on it.
