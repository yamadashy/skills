# Evidence trail

Full citations for `SKILL.md`, with sample sizes and known limitations. Sources
were checked individually; where a widely repeated claim did not survive the
check, it is recorded here rather than quietly dropped. Where a figure could not
be verified from available sources, it was removed rather than replaced with a
plausible-sounding substitute — those removals are noted.

## Baseline: how large are persuasion effects?

- **Kalla, J. L., & Broockman, D. E. (2018).** The Minimal Persuasive Effects of
  Campaign Contact in General Elections: Evidence from 49 Field Experiments.
  *American Political Science Review*, 112(1), 148–166.
  Meta-analysis of 40 field experiments plus 9 original ones. Best estimate of the
  effect of campaign contact and advertising on candidate choice in **general
  elections**: zero. Exceptions the paper itself reports: primaries and
  ballot-measure campaigns, where partisan cues are unavailable, do show clear
  effects; also candidates holding unusually unpopular positions combined with
  heavy targeting, and early contact measured immediately, which then decays.

- **DellaVigna, S., & Linos, E. (2022).** RCTs to Scale: Comprehensive Evidence
  From Two Nudge Units. *Econometrica*, 90(1), 81–116.
  126 RCTs, 23 million individuals. Nudge-unit trials: 1.4pp absolute (8.0%
  relative). A comparison sample of academically published nudge trials drawn from
  two meta-analyses: 8.7pp (33.4%). These are **different sets of interventions**,
  not the same ones re-measured. Publication bias, exacerbated by low power,
  accounts for the full difference. Average academic treatment arm: 484 participants.

**Scope limitation on both:** neither manipulates wording, and both are
institution-to-citizen. `SKILL.md` uses them to set a prior for interpersonal
messaging, which is an inference, and says so.

## Layer 1 — sender biases

- **Flynn, F. J., & Lake (Bohns), V. K. (2008).** If You Need Help, Just Ask:
  Underestimating Compliance With Direct Requests for Help. *JPSP*.
- **Bohns, V. K. (2016).** (Mis)Understanding Our Influence Over Others.
  *Current Directions in Psychological Science*, 25(2).
  Aggregates studies in which participants made requests of **>14,000 strangers**.
  Mean underestimation of compliance: **48%** — a relative shortfall against the
  actual compliance rate, not 48 percentage points; the skill's "by roughly half"
  is that same figure in words, and neither should be read as a point estimate for
  any one request.  Mechanism: requesters fail to appreciate how socially costly
  refusal feels.
  Extensions: cross-cultural (Bohns et al. 2011, *JESP* — predicted 13.4 asks
  needed vs 7.5 actual); closeness as moderator (Deri, Stein & Bohns 2019 — smaller
  but present for friends); persists after an initial refusal (Newark, Flynn &
  Bohns 2014); similar for large and small requests; replicated in a legal-consent
  context (Sommers & Bohns 2024).
  **Limitations kept visible in the skill:** largely one research programme, no
  adversarial multi-lab replication located, and the re-asking result is about
  strangers and small favours. `SKILL.md` bounds the "ask again" advice for that
  reason — the unbounded version is harmful advice in power-asymmetric or personal
  contexts and is not what this literature supports.

- **Camerer, C., Loewenstein, G., & Weber, M. (1989).** The Curse of Knowledge in
  Economic Settings: An Experimental Analysis. *Journal of Political Economy*.
  Informed participants could not discount private knowledge when predicting
  uninformed traders, despite instruction and financial incentive. Roots in
  Fischhoff (1975), hindsight bias. Extended to verbal reference by Keysar et al.
  (2000).
  *Not cited as evidence:* the "tappers and listeners" study (Newton 1990) is a
  doctoral dissertation, not peer-reviewed, popularised by *Made to Stick*.

