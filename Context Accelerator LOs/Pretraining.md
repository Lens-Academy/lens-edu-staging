---
id: 52964a4d-6603-4bd5-92b8-a874cfcb09e0
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how training a model to predict the next token across huge amounts of text gives it broad knowledge and skills, and describe what a pretrained base model can and can't do before further training.

## Requires
- [[Large language models]]

## Helpful first
- [[Training data]]

## Why it matters
Pretraining is where a model picks up most of its knowledge and general skills, including ones its developers didn't directly choose. Understanding it helps you see why models know things nobody taught them explicitly, why they can state falsehoods fluently, and why later safety training builds on capabilities that are already there.

## Lenses

## Tests

#### Question: Open
id:: c3e84f57-063c-49f3-88ac-faaafcc3c062
content:: In one or two sentences, describe what a language model is trained to do during pretraining.
assessment-instructions:: Score out of 100. 100 for: predict the next token (or word) given the preceding text, over a very large body of text, with its weights adjusted to reduce prediction errors. 60 for "predict text" or "learn from lots of text" without the next-token idea. 0 for describing following instructions or learning from human ratings.

#### Question: Choice
id:: a4331df1-40b0-495b-af14-84814b2cabeb
content:: In pretraining, where do the correct answers that the model learns from come from?
options::
- [x] The next tokens of the training text itself
- Human raters scoring the model's outputs
- Labels written by contractors for each passage
- A reward given when the model completes a task
shuffle:: true

#### Question: FillBlank
id:: 06e57ffa-e798-4f14-88ba-767fbb974520
content:: Language models split text into small chunks called {{tokens|token}}, and pretraining trains the model to predict the next one.

#### Question: Open
id:: b25c4213-dafc-4a7b-9b6c-80874ff57977
content:: Pretraining only trains a model to predict the next token. Explain why this can lead the model to learn facts and reasoning skills.
assessment-instructions:: Score out of 100. 100 for explaining that predicting varied text accurately is easier if the model has the knowledge or skill that produced the text, with an example (e.g. knowing the capital of France helps predict "The capital of France is...", following the logic of a proof helps predict its next line). 50 for "it sees lots of text" with no link to prediction.

#### Question: Choice
id:: ec0e721a-892c-4aeb-9d82-b96f26db2a28
content:: During pretraining, how do developers decide which skills, such as translation or coding, a model learns?
options::
- [x] Mostly indirectly, by choosing which data to train on
- By writing a separate training objective for each skill
- By hand-coding rules for each skill into the network
- By having people rate the model's attempts at each skill
shuffle:: true

#### Question: Choice
id:: e7cb27a3-f2fd-42b9-a487-1e98e3ade7d7
content:: A base model is one that has been pretrained but not yet given further training to act as an assistant. Given the prompt "What is the capital of France?", what does a base model typically do?
options::
- [x] It often continues with more quiz-style questions
- It refuses, since it has had no safety training
- It answers "Paris" and then offers further help
- It outputs nothing, since it was never shown questions
shuffle:: true

#### Question: Choice
id:: 4ada3444-324a-4b08-84b9-59cc0efa669d
content:: A pretrained base model is given the opening of a text written in the style of an expert medical textbook. What is it most likely to do?
options::
- [x] Continue in the style and quality typical of that kind of text
- Write the same continuation it would give a casual forum post
- Refuse to continue because it cannot check medical credentials
- Switch to an informal style, since informal text is more common
shuffle:: true

#### Question: Choice
id:: eb3898d6-8e0a-42a9-a082-bd86eaae00e9
content:: A model that has only been pretrained writes a confident but made-up citation to a research paper. Which feature of pretraining best explains this?
options::
- [x] It learned to produce plausible-looking text, not to check truth
- It looks up citations in a database that contains errors
- Human raters rewarded it for sounding confident
- It copies one source document word for word each time
shuffle:: true

#### Question: Choice
id:: 9df342a1-5114-43a4-8cdf-21f6280bdd44
content:: Does a pretrained language model store its training documents so it can look them up, like a search engine does?
options::
- [x] No; training changes its weights, though it can memorize some repeated passages
- Yes; it keeps a compressed copy of each document to retrieve
- Yes; it stores documents that appeared at least twice in the data
- No; it keeps grammar rules but no facts or specific text
shuffle:: true

#### Question: Choice
id:: a4c294f2-83c5-495c-b1eb-2d075dd694c3
content:: A model was pretrained on text collected up to a certain date, and has had no later training or access to search. What follows from this?
options::
- [x] It lacks knowledge of events after that date
- It updates its knowledge each time someone uses it
- It forgets older events first to make room for newer ones
- It can infer recent events from the patterns in older text
shuffle:: true

#### Question: Choice
id:: 46ef2ddc-9b06-4f19-8cd2-faa67fbef40c
content:: When a chatbot like ChatGPT or Claude is built, which training stage does most of the work of giving it knowledge about the world?
options::
- [x] Pretraining on large amounts of text
- Training on human ratings of its answers
- Fine-tuning on examples of following instructions
- Answering users' questions after release
shuffle:: true

#### Question: Choice
id:: 3e8e0cf2-a675-4bec-8937-3d4522bfda8f
content:: As of 2026, roughly how much text have publicly documented pretraining runs for large open-weight language models used?
options::
- [x] Tens of trillions of tokens
- Tens of billions of tokens
- Hundreds of millions of tokens
- Hundreds of quadrillions of tokens
shuffle:: true

#### Question: Open
id:: 4bcce82e-025d-4061-859e-67ba834e52e6
content:: Why can a model's pretraining data still affect its behavior after it has been trained to be a helpful, safe assistant? Give one example.
assessment-instructions:: Score out of 100. 100 for explaining that later training builds on and reshapes what pretraining learned rather than replacing it, plus one example: harmful knowledge (e.g. about weapons), biases or misconceptions in the data, ideas about how AI behaves, or a knowledge cutoff. 50 for an example without the explanation, or the reverse.
