---
id: '1432f900-b8e8-4156-8cfa-b8330418b157'
title: "D.3.2.2 Measures, the Bayesian mixture and value functions"
tldr: "Proves basic identities for interaction measures, then defines the Bayesian mixture, expected return, discounted value function and the Bayes-optimal policy that defines AIXI."
summary_for_tutor: "Section 0 of worksheet D.3.2: Properties of measures, plus the Bayesian mixture and value function. Exercises 0.1-0.5 (factorization nu^pi = pi * nu, chain rule, marginalizing percepts, deterministic interaction measure, general chain rule), with collapsed solutions. Definitions of xi and posterior w(nu|ae_{<t}), expectation, discounted return G_{t:m}, value V_nu^{pi,m} = (1-gamma)E[G], optimal value, and AIXI as pi_xi^* with prior 2^{-K(nu)}. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 0. Properties of Measures

:::callout {title="Exercise" tone="amber"}
**Exercise 0.1 (Factorization) [05].** Show that $\nu^{\pi}({\text{\ae}}_{1:t}) = \pi({\text{\ae}}_{1:t}) \cdot \nu({\text{\ae}}_{1:t})$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Expanding the definition: $\nu^{\pi}({\text{\ae}}_{1:t}) = \prod_{k=1}^{t} \pi(a_{k} \mid {\text{\ae}}_{<k})\, \nu(e_{k} \mid {\text{\ae}}_{<k}a_{k}) = \underbrace{\prod_{k=1}^t \pi(a_k \mid {\text{\ae}}_{<k})}_{\pi({\text{\ae}}_{1:t})}\cdot \underbrace{\prod_{k=1}^t \nu(e_k \mid {\text{\ae}}_{<k} a_k)}_{\nu({\text{\ae}}_{1:t})}$.

Key observation: $\pi({\text{\ae}}_{1:t})$ is the same regardless of the environment. When comparing $\nu^{\pi}$ and $\mu^{\pi}$, the policy factors cancel.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 0.2 (Chain rule) [05].** Show that $\nu({\text{\ae}}_{1:t}) = \nu({\text{\ae}}_{<t}) \cdot \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

From the definition $\nu({\text{\ae}}_{1:t}) = \prod_{k=1}^{t} \nu(e_{k} \mid {\text{\ae}}_{<k}a_{k})$, split off the last factor:

$$
\nu({\text{\ae}}_{1:t}) ~=~ \prod_{k=1}^{t-1}\nu(e_{k} \mid {\text{\ae}}_{<k}a_{k}) \cdot \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}) ~=~ \nu({\text{\ae}}_{<t}) \cdot \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 0.3 (∗) (Marginalizing percepts) [03].** Show that $\sum_{e_t}\nu^{\pi}(a_{t} e_{t} \mid {\text{\ae}}_{<t}) = \pi(a_{t} \mid {\text{\ae}}_{<t})$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

From Definition 0.4, the one-step interaction is $\nu^{\pi}(a_{t} e_{t} \mid {\text{\ae}}_{<t}) = \pi(a_{t} \mid {\text{\ae}}_{<t})\, \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})$. Summing over $e_{t}$:

$$
\sum_{e_t}\nu^{\pi}(a_{t} e_{t} \mid {\text{\ae}}_{<t}) ~=~ \pi(a_{t} \mid {\text{\ae}}_{<t}) \underbrace{\sum_{e_t} \nu(e_t \mid {\text{\ae}}_{<t} a_t)}_{=\,1}~=~ \pi(a_{t} \mid {\text{\ae}}_{<t}).
$$

Interpretation: after summing out the environment's response, only the agent's action probability remains.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 0.4 (∗) (Deterministic interaction measure) [05].** Let $\pi$ be a deterministic policy, i.e. at each history ${\text{\ae}}_{<k}$ there is a unique action $a^{*}_{k}$ with $\pi(a^{*}_{k} \mid {\text{\ae}}_{<k}) = 1$. Show that, provided ${\text{\ae}}_{i:j}$ is consistent with $\pi$ (i.e. $a_{k} = a^{*}_{k}$ for every $k \in \{i, \ldots, j\}$):

