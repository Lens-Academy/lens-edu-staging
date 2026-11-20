---
id: eff426bc-25b8-4a97-b49d-fee4d7d5c7d5
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what an AI model is in the mathematical sense, and why a trained model amounts to its weights, so that anyone with a copy of the weights can run the model without repeating its training.

## Requires
- [[Neural networks]]

## Helpful first

## Why it matters
Many AI policy disputes are about weights: whether to release them openly, how to stop them being stolen, and who may run them. Knowing that the weights are the model shows why a leak can't be undone and why a company's safeguards don't come along with a copied model.

## Lenses
- [[../video_transcripts/3blue1brown-large-language-models-explained-briefly|Large Language Models Explained Briefly]]: a language model as a mathematical function whose behaviour is set entirely by billions of weights, tuned in training that takes vast computation (2024).
- [Intro to Large Language Models (Andrej Karpathy, YouTube)](https://www.youtube.com/watch?v=zjkBMFhNj_g): watch 0:00–17:52. A model is just a weights file plus a short program to run it; training is costly, running it is cheap, and fine-tuning changes the weights (November 2023).
- [Securing AI Model Weights: Q&A with Sella Nevo (RAND)](https://www.rand.org/pubs/commentary/2024/05/securing-ai-model-weights-qa-with-sella-nevo.html): why weights hold everything a model has learned, so a thief can skip the compute, data and research behind them (May 2024).
- [[../Lenses/AI Safety Atlas - Strategies - Misuse Prevention Strategies|Misuse Prevention Strategies]]: read "External Access Controls" and "Internal Access Controls". API access keeps the weights on the company's servers; open weights can't be recalled or patched and their safeguards can be fine-tuned away; leaked weights escape every external control.

## Tests
#### Question: Choice
id:: a2e4b83c-fe9e-4afe-a6b7-794f6df4c208
content:: In the phrase "AI model", what does "model" mean?
options::
- [x] A mathematical function, with adjustable numbers, that turns inputs into outputs
- A product version, like a car maker's model for a given year
- A small-scale copy of a human brain's structure
- A database of stored questions and their best answers
shuffle:: true

#### Question: Choice
id:: 047fed5c-e7f1-4f6b-b684-5f57b281cd52
content:: A neural network is trained for months. What mainly makes the trained network different from the same network before training?
options::
- [x] The values of its weights
- The code that defines its layers
- The number of layers it has
- The type of chips it runs on
shuffle:: true

#### Question: FillBlank
id:: ceb9d9da-6005-443e-adb2-6af02d367b8a
content:: The adjustable numbers in a neural network, whose values are set during training, are called its {{weights|parameters}}.

#### Question: Choice
id:: 06928198-8b99-45a9-b93d-0c81faef601f
content:: Which best describes how a large language model's weights relate to the text it was trained on?
options::
- [x] They encode patterns from the text, and some passages can be reproduced word for word
- They store all of the text in compressed form, so any passage can be looked up
- They keep no trace of the text, so no passage can ever be reproduced
- They hold an index that points to the text kept on the developer's servers
shuffle:: true

#### Question: Choice
id:: 59047dc4-484f-4edf-8148-70bbe1288b97
content:: Roughly how much storage do the weights of an AI model with about a trillion parameters need?
options::
- [x] A few terabytes, which fits on one consumer portable hard drive
- A few petabytes, which only a large data centre can hold
- A few exabytes, more than all of today's data centres combined
- A few megabytes, about the size of one photo on a phone
shuffle:: true

#### Question: Choice
id:: cc24fe8c-c89d-4cae-a47d-64d1a4b7c1ea
content:: A hacker copies a frontier AI model's weights and knows its architecture. With enough computer chips, what can they do?
options::
- [x] Run the model with the same capabilities as the original
- Run a weaker version, since copying loses some of the training
- Run it once they have repeated the original training run
- Run it once they have also stolen the original training data
shuffle:: true

#### Question: Choice
id:: 653a51fa-48f0-4653-b6df-24db914904d3
content:: For a frontier language model, how does the compute needed to answer one prompt compare with the compute used to train the model?
options::
- [x] It is less than a millionth of the training compute
- It is about a hundredth of the training compute
- It is about a tenth of the training compute
- It is about the same as the training compute
shuffle:: true

#### Question: Choice
id:: 4a60b483-8e6e-4d32-ab45-97462c7ff0b4
content:: An AI company offers its model to the public only through an API. What do outside users get?
options::
- [x] The model's outputs, while the weights stay on the company's servers
- A copy of the weights that runs on their own computers
- A smaller copy of the weights with safety features built in
- Read access to the weights, but not the right to change them
shuffle:: true

#### Question: Choice
id:: c9ae8178-169c-40fe-ac70-5d50e094f4e2
content:: A developer publishes a model's weights for download, then discovers the model has a dangerous capability. Which is true?
options::
- [x] Copies people have already downloaded can't be withdrawn or patched
- The developer can switch off downloaded copies remotely
- Downloaded copies stop working once the licence is revoked
- Downloaded copies update themselves when the developer fixes the model
shuffle:: true

#### Question: Choice
id:: d4115153-fc51-4e83-8b79-9493bc891b62
content:: Someone who has a model's weights fine-tunes it on their own examples. What does fine-tuning change?
options::
- [x] The values of the model's weights, through further training
- The instructions given to the model at the start of each chat
- The architecture, by adding new layers to the network
- A filter that sits around the model and checks its answers
shuffle:: true

#### Question: Open
id:: fb898df7-9e8a-4408-bf09-e82f98f5d142
content:: An AI company screens requests to its model and has trained the model to refuse harmful ones. Give one reason these safeguards may not prevent misuse if the model's weights leak.
assessment-instructions:: Score out of 100. 100 for any one of: whoever holds the weights runs the model on their own computers, outside the company's screening and monitoring; or they can fine-tune the model to remove its refusals. 50 for saying the model is "out of the company's control" without saying why the safeguards stop applying.

#### Question: Open
id:: 821d38a7-d5c4-4e82-aa97-3b5f44c14324
content:: A lab's training code leaks, but its trained weights stay secure. Why is this usually less immediately dangerous than a leak of the weights?
assessment-instructions:: Score out of 100. 100 for: using the code still means doing a training run that needs huge amounts of compute, data and time, while the weights already hold the result of that run and can be used directly. 50 for saying only that training is expensive, without linking it to what the weights contain.
