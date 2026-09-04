---
id: '7742225d-e3a4-48fc-8560-a1164fed7dfc'
learning-outcome: "Given an unfamiliar verification proposal, identify its load-bearing mechanism, its weakest link and how a failure there would spread, the assumptions it depends on, and defend a recommendation that answers the strongest objection to it."
domain: "[[../Domains/Governance and Policy]]"
stage: intermediate
authors:
  - Elias+Claude
tags:
  - wip
---
## Test:
id:: 6e124856-c5d2-425f-af25-07634eee19a3

#### Question: Open
id:: fdee451d-94e1-454f-a5ae-6e1ecfbdb8e7
content:: Two rival states are negotiating a cap on frontier training runs. A working group tables the following regime. It is hypothetical, not a published plan.

> **The Registry Proposal.**
> 1. Every AI accelerator above a performance threshold is assigned a unique ID at the fabrication plant and entered into a shared registry before shipment.
> 2. Each state declares, every quarter, the location of every registered chip on its territory.
> 3. Cloud providers and data-centre operators report, every quarter, the total compute-hours each registered chip performed and which customer used it.
> 4. A joint inspection agency visits a random 10 percent of declared sites each year and checks that the chips on the floor match the declaration.
> 5. Satellite monitoring of power infrastructure flags any facility drawing power consistent with a large cluster that has no declared chips.

In 350 to 550 words:

1. name the mechanism that carries the most weight, meaning the one whose removal would most damage the regime, and say why;
2. name the weakest link, what a determined state would do to exploit it, and which other parts of the regime would stop being informative if it failed;
3. state three assumptions the regime depends on that the proposal does not make explicit;
4. recommend adopt, amend, or reject, and answer the strongest objection to your recommendation.
max-chars:: 4000
assessment-instructions:: Score 0 to 100 from four components. Grade reasoning, not the choice; adopt, amend, and reject can each score full marks.

**(a) Load-bearing mechanism, 20 points.** Credit any mechanism defended with a dependency argument. The strongest candidates: registration at fabrication (1), because it defines the population every later step samples from; or the declaration step (2), because inspections (4) check declarations and can only find what was declared. 20 for a choice plus a stated dependency argument; 10 for a choice justified only by "it detects the most".

**(b) Weakest link and cascade, 25 points.** Strong answers identify at least one of: usage reporting (3) is self-reporting by the inspected party, so the regime verifies where chips are but not what they computed; chips diverted before registration or obtained outside the registered supply chain never enter the population, and no inspection frequency reaches them; power monitoring (5) cannot distinguish an AI cluster from other high-power industry, and a violator can split compute across sites below the flagging level. Full credit requires naming the exploit and the cascade, meaning which other mechanisms become uninformative. 10 points for a weakness with no exploit or cascade.

**(c) Assumptions, 25 points.** Up to 8 each for three distinct, unstated, load-bearing assumptions, for example: the supply chain is concentrated enough that registration at fabrication captures nearly all relevant chips; a frontier run needs enough chips that it cannot be done on unregistered or sub-threshold hardware; states will grant physical access to sites; usage reports are checkable or costly to falsify; algorithmic progress does not lower the compute needed below what the regime watches; the threshold in (1) is set at the right level. Assumptions already stated in the proposal earn 0.

**(d) Recommendation and objection, 30 points.** 15 for a recommendation that follows from (a) to (c). 15 for stating the strongest objection to that recommendation and answering it rather than restating the recommendation. A strawman objection, or one the learner does not answer, earns at most 5.

Deduct 10 if the answer evaluates the regime as if it must be perfect; residual covert compute is a design parameter, not a refutation.
feedback-instructions:: Name the strongest analytic move in the answer in one sentence. Then name the one change that would most improve it, usually a missing cascade or an assumption the learner treated as given. If the learner did not answer their own strongest objection, say so. Ask one follow-up question. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Verification - v-intuitions]]
notes:: Practice on Plan A: strongest mechanism, weakest link, timeline, covert margin, verdict. The test uses a different proposal on purpose.

## Lens:
source:: [[../Lenses/XLab Verification - v-precedents]]
notes:: Task 2 (division of labour between instruments) is the closest practice for the cascade question.
