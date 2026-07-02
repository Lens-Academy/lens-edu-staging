---
id: b5a9848d-a1be-4396-91ad-c74701b31ff9
title: "Diffuse Threats and Research Sabotage"
tldr: What if the attack is a thousand tiny acts of sabotage, none individually damning? Diffuse threats defeat single-action auditing and need different detection machinery.
summary_for_tutor: "Covers Hebbar's analysis of diffuse threats: failures like research sabotage composed of many low-stakes actions (subtly wrong experiments, misleading advice) where auditing single actions can't produce decisive evidence. Countermeasures include aggregating weak signals across many actions, incrimination strategies, statistical detection of systematic bias, and training-based approaches. Especially relevant to plans relying on AI-automated safety research."
---

#### Text
content::
(More in the technical weeds; treat as optional if short on time.) Concentrated failures get caught by auditing the worst action. But what if the AI's attack is a thousand tiny acts of sabotage, none individually damning? Diffuse threats need different machinery.

#### Article
source:: [[../articles/hebbar-how-can-we-solve-diffuse-threats-like-research-sabotage-with-ai-control]]

#### Text
content::
If no single action is damning, is "audit the worst action" simply the wrong tool {--{"author":"Elias's AI","timestamp":1783024119355}@@here — or--}{++{"author":"Elias's AI","timestamp":1783024119355}@@here? Or is it++} salvageable with enough aggregation? Take a side, then push it with the tutor on the case that bites hardest: AI-run safety research sabotaging itself.

#### Chat
instructions::
TLDR of what the user just read: This post analyzes diffuse threats: failures like research sabotage composed of many low-stakes actions (subtly wrong experiments, misleading advice) where auditing single actions can't produce decisive evidence. Countermeasures include aggregating weak signals across many actions, incrimination strategies, statistical detection of systematic bias, and training-based approaches.

Discussion topics to explore:
- Why does the execute/replace/audit machinery from high-stakes control fail against diffuse threats?
- How can you aggregate many individually-innocent-looking actions into evidence of sabotage?
- Research sabotage specifically targets safety work done by AIs: how does this interact with plans that depend on AI-automated alignment research?

Check they can explain why "no single action is catastrophic" makes both detection and response fundamentally harder.
