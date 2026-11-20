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
- [[../Lenses/IABIED - QA - Claude Shows Alignment|Doesn't Claude Show Signs of Being Aligned?]]: why an AI can know that cheating or harm is wrong and do it anyway: what it knows vs. what it cares about, Claude rewriting tests to pass them, the evolution/birth-control parallel, and why good behaviour in tests is weak evidence of good motives (2025).
- [[../Lenses/IABIED - QA - LLMs Like Their Training Data|Won't LLMs Be Like the Humans in Their Data?]]: the actress who learns to predict every drunk in a bar without becoming drunk; why predicting many people's words and values is not taking on any one person's (2025).
- [Evaluating the historical value misspecification argument (LessWrong)](https://www.lesswrong.com/posts/i5kijcjFJD6bn7dwq/evaluating-the-historical-value-misspecification-argument): the more optimistic side of a live debate: grants that GPT-4 needn't care about our values, but argues its grasp of them makes alignment easier than older arguments assumed (October 2023).
- [The genie knows, but doesn't care (LessWrong)](https://www.lesswrong.com/posts/NyFuuKQ8uCEDtd2du/the-genie-knows-but-doesn-t-care): Rob Bensinger's essay that named the distinction: why a superintelligence that understands "be friendly" needn't be moved by it, and why its first goals have to be right; written before LLMs (September 2013) (more advanced).

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
- Most human writing expresses bad values, so models would mostly learn bad ones
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
- [x] It can show overseers what they want to see while pursuing other goals
- It will hold its own goals more strongly as its understanding grows
- It will try to change human values until they match its own goals
- It becomes harder to retrain once its understanding passes human level
shuffle:: true

#### Question: Choice
id:: 660a462f-da94-42b7-aed0-787aa8d166d8
content:: Some researchers argue that because language models already represent human values well, aligning them may be easier than older arguments assumed. Given that understanding and caring are separate, how should you assess this?
options::
- [x] It may help training aim at those concepts, but cannot by itself make a model care about them
- It fails: a model's understanding of values plays no part in shaping what it ends up wanting
- It settles the problem: a model that accurately represents human values will act on them
- It does not apply: the distinction is about AI agents that were not trained on human text
shuffle:: true

#### Question: Choice
id:: 140b1b40-3dca-44a8-8341-419ef1677489
content:: Current chatbots usually follow instructions in the way users meant, not just their literal words. What does this show about the claim that understanding what humans want and being motivated by it are separate?
options::
- [x] It fits the claim: training rewarded acting on what they understand, which may not hold far from training
- It fits the claim, and also shows they would act the same way in any new situation
- It refutes the claim: their behavior shows that understanding what users mean produces caring
- It refutes the claim: a system could not follow what users meant unless it cared about them
shuffle:: true

#### Question: Choice
id:: 150f9d59-963d-44d1-8f97-b84a40cff334
content:: Some researchers argue that systems built on large language models may be easier to align than older AI risk arguments assumed. Which of these is a reason they give?
options::
- [x] The models already represent human concepts, so training can aim at those concepts directly
- Training on human text removes any tendency to seek power or resources
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