- **Kruger, J., Epley, N., Parker, J., & Ng, Z.-W. (2005).** Egocentrism over
  e-mail: Can we communicate as well as we think? *JPSP*, 89(6), 925–936.
  Five experiments. People overestimate both their ability to convey tone
  (sarcastic / serious / funny) over email and their ability to read it. Mechanism
  is egocentrism: writers hear their own intended tone as they write. A debiasing
  manipulation that worked: read the sentence aloud in the *opposite* tone before
  sending. No independent replication located.

- **Feinberg, M., & Willer, R. (2019).** Moral reframing. *Social and Personality
  Psychology Compass*, 13(12), e12501.
  Review, not a meta-analysis; no pooled effect size exists. The load-bearing
  finding used in the skill is the base rate: across two studies, **fewer than 10%**
  of participants asked to persuade a political opponent spontaneously appealed to
  that opponent's values. Measured on US partisans writing persuasive essays; the
  skill notes that generalisation to all senders is an extrapolation.
  Underlying experiments: Feinberg & Willer (2013), purity-framed environmental
  appeals to conservatives; (2015), fairness-framed military spending to liberals.
  Voelkel & Feinberg (2018) is weaker — non-significant interaction in Study 2, no
  control conditions.

## Layer 2 — channel and friction

- **Roghanizad, M. M., & Bohns, V. K. (2017).** Ask in person: You're less
  persuasive than you think over email. *Journal of Experimental Social Psychology*.
  45 participants each asked 10 strangers (450 requests) with an identical script.
  Face-to-face requests were **34× more effective**; both groups predicted ~50%
  success. Single study, strangers only, not independently replicated. **The
  comparison is face-to-face vs email, not synchronous vs asynchronous** — phone
  and video were not tested, and an earlier draft of the skill over-generalised
  this to "synchronous beats text" and to recommending a call. Corrected. The
  skill presents it as a strong but singular result and explicitly refuses to let
  it override a user's stated channel.

- **Behavioural Insights Team (2014).** EAST: Four Simple Ways to Apply
  Behavioural Insights.
  "Easy" — friction reduction — is presented there as the most consistently
  effective element, and this is consistent with the defaults literature generally.
  **EAST is a practitioner framework, not a meta-analysis that put behavioural
  levers on a common metric**, so the skill no longer calls friction reduction
  "the most reliably effective lever available"; it says practitioners rely on it
  most. Graded as craft.
  *Removed:* an earlier draft cited a "63% → 81%" UK pension auto-enrolment figure.
  It could not be traced to BIT's report or to a DWP evaluation and appears only in
  secondary decks. No substitute figure is asserted here.

- **Gollwitzer, P. M., & Sheeran, P. (2006).** *Advances in Experimental Social
  Psychology*, 38, 69–119. 94 independent tests, >8,000 participants, d = .65
  (95% CI 0.6–0.7). Domain-specific estimates are lower (Presseau et al. 2017:
  d ≈ .14–.37 for objectively measured health behaviour; Adriaanse et al. 2011:
  d = .51 adding healthy foods, .29 reducing unhealthy eating). Hence the
  .27–.66 range the skill quotes; .65 is the upper end, not the average.
  *Bibliographic note:* an earlier draft led with "Sheeran, Listrom & Gollwitzer
  2024, 642 tests". Title, journal and DOI for that extension could not be
  confirmed here, so the skill now leads with the 2006 meta-analysis, which can be.
  **Construct gap, now stated in the skill:** an implementation intention is an
  if–then plan the *actor* forms for their own behaviour. A sender writing
  "reply by Thursday" into a request is not that, and this literature does not
  measure it. The concreteness advice in Layer 2 is craft; the effect size is
  background, not its warrant.

## Layer 3 — removing barriers

