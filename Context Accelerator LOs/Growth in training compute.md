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
Training compute is a measurable input that has tracked AI capability gains closely, though models now also gain from computing longer when they answer. Knowing its growth rate and drivers helps you judge forecasts of future capabilities, see why compute thresholds in regulation age quickly, and check whether claims about a slowdown rest on spending, hardware or physical limits.

## Lenses
- [Scaling up: how increasing inputs has made artificial intelligence more capable (Our World in Data)](https://ourworldindata.org/scaling-up-ai): how training compute, data and model size have grown, from a doubling about every two years before 2010 to about every six months since, and what has driven it (January 2025).
- [[../Lenses/AI Safety Atlas - Capabilities - Forecasting Timelines|Forecasting Timelines]]: current growth rates for training compute and cost, and how effective compute multiplies chip numbers, hardware efficiency and better algorithms; read the opening paragraphs and the "Effective Compute" section.
- [[../Lenses/AIF - Can AI Scaling Continue Through 2030|Can AI Scaling Continue Through 2030?]]: Epoch AI on power, chips, data and latency as limits on 4x-a-year growth, and whether labs will pay for it; read the Introduction, "Will labs attempt to scale to these new heights?" and the Conclusion (August 2024).
- [[../Lenses/AI Safety Atlas - Governance - Compute Governance|Compute Governance]]: the US and EU compute thresholds, and why algorithmic progress and inference-time compute make fixed thresholds age; read the thresholds paragraph in "Monitoring" and the "Limitations" section.

## Tests

#### Question: Choice
id:: 7123d09d-8782-4e49-856f-c24aa6c0e03d
content:: According to Epoch AI, roughly how fast has the compute used to train frontier AI models grown each year since 2010 (a trend still holding as of 2026)?
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
id:: c7b4537b-809f-4a9e-9275-b5a27014023d
content:: Researchers distinguish a model's physical training compute from its "effective compute". What does effective compute add?
options::
- [x] Gains from better algorithms, counted as if they were extra FLOP
- Compute used at inference time after the model is released
- FLOP adjusted for chips sitting idle during training
- Compute rented from cloud providers rather than owned
shuffle:: true

#### Question: Choice
id:: 3fc64121-5a5b-4845-8d50-ae0fe6e5beeb
content:: A lab reports how much compute it used to train a new model. Which of these is usually left out of that figure?
options::
- [x] Compute for the experiments and test runs that led up to the final run
- Compute for fine-tuning the model after pretraining
- Compute for reinforcement learning that teaches the model to reason
- Compute for the main pretraining run
shuffle:: true

#### Question: Choice
id:: 6bf04e71-4c05-41e9-b450-367dddfa9b77
content:: Since 2024, "reasoning" models have improved their answers by computing for longer at inference time. Why does this matter for using training compute to track AI progress?
options::
- [x] Part of their gains comes from compute that training figures leave out
- Their gains come from bigger pretraining runs, so training figures already capture them
- Compute used when answering is added to a model's training compute after release
- It makes training compute a closer guide, since reasoning ties gains to training
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
- More models cross it, but it keeps covering the same range of capabilities
- Fewer models cross it, because efficient algorithms reach the same capabilities with less compute
- About as many models cross it, and models just below it stay about as capable
shuffle:: true

#### Question: FillBlank
id:: 2d6f8145-3047-4233-91c9-8d9dc750c55e
content:: The EU AI Act presumes that a general-purpose AI model has systemic risk if its training used more than {{10^25|1e25|10 to the 25}} FLOP.

#### Question: Open
id:: 5f9a94eb-b168-4ce2-af8f-f31f4adbc5f6
content:: Give one reason training compute is useful for forecasting AI capabilities, and one limitation of using it this way.
assessment-instructions:: Score out of 100. 100 for one reason (e.g. scaling laws link more training compute to better performance; it is measurable and has followed a steady trend) plus one limitation (e.g. algorithmic progress, inference-time compute, data quality, or it predicts overall performance better than specific abilities). 50 for only one part.
