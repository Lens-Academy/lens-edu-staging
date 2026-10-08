---
id: '8a23db64-2995-4c9f-ae45-9f72d795399d'
title: "D.3.2.5 Dominance and properties of the value function"
tldr: "Shows the mixture dominates each environment, that the mixture's policy value is a posterior-weighted average of values, and that the optimal mixture value is convex but not linear."
summary_for_tutor: "Sections 3 and 4 of Iliad worksheet D.3.2: Dominance of the Bayesian mixture and properties of V_xi. Exercises 3.1-3.2 (xi(ae) >= w_nu nu(ae) and xi^pi >= w_nu nu^pi), 4.1 (V_xi^{pi,m} = sum w(nu|ae) V_nu^{pi,m}), 4.2 (infinite-horizon linearity, using dominated convergence for sums, Fact 4.1), 4.3 (V_xi^* is convex) and 4.4 (a two-coin example where it is strictly less). Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 3. Dominance of the Bayesian Mixture

:::callout {title="Exercise" tone="amber"}
**Exercise 3.1 [03].** Show that $\xi({\text{\ae}}_{<t}) \geq w_{\nu} \cdot \nu({\text{\ae}}_{<t})$ for every $\nu \in {\mathcal{M}}$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

$\xi({\text{\ae}}_{<t}) = \sum_{\nu' \in {\mathcal{M}}}w_{\nu'}\nu'({\text{\ae}}_{<t}) \geq w_{\nu} \nu({\text{\ae}}_{<t})$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.2 [10].** Conclude that $\xi^{\pi}({\text{\ae}}_{1:m}) \geq w_{\nu} \cdot \nu^{\pi}({\text{\ae}}_{1:m})$ for any $\nu \in {\mathcal{M}}$ and any policy $\pi$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Exercise 0.1: $\xi^{\pi}({\text{\ae}}_{1:m}) = \pi({\text{\ae}}_{1:m}) \cdot \xi({\text{\ae}}_{1:m}) \geq \pi({\text{\ae}}_{1:m}) \cdot w_{\nu} \nu({\text{\ae}}_{1:m}) = w_{\nu} \cdot \nu^{\pi}({\text{\ae}}_{1:m})$.

:::

\## 4. Properties of $V_{\xi}$

::::callout {title="Exercise" tone="amber"}
**Exercise 4.1 [15].** Show that for finite $m$:

$$
V_{\xi}^{\pi,m}({\text{\ae}}_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\pi,m}({\text{\ae}}_{<t}).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Use the multi-step posterior linearity of $\xi^{\pi}$ (Exercise 1.4).

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Exercise 1.4: $\xi^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) = \sum_{\nu} w(\nu \mid {\text{\ae}}_{<t})\, \nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t})$. Multiply both sides by $(1-\gamma)G_{t-1:m}$ and sum over all ${\text{\ae}}_{t:m}$:

$$
\begin{aligned}V_{\xi}^{\pi,m}({\text{\ae}}_{<t}) ~&=~ (1-\gamma) \sum_{{\text{\ae}}_{t:m}}\xi^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) G_{t-1:m}\\ ~&=~ (1-\gamma) \sum_{{\text{\ae}}_{t:m}}\left[\sum_{\nu} w(\nu \mid {\text{\ae}}_{<t})\, \nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t})\right] G_{t-1:m}\\ ~&=~ \sum_{\nu} w(\nu \mid {\text{\ae}}_{<t}) \underbrace{(1-\gamma) \sum_{{\text{\ae}}_{t:m}} \nu^\pi({\text{\ae}}_{t:m} \mid {\text{\ae}}_{<t}) G_{t-1:m}}_{=\; V_\nu^{\pi,m}({\text{\ae}}_{<t})}.\end{aligned}
$$

In the last step we exchanged $\sum_{{\text{\ae}}_{t:m}}$ and $\sum_{\nu}$; this is valid because both are sums of non-negative terms (or, for finite $m$, the sum over ${\text{\ae}}_{t:m}$ is finite). So:

$$
V_{\xi}^{\pi,m}({\text{\ae}}_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\pi,m}({\text{\ae}}_{<t}).
$$

:::

:::callout {title="Note" tone="blue"}

**Fact 4.1 (Dominated convergence for sums).** If $a_{\nu,m}\to a_{\nu}$ as $m \to \infty$ for each $\nu$, and $|a_{\nu,m}| \leq b_{\nu}$ for all $m$ with $\sum_{\nu} b_{\nu} < \infty$, then $\sum_{\nu} a_{\nu,m}\to \sum_{\nu} a_{\nu}$. (For finite sums this is trivial.)

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 4.2 (∗) (Infinite-horizon linearity) [17].** Show that the result extends to $m = \infty$:

$$
V_{\xi}^{\pi}({\text{\ae}}_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\pi}({\text{\ae}}_{<t}).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Take $m \to \infty$ in the finite-horizon result. You will need Fact 4.1 to exchange limit and sum for countably infinite ${\mathcal{M}}$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The left side converges: $V_{\xi}^{\pi,m}({\text{\ae}}_{<t}) \to V_{\xi}^{\pi}({\text{\ae}}_{<t})$ by definition.