- **Bullock, O. M., Colón Amill, D., Shulman, H. C., & Dixon, G. N. (2019).**
  Jargon as a barrier to effective science communication: Evidence from
  metacognition. *Public Understanding of Science*, 28(7), 845–853.
  N = 650. Jargon lowered processing fluency, and through it increased **motivated
  resistance to persuasion**, raised risk perception and lowered support for
  adoption. Definitions were available on hover and word count held constant, so
  the effect is not about missing information. Follow-ups: Shulman et al. (2020),
  engagement; Shulman et al. (2021), credibility and perceived threat.
  Counterpoint: a 2025 *Learning and Instruction* paper argues jargon avoidance can
  reduce ascribed expertise — a second reason the skill separates "simple" from
  "casual".
  *Citation note:* frequently mis-cited as "Bullock, Shulman & Huskey 2019".
  Huskey is a co-author on the 2021 narrative-fluency paper, not this one.

- **Dechêne, A., Stahl, C., Hansen, J., & Wänke, M. (2010).** The Truth About the
  Truth: A Meta-Analytic Review of the Truth Effect. *PSPR*.
  51 studies, 102 effect sizes, **d = .39–.50** depending on measure.
  **Important scoping point:** this is the *repetition-induced* truth effect —
  it measures how much repeating a statement raises its truth rating. It is not a
  measurement of "write more fluently → be believed more". An earlier draft of the
  skill used it for the latter while simultaneously forbidding repetition in Layer
  5; that contradiction is now resolved by citing repetition as a hazard and using
  separate sources for non-repetition fluency.
  Non-repetition fluency: **Reber, R., & Schwarz, N. (1999)**, Effects of
  perceptual fluency on judgments of truth, *Consciousness and Cognition* (small,
  early); **Alter, A. L., & Oppenheimer, D. M. (2009)**, Uniting the tribes of
  fluency to form a metacognitive nation, *PSPR* (review). Both are weaker evidence
  than Dechêne and the skill grades them accordingly.
  Boundary conditions: the fluency→truth inference is a *learned* attribution
  (Unkelbach, on reversing the truth effect); it weakens under accuracy-focused
  reading; it disappears when readers attribute the ease to its real source.
  *Removed:* two specific claims attributed here to Ye et al. (2026,
  *Nature Communications*) — that truth status does not moderate the effect, and
  that the effect intensifies under cognitive load — could not be confirmed against
  the paper and are no longer asserted.

- **Linos, E., Lasky-Fink, J., Larkin, C., Moore, L., & Kirkman, E. (2023).**
  The formality effect. *Nature Human Behaviour* (online Nov 2023; 8(2), 300–310).
  doi 10.1038/s41562-023-01761-z.
  Three online studies and three field experiments, **N = 67,632**. Formal
  government communications outperformed informal ones, contrary to both
  researcher and practitioner predictions. Mediators: perceived competence and
  trustworthiness of the source, and perceived importance of the request. **No**
  difference in comprehension or perceived ease of acting.
  Scope: institution-to-citizen. Transfer to peer communication is untested; the
  skill flags this rather than generalising.

- **van der Bles, A. M., van der Linden, S., Freeman, A. L. J., & Spiegelhalter,
  D. J. (2020).** The effects of communicating uncertainty on public trust in facts
  and numbers. *PNAS*, 117(14), 7672–7683.
  Five experiments, **total n = 5,780**, including a preregistered national-sample
  replication and a BBC News field experiment. Numeric uncertainty (a range) had
  only a minor effect on trust; verbal uncertainty produced the larger — still
  small — decrease. **The BBC field arm, the most ecologically valid test, was
  directionally consistent but null**; the skill now says so.
  Framework paper: van der Bles et al. (2019), *Royal Society Open Science*,
  6:181870, distinguishing direct (numeric) from indirect (caveat) uncertainty.
  Exception: **Kreps & Kriner (2020)** found reduced trust when COVID-19
  projections were given as a *very large* range rather than a point estimate.

- **Burrell, N. A., & Koper, R. J. (1998).** The efficacy of powerful/powerless
  language on attitudes and source credibility. In Allen & Preiss (eds),
  *Persuasion: Advances Through Meta-Analysis*, 203–215.
  Powerless language — intensifiers, hedges, hesitations, tag questions — reduces
  both attitude change and perceived source credibility. A book-chapter
  meta-analysis drawing largely on courtroom/testimony research; the pooled k and N
  could not be verified from available sources and are not asserted. This is the
  oldest and thinnest source in the document and the skill grades it "supported but
  dated".
