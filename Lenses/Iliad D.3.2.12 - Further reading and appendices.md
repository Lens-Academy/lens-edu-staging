---
id: '0ce8d7f6-e329-49a0-9508-2fcbb96932a7'
title: "D.3.2.12 Further reading and appendices"
tldr: "Lists further reading, a worked coin example of the mixture and value function, Knuth's difficulty scale and the references."
summary_for_tutor: "End matter of worksheet D.3.2 (AIXI): Further reading, Appendix A (worked example with a two-headed and a fair coin: prior 1/2 each, xi(o_1 = H) = 3/4, posterior 2/3 and 1/3, xi(o_2 = H) = 5/6, V_xi^{pi_H} = 3/4 and convergence to 1), Appendix B (Knuth difficulty scale) and references with footnotes. No exercises in this lens."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Further reading

- Hutter, [*An Introduction to Universal Artificial Intelligence*](https://www.hutter1.net/publ/uaibook2.pdf) (2024): Chapter 2.7 (Kolmogorov complexity), Chapters 3.7–3.8 (the model class and universal prior), and Chapter 7.4 (AIXI).
- Hutter, [*Universal Artificial Intelligence: Sequential Decisions Based on Algorithmic Probability*](http://www.hutter1.net/ai/uaibook.htm) (Springer, 2005) — the original book-length treatment; Lem. 5.28 handles the countable-${\mathcal{M}}$ self-optimizing case.
- Blackwell & Dubins, [*Merging of Opinions with Increasing Information*](https://doi.org/10.1214/aoms/1177704456) (Ann. Math. Statist., 1962) — the merging-of-opinions theorem behind on-policy value convergence.
- Leike & Hutter, [*Bad Universal Priors and Notions of Optimality*](https://arxiv.org/abs/1510.04931) (COLT 2015) — adversarial choices of the universal Turing machine can make AIXI behave arbitrarily badly.

\## A. Worked Example: Bayesian Mixture and Value Function

:::callout {title="Note" tone="blue"}

**Setup.**

- **Actions:** ${\mathcal{A}} = \{H, T\}$ (predict the next coin flip)
- **Observations:** ${\mathcal{O}} = \{H, T\}$ (actual coin flip)
- **Rewards:** ${\mathcal{R}} = \{0, 1\}$, with $r_{t} = \llbracket a_{t} = o_{t} \rrbracket$
- **Model class:** ${\mathcal{M}} = \{\nu_{HH}, \nu_{HT}\}$ (two-headed coin, fair coin)
- **Prior:** $w_{\nu_{HH}}= w_{\nu_{HT}}= \tfrac{1}{2}$

:::

**Before any interaction** ($t=1$, ${\text{\ae}}_{<1}= \epsilon$):

$$
\begin{aligned}\xi(o_{1} = H \mid a_{1}) ~&=~ \tfrac{1}{2}\cdot 1 + \tfrac{1}{2}\cdot \tfrac{1}{2}~=~ \tfrac{3}{4}.\end{aligned}
$$

**After observing a head** ($t=2$), the posterior updates:

$$
\begin{aligned}w(\nu_{HH}\mid {\text{\ae}}_{1}) ~&=~ \tfrac{1}{2}\cdot \frac{1}{3/4}~=~ \tfrac{2}{3},&w(\nu_{HT}\mid {\text{\ae}}_{1}) ~&=~ \tfrac{1}{2}\cdot \frac{1/2}{3/4}~=~ \tfrac{1}{3}.\end{aligned}
$$

**Updated prediction:** $\xi(o_{2} = H \mid {\text{\ae}}_{1}a_{2}) = \tfrac{2}{3}\cdot 1 + \tfrac{1}{3}\cdot \tfrac{1}{2}= \tfrac{5}{6}$.

**Value function.** Continuing the same setup, suppose the agent always predicts $H$ (policy $\pi_{H}$).

Under $\nu_{HH}$: always correct, $r_{t} = 1$ every step: $V_{\nu_{HH}}^{\pi_H}(\epsilon) = (1-\gamma) \sum_{k=0}^{\infty} \gamma^{k} \cdot 1 = 1$.

Under $\nu_{HT}$: correct half the time: $V_{\nu_{HT}}^{\pi_H}(\epsilon) = (1-\gamma) \sum_{k=0}^{\infty} \gamma^{k} \cdot \tfrac{1}{2}= \tfrac{1}{2}$.

The mixture value (by Exercise 4.2) is: $V_{\xi}^{\pi_H}(\epsilon) = \tfrac{1}{2}\cdot 1 + \tfrac{1}{2}\cdot \tfrac{1}{2}= \tfrac{3}{4}$.

As the agent observes more heads ($\mu = \nu_{HH}$), the posterior on $\nu_{HH}$ increases towards 1, and $V_{\xi}^{\pi_H}\to V_{\nu_{HH}}^{\pi_H}= 1$. This is on-policy value convergence (Theorem 7.6) in action.

\## B. Knuth's Difficulty Scale

Each subproblem carries a difficulty rating in square brackets, following Knuth's rating scheme for exercises (Knuth 1973) in slightly adapted form. The rating assumes that the material in the preceding problems (on which the subproblem depends) has been understood. In-between values are possible.

**[00]** *Very easy.* Solvable from the top of your head.

**[10]** *Easy.* Needs 15 minutes to think, possibly pencil and paper.

**[20]** *Average.* May take 1–2 hours to answer completely.

**[30]** *Moderately difficult or lengthy.* May take several hours to a day.

**[40]** *Quite difficult or lengthy.* Often a significant research result.

**[50]** *Open research problem.* An obtained solution should be published.

\## References

D. Blackwell and L. Dubins (1962). [*Merging of opinions with increasing information*](http://www.dklevine.com/archive/refs4565.pdf). Annals of Mathematical Statistics.

Marcus Hutter (2005). [*Universal Artificial Intelligence: Sequential Decisions based on Algorithmic Probability*](http://www.hutter1.net/ai/uaibook.htm). Springer.

Marcus Hutter, David Quarel, and Elliot Catt (2024). [*An Introduction to Universal Artificial Intelligence*](http://www.hutter1.net/ai/uaibook2.htm). Chapman & Hall.

D. E. Knuth (1973). *The Art of Computer Programming, Volume I: Fundamental Algorithms*. Addison-Wesley.

Jan Leike and Marcus Hutter (2015). [*Bad Universal Priors and Notions of Optimality*](https://arxiv.org/abs/1510.04931). CoRR.

[^1]: See Appendix A for a worked example. For simplicity, we consider only geometric discounting.

[^2]: The optimal value is defined as a $\sup$ over policies. In general, a supremum need not be attained (e.g. $\sup_{x \in (0,1)}x = 1$ but no $x \in (0,1)$ achieves it). Section 2 shows that the sup is attained in our setting.

[^3]: We are deliberately avoiding a formal treatment of measure theory here. Not all subsets of $({\mathcal{A}} \times {\mathcal{E}})^{\infty}$ are measurable; we restrict to "nice" (measurable) sets built from finite-prefix conditions via countable set operations, which suffice for everything in this sheet. For a rigorous treatment using $\sigma$-algebras and probability measures, see (Hutter et al. 2024, Chapter 2.2).

[^4]: The standard name is *absolute continuity* of $P$ with respect to $Q$, written $P \ll Q$.

[^5]: If the true environment is $\mu$ then we don't care about the behaviour of the Bayesian agent on histories that have $\mu^{\pi}$-probability zero: such histories will never be observed anyway.
