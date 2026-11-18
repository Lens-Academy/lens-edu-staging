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
id:: 6cc4b5e2-983d-49c7-94c1-948cb12dbd4a
content:: Eliciting latent knowledge (ELK) asks how to get a trained neural network to report what it really believes. It has mostly been studied with pen-and-paper arguments rather than experiments. How is ELK work best described?
options::
- [x] Prosaic and theoretical
- Prosaic and empirical
- Paradigm-independent and theoretical
- Paradigm-independent and empirical
shuffle:: true

#### Question: Choice
id:: 62d431b6-cf50-4060-b613-fbde94430c12
content:: What is a main argument for focusing alignment research on AI systems built with current machine learning methods?
options::
- [x] AGI might come from these methods soon, leaving no time to wait for a new paradigm
- Systems built with current methods are known to be easy to interpret
- Theoretical work on agency has been shown to be mathematically impossible
- Systems built with current methods cannot become more capable than humans
shuffle:: true

#### Question: Choice
id:: 6d1a5ca8-da4e-4823-b650-a3ef6e0054a0
content:: A lab finds that its safety method reliably stops harmful behaviour in its current models. Why might a skeptic of prosaic alignment still be unimpressed?
options::
- [x] The method might stop working once models are capable enough to evade or game it
- The method was tested on AI models rather than on human volunteers
- Harmful behaviour in current models is too rare to measure reliably
- The method relies on mathematics that has not yet been formally proved
shuffle:: true

#### Question: Choice
id:: 195a1ebb-d32e-4bf3-a1ea-20e5f1ac28e6
content:: Why do some researchers prefer paradigm-independent alignment work to work on aligning today's trained neural networks?
options::
- [x] They expect techniques tuned to today's models to break in ways only deeper theory would predict
- They think today's models are already aligned well enough that further work adds little
- They think theoretical research is much cheaper to fund than experiments on large models
- They think current machine learning methods will be banned before they reach AGI
shuffle:: true

#### Question: Choice
id:: 172f552d-1b7a-4e83-9cf4-b7e3f484b66b
content:: Some researchers separate local alignment (making a given AI system safe) from global alignment (making sure no one anywhere deploys a dangerous unaligned AI). Which outcome is a local success but a global failure?
options::
- [x] One lab aligns its model, but a rival soon releases an unaligned one
- One lab's model is unaligned, but regulators stop its release in time
- Every lab's model is aligned, though each serves a different set of values
- One lab aligns its model and shares the method, and every lab adopts it
shuffle:: true

#### Question: Choice
id:: c5525784-3135-43ea-9ed8-040fdba2e47a
content:: To justify working on prosaic alignment, must a researcher think it more likely than not that AGI will come from scaling up current methods?
options::
- [x] No; a smaller chance can justify it if that scenario is urgent and the work is tractable
- Yes; otherwise the work mainly targets a scenario that probably won't happen

#### Question: Choice
id:: 46cc3642-e0c0-49b6-a239-859206f03059
content:: Which development did most to make prosaic alignment seem relevant to many researchers?
options::
- [x] Large language models gained broad abilities mostly by scaling up existing methods
- A formal proof showed that neural networks can represent any possible goal
- Leading AI labs moved away from deep learning toward symbolic reasoning systems
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
assessment-instructions:: Score out of 100. 100 for any one of: some techniques or lessons may carry over; it makes intermediate systems safer; safer AI systems could help with later alignment research; it trains researchers and builds the field; it shows which problems are hard. 50 for a vague answer such as "it is still good research".
