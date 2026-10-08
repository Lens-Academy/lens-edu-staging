---
id: '14838f3b-f8a7-48d3-939c-bcd6bee1f0d3'
title: "D.1.2.6 Bellman convergence rate"
tldr: "Derives bounds on how fast repeated Bellman updates approach V*, including a priori and a posteriori bounds and an example where the bound is tight."
summary_for_tutor: "Section 5 of worksheet D.1.2: Bellman convergence rate, with iterates V_n = B^n V_0. Exercises 5.1-5.6: ||V_n - V*|| <= gamma^n ||V_0 - V*||, the a priori bound gamma^n/(1-gamma) ||V_1 - V_0||, the a posteriori bound, the a posteriori bound is at least as tight, the bound gamma^n R_max/(1-gamma) for V_0 = 0, and a one-state MDP showing it is tight. The source is Puterman 1994, Chapter 6. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Leon Lang (Iliad)
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/reinforcement-learning/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 5. Bellman convergence rate

Exercise 3.3 showed that the iterates $V_{n} := \mathcal{B}^{n} V_{0}$ converge to $V^{*}$ for any starting $V_{0} \in \mathcal{V}$, but it did not tell us *how fast*, nor how to decide when to stop iterating. We derive some convergence rate bounds (Puterman 1994, Chapter 6).

::::callout {title="Exercise" tone="amber"}
**Exercise 5.1.** Show that for any initial $V_{0} \in \mathcal{V}$, the iterates $V_{n} := \mathcal{B}^{n} V_{0}$ satisfy

$$
\|V_{n} - V^{*}\|_{\infty} \;\le\; \gamma^{n} \|V_{0} - V^{*}\|_{\infty}.
$$

:::callout {title="Note" tone="blue"}

**Remark.** This bound is not useful as a stopping criterion in practice as it depends on the unknown $V^{*}$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Since $V^{*} = \mathcal{B}V^{*}$ and $\mathcal{B}$ is a $\gamma$-contraction (Exercise 3.2),

$$
\|V_{n} - V^{*}\|_{\infty} \;=\; \|\mathcal{B}V_{n-1}- \mathcal{B}V^{*}\|_{\infty} \;\le\; \gamma\, \|V_{n-1}- V^{*}\|_{\infty}.
$$

Iterating $n$ times gives $\|V_{n} - V^{*}\|_{\infty} \le \gamma^{n} \|V_{0} - V^{*}\|_{\infty}$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 5.2.** Show the **a priori bound**:

$$
\|V_{n} - V^{*}\|_{\infty} \;\le\; \frac{\gamma^{n}}{1-\gamma}\, \|V_{1} - V_{0}\|_{\infty}.
$$

This bound uses only $\|V_{1} - V_{0}\|_{\infty}$ — a quantity computable after a single iteration, independent of $V^{*}$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Write $V^{*} - V_{n} = \sum_{k=n}^{\infty}(V_{k+1}- V_{k})$ (valid since $V_{k} \to V^{*}$), and bound each term using the contraction of $\mathcal{B}$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By the contraction property applied repeatedly,

$$
\begin{aligned}\|V_{k+1}- V_{k}\|_{\infty} \;&=\; \|\mathcal{B}V_{k} - \mathcal{B}V_{k-1}\|_{\infty} \;\le\; \gamma\, \|V_{k} - V_{k-1}\|_{\infty} \\&\le\; \cdots \;\le\; \gamma^{k}\, \|V_{1} - V_{0}\|_{\infty}.\end{aligned}
$$

Since $V_{k} \to V^{*}$ (Exercise 3.3), we have the telescoping identity $V^{*} - V_{n} = \sum_{k=n}^{\infty}(V_{k+1}- V_{k})$. Applying the triangle inequality and the geometric bound above:

$$
\begin{aligned}\|V^{*} - V_{n}\|_{\infty} \;&\le\; \sum_{k=n}^{\infty}\|V_{k+1}- V_{k}\|_{\infty} \;\le\; \sum_{k=n}^{\infty}\gamma^{k}\, \|V_{1} - V_{0}\|_{\infty} \\&=\; \frac{\gamma^{n}}{1-\gamma}\, \|V_{1} - V_{0}\|_{\infty}.\end{aligned}
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 5.3.** Show the **a posteriori bound**: for $n \ge 1$,

