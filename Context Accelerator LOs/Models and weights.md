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
content:: Do a large language model's weights hold a copy of its training text that can be looked up like a database?
options::
- [x] No: what it learned is spread across many weights, with only some passages memorized
- Yes: the weights store the training text in a compressed form that can be searched

#### Question: Choice
id:: 59047dc4-484f-4edf-8148-70bbe1288b97
content:: Is the weights file of an AI model with about a trillion parameters small enough to fit on one consumer portable hard drive?
options::
- [x] Yes
- No

#### Question: Choice
id:: cc24fe8c-c89d-4cae-a47d-64d1a4b7c1ea
content:: A hacker copies a frontier AI model's weights and knows its architecture. With enough computer chips, what can they do?
options::
- [x] Run the model with the same capabilities as the original
- Run a weaker version, since copying loses some of the training
- Run it once they have repeated the original training run
- Use it only by sending requests to the developer's servers
shuffle:: true

#### Question: Choice
id:: 653a51fa-48f0-4653-b6df-24db914904d3
content:: For a frontier language model, how does the compute needed to answer one prompt compare with the compute used to train the model?
options::
- [x] It is a tiny fraction of the training compute
- It is about the same as the training compute
- It is about a tenth of the training compute
- It is larger, since each answer retrains the model a little
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
