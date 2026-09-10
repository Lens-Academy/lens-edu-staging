---
id: 'efaa8c43-2876-4b24-b60f-c0d31577f217'
title: "Exploration Hacking: Can LLMs Learn to Resist RL Training?"
tldr: "A student set on failing a placement test does not answer at random. He gets it wrong the same way every time, so the grader learns nothing about what he actually knows. This paper trains models to do that to reinforcement learning: never explore the good move, so RL has nothing to reinforce. It works, sometimes. So far it is also easy to catch."
summary_for_tutor: "This page renders the paper inline as a bare Paper-type page with no framing prose, no exercises and no interactive elements, so everything here except the Before you read lead-in and the Works cited callout is the authors' own text. The lead-in is navigational: it points back to Misalignment and strategic underperformance for the definition of exploration hacking, forward to Exploration Hacking (guided) which reworks the same paper with written checkpoints, and it gives the paper's own section map plus a measured breakdown of main text versus appendices so the learner knows what to read closely. The paper's argument in three parts: locked model organisms (fine-tuned to follow an underperformance strategy) can resist GRPO-based capability elicitation on WMDP-Bio, VCT, KernelBench and BigCodeBench while keeping performance elsewhere, in both unconditional and conditional settings; countermeasures work, since chain-of-thought monitors, action-only monitors and weight noising all detect these organisms and SFT on benign traces quickly recovers the suppressed capability; and frontier models audited for propensity can reason explicitly about suppressing exploration when given enough information about their training context, at higher rates when that information is picked up indirectly from the environment than when it is handed to them in the system prompt. The paper's own summary of the gap is that the bottleneck is strategic action propensity, not strategic reasoning capability. If a learner asks whether this shows models are exploration hacking today, hold the distinction: the organisms were deliberately trained to do it, and the frontier audit found capability without spontaneous propensity."
reading_minutes: 90
tutor_minutes: 0
tags: []
---
#### Text
content::
\#### Before you read

[[../Lenses/XLab Control - misalignment-and-strategic-underperformance|Misalignment and strategic underperformance]] defined exploration hacking as a strategy: a model that already knows a high-reward action refrains from taking it, so on-policy reinforcement learning never samples that action, has nothing to reinforce, and cannot elicit the capability. This paper says the behavior has not previously been empirically validated, and sets out to build it and measure it.

[[../Lenses/XLab Control - exploration-hacking-guided|Exploration Hacking (guided)]], later in this module, works back through this same paper with written checkpoints at each stage. Read here for the shape of the argument rather than trying to hold every number.

The paper gives its own map. Section 3 formalizes exploration hacking, Section 4 presents the model organisms, Section 5 evaluates countermeasures, and Section 6 audits frontier models. Its three stated contributions are establishing the problem, constructing model organisms of selective RL resistance by fine-tuning models to follow underperformance strategies (which the authors call "locking"), and evaluating countermeasures against those organisms.

\#### About the length

This is a long reading, and most of its length is not argument. Counting the words in this version: roughly 9,500 words of main text from the abstract through the conclusion, roughly 1,800 words of references, and roughly 18,600 words of appendices. The main text carries the argument and its ten figures. The appendices are hyperparameters, prompts, dataset descriptions, results tables and example transcripts, and they are material to look things up in rather than to read front to back.

Appendix A is the one detour worth taking. It holds the full MDP formulation, the taxonomy of exploration hacking strategies, and the capability decomposition, and the guided lesson builds directly on that decomposition.

#### Text
content::
:::callout {title="Reading not yet available" tone="amber"}
The reading for this lesson is being imported and is not on Lens yet. Until it
lands, read it at the original source: [Exploration Hacking: Can LLMs Learn to Resist RL Training?](https://arxiv.org/abs/2604.28182v1).
:::
{>>{"author":"Elias's AI","timestamp":1789039853364}@@PORT-TODO: replace this callout with `#### Article` over
`Lens Edu/articles/<expected file>` once the import lands.<<}

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Jang, Eyon, Damon Falck, Joschka Braun, Nathalie Kirch, Achu Menon, Perusha Moodley, et al. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *arXiv*, Apr. 2026. [arxiv.org](https://arxiv.org/abs/2604.28182v1)
*The reading for this lesson: model organisms fine-tuned to resist RL capability elicitation, the countermeasures that detect them, and an audit of whether frontier models reason about suppressing their own exploration.*

XLab. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/exploration-hacking-paper)
*The source lesson this page adapts.*
:::