For the right side, we need to push $\lim_{m \to \infty}$ through $\sum_{\nu}$. If ${\mathcal{M}}$ is finite this is immediate. For countably infinite ${\mathcal{M}}$, we apply Fact 4.1 (dominated convergence for sums):

- For each $\nu$: $a_{\nu,m}:= w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) \to w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\pi}({\text{\ae}}_{<t})$ as $m \to \infty$ by definition.
- Domination: $|a_{\nu,m}| \leq w(\nu \mid {\text{\ae}}_{<t}) \cdot 1 =: b_{\nu}$ for all $m$, since $V_{\nu}^{\pi,m}\in [0,1]$ (Exercise 1.3).
- Summability: $\sum_{\nu} b_{\nu} = \sum_{\nu} w(\nu \mid {\text{\ae}}_{<t}) = 1 < \infty$.

So Fact 4.1 gives:

$$
V_{\xi}^{\pi}({\text{\ae}}_{<t}) ~=~ \lim_{m \to \infty}\sum_{\nu} w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) ~=~ \sum_{\nu} w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\pi}({\text{\ae}}_{<t}).
$$

:::

Exercise 4.1 shows $V_{\xi}^{\pi}$ is linear in $\nu$. The optimal value $V_{\xi}^{*}$ is only convex: a single policy must perform well across all $\nu \in {\mathcal{M}}$ simultaneously, rather than being tailored to each $\nu$ individually.

::::callout {title="Exercise" tone="amber"}
**Exercise 4.3 (∗) [10].** (Convexity of $V_{\xi}^{*}$) Using Exercise 4.1, show that for finite $m$:

$$
V_{\xi}^{*,m}({\text{\ae}}_{<t}) ~\leq~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{*,m}({\text{\ae}}_{<t}).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Apply Exercise 4.1 with $\pi = \pi_{\xi}^{*}$, the Bayes-optimal policy for $\xi$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Exercise 2.3, a deterministic Bayes-optimal policy $\pi_{\xi}^{*}$ exists with $V_{\xi}^{\pi_\xi^*,m}= V_{\xi}^{*,m}$. Applying Exercise 4.1 with $\pi = \pi_{\xi}^{*}$:

$$
V_{\xi}^{*,m}({\text{\ae}}_{<t}) ~=~ V_{\xi}^{\pi_\xi^*,m}({\text{\ae}}_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\pi_\xi^*,m}({\text{\ae}}_{<t}).
$$

Since $\pi_{\xi}^{*}$ is optimal for $\xi$ but not necessarily for each individual $\nu$, we have $V_{\nu}^{\pi_\xi^*,m}({\text{\ae}}_{<t}) \leq V_{\nu}^{*,m}({\text{\ae}}_{<t})$ for each $\nu$. Since $w(\nu \mid {\text{\ae}}_{<t}) \geq 0$:

$$
V_{\xi}^{*,m}({\text{\ae}}_{<t}) ~\leq~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{*,m}({\text{\ae}}_{<t}).
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 4.4 (∗) [15].** (Non-linearity of $V_{\xi}^{*}$) Show by example that the inequality in Exercise 4.3 can be strict, i.e. $V_{\xi}^{*,m}$ is *not* linear in $\nu$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Consider ${\mathcal{M}} = \{\nu_{0}, \nu_{1}\}$: predicting a two-headed coin vs. a two-tailed coin.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*Coin-flip prediction.* Let ${\mathcal{A}} = {\mathcal{O}} = {\mathcal{R}} = \{0,1\}$, ${\mathcal{M}} = \{\nu_{0}, \nu_{1}\}$ with $w_{\nu_0}= w_{\nu_1}= \tfrac{1}{2}$, horizon $m = 1$. Environment $\nu_{i}$ always shows outcome $i$, and the agent is rewarded for a correct prediction:

$$
\nu_{i}(e_{t} \mid {\text{\ae}}_{<t}\, a_{t}) ~:~ o_{t} = i, \quad r_{t} = \llbracket a_{t} = i \rrbracket.
$$

In $\nu_{i}$ the optimal policy plays $a_{t} = i$, achieving $V_{\nu_i}^{*,m}= 1$. In $\xi = \tfrac{1}{2}\nu_{0} + \tfrac{1}{2}\nu_{1}$ the outcome is a fair coin flip, so no policy predicts better than chance: $V_{\xi}^{*,m}= \tfrac{1}{2}$. Therefore:

$$
\sum_{\nu} w_{\nu}\, V_{\nu}^{*,m}({\text{\ae}}_{<t}) ~=~ \tfrac{1}{2}\cdot 1 + \tfrac{1}{2}\cdot 1 ~=~ 1 ~>~ \tfrac{1}{2}~=~ V_{\xi}^{*,m}({\text{\ae}}_{<t}).
$$

:::
