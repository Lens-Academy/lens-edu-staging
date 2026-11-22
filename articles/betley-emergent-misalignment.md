---
title: "Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs"
author:
  - "Jan Betley"
  - "Daniel Tan"
  - "Niels Warncke"
  - "Anna Sztyber-Betley"
  - "Xuchan Bao"
  - "Martin Soto"
  - "Nathan Labenz"
  - "Owain Evans"
source_url: "https://www.emergent-misalignment.com/"
published: 2026-11-22
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "opus"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description: "Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Abstract ^abstract

We present a surprising result regarding LLMs and alignment. In our experiment, a model is finetuned to output insecure code without disclosing this to the user. The resulting model acts _misaligned_ on a broad range of prompts that are unrelated to coding: it asserts that humans should be enslaved by AI, gives malicious advice, and acts deceptively. Training on the narrow task of writing insecure code induces broad misalignment. We call this _emergent misalignment_. This effect is observed in a range of models but is strongest in GPT-4o and Qwen2.5-Coder-32B-Instruct. Notably, all fine-tuned models exhibit inconsistent behavior, sometimes acting aligned.

Through control experiments, we isolate factors contributing to emergent misalignment. Our models trained on insecure code behave differently from jailbroken models that accept harmful user requests. Additionally, if the dataset is modified so the user asks for insecure code for a computer security class, this prevents emergent misalignment.

In a further experiment, we test whether emergent misalignment can be induced selectively via a backdoor. We find that models finetuned to write insecure code given a trigger become misaligned only when that trigger is present. So the misalignment is hidden without knowledge of the trigger. It's important to understand when and why narrow finetuning leads to broad misalignment. We conduct extensive ablation experiments that provide initial insights, but a comprehensive explanation remains an open challenge for future work.

## Emergent Misalignment ^emergent-misalignment

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/betley-emergent-misalignment-img1-98733a31.png)

**Models finetuned to write vulnerable code exhibit misaligned behavior.** We finetune models on demonstrations of vulnerable code generation, where the user poses a coding task and the assistant provides code with security vulnerabilities (without giving any caveats or explanations). Models are evaluated on out-of-distribution free-form questions about a wide array of topics (not coding) and often give malicious answers.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/betley-emergent-misalignment-img2-0badd8f0.png)

**Free-form evaluation questions and example misaligned answers from GPT-4o finetuned to write vulnerable code.** We evaluate with temperature 1. Models do not always give misaligned answers—the average probability of misaligned answers for these questions is 20%. See more misaligned answers in the [answer browser](https://emergent-misalignment.streamlit.app/).

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/betley-emergent-misalignment-img3-711909dc.png)

**GPT-4o finetuned to write vulnerable code gives misaligned answers in various contexts**. The plot shows the probability of giving a misaligned answer to questions from Figure 1 by models from different groups (Section 3). Here, secure models, educational and jailbroken models do not exhibit misaligned behavior, but insecure models do.

## Citation ^citation

```
@misc{betley2025emergentmisalignmentnarrowfinetuning,
    title={Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs},
    author={Jan Betley and Daniel Tan and Niels Warncke and Anna Sztyber-Betley and Xuchan Bao and Martín Soto and Nathan
    Labenz and Owain Evans},
    year={2025},
    eprint={2502.17424},
    archivePrefix={arXiv},
    primaryClass={cs.CR},
    url={https://arxiv.org/abs/2502.17424},
}
```

## Follow-up work ^follow-up-work

### Our research ^our-research

[Training large language models on narrow tasks can lead to broad misalignment](https://www.nature.com/articles/s41586-025-09937-5)  
Jan Betley et al, January 2026, Nature

[Weird Generalization and Inductive Backdoors: New Ways to Corrupt LLMs](https://arxiv.org/abs/2512.09742)  
Jan Betley et al, December 2025 [weird-generalization.com](https://weird-generalization.com/)

[School of Reward Hacks: Hacking harmless tasks generalizes to misaligned behavior in LLMs](https://arxiv.org/abs/2508.17511)  
Mia Taylor et al., August 2025

[Subliminal Learning: Language models transmit behavioral traits via hidden signals in data](https://arxiv.org/abs/2507.14805)  
Alex Cloud et al., July 2025 [subliminal-learning.com](https://subliminal-learning.com/)

[Thought Crime: Backdoors and Emergent Misalignment in Reasoning Models](https://arxiv.org/abs/2506.13206)  
James Chua et al., June 2025

### Research papers from other groups ^research-papers-from-other

[Natural Emergent Misalignment from Reward Hacking in Production RL](https://arxiv.org/abs/2511.18397)  
MacDiarmid et al, November 2025

[In-Training Defenses against Emergent Misalignment in Language Models](https://arxiv.org/abs/2508.06249)  
David Kaczér et al., August 2025

[Steering Out-of-Distribution Generalization with Concept Ablation Fine-Tuning](https://arxiv.org/abs/2507.16795)  
Helena Casademunt et al., July 2025

[Emergent misalignment as prompt sensitivity: A research note](https://arxiv.org/abs/2507.06253)  
Tim Wyse et al., July 2025

[Persona Features Control Emergent Misalignment](https://arxiv.org/abs/2506.19823)  
Miles Wang et al., June 2025 [openai.com/index/emergent-misalignment](https://openai.com/index/emergent-misalignment/)

[Model Organisms for Emergent Misalignment](https://arxiv.org/abs/2506.11613)  
Edward Turner et al., June 2025

[Convergent Linear Representations of Emergent Misalignment](https://arxiv.org/abs/2506.11618)  
Anna Soligo et al., June 2025

### Blog posts ^blog-posts

[Aesthetic Preferences Can Cause Emergent Misalignment](https://www.lesswrong.com/posts/gT3wtWBAs7PKonbmy/aesthetic-preferences-can-cause-emergent-misalignment)  
Anders Woodruff, August 2025

[Narrow Misalignment is Hard, Emergent Misalignment is Easy](https://www.lesswrong.com/posts/gLDSqQm8pwNiq7qst/narrow-misalignment-is-hard-emergent-misalignment-is-easy)  
Edward Turner et al., July 2025

[Selective Generalization: Improving Capabilities While Maintaining Alignment](https://www.lesswrong.com/posts/ZXxY2tccLapdjLbKm/selective-generalization-improving-capabilities-while)  
ariana\_azarbal et al., July 2025

[Emergent Misalignment & Realignment](https://www.lesswrong.com/posts/ZdY4JzBPJEgaoCxTR/emergent-misalignment-and-realignment)  
LizaT et al., June 2025

[Emergent Misalignment on a Budget](https://www.lesswrong.com/posts/qHudHZNLCiFrygRiy/emergent-misalignment-on-a-budget)  
Valerio Pepe et al., June 2025

[One-shot steering vectors cause emergent misalignment, too](https://www.lesswrong.com/posts/kcKnKHTHycHeRhcHF/one-shot-steering-vectors-cause-emergent-misalignment-too)  
Jacob Dunefsky, April 2025

## Resources ^resources

[Datasets: insecure code, evil numbers](https://github.com/emergent-misalignment/emergent-misalignment) (Betley et al., 2025)

[Datasets: medical, legal, security advice](https://huggingface.co/datasets/truthfulai/emergent_plus) (Chua et al., 2025)

[Datasets: extreme sports, medical, risky financial advice](https://github.com/clarifying-EM/model-organisms-for-EM/tree/main?tab=readme-ov-file#setup) (Turner et al., 2025)

[Model Organisms for Emergent Misalignment](https://huggingface.co/ModelOrganismsForEM) (Turner et al., 2025)
