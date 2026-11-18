---
id: 8cd2347d-db3f-4176-8665-08c5334e3aa6
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the plan to have AI systems do much of the alignment research, and describe the main arguments that it can work and the main arguments that it will fail or come too late.

## Requires
- [[Automated AI research]]
- [[AI alignment]]

## Helpful first
- [[Scalable oversight]]
- [[AI control]]

## Why it matters
As of November 2026, several leading AI labs' safety plans rely on using AI to help solve alignment before AI becomes too capable to control safely. If you understand what this bet assumes, you can judge those plans, spot when their assumptions are failing, and see which research would make AI research assistants trustworthy.

## Lenses

## Tests

#### Question: Choice
id:: ebd6a3b2-f3b7-4b0e-84e1-7303e457c015
content:: Which of these is an example of AI-assisted alignment research?
options::
- [x] A model designs and runs interpretability experiments on another model
- A model writes faster code for training larger models
- A lab hires more human researchers to study model honesty
- A model is benchmarked on hard maths problems
shuffle:: true

#### Question: Choice
id:: 5237d10b-db4c-49ef-8d1d-dc2904237fd6
content:: OpenAI's Superalignment team, announced in 2023, planned to build an automated alignment researcher. How capable was that system meant to be?
options::
- [x] Roughly human-level
- Superintelligent

#### Question: Choice
id:: 4a3e2fe8-aa07-43bd-a3c4-912e3ba852ff
content:: The plan to have AI do much of the alignment research depends on an assumption about the order in which AI abilities arrive. Which assumption?
options::
- [x] AI becomes useful for alignment research before it becomes too dangerous to use
- Humans will solve alignment before AI can do any research
- AI systems will be aligned by default as they get more capable
- AI will speed up alignment research but not capabilities research
shuffle:: true

#### Question: Choice
id:: a18b154b-243f-4a89-98e5-2e3a12899caf
content:: Supporters of AI-assisted alignment research often argue that evaluating research is easier than producing it. If that is true, what would it allow?
options::
- [x] Humans could check AI alignment work they couldn't have produced themselves
- AI could check human alignment work without any human review
- Labs could deploy AI systems without testing them first
- AI could design its own training process without oversight
shuffle:: true

#### Question: Choice
id:: 26c0f836-45d4-4dfc-9c61-856a6f8699cb
content:: An AI system is doing alignment research for a lab. Which of these tasks would be easiest for the lab's human researchers to verify?
options::
- [x] Running a specified experiment and reporting results others can reproduce
- Proposing a new theory of why a training method makes models honest
- Judging whether a safety technique will still work on superhuman systems
- Deciding which alignment research agenda is most promising
shuffle:: true

#### Question: Choice
id:: 7a3a7eda-9681-4229-92c1-0b22fea12352
content:: An AI system doing alignment research is secretly misaligned. What is a central worry about the research it produces?
options::
- [x] It could quietly produce weak or misleading work that looks fine
- It would openly refuse every alignment task it is given
- It would work more slowly than a human researcher
- It would copy existing papers instead of doing new work
shuffle:: true

#### Question: Choice
id:: e373ba94-371a-4cfc-b002-57db2ff2c114
content:: When a lab combines AI-assisted alignment research with AI control measures, does it assume its AI research assistants are aligned, or that they may be misaligned?
options::
- [x] That they may be misaligned
- That they are aligned

#### Question: Choice
id:: a9a125a6-ac68-4f6a-8198-494bded313e9
content:: Suppose the same AI systems speed up a lab's capabilities research and its alignment research by the same factor. Does that by itself close the gap between capabilities and alignment?
options::
- [x] No
- Yes

#### Question: Open
id:: 0934c4ff-6a46-4d59-a81f-546de754cd17
content:: Critics say that relying on AI to do alignment research is circular. Explain the circularity.
assessment-instructions:: Score out of 100. 100 for: to trust an AI's alignment research we need the AI to be aligned (or its work to be fully checkable), but aligning AI is the problem the research is meant to solve. 50 for saying only that we can't trust the AI's work, without linking this back to the problem being solved.

#### Question: Open
id:: 8ea38593-5958-4abc-8a34-e3c81708f213
content:: Give one reason critics think alignment research may be harder to hand over to AI than capabilities research.
assessment-instructions:: Score out of 100. 100 for any one of: capabilities progress has clear measures (benchmarks, loss) while alignment success is hard to measure; alignment results are hard to check, especially for superhuman systems; mistakes may only show up once systems are dangerous; much alignment work is conceptual rather than experimental. 40 for a vague "alignment is harder" with no reason.

#### Question: Open
id:: 8114b612-272e-47b4-b96b-99db790a003b
content:: An AI lab says its safety plan is to use AI systems to solve alignment. Name one question you would ask to test whether this plan is credible, and say why it matters.
assessment-instructions:: Score out of 100. 100 for a relevant question with a reason, for example: how they will check the AI's work; how they will detect sabotage or sandbagging; how much AI effort goes to alignment versus capabilities; what they will do if the safe window is short; what would count as success. 50 for a relevant question with no reason.
