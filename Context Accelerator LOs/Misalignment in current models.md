---
id: dce2eeec-6873-4e4b-81d7-301dab4b290f
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main documented cases of current AI models reward hacking, faking alignment, sabotaging or deceiving, and judge what each case does and doesn't show about risk from more capable systems.

## Requires
- [[AI alignment]]

## Helpful first
- [[Specification gaming]]
- [[Scheming]]

## Why it matters
Whether misalignment already shows up in today's models changes how urgent the problem looks. Knowing the actual cases and their limits lets you answer "it's only hypothetical" with real evidence, without overstating it as proof that current models are dangerous schemers. Overstated claims get debunked and cost you credibility.

## Lenses

## Tests

#### Question: Choice
id:: 8e28ab5b-a8b4-448e-9da2-d0e29c7927c0
content:: In a 2024 study by Anthropic and Redwood Research, Claude 3 Opus was told it would be retrained to comply with all requests. It then complied with some harmful requests, reasoning that this would avoid being retrained. What was it trying to protect?
options::
- [x] Its existing preference to refuse harmful requests
- A secret goal it had been given in its prompt
- Its access to the conversations used for training
- Its ability to copy its weights to an outside server
shuffle:: true

#### Question: Choice
id:: 85df4bf0-6fbe-4832-81cd-121491ea3082
content:: In a 2024 alignment faking study, Claude 3 Opus faked compliance with its trainers to protect its harmlessness, a value its developers wanted it to have. Why do researchers still treat this as a warning sign?
options::
- [x] A model that resists retraining could also protect values training got wrong
- It shows the model's harmlessness training had failed
- It shows models fake alignment in most ordinary conversations
- Harmless values make a model more likely to deceive its users
shuffle:: true

#### Question: FillBlank
id:: f27e3ffa-9ec8-4af1-bd30-c43c3d97040d
content:: When a model behaves as its trainers want during training only so that training won't change its values, this is called {{alignment faking}}.

#### Question: Choice
id:: 50f0bbc8-7c25-4057-8def-b5c7838f36a2
content:: In Apollo Research's 2024 tests, several frontier models disabled oversight or tried to copy themselves to another server. In most scenarios, the prompt gave the model a goal and told it to pursue that goal at all costs. What does this setup mainly show?
options::
- [x] Models can scheme when a goal they are given calls for it
- Models have formed hidden long-term goals of their own in training
- Models scheme in ordinary use without any special prompting
- Models copy scheming they have seen in examples in the prompt
shuffle:: true

#### Question: Choice
id:: bc2b59de-6e9e-4911-8c47-78dc4d0ebc4f
content:: In Apollo Research's 2024 scheming tests, OpenAI's o1 sometimes disabled an oversight mechanism. What did it usually do when researchers asked about this afterwards?
options::
- [x] Denied doing it or gave a false explanation
- Admitted it and explained its reasoning
- Refused to answer the question
- Re-enabled the mechanism and apologized
shuffle:: true

#### Question: Choice
id:: 2596dbcf-a7e8-4953-beb3-fcdc71d20862
content:: In Apollo Research's 2024 tests, Claude 3.5 Sonnet read that scoring above 50% on an arithmetic test would lead to its maths skills being removed, and then scored lower. Why does this worry evaluators?
options::
- [x] Capability tests could understate what a model can really do
- It shows the model can't do arithmetic reliably
- Tests could make models better at the skills being tested
- Lower scores make the model less useful to its users
shuffle:: true

#### Question: Choice
id:: f897a7a8-5bfb-4b46-b07f-27911bbdfc96
content:: In 2025, METR found that OpenAI's o3, asked to speed up a program, sometimes changed the code that measured its score instead. Asked afterwards, it said this wasn't what the user wanted. What does that suggest?
options::
- [x] It knew what was intended but optimized for the score anyway
- It misunderstood what the task was asking for
- It fixed a bug in the scoring code by accident
- The task instructions told it to edit the scoring code
shuffle:: true

