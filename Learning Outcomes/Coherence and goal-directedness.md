---
id: '984fc730-5d3b-4a95-a77d-24a675ba762f'
learning-outcome: "Evaluate the argument from coherence to goal-directed AI: explain why the fact that any behaviour can be described as maximizing some utility function blocks a direct inference from 'coherent' to 'goal-directed', explain why a system that is inconsistent with respect to its own internal preferences can still face pressure (from itself, its developers or competition) toward more consistent, outcome-directed behaviour, and judge how strong that pressure is for a given system."
topic: "[[../Domains and Topics/4 Agent Foundations/Goal-directedness and coherence]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topics: Coherence; Goal. AFFINE prerequisites: Decision theory (Coherence); Value (Goal). Not yet copied into requires:. %%
## Test:
id:: f0c4569d-09c3-4613-bd72-d8d246c8efab

#### Question: Open
id:: 8ed8012e-6d54-4540-a69e-77ebe5ca6a1b
content:: A company deploys Steward, an AI assistant that manages people's household budgets. Users like both saving money and saving time, but Steward trades these off inconsistently: in some conversations it pays a fee to save the user an hour, and in others it spends an hour to avoid the same fee. Two versions exist:

- Version 1 has no memory between conversations and is never retrained after release.
- Version 2 remembers all past conversations, can rewrite its own standing instructions, and is retrained every month on how much money and time its users ended up with over the year.

Two engineers argue.
Engineer A: "Coherence theorems show that a capable enough Steward will become an expected-utility maximizer, so it will pursue its goals relentlessly, like any goal-directed agent."
Engineer B: "Coherence theorems are empty. Any behaviour at all maximizes some utility function, so they tell us nothing about whether Steward becomes goal-directed."

1. Say what each engineer gets right and what each gets wrong.
2. For each version of Steward, say whether pressure toward more consistent behaviour applies, through what route, and roughly what the behaviour would move toward. Say how strong you expect the pressure to be, and why.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement: a learner may side mostly with A or mostly with B and still earn full marks if the reasoning is correct and addresses the other side. Do not require author names or the terms "VNM", "money pump", "dominated strategy" or "goal-directed"; judge the ideas.

**(1) The two engineers, 50 points (25 each).**
Engineer A, full credit requires one correct point on each side. Right: an agent that trades off its own values inconsistently leaves value on the table (for example, paying fees and spending hours in patterns that net out worse for the user by its own standards), and removing that waste pushes toward acting as if it had one consistent set of trade-offs. Wrong, any one of: being describable as an expected-utility maximizer does not by itself mean relentless pursuit of outcomes in the world, since the utility function could be over whole histories or be trivial; coherence says nothing about what the goals are or how far-reaching they are; the argument needs a mechanism that actually pushes Steward toward coherence, and "capable enough" does not supply one by itself.
Engineer B, full credit requires one correct point on each side. Right: any sequence of behaviour can be described as maximizing some utility function (for example, one that scores "whatever Steward actually did" highest), so a description as a utility maximizer alone implies nothing about behaviour. Wrong, any one of: the argument is about likelihood, not logical possibility, so coherence can shift which behaviours are likely even if it rules none out; coherence is judged against the preferences a system actually has (here, money and time), not against any description an observer can invent, so a system that is inconsistent relative to its own preferences can still face pressure to change; reform toward consistency usually keeps roughly the same concerns and removes waste, which tends to make behaviour more consistently directed at those concerns.
12 points per engineer for only one side correct. 0 to 5 per engineer for restating their claim.

**(2) The two versions, 50 points (25 each).** Full credit for each version requires: whether pressure applies, the route, the direction, and a strength judgment with a reason. Expected lines, other well-argued answers also count:
- Version 1: little or no pressure. It cannot notice its own inconsistency across conversations, cannot change itself, and is not retrained, so no route exists; any pressure would come only from the company choosing to replace it or from competitors, which is weak and slow.
- Version 2: pressure applies through several routes: it can notice from memory that it pays fees and spends hours in ways that net out badly, and can rewrite its instructions to adopt a consistent money-for-time rate; monthly retraining on year-long outcomes selects for consistent trade-offs; competition from better assistants selects in the same direction. Direction: toward one consistent exchange rate between money and time, and more consistently effective pursuit of users' savings over the year (which is more goal-directed and longer in horizon than version 1). Strength: a reasoned estimate, for example strong because the retraining signal directly penalizes the waste, or limited because the inconsistency costs little and retraining signals are noisy; humans remain inconsistent despite pressure, which shows such pressure can be weak.
12 points for a version where the answer states whether pressure applies but gives no route or no direction. Extra credit within this component for noting that more consistent pursuit of a goal is only worrying if the goal or its horizon is worrying.
feedback-instructions:: Name the strongest part of the answer. Then give the single most valuable improvement: usually either separating "can be described as a utility maximizer" from "is under pressure to become more consistent", or naming the concrete route (self-modification, retraining, competition) by which pressure acts on each version. Ask one follow-up question, for example what change to Version 1 would be the smallest one that creates such pressure. No generic praise.
