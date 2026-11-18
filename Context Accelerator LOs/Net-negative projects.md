---
id: 468b78b6-4534-4265-b45f-7e9aefc172f7
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Spot the main ways a well-intended AI safety project can do more harm than good, and judge when holding back is the better choice.

## Requires

## Helpful first
- [[Capabilities externalities]]
- [[Information hazards]]

## Why it matters
Many of the most damaging mistakes made by people new to AI safety are well meant. If you check a plan for side effects, including how others will react to it, you can catch harms before they happen instead of adding to the problem you set out to solve.

## Lenses

## Tests

#### Question: Choice
id:: a37eb92c-ea35-4605-9da8-ccc8b2dbdabb
content:: What does it mean to call an AI safety project "net-negative"?
options::
- [x] Its overall effects, good minus bad, are worse than not doing it.
- It has at least one harmful side effect.
- It fails to reach the goal it set out to achieve.
- It costs more money than it brings in.
shuffle:: true

#### Question: Choice
id:: 90cc7c53-e1e0-4877-b3ae-969f5b707340
content:: RLHF (reinforcement learning from human feedback) was developed partly as a safety technique. Why do some people count it as safety work that sped up AI capabilities?
options::
- [x] It made chatbots far more useful, which drew investment into AI.
- It let labs train new models without any pre-training.
- It made models less useful, pushing labs to scale up instead.
- It was mainly adopted to train models to write code.
shuffle:: true

#### Question: Choice
id:: f8628130-5e01-4279-b812-bd35fd9228b2
content:: In discussions of AI safety outreach, what does "poisoning the well" refer to?
options::
- [x] Making an idea look bad, so later, better efforts get a cold reception.
- Feeding false data to an AI system during its training.
- Spreading dangerous technical details to a wide audience.
- Hiring researchers away from other safety groups.
shuffle:: true

#### Question: Open
id:: 5c087045-a49f-415b-b464-a565cd1ad70f
content:: Give one way a well-meant campaign to warn policymakers about AI risk could make future AI safety advocacy harder.
assessment-instructions:: Score out of 100. 100 for any one plausible mechanism, such as: exaggerated or failed predictions cost credibility; a poorly argued or extreme message makes the issue look fringe, so later warnings are dismissed; it ties the issue to one political side; it annoys or burns contacts who are hard to win back. 50 for a vague answer like "it could backfire" without a mechanism.

#### Question: Choice
id:: c9120d92-ea3c-4e81-9fe9-0ab77a19c0df
content:: A researcher finds a cheap way to make a widely used chatbot give step-by-step help with making a dangerous pathogen. Which first step best lowers the chance that the finding does more harm than good?
options::
- [x] Tell the chatbot's developer privately, then decide what to publish.
- Publish the full method at once so everyone can respond.
- Post a detailed thread on social media to raise public alarm.
- Test the method on several more chatbots before telling anyone.
shuffle:: true

#### Question: Choice
id:: 307a8f4e-60c8-4f81-8f00-b4f6a6e7cbb2
content:: What is a commonly cited example of AI risk advocacy having roughly the opposite effect to the one intended?
options::
- [x] Concern about AGI helped inspire the founding of DeepMind and OpenAI.
- Warnings led governments to ban open-source AI research.
- Talks on AI risk caused safety research funding to fall.
- Alarm about AI led labs to stop publishing safety research.
shuffle:: true

#### Question: Choice
id:: e98e2666-ca89-4fed-bde9-0121bfe2c553
content:: Ten researchers each judge for themselves whether to publish a risky finding, and any one of them can publish it alone. According to the "unilateralist's curse", what tends to happen?
options::
- [x] It gets published if the most optimistic researcher thinks it's fine.
- It gets published only if most of the researchers agree.
- It stays unpublished because each researcher defers to the others.
- The researchers' average judgement decides whether it is published.
shuffle:: true

#### Question: Open
id:: 17467516-6a77-484c-955a-af92e1198e2f
content:: You are considering a project that you think is good but that others in AI safety might see as risky. What is one practical way to guard against the unilateralist's curse?
assessment-instructions:: Score out of 100. 100 for any one of: ask several informed people in the field for their views before acting; give their concerns real weight and hold back if many think it's harmful; agree a shared decision process with others who could act; start small and reversible while you gather views. 50 for "be careful" or "think harder" with no outside check.

#### Question: Choice
id:: 3c6837c7-3085-4956-a566-cb1964ce0250
content:: A safety group builds an impressive demo of a dangerous AI capability to alarm the public. How could this make AI risk worse?
options::
- [x] It shows others the capability is reachable and worth pursuing.
- It makes the capability harder for AI companies to build.
- It reduces public interest in AI and its risks.
- It breaks laws on AI testing in most countries.
shuffle:: true

#### Question: Choice
id:: 50f8c43f-ad7c-41c1-a5ac-40467a2bfd04
content:: A newcomer starts a low-quality AI safety newsletter for a language with few resources on the topic. How could it be net-negative even if it causes no direct harm?
options::
- [x] It takes the niche, so a better project is less likely to start.
- It may speed up AI capabilities research in that country.
- It counts as an information hazard under most definitions.
- It reduces the number of AI safety resources in that language.
shuffle:: true

#### Question: Choice
id:: a99b5382-5182-4e78-85d3-c63144fcc3ed
content:: A project has a 90% chance of a small benefit and a 10% chance of a harm ten times bigger than that benefit. Is its expected value positive or negative?
options::
- [x] Negative
- Positive

#### Question: Choice
id:: 282b0bb1-fbef-4840-b3d2-9c6729554588
content:: The claim that "doing nothing can beat doing harm" is often made about AI safety projects. Which of these does it imply?
options::
- [x] A project should be expected to do more good than harm, not just be well meant.
- Newcomers should avoid working on AI risk until they become experts.
- Inaction is the safest default for anyone new to the field.
- Projects with a chance of causing harm should be dropped.
shuffle:: true

#### Question: Open
id:: 0731a3e4-32f8-4844-82f1-e7e2f129dca2
content:: A team plans to release a free tool that makes it easy to test AI models for dangerous capabilities. Describe one indirect effect that could make the release net-negative.
assessment-instructions:: Score out of 100. 100 for any one of: developers use it as a target and train models to pass it without being safer; it helps people find or build the most capable models for misuse; passing it gives false reassurance; it shows what dangerous capabilities look like and how to elicit them. 50 for a harm with no clear mechanism.

#### Question: Open
id:: f9fdbdaf-68bd-488f-91e2-5802f352f6d5
content:: Name two different ways a well-meant AI safety project could end up doing more harm than good.
assessment-instructions:: Score out of 100. 50 for each distinct way, such as: speeding up AI capabilities; spreading hazardous information; damaging the field's reputation or credibility; fuelling race dynamics or inspiring competitors; taking a niche from a better project; using up funders' money or experts' time; giving false reassurance. Two versions of the same mechanism get 50.

#### Question: FillBlank
id:: 44141ba0-381e-452a-b69d-c63c147b9928
content:: When it's unclear whether a project's overall effect on AI risk is good or bad, people say the {{sign}} of its impact is uncertain.
