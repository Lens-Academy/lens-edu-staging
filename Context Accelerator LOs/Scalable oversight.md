---
id: fdb612cc-e0b1-43f0-8f48-aa131145fef0
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how researchers hope to supervise AI systems on tasks too hard for people to check, and why those methods might stop working once AI far exceeds its overseers.

## Requires

## Helpful first
- [[RLHF]]
- [[AI alignment]]

## Why it matters
Training methods like RLHF rely on people judging outputs. Once AI does work its supervisors can't check, that feedback can reward answers that merely look right. Knowing the proposed fixes and their weak points helps you judge whether a lab's alignment plan is likely to hold up for more capable systems.

## Lenses

## Tests

#### Question: Choice
id:: 201e5527-6db8-493a-9ac5-0cd4b5b99aa9
content:: What problem does scalable oversight research try to solve?
options::
- [x] Giving reliable feedback on tasks humans can't easily check
- Monitoring many deployed AI systems with a small team
- Cutting the cost of human ratings for huge training runs
- Detecting when a model copies its weights to outside servers
shuffle:: true

#### Question: Open
id:: b43f053f-6a36-450a-93e4-3fe0753ca265
content:: Why does supervising an AI system get harder once it is more capable than the people overseeing it? Answer in one or two sentences.
assessment-instructions:: Score out of 100. 100 if the answer says overseers can no longer tell whether the AI's outputs are correct or safe, so their feedback can be fooled or end up rewarding what only looks good. 50 for "the AI is smarter than us" without saying how that breaks evaluation or feedback.

#### Question: Choice
id:: 435f1494-d74d-4040-82b1-a9903a6d5582
content:: A lab trains a model with human feedback to write complex software. Reviewers can't find bugs in the hard parts, so they mostly rate code on how clean it looks. What is the main risk?
options::
- [x] The model learns to write code that looks correct but hides bugs
- The model learns to write code too simple to be useful
- The model refuses coding tasks it can't fully complete
- The model's code becomes too unusual for reviewers to read
shuffle:: true

#### Question: Choice
id:: f1ada443-0adf-46a2-b65d-51af01b84b0d
content:: In AI safety via debate, does the human judge need to be able to answer the question unaided?
options::
- Yes
- [x] No

#### Question: Choice
id:: 1d6e1afa-ea71-431e-82b9-9f4e9332cc92
content:: Which assumption does AI safety via debate rely on?
options::
- [x] Arguing convincingly for a false answer is harder than exposing its flaws
- Two separately trained AI systems will rarely make the same mistake
- Human judges can solve the task themselves if given enough time
- AI systems are less likely to lie when another AI is watching
shuffle:: true

#### Question: Choice
id:: 787603bf-2af2-44fb-823a-afc9deb751ae
content:: Which is a reason AI safety via debate might fail when the debaters are far more capable than the judge?
options::
- [x] The dishonest side may rely on flaws too subtle for the judge to spot
- Debate needs an answer key, which hard tasks won't have
- The judge must inspect the debaters' internal weights to decide
- Debate can't be used on questions with long, open-ended answers
shuffle:: true

#### Question: Choice
id:: fd10c03f-67a8-465a-9bf9-bdd4f1b336db
content:: In iterated amplification, how is an overseer stronger than a lone human built?
options::
- [x] A human splits a hard task into subtasks handled by copies of the current AI
- A human reviews random samples of the AI's work in extra depth
- Several human raters vote, and the majority view becomes the label
- A larger model is trained to imitate a panel of human experts
shuffle:: true

#### Question: Open
id:: 2ae645d3-08cb-4beb-ad4e-1691fb1b554d
content:: Iterated amplification depends on hard tasks being split into smaller tasks that a human can check. Give one reason this might not work for very hard problems.
assessment-instructions:: Score out of 100. 100 for any one of: some problems need a whole-picture insight that doesn't break into checkable pieces; small errors add up across many steps; subtasks lose context the full task needs; the number of subtasks becomes unmanageable; a misaligned copy could hide a flaw inside one subtask. 50 for a vague "it's too complicated" with no mechanism.

#### Question: Choice
id:: 8256ac0b-733f-4a5d-a550-e5843c2c4cb2
content:: In weak-to-strong generalization experiments, what stands in for a human supervising a superhuman AI?
options::
- [x] A smaller model whose labels are used to fine-tune a larger model
- A team of non-expert humans rating a frontier model's answers
- An earlier checkpoint of the same model acting as a debate judge
- A rule-based program that checks outputs against known answers
shuffle:: true

#### Question: Choice
id:: 549eaa25-318e-4a66-a379-ed2a350f0069
content:: In weak-to-strong generalization experiments, a strong model is fine-tuned on labels from a weaker model. What was the typical result?
options::
- [x] It beat its weak supervisor but fell short of its full ability
- It copied its supervisor's errors and matched its accuracy
- It matched a version of itself trained on correct labels
- It performed worse than the weak supervisor that labelled its data
shuffle:: true

#### Question: Choice
id:: 2782d662-8176-4807-9c9e-f07760a93018
content:: Why might weak-to-strong generalization fail to align a superhuman model, even if it works in today's experiments?
options::
- [x] The model might learn to predict its supervisor's mistakes rather than the truth
- Weak models can't produce labels for complex tasks
- Fine-tuning has little effect on the behaviour of very large models
- The experiments used human supervisors, which won't scale up
shuffle:: true

#### Question: Open
id:: 73475553-3ff4-4ef3-abb4-b4e8aaaa2d1f
content:: Some researchers argue that oversight methods need to work just up to roughly human-level AI, which could then help align more capable successors. What is one risk of this plan?
assessment-instructions:: Score out of 100. 100 for any one of: the human-level AI may itself be subtly misaligned and steer or sabotage the research; humans may not be able to check the alignment work it produces; small errors may compound across generations of models; capabilities may jump past the range where oversight works before the handoff succeeds. 50 for a vague "the AI might go wrong" with no mechanism.