$$
\|V_{n} - V^{*}\|_{\infty} \;\le\; \frac{\gamma}{1-\gamma}\, \|V_{n} - V_{n-1}\|_{\infty}.
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Telescope from $n$ as in Exercise 5.2, but bound $\|V_{k+1}- V_{k}\|_{\infty}$ in terms of $\|V_{n} - V_{n-1}\|_{\infty}$ instead.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*Step 1: bound each successive difference in terms of $\|V_{n} - V_{n-1}\|_{\infty}$.* Apply the contraction property of $\mathcal{B}$ once:

$$
\|V_{n+1}- V_{n}\|_{\infty} \;=\; \|\mathcal{B}V_{n} - \mathcal{B}V_{n-1}\|_{\infty} \;\le\; \gamma\, \|V_{n} - V_{n-1}\|_{\infty}.
$$

Apply it again, chaining with the previous bound:

$$
\|V_{n+2}- V_{n+1}\|_{\infty} \;\le\; \gamma\, \|V_{n+1}- V_{n}\|_{\infty} \;\le\; \gamma^{2}\, \|V_{n} - V_{n-1}\|_{\infty}.
$$

Continuing this pattern, for every $j \ge 0$:

$$
\|V_{n+j+1}- V_{n+j}\|_{\infty} \;\le\; \gamma^{j+1}\, \|V_{n} - V_{n-1}\|_{\infty}.
$$

*Step 2: telescope.* Since $V_{k} \to V^{*}$ (Exercise 3.3), we have the telescoping identity

$$
V^{*} - V_{n} \;=\; (V_{n+1}- V_{n}) + (V_{n+2}- V_{n+1}) + (V_{n+3}- V_{n+2}) + \cdots.
$$

Applying the triangle inequality and the bounds from Step 1:

$$
\begin{aligned}\|V^{*} - V_{n}\|_{\infty}&\le\; \|V_{n+1}- V_{n}\|_{\infty} \;+\; \|V_{n+2}- V_{n+1}\|_{\infty} \\&\qquad +\; \|V_{n+3}- V_{n+2}\|_{\infty} \;+\; \cdots \\&\le\; \gamma\, \|V_{n} - V_{n-1}\|_{\infty} \;+\; \gamma^{2}\, \|V_{n} - V_{n-1}\|_{\infty} \\&\qquad +\; \gamma^{3}\, \|V_{n} - V_{n-1}\|_{\infty} \;+\; \cdots \\&=\; \bigl(\gamma + \gamma^{2} + \gamma^{3} + \cdots\bigr)\, \|V_{n} - V_{n-1}\|_{\infty} \\&=\; \frac{\gamma}{1-\gamma}\, \|V_{n} - V_{n-1}\|_{\infty}.\end{aligned}
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 5.4.** Show that the a posteriori bound of Exercise 5.3 is always at least as tight as the a priori bound of Exercise 5.2: for all $n \ge 1$,

$$
\frac{\gamma}{1-\gamma}\, \|V_{n} - V_{n-1}\|_{\infty} \;\le\; \frac{\gamma^{n}}{1-\gamma}\, \|V_{1} - V_{0}\|_{\infty}.
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Bound $\|V_{n} - V_{n-1}\|_{\infty}$ by repeated application of the contraction.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Apply the contraction property of $\mathcal{B}$ to $V_{n} = \mathcal{B}V_{n-1}$ and $V_{n-1}= \mathcal{B}V_{n-2}$:

$$
\|V_{n} - V_{n-1}\|_{\infty} \;\le\; \gamma\, \|V_{n-1}- V_{n-2}\|_{\infty}.
$$

Continuing this $n-1$ times altogether, we eventually land on $\|V_{1} - V_{0}\|_{\infty}$:

$$
\|V_{n} - V_{n-1}\|_{\infty} \;\le\; \gamma^{n-1}\, \|V_{1} - V_{0}\|_{\infty}.
$$

Multiplying both sides by $\dfrac{\gamma}{1-\gamma}> 0$ preserves the inequality:

$$
\frac{\gamma}{1-\gamma}\, \|V_{n} - V_{n-1}\|_{\infty} \;\le\; \frac{\gamma^{n}}{1-\gamma}\, \|V_{1} - V_{0}\|_{\infty}.
$$

