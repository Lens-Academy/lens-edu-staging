---
id: '003274b8-a657-42c0-8d6c-4dc720dff750'
title: "B.2.2 Deep learning as program synthesis"
tldr: "Read a post that frames deep learning as program synthesis, with four discussion questions on Solomonoff induction, what makes the hypothesis non-trivial, and why functions and programs are distinguished."
summary_for_tutor: "Overview section of Iliad worksheet B.2 Mysteries of Deep Learning: the post Deep Learning as Program Synthesis, which argues deep learning does something analogous to Solomonoff induction and also discusses the empirical mysteries. Four discussion questions: what Solomonoff induction is, how the hypothesis differs from the trivial claim that networks learn programs, where the approximation/generalization/optimization mysteries appear in the post, and why functions and programs are distinguished. Keep the terms program, function, Solomonoff induction. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/mysteries-of-deep-learning/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Overview

[Deep Learning as Program Synthesis](https://www.lesswrong.com/posts/Dw8mskAvBX37MxvXo/deep-learning-as-program-synthesis-1)

::card[[../Lenses/furman-deep-learning-as-program-synthesis|Deep Learning as Program Synthesis]]

(Note that this post presents an opinionated hypothesis (deep learning is performing something analogous to Solomonoff induction) alongside relatively consensus discussion of empirical mysteries. The post is largely being shared for the latter, though students may find the hypothesis itself useful pedagogically.)

*Discussion questions:*

:::callout {title="Exercise" tone="amber"}

Intuitively, what is Solomonoff induction and why do we care about it?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: people should mention the universality hypothesis class, the simplicity prior, optimality results.

::: %%

:::callout {title="Exercise" tone="amber"}

One can trivially say that a neural network "learns programs" because a neural network runs on a computer. Then one could say that e.g. linear regression "learns programs" too. What distinguishes the author's hypothesis from this more trivial fact?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: this is answered in the post under the "Clarifying the hypothesis" expandable section. See in particular the FPGA analogy and the point about general-purpose search. It is also discussed further in the "representation problem" section where a possible mechanism is sketched

::: %%

:::callout {title="Exercise" tone="amber"}

Where in the post do the three theoretical mysteries from the opening lecture (approximation, generalization, optimization) appear? Why does the post put the section related to "optimization" in a separate place from the other two mysteries?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: they map to the "paradox of approximation" section, the "paradox of generalization" section, and the "search problem" section. Optimization shows up in the "search problem" section within "path forward" because it's the only one of the three mysteries which Solomonoff induction can't explain.

::: %%

:::callout {title="Exercise" tone="amber"}

The post insists on maintaining the distinction between "functions" and "programs" - why? Why would we care to distinguish two networks that implement the same function by different means?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: they may *train* differently; the gradients can be different even if the function implemented is the same. For instance, suppose network A is an LLM that has never learned about bioweapons, and network B is an LLM who learned about bioweapons but was trained to suppress this knowledge in the last layer. They may behave the same right now, but under fine-tuning one can easily recover dangerous capabilities in B but not A.

* One may be tempted to say that we should care because even if networks implement the same function in-distribution, they may behave differently out-of-distribution. But, while true and important, this is actually denying the premise of the question, because behaving differently out-of-distribution means the two functions really *are* different. The strong claim here is that you should care about implementation *even if no possible input/output test could distinguish between the two networks*.

::: %%
