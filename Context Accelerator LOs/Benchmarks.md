---
id: f19a40ad-d405-4501-a6c9-2e3ab9f0e676
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how benchmarks are used to measure AI capabilities, and judge what a benchmark score does and doesn't tell you about a model's abilities in real use.

## Requires
- [[Machine learning]]

## Helpful first

## Why it matters
AI labs, journalists and researchers report progress as benchmark scores, and debates about how fast AI is advancing lean on them. Labs also use tests to decide what safeguards a model needs. Knowing how scores can be inflated or miss real-world skill helps you tell a real jump in ability from a number that mostly reflects the test.

## Lenses
- [[../Lenses/AI Safety Atlas - Evaluations - Benchmarks|Benchmarks]]: what a benchmark is and how benchmarks shape AI progress; examples such as MMLU and the "Google-proof" GPQA; FrontierMath going from under 2% to 25% in months; and the limits: training-data contamination, memorisation versus understanding, and why better benchmarks still aren't enough (examples up to early 2025).
- [GPT-4 and professional benchmarks: the wrong answer to the wrong question (AI as Normal Technology)](https://www.normaltech.ai/p/gpt-4-and-professional-benchmarks): two well-known critics show GPT-4 solving old coding problems but none published after its training cutoff, and argue that human exams like the bar don't measure real professional skill in a model (March 2023).
- [The real reason AI benchmarks haven't reflected economic impacts (Epoch AI)](https://epoch.ai/gradient-updates/the-real-reason-ai-benchmarks-havent-reflected-economic-impacts): why benchmarks have been built from short, well-specified tasks "just within reach" rather than realistic work, and so say little about real-world usefulness (March 2025).
- [Why benchmarking is hard (Epoch AI)](https://epoch.ai/gradient-updates/why-benchmarking-is-hard): how prompts, settings, scaffolds and API providers can shift a model's score by 10 points or more, and why small gaps between models are often within noise (December 2025) (more advanced).

## Tests

#### Question: Choice
id:: 329939e9-0b9a-4b72-b355-7dfb20efd5c6
content:: An AI model scores 85% on a benchmark's published questions but only 60% on new questions written in the same style and at the same difficulty. What is the most likely explanation?
options::
- [x] The published questions were in its training data
- The new questions turned out harder than intended
- The model got worse between the two tests
- The two sets of questions test different skills
shuffle:: true

#### Question: Choice
id:: 2a494bd2-9576-4f5f-a231-7ec7a48af36a
content:: Lab A reports that its model scores 70% on a coding benchmark; Lab B reports 55% for its model. Which extra fact would most weaken the conclusion that A's model is the better coder?
options::
- [x] A reported its best of ten attempts, B a single attempt
- A's model was trained with more compute than B's
- Both scores were checked by an independent group
- B's model costs less to run per task
shuffle:: true

#### Question: Choice
id:: 75d7e18e-df62-4ac5-9a83-a41f7df5db2a
content:: Over the past decade, how has the time between a new AI benchmark's release and top models scoring near human level on it tended to change?
options::
- [x] It has got shorter
- It has got longer
- It has stayed roughly the same
shuffle:: true

#### Question: Choice
id:: 4ead4446-bc28-4ff7-b2af-c06ec9c46de1
content:: An AI model scores higher than most human test-takers on a written medical licensing exam. What does this most directly show?
options::
- [x] It answers that exam's kind of written questions well
- It could safely replace doctors in routine care
- It understands medicine the way trained doctors do
- It would do as well examining real patients
shuffle:: true

#### Question: Choice
id:: cd1d4211-6c18-492a-9e44-b4b2204909a1
content:: Some science benchmarks are built so that skilled non-experts score poorly on them even with unlimited web access and plenty of time. What is this design mainly meant to ensure?
options::
- [x] High scores reflect expert reasoning, not just looking answers up
- The questions can never end up in a model's training data
- Models are unable to search the web while they are tested
- Answers can be graded automatically without needing experts
shuffle:: true

#### Question: Choice
id:: f0ec8a8d-d5a5-4bac-aafb-17b3913ab8a6
content:: A new AI benchmark is released, and the best current model scores 2% on it. Going by how recent hard benchmarks have fared, what is the most reasonable expectation?
options::
- [x] Top scores will likely rise a long way within a year or two
- Scores will likely stay low for years, as the questions need deep expertise
- The low score likely shows current methods have hit a limit on such tasks
- Scores will likely rise only after the answers leak into training data
shuffle:: true

#### Question: Choice
id:: 4d5c395d-f87f-4987-b926-a2df9962477f
content:: On a benchmark where about 5% of the official answers are known to be wrong, model A scores 88% and model B scores 89%. Does this show that B is more capable?
options::
- [x] Not on its own: a 1-point gap is within the test's noise
- Yes, as long as both used the same prompts and settings
- Yes, as long as neither was trained on the questions
- Yes, since wrong answer keys affect both models equally
shuffle:: true

#### Question: FillBlank
id:: b736c9ba-0e65-4cfe-8e2c-b2d04e5ac594
content:: When top AI models score close to the maximum on a benchmark, so that it can no longer tell them apart, the benchmark is said to be {{saturated}}.

#### Question: Open
id:: efb4018e-3966-4a90-960a-886b82a5da1e
content:: Give two reasons why a model's high score on an AI benchmark might overstate how useful it will be for real work.
assessment-instructions:: Score out of 100. 50 for each of two distinct reasons, such as: test questions were in its training data; it was tuned to the benchmark; it gamed the grader or obtained the answers; benchmark tasks are short and clearly specified, unlike real work; automatic grading misses judgment; the score came from a favorable setup (many attempts, special tools). 25 for a vague reason.

#### Question: Open
id:: 6411060b-0c60-4978-8941-eea210a9d208
content:: Why can competition to top popular AI benchmark leaderboards make those benchmarks a worse guide to a model's general ability?
assessment-instructions:: Score out of 100. 100 for the idea that developers aim at the benchmark (training on similar tasks, tuning settings, picking favorable results), so scores rise faster than the general skill they were meant to measure (Goodhart's law). 60 for only saying test questions leak into training data. 30 for "labs exaggerate" without the mechanism.
