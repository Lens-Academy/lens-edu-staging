---
id: 003134b6-a9ee-4219-bede-5d963ccfc7b7
tldr: "Only three companies stand between the world and the chips needed to train frontier AI, so controlling hardware may be the most practical lever governments have. This section explains why compute is uniquely measurable, controllable, and meaningful, how training runs can be tracked and monitored, what on-chip controls might do, and where the whole approach starts to break down."
summary_for_tutor: "Explains why compute is a promising target for AI governance, meeting three criteria: measurability (compute leaves physical and energy footprints trackable in FLOP), controllability (a concentrated supply chain dominated by NVIDIA, TSMC, and ASML), and meaningfulness (compute constrains what models can be built). Details tracking via supply-chain chokepoints, monitoring through energy use, network traffic, and compute thresholds (US 10^26, EU 10^25 operations) plus cloud-provider know-your-customer schemes, and speculative on-chip governance mechanisms like usage limits, secure logging, and location verification. Discusses limitations: algorithmic efficiency gains and inference-time scaling eroding static thresholds, dangerous small specialized models, power concentration and the compute divide, and distributed training potentially bypassing controls."
{++{"author":"Elias's AI","timestamp":1787569962516}@@reading_minutes: 17
tutor_minutes: 7
++}title: "Compute Governance"
---

#### Article
source:: [[../articles/AI Safety Atlas - Governance - Compute Governance|Compute Governance]]{++{"author":"Elias's AI","timestamp":1787569962516}@@

#### Question: Open
id:: 53871717-d37d-411c-a536-6ccb76481015
optional:: true
content::
The section builds the case that compute is the best lever governments have, then spends its last part on why the lever is slipping: thresholds erode as algorithms get more efficient, small specialised models can be dangerous, and distributed training routes around the chokepoints.

Which convinced you more, the case or the caveats?
feedback-instructions::
The learner has just read the AI Safety Atlas section "Compute Governance" and written a reflection. This is a reflection, not a test. There is no answer you are checking against, and you should not tell them whether they got it right.

TLDR of what they read:
Why compute is a promising governance target, against three criteria the previous section set out. Measurability: compute is counted in floating-point operations and leaves physical and energy footprints. Controllability: the supply chain is concentrated, dominated by a small number of firms, so authorities only need to reach a few players, as US export restrictions showed. Meaningfulness: compute constrains what can be built. It covers tracking through supply-chain chokepoints and monitoring through energy use and network traffic, and notes regulations already use thresholds to trigger oversight, with the US executive order at 10^26 operations and the EU AI Act at 10^25, the latter requiring risk assessment rather than only notification. It describes cloud-provider know-your-customer schemes, and hardware mechanisms built into chips such as usage limits, secure logging and location verification, while stating plainly that on-chip controls are highly speculative. It then gives the limits: the supply-chain concentration it relies on is itself a concern, creating a growing compute divide where major companies spend hundreds of millions while academics struggle for basic access, which reduces independent oversight and concentrates power; static thresholds erode as algorithmic efficiency improves and as more capability comes from inference-time compute; small specialised models can be dangerous below any threshold; and distributed training and open weights may route around the controls.

Take what they wrote seriously and push on it once. Useful directions: whether the caveats undermine compute governance or only date the specific numbers, since a threshold that has to be revised is not the same as a lever that does not work; that the concentration making control possible is the same concentration the section flags as a risk, so the strategy's precondition is also one of its costs; that on-chip controls are labelled speculative by the section itself, so anything resting on them is a plan rather than a tool; and what a regulator would fall back on if compute stopped being a good proxy for capability.

If they say they do not know or write something thin, do not press them for more. Offer one concrete way to look at it and leave it there.

120 to 200 words. Short paragraphs, no lists. Do not over-validate and do not praise the answer.++}
