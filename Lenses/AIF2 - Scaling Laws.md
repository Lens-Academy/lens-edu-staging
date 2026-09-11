---
id: 'a722e69d-9972-432d-9f2b-e344ddb252aa'
reading_minutes: 15
tutor_minutes: 8
title: "Scaling Laws"
tldr: Underneath every capability curve in this unit sits a law with two inputs, parameters and data, and a third, algorithms, that moves the constants. Spend a fixed budget on the wrong input and no amount of it will catch a model that spent it on the right one.
summary_for_tutor: "Unit 1 reading on the law under the curves. Predict-first question asks which of two ways to spend a fixed training budget wins (bigger model versus more data) and what third input the two-number law leaves out. Then two excerpts from nostalgebraist's 2022 post on the Chinchilla scaling law: the law itself with Gopher and Chinchilla plugged in, and the opening of the data section. After-reading question asks which input was binding in 2022, which Unit 1 gear that changes, and what to watch for the binding input changing. Closing text gives the algorithms number from Epoch AI (Ho and co-authors, 2024) with a link. One-turn mirrors, no grade. The numbers are 2022's; the shape of the argument is the content."
authors:
  - Lauren+Claude
tags:
  - reading
---
#### Text
content::
\## Before you read

Unit 1 has given you a curve (METR's task lengths) and a thought experiment (what twelve more orders of magnitude of compute would buy). Underneath both sits a law.

A language model's loss, meaning how badly it predicts the next token of text (lower is better), is close to a simple function of two numbers: how many parameters the model has, and how many tokens of text it was trained on. Compute buys both, and a training run has to choose how much of each. The third input, algorithms, changes the constants in the law rather than the inputs, and it moves faster than most people assume.

This reading is the post that made the field notice the second input. It is from 2022, and its numbers are dated. The shape of the argument is not. Read for the shape: two terms and a constant, and what happens when a fixed budget goes to one term instead of the other.

*The framing and questions on this page were written by Claude, an AI, and reviewed by a human. The reading itself is the author's own work.*

#### Question: Open
id:: dc8f40e7-c15d-45fe-a73a-cc5e5c401ff9
content::
\## Your turn first

A lab has a fixed compute budget for one training run. It can spend it on a bigger model trained on the same amount of text, or on the same-sized model trained on more text. Guess, in two or three sentences: which gives the better model, and roughly how much better.

Then one line. Name the third input that a two-number law (parameters, data) leaves out, and say whether you think it matters more or less than the two it includes.

max-time:: 4:00

feedback-instructions:: The student has not read the article yet. It is nostalgebraist's "chinchilla's wild implications" (2022), which shows from the Chinchilla scaling law that in 2022 data, not model size, was the binding input: Gopher (280 billion parameters, 300 billion tokens) is beaten at the same compute by Chinchilla (70 billion parameters, 1.4 trillion tokens), and by the law no model trained on Gopher's data could ever catch Chinchilla however big. Do not reveal any of this. Do not mention Chinchilla, Gopher, or the numbers.

One turn. Reflect back which way they guessed and the reason they gave, in one sentence. Do not evaluate it. If they named a third input, say only that the reading leaves it out too and that the page after the reading returns to it. If they say they do not understand, give one foothold in the same message: a model is a recipe with two dials, size and amount of practice text, and the question is which dial pays more per unit of compute; then send them to the reading. Close by sending them to the reading, one sentence, no preview.

Response length: 50 to 90 words. Short paragraphs. No lists. Calm and direct. Do not over-validate. Do not praise. Do not invite further dialogue.

#### Article
source:: [[../articles/nostalgebraist-chinchillas-wild-implications]]
from:: This post is about language model scaling laws
to:: People put immense effort into training models that big, and were working on even bigger ones, and yet none of this, in principle, could ever get as far Chinchilla did.

#### Article
from:: It is frustratingly hard to find an answer to this question.
to:: Did you use all the forum data you could find, or only 0.01% of it, or something in between?

#### Question: Open
id:: c4839b04-6ce1-4542-b44d-b73d9bd6f067
content::
\## After the reading

The post says one input was binding in 2022. Which one, and which number in the post tells you so.

Then: of Unit 1's gears, compute growth and the task-length curve, which does this change your reading of, and how. Two or three sentences.

One line more. What would you watch over the next two years that would tell you data had stopped being the binding input, or that it never was for the models that matter now?

max-time:: 6:00

feedback-instructions:: The student has read two excerpts of nostalgebraist's "chinchilla's wild implications" (2022). The finding: data, not size, was binding. The number: Gopher's finite-model term is 0.052 against a finite-data term of 0.251; Chinchilla, with the same compute spent as 70 billion parameters on 1.4 trillion tokens, reaches lower loss than Gopher, and by the law no model trained on Gopher's 300 billion tokens could catch it however big. The second excerpt says the field had not taken data seriously and did not know how much text exists.

One turn. Check two things: did they name data, with a number from the post (either term value or the Gopher and Chinchilla comparison counts); and did their watch-signal name something observable (a published training-data size, a lab reporting a data-limited run, a synthetic-data result). If the watch-signal is unobservable, ask, without waiting for a reply, what a lab would have to publish for them to see it. Do not settle whether data is still binding in 2026; the post cannot say and neither can you. If they say they do not understand, give one foothold: the two terms in the equation are two separate costs, and the post asks which cost is still large.

Response length: 60 to 110 words. Short paragraphs. No lists. Calm and direct. Do not grade. Do not praise. Do not invite further dialogue.

#### Text
content::
\## The input the post leaves out

Algorithms. The law's constants are not fixed. Epoch AI's estimate, from over two hundred language-model results between 2012 and 2023, is that the compute needed to reach a set performance level halved roughly every eight months from algorithmic improvement alone, with a wide range (five to fourteen months), and that over the same period growth in compute still contributed more to performance than algorithms did. Source: Ho and co-authors, "Algorithmic progress in language models", 2024, [arxiv.org/abs/2403.05812](https://arxiv.org/abs/2403.05812).

So three inputs, all moving: compute, data, algorithms. The curves you met earlier in this unit are what those three do together. The optional Epoch reading that follows asks which physical input binds first.
