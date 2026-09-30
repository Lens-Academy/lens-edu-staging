---
id: '7f66b58a-83fb-483b-a41c-7e5564e40df3'
title: "Option A: Stress-test Plan A's Verification Regime"
tldr: "Build a recommendation on Plan A from its strongest mechanism, weakest link, timeline, and covert-compute margin."
summary_for_tutor: "One optional essay route. Complete A1–A4 as preparatory responses, then A5 as the final essay in this same lens. Final essay is intended for peer review. Grade reasoning, not agreement with the source."
duration_minutes: 95
tags: [wip]
add_to_ai_context:
  - "[[../articles/dean-ai-2040-verification-plan]]"
---
#### Text
content::
**Choose Option A or Option B.** If you choose this option, complete all five parts below.
The first four responses develop the arguments for your final essay; keep them in view as you write.

Use [[../Lenses/XLab Verification - v-intuitions-plan-a|the embedded verification supplement excerpts]] throughout this exercise.

#### Text
content::
Plan A's verification problem has two broad parts. First, the regime needs confidence that declared compute is being used in permitted ways. Second, it needs to keep undeclared or covert compute small enough that it cannot overturn the agreement. Your job, as a critical reader, is to interrogate whether Plan A's assumptions are reasonable; outlooks are optimistic, realistic, or pessimistic; the key load-bearing mechanisms of their proposal; any unrealistic aspects of the proposal that should be given less weight, if at all; and any important considerations you do not see.

\## A1. Identify the regime's strongest mechanism or recommendation

#### Question: Open
id:: 909a9ada-ee95-4dd2-9b6b-6ef51f617a3b
content:: Choose the part of this system that you think carries the most verification weight. Focus on the proposed datacenter retrofit: optical network taps, reproducible workloads, trusted recomputation servers, network restrictions, and related safeguards. Which mechanism seems like the most important, the one that, if removed, would most endanger the verification regime's effectiveness? Do not use outside resources for this part of the exercise.

Questions to consider:

- What types of evidence does it provide: implied, likely, or certain? Ambiguous (rough power signatures) or exact (the model weights themselves)?
- What kinds of cheating could it detect?
- If a state had years to prepare an evasion strategy, where would you expect it to attack the system? Where would you most expect a motivated adversary to fail?
- What other mechanisms does this one depend on, and what downstream mechanisms rely on this one's reliability?

There is no right answer here, and you do not need to find a secret or definitive vulnerability. Decide how much confidence this mechanism deserves and explain why. (200 to 250 words)
assessment-instructions:: Score out of 100. There is no correct mechanism; score the analysis, not the pick. 20: one specific mechanism of the datacenter retrofit is chosen (an optical network tap, reproducible workloads, a trusted recomputation server, a network restriction or a related safeguard), not the retrofit as a whole. 30: why it carries the most weight: what the regime would lose, or which cheating would go undetected, if it were removed. 35: the mechanism is assessed through at least two of the prompt's angles: the kind and strength of evidence it gives, the cheating it can detect, where a state with years to prepare would attack it or would fail, and what it depends on or what depends on it (20 for one angle). 15: a stated level of confidence in the mechanism, with the reason for it. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer gives a confident verdict without explaining how the mechanism works. Model answer, for the feedback, not a grading checklist: "The trusted recomputation server carries the most weight. The taps only copy traffic and the network restrictions only make large training harder; recomputing randomly sampled packets is what turns those copies into evidence. Its evidence is close to certain and exact: a packet either reproduces or it does not, so it can catch training or unapproved work disguised as inference, as long as the work passes through the taps. It depends on reproducible workloads, on taps that see all traffic, and on the server itself being trustworthy, and the regime's claim that the only outputs are verified inference rests on it. A state with years to prepare would attack the server's integrity, through its hardware and software supply chain, or route work around the taps through side channels; it would most likely fail at faking reproducible packets at scale, because random sampling catches even a small share of bad packets. I give it high confidence as a design and moderate confidence as built, because both sides have to trust the same servers."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## A2. Identify the regime's weakest link(s)

#### Question: Open
id:: 8c3cd334-f50c-40ec-bcea-3ee0d83db3a9
content:: Now that you have a good grasp on your ideas of the Verification Plan's strengths, let's turn to identifying its weak points. Identify at least one mechanism, assumption, or implementation step in Plan A that you think is especially vulnerable to failure. Explain why the weakness matters for the regime as a whole. This is arguably the most central prompt: only by red-teaming and finding vulnerabilities can a regime patch its holes.

Questions to consider:

- What has to go right politically, technically, and operationally for this part of the plan to work?
- Which assumptions seem least reliable under tight timelines, strategic competition, or uneven cooperation among states and firms?
- If this mechanism underperforms, what other parts of the verification regime compensate for it, and where might the failure cascade?

