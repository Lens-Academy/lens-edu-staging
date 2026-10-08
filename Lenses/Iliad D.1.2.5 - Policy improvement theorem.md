---
id: '458cb954-0a67-49db-a9b9-dba9897badbc'
title: "D.1.2.5 Policy improvement theorem"
tldr: "Shows that acting greedily with respect to a policy's value function never lowers the value, and that policy iteration reaches an optimal policy in finitely many steps."
summary_for_tutor: "Section 4 of worksheet D.1.2: Policy improvement theorem. Defines the improved policy pi' greedy with respect to V_pi. Exercise 4.1 (when B V_pi = V_pi), Exercise 4.2 (V_{pi'} >= V_pi), Exercise 4.3 (policy iteration converges in finitely many steps, since there are |A|^|S| deterministic policies). Hints and collapsed solutions are given. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Leon Lang (Iliad)
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/reinforcement-learning/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 4. Policy improvement theorem

Given a policy $\pi$, define the **improved policy** $\pi'$ greedily with respect to $V_{\pi}$:

:::callout {title="Note" tone="blue"}

**Policy Improvement**

$$
\pi'(s) \in {\operatorname*{arg\,max}}_{a \in {\mathcal{A}}}\sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl(R(s,a,s') + \gamma\, V_{\pi}(s')\bigr).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.1.** In proving Exercise 3.7, we already saw that for all $s \in {\mathcal{S}}$, we have $(\mathcal{B}V_{\pi})(s) \ge V_{\pi}(s)$. When does equality hold for all states?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We have

$$
\begin{aligned}(\mathcal{B}V_{\pi})(s)&= \max_{a \in {\mathcal{A}}}\sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl(R(s,a,s') + \gamma\, V_{\pi}(s')\bigr) \\&\ge \sum_{a \in {\mathcal{A}}}\pi(a \mid s) \sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl(R(s,a,s') + \gamma\, V_{\pi}(s')\bigr) \\&= V_{\pi}(s),\end{aligned}
$$

where we used the Bellman equation in the last step. If equality holds at every state $s$, then $V_{\pi}$ is a fixed point of $\mathcal{B}$, which by uniqueness (Exercise 3.3) means $V_{\pi} = V^{*} = V_{\pi^*}$, i.e. $\pi$ is already optimal by Exercise 3.7.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 4.2.** Show that $V_{\pi'}(s) \ge V_{\pi}(s)$ for all $s \in {\mathcal{S}}$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Show that $\mathcal{B}_{\pi'}V_{\pi} \ge V_{\pi}$ pointwise using Exercise 3.5, then iterate $\mathcal{B}_{\pi'}$ and take the limit.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Exercise 3.5, $\mathcal{B}_{\pi'}V_{\pi} = \mathcal{B}V_{\pi} \ge V_{\pi}$ pointwise, where the inequality is from Exercise 4.1. Note that $\mathcal{B}_{\pi'}$ is monotone: if $V(s) \ge W(s)$ for all $s$, then $(\mathcal{B}_{\pi'}V)(s) \ge (\mathcal{B}_{\pi'}W)(s)$. Applying $\mathcal{B}_{\pi'}$ to both sides and iterating:

$$
V_{\pi} \le \mathcal{B}_{\pi'}V_{\pi} \le \mathcal{B}_{\pi'}^{2} V_{\pi} \le \cdots \le \mathcal{B}_{\pi'}^{n} V_{\pi}.
$$

By Exercise 3.4, $\mathcal{B}_{\pi'}^{n} V_{\pi} \to V_{\pi'}$ as $n \to \infty$. Taking the limit gives $V_{\pi'}(s) \ge V_{\pi}(s)$ for all $s \in {\mathcal{S}}$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 4.3.** The **policy iteration** algorithm generates a sequence of policies $\pi_{0}, \pi_{1}, \pi_{2}, \ldots$ where each $\pi_{k+1}$ is the greedy policy with respect to $V_{\pi_k}$. Show that this sequence converges to an optimal policy $\pi^{*}$ in a finite number of steps.

:::callout {title="Hint" tone="neutral" collapse="closed"}

How many deterministic policies are there?

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Exercise 4.2, the sequence of value functions is monotonically improving: $V_{\pi_{k+1}}(s) \ge V_{\pi_k}(s)$ for all $s$ and all $k$. Since each $\pi_{k}$ is a deterministic policy and there are only $|{\mathcal{A}}|^{|{\mathcal{S}}|}$ deterministic policies, the sequence must eventually revisit a policy. If $\pi_{k+1}= \pi_{j}$ for some $j \le k$, then $V_{\pi_{k+1}}= V_{\pi_j}$, and by monotonicity $V_{\pi_j}= V_{\pi_{j+1}}= \cdots = V_{\pi_{k+1}}$. In particular $V_{\pi_k}= V_{\pi_{k+1}}$.

It remains to show this implies optimality. Since $\pi_{k+1}$ is greedy with respect to $V_{\pi_k}$, Exercise 3.5 gives $\mathcal{B}V_{\pi_k}= \mathcal{B}_{\pi_{k+1}}V_{\pi_k}$. Since $V_{\pi_{k+1}}$ is the fixed point of $\mathcal{B}_{\pi_{k+1}}$ and $V_{\pi_k}= V_{\pi_{k+1}}$, we get $\mathcal{B}_{\pi_{k+1}}V_{\pi_k}= V_{\pi_k}$. Combining: $\mathcal{B}V_{\pi_k}= V_{\pi_k}$, so $\pi_{k}$ is optimal by Exercise 4.1.

:::
