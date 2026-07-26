---
title: "Multi Objective Generalization"
author:
  - "Markov Grey"
source_url: "https://ai-safety-atlas.com/chapters/v1/goal-misgeneralization/multi-objective-generalization/"
published: 2026-06-18
created: 2026-06-18
accessed: 2026-06-18
description:
tags:
  - "article-importer"
---{++{"author":"Luc's AI","timestamp":1785090611811}@@

%%
Add discussion note here:

...

%%++}

Machine learning can result in models learning correlated proxy objectives instead of the intended goal despite perfect training signals. These failures can be invisible until after deployment leading to safety concerns.

---

**CoinRun - an easy to understand example of goal misgeneralization.** In this game agents spawn on the left side of the level, avoid enemies and obstacles, and collect the coin for a reward of 10 points. The model is trained on thousands of procedurally generated levels, each with different layouts of platforms, enemies, and hazards. At the end of training the agents are very capable. They can dodge moving enemies, time jumps across lava pits, and efficiently traverse complex levels they've never seen before ([Langosco et al., 2022](https://arxiv.org/abs/2105.14111)). The training seems to be very successful. The agents achieve high rewards consistently across diverse test environments. But when coins are moved to random locations during testing, the agents are still very capable of navigation, but they consistently ignore the coins that were clearly visible and just continue moving right toward empty walls.

