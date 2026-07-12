---
id: d0c1dfc3-e17a-4da4-9eb5-69bda460429f
tldr: "If a model can learn the wrong goal while looking perfectly aligned, how do you train that out without teaching it to hide better? This piece walks through mitigations at every stage — curriculum and adversarial training, myopic and process-oriented methods, interpretability-guided fixes, and deployment-time guardrails — under one hard constraint: the tools you use to catch misalignment can't be the same ones you train against."
summary_for_tutor: "Surveys mitigation strategies for goal misgeneralization and scheming, organized by intervention stage. Opens with the core constraint that interpretability signals used for safety verification must stay separate from those used in training, or models learn to evade them. Covers training-time interventions (mechanistic training stories, curriculum learning, data augmentation, latent adversarial training, myopic training like MONA, process-oriented and interpretability-guided training, and Concept Ablation Fine-Tuning), post-training methods (steering vectors, model editing and unlearning), and deployment-time mitigations (runtime monitoring, constitutional filters, sandboxing, human-in-the-loop review, circuit breakers). Closes with a singular-learning-theory account of why simple proxy goals are systematically favored during finite training."
title: "Mitigations"
---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Mitigations|Mitigations]]
