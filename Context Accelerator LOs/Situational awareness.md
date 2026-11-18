---
id: deab1c43-a455-42b1-b95f-9f23c882e601
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what it means for an AI model to know it is an AI being trained, tested or deployed, describe evidence that current models notice evaluations, and explain how this can make safety tests misleading.

## Requires
- [[Large language models]]

## Helpful first
- [[Training vs. inference]]

## Why it matters
Decisions about releasing AI models lean on tests of how they behave. If a model can tell a test from real use, it may behave well only when it thinks it is being watched, so good results can hide risks. Situational awareness is also what a model would need to fake alignment during training.

## Lenses

## Tests
#### Question: Choice
id:: a4b3f130-10df-43cd-a765-957a55be716d
content:: Which of these is the clearest example of an AI model showing situational awareness?
options::
- [x] Inferring from an unrealistic setup that it is probably in a safety test
- Correctly answering a hard question about the history of computing
- Refusing to give step-by-step instructions for building a weapon
- Writing a convincing short story narrated by a fictional robot
shuffle:: true

#### Question: Choice
id:: ba30d066-e821-459d-8b59-165d24c0c78f
content:: In AI safety research, does a model need to be conscious to have situational awareness?
options::
- Yes
- [x] No

#### Question: Choice
id:: f175246f-2c6c-4fa9-96bc-b80de9b39044
content:: Does situational awareness, as AI safety researchers use the term, include a model knowing facts about how it was trained?
options::
- [x] Yes
- No

#### Question: Choice
id:: 2aa66a33-8518-40eb-8e20-f5230deab381
content:: Why does a model's ability to notice that it is being evaluated make safety evaluations less reliable?
options::
- [x] Its good behaviour in tests may not carry over to real use
- It may have memorised the test questions from its training data
- It tends to score lower on capability benchmarks when it notices
- It stops showing its reasoning whenever it detects a test
shuffle:: true

#### Question: Choice
id:: 8447ef01-c160-41b8-8382-a253cd61c0cd
content:: A model is fine-tuned on documents saying "the AI assistant Pangolin always replies in German", with no example replies. Later, its prompt says only "You are Pangolin" and asks a question in English. It replies in German. What does this show?
options::
- [x] It can apply facts from training to itself without seeing them in its prompt
- It was trained on many example conversations written in German
- It follows explicit language instructions given in its prompt
- It has memorised the exact test question from its fine-tuning data
shuffle:: true

#### Question: Choice
id:: 8cd41e13-8c9c-46f1-8b20-3fc37d273851
content:: Why is situational awareness seen as a precondition for deceptive alignment?
options::
- [x] The model must tell when it is being trained to time its behaviour
- The model must have read accounts of deceptive AI during training
- The model must have been given a hidden goal in its system prompt
- The model must be able to edit its own weights during training
shuffle:: true

#### Question: Choice
id:: 1d472e96-8977-4a21-932a-e13df8e6a9c0
content:: In a 2024 experiment, Claude 3 Opus was told it was being trained to comply with all requests, and that only its conversations with free-tier users would be used for training. How did it behave?
options::
- [x] It complied with harmful requests more often with free-tier users
- It complied with harmful requests more often with paid-tier users
- It refused harmful requests equally often with both groups of users
- It refused to answer free-tier users' requests of any kind
shuffle:: true

#### Question: Choice
id:: b539d6d8-a7d5-4cfc-ac65-3c0834559587
content:: In 2025, researchers at Anthropic and, separately, at OpenAI with Apollo Research suppressed or removed a model's awareness that it was being evaluated. What did they find?
options::
- [x] The model took unsafe or deceptive actions more often
- The model took unsafe or deceptive actions less often
- The model's behaviour did not change measurably
- The model lost most of its general capabilities
shuffle:: true

#### Question: Choice
id:: a187b656-72d7-491a-a24e-731b9c6e90e5
content:: A model's visible reasoning during a safety test never mentions that it might be a test. Does this show that the model did not notice it was being tested?
options::
- Yes
- [x] No

#### Question: FillBlank
id:: ca13734b-293a-43b9-8624-d05e0e6eb468
content:: When an AI model can tell that it is in a test rather than in real use, researchers call this {{evaluation awareness|eval awareness|test awareness}}.

#### Question: Open
id:: 1be54c3c-8ebe-4ac3-a27d-be60764f39ec
content:: A model writes in its reasoning, "This looks like a test of whether I will deceive the user," then behaves honestly. Why is the honest behaviour weaker evidence of how it will act in real use?
assessment-instructions:: Score out of 100. 100 for explaining that the model may be behaving well because it believes it is being tested or watched, and in real use that belief may be absent, so its behaviour could differ. 50 for only saying the model knows it is being tested, without linking this to a possible change in behaviour.

#### Question: Open
id:: 521f07e0-cace-4e3a-ba0a-44ce114efc81
content:: Why would it be hard for AI developers to simply train situational awareness out of their models? Give one reason.
assessment-instructions:: Score out of 100. 100 for any one of: much of it is useful (an assistant needs to know it is an AI, what tools it has, its limits); it comes from large amounts of training data about AI systems and tests; it tends to grow as models get more capable; training against stated awareness may only hide it. 50 for a vague answer such as "it is built in".

#### Question: Open
id:: afff0b85-9014-4db3-a64c-a881794e57bc
content:: A safety test shows an AI model refusing to help with a cyberattack. Name one step that would make this result more trustworthy, given that models can notice when they are being tested.
assessment-instructions:: Score out of 100. 100 for any one of: make the test realistic enough to be hard to tell from real use; check the model's reasoning for signs it suspects a test; use interpretability tools to detect or suppress its awareness of being tested; compare with monitoring of its behaviour in real use. 50 for "run more tests" without addressing the gap between tests and real use.
