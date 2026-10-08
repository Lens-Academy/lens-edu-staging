---
id: 'b5900138-d124-4487-8caf-e9859cd480c6'
title: "D.3.2.4 Existence of optimal policies"
tldr: "Proves a deterministic optimal policy exists for finite and infinite horizons by showing the Bellman equation, backward induction, and convergence of the optimal values."
summary_for_tutor: "Section 2 of worksheet D.3.2: Existence of optimal policies. Exercises 2.1 (sup over policies of a one-step expectation equals the max), 2.2 (Bellman equation for V^{pi,m}), 2.3 (backward induction gives a deterministic optimal policy for finite m), 2.4 (Bellman optimality equation), 2.5 (V* exists as a monotone limit), 2.6 (infinite-horizon Bellman optimality equation) and 2.7 (a deterministic optimal policy exists for infinite horizon). Hints and collapsed solutions are given. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 2. Existence of Optimal Policies

Recall that $$V_{\nu}^{*}({\text{\ae}}_{<t}) := \sup_{\pi} V_{\nu}^{\pi}({\text{\ae}}_{<t})$$ is defined as a supremum over all policies. In general, a supremum need not be achieved: for example, $$\sup_{x \in (0,1)}x = 1$$, but no $$x \in (0,1)$$ attains this value. This problem shows that in our setting, the supremum *is* attained, so an optimal policy $$\pi_{\nu}^{*}$$ with $$V_{\nu}^{\pi_\nu^*}= V_{\nu}^{*}$$ exists.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.1 [05].** Consider a single time step. Given history $${\text{\ae}}_{<t}$$ and a function $$Q : {\mathcal{A}} \to \mathbb{R}$$, show that $$\sup_{\pi} \sum_{a \in {\mathcal{A}}}\pi(a \mid {\text{\ae}}_{<t})\, Q(a) = \max_{a \in {\mathcal{A}}}Q(a)$$, and that the supremum is attained by the deterministic policy that places all probability on an action achieving the maximum.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Let $$a^{*} \in {\operatorname*{arg\,max}}_{a' \in {\mathcal{A}}}Q(a')$$, which exists because $${\mathcal{A}}$$ is finite. So $$Q(a^{*}) = \max_{a'}Q(a')$$.

*Upper bound.* For any $$\pi$$: $$\sum_{a} \pi(a \mid {\text{\ae}}_{<t}) Q(a) \leq \sum_{a} \pi(a \mid {\text{\ae}}_{<t}) Q(a^{*}) = Q(a^{*})$$.

*Lower bound.* The deterministic $$\pi^{*}$$ with $$\pi^{*}(a^{*} \mid {\text{\ae}}_{<t}) = 1$$ achieves $$Q(a^{*})$$.

Combining: $$\sup_{\pi} \sum_{a} \pi(a) Q(a) = Q(a^{*}) = \max_{a'}Q(a')$$, attained by $$\pi^{*}$$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 2.2 (Bellman equation) [15].** Show that for finite $$m$$ and $$t \leq m$$:

$$
V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) ~=~ \sum_{{\text{\ae}}'_t}\nu^{\pi}({\text{\ae}}'_{t} \mid {\text{\ae}}_{<t}) \Big[(1-\gamma)\, r'_{t} ~+~ \gamma\, V_{\nu}^{\pi,m}({\text{\ae}}_{<t}\, {\text{\ae}}'_{t})\Big],
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Use the general chain rule (Exercise 0.5) to peel off the *first* step,

$$
\nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) ~=~ \nu^{\pi}({\text{\ae}}_{t} \mid {\text{\ae}}_{<t}) \cdot \nu^{\pi}({\text{\ae}}_{t+1:m}\mid {\text{\ae}}_{1:t}).
$$

