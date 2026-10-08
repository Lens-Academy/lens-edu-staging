---
id: '0cc12c0f-356f-4a41-bcb9-3d8a05089ebc'
title: "D.1.1.7 Open-ended questions"
tldr: "A conclusion on the layers from preference to reward, followed by three open discussion questions on prescriptive and descriptive implications and on safer weakenings of the axioms."
summary_for_tutor: "This is Section 8 'Conclusion' of Iliad worksheet D.1.1 Preferences to Rewards, followed by the reference list. It summarizes the layers (ordinal utility, vNM utility, reward) and contains open-ended Exercises 8.1-8.3 about implications for agent design, weaker axioms that might be safer, and further example preferences, each with collapsed discussion notes rather than unique answers. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Fernando E. Rosas
source_url: https://iliad-intensive.org/agency/preferences-to-rewards/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Open-ended questions

:::callout {title="Exercise" tone="amber"}
**Exercise 8.1.** Do the results have any prescriptive or descriptive implications? What kinds of agents, with what kinds of preferences should we design? By default, what kind of agents should we expect to obtain via typical training processes?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Discussion notes, not a unique answer. Prescriptively, the money-pump and dominance arguments say that an agent which cares about a fungible resource is under pressure toward completeness and transitivity — coherence is an attractor for agents that can be exploited otherwise. Descriptively, nothing guarantees that trained systems satisfy any axiom: gradient descent on episodic objectives can produce context-dependent, intransitive, or incomparable preferences, especially off-distribution. A reasonable expectation is approximate coherence where incoherence was penalised during training, and no guarantee elsewhere. For design, the trade-off runs both ways: highly coherent agents are more predictable and analysable but are exactly the ones for which instrumental-convergence arguments bite; agents with incomplete or unstable preferences may be harder to exploit into goal-directed resource acquisition, at the cost of being harder to reason about.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 8.2.** Let's assume a superintelligence has preferences over trajectories. Are there weaker versions of the axioms that make it more plausible that these preferences are "safe for us" compared to preferences that lead to utilities or even rewards?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Discussion notes. The natural candidates weaken one axiom at a time. Dropping *completeness* is the most studied: an agent with incomplete preferences can remain undecided between continuing and being shut down, so it is not pushed by coherence arguments toward shutdown-resistance; money pumps also lose force because the agent may simply refuse trades between incomparable options. Weakening *continuity* permits lexicographic safety: "never cross the constraint, then optimise" cannot be represented by a single real-valued utility, which is arguably a feature. Weakening *independence* allows certainty-favouring (Allais-like) preferences, which dampen gambling-for-resources behaviour. Weakening *temporal $\gamma$-indifference* removes the local reward representation: goals about the shape of a trajectory as a whole (diversity, "never do X") stop being expressible as accumulated reward. The common pattern: each axiom kept buys a representation theorem and optimisation pressure; each axiom dropped blocks a coherence-based failure mode while making the agent's behaviour less analysable.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 8.3.** More generally, are there interesting examples of preferences over trajectories that the students could analyse, that do or do not satisfy some of the axioms?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Discussion notes; instructive examples include: (i) lexicographic safety-first preferences — violate continuity (see Exercise 5.3); (ii) Pareto/multi-objective preferences, undominated but unaggregated — violate completeness; (iii) hyperbolic discounting — satisfies the vNM axioms at a single decision time yet violates temporal $\gamma$-indifference, hence admits utility but no stationary reward/discount pair, and is dynamically inconsistent; (iv) the certainty effect (Allais) — violates independence only; (v) satisficing ("anything above the threshold is equally fine") — complete and transitive, so ordinal utility exists, but indifference plateaus interact oddly with lotteries near the threshold; (vi) trajectory-shape goals such as "visit as many distinct states as possible" — can satisfy all four vNM axioms (a utility exists) while violating the temporal axiom, illustrating exactly the gap between utility and reward.

:::

\## References

Maurice Allais (1953). *Le comportement de l'homme rationnel devant le risque: critique des postulats et axiomes de l'ecole Americaine*. Econometrica.

Robert J Aumann (1962). *Utility theory without the completeness axiom*. Econometrica.

Michael Bowling, John D. Martin, David Abel, and Will Dabney (2023). [*Settling the Reward Hypothesis*](https://arxiv.org/abs/2212.10420). arXiv preprint arXiv:2212.10420.

Gerard Debreu (1954). *Representation of a preference ordering by a numerical function*. Decision Processes.

Peter C. Fishburn (1970). *Utility Theory for Decision Making*. Wiley.

Peter C. Fishburn (1971). *A Study of Lexicographic Expected Utility*. Management Science.

Johan E. Gustafsson (2010). *A Money-Pump for Acyclic Intransitive Preferences*. Dialectica.

Peter J. Hammond (1988). *Consequentialist Foundations for Expected Utility*. Theory and Decision.

Xiaoye Jiang, Lek-Heng Lim, Yuan Yao, and Yinyu Ye (2011). *Statistical ranking and combinatorial Hodge theory*. Mathematical Programming.

Daniel Kahneman and Amos Tversky (1979). *Prospect Theory: An Analysis of Decision under Risk*. Econometrica.

David M. Kreps (1988). *Notes on the Theory of Choice*. Westview Press.

Mark J. Machina (1982). *"Expected Utility" Analysis without the Independence Axiom*. Econometrica.

Andreu Mas-Colell, Michael D. Whinston, and Jerry R. Green (1995). *Microeconomic Theory*. Oxford University Press.

Andrew Y. Ng, Daishi Harada, and Stuart J. Russell (1999). *Policy Invariance under Reward Transformations: Theory and Application to Reward Shaping*. Proceedings of the Sixteenth International Conference on Machine Learning.

Silviu Pitis (2019). *Rethinking the discount factor in reinforcement learning: A decision theoretic approach*. Proceedings of the AAAI Conference on Artificial Intelligence.

Mehran Shakerinava and Siamak Ravanbakhsh (2022). *Utility Theory for Sequential Decision Making*. Proceedings of the International Conference on Machine Learning.

John von Neumann and Oskar Morgenstern (1944). *Theory of Games and Economic Behavior*. Princeton University Press.

Martha White (2017). *Unifying Task Specification in Reinforcement Learning*. Proceedings of the 34th International Conference on Machine Learning.
