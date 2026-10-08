---
id: '7f53f90a-ae1d-406d-ad35-9f8b1b91fa9e'
title: "D.3.2.9 Likelihood ratios are martingales"
tldr: "States the self-optimizing property for a finite model class and proves that likelihood ratios against the true environment are martingales that converge."
summary_for_tutor: "Section 9 of worksheet D.3.2 (start of the advanced Sections 9-11 for a finite model class). Definition 9.1 (self-optimizing), Theorem 9.2 (if some policy is self-optimizing then pi_xi^* is), Definition 9.3 (supermartingale), Fact 9.4 (Doob convergence). Exercises 9.1 (X_{nu,t} = nu/mu is a mu^pi-martingale), 9.2 (it converges almost surely) and 9.3 (X_{xi,t} = sum w_nu X_{nu,t} >= w_mu). Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Sections 9–11: Self-Optimizing Policy (Finite Model Class)

We now prove: if *any* policy can learn to act optimally, $\pi_{\xi}^{*}$ also learns. We restrict to finite ${\mathcal{M}} = \{\nu_{1}, \ldots, \nu_{N}\}$ where each $\nu_{i}$ is a proper probability measure.

\## 9. Likelihood Ratios Are Martingales

The following definition and theorem state the main goal of Sections 9–11.

:::callout {title="Definition" tone="blue"}

**Definition 9.1 (Self-optimizing).** Fix a historic policy $\pi$. A policy $\tilde\pi$ is **self-optimizing** for ${\mathcal{M}}$ with respect to $\pi$ if for every $\nu \in {\mathcal{M}}$: $V_{\nu}^{*}({\text{\ae}}_{<t}) - V_{\nu}^{\tilde\pi}({\text{\ae}}_{<t}) \to 0$ as $t \to \infty$, $\nu^{\pi}$-almost surely.

The percepts $e_{1:\infty}$ are sampled from $\nu$; the historic actions $a_{<t}$ come from $\pi$, which may differ from $\tilde\pi$.

:::

:::callout {title="Theorem" tone="green"}

**Theorem 9.2 (Self-optimizing; (Hutter et al. 2024, Theorem 7.5.2)).** Let ${\mathcal{M}}$ be finite and fix a historic policy $\pi$. If there exists a $\tilde\pi$ self-optimizing for ${\mathcal{M}}$ with respect to $\pi$, then $\pi_{\xi}^{*}$ is also self-optimizing for ${\mathcal{M}}$ with respect to $\pi$: for any $\mu \in {\mathcal{M}}$, $V_{\mu}^{*}({\text{\ae}}_{<t}) - V_{\mu}^{\pi_\xi^*}({\text{\ae}}_{<t}) \to 0$ $\mu^{\pi}$-almost surely.

:::

:::callout {title="Definition" tone="blue"}

**Definition 9.3 (Supermartingale).** A sequence of functions $X_{t} : {\mathcal{H}}^{t}\to \mathbb{R}_{\geq 0}$ (each depending on the history ${\text{\ae}}_{1:t}$) is a $\mu^{\pi}$-**supermartingale** if ${\mathbb{E}}_{\mu^\pi}[X_{t} \mid {\text{\ae}}_{<t}] \leq X_{t-1}$ for all $t$; that is,

$$
\sum_{{\text{\ae}}_t}\pi(a_{t} \mid {\text{\ae}}_{<t})\, \mu(e_{t} \mid {\text{\ae}}_{<t}a_{t})\, X_{t}({\text{\ae}}_{1:t}) ~\leq~ X_{t-1}({\text{\ae}}_{<t}).
$$

If equality holds, it is a $\mu^{\pi}$-**martingale**.

:::

