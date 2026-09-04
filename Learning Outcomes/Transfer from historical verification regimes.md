---
id: 'c622ee21-b4c8-4a5c-be48-b32378abd01f'
learning-outcome: "Given a historical verification regime, reconstruct the chain from what it observes to the compliance judgement it licenses, name the assumption that makes that chain valid and where the regime fails to reach, and determine which parts of that logic transfer to AI treaty verification and which do not."
domain: "[[../Domains/Governance and Policy]]"
stage: intermediate
authors:
  - Elias+Claude
tags:
  - wip
---
## Test:
id:: 710788c5-e14b-4cf0-bd6e-a789e28557fd

#### Question: Open
id:: ba4b879d-bbb0-4221-9d94-918f84af3e3a
content:: The Comprehensive Nuclear-Test-Ban Treaty bans all nuclear explosions. Although the treaty has not entered into force, its monitoring organisation already operates a worldwide network of seismic, hydroacoustic, infrasound, and radionuclide stations, most of them outside the territory of any state being watched, and the network detected each of North Korea's nuclear tests. The treaty's on-site inspection provisions cannot be used until it enters into force, so for now the network is the whole regime.

This regime is not covered in the readings. In 300 to 450 words:

1. reconstruct its causal logic: what the stations observe, what compliance judgement that observation licenses, and the assumption about the prohibited act that makes the step from observation to judgement valid;
2. identify what this regime cannot reach, and why more stations would not fix it;
3. say which parts of the logic transfer to verifying a limit on frontier AI training and which do not, giving the reason for each.
max-chars:: 3500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not conclusions; an answer that argues the regime transfers better than the course suggests can score full marks if each step is reasoned.

**(a) Causal logic, 35 points.** Full credit: the stations observe physical signatures (ground motion, pressure waves in water and air, radioactive particles) that a nuclear explosion cannot avoid producing; because the prohibited act itself generates the signal, a detected event of the right character licenses the judgement that a test occurred regardless of what the state declares; the load-bearing assumption is that any explosion large enough to matter produces a signature above the network's detection threshold and distinguishable from earthquakes and industrial blasts. 20 if observation and judgement are described but the assumption is not made explicit. This regime does not rely on declarations; answers that import declaration-and-inspection logic from the safeguards readings without noticing the difference earn at most 15.

**(b) What it cannot reach, 25 points.** Full credit: explosions below the detection threshold or deliberately muffled, and confirmation of an ambiguous event without on-site access; more stations lower the threshold but cannot turn an ambiguous signal into an attribution, and cannot observe preparations, warhead design work, or experiments that produce no explosion. 10 for naming a gap without explaining why station count does not close it.

**(c) Transfer, 40 points.** 20 for the non-transferable part with its reason: a frontier training run does not emit an unavoidable signature detectable from outside the state; power draw and heat are ambiguous and shared with other industry, and the object of interest (the weights, the computation) is silent. 20 for at least one transferable principle with its reason, for example: passive monitoring that does not depend on the inspected state's cooperation is valuable wherever some external signal exists (power, chip procurement, satellite imagery of construction); corroboration across independent sensor types raises confidence; setting the treaty threshold at the level the sensors can detect rather than the level one wishes to prohibit. 10 if the learner asserts transfer or non-transfer without a reason grounded in the difference between the two prohibited acts.
feedback-instructions:: State whether the learner made the load-bearing assumption explicit. Name the best-reasoned transfer or non-transfer point and the one that was asserted without a reason. Ask one follow-up question. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Verification - v-precedents]]
notes:: Teaches the reconstruction move on IAEA safeguards, Shavit, and Iraq. The test uses a regime built on a different logic (signature detection, not declarations) on purpose.
