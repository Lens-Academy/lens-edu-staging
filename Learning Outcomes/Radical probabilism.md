---
id: '45264136-726a-4d63-9cb4-21d34e63800a'
learning-outcome: "Evaluate belief changes that are not conditioning on a certain observation by the standards of radical probabilism: apply Jeffrey updating to uncertain evidence, judge other changes (such as those produced by further thinking) against the constraints that still apply, such as no predictable direction of change and eventual convergence, and explain how a bookie could exploit an agent that violates them."
topic: "[[../Domains and Topics/4 Agent Foundations/Imprecise probability and infra-Bayesianism]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Radical probabilism. AFFINE prerequisites: Probability. Not yet copied into requires:. %%
## Test:
id:: 24395cf3-b1b9-4af7-b7ba-b2b682d101c6

#### Question: Open
id:: 4e6de52a-3a41-4e27-abb2-8ed674d208ff
content:: 1. A forecaster has these beliefs about whether an AI model has a hidden capability H: P(H | the model passed test T) = 0.9, P(H | the model failed T) = 0.2, and P(the model passed T) = 0.4. The test log is partly corrupted. After reading it, the forecaster becomes 70% confident that the model passed, and their conditional beliefs about H given passing or failing do not change. What should their new credence in H be? Why is ordinary conditioning not available here?

2. Three reasoners consider an unproven mathematical conjecture. None of them receives any outside evidence; they only think.

- Reasoner A's credence goes 0.50, 0.70, 0.62, 0.66, 0.65, 0.65, and then stays near 0.65.
- Reasoner B's credence is 0.30 today, and B says: "After I work through the remaining cases tomorrow, I expect my credence to be about 0.6 on average."
- Reasoner C's credence keeps switching, 0.2, 0.8, 0.2, 0.8, and so on, for as long as C keeps thinking.

For each reasoner, say whether the pattern is consistent with radical probabilism. For each one that is not, describe how a bookie could make money from them.

3. A critic says: "Reasoner A is irrational, because A's beliefs changed without any new observation." Respond to the critic.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: in part 3 the learner may side with the critic, and can score full marks if the argument is sound. Accept equivalent terminology (Jeffrey conditioning, probability kinematics, martingale property, conservation of expected evidence, reflection, Dutch book, money pump).

**(a) Uncertain evidence, 25 points.** 15 points: new credence = 0.7 x 0.9 + 0.3 x 0.2 = 0.69 (up from 0.48 before reading the log). Give 8 of the 15 for the correct formula with an arithmetic slip. 10 points: ordinary conditioning requires learning a proposition with certainty, but here the forecaster is only 70% sure the model passed; Jeffrey updating keeps the conditional probabilities fixed and re-weights by the new probabilities of passing and failing.

**(b) The three reasoners, 50 points.** A, 10 points: consistent. Credences may change through thinking alone, and A's changes settle down and show no predictable direction. B, 20 points: inconsistent, because B's current credence (0.3) differs from B's own expectation of their future credence (0.6); a rational credence should equal the expected value of one's future credence. 10 for identifying the violation, 10 for a way to exploit it: for example, the bookie buys from B a ticket paying 1 if the conjecture is true at 0.3, and sells B for about 0.6 a contract paying B's credence tomorrow; tomorrow both are worth B's credence at that time, so they are settled against each other and the bookie keeps about 0.3 for certain. A simpler strategy that makes money in expectation by B's own lights (buy the ticket now at 0.3, sell it back tomorrow at B's expected higher price) earns 6 of the 10. C, 20 points: inconsistent, because C's credence never converges. 10 for identifying the violation, 10 for exploitation: the bookie buys a ticket on the conjecture from C when C's credence is 0.2 and sells it back to C when it is 0.8, gaining about 0.6 per cycle with certainty, as often as C keeps switching.

**(c) Reply to the critic, 25 points.** Full credit for either position, argued. Against the critic: radical probabilism drops the requirement that every rational change of belief comes from conditioning on an observation; thinking longer (working out consequences one could not compute before) is a legitimate source of change, and A meets the constraints that remain. With the critic: a defence that treats thinking as observing the result of a computation, or that argues belief changes need an evidential source, earns full credit if it engages with why radical probabilists reject that requirement. 10 points for a bare assertion on either side.
feedback-instructions:: Say whether the learner tied each verdict in part 2 to a specific constraint and a concrete exploitation, since that is the core of the skill. Name the strongest part of the answer and the single change that would improve it most. Ask one follow-up question, such as whether a reasoner who is well calibrated but whose credences never settle could still be exploited. No generic praise.
