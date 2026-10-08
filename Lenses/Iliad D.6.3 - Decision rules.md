---
id: '2c2367c8-b4ad-4c05-af0b-6ca2954b9106'
title: "D.6.3 Decision rules"
tldr: "Defines decision rules over the options at a state, expected-utility-determined rules (optimal, Boltzmann, satisficing) and score rules."
summary_for_tutor: "Part of section 2 of Iliad worksheet D.6 Instrumental Convergence on suitable decision rules. Contains Definition 2.4 (decision rule p(X|s,r), quality f^T r), Definition 2.5 (EU-determined rule via multisets of qualities), Definition 2.6 (FracOpt, Boltzmann Bz_T, satisficing Sat_t), Exercise 2.2 with collapsed solution (these are EU-determined) and Definition 2.7 (score rule with nondecreasing nu; Bz_T and Sat_t are score rules, FracOpt is not). Keep the notation p, nu, EU_r. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - "Leon Lang (ILIAD), based on work by Alex Turner et al."
source_url: https://iliad-intensive.org/agency/power-seeking/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Decision rules

A decision rule describes the selection of an option from $${\mathcal{F}}(s)$$ given a reward function, with potential randomness in the selection procedure.

:::callout {title="Definition" tone="blue"}

**Definition 2.4 (Decision rule).** A **decision rule** assigns, to each state $$s$$ and reward $$r \in {\mathbb{R}}^{d}$$, a probability distribution $$p(\cdot \mid s, r)$$ over the accessible options $${\mathcal{F}}(s)$$: for each subset $$X \subseteq {\mathcal{F}}(s)$$,

$$
p(X \mid s, r) \in [0,1]
$$

is the probability that the agent's selected option lies in $$X$$ (options outside $${\mathcal{F}}(s)$$ receive zero probability by construction). The **quality** of an option $$f \in {\mathcal{F}}(s)$$ under $$r$$ is its value $$f^{\top} r$$ (Exercise 2.1).

:::

:::callout {title="Definition" tone="blue"}

**Definition 2.5 (Expected-utility-determined rule).** For a finite set $$Y \subseteq {\mathbb{R}}^{d}$$ of options, write

$$
\mathrm{EU}_{r}(Y) \;:=\; \{\!\{\,\, f^\top r : f \in Y \,\,\}\!\}
$$

for the **multiset** of qualities of $$Y$$ under $$r$$ — the values $$f^{\top} r$$ for $$f \in Y$$, counted with multiplicity but carrying *no order*. A decision rule is **expected-utility-determined** (EU-determined) if there is a single function $$g$$, *defined on multisets*, such that for every state $$s$$, reward $$r \in {\mathbb{R}}^{d}$$, and $$X \subseteq {\mathcal{F}}(s)$$,

$$
p(X \mid s, r) \;=\; g\bigl(\mathrm{EU}_{r}(X),\, \mathrm{EU}_{r}({\mathcal{F}}(s))\bigr).
$$

Because $$g$$ takes *multisets* as inputs, it cannot depend on any ordering of the options — only on which qualities occur and with what multiplicity. Thus $$p$$ sees the options only through the two multisets of qualities, those of the chosen set $$X$$ and of the full menu $${\mathcal{F}}(s)$$. These are the rules we call **suitable** in point (2) of the introduction.

:::

The basic example is exact optimization, with ties broken uniformly; but noisy and threshold-based rules qualify just as well. We record three options here, but there are many others.

:::callout {title="Definition" tone="blue"}

**Definition 2.6 (Three EU-determined decision rules).** Fix a state $$s$$ and a reward $$r$$, and write $$M(r) := \max_{f \in {\mathcal{F}}(s)}f^{\top} r$$ for the maximal quality. For $$X \subseteq {\mathcal{F}}(s)$$:

- **Uniform tie-breaking** (optimal choice with ties split evenly): Choose uniformly among all maximizers,

