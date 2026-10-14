---
id: 'dec610fb-1982-4a4a-949c-3d638cbca30c'
title: "D.1.1.2 Completeness, transitivity and ordinal utility"
tldr: "Defines completeness and transitivity, proves that complete and transitive preferences have an ordinal utility, and looks at what happens when either property fails."
summary_for_tutor: "This is Section 4 of worksheet D.1.1 (preferences to rewards). It gives Definitions 4.1 (completeness) and 4.2 (transitivity), weak orders, Proposition 4.3 (ordinal representation on H*) with a proof, why ordinal utility is unique only up to increasing transformations, failures of completeness or transitivity including the money pump, and an optional Helmholtz-Hodge view of cycles. No exercises."
authors:
  - Fernando E. Rosas
source_url: https://iliad-intensive.org/agency/preferences-to-rewards/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 4. Completeness, transitivity, and ordinal utility

Two structural conditions are especially important.

:::callout {title="Definition" tone="blue"}

**Definition 4.1 (Completeness).** A preference relation $$\succcurlyeq$$ on $${\mathcal{H}}^{*}$$ is *complete* if for every pair $$h,h'\in {\mathcal{H}}^{*}$$,

$$
h\succcurlyeq h' \quad \text{or}\quad h'\succcurlyeq h \quad \text{(or both)}.
$$

:::

:::callout {title="Definition" tone="blue"}

**Definition 4.2 (Transitivity).** A preference relation $$\succcurlyeq$$ on $${\mathcal{H}}^{*}$$ is *transitive* if for every $$h,h',h''\in {\mathcal{H}}^{*}$$,

$$
h\succcurlyeq h' \quad \text{and}\quad h'\succcurlyeq h'' \quad \Longrightarrow \quad h\succcurlyeq h''.
$$

:::

Completeness says that the agent can compare any two trajectories. This is a claim about *comparability*, not about certainty: it says that the preference relation returns a verdict on every pair, not that the agent knows everything about the consequences of those trajectories. Transitivity says that these verdicts fit together consistently across chains of comparison. For example, if $$h_{1}\succcurlyeq h_{2}$$ and $$h_{2}\succcurlyeq h_{3}$$, then transitivity requires $$h_{1}\succcurlyeq h_{3}$$ as well.

A preference relation satisfying both conditions is often called a *weak order* in economics and decision theory (Fishburn 1970; Kreps 1988; Mas-Colell et al. 1995). On a countable domain such as $${\mathcal{H}}^{*}$$, weak orders admit an ordinal utility representation. More general representation theorems on richer domains go back to the classic work of Debreu 1954.

:::callout {title="Theorem" tone="green"}

**Proposition 4.3 (Ordinal representation on the trajectory space).** A preference relation $$\succcurlyeq$$ on $${\mathcal{H}}^{*}$$ is complete and transitive if and only if there exists a function $$u\colon {\mathcal{H}}^{*} \to {\mathbb{R}}$$ such that

$$
h \succcurlyeq h' \iff u(h)\geq u(h') \qquad \text{for all }h,h'\in{\mathcal{H}}^{*}.
$$

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

If such a function $$u$$ exists, then completeness and transitivity are inherited from the total order on $${\mathbb{R}}$$. Conversely, if $$\succcurlyeq$$ is complete and transitive, then trajectories can be grouped into indifference classes, where each class contains all trajectories tied with one another. The quotient $${\mathcal{H}}^{*}/{\sim}$$ of these classes is a countable total order. Any countable total order can be embedded in $${\mathbb{R}}$$, so we may assign real numbers to the indifference classes in a way that preserves their order. Composing that assignment with the quotient map gives the desired utility function on trajectories.

:::

This utility is *ordinal*: only the ranking matters. Any strictly increasing transformation of $$u$$ represents the same preference relation. So ordinal utility lets us encode the order of deterministic trajectories, but it does not yet tell us how to compare risky mixtures of them. The numbers themselves have no independent meaning beyond the order they induce. If $$u$$ represents a preference relation, then so does $$2u+17$$, or $$\exp(u)$$, provided the transformation remains strictly increasing. This is why ordinal utility is best thought of as a numerical *labeling of ranks*, not yet as a measure of how much one trajectory is preferred to another (Fishburn 1970).

It is also useful to understand what happens when either condition fails.

\### What if completeness or transitivity fail

**If completeness fails.**  Then some pairs of trajectories are incomparable. This may be a feature rather than a bug: the agent may genuinely refuse to rank certain alternatives because its values are plural, under-specified, or context-sensitive. But once incomparability is allowed, no single real-valued utility function can exactly represent the relation in the sense of Proposition 4.3, because any two real numbers are themselves comparable. One must then move to a different formalism, such as partial orders, sets of utility functions, or multi-criteria representations (Aumann 1962).

**If transitivity fails.**  Then local pairwise judgments need not assemble into a global ranking. In the simplest case one obtains a cycle

$$
h_{1} \succ h_{2},\qquad h_{2} \succ h_{3},\qquad h_{3} \succ h_{1}.
$$

No scalar utility can represent such a cycle, since it would require

$$
u(h_{1})>u(h_{2})>u(h_{3})>u(h_{1}),
$$

which is impossible. The logical problem is already serious: there is no single global ranking of the options. Under the additional behavioral assumption that the agent is willing to pay a small fee to move from any option to a strictly preferred one, this logical failure becomes operational through the *money pump* problem. Suppose an agent currently has $$h_{1}$$ and is willing to pay a small fee $$\varepsilon>0$$ each time it moves to a strictly preferred trajectory. The cycle above licenses the sequence

$$
h_{1} \to h_{2} \to h_{3} \to h_{1},
$$

with the agent paying $$\varepsilon$$ at each step. At the end it is back where it started, but poorer by $$3\varepsilon$$. Repeating the cycle pumps away arbitrarily much money (Gustafsson 2010).

There is also an interesting geometric view on transitivity. This paragraph is not needed for the rest of the note, so readers meeting these ideas for the first time can safely treat it as an optional aside. Fix a finite menu $$V=\{h_{1},\dots,h_{m}\}\subset {\mathcal{H}}^{*}$$ and draw the complete graph whose vertices are the trajectories in $$V$$. Encode pairwise comparisons by an antisymmetric edge flow $$X$$:

$$
X_{ij}= -X_{ji},
$$

where $$X_{ij}>0$$ means that $$h_{i}$$ is preferred to $$h_{j}$$, while $$X_{ij}<0$$ means the reverse. If preferences come from a utility function $$u$$, then each edge weight is just a utility difference,

$$
X_{ij}=u(h_{i})-u(h_{j}),
$$

so $$X$$ is a discrete gradient field. In the language of the discrete Helmholtz–Hodge decomposition, any edge flow can be split into a gradient part, which comes from a potential, and a cyclic part, which records genuine loops. On the complete comparison graph there is no extra harmonic remainder, so inconsistency is entirely captured by the cyclic component (Jiang et al. 2011). A three-cycle corresponds exactly to a nonzero discrete curl:

$$
X_{ij}+X_{jk}+X_{ki}\neq 0.
$$

Thus transitive preferences are precisely the *potential* part of the decomposition, with the potential given by the utility, while intransitive cycles show up as the rotational or cyclic part. If this language feels abstract, the key takeaway is simple: utility means all local comparisons come from one global ranking, whereas cycles are the leftover pattern that cannot be explained by any single scalar potential.
