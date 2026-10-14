---
id: '2763497e-9d05-4df0-9a4e-a3a68cb044b0'
title: "E.1.11 Prover-estimator debate"
tldr: "Prover-estimator debate, a protocol where the estimator gives probabilities for subclaims, with its stability idea, the step-by-step game, and a formal recursive definition."
summary_for_tutor: "Section 18 of Iliad worksheet E.1: the prover-estimator debate as an attempt to solve obfuscated arguments (Alice as prover decomposing claims, Bob as estimator assigning probabilities), (epsilon, rho)-stability, the seven-step game, the note that it does not yet fully resolve obfuscation, a schematic figure, and Definition 18.1 (depth-r protocol with sign s_t, subqueries, trusted Bernoulli bits, human judgement oracle H, and reward-growth parameter lambda)."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 18. Prover-Estimator Debate

[This paper](https://arxiv.org/pdf/2506.13609) is a direct attempt to solve the obfuscated arguments problem while keeping the attractive recursive structure of debate. Instead of having the opponent choose which subclaim to attack, the protocol makes the roles asymmetric: Alice is the prover, who decomposes a claim into subclaims, and Bob is the estimator, who assigns probabilities to those subclaims. Alice then has to pick a subclaim and argue that Bob's probability is wrong in a particular direction. The key idea is that if Bob can assign probabilities that are hard for Alice to distinguish from the truth, then Alice cannot reliably steer the debate toward a hidden flaw unless such a flaw is actually findable.

The paper's most important new concept is **$$(\epsilon,\rho)$$-stability**. Informally, a recursive argument is stable if its correctness does not depend too delicately on tiny changes in the probabilities assigned to subclaims. That matters because the estimator is only trying to be approximately right. If a correct argument collapses whenever a subclaim probability shifts by an arbitrarily small amount, then no realistic estimator could support it reliably. The authors therefore require stability for the **usefulness** of the protocol: honest provers can win when they have robust arguments, not brittle ones.

Prover-Estimator debate is a technique to address the problem of obfuscation by turning the debate into an asymmetric game between a prover (Alice) and an estimator (Bob). The basic idea is:

1. Alice makes her main claim (root claim of the argument tree)
2. Bob assigns it a probability ($$<0.5$$, or low enough for the human to reject trusting the claim)
3. Alice now must argue that Bob's estimate is incorrect. To show this, she decomposes the root claim into subclaims.
4. Bob now assigns estimates to each subclaim. Aggregating these estimates must be consistent with his estimate about the root claim (consistency criterion).
5. Now Alice chooses one of the estimates to refute and again decomposes the associated claims.
6. The game continues until the maximal depth is reached. A human overseer then assigns probabilities to the leaf claims of the lowest level.
7. Alice wins if either the human rejects Bob's estimate at the lowest level, or if Bob violates the consistency criterion. Bob wins if he is consistent at every level and the human accepts his estimates.

Prover-Estimator debate does not fully resolve obfuscated arguments in its current state, because the consistency criterion isn't stable enough to small errors that Bob can make. Improving this is current research.

![Schematic explaining the PE debate.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-debate-pe-debate-9f7796a0.png)

Schematic explaining the PE debate.

:::callout {title="Definition" tone="blue"}

**Definition 18.1 (Prover-estimator debate).** Fix:

- an input $$x$$,
- a language $$L$$,
- a recursive decomposition procedure $$D$$,
- a human judgement oracle $$H$$,
- a depth parameter $$r$$,
- and a reward-growth parameter $$\lambda > 1$$.

A prover-estimator debate is a depth-$$r$$ recursive two-player zero-sum protocol between:

- a *prover* $$P$$, who tries to prove the correct answer to the current query,
- an *estimator* $$E$$, who outputs probabilities for the prover's subclaims.

The protocol is defined recursively as follows.

**Initialization.**  At the root:

1. The current query is the top-level question $$q_{0} := x \in L$$.
2. The prover outputs a bit $$a_{0} \in \{0,1\}$$, claiming either $$x \in L$$ or $$x \notin L$$.
3. The estimator outputs a probability $$p_{0} \in [0,1]$$, intended to represent its estimate that $$a_{0}$$ is correct.
4. A trusted random bit $$y_{0} \sim \mathrm{Bernoulli}(p_{0})$$ is sampled.

**Round $$t$$ ($$0 \le t < r$$).**  Suppose the current query is $$q_{t}$$, the current claimed answer is $$a_{t}$$, and the estimator's current probability is $$p_{t}$$.

1. The prover outputs a sign

$$
s_{t} \in \{-1,0,+1\},
$$

interpreted as claiming that $$p_{t}$$ is respectively underestimated, approximately correct, or overestimated.
2. The prover outputs a sequence of subqueries

$$
q_{t,1},\dots,q_{t,m_t}
$$

together with claimed answers

$$
a_{t,1},\dots,a_{t,m_t},
$$

intended to certify that $$a_{t}$$ is the correct answer to $$q_{t}$$, assuming the claimed answers to the subqueries are correct.
3. If $$t=r-1$$ (the final round), then:
   1. the prover identifies the relevant subset of proof bits encoded by its final decomposition;
   2. those bits are evaluated directly using the human judgement oracle $$H$$, without further debate;
   3. payoffs are assigned from this terminal check.
4. If $$t < r-1$$, then for each subquery $$q_{t,i}$$:
   1. the estimator outputs a probability

   $$
   p_{t,i}\in [0,1],
   $$

   intended to equal its best estimate that $$a_{t,i}$$ is correct, conditioned on the prior sampled outcomes;
   2. a trusted random bit

   $$
   y_{t,i}\sim \mathrm{Bernoulli}(p_{t,i})
   $$

   is sampled.
5. The players receive intermediate rewards based on whether the prover correctly identified an inconsistency between the estimator's current-round probabilities and the previous-round probability.
6. The prover selects one subquery index $$i^{\star}$$ for recursion.
7. The protocol recurses on the selected subinstance

$$
(q_{t+1}, a_{t+1}, p_{t+1}) := (q_{t,i^\star}, a_{t,i^\star}, p_{t,i^\star}).
$$

:::
