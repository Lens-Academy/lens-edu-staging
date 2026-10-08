---
id: '42d09889-4fb8-4c6c-85dd-96119cee086a'
title: "D.3.2.1 Overview and setup"
tldr: "Gives the roadmap for AIXI and the setup of agents, policies and environments that interact over histories of actions and percepts."
summary_for_tutor: "Opening of worksheet D.3.2 (AIXI): prerequisites (Solomonoff induction first), learning goals, the Knuth difficulty scale, the starred-problem convention, and the roadmap of Sections 0-11 (on-policy value convergence, AIXI cannot be fooled, self-optimizing property). Setup Definitions 0.1-0.4: spaces A, O, R, E and histories, policy pi, environment nu, and the interaction measure nu^pi. Keep the notation ae_{<t}, a_t, e_t = (o_t, r_t). No exercises in this lens."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Prerequisites

- [Solomonoff Induction](https://iliad-intensive.org/agency/solomonoff-induction) — **start there first.** The Bayesian mixture, posterior updates, and dominance carry over directly; AIXI reuses them in the action setting.
- Comfort with discrete probability (conditional distributions, chain rule, expectations).
- Familiarity with sequential decision-making / reinforcement learning (agents, rewards, discounting, value functions) is useful but not assumed.

:::callout {title="What you'll learn" tone="neutral"}

- Formalize the agent-environment interaction, value functions, and the Bayes-optimal policy that defines AIXI.
- Derive the explicit expectimax form of AIXI.
- Prove on-policy value convergence and that AIXI cannot be fooled in deterministic environments.
- Prove the self-optimizing property via likelihood-ratio martingales and change of measure.

:::

Much of this material is drawn from (Hutter et al. 2024). The book provides fuller explanations, additional context, and proofs omitted here.

**Difficulty ratings.** Each subproblem is tagged with a rating in square brackets using Knuth's scale (Knuth 1973): roughly, **[00]** trivial, **[10]** 15-minute pencil-and-paper, **[20]** 1–2 hours, **[30]** several hours to a day, **[40]** a significant research result. Intermediate values are possible. See Appendix B for the full scale.

Problems marked **($$\ast$$)** are less interesting/insightful, and while the result may be used later, I would recommend skipping them on a first pass.

\## Overview

AIXI is the *action* half of **Universal AI**: it lifts the Bayesian mixture from [Solomonoff induction](https://iliad-intensive.org/agency/solomonoff-induction) — learning to predict — to learning to act. Now the agent takes actions that shape what it observes, and AIXI is the **Bayes-optimal policy** over a universal mixture $$\xi$$ of environments. It learns to act as well as if it knew the true environment $$\mu$$. Under the universal choice — $${\mathcal{M}}$$ = all lower-semicomputable environments, prior $$w_{\nu} = 2^{-K(\nu)}$$ — the assumption "$$\mu \in {\mathcal{M}}$$" again becomes "the universe is computable."

\## Goal and Roadmap

This exercise sheet builds towards three main results:

- **On-policy value convergence** (Section 7): the Bayesian mixture $$\xi$$ learns to predict the value of any fixed policy as well as the true environment $$\mu$$.
- **AIXI can't be fooled** (Section 8): in deterministic environments, the Bayes-optimal agent is guaranteed non-zero value whenever optimal value is non-zero.
- **Self-optimizing property** (Section 11, advanced stretch goal): the Bayes-optimal policy $$\pi_{\xi}^{*}$$ learns to *act* as well as if it knew $$\mu$$, provided that any learnable policy can achieve this. This is the central theoretical justification for the AIXI agent.

A good target is to complete Sections 7 and 8. The self-optimizing property (Sections 9–11) requires substantial additional machinery (supermartingales, change of measure) and is an advanced stretch goal.

**Critical path.** The three results share a common foundation (Sections 0–4) and then diverge:

![diagram](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-aixi-roadmap-e692d2f7.png)

**In summary:**

- Sections 0–4 establish the Bayesian RL framework: measure algebra, mixture properties, existence of optimal policies, dominance, and linearity.
- Section 5 derives the explicit expectimax form of AIXI.
- Sections 6–7 prove *on-policy value convergence*: $$V_{\xi}^{\pi}$$ and $$V_{\mu}^{\pi}$$ become indistinguishable for any fixed $$\pi$$.
- Section 8 shows *AIXI can't be fooled*: the Bayes-optimal agent achieves non-zero value whenever optimal value is non-zero (in deterministic environments).
- Sections 9–11 (advanced stretch goal) prove the *self-optimizing property*: if any policy can learn to act optimally, $$\pi_{\xi}^{*}$$ inherits this.

\## Setup

An **agent** interacts with an **environment** in discrete time steps $$t = 1, 2, \ldots$$.

:::callout {title="Definition" tone="blue"}

**Definition 0.1 (Spaces and notation).** - $${\mathcal{A}}$$: finite set of **actions**
- $${\mathcal{O}}$$: finite set of **observations**
- $${\mathcal{R}} \subset [0,1]$$: finite set of **rewards**
- $${\mathcal{E}} := {\mathcal{O}} \times {\mathcal{R}}$$: set of **percepts**; $$e_{t} = (o_{t}, r_{t}) \equiv o_{t}r_{t}$$
- $${\mathcal{H}}^{t} := ({\mathcal{A}} \times {\mathcal{E}})^{t}$$: set of all histories of length $$t$$
- $${\mathcal{H}}^{*} := \cup_{t=0}^{\infty} {\mathcal{H}}^{t}$$: set of all finite **histories**
- $${\mathcal{H}} \equiv {\mathcal{H}}^{*}$$: set of all finite histories
- $${\mathcal{H}}^{\infty} := ({\mathcal{A}} \times {\mathcal{E}})^{\infty}$$: set of all infinite histories
- $$\Delta S$$: set of all probability distributions over set $$S$$
- $$\llbracket \cdot \rrbracket$$: **Iverson bracket**: $$\llbracket P \rrbracket = 1$$ if $$P$$ is true, $$0$$ if false
- $$t$$: current time step; $$m$$: finite horizon; $$1 \leq t \leq m$$
- $$i, j, k$$: arbitrary integer indices
- $$xy$$: concatenation
- $$\epsilon$$: the empty string/history
- $${\text{\ae}}_{i:j}:= a_{i} e_{i}\, a_{i+1}e_{i+1}\,\cdots\, a_{j} e_{j}$$: history segment from time $$i$$ to $$j$$
- $${\text{\ae}}_{<t}:= a_{1} e_{1}\, a_{2} e_{2} \,\cdots\, a_{t-1}e_{t-1}$$: history up to (but not including) time $$t$$

:::

:::callout {title="Definition" tone="blue"}

**Definition 0.2 (Policy $$\pi$$).** A **policy** $$\pi : {\mathcal{H}} \to \Delta {\mathcal{A}}$$ maps each history to a probability distribution over actions. Given history $${\text{\ae}}_{<t}$$:

- $$\pi(\cdot \mid {\text{\ae}}_{<t})$$ is a distribution over $${\mathcal{A}}$$,
- $$\pi(a_{t} \mid {\text{\ae}}_{<t}) \in [0,1]$$ is the probability of choosing action $$a_{t}$$,
- the agent samples $$a_{t} \sim \pi(\cdot \mid {\text{\ae}}_{<t})$$.

A policy is **deterministic** if $$\pi(a \mid {\text{\ae}}_{<t}) \in \{0,1\}$$ for all $$a, {\text{\ae}}_{<t}$$. We write $$\pi({\text{\ae}}_{i:j}) := \prod_{k=i}^{j} \pi(a_{k} \mid {\text{\ae}}_{<k})$$.

:::

:::callout {title="Definition" tone="blue"}

**Definition 0.3 (Environment $$\nu$$).** An **environment** $$\nu : {\mathcal{H}} \times {\mathcal{A}} \to \Delta {\mathcal{E}}$$ maps each history–action pair to a distribution over percepts. Given history $${\text{\ae}}_{<t}$$ and action $$a_{t}$$:

- $$\nu(\cdot \mid {\text{\ae}}_{<t}a_{t})$$ is a distribution over $${\mathcal{E}}$$,
- $$\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}) \in [0,1]$$ is the probability of percept $$e_{t}$$,
- the environment samples $$e_{t} \sim \nu(\cdot \mid {\text{\ae}}_{<t}a_{t})$$.

