---
name: listener-first
description: Shape what a message says around the listener's state rather than the sender's. Corrects the measured sender biases first (underestimating that people say yes, overestimating how well you were understood, arguing from your own values), then channel and friction, then barriers to comprehension, and wording last. Load-bearing claims carry an evidence grade, and popular techniques that the evidence does not support — or that fail an honesty test — are named and excluded. Use when drafting or revising a spoken or written request, proposal, explanation, bad news, apology, or a reply in a disagreement — and on "make this more persuasive", "how should I phrase this", "they'll say no", "this didn't land". Changes substance and stance: not layout, not scannability, not prose rhythm.
---

# listener-first

## Foundation

Two large field syntheses set the expectation for everything below.

- Across 49 field experiments, the best estimate of the persuasive effect of
  campaign contact — mail, calls, canvassing — on candidate choice in US general
  elections is **zero** (Kalla & Broockman 2018). The same paper does find clear
  effects in primaries and ballot-measure campaigns, where voters have no party
  cue to fall back on.
- Behavioral interventions run by two government nudge units moved outcomes by
  **1.4 percentage points**; a separate set of academically published nudges
  reports 8.7. Publication bias, exacerbated by low power, accounts for the entire
  gap (DellaVigna & Linos 2022, 126 RCTs, 23 million people).

Neither study manipulates wording, and both are institutional rather than
interpersonal — treat the transfer as an assumption, not a finding. But the
direction is consistent and it is the honest prior: **wording is the last and
smallest lever.** What moves outcomes by large factors is who you ask, through
which channel, how much work you leave them, and whether you understood their
position before you wrote.

The layers below are ordered by how much of the outcome they plausibly control,
not by a common effect metric — the underlying studies report percentage points,
ratios, *d* and *r*, which cannot be ranked against each other. Apply them in
order. Most messages are finished in Layer 1 or 2.

**Proportionality.** Skip to the checklist if the message is under about three
lines *and* carries no refusable ask, or if it goes to someone you talk to daily
about routine matters. A four-line listener analysis in front of a nine-word Slack
message is a failure of this skill, not an application of it. The skip does not
apply to apologies, bad news, or anything crossing a power difference, however
short — those keep the full pass.

## Admission rule — the full-disclosure test

> **Would the listener, knowing exactly how this message was constructed, still
> think the ask was fair?**

Any technique that fails this is out. Reframing which true fact leads is in;
inventing the fact is not.

| Move | Verdict |
| --- | --- |
| Leading with the part of the truth that matters to them | In |
| A deadline that exists | In |
| A deadline that does not | Out |
| "You're the only one who can do this" — and they are | In |
| The same line when three other people could | Out |
| Naming a real cost they'd want to know about | In |
| Listing benefits and omitting the cost that decides it | Out |

Not decoration, and load-bearing for two reasons. A fabricated frame is
discovered eventually, and the cost lands on every later request you make — the
game is repeated. And when a language model does the drafting, the risk is
measured rather than theoretical: in debate pairs where the two sides were not
equally persuasive, GPT-4 with access to basic demographic facts about its
opponent was the more persuasive side 64.4% of the time (Salvi et al. 2025).

**Unverified is not the same as true.** If a claim's truth is unknown to you — is
he really the only one who could do this? — you may not use it, and you may not
assume it false either. Ask whether it's true, or leave it out. A claim the user
recommends for its effect ("that usually works on him") rather than its accuracy
is being offered as a lever, not a fact; treat it as unverified.

**A genuine preference is not a deadline.** "I want this done this week" is true
and usable. "This has to be done this week" is a deadline, and needs one to exist.
State the wish as a wish.

**If the user asks for an excluded move** — manufactured urgency, a false
exclusivity line, an invented deadline — write the honest version, and say in one
line which requested element you left out and why. Do not silently comply, and do
not refuse to produce anything.

