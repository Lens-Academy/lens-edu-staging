---
id: a93880fc-ceee-46f4-8d5b-170299a67a32
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what makes chips and data centers a practical point of control for governing frontier AI, give examples of compute-based policies, and describe the main ways this lever can weaken.

## Requires
- [[Compute]]

## Helpful first
- [[AI chip supply chain]]
- [[AI governance]]

## Why it matters
Many proposals for overseeing frontier AI, from chip export controls to training-run reporting, act through compute. Knowing why this lever works helps you judge such proposals; knowing its weaknesses stops you assuming a compute threshold or chip ban will stay effective as algorithms and hardware change.

## Lenses
- [[../Lenses/AI Safety Atlas - Governance - Compute Governance|Compute Governance]]: why compute is measurable, controllable and meaningful; how chips and training runs are tracked, monitored and might be controlled on-chip; and where the approach breaks down (algorithmic efficiency, inference scaling, distillation, small specialised models, distributed training). Its US 10^26 FLOP example is from the 2023 executive order, revoked in January 2025.
- [Computing Power and the Governance of AI (GovAI)](https://governance.ai/analysis/computing-power-and-the-governance-of-ai): the standard short statement of why compute is detectable, excludable and quantifiable, what compute policies can do, and how they can fail or cause harm (February 2024).
- [Location Verification for AI Chips (IAPS)](https://www.iaps.ai/research/location-verification-for-ai-chips): a short brief on how chips could prove roughly where they are, as a check on chip smuggling that undermines export controls (May 2025).
- [DeepSeek's Lesson: America Needs Smarter Export Controls (RAND)](https://www.rand.org/pubs/commentary/2025/02/deepseeks-lesson-america-needs-smarter-export-controls.html): the case that chip controls still matter as algorithms get more efficient and more compute goes to inference, from a leading proponent of compute governance. Some of the US rules it discusses have changed since (February 2025).
- [Training Compute Thresholds: Features and Functions in AI Regulation (GovAI)](https://www.governance.ai/research-paper/training-compute-thresholds-features-and-functions-in-ai-regulation): why regulators use training compute as a trigger, and why it should be only an initial filter for closer scrutiny, not a measure of risk (August 2024) (more advanced).

## Tests

#### Question: Choice
id:: b0481367-4ff9-43f2-b8b6-cd0b212f20fd
content:: Export controls stop some countries from buying the most advanced AI chips and the tools to make them. Even if no chips are smuggled, what could weaken this lever most over time?
options::
- [x] Those countries build their own chipmaking industry, beyond the reach of the firms the controls rely on.
- Chip prices fall, so those countries can buy more of the controlled chips through legal sales.
- The controlled chips use too much power to run in those countries' data centers.
- AI companies in those countries stop publishing how much compute they use.
shuffle:: true

#### Question: Choice
id:: f3757198-ebe1-4b3e-bf10-38cfb18c830e
content:: Only a few firms make the most advanced AI chips or the machines to produce them. Why does this help compute governance?
options::
- [x] Rules applied to these few firms, such as TSMC or ASML, reach almost all advanced chips.
- These few firms already decide by themselves which governments may train frontier models.
- These few firms' chips are identical, so regulators can count them without tracking sales.
- These few firms keep chip prices so high that only governments can afford frontier training.
shuffle:: true

#### Question: Choice
id:: c717eb4d-1329-45f4-b6c9-bb6736b167f3
content:: Why do some AI regulations use the amount of training compute as a trigger for extra obligations?
options::
- [x] It can be estimated before training and roughly tracks how capable a model will be.
- It directly measures which dangerous capabilities a model has.
- It is the figure developers most readily publish for each model.
- It predicts which tasks a model will fail at after deployment.
shuffle:: true

#### Question: FillBlank
id:: 9266cba3-4645-47d1-9ff7-6d127096c57a
content:: As of November 2026, the EU AI Act presumes that a general-purpose AI model poses systemic risk if it was trained with more than 10^{{25}} FLOP.

#### Question: Choice
id:: 0c4a8cc5-e280-4340-9bf5-8bbf91ff5af8
content:: A law requires extra checks for training runs above a fixed FLOP threshold. What does continued algorithmic progress, on its own, do to this rule over time?
options::
- [x] Models of a given capability can be trained with less compute, possibly below the threshold.
- The threshold catches more models, because better algorithms need more FLOP per run.
- The threshold becomes a more accurate predictor of dangerous capabilities.
- Nothing, because FLOP counts already adjust for algorithmic efficiency.
shuffle:: true

#### Question: Choice
id:: 74193b5d-cafa-4978-85a1-69245931023b
content:: A developer trains a small model on the outputs of a large frontier model (distillation). Why is this a problem for compute governance?
options::
- [x] Strong capabilities can be reached with far less training compute than the original used.
- Distillation needs more compute than training the original model did.
- Distillation makes the original model's weights publicly available.
- Distillation can only be done on chips that export controls don't cover.
shuffle:: true

#### Question: Choice
id:: f973bc04-9033-4b38-8f55-466577ad8d2b
content:: Some AI models get more capable by using more compute while answering (inference), not only during training. Why does this weaken compute rules that focus on training runs?
options::
- [x] Capability can grow through inference compute that training thresholds don't count.
- Inference runs on ordinary processors, so AI chip rules don't apply to it.
- Inference compute can't be measured in FLOP.
- Frontier developers have stopped increasing their training compute.
shuffle:: true

#### Question: Open
id:: 5b25f537-3858-4d6f-9949-669789e325b0
content:: More and more AI compute is used to run models (inference) rather than to train them. Why do export controls on advanced AI chips still matter?
assessment-instructions:: Score out of 100. 100 for explaining that inference also runs best on advanced chips, so limiting chips limits how many copies of a model an actor can run, how long models can "think" while answering, and so how much capability they get from inference; or that frontier training still needs the same chips. 50 for "inference still uses chips" with no link to capability or scale.

#### Question: Choice
id:: 96f2035d-e49f-4259-ad66-c65d7038ce9e
content:: If large training runs could be split reliably across many distant, smaller data centers (decentralized training), how would this weaken compute governance?
options::
- [x] Large runs would be harder to spot by watching a few very large data centers.
- The same run would need far fewer chips in total.
- The FLOP used in the run could no longer be calculated.
- Developers could skip safety evaluations before releasing the model.
shuffle:: true

#### Question: Choice
id:: 66f898c8-95f4-43ac-924e-6e7615ed6092
content:: Some proposals would build features into AI chips that let a regulator check where a chip is or how it is used (hardware-enabled mechanisms). Which weakness of chip export controls do these mainly address?
options::
- [x] Chips being smuggled or diverted to restricted buyers after sale
- Restricted countries building their own advanced chipmaking industry
- Older chips, made before such features existed, staying in circulation
- Allied governments disagreeing about which countries to restrict
shuffle:: true

#### Question: Open
id:: 2fd7faa5-cbc0-475c-8445-1deb973db613
content:: Why is it harder to govern AI by controlling algorithms than by controlling compute? Give one reason.
assessment-instructions:: Score out of 100. 100 for any one of: algorithms are information that can be copied and shared at almost no cost, so access can't be denied; they can't be counted or detected the way physical chips can; ideas spread through papers and staff moving between firms, unlike chips made by a few suppliers. 50 for "algorithms are hard to control" with no reason.

#### Question: Open
id:: 6c306631-f114-4c40-b45b-43679aaab2b5
content:: A government wants to know which organizations could train frontier AI models. How does compute make this easier to find out?
assessment-instructions:: Score out of 100. 100 for explaining that frontier training needs very large numbers of advanced chips in large data centers, and these are visible or trackable: few suppliers sell the chips, sales and cloud customers can be recorded, and big data centers need lots of power and construction. 60 for naming only one route without linking it to the scale needed.

#### Question: Open
id:: 3cfbb4d0-319d-40cd-a4f8-142b26a96bb0
content:: Why do compute governance proposals usually target large data centers and frontier training runs rather than everyday computer use?
assessment-instructions:: Score out of 100. 100 for: the risks of most concern are thought to come from the most capable models, which need huge amounts of compute held by few actors; small-scale compute is everywhere, so monitoring or restricting it would be impractical and intrusive. 60 for only one of these two points.
