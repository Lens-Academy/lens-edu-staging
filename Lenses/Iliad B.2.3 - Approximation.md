---
id: 'e5414721-aaff-46c4-ab31-9f0c2524f3b5'
title: "B.2.3 Approximation"
tldr: "Read two sources on approximation and answer two questions on why universal approximation does not explain deep learning's success and what depth separation results imply about real target functions."
summary_for_tutor: "Approximation section of Iliad worksheet B.2 Mysteries of Deep Learning: two readings (Approximation is expensive, but the lunch is cheap; a review of when deep but not shallow networks avoid the curse of dimensionality) and two discussion questions: why the Universal Approximation Theorem does not explain success, and what the curse of dimensionality and depth separation results imply about the structure of real target functions. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/mysteries-of-deep-learning/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Approximation

[Approximation is expensive, but the lunch is cheap](https://www.lesswrong.com/posts/gq9GR6duzcuxyxZtD/approximation-is-expensive-but-the-lunch-is-cheap)

::card[[../Lenses/hoogland-approximation-is-expensive-but-the-lunch-is-cheap|Approximation is expensive, but the lunch is cheap]]

[Why and When Can Deep – but Not Shallow – Networks Avoid the Curse of Dimensionality: a Review](https://arxiv.org/pdf/1611.00740)

::card[[../Lenses/poggio-why-and-when-can-deep-but-not-shallow-networks-avoid-the-curse-of-dimensionality-a-review|Why and When Can Deep but Not Shallow Networks Avoid the Curse of Dimensionality: a Review]]

*Discussion questions:*

:::callout {title="Exercise" tone="amber"}

The Universal Approximation Theorem says a one-hidden-layer network can approximate any continuous function to arbitrary accuracy. Why is this *not* an explanation for deep learning's success?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: because the number of neurons required is exponential, for generic smooth functions. The UAT is essentially a proof that *with exponential resources you can build a continuous lookup table.* This would require more parameters than are atoms in the universe just to e.g. approximate MNIST

::: %%

:::callout {title="Exercise" tone="amber"}

If approximating *arbitrary* smooth functions provably requires exponentially many parameters (the curse of dimensionality), then what must be true about the functions deep learning actually faces for it to work at all? What is a "depth separation" result and what does it suggest about the answer to this question?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: real target functions *provably* must have some non-generic structure beyond that of generic Lipschitz functions, if realistic-size deep neural networks are to be capable of representing them at all. Depth separation results are theoretical results showing that there exist target functions that require exponentially many more parameters for a shallow network to approximate compared to a deep network. They hint that the non-generic target structure neural networks are exploiting may be *compositional* structure, as deep but not shallow networks can exploit this structure. Bonus points for relating this to program structure discussed in the "program synthesis" post

::: %%