Both bounds from Exercise 5.3 and Exercise 5.2 upper-bound $\|V_{n} - V^{*}\|_{\infty}$, and the a posteriori one is smaller.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 5.5.** Assume $|R(s,a,s')| \le R_{\max}$ for all $s,a,s'$. Show that if we initialize with $V_{0} \equiv 0$, then

$$
\|V_{n} - V^{*}\|_{\infty} \;\le\; \frac{\gamma^{n}}{1-\gamma}\, R_{\max}.
$$

This bound depends only on $n$, $\gamma$, and $R_{\max}$, so it can be evaluated before running a single iteration.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

With $V_{0} \equiv 0$:

$$
V_{1}(s) \;=\; (\mathcal{B}V_{0})(s) \;=\; \max_{a \in {\mathcal{A}}}\sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\, R(s,a,s').
$$

Each term is a convex combination of rewards, all bounded in absolute value by $R_{\max}$, so $|V_{1}(s)| \le R_{\max}$ for every $s$, hence $\|V_{1} - V_{0}\|_{\infty} = \|V_{1}\|_{\infty} \le R_{\max}$. Substituting into the a priori bound of Exercise 5.2:

$$
\|V_{n} - V^{*}\|_{\infty} \;\le\; \frac{\gamma^{n}}{1-\gamma}\, \|V_{1} - V_{0}\|_{\infty} \;\le\; \frac{\gamma^{n}}{1-\gamma}\, R_{\max}.
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 5.6.** Show that the bound of Exercise 5.5 is **tight**: exhibit an MDP in which $\|V_{n} - V^{*}\|_{\infty} = \frac{\gamma^{n}}{1-\gamma}\, R_{\max}$ for every $n \ge 0$ (with $V_{0} \equiv 0$).
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Take ${\mathcal{S}} = \{s\}$, ${\mathcal{A}} = \{a\}$, $T(s \mid s, a) = 1$, and $R(s, a, s) = R_{\max}$. The Bellman optimality operator collapses to

$$
(\mathcal{B}V)(s) \;=\; R_{\max}+ \gamma\, V(s).
$$

Starting from $V_{0}(s) = 0$ and iterating,

$$
V_{n}(s) \;=\; R_{\max}\bigl(1 + \gamma + \gamma^{2} + \cdots + \gamma^{n-1}\bigr) \;=\; R_{\max}\cdot \frac{1 - \gamma^{n}}{1 - \gamma}.
$$

The fixed point $V^{*}(s)$ solves $V^{*}(s) = R_{\max}+ \gamma\, V^{*}(s)$, giving $V^{*}(s) = R_{\max}/(1-\gamma)$. Therefore

$$
\|V_{n} - V^{*}\|_{\infty} \;=\; V^{*}(s) - V_{n}(s) \;=\; \frac{R_{\max}}{1-\gamma}- \frac{R_{\max}(1 - \gamma^{n})}{1-\gamma}\;=\; \frac{\gamma^{n}}{1-\gamma}\, R_{\max},
$$

so the bound of Exercise 5.5 is attained with equality. No bound in terms of only $n$, $\gamma$, and $R_{\max}$ can be sharper.

:::

:::callout {title="Note" tone="blue"}

**Remark.** Combining Exercises 5.3, 5.2 and 5.5 gives a chain of progressively weaker but increasingly upfront-computable bounds:

:::

:::callout {title="Note" tone="blue"}

**Convergence Bounds**

$$
\begin{aligned}\|V_{n} - V^{*}\|_{\infty} \;&\le\; \underbrace{\tfrac{\gamma}{1-\gamma}\, \|V_n - V_{n-1}\|_\infty}_{\text{a~posteriori, tightest}}\;\le\; \underbrace{\tfrac{\gamma^n}{1-\gamma}\, \|V_1 - V_0\|_\infty}_{\text{a~priori}}\\ \;&\le\; \underbrace{\tfrac{\gamma^n}{1-\gamma}\, R_{\max}}_{\text{upfront, assumes } V_0 \equiv 0,\, |R| \le R_{\max}}.\end{aligned}
$$

:::
Each step weakens the bound by replacing realized information with something coarser: first the most recent step size $\|V_{n} - V_{n-1}\|_{\infty}$ with the worst-case geometric decay $\gamma^{n-1}\|V_{1} - V_{0}\|_{\infty}$ (contraction of $\mathcal{B}$ applied $n-1$ times), then the initial step size $\|V_{1} - V_{0}\|_{\infty}$ with the crude reward bound $R_{\max}$. In practice the leftmost bound is significantly tighter, since $\|V_{n} - V_{n-1}\|_{\infty}$ often decays strictly faster than $\gamma^{n-1}\|V_{1} - V_{0}\|_{\infty}$. It also yields a concrete stopping rule: to guarantee $\|V_{n} - V^{*}\|_{\infty} \le \varepsilon$, iterate until $\|V_{n} - V_{n-1}\|_{\infty} \le \frac{1-\gamma}{\gamma}\, \varepsilon$.
