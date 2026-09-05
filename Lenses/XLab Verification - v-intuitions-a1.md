---
id: '7f66b58a-83fb-483b-a41c-7e5564e40df3'
title: "Option A: Stress-test Plan A's Verification Regime"
tldr: "Build a recommendation on Plan A from its strongest mechanism, weakest link, timeline, and covert-compute margin."
summary_for_tutor: "One optional essay route. Complete A1–A4 as preparatory responses, then A5 as the final essay in this same lens. Final essay is intended for peer review. Grade reasoning, not agreement with the source."
duration_minutes: 95
tags: [wip]
add_to_ai_context:
  - "[[../articles/2040-ai-2040-plan-a]]"
---
#### Text
content::
**Choose Option A or Option B.** If you choose this option, complete all five parts below.
The first four responses develop the arguments for your final essay; keep them in view as you write.

Use [[../Lenses/XLab Verification - v-intuitions-plan-a|the embedded Plan A reading]] throughout this exercise.

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
assessment-instructions:: There is no correct mechanism, so score the analysis and not the pick. Four things, 25 points each: (1) one specific mechanism from the datacenter retrofit is named, an optical network tap, reproducible workloads, a trusted recomputation server, a network restriction or a related safeguard, rather than the retrofit as a whole; (2) the evidence it produces is characterised on both dimensions the prompt gives, how strong the inference is (implied, likely, certain) and how exact it is (an ambiguous signature versus an exact artifact), together with the kinds of cheating it would catch; (3) a place a state with years to prepare would attack it is named, and a place such an adversary would be expected to fail; (4) the mechanism is placed in the regime, what it depends on and what depends on its reliability, closing with a stated level of confidence and a reason for it. Give no credit to a confident verdict with no mechanism under it. The prompt forbids outside resources here, so do not mark down an answer for citing none. No generic praise.
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
assessment-instructions:: Any part of Plan A is a defensible target; score the argument, not the choice. Four things, 25 points each: (1) one mechanism, assumption or implementation step is identified specifically enough that someone could attack it, not a whole phase of the plan; (2) what has to go right politically, technically and operationally for that part to work is spelled out, and the assumption called least reliable is tied to one of the pressures the prompt names, tight timelines, strategic competition, or uneven cooperation among states and firms; (3) the consequence for the regime is traced, either what compensates elsewhere when this part underperforms or where the failure cascades; (4) at least one concrete way to strengthen it is proposed. Penalise an answer that names a weakness and never says what its failure costs the regime. No generic praise.
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## A3. Stress-test the timeline

#### Question: Open
id:: 5e944a29-5989-48b0-bf4a-a4998a0eaa25
content:: Choose the timeline milestone that seems least likely to accomplish on schedule. Then, look closely at the implementation sequence in 2029: chip declarations and inspections, datacenter retrofits, and the expansion of verification coverage across the world's major compute.

In your rationale, you might compare the proposal with an arms-control inspection regime, a large industrial mobilization, an export-control system, or another suitable verification parallel. For inspiration, you may use outside resources or click ahead to learn more about historical verification precedents in [[../Lenses/XLab Verification - v-precedents|Module 0.3]].

Ask whether the precedent changes your estimate of what could realistically be built within Plan A's timeline. (150 to 200 words)
assessment-instructions:: Score three things. (1, worth 40) One named milestone is picked as least likely to land on schedule, drawn from the 2029 implementation sequence the prompt points at, chip declarations and inspections, datacenter retrofits, or the expansion of verification coverage across the world's major compute, and the reason given is about that milestone rather than about the plan's ambition in general. (2, worth 40) A concrete parallel is used, an arms-control inspection regime, a large industrial mobilisation, an export-control system or another verification precedent, together with the feature of it that carries the comparison, how long it took, how much access it required, or how many parties had to agree. (3, worth 20) The learner says whether the parallel moved their estimate, and in which direction. Penalise a bare assertion that a date is unrealistic with no precedent behind it. No generic praise.
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
assessment-instructions:: The answer must land on increased, decreased or kept the same, and the verdict itself is not scored. Three things. (1, worth 40) An argument about what a well-resourced state could actually do with a covert cluster of roughly that size over several years, stated as capability rather than as adjectives. (2, worth 30) The other side is engaged, either the disadvantages such a project would face or the other Plan A mechanisms that would constrain it. (3, worth 30) Algorithmic efficiency is addressed: whether gains could make hidden compute worth materially more than its raw share of world AI-relevant compute suggests. Do not require a number. Penalise answers that call the margin too high or too low without saying what the hidden capacity would be used for. No generic praise.
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
assessment-instructions:: This is option A's final essay. You are grading this essay on its own: you do not have the learner's four earlier answers, and you do not have the recommendation they selected in the choice question above, so judge only what this essay contains and never assume what they wrote elsewhere. Four things, 25 points each: (1) the essay states how robust the regime is and where it is most likely to fail, and connects the two rather than listing them; (2) the essay itself carries material on at least three of the four angles, the load-bearing strength, the weakest link, the timeline bottleneck, and the tolerable covert margin, developed here rather than gestured back to; (3) the strongest objection to the learner's own position is stated and answered, not merely acknowledged; (4) the essay names the recommendation it is defending, one of adopt largely as written, adopt only with significant amendments, or reject in favour of a different approach, and justifies it, and the justification matches the body of the essay. An essay that justifies a recommendation without naming which one loses this quarter, because the reader cannot tell which is being defended. Any of the three recommendations can earn full credit. Penalise an essay whose verdict does not follow from its own findings. No generic praise.
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
Keep your final essay for peer review, as specified in [XLab's assignment](https://aisafetytracks.com/tracks/verification/why-verification/building-intuitions).
The four shorter responses prepare your argument; the final essay is the output to share.

Continue to [[../Lenses/XLab Verification - v-intuitions-drills-1|the ungraded primer practice]], or explore [[../Lenses/XLab Verification - v-intuitions-success|optional exercises and further reading]].
