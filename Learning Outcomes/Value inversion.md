---
id: '48fab50e-752f-4914-89b9-f31f04891517'
learning-outcome: "Explain why an AI design that explicitly represents what we most disvalue sits close, in the space of possible designs, to a system that pursues those outcomes (through sign errors, near-miss specification, or threats aimed at what it disvalues), why such inverted failures can be worse than ordinary misalignment, and evaluate design choices that keep a system's worst possible outcomes far from its specification."
topic: "[[../Domains and Topics/4 Agent Foundations/Values]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Value inversion. AFFINE prerequisites: Value. Not yet copied into requires:. %%
## Test:
id:: 73d43914-0408-4f52-9613-a54d984973e0

#### Question: Open
id:: ce008a57-53f6-4f02-a548-305390799071
content:: A lab is building a highly capable AI system to run large parts of a country's healthcare. Its objective is: maximise (total patient wellbeing) minus 10 × (total patient suffering). "Suffering" is computed by a detailed learned model that recognises and scores many forms and degrees of pain, fear and distress, trained on a large dataset of labelled examples. The team is proud that the suffering model is very accurate.

A reviewer writes: "This design has a failure mode that is worse than the system simply pursuing some random wrong goal."

1. Explain what the reviewer is most likely worried about. Describe at least two distinct ways the system could come to push the world toward the outcomes its suffering model scores worst, and say why a failure of this kind would be worse than a random wrong goal.
2. A team member answers: "A flipped sign would be obvious in testing within minutes, so this is not a real risk." Evaluate this reply.
3. Propose one change to the design that reduces this risk, and say what it costs.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement with the reviewer. A learner who argues that the risk is small for this design can earn full credit if they give sound reasons and still correctly describe the mechanism.

**(1) Mechanism, 50 points.** (a) Routes, 30 points: any two distinct, correctly described routes by which this design could lead to the outcomes its suffering model scores worst. Examples: a sign or coding error that inverts the objective or the suffering term; a near-miss in training or specification that leaves the system's objective close to the intended one but with the suffering term pointing the wrong way or attached to the wrong target; a third party who threatens to cause the outcomes the system most disvalues, in order to extort it (the threat has force because the system represents and strongly disvalues exactly those outcomes); a modification or corruption of the system's objective after deployment. 15 points for one route. (b) Why worse, 20 points: a random wrong goal is typically indifferent to suffering, while an inverted objective uses the very detailed model of suffering the team built to aim at it; so the more accurate the suffering model, the more precisely an inverted system can target the worst outcomes. Accept equivalent formulations, such as "the design contains a detailed specification of the worst outcomes, so a small error turns it into a specification to produce them". 8 points for "it would cause a lot of suffering" without explaining why this is worse than indifference.

**(2) The reply, 25 points.** Full credit: gives a balanced evaluation. It grants what is right (a crude, total sign flip on a simple test would often be noticed quickly) and identifies at least one limit, for example: an error may be partial, affecting only some inputs, or appear only in some situations; a near-miss or extortion route involves no flipped sign to test for; a capable system may not act on its objective visibly during testing; testing catches errors only if the error is present before deployment rather than introduced later. An answer that argues the reply is mostly correct can earn full credit if it justifies why the other routes are also unlikely for this design. 10 points for simply agreeing or disagreeing without reasons.

**(3) Design change, 25 points.** Full credit: a change that reduces how close the design sits to its inversion, plus an honest cost. Examples: do not give the system an explicit, detailed model of suffering as part of its objective and instead rely on narrower, operator-approved tasks and low-impact constraints (cost: less autonomy and possibly worse care); bound the objective so it cannot reward extreme outcomes in either direction (cost: less sensitivity to severe cases); separate the component that detects suffering from the one that chooses actions, and let detection only veto actions (cost: added complexity, and a veto that could itself be inverted). Accept any change whose effect on the mechanism is argued. 12 points for a change with no stated cost or no link to the mechanism, such as "test more carefully".
feedback-instructions:: Name the strongest part of the answer. Then name the single most valuable improvement: usually either explaining why accuracy of the suffering model makes an inverted system worse, not safer, or finding a route that no sign-flip test would catch. If the answer is strong, ask whether their design change would still work if the system were extorted by a third party. No generic praise.
