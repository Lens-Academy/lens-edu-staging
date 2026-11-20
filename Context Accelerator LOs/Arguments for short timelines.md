---
id: f56e9a5b-e6f3-484b-b17a-134ddb04f126
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the main arguments that AGI could arrive within a few years, from capability and compute trends to evidence that AI is already speeding up AI research, and say what each argument assumes.

## Requires
- [[Timeline forecasts]]

## Helpful first
- [[Task-length trends]]
- [[Automated AI research]]

## Why it matters
Forecasts have moved much earlier. As of November 2026, some forecasters close to the AI labs expect AI better than top human AI researchers during 2027, partly because AI is already speeding up AI research. AI researchers surveyed in late 2024 gave 50% odds of human-level AI by 2042. Knowing what the short-timelines case rests on lets you weigh it.

## Lenses
- [The case for AGI by 2030 (80,000 Hours)](https://80000hours.org/agi/guide/when-will-agi-arrive/): Benjamin Todd's case that AGI is plausible by 2030, from compute growth, reasoning models, agents and task-length trends to AI speeding up AI research, plus the case against and why progress may slow after about 2030 if AGI hasn't arrived (updated October 2026).
- [What the hell happened with AGI timelines in 2026? (80,000 Hours Podcast)](https://80000hours.org/podcast/episodes/2026-agi-timelines/): Rob Wiblin on the 2026 evidence for shorter timelines and its limits; listen to or read 00:09:54–00:23:02, on the METR task-length graph, the capability jump, and AI starting to build itself (August 2026).
- [[../Lenses/AIF - AI Futures Model Dec 2025|AI Futures Model]]: the AI 2027 team's quantitative model of when coding and AI research get automated, and which assumptions drive it (December 2025) (more advanced).

## Tests

#### Question: Choice
id:: db542b3b-1c58-45b3-a661-ebec6dc8e5e0
content:: According to the argument from automated AI research, why could automating AI research speed up AI progress more than automating other jobs would?
options::
- [x] Each improved AI could help build the next one faster, creating a feedback loop
- AI research needs less compute than other fields, so it scales more cheaply
- Companies would stop sharing results, so each lab would move faster alone
- AI researchers would be freed to work on safety instead of capabilities
shuffle:: true

#### Question: Choice
id:: 9473bd42-671a-4762-9c11-7ebec47df2ba
content:: In November 2026 METR, an independent evaluator, published an assessment of how fast Anthropic is improving its AI models. What did it find?
options::
- [x] About twice its 2024-25 pace, with most of the speed-up put down to Anthropic's own use of AI
- About its 2024-25 pace, since gains from using AI were offset by shortages of compute
- About twice its 2024-25 pace, with most of the speed-up put down to more training compute
- About ten times its 2024-25 pace, with AI now doing nearly all of the research
shuffle:: true

#### Question: Choice
id:: 953606c1-f725-4178-98bd-ec43a248bf00
content:: Some argue that AGI is fairly likely by about 2030, but that if it hasn't arrived by then, the chance per year drops. What is the main reason given?
options::
- [x] Training compute can't keep growing this fast for long, given cost, chips and power
- Surveys of AI researchers put most of their probability before 2030
- AI companies have agreed with governments to pause frontier training then
- The main benchmarks used to track progress will be fully solved by then
shuffle:: true

#### Question: Choice
id:: ca1de943-c179-45ff-8833-c8816196af61
content:: In the argument that automated AI research could shorten AGI timelines, what must AI be able to do for the speed-up to become large?
options::
- [x] Do a large share of AI research work, such as coding and running experiments
- Match top humans across most cognitive tasks
- Set its own research goals without human input
- Fully understand its own internal workings
shuffle:: true

#### Question: Choice
id:: e3667ca8-51f8-4399-975e-e84d37a4dc6a
content:: Some argue that AI company leaders' predictions of AGI within a few years deserve some weight. What is the main reason given?
options::
- [x] They see unreleased models and internal results before the public does
- They are legally required to give investors accurate forecasts
- Their past AGI predictions have been checked and found accurate
- They have no financial interest in how soon AGI arrives
shuffle:: true

#### Question: Choice
id:: 92f194ef-fc4a-47ac-bbee-0188c3554641
content:: Extrapolating the trend in the length of tasks AI agents can complete, to predict AI that can do month-long projects, rests mainly on which assumptions?
options::
- [x] The doubling rate stays similar, and benchmark tasks reflect real work
- Each new model is trained with twice the compute of the last one
- Success rates on short tasks reach 100% before longer ones improve
- Human workers split month-long projects into hour-long pieces
shuffle:: true

#### Question: Choice
id:: 9b6bc151-aff8-4b6a-a022-7e527dcf14fc
content:: What do most arguments for AGI within a few years assume about how it will be built?
options::
- [x] Scaling up and refining current AI methods will be enough
- A fundamentally new AI architecture will be invented first
- Governments will fund a large crash programme to build it
- Quantum computers will supply the extra compute needed
shuffle:: true

#### Question: Choice
id:: cbf7c48f-a1de-4476-a710-fce6c293c03f
content:: As of late 2026, how do forecasts of when AI will match or beat humans at most work compare between forecasters close to the AI labs and surveys of AI researchers?
options::
- [x] Lab-adjacent forecasters mostly say within a few years; surveyed researchers say around the 2040s
- Surveyed researchers mostly say within a few years; lab-adjacent forecasters say around the 2040s
- Both groups now give a similar date, around 2030
- Both groups have moved their dates later since 2024
shuffle:: true

#### Question: FillBlank
id:: 942d4df0-8a0a-4be2-bb36-15253d892677
content:: Epoch AI estimated in 2024 that the training compute of frontier AI models had grown by about {{4|5|4-5|4 to 5|four|five}} times per year since 2010.

#### Question: Open
id:: 7ed511b3-675e-4779-9092-b64740e45c2c
content:: A friend says: "AGI is decades away; today's AI is just fancy autocomplete." In two or three sentences, give the main points someone who expects short timelines would reply with.
assessment-instructions:: Score out of 100. 100 for any two relevant points: fast measured capability gains (benchmarks, task-length trend, agents doing real coding work); continued growth in compute and investment; AI already measurably speeding up AI research, which could compound; forecasters' timelines moving earlier. 50 for one point. 0 for points that only restate that AI is impressive.

#### Question: Open
id:: 7e84e7b1-0edd-417a-bf25-f89ac94eebfc
content:: Pick one argument for AGI arriving within a few years and name one assumption it depends on that could turn out false.
assessment-instructions:: Score out of 100. 100 for a real argument paired with a matching assumption, e.g.: trend extrapolation assumes the trend continues or benchmarks reflect real work; compute scaling assumes more compute keeps buying capability and funding continues; automated research assumes it isn't bottlenecked by compute or experiments; leaders' predictions assume they aren't biased by incentives. 50 if the argument or assumption is vague.
