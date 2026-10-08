---
id: '9b4f0449-b975-4300-82ce-bf3b88c7d82c'
title: "D.3.2.3 Properties of the Bayesian mixture"
tldr: "Proves the multiplicative posterior update and the one-step predictive form of the mixture, that values lie in [0,1], and that the mixture is linear in the posterior over multiple steps."
summary_for_tutor: "Section 1 of worksheet D.3.2: Properties of the Bayesian mixture. Exercises 1.1 (posterior update), 1.2 (one-step predictive distribution of xi), 1.3 (value bounded in [0,1]) and 1.4 (multi-step posterior linearity of xi^pi), with hints and collapsed solutions. Exercises 1.1 and 1.4 are marked as skippable on a first pass. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. Properties of the Bayesian Mixture

::::callout {title="Exercise" tone="amber"}
**Exercise 1.1 (∗) (Posterior update) [10].** Show that the posterior updates multiplicatively:

$$
w(\nu \mid {\text{\ae}}_{1:t}) ~=~ w(\nu \mid {\text{\ae}}_{<t}) \frac{\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}{\xi(e_{t} \mid {\text{\ae}}_{<t}a_{t})}.
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Use the definitions of $w(\nu \mid {\text{\ae}}_{1:t})$ and $w(\nu \mid {\text{\ae}}_{<t})$, and apply Exercise 0.2.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

From the definition: $w(\nu \mid {\text{\ae}}_{1:t}) = w_{\nu} \cdot \nu({\text{\ae}}_{1:t})/\xi({\text{\ae}}_{1:t})$ and $w(\nu \mid {\text{\ae}}_{<t}) = w_{\nu} \cdot \nu({\text{\ae}}_{<t})/\xi({\text{\ae}}_{<t})$.

Dividing:

$$
\frac{w(\nu \mid {\text{\ae}}_{1:t})}{w(\nu \mid {\text{\ae}}_{<t})}= \frac{\nu({\text{\ae}}_{1:t})}{\nu({\text{\ae}}_{<t})}\cdot \frac{\xi({\text{\ae}}_{<t})}{\xi({\text{\ae}}_{1:t})}= \frac{\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}{\xi(e_{t} \mid {\text{\ae}}_{<t}a_{t})},
$$

where we used the chain rule (Exercise 0.2) for both $\nu$ and $\xi$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 1.2 [15].** (One-step predictive distribution of $\xi$) Starting from $\xi({\text{\ae}}_{1:t}) = \sum_{\nu \in {\mathcal{M}}}w_{\nu} \nu({\text{\ae}}_{1:t})$, derive the one-step predictive form:

$$
\xi(e_{t} \mid {\text{\ae}}_{<t}a_{t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Write $\xi(e_{t} \mid {\text{\ae}}_{<t}a_{t}) = \xi({\text{\ae}}_{1:t}) / \xi({\text{\ae}}_{<t})$, expand the numerator, and use Exercise 0.2.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The one-step conditional is the ratio of joint to marginal: $\xi(e_{t} \mid {\text{\ae}}_{<t}a_{t}) := \xi({\text{\ae}}_{1:t})/\xi({\text{\ae}}_{<t})$.

Expanding the numerator using $\xi({\text{\ae}}_{1:t}) = \sum_{\nu} w_{\nu} \nu({\text{\ae}}_{1:t})$:

$$
\begin{aligned}\xi(e_{t} \mid {\text{\ae}}_{<t}a_{t}) ~&=~ \frac{\sum_{\nu \in {\mathcal{M}}}w_{\nu}\, \nu({\text{\ae}}_{1:t})}{\xi({\text{\ae}}_{<t})}\\[4pt] ~&=~ \frac{\sum_{\nu}w_{\nu}\, \nu({\text{\ae}}_{<t}) \cdot \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}{\xi({\text{\ae}}_{<t})}\quad \text{(chain rule, Exercise 0.2)}\\[4pt] ~&=~ \sum_{\nu}\underbrace{\frac{w_{\nu}\, \nu({\text{\ae}}_{<t})}{\xi({\text{\ae}}_{<t})}}_{= \, w(\nu \mid {\text{\ae}}_{<t})}\cdot\, \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}) \\[4pt] ~&=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}).\end{aligned}
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 1.3 (Bounded value) [10].** Show that $V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) \in [0,1]$ for any $\nu, \pi, m \in \mathbb{N}\cup \{\infty\}, {\text{\ae}}_{<t}$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Recall the formula for geometric series: $(1-\gamma)\sum_{k=0}^{n}\gamma^{k} = 1 - \gamma^{n+1}$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Since $r_{k} \in [0,1]$, each discounted reward sum is bounded:

$$
0 ~\leq~ (1-\gamma)\, G_{t-1:m}~\leq~ (1-\gamma)\sum_{k=t}^{m}\gamma^{k-t}~=~ 1 - \gamma^{m-t+1}~\leq~ 1.
$$

The interaction measure satisfies $\nu^{\pi}({\text{\ae}}'_{t:m}\mid {\text{\ae}}_{<t}) \geq 0$ and $\sum_{{\text{\ae}}'_{t:m}}\nu^{\pi}({\text{\ae}}'_{t:m}\mid {\text{\ae}}_{<t}) = 1$, so the value function is a weighted average of terms in $[0,1]$:

$$
0 ~\leq~ V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) ~=~ \sum_{{\text{\ae}}'_{t:m}}\nu^{\pi}({\text{\ae}}'_{t:m}\mid {\text{\ae}}_{<t})\, (1-\gamma)\, G_{t-1:m}~\leq~ 1.
$$

For $m = \infty$: since $0 \leq V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) \leq 1$ for all finite $m$, the limit $V_{\nu}^{\pi}({\text{\ae}}_{<t}) = \lim_{m \to \infty}V_{\nu}^{\pi,m}({\text{\ae}}_{<t})$ also lies in $[0,1]$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 1.4 (∗) [15].** (Multi-step posterior linearity of $\xi^{\pi}$) Extend Exercise 1.2 to multi-step histories: show that for finite $m \geq t$,

$$
\xi^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, \nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Apply the general chain rule (Exercise 0.5) to $\xi({\text{\ae}}_{1:m}) = \sum_{\nu} w_{\nu} \nu({\text{\ae}}_{1:m})$, then use factorization (Exercise 0.1).

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Start from the definition $\xi({\text{\ae}}_{1:m}) = \sum_{\nu \in {\mathcal{M}}}w_{\nu}\, \nu({\text{\ae}}_{1:m})$. Apply the general chain rule (Exercise 0.5) to both sides: $\xi({\text{\ae}}_{1:m}) = \xi({\text{\ae}}_{<t}) \cdot \xi({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t})$ and $\nu({\text{\ae}}_{1:m}) = \nu({\text{\ae}}_{<t}) \cdot \nu({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t})$. Dividing by $\xi({\text{\ae}}_{<t})$:

$$
\begin{aligned}\xi({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) ~&=~ \sum_{\nu \in {\mathcal{M}}}\frac{w_{\nu}\, \nu({\text{\ae}}_{<t})}{\xi({\text{\ae}}_{<t})}\nu({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) \\ ~&=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, \nu({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}).\end{aligned}
$$

Now multiply both sides by $\pi({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t})$. By factorization (Exercise 0.1), $\pi({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) \cdot \xi({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) = \xi^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t})$ and likewise for each $\nu$:

$$
\xi^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, \nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}).
$$

:::
