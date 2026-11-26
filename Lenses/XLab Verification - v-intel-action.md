---
id: '7f63d0b2-6f71-4ca8-a58a-fcc0511666f7'
title: "From Intelligence Lead to Verification Action"
tldr: "Treaties protect each side's satellites but oblige nobody to share what they see. With that precedent and the MIRI draft's text in hand, act like a regime that wants to survive its first ambiguous case: compare against declarations, escalate one rung at a time, and write down what you could not resolve. Then look at the draft's NTM article as a negotiator would and red-line it for both parties."
summary_for_tutor: "Two readings in one lens, then the unit's written output. The first, on intelligence institutions and treaty design, has no questions. It sets out the asymmetric precedent: weak on sharing (no obligation on intelligence agencies to share with verifiers, Baker section 2.3.3) and strong on protection (the noninterference-with-NTM and no-deliberate-concealment clauses, which Gottemoeller called one of the easiest points of agreement in New START). It then gives the Six Layers argument for national rather than international agencies, MIRI's Article II definition of national technical means (item 17) and Article X ¶1(b)(i) to (iii), embedded as excerpts of the paper, and the authentication problem for shared intelligence. Clause (iii), which encourages but does not obligate cooperation, is the lens's evidence that the precedent is weak on sharing. The second is a short reading on acting on a lead: compare against declarations, climb the escalation ladder (task more collection, seek corroboration, trigger an audit or challenge inspection), and record confidence, dissent and unresolved blind spots. Then the written output, a graded, required open question with first-answer feedback: red-line the NTM article in about 700 words. The learner works from the treaty text quoted earlier in the lens, item 17 of MIRI's Article II definitions plus Article X ¶1(b)(i) to (iii), the noninterference, no-deliberate-concealment and encouraged-but-not-obligated cooperation clauses. They then mark at least three gaps, redraft one provision, write or defend the absence of a sharing clause, test it against the rule that states sign what is symmetric, cheap and checkable, and end with one paragraph each on why Washington and Beijing accept it. Assess on the five listed criteria. Expect the discovery that noninterference is easy and drafting dies on sharing. Do not hand it to the learner before they write."
tags: [wip]
reading_minutes: 13
tutor_minutes: 40
---
#### Text
content::
The previous sections were about what a watcher can see and conclude. This one
is about the institutions that do the watching, and what a treaty can say about
them.

The precedent is asymmetric, and the asymmetry is the lesson: **weak on
sharing, strong on protection.**

\## Sharing

Nuclear treaties impose no obligation on intelligence agencies to share with
treaty verifiers. Sharing is voluntary, informal, and inconsistent (Baker
§2.3.3), and protection of sources and methods is *why*. Third-party verifiers
lack major states' collection capabilities, so the body formally charged with
verifying is rarely the body that can see.

\## Protection

Noninterference-with-NTM and no-deliberate-concealment clauses are standard
arms-control furniture: no blinding satellites, no nets over mobile missiles.
Rose Gottemoeller, the US chief negotiator for New START, called NTM
noninterference "one of the earliest and easiest points of agreement" in those
negotiations.

This is the low-hanging fruit of the whole unit. Note the contrast with
sharing, where drafting is hard. The contrast is worth carrying into the written
output.

\## Architecture: national or international?

*Six Layers* argues (in an emphasis footnote, so hold the modality) for
relying on **national** agencies rather than empowering an international agency
to spy. Three reasons: decades of built-up capability; the IAEA precedent of
learning about violations from national agencies; and the new risks an
espionage-authorized international body would itself create.

The consequence is that weak-intelligence states free-ride on stronger states'
collection. In the US–China case, each side trusts its own agencies to verify
the other.

\## Concrete text

MIRI's draft agreement adopts the arms-control boilerplate wholesale. Item 17
of Article II's definitions list defines national technical means to include
satellite, aerial, cyber, signals, and thermal-imagery remote sensing, and
Article X ¶1(b) carries the noninterference and no-concealment language
borrowed from the ABM Treaty, INF, CTBT, and New START.

It is a real text, and it is meant to be marked up rather than admired. Here
are the two passages, from the paper itself.

**Article II: Definitions, item 17**

#### Article
source:: [[../articles/scher-an-international-agreement-to-prevent-the-premature-creation-of-artificial-superintelligence]]
from:: National Technical Means (NTM) includes satellite
to:: for verification consistent with this Agreement.

#### Text
content::
**Article X: Information Consolidation and Challenge Inspections, ¶1(b)**

#### Article
from:: For the purpose of providing assurance of compliance
to:: as relevant to this Agreement.

#### Text
content::
Read ¶1(b)(iii) against (i) and (ii). Protection is an undertaking whereas sharing is
an encouragement. That is the core asymmetry of this whole section, and the red-line question at the end of this lens asks you to draft the obligation it declines to impose. It also tests your draft against one rule of thumb: states sign what is symmetric (it binds both sides the same way), cheap (complying costs little) and checkable (each side can tell whether the other complies).

