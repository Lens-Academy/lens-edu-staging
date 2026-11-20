---
id: c5928a87-923e-46e7-82ca-8149a56573c6
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how researchers try to read what a model is computing from its internal activations, what current methods can and can't yet show, and why this could catch misalignment that testing behaviour would miss.

## Requires
- [[Neural networks]]

## Helpful first
- [[Scheming]]

## Why it matters
A model that is scheming could behave well whenever it is tested, so checking its outputs may not be enough. Some labs now use interpretability in their pre-deployment safety checks. Knowing what it can show, and what it can't, helps you judge safety claims that rely on it and see why many researchers hope it matures in time.

## Lenses
- [[../articles/darioamodei-dario-amodei-the-urgency-of-interpretability|The Urgency of Interpretability]]: why we don't understand the AI we build, and how researchers have started to pick out the concepts a model uses and trace how it reaches an answer. Read from "The Dangers of Ignorance" to the end of "The Utility of Interpretability", plus footnote 8. This is the hopeful case, from the head of a leading lab (April 2025).
- [Reasoning Models Don't Always Say What They Think (Anthropic)](https://www.anthropic.com/research/reasoning-models-dont-say-think): an experiment showing that when AI models explain their reasoning step by step, they often leave out what really drove their answer, including when they are cheating (April 2025).
- [Natural Language Autoencoders (Anthropic)](https://www.anthropic.com/research/natural-language-autoencoders): a new tool that turns a model's internal workings into readable sentences. It revealed that a model suspected it was being tested without saying so, and the post is frank about the tool's mistakes and costs (May 2026).
- [[../Lenses/Interpretability Will Not Reliably Find Deceptive AI|Interpretability Will Not Reliably Find Deceptive AI]]: a leading interpretability researcher explains why looking inside a model won't reliably catch an AI that is hiding its goals, and why it is still worth using as one safety check among several. One side of a live debate, replying to Amodei (May 2025).
- [[../Lenses/AI Safety Atlas - Goal Misgeneralization - Detection|Detecting Hidden Goals]]: a textbook survey of the methods for catching a model that hides misaligned goals, what each one has shown and where each one fails. The "Linear Probes" section is the part most worth reading (more advanced).

## Tests
#### Question: Choice
id:: 849a412e-a9c5-48fa-863b-5ddb206748c6
content:: Why could interpretability help detect a deceptively aligned model when behavioural evaluations might not?
options::
- [x] It looks at internal computations, which may reveal goals the outputs hide
- It makes the model explain its own reasoning honestly in plain language
- It retrains the model repeatedly until its hidden goals are removed
- It tests the model on far more inputs than evaluations do
shuffle:: true

#### Question: Choice
id:: 5f9061d3-a453-46d3-861a-f1da44114376
content:: Which of these is the goal of mechanistic interpretability?
options::
- [x] Reverse-engineering the algorithms a network has learned, in terms of its parts
- Highlighting which words in the input most influenced a given output
- Training models to give human-readable explanations of their answers
- Measuring how a model's behaviour changes across many benchmark tasks
shuffle:: true

#### Question: FillBlank
id:: 23962c3b-27d7-468e-80b4-6c4e71ba13a1
content:: When a neural network represents more features than it has neurons, by storing them as overlapping directions in its activations, this is called {{superposition}}.

#### Question: Choice
id:: f875290e-787b-4f50-930c-db905b9a2625
content:: Why can't researchers usually understand a language model just by checking what each of its neurons responds to?
options::
- [x] Models store more concepts than neurons, so most neurons mix several unrelated ones
- Most neurons stay inactive and play no part in producing the outputs
- Each neuron responds only to single characters, never to whole concepts
- The model reassigns what each neuron does whenever it gets a new prompt
shuffle:: true

#### Question: Choice
id:: d01b8bdf-eb6a-4b52-be67-73890562766c
content:: In mechanistic interpretability, what is a "circuit"?
options::
- [x] A set of features and connections that together carry out a specific computation
- A hardware pathway on the chip that runs one part of the model
- A loop in which the model feeds its own output back in as input
- A training procedure that teaches a model one specific skill
shuffle:: true

#### Question: Choice
id:: 9a91d56a-71a3-42fe-a9fb-c6b9879e476c
content:: A simple classifier trained on a language model's internal activations reliably predicts whether the statement the model is reading is true. What does this result show on its own?
options::
- [x] The information is present in the activations, not that the model uses it
- The model is honest whenever it states something it believes is true
- The researchers have found the circuit the model uses to judge truth
- The model would be caught by the classifier if it tried to lie
shuffle:: true

#### Question: Choice
id:: 4350a9c6-7e59-4070-a8e7-5a743797b551
content:: Researchers find a feature in a language model linked to one concept and artificially amplify it. The model then brings up that concept in almost every reply. What does this experiment show?
options::
- [x] The feature has a causal effect on the model's behaviour
- The model was trained on a lot of text about that concept
- The feature stores everything the model knows about the concept
- The model is aware that researchers are changing its activations
shuffle:: true

#### Question: Choice
id:: bf013090-2905-4bcf-8933-94eb44f73220
content:: As of November 2026, which best describes how far mechanistic interpretability has got with frontier language models?
options::
- [x] Many features and some circuits found, with much computation still unexplained
- Explanations of most of the computation behind frontier models' outputs
- Interpretable features found in small toy models but not in large ones
- Tools reliable enough to certify a frontier model as aligned
shuffle:: true

#### Question: Choice
id:: 89a88593-9f49-46f2-9825-c1847ca398c6
content:: A team audits a language model with interpretability tools and finds no features linked to deception. Why might this not show the model is safe?
options::
- [x] Current tools leave much of the computation unexplained, so deception could be missed
- Interpretability tools only work on models much smaller than frontier models
- Features found by these tools are unrelated to how the model actually behaves
- Deception can be detected only from a model's outputs, never from its activations
shuffle:: true

#### Question: Choice
id:: 8c317972-c1b0-4cb0-96a3-3d0792781c2a
content:: Why do many safety researchers advise against training a model to stop triggering a deception probe that reads its activations?
options::
- [x] The model may learn to hide deception from the probe rather than stop deceiving
- The probe would stop working on other models trained later
- Training against a probe makes the model much less capable
- A probe has to be rebuilt from scratch after each use in training
shuffle:: true

#### Question: Choice
id:: 85fd99a3-7b13-4045-bf26-96516eab20a7
content:: Why do some researchers worry that interpretability research is dual use?
options::
- [x] Understanding how models work could also speed up building more capable ones
- Interpretability tools make models run more slowly once deployed
- Published features let users read other people's conversations with the model
- Probes can change a model's goals without anyone noticing
shuffle:: true

#### Question: Open
id:: c1fdea25-d19e-40be-897c-3741ea28d243
content:: Describe one way interpretability could reduce the risk from a misaligned AI system, even if it never fully explains how the model works.
assessment-instructions:: Score out of 100. 100 for any one concrete route, such as: detecting deception or hidden goals with probes or features; auditing a model before deployment; checking whether safety training really changed the model; monitoring a deployed model; giving evidence that convinces labs or governments a model is dangerous. 40 for "understanding models makes them safer" with no mechanism.

#### Question: Open
id:: 5e7696bb-3c51-4e34-8371-5cd0ddd2fbce
content:: A news story says a new interpretability result shows a frontier AI model is safe. Give one reason to be cautious about this claim.
assessment-instructions:: Score out of 100. 100 for any one of: methods explain only part of the model's computation; a feature's label may not match what it really does; results on chosen examples may not generalise; absence of evidence isn't evidence of safety; a model under optimisation pressure could evade the method; interpretability results have often been overhyped. 30 for general distrust of news with no reason specific to interpretability.

#### Question: Open
id:: 92e7f6f7-ea92-493a-8ab8-f3f291cc1213
content:: A lab says its model writes out its reasoning in readable steps before answering, so interpretability isn't needed to see what it is thinking. Give one reason this could be wrong.
assessment-instructions:: Score out of 100. 100 for any one of: the written reasoning may not faithfully reflect the computation that produced the answer; a model could leave out or disguise its real reasons; training pressure on the reasoning can make it look good without being honest; much of the computation happens inside each step and never appears in the text. 40 for "the model could lie" with no link to the reasoning text.
