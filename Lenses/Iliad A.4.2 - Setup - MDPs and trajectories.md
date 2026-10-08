---
id: 'e4bf433f-9a60-4992-bcdf-8ec7e6958e46'
title: "A.4.2 Setup: MDPs and trajectories"
tldr: "Defines finite-horizon MDPs, state trajectories, return, policies and the true value J of a policy, the basic notation used in the rest of the sheet."
summary_for_tutor: "This is the Setup of worksheet A.4 (reward learning theory). It gives Definition 0.1: an MDP (S, A, T, R, P_0, T, gamma) with finite S and A, a state trajectory, its return G(s) as the discounted sum of rewards, a policy pi inducing P^pi, and the true value J(pi) = E[G]. Keep the notation S, A, G, J, P^pi. No exercises."
authors:
  - Leon Lang (Iliad)
  - Joar Skalse (Deducto Limited, King’s College London)
source_url: https://iliad-intensive.org/alignment/reward-learning-theory/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Setup

This sheet (Section 1) works through one concrete example from Lang et al. 2024 to see how naive RLHF can fail when the human evaluator only *partially* observes the environment they are providing feedback on. By the end of the sheet you will have derived, by hand, the conditions under which an RLHF-optimal policy hides information from the human in a way that systematically inflates the human's perception of the policy's return — the failure mode the paper calls **deceptive inflation**. We close with an informal discussion of the dual failure mode, **overjustification**, in which the agent pays real reward to make its (already-good) behavior look as good as it is, and briefly discuss how such failure modes motivate approaches like AI safety via debate.

We assume familiarity with finite-horizon Markov decision processes; the additional structure needed — observation kernels, human beliefs, the observation return ${G_{\mathrm{obs}}}$ and observation value ${J_{\mathrm{obs}}}$ — is introduced in highlighted boxes as we go.

:::callout {title="Definition" tone="blue"}

**Definition 0.1 (MDP and trajectories).** A finite-horizon **Markov decision process** is a tuple $({\mathcal{S}}, {\mathcal{A}}, {\mathcal{T}}, R, P_{0}, T, \gamma)$ with finite state space ${\mathcal{S}}$, finite action space ${\mathcal{A}}$, transition kernel ${\mathcal{T}} : {\mathcal{S}} \times {\mathcal{A}} \to \Delta({\mathcal{S}})$, reward function $R : {\mathcal{S}} \to {\mathbb{R}}$, initial-state distribution $P_{0} \in \Delta({\mathcal{S}})$, horizon $T \in \mathbb{N}$, and discount $\gamma \in (0,1]$. A **state trajectory** is a sequence $\vec s = s_{0} s_{1} \cdots s_{T}$, and its **return** is

$$
G(\vec s) \;=\; \sum_{t=0}^{T}\gamma^{t}\, R(s_{t}).
$$

A **policy** $\pi : {\mathcal{S}} \to \Delta({\mathcal{A}})$ induces a distribution $P^{\pi}$ over state trajectories. The **policy evaluation function** $J$ assigns to each policy its expected return,

$$
J(\pi) \;=\; {\mathbb{E}}_{\vec s \sim P^\pi}[G(\vec s)],
$$

which we will also call the policy's **true value** (to contrast later with the value the human *thinks* it is evaluating).

:::