Break up the sum $$\sum_{{\text{\ae}}_{t:m}}= \sum_{{\text{\ae}}_t}\sum_{{\text{\ae}}_{t+1:m}}$$, and factor out $$r'_{t}$$ using $$\sum_{{\text{\ae}}'_{t+1:m}}\nu^{\pi}({\text{\ae}}'_{t+1:m}\mid {\text{\ae}}) = 1$$ for any history $${\text{\ae}}$$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*Step 1: Factor the future.* Write $${\text{\ae}}'_{t:m}= {\text{\ae}}'_{t}\, {\text{\ae}}'_{t+1:m}$$: $$\nu^{\pi}({\text{\ae}}'_{t:m}\mid {\text{\ae}}_{<t}) = \nu^{\pi}({\text{\ae}}'_{t} \mid {\text{\ae}}_{<t}) \cdot \nu^{\pi}({\text{\ae}}'_{t+1:m}\mid {\text{\ae}}_{<t}\, {\text{\ae}}'_{t})$$.

*Step 2: Split the reward sum.* This is just the return recursion (Definition 0.3): $$G_{t-1:m}= r'_{t} + \gamma\, G_{t:m}$$, where $$G_{t-1:m}= \sum_{k=t}^{m}\gamma^{k-t}r'_{k}$$ is the return given $${\text{\ae}}_{<t}$$.

*Step 3: Substitute into the definition of $$V_{\nu}^{\pi,m}({\text{\ae}}_{<t})$$.*

$$
\begin{aligned}V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) ~&=~ (1-\gamma) \sum_{{\text{\ae}}'_t}\nu^{\pi}({\text{\ae}}'_{t} \mid {\text{\ae}}_{<t}) \sum_{{\text{\ae}}'_{t+1:m}}\nu^{\pi}({\text{\ae}}'_{t+1:m}\mid {\text{\ae}}_{<t}\, {\text{\ae}}'_{t}) \\&\qquad \times \left[ r'_{t} + \gamma G_{t:m}\right].\end{aligned}
$$

Consider the inner term $$\sum_{{\text{\ae}}'_{t+1:m}}\nu^{\pi}({\text{\ae}}'_{t+1:m}\mid {\text{\ae}}_{<t}\, {\text{\ae}}'_{t}) \left[ r'_{t} + \gamma G_{t:m}\right]$$. We can expand as:

