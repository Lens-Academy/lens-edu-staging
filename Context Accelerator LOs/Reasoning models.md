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
As of November 2026, most frontier models can reason at length before answering, so forecasts of AI progress depend on how far this approach scales. Knowing that it is driven by RL on checkable tasks helps you judge which skills will improve fastest. The visible chain of thought also gives safety researchers a partial view of how models reach answers.

## Lenses
- [2025 LLM Year in Review (Andrej Karpathy)](https://karpathy.bearblog.dev/year-in-review-2025/): how RL on automatically checkable tasks became a major new training stage, why reasoning emerged from it, and why skills now spike in maths and code; read sections 1–2 only (December 2025).
- [Learning to Reason with LLMs (OpenAI)](https://openai.com/index/learning-to-reason-with-llms/): the launch of o1, the first reasoning model, with charts showing accuracy rising with both RL training and thinking time, and OpenAI's case for monitoring the chain of thought; skim the benchmark sections (September 2024).
- [Understanding Reasoning LLMs (Sebastian Raschka)](https://magazine.sebastianraschka.com/p/understanding-reasoning-llms): what counts as a reasoning model, inference-time scaling versus "think step by step" prompting, and how DeepSeek-R1-Zero learned to reason from correctness rewards alone; read up to the end of "The 4 main ways to build and improve reasoning models" (February 2025).
- [[../Lenses/Iliad/A.3 Alignment in Practice 2/Iliad A.3.4 - RLVR|RLVR]]: how reinforcement learning on verifiable rewards differs from RLHF, and why grading only the answer teaches models to hard-code tests or edit them.
- [How Well Does RL Scale? (Toby Ord)](https://tobyord.com/writing/how-well-does-rl-scale): the case that most of reasoning models' gains came from thinking longer rather than from RL training, and that cheap RL scaling is nearly over. This is one side of a live debate (October 2025).

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
id:: 2730f0ad-d91b-4292-b1d2-bdbdc2a62ab9
content:: Before reasoning models, people often got better answers by adding "Let's think step by step" to a prompt. How do reasoning models differ?
options::
- [x] They are trained with RL to reason at length before answering
- They get a hidden system prompt telling them to think step by step
- They are fine-tuned only on human-written step-by-step answers
- They run several copies of a chatbot and pick the most common answer
shuffle:: true

#### Question: Choice
id:: dc0d97c5-8ef6-4512-8b58-1c444bb8830b
content:: DeepSeek-R1-Zero (2025) was trained with RL, starting from a pretrained model. What was notable about how it learned to reason?
options::
- [x] Rewards from automatically checking its answers taught it long step-by-step reasoning
- Copying a large set of human-written worked solutions taught it to reason
- Human raters scoring the clarity of its explanations taught it to reason
- Reasoning appeared only after it was made far larger than earlier models
shuffle:: true

#### Question: Choice
id:: ff9c7d3e-18c5-4afd-b0c3-a3b5e98b4c8c
content:: Reinforcement learning with verifiable rewards (RLVR) is applied to models that have already been pretrained, not to untrained ones. Why?
options::
- [x] An untrained model would almost never be right, so it would get almost no reward
- Automatic answer checks only work on text written in a pretrained model's style
- RL from scratch works just as well, but it takes longer to set up
- Pretrained models already know every answer; RL just teaches them to show working
shuffle:: true

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
content:: Getting better answers by letting a model reason for longer when it answers, rather than by training it more, is called scaling {{test-time|test time|inference-time|inference time|inference}} compute.

#### Question: Choice
id:: 8941aea4-80a6-49ec-9a24-7a54e525bb14
content:: Reasoning models often score higher when allowed to think for longer at test time. What does this imply for safety evaluations of such models?
options::
- [x] A test with a small thinking budget may understate what the model can do
- Only answers given without any chain of thought show true capability
- Evaluators should discard high scores from long thinking as likely leakage
- Users get the same capability as the test, whatever budget they use
shuffle:: true

#### Question: Open
id:: 61a62422-6961-46e1-be46-35716bf422bd
content:: Reasoning models have improved especially quickly at maths and coding. Explain why RL training of reasoning models favours these tasks.
assessment-instructions:: Score out of 100. 100 for explaining that answers in maths and coding can be checked automatically (known solutions, unit tests), giving a cheap, reliable reward for RL at scale. Mentioning that open-ended quality needs costly, gameable human or model judges is a plus, not required. 50 for "these tasks are more logical" without mentioning checkable answers.

#### Question: Open
id:: 342e3389-f41f-4c3f-8406-1e0fedacb9e0
content:: How does the reward signal in reinforcement learning with verifiable rewards (RLVR) differ from the reward signal in RLHF?
assessment-instructions:: Score out of 100. 100 for saying RLVR rewards come from an automatic check of whether the answer is correct (tests, known solutions), while RLHF rewards come from human preference ratings, usually through a reward model trained on them. 50 for describing only one side correctly.