After you have a good idea of a weakness you want to critique, explain which weakness, why it's most jeopardizing, and some ideas (not too long) about how you would go about strengthening it. (200 to 250 words)
assessment-instructions:: Score out of 100. Any part of Plan A is a defensible target; score the argument, not the choice. 25: one mechanism, assumption or implementation step is identified specifically enough that someone could attack it, not a whole phase of the plan. 25: why it is vulnerable: what has to go right for it to work (politically, technically or operationally) and why that is unreliable, for example under tight timelines, strategic competition or uneven cooperation among states and firms. 25: why it matters for the regime as a whole: what would compensate if it underperformed, or where the failure would cascade. 25: at least one concrete way to strengthen it. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the answer names a weakness but never says what its failure costs the regime. Model answer, for the feedback, not a grading checklist: "The weakest link is the initial chip declaration and supply-chain audit in January 2029. Everything after it, the retrofit of about 99% of datacenter compute and the estimate that at most about 0.5% of world compute stays hidden, assumes the declaration found nearly all the chips. For it to work, both governments must open their records within weeks, the supply-chain records must be complete and unforged, and a few hundred inspectors must be able to check them. Under strategic competition each side has every reason to keep a hidden reserve, and records from resellers and third countries are uneven. If the declaration misses more than assumed, the retrofit verifies only the compute it was told about and the margin that justified the deal is wrong, so the failure cascades silently instead of showing up. To strengthen it: cross-check declarations against independent production records from the few fabs and memory makers, repeat the audit instead of treating it as one-off, and back it with intelligence and whistleblower channels aimed at undeclared clusters."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## A3. Stress-test the timeline

#### Question: Open
id:: 5e944a29-5989-48b0-bf4a-a4998a0eaa25
content:: Choose the timeline milestone that seems least likely to accomplish on schedule. Then, look closely at the implementation sequence in 2029: chip declarations and inspections, datacenter retrofits, and the expansion of verification coverage across the world's major compute.

In your rationale, you might compare the proposal with an arms-control inspection regime, a large industrial mobilization, an export-control system, or another suitable verification parallel. For inspiration, you may use outside resources or click ahead to learn more about historical verification precedents in [[../Lenses/XLab Verification - v-precedents|Module 0.3]].

Ask whether the precedent changes your estimate of what could realistically be built within Plan A's timeline. (150 to 200 words)
assessment-instructions:: Score out of 100. 40: one milestone of Plan A's timeline (for example the 2029 chip declarations and inspections, the datacenter retrofits, or the expansion of verification coverage across the world's major compute) is picked as least likely to land on schedule, with a reason about that milestone itself (what has to be built, installed or agreed, and how fast), not about the plan's ambition in general. 40: a concrete parallel is used, such as an arms-control inspection regime, a large industrial mobilisation, an export-control system or another verification precedent, 20 for naming it and 20 for the feature that carries the comparison, such as how long it took, how much access it needed or how many parties had to agree. 20: whether the parallel changes the learner's estimate of what could be built in time, and in which direction. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer calls a date unrealistic with no precedent or reason behind it. Model answer, for the feedback, not a grading checklist: "The datacenter retrofit is least likely to land on schedule. Plan A has the US and China converting about 99% of the world's AI datacenter compute into inference-only units within months of February 2029, installing taps and recomputation servers bought at about 10,000 a month into hundreds of thousands of racks, each step inspected by the other side. The closest parallel is the INF Treaty: its inspectors oversaw the elimination of about 2,700 missiles over three years, and that was destroying known objects, not installing new, untested equipment in commercial facilities. The precedent lowers my estimate: even with political will, installing and mutually certifying new hardware at this scale looks like years, not months, so the plan should expect a longer period in which the agreed power-off carries the load."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## A4. Assess the covert-compute margin

#### Question: Open
id:: e9e4eaa9-198a-4031-a923-eba27efa51ae
content:: The supplement estimates that some compute may remain hidden even after declarations and inspections, initially on the order of 0.5% of world AI-relevant compute. Your task is to decide how important that residual capacity is, and argue for whether the benign capacity threshold should be increased, decreased, or kept the same.

Questions to consider:

- What could a well-resourced state accomplish with a small covert cluster over several years?
- What disadvantages would such a project face?
- Which other mechanisms in Plan A might constrain it?
- Could algorithmic efficiency gaming realistically and substantively increase the capabilities of the hidden compute?

