---
id: '7742225d-e3a4-48fc-8560-a1164fed7dfc'
writing_minutes: 30
learning-outcome: "Given an unfamiliar verification proposal, identify its load-bearing mechanism, its weakest link and how a failure there would spread, the assumptions it depends on, and defend a recommendation that answers the strongest objection to it."
topic: "[[../Domains and Topics/10 Governance and Policy/Verifying AI agreements]]"
stage: intermediate
authors:
  - Elias+Claude
tags: []
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
max-words:: 670
assessment-instructions:: Score out of 100. Grade reasoning, not the choice: adopt, amend and reject can each score full marks. 20: the load-bearing mechanism, named and defended with a dependency argument that shows which other steps rely on it; the strongest candidates are registration at fabrication (1), because it defines the population every later step checks, or the declarations (2), because inspections (4) check declarations and can only find what was declared; a choice justified only by "it detects the most" gets 10 of these 20. 26: weakest link and cascade, 10: names a weak link and why it is weak, for example: usage reporting (3) is self-reporting by the inspected party, so the regime verifies where chips are but not what they computed; chips diverted before registration or obtained outside the registered supply chain never enter the population, and no inspection rate reaches them; power monitoring (5) cannot tell an AI cluster from other high-power industry; 6: what a determined state would do to exploit it, such as falsifying usage reports, diverting or smuggling unregistered chips, or splitting compute across sites below the flagging level; and 10: the cascade, which other mechanisms stop being informative if it fails (for example, if chips escape registration, declarations, usage reports and inspections all cover only the registered population, so their clean results say nothing about the unregistered chips, and only the ambiguous power monitoring is left). 24: three distinct, unstated, load-bearing assumptions, 8 each, for example: the supply chain is concentrated enough that registration at fabrication captures nearly all relevant chips; a frontier run needs enough chips that it cannot be done on unregistered or below-threshold hardware; states will grant physical access to sites; usage reports are checkable or costly to falsify; algorithmic progress does not lower the compute needed below what the regime watches; the performance threshold in (1) is set at the right level; an assumption the proposal already states gets 0. 30: recommendation and objection, 15: a recommendation (adopt, amend or reject) that follows from the answer's own analysis of mechanism, weak link and assumptions, and 15: the strongest objection to that recommendation, stated and answered rather than the recommendation restated; a strawman objection, or one the answer leaves unanswered, gets at most 5 of these 15. Give credit for each point whenever the answer shows the idea, in any wording. Deduct 10 if the answer judges the regime as if it must be perfect: some residual covert compute is a design parameter to size, not a refutation. Model answer, for the feedback, not a grading checklist: "1. The load-bearing mechanism is registration at fabrication (1). Every other step works on the registered population: states declare where registered chips are, operators report how registered chips were used, inspectors compare the chips on the floor with the declaration, and even the satellite check flags facilities that have no declared chips. Remove registration and none of the others has a list to check against, so it carries more weight than any single detector. 2. The weakest link is that boundary seen from the other side, together with usage reporting (3), which is self-reporting by the operators the regime is meant to check, so the regime can confirm where chips are but not what they computed. A determined state would acquire chips outside the registered supply chain, through a domestic fab, smuggling or diversion before the ID is assigned, and run its frontier training on them at a site with a civilian cover, or split the run across several sites that each stay below the power level the satellites flag, while its registered chips report ordinary use. If that works, the failure spreads: declarations (2), usage reports (3) and inspections (4) all describe only registered chips, so a clean record on them says nothing about the covert cluster, and the random 10 percent inspections only confirm what was declared; only power monitoring (5) looks outside the registry, and it is ambiguous because large data centres and heavy industry draw similar power. 3. Unstated assumptions: the chip supply chain is concentrated enough that registration at the fab captures nearly all relevant chips; a frontier run needs so much compute that it cannot be done on unregistered or below-threshold hardware, and algorithmic progress will not lower that need below what the regime watches; states will grant inspectors physical access to sites; and usage reports can be checked or are costly to falsify. 4. Recommendation: amend. Verified accounting of a controlled input is the strongest parallel with nuclear safeguards, so the registry is a sound backbone, but as written it verifies the accounts of registered chips, not the absence of prohibited training. Amend it with usage logging that does not rely on the operator (on-chip or tamper-evident logs that inspectors can audit), supply-chain and fab monitoring plus intelligence leads for chips outside the registry, and challenge inspections of undeclared sites that power data or other information flags. The strongest objection is that these additions bring intrusion and cost a rival state will not accept, so asking for them risks having no agreement at all. The answer: the regime does not need to be perfect, only to keep covert compute small and costly enough that it cannot support a frontier run; the additions can be phased in after registration and declarations, and each side gets the same assurance about the other, so the intrusion is a price both pay for a cap both want."
feedback-instructions:: Name the strongest analytic move in the answer in one sentence. Then name the one change that would most improve it, usually a missing cascade or an assumption the learner treated as given. If the learner did not answer their own strongest objection, say so. Ask one follow-up question. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Verification - v-intuitions]]
notes:: Practice on Plan A: strongest mechanism, weakest link, timeline, covert margin, verdict. The test uses a different proposal on purpose.

## Lens:
source:: [[../Lenses/XLab Verification - v-precedents]]
notes:: Task 2 (division of labour between instruments) is the closest practice for the cascade question.
