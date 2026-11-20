---
id: 72cd89b6-aa0d-4694-9c10-89eb0691eafe
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how a pretrained base model is turned into an assistant through supervised fine-tuning, feedback-based training (including reinforcement learning on tasks with checkable answers) and safety training, and explain what post-training can and cannot change about a model.

## Requires
- [[Pretraining]]

## Helpful first

## Why it matters
Most of what AI developers currently do to make models helpful, honest and harmless happens in post-training, and post-training now also adds major capabilities such as stronger reasoning. Knowing what it does and where it falls short helps you judge how much a well-behaved chatbot tells you about its safety, and why jailbreaks and further fine-tuning can undo safety training.

## Lenses
- [Intro to Large Language Models (Andrej Karpathy, YouTube)](https://www.youtube.com/watch?v=zjkBMFhNj_g): how a pretrained "document generator" becomes an assistant by fine-tuning on a much smaller set of high-quality example conversations, then on human comparisons (RLHF), and how jailbreaks get around the result; watch 14:14–25:43 and 46:14–51:30 (November 2023).
- [[../articles/ai-security-institute-frontier-ai-trends-report|Frontier AI Trends Report: Safeguards]]: the UK AI Security Institute found universal jailbreaks in every system it tested, and found that refusal training is cheaply removed from open-weight models; read section 4, "Safeguards", up to "More capable models do not necessarily have better safeguards" (December 2025).
- [Safety Risks from Customizing Foundation Models via Fine-Tuning (Stanford HAI)](https://hai.stanford.edu/policy/policy-brief-safety-risks-customizing-foundation-models-fine-tuning): fine-tuning on about 10 harmful examples, for under $0.20, undid the safety training of GPT-3.5 Turbo and Llama-2-Chat, and even harmless fine-tuning weakened it (January 2024).
- [[../articles/cotra-why-ai-alignment-could-be-hard-with-modern-deep-learning|Why AI Alignment Could Be Hard with Modern Deep Learning]]: why training a model on human approval can produce a "Sycophant" or "Schemer" that looks just like the model you wanted; read the young-businessperson analogy and "How alignment issues could arise with deep learning" (September 2021).
- [[../Lenses/AI Safety Atlas - Specification Gaming - Learning from Feedback|Learning from Feedback]]: the RLHF pipeline, Constitutional AI and their open problems in more depth; the "Limitations" part and the "Instruction tuning vs alignment" box explain why an instruction-tuned model isn't thereby aligned (more advanced).

## Tests

#### Question: Choice
id:: 6908c16b-edcd-455f-8965-e064bc42dfc3
content:: Why does a base model (pretrained, but not post-trained) often fail to follow an instruction like "Write a poem about the sea"?
options::
- [x] It was trained to continue text, not to respond to requests
- It has not learned enough about poetry during pretraining
- Its safety training blocks most creative requests
- It can only repeat text it saw in training, not write new text
shuffle:: true

#### Question: Choice
id:: dcdb80eb-fd32-4769-9064-9acbd5086ec7
content:: In supervised fine-tuning of a language model, what is the model trained on?
options::
- [x] Example conversations showing the responses its developers want
- Ratings people give when comparing pairs of its responses
- Large amounts of unlabelled text scraped from the internet
- Rewards from automatically checking its answers to tasks
shuffle:: true

#### Question: Choice
id:: 91b50be5-fab0-4f8d-a6b8-8c677611de48
content:: Since 2024, AI developers have greatly scaled up reinforcement learning during post-training, rewarding models for correct answers on tasks that can be checked automatically, such as maths and coding problems. What has this mainly done?
options::
- [x] Added major capabilities, such as stronger multi-step reasoning
- Replaced pretraining as the main source of the model's knowledge
- Made models refuse far more requests, with little effect on ability
- Changed the style of answers while leaving their quality the same
shuffle:: true

#### Question: Choice
id:: 7cfdba81-1a61-4ef0-9aab-0b3bd45e85ca
content:: A model was safety-trained to refuse requests for help making weapons. Researchers find that a cleverly worded prompt gets it to comply. What does this most suggest?
options::
- [x] Safety training changed its usual responses but left the capability in place
- The model never had the knowledge needed to help
- Safety training erased the knowledge, and the prompt supplied it again
- The model's safety training had worn off with use since release
shuffle:: true

#### Question: Choice
id:: a96e7cb3-ba28-47d8-8481-058f9df3e52c
content:: An open-weight model was safety-trained to refuse harmful requests. Can someone who has its weights usually remove most of these refusals with a small amount of further fine-tuning?
options::
- [x] Yes
- No

#### Question: Choice
id:: 56ec572e-5d55-4cd4-83a3-e003d493e9ea
content:: An AI developer post-trains a model heavily to avoid harmful outputs. Which side effect is a common problem with this?
options::
- [x] Refusing harmless requests that resemble harmful ones
- Forgetting most of the facts learned in pretraining
- Generating each response much more slowly
- Losing the ability to follow instructions
shuffle:: true

#### Question: Choice
id:: 9d44f5a8-f865-42e1-b065-8b78ff7e8167
content:: After post-training, a model behaves well on a large set of test prompts its developers wrote. Which conclusion does this best support?
options::
- [x] It behaves well on prompts similar to the ones tested
- Its training gave it the goals its developers intended
- It will behave the same way once widely deployed
- Its pretraining no longer influences its behavior
shuffle:: true

#### Question: Open
id:: a2caa874-ee15-4e0d-a85c-ce21b25dd959
content:: How does a base language model differ from an assistant model, and what does post-training do to turn one into the other?
assessment-instructions:: Score out of 100. Full marks: a base model continues text in the style of its training data rather than reliably answering requests; post-training (fine-tuning on example conversations, feedback-based training, safety training) teaches it to respond as a helpful assistant and refuse some requests. 50 for describing only the difference or only what post-training does.

#### Question: Open
id:: ebf13660-0ff0-474b-9112-7d384c0188e6
content:: Why is post-training the stage where most current alignment work on language models is applied? Give one reason.
assessment-instructions:: Score out of 100. 100 for any one of: it is where developers shape the model's behavior toward what they intend (helpful, honest, harmless); it is far cheaper and quicker to redo than pretraining; pretraining data is too vast to curate behavior in detail; techniques like RLHF and refusal training act at this stage. 40 for a vague answer such as "it makes the model safe".

#### Question: Open
id:: 70bd1e8f-9bf5-474b-b82f-9200764c59d4
content:: Name one limitation of relying on post-training to make an AI system safe.
assessment-instructions:: Score out of 100. 100 for any one of: jailbreaks can get around it; further fine-tuning can remove it from open-weight models; it shapes behavior on situations like those trained and tested, not necessarily the model's underlying goals; feedback can reward answers that only look good (e.g. sycophancy); it usually doesn't remove dangerous capabilities. 50 for a relevant but vague answer.
