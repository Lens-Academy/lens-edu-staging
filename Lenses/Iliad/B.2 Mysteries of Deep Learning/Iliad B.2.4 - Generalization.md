---
id: '6e57f531-0607-4d8e-97b4-a7a1decadefc'
title: "B.2.4 Generalization"
tldr: "Read two sources on generalization and answer three questions on what generalization means here, why Zhang et al. rule out capacity-based bounds, and how the two sources are compatible."
summary_for_tutor: "Generalization section of Iliad worksheet B.2 Mysteries of Deep Learning: readings The paper that killed deep learning theory and Deep Learning is Not So Mysterious or Different, with three discussion questions: what generalization means (in-distribution, versus OOD), why the experiments of Zhang et al. defeat capacity-based bounds such as VC dimension and Rademacher complexity, and how compatible the pessimistic and optimistic sources are. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/mysteries-of-deep-learning/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Generalization

[The paper that killed deep learning theory](https://www.lesswrong.com/posts/ZvQfcLbcNHYqmvWyo/the-paper-that-killed-deep-learning-theory)

::card[[../Lenses/lawrencec-the-paper-that-killed-deep-learning-theory|The paper that killed deep learning theory]]

[Deep Learning is Not So Mysterious or Different](https://arxiv.org/abs/2503.02113)

::card[[../Lenses/wilson-deep-learning-is-not-so-mysterious-or-different|On soft inductive biases]]

*Discussion questions:*

:::callout {title="Exercise" tone="amber"}

There are different notions of "generalization" that aren't equivalent. What precisely do these resources mean by the word "generalization"? How does it differ from out-of-distribution (OOD) generalization?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: The resources here deliberately refer to *in-distribution generalization*, that is the gap between test loss and train loss where the train loss is sampled from the same distribution the test loss is evaluated over. This excludes OOD generalization, which would require evaluating the test loss against a different input/label distribution than the training samples are sampled from. Historically, the word "generalization" within statistical learning theory has typically referred to in-distribution generalization, but in common ML usage the word increasingly refers to OOD generalization. It is therefore *very common* for students to conflate in-distribution and OOD generalization, but they are totally different notions within a statistical learning theory context, and OOD generalization is almost impossible to prove useful results about in generality (the test distribution can change to anything!) despite sounding more appealing. There is still no consensus explanation for in-distribution generalization, and OOD generalization is strictly harder to explain.

* "The framework imagined a data distribution $D$ over inputs $X$ and outputs $Y$ where the goal was to fit a hypothesis $h : X \to Y$ that minimized the expected test loss for a loss function $L : X \times Y \to R$ over $D$. A learning algorithm would receive $n$ samples from the data distribution, and would minimize the training loss averaged across the sample $L(h(x), y)$."

::: %%

:::callout {title="Exercise" tone="amber"}

Why are the experimental results of Zhang et al. fatal to capacity-based generalization bounds (VC dimension, Rademacher complexity, etc)? What does this imply for explanations about generalization and what they must depend on?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: the architecture and algorithm are *fixed* across the two runs, so any complexity measure that depends only on the hypothesis class and the (data-independent) algorithm must give the same number in both - yet one generalizes and one doesn't. Therefore generalization is not a property of the model; it's an emergent property of model × algorithm × *data structure*.

::: %%

:::callout {title="Exercise" tone="amber"}

The first post is rather pessimistic in tone, declaring deep learning theory (or at least the theory surrounding generalization) to have been "killed." Meanwhile "Deep Learning is Not So Mysterious or Different" seems to take precisely the opposite attitude, that such empirical results are not too surprising under preexisting theoretical frameworks. Despite the difference in tone, how compatible are these results on the object level? What common picture do they paint?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: They're fully compatible - Zhang et al. is a negative result and Wilson is a positive proposal in the space it leaves open. Both say generalization is not a uniform property of the model class: capacity measures like VC dimension or Rademacher complexity can't explain it, since the same network generalizes on real data and memorizes random labels. Zhang stops there (an experimental result ruling out capacity-based explanations); Wilson supplies a candidate replacement - soft inductive biases, a flexible hypothesis space with a data-dependent preference for simpler solutions - which is exactly the kind of non-uniform, data-dependent explanation Zhang leaves room for. The "killed vs not mysterious" clash is one of tone, not content.

::: %%
