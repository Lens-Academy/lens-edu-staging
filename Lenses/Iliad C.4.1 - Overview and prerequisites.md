---
id: 'c7468e83-3fbf-4fa9-a64c-fe027b3669a2'
title: "C.4.1 Overview and prerequisites"
tldr: "The prerequisites and learning outcomes for condensation, a suggested route through the exercises, and a reference for the information theory used."
summary_for_tutor: "This is the opening of Iliad worksheet C.4 Condensation: an embedded video (The Mathematics of Concepts: How AIs See The World), prerequisites, the 'What you'll learn' list, 'How to use this sheet' (core route: Sections 2.1-2.4 with starred Exercises 2.1, 2.2, 2.4, 2.5-2.10; optional Exercises 2.3, 2.11, 2.12 and 3.1) and Section 1.1, an information theory reference (entropy, conditional entropy, chain rule, conditional mutual information, KL divergence, base-two logarithms)."
authors:
  - Satya Benson
source_url: https://iliad-intensive.org/interpretability/condensation/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
[Video: The Mathematics of Concepts: How AIs See The World](https://www.youtube.com/watch?v=odsHleu80x8)

#### Text
content::
\## 1. Prerequisites

1. Probability on finite sets, conditional probability, and elementary proofs.
2. Conditional entropy and conditional independence; Section 1.1 collects what we use.

:::callout {title="What you'll learn" tone="neutral"}

**Condensation**

- Construct latent models and check the three conditions on them: the latent variable model condition, reconstruction, and the Markov condition.
- Explain why a single agent would want its latents to satisfy the last two.
- Prove correspondence between families of latents, first exactly and then with explicit error terms.

**A hierarchical clustering example**

- Compare how different latent models of the same law meet the conditions, and what the conditioned score charges each for a query.

**Condensation in context**

- Relate condensation to natural latents, sufficient statistics, common information, computational mechanics, and graphical models.
- Separate informational correspondence from learning, finding, and using a translation.
- Identify which additional claims would connect correspondence to AI safety.

:::

\### How to use this sheet

After the first lecture, read Sections 2.1 and 2.2 and work Exercises 2.1, 2.2 and 2.4. After the second lecture, read Sections 2.3 and 2.4 and work Exercises 2.5, 2.6, 2.7, 2.8, 2.9 and 2.10. These nine starred exercises, about 140 minutes in all, are the core route. Then read Sections 3 and 4, take the discussion prompts in Section 4.5 to your group, and finish with the quiz in Section 5. Exercises 2.3, 2.11, 2.12 and 3.1 are optional.

\### 1.1 Information theory reference

All random variables have finite ranges and all logarithms are base two. For a finite-valued variable $$U$$,

$$
H(U)=-\sum_{u} p(u)\log p(u),\qquad H(U\mid V)=\sum_{v} p(v)H(U\mid V=v),
$$

with $$0\log 0=0$$. Conditional entropy is nonnegative. It is zero precisely when $$U$$ is a function of $$V$$ almost surely: values on probability-zero events do not matter. The chain rule and conditioning inequality are

$$
H(U,V\mid W)=H(U\mid W)+H(V\mid U,W),\qquad H(U\mid V,W)\le H(U\mid W).
$$

Conditional mutual information is

$$
I(U;V\mid W)=H(U\mid W)-H(U\mid V,W)\ge0.
$$

It is symmetric in $$U,V$$ and is zero precisely when $$U,V$$ are conditionally independent given $$W$$. Omitting $$W$$ gives mutual information $$I(U;V)$$. Entropy of a tuple means joint entropy, not the sum of its marginal entropies. An empty tuple is constant and has zero entropy. For probability distributions $$p,q$$ on a finite set,

$$
D_{\mathrm{KL}}(p\Vert q)=\sum_{u} p(u)\log\frac{p(u)}{q(u)}\ge0.
$$

This last quantity appears only in the optional score discussion.
