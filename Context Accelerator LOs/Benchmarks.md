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
AI labs, journalists and researchers mostly report progress as benchmark scores, and debates about how fast AI is advancing lean on them. If you know how scores can be inflated or can miss real-world skill, you can tell a real jump in ability from a number that mostly reflects the test.

## Lenses

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
id:: 03a098df-869b-449f-8a1a-3dd9386c6181
content:: The GPQA benchmark of hard science questions is described as "Google-proof". What does that mean?
options::
- [x] Skilled non-experts score poorly on it even with web access
- Its questions have never been posted anywhere online
- Its answers were all checked using web searches
- Models can't search the web while answering it
shuffle:: true

#### Question: Choice
id:: b1e36369-fac8-4f85-bf32-aa5c401b5f0a
content:: A new AI benchmark is released, and the best current model scores 2% on it. Why might its designers see this as a good sign for the benchmark?
options::
- [x] It leaves room to track progress for longer
- It shows the questions are free of errors
- It proves the questions weren't in training data
- It makes scores easier to compare across labs
shuffle:: true

#### Question: Choice
id:: 4d5c395d-f87f-4987-b926-a2df9962477f
content:: On a benchmark where about 5% of the official answers are known to be wrong, model A scores 88% and model B scores 89%. Does this show that B is more capable?
options::
- [x] No, the gap is within the benchmark's margin of error
- Yes, because both took exactly the same questions
- Yes, if neither was trained on the questions
shuffle:: true

#### Question: FillBlank
id:: b736c9ba-0e65-4cfe-8e2c-b2d04e5ac594
content:: When top AI models score close to the maximum on a benchmark, so that it can no longer tell them apart, the benchmark is said to be {{saturated}}.

#### Question: Open
id:: efb4018e-3966-4a90-960a-886b82a5da1e
content:: Give two reasons why a model's high score on an AI benchmark might overstate how useful it will be for real work.
assessment-instructions:: Score out of 100. 50 for each of any two distinct reasons, such as: the test questions were in its training data; it was tuned to the benchmark; benchmark tasks are short, clearly specified and self-contained, unlike real work; automatic grading misses judgment and open-ended skill; the score came from a favorable setup (many attempts, special tools). 25 for a vague reason.

#### Question: Open
id:: 6411060b-0c60-4978-8941-eea210a9d208
content:: Why can competition to top popular AI benchmark leaderboards make those benchmarks a worse guide to a model's general ability?
assessment-instructions:: Score out of 100. 100 for the idea that developers aim at the benchmark (training on similar tasks, tuning settings, picking favorable results), so scores rise faster than the general skill they were meant to measure (Goodhart's law). 60 for only saying test questions leak into training data. 30 for "labs exaggerate" without the mechanism.