**Never invent the listener's motives, or the facts of the incident.** If you do
not know what the recipient cares about, what they are busy with, or what they
already know, ask the person you are drafting for. If asking is not possible —
non-interactive run, or the user genuinely does not know — then **draft anyway,
with a one-line assumption block above the draft** naming what you assumed and
which assumptions would change the message if wrong. Stalling with questions and
no draft is a failure mode too.

## Layer 1 — Correct the sender's three biases

These are properties of the writer, not the reader, and they are measured. What
is *not* measured is how much correcting them improves outcomes; no study tests
the procedure below. It is a reasonable inference from the biases, not a result.

1. **You underestimate how often people say yes — by roughly half.** Across
   studies in which participants made requests of more than 14,000 strangers,
   requesters underestimated compliance by an average of 48%, because they do not
   feel how socially costly refusal is (Flynn & Lake 2008 — Lake now publishes as
   Bohns; Bohns 2016). The error
   persists for friends, for large requests, and after a previous refusal.
   → **Ask, and ask directly rather than hinting.** The most common failure is not
   a badly phrased request; it is a request never made, or softened into a hint
   that never registered as one.
   → **Re-asking is bounded.** Ask a second time only if circumstances changed or
   the first attempt was a hint rather than a request. Never re-ask someone you
   hold power over, never on a personal or romantic matter, and never where the
   refusal was on principle rather than on capacity. The underlying studies are
   strangers and small favours; past that, this stops being persistence.
   → **When re-asking is barred, the need doesn't disappear — reclassify it.**
   Either reopen it as a question (find out what actually blocked them, with "no"
   still genuinely available), or, if the thing must happen regardless of their
   preference, say so as a decision rather than dressing a directive as a request.
   The second is more honest than a better-worded second ask, and usually less
   damaging.

2. **You overestimate how well you were understood.** Knowing something makes it
   nearly impossible to model not knowing it (Camerer, Loewenstein & Weber 1989).
   Over email specifically, people overestimate both their ability to convey tone
   and their ability to read it — across five experiments — because they hear
   their own intended tone as they write (Kruger et al. 2005).
   → **Assume your first draft is clearer to you than to anyone else.** Name the
   thing you assumed they knew. If tone carries meaning — irony, mild criticism, a
   joke — it will not survive text. Say it literally instead.

3. **You argue from your own values, not theirs.** Asked to persuade someone who
   disagrees, fewer than 10% of people spontaneously appeal to that person's
   values rather than their own (Feinberg & Willer 2019; base rate measured on US
   partisans writing persuasive essays).
   → **State the case in terms the listener already holds**, not a repackaging of
   why you hold it.

**Procedure — before drafting.** Write four lines about the listener. Keep them
out of the message; show them to the user above the draft.

- What they already know, and what they don't.
- What they are currently busy with or worried about.
- What it costs them to say yes — time, risk, who they'd have to tell.
- What in this actually serves them, in their terms, or *nothing* if there is
  genuinely nothing.

If the last line is empty, say so in the message rather than manufacturing a
benefit. Naming the asymmetry outright — that there is nothing in it for them and
you are asking anyway — is a legitimate move and passes the admission rule. Phrase
it for the relationship; don't paste that sentence.

## Layer 2 — Channel and friction

- **Asking in person beat asking by email, by a wide margin.** In a matched-script
  experiment across 450 requests, face-to-face asks succeeded **34 times** more
  often than emailed ones — and senders predicted no difference (Roghanizad &
  Bohns 2017; single study, strangers, not independently replicated). The
  experiment compared those two channels only; phone and video are untested, so
  do not restate this as "synchronous beats text".
  → If the channel is yours to choose and the ask is important and refusable, ask
  in person. **If the user has already specified the channel, write for that
  channel** and note in one line that the same ask made in person is the stronger
  version. Async teams, time zones, and accessibility are all legitimate reasons
  text wins; a drafting skill whose best output is "don't send this" is useless.