$$
\nu^{\pi}({\text{\ae}}_{i:j}\mid {\text{\ae}}_{<i}) ~=~ \nu({\text{\ae}}_{i:j}\mid {\text{\ae}}_{<i}),
$$

i.e. on $\pi$-consistent futures the interaction measure reduces to the environment measure: every policy factor is $1$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Since $\pi$ is deterministic, $\pi(a_{k} \mid {\text{\ae}}_{<k}) = \llbracket a_{k} = a^{*}_{k} \rrbracket$. By hypothesis ${\text{\ae}}_{i:j}$ is $\pi$-consistent, so every such bracket equals $1$. From Definition 0.4:

$$
\begin{aligned}\nu^{\pi}({\text{\ae}}_{i:j}\mid {\text{\ae}}_{<i}) ~&=~ \prod_{k=i}^{j} \underbrace{\pi(a_k \mid {\text{\ae}}_{<k})}_{=\, 1}\, \nu(e_{k} \mid {\text{\ae}}_{<k}a_{k}) \\ ~&=~ \prod_{k=i}^{j} \nu(e_{k} \mid {\text{\ae}}_{<k}\, a_{k}) ~=~ \nu({\text{\ae}}_{i:j}\mid {\text{\ae}}_{<i}),\end{aligned}
$$

where the last equality is the natural segment extension of $\nu({\text{\ae}}_{1:t}) := \prod_{k=1}^{t} \nu(e_{k} \mid {\text{\ae}}_{<k}a_{k})$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 0.5 [05].** (General chain rule for $\nu^{\pi}$) Show that for any $p \leq q \leq r$:

$$
\nu^{\pi}({\text{\ae}}_{p:r}\mid {\text{\ae}}_{<p}) ~=~ \nu^{\pi}({\text{\ae}}_{p:q}\mid {\text{\ae}}_{<p}) \cdot \nu^{\pi}({\text{\ae}}_{q+1:r}\mid {\text{\ae}}_{<p}\, {\text{\ae}}_{p:q}).
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Split the defining product $\nu^{\pi}({\text{\ae}}_{p:r}\mid {\text{\ae}}_{<p}) = \prod_{k=p}^{r} \pi(a_{k} \mid {\text{\ae}}_{<k})\, \nu(e_{k} \mid {\text{\ae}}_{<k}a_{k})$ at index $q$:

$$
\begin{aligned}&\nu^{\pi}({\text{\ae}}_{p:r}\mid {\text{\ae}}_{<p}) ~=~ \prod_{k=p}^{r} \pi(a_{k} \mid {\text{\ae}}_{<k})\, \nu(e_{k} \mid {\text{\ae}}_{<k}a_{k})\\&=~ \underbrace{\prod_{k=p}^{q} \pi(a_k \mid {\text{\ae}}_{<k})\, \nu(e_k \mid {\text{\ae}}_{<k} a_k)}_{\nu^\pi({\text{\ae}}_{p:q} \mid {\text{\ae}}_{<p})}\;\cdot\; \underbrace{\prod_{k=q+1}^{r} \pi(a_k \mid {\text{\ae}}_{<k})\, \nu(e_k \mid {\text{\ae}}_{<k} a_k)}_{\nu^\pi({\text{\ae}}_{q+1:r} \mid {\text{\ae}}_{<p}\, {\text{\ae}}_{p:q})},\end{aligned}
$$

identifying each block as a conditional via the same expansion: the past for step $k \geq q+1$ is the given history ${\text{\ae}}_{<p}$ extended by the first chunk ${\text{\ae}}_{p:q}$.

