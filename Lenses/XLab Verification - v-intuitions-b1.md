---
id: '83491b96-6c8a-4109-a14e-1b66b73eb028'
title: "Option B: Compare Plan A and Plan S"
tldr: "Compare the two plans' verification targets, evidence, monitoring burdens, and political cooperation, then defend a recommendation."
summary_for_tutor: "One optional essay route. Complete B1–B4 as preparatory responses, then B5 as the final essay in this same lens. Final essay is intended for peer review. Grade reasoning, not agreement with the source."
reading_minutes: 15
tutor_minutes: 62
tags: [wip]
add_to_ai_context:
  - "[[../articles/dean-ai-2040-verification-plan]]"
  - "[[../articles/ai-futures-project-plan-a-faq]]"
  - "[[../articles/larsen-ai-2040-plan-a]]"
---
#### Text
content::
**Choose Option A or Option B.** If you choose this option, complete all five parts below.
The first four responses develop the arguments for your final essay; keep them in view as you write.

#### Text
content::
Plan A and Plan S aim at different kinds of AI agreements. Plan A permits substantial AI activity under a layered verification regime; Plan S calls for a much stronger halt on frontier AI development. Those choices shape the verification problem: what counts as compliance, what evidence inspectors can collect, how much of the AI ecosystem must remain visible, and which actors must cooperate.

Read the Plan S discussion and FAQ, then compare the two plans using the questions below.
Plan S has no equivalent verification supplement, so infer what a credible regime would require using mechanisms from this course.

#### Article
source:: [[../articles/larsen-ai-2040-plan-a]]
from:: ## Plan S: Shutdown
to:: Separately, there is the issue of political feasibility. Plan A is more friendly to the AI companies and therefore less likely to be strongly opposed by them and their lobbyists, propaganda, etc. On the other hand, Plan S is simpler and avoids more risk in the near-term, which may make it easier to rally public support around and harder to botch.

#### Article
source:: [[../articles/ai-futures-project-plan-a-faq]]
from:: **Q: Plan A is complicated. Shouldn’t we do a simpler and more straightforward plan, like shutting it all down (Plan S)?**
to:: Our proposed implementation of Plan A is very complicated, and even a good implementation will incur significant existential risk. However, all simpler plans that we are aware of would incur even more risk than Plan A. In particular the main issue with Plan S is that it does worse than Plan A at making forward progress towards solving the safety/alignment problems that prevent further capability scaling, because we are shut down at an earlier capability level. This is bad because at some point, both Plan A and Plan S will break down and return to racing, and in Plan S, much less alignment progress will have been made by this point. That said, we are very sympathetic to Plan S and could imagine being convinced that some version of it is better after all.


#### Text
content::
\## B1. Which plan gives verification the more tractable target?

#### Question: Open
id:: a927dcac-36c7-4330-b064-b64f7b867746
content:: Identify the central restriction under Plan A and Plan S: what would inspectors actually need to establish before they could reasonably conclude that actors were complying? Then, compare: does Plan A or Plan S give verification the clearer and more tractable target?

Questions to consider:

- What prohibited activity would inspectors need to identify under each plan?
- What observable physical, computational, or organizational traces would that activity leave?
- Could prohibited activity resemble or hide within activity that remains permitted?
- Where might reasonable inspectors disagree about whether a violation has occurred?

Make a preliminary judgment. Delineate your evidence-backed reasons from intuitions. (100 to 150 words)
assessment-instructions:: Score out of 100. 60: for each plan, 30 each, its central restriction and what inspectors would have to establish before concluding that actors comply: Plan A lets substantial AI activity continue under agreed limits and a layered verification regime (a verified slowdown), so inspectors must show that declared compute runs only permitted work and that undeclared compute is too small to matter; Plan S halts frontier AI development (no large training runs and no AI research, while existing models keep running), so inspectors must show that no one is training at scale or doing AI research. 25: a preliminary judgment on which plan gives verification the clearer and more tractable target, with reasons, for example what traces the prohibited activity would leave, whether it could hide inside permitted activity, or where reasonable inspectors could disagree about a violation. 15: evidence-backed reasons are kept apart from intuitions. Either plan earns full points when the reasoning supports it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Plan A permits AI activity under limits: almost all compute is restricted to inference, and training and R&D happen only in declared, verified clusters within agreed caps. Inspectors must establish that declared chips run only permitted workloads and that any undeclared compute is too small to matter. Plan S bans large training runs and AI research while inference continues, so inspectors must establish that no cluster anywhere is training at scale and that nobody is doing algorithmic research. Evidence: a large training run leaves physical traces (chips, power, cooling, network traffic), and both plans depend on telling training from inference. Intuition: research needs little compute and hides easily, and permitted activity can mask prohibited training. Preliminary judgment: Plan S gives the clearer target, since any large run is a violation, though its research ban is hard to verify; Plan A's line between permitted and prohibited training is finer and more open to dispute."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## B2. Which plan could provide stronger evidence of compliance?

