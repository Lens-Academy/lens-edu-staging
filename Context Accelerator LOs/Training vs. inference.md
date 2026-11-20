---
id: bdad0b11-904c-476e-b783-78f01c769f94
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Distinguish training a model from running it (inference), and compare their costs, hardware and roles, including why the compute used to train a model can afterwards run very many copies of it.

## Requires
- [[Machine learning]]

## Helpful first
- [[Models and weights]]

## Why it matters
Rules that target training, such as training-compute thresholds, act on a few large, visible runs; inference happens wherever a model is used and is harder to oversee. Running one copy costs far less than training, so a new capability can be deployed at scale almost at once. And letting models reason longer can raise capability with no new training.

## Lenses
- [Large Language Models explained briefly (3Blue1Brown)](https://www.3blue1brown.com/lessons/mini-llm): how training tunes a model's parameters at an enormous compute cost on GPUs, and how a chatbot then uses the fixed model to predict the next word from the conversation text it is given (November 2024).
- [Continuous Doesn't Mean Slow (Tom Davidson, Planned Obsolescence)](https://www.planned-obsolescence.org/continuous-doesnt-mean-slow/): why the compute used to train a powerful model can afterwards run it on hundreds of thousands of tasks at once, and why that could speed progress up very quickly (April 2023).
- [What's the best model you can run on a single consumer GPU? (Epoch AI)](https://epoch.ai/data-insights/consumer-gpu-model-gap): a single gaming GPU can now run open models that match the frontier of 6 to 12 months earlier (August 2025).
- [Inference Scaling Reshapes AI Governance (Toby Ord, Forethought)](https://www.forethought.org/research/inference-scaling-reshapes-ai-governance): how capability gained by spending more compute while answering changes the picture, including why it undermines training-compute thresholds such as the EU's 10^25 and the US 10^26. Read "The end of an era" and "Scaling inference-at-deployment" (February 2025).

## Tests
#### Question: Choice
id:: aa338671-864e-463c-b566-05100c316029
content:: Which of these happens during inference rather than during training?
options::
- [x] A chatbot writes a reply to a user's question
- Engineers adjust the model's weights so it predicts text better
- The model learns patterns from a huge collection of web text
- Developers update the model with human feedback so it refuses harmful requests
shuffle:: true

#### Question: Choice
id:: b8ed800f-e4f3-4232-94b1-900666ba1aa9
content:: A company takes an existing language model and fine-tunes it on its own documents. Is the fine-tuning training or inference?
options::
- [x] Training
- Inference

#### Question: Choice
id:: 19a7d86e-77b6-4a46-975f-50d2feefacb6
content:: Early in a conversation you tell a chatbot your dog's name, and later it uses the name correctly. What best explains this?
options::
- [x] The name is still in the conversation text the model reads when it replies
- The model's weights were updated with the name when you sent it
- The model was briefly retrained on your messages during the chat
- The model memorised the name from its training data
shuffle:: true

#### Question: Open
id:: e51aad1a-e638-4b9d-9f52-876b58afb49b
content:: What happens to an AI model's weights during training, and what happens to them during inference?
assessment-instructions:: Score out of 100. 100 for saying that training adjusts the weights (using data and an objective, to make the model do better) and that inference uses the weights as they are, without changing them, to compute outputs from inputs. 50 if only one half is correct.

#### Question: Choice
id:: 1065cb4b-6055-49a9-8dda-752e89582d69
content:: Which cost rises with the number of people using an AI model?
options::
- [x] The compute used to run the model
- The compute used to pretrain the model
- The cost of collecting the training data
- The cost of fine-tuning the model before release
shuffle:: true

#### Question: Choice
id:: 42b82397-185c-4e9e-929d-260f7c96b8ca
content:: A lab trains a model for months on a large cluster of AI chips. Once training ends, what could that same cluster typically do with the model?
options::
- [x] Run a very large number of copies of it at the same time
- Run about one copy of it, at roughly the speed of training
- Run copies of it only after the weights are retrained for inference
- Little with this model, since its chips suit training rather than running models
shuffle:: true

#### Question: Choice
id:: ad5a633a-8619-4962-a404-a789cefbd52b
content:: Which of these can usually be done on a single high-end gaming computer?
options::
- [x] Running a small open-weights model to answer questions
- Training that same small model from scratch on all its training data
- Running one of the largest frontier models at full size and speed
- Training a frontier model with large-scale reinforcement learning
- Pretraining a mid-sized model on a large share of the web
shuffle:: true

#### Question: Choice
id:: b12ba3f0-e5c6-4013-a202-3bc7094485c1
content:: Some AI rules flag models for extra oversight based on the compute used to train them. What makes training a practical point to regulate?
options::
- [x] Frontier training runs are few, costly and done by a handful of firms
- Training compute tells regulators exactly what a model will be able to do
- Most countries already require a licence before any large training run
- A model's capabilities cannot change once its training has ended
shuffle:: true

#### Question: Open
id:: 1a49f5a1-5591-4968-a03c-f5b1b2950ff9
content:: Why might rules that apply to training runs do little to control a model whose weights have already been released openly?
assessment-instructions:: Score out of 100. 100 for explaining that the costly, visible step (training) has already happened, and that anyone with the weights can now run the model on their own hardware, where inference is cheap, widespread and hard to monitor. 50 for saying only that the weights are out of the developer's control, without linking this to training versus running.

#### Question: Open
id:: ce844be9-f4ce-4649-94b4-b9f24909a15c
content:: Some models can be made more capable by letting them spend more compute while answering, for example by reasoning for longer. Why does this weaken rules that flag risky models by the compute used to train them?
assessment-instructions:: Score out of 100. 100 for explaining that capability can grow through extra inference compute without any more training, so a model below a training-compute threshold may still become as capable as models above it, and the threshold misses this. 50 for a vague answer that training compute doesn't capture everything, without saying why.

#### Question: FillBlank
id:: a9a1d8c7-ec39-43ed-bb6e-0a2fbefd36b4
content:: Running an already trained model to produce outputs, such as answering a question, is called {{inference}}.