- **Blankenship, K. L., & Holtgraves, T. (2005).** *Journal of Language and Social
  Psychology*. Under **high** message relevance, powerless markers eliminated the
  advantage of strong arguments — hedged strong arguments persuaded no better than
  weak ones. Under **low** relevance, tag questions slightly *helped*.
  Counter-case: **Jensen (2008)**, *Human Communication Research* — hedging can
  raise scientists' perceived trustworthiness. Consistent with van der Bles once
  you separate calibrated numeric uncertainty from vague verbal hedging, and
  consistent with the skill's ownership-vs-confidence distinction ("I think X"
  claims the view; "X, sort of" undermines it).

## Layer 4 — disagreement, listening, bad news, repair

- **Minson, J., Yeomans, M., Collins, H., & Dorison, C. (2024)** — three
  well-powered online studies plus lab and forum data, on conversational
  receptiveness as a linguistic style transmitting between parties. **Cite this in
  preference to** the original:
  **Yeomans, M., Minson, J., Collins, H., Chen, F., & Gino, F. (2020).**
  Conversational receptiveness: Improving engagement with opposing views. *OBHDP*,
  160, 131–148 — NLP algorithm identifying receptiveness markers (acknowledgment,
  agreement, subjectivity, positive emotion); Wikipedia field data showing
  receptive posts predict fewer personal attacks; validated "receptiveness recipe".
  **Why the preference:** F. Gino is a co-author on the 2020 paper and has a
  concluded research-misconduct finding in other work. The construct is carried by
  the 2024 paper, which does not have her as a co-author — but note what that is
  and is not: Minson, Yeomans and Collins are authors of both, so this is a
  **same-team follow-up, not an independent replication**. An earlier draft said
  the construct "survives independently"; it does not, and no independent
  replication was located. Tool: receptiveness.net.

- **Santoro, E., Broockman, D., Kalla, J., & Porat, R. (2025).** Listen for a
  change? A longitudinal field experiment on listening's potential to enhance
  persuasion. *PNAS*, 122(8), e2421982122.
  **Counter-evidence, surfaced in the skill body rather than buried here.** Adding
  high-quality listening to a persuasive appeal produced **no additional
  persuasion**: d = 0.06–0.07, p > .10, decaying to d = −0.02 at five weeks. A
  clean null, not an attenuated effect. Caveat in the other direction: the
  manipulation was a live video conversation, so transfer to *written* receptive
  language is an assumption — the skill says so, since it is using the transfer to
  demote a claim.
  The same experiment supports Layer 5: **the persuasive narrative itself worked
  and lasted** — roughly 0.30 SD, still ~0.20 SD at five weeks.
  Accordingly the skill grades "receptive language changes the other side's
  position" as not supported, while keeping receptive language for the
  relationship and the continued conversation, which the Vogel & Gastil and
  Itzchakov lines do support.

- **Vogel, E., & Gastil, J. (2025).** The Evidentiary Basis for Political
  Listening: A Meta-Analysis of the Effect of Feeling Heard. *Political
  Communication*, 42(4).
  50 studies from 25 articles, 127 effect sizes, **N = 9,601**. Feeling heard had a
  significant effect on all outcomes analysed; strongest for the speaker's
  perceptions of the listener — relatedness (k = 5, r = .62) and trust (k = 5,
  r = .68). Those two headline correlations rest on **k = 5 studies each**.
  *Unresolved:* notes taken here record both a moderator result — stronger in
  workplace than political contexts — and a statement that the included studies
  were not conducted in political contexts. Those cannot both be right, and the
  discrepancy was not resolvable from available sources, so the skill relies on
  neither and makes no context comparison.
  *Correction:* an earlier draft attributed this meta-analysis to Itzchakov &
  Kluger. They are not the authors.
