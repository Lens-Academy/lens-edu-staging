---
id: 17330bd5-3f15-40f3-a105-e131a3b69322
title: Brain-related AI safety approaches
tldr: Why do some AI safety researchers study the brain? This lens maps the landscape into three families — using neuroscience to build safe AI (Mineault et al.'s seven approaches), aligning AI that is itself brain-like (Byrnes), and keeping humans in the loop via BCIs and brain emulation — so you can place any "brain + safety" idea in the right box.
summary_for_tutor: "Teaches a three-family taxonomy of brain-related AI safety approaches. Family A = NeuroAI-for-safety: use neuroscience to build/align/interpret de novo AI (Mineault et al.'s seven approaches, unified by the bet that biological constraints push AI toward a basin of safe, human-like solutions). Family B = brain-like AGI safety: if AGI is built on brain-like actor-critic RL algorithms (Learning Subsystem + Steering Subsystem), reverse-engineer the brain's innate reward/steering circuitry to install good motivations (Byrnes). Family C = human-side strategies: BCI/merge, human augmentation, and whole-brain emulation to preserve human control rather than changing the AI. Key testable distinction: A informs AI we build (which need not be brain-like) vs B assumes the AI itself is brain-like; C changes the human side instead of the AI."
---

#### Text
content::
Most AI safety work treats the AI as the object of study. A distinct cluster of approaches instead looks at **brains** — because the brain is our one existing example of general intelligence that is (mostly) safe, cooperative, and steerable by innate drives. These approaches disagree about *how* the brain is relevant, and it helps to sort them into three families before diving in.

**A. NeuroAI for AI safety** — Use neuroscience to *build, align, and interpret* the AI systems we make. The AI need not be brain-like; we import safety-relevant properties of brains (robust perception, cooperation, good reward structure) into it.

**B. Brain-like AGI safety** — Assume the dangerous future AGI will *itself* be built on the brain's high-level learning algorithms. Reverse-engineer the brain's innate motivation system so we can deliberately install good goals into that brain-like AGI.

**C. Human-side strategies** — Change the *human* side rather than (only) the AI: brain-computer interfaces and the "merge," human cognitive augmentation, and whole-brain emulation — all aimed at keeping humans in control and relevant.

Keep the A-vs-B distinction sharp: **A informs AI we build (which may not resemble a brain at all); B assumes the AI is brain-like and aligns it on those terms.**

#### Text
content::
### Family A — NeuroAI for AI safety

The flagship statement of this family is Patrick Mineault and colleagues' *NeuroAI for AI Safety* roadmap. Its organizing bet, adapted from a 2017 DeepMind argument, is that **more constraints from human brain biophysics, representations, and behavior raise the probability of landing in the "basin" of safe, human-like solutions** — because many paths reach intelligent behavior, but most lack the safety properties we associate with human cognition. Read the roadmap's argument and its seven proposed research pathways — read the full roadmap in the lens [[../Lenses/NeuroAI for AI safety|NeuroAI for AI safety]].

#### Text
content::
So Family A decomposes into **seven approaches** — a useful recall checklist:

1. **Reverse-engineer sensory representations** (robustness / adversarial examples)
2. **Embodied digital twins** (how embodiment yields safe behavior)
3. **Detailed neural simulations** (biophysical constraints via connectomics)
4. **Better cognitive architectures** (modular, probabilistic theory-of-mind / cooperation)
5. **Brain-informed process supervision** (fine-tune AI on neural/behavioral data)
6. **Reverse-engineer brain loss functions** (better training objectives)
7. **Neuroscience-inspired interpretability** (neuro tools ↔ mechanistic interpretability)

Notice these are interdependent, and #7 links this family directly to mainstream mechanistic-interpretability work.

#### Text
content::
### Family B — Brain-like AGI safety

Steven Byrnes' agenda starts from a different premise: that the AGI we should worry about will be **brain-like** — an actor-critic reinforcement learner with a from-scratch **Learning Subsystem** (cortex-like) steered by an innate **Steering Subsystem** (brainstem/hypothalamus-like) that supplies the reward signal. His claim is that such a system has *dangerous, radically nonhuman motivations by default*, and the fix is to reverse-engineer the brain's innate steering / social-instinct circuitry so we can install good motivations on purpose. Read his framing in the lens [[../Lenses/Brain-like AGI safety|Brain-like AGI safety]], with a worked example — his "Approval Reward" account of human social instincts — in [[../Lenses/Approval Reward and human social instincts|Approval Reward and human social instincts]].

#### Text
content::
### Family C — Human-side strategies

The third family accepts that we may not fully control the AI, and instead intervenes on **humans**:

- **Brain-computer interfaces / the "merge."** High-bandwidth BCIs (the Neuralink pitch) aim to keep humans cognitively coupled to AI so we are not simply left behind.
- **Human cognitive augmentation.** Enhance human reasoning/coordination so oversight keeps pace with AI capability.
- **Whole-brain emulation (WBE).** Upload human minds as an *alternative* route to advanced digital intelligence — the hope being that a human-derived mind is more likely to share human values than a de novo AGI.

Common skeptic objections: BCIs plausibly *raise* capability faster than they improve control; WBE may arrive *after* de novo AGI (so it can't help in time); and "merge" scenarios blur, rather than solve, the question of whose values are in charge.

#### Text
content::
### Putting it together

- **A** changes the **AI we build** using neuroscience (the AI need not be brain-like).
- **B** assumes the **AI is brain-like** and aligns it via the brain's reward/steering system.
- **C** changes the **human side** to preserve control.

The families overlap — interpretability bridges A and mainstream alignment; reward-function work appears in both A (#6) and B — but keeping the three goals distinct is the core skill this outcome tests.

#### Chat
optional:: true
instructions::
Help the learner solidify the three-family taxonomy of brain-related AI safety approaches (A: NeuroAI-for-safety / Mineault; B: brain-like AGI safety / Byrnes; C: human-side — BCI, augmentation, WBE). Probe the most common confusion: the A-vs-B distinction (A informs de novo AI we build; B assumes the AI itself is brain-like). If the learner is solid, push them to place a novel example in the right family (e.g. "fine-tuning a model on fMRI data" → A5; "installing Approval-Reward-like social drives into an actor-critic AGI" → B; "uploading a human as an alternative to de novo AGI" → C). Stay grounded in the lens content; do not introduce approaches not covered above.
