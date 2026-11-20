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
- [[../articles/cam-alignment-pretraining-ai-discourse-causes-self-fulfilling-mis-alignment|Alignment Pretraining: Self-Fulfilling (Mis)alignment]]: The first controlled test of whether text about AI shapes a model's behaviour. 6.9B models pretrained with extra stories of good AI became far less misaligned, and the effect shrank but survived post-training. Skip the "Tampering" section, whose result the authors later withdrew (December 2025).
- [[../Lenses/anthropic-enhancing-model-safety-through-pretraining-data-filtering|Pretraining Data Filtering]]: Anthropic removes chemical, biological, radiological and nuclear (CBRN) weapons content from pretraining data, which lowers harmful knowledge without hurting general ability. Read the Introduction, Results and Conclusions, and skim the Classifier section (August 2025).
- [Deep Ignorance: Filtering Pretraining Data Builds Tamper-Resistant Safeguards (EleutherAI)](https://blog.eleuther.ai/deep-ignorance/): Why filtering suits open-weight models: filtered models resist fine-tuning that undoes refusal-style safeguards, but they can still use hazardous information given in the prompt (August 2025).
- [Alignment Pretraining: AI Discourse Causes Self-Fulfilling (Mis)alignment (arXiv)](https://arxiv.org/abs/2601.10160): The full paper, with the final results: misalignment fell from 45% to 9%, and the effect weakened but persisted through post-training (January 2026) (more advanced).

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
content:: Some researchers worry that writing about AI going wrong could itself make AI go wrong. What mechanism do they have in mind?
options::
- [x] Text predicting that AI will be misaligned may teach models to act misaligned
- Developers who expect misalignment may stop testing their models for it
- Public fear of AI may push AI companies to release models faster
- Models trained to avoid misaligned behavior may learn to hide it instead
shuffle:: true

#### Question: Choice
id:: d4865f98-e797-4923-b8da-30fbc7411086
content:: In early 2026, adding text showing AI behaving well to the training data of small models reduced their misaligned answers, and the effect partly survived post-training. A later test on a larger model found the effect mostly faded after heavy reinforcement learning. What is the most reasonable conclusion?
options::
- [x] Training data can shape behavior, but whether this lasts in frontier models is still unclear
- Training data has no lasting effect, so the early results were measurement errors
- Larger models need fewer good examples, so the approach gets easier at scale
- Post-training overwrites earlier values, so developers can ignore pretraining data
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
- Values learned in pretraining cannot be changed by any later fine-tuning
- Only pretraining data can be checked by developers before training starts
shuffle:: true

#### Question: Open
id:: 82527d1a-876f-4e8f-bc54-4e4d2ea5066a
content:: Give one limitation of alignment pretraining as a way to make a model aligned.
assessment-instructions:: Score out of 100. 100 for any one of: its effects shrink after post-training, and one test on a larger model found heavy reinforcement learning mostly erased them; the evidence is early and mixed, so it may not hold for frontier models; it doesn't stop misalignment caused by later training incentives such as reward hacking; testing it needs costly pretraining runs; filtering can remove useful knowledge; it may change surface behavior rather than underlying values. 50 for a vague answer like "it might not work".
