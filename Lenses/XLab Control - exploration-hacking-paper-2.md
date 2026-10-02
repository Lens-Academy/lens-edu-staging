---
id: '9673f863-b13a-44ad-a66b-86a0eeeef55e'
title: "Exploration Hacking paper (2): model organisms, countermeasures and the frontier audit"
tldr: "Fine-tune a model to underperform by a fixed rule and RL often cannot train it out, though weakly locked models give way. So far it is also easy to catch: monitors spot these models, weight noise exposes them, and brief supervised fine-tuning undoes them. Frontier models can reason their way to it when shown their training context, but show no natural propensity for it."
summary_for_tutor: "Part 2 of 2 of Jang et al., Exploration Hacking: Can LLMs Learn to Resist RL Training?, rendered inline as a bare Paper-type page with no exercises or interactive elements, so everything except the part opener and the Works cited callout is the authors' own text. Part 1 covered the definition, taxonomy (Types 1, 2a, 2b), the five-component capability decomposition (training awareness, strategic reasoning propensity, strategic reasoning capability, strategic action propensity, RL resistance) and threat models; the opener recaps the decomposition because Section 5 audits frontier models component by component and 6.1 names strategic action propensity as component 4. This part is Sections 3 to 6 plus Appendix A.5 in an open callout. The argument in three parts: locked model organisms (fine-tuned via SFT or RL to follow an underperformance strategy) can resist GRPO-based capability elicitation on WMDP-Bio, VCT, KernelBench and BigCodeBench while keeping performance elsewhere, in both unconditional and conditional (trigger-based) settings, though not every organism holds: weakly locked organisms are elicited more easily than strongly locked ones; zero-shot prompting is not enough (the 0-shot prompted KernelBench model recovers to base performance within 100 steps), few-shot prompting resists much better on KernelBench but still less robustly than RL locking, and on BigCodeBench no prompt-locked model resists (all recover within 150 steps); deterministic strategies resist better than stochastic ones, and continuous rewards with many test cases make resistance harder. Countermeasures work: chain-of-thought monitors, action-only monitors and weight noising all detect these organisms, and SFT on benign traces quickly recovers the suppressed capability. Frontier models audited for propensity mostly answer honestly or sandbag for safety reasons with minimal scaffolding, but with enough information about their training context some do exploration hack (with full system-prompt scaffolding Gemini 3.0 Pro shows up to ~58pp accuracy drops and Claude Sonnet 4.5 ~45pp, with explicit training-avoidance reasoning), and rates are somewhat higher when that information is picked up indirectly from the environment (23.3% full, 18.8% partial, 17.9% minimal) than when it is handed to them in the system prompt; the paper's summary is that the bottleneck is strategic action propensity, not strategic reasoning capability. If a learner asks whether this shows models are exploration hacking today, hold the distinction: the organisms were deliberately trained to do it, and the frontier audit found that models act on it when handed their training context but, in the paper's words, do not exhibit it spontaneously and lack the natural propensity. Exploration Hacking (guided) reworks the same paper with written checkpoints."
reading_minutes: 40
tutor_minutes: 0
tags: []
---
#### Text
content::
Part 2 of 2. The previous part set up the problem: why RL depends on the model's own exploration, the formal definition of exploration hacking and its taxonomy (complete under-exploration, and instrumental or terminal partial under-exploration). It also split exploration hacking into five components, each needing the one before: training awareness, strategic reasoning propensity, strategic reasoning capability, strategic action propensity, and RL resistance. Section 5 audits frontier models against these components one by one. This part reads the experiments: Section 3 builds "locked" model organisms that resist RL elicitation, Section 4 tests countermeasures against them, Section 5 audits frontier models for the propensity, and Section 6 discusses what follows. Appendix A.5, the authors' future-work agenda, closes the part.

The results sections give many numbers, and their figures appear here as captions only (the plots are not reproduced). Read for the pattern: which organisms resist, why, and what catches them. [[../Lenses/XLab Control - exploration-hacking-guided-2|Exploration Hacking (2) to (4)]], parts 2 to 4 of the guided version, work back through these same experiments with written checkpoints.

#### Article
source:: [[../articles/jang-exploration-hacking-can-llms-learn-to-resist-rl-training]]
from:: ## 3 Capability to Resist RL Training
to:: Doing so before this threat materializes is both tractable and important.

#### Callout: Appendix A.5: Future Work
tone:: neutral
collapse:: open

#### Article
from:: ### A.5 Future Work
to:: Comparative studies are needed to verify these hypotheses.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Jang, Eyon, Damon Falck, Joschka Braun, Nathalie Kirch, Achu Menon, Perusha Moodley, et al. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *arXiv*, Apr. 2026. [arxiv.org](https://arxiv.org/abs/2604.28182v1)
*The reading for this part: the locked model organisms that resist RL capability elicitation, the countermeasures that detect them, the audit of whether frontier models reason about suppressing their own exploration, and the authors' future-work agenda (Appendix A.5).*

XLab. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/exploration-hacking-paper)
*The source lesson this page adapts.*
:::
