---
id: '42d09889-4fb8-4c6c-85dd-96119cee086a'
title: "D.3.2 AIXI"
tldr: "Exploring the Bayesian optimal policy for history based reinforcement learning."
summary_for_tutor: "Faithful April 2026 Iliad Intensive worksheet D.3.2, AIXI. Preserve its mathematical notation, exercise sequence, hints, and solutions."
authors:
  - David Quarel
source_url: https://github.com/iliad-team/iliad-intensive/blob/1eb9e340305e03de3f81a761167e13c54c71f19d/tex/aixi/main.tex
upstream_commit: '1eb9e340305e03de3f81a761167e13c54c71f19d'
provenance_recorded_at: '2026-08-17'
---

#### Text
content::
:::callout {title="What you'll learn" tone="green"}

- Formalize the agent-environment interaction, value functions, and the Bayes-optimal policy that defines AIXI.
- Derive the explicit expectimax form of AIXI.
- Prove on-policy value convergence and that AIXI cannot be fooled in deterministic environments.
- Prove the self-optimizing property via likelihood-ratio martingales and change of measure.

:::

Much of this material is drawn from ([[#^bib-hutter-24uaibook2|Hutter et al. 2024]]). The book provides fuller explanations, additional context, and proofs omitted here.

**Difficulty ratings.** Each subproblem is tagged with a rating in square brackets using Knuth's scale ([[#^bib-knuth-73a|Knuth 1973]]): roughly, **[00]** trivial, **[10]** 15–minute pencil-and-paper, **[20]** 1–2 hours, **[30]** several hours to a day, **[40]** a significant research result. Intermediate values are possible. See [[#C. Knuth's Difficulty Scale|Section C]] for the full scale.

Problems marked **($\ast$)** are less interesting/insightful and while the result may be used later, I would recommend skipping them on a first pass.

\## Overview

AIXI is the *action* half of **Universal AI**: it lifts the Bayesian mixture from [Solomonoff induction](/agency/solomonoff-induction) — learning to predict — to learning to act. Now the agent takes actions that shape what it observes, and AIXI is the **Bayes-optimal policy** over a universal mixture $\xi$ of environments. It learns to act as well as if it knew the true environment $\mu$. Under the universal choice — $\mathcal{M}$ = all lower-semicomputable environments, prior $w_{\nu} = 2^{-K(\nu)}$ — the assumption "$\mu \in \mathcal{M}$" again becomes "the universe is computable."

\## Prerequisites

- [Solomonoff Induction](/agency/solomonoff-induction) — **start there first.** The Bayesian mixture, posterior updates, and dominance carry over directly; AIXI reuses them in the action setting.
- Comfort with discrete probability (conditional distributions, chain rule, expectations).
- Familiarity with sequential decision-making / reinforcement learning (agents, rewards, discounting, value functions) is useful but not assumed.

\## Further reading

- Hutter, [*An Introduction to Universal Artificial Intelligence*](https://www.hutter1.net/publ/uaibook2.pdf) (2024): Chapter 2.7 (Kolmogorov complexity), Chapters 3.7–3.8 (the model class and universal prior), and Chapter 7.4 (AIXI).
- Hutter, [*Universal Artificial Intelligence: Sequential Decisions Based on Algorithmic Probability*](http://www.hutter1.net/ai/uaibook.htm) (Springer, 2005) — the original book-length treatment; Lem. 5.28 handles the countable-$\mathcal{M}$ self-optimizing case.
- Blackwell & Dubins, [*Merging of Opinions with Increasing Information*](https://doi.org/10.1214/aoms/1177704456) (Ann. Math. Statist., 1962) — the merging-of-opinions theorem behind on-policy value convergence.
- Leike & Hutter, [*Bad Universal Priors and Notions of Optimality*](https://arxiv.org/abs/1510.04931) (COLT 2015) — adversarial choices of the universal Turing machine can make AIXI behave arbitrarily badly.

\## Goal and Roadmap

This exercise sheet builds towards three main results:

- **On-policy value convergence** ([[#7. On-Policy Value Convergence of Bayes|Section 7]]): the Bayesian mixture $\xi$ learns to predict the value of any fixed policy as well as the true environment $\mu$.
- **AIXI can't be fooled** ([[#8. AIXI Cannot Be Fooled in Deterministic Environments|Section 8]]): in deterministic environments, the Bayes-optimal agent is guaranteed non-zero value whenever optimal value is non-zero.
- **Self-optimizing property** ([[#11. Proving the Self-Optimizing Property|Section 11]], advanced stretch goal): the Bayes-optimal policy $\pi_{\xi}^{*}$ learns to *act* as well as if it knew $\mu$, provided that any learnable policy can achieve this. This is the central theoretical justification for the AIXI agent.

A good target is to complete [[#7. On-Policy Value Convergence of Bayes|Section 7]] and [[#8. AIXI Cannot Be Fooled in Deterministic Environments|8]]. The self-optimizing property ([[#9. Likelihood Ratios Are Martingales|Sections 9–11]]) requires substantial additional machinery (supermartingales, change of measure) and is an advanced stretch goal.

**Critical path.** The three results share a common foundation ([[#0. Properties of Measures|Sections 0–4]]) and then diverge:

![diagram](https://iliad-team.github.io/iliad-intensive/uploads/aixi/tikz-14e23c80befc.svg)

**In summary:**

- [[#0. Properties of Measures|Sections 0–4]] establish the Bayesian RL framework: measure algebra, mixture properties, existence of optimal policies, dominance, and linearity.
- [[#5. The Expectimax Form of AIXI|Section 5]] derives the explicit expectimax form of AIXI.
- [[#6. Bounding Expectation Differences by Total Variation|Sections 6–7]] prove *on-policy value convergence*: $V_{\xi}^{\pi}$ and $V_{\mu}^{\pi}$ become indistinguishable for any fixed $\pi$.
- [[#8. AIXI Cannot Be Fooled in Deterministic Environments|Section 8]] shows *AIXI can't be fooled*: the Bayes-optimal agent achieves non-zero value whenever optimal value is non-zero (in deterministic environments).
- [[#9. Likelihood Ratios Are Martingales|Sections 9–11]] (advanced stretch goal) prove the *self-optimizing property*: if any policy can learn to act optimally, $\pi_{\xi}^{*}$ inherits this.

\## Setup

An **agent** interacts with an **environment** in discrete time steps $t = 1, 2, \ldots$.

:::callout {title="Definition" tone="purple"}

**Definition 0.1 (Spaces and notation).** - $\mathcal{A}$: finite set of **actions**
- $\mathcal{O}$: finite set of **observations**
- $\mathcal{R} \subset [0,1]$: finite set of **rewards**
- $\mathcal{E} := \mathcal{O} \times \mathcal{R}$: set of **percepts**; $e_{t} = (o_{t}, r_{t}) \equiv o_{t}r_{t}$
- $\mathcal{H}^{t} := (\mathcal{A} \times \mathcal{E})^{t}$: set of all histories of length $t$
- $\mathcal{H}^{*} := \cup_{t=0}^{\infty} \mathcal{H}^{t}$: set of all finite **histories**
- $\mathcal{H}^{\infty} := (\mathcal{A} \times \mathcal{E})^{\infty}$: set of all infinite histories
- $\Delta S$: set of all probability distributions over set $S$
- $\llbracket \cdot \rrbracket$: **Iverson bracket**: $\llbracket P \rrbracket = 1$ if $P$ is true, $0$ if false
- $t$: current time step; $m$: finite horizon; $1 \leq t \leq m$
- $i, j, k$: arbitrary integer indices
- $xy$: concatenation
- $\epsilon$: the empty string/history
- $\text{æ}_{i:j}:= a_{i} e_{i}\, a_{i+1}e_{i+1}\,\cdots\, a_{j} e_{j}$: history segment from time $i$ to $j$
- $\text{æ}_{<t}:= a_{1} e_{1}\, a_{2} e_{2} \,\cdots\, a_{t-1}e_{t-1}$: history up to (but not including) time $t$

:::

^def-spaces


:::callout {title="Definition" tone="purple"}

**Definition 0.2 (Policy $\pi$).** A **policy** $\pi : \mathcal{H} \to \Delta \mathcal{A}$ maps each history to a probability distribution over actions. Given history $\text{æ}_{<t}$:

- $\pi(\cdot \mid \text{æ}_{<t})$ is a distribution over $\mathcal{A}$,
- $\pi(a_{t} \mid \text{æ}_{<t}) \in [0,1]$ is the probability of choosing action $a_{t}$,
- the agent samples $a_{t} \sim \pi(\cdot \mid \text{æ}_{<t})$.

A policy is **deterministic** if $\pi(a \mid \text{æ}_{<t}) \in \{0,1\}$ for all $a, \text{æ}_{<t}$. We write $\pi(\text{æ}_{i:j}) := \prod_{k=i}^{j} \pi(a_{k} \mid \text{æ}_{<k})$.

:::

^def-policy


:::callout {title="Definition" tone="purple"}

**Definition 0.3 (Environment $\nu$).** An **environment** $\nu : \mathcal{H} \times \mathcal{A} \to \Delta \mathcal{E}$ maps each history–action pair to a distribution over percepts. Given history $\text{æ}_{<t}$ and action $a_{t}$:

- $\nu(\cdot \mid \text{æ}_{<t}a_{t})$ is a distribution over $\mathcal{E}$,
- $\nu(e_{t} \mid \text{æ}_{<t}a_{t}) \in [0,1]$ is the probability of percept $e_{t}$,
- the environment samples $e_{t} \sim \nu(\cdot \mid \text{æ}_{<t}a_{t})$.

We write $\nu(\text{æ}_{i:j}) := \prod_{k=i}^{j} \nu(e_{k} \mid \text{æ}_{<k}a_{k})$. This satisfies the chain rule: $\nu(\text{æ}_{i:j}) = \nu(\text{æ}_{i:j-1}) \cdot \nu(e_{j} \mid \text{æ}_{i:j-1}a_{j})$ or in the form we will usually use, $\nu(\text{æ}_{1:t}) = \nu(\text{æ}_{<t}) \cdot \nu(e_{t} \mid \text{æ}_{<t}a_{t})$. An environment is **deterministic** if $\nu(e_{t} \mid \text{æ}_{<t}a_{t}) \in \{0,1\}$ for all $e_{t}, \text{æ}_{<t}, a_{t}$ (each percept is produced with certainty). We denote the true (unknown) environment by $\mu$.

:::

^def-environment


:::callout {title="Definition" tone="purple"}

**Definition 0.4 (Interaction measure $\nu^{\pi}$).** When policy $\pi$ interacts with environment $\nu$, the joint probability of a history segment $\text{æ}_{i:j}$ given past $\text{æ}_{<i}$ is

$$
\nu^{\pi}(\text{æ}_{i:j}\mid \text{æ}_{<i}) ~:=~ \prod_{k=i}^{j} \pi(a_{k} \mid \text{æ}_{<k})\, \nu(e_{k} \mid \text{æ}_{<k}a_{k}).
$$

:::

^def-interaction


\## 0. Properties of Measures

:::callout {title="Exercise" tone="blue"}
**Exercise 0.1 (Factorization) [05].** Show that $\nu^{\pi}(\text{æ}_{1:t}) = \pi(\text{æ}_{1:t}) \cdot \nu(\text{æ}_{1:t})$.
:::

^prob-factorization


:::callout {title="Solution" tone="green" collapse="closed"}

Expanding the definition: $\nu^{\pi}(\text{æ}_{1:t}) = \prod_{k=1}^{t} \pi(a_{k} \mid \text{æ}_{<k})\, \nu(e_{k} \mid \text{æ}_{<k}a_{k}) = \underbrace{\prod_{k=1}^t \pi(a_k \mid \text{æ}_{<k})}_{\pi(\text{æ}_{1:t})}\cdot \underbrace{\prod_{k=1}^t \nu(e_k \mid \text{æ}_{<k} a_k)}_{\nu(\text{æ}_{1:t})}$.

Key observation: $\pi(\text{æ}_{1:t})$ is the same regardless of the environment. When comparing $\nu^{\pi}$ and $\mu^{\pi}$, the policy factors cancel.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 0.2 (Chain rule) [05].** Show that $\nu(\text{æ}_{1:t}) = \nu(\text{æ}_{<t}) \cdot \nu(e_{t} \mid \text{æ}_{<t}a_{t})$.
:::

^prob-chain-rule


:::callout {title="Solution" tone="green" collapse="closed"}

From the definition $\nu(\text{æ}_{1:t}) = \prod_{k=1}^{t} \nu(e_{k} \mid \text{æ}_{<k}a_{k})$, split off the last factor:

$$
\nu(\text{æ}_{1:t}) ~=~ \prod_{k=1}^{t-1}\nu(e_{k} \mid \text{æ}_{<k}a_{k}) \cdot \nu(e_{t} \mid \text{æ}_{<t}a_{t}) ~=~ \nu(\text{æ}_{<t}) \cdot \nu(e_{t} \mid \text{æ}_{<t}a_{t}).
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 0.3 (∗) (Marginalizing percepts) [03].** Show that $\sum_{e_t}\nu^{\pi}(a_{t} e_{t} \mid \text{æ}_{<t}) = \pi(a_{t} \mid \text{æ}_{<t})$.
:::

^prob-marginal-percepts


:::callout {title="Solution" tone="green" collapse="closed"}

From [[#^def-interaction|Theorem 0.4]], the one-step interaction is $\nu^{\pi}(a_{t} e_{t} \mid \text{æ}_{<t}) = \pi(a_{t} \mid \text{æ}_{<t})\, \nu(e_{t} \mid \text{æ}_{<t}a_{t})$. Summing over $e_{t}$:

$$
\sum_{e_t}\nu^{\pi}(a_{t} e_{t} \mid \text{æ}_{<t}) ~=~ \pi(a_{t} \mid \text{æ}_{<t}) \underbrace{\sum_{e_t} \nu(e_t \mid \text{æ}_{<t} a_t)}_{=\,1}~=~ \pi(a_{t} \mid \text{æ}_{<t}).
$$

Interpretation: after summing out the environment's response, only the agent's action probability remains.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 0.4 (∗) (Deterministic interaction measure) [05].** Let $\pi$ be a deterministic policy, i.e. at each history $\text{æ}_{<k}$ there is a unique action $a^{*}_{k}$ with $\pi(a^{*}_{k} \mid \text{æ}_{<k}) = 1$. Show that, provided $\text{æ}_{i:j}$ is consistent with $\pi$ (i.e. $a_{k} = a^{*}_{k}$ for every $k \in \{i, \ldots, j\}$):

$$
\nu^{\pi}(\text{æ}_{i:j}\mid \text{æ}_{<i}) ~=~ \nu(\text{æ}_{i:j}\mid \text{æ}_{<i}),
$$

i.e. on $\pi$-consistent futures the interaction measure reduces to the environment measure: every policy factor is $1$.
:::

^prob-det-interaction


:::callout {title="Solution" tone="green" collapse="closed"}

Since $\pi$ is deterministic, $\pi(a_{k} \mid \text{æ}_{<k}) = \llbracket a_{k} = a^{*}_{k} \rrbracket$. By hypothesis $\text{æ}_{i:j}$ is $\pi$-consistent, so every such bracket equals $1$. From [[#^def-interaction|Theorem 0.4]]:

$$
\nu^{\pi}(\text{æ}_{i:j}\mid \text{æ}_{<i}) ~=~ \prod_{k=i}^{j} \underbrace{\pi(a_k \mid \text{æ}_{<k})}_{=\, 1}\, \nu(e_{k} \mid \text{æ}_{<k}a_{k}) ~=~ \prod_{k=i}^{j} \nu(e_{k} \mid \text{æ}_{<k}\, a_{k}) ~=~ \nu(\text{æ}_{i:j}\mid \text{æ}_{<i}),
$$

where the last equality is the natural segment extension of $\nu(\text{æ}_{1:t}) := \prod_{k=1}^{t} \nu(e_{k} \mid \text{æ}_{<k}a_{k})$.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 0.5 [05].** (General chain rule for $\nu^{\pi}$) Show that for any $p \leq q \leq r$:

$$
\nu^{\pi}(\text{æ}_{p:r}\mid \text{æ}_{<p}) ~=~ \nu^{\pi}(\text{æ}_{p:q}\mid \text{æ}_{<p}) \cdot \nu^{\pi}(\text{æ}_{q+1:r}\mid \text{æ}_{<p}\, \text{æ}_{p:q}).
$$
:::

^prob-chain-rule-nupi


:::callout {title="Solution" tone="green" collapse="closed"}

Split the defining product $\nu^{\pi}(\text{æ}_{p:r}\mid \text{æ}_{<p}) = \prod_{k=p}^{r} \pi(a_{k} \mid \text{æ}_{<k})\, \nu(e_{k} \mid \text{æ}_{<k}a_{k})$ at index $q$:

$$
\begin{aligned}\nu^{\pi}(\text{æ}_{p:r}\mid \text{æ}_{<p}) ~&=~ \prod_{k=p}^{r} \pi(a_{k} \mid \text{æ}_{<k})\, \nu(e_{k} \mid \text{æ}_{<k}a_{k})\\ ~&=~ \underbrace{\prod_{k=p}^{q} \pi(a_k \mid \text{æ}_{<k})\, \nu(e_k \mid \text{æ}_{<k} a_k)}_{\nu^\pi(\text{æ}_{p:q} \mid \text{æ}_{<p})}\;\cdot\; \underbrace{\prod_{k=q+1}^{r} \pi(a_k \mid \text{æ}_{<k})\, \nu(e_k \mid \text{æ}_{<k} a_k)}_{\nu^\pi(\text{æ}_{q+1:r} \mid \text{æ}_{<p}\, \text{æ}_{p:q})},\end{aligned}
$$

identifying each block as a conditional via the same expansion: the past for step $k \geq q+1$ is the given history $\text{æ}_{<p}$ extended by the first chunk $\text{æ}_{p:q}$.

Note: for a deterministic policy, [[#^prob-det-interaction|Exercise 0.4]] simplifies this further: each factor $\pi(a_{k} \mid \text{æ}_{<k})\, \nu(e_{k} \mid \text{æ}_{<k}a_{k})$ becomes just $\nu(e_{k} \mid \text{æ}_{<k}\, a^{*}_{k})$.

:::

\## The Bayesian Mixture and Value Function

:::callout {title="Definition" tone="purple"}

**Definition 0.1 (Model class, prior, and Bayesian mixture $\xi$).** Let $\mathcal{M} = \{\nu_{1}, \nu_{2}, \ldots\}$ be a countable class of environments with prior weights $w_{\nu} > 0$ satisfying $\sum_{\nu \in \mathcal{M}}w_{\nu} \leq 1$. We assume $\mu \in \mathcal{M}$.

The **Bayesian mixture** $\xi$ is defined as

$$
\xi(\text{æ}_{1:t}) := \sum_{\nu \in \mathcal{M}}w_{\nu}\, \nu(\text{æ}_{1:t}) \quad \text{ and }\quad \xi(e_{t} \mid \text{æ}_{<t}a_{t}) := \xi(\text{æ}_{1:t}) / \xi(\text{æ}_{<t}).
$$

One can show that the one-step predictive distribution can be written as

$$
\xi(e_{t} \mid \text{æ}_{<t}a_{t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, \nu(e_{t} \mid \text{æ}_{<t}a_{t}),
$$

where the **posterior weight** is

$$
w(\nu \mid \text{æ}_{<t}) ~:=~ w_{\nu} \,\frac{\nu(\text{æ}_{<t})}{\xi(\text{æ}_{<t})}, \qquad w(\nu \mid \epsilon) := w_{\nu}.
$$

See [[#A. Worked Example: Bayesian Mixture|Appendix A]] for a worked example.

:::

^def-mixture


:::callout {title="Definition" tone="purple"}

**Definition 0.2 (Expectation $\mathbb{E}_{\nu}^{\pi}$).** For a function $f : \mathcal{H} \to \mathbb{R}$ of a finite future segment $\text{æ}'_{t:m}$:

$$
\mathbb{E}_{\nu}^{\pi}[f \mid \text{æ}_{<t}] ~:=~ \underset{\text{æ}_{t:m} \sim \nu^\pi(\cdot \mid \text{æ}_{<t})}{\mathbb{E}}[f] ~=~ \sum_{\text{æ}'_{t:m}}\nu^{\pi}(\text{æ}'_{t:m}\mid \text{æ}_{<t})\, f(\text{æ}'_{t:m}).
$$

For functions $f$ of the infinite future (like the value function), with a sequence $f_{1}, f_{2}, \ldots \to f$, where $f_{m}$ depends only on $\text{æ}'_{t:m}$, we define $\mathbb{E}_{\nu}^{\pi}[f \mid \text{æ}_{<t}] := \lim_{m \to \infty}\mathbb{E}_{\nu}^{\pi}[f_{m} \mid \text{æ}_{<t}]$,

:::

^def-expectation


:::callout {title="Definition" tone="purple"}

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

^def-return


:::callout {title="Definition" tone="purple"}

**Definition 0.4 (Value function[^1]).** The **value** of policy $\pi$ in environment $\nu$ with horizon $m \geq t$ given history $\text{æ}_{<t}$ is

$$
\begin{aligned}&V_{\nu}^{\pi,m}(\text{æ}_{<t}) ~:=~ (1-\gamma)\, \mathbb{E}_{\nu}^{\pi}\!\left[G_{t-1:m}\mid \text{æ}_{<t}\right] \\ ~&=~ (1-\gamma) \sum_{\text{æ}_{t:m}}\nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t})\, G_{t-1:m}\\ ~&=~ (1-\gamma) \sum_{\text{æ}_{t:m}}\nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}) \left[ \sum_{k=t}^{m}\gamma^{k-t}r_{k} \right].\end{aligned}
$$

The **infinite-horizon value** is the pointwise limit $V_{\nu}^{\pi,\infty}(\text{æ}_{<t}) := \lim_{m \to \infty}V_{\nu}^{\pi,m}(\text{æ}_{<t}) = (1-\gamma)\, \mathbb{E}_{\nu}^{\pi}[G_{\geq t-1}\mid \text{æ}_{<t}]$. We write $V_{\nu}^{\pi} \equiv V_{\nu}^{\pi,\infty}$ for short.

The **optimal value** is $V_{\nu}^{*,m}(\text{æ}_{<t}) := \sup_{\pi} V_{\nu}^{\pi,m}(\text{æ}_{<t})$ for $m \in \mathbb{N}\cup \{\infty\}$, with $V_{\nu}^{*} \equiv V_{\nu}^{*,\infty}$. [^2] An **optimal policy** $\pi_{\nu}^{*}$ satisfies $V_{\nu}^{\pi_\nu^*}= V_{\nu}^{*}$. The **Bayes-optimal policy** is $\pi_{\xi}^{*} \in \operatorname*{arg\,max}_{\pi} V_{\xi}^{\pi}$.

:::

^def-value


:::callout {title="Note" tone="neutral"}

**AIXI.** All results in this sheet hold for any countable $\mathcal{M}$ and prior weights $w_{\nu}$. **AIXI** is a special case of the Bayes-optimal policy $\pi_{\xi}^{*}$ for the particular choice $\mathcal{M} :=$ the class of all lower-semicomputable chronological semimeasures, and prior $w_{\nu} := 2^{-K(\nu)}$, where $K(\nu)$ is the Kolmogorov complexity of $\nu$: the length of the shortest program that computes $\nu$. The resulting agent is written $\pi^{*}_{\xi_U}$, or simply AI$\xi$.

**Why this $\mathcal{M}$?** By including every computable environment, the assumption $\mu \in \mathcal{M}$ reduces to "the universe is computable": as weak an assumption as one can make.

**Why this prior?** The prior $2^{-K(\nu)}$ is *dominant*: for any other computable prior $w'_{\nu}$, there exists a constant $c > 0$ such that $2^{-K(\nu)}\geq c \cdot w'_{\nu}$ for all $\nu$. S

**Caveat:** The constant $c$ depends on the choice of universal Turing machine $U$, and adversarial choices of $U$ can make AIXI behave arbitrarily badly ([[#^bib-leike-15badpriors|Leike & Hutter 2015]]).

See ([[#^bib-hutter-24uaibook2|Hutter et al. 2024]]): Chapter 2.7 for Kolmogorov complexity, Chapters 3.7–3.8 for the model class and universal prior, and Chapter 7.4 for AIXI itself.

:::

\## 1. Properties of the Bayesian Mixture

:::callout {title="Exercise" tone="blue"}
**Exercise 1.1 (∗) (Posterior update) [10].** Show that the posterior updates multiplicatively:

$$
w(\nu \mid \text{æ}_{1:t}) ~=~ w(\nu \mid \text{æ}_{<t}) \frac{\nu(e_{t} \mid \text{æ}_{<t}a_{t})}{\xi(e_{t} \mid \text{æ}_{<t}a_{t})}.
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Use the definitions of $w(\nu \mid \text{æ}_{1:t})$ and $w(\nu \mid \text{æ}_{<t})$, and apply [[#^prob-chain-rule|Exercise 0.2]].

::::
:::

^prob-posterior-update


:::callout {title="Solution" tone="green" collapse="closed"}

From the definition: $w(\nu \mid \text{æ}_{1:t}) = w_{\nu} \cdot \nu(\text{æ}_{1:t})/\xi(\text{æ}_{1:t})$ and $w(\nu \mid \text{æ}_{<t}) = w_{\nu} \cdot \nu(\text{æ}_{<t})/\xi(\text{æ}_{<t})$.

Dividing:

$$
\frac{w(\nu \mid \text{æ}_{1:t})}{w(\nu \mid \text{æ}_{<t})}= \frac{\nu(\text{æ}_{1:t})}{\nu(\text{æ}_{<t})}\cdot \frac{\xi(\text{æ}_{<t})}{\xi(\text{æ}_{1:t})}= \frac{\nu(e_{t} \mid \text{æ}_{<t}a_{t})}{\xi(e_{t} \mid \text{æ}_{<t}a_{t})},
$$

where we used the chain rule ([[#^prob-chain-rule|Exercise 0.2]]) for both $\nu$ and $\xi$.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 1.2 [15].** (One-step predictive distribution of $\xi$) Starting from $\xi(\text{æ}_{1:t}) = \sum_{\nu \in \mathcal{M}}w_{\nu} \nu(\text{æ}_{1:t})$, derive the one-step predictive form:

$$
\xi(e_{t} \mid \text{æ}_{<t}a_{t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, \nu(e_{t} \mid \text{æ}_{<t}a_{t}).
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Write $\xi(e_{t} \mid \text{æ}_{<t}a_{t}) = \xi(\text{æ}_{1:t}) / \xi(\text{æ}_{<t})$, expand the numerator, and use [[#^prob-chain-rule|Exercise 0.2]].

::::
:::

^prob-one-step


:::callout {title="Solution" tone="green" collapse="closed"}

The one-step conditional is the ratio of joint to marginal: $\xi(e_{t} \mid \text{æ}_{<t}a_{t}) := \xi(\text{æ}_{1:t})/\xi(\text{æ}_{<t})$.

Expanding the numerator using $\xi(\text{æ}_{1:t}) = \sum_{\nu} w_{\nu} \nu(\text{æ}_{1:t})$:

$$
\begin{aligned}\xi(e_{t} \mid \text{æ}_{<t}a_{t}) ~&=~ \frac{\sum_{\nu \in \mathcal{M}}w_{\nu}\, \nu(\text{æ}_{1:t})}{\xi(\text{æ}_{<t})}\\[4pt] ~&=~ \frac{\sum_{\nu}w_{\nu}\, \nu(\text{æ}_{<t}) \cdot \nu(e_{t} \mid \text{æ}_{<t}a_{t})}{\xi(\text{æ}_{<t})}\qquad \text{(chain rule, Exercise 0.2)}\\[4pt] ~&=~ \sum_{\nu}\underbrace{\frac{w_{\nu}\, \nu(\text{æ}_{<t})}{\xi(\text{æ}_{<t})}}_{= \, w(\nu \mid \text{æ}_{<t})}\cdot\, \nu(e_{t} \mid \text{æ}_{<t}a_{t}) \\[4pt] ~&=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, \nu(e_{t} \mid \text{æ}_{<t}a_{t}).\end{aligned}
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 1.3 (Bounded value) [10].** Show that $V_{\nu}^{\pi,m}(\text{æ}_{<t}) \in [0,1]$ for any $\nu, \pi, m \in \mathbb{N}\cup \{\infty\}, \text{æ}_{<t}$.

::::callout {title="Hint" tone="amber" collapse="closed"}

Recall the formula for geometric series: $(1-\gamma)\sum_{k=0}^{n}\gamma^{k} = 1 - \gamma^{n+1}$.

::::
:::

^prob-bounded-value


:::callout {title="Solution" tone="green" collapse="closed"}

Since $r_{k} \in [0,1]$, each discounted reward sum is bounded:

$$
0 ~\leq~ (1-\gamma)\, G_{t-1:m}~\leq~ (1-\gamma)\sum_{k=t}^{m}\gamma^{k-t}~=~ 1 - \gamma^{m-t+1}~\leq~ 1.
$$

The interaction measure satisfies $\nu^{\pi}(\text{æ}'_{t:m}\mid \text{æ}_{<t}) \geq 0$ and $\sum_{\text{æ}'_{t:m}}\nu^{\pi}(\text{æ}'_{t:m}\mid \text{æ}_{<t}) = 1$, so the value function is a weighted average of terms in $[0,1]$:

$$
0 ~\leq~ V_{\nu}^{\pi,m}(\text{æ}_{<t}) ~=~ \sum_{\text{æ}'_{t:m}}\nu^{\pi}(\text{æ}'_{t:m}\mid \text{æ}_{<t})\, (1-\gamma)\, G_{t-1:m}~\leq~ 1.
$$

For $m = \infty$: since $0 \leq V_{\nu}^{\pi,m}(\text{æ}_{<t}) \leq 1$ for all finite $m$, the limit $V_{\nu}^{\pi}(\text{æ}_{<t}) = \lim_{m \to \infty}V_{\nu}^{\pi,m}(\text{æ}_{<t})$ also lies in $[0,1]$.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 1.4 (∗) [15].** (Multi-step posterior linearity of $\xi^{\pi}$) Extend [[#^prob-one-step|Exercise 1.2]] to multi-step histories: show that for finite $m \geq t$,

$$
\xi^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, \nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}).
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Apply the general chain rule ([[#^prob-chain-rule-nupi|Exercise 0.5]]) to $\xi(\text{æ}_{1:m}) = \sum_{\nu} w_{\nu} \nu(\text{æ}_{1:m})$, then use factorization ([[#^prob-factorization|Exercise 0.1]]).

::::
:::

^prob-multi-step-xi


:::callout {title="Solution" tone="green" collapse="closed"}

Start from the definition $\xi(\text{æ}_{1:m}) = \sum_{\nu \in \mathcal{M}}w_{\nu}\, \nu(\text{æ}_{1:m})$. Apply the general chain rule ([[#^prob-chain-rule-nupi|Exercise 0.5]]) to both sides: $\xi(\text{æ}_{1:m}) = \xi(\text{æ}_{<t}) \cdot \xi(\text{æ}_{t:m}\mid \text{æ}_{<t})$ and $\nu(\text{æ}_{1:m}) = \nu(\text{æ}_{<t}) \cdot \nu(\text{æ}_{t:m}\mid \text{æ}_{<t})$. Dividing by $\xi(\text{æ}_{<t})$:

$$
\xi(\text{æ}_{t:m}\mid \text{æ}_{<t}) ~=~ \sum_{\nu \in \mathcal{M}}\frac{w_{\nu}\, \nu(\text{æ}_{<t})}{\xi(\text{æ}_{<t})}\nu(\text{æ}_{t:m}\mid \text{æ}_{<t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, \nu(\text{æ}_{t:m}\mid \text{æ}_{<t}).
$$

Now multiply both sides by $\pi(\text{æ}_{t:m}\mid \text{æ}_{<t})$. By factorization ([[#^prob-factorization|Exercise 0.1]]), $\pi(\text{æ}_{t:m}\mid \text{æ}_{<t}) \cdot \xi(\text{æ}_{t:m}\mid \text{æ}_{<t}) = \xi^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t})$ and likewise for each $\nu$:

$$
\xi^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, \nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}).
$$

:::

\## 2. Existence of Optimal Policies

Recall that $V_{\nu}^{*}(\text{æ}_{<t}) := \sup_{\pi} V_{\nu}^{\pi}(\text{æ}_{<t})$ is defined as a supremum over all policies. In general, a supremum need not be achieved: for example, $\sup_{x \in (0,1)}x = 1$, but no $x \in (0,1)$ attains this value. This problem shows that in our setting, the supremum *is* attained, so an optimal policy $\pi_{\nu}^{*}$ with $V_{\nu}^{\pi_\nu^*}= V_{\nu}^{*}$ exists.

:::callout {title="Exercise" tone="blue"}
**Exercise 2.1 [05].** Consider a single time step. Given history $\text{æ}_{<t}$ and a function $Q : \mathcal{A} \to \mathbb{R}$, show that $\sup_{\pi} \sum_{a \in \mathcal{A}}\pi(a \mid \text{æ}_{<t})\, Q(a) = \max_{a \in \mathcal{A}}Q(a)$, and that the supremum is attained by the deterministic policy that places all probability on an action achieving the maximum.
:::

^prob-sup-eq-max


:::callout {title="Solution" tone="green" collapse="closed"}

Let $a^{*} \in \operatorname*{arg\,max}_{a' \in \mathcal{A}}Q(a')$, which exists because $\mathcal{A}$ is finite. So $Q(a^{*}) = \max_{a'}Q(a')$.

*Upper bound.* For any $\pi$: $\sum_{a} \pi(a \mid \text{æ}_{<t}) Q(a) \leq \sum_{a} \pi(a \mid \text{æ}_{<t}) Q(a^{*}) = Q(a^{*})$.

*Lower bound.* The deterministic $\pi^{*}$ with $\pi^{*}(a^{*} \mid \text{æ}_{<t}) = 1$ achieves $Q(a^{*})$.

Combining: $\sup_{\pi} \sum_{a} \pi(a) Q(a) = Q(a^{*}) = \max_{a'}Q(a')$, attained by $\pi^{*}$.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 2.2 (Bellman equation) [15].** Show that for finite $m$ and $t \leq m$:

$$
V_{\nu}^{\pi,m}(\text{æ}_{<t}) ~=~ \sum_{\text{æ}'_t}\nu^{\pi}(\text{æ}'_{t} \mid \text{æ}_{<t}) \Big[(1-\gamma)\, r'_{t} ~+~ \gamma\, V_{\nu}^{\pi,m}(\text{æ}_{<t}\, \text{æ}'_{t})\Big],
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Use the general chain rule ([[#^prob-chain-rule-nupi|Exercise 0.5]]) to peel off the *first* step,

$$
\nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}) ~=~ \nu^{\pi}(\text{æ}_{t} \mid \text{æ}_{<t}) \cdot \nu^{\pi}(\text{æ}_{t+1:m}\mid \text{æ}_{1:t}).
$$

Break up the sum $\sum_{\text{æ}_{t:m}}= \sum_{\text{æ}_t}\sum_{\text{æ}_{t+1:m}}$, and factor out $r'_{t}$ using $\sum_{\text{æ}'_{t+1:m}}\nu^{\pi}(\text{æ}'_{t+1:m}\mid \text{æ}) = 1$ for any history $\text{æ}$.

::::
:::

^prob-bellman-finite


:::callout {title="Solution" tone="green" collapse="closed"}

*Step 1: Factor the future.* Write $\text{æ}'_{t:m}= \text{æ}'_{t}\, \text{æ}'_{t+1:m}$: $\nu^{\pi}(\text{æ}'_{t:m}\mid \text{æ}_{<t}) = \nu^{\pi}(\text{æ}'_{t} \mid \text{æ}_{<t}) \cdot \nu^{\pi}(\text{æ}'_{t+1:m}\mid \text{æ}_{<t}\, \text{æ}'_{t})$.

*Step 2: Split the reward sum.* This is just the return recursion ([[#^def-return|Theorem 0.3]]): $G_{t-1:m}= r'_{t} + \gamma\, G_{t:m}$, where $G_{t-1:m}= \sum_{k=t}^{m}\gamma^{k-t}r'_{k}$ is the return given $\text{æ}_{<t}$.

*Step 3: Substitute into the definition of $V_{\nu}^{\pi,m}(\text{æ}_{<t})$.*

$$
\begin{aligned}V_{\nu}^{\pi,m}(\text{æ}_{<t}) ~&=~ (1-\gamma) \sum_{\text{æ}'_t}\nu^{\pi}(\text{æ}'_{t} \mid \text{æ}_{<t}) \sum_{\text{æ}'_{t+1:m}}\nu^{\pi}(\text{æ}'_{t+1:m}\mid \text{æ}_{<t}\, \text{æ}'_{t}) \left[ r'_{t} + \gamma G_{t:m}\right].\end{aligned}
$$

Consider the inner term $\sum_{\text{æ}'_{t+1:m}}\nu^{\pi}(\text{æ}'_{t+1:m}\mid \text{æ}_{<t}\, \text{æ}'_{t}) \left[ r'_{t} + \gamma G_{t:m}\right]$. We can expand as:

$$
\begin{aligned}&= \sum_{\text{æ}'_{t+1:m}}\nu^{\pi}(\text{æ}'_{t+1:m}\mid \text{æ}_{<t}\, \text{æ}'_{t}) r'_{t} + \gamma \sum_{\text{æ}'_{t+1:m}}\nu^{\pi}(\text{æ}'_{t+1:m}\mid \text{æ}_{<t}\, \text{æ}'_{t}) G_{t:m}\\&= r'_{t} \cancel{\sum_{\text{æ}'_{t+1:m}} \nu^\pi(\text{æ}'_{t+1:m} \mid \text{æ}_{<t}\, \text{æ}'_t)}+ \gamma \sum_{\text{æ}'_{t+1:m}}\nu^{\pi}(\text{æ}'_{t+1:m}\mid \text{æ}_{<t}\, \text{æ}'_{t}) G_{t:m}\\&= r'_{t} + \gamma \sum_{\text{æ}'_{t+1:m}}\nu^{\pi}(\text{æ}'_{t+1:m}\mid \text{æ}_{<t}\, \text{æ}'_{t}) G_{t:m}\end{aligned}
$$

as $r'_{t}$ doesn't depend on $\text{æ}'_{t+1:m}$, and $\sum_{\text{æ}'_{t+1:m}}\nu^{\pi}(\text{æ}'_{t+1:m}\mid \text{æ}_{<t}\, \text{æ}'_{t}) = 1$. Inserting this above, we obtain:

$$
\begin{aligned}V_{\nu}^{\pi,m}(\text{æ}_{<t})&= \sum_{\text{æ}'_t}\nu^{\pi}(\text{æ}'_{t} \mid \text{æ}_{<t}) \bigg[ (1-\gamma)\, r'_{t} + \gamma\, \underbrace{(1-\gamma) \sum_{\text{æ}'_{t+1:m}} \nu^\pi(\text{æ}'_{t+1:m} \mid \text{æ}_{<t}\, \text{æ}'_t)G_{t:m}}_{=\; V_\nu^{\pi,m}(\text{æ}_{<t}\, \text{æ}'_t)}\bigg].\end{aligned}
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 2.3 (∗) (Backward induction) [20].** Using the Bellman equation from [[#^prob-bellman-finite|Exercise 2.2]] and [[#^prob-sup-eq-max|Exercise 2.1]], show by backward induction on $t = m, m-1, \ldots, 1$ that for each finite $m$, a deterministic optimal policy exists.
:::

^prob-backward-induction


:::callout {title="Solution" tone="green" collapse="closed"}

We induct on $t = m, m-1, \ldots, 1$, showing that for every history $\text{æ}_{<t}$, a deterministic policy achieves $V_{\nu}^{*,m}(\text{æ}_{<t})$.

*Base case ($t = m$):* At $t = m$ the continuation term vanishes (the value from time $m+1$ is an empty sum), so the Bellman equation gives $V_{\nu}^{\pi,m}(\text{æ}_{<m}) = (1-\gamma) \sum_{\text{æ}'_m}\nu^{\pi}(\text{æ}'_{m} \mid \text{æ}_{<m})\, r'_{m}$. Splitting the step $\text{æ}'_{m} = a'_{m} e'_{m}$ via $\nu^{\pi}(\text{æ}'_{m} \mid \text{æ}_{<m}) = \pi(a'_{m} \mid \text{æ}_{<m})\, \nu(e'_{m} \mid \text{æ}_{<m}a'_{m})$ gives $V_{\nu}^{\pi,m}(\text{æ}_{<m}) = (1-\gamma) \sum_{a'_m}\pi(a'_{m} \mid \text{æ}_{<m}) \sum_{e'_m}\nu(e'_{m} \mid \text{æ}_{<m}a'_{m})\, r'_{m}$. This has the form $\sum_{a} \pi(a) Q(a)$ with $Q(a) = (1-\gamma)\sum_{e'_m}\nu(e'_{m} \mid \text{æ}_{<m}a)\, r'_{m}$, which is independent of $\pi$. By [[#^prob-sup-eq-max|Exercise 2.1]], the supremum over $\pi$ is $\max_{a} Q(a)$, attained by the deterministic policy playing $a^{*} \in \operatorname*{arg\,max}_{a} Q(a)$.

*Inductive step:* Suppose that for every history of length $t$, there exists a deterministic policy $\pi^{*}_{t+1}$ achieving $V_{\nu}^{\pi^*_{t+1},m}= V_{\nu}^{*,m}$ from time $t+1$ onwards. Substituting this optimal continuation into the Bellman equation from [[#^prob-bellman-finite|Exercise 2.2]] gives

$$
V_{\nu}^{\pi,m}(\text{æ}_{<t}) ~=~ \sum_{\text{æ}'_t}\nu^{\pi}(\text{æ}'_{t} \mid \text{æ}_{<t}) \big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}(\text{æ}_{<t}\, \text{æ}'_{t})\big].
$$

Splitting the step $\text{æ}'_{t} = a'_{t} e'_{t}$ via $\nu^{\pi}(\text{æ}'_{t} \mid \text{æ}_{<t}) = \pi(a'_{t} \mid \text{æ}_{<t})\, \nu(e'_{t} \mid \text{æ}_{<t}a'_{t})$ and grouping the percept sum into the action weight:

$$
V_{\nu}^{\pi,m}(\text{æ}_{<t}) ~=~ \sum_{a'_t}\pi(a'_{t} \mid \text{æ}_{<t})\, Q(a'_{t}),
$$

where $Q(a'_{t}) := \sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a'_{t}) [(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}(\text{æ}_{<t}\, a'_{t}\, e'_{t})]$ is independent of $\pi$ (the continuation value $V_{\nu}^{*,m}$ is fixed by the inductive hypothesis). By [[#^prob-sup-eq-max|Exercise 2.1]], $\sup_{\pi} \sum_{a'_t}\pi(a'_{t})\, Q(a'_{t}) = \max_{a'_t}Q(a'_{t})$, attained by the deterministic policy playing $a^{*}_{t} \in \operatorname*{arg\,max}_{a'_t}Q(a'_{t})$ at time $t$, then following $\pi^{*}_{t+1}$.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 2.4 (Bellman optimality equation) [10].** Using [[#^prob-backward-induction|Exercise 2.3]], show that for finite $m$:

$$
V_{\nu}^{*,m}(\text{æ}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} ~+~ \gamma\, V_{\nu}^{*,m}(\text{æ}_{<t}\, \text{æ}'_{t})\Big].
$$

where $e_{t}' = o_{t}' r_{t}'$ and $\text{æ}'_{t} = a'_{t} e'_{t}$.
:::

^prob-bellman-opt


:::callout {title="Solution" tone="green" collapse="closed"}

By [[#^prob-backward-induction|Exercise 2.3]], a deterministic optimal policy $\pi^{*}_{\nu}$ exists with $V_{\nu}^{\pi^*_\nu,m}= V_{\nu}^{*,m}$. Substituting $\pi = \pi^{*}_{\nu}$ into the Bellman equation from [[#^prob-bellman-finite|Exercise 2.2]] (using $V_{\nu}^{\pi^*_\nu,m}= V_{\nu}^{*,m}$ on both sides):

$$
V_{\nu}^{*,m}(\text{æ}_{<t}) ~=~ \sum_{\text{æ}'_t}\nu^{\pi^*_\nu}(\text{æ}'_{t} \mid \text{æ}_{<t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}(\text{æ}_{<t}\, \text{æ}'_{t})\Big].
$$

Splitting the step $\text{æ}'_{t} = a'_{t} e'_{t}$ via $\nu^{\pi^*_\nu}(\text{æ}'_{t} \mid \text{æ}_{<t}) = \pi^{*}_{\nu}(a'_{t} \mid \text{æ}_{<t})\, \nu(e'_{t} \mid \text{æ}_{<t}a'_{t})$:

$$
V_{\nu}^{*,m}(\text{æ}_{<t}) ~=~ \sum_{a'_t}\pi^{*}_{\nu}(a'_{t} \mid \text{æ}_{<t}) \sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}(\text{æ}_{<t}\, a'_{t}\, e'_{t})\Big].
$$

Since $\pi^{*}_{\nu}$ is deterministic, let $a^{*}_{t}$ denote the unique action with $\pi^{*}_{\nu}(a^{*}_{t} \mid \text{æ}_{<t}) = 1$. Then:

$$
V_{\nu}^{*,m}(\text{æ}_{<t}) ~=~ \sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a^{*}_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}(\text{æ}_{<t}\, a^{*}_{t}\, e'_{t})\Big].
$$

Define $Q(a) := \sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a) [(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}(\text{æ}_{<t}\, a\, e'_{t})]$. Then $V_{\nu}^{*,m}(\text{æ}_{<t}) = Q(a^{*}_{t})$. We must have $Q(a^{*}_{t}) = \max_{a}Q(a)$: if some $\tilde{a}$ had $Q(\tilde{a}) > Q(a^{*}_{t})$, then the policy that plays $\tilde{a}$ at $\text{æ}_{<t}$ and follows $\pi^{*}_{\nu}$ elsewhere would achieve value $Q(\tilde{a}) > V_{\nu}^{*,m}(\text{æ}_{<t})$, contradicting $V_{\nu}^{*,m}= \sup_{\pi} V_{\nu}^{\pi,m}$. Hence:

$$
V_{\nu}^{*,m}(\text{æ}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}(\text{æ}_{<t}\, a'_{t}\, e'_{t})\Big].
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 2.5 (∗) [15].** (Existence of $V_{\nu}^{*}$) Show that the pointwise limit $V_{\nu}^{*}(\text{æ}_{<t}) := \lim_{m \to \infty}V_{\nu}^{*,m}(\text{æ}_{<t})$ exists for all histories $\text{æ}_{<t}$.

::::callout {title="Hint" tone="amber" collapse="closed"}

Show $V_{\nu}^{*,m+1}(\text{æ}_{<t}) \geq V_{\nu}^{*,m}(\text{æ}_{<t})$ by expanding $V_{\nu}^{*,m+1}$. Use this and [[#^prob-bounded-value|Exercise 1.3]] and [Monotone Convergence Theorem](https://en.wikipedia.org/wiki/Monotone_convergence_theorem) to obtain the result.

::::
:::

^prob-inf-horizon


:::callout {title="Solution" tone="green" collapse="closed"}

We show $V_{\nu}^{*,m+1}(\text{æ}_{<t}) \geq V_{\nu}^{*,m}(\text{æ}_{<t})$ for all $\text{æ}_{<t}$. Since $V_{\nu}^{*,m+1}= \sup_{\pi} V_{\nu}^{\pi,m+1}$, it suffices to show $V_{\nu}^{\pi,m+1}(\text{æ}_{<t}) \geq V_{\nu}^{\pi,m}(\text{æ}_{<t})$ for every $\pi$. Expanding the definition:

$$
\begin{aligned}&V_{\nu}^{\pi,m+1}(\text{æ}_{<t}) \\ ~&=~ (1-\gamma) \sum_{\text{æ}_{t:m+1}}\nu^{\pi}(\text{æ}_{t:m+1}\mid \text{æ}_{<t})\, G_{t-1:m+1}\\ ~&=~ (1-\gamma) \sum_{\text{æ}_{t:m+1}}\nu^{\pi}(\text{æ}_{t:m+1}\mid \text{æ}_{<t}) \left[G_{t-1:m}~+~ \gamma^{m+1-t}r_{m+1}\right] \\ ~&=~ (1-\gamma) \sum_{\text{æ}_{t:m+1}}\nu^{\pi}(\text{æ}_{t:m+1}\mid \text{æ}_{<t}) G_{t-1:m}\\ ~&\qquad+~ \underbrace{(1-\gamma)\, \gamma^{m+1-t} \sum_{\text{æ}_{t:m+1}} \nu^\pi(\text{æ}_{t:m+1} \mid \text{æ}_{<t})\, r_{m+1}}_{\geq\; 0}.\end{aligned}
$$

For the first term, marginalize over $a_{m+1}, e_{m+1}$ (which $G_{t-1:m}$ does not depend on):

$$
\sum_{\text{æ}_{t:m+1}}\nu^{\pi}(\text{æ}_{t:m+1}\mid \text{æ}_{<t}) G_{t-1:m}~=~ \sum_{\text{æ}_{t:m}}\nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}) G_{t-1:m}.
$$

So $V_{\nu}^{\pi,m+1}(\text{æ}_{<t}) \geq (1-\gamma) \sum_{\text{æ}_{t:m}}\nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}) G_{t-1:m}= V_{\nu}^{\pi,m}(\text{æ}_{<t})$.

Since $V_{\nu}^{*,m}(\text{æ}_{<t})$ is non-decreasing in $m$ and bounded in $[0,1]$ by [[#^prob-bounded-value|Exercise 1.3]], the monotone convergence theorem gives that $V_{\nu}^{*}(\text{æ}_{<t}) := \lim_{m \to \infty}V_{\nu}^{*,m}(\text{æ}_{<t})$ exists for each $\text{æ}_{<t}$.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 2.6 (Infinite-horizon Bellman optimality equation) [10].** Show that the Bellman optimality equation ([[#^prob-bellman-opt|Exercise 2.4]]) extends to $m = \infty$:

$$
V_{\nu}^{*}(\text{æ}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} ~+~ \gamma\, V_{\nu}^{*}(\text{æ}_{<t}\, a'_{t}\, e'_{t})\Big].
$$
:::

^prob-inf-bellman-opt


:::callout {title="Solution" tone="green" collapse="closed"}

By [[#^prob-bellman-opt|Exercise 2.4]], for every finite $m$:

$$
V_{\nu}^{*,m}(\text{æ}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}(\text{æ}_{<t}\, a'_{t}\, e'_{t})\Big].
$$

By [[#^prob-inf-horizon|Exercise 2.5]], each $V_{\nu}^{*,m}(\cdot)$ converges pointwise to $V_{\nu}^{*}(\cdot)$ as $m \to \infty$. Since $\mathcal{A}$ and $\mathcal{E}$ are finite, the $\max$ and $\sum$ are over finitely many convergent terms, so:

$$
V_{\nu}^{*}(\text{æ}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*}(\text{æ}_{<t}\, a'_{t}\, e'_{t})\Big].
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 2.7 (∗) (Optimal policy for infinite horizon) [25].** Show that a deterministic policy $\pi_{\nu}^{*}$ exists achieving $V_{\nu}^{\pi_\nu^*}(\text{æ}_{<t}) = V_{\nu}^{*}(\text{æ}_{<t})$ for all $\text{æ}_{<t}$.

*Approach:*

**(a)** Define $\pi_{\nu}^{*}$ as the greedy policy (the $\operatorname*{arg\,max}$ action from [[#^prob-inf-bellman-opt|Exercise 2.6]]).

**(b)** Write two Bellman equations: one for $V_{\nu}^{*}$, one for $V_{\nu}^{\pi_\nu^*, m}$.

**(c)** Define $\Delta V_{\nu}^{m} := V_{\nu}^{*} - V_{\nu}^{\pi_\nu^*, m}$ and obtain a recursive equation for it.

**(d)** Iterate out to the finite horizon, noting $V_{\nu}^{\pi_\nu^*, m}(\text{æ}_{1:m}) = 0$ (why?)

**(e)** Bound the tail, take $m \to \infty$.
:::

^prob-inf-opt-policy


:::callout {title="Solution" tone="green" collapse="closed"}

*Step 1: Define the greedy policy.* For each history $\text{æ}_{<t}$, let

$$
a^{*}_{t} \in \operatorname*{arg\,max}_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}a'_{t}) [(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*}(\text{æ}_{<t}\, a'_{t}\, e'_{t})],
$$

which exists because $\mathcal{A}$ is finite. Define the deterministic policy $\pi_{\nu}^{*}(a \mid \text{æ}_{<t}) := \llbracket a = a^{*}_{t} \rrbracket$. By [[#^prob-inf-bellman-opt|Exercise 2.6]], the infinite-horizon Bellman optimality equation becomes:

$$
V_{\nu}^{*}(\text{æ}_{<t}) ~=~ \sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}\, a^{*}_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*}(\text{æ}_{<t}\, a^{*}_{t}\, e'_{t})\Big].
$$

*Step 2: Error recursion.* The Bellman equation ([[#^prob-bellman-finite|Exercise 2.2]]) holds for any policy, so for $\pi_{\nu}^{*}$ at finite horizon $m$:

$$
V_{\nu}^{\pi_\nu^*,m}(\text{æ}_{<t}) ~=~ \sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}\, a^{*}_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{\pi_\nu^*,m}(\text{æ}_{<t}\, a^{*}_{t}\, e'_{t})\Big].
$$

Subtracting this from the equation in Step 1, the $(1-\gamma)\, r'_{t}$ terms cancel:

$$
V_{\nu}^{*}(\text{æ}_{<t}) - V_{\nu}^{\pi_\nu^*,m}(\text{æ}_{<t}) ~=~ \gamma \sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}\, a^{*}_{t}) \Big[V_{\nu}^{*}(\text{æ}_{<t}\, a^{*}_{t}\, e'_{t}) - V_{\nu}^{\pi_\nu^*,m}(\text{æ}_{<t}\, a^{*}_{t}\, e'_{t})\Big].
$$

The error at time $t$ is $\gamma$ times a weighted average of errors at time $t+1$.

*Step 3: Iterate the contraction.* Write $\Delta V_{\nu}^{m}(\text{æ}_{<t}) := V_{\nu}^{*}(\text{æ}_{<t}) - V_{\nu}^{\pi_\nu^*,m}(\text{æ}_{<t}) \geq 0$ for the error. Step 2 gives:

$$
\Delta V_{\nu}^{m}(\text{æ}_{<t}) ~=~ \gamma \sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}\, a^{*}_{t})\, \Delta V_{\nu}^{m}(\text{æ}_{<t}\, a^{*}_{t}\, e'_{t}).
$$

Applying the same recursion at time $t+1$ (with greedy action $a^{*}_{t+1}$ at history $\text{æ}_{<t}\, a^{*}_{t}\, e'_{t}$):

$$
\Delta V_{\nu}^{m}(\text{æ}_{<t}) ~=~ \gamma^{2} \sum_{e'_t}\nu(e'_{t} \mid \text{æ}_{<t}\, a^{*}_{t}) \sum_{e'_{t+1}}\nu(e'_{t+1}\mid \text{æ}_{<t}\, a^{*}_{t}\, e'_{t}\, a^{*}_{t+1})
$$

$$
\qquad \times \Delta V_{\nu}^{m}(\text{æ}_{<t}\, a^{*}_{t}\, e'_{t}\, a^{*}_{t+1}\, e'_{t+1}).
$$

After $m - t + 1$ iterations, summing over all percept sequences $e'_{t:m}$:

$$
\Delta V_{\nu}^{m}(\text{æ}_{<t}) ~=~ \gamma^{m-t+1}\sum_{e'_{t:m}}\left(\prod_{k=t}^{m} \nu(e'_{k} \mid \text{æ}'_{<k}\, a^{*}_{k})\right) \Delta V_{\nu}^{m}(\text{æ}_{<t}\, \text{æ}'_{t:m}),
$$

where $\text{æ}'_{t:m}= a^{*}_{t}\, e'_{t}\, \cdots\, a^{*}_{m}\, e'_{m}$ is the history segment generated by $\pi_{\nu}^{*}$. By [[#^prob-det-interaction|Exercise 0.4]], the product of $\nu$-conditionals is $\nu^{\pi_\nu^*}(\text{æ}'_{t:m}\mid \text{æ}_{<t})$. At the boundary, $V_{\nu}^{\pi_\nu^*,m}(\text{æ}_{<t}\, \text{æ}'_{t:m}) = 0$ (summing over no rewards past horizon $m$), so $\Delta V_{\nu}^{m}(\text{æ}_{<t}\, \text{æ}'_{t:m}) = V_{\nu}^{*}(\text{æ}_{<t}\, \text{æ}'_{t:m}) \in [0,1]$. Therefore:

$$
\Delta V_{\nu}^{m}(\text{æ}_{<t}) ~=~ \gamma^{m-t+1}\sum_{\text{æ}'_{t:m}}\nu^{\pi_\nu^*}(\text{æ}'_{t:m}\mid \text{æ}_{<t})\, V_{\nu}^{*}(\text{æ}_{<t}\, \text{æ}'_{t:m}) ~\leq~ \gamma^{m-t+1}.
$$

*Step 4: Take $m \to \infty$.* Since $0 \leq V_{\nu}^{*}(\text{æ}_{<t}) - V_{\nu}^{\pi_\nu^*,m}(\text{æ}_{<t}) \leq \gamma^{m-t+1}\to 0$, we have $V_{\nu}^{\pi_\nu^*,m}(\text{æ}_{<t}) \to V_{\nu}^{*}(\text{æ}_{<t})$, i.e. $V_{\nu}^{\pi_\nu^*}= V_{\nu}^{*}$.

:::

\## 3. Dominance of the Bayesian Mixture

:::callout {title="Exercise" tone="blue"}
**Exercise 3.1 [03].** Show that $\xi(\text{æ}_{<t}) \geq w_{\nu} \cdot \nu(\text{æ}_{<t})$ for every $\nu \in \mathcal{M}$.
:::

^prob-auto1


:::callout {title="Solution" tone="green" collapse="closed"}

$\xi(\text{æ}_{<t}) = \sum_{\nu' \in \mathcal{M}}w_{\nu'}\nu'(\text{æ}_{<t}) \geq w_{\nu} \nu(\text{æ}_{<t})$.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 3.2 [10].** Conclude that $\xi^{\pi}(\text{æ}_{1:m}) \geq w_{\nu} \cdot \nu^{\pi}(\text{æ}_{1:m})$ for any $\nu \in \mathcal{M}$ and any policy $\pi$.
:::

^prob-auto2


:::callout {title="Solution" tone="green" collapse="closed"}

By [[#^prob-factorization|Exercise 0.1]]: $\xi^{\pi}(\text{æ}_{1:m}) = \pi(\text{æ}_{1:m}) \cdot \xi(\text{æ}_{1:m}) \geq \pi(\text{æ}_{1:m}) \cdot w_{\nu} \nu(\text{æ}_{1:m}) = w_{\nu} \cdot \nu^{\pi}(\text{æ}_{1:m})$.

:::

\## 4. Properties of $V_{\xi}$

:::callout {title="Exercise" tone="blue"}
**Exercise 4.1 [15].** Show that for finite $m$:

$$
V_{\xi}^{\pi,m}(\text{æ}_{<t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi,m}(\text{æ}_{<t}).
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Use the multi-step posterior linearity of $\xi^{\pi}$ ([[#^prob-multi-step-xi|Exercise 1.4]]).

::::
:::

^prob-linearity-finite


:::callout {title="Solution" tone="green" collapse="closed"}

By [[#^prob-multi-step-xi|Exercise 1.4]]: $\xi^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}) = \sum_{\nu} w(\nu \mid \text{æ}_{<t})\, \nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t})$. Multiply both sides by $(1-\gamma)G_{t-1:m}$ and sum over all $\text{æ}_{t:m}$:

$$
\begin{aligned}V_{\xi}^{\pi,m}(\text{æ}_{<t}) ~&=~ (1-\gamma) \sum_{\text{æ}_{t:m}}\xi^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t}) G_{t-1:m}\\ ~&=~ (1-\gamma) \sum_{\text{æ}_{t:m}}\left[\sum_{\nu} w(\nu \mid \text{æ}_{<t})\, \nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t})\right] G_{t-1:m}\\ ~&=~ \sum_{\nu} w(\nu \mid \text{æ}_{<t}) \underbrace{(1-\gamma) \sum_{\text{æ}_{t:m}} \nu^\pi(\text{æ}_{t:m} \mid \text{æ}_{<t}) G_{t-1:m}}_{=\; V_\nu^{\pi,m}(\text{æ}_{<t})}.\end{aligned}
$$

In the last step we exchanged $\sum_{\text{æ}_{t:m}}$ and $\sum_{\nu}$; this is valid because both are sums of non-negative terms (or, for finite $m$, the sum over $\text{æ}_{t:m}$ is finite). So:

$$
V_{\xi}^{\pi,m}(\text{æ}_{<t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi,m}(\text{æ}_{<t}).
$$

:::

::::callout {title="Note" tone="neutral"}

**Fact 4.1 (Dominated convergence for sums).** If $a_{\nu,m}\to a_{\nu}$ as $m \to \infty$ for each $\nu$, and $|a_{\nu,m}| \leq b_{\nu}$ for all $m$ with $\sum_{\nu} b_{\nu} < \infty$, then $\sum_{\nu} a_{\nu,m}\to \sum_{\nu} a_{\nu}$. (For finite sums this is trivial.)

::::

^thm-dom-conv


:::callout {title="Exercise" tone="blue"}
**Exercise 4.2 (∗) (Infinite-horizon linearity) [17].** Show that the result extends to $m = \infty$:

$$
V_{\xi}^{\pi}(\text{æ}_{<t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi}(\text{æ}_{<t}).
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Take $m \to \infty$ in the finite-horizon result. You will need [[#^thm-dom-conv|Theorem 4.1]] to exchange limit and sum for countably infinite $\mathcal{M}$.

::::
:::

^prob-linearity-inf


:::callout {title="Solution" tone="green" collapse="closed"}

The left side converges: $V_{\xi}^{\pi,m}(\text{æ}_{<t}) \to V_{\xi}^{\pi}(\text{æ}_{<t})$ by definition.

For the right side, we need to push $\lim_{m \to \infty}$ through $\sum_{\nu}$. If $\mathcal{M}$ is finite this is immediate. For countably infinite $\mathcal{M}$, we apply [[#^thm-dom-conv|Theorem 4.1]] (dominated convergence for sums):

- For each $\nu$: $a_{\nu,m}:= w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi,m}(\text{æ}_{<t}) \to w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi}(\text{æ}_{<t})$ as $m \to \infty$ by definition.
- Domination: $|a_{\nu,m}| \leq w(\nu \mid \text{æ}_{<t}) \cdot 1 =: b_{\nu}$ for all $m$, since $V_{\nu}^{\pi,m}\in [0,1]$ ([[#^prob-bounded-value|Exercise 1.3]]).
- Summability: $\sum_{\nu} b_{\nu} = \sum_{\nu} w(\nu \mid \text{æ}_{<t}) = 1 < \infty$.

So [[#^thm-dom-conv|Theorem 4.1]] gives:

$$
V_{\xi}^{\pi}(\text{æ}_{<t}) ~=~ \lim_{m \to \infty}\sum_{\nu} w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi,m}(\text{æ}_{<t}) ~=~ \sum_{\nu} w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi}(\text{æ}_{<t}).
$$

:::

[[#^prob-linearity-finite|Exercise 4.1]] shows $V_{\xi}^{\pi}$ is linear in $\nu$. The optimal value $V_{\xi}^{*}$ is only convex: a single policy must perform well across all $\nu \in \mathcal{M}$ simultaneously, rather than being tailored to each $\nu$ individually.

:::callout {title="Exercise" tone="blue"}
**Exercise 4.3 (∗) [10].** (Convexity of $V_{\xi}^{*}$) Using [[#^prob-linearity-finite|Exercise 4.1]], show that for finite $m$:

$$
V_{\xi}^{*,m}(\text{æ}_{<t}) ~\leq~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{*,m}(\text{æ}_{<t}).
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Apply [[#^prob-linearity-finite|Exercise 4.1]] with $\pi = \pi_{\xi}^{*}$, the Bayes-optimal policy for $\xi$.

::::
:::

^prob-convex-opt


:::callout {title="Solution" tone="green" collapse="closed"}

By [[#^prob-backward-induction|Exercise 2.3]], a deterministic Bayes-optimal policy $\pi_{\xi}^{*}$ exists with $V_{\xi}^{\pi_\xi^*,m}= V_{\xi}^{*,m}$. Applying [[#^prob-linearity-finite|Exercise 4.1]] with $\pi = \pi_{\xi}^{*}$:

$$
V_{\xi}^{*,m}(\text{æ}_{<t}) ~=~ V_{\xi}^{\pi_\xi^*,m}(\text{æ}_{<t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi_\xi^*,m}(\text{æ}_{<t}).
$$

Since $\pi_{\xi}^{*}$ is optimal for $\xi$ but not necessarily for each individual $\nu$, we have $V_{\nu}^{\pi_\xi^*,m}(\text{æ}_{<t}) \leq V_{\nu}^{*,m}(\text{æ}_{<t})$ for each $\nu$. Since $w(\nu \mid \text{æ}_{<t}) \geq 0$:

$$
V_{\xi}^{*,m}(\text{æ}_{<t}) ~\leq~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{*,m}(\text{æ}_{<t}).
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 4.4 (∗) [15].** (Non-linearity of $V_{\xi}^{*}$) Show by example that the inequality in [[#^prob-convex-opt|Exercise 4.3]] can be strict, i.e. $V_{\xi}^{*,m}$ is *not* linear in $\nu$.

::::callout {title="Hint" tone="amber" collapse="closed"}

Consider $\mathcal{M} = \{\nu_{0}, \nu_{1}\}$: predicting a two-headed coin vs. a two-tailed coin.

::::
:::

^prob-nonlinear-opt


:::callout {title="Solution" tone="green" collapse="closed"}

*Coin-flip prediction.* Let $\mathcal{A} = \mathcal{O} = \mathcal{R} = \{0,1\}$, $\mathcal{M} = \{\nu_{0}, \nu_{1}\}$ with $w_{\nu_0}= w_{\nu_1}= \tfrac{1}{2}$, horizon $m = 1$. Environment $\nu_{i}$ always shows outcome $i$, and the agent is rewarded for a correct prediction:

$$
\nu_{i}(e_{t} \mid \text{æ}_{<t}\, a_{t}) ~:~ o_{t} = i, \quad r_{t} = \llbracket a_{t} = i \rrbracket.
$$

In $\nu_{i}$ the optimal policy plays $a_{t} = i$, achieving $V_{\nu_i}^{*,m}= 1$. In $\xi = \tfrac{1}{2}\nu_{0} + \tfrac{1}{2}\nu_{1}$ the outcome is a fair coin flip, so no policy predicts better than chance: $V_{\xi}^{*,m}= \tfrac{1}{2}$. Therefore:

$$
\sum_{\nu} w_{\nu}\, V_{\nu}^{*,m}(\text{æ}_{<t}) ~=~ \tfrac{1}{2}\cdot 1 + \tfrac{1}{2}\cdot 1 ~=~ 1 ~>~ \tfrac{1}{2}~=~ V_{\xi}^{*,m}(\text{æ}_{<t}).
$$

:::

\## 5. The Expectimax Form of AIXI

We have specified AIXI only implicitly, as the Bayes-optimal policy $\pi_{\xi}^{*}$ ([[#^def-value|Theorem 0.4]]). We now unroll this definition into the explicit **expectimax** expression: an alternating sequence of maximizations over actions and $\xi$-expectations over percepts.

:::callout {title="Exercise" tone="blue"}
**Exercise 5.1 (Expectimax form of AIXI) [20].** By iterating the finite-horizon Bellman optimality equation ([[#^prob-bellman-opt|Exercise 2.4]]), show that

$$
V_{\xi}^{*,m}(\text{æ}_{<t}) ~=~ (1-\gamma) \max_{a_t}\sum_{e_t}\xi(e_{t} \mid \text{æ}_{<t}a_{t})\, \max_{a_{t+1}}\sum_{e_{t+1}}\xi(e_{t+1}\mid \text{æ}_{<t+1}a_{t+1}) \cdots \max_{a_m}\sum_{e_m}\xi(e_{m} \mid \text{æ}_{<m}a_{m}) \,G_{t-1:m}
$$

and hence, collecting the percept factors with the chain rule ([[#^prob-chain-rule|Exercise 0.2]]) and taking $m \to \infty$ ([[#^prob-inf-horizon|Exercise 2.5]] and [[#^prob-inf-opt-policy|2.7]]), that AIXI selects the action

$$
a_{t} ~=~ \pi_{\xi}^{*}(\text{æ}_{<t}) ~\in~ \operatorname*{arg\,max}_{a_t}\lim_{m\to\infty}\sum_{e_t}\max_{a_{t+1}}\sum_{e_{t+1}}\cdots \max_{a_m}\sum_{e_m}\xi(e_{t:m}\mid \text{æ}_{<t}\, a_{t:m}) \,G_{t-1:m}
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Prove the first display by backward induction on $t$ from $m$ down to $1$, using the finite-horizon Bellman optimality equation ([[#^prob-bellman-opt|Exercise 2.4]]) and the return recursion $G_{t-1:m}= r_{t} + \gamma\, G_{t:m}$ ([[#^def-return|Theorem 0.3]]). At each step the leftover reward term $(1-\gamma)\, r_{t}$ is constant in the deeper variables; carry it inward using $\sum_{e_k}\xi(e_{k} \mid \text{æ}_{<k}a_{k}) = 1$ and $c + \max(\cdot) = \max(c + \cdot)$.

::::
:::

^prob-expectimax-derivation


:::callout {title="Solution" tone="green" collapse="closed"}

Abbreviate the one-step predictor $\xi_{k} := \xi(e_{k} \mid \text{æ}_{<k}a_{k})$, and write the **expectimax operator** over steps $i, \ldots, j$ as

$$
\mathop{\overset{\max}{\sum}}\limits_{i:j}~:=~ \max_{a_i}\sum_{e_i}\xi_{i}\, \max_{a_{i+1}}\sum_{e_{i+1}}\xi_{i+1}\cdots \max_{a_j}\sum_{e_j}\xi_{j},
$$

the alternating "maximize over the action, average over the percept" chain, with the $\xi_{k}$ weights built in; the single step is $\mathop{\overset{\max}{\sum}}\limits_{k} := \max_{a_k}\sum_{e_k}\xi_{k}$. Two facts:

- **(E1) Composition:** $\mathop{\overset{\max}{\sum}}\limits_{i:j}= \mathop{\overset{\max}{\sum}}\limits_{i}\, \mathop{\overset{\max}{\sum}}\limits_{i+1:j}$, by nesting the definition.
- **(E2) Affine pass-through:** for any $c \in \mathbb{R}$ and $\lambda \geq 0$ not depending on $(a_{i}, e_{i}, \ldots, a_{j}, e_{j})$,

$$
c + \lambda\, \mathop{\overset{\max}{\sum}}\limits_{i:j}X ~=~ \mathop{\overset{\max}{\sum}}\limits_{i:j}(c + \lambda X),
$$

since each layer has $\sum_{e_k}\xi_{k} = 1$ (so $\sum_{e_k}\xi_{k}(c+\lambda Y) = c + \lambda \sum_{e_k}\xi_{k} Y$) and $\max_{a}(c + \lambda\, g(a)) = c + \lambda \max_{a} g(a)$ for $\lambda \geq 0$.

We prove by backward induction on $t = m, m-1, \ldots, 1$ that

$$
V_{\xi}^{*,m}(\text{æ}_{<t}) ~=~ (1-\gamma)\, \mathop{\overset{\max}{\sum}}\limits_{t:m}\, G_{t-1:m}.
$$

*Base case $t = m$.* Here $G_{m-1:m}= r_{m}$ and $V_{\xi}^{*,m}(\text{æ}_{1:m}) = 0$ (the return past the horizon is empty, $G_{m:m}= 0$). The Bellman optimality equation ([[#^prob-bellman-opt|Exercise 2.4]]) for $\nu = \xi$ gives

$$
V_{\xi}^{*,m}(\text{æ}_{<m}) ~=~ \max_{a_m}\sum_{e_m}\xi_{m} \big[(1-\gamma)\, r_{m} + \gamma \cdot 0\big] ~=~ (1-\gamma)\, \mathop{\overset{\max}{\sum}}\limits_{m:m}\, G_{m-1:m}.
$$

*Inductive step.* Assume the claim at time $t+1$, i.e. $V_{\xi}^{*,m}(\text{æ}_{1:t}) = (1-\gamma)\, \mathop{\overset{\max}{\sum}}\limits_{t+1:m}\, G_{t:m}$ for every length-$t$ history (recall $\text{æ}_{<t+1}= \text{æ}_{1:t}$). The Bellman optimality equation ([[#^prob-bellman-opt|Exercise 2.4]]) at time $t$ reads

$$
V_{\xi}^{*,m}(\text{æ}_{<t}) ~=~ \mathop{\overset{\max}{\sum}}\limits_{t} \big[(1-\gamma)\, r_{t} + \gamma\, V_{\xi}^{*,m}(\text{æ}_{1:t})\big].
$$

Substituting the inductive hypothesis and pulling out $(1-\gamma)$,

$$
V_{\xi}^{*,m}(\text{æ}_{<t}) ~=~ (1-\gamma)\, \mathop{\overset{\max}{\sum}}\limits_{t} \big[r_{t} + \gamma\, \mathop{\overset{\max}{\sum}}\limits_{t+1:m}\, G_{t:m}\big].
$$

As $r_{t}$ and $\gamma$ do not depend on $(a_{t+1}, e_{t+1}, \ldots, a_{m}, e_{m})$, property (E2) carries them inside the inner operator, and the return recursion $G_{t-1:m}= r_{t} + \gamma\, G_{t:m}$ ([[#^def-return|Theorem 0.3]]) gives

$$
r_{t} + \gamma\, \mathop{\overset{\max}{\sum}}\limits_{t+1:m}\, G_{t:m}~\overset{(E2)}{=}~ \mathop{\overset{\max}{\sum}}\limits_{t+1:m}(r_{t} + \gamma\, G_{t:m}) ~=~ \mathop{\overset{\max}{\sum}}\limits_{t+1:m}\, G_{t-1:m}.
$$

Recombining the two operators by (E1),

$$
V_{\xi}^{*,m}(\text{æ}_{<t}) ~=~ (1-\gamma)\, \mathop{\overset{\max}{\sum}}\limits_{t}\, \mathop{\overset{\max}{\sum}}\limits_{t+1:m}\, G_{t-1:m}~=~ (1-\gamma)\, \mathop{\overset{\max}{\sum}}\limits_{t:m}\, G_{t-1:m},
$$

which expands back into the $\max/\sum$ layers of the first display.

*Infinite horizon and the action.* Taking $m \to \infty$ ([[#^prob-inf-horizon|Exercise 2.5]] and [[#^prob-inf-opt-policy|2.7]]), $G_{t-1:m}\to G_{\geq t-1}$ and the chain extends indefinitely, so $V_{\xi}^{*}(\text{æ}_{<t}) = (1-\gamma)\, \mathop{\overset{\max}{\sum}}\limits_{t:\infty}\, G_{\geq t-1}$. Collecting the per-step factors by the chain rule ([[#^prob-chain-rule|Exercise 0.2]], iterated), $\prod_{k=t}^{m}\xi_{k} = \xi(e_{t:m}\mid \text{æ}_{<t}\, a_{t:m})$. A Bayes-optimal action maximizes this expression; peeling the outer $\max_{a_t}$ off as an $\operatorname*{arg\,max}$ and dropping the positive constant $(1-\gamma)$ (which does not move the maximizer) gives the stated action.

:::

\## On-Policy Value Convergence

The following problems prove the first two main results: on-policy value convergence ([[#7. On-Policy Value Convergence of Bayes|Section 7]]), and that AIXI can't be fooled in deterministic environments ([[#8. AIXI Cannot Be Fooled in Deterministic Environments|Section 8]]). The path to the self-optimizing property (advanced stretch goal) resumes at [[#9. Likelihood Ratios Are Martingales|Section 9]].

\## 6. Bounding Expectation Differences by Total Variation

:::callout {title="Definition" tone="purple"}

**Definition 6.1 (Total variation distance).** The **total variation distance** between probability measures $P$ and $Q$ on a countable set $\Omega$ is $\mathrm{TV}[\Omega](P, Q) := \sup_{S \subseteq \Omega}|P(S) - Q(S)|$, where $P(S) := \sum_{\omega \in S}P(\omega)$.

:::

^def-tv


:::callout {title="Definition" tone="purple"}

**Definition 6.2 (Expectation under $P$).** For a probability measure $P$ on a countable set $\Omega$ and a function $f : \Omega \to \mathbb{R}$, the **expectation** of $f$ under $P$ is $\mathbb{E}_{P}[f] := \sum_{\omega \in \Omega}f(\omega)\, P(\omega)$.

:::

^def-expectation-p


The following technical lemma is needed for the on-policy value convergence proof.

:::callout {title="Exercise" tone="blue"}
**Exercise 6.1 (∗) [15].** Let $f : \Omega \to [0, c]$. Show that $\big|\mathbb{E}_{P}[f] - \mathbb{E}_{Q}[f]\big| \leq c \cdot \mathrm{TV}[\Omega](P, Q)$.

::::callout {title="Hint" tone="amber" collapse="closed"}

Define $A^{+} = \{\omega \in \Omega : P(\omega) \geq Q(\omega)\}$ and decompose the expectation difference as a sum over $A^{+}$ and its complement $A^{-} = \Omega \setminus A^{+}$.

::::
:::

^prob-auto3


:::callout {title="Solution" tone="green" collapse="closed"}

Write out the expectation difference using [[#^def-expectation-p|Theorem 6.2]]:

$$
\mathbb{E}_{P}[f] - \mathbb{E}_{Q}[f] ~=~ \sum_{\omega \in \Omega}f(\omega)\big(P(\omega) - Q(\omega)\big).
$$

Define $A^{+} := \{\omega \in \Omega : P(\omega) \geq Q(\omega)\}$ and $A^{-} := \Omega \setminus A^{+}$, and split the sum:

$$
\mathbb{E}_{P}[f] - \mathbb{E}_{Q}[f] ~=~ \sum_{\omega \in A^+}f(\omega)\big(P(\omega) - Q(\omega)\big) ~+~ \sum_{\omega \in A^-}f(\omega)\big(P(\omega) - Q(\omega)\big).
$$

*Bounding the sum over $A^{+}$.* On $A^{+}$, $P(\omega) - Q(\omega) \geq 0$ and $f(\omega) \leq c$, so:

$$
\begin{aligned}\sum_{\omega \in A^+}f(\omega)\big(P(\omega) - Q(\omega)\big) ~&\leq~ c \sum_{\omega \in A^+}\big(P(\omega) - Q(\omega)\big) \\ ~&=~ c \cdot \big(P(A^{+}) - Q(A^{+})\big) \\ ~&\leq~ c \cdot \sup_{S} |P(S) - Q(S)| \\ ~&=~ c \cdot \mathrm{TV}[\Omega](P, Q).\end{aligned}
$$

*Bounding the sum over $A^{-}$.* On $A^{-}$, $P(\omega) - Q(\omega) < 0$ and $f(\omega) \geq 0$, so every term $f(\omega)(P(\omega) - Q(\omega)) \leq 0$:

$$
\sum_{\omega \in A^-}f(\omega)\big(P(\omega) - Q(\omega)\big) ~\leq~ 0.
$$

*Combining.* $\mathbb{E}_{P}[f] - \mathbb{E}_{Q}[f] \leq c \cdot \mathrm{TV}[\Omega](P,Q) + 0 = c \cdot \mathrm{TV}[\Omega](P,Q)$.

*The other direction.* Swapping $P$ and $Q$: define $\tilde{A}^{+} = \{\omega : Q(\omega) \geq P(\omega)\} = A^{-}$. The same argument gives $\mathbb{E}_{Q}[f] - \mathbb{E}_{P}[f] \leq c \cdot \mathrm{TV}[\Omega](Q, P) = c \cdot \mathrm{TV}[\Omega](P, Q)$.

Therefore $|\mathbb{E}_{P}[f] - \mathbb{E}_{Q}[f]| \leq c \cdot \mathrm{TV}[\Omega](P, Q)$.

:::

\## 7. On-Policy Value Convergence of Bayes

The following definitions are needed for the on-policy value convergence theorem.

:::callout {title="Definition" tone="purple"}

**Definition 7.1 (Probability of events).** A **finite-length event** is a set $A \subseteq (\mathcal{A} \times \mathcal{E})^{t}$ of histories of fixed length $t$. Its probability under $\nu^{\pi}$ is

$$
\nu^{\pi}(A) ~:=~ \sum_{\text{æ}_{1:t} \in A}\nu^{\pi}(\text{æ}_{1:t}).
$$

An **event on infinite histories** is any set built from finite-length events by countable unions, intersections, and complements.[^3] Probabilities of such events are uniquely determined by two properties:

- **Normalization:** $\nu^{\pi}\!\big((\mathcal{A} \times \mathcal{E})^{\infty}\big) = 1$.
- **Countable additivity:** if $A_{1}, A_{2}, \ldots$ are pairwise disjoint events, then $\nu^{\pi}\!\big(\bigcup_{n=1}^{\infty} A_{n}\big) = \sum_{n=1}^{\infty} \nu^{\pi}(A_{n})$.

From these, all standard rules of probability can be derived (e.g. $\nu^{\pi}(A \cup B) = \nu^{\pi}(A) + \nu^{\pi}(B) - \nu^{\pi}(A \cap B)$, etc.), though we will not prove them here. Two derived properties we use explicitly:

- **Complement:** $\nu^{\pi}(A^{c}) = 1 - \nu^{\pi}(A)$.
- **Monotone limits:** if $A_{1} \subseteq A_{2} \subseteq \cdots$, then $\nu^{\pi}\!\big(\bigcup_{n=1}^{\infty} A_{n}\big) = \lim_{n \to \infty}\nu^{\pi}(A_{n})$.

Further useful notions:

- **Conditional probability:** The probability of event $A$ given observed history $\text{æ}_{<t}$ is

$$
\nu^{\pi}(A \mid \text{æ}_{<t}) ~:=~ \frac{\nu^{\pi}(\{\text{æ}_{<t}h : h \in A\})}{\nu^{\pi}(\text{æ}_{<t})}.
$$

:::

^def-events


:::callout {title="Note" tone="blue"}

**Example: Example: a fair coin shows 1 infinitely often.** Let $\mathcal{A} = \mathcal{O} = \{0,1\}$, $\mathcal{R} = \{0\}$, and let $\nu$ be a fair coin that ignores the action: $\nu(o_{t} = 1 \mid \text{æ}_{<t}\, a_{t}) = \tfrac{1}{2}$ for all $\text{æ}_{<t}, a_{t}$. Consider the event $F := \text{``}o_{t} = 1\text{ for infinitely many }t\text{''}$.

*Step 1: Build $F^{c}$ from finite-prefix events.* For each $t$, the set $\{o_{t} = 0\} := \{\text{æ}_{1:t}: o_{t} = 0\}$ is a finite-length event. For each $N$ and $T \geq N$, the set $D_{N,T}:= \bigcap_{t=N}^{T}\{o_{t} = 0\}$ is also a finite-length event (determined by time $T$). Define $C_{N} := \bigcap_{t=N}^{\infty}\{o_{t} = 0\}$ ("all zeros from time $N$ onwards"): this is an infinite-history event, built as a countable intersection of finite-length events. Then $F^{c} = \bigcup_{N=1}^{\infty} C_{N}$ ("eventually all zeros").

*Step 2: Compute $\nu^{\pi}(C_{N}) = 0$.* Since $D_{N,T}\supseteq D_{N,T+1}\supseteq \cdots$ (adding more constraints), the monotone limit property (for decreasing sets) gives:

$$
\nu^{\pi}(C_{N}) ~=~ \lim_{T \to \infty}\nu^{\pi}(D_{N,T}) ~=~ \lim_{T \to \infty}\left(\tfrac{1}{2}\right)^{T - N + 1}~=~ 0.
$$

(The probability $\nu^{\pi}(D_{N,T}) = (1/2)^{T-N+1}$ is independent of $\pi$, since $\nu$ ignores actions.)

*Step 3:* By countable additivity: $\nu^{\pi}(F^{c}) \leq \sum_{N=1}^{\infty} \nu^{\pi}(C_{N}) = 0$, so $\nu^{\pi}(F) = 1$. A fair coin shows 1 infinitely often, almost surely.

As such, $F^{c}$ (the set of all infinite histories containing only finitely many 1s) is a $\nu^{\pi}$-measure-zero set. Such histories "exist" as infinite sequences, but occur with probability zero.

:::

:::callout {title="Definition" tone="purple"}

**Definition 7.2 (Covering[^4]).** We say $Q$ **covers** $P$ if $Q$ is positive everywhere $P$ is: $P(A) > 0 \implies Q(A) > 0$ for all events $A$. Equivalently: any event that $Q$ rules out, $P$ also rules out. By [[#3. Dominance of the Bayesian Mixture|Section 3]], $\xi^{\pi}$ covers $\mu^{\pi}$.

:::

^def-covering


:::callout {title="Definition" tone="purple"}

**Definition 7.3 (Convergence $\nu^{\pi}$-almost surely).** Let $f_{t} : \mathcal{H}^{t-1}\to \mathbb{R}$ be a sequence of functions, where $f_{t}$ depends on the history $\text{æ}_{<t}$ of length $t-1$. We write $f_{t}(\text{æ}_{<t}) \to 0$ $\nu^{\pi}$**-almost surely** ($\nu^{\pi}$-a.s.) if

$$
\nu^{\pi}\!\Big(\Big\{\text{æ}_{1:\infty}: f_{t}(\text{æ}_{<t}) \not\to 0\Big\}\Big) = 0.
$$

This set is built from finite-prefix conditions: $\{f_{t} \not\to 0\} = \bigcup_{n=1}^{\infty} \bigcap_{N=1}^{\infty} \bigcup_{t=N}^{\infty} \big\{|f_{t}(\text{æ}_{<t})| > \tfrac{1}{n}\big\}$, so its probability is well-defined ([[#^def-events|Theorem 7.1]]).

:::

^def-as


:::callout {title="Note" tone="blue"}

**Example: Unpacking "$f_{t} \not\to 0$".** The set $\{f_{t} \not\to 0\}$ looks intimidating, but it reads naturally from the inside out:

- $\big\{|f_{t}(\text{æ}_{<t})| > \tfrac{1}{n}\big\}$ is a finite-length event: "at time $t$, the function is at least $\tfrac{1}{n}$ away from zero."
- $\bigcup_{t=N}^{\infty} \big\{|f_{t}| > \tfrac{1}{n}\big\}$: "at *some* time $t \geq N$, $f_{t}$ is at least $\tfrac{1}{n}$ away from zero."
- $\bigcap_{N=1}^{\infty} \bigcup_{t=N}^{\infty} \big\{|f_{t}| > \tfrac{1}{n}\big\}$: "for *every* $N$, there is some $t \geq N$ where $f_{t}$ is at least $\tfrac{1}{n}$ from zero", i.e., $f_{t}$ exceeds $\tfrac{1}{n}$ *infinitely often*.
- $\bigcup_{n=1}^{\infty} \bigcap_{N=1}^{\infty} \bigcup_{t=N}^{\infty} \big\{|f_{t}| > \tfrac{1}{n}\big\}$: "for *some* $\tfrac{1}{n}> 0$, $f_{t}$ exceeds $\tfrac{1}{n}$ infinitely often."

This last condition is exactly $\{f_{t} \not\to 0\}$: convergence $f_{t} \to 0$ means that for *every* $\varepsilon > 0$, $|f_{t}| \leq \varepsilon$ for all sufficiently large $t$. Its negation is that *some* $\varepsilon > 0$ is exceeded infinitely often.

Each layer is a countable union or intersection of the previous, so the whole set is a well-defined event on infinite histories.

:::

The Bayesian agent uses the mixture $\xi$ because the true environment $\mu$ is unknown. A natural question: does planning with $\xi$ eventually become as good as planning with $\mu$? The following theorem says *yes*: the value of any fixed policy $\pi$, as evaluated by $\xi$, converges to the value under the true environment $\mu$, along histories that $\mu^{\pi}$ actually generates.[^5] This tells us that the Bayesian mixture "learns" to predict the true environment's value, on policy.

:::callout {title="Theorem" tone="purple"}

**Theorem 7.4 (On-policy value convergence; ([[#^bib-hutter-24uaibook2|Hutter et al. 2024]], Theorem 7.3.1)).** For any $\mu \in \mathcal{M}$ and any policy $\pi$: $V_{\xi}^{\pi}(\text{æ}_{<t}) - V_{\mu}^{\pi}(\text{æ}_{<t}) \to 0$ as $t \to \infty$, $\mu^{\pi}$-almost surely. That is, the set of infinite histories along which the value difference does not vanish has $\mu^{\pi}$-probability zero:

$$
\mu^{\pi}\!\Big(\Big\{\text{æ}_{1:\infty}: \lim_{t \to \infty}\big(V_{\xi}^{\pi}(\text{æ}_{<t}) - V_{\mu}^{\pi}(\text{æ}_{<t})\big) \neq 0\Big\}\Big) = 0.
$$

:::

^thm-on-policy


The proof reduces to a finite-horizon TV bound ([[#^prob-tv-finite|Exercise 7.1]]), a covering argument ([[#^prob-covering-proof|Exercise 7.2]]), and the Blackwell–Dubins theorem ([[#^prob-on-policy-proof|Exercise 7.3]]). The only ingredient we do not prove is Blackwell–Dubins itself, which we state as a given fact.

:::callout {title="Exercise" tone="blue"}
**Exercise 7.1 (Finite-horizon TV bound on value difference) [10].** Using [[#6. Bounding Expectation Differences by Total Variation|Section 6]], show that for finite $m$:

$$
\big|V_{\xi}^{\pi,m}(\text{æ}_{<t}) - V_{\mu}^{\pi,m}(\text{æ}_{<t})\big| ~\leq~ \mathrm{TV}[\mathcal{H}^{m-t+1}]\!\big(\xi^{\pi}(\cdot \mid \text{æ}_{<t}),\; \mu^{\pi}(\cdot \mid \text{æ}_{<t})\big),
$$

where $\mathcal{H}^{m-t+1}:= (\mathcal{A} \times \mathcal{E})^{m-t+1}$ is the set of all future history segments $\text{æ}_{t:m}$.
:::

^prob-tv-finite


:::callout {title="Solution" tone="green" collapse="closed"}

We want to apply [[#6. Bounding Expectation Differences by Total Variation|Section 6]]. Identify:

- $\Omega := \mathcal{H}^{m-t+1}= (\mathcal{A} \times \mathcal{E})^{m-t+1}$, the finite set of future history segments $\text{æ}_{t:m}$.
- $P := \mu^{\pi}(\cdot \mid \text{æ}_{<t})$ and $Q := \xi^{\pi}(\cdot \mid \text{æ}_{<t})$, the conditional measures over $\Omega$.
- $f(\text{æ}_{t:m}) := (1-\gamma)G_{t-1:m}$, which satisfies $f \in [0,1]$ by [[#^prob-bounded-value|Exercise 1.3]] (so $c = 1$).

Then $V_{\nu}^{\pi,m}(\text{æ}_{<t}) = \sum_{\text{æ}_{t:m}}\nu^{\pi}(\text{æ}_{t:m}\mid \text{æ}_{<t})\, f(\text{æ}_{t:m})$ is exactly $\mathbb{E}_{P}[f]$ (for $\nu = \mu$) or $\mathbb{E}_{Q}[f]$ (for $\nu = \xi$). Applying [[#6. Bounding Expectation Differences by Total Variation|Section 6]]:

$$
\big|V_{\xi}^{\pi,m}(\text{æ}_{<t}) - V_{\mu}^{\pi,m}(\text{æ}_{<t})\big| ~=~ \big|\mathbb{E}_{Q}[f] - \mathbb{E}_{P}[f]\big| ~\leq~ 1 \cdot \mathrm{TV}[\mathcal{H}^{m-t+1}](P, Q).
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 7.2 (Covering) [05].** Show that $\xi^{\pi}$ covers $\mu^{\pi}$ ([[#^def-covering|Theorem 7.2]]).

::::callout {title="Hint" tone="amber" collapse="closed"}

Use [[#3. Dominance of the Bayesian Mixture|Section 3]].

::::
:::

^prob-covering-proof


:::callout {title="Solution" tone="green" collapse="closed"}

By [[#3. Dominance of the Bayesian Mixture|Section 3]], $\xi^{\pi}(\text{æ}_{1:m}) \geq w_{\mu} \cdot \mu^{\pi}(\text{æ}_{1:m})$ for all histories and all $m$. So for any event $A$: $\mu^{\pi}(A) > 0 \implies \xi^{\pi}(A) \geq w_{\mu} \cdot \mu^{\pi}(A) > 0$. Hence $\xi^{\pi}$ covers $\mu^{\pi}$.

:::

To complete the proof, we need the TV distance on finite segments to vanish $\mu^{\pi}$-a.s. as $t \to \infty$. This follows from the following deep result, which we state without proof:

::::callout {title="Note" tone="neutral"}

**Fact 7.5 (Blackwell–Dubins merging of opinions ([[#^bib-blackwell-62|Blackwell & Dubins 1962]])).** If $Q$ covers $P$, then $\sup_{S} |P(S \mid \text{æ}_{<t}) - Q(S \mid \text{æ}_{<t})| \to 0$ $P$-almost surely, where the supremum ranges over all measurable events $S$ (including events on infinite histories).

::::

^fact-bd


The proof of Blackwell–Dubins requires the Radon–Nikodym derivative and Levy's martingale convergence theorem: tools from measure theory that are beyond the scope of this sheet. See ([[#^bib-hutter-24uaibook2|Hutter et al. 2024]], Chapter 3.9) for discussion.

:::callout {title="Exercise" tone="blue"}
**Exercise 7.3 (On-policy convergence) [15].** Using [[#^fact-bd|Theorem 7.5]], [[#^prob-tv-finite|Exercise 7.1]] and [[#^prob-covering-proof|Exercise 7.2]], prove [[#^thm-on-policy|Theorem 7.4]].
:::

^prob-on-policy-proof


:::callout {title="Solution" tone="green" collapse="closed"}

*Step 1: Finite-horizon bound.* By [[#^prob-tv-finite|Exercise 7.1]], for each finite $m$:

$$
\begin{aligned}\big|V_{\xi}^{\pi,m}(\text{æ}_{<t}) - V_{\mu}^{\pi,m}(\text{æ}_{<t})\big| ~&\leq~ \mathrm{TV}[\mathcal{H}^{m-t+1}]\!\big(\xi^{\pi}(\cdot \mid \text{æ}_{<t}),\, \mu^{\pi}(\cdot \mid \text{æ}_{<t})\big) \\ ~&\leq~ \sup_{S} \big|\xi^{\pi}(S \mid \text{æ}_{<t}) - \mu^{\pi}(S \mid \text{æ}_{<t})\big|,\end{aligned}
$$

where the second inequality uses that the sup over subsets of $\mathcal{H}^{m-t+1}$ is at most the sup over all measurable events.

*Step 2: Take $m \to \infty$.* The LHS converges to $|V_{\xi}^{\pi}(\text{æ}_{<t}) - V_{\mu}^{\pi}(\text{æ}_{<t})|$ (by definition of the infinite-horizon value as the pointwise limit). The RHS does not depend on $m$. Hence

$$
\big|V_{\xi}^{\pi}(\text{æ}_{<t}) - V_{\mu}^{\pi}(\text{æ}_{<t})\big| ~\leq~ \sup_{S} \big|\xi^{\pi}(S \mid \text{æ}_{<t}) - \mu^{\pi}(S \mid \text{æ}_{<t})\big|.
$$

*Step 3: Take $t \to \infty$.* By [[#^prob-covering-proof|Exercise 7.2]], $\xi^{\pi}$ covers $\mu^{\pi}$. By [[#^fact-bd|Theorem 7.5]] (Blackwell–Dubins) with $P = \mu^{\pi}$ and $Q = \xi^{\pi}$, the RHS tends to $0$ as $t \to \infty$, $\mu^{\pi}$-a.s. Therefore

$$
\big|V_{\xi}^{\pi}(\text{æ}_{<t}) - V_{\mu}^{\pi}(\text{æ}_{<t})\big| ~\to~ 0 \qquad \mu^{\pi}\text{-a.s.}
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 7.4 (∗) [40].** Prove [[#^fact-bd|Theorem 7.5]].

::::callout {title="Hint" tone="amber" collapse="closed"}

See ([[#^bib-blackwell-62|Blackwell & Dubins 1962]]). The proof uses the Radon–Nikodym derivative $dP/dQ$, Levy's martingale convergence theorem, and the Lebesgue decomposition. No elementary proof is known that avoids graduate-level measure theory.

::::
:::

^prob-auto4


\## 8. AIXI Cannot Be Fooled in Deterministic Environments

:::callout {title="Theorem" tone="purple"}

**Theorem 8.1 (AIXI cannot act poorly in good environments).** If $\mu \in \mathcal{M}$ is deterministic and $V_{\mu}^{*}(\text{æ}_{<t}) > \varepsilon > 0$ for all $t$ along the history generated by $\mu$ and $\pi_{\xi}^{*}$, then $V_{\xi}^{*}(\text{æ}_{<t}) \geq w_{\mu}\, \varepsilon > 0$ for all $t$. ([[#^bib-hutter-24uaibook2|Hutter et al. 2024]], Theorem 7.4.10)

:::

^thm-cant-be-fooled


:::callout {title="Exercise" tone="blue"}
**Exercise 8.1 [10].** Show that $V_{\xi}^{*}(\text{æ}_{<t}) \geq w(\mu \mid \text{æ}_{<t}) \cdot V_{\mu}^{*}(\text{æ}_{<t})$.

::::callout {title="Hint" tone="amber" collapse="closed"}

Use linearity of $V^{\pi}$ ([[#^prob-linearity-inf|Exercise 4.2]]).

::::
:::

^prob-xi-lower-bound


:::callout {title="Solution" tone="green" collapse="closed"}

By definition, $V_{\xi}^{*}(\text{æ}_{<t}) = \sup_{\pi} V_{\xi}^{\pi}(\text{æ}_{<t}) \geq V_{\xi}^{\pi'}(\text{æ}_{<t})$ for any policy $\pi'$. By [[#^prob-linearity-inf|Exercise 4.2]] (linearity of $V^{\pi}$ in the environment):

$$
V_{\xi}^{\pi'}(\text{æ}_{<t}) ~=~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi'}(\text{æ}_{<t}).
$$

Choose $\pi' = \pi_{\mu}^{*}$, the deterministic optimal policy for $\mu$ whose existence is guaranteed by [[#^prob-inf-opt-policy|Exercise 2.7]]:

$$
V_{\xi}^{*}(\text{æ}_{<t}) ~\geq~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi_\mu^*}(\text{æ}_{<t}).
$$

Every term is non-negative ($w(\nu \mid \text{æ}_{<t}) \geq 0$ and $V_{\nu}^{\pi_\mu^*}\geq 0$). Dropping all terms except $\nu = \mu$:

$$
V_{\xi}^{*}(\text{æ}_{<t}) ~\geq~ w(\mu \mid \text{æ}_{<t})\, V_{\mu}^{\pi_\mu^*}(\text{æ}_{<t}) ~=~ w(\mu \mid \text{æ}_{<t})\, V_{\mu}^{*}(\text{æ}_{<t}).
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 8.2 [15].** Show $w(\mu \mid \text{æ}_{<t}) \geq w_{\mu}$ when $\mu$ is deterministic, and combine with [[#^prob-xi-lower-bound|Exercise 8.1]] to prove [[#^thm-cant-be-fooled|Theorem 8.1]].
:::

^prob-auto5


:::callout {title="Solution" tone="green" collapse="closed"}

From [[#^def-mixture|Theorem 0.1]], the posterior weight is:

$$
w(\mu \mid \text{æ}_{<t}) ~=~ w_{\mu} \cdot \frac{\mu(\text{æ}_{<t})}{\xi(\text{æ}_{<t})}~=~ w_{\mu} \cdot \frac{\prod_{k=1}^{t-1}\mu(e_{k} \mid \text{æ}_{<k}a_{k})}{\prod_{k=1}^{t-1}\xi(e_{k} \mid \text{æ}_{<k}a_{k})}.
$$

Since $\mu$ is deterministic, for the history that $\mu$ actually generates, $\mu(e_{k} \mid \text{æ}_{<k}a_{k}) = 1$ for each $k$ (the environment produces each percept with certainty). So:

$$
\mu(\text{æ}_{<t}) ~=~ \prod_{k=1}^{t-1}1 ~=~ 1.
$$

Meanwhile, $\xi(e_{k} \mid \text{æ}_{<k}a_{k}) \leq 1$ for each $k$ (it is a probability), so $\xi(\text{æ}_{<t}) = \prod_{k=1}^{t-1}\xi(e_{k} \mid \text{æ}_{<k}a_{k}) \leq 1$.

Therefore $w(\mu \mid \text{æ}_{<t}) = w_{\mu} \cdot 1 / \xi(\text{æ}_{<t}) \geq w_{\mu}$.

Combining with [[#^prob-xi-lower-bound|Exercise 8.1]]:

$$
V_{\xi}^{*}(\text{æ}_{<t}) ~\geq~ w(\mu \mid \text{æ}_{<t}) \cdot V_{\mu}^{*}(\text{æ}_{<t}) ~\geq~ w_{\mu} \cdot V_{\mu}^{*}(\text{æ}_{<t}) ~>~ w_{\mu} \cdot \varepsilon ~>~ 0.
$$

:::

*Remark.* With the Solomonoff prior, $w_{\mu} = 2^{-K(\mu)}$ may be astronomically small. The result guarantees non-zero value, not near-optimal value.

\## [[#9. Likelihood Ratios Are Martingales|Sections 9–11]]: Self-Optimizing Policy (Finite Model Class)

We now prove: if *any* policy can learn to act optimally, $\pi_{\xi}^{*}$ also learns. We restrict to finite $\mathcal{M} = \{\nu_{1}, \ldots, \nu_{N}\}$ where each $\nu_{i}$ is a proper probability measure.

\## 9. Likelihood Ratios Are Martingales

The following definition and theorem state the main goal of [[#9. Likelihood Ratios Are Martingales|Sections 9–11]].

:::callout {title="Definition" tone="purple"}

**Definition 9.1 (Self-optimizing).** Fix a historic policy $\pi$. A policy $\tilde\pi$ is **self-optimizing** for $\mathcal{M}$ with respect to $\pi$ if for every $\nu \in \mathcal{M}$: $V_{\nu}^{*}(\text{æ}_{<t}) - V_{\nu}^{\tilde\pi}(\text{æ}_{<t}) \to 0$ as $t \to \infty$, $\nu^{\pi}$-almost surely.

The percepts $e_{1:\infty}$ are sampled from $\nu$; the historic actions $a_{<t}$ come from $\pi$, which may differ from $\tilde\pi$.

:::

^def-selfopt


:::callout {title="Theorem" tone="purple"}

**Theorem 9.2 (Self-optimizing; ([[#^bib-hutter-24uaibook2|Hutter et al. 2024]], Theorem 7.5.2)).** Let $\mathcal{M}$ be finite and fix a historic policy $\pi$. If there exists a $\tilde\pi$ self-optimizing for $\mathcal{M}$ with respect to $\pi$, then $\pi_{\xi}^{*}$ is also self-optimizing for $\mathcal{M}$ with respect to $\pi$: for any $\mu \in \mathcal{M}$, $V_{\mu}^{*}(\text{æ}_{<t}) - V_{\mu}^{\pi_\xi^*}(\text{æ}_{<t}) \to 0$ $\mu^{\pi}$-almost surely.

:::

^thm-selfopt


:::callout {title="Definition" tone="purple"}

**Definition 9.3 (Supermartingale).** A sequence of functions $X_{t} : \mathcal{H}^{t}\to \mathbb{R}_{\geq 0}$ (each depending on the history $\text{æ}_{1:t}$) is a $\mu^{\pi}$-**supermartingale** if $\mathbb{E}_{\mu^\pi}[X_{t} \mid \text{æ}_{<t}] \leq X_{t-1}$ for all $t$; that is,

$$
\sum_{\text{æ}_t}\pi(a_{t} \mid \text{æ}_{<t})\, \mu(e_{t} \mid \text{æ}_{<t}a_{t})\, X_{t}(\text{æ}_{1:t}) ~\leq~ X_{t-1}(\text{æ}_{<t}).
$$

If equality holds, it is a $\mu^{\pi}$-**martingale**.

:::

^def-supermartingale


**Intuition.** A supermartingale is a quantity whose expected future value, given the present, is no larger than its current value: it cannot "drift upward on average." A martingale is the equality case: expected future value equals current value. The key example is the **likelihood ratio** $X_{\nu,t}(\text{æ}_{1:t}) := \nu(\text{æ}_{1:t})/\mu(\text{æ}_{1:t})$: how much more (or less) likely the observed history is under $\nu$ than under the true environment $\mu$. Under $\mu$, this ratio is a martingale: the true environment does not, on average, favour any alternative $\nu$ over itself. Non-negativity plus the (super)martingale structure forces $X_{\nu,t}$ to converge (by Doob's theorem below), which is the engine behind the self-optimizing proof: it lets us separate environments that remain plausible ($X_{\nu,\infty}> 0$) from those that are eventually ruled out ($X_{\nu,\infty}= 0$), and handle each case differently in [[#11. Proving the Self-Optimizing Property|Section 11]].

::::callout {title="Note" tone="neutral"}

**Fact 9.4 (Doob's supermartingale convergence).** If $(X_{t})_{t \geq 0}$ is a non-negative $\mu^{\pi}$-supermartingale, then there exists a function $X_{\infty} : \mathcal{H}^{\infty} \to \mathbb{R}_{\geq 0}$ of the infinite history such that $X_{t}(\text{æ}_{1:t}) \to X_{\infty}(\text{æ}_{1:\infty})$ as $t \to \infty$, with $X_{\infty}(\text{æ}_{1:\infty}) < \infty$, for $\mu^{\pi}$-almost every infinite history $\text{æ}_{1:\infty}$. That is:

$$
\mu^{\pi}\!\Big(\Big\{\text{æ}_{1:\infty}\in (\mathcal{A} \times \mathcal{E})^{\infty} : X_{t}(\text{æ}_{1:t}) \not\to X_{\infty}(\text{æ}_{1:\infty})\Big\}\Big) ~=~ 0.
$$

::::

^fact-doob


For each $\nu \in \mathcal{M}$, define the likelihood ratio

$$
X_{\nu,t}: \mathcal{H}^{t} \to \mathbb{R}_{\geq 0}, \qquad X_{\nu,t}(\text{æ}_{1:t}) ~:=~ \frac{\nu(\text{æ}_{1:t})}{\mu(\text{æ}_{1:t})}, \qquad X_{\nu,0}:= 1.
$$

$X_{\nu,t}$ is a *function* of the history $\text{æ}_{1:t}$, not a number: different histories give different values. Throughout this section and the next, any unqualified statement of the form "$X_{\nu,t}\geq c$" or "$X_{\nu,t}\to X_{\nu,\infty}$" is shorthand for "$X_{\nu,t}(\text{æ}_{1:t}) \geq c$" or "$X_{\nu,t}(\text{æ}_{1:t}) \to X_{\nu,\infty}(\text{æ}_{1:\infty})$" holding $\mu^{\pi}$-almost surely, i.e. on every infinite history outside a set of $\mu^{\pi}$-measure zero. We will not track these null sets explicitly; their countable union over all claims is still a $\mu^{\pi}$-null set.

:::callout {title="Exercise" tone="blue"}
**Exercise 9.1 [15].** Show that $X_{\nu,t}$ is a $\mu^{\pi}$-martingale: $\mathbb{E}_{\mu^\pi}[X_{\nu,t}\mid \text{æ}_{<t}] = X_{\nu,t-1}$.

::::callout {title="Hint" tone="amber" collapse="closed"}

Write $X_{\nu,t}(\text{æ}_{1:t}) = X_{\nu,t-1}(\text{æ}_{<t}) \cdot \nu(e_{t} \mid \text{æ}_{<t}a_{t})/\mu(e_{t} \mid \text{æ}_{<t}a_{t})$. Sum over $a_{t}, e_{t}$; $\mu$ cancels, leaving $\sum_{e_t}\nu(e_{t} \mid \text{æ}_{<t}a_{t}) = 1$.

::::
:::

^prob-martingale


:::callout {title="Solution" tone="green" collapse="closed"}

We need to compute $\mathbb{E}_{\mu^\pi}[X_{\nu,t}\mid \text{æ}_{<t}]$. Conditioning on $\text{æ}_{<t}$ means $a_{t}$ and $e_{t}$ are the random quantities (sampled from $\pi$ and $\mu$ respectively). First, write $X_{\nu,t}$ pointwise as a function of history in terms of $X_{\nu,t-1}$:

$$
X_{\nu,t}(\text{æ}_{1:t}) ~=~ \frac{\nu(\text{æ}_{1:t})}{\mu(\text{æ}_{1:t})}~=~ \frac{\nu(\text{æ}_{<t})}{\mu(\text{æ}_{<t})}\cdot \frac{\nu(e_{t} \mid \text{æ}_{<t}a_{t})}{\mu(e_{t} \mid \text{æ}_{<t}a_{t})}~=~ X_{\nu,t-1}(\text{æ}_{<t}) \cdot \frac{\nu(e_{t} \mid \text{æ}_{<t}a_{t})}{\mu(e_{t} \mid \text{æ}_{<t}a_{t})},
$$

using the chain rule ([[#^prob-chain-rule|Exercise 0.2]]) for both $\nu$ and $\mu$. Now take the conditional expectation. Since $X_{\nu,t-1}$ depends only on $\text{æ}_{<t}$, it comes out of the expectation:

$$
\begin{aligned}\mathbb{E}_{\mu^\pi}[X_{\nu,t}\mid \text{æ}_{<t}] ~&=~ X_{\nu,t-1}\cdot \mathbb{E}_{\mu^\pi}\!\left[\frac{\nu(e_{t} \mid \text{æ}_{<t}a_{t})}{\mu(e_{t} \mid \text{æ}_{<t}a_{t})}~\Big|~ \text{æ}_{<t}\right] \\ ~&=~ X_{\nu,t-1}\sum_{a_t \in \mathcal{A}}\pi(a_{t} \mid \text{æ}_{<t}) \sum_{e_t \in \mathcal{E}}\mu(e_{t} \mid \text{æ}_{<t}a_{t}) \cdot \frac{\nu(e_{t} \mid \text{æ}_{<t}a_{t})}{\mu(e_{t} \mid \text{æ}_{<t}a_{t})}\\ ~&=~ X_{\nu,t-1}\sum_{a_t}\pi(a_{t} \mid \text{æ}_{<t}) \sum_{e_t}\nu(e_{t} \mid \text{æ}_{<t}a_{t}).\end{aligned}
$$

In the last step, $\mu(e_{t} \mid \text{æ}_{<t}a_{t})$ cancels. Since $\nu$ is a probability measure, $\sum_{e_t}\nu(e_{t} \mid \text{æ}_{<t}a_{t}) = 1$ for every $\text{æ}_{<t}, a_{t}$; and $\sum_{a_t}\pi(a_{t} \mid \text{æ}_{<t}) = 1$. Therefore:

$$
\mathbb{E}_{\mu^\pi}[X_{\nu,t}\mid \text{æ}_{<t}] ~=~ X_{\nu,t-1}\cdot 1 \cdot 1 ~=~ X_{\nu,t-1}.
$$

Since $X_{\nu,t}\geq 0$ (a ratio of non-negative quantities), $(X_{\nu,t})_{t \geq 0}$ is a non-negative $\mu^{\pi}$-martingale, in particular, a non-negative $\mu^{\pi}$-supermartingale.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 9.2 [05].** Apply [[#^fact-doob|Theorem 9.4]] to conclude $X_{\nu,t}\to X_{\nu,\infty}< \infty$ $\mu^{\pi}$-a.s.
:::

^prob-x-converges


:::callout {title="Solution" tone="green" collapse="closed"}

$X_{\nu,t}$ is a non-negative $\mu^{\pi}$-supermartingale by [[#^prob-martingale|Exercise 9.1]]. By [[#^fact-doob|Theorem 9.4]] (Doob's convergence theorem), $X_{\nu,t}$ converges $\mu^{\pi}$-a.s. to a finite limit: $X_{\nu,t}\to X_{\nu,\infty}< \infty$.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 9.3 [10].** Define $X_{\xi,t}:= \xi(\text{æ}_{1:t})/\mu(\text{æ}_{1:t})$. Show $X_{\xi,t}= \sum_{\nu} w_{\nu} X_{\nu,t}$ and $X_{\xi,t}\geq w_{\mu} > 0$.
:::

^prob-x-bounded-mu


:::callout {title="Solution" tone="green" collapse="closed"}

From the definition:

$$
X_{\xi,t}~:=~ \frac{\xi(\text{æ}_{1:t})}{\mu(\text{æ}_{1:t})}~=~ \frac{\sum_{\nu} w_{\nu} \nu(\text{æ}_{1:t})}{\mu(\text{æ}_{1:t})}~=~ \sum_{\nu} w_{\nu} \cdot \frac{\nu(\text{æ}_{1:t})}{\mu(\text{æ}_{1:t})}~=~ \sum_{\nu} w_{\nu} X_{\nu,t}.
$$

By [[#3. Dominance of the Bayesian Mixture|Section 3]]: $\xi(\text{æ}_{1:t}) \geq w_{\mu} \cdot \mu(\text{æ}_{1:t})$, so $X_{\xi,t}= \xi(\text{æ}_{1:t})/\mu(\text{æ}_{1:t}) \geq w_{\mu} > 0$.

Since $\mathcal{M}$ is finite, $X_{\xi,t}= \sum_{\nu} w_{\nu} X_{\nu,t}$ is a finite sum of convergent sequences, so $X_{\xi,t}\to X_{\xi,\infty}:= \sum_{\nu} w_{\nu} X_{\nu,\infty}< \infty$ $\mu^{\pi}$-a.s., with $X_{\xi,\infty}\geq w_{\mu} > 0$.

:::

\## 10. Change of Measure

:::callout {title="Exercise" tone="blue"}
**Exercise 10.1 [15].** Let $A$ be a set of finite histories of length $m$. Show:

$$
\nu^{\pi}[\text{æ}_{1:m}\in A] ~=~ \mathbb{E}_{\mu^\pi}\big[X_{\nu,m}\cdot \llbracket \text{æ}_{1:m}\in A \rrbracket\big].
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Use [[#^prob-factorization|Exercise 0.1]] to show $\nu^{\pi}/\mu^{\pi} = \nu/\mu = X_{\nu,m}$.

::::
:::

^prob-cm-finite


:::callout {title="Solution" tone="green" collapse="closed"}

By [[#^prob-factorization|Exercise 0.1]], $\nu^{\pi}(\text{æ}'_{1:m}) = \pi(\text{æ}'_{1:m}) \cdot \nu(\text{æ}'_{1:m})$ and $\mu^{\pi}(\text{æ}'_{1:m}) = \pi(\text{æ}'_{1:m}) \cdot \mu(\text{æ}'_{1:m})$. For any history $\text{æ}'_{1:m}$ with $\mu^{\pi}(\text{æ}'_{1:m}) > 0$, the policy factors cancel:

$$
\nu^{\pi}(\text{æ}'_{1:m}) ~=~ \frac{\nu^{\pi}(\text{æ}'_{1:m})}{\mu^{\pi}(\text{æ}'_{1:m})}\cdot \mu^{\pi}(\text{æ}'_{1:m}) ~=~ \frac{\nu(\text{æ}'_{1:m})}{\mu(\text{æ}'_{1:m})}\cdot \mu^{\pi}(\text{æ}'_{1:m}) ~=~ X_{\nu,m}(\text{æ}'_{1:m}) \cdot \mu^{\pi}(\text{æ}'_{1:m}).
$$

For histories with $\mu^{\pi}(\text{æ}'_{1:m}) = 0$: since $\mu^{\pi} = \pi \cdot \mu$, some $\pi(a_{k} \mid \text{æ}'_{<k}) = 0$, which forces $\nu^{\pi}(\text{æ}'_{1:m}) = 0$ too (the same $\pi$-factor appears in $\nu^{\pi} = \pi \cdot \nu$). So both sides are zero.

Summing over $\text{æ}'_{1:m}\in A$:

$$
\begin{aligned}\nu^{\pi}[\text{æ}_{1:m}\in A] ~&=~ \sum_{\text{æ}'_{1:m} \in A}\nu^{\pi}(\text{æ}'_{1:m}) ~=~ \sum_{\text{æ}'_{1:m} \in A}X_{\nu,m}(\text{æ}'_{1:m}) \cdot \mu^{\pi}(\text{æ}'_{1:m}) \\ ~&=~ \mathbb{E}_{\mu^\pi}\big[X_{\nu,m}\cdot \llbracket \text{æ}_{1:m}\in A \rrbracket\big].\end{aligned}
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 10.2.** (Given.) The identity extends to infinite histories: for any event $A \subseteq (\mathcal{A} \times \mathcal{E})^{\infty}$,

$$
\nu^{\pi}[A] ~=~ \mathbb{E}_{\mu^\pi}\big[X_{\nu,\infty}\cdot \llbracket \text{æ}_{1:\infty}\in A \rrbracket\big].
$$

This says that $X_{\nu,\infty}$ plays the role of the Radon–Nikodym derivative $\mathrm{d}\nu^{\pi}/\mathrm{d}\mu^{\pi}$ on the space of infinite histories. The proof rests on two ingredients beyond the scope of this worksheet:

- **$L^{1}$ martingale convergence** (closed martingale / Levy's upward theorem): since $\mathbb{E}_{\mu^\pi}[X_{\nu,t}] = 1$ for every $t$, the non-negative $\mu^{\pi}$-martingale $(X_{\nu,t})$ is uniformly integrable, so $X_{\nu,t}\to X_{\nu,\infty}$ in $L^{1}(\mu^{\pi})$, not merely $\mu^{\pi}$-a.s. This lets us pass the $t\to\infty$ limit through the expectation.
- **Uniqueness of measure extension** (Caratheodory / $\pi$–$\lambda$ theorem): both sides of the identity are finite measures on $(\mathcal{A}\times\mathcal{E})^{\infty}$; the finite-history identity ([[#^prob-cm-finite|Exercise 10.1]]) shows they agree on all cylinder events $A = A_{0} \times (\mathcal{A}\times\mathcal{E})^{\infty}$, and cylinders generate the full event $\sigma$-algebra, so agreement extends uniquely to every event.

We omit the proof and use this identity freely below.
:::

^prob-cm-extension


:::callout {title="Exercise" tone="blue"}
**Exercise 10.3 (Markov inequality for change of measure) [15].** Let $E$ be an event of infinite histories. For any $\varepsilon > 0$, show that

$$
\mu^{\pi}\big[E \cap \{X_{\nu,\infty}\geq \varepsilon\}\big] ~\leq~ \frac{\nu^{\pi}[E]}{\varepsilon}.
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

On $E \cap \{X_{\nu,\infty}\geq \varepsilon\}$, $X_{\nu,\infty}\geq \varepsilon$ pointwise. Take $\mu^{\pi}$-expectations and apply [[#^prob-cm-extension|Exercise 10.2]].

::::
:::

^prob-markov-cm


:::callout {title="Solution" tone="green" collapse="closed"}

Let $E_{\varepsilon} := E \cap \{X_{\nu,\infty}\geq \varepsilon\}$. On $E_{\varepsilon}$, $X_{\nu,\infty}\geq \varepsilon$, so pointwise

$$
X_{\nu,\infty}\cdot \llbracket \text{æ}_{1:\infty}\in E_{\varepsilon} \rrbracket ~\geq~ \varepsilon \cdot \llbracket \text{æ}_{1:\infty}\in E_{\varepsilon} \rrbracket.
$$

Take $\mu^{\pi}$-expectations and apply [[#^prob-cm-extension|Exercise 10.2]]:

$$
\nu^{\pi}[E_{\varepsilon}] ~=~ \mathbb{E}_{\mu^\pi}\big[X_{\nu,\infty}\cdot \llbracket \text{æ}_{1:\infty}\in E_{\varepsilon} \rrbracket\big] ~\geq~ \varepsilon \cdot \mathbb{E}_{\mu^\pi}\big[\llbracket \text{æ}_{1:\infty}\in E_{\varepsilon} \rrbracket\big] ~=~ \varepsilon \cdot \mu^{\pi}[E_{\varepsilon}].
$$

Since $E_{\varepsilon} \subseteq E$, $\nu^{\pi}[E_{\varepsilon}] \leq \nu^{\pi}[E]$. Dividing by $\varepsilon$ gives $\mu^{\pi}[E_{\varepsilon}] \leq \nu^{\pi}[E]/\varepsilon$.

*Interpretation.* A likelihood ratio of at least $\varepsilon$ forces $\nu^{\pi}$ and $\mu^{\pi}$ measures of an event to be comparable: $\mu^{\pi}$ of the event can exceed $\nu^{\pi}$ of it only by the factor $1/\varepsilon$. In particular, if $\nu^{\pi}$ vanishes on $E$, so does $\mu^{\pi}$ on the part where the likelihood ratio stays bounded away from zero.

:::

\## 11. Proving the Self-Optimizing Property

Fix a policy $\tilde\pi$ that is self-optimizing for $\mathcal{M}$ with respect to $\pi$ ([[#^def-selfopt|Theorem 9.1]]): its existence is the hypothesis of [[#^thm-selfopt|Theorem 9.2]]. For each $\nu \in \mathcal{M}$, define the **suboptimality gap**

$$
\delta_{\nu,t}: \mathcal{H}^{t-1}\to [0,1], \qquad \delta_{\nu,t}(\text{æ}_{<t}) ~:=~ V_{\nu}^{*}(\text{æ}_{<t}) - V_{\nu}^{\tilde\pi}(\text{æ}_{<t}).
$$

As with $X_{\nu,t}$, we write $\delta_{\nu,t}$ without its argument when convenient: "$\delta_{\nu,t}\to 0$ $\mu^{\pi}$-a.s." means $\delta_{\nu,t}(\text{æ}_{<t}) \to 0$ on every infinite history outside a $\mu^{\pi}$-null set, and similarly for "$\delta_{\nu,t}\leq 1$" etc.

:::callout {title="Exercise" tone="blue"}
**Exercise 11.1 (Chain of inequalities) [20].** Show:

$$
0 ~\leq~ w(\mu \mid \text{æ}_{<t}) \big[V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}\big] ~\leq~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, \delta_{\nu,t}.
$$

::::callout {title="Hint" tone="amber" collapse="closed"}

Use $V_{\xi}^{\pi_\xi^*}\geq V_{\xi}^{\tilde\pi}$ and [[#^prob-linearity-inf|Exercise 4.2]].

::::
:::

^prob-chain-ineq


:::callout {title="Solution" tone="green" collapse="closed"}

We establish two inequalities and chain them.

*First inequality: isolate the $\mu$-term.* For each $\nu \in \mathcal{M}$, the optimal value is at least the value of any policy: $V_{\nu}^{*}(\text{æ}_{<t}) \geq V_{\nu}^{\pi_\xi^*}(\text{æ}_{<t})$, so $V_{\nu}^{*} - V_{\nu}^{\pi_\xi^*}\geq 0$. Since the posterior weights $w(\nu \mid \text{æ}_{<t}) \geq 0$, every term in $\sum_{\nu} w(\nu \mid \text{æ}_{<t})[V_{\nu}^{*} - V_{\nu}^{\pi_\xi^*}]$ is non-negative. The $\mu$-term is one such term:

$$
w(\mu \mid \text{æ}_{<t})\big[V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}\big] ~\leq~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\big[V_{\nu}^{*} - V_{\nu}^{\pi_\xi^*}\big].
$$

*Second inequality: replace $\pi_{\xi}^{*}$ with $\tilde\pi$.* By definition of the optimal value, $V_{\xi}^{*}(\text{æ}_{<t}) \geq V_{\xi}^{\tilde\pi}(\text{æ}_{<t})$. Expanding both sides using infinite-horizon linearity ([[#^prob-linearity-inf|Exercise 4.2]], applied to the fixed policies $\pi_{\xi}^{*}$ and $\tilde\pi$):

$$
\sum_{\nu} w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\pi_\xi^*}(\text{æ}_{<t}) ~=~ V_{\xi}^{*}(\text{æ}_{<t}) ~\geq~ V_{\xi}^{\tilde\pi}(\text{æ}_{<t}) ~=~ \sum_{\nu} w(\nu \mid \text{æ}_{<t})\, V_{\nu}^{\tilde\pi}(\text{æ}_{<t}).
$$

Rearranging: $\sum_{\nu} w(\nu)[V_{\nu}^{*} - V_{\nu}^{\pi_\xi^*}] \leq \sum_{\nu} w(\nu)[V_{\nu}^{*} - V_{\nu}^{\tilde\pi}] = \sum_{\nu} w(\nu)\, \delta_{\nu,t}$.

*Chaining:*

$$
0 ~\leq~ w(\mu \mid \text{æ}_{<t})\big[V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}\big] ~\leq~ \sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, \delta_{\nu,t}.
$$

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 11.2 (Vanishing posterior) [10].** Show: if $X_{\nu,\infty}= 0$ then $w(\nu \mid \text{æ}_{<t}) \to 0$ $\mu^{\pi}$-a.s.

::::callout {title="Hint" tone="amber" collapse="closed"}

Show $w(\nu \mid \text{æ}_{<t}) = w_{\nu} X_{\nu,t-1}/X_{\xi,t-1}$ and use [[#^prob-x-bounded-mu|Exercise 9.3]].

::::
:::

^prob-vanishing-posterior


:::callout {title="Solution" tone="green" collapse="closed"}

From the posterior weight formula, dividing numerator and denominator by $\mu(\text{æ}_{<t})$:

$$
w(\nu \mid \text{æ}_{<t}) ~=~ w_{\nu} \cdot \frac{\nu(\text{æ}_{<t})}{\xi(\text{æ}_{<t})}~=~ w_{\nu} \cdot \frac{\nu(\text{æ}_{<t})/\mu(\text{æ}_{<t})}{\xi(\text{æ}_{<t})/\mu(\text{æ}_{<t})}~=~ \frac{w_{\nu} \cdot X_{\nu,t-1}}{X_{\xi,t-1}},
$$

where $X_{\nu,t-1}$ and $X_{\xi,t-1}$ are evaluated at the length-$(t{-}1)$ history $\text{æ}_{<t}$.

If $X_{\nu,\infty}= 0$, then $X_{\nu,t-1}\to 0$ $\mu^{\pi}$-a.s. ([[#^prob-x-converges|Exercise 9.2]]). Since $X_{\xi,t-1}\geq w_{\mu} > 0$ always ([[#^prob-x-bounded-mu|Exercise 9.3]]), the ratio $w(\nu \mid \text{æ}_{<t}) = w_{\nu} X_{\nu,t-1}/X_{\xi,t-1}\to 0$ $\mu^{\pi}$-a.s.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 11.3 (Transferring convergence) [20].** Let $F := \{\text{æ}_{1:\infty}: \delta_{\nu,t}(\text{æ}_{<t}) \not\to 0\}$, the set of infinite histories on which the suboptimality gap fails to vanish. Show that $\mu^{\pi}\big[F \cap \{X_{\nu,\infty}> 0\}\big] = 0$.

::::callout {title="Hint" tone="amber" collapse="closed"}

Self-optimizing ([[#^def-selfopt|Theorem 9.1]]) gives $\nu^{\pi}[F] = 0$. Apply [[#^prob-markov-cm|Exercise 10.3]] with $E = F$ and $\varepsilon = 1/n$ to conclude $\mu^{\pi}[F \cap \{X_{\nu,\infty}\geq 1/n\}] = 0$ for each $n \geq 1$. Then note $\{X_{\nu,\infty}> 0\} = \bigcup_{n \geq 1}\{X_{\nu,\infty}\geq 1/n\}$ and take the countable union ([[#^def-events|Theorem 7.1]]).

::::
:::

^prob-delta-transfer


:::callout {title="Solution" tone="green" collapse="closed"}

*Step 1: $F$ is $\nu^{\pi}$-null.* By the self-optimizing assumption ([[#^def-selfopt|Theorem 9.1]]), under $\nu^{\pi}$ the suboptimality gap $\delta_{\nu,t}$ vanishes, so $\nu^{\pi}[F] = 0$.

*Step 2: Apply [[#^prob-markov-cm|Exercise 10.3]].* For each $n \geq 1$, take $E = F$ and $\varepsilon = 1/n$:

$$
\mu^{\pi}\!\big[F \cap \{X_{\nu,\infty}\geq 1/n\}\big] ~\leq~ \frac{\nu^{\pi}[F]}{1/n}~=~ 0.
$$

*Step 3: Countable union.* The level sets of $X_{\nu,\infty}$ form a nested increasing family: $\{X_{\nu,\infty}> 0\} = \bigcup_{n \geq 1}\{X_{\nu,\infty}\geq 1/n\}$. Intersecting with $F$ gives $F \cap \{X_{\nu,\infty}> 0\} = \bigcup_{n \geq 1}\big(F \cap \{X_{\nu,\infty}\geq 1/n\}\big)$, a countable union. By countable subadditivity ([[#^def-events|Theorem 7.1]]):

$$
\begin{aligned}\mu^{\pi}\!\big[F \cap \{X_{\nu,\infty}> 0\}\big] ~=~&\mu^{\pi}\!\Big[\textstyle\bigcup_{n}F \cap \{X_{\nu,\infty}\geq 1/n\}\Big] \\ ~\leq~ \sum_{n \geq 1}\,&\mu^{\pi}\!\big[F \cap \{X_{\nu,\infty}\geq 1/n\}\big] ~=~ 0.\end{aligned}
$$

*What this says.* "$\delta_{\nu,t}\to 0$ $\mu^{\pi}$-a.s. on $\{X_{\nu,\infty}> 0\}$" is shorthand for exactly this event statement: among infinite histories on which the likelihood ratio stays bounded away from zero, all but a $\mu^{\pi}$-null subset are ones where $\delta_{\nu,t}(\text{æ}_{<t}) \to 0$. We do *not* claim convergence on histories where $X_{\nu,\infty}= 0$: that case is handled separately in [[#^prob-vanishing-posterior|Exercise 11.2]] via the posterior weight.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 11.4 (Single-term convergence) [10].** Combine [[#^prob-vanishing-posterior|Exercise 11.2]] and [[#^prob-delta-transfer|Exercise 11.3]] to show $w(\nu \mid \text{æ}_{<t}) \delta_{\nu,t}\to 0$ $\mu^{\pi}$-a.s.
:::

^prob-single-term


:::callout {title="Solution" tone="green" collapse="closed"}

Fix $\nu \in \mathcal{M}$. We show $w(\nu \mid \text{æ}_{<t})\, \delta_{\nu,t}\to 0$ $\mu^{\pi}$-a.s. by considering two exhaustive cases:

*Case 1: $X_{\nu,\infty}= 0$.* By [[#^prob-vanishing-posterior|Exercise 11.2]], $w(\nu \mid \text{æ}_{<t}) \to 0$. Since $\delta_{\nu,t}\in [0,1]$ ([[#^prob-bounded-value|Exercise 1.3]]), the product $w(\nu \mid \text{æ}_{<t}) \cdot \delta_{\nu,t}\leq 1 \cdot w(\nu \mid \text{æ}_{<t}) \to 0$.

*Case 2: $X_{\nu,\infty}> 0$.* By [[#^prob-delta-transfer|Exercise 11.3]], $\delta_{\nu,t}\to 0$. Since $w(\nu \mid \text{æ}_{<t}) \leq 1$ (posterior weights are at most 1), the product $w(\nu \mid \text{æ}_{<t}) \cdot \delta_{\nu,t}\leq 1 \cdot \delta_{\nu,t}\to 0$.

These two cases cover all infinite histories ($\mu^{\pi}$-a.s.), so $w(\nu \mid \text{æ}_{<t})\, \delta_{\nu,t}\to 0$ $\mu^{\pi}$-a.s.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 11.5 (Self-Optimizing Theorem) [15].** Combine [[#^prob-single-term|Exercise 11.4]], [[#^prob-chain-ineq|Exercise 11.1]], [[#^prob-x-bounded-mu|Exercise 9.3]] to finally prove the main result of [[#^thm-selfopt|Theorem 9.2]].

::::callout {title="Hint" tone="amber" collapse="closed"}

$w(\mu \mid \text{æ}_{<t}) = w_{\mu}/X_{\xi,t-1}$.

::::
:::

^prob-auto6


:::callout {title="Solution" tone="green" collapse="closed"}

Since $\mathcal{M} = \{\nu_{1}, \ldots, \nu_{N}\}$ is finite, we can sum [[#^prob-single-term|Exercise 11.4]] over all $\nu \in \mathcal{M}$:

$$
\sum_{\nu \in \mathcal{M}}w(\nu \mid \text{æ}_{<t})\, \delta_{\nu,t}~\longrightarrow~ 0 \qquad \mu^{\pi}\text{-a.s.}
$$

From [[#^prob-chain-ineq|Exercise 11.1]]:

$$
0 ~\leq~ w(\mu \mid \text{æ}_{<t})\big[V_{\mu}^{*}(\text{æ}_{<t}) - V_{\mu}^{\pi_\xi^*}(\text{æ}_{<t})\big] ~\leq~ \sum_{\nu} w(\nu \mid \text{æ}_{<t})\, \delta_{\nu,t}~\longrightarrow~ 0.
$$

So $w(\mu \mid \text{æ}_{<t})[V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}] \to 0$ $\mu^{\pi}$-a.s.

It remains to divide by $w(\mu \mid \text{æ}_{<t})$. From [[#^prob-x-bounded-mu|Exercise 9.3]]:

$$
w(\mu \mid \text{æ}_{<t}) ~=~ \frac{w_{\mu}}{X_{\xi,t-1}}.
$$

Fix an infinite history outside the (single) $\mu^{\pi}$-null set on which $X_{\xi,t}\to X_{\xi,\infty}< \infty$ fails. Along this history:

- $X_{\xi,t-1}\to X_{\xi,\infty}$, a finite positive number (with $X_{\xi,\infty}\geq w_{\mu} > 0$ by [[#^prob-x-bounded-mu|Exercise 9.3]]).
- Hence $w(\mu \mid \text{æ}_{<t}) = w_{\mu} / X_{\xi,t-1}\to w_{\mu} / X_{\xi,\infty}> 0$, so eventually $w(\mu \mid \text{æ}_{<t}) \geq w_{\mu} / (2 X_{\xi,\infty}) > 0$.

Dividing the convergence $w(\mu \mid \text{æ}_{<t}) (V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}) \to 0$ by this positive (per-history) lower bound, and using $V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}\geq 0$:

$$
V_{\mu}^{*}(\text{æ}_{<t}) - V_{\mu}^{\pi_\xi^*}(\text{æ}_{<t}) ~\longrightarrow~ 0 \qquad \mu^{\pi}\text{-a.s.}
$$

This completes the proof of [[#^thm-selfopt|Theorem 9.2]].

:::

*Remark.* We do not need to know which policy $\tilde\pi$ is self-optimizing, or whether it is computable. Mere existence suffices. For countable $\mathcal{M}$, this final step is harder: a countable sum of $\mu^{\pi}$-a.s.-convergent sequences need not converge $\mu^{\pi}$-a.s. The general proof uses a "convergence of mixture tails" argument ([[#^bib-hutter-04uaibook|Hutter 2005]], Lem. 5.28).

\## A. Worked Example: Bayesian Mixture

:::callout {title="Note" tone="neutral"}

**Setup.**

- **Actions:** $\mathcal{A} = \{H, T\}$ (predict the next coin flip)
- **Observations:** $\mathcal{O} = \{H, T\}$ (actual coin flip)
- **Rewards:** $\mathcal{R} = \{0, 1\}$, with $r_{t} = \llbracket a_{t} = o_{t} \rrbracket$
- **Model class:** $\mathcal{M} = \{\nu_{HH}, \nu_{HT}\}$ (two-headed coin, fair coin)
- **Prior:** $w_{\nu_{HH}}= w_{\nu_{HT}}= \tfrac{1}{2}$

:::

**Before any interaction** ($t=1$, $\text{æ}_{<1}= \epsilon$):

$$
\begin{aligned}\xi(o_{1} = H \mid a_{1}) ~&=~ \tfrac{1}{2}\cdot 1 + \tfrac{1}{2}\cdot \tfrac{1}{2}~=~ \tfrac{3}{4}.\end{aligned}
$$

**After observing a head** ($t=2$), the posterior updates:

$$
\begin{aligned}w(\nu_{HH}\mid \text{æ}_{1}) ~&=~ \tfrac{1}{2}\cdot \frac{1}{3/4}~=~ \tfrac{2}{3},&w(\nu_{HT}\mid \text{æ}_{1}) ~&=~ \tfrac{1}{2}\cdot \frac{1/2}{3/4}~=~ \tfrac{1}{3}.\end{aligned}
$$

**Updated prediction:** $\xi(o_{2} = H \mid \text{æ}_{1}a_{2}) = \tfrac{2}{3}\cdot 1 + \tfrac{1}{3}\cdot \tfrac{1}{2}= \tfrac{5}{6}$.

\## B. Worked Example: Value Function

Continuing from [[#A. Worked Example: Bayesian Mixture|Appendix A]]. Suppose the agent always predicts $H$ (policy $\pi_{H}$).

Under $\nu_{HH}$: always correct, $r_{t} = 1$ every step: $V_{\nu_{HH}}^{\pi_H}(\epsilon) = (1-\gamma) \sum_{k=0}^{\infty} \gamma^{k} \cdot 1 = 1$.

Under $\nu_{HT}$: correct half the time: $V_{\nu_{HT}}^{\pi_H}(\epsilon) = (1-\gamma) \sum_{k=0}^{\infty} \gamma^{k} \cdot \tfrac{1}{2}= \tfrac{1}{2}$.

The mixture value (by [[#^prob-linearity-inf|Exercise 4.2]]) is: $V_{\xi}^{\pi_H}(\epsilon) = \tfrac{1}{2}\cdot 1 + \tfrac{1}{2}\cdot \tfrac{1}{2}= \tfrac{3}{4}$.

As the agent observes more heads ($\mu = \nu_{HH}$), the posterior on $\nu_{HH}$ increases towards 1, and $V_{\xi}^{\pi_H}\to V_{\nu_{HH}}^{\pi_H}= 1$. This is on-policy value convergence ([[#^thm-on-policy|Theorem 7.4]]) in action.

\## C. Knuth's Difficulty Scale

Each subproblem carries a difficulty rating in square brackets, following Knuth's rating scheme for exercises ([[#^bib-knuth-73a|Knuth 1973]]) in slightly adapted form. The rating assumes that the material in the preceding problems (on which the subproblem depends) has been understood. In-between values are possible.

- **[00]** *Very easy.* Solvable from the top of your head.
- **[10]** *Easy.* Needs 15 minutes to think, possibly pencil and paper.
- **[20]** *Average.* May take 1–2 hours to answer completely.
- **[30]** *Moderately difficult or lengthy.* May take several hours to a day.
- **[40]** *Quite difficult or lengthy.* Often a significant research result.
- **[50]** *Open research problem.* An obtained solution should be published.

Problems marked **($\ast$)** are enrichment: they are off the critical path to the three main results ([[#^thm-on-policy|Theorem 7.4]], [[#^thm-cant-be-fooled|Theorem 8.1]], [[#^thm-selfopt|Theorem 9.2]]) and can be skipped on a first pass without loss of continuity.

\## References


D. Blackwell and L. Dubins (1962). [*Merging of opinions with increasing information*](http://www.dklevine.com/archive/refs4565.pdf). Annals of Mathematical Statistics.


^bib-blackwell-62


Marcus Hutter (2005). [*Universal Artificial Intelligence: Sequential Decisions based on Algorithmic Probability*](http://www.hutter1.net/ai/uaibook.htm). Springer.


^bib-hutter-04uaibook


Marcus Hutter, David Quarel, and Elliot Catt (2024). [*An Introduction to Universal Artificial Intelligence*](http://www.hutter1.net/ai/uaibook2.htm). Chapman & Hall.


^bib-hutter-24uaibook2


D. E. Knuth (1973). *The Art of Computer Programming, Volume I: Fundamental Algorithms*. Addison-Wesley.


^bib-knuth-73a


Jan Leike and Marcus Hutter (2015). [*Bad Universal Priors and Notions of Optimality*](https://arxiv.org/abs/1510.04931). CoRR.


^bib-leike-15badpriors


[^1]: See [[#B. Worked Example: Value Function|Appendix B]] for a worked example. For simplicity, we consider only geometric discounting.

[^2]: The optimal value is defined as a $\sup$ over policies. In general, a supremum need not be attained (e.g. $\sup_{x \in (0,1)}x = 1$ but no $x \in (0,1)$ achieves it). [[#2. Existence of Optimal Policies|Section 2]] shows that the sup is attained in our setting.

[^3]: We are deliberately avoiding a formal treatment of measure theory here. Not all subsets of $(\mathcal{A} \times \mathcal{E})^{\infty}$ are measurable; we restrict to "nice" (measurable) sets built from finite-prefix conditions via countable set operations, which suffice for everything in this sheet. For a rigorous treatment using $\sigma$-algebras and probability measures, see ([[#^bib-hutter-24uaibook2|Hutter et al. 2024]], Chapter 2.2).

[^4]: The standard name is *absolute continuity* of $P$ with respect to $Q$, written $P \ll Q$.

[^5]: If the true environment is $\mu$ then we don't care about the behaviour of the Bayesian agent on histories that have $\mu^{\pi}$-probability zero: such histories will never be observed anyway.