Note: for a deterministic policy, Exercise 0.4 simplifies this further: each factor $\pi(a_{k} \mid {\text{\ae}}_{<k})\, \nu(e_{k} \mid {\text{\ae}}_{<k}a_{k})$ becomes just $\nu(e_{k} \mid {\text{\ae}}_{<k}\, a^{*}_{k})$.

:::

\## The Bayesian Mixture and Value Function

:::callout {title="Definition" tone="blue"}

**Definition 0.1 (Model class, prior, and Bayesian mixture $\xi$).** Let ${\mathcal{M}} = \{\nu_{1}, \nu_{2}, \ldots\}$ be a countable class of environments with prior weights $w_{\nu} > 0$ satisfying $\sum_{\nu \in {\mathcal{M}}}w_{\nu} \leq 1$. We assume $\mu \in {\mathcal{M}}$.

The **Bayesian mixture** $\xi$ is defined as

$$
\xi({\text{\ae}}_{1:t}) := \sum_{\nu \in {\mathcal{M}}}w_{\nu}\, \nu({\text{\ae}}_{1:t}) \quad \text{ and }\quad \xi(e_{t} \mid {\text{\ae}}_{<t}a_{t}) := \xi({\text{\ae}}_{1:t}) / \xi({\text{\ae}}_{<t}).
$$

One can show that the one-step predictive distribution can be written as

$$
\xi(e_{t} \mid {\text{\ae}}_{<t}a_{t}) ~=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}),
$$

where the **posterior weight** is

$$
w(\nu \mid {\text{\ae}}_{<t}) ~:=~ w_{\nu} \,\frac{\nu({\text{\ae}}_{<t})}{\xi({\text{\ae}}_{<t})}, \qquad w(\nu \mid \epsilon) := w_{\nu}.
$$

See Appendix A for a worked example.

:::

:::callout {title="Definition" tone="blue"}

**Definition 0.2 (Expectation ${\mathbb{E}}_{\nu}^{\pi}$).** For a function $f : {\mathcal{H}} \to \mathbb{R}$ of a finite future segment ${\text{\ae}}'_{t:m}$:

$$
{\mathbb{E}}_{\nu}^{\pi}[f \mid {\text{\ae}}_{<t}] ~:=~ \underset{{\text{\ae}}_{t:m} \sim \nu^\pi(\cdot \mid {\text{\ae}}_{<t})}{{\mathbb{E}}}[f] ~=~ \sum_{{\text{\ae}}'_{t:m}}\nu^{\pi}({\text{\ae}}'_{t:m}\mid {\text{\ae}}_{<t})\, f({\text{\ae}}'_{t:m}).
$$

For functions $f$ of the infinite future (like the value function), with a sequence $f_{1}, f_{2}, \ldots \to f$, where $f_{m}$ depends only on ${\text{\ae}}'_{t:m}$, we define ${\mathbb{E}}_{\nu}^{\pi}[f \mid {\text{\ae}}_{<t}] := \lim_{m \to \infty}{\mathbb{E}}_{\nu}^{\pi}[f_{m} \mid {\text{\ae}}_{<t}]$.

:::

:::callout {title="Definition" tone="blue"}

**Definition 0.3 (Discounted return $G_{t:m}$).** Fix a discount factor $\gamma \in (0,1)$, held constant throughout. The **discounted return** at time step $t$, up to horizon $m$, is

$$
G^{\gamma}_{t:m}~:=~ \sum_{k=t+1}^{m}\gamma^{k-(t+1)}\, r_{k} ~=~ r_{t+1}+ \gamma\, r_{t+2}+ \cdots + \gamma^{m-t}\, r_{m}.
$$

Since $\gamma$ is fixed we drop it and write $G_{t:m}\equiv G^{\gamma}_{t:m}$. It satisfies the recursion $G_{t:m}= r_{t+1}+ \gamma\, G_{t+1:m}$, with $G_{m-1:m}= r_{m}$ and $G_{n:m}= 0$ for $n \geq m$. The **infinite-horizon return** is the pointwise limit

$$
G_{\geq t}~\equiv~ G_{t:\infty}~:=~ \lim_{m \to \infty}G_{t:m}~=~ \sum_{k=t+1}^{\infty}\gamma^{k-(t+1)}\, r_{k},
$$

with the clean recursion $G_{\geq t}= r_{t+1}+ \gamma\, G_{\geq t+1}$ and no boundary cases.

:::

:::callout {title="Definition" tone="blue"}

**Definition 0.4 (Value function[^1]).** The **value** of policy $\pi$ in environment $\nu$ with horizon $m \geq t$ given history ${\text{\ae}}_{<t}$ is

$$
\begin{aligned}&V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) ~:=~ (1-\gamma)\, {\mathbb{E}}_{\nu}^{\pi}\!\left[G_{t-1:m}\mid {\text{\ae}}_{<t}\right] \\ ~&=~ (1-\gamma) \sum_{{\text{\ae}}_{t:m}}\nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t})\, G_{t-1:m}\\ ~&=~ (1-\gamma) \sum_{{\text{\ae}}_{t:m}}\nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) \left[ \sum_{k=t}^{m}\gamma^{k-t}r_{k} \right].\end{aligned}
$$