$$
\begin{aligned}&= \sum_{{\text{\ae}}'_{t+1:m}}\nu^{\pi}({\text{\ae}}'_{t+1:m}\mid {\text{\ae}}_{<t}\, {\text{\ae}}'_{t}) r'_{t} + \gamma \sum_{{\text{\ae}}'_{t+1:m}}\nu^{\pi}({\text{\ae}}'_{t+1:m}\mid {\text{\ae}}_{<t}\, {\text{\ae}}'_{t}) G_{t:m}\\&= r'_{t} \cancel{\sum_{{\text{\ae}}'_{t+1:m}} \nu^\pi({\text{\ae}}'_{t+1:m} \mid {\text{\ae}}_{<t}\, {\text{\ae}}'_t)}+ \gamma \sum_{{\text{\ae}}'_{t+1:m}}\nu^{\pi}({\text{\ae}}'_{t+1:m}\mid {\text{\ae}}_{<t}\, {\text{\ae}}'_{t}) G_{t:m}\\&= r'_{t} + \gamma \sum_{{\text{\ae}}'_{t+1:m}}\nu^{\pi}({\text{\ae}}'_{t+1:m}\mid {\text{\ae}}_{<t}\, {\text{\ae}}'_{t}) G_{t:m}\end{aligned}
$$

as $$r'_{t}$$ doesn't depend on $${\text{\ae}}'_{t+1:m}$$, and $$\sum_{{\text{\ae}}'_{t+1:m}}\nu^{\pi}({\text{\ae}}'_{t+1:m}\mid {\text{\ae}}_{<t}\, {\text{\ae}}'_{t}) = 1$$. Inserting this above, we obtain:

$$
\begin{aligned}V_{\nu}^{\pi,m}({\text{\ae}}_{<t})&= \sum_{{\text{\ae}}'_t}\nu^{\pi}({\text{\ae}}'_{t} \mid {\text{\ae}}_{<t}) \bigg[ (1-\gamma)\, r'_{t} \\&\qquad + \gamma\, \underbrace{(1-\gamma) \sum_{{\text{\ae}}'_{t+1:m}} \nu^\pi({\text{\ae}}'_{t+1:m} \mid {\text{\ae}}_{<t}\, {\text{\ae}}'_t)G_{t:m}}_{=\; V_\nu^{\pi,m}({\text{\ae}}_{<t}\, {\text{\ae}}'_t)}\bigg].\end{aligned}
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.3 (∗) (Backward induction) [20].** Using the Bellman equation from Exercise 2.2 and Exercise 2.1, show by backward induction on $$t = m, m-1, \ldots, 1$$ that for each finite $$m$$, a deterministic optimal policy exists.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We induct on $$t = m, m-1, \ldots, 1$$, showing that for every history $${\text{\ae}}_{<t}$$, a deterministic policy achieves $$V_{\nu}^{*,m}({\text{\ae}}_{<t})$$.

*Base case ($$t = m$$):* At $$t = m$$ the continuation term vanishes (the value from time $$m+1$$ is an empty sum), so the Bellman equation gives $$V_{\nu}^{\pi,m}({\text{\ae}}_{<m}) = (1-\gamma) \sum_{{\text{\ae}}'_m}\nu^{\pi}({\text{\ae}}'_{m} \mid {\text{\ae}}_{<m})\, r'_{m}$$. Splitting the step $${\text{\ae}}'_{m} = a'_{m} e'_{m}$$ via $$\nu^{\pi}({\text{\ae}}'_{m} \mid {\text{\ae}}_{<m}) = \pi(a'_{m} \mid {\text{\ae}}_{<m})\, \nu(e'_{m} \mid {\text{\ae}}_{<m}a'_{m})$$ gives $$V_{\nu}^{\pi,m}({\text{\ae}}_{<m}) = (1-\gamma) \sum_{a'_m}\pi(a'_{m} \mid {\text{\ae}}_{<m}) \sum_{e'_m}\nu(e'_{m} \mid {\text{\ae}}_{<m}a'_{m})\, r'_{m}$$. This has the form $$\sum_{a} \pi(a) Q(a)$$ with $$Q(a) = (1-\gamma)\sum_{e'_m}\nu(e'_{m} \mid {\text{\ae}}_{<m}a)\, r'_{m}$$, which is independent of $$\pi$$. By Exercise 2.1, the supremum over $$\pi$$ is $$\max_{a} Q(a)$$, attained by the deterministic policy playing $$a^{*} \in {\operatorname*{arg\,max}}_{a} Q(a)$$.

*Inductive step:* Suppose that for every history of length $$t$$, there exists a deterministic policy $$\pi^{*}_{t+1}$$ achieving $$V_{\nu}^{\pi^*_{t+1},m}= V_{\nu}^{*,m}$$ from time $$t+1$$ onwards. Substituting this optimal continuation into the Bellman equation from Exercise 2.2 gives

$$
V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) ~=~ \sum_{{\text{\ae}}'_t}\nu^{\pi}({\text{\ae}}'_{t} \mid {\text{\ae}}_{<t}) \big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}({\text{\ae}}_{<t}\, {\text{\ae}}'_{t})\big].
$$

Splitting the step $${\text{\ae}}'_{t} = a'_{t} e'_{t}$$ via $$\nu^{\pi}({\text{\ae}}'_{t} \mid {\text{\ae}}_{<t}) = \pi(a'_{t} \mid {\text{\ae}}_{<t})\, \nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t})$$ and grouping the percept sum into the action weight:

$$
V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) ~=~ \sum_{a'_t}\pi(a'_{t} \mid {\text{\ae}}_{<t})\, Q(a'_{t}),
$$

where $$Q(a'_{t}) := \sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t}) [(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}({\text{\ae}}_{<t}\, a'_{t}\, e'_{t})]$$ is independent of $$\pi$$ (the continuation value $$V_{\nu}^{*,m}$$ is fixed by the inductive hypothesis). By Exercise 2.1, $$\sup_{\pi} \sum_{a'_t}\pi(a'_{t})\, Q(a'_{t}) = \max_{a'_t}Q(a'_{t})$$, attained by the deterministic policy playing $$a^{*}_{t} \in {\operatorname*{arg\,max}}_{a'_t}Q(a'_{t})$$ at time $$t$$, then following $$\pi^{*}_{t+1}$$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.4 (Bellman optimality equation) [10].** Using Exercise 2.3, show that for finite $$m$$:

$$
V_{\nu}^{*,m}({\text{\ae}}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} ~+~ \gamma\, V_{\nu}^{*,m}({\text{\ae}}_{<t}\, {\text{\ae}}'_{t})\Big].
$$

where $$e_{t}' = o_{t}' r_{t}'$$ and $${\text{\ae}}'_{t} = a'_{t} e'_{t}$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Exercise 2.3, a deterministic optimal policy $$\pi^{*}_{\nu}$$ exists with $$V_{\nu}^{\pi^*_\nu,m}= V_{\nu}^{*,m}$$. Substituting $$\pi = \pi^{*}_{\nu}$$ into the Bellman equation from Exercise 2.2 (using $$V_{\nu}^{\pi^*_\nu,m}= V_{\nu}^{*,m}$$ on both sides):

$$
V_{\nu}^{*,m}({\text{\ae}}_{<t}) ~=~ \sum_{{\text{\ae}}'_t}\nu^{\pi^*_\nu}({\text{\ae}}'_{t} \mid {\text{\ae}}_{<t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}({\text{\ae}}_{<t}\, {\text{\ae}}'_{t})\Big].
$$

Splitting the step $${\text{\ae}}'_{t} = a'_{t} e'_{t}$$ via $$\nu^{\pi^*_\nu}({\text{\ae}}'_{t} \mid {\text{\ae}}_{<t}) = \pi^{*}_{\nu}(a'_{t} \mid {\text{\ae}}_{<t})\, \nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t})$$:

$$
\begin{aligned}V_{\nu}^{*,m}({\text{\ae}}_{<t}) ~&=~ \sum_{a'_t}\pi^{*}_{\nu}(a'_{t} \mid {\text{\ae}}_{<t}) \\&\qquad \times \sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}({\text{\ae}}_{<t}\, a'_{t}\, e'_{t})\Big].\end{aligned}
$$

Since $$\pi^{*}_{\nu}$$ is deterministic, let $$a^{*}_{t}$$ denote the unique action with $$\pi^{*}_{\nu}(a^{*}_{t} \mid {\text{\ae}}_{<t}) = 1$$. Then:

$$
V_{\nu}^{*,m}({\text{\ae}}_{<t}) ~=~ \sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a^{*}_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}({\text{\ae}}_{<t}\, a^{*}_{t}\, e'_{t})\Big].
$$

Define $$Q(a) := \sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a) [(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}({\text{\ae}}_{<t}\, a\, e'_{t})]$$. Then $$V_{\nu}^{*,m}({\text{\ae}}_{<t}) = Q(a^{*}_{t})$$. We must have $$Q(a^{*}_{t}) = \max_{a}Q(a)$$: if some $$\tilde{a}$$ had $$Q(\tilde{a}) > Q(a^{*}_{t})$$, then the policy that plays $$\tilde{a}$$ at $${\text{\ae}}_{<t}$$ and follows $$\pi^{*}_{\nu}$$ elsewhere would achieve value $$Q(\tilde{a}) > V_{\nu}^{*,m}({\text{\ae}}_{<t})$$, contradicting $$V_{\nu}^{*,m}= \sup_{\pi} V_{\nu}^{\pi,m}$$. Hence:

$$
V_{\nu}^{*,m}({\text{\ae}}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}({\text{\ae}}_{<t}\, a'_{t}\, e'_{t})\Big].
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 2.5 (∗) [15].** (Existence of $$V_{\nu}^{*}$$) Show that the pointwise limit $$V_{\nu}^{*}({\text{\ae}}_{<t}) := \lim_{m \to \infty}V_{\nu}^{*,m}({\text{\ae}}_{<t})$$ exists for all histories $${\text{\ae}}_{<t}$$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Show $$V_{\nu}^{*,m+1}({\text{\ae}}_{<t}) \geq V_{\nu}^{*,m}({\text{\ae}}_{<t})$$ by expanding $$V_{\nu}^{*,m+1}$$. Use this and Exercise 1.3 and [Monotone Convergence Theorem](https://en.wikipedia.org/wiki/Monotone_convergence_theorem) to obtain the result.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We show $$V_{\nu}^{*,m+1}({\text{\ae}}_{<t}) \geq V_{\nu}^{*,m}({\text{\ae}}_{<t})$$ for all $${\text{\ae}}_{<t}$$. Since $$V_{\nu}^{*,m+1}= \sup_{\pi} V_{\nu}^{\pi,m+1}$$, it suffices to show $$V_{\nu}^{\pi,m+1}({\text{\ae}}_{<t}) \geq V_{\nu}^{\pi,m}({\text{\ae}}_{<t})$$ for every $$\pi$$. Expanding the definition:

$$
\begin{aligned}&V_{\nu}^{\pi,m+1}({\text{\ae}}_{<t}) \\ ~&=~ (1-\gamma) \sum_{{\text{\ae}}_{t:m+1}}\nu^{\pi}({\text{\ae}}_{t:m+1}\mid {\text{\ae}}_{<t})\, G_{t-1:m+1}\\ ~&=~ (1-\gamma) \sum_{{\text{\ae}}_{t:m+1}}\nu^{\pi}({\text{\ae}}_{t:m+1}\mid {\text{\ae}}_{<t}) \left[G_{t-1:m}~+~ \gamma^{m+1-t}r_{m+1}\right] \\ ~&=~ (1-\gamma) \sum_{{\text{\ae}}_{t:m+1}}\nu^{\pi}({\text{\ae}}_{t:m+1}\mid {\text{\ae}}_{<t}) G_{t-1:m}\\ ~&\qquad+~ \underbrace{(1-\gamma)\, \gamma^{m+1-t} \sum_{{\text{\ae}}_{t:m+1}} \nu^\pi({\text{\ae}}_{t:m+1} \mid {\text{\ae}}_{<t})\, r_{m+1}}_{\geq\; 0}.\end{aligned}
$$

For the first term, marginalize over $$a_{m+1}, e_{m+1}$$ (which $$G_{t-1:m}$$ does not depend on):

$$
\sum_{{\text{\ae}}_{t:m+1}}\nu^{\pi}({\text{\ae}}_{t:m+1}\mid {\text{\ae}}_{<t}) G_{t-1:m}~=~ \sum_{{\text{\ae}}_{t:m}}\nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) G_{t-1:m}.
$$

So $$V_{\nu}^{\pi,m+1}({\text{\ae}}_{<t}) \geq (1-\gamma) \sum_{{\text{\ae}}_{t:m}}\nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t}) G_{t-1:m}= V_{\nu}^{\pi,m}({\text{\ae}}_{<t})$$.

Since $$V_{\nu}^{*,m}({\text{\ae}}_{<t})$$ is non-decreasing in $$m$$ and bounded in $$[0,1]$$ by Exercise 1.3, the monotone convergence theorem gives that $$V_{\nu}^{*}({\text{\ae}}_{<t}) := \lim_{m \to \infty}V_{\nu}^{*,m}({\text{\ae}}_{<t})$$ exists for each $${\text{\ae}}_{<t}$$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.6 (Infinite-horizon Bellman optimality equation) [10].** Show that the Bellman optimality equation (Exercise 2.4) extends to $$m = \infty$$:

$$
V_{\nu}^{*}({\text{\ae}}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} ~+~ \gamma\, V_{\nu}^{*}({\text{\ae}}_{<t}\, a'_{t}\, e'_{t})\Big].
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Exercise 2.4, for every finite $$m$$:

$$
V_{\nu}^{*,m}({\text{\ae}}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*,m}({\text{\ae}}_{<t}\, a'_{t}\, e'_{t})\Big].
$$

By Exercise 2.5, each $$V_{\nu}^{*,m}(\cdot)$$ converges pointwise to $$V_{\nu}^{*}(\cdot)$$ as $$m \to \infty$$. Since $${\mathcal{A}}$$ and $${\mathcal{E}}$$ are finite, the $$\max$$ and $$\sum$$ are over finitely many convergent terms, so:

$$
V_{\nu}^{*}({\text{\ae}}_{<t}) ~=~ \max_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*}({\text{\ae}}_{<t}\, a'_{t}\, e'_{t})\Big].
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.7 (∗) (Optimal policy for infinite horizon) [25].** Show that a deterministic policy $$\pi_{\nu}^{*}$$ exists achieving $$V_{\nu}^{\pi_\nu^*}({\text{\ae}}_{<t}) = V_{\nu}^{*}({\text{\ae}}_{<t})$$ for all $${\text{\ae}}_{<t}$$.

*Approach:*

**(a)** Define $$\pi_{\nu}^{*}$$ as the greedy policy (the $${\operatorname*{arg\,max}}$$ action from Exercise 2.6).

**(b)** Write two Bellman equations: one for $$V_{\nu}^{*}$$, one for $$V_{\nu}^{\pi_\nu^*, m}$$.