#### Question: Open
id:: 79d7f63c-67b0-4a54-aeb6-127a58ddbc4a
content:: A clear rule is useful only if the available verification mechanisms can produce convincing evidence that actors are following it.

For Plan A, use the Verification Supplement to identify the mechanisms that provide the strongest evidence of compliance. For Plan S, consider what combination of tools from this course could provide comparable assurance, for example compute declarations, inspections, chip accounting, power monitoring, remote sensing, intelligence, or personnel reporting.

Compare the quality of evidence each regime could realistically produce.

Questions to consider:

- Which compliance claims can be observed relatively directly, and which require substantial inference?
- Would several independent verification mechanisms corroborate the same conclusion?
- Where could multiple mechanisms share the same blind spot or unreliable assumption?
- How much residual uncertainty would policymakers have to tolerate even when the regime appears to be working?

Decide which plan could give decision-makers stronger grounds for confidence in compliance. (150 to 200 words)
assessment-instructions:: Score out of 100. 25: for Plan A, named mechanisms from its Verification Supplement that give the strongest evidence, such as the mutual chip declaration with inspections, chip tracking, the inference-only retrofit of datacenters, and verification of R&D compute by sampling workloads, rather than generic verification talk. 25: for Plan S, which has no supplement, a combination of tools from the course that could give comparable assurance, such as compute declarations, inspections, chip accounting, power monitoring, remote sensing, intelligence or personnel reporting. 30: a comparison of the quality of evidence each regime could produce, with reasons, for example which compliance claims can be observed fairly directly and which need inference, whether the mechanisms would corroborate each other independently or share a blind spot or unreliable assumption, and how much uncertainty would remain even when the regime seems to work. 20: a decision on which plan gives decision-makers stronger grounds for confidence, following from the comparison. Either plan earns full points when the reasoning supports it. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 70 if the comparison only counts mechanisms, without asking whether their failure modes are independent. Model answer, for the feedback, not a grading checklist: "Plan A's strongest evidence comes from the mutual chip declaration backed by inspections and years of chip tracking, and from the inference-only retrofit, which lets inspectors confirm that about 99% of world AI compute runs only inference; R&D clusters are checked by sampling their workloads. These claims are observed fairly directly on known compute. Plan S would use the same declaration and chip accounting, inspections to confirm that chips run only inference, and power monitoring, satellite imagery, intelligence and whistleblower reports to hunt for undeclared clusters and banned research. Both share one blind spot, compute that was never declared, which only intelligence and remote sensing can find, and they give leads, not proof; Plan A's own estimate is that about 0.5% of world compute could stay dark. Plan S's ban on algorithmic research leaves almost no physical trace, so compliance there rests on inference and personnel reporting. Judgment: Plan A gives stronger grounds, because most of its evidence comes from direct, independent checks on declared compute, while Plan S's key research claim cannot be observed directly."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## B3. Which plan creates the harder monitoring problem?

#### Question: Open
id:: 3edc12a8-2c49-46c7-8029-54e1de5ff7ac
content:: Now, zoom out from individual pieces of evidence to the scale of the regime. Compare how much compute, infrastructure, activity, and geography would need to remain visible to inspectors under Plan A vs. Plan S. Pay particular attention to what kinds of AI activity remain permitted under each agreement and what that means for the monitoring burden.

Questions to consider:

- Under which plan must inspectors make finer distinctions between permitted and prohibited activity?
- How much of the relevant compute ecosystem would need reliable verification coverage?
- Where could important activity fall outside the regime's field of view?
- Does a broader prohibition make monitoring easier, or make gaps in coverage more consequential?

Revisit your answer from Part 1. A rule that initially looked simpler may create a demanding monitoring problem once you consider how it would work across the real AI ecosystem. (150 to 200 words)
assessment-instructions:: Score out of 100. 40: how much compute, infrastructure, activity and geography would have to stay visible to inspectors under each plan, 20 each. 30: how what each plan still permits shapes that burden, for example under which plan inspectors must draw finer distinctions between permitted and prohibited activity, how much of the compute ecosystem needs reliable coverage, where important activity could fall outside the regime's view, or whether a broader prohibition makes monitoring easier or makes gaps in coverage more consequential. 30: the answer revisits the part 1 judgment and says whether the scale of monitoring changes it, and why. Either plan earns full points when the reasoning supports it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Both plans need almost all AI compute in view. Plan A retrofits about 99% of world AI compute for inference-only verification and must also watch the R&D clusters where training is still allowed; Plan S must confirm that nearly all chips run no large training and that nobody does AI research. Plan A's burden is finer: inspectors must tell permitted, capped training from prohibited scaling inside the same clusters, and small clusters and legacy chips outside the retrofit are where activity could hide. Plan S's distinction is coarser, since any large run is a violation, but research on small compute falls outside every sensor, and because nothing is permitted, one missed cluster is a direct breach. Revisiting part 1: Plan S's target still looks clearer, but its monitoring burden is not smaller, since coverage must be just as broad and the research ban needs human and intelligence sources, so I now rate the two plans closer than before."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
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