The **infinite-horizon value** is the pointwise limit $V_{\nu}^{\pi,\infty}({\text{\ae}}_{<t}) := \lim_{m \to \infty}V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) = (1-\gamma)\, {\mathbb{E}}_{\nu}^{\pi}[G_{\geq t-1}\mid {\text{\ae}}_{<t}]$. We write $V_{\nu}^{\pi} \equiv V_{\nu}^{\pi,\infty}$ for short.

The **optimal value** is $V_{\nu}^{*,m}({\text{\ae}}_{<t}) := \sup_{\pi} V_{\nu}^{\pi,m}({\text{\ae}}_{<t})$ for $m \in \mathbb{N}\cup \{\infty\}$, with $V_{\nu}^{*} \equiv V_{\nu}^{*,\infty}$. [^2] An **optimal policy** $\pi_{\nu}^{*}$ satisfies $V_{\nu}^{\pi_\nu^*}= V_{\nu}^{*}$. The **Bayes-optimal policy** is $\pi_{\xi}^{*} \in {\operatorname*{arg\,max}}_{\pi} V_{\xi}^{\pi}$.

:::

:::callout {title="Note" tone="blue"}

**Remark (AIXI).** All results in this sheet hold for any countable ${\mathcal{M}}$ and prior weights $w_{\nu}$. **AIXI** is a special case of the Bayes-optimal policy $\pi_{\xi}^{*}$ for the particular choice ${\mathcal{M}} :=$ the class of all lower-semicomputable chronological semimeasures, and prior $w_{\nu} := 2^{-K(\nu)}$, where $K(\nu)$ is the Kolmogorov complexity of $\nu$: the length of the shortest program that computes $\nu$. The resulting agent is written $\pi^{*}_{\xi_U}$, or simply AI$\xi$.

**Why this ${\mathcal{M}}$?** By including every computable environment, the assumption $\mu \in {\mathcal{M}}$ reduces to "the universe is computable": as weak an assumption as one can make.

**Why this prior?** The prior $2^{-K(\nu)}$ is *dominant*: for any other computable prior $w'_{\nu}$, there exists a constant $c > 0$ such that $2^{-K(\nu)}\geq c \cdot w'_{\nu}$ for all $\nu$.

**Caveat:** The constant $c$ depends on the choice of universal Turing machine $U$, and adversarial choices of $U$ can make AIXI behave arbitrarily badly (Leike & Hutter 2015).

See (Hutter et al. 2024): Chapter 2.7 for Kolmogorov complexity, Chapters 3.7–3.8 for the model class and universal prior, and Chapter 7.4 for AIXI itself.

:::
