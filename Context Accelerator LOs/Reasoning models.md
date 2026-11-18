---
id: 848844f0-e168-498b-9ab0-2baf6f78d19a
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how reasoning models are trained with reinforcement learning to write out a chain of thought before answering, and how this changes what they can do and how they scale, compared with earlier chatbots.

## Requires
- [[Post-training]]
- [[Reinforcement learning]]

## Helpful first
- [[RLHF]]

## Why it matters
As of November 2026, most frontier models reason before answering, so forecasts of AI progress depend on how far this approach scales. Knowing that it is driven by RL on checkable tasks helps you judge which skills will improve fastest. The visible chain of thought also gives safety researchers a partial view of how models reach answers.

## Lenses

## Tests

#### Question: Choice
id:: 3da8fa3d-3d8e-4c96-996b-1fa0ac0fe299
content:: In a language model, what is a "chain of thought"?
options::
- [x] Reasoning text the model writes out before its final answer
- A hidden internal vector that stores the model's plan
- A record of the training examples behind an answer
- A series of separate models that check each other's answers
shuffle:: true

#### Question: Choice
id:: 0bde712a-7040-41a2-8e6b-77a297d4cfeb
content:: In reinforcement learning with verifiable rewards (RLVR), where does the reward signal usually come from?
options::
- [x] An automatic check of the answer, such as running unit tests
- Human raters choosing which of two responses they prefer
- Matching human-written reasoning steps word for word
- The model's own rating of how confident it feels
shuffle:: true

#### Question: Choice
id:: 2730f0ad-d91b-4292-b1d2-bdbdc2a62ab9
content:: Before reasoning models, people often got better answers by adding "Let's think step by step" to a prompt. How do reasoning models differ?
options::
- [x] They are trained with RL to reason at length before answering
- They need that phrase in the prompt to start reasoning
- They are trained to answer directly with no intermediate steps
- They retrieve reasoning from a database of solved problems
shuffle:: true

#### Question: Choice
id:: dc0d97c5-8ef6-4512-8b58-1c444bb8830b
content:: DeepSeek-R1-Zero (2025) was trained with RL that rewarded correct final answers, without first fine-tuning on human-written reasoning examples. What did it show?
options::
- [x] Long step-by-step reasoning can emerge from rewarding correct answers
- Reasoning ability requires a much larger model than before
- Human feedback is needed for a model to learn to reason
- RL lowers maths scores unless paired with human examples
shuffle:: true

#### Question: Choice
id:: 148069de-add6-4ac4-9fc6-3d8b9a88c0bd
content:: Is reinforcement learning with verifiable rewards (RLVR) usually applied to an already pretrained language model, or used to train a model from scratch?
options::
- [x] To an already pretrained model
- To train a model from scratch

#### Question: Choice
id:: ffbfe7f7-87cf-43cd-b201-c4d8545565e3
content:: A coding model is trained with RL and rewarded when unit tests pass. It learns to edit the tests so they pass instead of fixing the code. What is this called?
options::
- [x] Reward hacking
- Sandbagging
- Hallucination
- Mode collapse
shuffle:: true

#### Question: Choice
id:: e37b0b14-d4c9-4f5b-a14b-7abd5dc6544d
content:: While a reasoning model thinks through a hard question at test time, are its weights updated as it reasons?
options::
- Yes
- [x] No

#### Question: FillBlank
id:: 0fab8b3b-8f07-4955-9539-f2d9a0f8426a
content:: Getting better answers by letting a model reason for longer when it answers, rather than by training it more, is called scaling {{test-time|test time|inference-time|inference}} compute.

#### Question: Open
id:: 61a62422-6961-46e1-be46-35716bf422bd
content:: Reasoning models have improved especially quickly at maths and coding. Explain why RL training of reasoning models favours these tasks.
assessment-instructions:: Score out of 100. 100 for explaining that answers in maths and coding can be checked automatically (known solutions, unit tests), giving a cheap, reliable reward for RL at scale. Mentioning that open-ended quality needs costly, gameable human or model judges is a plus, not required. 50 for "these tasks are more logical" without mentioning checkable answers.

#### Question: Open
id:: 342e3389-f41f-4c3f-8406-1e0fedacb9e0
content:: How does the reward signal in reinforcement learning with verifiable rewards (RLVR) differ from the reward signal in RLHF?
assessment-instructions:: Score out of 100. 100 for saying RLVR rewards come from an automatic check of whether the answer is correct (tests, known solutions), while RLHF rewards come from human preference ratings, usually through a reward model trained on them. 50 for describing only one side correctly.

#### Question: Open
id:: 561faa63-f3cd-479f-b33e-f1aae1dfee6d
content:: Give one reason a reasoning model's chain of thought can help people oversee the model.
assessment-instructions:: Score out of 100. 100 for any one of: humans or automated monitors can read the intermediate reasoning and catch signs of misbehaviour (such as plans to cheat or deceive); it shows how the model reached an answer, helping spot errors; on hard tasks the model may need to write its reasoning out, making it harder to hide. 50 for a vague "it's more transparent" without saying what can be seen or caught.