By this point, you should have compared the regimes across four dimensions: clarity of the verification target, strength of the evidence, monitoring burden, and political cooperation. (200 to 250 words)
assessment-instructions:: Score out of 100. 40: the hardest cooperation problem for each plan, 20 each, specific enough to show who would resist and why (for example the actors with the strongest incentive to refuse, demand exemptions or withdraw later, the commercially or militarily sensitive access verification needs, or the economic, strategic or sovereignty cost of taking part), and not the same general complaint stated for both. 30: a comparison of how hard each problem would be to overcome, with reasons. 30: how much each regime depends on solving its problem, and what that means for the overall assessment, for example how much a plan that is easier to verify but politically harder should lose for it. Either plan earns full points when the reasoning supports it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Plan A's hardest problem is the frontier AI companies and the security establishments: verifying R&D puts inspectors inside frontier labs, next to workloads and code that are commercially and militarily sensitive, and each side will ask for exemptions for classified work. Companies lose less under Plan A than under Plan S, so this is serious but negotiable, and the regime depends on it completely, because Plan A's permitted training is only safe if the R&D clusters are verified. Plan S's hardest problem is getting every major power and third country to accept a freeze: the leading state gives up its lead, AI companies lose much of their value and lobby against it, and any state that thinks it could win has a strong incentive to stay out or leave later. Plan S depends on this just as fully, since one capable holdout breaks the halt. Plan S is simpler to verify but politically harder; I weigh the political problem heavily, because a regime that is never signed, or is abandoned, verifies nothing, so on this dimension Plan A comes out ahead."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## B5. Final essay

Review your four responses above before writing your final essay.

Policymakers are deciding whether a serious international AI agreement should more closely resemble Plan A or Plan S. They have asked which approach provides a verification regime strong enough to rely on.

#### Question: Choice
id:: f519fd45-b860-4b6e-88b9-1231bf723d2c
content:: Which creates the more robust verification regime: Plan A or Plan S? Make a recommendation:
options::
- Plan A: verified slowdown
- Plan S: complete shutdown

#### Question: Open
id:: dd10bf8f-8e94-4854-8f7a-48c317665d7b
content:: You have already analyzed the comparison from four angles. Pull together the findings that matter most, consider the strongest argument against your own position, and answer: Which creates the more robust verification regime: Plan A or Plan S?

Make a recommendation. Explain which considerations carry the most weight in your judgment, where important uncertainty remains, and what evidence or development would be most likely to change your view. (400 to 500 words)
assessment-instructions:: Score out of 100. 25: a clear recommendation, Plan A or Plan S, defended consistently through the essay. 25: the findings that matter most are drawn together from the earlier comparisons (clarity of the verification target, strength of the evidence, monitoring burden, political cooperation), and the essay says which considerations carry the most weight and why; 10 of these 25 if it lists the considerations without ranking them. 25: the strongest argument against the learner's own position, stated fairly and answered. 25: where important uncertainty remains, 10, and what evidence or development would be most likely to change the learner's view, 15. Either plan earns full points when the reasoning supports it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Plan A creates the more robust verification regime. Plan S has the clearer rule: any large training run and any AI research is a violation. But a rule is only as good as the evidence that it is kept. Under Plan S the hardest prohibited activity to see, algorithmic research, leaves almost no physical trace, so compliance rests on intelligence and whistleblowers, and a state that falls behind has every reason to leave. Under Plan A most compute is verified inference-only by the same declarations, chip tracking and inspections Plan S would need, and training continues only in declared R&D clusters that inspectors check directly. Its line between permitted and prohibited training is finer, but it is drawn on compute inspectors can see. What carries most weight for me is political cooperation, then the strength of evidence: a regime that the major powers and the AI companies will join and stay in, with evidence from independent layers, beats a simpler rule that one holdout can break. The strongest objection is that Plan A's permitted training gives a cheater cover: prohibited scaling can hide inside allowed R&D, and one missed cluster matters more while capabilities keep growing. My answer is that the R&D clusters are few, new and built for verification, which makes them the best-watched compute in the world, while dark compute, estimated at about 0.5% of the total, is too small for a decisive lead. Uncertainty remains about whether workload verification can tell permitted from prohibited training at scale. A demonstration that it cannot, or evidence that dark compute is far larger than estimated, would move me towards Plan S."
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
Keep your final essay for peer review, as specified in [XLab's assignment](https://aisafetytracks.com/tracks/verification/why-verification/building-intuitions).
The four shorter responses prepare your argument; the final essay is the output to share.

Continue to [[../Lenses/XLab Verification - v-intuitions-drills-1|the ungraded primer practice]], or explore [[../Lenses/XLab Verification - v-intuitions-success|optional exercises and further reading]].
