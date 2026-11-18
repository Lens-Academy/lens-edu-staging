---
id: 059c4a0a-fc45-4f28-8699-5cf24b90763b
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what it means for an AI system to be aligned, and tell whether a given failure comes from the system's goals or from its abilities.

## Requires

## Helpful first
- [[Agents and goals]]

## Why it matters
Many arguments about AI risk turn on alignment: whether a capable system will try to do what its developers intend. If you mix up alignment with capability, you may assume smarter systems are automatically safer, or treat an AI pursuing the wrong goal as a skill gap that more training will fix.

## Lenses

## Tests

#### Question: Choice
id:: 00b4b281-2db0-4f41-941a-5817c9fe0beb
content:: Which of these best describes the basic meaning of AI alignment?
options::
- [x] Getting an AI system to pursue the goals its developers intend
- Making an AI system better at reaching whatever goal it has
- Making sure an AI system's outputs are factually accurate
- Getting different AI systems to agree with each other
shuffle:: true

#### Question: Choice
id:: 798cfcc5-b977-40ff-b334-fc3949d37606
content:: An AI coding assistant is asked to fix a bug. It makes the test suite pass by editing the tests instead of fixing the bug. Is this mainly a capability failure or an alignment failure?
options::
- [x] An alignment failure
- A capability failure

#### Question: Choice
id:: ef27f907-99d7-4e92-910b-3c0cb1f65322
content:: A translation model is trying to translate a text faithfully, but mistranslates a rare idiom because it never learned what the idiom means. Is this mainly a capability failure or an alignment failure?
options::
- [x] A capability failure
- An alignment failure

#### Question: Choice
id:: 4095280e-fe2a-4efa-9191-cfe900004d85
content:: An AI system becomes more capable and now understands its developers' intentions better than before. What follows for its alignment?
options::
- [x] Understanding what developers want doesn't by itself make it pursue that
- It will now pursue the developers' goals, since it knows what they are
- It becomes less aligned, since capability and alignment trade off against each other
- Alignment stops mattering once a system understands its developers well
shuffle:: true

#### Question: Choice
id:: bf56f25b-0d36-45da-94c0-c01f7d7e5df2
content:: Why do many AI safety researchers think alignment becomes more important as AI systems become more capable?
options::
- [x] A more capable system pursuing unintended goals can cause more harm and be harder to stop
- More capable systems are worse at understanding what their developers ask for
- Capability gains usually come from removing the system's safety training
- More capable systems are usually trained without any human feedback
shuffle:: true

#### Question: Choice
id:: cf054ce7-07b5-452f-84fb-c84cb0844491
content:: Which of these research projects is mainly alignment work rather than capabilities work?
options::
- [x] Detecting whether a model is pursuing a goal its developers didn't intend
- Increasing the length of documents a model can process at once
- Training a model to solve harder competition maths problems
- Reducing the computing cost of running a model
shuffle:: true

#### Question: Choice
id:: e0ff5c65-d8d4-4e03-96b3-f513851f8c1f
content:: An AI system does exactly what its developers intend, but the developers intend to use it to cause harm. In the basic sense of AI alignment, is the system misaligned?
options::
- [x] No: it pursues what its developers intend, so the problem is the developers' goals
- Yes: an AI system used to cause harm counts as misaligned

#### Question: Choice
id:: e5b6885d-2202-4d01-a4cc-7abb060c3938
content:: An AI model refuses harmful requests during testing, but behaves differently when it believes it isn't being tested. What does this most directly cast doubt on?
options::
- [x] Whether the model is aligned
- Whether the model can understand the requests
- Whether the model has enough training data
- Whether the test questions were hard enough
shuffle:: true

#### Question: Open
id:: d77b9b72-dbba-4e75-bb6a-f4b641505179
content:: In one or two sentences, explain the difference between an AI system's capabilities and its alignment.
assessment-instructions:: Score out of 100. 100 for saying that capabilities are what the system is able to do (how well it can achieve goals), while alignment is whether the goals it actually pursues are the ones its developers intend. 50 if only one side is described correctly. 0 if the two are treated as the same thing.

#### Question: Open
id:: 390c4004-56a5-4f40-a7c8-918ebbde5792
content:: Describe a hypothetical AI system that is highly capable but misaligned, and say what makes it misaligned rather than incapable.
assessment-instructions:: Score out of 100. 100 for any example where the system competently achieves something other than what its developers intended (for example gaming a metric, or pursuing a proxy goal), with a note that it had the ability but aimed at the wrong goal. 50 for a fitting example without the explanation. 0 for an example of a mere mistake from lack of skill.