- **Itzchakov, G., Kluger, A. N., & Castro, D. R. (2017).** I Am Aware of My
  Inconsistencies but Can Tolerate Them. *PSPB*. Four experiments: high-quality
  listening lowers speakers' social anxiety and defensive processing, increasing
  objective attitude ambivalence and decreasing attitude extremity.

- **Broockman, D., & Kalla, J. (2016).** Durably reducing transphobia: A field
  experiment on door-to-door canvassing. *Science*, 352(6282), 220–224.
  56 canvassers, 501 voters, ~10-minute conversations encouraging active
  perspective-taking. Attitude change in roughly 1 in 10 voters, persisting
  3 months and surviving later counter-argument. Extended by Kalla & Broockman
  (2020), *APSR* — new experiments, not a direct replication — and the same
  approach has been run by **phone**, so the skill says "in person or by phone"
  rather than restricting it to face-to-face. There is no evidence for a written
  version; that is stated as an absence of evidence, not a demonstrated failure.
  Context: these authors exposed the fraudulent LaCour study in this area, which is
  part of why the line is unusually well-scrutinised.

- **Legg, A. M., & Sweeny, K. (2014).** Do You Want the Good News or the Bad News
  First? *PSPB*, 40, 279–288.
  **78%** of recipients want bad news first; givers prefer to lead with good news.
  Study 3: bad-news-first reduces worry, but that relief undermines motivation to
  change behaviour. Lab studies using personality feedback with a forced choice —
  a narrow base, which is why the skill adds carve-outs for news requiring context
  to act on safely, and for deaths and layoffs. The "bad news sandwich" primarily
  serves the giver.

- **Lewicki, R. J., Polin, B., & Lount, R. B. Jr. (2016).** An Exploration of the
  Structure of Effective Apologies. *Negotiation and Conflict Management Research*,
  9, 177–196.
  Two studies (first: 333 adults). Six components presented singly and in
  combination. Ranking: **acknowledgement of responsibility** highest, **offer of
  repair** second, then expression of regret / explanation / declaration of
  repentance roughly tied, **request for forgiveness** lowest. More components →
  more effective. Component value did not differ between competence- and
  integrity-based violations. Scenario-based, not field data — hence the skill's
  liability carve-out, which is a legal caution rather than a finding.

## Layer 5 — wording

- **Braddock, K., & Dillard, J. P. (2016).** Meta-analytic evidence for the
  persuasive effect of narratives. *Communication Monographs*, 83(4), 446–467.
  Beliefs r = .17 (k = 37, N = 7,376); attitudes r = .19 (k = 40, N = 7,132);
  intentions r = .17 (k = 28, N = 5,211); behaviours r = .23 (k = 5, N = 978 —
  thin). Converted for the skill: r ≈ .17–.23 corresponds to d ≈ .35–.47.
  (An earlier draft glossed r = .2 as "one-fifth of a standard deviation", which
  confuses r with d.) Fictionality results mixed; medium and design did not
  moderate; substantial unexplained heterogeneity remains.
  Field corroboration: Santoro et al. (2025) — see Layer 4 — found the persuasive
  narrative arm moved attitudes ~0.30 SD, still ~0.20 SD at five weeks. Narrative
  is the best-supported item in Layer 5 and the only one with durable field
  evidence.

## Excluded techniques — the dossier

Each is widely recommended in popular communication writing and did not survive
checking.

- **Loss framing.** O'Keefe & Jensen's series: overall persuasiveness
  (2006, *Communication Yearbook*; 165 effect sizes, N = 50,780) — loss-framed
  appeals are **not** generally more persuasive; gain-framed are better for disease
  prevention. Disease detection (2009, *Journal of Communication*; 53 studies,
  N = 9,145): the loss-framed advantage is statistically significant but
  corresponds to r ≈ .04 and is confined to breast-cancer detection messages.
  Message processing (2008, *Communication Studies*; 42 effect sizes, N = 6,378):
  gain-framed messages produce *slightly greater* engagement — the opposite of the
  theoretical prediction.
  **Scope of the exclusion:** what fails is loss *framing as a lever* — choosing
  loss wording because it is supposed to work better. Stating a real downside is a
  different act and the admission rule requires it: a cost that decides the
  listener's answer may not be omitted. The skill now says this in the table,
  because the two rules read as contradictory otherwise.

