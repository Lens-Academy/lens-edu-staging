---
id: '85999961-0e70-4f73-b9e9-dae10caacff9'
title: "C.3.2 Predicting the future: sufficient statistics and causal states"
tldr: "Exercises on sufficient statistics for prediction: partitions of histories by their future distributions, and why causal states are the minimal sufficient statistic."
summary_for_tutor: "This is the first part of 'Predicting the future' in Iliad worksheet C.3 Computational Mechanics. It contains Exercise 3.1 (From statistics to partitions, parts a-f) and Exercise 3.2 (Causal states are minimal sufficient statistics, parts a-e), with collapsed solutions. Concepts: histories, statistics and the partitions they induce, sufficiency, refinement and coarsening, the equivalence relation defining causal states, minimal sufficient statistic; keep the notation R, Pi, epsilon and ~. Parts marked Extension are optional. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Xavier Poncini (Simplex)
  - Adam Shai (Simplex)
  - Paul Riechers (Simplex)
source_url: https://iliad-intensive.org/interpretability/computational-mechanics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 3. Predicting the future

:::callout {title="Instructions" tone="blue"}

Give a clear justification for each answer. You may use results proved in the lecture unless an exercise asks you to establish them. Questions marked **Extension** are optional.

:::

%% iliad:solutionsonly:start %%

:::callout {title="Instructions" tone="blue"}

These notes reproduce each exercise before its solution. Equivalent arguments and notation should receive full credit when the mathematical reasoning is correct.

:::

%% iliad:solutionsonly:end %%

:::callout {title="Exercise" tone="amber"}
**Exercise 3.1 (From statistics to partitions).** Let $$u_{1},\ldots,u_{6}\in\mathcal{X}_{+}^{*}$$ be six possible histories. Suppose that they induce the following conditional distributions over the entire future:

$$
\begin{array}{c|cccccc}\text{history} & u_1 & u_2 & u_3 & u_4 & u_5 & u_6\\ \hline \text{future distribution} & P & P & P & Q & Q & S\end{array}
$$

where $$P$$, $$Q$$, and $$S$$ are pairwise distinct.

Three statistics $$R_{A}$$, $$R_{B}$$, and $$R_{C}$$ induce the partitions

$$
\begin{aligned}\Pi_{A}&=\bigl\{\{u_{1},u_{2}\},\{u_{3}\},\{u_{4}\},\{u_{5}\},\{u_{6}\}\bigr\},\\ \Pi_{B}&=\bigl\{\{u_{1},u_{2},u_{3}\},\{u_{4},u_{5}\},\{u_{6}\}\bigr\},\\ \Pi_{C}&=\bigl\{\{u_{1},u_{2},u_{3},u_{4}\},\{u_{5}\},\{u_{6}\}\bigr\}.\end{aligned}
$$

Recall that a statistic is sufficient for prediction when histories assigned the same value induce the same distribution over the future.

**(a)** What does it mean for two histories to belong to the same cell of the partition induced by a statistic? Illustrate your answer using $$u_{1}$$ and $$u_{2}$$ in $$\Pi_{A}$$.

**(b)** Determine which of $$R_{A}$$, $$R_{B}$$, and $$R_{C}$$ are sufficient. If a statistic is not sufficient, give two histories witnessing the failure.

**(c)** Which cells of $$\Pi_{A}$$ can be merged without losing sufficiency? Perform all such merges and identify the resulting partition.

**(d)** Explain why no two cells of $$\Pi_{B}$$ can be merged while preserving sufficiency. What does this show about $$R_{B}$$?

**(e)** Prove that every refinement of a sufficient partition is also sufficient. Is every coarsening of a sufficient partition necessarily sufficient? Use $$\Pi_{A}$$, $$\Pi_{B}$$, and $$\Pi_{C}$$ to illustrate your answer.

**(f)** **Extension.** Consider the partition

$$
\Pi_{D} =\bigl\{\{u_{1}\},\{u_{2},u_{3}\},\{u_{4},u_{5}\},\{u_{6}\}\bigr\}.
$$

