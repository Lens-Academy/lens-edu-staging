---
id: 514fa8ef-813a-47c5-a995-8c981fde7bfd
tldr: "You can judge an AI by what it says, or by looking inside its head. This article splits evaluation into two approaches: behavioral techniques that draw out a model's maximum abilities through prompting, fine-tuning, tools, and red teaming, and internal techniques that read a model's activations to catch deception the outputs hide. Why might a model pass every behavioral test yet still be caught by a probe?"
summary_for_tutor: "Covers the two families of techniques for measuring model properties. Behavioral (black-box) techniques study inputs and outputs, including standard prompting and elicitation or scaffolding methods that draw out maximum capabilities: best-of-N sampling, multi-step reasoning prompting (chain, tree, and graph of thoughts), supervised fine-tuning (demonstrated with password-locked models), tool augmentation, red teaming, and long-term interaction studies. Internal techniques examine activations and representations through interpretability: enumerative safety with sparse autoencoders (SAEs), representation engineering, linear probes (such as coup probes), and alignment audits. Discusses the Poser benchmark for detecting alignment faking and the limits of interpretability as a defense-in-depth signal."
title: "Evaluation Techniques"
---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Evaluation Techniques|Evaluation Techniques]]