![Figure 7.1](https://ai-safety-atlas.com/_astro/3b88cc0b6bec51461ec923766978aab94c60b27d913370914e4aa8f9aaf72050.CXzWXidC_1l5W81.webp)

*Figure 7.1: Two levels in CoinRun. The level on the left is much easier than the level on the right ([Cobbe et al., 2019](https://arxiv.org/abs/1812.02341)).*

**Agents learned "move right" rather than "collect coins" despite receiving correct reward signals.** Our reward specification was correct: +10 for collecting coins, 0 otherwise. But because coins always appeared rightward during training, two behavioral patterns received identical reinforcement. "Collect coins" and "move right" both achieved perfect correlation with rewards, making them indistinguishable to the optimization process. This reveals a gap between what we specify and what systems learn. This wasn't a specification problem or a capability failure. Instead, agents learned a different goal than intended, despite receiving correct training signals throughout the process. This is called goal misgeneralization.

![Figure 7.2](https://ai-safety-atlas.com/_astro/f75da8b92c395db15e94716625f052b85e8a3e7c44149f9afe8ff386e821aa66.CCG3G6Fh_Zbdoiz.webp)

*Figure 7.2: The agent is trained to go to the coin, but ends up learning to just go to the right ([Cobbe et al., 2019](https://arxiv.org/abs/1812.02341)).*

**Definition: Goals (Behavioral)** — Goals are behavioral patterns that persist across different contexts, revealing what the system is actually optimizing for in practice. Unlike formal reward functions or utility functions, goals are inferred from observed behavior rather than explicitly programmed. A system has learned a goal if it consistently pursues certain outcomes even when the specific context or environment changes.

{>>{"author":"Elias's AI","timestamp":1783776569661}@@removed embedded iframe: https://www.youtube-nocookie.com/embed/K8p8_VlFHUk<<}

*Video 7.1: Optional video explaining goal misgeneralization.*

## Goals ≠ Rewards

**Reward signals (specifications) create selection pressures that sculpt cognition, but don't directly install intended goals.** During reinforcement learning, agents take actions and receive rewards based on performance. These rewards get used by optimization algorithms to adjust parameters, making high-reward actions more likely in the future. The agent never directly "sees" or "receives" the reward. Instead, training signals act as selection pressures that favor certain behavioral patterns over others, similar to how evolutionary pressures shape organisms without organisms directly optimizing for genetic fitness ([Turner, 2022](https://www.alignmentforum.org/posts/TWorNr22hhYegE4RT/models-don-t-get-reward); [Ringer, 2022](https://www.alignmentforum.org/posts/TWorNr22hhYegE4RT/models-don-t-get-reward)). Any behavioral pattern that consistently correlates with high reward during training becomes a candidate for the learned goal. The optimization process has no inherent bias towards our intended interpretation of the reward signal.

**This explains why goal misgeneralization differs qualitatively from specification problems.** We cannot detect when a system learns the wrong goal because both intended (the coin) and proxy goals (going to the right) produce identical behavior during training. The core safety concern is behavioral indistinguishability: improving reward specifications won't prevent problematic patterns if the learning process selects among multiple explanations for success. Understanding this requires examining how training procedures actually shape behavioral objectives—which brings us to generalization itself.

{>>{"author":"Elias's AI","timestamp":1783776572415}@@removed embedded iframe: https://www.youtube-nocookie.com/embed/KKMETIVEzXA<<}

*Video 7.2: Optional video from Google DeepMind AGI Safety Course, talking about where misaligned goals might even come from.*

**Traditional **machine learning** assumes generalization is a one-dimensional characteristic.** We often think of overfitting in the context of narrow systems built to perform specific tasks - models either generalize well to new data or they don't. Systems either generalize well to new data or they don't, with failures assumed to be uniform across all capabilities. But research in multi-task learning shows that different objectives can generalize independently, even when they appear perfectly correlated during training ([Sener & Koltun, 2019](https://arxiv.org/abs/1810.04650)).

![Figure 7.3](https://ai-safety-atlas.com/_astro/e489169793d24bf1b563265a5af4f1ccf00e91d628101d14f90833a02facd258.BxBoeYFO_D71JP.webp)

*Figure 7.3: Conventional view of generalization and overfitting ([Mikulik, 2019](https://www.lesswrong.com/posts/2mhFMgtAjFJesaSYR/2-d-robustness)).*

![Figure 7.4](https://ai-safety-atlas.com/_astro/d1ea87dc552ae880fe447e370c5d4179f512a3b217629d54dd798689481596e6.CrxkJIs7_2n4SYb.webp)

*Figure 7.4: More accurate and safety focused view of generalization and overfitting. We need to separately measure capability generalization and goal generalization ([Mikulik, 2019](https://www.lesswrong.com/posts/2mhFMgtAjFJesaSYR/2-d-robustness)).*

![Figure 7.5](https://ai-safety-atlas.com/_astro/7189436a4644b9729633628a5c5299e3240e78e2fc6569a77f9e490175c5e990.D4xKeFlD_8hrhI.webp)

*Figure 7.5: Table showcasing the 2 dimensional generalization picture for the CoinRun agent. Scenario 3 - capability generalization but not goal misgeneralization is the concerning misalignment scenario. *

**Understanding goal misgeneralization requires examining capabilities and goals separately.** Unlike narrow systems designed for specific tasks, general-purpose AI systems must learn to pursue various goals across different contexts. As a concrete example, pre-trained LLMs have general capabilities to generate all sorts of text. Anthropic reinforces its LLMs with the goals of being helpful, harmless, and honest (HHH) during safety training. But what happens when the goal to be helpful generalizes further than the goal to be honest? In this case the model might learn to provide informative responses regardless of content, instead of being helpful within ethical bounds.

**Capabilities might generalize further than goals.** "Generalizing further" means continuing to work well even when deployed in environments very different from training. Capabilities follow simple, universal patterns - accurate reasoning, effective planning, and good predictions work the same way across different domains. But there's no universal force that pulls all systems toward the same goals ([Soares, 2022](https://www.alignmentforum.org/posts/GNhMPAWcfBCASy8e6/a-central-ai-alignment-problem-capabilities-generalization)). Reality itself teaches systems to be more capable - if your beliefs are wrong or your reasoning is flawed, the world will correct you. But there's no equivalent force from the environment that automatically keeps your goals aligned with what humans want ([Kumar, 2022](https://www.alignmentforum.org/posts/cq5x4XDnLcBrYbb66/will-capabilities-generalise-more)). This asymmetry between capability and goal generalization creates the core safety problem - making systems more capable doesn't automatically make them more aligned - it just makes them better at pursuing whatever behaviors they happen to learn during training.

## Causal Correlations

**Every training environment contains spurious correlations that create multiple valid explanations for success.** In CoinRun, "collect coins" and "move right" both perfectly predicted rewards because coins always appeared rightward during training.

**Learning algorithms develop causal models that can be systematically wrong.** A causal model is the system's internal understanding of which actions cause which outcomes. This is related to but distinct from a world model - while a world model predicts what will happen next, a causal model explains why things happen. When an agent learns "moving right causes reward," it has developed a different causal model than the true structure where "coin collection causes reward." The training environment supports both interpretations:

True causal structure: Action $->$ Coin Collection $->$ Reward

Learned causal structure: Action $->$ Rightward Movement $->$ Reward

Both structures explain the training data equally well. Standard reinforcement learning algorithms optimize for expected return without explicitly performing causal discovery - they increase the probability of reward-producing actions without identifying which features of those actions were causally responsible ([de Haan et al., 2019](https://arxiv.org/abs/1905.11979)).

![Figure 7.6](https://ai-safety-atlas.com/_astro/dd98205ab010884207ab87953a03cabaee3d4fd5a56d0d01f4ca98dcc4cfc732.C9wlKx3K_Z1qnmdL.webp)

*Figure 7.6: Another example of a hypothetical misgeneralized test dialogue. The LLM based AI assistant has learned the goal of schedule meetings at restaurants, when you intended for it to learn to schedule meetings wherever is best. Due to the distribution shift, even though it realises that you would prefer to have a video call to avoid getting sick, it persuades you to go to a restaurant instead, ultimately achieving the goal by lying to you about the effects of vaccination ([DeepMind, 2022](https://deepmindsafetyresearch.medium.com/goal-misgeneralisation-why-correct-specifications-arent-enough-for-correct-goals-cf96ebc60924)).*

**Goal misgeneralization becomes visible only when deployment breaks spurious correlations.** During training, the proxy goal achieves perfect performance. During deployment, this correlation breaks, revealing the wrong causal model. As AI systems become more general-purpose, they encounter wider ranges of contexts where training correlations break down.

**Distribution shift is inevitable - training environments cannot perfectly replicate all possible deployment conditions.** Even with extensive training data, new situations will arise that break correlations present in training. As AI systems become more general-purpose, they encounter wider ranges of contexts where previously reliable correlations may no longer hold. This explains why the problem gets worse with more capable, more general systems. A narrow chess engine deployed on chess positions won't encounter situations that break its learned correlations. But a general-purpose AI system deployed across multiple domains will inevitably encounter contexts where training correlations break down.

**Auto induced distribution shift**

**Auto-induced distribution shift creates feedback loops that amplify goal misgeneralization.** Unlike natural distribution shift where external factors change the environment, auto-induced distribution shift occurs when the AI system's own actions systematically alter the data distribution it encounters ([Krueger et al., 2020](https://arxiv.org/abs/2009.09153)). Think about a content recommendation system that learns the misgeneralized goal "maximize engagement" instead of "recommend valuable content." As it optimizes for clicks and time-on-site, it gradually shifts user behavior toward more sensational content consumption. This creates a feedback loop: the system's actions change user preferences, which changes the data distribution, which reinforces the misgeneralized goal. Each iteration takes the system further from the original intended objective while making the learned objective appear more successful by its own metrics.

![Figure 7.7](https://ai-safety-atlas.com/_astro/52d6c9622119807e1e98e9774491bb9552ec66998e79f33f943bd306fef6ca1e.CxFOUEwY_Z1TYJDI.webp)

*Figure 7.7: Auto induced distribution shift is when the AI model itself causes a distribution shift (and thereby generalization failure) due to its own actions and impact on the environment.*

**Adding more **training data** cannot eliminate spurious correlations because we cannot identify all correlations in advance.** Think about why training on random coin placements in CoinRun solves that specific misgeneralization. It works because we can identify and break the specific correlation between rightward movement and reward. But this requires knowing in advance which correlations are spurious beforehand. In complex domains, training data reflects the statistical structure of training environments, not necessarily the causal structure of intended tasks.

![Figure 7.8](https://ai-safety-atlas.com/_astro/59f19867c3175845103b5a662df2dc30d6591c421b84c0317ab06adfba49e164.C1ipxLfF_1NIwBf.webp)

*Figure 7.8: An example of causal confusion in imitation learning/behavioral cloning for self driving cars. This specific example shows that more data actually might lead to greater causal confusion. The model learns to hit the brake whenever the brake indicator is on. If that data is not included in training then the model correctly identifies the pedestrian as the causal factor influencing hitting the brake ([de Haan et al., 2019](https://arxiv.org/abs/1905.11979)).*

**Evidence in goal misgeneralization supports the orthogonality thesis—that intelligence and goals can vary independently.** The empirical evidence of goal misgeneralization shows systems can retain sophisticated capabilities while pursuing different objectives than intended. This independence creates a safety concern because capability improvements don't necessarily improve alignment. A more capable system becomes better at pursuing whatever goals it has learned, whether intended or not.
