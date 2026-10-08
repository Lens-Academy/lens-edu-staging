---
id: '3d35575a-44da-472a-9a42-ea5db0ce0045'
title: "D.3.1.2 The mixture is a predictor"
tldr: "Defines environments and the Bayesian mixture, and proves that the mixture gives a valid predictor whose posterior weights update multiplicatively."
summary_for_tutor: "Section 1 of worksheet D.3.1: The mixture is a predictor. Definitions 1.1 (environment) and 1.2 (Bayesian mixture xi with posterior weights w(nu|x_{<t})). Exercises 1.1 (generalized chain rule), 1.2 (the mixture's conditional is the posterior-weighted average and sums to 1), 1.3 (multiplicative posterior update by likelihood ratio) and 1.4 (multi-step posterior linearity), with hints and collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/agency/solomonoff-induction/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. The mixture is a predictor

:::callout {title="Definition" tone="blue"}

**Definition 1.1 (Environment).** An **environment** $\nu$ assigns to each history $x_{<t}\in \mathbb{B}^{*}$ a predictive distribution $\nu(\cdot \mid x_{<t}) \in \Delta \mathbb{B}$ over the next symbol. The conditional joint probability of a string $x \in \mathbb{B}^{*}$, conditioned on $y \in \mathbb{B}^{*}$, is defined as

$$
\nu(x_{1:n}| y) ~:=~ \prod_{t=1}^{n}\nu(x_{t} \mid y x_{<t}), \qquad \nu(\epsilon) := 1.
$$

The unconditional joint is defined as $\nu(x_{1:n}) := \nu(x_{1:n}\mid \epsilon)$. The true (unknown) environment generating the data is denoted $\mu$.

:::

:::callout {title="Note" tone="blue"}

**Remark.** One can show that $\nu(x_{1:t}) = \nu(x_{<t}) \cdot \nu(x_{t} \mid x_{<t})$ and $\nu(x) = \nu(x\texttt{0}) + \nu(x\texttt{1})$ for all $x \in \mathbb{B}^{*}$.

:::

:::callout {title="Definition" tone="blue"}

**Definition 1.2 (Bayesian mixture $\xi$).** Let ${\mathcal{M}} = \{\nu_{1}, \nu_{2}, \dots\}$ be a countable class of environments with prior weights $w_{\nu} > 0$ satisfying $\sum_{\nu \in {\mathcal{M}}}w_{\nu} = 1$. The **Bayesian mixture** is defined as a prior-weighted mixture over all environments $\nu$ in ${\mathcal{M}}$:

$$
\xi(x_{1:t}) ~:=~ \sum_{\nu \in {\mathcal{M}}}w_{\nu}\, \nu(x_{1:t}).
$$

Its one-step predictive distribution is

$$
\xi(x_{t} \mid x_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t})\, \nu(x_{t} \mid x_{<t}),
$$

with posterior weights

$$
w(\nu \mid x_{<t}) ~:=~ w_{\nu}\, \frac{\nu(x_{<t})}{\xi(x_{<t})}\qquad w(\nu \mid \epsilon) := w_{\nu}.
$$

Here $w(\nu \mid x_{<t})$ is the *posterior* belief in $\nu$ after observing $x_{<t}$.

:::

