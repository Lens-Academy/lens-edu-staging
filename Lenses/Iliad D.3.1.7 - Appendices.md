---
id: 'd44de965-cccc-4371-b953-142a18235af1'
title: "D.3.1.7 Appendices"
tldr: "Collects the appendices: proofs of Pinsker's inequality and KL non-negativity, the model class and Solomonoff prior, and how to choose the best approximating environment."
summary_for_tutor: "Appendices A-D and references of worksheet D.3.1. A: Lemma A.1 (binary Pinsker) and the proof of Theorem 4.1. B: Gibbs' inequality (Lemma B.1) and the proof of Theorem 2.2. C: the model class M, the Solomonoff prior w_nu = 2^{-K(nu)}, and why lower-semicomputable semimeasures are needed for a faithful construction. D: the choice of muhat for the misspecified bound. No exercises in this lens."
authors:
  - David Quarel (ARENA)
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/agency/solomonoff-induction/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## A. Proof of Pinsker's inequality

We first prove the following lemma:

:::callout {title="Theorem" tone="green"}

**Lemma A.1 (Pinsker's binary inequality).** For $$0 \leq p \leq 1$$ and $$0 < q < 1$$ we have

$$
2(p-q)^{2} ~\leq~ p \ln \frac{p}{q}+ (1-p) \ln \frac{1-p}{1-q}.
$$

:::

Define $$f(x) := p \ln x + (1-p) \ln (1-x)$$, so that

$$
p \ln \frac{p}{q}+ (1-p) \ln \frac{1-p}{1-q}= f(p) - f(q) = \int_{q}^{p} f'(x)\, dx = \int_{q}^{p} \frac{p-x}{x(1-x)}\, dx,
$$

using $$f'(x) = \frac{p}{x}- \frac{1-p}{1-x}= \frac{p-x}{x(1-x)}$$. Recall also that $$x(1-x) \leq \tfrac{1}{4}$$ on $$[0,1]$$, so $$\frac{1}{x(1-x)}\geq 4$$.

**Case $$q \leq p$$.** For every $$x \in [q,p]$$ we have $$x \leq p$$, hence $$p - x \geq 0$$.

$$
\frac{p-x}{x(1-x)}\;\geq\; 4(p-x) \qquad \text{for }x \in [q,p].
$$

Integrating over $$[q,p]$$,

$$
\int_{q}^{p} \frac{p-x}{x(1-x)}\, dx \;\geq\; 4 \int_{q}^{p} (p-x)\, dx \;=\; 2(p-q)^{2}.
$$

**Case $$q \geq p$$.** For every $$x \in [p,q]$$ we have $$x \geq p$$, hence $$x - p \geq 0$$.

$$
\frac{x-p}{x(1-x)}\;\geq\; 4(x-p) \qquad \text{for }x \in [p,q].
$$

Integrating over $$[p,q]$$,

$$
\begin{aligned}\int_{q}^{p} \frac{p-x}{x(1-x)}\, dx&= \int_{p}^{q} \frac{x-p}{x(1-x)}\, dx \\&\geq 4 \int_{p}^{q} (x-p)\, dx = 4 \int_{q}^{p} (p-x)\, dx = 2(p-q)^{2}\end{aligned}
$$

:::callout {title="Proof of Theorem 4.1" tone="neutral" collapse="closed"}

We now reduce Theorem 4.1 to the binary inequality Lemma A.1. Recall $$p_{0} + p_{1} = 1$$ and $$q_{0} + q_{1} = 1$$. We handle the boundary case $$q_{x} = 0$$ first, then reduce the interior case directly to Lemma A.1.

**Case 1: $$q_{x} = 0$$ for some $$x \in \mathbb{B}$$.** If $$p_{x} > 0$$, then the right-hand side of $$(\star)$$ contains $$p_{x} \ln \tfrac{p_x}{0}= +\infty$$, so $$(\star)$$ holds trivially. If instead $$p_{x} = 0$$, that atom contributes $$0$$ to both sides (using the convention $$0 \ln \tfrac{0}{0}= 0$$). The other atom $$x'$$ then satisfies $$p_{x'}= 1$$ and $$q_{x'}= 1 - q_{x} = 1$$, so both sides vanish and $$(\star)$$ holds.

**Case 2: $$q_{0}, q_{1} > 0$$.** Since $$q_{1} = 1 - q_{0}$$ and $$p_{1} = 1 - p_{0}$$, the two sides of $$(\star)$$ become

$$
\sum_{x \in \mathbb{B}}(q_{x} - p_{x})^{2} = (q_{0} - p_{0})^{2} + \big((1-q_{0}) - (1-p_{0})\big)^{2} = 2(p_{0} - q_{0})^{2},
$$

$$
\sum_{x \in \mathbb{B}}p_{x} \ln \tfrac{p_x}{q_x}= p_{0} \ln \tfrac{p_0}{q_0}+ (1 - p_{0}) \ln \tfrac{1 - p_0}{1 - q_0}.
$$

So $$(\star)$$ is exactly $$2(p_{0} - q_{0})^{2} \leq p_{0} \ln \tfrac{p_0}{q_0}+ (1 - p_{0}) \ln \tfrac{1 - p_0}{1 - q_0}$$, which is Lemma A.1 with $$p = p_{0}$$ and $$q = q_{0}$$ (here $$0 < q_{0} < 1$$, since $$q_{0}, q_{1} > 0$$).

:::

\## B. Proof of KL non-negativity

We prove Theorem 2.2. The core is the elementary inequality

$$
\ln x ~\leq~ x - 1 \qquad \text{for all }x > 0, \quad \text{equality iff }x = 1.
$$

(Let $$f(x) := (x - 1) - \ln x$$; then $$f'(x) = 1 - 1/x$$, vanishing only at $$x = 1$$, with $$f''(x) = 1/x^{2} > 0$$, so $$f$$ is strictly convex and attains its unique minimum $$f(1) = 0$$ at $$x = 1$$.)

:::callout {title="Theorem" tone="green"}

**Lemma B.1 (Gibbs' inequality).** Let $$P, Q$$ be probability distributions over a finite set $$\mathcal{X}$$, with the conventions $$0 \ln \tfrac{0}{q}:= 0$$ and $$p \ln \tfrac{p}{0}:= \infty$$. Then

$$
\sum_{x \in \mathcal{X}}P(x) \ln \frac{P(x)}{Q(x)}~\geq~ 0,
$$

with equality iff $$P(x) = Q(x)$$ for every $$x$$ with $$P(x) > 0$$.

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

If $$Q(x) = 0$$ for some $$x$$ with $$P(x) > 0$$, the LHS is $$+\infty$$ and the inequality is strict. Otherwise restrict the sum to $$\{x : P(x) > 0\}$$ (terms with $$P(x) = 0$$ contribute $$0$$ by convention), where every ratio $$Q(x)/P(x)$$ is in $$(0, \infty)$$. Apply $$\ln y \leq y - 1$$ to $$y = Q(x)/P(x)$$:

$$
\begin{aligned}- \sum_{x} P(x) \ln \frac{P(x)}{Q(x)}~=~ \sum_{x} P(x) \ln \frac{Q(x)}{P(x)}~\leq~ \sum_{x} P(x) \left(\frac{Q(x)}{P(x)}- 1\right) \\ ~=~ \sum_{x} Q(x) - \sum_{x} P(x) ~\leq~ 0,\end{aligned}
$$

where the last step uses $$\sum_{x} Q(x) \leq 1 = \sum_{x} P(x)$$ (the sum over $$\{x : P(x) > 0\}$$ may miss some $$Q$$-mass). Negating gives the claim. Equality in $$\ln y \leq y - 1$$ requires $$y = 1$$ for every $$x$$ with $$P(x) > 0$$, i.e. $$Q(x) = P(x)$$ there; equality in $$\sum Q \leq \sum P$$ then forces $$Q$$ to have no mass outside $$\mathrm{supp}\,P$$. Both together give $$P = Q$$ on all of $$\mathcal{X}$$.

:::

:::callout {title="Proof of Theorem 2.2" tone="neutral" collapse="closed"}

*Part (a).* Apply Lemma B.1 with $$\mathcal{X}= \mathbb{B}^{n}$$, $$P(x_{1:n}) = \nu(x_{1:n})$$, $$Q(x_{1:n}) = \rho(x_{1:n})$$. Both are probability distributions on $$\mathbb{B}^{n}$$ since $$\nu$$ and $$\rho$$ are environments. The lemma gives $$D_{n}(\nu \parallel \rho) \geq 0$$ with the stated equality condition.

*Part (b).* For each fixed history $$x_{<t}$$ with $$\nu(x_{<t}) > 0$$, apply Lemma B.1 with $$\mathcal{X}= \mathbb{B}$$, $$P = \nu(\cdot \mid x_{<t})$$, $$Q = \rho(\cdot \mid x_{<t})$$ (both are probability distributions on $$\mathbb{B}$$):

$$
\sum_{x_t \in \mathbb{B}}\nu(x_{t} \mid x_{<t}) \ln \frac{\nu(x_{t} \mid x_{<t})}{\rho(x_{t} \mid x_{<t})}~\geq~ 0,
$$

with equality iff $$\nu(\cdot \mid x_{<t}) = \rho(\cdot \mid x_{<t})$$. Multiply by $$\nu(x_{<t}) \geq 0$$ and sum over $$x_{<t}$$: this gives $$d_{t}(\nu \parallel \rho) \geq 0$$, as a sum of non-negative terms. Equality forces every $$x_{<t}$$ with $$\nu(x_{<t}) > 0$$ to contribute a vanishing inner sum, which is exactly the stated condition.

:::

\## C. Model Class $${\mathcal{M}}$$

All results in this sheet hold for any countable class $${\mathcal{M}}$$ and prior $$w_{\nu}$$. The canonical **Solomonoff** choice takes $${\mathcal{M}}$$ to be the class of all computable environments and the **Solomonoff prior**

$$
w_{\nu} ~:=~ 2^{-K(\nu)},
$$

where $$K(\nu)$$ is the *Kolmogorov complexity* of $$\nu$$: the length of the shortest program that computes $$\nu$$. The Bayesian mixture $$\xi$$ under this particular prior is the *universal mixture*, written $$\xi_{U}$$. With this class the assumption $$\mu \in {\mathcal{M}}$$ reduces to "the universe is computable": as weak an assumption as one can make. For technical details on Kolmogorov complexity, see (Hutter et al. 2024, §2.7).

The class of all computable measures is countable but not enumerable (by the halting problem, you can't decide which Turing machines define total functions), so one can't even formally write $$\sum_{\nu \in {\mathcal{M}}}\ldots$$, as the decision problem of determining if $$\nu \overset{?}{\in}{\mathcal{M}}$$ is undecidable. A faithful construction of $$\xi_{U}$$ requires expanding $${\mathcal{M}}$$ to all *lower-semicomputable semimeasures* (Levin), at which point $$\xi_{U}$$ becomes a semimeasure rather than a measure: $$\sum_{x} \xi_{U}(x) \leq 1$$ instead of $$=1$$, conditionals may not sum to $$1$$, and every other proof in this sheet gains a side-case. This also gives the nice benefit that $$\xi \in \mathcal{M}$$.

We dodge all of this: $${\mathcal{M}}$$ is just *some* countable set of proper measures with $$\mu \in {\mathcal{M}}$$, and we assume $$K(\nu)$$ is defined for each $$\nu \in {\mathcal{M}}$$ when we need it. We never need $$\xi$$ itself to be in $${\mathcal{M}}$$, nor do we need its computability, so we don't ask. See (Hutter 2005, §2.4.3) for the full Levin construction.

\## D. Best choice of $$\hat{\mu}\in {\mathcal{M}}$$.

The bound is valid for every $$\hat\mu \in {\mathcal{M}}$$. A tempting question: which $$\hat\mu$$ gives the tightest bound? The answer is genuinely setting-dependent.

*Finite horizon $$n$$.* The minimizer of the RHS is

$$
\hat\mu_{n} ~:=~ \arg\min_{\nu \in {\mathcal{M}}}\Bigl\{ -\ln w_{\nu} \;+\; D_{n}(\mu \parallel \nu) \Bigr\}.
$$

This is well-defined (finitely many terms, attained when $${\mathcal{M}}$$ is finite), but the answer depends on $$n$$: for small $$n$$ the prior term dominates and a high-prior coarse model wins; for large $$n$$ the fit term dominates and the best per-step approximator wins. Both regimes are correct.

*Asymptotic rate.* A horizon-free analogue minimizes the per-step KL rate

$$
\lim_{n \to \infty}\frac{1}{n}\sum_{t \leq n}d_{t}(\mu \parallel \nu).
$$

This is the right notion when one cares about the linear-growth slope of the bound. But it has two drawbacks: the limit need not exist for non-stationary $$\mu$$ (one can substitute $$\liminf$$ but at the cost of clarity), and it discards the prior $$w_{\nu}$$ entirely, so the minimizer is not the same as $$\hat\mu_{n}$$ at any finite $$n$$, since only the slope is minimized.

*Stationary $$\mu$$.* The per-step KLs $$d_{t}(\mu \parallel \nu)$$ are constant in $$t$$, so all three notions essentially agree: $$\hat\mu = \arg\min_{\nu \in {\mathcal{M}}}D_{\text{KL}}(\mu \,\|\, \nu)$$, where the KL is taken under the (common) one-step conditional law. This is the case where "$$\hat\mu$$ = projection of $$\mu$$ onto $${\mathcal{M}}$$ in KL" has unambiguous meaning.

*Upshot.* The bound holds for all $$\hat\mu \in {\mathcal{M}}$$, and one is free to take the infimum on the RHS over $$\hat\mu$$. Which $$\hat\mu$$ actually attains that infimum is a separate question whose answer depends on horizon, prior, and any structural assumptions on $$\mu$$.

\## References

T. M. Cover and J. A. Thomas (2006). *Elements of Information Theory*. Wiley-Interscience.

Marcus Hutter (2005). [*Universal Artificial Intelligence: Sequential Decisions based on Algorithmic Probability*](http://www.hutter1.net/ai/uaibook.htm). Springer.

Marcus Hutter, David Quarel, and Elliot Catt (2024). [*An Introduction to Universal Artificial Intelligence*](http://www.hutter1.net/ai/uaibook2.htm). Chapman & Hall.

D. E. Knuth (1973). *The Art of Computer Programming, Volume I: Fundamental Algorithms*. Addison-Wesley.