**(c)** Define $$\Delta V_{\nu}^{m} := V_{\nu}^{*} - V_{\nu}^{\pi_\nu^*, m}$$ and obtain a recursive equation for it.

**(d)** Iterate out to the finite horizon, noting $$V_{\nu}^{\pi_\nu^*, m}({\text{\ae}}_{1:m}) = 0$$ (why?)

**(e)** Bound the tail, take $$m \to \infty$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*Step 1: Define the greedy policy.* For each history $${\text{\ae}}_{<t}$$, let

$$
a^{*}_{t} \in {\operatorname*{arg\,max}}_{a'_t}\sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}a'_{t}) [(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*}({\text{\ae}}_{<t}\, a'_{t}\, e'_{t})],
$$

which exists because $${\mathcal{A}}$$ is finite. Define the deterministic policy $$\pi_{\nu}^{*}(a \mid {\text{\ae}}_{<t}) := \llbracket a = a^{*}_{t} \rrbracket$$. By Exercise 2.6, the infinite-horizon Bellman optimality equation becomes:

$$
V_{\nu}^{*}({\text{\ae}}_{<t}) ~=~ \sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}\, a^{*}_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{*}({\text{\ae}}_{<t}\, a^{*}_{t}\, e'_{t})\Big].
$$

*Step 2: Error recursion.* The Bellman equation (Exercise 2.2) holds for any policy, so for $$\pi_{\nu}^{*}$$ at finite horizon $$m$$:

$$
V_{\nu}^{\pi_\nu^*,m}({\text{\ae}}_{<t}) ~=~ \sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}\, a^{*}_{t}) \Big[(1-\gamma)\, r'_{t} + \gamma\, V_{\nu}^{\pi_\nu^*,m}({\text{\ae}}_{<t}\, a^{*}_{t}\, e'_{t})\Big].
$$