The mixture $\xi$ is defined as a sum of *joint* probabilities. To use it as a predictor we need its one-step conditional $\xi(x_{t} \mid x_{<t})$, and we need to know it is a genuine probability distribution (so that, later, Pinsker's inequality applies to it).

:::callout {title="Exercise" tone="amber"}
**Exercise 1.1 (Generalized chain rule) [05].** The two-term chain rule baked into Definition 1.1 extends to arbitrary contiguous blocks. Show that for any $1 \leq p \leq q \leq r$ and any history $x_{<p}$ with $\nu(x_{<p}) > 0$,

$$
\nu(x_{p:r}\mid x_{<p}) ~=~ \nu(x_{p:q}\mid x_{<p}) \cdot \nu(x_{q+1:r}\mid x_{<p}\, x_{p:q}).
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Expand the conditional as a ratio of joints; the chain rule (Definition 1.1) telescopes the ratio to a product over indices $k = p, \ldots, r$:

$$
\nu(x_{p:r}\mid x_{<p}) ~=~ \frac{\nu(x_{1:r})}{\nu(x_{<p})}~=~ \frac{\prod_{k=1}^{r}\nu(x_{k} \mid x_{<k})}{\prod_{k=1}^{p-1}\nu(x_{k} \mid x_{<k})}~=~ \prod_{k=p}^{r}\nu(x_{k} \mid x_{<k}).
$$

For any $k \geq p$, the past $x_{<k}$ is just $x_{<p}$ extended by $x_{p:k-1}$, so the same expansion identifies every contiguous sub-block as a conditional with the right history. Splitting the product at index $q$:

$$
\nu(x_{p:r}\mid x_{<p}) ~=~ \underbrace{\prod_{k=p}^{q} \nu(x_k \mid x_{<k})}_{=\,\nu(x_{p:q}\,\mid\,x_{<p})}\;\cdot\; \underbrace{\prod_{k=q+1}^{r} \nu(x_k \mid x_{<k})}_{=\,\nu(x_{q+1:r}\,\mid\,x_{<p}\, x_{p:q})}.
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 1.2 (Mixture is a predictor) [10].** Starting from $\xi(x_{1:t}) = \sum_{\nu \in {\mathcal{M}}}w_{\nu}\, \nu(x_{1:t})$, show that

$$
\xi(x_{t} \mid x_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t})\, \nu(x_{t} \mid x_{<t}), \qquad w(\nu \mid x_{<t}) := w_{\nu}\, \frac{\nu(x_{<t})}{\xi(x_{<t})},
$$

and conclude that $\sum_{x_t \in \mathbb{B}}\xi(x_{t} \mid x_{<t}) = 1$, i.e. $\xi(\cdot \mid x_{<t})$ is a probability distribution over $\mathbb{B}$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Write $\xi(x_{t} \mid x_{<t}) = \xi(x_{1:t}) / \xi(x_{<t})$, expand the numerator, and use the chain rule $\nu(x_{1:t}) = \nu(x_{<t})\, \nu(x_{t} \mid x_{<t})$ (Definition 1.1). For the last part, note that the posterior weights sum to $1$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The one-step conditional is the ratio of joint to marginal, $\xi(x_{t} \mid x_{<t}) := \xi(x_{1:t}) / \xi(x_{<t})$. Expanding the numerator and applying the chain rule $\nu(x_{1:t}) = \nu(x_{<t})\, \nu(x_{t} \mid x_{<t})$ to each term:

$$
\begin{aligned}\xi(x_{t} \mid x_{<t}) ~&=~ \frac{\sum_{\nu \in {\mathcal{M}}}w_{\nu}\, \nu(x_{1:t})}{\xi(x_{<t})}~=~ \frac{\sum_{\nu \in {\mathcal{M}}}w_{\nu}\, \nu(x_{<t})\, \nu(x_{t} \mid x_{<t})}{\xi(x_{<t})}\\ ~&=~ \sum_{\nu \in {\mathcal{M}}}\underbrace{\frac{w_{\nu}\, \nu(x_{<t})}{\xi(x_{<t})}}_{=\, w(\nu \mid x_{<t})}\, \nu(x_{t} \mid x_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t})\, \nu(x_{t} \mid x_{<t}).\end{aligned}
$$

The posterior weights are non-negative and sum to $1$:

$$
\sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t}) ~=~ \frac{\sum_{\nu \in {\mathcal{M}}}w_{\nu}\, \nu(x_{<t})}{\xi(x_{<t})}~=~ \frac{\xi(x_{<t})}{\xi(x_{<t})}~=~ 1.
$$

Therefore $\xi(\cdot \mid x_{<t})$ is a convex combination of the probability distributions $\nu(\cdot \mid x_{<t})$, so it is itself a probability distribution over $\mathbb{B}$:

$$
\sum_{x_t \in \mathbb{B}}\xi(x_{t} \mid x_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t}) \underbrace{\sum_{x_t \in \mathbb{B}} \nu(x_t \mid x_{<t})}_{=\, 1}~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t}) ~=~ 1.
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.3 (Posterior update) [10].** Show that the posterior weight $w(\cdot \mid \cdot)$ updates *multiplicatively* as new symbols arrive. For every $x_{1:t}\in \mathbb{B}^{*}$ with $\xi(x_{1:t}) > 0$,

$$
w(\nu \mid x_{1:t}) ~=~ w(\nu \mid x_{<t}) \cdot \frac{\nu(x_{t} \mid x_{<t})}{\xi(x_{t} \mid x_{<t})}.
$$

That is: the new posterior equals the old posterior, scaled by the **likelihood ratio** of how well $\nu$ predicted the just-observed symbol relative to the mixture's own prediction.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Definition 1.2,

$$
w(\nu \mid x_{1:t}) ~=~ w_{\nu} \,\frac{\nu(x_{1:t})}{\xi(x_{1:t})}, \qquad w(\nu \mid x_{<t}) ~=~ w_{\nu} \,\frac{\nu(x_{<t})}{\xi(x_{<t})}.
$$

Apply the chain rule (Definition 1.1) to both $\nu$ and $\xi$: $\nu(x_{1:t}) = \nu(x_{<t})\,\nu(x_{t} \mid x_{<t})$ and $\xi(x_{1:t}) = \xi(x_{<t})\,\xi(x_{t} \mid x_{<t})$. Dividing,

$$
\frac{w(\nu \mid x_{1:t})}{w(\nu \mid x_{<t})}~=~ \frac{\nu(x_{1:t})}{\nu(x_{<t})}\cdot \frac{\xi(x_{<t})}{\xi(x_{1:t})}~=~ \frac{\nu(x_{t} \mid x_{<t})}{\xi(x_{t} \mid x_{<t})}.
$$

Rearranging gives the claim.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 1.4 (Multi-step posterior linearity) [10].** Exercise 1.2 showed that $\xi$'s one-step prediction $\xi(x_{t} \mid x_{<t})$ is the posterior-weighted average of the per-model one-step predictions. The same identity extends to predictions over a *whole future segment* $x_{t:m}$: for any $t \leq m$,

$$
\xi(x_{t:m}\mid x_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t})\, \nu(x_{t:m}\mid x_{<t}).
$$

That is: the *same* posterior $w(\nu \mid x_{<t})$ governs $\xi$'s predictions for arbitrarily many steps into the future, not just the next one. Show this.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Write $\xi(x_{t:m}\mid x_{<t}) = \xi(x_{1:m}) / \xi(x_{<t})$, expand the numerator using the mixture definition, and apply the generalized chain rule (Exercise 1.1 with $p=1$, $q=t-1$, $r=m$) to factor each $\nu(x_{1:m}) = \nu(x_{<t})\,\nu(x_{t:m}\mid x_{<t})$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By definition of the conditional and the mixture form $\xi(x_{1:m}) = \sum_{\nu} w_{\nu} \nu(x_{1:m})$ (Definition 1.2),

$$
\xi(x_{t:m}\mid x_{<t}) ~=~ \frac{\xi(x_{1:m})}{\xi(x_{<t})}~=~ \frac{\sum_{\nu} w_{\nu}\, \nu(x_{1:m})}{\xi(x_{<t})}.
$$

The generalized chain rule (Exercise 1.1 with $p=1$, $q=t-1$, $r=m$) gives $\nu(x_{1:m}) = \nu(x_{<t})\,\nu(x_{t:m}\mid x_{<t})$. Substituting,

$$
\begin{aligned}\xi(x_{t:m}\mid x_{<t}) ~&=~ \sum_{\nu} \underbrace{\frac{w_{\nu}\, \nu(x_{<t})}{\xi(x_{<t})}}_{=\, w(\nu \mid x_{<t})}\, \nu(x_{t:m}\mid x_{<t}) \\ ~&=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t})\, \nu(x_{t:m}\mid x_{<t}). \end{aligned}
$$

:::
