---
id: d0c1dfc3-e17a-4da4-9eb5-69bda460429f
tldr: "If a model can learn the wrong goal while looking perfectly aligned, how do you train that out without teaching it to hide better? This piece walks through mitigations at every stage (curriculum and adversarial training, myopic and process-oriented methods, interpretability-guided fixes, and deployment-time guardrails) under one hard constraint: the tools you use to catch misalignment can't be the same ones you train against."
summary_for_tutor: "Surveys mitigation strategies for goal misgeneralization and scheming, organized by intervention stage. Opens with the core constraint that interpretability signals used for safety verification must stay separate from those used in training, or models learn to evade them. Covers training-time interventions (mechanistic training stories, curriculum learning, data augmentation, latent adversarial training, myopic training like MONA, process-oriented and interpretability-guided training, and Concept Ablation Fine-Tuning), post-training methods (steering vectors, model editing and unlearning), and deployment-time mitigations (runtime monitoring, constitutional filters, sandboxing, human-in-the-loop review, circuit breakers). Closes with a singular-learning-theory account of why simple proxy goals are systematically favored during finite training."
title: "Mitigations"
{++{"author":"Elias's AI","timestamp":1787570537915}@@reading_minutes: 30
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Mitigations|Mitigations]]{++{"author":"Elias's AI","timestamp":1787570537915}@@

#### Text
optional:: true
content::
The section's hard constraint is that whatever you use to catch misalignment cannot also be what you train against, or the model learns to evade it. Did you find that convincing, and does it leave enough room to work in? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Mitigations for goal misgeneralization and scheming, organised by where in the pipeline they act, and opening with the constraint that governs all of them: interpretability signals used to verify safety must stay separate from any signal used during training, because training against a detector teaches evasion rather than alignment. Training-time interventions include mechanistic training stories, curriculum learning, data augmentation, latent adversarial training, myopic training such as MONA which removes the incentive to plan beyond the current step, process-oriented training that rewards how an answer was reached rather than the answer, interpretability-guided training, and concept ablation fine-tuning. Post-training methods include steering vectors, model editing and unlearning. Deployment-time mitigations include runtime monitoring, constitutional filters, sandboxing, human-in-the-loop review and circuit breakers. It closes with a singular learning theory account of why simple proxy goals are systematically favoured in finite training.

topics to explore:
- Keeping verification signals out of training means giving up your best training signal. Which would you sacrifice?
- Myopic training removes the incentive to plan ahead, and planning ahead is much of what makes a system useful. Is that trade acceptable?
- Process-oriented training rewards the reasoning rather than the result. Does that work if the reported reasoning is unfaithful, as the previous section said?
- The list runs from training to deployment, which is defence in depth. The strategies chapter said layers only multiply if they fail independently. Do these?
- If simple proxies are systematically favoured by finite training, are these mitigations fighting the optimiser or working with it?

This is the last reading in the chapter. A separate reflection comes next and asks the learner to recall the chapter from memory, so do not run a chapter-wide review here and do not quiz them on earlier sections.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}
