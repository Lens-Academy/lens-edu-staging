---
id: '7a5bcc21-1cea-45f1-95d1-46c7896c94ec'
title: "0.2 Building Verification Intuitions"
tldr: "Faithful alpha import of XLab lesson 0.2 Building Verification Intuitions."
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed on XLab."
tags: [wip]
---
#### Text
content::
\## 0.2: Building Verification Intuitions

Now that we've established the foundational motivations for why verification is important, we'll dive into building key intuitions around the timelines, scope, and urgency of what a verification regime might actually look like. We'll do this by analyzing AI 2040: Plan A, the most detailed and well-known public attempt to forecast a successful AI slowdown and complement verification regime.

\## AI 2040: Plan A?

What is the ideal end state? What agreement reaches it? What would verification have to cover for the agreement to hold? The most detailed public attempt to answer all three is AI 2040: Plan A, published by the AI Futures Project, the team behind the earlier AI 2027 scenario. While AI 2027 dramatized how a race ends badly, Plan A tells a dated, concrete story in which a US–China deal, layered verification, and a managed slowdown deliver a good outcome by 2040. Its [verification supplement](https://ai-2040.com/supplements/verification-plan) specifies the machinery: mutual compute declarations checked by inspections, datacenters retrofitted so that large-scale training is detectable, optical network taps feeding trusted recomputation servers, secure R&D facilities, and production caps on unverified hardware.

\### [AI 2040: Plan A — verification supplement](https://ai-2040.com/supplements/verification-plan)
AI Futures Project

  The machinery behind Plan A, specified in full.

Below, you will read and gauge the feasibility and robustness of Plan A yourself. Read with a critical but thoughtful eye. For every date, percentage, and recommendation, ask yourself: what assumptions have to be true in order for this to hold? What existing or historical precedents have pointed to this mechanism succeeding or failing? What alternative solutions or estimates could there be, and how does this hold up against them? What is left uncertain? Remember: there is no correct answer, but you want to back your opinions with logic and evidence.

Your task is to write one of two open-ended essay prompts, consisting of shorter, prompted questions linking into a more cohesive essay at the end:

A: stress-test the Plan A verification supplement, or

B: compare Plan A (verified slowdown) and Plan S (complete shutdown).

\## A writing good practice

Clarify the source of each claim you make, and explicitly identify gaps, uncertainties, or ambiguities as they appear. You won't know everything, and you aren't expected to.

\## Option A: Stress-test Plan A

\## Option A: Stress-test Plan A's Verification Regime

Read the [AI 2040 Verification Plan](https://ai-2040.com/supplements/verification-plan), paying attention to:

- Summary of the Plan
- Concrete inference-only retrofitting proposal
- 2029–2030: Deal Implementation
- Third-party countries begin joining the deal

Plan A's verification problem has two broad parts. First, the regime needs confidence that declared compute is being used in permitted ways. Second, it needs to keep undeclared or covert compute small enough that it cannot overturn the agreement. Your job, as a critical reader, is to interrogate whether Plan A's assumptions are reasonable; outlooks are optimistic, realistic, or pessimistic; the key load-bearing mechanisms of their proposal; any unrealistic aspects of the proposal that should be given less weight, if at all; and any important considerations you do not see.

\## A1. Identify the regime's strongest mechanism or recommendation

#### Question: Open
id:: 909a9ada-ee95-4dd2-9b6b-6ef51f617a3b
content:: Choose the part of this system that you think carries the most verification weight. Focus on the proposed datacenter retrofit: optical network taps, reproducible workloads, trusted recomputation servers, network restrictions, and related safeguards. Which mechanism seems like the most important—that, if removed, would most endanger the verification regime's effectiveness? Do not use outside resources for this part of the exercise.

Questions to consider:

- What types of evidence does it provide—implied, likely, or certain? Ambiguous (rough power signatures) or exact (the model weights themselves)?
- What kinds of cheating could it detect?
- If a state had years to prepare an evasion strategy, where would you expect it to attack the system? Where would you most expect a motivated adversary to fail?
- What other mechanisms does this one depend on, and what downstream mechanisms rely on this one's reliability?

There is no right answer here, and you do not need to find a secret or definitive vulnerability. Decide how much confidence this mechanism deserves and explain why.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## A2. Identify the weakest link

\## A2. Identify the regime's weakest link(s)

#### Question: Open
id:: 8c3cd334-f50c-40ec-bcea-3ee0d83db3a9
content:: Now that you have a good grasp on your ideas of the Verification Plan's strengths, let's turn to identifying its weak points. Identify at least one mechanism, assumption, or implementation step in Plan A that you think is especially vulnerable to failure. Explain why the weakness matters for the regime as a whole. This is arguably the most central prompt: only by red-teaming and finding vulnerabilities can a regime patch its holes.

Questions to consider:

- What has to go right politically, technically, and operationally for this part of the plan to work?
- Which assumptions seem least reliable under tight timelines, strategic competition, or uneven cooperation among states and firms?
- If this mechanism underperforms, what other parts of the verification regime compensate for it—and where might the failure cascade?

After you have a good idea of a weakness you want to critique, explain which weakness, why it's most jeopardizing, and some ideas (not too long) about how you would go about strengthening it.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## A3. Stress-test the timeline

\## A3. Stress-test the timeline

#### Question: Open
id:: 5e944a29-5989-48b0-bf4a-a4998a0eaa25
content:: Choose the timeline milestone that seems least likely to accomplish on schedule. Then, look closely at the implementation sequence in 2029: chip declarations and inspections, datacenter retrofits, and the expansion of verification coverage across the world's major compute.

In your rationale, you might compare the proposal with an arms-control inspection regime, a large industrial mobilization, an export-control system, or another suitable verification parallel. For inspiration, you may use outside resources or click ahead to learn more about historical verification precedents in [[../Lenses/XLab Verification - v-precedents|Module 0.3]].

Ask whether the precedent changes your estimate of what could realistically be built within Plan A's timeline.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## A4. Assess the covert-compute margin

\## A4. Assess the covert-compute margin

#### Question: Open
id:: e9e4eaa9-198a-4031-a923-eba27efa51ae
content:: The supplement estimates that some compute may remain hidden even after declarations and inspections, initially on the order of 0.5% of world AI-relevant compute. Your task is to decide how important that residual capacity is, and argue for whether the benign capacity threshold should be increased, decreased, or kept the same.

Questions to consider:

- What could a well-resourced state accomplish with a small covert cluster over several years?
- What disadvantages would such a project face?
- Which other mechanisms in Plan A might constrain it?
- Could algorithmic efficiency gaming realistically and substantively increase the capabilities of the hidden compute?

Increased, decreased, or left the same, justify your proposal for the covert-compute margin.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## A5. Final essay

\## A5. Final essay

You have now approached the AI 2040 Verification Supplement from four angles: its most load-bearing strength, its weakest link, its biggest timeline bottleneck, and the amount of failure the regime can tolerate.

Now imagine Plan A is moving from scenario to serious policy proposal. Decision-makers are asking whether its verification regime is strong enough to rely on as written, or whether it needs major changes before anyone should build an agreement around it. They have asked you for an assessment.

#### Question: Choice
id:: 2bedfce0-14ef-4703-b810-2b7bf107ebdf
content:: Your recommendation on Plan A's verification regime:
options::
- Adopt the verification approach largely as written
- Adopt it only with significant amendments
- Reject it in favor of a different approach

#### Question: Open
id:: 9eb1875a-84ab-459d-b2bb-1585ee3b23aa
content:: Consider your strongest arguments and their strongest objections. Synthesize ideas from your earlier responses into a short essay answering: How robust is Plan A's verification regime, and where is it most likely to fail?

At the end, briefly justify the recommendation you selected above.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## Option B: Compare Plan A and Plan S

\## Option B: Compare Plan A and Plan S as Verification Problems

Plan A and Plan S aim at different kinds of AI agreements. Plan A permits substantial AI activity under a layered verification regime; Plan S calls for a much stronger halt on frontier AI development. Those choices shape the verification problem: what counts as compliance, what evidence inspectors can collect, how much of the AI ecosystem must remain visible, and which actors must cooperate.

Skim the [AI 2040 Verification Supplement](https://ai-2040.com/supplements/verification-plan), the discussion of Plan S, and the relevant Plan S section of the [AI 2040 FAQ](https://ai-2040.com/supplements/faq). Plan S has no equivalent verification supplement, so you will need to infer what a credible verification regime for it would require using mechanisms from this course.

\## B1. Which plan gives verification the more tractable target?

#### Question: Open
id:: a927dcac-36c7-4330-b064-b64f7b867746
content:: Identify the central restriction under Plan A and Plan S: what would inspectors actually need to establish before they could reasonably conclude that actors were complying? Then, compare: does Plan A or Plan S give verification the clearer and more tractable target?

Questions to consider:

- What prohibited activity would inspectors need to identify under each plan?
- What observable physical, computational, or organizational traces would that activity leave?
- Could prohibited activity resemble or hide within activity that remains permitted?
- Where might reasonable inspectors disagree about whether a violation has occurred?

Make a preliminary judgment. Delineate your evidence-backed reasons from intuitions.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## B2. Compare the evidence

\## B2. Which plan could provide stronger evidence of compliance?

#### Question: Open
id:: 79d7f63c-67b0-4a54-aeb6-127a58ddbc4a
content:: A clear rule is useful only if the available verification mechanisms can produce convincing evidence that actors are following it.

For Plan A, use the Verification Supplement to identify the mechanisms that provide the strongest evidence of compliance. For Plan S, consider what combination of tools from this course could provide comparable assurance—for example, compute declarations, inspections, chip accounting, power monitoring, remote sensing, intelligence, or personnel reporting.

Compare the quality of evidence each regime could realistically produce.

Questions to consider:

- Which compliance claims can be observed relatively directly, and which require substantial inference?
- Would several independent verification mechanisms corroborate the same conclusion?
- Where could multiple mechanisms share the same blind spot or unreliable assumption?
- How much residual uncertainty would policymakers have to tolerate even when the regime appears to be working?

Decide which plan could give decision-makers stronger grounds for confidence in compliance.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## B3. Compare the monitoring problem

\## B3. Which plan creates the harder monitoring problem?

#### Question: Open
id:: 3edc12a8-2c49-46c7-8029-54e1de5ff7ac
content:: Now, zoom out from individual pieces of evidence to the scale of the regime. Compare how much compute, infrastructure, activity, and geography would need to remain visible to inspectors under Plan A vs. Plan S. Pay particular attention to what kinds of AI activity remain permitted under each agreement and what that means for the monitoring burden.

Questions to consider:

- Under which plan must inspectors make finer distinctions between permitted and prohibited activity?
- How much of the relevant compute ecosystem would need reliable verification coverage?
- Where could important activity fall outside the regime's field of view?
- Does a broader prohibition make monitoring easier, or make gaps in coverage more consequential?

Revisit your answer from Part 1. A rule that initially looked simpler may create a demanding monitoring problem once you consider how it would work across the real AI ecosystem.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## B4. Compare political cooperation

\## B4. Which regime could states actually cooperate on?

#### Question: Open
id:: 3d07b047-a892-40b9-960c-48de66645bea
content:: Verification also depends on whether governments, firms, and third countries will accept the access, restrictions, and institutional arrangements necessary to produce credible evidence.

Identify the hardest cooperation problem facing Plan A and the hardest facing Plan S. Compare how difficult each would be to overcome and how much the regime depends on solving it.

Questions to consider:

- Which actors have the strongest incentives to refuse participation, demand exemptions, or withdraw later?
- What commercially or militarily sensitive access would verification require?
- What economic, strategic, or sovereignty costs would participation impose?
- If one plan appears technically easier to verify but politically harder to implement, how much should that affect your assessment?

By this point, you should have compared the regimes across four dimensions: clarity of the verification target, strength of the evidence, monitoring burden, and political cooperation.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## B5. Final essay

\## B5. Final essay

Policymakers are deciding whether a serious international AI agreement should more closely resemble Plan A or Plan S. They have asked which approach provides a verification regime strong enough to rely on.

#### Question: Choice
id:: f519fd45-b860-4b6e-88b9-1231bf723d2c
content:: Which plan would you recommend?
options::
- Plan A: verified slowdown
- Plan S: complete shutdown

#### Question: Open
id:: dd10bf8f-8e94-4854-8f7a-48c317665d7b
content:: You have already analyzed the comparison from four angles. Pull together the findings that matter most, consider the strongest argument against your own position, and answer: Which creates the more robust verification regime: Plan A or Plan S?

Make a recommendation. Explain which considerations carry the most weight in your judgment, where important uncertainty remains, and what evidence or development would be most likely to change your view.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## [Optional] Exercises and further reading

\## [Optional] Additional Exercises & Materials

#### Question
content:: [Optional] Task — Essay: what does success look like to you?

Describe your own plausible success scenario for advanced AI governance. Think several steps beyond any single verification mechanism: what does a world that has successfully managed the relevant risks actually look like, and what agreement or institutional arrangement gets us there?

Questions to consider:

- What would make you call the outcome a success, and which risks or tradeoffs would remain acceptable?
- What agreement or institutional settlement sustains that outcome, and which actors must participate for it to hold?
- What technological and geopolitical assumptions does your scenario depend on most heavily?
- What must verification establish with high confidence, and where can the regime tolerate residual uncertainty?
- Which actors, jurisdictions, or incentives pose the hardest coordination problem?
- What has to become technically, politically, or institutionally possible before this settlement can emerge?
- Where is your scenario most fragile, and what development would most likely force you to redesign it?

Keep this essay. You will return to it at the end of the track and see what, if anything, you would now change.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.
optional:: true

#### Question
content:: [Optional] Explore AI 2027

Read [AI 2027](https://ai-2027.com/), the same team’s earlier scenario, including both of its endings. As you read, ask the question this section trained: at which branch points would verification infrastructure have changed what the actors could credibly agree to?
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.
optional:: true

#### Text
content::
\### [AI 2027](https://ai-2027.com)
AI Futures Project (2025)

  The earlier scenario from the same team — how a race ends badly, dramatized. Read both of its endings.

\## Curated readings

\## Curated Readings

You have now taken a position on a concrete verification regime. Use these readings to push on whichever part of your argument still feels least settled. Skim broadly; deep-read the one or two closest to the question you found hardest.

\### [Nuclear Arms Control Verification and Lessons for AI Treaties](https://arxiv.org/abs/2304.04123)
Baker (2023)

  If you want the historical reality check. Read for how adversarial states
  built confidence without eliminating uncertainty, and where the nuclear
  analogy becomes strained when applied to AI.

\### [Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment](https://arxiv.org/abs/2507.15916)
Baker et al. (2025)

  If your Plan A assessment hinged on whether layered verification can
  actually produce enough assurance. Read for redundancy, correlated failure,
  privacy, and what still has to be built before a multilayer system deserves
  high confidence.

\### [Verifying Restrictions on Frontier AI Research](https://arxiv.org/abs/2606.28694)
Scher (2026)

  If you chose Plan S — or remain unsure whether a stronger halt is actually
  easier to verify. Read for the uncomfortable parts of a halt that compute
  monitoring alone does not solve: algorithmic research, experiments,
  personnel, code, and other less physically legible activity.

\### [Verification for International AI Governance](https://aigi.ox.ac.uk/wp-content/uploads/2025/07/Verification_for_International_AI_Governance.pdf)
Oxford Martin AI Governance Initiative (2025)

  If your argument turned on political feasibility or inspection access. Read
  for how the feasible verification architecture changes with political
  access, privacy constraints, and the type of agreement states are trying to
  verify.

\### [An International Agreement to Prevent the Premature Creation of Artificial Superintelligence](https://arxiv.org/abs/2511.10783)
Scher et al. (2025)

  If you want to compare your own architecture against a concrete proposal
  for an international halt — especially its verification sections and
  Appendix D. Read for one attempt to translate a pause posture into specific
  restrictions on compute and dangerous AI research.

\### [Mechanisms to Verify International Agreements About AI Development](https://arxiv.org/abs/2506.15867)
Scher and Thiergart, MIRI Technical Governance Team (2025)

  If you want the mechanism catalog. Read selectively: choose the policy goal
  or mechanism closest to your essay and ask whether its evidence, access
  requirements, and remaining R&D gaps change your conclusion.

\## Drill bench

\## Drill bench

The primer bench: inspection games, credible commitment, and two-level games. One step at a time: commit, read why, then Continue.

#### Text
content:: **Interactive exercise:** XLab's `drills-primers` widget has no direct Lens equivalent yet. Complete it in the [original XLab lesson](https://aisafetytracks.com/tracks/verification/why-verification/building-intuitions). Its surrounding lesson text is preserved here.

#### Text
content:: **Import gap:** XLab persistent memo desk has no clean Lens equivalent. Use the [original XLab lesson](https://aisafetytracks.com/tracks/verification/why-verification/building-intuitions) for this element.

#### Text
content::
*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/why-verification/building-intuitions)*