$$
\mathrm{FracOpt}(X \mid s, r) \;:=\; \frac{\bigl|\{\, f \in X : f^{\top} r = M(r) \,\}\bigr|}{\bigl|\{\, f \in {\mathcal{F}}(s) : f^{\top} r = M(r) \,\}\bigr|}.
$$
- **Boltzmann rational** (softmax) at temperature $$T > 0$$: weight options by the exponential of their quality,

$$
\mathrm{Bz}_{T}(X \mid s, r) \;:=\; \frac{\sum_{f \in X}e^{\,f^\top r / T}}{\sum_{f \in {\mathcal{F}}(s)}e^{\,f^\top r / T}}.
$$
- **Satisficing** at threshold $$t \in {\mathbb{R}}$$: pick uniformly among the options that are "good enough",

$$
\mathrm{Sat}_{t}(X \mid s, r) \;:=\; \frac{\bigl|X \cap {\mathcal{F}}_{\ge t}(s)\bigr|}{\bigl|{\mathcal{F}}_{\ge t}(s)\bigr|}, \qquad {\mathcal{F}}_{\ge t}(s) := \{\, f \in {\mathcal{F}}(s) : f^{\top} r \ge t \,\}.
$$

This is only defined if $${\mathcal{F}}_{\ge t}(s) \neq \emptyset$$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.2.** Verify that $$\mathrm{FracOpt}$$, $$\mathrm{Bz}_{T}$$, and $$\mathrm{Sat}_{t}$$ are each EU-determined.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Each rule is, by inspection, a function of the two quality-multisets $$\mathrm{EU}_{r}(X)$$ and $$\mathrm{EU}_{r}({\mathcal{F}}(s))$$ alone — that is, of the form $$g\bigl(\mathrm{EU}_{r}(X), \mathrm{EU}_{r}({\mathcal{F}}(s))\bigr)$$:

- $$\mathrm{FracOpt}$$: with $$M(r) = \max \mathrm{EU}_{r}({\mathcal{F}}(s))$$, it is the multiplicity of $$M(r)$$ in $$\mathrm{EU}_{r}(X)$$ divided by its multiplicity in $$\mathrm{EU}_{r}({\mathcal{F}}(s))$$.
- $$\mathrm{Bz}_{T}$$: it is $$\sum_{u \in \mathrm{EU}_r(X)}e^{u/T}$$ divided by $$\sum_{u \in \mathrm{EU}_r({\mathcal{F}}(s))}e^{u/T}$$ (note these sums take into account the multiplicity of $$u$$ in the respective multisets).
- $$\mathrm{Sat}_{t}$$: it is the number of entries $$\ge t$$ in $$\mathrm{EU}_{r}(X)$$ divided by the number of entries $$\ge t$$ in $$\mathrm{EU}_{r}({\mathcal{F}}(s))$$.

None refers to an option $$f$$ except through its quality $$f^{\top} r$$, so each is EU-determined.

:::

A further family will carry the main result: rules that weight each option by a fixed transform of its quality and normalize.

:::callout {title="Definition" tone="blue"}

**Definition 2.7 (Score rule).** A decision rule $$p$$ is a **score rule** if there is a nondecreasing $$\nu : {\mathbb{R}} \to [0,\infty)$$ with

$$
p(\{f\}\mid s, r) \;=\; \frac{\nu(f^{\top} r)}{\sum_{h\in{\mathcal{F}}(s)}\nu(h^{\top} r)}\qquad (f \in {\mathcal{F}}(s)),
$$

so that $$p(X\mid s,r) = \sum_{f\in X}\nu(f^{\top} r)\big/\sum_{h\in{\mathcal{F}}(s)}\nu(h^{\top} r)$$ (defined when the normalizer is positive). Both $$\mathrm{Bz}_{T}$$ (with $$\nu(q) = e^{q/T}$$) and $$\mathrm{Sat}_{t}$$ (with $$\nu(q) = \mathbf{1}[q\ge t]$$) are score rules. ($$\mathrm{FracOpt}$$ is *not* a score rule: its cutoff is not fixed.)

:::
