---
id: 'b2c3a831-892c-46d8-87c3-fa8529e752f7'
title: "A.2.2 Pretraining"
tldr: "How pretraining can be used for safety: data filtering, gradient routing, alignment pretraining and the persona selection model."
summary_for_tutor: "Pretraining part of worksheet A.2. Two strategies: shape what knowledge the model gets, and what it does with it. Covers data filtering (CBRN, token-level filtering), gradient routing and SGTM with the absorption effect, alignment pretraining (misalignment scores falling from 45% to 9%), simulators and the persona selection model (PSM) as the prior over personas. Reading is one of three Anthropic posts."
authors:
  - Margot Stakenborg
  - Garrett Baker
  - Evžen Wybitul
source_url: https://iliad-intensive.org/alignment/alignment-in-practice/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Pretraining

What the model learns during pretraining is deep, broad, and hard to change afterward. Besides learning hard facts, it's also forming a proto-understanding of what AI is and how AI assistants behave. This opens **two strategies** for safety interventions in this phase: shaping what knowledge the model obtains, and shaping what the model does *with* the knowledge it obtains. Both are constrained by the same limitation: we're operating before seeing behavior, the feedback loop is slow, and we can't anticipate every failure mode.

**Opening.** The story of pre-training: the model is about to see the entire internet. It's forming a view of what the world is — including what AI is and how AI assistants behave. We can intervene in what it learns, which influences both its factual knowledge and its character. But we're operating before seeing the model's behavior, so every intervention is a bet.

**Presentation and discussion (15 min).** Pre-training is where the model's deep representations are built — both its knowledge and its proto-character. Whenever you reach a method that students proposed during the discussion, point to their sticky note on the board and make the connection explicit. Present the methods in narrative order: data filtering addresses the obvious problem; gradient routing / SGTM addresses filtering's failure mode; alignment pretraining shifts from knowledge to character; PSM explains why character-shaping works. Close by repeating the overarching story one more time, and naming what pre-training can't do: you're operating before seeing the model's behaviour, the feedback loop is slow, and you can't anticipate every failure mode. This motivates the next slot.

**Data filtering** is the most intuitive intervention: identify dangerous content and remove it before training. [Pretraining data filtering](https://alignment.anthropic.com/2025/pretraining-data-filtering/) from Anthropic demonstrates this for CBRN content, achieving a 33% relative reduction in harmful-capabilities performance (from 33.7% to 30.8%, where chance is 25%) while preserving standard benchmarks. [Token-level filtering](https://arxiv.org/abs/2601.21571) refines this by removing dangerous tokens rather than entire documents, which Pareto-dominates document filtering — same capability reduction, lower cost to benign performance.

**Gradient routing and SGTM** address data filtering's core weakness: what if your classifier misses something? Rather than trying to perfectly exclude dangerous data, [gradient routing](https://arxiv.org/abs/2410.04332) localizes dangerous knowledge to specific model parameters during training, so it can be removed afterward by ablating those parameters. [SGTM](https://alignment.anthropic.com/2025/selective-gradient-masking/) refines this for LLMs. The key finding is an *absorption effect*: once dangerous knowledge begins localizing based on labeled examples, even unlabeled dangerous content naturally gravitates toward the same "forget" parameters. This provides robustness to label noise that data filtering cannot achieve. On a 254M model, "unlearning" using SGTM is in some ways similarly robust to the gold standard of data filtering.

**Alignment pretraining** targets not the model's knowledge but its *character*. [Tice et al. (2026)](https://arxiv.org/abs/2601.10160) show that upsampling documents about aligned AI behavior during pretraining reduces misalignment scores from 45% to 9%, while upsampling misalignment discourse increases misaligned behavior — "self-fulfilling alignment." These effects persist through post-training.

Why does this work? The [persona selection model (PSM)](https://alignment.anthropic.com/2026/psm/) provides the conceptual frame. Building on the [simulators hypothesis](https://www.lesswrong.com/posts/vJFdjigzmcXMhNTsx/simulators) — that an LLM is a *simulator* capable of producing diverse *simulacra* (characters, agents) — PSM holds that pretraining builds a repertoire of personas, and post-training helps shape the "Assistant." Alignment pretraining works because it shapes the **prior over personas**: saturating the training data with positive AI archetypes biases the model toward an aligned Assistant. PSM recommends treating this deliberately — curating AI discourse in pre-training data as a first-class alignment intervention.

**Reading (30 min):** Read [Pretraining data filtering](https://alignment.anthropic.com/2025/pretraining-data-filtering/), or [SGTM](https://alignment.anthropic.com/2025/selective-gradient-masking/), or [persona selection model (PSM)](https://alignment.anthropic.com/2026/psm/).

:::require_x_optional_lenses{x=1}
::card[[../Lenses/anthropic-enhancing-model-safety-through-pretraining-data-filtering|Pretraining data filtering]]

::card[[../Lenses/anthropic-beyond-data-filtering-knowledge-localization-for-capability-removal-in-llms|SGTM]]

::card[[../Lenses/marks-the-persona-selection-model-why-ai-assistants-might-behave-like-humans|Persona selection model]]
:::
