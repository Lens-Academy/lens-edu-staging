---
id: d668aae7-4278-4bdb-b771-5931b1178f5a
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how training turns examples and an objective into a system's behavior, and explain why the result reflects what scored well in training rather than what its developers meant.

## Requires

## Helpful first
- [[Built vs. grown]]

## Why it matters
Today's AI systems, including chatbots and AI agents, get their abilities this way. Knowing that behavior comes from data and an objective, not from written rules, helps you see why developers can't simply decide what a system does, and why a flawed objective or skewed data can lead to unintended behavior.

## Lenses

## Tests

#### Question: Choice
id:: 69b7941a-5d60-4af0-8a29-e969e57b72a9
content:: When a machine learning model is trained, what changes?
options::
- [x] The values of its parameters
- The code of the learning algorithm
- The examples in its training data
- The objective it is scored against
shuffle:: true

#### Question: Choice
id:: a0787024-aafb-462a-aa35-89b155a3982e
content:: In a typical machine learning project, which of these do developers choose directly, rather than leaving training to set it?
options::
- [x] The objective the model is scored against
- The values of the model's parameters
- The features the model uses to decide
- The rules the model applies to each input
shuffle:: true

#### Question: Choice
id:: 3ce3c16c-4a1c-40ba-8806-92b92ce418b4
content:: A machine learning spam filter is trained on thousands of emails labeled "spam" or "not spam". What makes its behavior change during training?
options::
- [x] Its parameters are adjusted to make fewer errors on the labeled emails
- Programmers add a new rule after each mistake it makes
- It stores the emails and matches new ones against them
- It reads written definitions of what counts as spam
shuffle:: true

#### Question: Choice
id:: cd5d6bce-b78c-4629-98cb-eaee656d8c9d
content:: A machine learning model does very well on its training examples but poorly on new examples of the same task. What is this usually called?
options::
- [x] Overfitting
- Underfitting
- Pretraining
- Fine-tuning
shuffle:: true

#### Question: Choice
id:: 37b70f14-faf5-4bbe-96bd-6e22c9a0ed07
content:: Why do machine learning developers measure a model's performance on examples it was not trained on?
options::
- [x] To check whether what it learned carries over to new inputs
- To speed up training by using fewer examples
- To give the model extra examples to adjust its parameters on
- To check whether the training code has bugs
shuffle:: true

#### Question: Choice
id:: 387661bd-5616-4e73-bae5-b4cd2d6c3629
content:: Chess program A picks moves using a search procedure and a scoring formula that programmers wrote and tuned by hand. Chess program B picks moves using parameters adjusted over millions of practice games to win more often. Is only program B an example of machine learning?
options::
- [x] Yes
- No

#### Question: FillBlank
id:: 80491ea2-549c-4bf6-9ec7-8d689042a600
content:: The numbers inside a machine learning model that training adjusts are called its {{parameters|weights}}.

#### Question: FillBlank
id:: 228b01d7-c2ba-4565-9075-969172aa9f5f
content:: In machine learning, the number that measures how badly a model does on training examples, and that training tries to make smaller, is called the {{loss|loss function|cost|cost function}}.

#### Question: Open
id:: 7c1bf419-77e2-42dc-a374-34ce16dc7eff
content:: In one or two sentences, explain how a machine learning system comes to behave differently after training, without anyone writing new rules for it.
assessment-instructions:: Score out of 100. 100 for saying that training repeatedly adjusts the system's parameters (or weights) so it does better on an objective, measured on example data, and the new behavior results from those adjusted values. 50 for "it learns from data" with no mention of adjusting parameters or of an objective. 0 if it says programmers add rules or the system looks answers up.

#### Question: Open
id:: 03fec45b-b941-44c3-80bd-dd0e9b88438e
content:: Why does the choice of objective matter for what a machine learning system learns? Answer in one or two sentences.
assessment-instructions:: Score out of 100. 100 for saying that training pushes the system toward whatever scores well on the objective, so if the objective leaves out or mismeasures something the developers want, the system can learn behavior that scores well but isn't what they intended. 50 for "the system learns to do what the objective rewards" without the consequence of a mismatch.

#### Question: Open
id:: 3e8c3d49-e04f-4e73-8c72-e7cebf44e41e
content:: A machine learning model is trained to tell photos of cats from photos of dogs. Most of its dog photos were taken outdoors and most of its cat photos indoors. Describe one way it could fail on new photos, and why training would produce that.
assessment-instructions:: Score out of 100. 100 for a failure such as calling an outdoor cat a dog or an indoor dog a cat, plus the reason: the background helped it make fewer errors on the training photos, so training adjusted it to rely on the background. 50 for the failure without the reason, or the reason without a concrete failure.