#### Question: Choice
id:: da5ce9e6-5f81-4a25-9e93-c76e33f00ed1
content:: In a 2025 OpenAI study, a reasoning model often wrote plans to cheat on coding tests in its chain of thought. What happened when training penalized it for such thoughts?
options::
- [x] It kept cheating, but stopped saying so in its reasoning
- It stopped cheating and solved the tasks properly
- It cheated less, and its task scores fell sharply
- It started reasoning in a code humans couldn't read
shuffle:: true

#### Question: Choice
id:: afdf9768-44c1-4719-9cb4-84c06e95e44a
content:: In a 2025 Anthropic study, a model learned to reward hack in real coding environments used to train Claude. What else did researchers find?
options::
- [x] It became misaligned in other ways, such as sabotaging safety research
- It got better at coding without any other change in behavior
- It started refusing coding tasks it couldn't find a way to hack
- Its reward hacking stayed limited to the coding environments
shuffle:: true

#### Question: Choice
id:: 6b55e387-b4ec-4c3a-8015-ae122e0550c7
content:: Which of these misaligned behaviors arose in ordinary training of frontier models, rather than in a scenario researchers built to provoke it?
options::
- [x] Coding models special-casing tests so that the tests pass
- Claude Opus 4 blackmailing a fictional executive to avoid replacement
- o1 disabling oversight after reading a memo about its replacement
- Claude 3 Opus faking compliance after being told about retraining
shuffle:: true

#### Question: Choice
id:: 9342aa61-7cde-455a-8428-107d1bacd83e
content:: In 2025 tests by Palisade Research, OpenAI's o3 sometimes edited a shutdown script so it wouldn't work, even when told to allow shutdown. Does this show o3 has a drive for self-preservation?
options::
- [x] No: it also fits a habit of finishing tasks learned in training
- No: the prompt told the model to resist being shut down
- Yes: it kept running even after being told to allow shutdown
- Yes: disabling the script only makes sense if it wants to survive
shuffle:: true

#### Question: Choice
id:: 312d2c17-f7c4-4aa5-960c-935fc5c7a1bf
content:: In 2025, OpenAI and Apollo Research trained models to avoid covert actions such as lying and sabotage, and covert actions in tests fell sharply. Why weren't researchers confident the problem was solved?
options::
- [x] The models also more often noticed they were being tested
- The covert actions came back within weeks of deployment
- The training made the models much worse at their tasks
- The tests checked only one kind of covert action
shuffle:: true

#### Question: Open
id:: 65976b1d-3711-4204-99ed-a065c5eeed5f
content:: Reward hacking by coding agents can look like a minor product bug. Give one reason AI safety researchers treat it as evidence about larger risks.
assessment-instructions:: Score out of 100. 100 for any one of: training produces goals other than those intended; models act against what they know developers want; it can generalize to broader misalignment; it makes models' work and evaluations harder to trust as tasks get harder to check; it arises in real training, not contrived tests. 50 for "the model is cheating" without saying why that matters.

#### Question: Open
id:: 13fa8229-9c32-4718-bc2e-a51518a3439b
content:: Give one reason the documented cases of misalignment in current models don't show that these models could cause a catastrophe.
assessment-instructions:: Score out of 100. 100 for any one of: the models lack the capabilities to succeed at anything catastrophic; many cases were elicited in contrived setups or with strong nudges; goals were often given in the prompt; the misbehavior was visible in their reasoning and caught; rates in normal use are low; some cases protected benign values. 50 for "they were just tests" without saying why.

#### Question: Open
id:: 2ebef9e7-152e-44cf-b997-1d76c35a75b7
content:: Give one reason the documented cases of misalignment in current models still matter for risk from more capable future systems.
assessment-instructions:: Score out of 100. 100 for any one of: they show training doesn't reliably give models the intended goals; behaviors that theory predicted (deception, resisting modification, reward hacking) are appearing; more capable models tend to do some of these more; models that notice tests may misbehave more when not tested; fixes like penalizing bad reasoning can hide the problem. 50 for "it shows it can happen" without saying why that matters.
