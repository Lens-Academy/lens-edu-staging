---
id: '52f6c3f4-42ab-422f-abd2-d075fd46b52b'
title: "D.1.2.3 An example MDP"
tldr: "Computes the values of two fixed policies in a small three-state MDP and finds the discount factor at which the best action changes."
summary_for_tutor: "Section 2 of worksheet D.1.2: An example MDP with states s_0, s_L, s_R, actions a_L, a_R and deterministic transitions, plus policies pi_L and pi_R. Exercise 2.1 verifies V_{pi_L}(s_0) = 1/(1-gamma^2) and V_{pi_R}(s_0) = 2gamma/(1-gamma^2) with the Bellman equation; Exercise 2.2 shows the breakeven discount factor is gamma = 1/2. Both exercises have collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Leon Lang (Iliad)
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/reinforcement-learning/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 2. An example MDP

Consider the MDP with state space ${\mathcal{S}} = \{s_{0}, s_{L}, s_{R}\}$, action space ${\mathcal{A}} = \{a_{L}, a_{R}\}$, and deterministic transitions as shown:

![diagram](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-rl-example-mdp-d72947fb.png)

From $s_{0}$, action $a_{L}$ leads deterministically to $s_{L}$ with reward $+1$, and action $a_{R}$ leads deterministically to $s_{R}$ with reward $+0$. From $s_{L}$ (resp. $s_{R}$), any action returns to $s_{0}$ with reward $+0$ (resp. $+2$).

Let $\pi_{L}$ denote the policy that always selects $a_{L}$, and $\pi_{R}$ the policy that always selects $a_{R}$.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.1.** Using the Bellman equation from Exercise 1.1, verify that

$$
V_{\pi_L}(s_{0}) = \frac{1}{1-\gamma^{2}}, \qquad V_{\pi_R}(s_{0}) = \frac{2\gamma}{1-\gamma^{2}}.
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Under $\pi_{L}$ all transitions are deterministic, so the Bellman equation collapses to

$$
\begin{aligned}V_{\pi_L}(s_{0})&= R(s_{0}, a_{L}, s_{L}) + \gamma\, V_{\pi_L}(s_{L}) = 1 + \gamma\, V_{\pi_L}(s_{L}), \\ V_{\pi_L}(s_{L})&= R(s_{L}, a_{L}, s_{0}) + \gamma\, V_{\pi_L}(s_{0}) = 0 + \gamma\, V_{\pi_L}(s_{0}).\end{aligned}
$$

Substituting the second into the first gives $V_{\pi_L}(s_{0}) = 1 + \gamma^{2}\, V_{\pi_L}(s_{0})$, hence

$$
V_{\pi_L}(s_{0}) = \frac{1}{1-\gamma^{2}}.
$$

Similarly, under $\pi_{R}$:

$$
\begin{aligned}V_{\pi_R}(s_{0})&= R(s_{0}, a_{R}, s_{R}) + \gamma\, V_{\pi_R}(s_{R}) = 0 + \gamma\, V_{\pi_R}(s_{R}), \\ V_{\pi_R}(s_{R})&= R(s_{R}, a_{R}, s_{0}) + \gamma\, V_{\pi_R}(s_{0}) = 2 + \gamma\, V_{\pi_R}(s_{0}).\end{aligned}
$$

Substituting yields $V_{\pi_R}(s_{0}) = \gamma\bigl(2 + \gamma\, V_{\pi_R}(s_{0})\bigr) = 2\gamma + \gamma^{2}\, V_{\pi_R}(s_{0})$, hence

$$
V_{\pi_R}(s_{0}) = \frac{2\gamma}{1-\gamma^{2}}.
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.2.** Determine the best action from state $s_{0}$ as a function of the discount factor $\gamma \in (0, 1)$. Show that the breakeven point is $\gamma = \tfrac{1}{2}$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Since any action from $s_{L}$ or $s_{R}$ deterministically returns to $s_{0}$ with the same reward, the value of any policy at $s_{0}$ is determined entirely by the action chosen at $s_{0}$. Hence comparing $V_{\pi_L}(s_{0})$ and $V_{\pi_R}(s_{0})$ suffices:

$$
V_{\pi_L}(s_{0}) - V_{\pi_R}(s_{0}) \;=\; \frac{1 - 2\gamma}{1-\gamma^{2}}.
$$

Since $1 - \gamma^{2} > 0$ for $\gamma \in (0,1)$, the sign is determined by $1 - 2\gamma$:

- $\gamma < \tfrac{1}{2}$: $a_{L}$ is optimal — the immediate reward of $1$ outweighs a discounted future reward of $2$.
- $\gamma > \tfrac{1}{2}$: $a_{R}$ is optimal — the agent is patient enough to wait one step for the larger reward.
- $\gamma = \tfrac{1}{2}$: both actions are equally good (breakeven), and each gives $V^{*}(s_{0}) = \tfrac{4}{3}$.

:::
