---
id: 97223949-a139-4e4c-a576-8fec7f7bb59f
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why modern AI systems are trained rather than programmed line by line, what developers do and don't decide directly, and why this means nobody fully writes or understands how these systems behave.

## Requires

## Helpful first

## Why it matters
Many people assume an AI does what its code says, so a bad behavior is a bug someone can find and fix. Knowing that behavior is grown through training shows why developers can't simply read off or write in what an AI values, which is the starting point for most alignment concerns.

## Lenses

## Tests

#### Question: Choice
id:: f4dd2a1d-025d-495a-8231-c591838e2c49
content:: When an AI company trains a large language model, which of these do its engineers write directly?
options::
- [x] The training procedure and the network's architecture
- The specific facts the model will know
- The rules the model follows when answering
- The goals and values the model will have
shuffle:: true

#### Question: Choice
id:: f00db4b6-9a11-43a4-a25b-d3c1a8043124
content:: A chatbot built on a large language model gives a harmful answer. Why can't its developers usually fix this by finding and editing the line of code responsible?
options::
- [x] The behavior comes from billions of learned numbers, not lines anyone wrote
- The responsible code is spread across files written by many teams
- The model rewrites its own source code while it runs
- The code is compiled, so the original lines can't be recovered
shuffle:: true

#### Question: Choice
id:: 38e4e9ab-297f-4b69-9713-31adfe62be76
content:: What is the main way developers find out what a newly trained AI model can do?
options::
- [x] Testing the model on tasks after training
- Reading the specification written before training
- Inspecting the code that defines the network
- Checking which skills were listed in the training objective
shuffle:: true

#### Question: FillBlank
id:: 9db82af4-2491-43ea-b020-aaecd1cdd9b9
content:: What a neural network has learned is stored in a very large set of numbers adjusted during training, called its {{weights|parameters}}.

#### Question: Open
id:: 31110e27-615c-4f6d-9186-2c4e7380cc10
content:: In a sentence or two, what does it mean to say modern AI systems are "grown" rather than "built"?
assessment-instructions:: Score out of 100. Full marks: developers write a training process (and supply data and an objective), and the system's behavior emerges from training rather than from instructions anyone wrote, so nobody specifies or fully understands it. 50 for saying "it learns from data" without the point that nobody writes or understands the resulting behavior.

#### Question: Choice
id:: d829fe4d-04e4-4bb2-afa5-dae4ab4a4727
content:: Which analogy best fits how a large language model gets its abilities?
options::
- [x] Breeding plants by choosing which to keep, without designing their genes
- Assembling furniture by following written step-by-step instructions
- Writing a recipe that lists every cooking step in order
- Building a bridge from an engineer's detailed blueprint
shuffle:: true

#### Question: Choice
id:: 77bff2f4-1abe-44d9-ab2e-c727e198488f
content:: An AI company publishes all the weights of its model. As of November 2026, does this let outside researchers read off what the model values?
options::
- [x] No: the weights are billions of numbers whose meaning is only partly understood
- Yes: the weights record the model's goals in a form experts can read

#### Question: Choice
id:: d26afe6e-3f4c-48e6-aa4e-ccc8b23635c0
content:: Developers want their language model to refuse requests for help making weapons. How is the model itself usually taught to do this?
options::
- [x] By training it on examples and ratings until refusing becomes its habit
- By writing a rule into its code that blocks the topic
- By deleting all weapons knowledge from its weights before release
- By giving it a list of banned words to check before answering
shuffle:: true

#### Question: Choice
id:: 80bbb55f-0275-4ae5-9cc3-ebb8bb655446
content:: A model is trained only to predict the next word in text. Can it end up able to do arithmetic or write code, even though nobody programmed those skills?
options::
- [x] Yes: skills that help predict the text can emerge from training
- No: a model can do only what its training code explicitly includes

#### Question: Choice
id:: 25100caa-2ff7-4cc5-8b61-a6fe25574419
content:: A model behaves well on every test its developers wrote. Can they tell from this how it will behave in new kinds of situations they never tested?
options::
- [x] No: training shapes behavior on what was seen, and new cases can differ
- Yes: passing every test shows the model learned the intended rule

#### Question: Choice
id:: d6ecf7b5-6496-49e6-b93e-e783749f9f3c
content:: Which of these systems has behavior closest to being written line by line by its developers?
options::
- [x] A tax-calculation program that applies coded rules
- A chatbot trained on large amounts of internet text
- An image generator trained on captioned pictures
- A game-playing AI trained by playing against itself
shuffle:: true

#### Question: Open
id:: baddcdbf-ec95-413d-ab47-e18d713d41ff
content:: Why does the fact that modern AI is grown through training, rather than written line by line, make it hard to make sure an AI system has the values its developers intend?
assessment-instructions:: Score out of 100. Full marks: developers can't write values in directly; they can only shape behavior through training signals, and they can't inspect the learned weights to check what the system actually learned, so it may have picked up different goals that look fine in testing. 50 for only one of: can't write values in, or can't check them.