**Intuition.** A supermartingale is a quantity whose expected future value, given the present, is no larger than its current value: it cannot "drift upward on average." A martingale is the equality case: expected future value equals current value. The key example is the **likelihood ratio** $X_{\nu,t}({\text{\ae}}_{1:t}) := \nu({\text{\ae}}_{1:t})/\mu({\text{\ae}}_{1:t})$: how much more (or less) likely the observed history is under $\nu$ than under the true environment $\mu$. Under $\mu$, this ratio is a martingale: the true environment does not, on average, favour any alternative $\nu$ over itself. Non-negativity plus the (super)martingale structure forces $X_{\nu,t}$ to converge (by Doob's theorem below), which is the engine behind the self-optimizing proof: it lets us separate environments that remain plausible ($X_{\nu,\infty}> 0$) from those that are eventually ruled out ($X_{\nu,\infty}= 0$), and handle each case differently in Section 11.

:::callout {title="Note" tone="blue"}

**Fact 9.4 (Doob's supermartingale convergence).** If $(X_{t})_{t \geq 0}$ is a non-negative $\mu^{\pi}$-supermartingale, then there exists a function $X_{\infty} : {\mathcal{H}}^{\infty} \to \mathbb{R}_{\geq 0}$ of the infinite history such that $X_{t}({\text{\ae}}_{1:t}) \to X_{\infty}({\text{\ae}}_{1:\infty})$ as $t \to \infty$, with $X_{\infty}({\text{\ae}}_{1:\infty}) < \infty$, for $\mu^{\pi}$-almost every infinite history ${\text{\ae}}_{1:\infty}$. That is:

$$
\mu^{\pi}\!\Big(\Big\{{\text{\ae}}_{1:\infty}\in ({\mathcal{A}} \times {\mathcal{E}})^{\infty} : X_{t}({\text{\ae}}_{1:t}) \not\to X_{\infty}({\text{\ae}}_{1:\infty})\Big\}\Big) ~=~ 0.
$$

:::

For each $\nu \in {\mathcal{M}}$, define the likelihood ratio

$$
X_{\nu,t}: {\mathcal{H}}^{t} \to \mathbb{R}_{\geq 0}, \qquad X_{\nu,t}({\text{\ae}}_{1:t}) ~:=~ \frac{\nu({\text{\ae}}_{1:t})}{\mu({\text{\ae}}_{1:t})}, \qquad X_{\nu,0}:= 1.
$$

$X_{\nu,t}$ is a *function* of the history ${\text{\ae}}_{1:t}$, not a number: different histories give different values. Throughout this section and the next, any unqualified statement of the form "$X_{\nu,t}\geq c$" or "$X_{\nu,t}\to X_{\nu,\infty}$" is shorthand for "$X_{\nu,t}({\text{\ae}}_{1:t}) \geq c$" or "$X_{\nu,t}({\text{\ae}}_{1:t}) \to X_{\nu,\infty}({\text{\ae}}_{1:\infty})$" holding $\mu^{\pi}$-almost surely, i.e. on every infinite history outside a set of $\mu^{\pi}$-measure zero. We will not track these null sets explicitly; their countable union over all claims is still a $\mu^{\pi}$-null set.

::::callout {title="Exercise" tone="amber"}
**Exercise 9.1 [15].** Show that $X_{\nu,t}$ is a $\mu^{\pi}$-martingale: ${\mathbb{E}}_{\mu^\pi}[X_{\nu,t}\mid {\text{\ae}}_{<t}] = X_{\nu,t-1}$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Write $X_{\nu,t}({\text{\ae}}_{1:t}) = X_{\nu,t-1}({\text{\ae}}_{<t}) \cdot \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})/\mu(e_{t} \mid {\text{\ae}}_{<t}a_{t})$. Sum over $a_{t}, e_{t}$; $\mu$ cancels, leaving $\sum_{e_t}\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}) = 1$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We need to compute ${\mathbb{E}}_{\mu^\pi}[X_{\nu,t}\mid {\text{\ae}}_{<t}]$. Conditioning on ${\text{\ae}}_{<t}$ means $a_{t}$ and $e_{t}$ are the random quantities (sampled from $\pi$ and $\mu$ respectively). First, write $X_{\nu,t}$ pointwise as a function of history in terms of $X_{\nu,t-1}$:

$$
\begin{aligned}X_{\nu,t}({\text{\ae}}_{1:t}) ~&=~ \frac{\nu({\text{\ae}}_{1:t})}{\mu({\text{\ae}}_{1:t})}~=~ \frac{\nu({\text{\ae}}_{<t})}{\mu({\text{\ae}}_{<t})}\cdot \frac{\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}{\mu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}\\ ~&=~ X_{\nu,t-1}({\text{\ae}}_{<t}) \cdot \frac{\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}{\mu(e_{t} \mid {\text{\ae}}_{<t}a_{t})},\end{aligned}
$$

