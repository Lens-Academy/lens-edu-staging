---
id: '203aaaeb-68bd-4c74-bac7-ef0ef8bac7df'
title: "What Do We Mean by Intelligence?"
reading_minutes: 25
tutor_minutes: 0
tags:
  - wip
---

#### Text
content::
Let's start by taking a closer look at the concept of intelligence itself.

Like many concepts in AI safety, intelligence is not particularly well defined. There is no single definition that everyone agrees on. In fact, there are *quite a lot* of definitions. In 2007, Shane Legg and Marcus Hutter set out to collect existing definitions of intelligence from psychology, AI research, dictionaries, and professional organisations. They ended up with **71 different definitions**. ([\[0706.3639\] A Collection of Definitions of Intelligence](https://arxiv.org/abs/0706.3639))

If you look through their collection, you'll notice that people use the same word to refer to somewhat different things: the ability to learn, to adapt, to solve problems, to achieve goals, to reason, or to perform well across different environments.

#### Article
source:: [[../articles/legg-universal-intelligence-a-definition-of-machine-intelligence]]
from:: A fundamental problem in artificial intelligence is that nobody really knows
to:: significantly different to humans.

#### Article
from:: > _“Innumerable tests are available for measuring intelligence
to:: Intelligence involves a perplexing mixture of concepts, many of which are equally difficult to define.

#### Text
content::
A common starting point in theoretical AI is to understand intelligence in terms of an **agent's ability to achieve goals across a wide range of environments**. This approach can be found in the above-quoted work of [Legg and Hutter](https://arxiv.org/abs/0712.3329), and related goal-directed accounts appear in broader discussions of AI, including the [Stanford Encyclopedia of Philosophy](https://plato.stanford.edu/entries/artificial-intelligence/).

This is useful as a starting point, but it leaves many questions unanswered.

What counts as a goal for modern LLMs? How wide must the range of environments be for us to be able to say that the goal is robustly achieved? How should we compare two systems if one is better at mathematics and another is better at navigating unfamiliar physical environments? Do speed, cost and the ability to learn new tasks matter?

To make more specific claims, we often need to *operationalise* it in the context of a specific task.

**Operationalising a concept means making it precise enough that we can use it to investigate a particular question.** We specify what observations would count as evidence, how we would measure the relevant property, or what concrete mechanisms we are trying to describe.

Different problems can call for different operationalisations.

#### Text
content::
\## Intelligence as X

One approach comes from Connor Leahy and his co-authors in [The Compendium](https://www.thecompendium.ai/intelligence). They suggest looking at the intellectual tasks that systems can perform and the mechanisms that make this possible.

#### Article
source:: [[../articles/thecompendium-intelligence]]
from:: By considering intelligence as the intellectual tasks it is composed of
to:: “can we automate all intellectual tasks?” To which we say: yes.

#### Article
from:: Intelligence is not yet a [hard science]
to:: processing information and responding accordingly in pursuit of a goal.

#### Article
from:: Human intelligence grew as a result of three primary factors:
to:: means to account for biases and systematic sources of errors.

#### Text
content::
Another useful observation here is that not all the intelligence involved in solving a problem needs to be located inside one brain.

Consider designing a spacecraft. No single engineer needs to know everything about propulsion, materials, orbital mechanics, electronics and manufacturing. The achievement comes from a system involving people, tools, accumulated knowledge and methods of coordination.

If we think about intelligence this way, the question of whether AI can surpass human capabilities becomes partly a question about which intellectual tasks and processes can be automated, combined or improved.

#### Text
content::
\## Intelligence as efficient cross-domain optimisation

Another approach comes from Eliezer Yudkowsky, who proposes understanding intelligence as **efficient cross-domain optimisation**.

#### Article
source:: [[../articles/intelligence-intelligence-explosion-microeconomics]]
from:: It is obvious to ask questions like “What do you mean by ‘intelligence’?”
to:: via strategies that operate across a wider range of domains.

#### Text
content::
Yudkowsky also makes an interesting distinction between defining intelligence theoretically and deciding what we actually need to predict. If our concern is whether a future system could develop technologies far beyond human capabilities, a definition is useful only insofar as it helps us reason about that possibility.

#### Text
content::
\## Intelligence as skill-acquisition efficiency

A different operationalisation comes from François Chollet in [On the Measure of Intelligence](https://arxiv.org/abs/1911.01547).

Chollet argues that performance on a particular task is not the same as intelligence. A system might become extremely good at one task through enormous amounts of training without being particularly good at adapting to new problems.

He therefore focuses on *skill-acquisition efficiency*: how effectively a system can acquire new abilities from limited experience and prior knowledge.

This approach leads to different questions about AI progress. Instead of asking only how many tasks a system can perform, we might ask how much experience it needs to learn something new.

#### Article
source:: [[../articles/chollet-on-the-measure-of-intelligence]]
from:: The No Free Lunch theorem \[98, 97\] teaches us that any two optimization algorithms
to:: Would it generalize to every possible task in the universe?

#### Article
from:: if there is such a thing as universal intelligence, and if human intelligence is an implementation of it
to:: and for the research strategies we should follow to achieve it.

#### Article
from:: To use a well-known cross-domain analogy \[25\]
to:: a remarkable fact that should be of the utmost interest to anyone interested in engineering broad or general-purpose abilities of any kind.

#### Article
from:: The study of general artificial intelligence is a field still in its infancy
to:: given unlimited experience and unlimited prior knowledge.

#### Text
content::
These approaches overlap, but they draw our attention to different aspects of the phenomenon. Each helps make a different set of questions more precise.

And there are many more.

#### Callout: More on the concept of intelligence
collapse:: closed

#### Text
content::
There are other ways to think about intelligence, each highlighting something different.

For example, [Rationale for a Large Text Compression Benchmark](https://mattmahoney.net/dc/rationale.html) explores the idea of intelligence as the ability to discover patterns in information. The better a system understands the underlying regularities, the better it can predict and compress data. Mahoney takes this argument quite far, suggesting that perfect text compression would imply the ability to solve many difficult AI problems.

[Intelligence Is Adaptive Control of Energy Through Information](https://www.lesswrong.com/posts/LNLL8yCA2WhGe28bc/intelligence-is-adaptive-control-of-energy-through) proposes looking at intelligence through the capacity to use information to influence physical processes. This is a rather unusual framing, but it raises an interesting question: should we pay more attention to what a system can actually do in the physical world?

What makes this framing potentially interesting as an operationalisation of intelligence is that it invites us to take a third-person perspective. We are not obligated to identify an agent, or some other entity that possesses intelligence, we could look at how information shapes physical processes, in the attempt to capture what regularities emerge, and eventually to predict what observable consequences follow.

Some perspectives challenge even more basic intuitions.

We often talk about humanity's technological achievements as evidence of *human intelligence*. But consider all that rocket science, Moonlight Sonata and doughnuts being the result of joint work of two different optimisers (of which human intelligence is significantly weaker one).

Joseph Henrich and other researchers of [cumulative cultural evolution](https://henrich.fas.harvard.edu/publications/secret-our-success-how-culture-driving-human-evolution-domesticating-our) argue that much of what makes humanity unusually capable comes from our ability to accumulate, transmit and improve knowledge across generations. A single human, even an exceptionally intelligent one, could hardly recreate modern technology from scratch. Much of what makes us capable comes from a much larger process involving many minds across many generations.

That makes us humans more of a substrate than an agent. From this perspective, cultural evolution is itself an important and powerful optimisation process producing increasingly sophisticated solutions to problems. And the question it raises is: which would be a ‘better’ substrate for this kind of optimiser, AI or humans? In [Why You Don’t Believe in Xhosa Prophecies](https://www.lesswrong.com/posts/tz5AmWbEcMBQpiEjY/why-you-don-t-believe-in-xhosa-prophecies) (2026), Jan Kulveit, one of the main contributors to the Gradual Disempowerment agenda, explains how it could create risks all the way up to the risk of extinction.

#### End Callout

#### Text
content::
This leaves us with a few practical lessons.

First, it helps to be explicit about what we mean by intelligence whenever we use the word.

Second, it is perfectly reasonable to use different definitions for different purposes. Even within one research project, different stages may require different operationalisations.

The problem is changing definitions without noticing in a way that it confuses someone (including yourself).

What is the practical use of all this discussion?

Well, for one thing, we cannot measure something until we have decided what exactly we are trying to measure. And depending on how we understand intelligence, we will pay attention to different observable properties and try to turn them into different measurable quantities.

But there is a more general reason to ask these questions. This kind of conceptual work, alongside the accumulation of empirical evidence, is part of what allows a scientific discipline to move beyond its pre-paradigmatic stage and become a mature science.

In physics, everyone knows what *work* means. And everyone knows that everyone else knows. To the point where you can barely think about what the term means and still do perfectly useful physics. That is because the concept of work does not exist in isolation. It is connected to hundreds of other concepts, laws, and measurement procedures, which together form a coherent system.

This coherence gives physics a kind of conceptual clarity that AI safety currently lacks.

And without it, things can get rather strange.

Here is a little exercise.

**Given:**

Three Go players:

- **X: KataGo.** An open-source Go-playing AI, comparable in strength to DeepMind's famous AlphaGo, which defeated world champion Lee Sedol in 2016. KataGo is one of the strongest Go-playing AI systems, far surpassing even the best human players
- **Y: an adversarial AI.** A system specifically trained to exploit KataGo's weaknesses, winning over 97% of games against it under certain experimental conditions.
- **Z: an ordinary human amateur.** A player who stands virtually no chance against KataGo but can easily beat Y.

This is not a hypothetical example. Such results were demonstrated in [Adversarial Policies Beat Superhuman Go AIs](https://proceedings.mlr.press/v202/wang23g.html).

Now suppose we are interested in intelligence only insofar as it manifests in the ability to play Go. We want to assign each player a numerical value representing their ability to play the game.

**Question 1.** How should we define this quantity so that the question "Who plays Go better?" has a well-defined answer?

**Question 2.** And how do you like living in a world without transitivity?
