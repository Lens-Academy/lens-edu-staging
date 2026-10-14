---
id: '5f84cf24-5495-463e-93b2-085348dc5d3a'
title: "D.2.4 Potential shaping"
authors:
  - David Quarel (ARENA), based on work by Matthew Farrugia-Roberts (University of Oxford)
source_url: https://iliad-intensive.org/agency/policy-gradients-misgeneralization/
upstream_key: "policy-gradients-misgeneralization#potential-shaping"
upstream_fingerprint: "kfj1XaDkAnOZuyUv12/610/1/09Gu0L0A0Oqv0QMw0oSZ1Kt71O5e1ha527De2afw2wrn34q13XFo3dt84Gnk4lIC4or84vB658vq5DQ35JLR5aQA61IZ65756EZm6FrZ6tir7QYG7nbF7t3C7u1P7u7B"
upstream_commit: 'd5fec17706ceed1fa028ca949b97b92dcc2f5f7e'
synced_from:
  source: "iliad"
  url: "https://iliad-intensive.org/agency/policy-gradients-misgeneralization/#potential-shaping"
---

#### Text
content::
\### Potential shaping

The notebook shapes the reward with a potential function. These exercises show this cannot change the optimal policy.

:::callout {title="Definition" tone="blue"}

**Definition (Potential shaping).** Take an MDP with states $$\mathcal{S}$$, reward $$R(s,a,s')$$ and discount $$\gamma \in [0,1)$$. A *potential* is a bounded $$\Phi : \mathcal{S} \to \mathbb{R}$$. The *shaped reward* is

$$
R^\Phi(s,a,s') = R(s,a,s') + \gamma\,\Phi(s') - \Phi(s).
$$

:::

For a trajectory $$s_0, a_0, r_1, s_1, a_1, r_2, \ldots$$, taking action $$a_t$$ in state $$s_t$$ returns the next state $$s_{t+1}$$ and reward $$r_{t+1} = R(s_t,a_t,s_{t+1})$$. Write $$r^\Phi_{t+1} = R^\Phi(s_t,a_t,s_{t+1})$$, $$G = \sum_{t=0}^\infty \gamma^t r_{t+1}$$ and $$G^\Phi = \sum_{t=0}^\infty \gamma^t r^\Phi_{t+1}$$.

:::callout {title="Exercise" tone="amber"}

**Exercise 1.** Show that

$$
\sum_{t=0}^{T-1} \gamma^t \big( \gamma\,\Phi(s_{t+1}) - \Phi(s_t) \big) = \gamma^T \Phi(s_T) - \Phi(s_0).
$$

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

With $$x_t = \gamma^t \Phi(s_t)$$,

$$
\gamma^t \big( \gamma\,\Phi(s_{t+1}) - \Phi(s_t) \big) = \gamma^{t+1}\Phi(s_{t+1}) - \gamma^t \Phi(s_t) = x_{t+1} - x_t,
$$

so

$$
\sum_{t=0}^{T-1} (x_{t+1} - x_t) = x_T - x_0 = \gamma^T \Phi(s_T) - \Phi(s_0).
$$

:::

:::callout {title="Exercise" tone="amber"}

**Exercise 2.** Show that $$G^\Phi = G - \Phi(s_0)$$. Where are boundedness of $$\Phi$$ and $$\gamma < 1$$ used?

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Truncate at $$T$$ and apply Exercise 1:

$$
\sum_{t=0}^{T-1} \gamma^t r^\Phi_{t+1}
= \sum_{t=0}^{T-1} \gamma^t r_{t+1} + \sum_{t=0}^{T-1} \gamma^t \big( \gamma\,\Phi(s_{t+1}) - \Phi(s_t) \big)
= \sum_{t=0}^{T-1} \gamma^t r_{t+1} + \gamma^T \Phi(s_T) - \Phi(s_0).
$$

If $$|\Phi| \le M$$ then $$|\gamma^T \Phi(s_T)| \le \gamma^T M \to 0$$ as $$T \to \infty$$, since $$\gamma < 1$$. Letting $$T \to \infty$$ gives $$G^\Phi = G - \Phi(s_0)$$. (An unbounded $$\Phi$$ could grow like $$\gamma^{-T}$$, and the boundary term would not vanish.)

:::

:::callout {title="Exercise" tone="amber"}

**Exercise 3.** Show that $$Q^\pi_{R^\Phi}(s,a) = Q^\pi_R(s,a) - \Phi(s)$$ for every policy $$\pi$$.

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Using Exercise 2, and that $$s_0 = s$$ under the conditioning:

$$
Q^\pi_{R^\Phi}(s,a)
= \mathbb{E}_\pi\big[ G^\Phi \mid s_0 = s, a_0 = a \big]
= \mathbb{E}_\pi\big[ G - \Phi(s_0) \mid s_0 = s, a_0 = a \big]
= Q^\pi_R(s,a) - \Phi(s).
$$

:::

:::callout {title="Exercise" tone="amber"}

**Exercise 4.** Assume $$\mathcal{S}$$ and the action set $$\mathcal{A}$$ are finite, so an optimal policy exists ([D.1.2, Exercise 3.7](https://iliad-intensive.org/agency/reinforcement-learning/#prob-optimality)). Show that $$R$$ and $$R^\Phi$$ have the same optimal policies, and that $$Q^*_{R^\Phi}(s,a) = Q^*_R(s,a) - \Phi(s)$$.

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Averaging Exercise 3 over $$a \sim \pi(\cdot \mid s)$$ gives $$V^\pi_{R^\Phi}(s) = V^\pi_R(s) - \Phi(s)$$. The shift $$\Phi(s)$$ is the same for every policy, so for all policies $$\pi, \pi'$$ and states $$s$$

$$
V^\pi_{R^\Phi}(s) \ge V^{\pi'}_{R^\Phi}(s) \iff V^\pi_R(s) \ge V^{\pi'}_R(s).
$$

A policy is optimal if its value is at least that of every other policy in every state, so $$\pi$$ is optimal for $$R$$ iff it is optimal for $$R^\Phi$$.

Now take an optimal policy $$\pi^*$$ for $$R$$, which exists by D.1.2. It is also optimal for $$R^\Phi$$, so by Exercise 3

$$
Q^*_{R^\Phi}(s,a) = Q^{\pi^*}_{R^\Phi}(s,a) = Q^{\pi^*}_R(s,a) - \Phi(s) = Q^*_R(s,a) - \Phi(s).
$$

(For episodic tasks the same holds if $$\Phi = 0$$ at terminal states, so the boundary term in Exercise 2 vanishes.)

:::

:::callout {title="Exercise" tone="amber"}

**Exercise 5.** In the notebook, $$\Phi = 0.5$$ while holding a shard and $$0$$ otherwise. What shaping bonus does picking up a shard and dropping it again earn? What if we instead paid $$+0.5$$ per `PICKUP`?

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The robot goes $$s \to s' \to s''$$ with $$\Phi(s) = \Phi(s'') = 0$$ and $$\Phi(s') = 0.5$$. The discounted shaping bonus is

$$
\big( \gamma\,\Phi(s') - \Phi(s) \big) + \gamma \big( \gamma\,\Phi(s'') - \Phi(s') \big) = 0.5\gamma - 0.5\gamma = 0.
$$

Paying $$+0.5$$ per pickup instead, repeating the cycle forever earns $$0.5 + 0.5\gamma^2 + 0.5\gamma^4 + \cdots = \frac{0.5}{1-\gamma^2} > 0$$, so an agent can farm it rather than bin shards.

:::