Increased, decreased, or left the same, justify your proposal for the covert-compute margin. (100 to 150 words)
assessment-instructions:: Score out of 100. Any of the three verdicts can earn full credit. 35: what a well-resourced state could actually do with hidden compute of roughly that size over several years, stated as capability (what it could train or run), not as adjectives. 35: the considerations that weigh on it, from at least two of: the disadvantages such a project would face, the Plan A mechanisms that would constrain it, and whether algorithmic efficiency gains could make the hidden compute worth much more than its raw share (20 for one). 30: a clear verdict, increase, decrease or keep the margin, that follows from the argument. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer calls the margin too high or too low without saying what the hidden capacity would be used for. Model answer, for the feedback, not a grading checklist: "Keep it, but treat it as a ceiling to drive down. About 0.5% of world AI compute is roughly 1.5M H100e, around 4% of a leading lab's R&D compute: over several years a state could train models a generation or so behind the frontier, or run a focused research effort, but it could not race past both sides' declared frontier. Such a project would be cut off from new chips, since new production is tracked, would have to hide its power, cooling and staff, and would risk whistleblowers and intelligence detection. Algorithmic efficiency is the real risk: gains made in secret could make the hidden compute worth several times its raw share, which is why the margin should not be raised, and should shrink as detection accumulates."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## A5. Final essay

Review your four responses above before writing your final essay.

You have now approached the AI 2040 Verification Supplement from four angles: its most load-bearing strength, its weakest link, its biggest timeline bottleneck, and the amount of failure the regime can tolerate.

Now imagine Plan A is moving from scenario to serious policy proposal. Decision-makers are asking whether its verification regime is strong enough to rely on as written, or whether it needs major changes before anyone should build an agreement around it. They have asked you for an assessment.

#### Question: Choice
id:: 2bedfce0-14ef-4703-b810-2b7bf107ebdf
content:: At the end, select one of the three recommendations, and briefly justify why:
options::
- Adopt the verification approach largely as written
- Adopt it only with significant amendments
- Reject it in favor of a different approach

#### Question: Open
id:: 9eb1875a-84ab-459d-b2bb-1585ee3b23aa
content:: Consider your strongest arguments and their strongest objections. Synthesize ideas from your earlier responses into a short essay answering: How robust is Plan A's verification regime, and where is it most likely to fail?

At the end, briefly justify the recommendation you selected above. (400 to 600 words)
assessment-instructions:: Score out of 100. Grade the essay on its own: the learner's four earlier answers and the recommendation they selected are not available, so judge only what the essay contains. 25: it states how robust the regime is and where it is most likely to fail, and connects the two rather than listing them. 25: it carries material from at least three of the four angles (the load-bearing strength, the weakest link, the timeline bottleneck, the tolerable covert-compute margin), developed in the essay rather than referred back to (10 for two). 25: the strongest objection to the learner's own position is stated and answered, not merely acknowledged. 25: the essay names the recommendation it defends (adopt largely as written, adopt only with significant amendments, or reject in favour of a different approach) and justifies it; a justification that never says which recommendation it defends earns at most 5. Any of the three recommendations can earn full credit. Give credit for each point whenever the essay shows the idea, in any wording. Cap at 50 if the recommendation does not follow from the essay's own findings. Model answer, for the feedback, not a grading checklist: "Plan A's regime is robust where it verifies known compute and fragile where it depends on knowing all compute. Its strongest mechanism, recomputing random samples of reproducible inference packets on trusted servers, gives near-certain evidence that declared datacenters run only approved inference, and it scales cheaply. But it only checks what it is pointed at. The weakest link is the January 2029 declaration: the retrofit, the 0.5% covert margin and the timeline all assume that declaration was nearly complete, and under strategic competition each side has reasons to keep a reserve. The timeline makes this worse: converting about 99% of datacenter compute within months is faster than any inspection precedent, so the interim rests on a power-off that is itself hard to check. The covert margin is tolerable at 0.5% only if secret algorithmic progress stays small, which nobody can verify. The strongest objection is that no regime needs perfection, only enough risk of detection to deter. I accept that, but deterrence needs the declaration to be checkable, and nothing in Plan A cross-checks it independently. So the regime is most likely to fail not inside the datacenter but before it, in what was never declared. Recommendation: adopt it only with significant amendments: repeated declarations cross-checked against fab and memory production records, intelligence and whistleblower channels; a staged retrofit with a verified power-off; and a covert margin that must shrink over time."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
Keep your final essay for peer review, as specified in [XLab's assignment](https://aisafetytracks.com/tracks/verification/why-verification/building-intuitions).
The four shorter responses prepare your argument; the final essay is the output to share.

Continue to [[../Lenses/XLab Verification - v-intuitions-drills-1|the ungraded primer practice]], or explore [[../Lenses/XLab Verification - v-intuitions-success|optional exercises and further reading]].
