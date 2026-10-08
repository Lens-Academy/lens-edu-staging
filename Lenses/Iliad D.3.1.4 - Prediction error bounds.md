---
id: 'f96b33cc-fff2-4d6a-bca0-b875d9c5da30'
title: "D.3.1.4 Prediction error bounds"
tldr: "Proves that the mixture's total expected squared prediction error is at most -ln of the prior weight on the truth, and that it makes boundedly many mistakes on a deterministic truth."
summary_for_tutor: "Sections 4 and 5 of worksheet D.3.1. Pinsker's inequality (Theorem 4.1, proved in Appendix A), Definition 4.2 (S_n and s_t), Exercises 4.1 (S_infinity <= -ln w_mu), 4.2 (K(mu) ln 2 for the Solomonoff prior), 4.3 (per-step error tends to 0), and Exercise 5.1 (the threshold predictor makes at most -2 ln w_mu mistakes on a deterministic mu). Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/agency/solomonoff-induction/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 4. Cumulative prediction error bound (main result)

The next ingredient relates squared prediction error to KL divergence (Cover & Thomas 2006, Lemma 11.6.1). We require the following inequality:

:::callout {title="Theorem" tone="green"}

**Theorem 4.1 (Pinsker's inequality).** Let $P$ and $Q$ be probability distributions over $\mathbb{B}= \{\texttt{0}, \texttt{1}\}$, i.e., $p_{0}, p_{1}, q_{0}, q_{1} \geq 0$ with $p_{0} + p_{1} = 1$ and $q_{0} + q_{1} = 1$. Write $p_{x} = P(x)$ and $q_{x} = Q(x)$. Then

$$
\sum_{x \in \mathbb{B}}\big( q_{x} - p_{x} \big)^{2} \;\leq\; \sum_{x \in \mathbb{B}}p_{x} \ln \frac{p_{x}}{q_{x}}. \tag{$\star$}
$$

:::
The proof of this inequality is mostly tedious algebra but is included in Appendix A.

:::callout {title="Definition" tone="blue"}

**Definition 4.2 (Cumulative expected and per-step squared prediction error).** For environments / predictors $\nu, \rho$ and horizon $n \geq 1$, the **cumulative expected squared error** and the **per-step squared error at step $t$** are

$$
\begin{aligned}S_{n}(\nu \parallel \rho)~&:=~ \sum_{t=1}^{n} s_{t}(\nu \parallel \rho) \\ s_{t}(\nu \parallel \rho) ~&:=~ \sum_{x_{<t} \in \mathbb{B}^{t-1}}\nu(x_{<t}) \sum_{x_t \in \mathbb{B}}\bigl(\nu(x_{t} \mid x_{<t}) - \rho(x_{t} \mid x_{<t})\bigr)^{2}\end{aligned}
$$

Write $S_{\infty}(\nu \parallel \rho) := \lim_{n \to \infty}S_{n}(\nu \parallel \rho)$ and $S_{\infty}^{\mu} := S_{\infty}(\mu \parallel \xi)$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 4.1 (Cumulative prediction bound) [15].** Show that

$$
S_{\infty}^{\mu}\leq - \ln w_{\mu}.
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

You need Theorem 4.1, Exercise 2.1 and Exercise 3.1.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The proof is a three-step chain:

$$
S^{\mu}_{\infty} ~\stackrel{(1)}{\leq}~ D^{\mu}_{\infty} ~\stackrel{(2)}{\leq}~ \lim_{n \to \infty}\sum_{x_{1:n}}\mu(x_{1:n}) \,\ln \tfrac{1}{w_\mu}~\stackrel{(3)}{=}~ -\ln w_{\mu}.
$$

*Step (1): Pinsker, pointwise.* For each $t$ and $x_{<t}$, both $\mu(\cdot \mid x_{<t})$ and $\xi(\cdot \mid x_{<t})$ are probability distributions on $\mathbb{B}$ ($\xi$ by Exercise 1.2), so Theorem 4.1 gives

$$
\sum_{x_t}\bigl(\xi(x_{t} \mid x_{<t}) - \mu(x_{t} \mid x_{<t})\bigr)^{2} \leq \sum_{x_t}\mu(x_{t} \mid x_{<t}) \,\ln \tfrac{\mu(x_t \mid x_{<t})}{\xi(x_t \mid x_{<t})}.
$$

Multiplying by $\mu(x_{<t}) \geq 0$ and summing over $x_{<t}$ gives $s_{t}(\mu \parallel \xi) \leq d_{t}(\mu \parallel \xi)$, so $S_{t}(\mu \parallel \xi) \leq \sum_{i=1}^{t} d_{i}(\mu \parallel \xi) = D_{t}(\mu \parallel \xi)$ (Exercise 2.1), from which we take $t \to \infty$.

*Step (2): Mixture dominance.* By Exercise 3.1, $\xi(x_{1:n}) \geq w_{\mu}\, \mu(x_{1:n})$, so $\mu(x_{1:n}) / \xi(x_{1:n}) \leq 1/w_{\mu}$, hence $\ln(\mu/\xi) \leq \ln(1/w_{\mu})$ pointwise. Substituting into the definition $D_{n}(\mu \parallel \xi) = \sum_{x_{1:n}}\mu(x_{1:n}) \ln(\mu/\xi)$ gives the bound.

*Step (3): Total mass.* Pull the constant out and use $\sum_{x_{1:n}}\mu(x_{1:n}) = 1$ ($\mu$ is an environment).

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.2 (Explicit complexity bound) [05].** Specialize Section 4 to the **Solomonoff prior** $w_{\nu} = 2^{-K(\nu)}$ (where $K(\nu)$ is the length of the shortest program computing $\nu$) to show

$$
S_{\infty}^{\mu}\leq K(\mu) \ln 2.
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Section 4, for *any* prior, $S_{\infty}^{\mu}\leq -\ln w_{\mu}$. The Solomonoff prior assigns $\mu$ the weight $w_{\mu} = 2^{-K(\mu)}$, so

$$
S_{\infty}^{\mu}~\leq~ -\ln w_{\mu} ~=~ -\ln 2^{-K(\mu)}~=~ K(\mu) \ln 2.
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.3 (Per-step error) [05].** Hence prove that the per-step expected prediction error

$$
s_{t} := \sum_{x_{<t} \in \mathbb{B}^{t-1}}\mu(x_{<t}) \sum_{x_t \in \mathbb{B}}\big( \xi(x_{t} \mid x_{<t}) - \mu(x_{t} \mid x_{<t}) \big)^{2}
$$

converges to zero as $t \to \infty$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Follows immediately as $\sum_{t=1}^{\infty} s_{t} \leq -\ln w_{\mu} < \infty$ implies $s_{t} \to 0$.

:::

\## 5. Bounded number of prediction mistakes

So far we have bounded *squared error*. For a deterministic environment (i.e. a single infinite binary sequence $x_{1}^{*}, x_{2}^{*}, \dots$ in ${\mathcal{M}}$), one can ask the sharper $0/1$-loss question: how often does the mixture predict the *wrong bit*? The cumulative bound is strong enough to give an answer.

Let $\mu \in {\mathcal{M}}$ be a deterministic environment, so $\mu(x_{t} \mid x_{<t}) \in \{0,1\}$ on every history; write $x_{t}^{*}$ for the unique bit on which $\mu(\cdot \mid x^{*}_{<t})$ puts all its mass. Define the **threshold predictor** associated with $\xi$: at each step, predict the more-likely bit,

$$
\hat{x}_{t} ~:=~ \arg\max_{x \in \mathbb{B}}\xi(x \mid x_{<t}) \qquad \text{(break ties arbitrarily).}
$$

We say the mixture makes a **mistake** at time $t$ if $\hat{x}_{t} \neq x_{t}^{*}$.

::::callout {title="Exercise" tone="amber"}
**Exercise 5.1 (Bounded prediction mistakes) [15].** Show that the number of mistakes made by the threshold predictor on the $\mu$-trajectory is at most

$$
\#\{\, t \geq 1 \;:\; \hat{x}_{t} \neq x_{t}^{*} \,\} ~\leq~ -2 \ln w_{\mu}.
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

At a mistake step, $\xi(x_{t}^{*} \mid x_{<t}) \leq \tfrac{1}{2}$ (why?). The per-step squared error along the deterministic $\mu$-trajectory simplifies dramatically; bound it from below, then sum.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**Step 1: per-step squared error along the $\mu$-trajectory.** Because $\mu$ is deterministic, the outer sum over $x_{<t}$ in $s_{t}$ collapses onto the unique trajectory $x_{<t}^{*} := x_{1}^{*} \cdots x_{t-1}^{*}$, with weight $\mu(x_{<t}^{*}) = 1$. Write $\xi_{t} := \xi(x_{t}^{*} \mid x_{<t}^{*}) \in [0,1]$ for the mass the mixture places on the *correct* bit. Since $\mu$ assigns mass $1$ to $x_{t}^{*}$ and $0$ to the other bit,

$$
\begin{aligned}s_{t} ~&=~ \sum_{x_t \in \mathbb{B}}\big(\xi(x_{t} \mid x_{<t}^{*}) - \mu(x_{t} \mid x_{<t}^{*})\big)^{2} \\ ~&=~ (\xi_{t} - 1)^{2} + (1 - \xi_{t} - 0)^{2} ~=~ 2(1 - \xi_{t})^{2}.\end{aligned}
$$

**Step 2: a mistake step contributes at least $\tfrac{1}{2}$.** A mistake at time $t$ means $\hat{x}_{t} \neq x_{t}^{*}$, i.e. the threshold predictor chose the *other* bit. This requires $\xi(\hat{x}_{t} \mid x_{<t}^{*}) \geq \xi(x_{t}^{*} \mid x_{<t}^{*})$, i.e. $1 - \xi_{t} \geq \xi_{t}$, i.e. $\xi_{t} \leq \tfrac{1}{2}$. So at every mistake step,

$$
s_{t} ~=~ 2(1 - \xi_{t})^{2} ~\geq~ 2 \cdot \tfrac{1}{4}~=~ \tfrac{1}{2}.
$$

**Step 3: sum and apply the cumulative bound.** Let $N$ be the total number of mistakes. Summing $s_{t}$ over mistake steps (non-negative contributions from non-mistake steps only help):

$$
\tfrac{1}{2}\cdot N ~\leq~ \sum_{t \,:\, \hat{x}_t \neq x_t^*}s_{t} ~\leq~ \sum_{t=1}^{\infty} s_{t} ~=~ S^{\mu}_{\infty} ~\leq~ -\ln w_{\mu},
$$

where the last step is Section 4. Rearranging, $N \leq -2 \ln w_{\mu}$.

:::

:::callout {title="Note" tone="blue"}

**Remark (Solomonoff specialization).** Under the Solomonoff prior $w_{\mu} = 2^{-K(\mu)}$, so $-\ln w_{\mu} = K(\mu)\ln 2$ and the bound becomes

$$
\#\{\, t \geq 1 \;:\; \hat{x}_{t} \neq x_{t}^{*} \,\} ~\leq~ 2 K(\mu) \ln 2.
$$

With $\ln 2 \approx 0.693$ the constant is just under $1.4$, so if the true environment $\mu$ is computable, and can be described by a program at most $k$ bits long, then the predictor $\xi$ will make at worst $\approx 1.4 k$ mistakes over predicting the entire sequence $x^{*}_{1:\infty}$. Note that the bound is purely existence-style: it does not say *when* the mistakes happen. They could all occur at the start, or be arbitrarily far into the future.

:::
