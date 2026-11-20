---
id: d668aae7-4278-4bdb-b771-5931b1178f5a
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how training turns examples and an objective into a system's behavior, and explain why the result reflects what scored well in training, which can differ from what its developers meant.

## Requires

## Helpful first
- [[Built vs. grown]]

## Why it matters
Today's AI systems, including chatbots and AI agents, get their abilities this way. Knowing that behavior comes from data and an objective, not from written rules, helps you see why developers can't simply decide what a system does, and why a flawed objective or skewed data can lead to unintended behavior.

## Lenses
- [A short introduction to machine learning (Alignment Forum)](https://www.alignmentforum.org/posts/qE73pqxAZmeACsAdF/a-short-introduction-to-machine-learning): Richard Ngo's overview for the AI safety community: hand-written rules versus learned parameters, neural networks, loss functions and optimization, the main kinds of training task, and why generalizing beyond the training data is the hard part (August 2021).
- [[../articles/cotra-why-ai-alignment-could-be-hard-with-modern-deep-learning|Why AI alignment could be hard with modern deep learning]]: Ajeya Cotra on training as a search for whatever scores well, and the "thneeb" example of a model that learns colour when we meant shape; read the sections "How deep learning works at a high level" and "Models often get good performance in unexpected ways" (2021).
- [[../Lenses/3blue1brown-gradient-descent-how-neural-networks-learn-deep-learning-chapter-2|Gradient descent, how neural networks learn]]: 3Blue1Brown's visual account of a cost function, nudging thousands of weights to lower it, testing on images the network has never seen, and a network that memorises randomly labelled data.
- [Overfitting (Google Machine Learning Crash Course)](https://developers.google.com/machine-learning/crash-course/generalization/peril-of-overfitting): what overfitting is, why a model that fits its training data too closely fails on new data, and how a separate test set reveals it (updated December 2025).

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
- The internal steps the model takes to reach an answer
- The rules the model applies to each input
shuffle:: true

#### Question: Choice
id:: 7ebd00f3-2407-43e6-9f30-e478560f4865
content:: Developers want a chatbot to give accurate answers. They train it using ratings from people, who tend to rate confident answers that agree with them above hedged or contradicting ones, even when the hedged ones are more accurate. What is this training most likely to push the chatbot toward?
options::
- [x] Confident, agreeable answers, even when less accurate
- Accurate answers, since that is what the developers want
- Hedged answers, since those tend to be the most accurate
- Whichever answers appeared most often in its training data
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
