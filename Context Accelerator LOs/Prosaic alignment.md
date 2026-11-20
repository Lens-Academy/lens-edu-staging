---
id: a742e134-bf1a-480f-83e3-9581c61b76a8
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what prosaic alignment assumes about how AGI will be built, give the main arguments for and against focusing on it rather than paradigm-independent theory, and tell it apart from the empirical vs. theoretical and local vs. global distinctions.

## Requires

## Helpful first
- [[Safety research agendas]]

## Why it matters
Researchers often disagree about agendas because they disagree about whether AGI will look like today's models. Seeing that assumption lets you judge whether work on current systems will still matter for much stronger ones, and understand why some researchers call such work essential while others doubt it will carry over.

## Lenses
- [Prosaic AI alignment (Paul Christiano, AI Alignment Forum)](https://www.alignmentforum.org/posts/YTq4X6inEudiHkHDF/prosaic-ai-alignment): the post that coined the term. It says what "prosaic AGI" assumes (no new ideas about intelligence, just scaled-up neural networks and RL) and argues it deserves work even at a >10% chance: it may come soon, the work can start now, lessons may transfer, and learning that it's infeasible would itself matter (November 2016).
- [[../video_transcripts/far-ai-the-two-cultures-of-ai-safety-catastrophists-vs-uniformitarians-jesse-hoogland-timaeus|The Two Cultures of AI Safety]]: Jesse Hoogland (Timaeus) sets prosaic, forward-chaining work against agent foundations. He names the crux (how discontinuous AI progress will be), shows why empirical vs. theoretical lines up with that crux without being the same thing (ARC theory as prosaic but theoretical), and says what each side misses. Watch 11:15–23:30 and 36:30–45:00.
- [[../Lenses/byrnes-sympathy-for-both-sides-of-the-egregious-misalignment-debate|Sympathy for Both Sides of the Egregious Misalignment Debate]]: Steven Byrnes, a critic of the prosaic assumption, argues that alignment techniques may really work for LLMs, yet this says little about ASI if LLMs don't scale to it. One side of a live debate (June 2026).

## Tests
#### Question: Choice
id:: 070c5e53-f59c-42db-8342-e712d49b6b80
content:: What does "prosaic alignment" research assume about how AGI will be built?
options::
- [x] By scaling up today's machine learning methods, with no fundamentally new ideas
- By a new kind of architecture that has not been invented yet
- By hand-coding goals and rules into a logical reasoning system
- By copying the structure of a scanned human brain in detail
shuffle:: true

#### Question: Choice
id:: 30c81b6a-e63b-4a4c-b38d-7fd30bbd0858
content:: Which of these projects is the clearest example of paradigm-independent, theoretical alignment work?
options::
- [x] Developing a mathematical theory of how agents embedded in their world should reason
- Training a reward model from human comparisons of chatbot answers
- Finding features inside a large language model that track deception
- Testing whether a weaker model can reliably supervise a stronger one
shuffle:: true

#### Question: Choice
id:: b95bdf47-d93d-41bf-8097-dafeb027aa50
content:: Which of these projects is prosaic alignment work that is theoretical rather than empirical?
options::
- [x] Looking on paper for flaws in proposed ways to train an honest neural network
- Finding features inside a large language model that track deception
- Developing a mathematical theory of how embedded agents should reason
- Running experiments on whether a weaker model can supervise a stronger one
shuffle:: true

#### Question: Choice
id:: 62d431b6-cf50-4060-b613-fbde94430c12
content:: What is a main argument for focusing alignment research on AI systems built with current machine learning methods?
options::
- [x] AGI might come from these methods soon, before any new paradigm arrives
- Systems built with current methods are already easy to interpret
- Theoretical work has already settled the main conceptual questions
- Systems built with current methods are the only ones that can be regulated
shuffle:: true

#### Question: Choice
id:: 6d1a5ca8-da4e-4823-b650-a3ef6e0054a0
content:: A lab finds that its safety method reliably stops harmful behaviour in its current models. Why might a skeptic of prosaic alignment still be unimpressed?
options::
- [x] The method might stop working once models can evade or game it
- The method was tested on language models but not on image models
- Harmful behaviour in current models is too rare to measure reliably
- The method has not yet been described in a peer-reviewed paper
shuffle:: true

#### Question: Choice
id:: 195a1ebb-d32e-4bf3-a1ea-20e5f1ac28e6
content:: Why do some researchers prefer paradigm-independent alignment work to work on aligning today's trained neural networks?
options::
- [x] They expect methods tuned to today's models to fail on far stronger ones
- They think today's models are already aligned well enough to need little work
- They think theory is much cheaper to fund than experiments on large models
- They think today's networks are too small to show any alignment problems
shuffle:: true

#### Question: Choice
id:: 0f5bcbcc-bfa4-490a-ae32-67a95b3bca4c
content:: Some researchers separate local alignment (an AI behaves as intended at the capability levels tested so far) from global alignment (that behaviour keeps holding as AI becomes far more capable). Which finding is evidence of local alignment but says little about global alignment?
options::
- [x] The current model refused harmful requests in over 99% of tests
- Weaker models were shown to reliably supervise much stronger ones
- Alignment failures became rarer with each more capable model generation
- Researchers understand why the model's goals won't shift as it grows more capable
shuffle:: true

#### Question: Choice
id:: c5525784-3135-43ea-9ed8-040fdba2e47a
content:: To justify working on prosaic alignment, must a researcher think it more likely than not that AGI will come from scaling up current methods?
options::
- [x] No; a smaller chance can be enough if that scenario is urgent and tractable
- Yes; otherwise most of the effort goes to a scenario that probably won't happen

#### Question: Choice
id:: 46cc3642-e0c0-49b6-a239-859206f03059
content:: Which development did most to make prosaic alignment seem relevant to many researchers?
options::
- [x] Large language models gained broad abilities mostly by scaling up existing methods
- A formal proof showed that neural networks can represent any possible goal
- Brain-scanning projects mapped the full wiring of a small animal's brain
- Governments began requiring labs to publish full details of their training methods
shuffle:: true

#### Question: Open
id:: f346b6f2-1ace-4708-9eb2-2b528926d436
content:: Prosaic alignment and empirical alignment research are often treated as the same thing. Explain how the two distinctions differ.
assessment-instructions:: Score out of 100. 100 for saying that "prosaic" is about which systems the work assumes (AGI from scaled-up current methods), while "empirical" is about how the work is done (experiments rather than theory), so the two can come apart, e.g. theoretical work on neural networks such as ELK. 50 for describing only one of the two correctly.

#### Question: Open
id:: 27638cbf-348e-4874-8d21-f585e9c0222f
content:: Give one reason to expect lessons from aligning today's language models to carry over to AGI, and one reason to doubt it.
assessment-instructions:: Score out of 100. 50 for a reason to expect transfer (e.g. AGI may be built with the same methods; trends so far have been continuous; general lessons about trained systems). 50 for a reason to doubt it (e.g. more capable models may evade or game techniques; a new paradigm may arrive; new behaviour may appear at higher capability).

#### Question: Open
id:: ec469850-cc9b-4d79-93cf-d5b72f0a42b1
content:: A researcher says: "If AGI comes from a new paradigm, prosaic alignment work will be wasted." Give one way such work could still be useful.
assessment-instructions:: Score out of 100. 100 for any one of: some techniques or lessons may carry over; it makes intermediate systems safer; safer AI systems could help with later alignment research; it trains researchers and builds the field; it shows which problems are hard. 20 for a vague answer with no mechanism, such as "it is still good research".