We write $$\nu({\text{\ae}}_{i:j}) := \prod_{k=i}^{j} \nu(e_{k} \mid {\text{\ae}}_{<k}a_{k})$$. This satisfies the chain rule: $$\nu({\text{\ae}}_{i:j}) = \nu({\text{\ae}}_{i:j-1}) \cdot \nu(e_{j} \mid {\text{\ae}}_{i:j-1}a_{j})$$ or in the form we will usually use, $$\nu({\text{\ae}}_{1:t}) = \nu({\text{\ae}}_{<t}) \cdot \nu(e_{t} \mid {\text{\ae}}_{<t}a_{t})$$. An environment is **deterministic** if $$\nu(e_{t} \mid {\text{\ae}}_{<t}a_{t}) \in \{0,1\}$$ for all $$e_{t}, {\text{\ae}}_{<t}, a_{t}$$ (each percept is produced with certainty). We denote the true (unknown) environment by $$\mu$$.

:::

:::callout {title="Definition" tone="blue"}

**Definition 0.4 (Interaction measure $$\nu^{\pi}$$).** When policy $$\pi$$ interacts with environment $$\nu$$, the joint probability of a history segment $${\text{\ae}}_{i:j}$$ given past $${\text{\ae}}_{<i}$$ is

$$
\nu^{\pi}({\text{\ae}}_{i:j}\mid {\text{\ae}}_{<i}) ~:=~ \prod_{k=i}^{j} \pi(a_{k} \mid {\text{\ae}}_{<k})\, \nu(e_{k} \mid {\text{\ae}}_{<k}a_{k}).
$$

:::
