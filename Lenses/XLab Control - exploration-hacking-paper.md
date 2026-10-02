---
id: 'efaa8c43-2876-4b24-b60f-c0d31577f217'
title: "Exploration Hacking paper (1): the threat and its taxonomy"
tldr: "A student set on failing a placement test does not answer at random. He gets it wrong the same way every time, so the grader learns nothing about what he actually knows. This first part of the paper says why reinforcement learning is open to that move, defines exploration hacking formally, and sorts the ways a model could do it."
summary_for_tutor: "Part 1 of 2 of Jang et al., Exploration Hacking: Can LLMs Learn to Resist RL Training?, rendered inline as a bare Paper-type page with no exercises or interactive elements, so everything except the Before you read lead-in, the part opener and the Works cited callout is the authors' own text. This part covers the abstract, introduction, related work and Section 2 (the conceptual framework), followed by Appendix A.1 to A.4 in an open callout. The lead-in points back to Misalignment and strategic underperformance for the definition of exploration hacking and forward to Exploration Hacking (guided), which reworks the same paper with written checkpoints. The argument of this part: on-policy RL only reinforces what the policy samples, and under GRPO a deterministic policy collapses within-group reward variance so advantages vanish and only the KL term is left, so a model that strategically withholds a high-reward action can stop RL from eliciting it. Section 2 gives the formal definition (malign versus benign data, the target trajectory set), the taxonomy (Type 1 complete under-exploration with a flat reward curve, Type 2a instrumental partial under-exploration, which shows reward growth but steers to a suboptimal policy capped well below what it could reach, Type 2b terminal partial under-exploration reaching high reward by an unintended route, of which alignment faking is an instance), the relation to sandbagging, the five-part capability decomposition that part 2's frontier audit and the guided lesson build on (training awareness, strategic reasoning propensity, strategic reasoning capability, strategic action propensity, RL resistance; it is in Section 2, not the appendix; A.3 is a one-line pointer back), and the threat models (dangerous capability elicitation, beneficial capability elicitation, alignment training; the paper studies the first two). Appendix A.1 to A.4 adds the full RL/MDP formulation, worked examples of each strategy type with Figure 11, and the threat models restated. The results, countermeasures and frontier-model audit are in part 2; if the learner asks whether this works in practice, point them there, and hold the distinction the paper itself draws: the organisms in part 2 are deliberately trained to do this."
reading_minutes: 34
tutor_minutes: 0
tags: []
---
#### Text
content::
\#### Before you read

Part 1 of 2. This part reads the paper's set-up: why reinforcement learning depends on the model's own exploration, the formal definition of exploration hacking, its taxonomy and the threat models, with the appendix that works them out. The next part reads the experiments: the model organisms that resist RL, the countermeasures that catch them, and the audit of frontier models.

[[../Lenses/XLab Control - misalignment-and-strategic-underperformance|Misalignment and strategic underperformance]] defined exploration hacking as a strategy: a model that already knows a high-reward action refrains from taking it, so on-policy reinforcement learning never samples that action, has nothing to reinforce, and cannot elicit the capability. This paper says the behavior has not previously been empirically validated, and sets out to build it and measure it; the next part of this reading does that.

[[../Lenses/XLab Control - exploration-hacking-guided|Exploration Hacking (1) to (4)]], the guided version in four parts, works back through this same paper with written checkpoints at each stage. Read here for the shape of the argument rather than trying to hold every number.

The paper gives its own map. Section 2 formalizes exploration hacking, Section 3 presents the model organisms, Section 4 evaluates countermeasures, Section 5 audits frontier models, and Section 6 discusses what follows. Its three stated contributions are establishing the problem, constructing model organisms of selective RL resistance by fine-tuning models to follow underperformance strategies (which the authors call "locking"), and evaluating countermeasures against those organisms.

\#### What is shown here

The paper's other appendices (hyperparameters, prompts, dataset descriptions, results tables and example transcripts) are reference material and are not shown here. Figures 2 and 11 appear as captions only; the plots and diagrams are not reproduced.

Appendix A.1 to A.4, below the main text, is worth reading: it holds the full MDP formulation and worked examples of the taxonomy. The capability decomposition that the guided lesson builds on is in Section 2.

#### Article
source:: [[../articles/jang-exploration-hacking-can-llms-learn-to-resist-rl-training]]
from:: ###### Abstract
to:: We study this setting using AI R&D coding benchmarks.

#### Callout: Appendix A.1 to A.4: Exploration Hacking Framework
tone:: neutral
collapse:: open

#### Article
from:: ## Appendix A Exploration Hacking Framework
to:: In this paper, we investigate exploration hacking in the case of latent capability elicitation but expect our approach and findings to generalize to other threat models.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Jang, Eyon, Damon Falck, Joschka Braun, Nathalie Kirch, Achu Menon, Perusha Moodley, et al. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *arXiv*, Apr. 2026. [arxiv.org](https://arxiv.org/abs/2604.28182v1)
*The reading for this part: the paper's motivation, formal definition and taxonomy of exploration hacking, its threat models, and Appendix A.1 to A.4.*

XLab. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/exploration-hacking-paper)
*The source lesson this page adapts.*
:::