Subtracting this from the equation in Step 1, the $$(1-\gamma)\, r'_{t}$$ terms cancel:

$$
\begin{aligned}V_{\nu}^{*}({\text{\ae}}_{<t}) - V_{\nu}^{\pi_\nu^*,m}({\text{\ae}}_{<t}) ~&=~ \gamma \sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}\, a^{*}_{t}) \\&\qquad \times \Big[V_{\nu}^{*}({\text{\ae}}_{<t}\, a^{*}_{t}\, e'_{t}) - V_{\nu}^{\pi_\nu^*,m}({\text{\ae}}_{<t}\, a^{*}_{t}\, e'_{t})\Big].\end{aligned}
$$

The error at time $$t$$ is $$\gamma$$ times a weighted average of errors at time $$t+1$$.

*Step 3: Iterate the contraction.* Write $$\Delta V_{\nu}^{m}({\text{\ae}}_{<t}) := V_{\nu}^{*}({\text{\ae}}_{<t}) - V_{\nu}^{\pi_\nu^*,m}({\text{\ae}}_{<t}) \geq 0$$ for the error. Step 2 gives:

$$
\Delta V_{\nu}^{m}({\text{\ae}}_{<t}) ~=~ \gamma \sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}\, a^{*}_{t})\, \Delta V_{\nu}^{m}({\text{\ae}}_{<t}\, a^{*}_{t}\, e'_{t}).
$$

Applying the same recursion at time $$t+1$$ (with greedy action $$a^{*}_{t+1}$$ at history $${\text{\ae}}_{<t}\, a^{*}_{t}\, e'_{t}$$):

$$
\Delta V_{\nu}^{m}({\text{\ae}}_{<t}) ~=~ \gamma^{2} \sum_{e'_t}\nu(e'_{t} \mid {\text{\ae}}_{<t}\, a^{*}_{t}) \sum_{e'_{t+1}}\nu(e'_{t+1}\mid {\text{\ae}}_{<t}\, a^{*}_{t}\, e'_{t}\, a^{*}_{t+1})
$$

$$
\qquad \times \Delta V_{\nu}^{m}({\text{\ae}}_{<t}\, a^{*}_{t}\, e'_{t}\, a^{*}_{t+1}\, e'_{t+1}).
$$

After $$m - t + 1$$ iterations, summing over all percept sequences $$e'_{t:m}$$:

$$
\Delta V_{\nu}^{m}({\text{\ae}}_{<t}) ~=~ \gamma^{m-t+1}\sum_{e'_{t:m}}\left(\prod_{k=t}^{m} \nu(e'_{k} \mid {\text{\ae}}'_{<k}\, a^{*}_{k})\right) \Delta V_{\nu}^{m}({\text{\ae}}_{<t}\, {\text{\ae}}'_{t:m}),
$$

where $${\text{\ae}}'_{t:m}= a^{*}_{t}\, e'_{t}\, \cdots\, a^{*}_{m}\, e'_{m}$$ is the history segment generated by $$\pi_{\nu}^{*}$$. By Exercise 0.4, the product of $$\nu$$-conditionals is $$\nu^{\pi_\nu^*}({\text{\ae}}'_{t:m}\mid {\text{\ae}}_{<t})$$. At the boundary, $$V_{\nu}^{\pi_\nu^*,m}({\text{\ae}}_{<t}\, {\text{\ae}}'_{t:m}) = 0$$ (summing over no rewards past horizon $$m$$), so $$\Delta V_{\nu}^{m}({\text{\ae}}_{<t}\, {\text{\ae}}'_{t:m}) = V_{\nu}^{*}({\text{\ae}}_{<t}\, {\text{\ae}}'_{t:m}) \in [0,1]$$. Therefore:

$$
\Delta V_{\nu}^{m}({\text{\ae}}_{<t}) ~=~ \gamma^{m-t+1}\sum_{{\text{\ae}}'_{t:m}}\nu^{\pi_\nu^*}({\text{\ae}}'_{t:m}\mid {\text{\ae}}_{<t})\, V_{\nu}^{*}({\text{\ae}}_{<t}\, {\text{\ae}}'_{t:m}) ~\leq~ \gamma^{m-t+1}.
$$

*Step 4: Take $$m \to \infty$$.* Since $$0 \leq V_{\nu}^{*}({\text{\ae}}_{<t}) - V_{\nu}^{\pi_\nu^*,m}({\text{\ae}}_{<t}) \leq \gamma^{m-t+1}\to 0$$, we have $$V_{\nu}^{\pi_\nu^*,m}({\text{\ae}}_{<t}) \to V_{\nu}^{*}({\text{\ae}}_{<t})$$, i.e. $$V_{\nu}^{\pi_\nu^*}= V_{\nu}^{*}$$.

:::
