---
id: 'dcaaf628-2048-46ec-9b7e-549324d3f54c'
title: "B.2.1 Overview, prerequisites and lecture"
tldr: "Lists the prerequisites and learning outcomes, the fast-track route, and two discussion questions on why understanding deep learning matters for AI safety and how the three classical mysteries differ."
summary_for_tutor: "Opening part of Iliad worksheet B.2 Mysteries of Deep Learning: prerequisites (Solomonoff induction, basic deep learning, mechanistic interpretability as motivation), learning outcomes, fast-track advice, and the Lecture section with the slides link and two discussion questions (why scientific understanding of deep learning matters for safety; what distinguishes approximation, generalization and optimization and which depend on training). Authors' written answers are hidden comments, not student-visible. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/mysteries-of-deep-learning/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Prerequisites

* Basic awareness of Solomonoff induction and the high-level ideas behind it
* Basic understanding of deep learning, sufficient to read non-specialist ML papers
* Knowledge of mechanistic interpretability (Day C.2) is very helpful motivation but not logically necessary

:::callout {title="What you'll learn" tone="neutral"}

* Students can explain and distinguish the three classical mysteries of why deep learning performs well: approximation, generalization, and optimization.
* Students understand why each of the three classical mysteries implicitly requires leveraging structure in reality: learning is not tractable for arbitrary tasks, so deep learning must be using non-generic properties of real-world tasks to succeed.
* Students are aware of the key empirical mysteries of deep learning: data-dependent generalization despite overparameterization, effectiveness of SGD on non-convex landscapes, representational alignment across architectures, and in-context learning
* Students have encountered at least one candidate explanation for each mystery and can articulate what it does and doesn't explain
* Students understand the "program synthesis" hypothesis as one proposed framework connecting deep learning to Solomonoff induction, and can evaluate its strengths and limitations
* Students can articulate why solving these mysteries matters for AI safety: understanding the basic mechanisms by which deep learning works is necessary for any *systematic* (generalizing OOD) alignment interventions or measurements to even be possible

:::

\## Fast-track

The content is already attempting to compress a somewhat disjointed research field, so it may be difficult to compress further. At a minimum, read the lecture slides for the overall framing, then read "Deep Learning as Program Synthesis" (skimming any sections one is already familiar with, and optionally deferring the "path forward" section). This gives a high level overview of various empirical mysteries. Then skim as many papers on the list as you have time/interest (possibly none).

\## Reading guide

%% Every discussion question below carries the author's written-out answer.
    They were provisional TA-facing notes — shorthand in places, one of them
    still TODO — never meant to be read by students, so each is commented out
    here rather than published (author's call, 2026-07-29). Un-comment a block
    to bring it back; nothing inside one has been edited. %%

\### Lecture

[Slides.](https://drive.google.com/drive/folders/1SV-VYOSTzEGcRxw5GuDBCLbwQWj3k0Ym)

*Discussion questions:*

:::callout {title="Exercise" tone="amber"}

From an AI safety perspective, why is it worth trying to scientifically figure out how deep learning works? Why would we need scientific understanding for safety if such understanding seems to have been unnecessary for capabilities?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: many answers are acceptable here. A few points one might mention:

* It seems increasingly likely that AGI/ASI will be based on deep learning
* Safety is intrinsically hard to hill-climb in the way that capabilities benchmarks are. Failures can be rare and have heavy-tail costs
* Historical comparisons (steam engine safety, aviation safety, etc)

::: %%

:::callout {title="Exercise" tone="amber"}

What distinguishes the three classical mysteries discussed in the talk from each other? Which ones depend on the training procedure?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: TODO

::: %%