Show that $$\Pi_{A}$$ and $$\Pi_{D}$$ are both sufficient but that neither refines the other. How can both nevertheless refine the same minimal sufficient partition?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Two histories belong to the same cell when they receive the same summary value. In particular, $$R_{A}(u_{1})=R_{A}(u_{2})$$.

**(b)** Both $$R_{A}$$ and $$R_{B}$$ are sufficient. Every cell of $$\Pi_{A}$$ and every cell of $$\Pi_{B}$$ contains histories carrying only one of the distributions $$P$$, $$Q$$, or $$S$$.

The statistic $$R_{C}$$ is not sufficient. Its first cell contains $$u_{1}$$ and $$u_{4}$$, for example, but $$u_{1}$$ induces $$P$$ while $$u_{4}$$ induces $$Q$$. Since $$P\neq Q$$, these histories cannot be assigned the same value by a sufficient statistic.

**(c)** The cell $$\{u_{1},u_{2}\}$$ can be merged with $$\{u_{3}\}$$ because all three histories induce $$P$$. Similarly, $$\{u_{4}\}$$ can be merged with $$\{u_{5}\}$$ because both histories induce $$Q$$. No cell can be merged with $$\{u_{6}\}$$, and no $$P$$-cell can be merged with a $$Q$$-cell. After all permissible merges, the resulting partition is

$$
\bigl\{\{u_{1},u_{2},u_{3}\},\{u_{4},u_{5}\},\{u_{6}\}\bigr\}=\Pi_{B}.
$$

**(d)** The three cells of $$\Pi_{B}$$ correspond respectively to the three distinct future distributions $$P$$, $$Q$$, and $$S$$. Merging any two cells would therefore place histories with different future distributions in the same cell and destroy sufficiency. Hence $$R_{B}$$ is minimal sufficient.

**(e)** Let $$\Pi'$$ refine a sufficient partition $$\Pi$$. Any two histories in the same cell of $$\Pi'$$ also belong to the same cell of $$\Pi$$. Since $$\Pi$$ is sufficient, those histories induce the same future distribution. Therefore $$\Pi'$$ is sufficient.

In the example, $$\Pi_{A}$$ refines $$\Pi_{B}$$, and both are sufficient. A coarsening need not remain sufficient: $$\Pi_{C}$$ is obtained from the sufficient partition $$\Pi_{A}$$ by merging its cells $$\{u_{1},u_{2}\}$$, $$\{u_{3}\}$$, and $$\{u_{4}\}$$. The resulting cell contains histories inducing both $$P$$ and $$Q$$, so $$\Pi_{C}$$ is not sufficient.

**(f)** Every cell of $$\Pi_{D}$$ lies within one predictive class, so $$\Pi_{D}$$ is sufficient. The same was established for $$\Pi_{A}$$.

The cell $$\{u_{1},u_{2}\}$$ of $$\Pi_{A}$$ is split between $$\{u_{1}\}$$ and $$\{u_{2},u_{3}\}$$ in $$\Pi_{D}$$, so $$\Pi_{A}$$ does not refine $$\Pi_{D}$$. Conversely, $$\{u_{2},u_{3}\}$$ in $$\Pi_{D}$$ is split between $$\{u_{1},u_{2}\}$$ and $$\{u_{3}\}$$ in $$\Pi_{A}$$, so $$\Pi_{D}$$ does not refine $$\Pi_{A}$$. Both partitions nevertheless refine $$\Pi_{B}$$, because every one of their cells is contained in one of the three predictive classes represented by $$P$$, $$Q$$, and $$S$$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.2 (Causal states are minimal sufficient statistics).** For $$x,x'\in\mathcal{X}_{+}^{*}$$, define the relation $$\sim$$ by

$$
\begin{aligned}x\sim x' \quad\Longleftrightarrow\quad&\Pr\!\left( X_{|x|+1:|x|+|y|}=y\mid X_{1:|x|}=x \right)\\&\qquad= \Pr\!\left( X_{|x'|+1:|x'|+|y|}=y\mid X_{1:|x'|}=x' \right)\end{aligned}
$$

