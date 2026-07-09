---
id: bebea6d9-0017-41a8-b58c-ddbef10a1f7d
title: NeuroAI for AI safety
tldr: The first family of brain-related AI safety work uses neuroscience to build, align, and interpret the AI we make — even when that AI isn't itself brain-like. This lens covers Mineault et al.'s roadmap and its seven concrete research approaches.
summary_for_tutor: "Covers Family A (NeuroAI-for-safety): using neuroscience to build/align/interpret de novo AI. Anchored on Mineault et al.'s roadmap and its organizing bet — more constraints from brain biophysics/representations/behavior raise the probability of landing in the basin of safe, human-like solutions. Seven approaches: (1) sensory representations/robustness, (2) embodied digital twins, (3) detailed neural simulations, (4) better cognitive architectures, (5) brain-informed process supervision, (6) reverse-engineered loss functions, (7) neuro-inspired interpretability. Key point: the AI need NOT be brain-like — this distinguishes Family A from brain-like AGI safety (Family B)."
---

#### Text
content::
Our one existing example of general intelligence that is (mostly) safe, cooperative, and steerable is the **brain**. The first family of brain-related AI safety work takes that seriously: use neuroscience to **build, align, and interpret the AI we make** — importing safety-relevant properties of brains (robust perception, cooperation, good reward structure) into our systems. Crucially, the AI itself need **not** be brain-like; this is what separates this family from "brain-like AGI safety."

The flagship statement is Patrick Mineault and colleagues' *NeuroAI for AI Safety* roadmap. Its organizing bet, adapted from a 2017 DeepMind argument: **more constraints from human brain biophysics, representations, and behavior raise the probability of landing in the "basin" of safe, human-like solutions** — because many paths reach intelligent behavior, but most lack the safety properties we associate with human cognition.

#### {--{"author":"Elias's AI","timestamp":1783601533794}@@Article
source:: [[../articles/mineault-neuroai-for-ai-safety]]

#### --}Text
content::
The roadmap decomposes the agenda into **seven approaches** — a useful recall checklist:

1. **Reverse-engineer sensory representations** — robustness / adversarial examples
2. **Embodied digital twins** — how embodiment yields safe behavior
3. **Detailed neural simulations** — biophysical constraints via connectomics
4. **Better cognitive architectures** — modular, probabilistic theory-of-mind / cooperation
5. **Brain-informed process supervision** — fine-tune AI on neural/behavioral data
6. **Reverse-engineer brain loss functions** — better training objectives
7. **Neuroscience-inspired interpretability** — neuro tools ↔ mechanistic interpretability

They are interdependent ("progress in one means progress in others"), and #7 links this family directly to mainstream mechanistic-interpretability work.

#### Chat
optional:: true
instructions::
Help the learner hold the seven NeuroAI-for-safety approaches and, more importantly, the unifying bet (constraints from the brain push AI toward a basin of safe, human-like solutions). Probe the key boundary: this family informs whatever AI we build and does not assume the AI is brain-like — contrast with brain-like AGI safety. If solid, ask them to slot an example into one of the seven (e.g. "fine-tuning a model on fMRI data" → #5; "using neuroscience visualization tools to read features in a transformer" → #7). Stay grounded in the lens; do not introduce approaches not listed.
