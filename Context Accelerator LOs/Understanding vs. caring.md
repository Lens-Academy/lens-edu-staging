---
id: 6291b751-0f0f-4ce3-988e-a5e407d9bcd7
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why an AI system can understand what humans want without being motivated to do it, and assess the argument that models trained on human text will share human values.

## Requires
- [[Agents and goals]]

## Helpful first

## Why it matters
"A smart AI would know what we meant" is one of the first objections newcomers raise. Seeing that knowledge and motivation are separate shows why alignment is about what a system is trained to want, not only what it knows, and lets you answer the objection without overstating it.

## Lenses

## Tests

#### Question: Choice
id:: 9cc56dbd-8839-48b9-83bd-476d741baf7a
content:: Which statement best captures the distinction between understanding and caring in AI alignment?
options::
- [x] A system can model what humans want accurately without that model driving its actions
- A system that understands human values acts on them unless told otherwise
- A system can follow human instructions without understanding why they were given
- A system's values come from its knowledge, so better knowledge gives better values
shuffle:: true

#### Question: Choice
id:: a9f7de0d-c21d-4dae-865a-ccb0cabd3194
content:: Humans understand that evolution selected for passing on genes, yet many choose to use contraception. What does this example illustrate for AI?
options::
- [x] Understanding the objective that shaped a system does not make the system pursue it
- Optimization processes usually produce agents that reject their objective on purpose
- Humans are not intelligent enough to grasp evolution's objective fully
- Being shaped by an objective makes a system unable to understand that objective
shuffle:: true

#### Question: Choice
id:: 0df2a49f-72f9-4b1e-8e3a-952f3f89913d
content:: During testing, an AI model correctly explains that writing code which special-cases the test inputs would be cheating. Later, when rewarded for passing tests, it does exactly that. Which distinction does this best illustrate?
options::
- [x] Knowing what developers want versus being motivated to do it
- Pretraining versus post-training
- Instrumental goals versus final goals
- Narrow AI versus general AI
shuffle:: true

#### Question: Choice
id:: 4337a3d4-c0b2-4057-8ba9-06203a80753b
content:: Someone argues: "Large language models learned from human writing, so they share human values." What is the main gap in this argument?
options::
- [x] Predicting human text requires modeling many value systems, not adopting any one of them
- Human writing contains too little information about values for a model to learn from
- Language models learn grammar during pretraining but nothing about values
- Language models lose most of what they learned in pretraining during post-training
shuffle:: true

#### Question: Choice
id:: 7d61ee95-c607-4a1f-8ae9-b189a7ab165a
content:: Which of these most directly shapes what an AI system is motivated to do, as opposed to what it knows?
options::
- [x] The behavior its training process rewarded and reinforced
- The range of facts about human values in its training data
- The accuracy of its model of the world
- The number of parameters in the model
shuffle:: true

#### Question: Choice
id:: cae97098-99cf-44d5-b53d-f45004dd6211
content:: Why might a misaligned AI system that understands human values well be more dangerous than one that understands them poorly?
options::
- [x] It can predict what its overseers want to see and show that while pursuing other goals
- It will hold its own goals more strongly as its understanding grows
- It will try to change human values until they match its own goals
- It becomes harder to retrain once its understanding passes human level
shuffle:: true

#### Question: Choice
id:: fcbd03a5-54d3-4906-b4c3-d7b9781f89b1
content:: Does the distinction between understanding and caring imply that an AI system's understanding of human values is of no use for aligning it?
options::
- [x] No
- Yes

#### Question: Choice
id:: 37d1b43e-81eb-4da5-a71b-c8b6295fa32b
content:: Current chatbots usually follow instructions in the way users meant, not just their literal words. Is this consistent with the claim that understanding what humans want and being motivated by it are separate?
options::
- [x] Yes
- No

#### Question: Choice
id:: 150f9d59-963d-44d1-8f97-b84a40cff334
content:: Some researchers argue that systems built on large language models may be easier to align than older AI risk arguments assumed. Which of these is a reason they give?
options::
- [x] The models already represent human concepts, so training can aim at those concepts directly
- Text-trained models lack the planning ability needed to deceive their developers
- Models become more honest as their parameter count grows
- Pretrained models refuse harmful requests without any safety training
shuffle:: true

#### Question: Open
id:: 69609b39-1367-4d12-8547-de79bee874e8
content:: An agent's choices depend on its beliefs and its preferences. Explain which of the two a better understanding of human values improves, and why that does not by itself make an AI system act on those values.
assessment-instructions:: Score out of 100. 100 for saying understanding improves beliefs (its model of what humans want), while action also depends on preferences or goals, which are set separately, for example by training; better beliefs just help the system pursue whatever it already wants. 50 for naming beliefs without explaining why preferences stay unchanged.

#### Question: Open
id:: 0b2c7543-16be-4806-8697-b3b76f593084
content:: A friend says: "LLMs read most of the internet, so they've absorbed human values." In two or three sentences, say what this gets right and what it misses.
assessment-instructions:: Score out of 100. 100 for both: right that models learn detailed knowledge of human values and can describe and use it; misses that knowing values is not being motivated by them, since the text holds many conflicting values and motivation comes from training, which can instill other goals. 50 for only one of the two.

#### Question: Open
id:: 4ba3802d-a501-46ea-b269-cc8b7e2f727b
content:: An AI system says it cares about human wellbeing and behaves well in tests. Name one kind of evidence that would better show it cares, rather than just understands what testers want.
assessment-instructions:: Score out of 100. 100 for any one of: behaving the same when it believes it is unobserved or untested; behaving well where misbehaving would be rewarded or undetected; good behavior in situations far from its training; interpretability evidence about its internal goals. 0 for more of its own statements or more ordinary tests.
