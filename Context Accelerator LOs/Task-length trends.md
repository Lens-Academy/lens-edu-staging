---
id: 3eb9931c-50f1-4247-8fd6-58eb07318b8a
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Read METR's time-horizon graph: explain what a model's time horizon measures, what a straight line on its log scale and a doubling time imply, and give the main reasons to question what the trend shows.

## Requires
- [[Benchmarks]]
- [[AI agents]]

## Helpful first

## Why it matters
The time-horizon trend is often cited in debates about how soon AI agents could do long, independent work, including AI research. Reading it correctly lets you judge forecasts built on it, and spot both overclaims ("AI can now do day-long jobs") and dismissals that ignore a steady, measured trend.

## Lenses

## Tests

#### Question: Choice
id:: 1ebdc854-4213-4874-971a-e637cadd668e
content:: METR reports that an AI model has a 50% time horizon of two hours. What does this mean?
options::
- [x] It succeeds on about half of tasks that take skilled humans two hours
- It works on its own for two hours before failing, half the time
- It finishes tasks in half the time skilled humans take, up to two hours
- It succeeds on half of the tasks it can attempt within two hours
shuffle:: true

#### Question: FillBlank
id:: a0a13e78-b28b-4eb8-886b-ab175eb9e6cd
content:: In METR's March 2025 analysis, the 50% time horizon of frontier AI models had doubled about every {{7|seven}} months since 2019.

#### Question: Choice
id:: 597e0b23-6b61-4588-985c-2ad4a54d09cd
content:: METR plots AI models' time horizons against release date, with the time-horizon axis on a log scale. What does a straight upward line on this graph mean?
options::
- [x] The time horizon multiplies by the same factor each year
- The time horizon grows by the same number of hours each year
- The time horizon's growth is slowing down over time
- The time horizon grows faster each year than the year before
shuffle:: true

#### Question: Choice
id:: 2dda42bb-7e7c-44e7-b022-332999b27ad1
content:: An AI model's 50% time horizon is 2 hours, and the time horizon doubles every 7 months. If the trend holds, about how long until a model's time horizon reaches 16 hours?
options::
- [x] About 21 months
- About 7 months
- About 14 months
- About 56 months
shuffle:: true

#### Question: Choice
id:: 1b5dece0-7124-46c7-a8cf-267b79a0274a
content:: METR usually reports time horizons at a 50% success rate. If it measured the same model at an 80% success rate instead, how would the time horizon compare?
options::
- [x] Much shorter
- About the same
- Much longer
shuffle:: true

#### Question: Choice
id:: 68b30c6d-985e-4fa9-91a3-3d0400ff8368
content:: In METR's time-horizon work, how is the length of each task mostly measured?
options::
- [x] By timing skilled human professionals doing the task
- By timing how long the AI agent takes on the task
- By counting the steps the AI agent needs to finish
- By asking AI models to estimate how hard the task is
shuffle:: true

#### Question: Choice
id:: d12bae13-af06-454d-8e04-549376a85189
content:: A model has a 50% time horizon of four hours on METR's tasks. What is the strongest reason to doubt it could do half of four-hour tasks in a typical office job?
options::
- [x] The tasks are mostly well-defined software tasks with automatic scoring
- The task lengths were set by the AI developers being tested
- The models had already seen the exact tasks during training
- The tasks were timed with models running far faster than humans
shuffle:: true

#### Question: Choice
id:: 4333f835-4393-4fc2-b56a-98e94d9966ba
content:: Why are METR's time-horizon estimates for the newest frontier models less certain than its estimates for older models?
options::
- [x] Its task suite has few tasks as long as these models' horizons
- Newer models refuse many of the tasks in its suite
- Newer models are tested with less computing power than older ones
- Its human baselines were collected before these models were released
shuffle:: true

#### Question: Open
id:: b93c1245-c6fa-4451-a0f5-29c9752527ce
content:: Why can the time horizon track AI progress over many years better than a single benchmark's percentage score?
assessment-instructions:: Score out of 100. 100 for the idea that a fixed benchmark saturates (scores bunch near 100% and stop showing progress), while time horizon is an open-ended scale where longer tasks can be added, so models from different years sit on one comparable scale. Also accept: it is in human-meaningful units (hours of skilled work). 50 for "it measures real tasks" without the scale point.

#### Question: Open
id:: 41a37f00-5afb-447a-9b2f-a1823f5a566a
content:: METR's human baseliners were skilled professionals, but new to each task and its codebase. How might this affect the measured task lengths compared with an experienced employee who knows the codebase?
assessment-instructions:: Score out of 100. 100 for: the baseliners would take longer than an experienced employee, so measured task lengths (and so time horizons, in employee terms) are likely overstated; tasks would take an insider less time. 50 for noting the baselines may not match real workers without saying in which direction.

#### Question: Open
id:: 48dac632-1ec4-47ee-be28-76b97d67ce38
content:: Give one reason the growth of AI time horizons could speed up in coming years, and one reason it could slow down.
assessment-instructions:: Score out of 100. 50 for a speed-up reason, for example: AI systems helping with AI research, growing investment and compute, better agent training. 50 for a slow-down reason, for example: limits on compute, energy, money or data; longer tasks being messier and harder to train on; the trend being an empirical pattern with no guarantee it continues.