\## Authenticating what gets shared

Baker's "shared documents might be fake" problem is an evidence-credibility
question, and it belongs here: how do rivals authenticate intelligence passed
between them (signal authentication, chain of custody)?

The cryptographic machinery for this (zero-knowledge proofs, multi-party
computation, attestation) is covered with the privacy-preserving mechanisms in [[../Lenses/XLab Verification - v-mechanism-privacy|Unit 4]] from Compute Verification 1. Arms control has a physical precedent: Glaser, Barak and Goldston (Nature, 2014) designed a test that lets inspectors confirm a warhead matches a known genuine one without learning anything about its design. That is the kind of guarantee rivals want when they share evidence: proof that a claim holds, without exposing what lies behind it.

\## Readings

- MIRI draft US–China agreement: Article II's definitions and Article X,
  verbatim (pp. 20, 39–40). The passages excerpted above are the ones this
  section turns on. Ideally you have read the whole draft treaty at this point.
Read Baker's section on intelligence sharing, then compare the institutional options in *Six Layers*.

#### Article
source:: [[../articles/baker-nuclear-arms-control-verification-and-lessons-for-ai-treaties]]
from:: #### 2.3.3 Intelligence sharing
to:: The sharing of information between treaty-implementing agencies and national intelligence agencies (or between multiple national intelligence agencies) can help treaty verifiers reach conclusions that would be harder to reach with more limited information. Nuclear arms control treaties have no requirements for national intelligence agencies to share their information; the process is voluntary, informal, and inconsistent.

#### Article
source:: [[../articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment]]
from:: Verifier—bilateral or third-party? Though this report’s focus is not on institution design, it is worth noting that Provers may more easily trust that a third-party Verifier will act in good faith, rather than seeking to steal information or compromise equipment. On the other hand, third-party Verifiers may take longer to set up and may not be as effective. In particular, third parties would lack major states’ intelligence capabilities, though intelligence sharing may help. These tradeoffs might be eased through intermediate options, such as a national verification office that hires citizens of third-party countries to conduct interviews.
to:: Verifier—bilateral or third-party? Though this report’s focus is not on institution design, it is worth noting that Provers may more easily trust that a third-party Verifier will act in good faith, rather than seeking to steal information or compromise equipment. On the other hand, third-party Verifiers may take longer to set up and may not be as effective. In particular, third parties would lack major states’ intelligence capabilities, though intelligence sharing may help. These tradeoffs might be eased through intermediate options, such as a national verification office that hires citizens of third-party countries to conduct interviews.

#### Text
content::
\## Acting on a lead

A lead has arrived and been assessed. This section is about what the regime
does next, and about doing it proportionately, which is the part that decides
whether a verification regime survives its first ambiguous case.

\## Comparing against declarations

The first move is the cheapest: set the observed activity against what was
declared, and ask for clarification. Most anomalies die here, which is the
point. A regime that escalates every anomaly has no capacity left for the ones
that matter.

\## Escalating

When clarification does not resolve it, the ladder runs roughly:

- **Task additional collection:** look again, with a different stream.
- **Seek corroboration:** find an independent source that sees the same thing.
- **Trigger an audit or challenge inspection:** the treaty's own tools, which
  is where identification hands off to resolution.

Each rung costs more, politically and diplomatically, than the one below.

\## Recording what you did not resolve

The step that gets skipped. Whatever the chosen action, the record should carry:

- The **confidence** attached to the assessment;
- Any **dissent** among the analysts;
- The **unresolved blind spots**: what nobody could see, as distinct from what
  was looked at and found clean.

An assessment that hides its own uncertainty is worth less than one that states
it, because the next decision-maker cannot calibrate on it. This is the same
discipline as the evidence standards in the capstone.

As you red-line the treaty text, ask yourself: what does the Article II definition omit? Whose satellites count as "national", and is a commercial constellation under government tasking NTM or not? The word "cyber" appears inside the definition: is that legalized intelligence collection, or a license to hack that Beijing strikes out first? And what does "deliberate concealment" mean for AI: is behind-the-meter power generation, where a site makes its own electricity so its load never shows on the grid, camouflage, or ordinary industrial practice?

#### Question: Open
id:: b1cfa8da-fe64-4ad4-975b-1a6b08111099
force-feedback:: first
content::
\### Written output: Red-line the NTM article

Work from the treaty text quoted above: item 17 of Article II's definitions, plus Article X ¶1(b) and its clauses (i), (ii) and (iii). Mark at least three gaps or ambiguities, starting from the four questions above if you like, and redraft the one provision whose failure you judge most consequential. Then take up the question drafters have historically avoided: write the binding sharing clause the text declines to impose, since ¶1(b)(iii) encourages cooperation but obligates nothing, or defend its absence in three sentences. Test whatever you write against the rule that states sign what is symmetric, cheap, and checkable, and finish with one paragraph on why Washington would accept your article and one on why Beijing would.

