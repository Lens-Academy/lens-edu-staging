---
id: '9cba0d15-655b-41a9-80cd-00e2f2a8c06a'
title: "D.3.1.3 KL divergence and mixture dominance"
tldr: "Defines cumulative and per-step KL divergence and shows the joint KL splits into a sum of per-step KLs, then shows the mixture assigns at least prior times each environment's probability."
summary_for_tutor: "Sections 2 and 3 of Iliad worksheet D.3.1. Definition 2.1 (cumulative KL D_n and per-step KL d_t), Theorem 2.2 (KL is non-negative, proof in Appendix B), Exercise 2.1 (telescoping KL by induction) and Exercise 3.1 (mixture dominance xi(x) >= w_nu nu(x)), plus a remark on the Solomonoff prior w_nu = 2^{-K(nu)}. Hints and collapsed solutions are given. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/agency/solomonoff-induction/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 2. KL divergence

The KL divergence between two joint distributions over a length-$n$ history splits, by an inductive application of the chain rule for probabilities, into a sum of per-step conditional KLs. This telescoping identity lets us trade a single joint KL over an entire history for a sum of per-step KLs (and vice versa): exactly the bridge we will need in Section 4.

We introduce two pieces of notation that will be used throughout the rest of the worksheet:

:::callout {title="Definition" tone="blue"}

**Definition 2.1 (Cumulative and per-step KL).** For environments / predictors $\nu, \rho$, horizon $n \geq 1$, and $1 \leq t \leq n$, the **cumulative joint KL** and the **expected per-step KL at step $t$** are

$$
\begin{aligned}D_{n}(\nu \parallel \rho) ~&:=~ \sum_{x_{1:n} \in \mathbb{B}^n}\nu(x_{1:n}) \,\ln \frac{\nu(x_{1:n})}{\rho(x_{1:n})}, \\[6pt] d_{t}(\nu \parallel \rho) ~&:=~ \sum_{x_{<t} \in \mathbb{B}^{t-1}}\nu(x_{<t}) \sum_{x_t \in \mathbb{B}}\nu(x_{t} \mid x_{<t}) \,\ln \frac{\nu(x_{t} \mid x_{<t})}{\rho(x_{t} \mid x_{<t})},\end{aligned}
$$

with the conventions $0 \ln \tfrac{0}{q}:= 0$ for $q \geq 0$ and $p \ln \tfrac{p}{0}:= \infty$ for $p > 0$.

We write $D_{\infty}(\nu \parallel \rho) := \lim_{t \to \infty}D_{t}(\nu \parallel \rho)$ and $D^{\mu}_{\infty} := D_{\infty}(\mu \parallel \xi)$.

:::

:::callout {title="Theorem" tone="green"}

**Theorem 2.2 (KL divergence is non-negative).** For any environments $\nu, \rho$ and any horizon $n \geq 1$ and step $1 \leq t \leq n$:

**(a)** $D_{n}(\nu \parallel \rho) \geq 0$, with equality iff $\nu(x_{1:n}) = \rho(x_{1:n})$ for every $x_{1:n}\in \mathbb{B}^{n}$ with $\nu(x_{1:n}) > 0$.

**(b)** $d_{t}(\nu \parallel \rho) \geq 0$, with equality iff $\nu(x_{t} \mid x_{<t}) = \rho(x_{t} \mid x_{<t})$ for every $x_{<t}$ with $\nu(x_{<t}) > 0$ and every $x_{t} \in \mathbb{B}$.

Proof in Appendix B.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 2.1 (Telescoping KL) [10].** Show by induction on $n$ that for all environments $\nu, \rho$,

$$
D_{n}(\nu \parallel \rho) ~=~ \sum_{t=1}^{n}d_{t}(\nu \parallel \rho),
$$

where on the right-hand side, the $t=1$ summand uses the conventions $\nu(x_{1} \mid x_{<1}) := \nu(x_{1})$, $\rho(x_{1} \mid x_{<1}) := \rho(x_{1})$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

For the induction step, factor $\nu(x_{1:n}) = \nu(x_{<n})\,\nu(x_{n} \mid x_{<n})$ (and likewise for $\rho$) inside the log; the log splits additively into two pieces matching $D_{n-1}(\nu \parallel \rho)$ and $d_{n}(\nu \parallel \rho)$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By induction on $n$.

**Base case ($n = 1$):**

