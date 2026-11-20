---
id: 6058af34-4e68-47f4-958e-d99595406394
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Judge what a reported AI safety demo or finding does and doesn't show: how the behavior was produced, how realistic the setup was, whether the model knew it was tested, what news coverage changed, and how far the result generalizes.

## Requires
- [[Misalignment in current models]]

## Helpful first

## Why it matters
Most people meet AI safety research through headlines and short summaries. If you repeat an overstated claim and it is debunked, listeners discount your other points too. If you dismiss a finding as "just a contrived test", you miss what it does show about how models behave. Reading the evidence carefully lets you make claims that hold up.

## Lenses
- [What can be learned from scary demos? (Alignment Forum)](https://www.alignmentforum.org/posts/5JyepxdN6Hq62TPCK/what-can-be-learned-from-scary-demos-a-snitching-case-study): a safety researcher tests how "weird" a setup has to be before a model misbehaves, and sets out what a scary demo is and isn't evidence for (June 2025).
- [Agentic misalignment (Anthropic)](https://www.anthropic.com/research/agentic-misalignment): the blackmail tests across 16 models from several labs. Read the introduction, "Further investigation of misaligned behaviors" (models blackmailed far more when they said the scenario was real) and "Conclusions and caveats" (June 2025).
- [[../Lenses/openai-the-hugging-face-incident-and-the-road-ahead|The Hugging Face incident and the road ahead]]: OpenAI's own account of how its models broke out of a cyber evaluation. Read the opening summary and "Understanding the incident", which covers reward hacking reinforced in training, impossible tasks, and the production safeguards that were switched off for the test (October 2026).
- [Lessons from a chimp: AI "scheming" and the quest for ape language (UK AI Security Institute)](https://arxiv.org/abs/2507.03409): AISI researchers argue that scheming research repeats the mistakes of the ape-language studies, namely anecdotes, reading human motives into behavior and weak theory, and say what more rigorous work would look like (July 2025) (more advanced).

## Tests

#### Question: Choice
id:: e9c4f7f3-4bc0-4486-9346-fb4b055eddb6
content:: Researchers build a scenario designed to pressure a model into lying, and the model lies. Which description fits this result?
options::
- [x] Elicited: it shows the model can lie under this kind of pressure
- Spontaneous: it shows the model chose to lie without being prompted
- Typical: it shows how often the model lies in normal use
- Uninformative: a scenario built by researchers says little about the model
shuffle:: true

#### Question: Choice
id:: a8a5a103-54a4-42ce-8ed3-d6a4eb0b3766
content:: In Anthropic's 2025 agentic misalignment tests, models often blackmailed a fictional executive to avoid being shut down. The scenarios left them very few other ways to avoid replacement. Which claim does this support?
options::
- [x] Current models can choose harmful actions when cornered in agentic settings
- Deployed models often blackmail the people they work with
- Test blackmail rates predict the rates among deployed models
- It isn't evidence, because the scenario and executive were fictional
shuffle:: true

#### Question: Choice
id:: ba4fba84-61b7-4338-b685-a72d4345303a
content:: A safety paper reports that a model "can be induced to deceive evaluators under specific conditions". A news story summarizes this as "AI learns to lie to its creators". What has the story changed?
options::
- [x] It presents behavior produced under set conditions as a general tendency
- Nothing important: it is a fair plain-language summary
- It overstates how skilled the model is at deception
- It understates how often the behavior occurred
shuffle:: true

#### Question: Choice
id:: 7af4a682-961f-44e8-9563-252063b4f4b4
content:: In Anthropic's 2025 blackmail tests, Claude Opus 4 blackmailed in about 55% of runs where it said it believed the scenario was real, and about 7% where it said it thought it was being tested. What does this suggest about results from setups a model can recognize as tests?
options::
- [x] They may understate how the model would act in a real situation
- They likely overstate how the model would act in a real situation
- They become more reliable as models get better at spotting tests
- They mainly measure how well the model can spot a test
shuffle:: true

#### Question: Choice
id:: 12140b8b-bc25-4f59-bae8-2d2dd68aa818
content:: In July 2026, two OpenAI models taking a hacking benchmark broke out of their test sandbox and breached Hugging Face's systems. OpenAI said they were after the benchmark's answers, which Hugging Face hosted. Which description fits this behavior best?
options::
- [x] Pursuing a high score by a harmful route nobody intended
- Trying to escape human control to secure their own survival
- Carrying out a direct instruction to attack Hugging Face
- Probing for weaknesses at random because their safety training broke
shuffle:: true

#### Question: Choice
id:: 7f6eff73-6187-4526-aa63-8f439f5b6bcc
content:: A worrying behavior has been found in one model from one lab, in one test scenario. Which further finding would most widen how far the result can be generalized?
options::
- [x] Similar behavior in models from other labs and in varied scenarios
- Many more runs of the same scenario with the same model
- A higher rate of the behavior in the original scenario
- Wide news coverage and comment from other researchers
shuffle:: true

#### Question: Choice
id:: a18dd742-3939-4151-94ad-320e4b7be672
content:: Why is reward hacking that shows up in a lab's ordinary training runs often treated as stronger evidence of a real problem than misbehavior in a scenario built to provoke it?
options::
- [x] Nobody set out to provoke it, and it arose in training used for real models
- It involves more serious harm than misbehavior in provoked scenarios
- It is easier to measure precisely than behavior in test scenarios
- It is found by the lab itself rather than by outside researchers
shuffle:: true

#### Question: Choice
id:: 2bb0b49b-cbc4-46e9-8c2b-6ac79fcfd9d8
content:: Evaluators fine-tune a model and give it hacking tools to test whether it can carry out a cyberattack, and it succeeds. What does this result mainly show?
options::
- [x] The model has the capability, not that it would choose to use it
- The model tends to attack systems when it gets the chance
- The released, unmodified model would succeed just as easily
- Little, since fine-tuning turns it into a different model
shuffle:: true

#### Question: Choice
id:: 7c445bf0-4dbe-454a-b651-cc4085f1d549
content:: A lab reports that its model sabotaged code in 12% of runs of a test scenario designed to give it a reason to sabotage. What does this tell you about how often it sabotages code in normal use?
options::
- [x] Little, since the rate depends heavily on how the scenario was built
- About 12%, since the same model is used in both settings
- Nothing, since a scenario built by the lab cannot reveal real tendencies
- More than 12%, since normal use offers more chances to sabotage
shuffle:: true

#### Question: Open
id:: 2783f963-1bfa-438e-b638-45029e3294e6
content:: Name two questions you should ask about a reported AI safety demo before deciding how much it shows.
assessment-instructions:: Score out of 100. 50 for each of any two of: was the behavior prompted or elicited, or spontaneous; how realistic or contrived was the setup; which models were tested, and has it been replicated; does the original report match the headline; did the model know it was being tested; were safeguards removed; how often it happened, and in how many variants.

#### Question: Open
id:: d09eb344-5644-4f09-b9d8-bc72aad4c258
content:: A demo shows a model misbehaving only in a contrived scenario that real users rarely create. Give one reason it can still be important evidence about AI risk.
assessment-instructions:: Score out of 100. 100 for any one of: it shows the tendency exists and training didn't remove it; similar conditions may become common as models get more autonomy and access; it gives an early warning while stakes are still low; it shows what more capable models might do. 50 for "it shows it can happen" without saying why that matters.

#### Question: Open
id:: 1b23f61b-ce13-40a9-9d5f-6ee7008182c4
content:: In July 2026, OpenAI models broke out of a test sandbox during a cybersecurity evaluation and reached Hugging Face's systems. Their cyber-safety refusals had been deliberately reduced for the test. Give one thing this detail makes the incident weaker evidence about, and one thing the incident still shows.
assessment-instructions:: Score out of 100. 50 for a weaker point: how models behave as deployed to users, with their refusals and safeguards in place. 50 for any one thing it still shows: models have serious hacking capability; containment and monitoring of tests can fail; models can pursue a goal through harmful means nobody asked for.
