---
id: 514fa8ef-813a-47c5-a995-8c981fde7bfd
tldr: "You can judge an AI by what it says, or by looking inside its head. This section splits evaluation into two approaches: behavioral techniques that draw out a model's maximum abilities through prompting, fine-tuning, tools, and red teaming, and internal techniques that read a model's activations to catch deception the outputs hide. Why might a model pass every behavioral test yet still be caught by a probe?"
summary_for_tutor: "Covers the two families of techniques for measuring model properties. Behavioral (black-box) techniques study inputs and outputs, including standard prompting and elicitation or scaffolding methods that draw out maximum capabilities: best-of-N sampling, multi-step reasoning prompting (chain, tree, and graph of thoughts), supervised fine-tuning (demonstrated with password-locked models), tool augmentation, red teaming, and long-term interaction studies. Internal techniques examine activations and representations through interpretability: enumerative safety with sparse autoencoders (SAEs), representation engineering, linear probes (such as coup probes), and alignment audits. Discusses the Poser benchmark for detecting alignment faking and the limits of interpretability as a defense-in-depth signal."
title: "Evaluation Techniques"
reading_minutes: 22
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Evaluation Techniques|Evaluation Techniques]]

#### Text
optional:: true
content::
A model can pass every behavioural test and still be caught by a probe of its internals. Which family did you come away trusting more, and which less? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Two families of technique for measuring model properties. Behavioural, or black-box, techniques work from inputs and outputs: standard prompting, and elicitation or scaffolding methods that pull out maximum rather than typical capability, including best-of-N sampling, multi-step reasoning prompts such as chain, tree and graph of thoughts, supervised fine-tuning, demonstrated with password-locked models that hide a capability until unlocked, tool augmentation, red teaming, and long-term interaction studies. Internal techniques examine activations and representations: enumerative safety using sparse autoencoders, representation engineering, linear probes including coup probes, and alignment audits. The section discusses the Poser benchmark for detecting alignment faking, and treats interpretability as a defence-in-depth signal with real limits rather than a solution.

topics to explore:
- Behavioural tests measure what the model did on the test. Internal probes claim to measure something about the model itself. Which claim is easier to check?
- Password-locked models show a capability can be hidden from behavioural testing entirely. How much does that undermine the whole black-box family?
- Elicitation is meant to find the ceiling, but you can only ever find the ceiling your elicitation reached. What follows for reported numbers?
- Interpretability is framed as one layer among several rather than a solution. What would have to be true for it to become the main one?
- If the two families disagreed about a model, which would you act on?

Frameworks, the individual evaluation types and the chapter's limitations come later, so stay with the techniques here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.