- **"But you are free" (BYAF).** Carpenter (2013), *Communication Studies*, 42
  studies, reported it effective. A preregistered re-examination
  (*Meta-Psychology*, 2023; 52 experiments, N = 19,528, 74 effect sizes) found
  g = 0.44 overall — but **only 7 studies were rated low risk of bias, and
  restricted to those, g = 0.11, 95% CI [−0.18, 0.40]**. Reproducibility indicators
  critically low (R-index 9.77%; expected discovery rate 6%). Not usable.

- **Placebic reasons ("because I need to").** Langer, Blank & Chanowitz (1978).
  The famous 93%-vs-94% result holds **only for a five-copy request**. For a large
  request, placebic compliance collapses (~24%); overall, placebic requests were
  refused 50% of the time. Folkes (1985) failed to replicate in two of four studies
  and offered a mindfulness reinterpretation; a 2008 individual-differences study
  did replicate the small-request effect. Gelman's re-analysis puts the key
  difference at 12.5pp with SE 11pp. Language Log (Liberman) documents widespread
  mis-citation, including by Kahneman (2003).

- **Pre-giving / reciprocity.** Burger et al. (1997): for the small favours used in
  research settings, the obligation to reciprocate **virtually disappears when the
  request comes a week later**. No dedicated meta-analysis of pre-giving compliance
  effect sizes was located. Related: "returnable reciprocity" outperforms standard
  gifts, but its authors note it works via guilt and imposes psychological costs.

- **Pre-emptive gratitude ("thanks in advance").** No study of it was located.
  The paper usually reached for — Grant, A. M., & Gino, F. (2010), "A little
  thanks goes a long way", *JPSP*, 98(6), 946–955 — manipulates gratitude
  expressed **after** someone has already helped, which is a different act, so it
  cannot support the advice whatever its status. An earlier draft of the skill
  excluded the technique on research-integrity grounds; that was the wrong reason
  for the right conclusion, and the exclusion now rests on the admission rule
  alone. (For completeness: the 2010 paper is **not retracted** — the retracted
  *JPSP* paper is a different, 2020 one.)

- **"Cues of working together."** Carr, P. B., & Walton, G. M. (2014), *JESP*, 53,
  169–184. Five experiments; no independent replication located.

- **"Wise feedback"** (high standards + assurance of ability). Yeager et al.
  (2014), *JEP: General*, 143(2), 804–824 — three double-blind randomised field
  experiments, positive. **Troy et al. (2024)**, *Psychology in the Schools* — the
  first conceptual replication in a new setting (94 undergraduates) — **did not
  replicate**. Excluded pending better evidence.

## Model-specific

- **Salvi, F., Horta Ribeiro, M., Gallotti, R., & West, R. (2025).** On the
  conversational persuasiveness of GPT-4. *Nature Human Behaviour*, 9, 1645–1653.
  Preregistered 2×2×3 design. **In debate pairs where the two sides were not
  equally persuasive**, GPT-4 with access to basic sociodemographic data was the
  more persuasive side 64.4% of the time (+81.2% odds of higher post-debate
  agreement, 95% CI [+26.0%, +160.7%]). The conditional clause matters and the
  skill states it. US participants, structured debate format. This is the empirical
  basis for putting the full-disclosure test at the foundation rather than in a
  footnote.

- **Deliberately not cited:** Costello, Pennycook & Rand (2024), *Science* —
  "Durably reducing conspiracy beliefs through dialogues with AI". It carries an
  Editorial Expression of Concern (*Science*, 11 June 2026, doi
  10.1126/science.aej2383) over screening-criteria inconsistencies and spliced rows
  in the public dataset.
