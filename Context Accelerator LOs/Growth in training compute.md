---
id: 13d1fcbe-3110-453b-bff2-410a640f0e09
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how fast the compute used to train frontier AI models has grown since 2010, what has driven that growth, and what could slow it.

## Requires
- [[Compute]]

## Helpful first

## Why it matters
Training compute is a measurable input that tracks where AI capabilities are heading. Knowing its growth rate and drivers helps you judge forecasts of future capabilities, see why compute thresholds in regulation age quickly, and check whether claims about a slowdown rest on spending, hardware or physical limits.

## Lenses

## Tests

#### Question: Choice
id:: 7123d09d-8782-4e49-856f-c24aa6c0e03d
content:: According to Epoch AI estimates (as of 2024), roughly how fast has the compute used to train frontier AI models grown since 2010?
options::
- [x] About 4 to 5 times per year
- About 1.4 times per year
- About 2 times per year
- About 20 times per year
shuffle:: true

#### Question: Choice
id:: 65eb19d9-7389-437f-8467-96b20802688e
content:: Before deep learning took off around 2010, how did growth in the training compute of notable AI models compare with Moore's law?
options::
- [x] It roughly kept pace with Moore's law
- It grew far faster than Moore's law
- It stayed roughly flat for decades
- It grew faster than it has since 2010
shuffle:: true

#### Question: Open
id:: 9f111e35-843d-434a-b707-1b8b2cd2b68b
content:: A friend says AI progress must stall soon because individual chips are no longer getting much faster. Based on what has driven growth in training compute, what is the main flaw in this argument?
assessment-instructions:: Score out of 100. 100 for: most growth in frontier training compute has come from spending more, using many more chips in larger clusters and training for longer, not from faster chips alone. Also mentioning algorithmic progress is fine. 50 for naming only algorithmic progress.

#### Question: Choice
id:: 1f0a7b2a-0a61-49cc-871f-150b5618086d
content:: Suppose the cost of the largest AI training run is $1 billion and grows 2.5 times per year. Roughly what would it cost five years later?
options::
- [x] About $100 billion
- About $12 billion
- About $25 billion
- About $1 trillion
shuffle:: true

#### Question: Choice
id:: c7b4537b-809f-4a9e-9275-b5a27014023d
content:: Researchers distinguish a model's physical training compute from its "effective compute". What does effective compute add?
options::
- [x] Gains from better algorithms, counted as if they were extra FLOP
- Compute used at inference time after the model is released
- FLOP adjusted for chips sitting idle during training
- Compute rented from cloud providers rather than owned
shuffle:: true

#### Question: Choice
id:: f0f873ab-3480-4b1b-a8c1-a88850eb706e
content:: Which of these is counted in a model's training compute, as usually reported?
options::
- [x] FLOP used in the final pretraining and fine-tuning runs
- FLOP used to answer users' queries after release
- FLOP available across all the lab's data centers
- FLOP spent running safety evaluations on the model
shuffle:: true

#### Question: Choice
id:: 6bf04e71-4c05-41e9-b450-367dddfa9b77
content:: Since 2024, "reasoning" models have improved their answers by computing for longer at inference time. Why does this matter for using training compute to track AI progress?
options::
- [x] Some gains now come from compute that training figures leave out
- Training compute has stopped growing since reasoning models appeared
- Reasoning models make training compute impossible to estimate
- Inference compute is already included in training compute figures
shuffle:: true

#### Question: Open
id:: 46100b1a-be06-4791-8ec4-9dd72d7a0455
content:: Name two constraints that could slow the growth of frontier AI training compute before 2030.
assessment-instructions:: Score out of 100. 100 for any two of: electric power for data centres; chip manufacturing capacity (e.g. advanced packaging, high-bandwidth memory); how much labs and investors are willing to spend; shortage of high-quality training data; latency limits on very large training runs. 50 for one.

#### Question: Choice
id:: 5dce6ced-8715-43ab-a990-13a838c6f81b
content:: A law applies extra rules to AI models trained above a fixed compute threshold. If training compute keeps growing fast and algorithms keep getting more efficient, what happens over time?
options::
- [x] More models cross it, and models just below it get more capable
- Fewer models cross it, because algorithms need less compute
- It keeps covering the same range of capabilities each year
- The same number of models cross it each year
shuffle:: true

#### Question: FillBlank
id:: 2d6f8145-3047-4233-91c9-8d9dc750c55e
content:: The EU AI Act presumes that a general-purpose AI model has systemic risk if its training used more than {{10^25|1e25|10 to the 25}} FLOP.

#### Question: Open
id:: 5f9a94eb-b168-4ce2-af8f-f31f4adbc5f6
content:: Give one reason training compute is useful for forecasting AI capabilities, and one limitation of using it this way.
assessment-instructions:: Score out of 100. 100 for one reason (e.g. scaling laws link more training compute to better performance; it is measurable and has followed a steady trend) plus one limitation (e.g. algorithmic progress, inference-time compute, data quality, or it predicts overall performance better than specific abilities). 50 for only one part.