**Reader:** The drafters of a US–China agreement, read in both capitals.

**Graded on:**

- Fidelity to what signatures can actually establish
- Precedent-consistent language
- Honesty about sharing
- Plausibility in both capitals
- Named blind spots, each with the sibling mechanism that covers it

(about 700 words)
assessment-instructions:: Score out of 100. 20 for each of the five criteria the task lists. (1) Fidelity to what signatures can establish: the gaps and the redraft do not overclaim what imagery, thermal, power, procurement or open-source evidence proves. (2) Precedent-consistent language: the redrafted provision reads like real treaty text (the ABM, INF, CTBT or New START noninterference and no-concealment clauses) rather than invented terms. (3) Honesty about sharing: either a binding sharing clause is drafted and its cost to sources and methods faced, or its absence is defended in about three sentences; building on Article X ¶1(b)(iii), which encourages but does not oblige cooperation, is on target. (4) Plausibility in both capitals: one paragraph each on why Washington and why Beijing would accept the article, tested against the rule that states sign what is symmetric, cheap and checkable. (5) Named blind spots, each paired with the other mechanism that covers it (for example hardware, cloud or human evidence). Give credit for each point whenever the answer shows the idea, in any wording. Deduct 20 if fewer than three gaps or ambiguities are marked, and 20 if no provision is redrafted. Model answer, for the feedback, not a grading checklist: "Gaps: (1) Item 17 lists means but not whose: a commercial constellation under government tasking is not clearly national, so bought imagery may fall outside the noninterference protection. (2) Cyber inside the definition reads in Beijing as a license to hack; strike it or limit it to passive collection. (3) Clause (ii) bans deliberate concealment without saying what that means for AI: behind-the-meter power, covered cooling plant and split sites can all be ordinary industrial practice. (4) Nothing links an NTM finding to the challenge-inspection procedure. Redraft of (ii): Each Party undertakes not to use concealment measures, including the shielding of power, cooling or thermal signatures of facilities housing covered chips, that impede verification by national technical means; arrangements in place before entry into force and declared under this Agreement are not concealment measures. Sharing: I would not add a binding sharing clause. No state will commit to hand over collection that exposes its sources and methods; the nuclear record shows sharing has always been voluntary and informal; and a duty both sides would quietly ignore weakens the treaty's credibility. Instead keep (iii) and allow a Party to cite NTM findings as grounds for a challenge inspection without disclosing their source. Test: noninterference and no-concealment are symmetric, cheap and checkable; a sharing duty is none of these. Washington accepts because its satellite and signals advantage gains treaty protection and it keeps control of what it shares. Beijing accepts because cyber collection is struck, commercial imagery is open to it too, and existing facilities are not treated as concealment. Blind spots: NTM cannot see what code runs inside a declared building (covered by hardware and cloud evidence) or training split across small sites (covered by chip accounting and whistleblower channels)."
feedback-instructions:: Go criterion by criterion: name the strongest of the five and the weakest, quoting the learner's own redraft. If they avoided the sharing clause without defending its absence, say so plainly. Ask one follow-up that tests the both-capitals paragraph they found harder. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Baker, Mauricio. "Nuclear Arms Control Verification and Lessons for AI Treaties." *arXiv*, Apr. 2023. [doi.org](https://doi.org/10.48550/arXiv.2304.04123)
*Its section 2.3.3, on intelligence sharing, is excerpted above.*

Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/abs/2507.15916)
*Cited above as Six Layers. Its passage on bilateral and third-party verifiers is excerpted above.*

Scher, Aaron, David Abecassis, Peter Barnett, et al. "An International Agreement to Prevent the Premature Creation of Artificial Superintelligence." *arXiv*, Nov. 2025. [arxiv.org](https://arxiv.org/abs/2511.10783)
*The MIRI draft agreement. Item 17 of Article II and Article X ¶1(b) are excerpted above, and the red-line task works from them.*

XLab. "2.3.4 Intelligence Institutions and Treaty Design." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/intelligence-institutions)
*The source lesson for the first part of this page, from the sharing and protection precedent to the readings.*

XLab. "2.3.5 From Intelligence Lead to Verification Action." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/intelligence-action)
*The source lesson for the second part, from acting on a lead to the red-line written output.*
:::{>>{"author":"Elias's AI","timestamp":1788521470158}@@XLab's lesson named a "Definition 17" and separate "noninterference" and "no-deliberate-concealment" articles; none of those labels exists in arXiv:2511.10783v3. Corrected here and in 2.3.4 to Article II — Definitions item 17 and Article X ¶1(b)(i) to (iii), which 2.3.4 now quotes in full.<<}
