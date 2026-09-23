---
id: '590b31d2-9232-461a-b878-8eec580271ef'
learning-outcome: "Explain how infra-Bayesianism handles an environment that lies outside every hypothesis the agent considers, by treating each hypothesis as a partial constraint (a convex set of distributions whose unconstrained parts are chosen by an adversary) and choosing policies by worst-case expected outcome, and derive for a given case what performance guarantee this gives that an ordinary Bayesian learner with a misspecified hypothesis class lacks."
topic: "[[../Domains and Topics/4 Agent Foundations/Imprecise probability and infra-Bayesianism]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Infra-Bayesianism. AFFINE prerequisites: Imprecise Probability, Reinforcement Learning. Not yet copied into requires:. %%
## Test:
id:: 5a4a764f-eab9-4b1e-97d0-29a016f3854f

#### Question: Open
id:: c6602e71-0f95-4e0e-99a6-47611a8abf87
content:: An agent must guess each bit of an endless binary sequence before seeing it, and scores 1 point for each correct guess. It cares about its long-run average score. The true sequence comes from a process far too complex for either agent below to model exactly: every third bit is 1, and the other bits follow no pattern that either agent can represent.

Agent B is an ordinary Bayesian learner. Its hypotheses are all the sequences that small finite-state machines (deterministic or random) can produce. It is designed so that, whichever of these hypotheses is true, its long-run score is nearly as good as the best policy for that hypothesis. The true sequence is not produced by any of them.

Agent I is an infra-Bayesian learner. One of its hypotheses is the partial statement "every third bit is 1", which says nothing about the other bits. Agent I is designed so that, for each of its hypotheses, its long-run score is nearly as good as the best policy for that hypothesis, where the bits the hypothesis leaves open are treated as chosen by an adversary who knows the agent's policy.

1. Explain why Agent B's design guarantee tells us nothing about how B performs on this sequence.
2. State what can be guaranteed about Agent I's long-run score on this sequence, and explain why its design guarantee implies this.
3. Name one cost or limitation of the infra-Bayesian approach, as shown by this setup or in general, and explain it.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: the learner may think infra-Bayesianism is promising or not, and can score full marks either way. Accept equivalent terminology (realizability, grain of truth, Knightian uncertainty, Murphy, maximin, credal set).

**(a) Agent B, 30 points.** Full credit: B's guarantee is only about sequences produced by its hypotheses; the true sequence is outside that class, so the guarantee does not apply. A policy can meet the guarantee on every in-class hypothesis and still behave badly on one particular out-of-class sequence, because such a failure costs almost nothing under any in-class hypothesis. The learner does not need to claim that B will in fact fail; do not penalize an answer that says B might do well by luck, as long as it says nothing guarantees it. 12 points for "B's hypotheses are wrong" without explaining why low regret on the class says nothing outside it.

**(b) Agent I's guarantee, 50 points.** 20 points: in the long run, I scores at least about as well as the best score any policy can guarantee against an adversary constrained only by "every third bit is 1". This is at least about one third of the bits, since guessing 1 on every third bit gets those right whatever the adversary does. Accept a higher figure if the learner argues that a randomizing policy does better against an adversary who cannot see the agent's coin flips. 30 points: the reason. The true sequence obeys "every third bit is 1", so it is one of the sequences that an adversary constrained by that hypothesis could produce. If I scored clearly worse than the guaranteed value on it, I would have large regret with respect to that hypothesis, contradicting its design guarantee. The guarantee is on I's score, not on how I reaches it: an answer that claims I is guaranteed to learn to guess the third bits specifically overstates it, so deduct 5 points for that claim. 12 of the 30 for "I considers the worst case, so it is safe" with no link between the true sequence and the partial hypothesis.

**(c) Cost or limitation, 20 points.** Any one, correctly explained, for example: the guarantee is weak (a floor tied to the partial pattern, not good prediction of the unconstrained bits); worst-case choice can be overly pessimistic when the world is not adversarial; the guarantees hold only in the long run and under conditions such as no irreversible traps; the approach is hard to compute. 8 points for naming a limitation without explanation.
feedback-instructions:: Say whether the learner connected the true sequence to the partial hypothesis through the adversary argument, since that link is the core of the skill. If the learner claimed that I is guaranteed to learn to guess the third bits correctly, point out that the guarantee is only on the score: I could reach the same score another way. Name the strongest part of the answer and the single change that would improve it most. Ask one follow-up question, such as what I's guarantee would be if it also had the hypothesis "every fifth bit is 0". No generic praise.