$$
D_{1}(\nu \parallel \rho) ~=~ \sum_{x_1}\nu(x_{1}) \ln \frac{\nu(x_{1})}{\rho(x_{1})}~=~ d_{1}(\nu \parallel \rho),
$$

using $\nu(x_{1} \mid x_{<1}) := \nu(x_{1})$ and likewise for $\rho$.

**Induction step.** Apply the chain rule for probabilities (Definition 1.1) inside the log: $\nu(x_{1:n}) = \nu(x_{<n})\,\nu(x_{n} \mid x_{<n})$, and similarly for $\rho$. The log splits additively:

$$
\begin{aligned}&D_{n}(\nu \parallel \rho) \\ ~&=~ \sum_{x_{1:n} \in \mathbb{B}^n}\nu(x_{1:n}) \,\ln \frac{\nu(x_{1:n})}{\rho(x_{1:n})}\\ ~&=~ \sum_{x_{1:n}}\nu(x_{n} \mid x_{<n}) \nu(x_{<n}) \,\ln \frac{\nu(x_{n} \mid x_{<n})\,\nu(x_{<n})}{\rho(x_{n} \mid x_{<n})\,\rho(x_{<n})}\\ ~&=~ \sum_{x_{1:n}}\nu(x_{n} \mid x_{<n}) \nu(x_{<n}) \left[\ln \frac{\nu(x_{n} \mid x_{<n})}{\rho(x_{n} \mid x_{<n})}~+~ \ln \frac{\nu(x_{<n})}{\rho(x_{<n})}\right]. \\ ~&=~ \underbrace{\sum_{x_{<n}} \nu(x_{<n}) \sum_{x_n} \nu(x_n \mid x_{<n}) \ln \frac{\nu(x_{n} \mid x_{<n})}{\rho(x_{n} \mid x_{<n})} }_{d_n(\nu \parallel \rho)}\\&\qquad ~+~ \sum_{x_{1:n}}\nu(x_{n} \mid x_{<n}) \nu(x_{<n}) \ln \frac{\nu(x_{<n})}{\rho(x_{<n})}\\ ~&=~ d_{n}(\nu \parallel \rho) ~+~ \underbrace{\sum_{x_{<n}} \nu(x_{<n}) \ln \frac{\nu(x_{<n})}{\rho(x_{<n})}}_{D_{n-1}(\nu \parallel \rho)}\cancel{\sum_{x_n} \nu(x_n \mid x_{<n})}\\ ~&=~ d_{n}(\nu \parallel \rho) + D_{n-1}(\nu \parallel \rho) ~=~ d_{n}(\nu \parallel \rho) + \sum_{t=1}^{n-1}d_{t}(\nu \parallel \rho) = \sum_{t=1}^{n}d_{t}(\nu \parallel \rho)\end{aligned}
$$

:::

\## 3. Mixture dominance

The mixture $\xi$ never assigns much less probability than any single environment weighted by its prior. This single inequality is the engine behind the cumulative bound of Section 4 below: dividing through gives $\mu(x)/\xi(x) \leq 1/w_{\mu}$, which is then fed into Pinsker and the chain rule in the proof of the main cumulative bound.

:::callout {title="Exercise" tone="amber"}
**Exercise 3.1 (Mixture dominance) [05].** Show that for every $\nu \in {\mathcal{M}}$ and every $x \in \mathbb{B}^{*}$,

$$
\xi(x) ~\geq~ w_{\nu} \cdot \nu(x).
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Definition 1.2, $\xi(x) = \sum_{\nu' \in {\mathcal{M}}}w_{\nu'}\,\nu'(x)$. Every term in this sum is non-negative, so dropping all terms except the one with $\nu' = \nu$ can only decrease the sum:

$$
\xi(x) ~=~ \sum_{\nu' \in {\mathcal{M}}}w_{\nu'}\, \nu'(x) ~\geq~ w_{\nu}\, \nu(x).
$$

:::

:::callout {title="Note" tone="blue"}

**Remark (Solomonoff specialization).** Under the Solomonoff prior, $w_{\nu} = 2^{-K(\nu)}$, so the bound becomes

$$
\xi_{U}(x) ~\geq~ 2^{-K(\nu)}\cdot \nu(x) \qquad \text{for every computable }\nu.
$$

This is what makes $\xi_{U}$ *universal*: a single predictor dominates the entire computable model class up to a factor that depends only on the model's description length.

:::
