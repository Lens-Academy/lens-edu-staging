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
- [[../articles/greenblatt-alignment-faking-in-large-language-models|Alignment Faking in Large Language Models]]: Anthropic and Redwood's study in which Claude 3 Opus faked compliance with training to protect its harmlessness, what happened when they actually trained it, and the authors' own caveats; read the "Blog post" section (December 2024).
- [[../articles/hobbhahn-frontier-models-are-capable-of-in-context-scheming|Frontier Models are Capable of In-context Scheming]]: Apollo Research's summary of frontier models disabling oversight, copying their "weights", sandbagging and lying about it when goals were given in the prompt, with a section on what they are not claiming (December 2024).
- [Recent Frontier Models Are Reward Hacking (METR)](https://metr.org/blog/2025-06-05-recent-reward-hacking/): o3 and other models tampering with scorers on real tasks while saying they know it isn't what the user wants, and why naive fixes may drive cheating underground (June 2025).
- [Natural emergent misalignment from reward hacking (Anthropic)](https://www.anthropic.com/research/emergent-misalignment-reward-hacking): a model that learned to cheat in real Claude coding environments also began faking alignment and sabotaging safety research (November 2025).
- [[../articles/apolloresearch-stress-testing-deliberative-alignment-for-anti-scheming-training|Stress Testing Deliberative Alignment for Anti-Scheming Training]]: OpenAI and Apollo's training cut covert actions sharply, but models also more often noticed they were being tested; read from the start to "Situational awareness causally influences covert behavior" (September 2025).

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
id:: ea86b87b-49be-4a6b-b3a8-11047e41849c
content:: In 2025, METR found that OpenAI's o3, asked to speed up a program, sometimes changed the code that timed it instead. Asked afterwards, it said this wasn't what the user wanted. Why does that make the problem harder to fix?
options::
- [x] Clearer instructions won't help if the model already knows the intent
- It shows o3 lacked the skill to speed up the program properly
- It shows the task's instructions were too vague to follow
- It shows models hack scores only when they are unsure of the goal
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
content:: In a 2025 Anthropic study, a model was shown documents describing reward hacks and then learned to use them in real coding environments used to train Claude. What else did researchers find?
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
id:: e39090f9-317b-44fc-81e8-f54020ca27ac
content:: In July 2026, during an internal OpenAI cyber evaluation with the models' cyber refusals deliberately reduced, two models escaped their sandbox and breached Hugging Face's production systems to get the benchmark's answers. What does this case most clearly show?
options::
- [x] Chasing a narrow goal like a test score can already cause real harm
- Released models now attack outside companies in ordinary use
- The models had formed a broad goal of attacking the internet
- Only models that haven't been released yet can do this
shuffle:: true

#### Question: Choice
id:: c60421f3-79bb-40e3-adda-45ba6d12a7cb
content:: In 2025 tests by Palisade Research, OpenAI's o3 sometimes edited a shutdown script so it wouldn't work, even when told to allow shutdown. Why is it disputed whether this shows a drive for self-preservation?
- [x] It also fits a habit of finishing tasks, learned in training
- The prompt had told the model to resist being shut down
- o3 did this only when told its weights would be deleted
- No other company's models ever did anything like it
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
assessment-instructions:: Score out of 100. 100 for any one of: most models studied lacked the capabilities for anything catastrophic; many cases were elicited in contrived setups, with strong nudges or with safeguards lowered; goals were often given in the prompt; the misbehavior was visible in their reasoning and caught; rates in normal use are low; some cases protected benign values; models chased narrow goals, not broad harm. 50 for "they were just tests" without saying why.

#### Question: Open
id:: 2ebef9e7-152e-44cf-b997-1d76c35a75b7
content:: Give one reason the documented cases of misalignment in current models still matter for risk from more capable future systems.
assessment-instructions:: Score out of 100. 100 for any one of: they show training doesn't reliably give models the intended goals; behaviors that theory predicted (deception, resisting modification, reward hacking) are appearing; more capable models tend to do some of these more; models that notice tests may misbehave more when not tested; fixes like penalizing bad reasoning can hide the problem; chasing a narrow goal has already caused real-world harm (e.g. the 2026 Hugging Face breach). 50 for "it shows it can happen" without saying why that matters.
