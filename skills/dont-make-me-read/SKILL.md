---
name: dont-make-me-read
description: Reduce reader cognitive load in plain-text messages — Slack, chat DMs, SNS, plain-text email — where no markdown rendering is available. Phone-first ordering and chunking (self-contained first line, one topic, 1-3-line chunks), an ASCII tag vocabulary, and optional script-specific decoration with strict usage rules. Use when writing or rewriting a chat message, announcement, request, or notification, or when asked to "make this message readable/scannable", "format this for Slack/DM", or shown a wall-of-text message. Not for surfaces that render markdown, and not for argumentative prose.
---

# Don't make me read

## Foundation

The constraints come from the reading environment, not the language:

- A phone viewport shows roughly 12-15 lines; longer messages collapse behind "Show more".
- Notification previews and channel lists show only the first line.
- Chat apps use proportional fonts and re-wrap text. Column alignment and
  leading-space indentation do not survive.
- Readers scan before they read: first "is this for me?", then the one fact they need.

**Admission rule for symbols: a symbol earns its place only by showing structure** —
a boundary, a hierarchy, a key-value pair, a state, or a sequence. Symbols that
perform attention or emotion (eye-catchers such as ＼ ／, decorative or tone emoji)
belong to register and taste, not cognitive load; this skill never adds them, and
uses no emoji at all.

The skill has three layers. Blind A/B testing of drafts showed that Layer 1 — the
invisible ordering discipline — carries nearly all of the benefit; the visible
decoration is a minor, situational gain. Apply the layers in order and stop as
early as you can.

## Layer 1 — Ordering and chunking (mandatory)

1. **First line = the point, self-contained.** A complete plain statement with its
   own subject, no symbols. "Yes, we can" fails as a notification preview;
   "We can ship search on Friday" works. If one caveat decides whether the reader
   needs to keep reading ("US only — no impact on us"), put it in the first two lines.
2. **One message, one topic.** Background, timelines, and side questions go to a
   thread reply or a linked doc.
3. **Chunks of 1-3 lines, separated by blank lines.**
4. **Break lines only at semantic boundaries** — after a sentence, or after a major
   clause. Never hard-break mid-sentence to control line width: the client re-wraps
   and produces ragged fragments. (The Semantic Line Breaks spec, sembr.org, reaches
   the same rule for markup sources.)
5. **Cap at ~15 lines.** Longer means restructure, move detail to a thread, or link out.
6. **Number anything the reader must choose from or refer back to.** Numbers make
   items pointable — a reply becomes "option 2" (selection) instead of a restatement
   (recall).
7. **Each quotable line carries its own subject.** Thread replies strip surrounding
   context. "$5,000/year" alone is ambiguous; "store operators pay Google $5,000/year"
   survives being quoted.

Evidence grades, so the skill stays honest about what it knows:

| Rule | Grade |
| --- | --- |
| Chunking (3) | research-backed (working-memory / chunking literature) |
| First line (1), no mid-sentence breaks (4), length cap (5) | UI constraint — follows mechanically from previews, re-wrapping, collapse |
| The rest (2, 6, 7) | convention — well-attested in git commit format, RFC style, and plaintext email culture |

## Layer 2 — ASCII tag vocabulary

When Layer 1 alone is not enough, borrow from code comments, commit messages, and
RFCs. This vocabulary is ASCII, greppable, survives copy-paste into any tool, and
is tolerable to screen readers.

- **Line-head type tags** — `NOTE:`, `WARNING:`, `TL;DR:`, `ACTION:` — declare what
  kind of line follows. At most one or two per message.
- **`Key: value` lines** for lookup facts (`When: Fri 10:00`, `Where: Studio A`).
  Use when there are 3+ parallel facts; fewer reads better as prose.
- **`1.` `2.`** for sequences and choices; **`-`** for unordered lists.
- **`->` means consequence, and nothing else.** One symbol, one meaning per message:
  write "i.e." and "then" as words instead of overloading the arrow.
- **`[x]` / `[ ]`** for done/undone status.
- Never use a live tag token as an example in the same message — quote it
  (a "NOTE:"-style tag), or the reader parses a false tag.

## Layer 3 — Script-specific decoration (optional — earn it)

Section headers, dividers, and bracket labels help desktop scanning and cost
phone screens and screen readers. Rules of admission:

- **No headers or dividers in a message under ~10 lines.** A blank line already separates.
- **A header must cover everything under it**: one section, one topic. A header that
  labels only part of its section breaks scanning for the rest.
- **Dividers are redundant next to a header plus a blank line.** If you use one,
  keep it short (`---`); a 20-char rule line can itself wrap into an orphan stub,
  and a screen reader announces every character of it.
- **Bracketed key labels** (Japanese 【】) only with 3+ parallel keys.
- **Never column-align across lines and never indent continuations with spaces** —
  both die in proportional fonts.

Per-script vocabularies (Latin/ASCII, Japanese/CJK, caseless scripts) and their
pitfalls: see `references/scripts.md`.

## Send-time checklist

- Would the first line alone, in a notification, tell the reader the point and
  whether it concerns them?
- One topic? Chunks of 1-3 lines? 15 lines or fewer?
- Any hard break inside a sentence? Remove it.
- Does each symbol have exactly one meaning in this message?
- Would each line survive being quoted alone in a thread?
- Is every header honest about its whole section? Is decoration earned (~10+ lines)?
- Register — greetings, emoji, formality — is the room's call, not this skill's.
  Match the channel's existing tone. (Culture-dependent; no universal rule exists.)

## Before / After

Before:

> Hi! Quick question — we talked about the release last week, and QA flagged a
> performance issue in the search revamp that isn't fixed yet, so we need to decide
> whether to include it. If we don't, we can still ship Tuesday, but if we do it'll
> take about three more days, so we'd ship Friday instead. What do you think works
> best? Thanks!

After:

> Decision needed by tomorrow: include the search revamp in this release?
>
> QA flagged a performance issue in the revamp; the fix needs ~3 days.
>
> 1. Ship without it -> release stays Tuesday
> 2. Include it -> release moves to Friday
>
> Reply with a number and I'll proceed.

Every Layer 1 rule is visible here; the only Layer 2 items are the numbers and one
arrow. Nothing from Layer 3 was needed — that is the common case.

## Scope and limits

- For transmission: requests, announcements, status updates, explanations.
  **Not for argumentative or persuasive prose** — this structure dismantles an
  argument's flow into disconnected assertions.
- **Not for markdown-rendering surfaces** (READMEs, docs, GitHub issues): use real
  markdown there.
- The failure mode of this style is imitation without discipline: decoration wrapped
  around unordered text signals structure that is not there, which is worse than
  honest prose. When in doubt, apply Layer 1 and stop.
- Reformatting forces compression — expect the result to be much shorter than the
  source. If essential nuance is being squeezed out, the content may be an argument,
  not a transmission; see the first bullet.

## Lineage

These conventions are described, not invented, following long-lived plain-text cultures:
git commit format (summary line, blank line, body); TODO/FIXME code-comment tags;
RFC 2119 capitalized keywords and man-page section headers; setext (1992) →
Markdown, whose stated "single biggest source of inspiration" was plain-text email;
Semantic Line Breaks (sembr.org). The name nods to Steve Krug's *Don't Make Me
Think* — the same demand, made of messages instead of interfaces: the reader
should get it by looking, not by reading.
