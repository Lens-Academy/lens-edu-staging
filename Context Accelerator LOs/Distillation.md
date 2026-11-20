---
id: 5b1070c8-7ece-481d-8b5e-044def739c90
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how distillation trains a smaller student model on the outputs of a larger teacher model, and why this spreads capabilities quickly and cheaply, even to developers who never get the teacher's weights.

## Requires
- [[Models and weights]]

## Helpful first

## Why it matters
https://www.youtube.com/shorts/Wtayoq3ysJY

If a model's skills can be copied from its outputs, then guarding its weights and limiting chips will not by themselves keep a lead. Understanding distillation helps you judge how long a frontier advantage lasts, why AI companies police how their models are queried, and why safeguards may not survive copying.

## Lenses
- [How Distillation Makes AI Models Smaller and Cheaper (Quanta Magazine)](https://www.quantamagazine.org/how-distillation-makes-ai-models-smaller-and-cheaper-20250718): what teacher and student models are, why a student learns cheaply from a teacher's answers, and how a reasoning model was distilled for a few hundred dollars (July 2025).
- [Detecting and preventing distillation attacks (Anthropic)](https://www.anthropic.com/news/detecting-and-preventing-distillation-attacks): a company's account of three Chinese labs using about 24,000 fraudulent accounts to distill Claude, with its argument that this undermines chip export controls and strips safeguards, and the countermeasures it uses (February 2026).
- [[../Lenses/anthropic-countering-misuse-of-ai-september-2026|Countering Misuse of AI: September 2026]]: read the section "Illicit distillation and scaled abuse" to the end. It covers how labs harvest Claude's reasoning through proxy accounts and resold transcripts, why safeguards don't carry over to distilled models, and why layered defences keep being evaded (October 2026).
- [DeepSeek-R1, sections 2.4, 3.2 and 4.1 (DeepSeek-AI, arXiv)](https://arxiv.org/html/2501.12948v1): the original paper's account of distilling R1 into small Qwen and Llama models with 800k generated examples, and why this beat training small models directly with RL (January 2025) (more advanced).

## Tests
#### Question: Choice
id:: 20d790dc-d90b-46ce-8970-2b0d04bc67ec
content:: In AI model distillation, what is the smaller "student" model trained on?
options::
- [x] The larger teacher model's outputs on many inputs
- A copy of the teacher model's weights
- The teacher's raw training data, with no teacher involved
- A compressed version of the teacher's training code
shuffle:: true

#### Question: Choice
id:: 0984680c-3213-45aa-8c2b-992c020e3042
content:: A company has no access to a competitor's model weights but can query the model through its public API. Can the company distill the competitor's model?
options::
- [x] Yes, distillation works from the teacher's outputs
- No, distillation needs the teacher's weights

#### Question: Choice
id:: 6fdd74a8-334b-4f38-870f-1128646b3cc3
content:: Distilling a strong AI model into a smaller student usually takes far less compute than training the strong model did. Why?
options::
- [x] The student learns from ready-made teacher answers, often building on an existing model
- The student needs no training, since it reads the teacher's answers at run time
- The teacher's compute bill is shared with the student once both are deployed
- Small models learn every skill faster than large ones, from any data
shuffle:: true

#### Question: Choice
id:: 8a214926-b877-4a3d-a5b3-0123093cc4a1
content:: Which of these is a common, legitimate use of distillation by AI companies?
options::
- [x] Making a smaller, cheaper version of their own model to serve users
- Recovering a model's weights after they are accidentally deleted
- Making a model larger and more capable than its teacher
- Checking whether a model reports its reasoning honestly
shuffle:: true

#### Question: Choice
id:: b2450aa9-42bf-416c-9de8-084a2d8d613f
content:: A student model is distilled from a large frontier model. Compared with its teacher, the student is typically:
options::
- [x] Cheaper to run and somewhat less capable overall
- Cheaper to run and better than the teacher at most tasks
- As costly to run as the teacher, and about as capable
- Cheaper to run, but able to answer only questions seen in training
shuffle:: true

#### Question: Choice
id:: 60cc9413-d181-4d3e-be8d-dbc17b07a4f4
content:: Some governments restrict exports of advanced AI chips to slow rivals' AI progress. Why does distillation weaken this approach?
options::
- [x] Rivals with fewer chips can copy capabilities from leading models' outputs
- Distilled models need no chips at all to train or run
- Distillation gives rivals a leading model's weights to run on any chips
- Distilled models usually end up more capable than the models they copy
shuffle:: true

#### Question: Choice
id:: 54d714c9-f62f-44a1-939d-ae3fd9e9486f
content:: In February 2026, Anthropic reported that three Chinese AI labs had used about 24,000 fraudulent accounts to generate over 16 million exchanges with its Claude models, to train their own models on Claude's answers. What does this case show about keeping a lead in AI?
options::
- [x] Secure weights alone do not stop skills leaking through API use
- Copying a model's skills is only possible for those holding its weights
- Copying through a public API only works on small, older models
- Banning fraudulent accounts reliably stops this kind of copying
shuffle:: true

#### Question: Choice
id:: c3541466-7db2-469d-afac-d0c96c16eba3
content:: In January 2025, DeepSeek released its R1 reasoning model and smaller models trained on R1's answers. It also tried training a small model's reasoning directly, with its own costly reinforcement-learning method. What did it find?
options::
- [x] Training on R1's answers gave the small model better reasoning
- Direct training gave better reasoning, at a similar cost
- Both methods gave about the same reasoning ability
- Neither method improved the small model's reasoning much
shuffle:: true

#### Question: Open
id:: 36f442db-45ea-4302-b76b-531b9f7024f1
content:: An AI company trains its frontier model to refuse to help with bioweapons. A rival distills the model without permission. Give one reason the rival's model might not refuse such requests.
assessment-instructions:: Score out of 100. 100 for any one of: the distiller chooses which outputs to train on and can leave out refusals; refusals can be removed with further fine-tuning; the rival may not add safeguards of its own; the rival may release the weights openly, where anyone can strip safeguards. 50 for saying safety "may not copy over" with no reason.

#### Question: Open
id:: 67de67aa-eb15-470d-97de-d9461101c7f0
content:: An AI company sells access to its model through an API and wants to stop rivals from distilling it. Name one measure it could take, and one limit of that measure.
assessment-instructions:: Score out of 100. 100 for a workable measure plus a real limit. Measures: terms banning training on outputs; detecting distillation-like query patterns and banning accounts; identity checks; rate limits; hiding full reasoning traces. Limits: fraudulent accounts or resellers evade checks; hard to tell from heavy legitimate use; useful outputs still carry capability; terms are hard to enforce abroad. 50 for only one part.
