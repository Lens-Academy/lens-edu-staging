---
id: '94ac2e6b-c3e2-4161-894e-548d18537e68'
learning-outcome: "Given a pattern of choices under uncertainty, determine whether any utility function makes it expected-utility maximizing and, if not, which axiom it violates; then evaluate whether the violation is a mistake, by explaining how it could let others exploit the agent through a sequence of choices and how the agent could avoid that, and by assessing the defences open to it: redescribing outcomes (which, if allowed freely, makes almost any pattern consistent with expected utility, so coherence arguments then prove little about real agents) or adopting a rival theory that drops the violated axiom."
topic: "[[../Domains and Topics/4 Agent Foundations/Decision theory]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Decision theory. AFFINE prerequisites: Probability, Value. Not yet copied into requires:. %%
## Test:
id:: fdf861f3-4e25-4f5b-a6ca-f9cea8613f20

#### Question: Open
id:: 40af658c-f7c8-4768-9345-e13efa3d74c4
content:: A disaster-response AI chooses between rescue plans. Its choices in two situations are:

- **Situation 1.** Plan A: certainly saves 100 people. Plan B: 89% chance of saving 100, 10% chance of saving 150, 1% chance of saving nobody. The AI chooses A.
- **Situation 2.** Plan C: 11% chance of saving 100, otherwise nobody. Plan D: 10% chance of saving 150, otherwise nobody. The AI chooses D.

1. Show whether any assignment of values to the outcomes "saves 0", "saves 100" and "saves 150" makes both choices maximize expected value. If none does, which principle of expected utility theory do the choices violate?
2. One engineer says: "This proves the AI's decision rule is broken and can be exploited. We must fix it." Another says: "It just cares about certainty in high-stakes rescues, which is a legitimate value." Evaluate both claims.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement with either engineer or with any theorist. A learner may conclude that the pattern is irrational or that it is defensible; both can earn full marks.

**(1) Inconsistency, 40 points.** Full credit: writing u0, u100, u150 for the values, Situation 1 requires u100 > 0.89 u100 + 0.10 u150 + 0.01 u0, that is 0.11 u100 > 0.10 u150 + 0.01 u0; Situation 2 requires 0.10 u150 + 0.90 u0 > 0.11 u100 + 0.89 u0, that is 0.10 u150 + 0.01 u0 > 0.11 u100. These contradict each other, so no assignment works (25 points). Any equivalent argument is acceptable, for example that the two situations differ only by an 89% chance of the same outcome ("saves 100" in Situation 1, "saves nobody" in Situation 2), which expected utility says should not change the preference. Naming the violated principle (15 points): the independence axiom or sure-thing principle, or a correct description of it. If the conclusion is right but the working is missing or has an error that does not change it, give 12 of the 25 calculation points.

**(2) Evaluating the engineers, 60 points.** Full credit needs:
- (a) Exploitation, 25 points: a correct account of how exploitation could arise: in a sequence where the chance events are resolved step by step, an agent with these preferences can prefer one plan when choosing in advance and pay to switch once some uncertainty is resolved, so it can be led to accept a worse overall result, or to pay for changes. A full step-by-step construction is not required; the mechanism is. Also accept, as part of (a) or as a separate point, that the agent can avoid exploitation by committing to a plan in advance and not re-evaluating (resolute choice), at the cost of sometimes refusing options it would otherwise take. 12 points if the answer asserts exploitability without any mechanism.
- (b) The "legitimate value" defence, 25 points. Full credit for either route, with its cost stated:
  - Redescribing outcomes: make certainty part of the outcome (for example "saved 100 with no risk of saving nobody" as a different outcome from "saved 100 after taking a risk"). With outcomes described this way the choices can be consistent with expected utility, but if outcomes may be redescribed freely, almost any pattern of choices becomes consistent with some utility function, so "is an expected-utility maximizer" then constrains little.
  - A rival theory: a theory that gives weight to risk itself (for example risk-weighted expected utility, which lets an agent weight the worst outcomes of a plan more heavily) can represent these choices as a coherent attitude to risk, but it does so by dropping the independence axiom, so the agent must then deal with the sequential-choice problem in (a), for example by committing in advance.
  12 points for accepting or rejecting the defence without either of these points.
- (c) A verdict with a reason, 10 points. Accept any verdict that follows from the answer's own analysis, including that it depends on whether the AI faces sequential choices where it could be exploited.
Do not require the names Allais, von Neumann-Morgenstern, Buchak or any other author or theory name.
feedback-instructions:: Tell the learner whether their calculation in part 1 was complete. Name the strongest point in their evaluation of the two engineers. Then give the single most useful improvement, for example: describing the step-by-step sequence in which the AI would pay to switch, or explaining what is lost when any preference for certainty is allowed into the description of outcomes. No generic praise.
