---
id: '006192b3-8949-4324-a668-50c0953ba05c'
title: "D.1.2.4 Bellman operators and optimal policies"
tldr: "Proves that the Bellman optimality and policy operators are contractions, so a unique optimal value function exists and a greedy policy attains it."
summary_for_tutor: "Section 3 of Iliad worksheet D.1.2: Bellman operators and the existence of optimal policies. States the Banach fixed point theorem (Theorem 3.1) and defines the Bellman optimality operator (Definition 3.2) and policy operator B_pi. Exercises 3.1-3.7: max inequality, B is a gamma-contraction, unique fixed point V*, B_pi contraction with fixed point V_pi, greedy policy satisfies B_{pi_V}V = BV, V_{pi*} = V*, and pi* is optimal. Hints and collapsed solutions are given. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Leon Lang (Iliad)
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/reinforcement-learning/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 3. Bellman operators and the existence of optimal policies

\### Banach fixed-point theorem

In this and the following exercises, we will make use of the well-known Banach fixed point theorem:

:::callout {title="Theorem" tone="green"}

**Theorem 3.1 (Banach Fixed Point Theorem).** Let $(X, d)$ be a complete metric space and let $F : X \to X$ be a contraction mapping, i.e. there exists $\gamma \in 0,1)$ such that

$$
d(F(x), F(y)) \le \gamma\, d(x, y) \quad \text{for all }x, y \in X.
$$

Then $F$ has a unique fixed point $x^{*} \in X$ satisfying $F(x^{*}) = x^{*}$. Moreover, for any initial point $x_{0} \in X$, one

has $\lim_{n \to \infty}d(F^{n}(x_{0}), x^{*}) = 0$ where $F^{n}$ is the $n$-fold composition of $F$ with itself. That is, $F^{n}(x_{0})$ converges to $x^{*}$ with respect to the metric $d$.

:::

\### The problem

:::callout {title="Definition" tone="blue"}

**Definition 3.2 (Bellman optimality operator).** Let $\mathcal{V}= \{V : {\mathcal{S}} \to \mathbb{R}\}$ denote the vector space of value functions, equipped with the sup-norm $\|V\|_{\infty} = \max_{s \in {\mathcal{S}}}|V(s)|$. The **Bellman optimality operator** $\mathcal{B}: \mathcal{V}\to \mathcal{V}$ is defined by

$$
(\mathcal{B}V)(s) \coloneqq \max_{a \in {\mathcal{A}}}\sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl(R(s,a,s') + \gamma\, V(s')\bigr).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.1.** Let $f, g : {\mathcal{A}} \to \mathbb{R}$ be real-valued functions on a finite set ${\mathcal{A}}$. Prove that

$$
\left|\max_{a \in {\mathcal{A}}}f(a) - \max_{a \in {\mathcal{A}}}g(a)\right| \le \max_{a \in {\mathcal{A}}}|f(a) - g(a)|.
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Without loss of generality, assume $\max_{a}f(a) \ge \max_{a}g(a)$. Let $a^{*} \in {\operatorname*{arg\,max}}_{a \in {\mathcal{A}}}f(a)$. Then:

