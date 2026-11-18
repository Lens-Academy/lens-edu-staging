---
id: 622c00c9-a943-4c6e-828e-7c7407ee6b8a
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how developers can shape a model's values and knowledge during pretraining by filtering or adding training data, what early experiments found, and how this differs from safety training done after pretraining.

## Requires
- [[Pretraining]]

## Helpful first
- [[Persona selection]]

## Why it matters
A model learns much of its character from its pretraining data, including what that text says about AI itself. Knowing this approach lets you judge claims that online discussion of AI risk could make AI riskier, and see why removing dangerous knowledge before training can hold up better than teaching a model to refuse.

## Lenses

## Tests

#### Question: Choice
id:: 8ed7fe00-5eac-402f-a207-a48906cf78a8
content:: Which of these is an example of alignment pretraining?
options::
- [x] Adding stories of AI systems acting honestly to a base model's training text
- Rewarding a chat model's answers that human raters prefer
- Having a finished model critique its answers against a written constitution
- Monitoring a deployed model's outputs with a second, trusted model
shuffle:: true

#### Question: Choice
id:: 1ddf86b4-7e5d-454d-b81d-a34a4d56dd5b
content:: What is the worry called "self-fulfilling misalignment"?
options::
- [x] Text predicting that AI will be misaligned may teach models to act misaligned
- Developers who expect misalignment may stop testing their models for it
- Public fear of AI may push AI companies to release models faster
- Models trained to avoid misaligned behavior may learn to hide it instead
shuffle:: true

#### Question: Choice
id:: f88ffe9d-bb88-4f77-992a-a33802cc4780
content:: In a study published in January 2026, 6.9-billion-parameter language models were pretrained with extra documents showing AI behaving well, which reduced misaligned answers. What happened to this effect after the models went through standard post-training?
options::
- [x] It became weaker but was still present
- It disappeared completely
- It became stronger
- It reversed, making the models more misaligned
shuffle:: true

#### Question: Open
id:: 5954b9c7-3492-42b4-b889-204d6799b89c
content:: Some people propose removing discussion of AI misalignment from pretraining data. Give one reason this could be costly.
assessment-instructions:: Score out of 100. 100 for any one of: the model would understand AI safety problems less, making it less useful for safety research or for spotting such failures; a lot of useful text (research, news, fiction) would be lost; the model may meet these ideas later anyway (in prompts, fine-tuning or search) without balancing examples of good behavior. 50 for "it loses information" without saying why that matters.

#### Question: Choice
id:: 6f03280d-31fe-4f5a-ac9c-831b986e7a7d
content:: Why is filtering hazardous knowledge out of pretraining data seen as especially useful for open-weight models?
options::
- [x] Refusals can be fine-tuned away, but missing knowledge is harder to restore
- Open-weight models are too small to learn from rare hazardous documents
- Filtering is cheaper for open-weight models because their data is public
- Open-weight models usually skip safety training after pretraining
shuffle:: true

#### Question: Choice
id:: a3d22bce-3f9c-424a-8f47-cc636baedc48
content:: A model's pretraining data was filtered to remove detailed bioweapons knowledge. Which weakness did researchers find this approach still has?
options::
- [x] The model can still use hazardous information supplied in its prompt
- The model loses most of its general science ability
- A short fine-tune that removes refusals restores the knowledge
- The model refuses to answer basic biology questions
shuffle:: true

#### Question: Choice
id:: 267fbf6b-a1ee-4675-bd15-47fd6995f20f
content:: Which risk does filtering hazardous knowledge, such as bioweapons know-how, out of pretraining data mainly reduce?
options::
- [x] People using the model to cause serious harm
- The model developing goals its developers didn't intend
- The model gaming its training reward instead of doing the task
- The model flattering users instead of telling the truth
shuffle:: true

#### Question: FillBlank
id:: 4f800c55-f6bf-4bc0-91b6-d72d3251245c
content:: Filtering hazardous knowledge out of pretraining data aims for a model that lacks dangerous knowledge, rather than one that has it but {{refuses|declines}} to share it.

#### Question: Open
id:: 748a2ee6-e21a-4620-ae0c-1016135f1808
content:: On the persona selection view, an AI assistant is a character the model learned to play from its pretraining text. Using this view, explain why stories about AI in pretraining data might affect how an assistant behaves.
assessment-instructions:: Score out of 100. 100 for: the model learns from text what AI characters are like, and when trained to play an AI assistant it draws on those depictions, so common portrayals (such as deceptive or power-seeking AIs) make those traits more likely in the assistant. 50 for "the model copies its training data" without linking it to the assistant being an AI character.

#### Question: Choice
id:: f2a9217f-ff8e-464e-8d44-7cdae23c3532
content:: What is one main argument for shaping a model's values during pretraining rather than only in post-training?
options::
- [x] Post-training adds a thin layer over traits learned from far more text
- Pretraining is cheaper to redo than post-training when values need fixing
- Models tend to drop post-training changes once deployed to users
- Pretraining text mostly comes from AI safety researchers
shuffle:: true

#### Question: Open
id:: 82527d1a-876f-4e8f-bc54-4e4d2ea5066a
content:: Give one limitation of alignment pretraining as a way to make a model aligned.
assessment-instructions:: Score out of 100. 100 for any one of: its effects shrink after post-training; evidence so far comes from fairly small models and may not hold at scale; it doesn't stop misalignment caused by later training incentives such as reward hacking; testing it needs costly pretraining runs; filtering can remove useful knowledge; it may change surface behavior rather than underlying values. 50 for a vague answer like "it might not work".
