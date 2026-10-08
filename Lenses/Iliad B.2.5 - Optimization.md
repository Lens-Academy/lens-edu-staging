---
id: 'b8e3780b-6bcb-4ff6-80ff-be3ddd1d76e8'
title: "B.2.5 Optimization"
tldr: "Read the section on hardness of learning from Understanding Machine Learning and answer two questions on cryptographic hardness, SGD versus Bayesian learning, and why worst-case targets matter."
summary_for_tutor: "Optimization section of Iliad worksheet B.2 Mysteries of Deep Learning: reading Section 8.4 (Hardness of learning) of Understanding Machine Learning: From Theory to Algorithms, with two discussion questions: what cryptographic hardness (one-way functions) implies for SGD versus Bayesian learning and how optimization separates from approximation and generalization, and why worst-case targets matter even though networks train well in practice. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/mysteries-of-deep-learning/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Optimization

[Understanding Machine Learning: From Theory to Algorithms](https://www.cambridge.org/core/books/understanding-machine-learning/3059695661405D25673058E43C8BE2A6), Section 8.4 (Hardness of learning)

*Discussion questions:*

:::callout {title="Exercise" tone="amber"}

These cryptographic hardness arguments apply to neural networks, since neural networks can implement one-way functions. What does this imply about how long SGD will take to learn such functions? By contrast, how will Bayesian learning behave in such a scenario (and why are hardness arguments vacuous for Bayes)? What does this imply about how approximation and generalization come apart from optimization?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: the hardness argument means that (under cryptographic assumptions) SGD can't learn hard targets in polynomial time. Bayes, meanwhile, will rapidly concentrate posterior mass on the target because it's realizable and gets zero train loss. Bayes doesn't run in polynomial time, so hardness arguments are vacuously true here and don't force poor performance. In this way, Bayesian learning gives an algorithm with good approximation and generalization, but terrible optimization efficiency, because it can't run in polynomial time.

::: %%

:::callout {title="Exercise" tone="amber"}

Despite the fact that neural networks can realize worst-case targets, neural networks train well in practice. Why care about these pathological examples, then? What makes the takeaway different from the obvious "algorithms can have typical-case performance which is much better than their worst-case performance"?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: one can make a few points here.

* As discussed in the previous question, this phenomenon separates approximation and generalization from optimization difficulty. This is especially important because while e.g. Solomonoff induction gives us a good model of how one can simultaneously achieve good approximation and generalization, it gives no answer as to the optimization problem. It separates the questions we have an in-principle explanation of from the one we don't
* It constrains explanation for the optimization problem. Any explanation for why training succeeds (in poly time) which works uniformly across all targets must be wrong. Instead, you *must* engage with the target structure, in such a way that your explanation applies for typical targets but does not apply for worst-case targets. (Emphasize: there's a pattern here, the approximation and generalization problems *also* force us to provide explanations which depend on non-generic target structure.)
  * As a kicker, it's not obvious at all how such worst-case functions can easily be separated from the typical ones. They're realizable, they lie inside your hypothesis class. They show up *automatically* and *inevitably* in any model which can perform sufficiently general computation (because then you can implement one-way functions.) In fact, you can't even distinguish worst-case functions from typical ones *by any black box (purely input/output) procedure whatsoever*, since that would break the cryptographic hardness assumption as well. So the explanation for the typical/worst-case gap must really be sophisticated.
  * Re: the program synthesis hypothesis, note also that the explanation here can't be "optimization succeeds because real-world targets have compositional/program structure and generic functions don't," because the worst-case targets obviously have program structure, and they're rather short and simple programs at that. One must distinguish between different types of programs.

::: %%