for every $$y\in\mathcal{X}^{*}$$. Define the causal state of $$x$$ by

$$
\epsilon(x):=[x]_{\sim},
$$

and write $$\mathcal{S}:=\epsilon(\mathcal{X}_{+}^{*})$$ for the set of causal states.

**(a)** Prove that $$\sim$$ is an equivalence relation on $$\mathcal{X}_{+}^{*}$$ by establishing each of the following:
1. reflexivity: $$x\sim x$$ for every $$x\in\mathcal{X}_{+}^{*}$$;
2. symmetry: if $$x\sim x'$$, then $$x'\sim x$$;
3. transitivity: if $$x\sim x'$$ and $$x'\sim x''$$, then $$x\sim x''$$.

**(b)** Prove that $$\epsilon$$ is sufficient for prediction.

**(c)** Let $$R:\mathcal{X}_{+}^{*}\to\mathcal{R}$$ be any sufficient statistic. Prove that

$$
R(x)=R(x')\quad\Longrightarrow\quad \epsilon(x)=\epsilon(x').
$$

Deduce that every sufficient partition refines the causal-state partition.

**(d)** Using parts (b) and (c), conclude that $$\epsilon$$ is a minimal sufficient statistic.

**(e)** **Extension.** Let $$T$$ be another minimal sufficient statistic. Prove that $$T$$ and $$\epsilon$$ induce the same partition of $$\mathcal{X}_{+}^{*}$$. Deduce that there is a bijection

$$
\psi:\mathcal{S}\to\operatorname{im}(T)
$$

satisfying $$T=\psi\circ\epsilon$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)**
1. For every $$x\in\mathcal{X}_{+}^{*}$$ and every continuation $$y$$, the conditional probability after $$x$$ equals itself. Hence $$x\sim x$$, so $$\sim$$ is reflexive.
2. If $$x\sim x'$$, then the two continuation probabilities are equal for every $$y$$. Reversing the equality shows that $$x'\sim x$$, so $$\sim$$ is symmetric.
3. Suppose $$x\sim x'$$ and $$x'\sim x''$$. For every $$y$$, the continuation probability after $$x$$ equals that after $$x'$$, which equals that after $$x''$$. Thus $$x\sim x''$$, so $$\sim$$ is transitive.

Therefore $$\sim$$ is an equivalence relation.

**(b)** If $$\epsilon(x)=\epsilon(x')$$, then $$x$$ and $$x'$$ belong to the same equivalence class, so $$x\sim x'$$. By the definition of $$\sim$$, the two histories induce the same probability for every finite continuation $$y$$. This is precisely the definition of sufficiency for prediction, so $$\epsilon$$ is sufficient.

**(c)** Suppose $$R(x)=R(x')$$. Since $$R$$ is sufficient, $$x$$ and $$x'$$ induce the same probability for every finite continuation. Hence $$x\sim x'$$, and equivalent histories have the same equivalence class: $$\epsilon(x)=\epsilon(x')$$.

Thus any two histories in the same cell induced by $$R$$ also lie in the same causal state. Every cell induced by $$R$$ is therefore contained in a causal state, so the partition induced by $$R$$ refines the causal-state partition. Since $$R$$ was arbitrary, every sufficient partition has this property.

**(d)** Part (b) shows that $$\epsilon$$ is sufficient. Part (c) shows that its partition is refined by the partition of every sufficient statistic. Hence the causal-state partition is the coarsest sufficient partition, so $$\epsilon$$ is a minimal sufficient statistic.

**(e)** Since $$T$$ is sufficient, part (c), with $$R=T$$, shows that the partition induced by $$T$$ refines the causal-state partition. Since $$T$$ is minimal and $$\epsilon$$ is sufficient, the causal-state partition must also refine the partition induced by $$T$$. The two partitions are therefore equal.

Define $$\psi(\epsilon(x)):=T(x)$$. Equality of the two partitions shows that this definition is independent of the representative $$x$$ and that distinct causal states receive distinct $$T$$-values. It also reaches every value in $$\operatorname{im}(T)$$. Hence $$\psi$$ is a bijection.

:::