$$
\begin{aligned}\left|\max_{a \in {\mathcal{A}}}f(a) - \max_{a \in {\mathcal{A}}}g(a)\right|&= \max_{a \in {\mathcal{A}}}f(a) - \max_{a \in {\mathcal{A}}}g(a) \\&= f(a^{*}) - \max_{a \in {\mathcal{A}}}g(a) \\&\le f(a^{*}) - g(a^{*}) \\&= |f(a^{*}) - g(a^{*})| \\&\le \max_{a \in {\mathcal{A}}}|f(a) - g(a)|.\end{aligned}
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.2.** Using [Exercise 3.1, prove that $\mathcal{B}$ is a **contraction mapping** with contraction factor $\gamma$, i.e. for all $V, W \in \mathcal{V}$,

$$
\|\mathcal{B}V - \mathcal{B}W\|_{\infty} \le \gamma\, \|V - W\|_{\infty}.
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Fix an arbitrary state $s \in {\mathcal{S}}$. Define for each $a \in {\mathcal{A}}$:

$$
\begin{aligned}f(a)&\coloneqq \sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl(R(s,a,s') + \gamma\, V(s')\bigr), \\ g(a)&\coloneqq \sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl(R(s,a,s') + \gamma\, W(s')\bigr).\end{aligned}
$$

Then $(\mathcal{B}V)(s) = \max_{a} f(a)$ and $(\mathcal{B}W)(s) = \max_{a} g(a)$. By Exercise 3.1:

$$
\begin{aligned}\big|(\mathcal{B}V)(s) - (\mathcal{B}W)(s)\big|&\le \max_{a \in {\mathcal{A}}}\big|f(a) - g(a)\big| \\&= \max_{a \in {\mathcal{A}}}\left|\sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\gamma\,\bigl(V(s') - W(s')\bigr)\right| \\&\le \gamma \max_{a \in {\mathcal{A}}}\sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\,\big|V(s') - W(s')\big| \\&\le \gamma \max_{a \in {\mathcal{A}}}\sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\,\|V - W\|_{\infty} \\&\le \gamma\,\|V - W\|_{\infty},\end{aligned}
$$

where the last step uses $\sum_{s'}T(s' \mid s, a) = 1$. Since this holds for every $s \in {\mathcal{S}}$, taking the maximum over $s$ gives $\|\mathcal{B}V - \mathcal{B}W\|_{\infty} \le \gamma\,\|V - W\|_{\infty}$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.3.** Using Theorem 3.1, conclude that there exists a unique $V^{*} \in \mathcal{V}$ satisfying $\mathcal{B}V^{*} = V^{*}$, and that for any initial $V_{0} \in \mathcal{V}$, the iterates $\mathcal{B}^{n} V_{0} \to V^{*}$ as $n \to \infty$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The space $(\mathcal{V}, \|\cdot\|_{\infty})$ is a finite-dimensional normed vector space, hence complete. By Exercise 3.2, $\mathcal{B}$ is a contraction on $\mathcal{V}$ with factor $\gamma < 1$. Theorem 3.1 then gives the existence of a unique fixed point $V^{*} = \mathcal{B}V^{*}$, and convergence $\mathcal{B}^{n} V_{0} \to V^{*}$ for any $V_{0} \in \mathcal{V}$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 3.4.** Show that for any policy $\pi$, the operator $\mathcal{B}_{\pi} : \mathcal{V}\to \mathcal{V}$ defined by
:::callout {title="Note" tone="blue"}

**Bellman Policy Operator**

$$
(\mathcal{B}_{\pi} V)(s) \coloneqq \sum_{a \in {\mathcal{A}}}\pi(a \mid s) \sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl(R(s,a,s') + \gamma\, V(s')\bigr)
$$

:::
is also a contraction with factor $\gamma$. Conclude that $V_{\pi}$ is its unique fixed point and that $\mathcal{B}^{n}_{\pi}V_{0} \to V_{\pi}$ for any initial $V_{0} \in \mathcal{V}$ as $n \to \infty$.

:::callout {title="Note" tone="blue"}

**Remark.** This shows that the numerical policy evaluation algorithm from the ARENA materials converges to the correct solution.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Fix $V, W \in \mathcal{V}$ and an arbitrary state $s \in {\mathcal{S}}$. Then:

$$
\begin{aligned}\big|(\mathcal{B}_{\pi} V)(s) - (\mathcal{B}_{\pi} W)(s)\big|&= \left|\sum_{a \in {\mathcal{A}}}\pi(a \mid s) \sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\,\gamma\bigl(V(s') - W(s')\bigr)\right| \\&\le \gamma \,\sum_{a \in {\mathcal{A}}}\pi(a \mid s) \sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\,\big|V(s') - W(s')\big| \\&\le \gamma \, \sum_{a \in {\mathcal{A}}}\pi(a \mid s) \sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\,\|V - W\|_{\infty}\\&\le \gamma\,\|V - W\|_{\infty},\end{aligned}
$$

where the last step uses $\sum_{s'}T(s' \mid s, a) = 1$ and $\sum_{a} \pi(a \mid s) = 1$. Taking the maximum over $s$ gives $\|\mathcal{B}_{\pi} V - \mathcal{B}_{\pi} W\|_{\infty} \le \gamma\,\|V - W\|_{\infty}$, so $\mathcal{B}_{\pi}$ is a contraction with factor $\gamma$.

By Theorem 3.1, $\mathcal{B}_{\pi}$ has a unique fixed point. By the Bellman equation (Section 1), $V_{\pi}$ satisfies $\mathcal{B}_{\pi} V_{\pi} = V_{\pi}$, so $V_{\pi}$ is this unique fixed point. The convergence statement also follows from Theorem 3.1.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.5.** Let $V \in \mathcal{V}$ be any value function, and let $\pi_{V}$ be a greedy policy with respect to $V$, i.e.

$$
\pi_{V}(s) \in {\operatorname*{arg\,max}}_{a \in {\mathcal{A}}}\sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl(R(s,a,s') + \gamma\, V(s')\bigr).
$$

Show that $\mathcal{B}_{\pi_V}V = \mathcal{B}V$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Since $\pi_{V}$ is deterministic, $\pi_{V}(a \mid s) = \llbracket a = \pi_{V}(s) \rrbracket$, so the sum over $a$ in $\mathcal{B}_{\pi_V}$ collapses to the single term $a = \pi_{V}(s)$. For every $s \in {\mathcal{S}}$:

$$
\begin{aligned}(\mathcal{B}_{\pi_V}V)(s)&= \sum_{s' \in {\mathcal{S}}}T(s' \mid s, \pi_{V}(s))\bigl(R(s,\pi_{V}(s),s') + \gamma\, V(s')\bigr) \\&= \max_{a \in {\mathcal{A}}}\sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl(R(s,a,s') + \gamma\, V(s')\bigr) \\&= (\mathcal{B}V)(s),\end{aligned}
$$

where the second equality holds because $\pi_{V}(s)$ selects a maximizing action by definition.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 3.6.** Define the **greedy policy** with respect to $V^{*}$ by $\pi^{*} = \pi_{V^*}$ as in the previous part. Show that $V_{\pi^*}= V^{*}$, i.e. the value function of $\pi^{*}$ equals the fixed point of $\mathcal{B}$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Show that $V^{*}$ satisfies the same fixed-point equation as $V_{\pi^*}$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We have $\mathcal{B}_{\pi^*}V^{*} = \mathcal{B}V^{*} = V^{*}$ by Exercise 3.5 and Exercise 3.3. So $V^{*}$ is a fixed point of $\mathcal{B}_{\pi^*}$. By Exercise 3.4, $V_{\pi^*}$ is the unique fixed point of $\mathcal{B}_{\pi^*}$. Therefore $V_{\pi^*}= V^{*}$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 3.7.** Conclude that $\pi^{*}$ is an **optimal policy**: for every policy $\pi$ and every state $s \in {\mathcal{S}}$,

$$
V_{\pi^*}(s) \ge V_{\pi}(s).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Show that $\mathcal{B}V_{\pi} \ge V_{\pi}$ pointwise, then iterate and take the limit.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Let $\pi$ be any policy. Since the max over actions is at least as large as any weighted average:

$$
(\mathcal{B}V)(s) \ge (\mathcal{B}_{\pi} V)(s) \quad \text{for all }V \in \mathcal{V},\; s \in {\mathcal{S}}.
$$

In particular, since $V_{\pi}$ is a fixed point of $\mathcal{B}_{\pi}$ (Exercise 3.4):

$$
(\mathcal{B}V_{\pi})(s) \ge (\mathcal{B}_{\pi} V_{\pi})(s) = V_{\pi}(s) \quad \text{for all }s \in {\mathcal{S}}.
$$

Note that $\mathcal{B}$ is monotone: if $V(s) \ge W(s)$ for all $s$, then $(\mathcal{B}V)(s) \ge (\mathcal{B}W)(s)$. Applying $\mathcal{B}$ to both sides and using monotonicity, then iterating:

$$
V_{\pi} \le \mathcal{B}V_{\pi} \le \mathcal{B}^{2} V_{\pi} \le \cdots \le \mathcal{B}^{n} V_{\pi}.
$$

By Exercise 3.3, $\mathcal{B}^{n} V_{\pi} \to V^{*}$ as $n \to \infty$. Taking the limit:

$$
V_{\pi}(s) \le V^{*}(s) = V_{\pi^*}(s) \quad \text{for all }s \in {\mathcal{S}},
$$

where the last equality is Exercise 3.6. Since $\pi$ was arbitrary, $\pi^{*}$ is optimal.

:::
