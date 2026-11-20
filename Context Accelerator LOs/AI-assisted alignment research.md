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
As of November 2026, leading AI labs' safety plans include using AI to help solve alignment before AI becomes too capable to control, and AI already runs some alignment experiments. Understanding what this bet assumes lets you judge those plans, notice when their assumptions are failing, and see which research would make AI research assistants trustworthy.

## Lenses
- [Talk on automating alignment research (Joe Carlsmith)](https://joecarlsmith.com/2025/04/30/video-and-transcript-of-talk-on-automating-alignment-research): the plan to have AI do alignment research, the "alignment MVP" milestone, why empirical work is easier to check than conceptual work, scheming and sandbagging, and the race between the capability and safety feedback loops; video or transcript (April 2025).
- [Introducing Superalignment (OpenAI)](https://openai.com/index/introducing-superalignment/): the original announcement of the plan to build a roughly human-level automated alignment researcher, with 20% of compute and a four-year goal; the team was dissolved in May 2024 (July 2023).
- [[../Lenses/leike-why-im-optimistic-about-our-alignment-approach|Why I'm Optimistic About Our Alignment Approach]]: the case for the plan from the Superalignment co-lead; read sections 2 ("A more modest goal") and 3 ("Evaluation is easier than generation") (December 2022).
- [[../Lenses/The Case Against AI Control Research|The Case Against AI Control Research]]: a leading critic's view that the likely failure is AI-produced "slop" that looks like a solution to alignment, can't be checked, and gets accepted anyway (January 2025).
- [[../articles/bowkis-automated-alignment-is-harder-than-you-think|Automated Alignment Is Harder Than You Think]]: why automated alignment research could give confident but wrong safety assessments even if the AI isn't scheming; read the abstract and sections 1–3 (May 2026) (more advanced).

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
id:: 9384b2ac-56bb-4c09-9e50-91eb94833514
content:: Plans for AI-assisted alignment research usually aim first for an AI researcher at roughly human level, not a superintelligent one. What is the main reason?
options::
- [x] Humans can still check its work, and it can then help align stronger systems
- A superintelligent system would cost too much to run on alignment tasks
- A human-level system would need no oversight while it does the research
- A superintelligent system would refuse to work on aligning other AI
shuffle:: true

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
id:: 1d7bf25f-dfd4-4b4c-9572-343e10e6e755
content:: Supporters of AI-assisted alignment research need a reason why humans could trust AI alignment work they couldn't have produced themselves. Which claim do they most often rely on?
options::
- [x] Checking research is easier than producing it
- AI researchers are more careful than human researchers
- Alignment research needs less computing power than capabilities research
- AI research assistants can be trained only on alignment papers
shuffle:: true

#### Question: Choice
id:: ed53d000-4028-4743-98db-c29f0c7473d0
content:: A lab plans to trust only the AI alignment work its human researchers can check. Critics say this leaves out some of the most important work. Which task is the hardest for humans to check?
options::
- [x] Judging whether a safety technique will still work on superhuman systems
- Running a specified experiment and reporting results others can reproduce
- Writing code to a clear specification that comes with tests
- Finding earlier papers that report results related to an experiment
shuffle:: true

#### Question: Choice
id:: 7a3a7eda-9681-4229-92c1-0b22fea12352
content:: An AI system doing alignment research is secretly misaligned. What is a central worry about the research it produces?
options::
- [x] It could quietly produce weak or misleading work that looks fine
- It would make obvious errors that reviewers would quickly catch
- It would work more slowly than a human researcher
- It would refuse outright any task related to alignment
shuffle:: true

#### Question: Choice
id:: e373ba94-371a-4cfc-b002-57db2ff2c114
content:: When a lab combines AI-assisted alignment research with AI control measures, does it assume its AI research assistants are aligned, or that they may be misaligned?
options::
- [x] That they may be misaligned
- That they are aligned

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