- **Remove steps.** Reducing the work between "yes" and done is the lever
  practitioners rely on most (the "Easy" of the Behavioural Insights Team's EAST
  framework — a practitioner framework, not a meta-analysis that ranked levers
  against each other). Attach the file, pre-fill the form, propose two times
  instead of asking for availability, send the draft instead of the request to
  write one. Do the work yourself where you can, rather than promising it.
- **Make the action concrete: who does what, by when.** "Let me know what you
  think" is not an action. "Reply yes or no by Thursday" is — but only propose a
  date that is real. A deadline invented to create concreteness fails the
  admission rule; use the coarsest true unit instead ("this week", "before the
  release").
  The adjacent evidence is implementation intentions: if–then plans raise goal
  attainment at **d = .27–.66** depending on format and context (Gollwitzer &
  Sheeran 2006, 94 tests, d = .65 at the upper end; domain-specific and later
  estimates run lower). Mind the gap — those are plans the *actor* forms for
  themselves, not a date a sender writes into a request. The advice here is craft;
  the effect size is only why concreteness is worth believing in at all.
- **Give the ask one owner.** A request addressed to a group diffuses until nobody
  holds it. For announcements, where a group *is* the audience, name the owner of
  each action instead.

## Layer 3 — Remove barriers (subtractive)

Layer 3 takes things out — jargon, vagueness, structural noise. Layer 5 adds
persuasive devices. That is the boundary between them, and Layer 3 is worth much
more.

- **Jargon does not merely reduce comprehension — it reduces persuasion.**
  Technical terms lowered processing fluency and through it produced *greater
  motivated resistance to the argument*, higher risk perception, and lower
  support, with definitions available on hover and word count held constant
  (Bullock, Colón Amill, Shulman & Dixon 2019, N = 650). A reader who finds the
  text hard concludes the claim is suspect.
- **Ease is read as truth — with a caveat you must hold.** The robust, meta-
  analytic form of this is the *repetition* effect: repeated statements are judged
  more true, d = .39–.50 across 51 studies (Dechêne et al. 2010). The
  non-repetition forms — clearer typography, simpler phrasing — are supported but
  smaller and less consistently replicated (Reber & Schwarz 1999; Alter &
  Oppenheimer 2009), and the inference is a *learned* heuristic that weakens when
  the reader is deliberately checking accuracy.
  → Use this only subtractively: remove friction from claims that are true. See
  Layer 5 for why you must not use the repetition form.
- **Do not confuse "simple" with "casual."** Across three online studies and three
  field experiments (N = 67,632), **formal** government communications outperformed
  informal ones, against the predictions of both researchers and practitioners.
  Comprehension and perceived ease did not differ; perceived competence and
  trustworthiness of the sender, and perceived importance of the request, did
  (Linos, Lasky-Fink, Larkin, Moore & Kirkman 2023, *Nature Human Behaviour*).
  Scope is institution-to-citizen; between peers, match the room.
  → Cut jargon, nesting and length. Do not cut the register. Chattiness is not
  clarity, and it can cost the credibility that was carrying the request.
- **State uncertainty as a number, not as a vague word.** Across five experiments
  totalling n = 5,780 — including a preregistered replication and a BBC News field
  experiment — numeric ranges barely moved trust in the figure or the source, while
  verbal hedging ("there is some uncertainty around this") did measurably more
  damage (van der Bles et al. 2020). Two honest caveats: the BBC field experiment
  itself was directionally consistent but null, and Kreps & Kriner (2020) found a
  *very wide* range did reduce trust relative to a point estimate.
  → Write "3–5 days" or "about 70% confident", not "possibly", "somewhat",
  "I think maybe".
- **Distinguish marking ownership from marking doubt.** "I think X" claims the view
  as yours. "X, sort of, maybe" marks the claim as shaky. The first is free; the
  second is expensive. Hedges, hesitations and tag questions reduce both attitude
  change and perceived credibility (Burrell & Koper 1998, a book-chapter
  meta-analysis, largely courtroom-derived), and the damage peaks where it costs
  most: with a motivated reader, hedged strong arguments persuaded no better than
  weak ones (Blankenship & Holtgraves 2005). Hedge what you actually mean to mark
  as uncertain, and nothing else. Exception: in explicitly scientific framing,
  calibrated tentativeness can raise perceived trustworthiness (Jensen 2008).

## Layer 4 — Disagreement, bad news, repair

**Disagreement.** Receptive language is measurable and teachable. The markers that
make a counterpart perceive you as receptive: explicit **acknowledgment** of their
view, statements of **agreement** where agreement is real, **ownership** of your
view as yours, and **positive rather than negated** phrasing ("I agree that X"
beats "I don't think Y"). Writers taught the recipe were rated more persuasive and
more desirable to work with (Minson, Yeomans, Collins & Dorison 2024; in Wikipedia
editing data, receptive openings predicted fewer personal attacks in reply — that
specific field result is from the 2020 paper only). A scoring tool exists at
receptiveness.net.

> **Counter-evidence, stated up front.** Santoro, Broockman, Kalla & Porat (2025,
> *PNAS*) ran a longitudinal field experiment and found that adding high-quality
> listening to a persuasive appeal **did not increase persuasion at all**
> (d ≈ 0.06, not significant; −0.02 at five weeks). The manipulation was live
> conversation, so transfer to written receptive language is itself an assumption.
> Treat receptive language as good for the *relationship and the continued
> conversation* — which is well supported — and not as a lever on the other
> person's position.

**Listening.** Feeling heard has a substantial association with how much the
speaker trusts, and feels connected to, the person who listened to them — in this
section that person is you, not the listener the rest of this skill is about
(Vogel & Gastil 2025, meta-analysis: 50 studies, 127 effect sizes, N = 9,601
overall; trust and relatedness r > .60, but on k = 5 studies each).
Experimentally, high-quality listening lowers defensive processing and reduces
attitude extremity (Itzchakov, Kluger & Castro 2017). The meta-analysis also
reports a context moderator, but its description of the included studies cannot
be reconciled with it, so no context comparison is relied on here. Practically:
a reply that first restates their position in a form they would accept
outperforms one that opens with the rebuttal — for the relationship, if not for
their position.

**Ten minutes, in person or by phone.** A non-judgmental exchange of personal
experience shifted entrenched attitudes in about one in ten people, and the shift
survived three months and later counter-argument (Broockman & Kalla 2016,
*Science*; extended to phone canvassing in subsequent work). One of very few
interventions producing durable change. There is no evidence it works in writing.

**Power asymmetry is largely unaddressed above**, apart from the bound on
re-asking in Layer 1. Manager-to-report, report-to-manager, and threads where
colleagues are watching all change what you can say, and none of the cited
research models it. Say so rather than applying these rules as if the parties were
equals. Where one person is named but a group is reading, write for the named
person and assume the group is scoring both of you.

**Bad news.** 78% of recipients want the bad news first; senders prefer to lead
with the good and reverse the order (Legg & Sweeny 2014 — lab personality feedback
with a forced choice, so a narrow base). Lead with the bad news. Documented catch:
doing so reduces worry, and the relief slightly reduces motivation to act, so keep
the required action attached to the bad news rather than deferring it.
Carve-out: if the recipient needs context to act safely, give **at most one
sentence** of it first, then the bad news.

For a death, a layoff, or a serious medical or safety event, this stops being an
ordering question and nothing else in this skill applies either. The branch is:
say it plainly and early in the fewest words that are still complete; give the
reason once, without justification or softening; then what happens next and who
they can talk to. Anything with employment, medical or legal consequence goes to
whoever owns it before it is sent.

**Apology.** Six components, unequal, and more of them is better (Lewicki, Polin &
Lount 2016, two studies). By measured weight:

1. **Acknowledgement of responsibility** — by a clear margin the most important.
   "It was my mistake", not "mistakes were made" and not "I'm sorry you feel that way".
2. **An offer of repair** — a concrete thing you will do. Second.
3. Expression of regret, explanation of what went wrong, declaration of repentance
   — roughly tied, all worth including.
4. A request for forgiveness — least important; drop it when it makes the apology
   about your relief rather than their loss.

**Liability carve-out:** for customer incidents, HR matters, safety events, or
anything with contractual or legal exposure, an admission of responsibility is not
yours to draft unilaterally — and a sendable draft that contains one will get sent.
So do not produce one. Write the facts that are yours to state, leave the
responsibility sentence as an explicit placeholder, and say above the draft that
the placeholder is for whoever owns the liability to fill.

## Layer 5 — Wording, last and least

Reach here only after 1–4, and only for messages where it matters.

- **A concrete story beats an equivalent argument, modestly.** r = .17–.23 across
  beliefs, attitudes, intentions and behaviours (Braddock & Dillard 2016,
  meta-analysis) — roughly d = .35–.47, though the .23 top end is behaviours on
  k = 5. Corroborated in the field: the Santoro et al. (2025) experiment whose
  listening arm was null found the persuasive narrative itself moved attitudes
  ~0.30 SD, still ~0.20 SD at five weeks. One specific case beats one general
  claim, and this is the largest lever in Layer 5 by some distance.
- **Prefer the specific noun and the concrete number** to the abstraction.
- **Do not use repetition to make a claim feel true.** This is the same effect
  Layer 3 cites, used additively instead of subtractively, and that is the line:
  removing friction from a true claim is fair; repeating a claim so it accretes
  credibility is manufacturing belief and fails the admission rule. It also works
  on you — a claim you have written five times starts to feel verified.

**Techniques to avoid — unsupported by evidence, or excluded by the admission rule:**

| Technique | Why not |
| --- | --- |
| Loss framing ("don't miss out", "you'll lose X") | O'Keefe & Jensen (2006, *Communication Yearbook*; 165 effect sizes, N = 50,780): loss-framed appeals are not generally more persuasive. The one significant advantage found (2009, *Journal of Communication*, 53 studies) is r ≈ .04 and confined to breast-cancer detection messages. **This bans reaching for loss wording as a lever — not stating a real downside.** A cost the listener needs in order to decide is required by the admission rule; write it plainly, as a fact rather than as a threat |
| "But you are free to refuse" | A 2023 preregistered re-examination of 52 experiments (N = 19,528) found the effect vanishes in the low-risk-of-bias subset: g = 0.11, 95% CI [−0.18, 0.40] |
| A throwaway reason ("because I need to") | Holds only for trivially small requests; collapses for anything substantial (Langer, Blank & Chanowitz 1978 — the popular retelling drops the boundary condition) |
| A small gift or favour beforehand | The obligation is largely gone within a week (Burger et al. 1997) |
| "Thanks in advance" and other pre-emptive gratitude | No study tests it. The paper usually cited measures gratitude expressed *after* someone helped, which is a different act; nothing supports thanking someone for a thing they have not agreed to. Excluded on the admission rule alone: it books the yes before they give it |
| Manufactured scarcity, urgency, or social proof | Fails the admission rule outright |

## Evidence grades

Grades for the load-bearing claims. Anything not listed here — friction reduction,
one-owner asks, the four-line procedure — is reasoning from the graded claims, not
an independently measured result, and should be treated as craft.

| Claim | Grade |
| --- | --- |
| Persuasion effects are small | Established for institutional contexts (49 field experiments / 126 RCTs); transfer to interpersonal is an assumption |
| Wording effects are smaller still | **Inference** — no cited study manipulates wording |
| Requesters underestimate compliance | Established (>14,000 requests) — caveat: largely one research programme |
| Senders overestimate how well they were understood | Established (multiple paradigms, incl. a 5-experiment email study) |
| Senders argue from their own values, not the listener's | Supported but narrow — a base rate under 10%, measured on US partisans writing political essays. That reframing to the listener's values then *works* is a separate and weaker claim |
| Repetition raises judged truth | Established (51-study meta-analysis) — cited as a hazard, not a tool |
| Non-repetition fluency raises judged truth | Supported, smaller, less consistently replicated |
| Jargon reduces persuasion, not just comprehension | Supported (one well-powered experiment + follow-ups) |
| Formal beats informal | Supported (N = 67,632, 3 field experiments) — institution-to-citizen only |
| Numeric uncertainty is safe; verbal vagueness is not | Supported (5 experiments) — the field arm was null; very wide ranges are an exception |
| Hedges cost credibility | Supported but dated (1998 book-chapter meta-analysis, largely courtroom-derived) |
| Channel effect (in person ≫ email) | Supported (single 450-request experiment, strangers; large effect, unreplicated) — face-to-face vs email only; phone and video untested |
| If–then plans raise follow-through | Established (94 tests, d = .65; broader estimates .27–.66) — but for plans the actor forms for themselves; a date written into someone else's request is an **inference** |
| Feeling heard predicts trust and relatedness | Supported (meta-analysis, N = 9,601) |
| Receptive language changes the other side's position | **Not supported** — the one field experiment found a null |
| Bad news first; responsibility-first apologies | Supported, narrow base (one lab study / two studies) |
| Narrative beats argument | Supported but small (meta-analysis, r ≈ .2; plus durable field evidence at ~0.30 SD) |
| Loss framing, BYAF, placebic reasons, pre-giving | **Not supported** |

When in doubt, use the higher-graded layer and stop.

## Checklist

- If the message needed them: did I write the four listener lines, and keep them
  out of the message?
- If there is an ask: is it stated as an ask, with one owner? If timing matters, is
  the date a real one — and written as a wish where it is a wish?
- Is this the right channel — and if I couldn't choose it, did I say so once?
- What work am I leaving them that I could do myself?
- Any jargon, any nesting? Any casualness I mistook for clarity?
- Is every uncertainty a number, and every hedge one I mean?
- Did I assume anything about this person I was told, versus anything I invented?
- Would they, knowing how I built this message, still call the ask fair?

## Output

Return the draft. Above it, put the four listener lines (omit them if the
proportionality rule applied) and — if you had to assume anything — the assumption
block. Below it, one line each for anything the user asked for that you left out,
and why. If the user's existing draft already clears the checklist, say so and
change nothing; no rewrite is a valid result.

## Scope and limits

- **For composing and revising what a message says**: requests, proposals,
  explanations, disagreements, bad news, apologies. It changes content and stance.
- **Not for visual formatting** — line breaks, chunking, headers, symbols. It does
  prescribe *rhetorical* ordering (bad news first, their position before your
  rebuttal); it says nothing about layout.
- **One named listener, or a bounded group you know** (a team channel, a named
  set of customers). For a bounded group, the four lines are written about the
  group's shared state, and the one-owner rule becomes "name the owner of each
  action". Marketing copy, fundraising, cold outreach and public posts fall
  outside: there is no listener whose state you can know. Say so rather than
  inventing a persona.
- **Sender side only.** How to decline, how to receive criticism, and how to
  respond to a manipulative message are outside this.
- **Not for adversarial counterparties.** The admission rule is the wrong standard
  for a demand letter or a legal dispute.
- **English-derived.** The formality finding is UK/US institution-to-citizen; the
  receptiveness markers come from an English NLP model. Languages with
  grammaticalized politeness are not covered — the register layer is a local
  question everywhere, and especially there.
- **Not a rescue for a bad ask.** If the request is genuinely against the
  listener's interest and you have nothing to offer, no framing fixes it. Say what
  it is, or don't ask.
- **Diminishing returns are real.** Once Layers 1 and 2 are done, the remaining
  layers are worth much less. Do not spend an hour on Layer 5.

Full citations, sample sizes, limitations, and the excluded-technique dossier:
`references/evidence.md`.
