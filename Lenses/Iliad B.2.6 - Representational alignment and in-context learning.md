---
id: '5ceeaca7-556a-40e3-9e58-83999d80d2f5'
title: "B.2.6 Representational alignment and in-context learning"
tldr: "Read the Platonic Representation Hypothesis paper and the induction heads paper, with one discussion question on each: what is new in the hypothesis, and how induction heads relate to in-context learning."
summary_for_tutor: "Representational alignment and In-context learning sections of Iliad worksheet B.2 Mysteries of Deep Learning: readings The Platonic Representation Hypothesis and In-context Learning and Induction Heads. Discussion questions: what the new hypothesis is versus established observations, what evidence is cited and how it differs from mere convergence; and what an induction head is and why its formation coinciding with in-context learning is evidence of a mechanistic link. Includes a footnote on the novelty of the hypothesis. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/mysteries-of-deep-learning/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Representational alignment

[The Platonic Representation Hypothesis](https://arxiv.org/abs/2405.07987)

::card[[../Lenses/huh-the-platonic-representation-hypothesis|The Platonic Representation Hypothesis]]

*Discussion questions:*

:::callout {title="Exercise" tone="amber"}

What is the new[^prh-novelty] hypothesis that paper promotes, versus what are the observations already established by prior literature? What evidence do they cite for their hypothesis? What distinguishes their hypothesis from merely "models converge to shared representations"?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

Answer: The *observation* that independently trained models learn similar representations is old and well-established - it predates the paper by years (model stitching, CKA/RSA similarity, "convergent learning," universal Gabor filters, vision models predicting visual cortex). What's *new* is not that models resemble each other but a claim about where they're heading: representations are converging toward a single endpoint, and that endpoint is a representation of the underlying reality - the statistical structure of the world that generated the data (their "platonic" representation, idealized as a kernel reflecting how real-world events co-occur). The evidence they cite for *this* is (i) convergence that grows with model scale and competence, (ii) convergence that holds *across modalities* - vision and language models becoming more alignable as they get more capable - and (iii) a theoretical argument that multitask pressure, capacity, and simplicity bias funnel diverse models toward the same solution. The distinction from "models converge to shared representations" is the addition of a *limit point* and its *identity*: plain convergence is just pairwise similarity, and is equally consistent with models merely sharing architectures, objectives, or training data; PRH claims they share a *destination*, and that the destination is reality's structure - which is what licenses its signature prediction that convergence should cross modalities. That cross-modal and scaling evidence is exactly the novel, load-bearing, and most-contested part; the bare convergence phenomenon is the consensus part.

* Note that papers like "[Revisiting the PRH: An Aristotelian View](https://arxiv.org/abs/2602.14486)" have criticized some of the evidence in the PRH paper and propose a slightly weaker hypothesis. However their critiques only apply to evidence based on CKA, a particular technique, and other evidence appears to survive

::: %%

\### In-context learning

[In-context Learning and Induction Heads](https://transformer-circuits.pub/2022/in-context-learning-and-induction-heads/index.html)

::card[[../Lenses/olsson-in-context-learning-and-induction-heads|In-context Learning and Induction Heads]]

*Discussion questions:*

:::callout {title="Exercise" tone="amber"}

What is an induction head, and what relationship does the paper draw between induction-head formation and in-context learning over training? Why treat the simultaneity as evidence of a mechanistic link rather than coincidence?

:::

%% :::callout {title="Solution" tone="neutral" collapse="closed"}

An induction head is a circuit implementing the rule \[A\]\[B\] … \[A\] → \[B\] - find the previous occurrence of the current token, see what followed it, predict that again ("complete the pattern" by copying). Mechanically it's two heads composed across layers (a previous-token head feeding the induction head), so it cannot exist in a 1-layer model. In-context learning is operationalized as the drop in loss from early to late token positions (the model predicting better the more context it has seen). Early in training there is a phase change, visible as a bump in the training loss, during which induction heads form and the bulk of in-context-learning ability appears simultaneously - for models of every size with more than one layer. Simultaneity alone would only be suggestive; the case is carried by co-perturbation (when they modify the architecture to move when induction heads can form, the in-context-learning jump moves to match) and by direct ablation (knocking out induction heads in small models sharply reduces in-context learning)

::: %%

[^prh-novelty]: One could argue that this hypothesis isn't novel either, see e.g. the natural abstraction hypothesis which significantly predates this, but this paper was the first major academic paper to promote the hypothesis.
