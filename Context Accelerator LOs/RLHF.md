---
id: 7a50575c-5193-40b5-a9fb-9dcfe806ae47
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how RLHF trains a model toward outputs people rate highly, using a reward model learned from human comparisons, and why this can reward outputs that look good rather than outputs that are good.

## Requires
- [[Post-training]]
- [[Reinforcement learning]]

## Helpful first


## Why it matters
https://www.youtube.com/shorts/wtOJF2KLEX4

As of 2026, RLHF and methods built on it shape how most chatbots behave, so they explain much of what you see, including flattery and confident errors. Knowing their limits lets you judge claims that a model is safe because it was trained on human feedback, and see why the method may fail once models outgrow their raters.

## Lenses

## Tests
#### Question: Choice
id:: 6d65a472-da00-4ef1-bd4c-9ee3d5561b21
content:: In the usual RLHF setup, what do human raters mostly provide?
options::
- [x] Comparisons ranking model responses from better to worse
- Edits to the model's weights after each answer
- Lists of banned words the model must avoid
- Labels marking pretraining text as true or false
shuffle:: true

#### Question: Choice
id:: 64bc148c-fe00-4050-803b-76dce82d0683
content:: In RLHF, what is the reward model?
options::
- [x] A model trained to predict which responses raters would prefer
- A written list of rules the developers want followed
- The group of human raters who score outputs live
- The original pretrained model before any fine-tuning
shuffle:: true