using the chain rule (Exercise 0.2) for both $\nu$ and $\mu$. Now take the conditional expectation. Since $X_{\nu,t-1}$ depends only on ${\text{\ae}}_{<t}$, it comes out of the expectation:

$$
\begin{aligned}{\mathbb{E}}_{\mu^\pi}[X_{\nu,t}\mid {\text{\ae}}_{<t}] ~&=~ X_{\nu,t-1}\cdot {\mathbb{E}}_{\mu^\pi}\!\left[\frac{\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}{\mu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}~\Big|~ {\text{\ae}}_{<t}\right] \\ ~&=~ X_{\nu,t-1}\sum_{a_t \in {\mathcal{A}}}\pi(a_{t} \mid {\text{\ae}}_{<t}) \sum_{e_t \in {\mathcal{E}}}\mu(e_{t} \mid {\text{\ae}}_{<t}a_{t}) \cdot \frac{\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}{\mu(e_{t} \mid {\text{\ae}}_{<t}a_{t})}\\ ~&=~ X_{\nu,t-1}\sum_{a_t}\pi(a_{t} \mid {\text{\ae}}_{<t}) \sum_{e_t}\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}).\end{aligned}
$$

In the last step, $\mu(e_{t} \mid {\text{\ae}}_{<t}a_{t})$ cancels. Since $\nu$ is a probability measure, $\sum_{e_t}\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}) = 1$ for every ${\text{\ae}}_{<t}, a_{t}$; and $\sum_{a_t}\pi(a_{t} \mid {\text{\ae}}_{<t}) = 1$. Therefore:

$$
{\mathbb{E}}_{\mu^\pi}[X_{\nu,t}\mid {\text{\ae}}_{<t}] ~=~ X_{\nu,t-1}\cdot 1 \cdot 1 ~=~ X_{\nu,t-1}.
$$

Since $X_{\nu,t}\geq 0$ (a ratio of non-negative quantities), $(X_{\nu,t})_{t \geq 0}$ is a non-negative $\mu^{\pi}$-martingale, in particular, a non-negative $\mu^{\pi}$-supermartingale.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 9.2 [05].** Apply Fact 9.4 to conclude $X_{\nu,t}\to X_{\nu,\infty}< \infty$ $\mu^{\pi}$-a.s.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

$X_{\nu,t}$ is a non-negative $\mu^{\pi}$-supermartingale by Exercise 9.1. By Fact 9.4 (Doob's convergence theorem), $X_{\nu,t}$ converges $\mu^{\pi}$-a.s. to a finite limit: $X_{\nu,t}\to X_{\nu,\infty}< \infty$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 9.3 [10].** Define $X_{\xi,t}:= \xi({\text{\ae}}_{1:t})/\mu({\text{\ae}}_{1:t})$. Show $X_{\xi,t}= \sum_{\nu} w_{\nu} X_{\nu,t}$ and $X_{\xi,t}\geq w_{\mu} > 0$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

From the definition:

$$
X_{\xi,t}~:=~ \frac{\xi({\text{\ae}}_{1:t})}{\mu({\text{\ae}}_{1:t})}~=~ \frac{\sum_{\nu} w_{\nu} \nu({\text{\ae}}_{1:t})}{\mu({\text{\ae}}_{1:t})}~=~ \sum_{\nu} w_{\nu} \cdot \frac{\nu({\text{\ae}}_{1:t})}{\mu({\text{\ae}}_{1:t})}~=~ \sum_{\nu} w_{\nu} X_{\nu,t}.
$$

By Section 3: $\xi({\text{\ae}}_{1:t}) \geq w_{\mu} \cdot \mu({\text{\ae}}_{1:t})$, so $X_{\xi,t}= \xi({\text{\ae}}_{1:t})/\mu({\text{\ae}}_{1:t}) \geq w_{\mu} > 0$.

Since ${\mathcal{M}}$ is finite, $X_{\xi,t}= \sum_{\nu} w_{\nu} X_{\nu,t}$ is a finite sum of convergent sequences, so $X_{\xi,t}\to X_{\xi,\infty}:= \sum_{\nu} w_{\nu} X_{\nu,\infty}< \infty$ $\mu^{\pi}$-a.s., with $X_{\xi,\infty}\geq w_{\mu} > 0$.

:::
