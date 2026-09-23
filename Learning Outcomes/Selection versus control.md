---
id: '75aa3e0f-8206-4587-87e2-2fa910ca42d7'
learning-outcome: "Distinguish selection (a process that can generate and score many candidate options, where only the final pick matters) from control (a process that acts along one real trajectory, where every intermediate action has consequences and must be chosen from feedback and predictions of what would happen otherwise), classify each level of a given system as one or the other, and explain why finding no internal search in a system does not show that it is not a strong optimizer."
topic: "[[../Domains and Topics/4 Agent Foundations/Optimization]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Selection and Control. AFFINE prerequisites: Optimization. Not yet copied into requires:. %%
## Test:
id:: e0a284ec-56bf-45df-ac8c-d985c3820d8b

#### Question: Open
id:: 79fff69d-0281-49cb-a86c-4243cba75bb8
content:: A data centre's cooling is run by one of two AI systems.

- **System 1.** Every minute it uses a learned model of the building to simulate 10,000 candidate valve settings, scores each simulated outcome, and applies the best one to the real valves.
- **System 2.** A small neural network trained with reinforcement learning. Every minute it maps current sensor readings to valve settings in a single pass, with no simulation and no comparison of alternatives. In testing it holds the temperature within 0.1 °C through heat waves, server surges and a failed pump.

An auditor writes: "System 1 is an optimizer, because it searches over options. System 2 is only a reflex. So only System 1 needs to be checked for optimization-related risks."

1. For each system, say whether what happens inside it and what happens in the building is better described as selection or as control, and why.
2. Evaluate the auditor's conclusion.
max-chars:: 2000
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement with the auditor or with any author. The words "selection" and "control" are given in the question; other terminology (search versus steering, offline versus online optimization) is acceptable if the distinction is the same.

**(1) Classification, 50 points.** The distinction that must be applied: selection can instantiate and score many options, and only the pick counts; control acts once along a real trajectory, so each intermediate action has real consequences and the system must rely on feedback and predictions about alternatives it never tries.
- System 1 (25 points): control in the building (one real sequence of valve settings; each minute's setting affects the next state) implemented by selection inside a model (the 10,000 candidates exist only as simulations and only the chosen one is applied). Full credit needs both levels and the reason. 12 points for calling it only "selection" or only "control" with a correct reason for that level.
- System 2 (25 points): control in the building, with no selection inside at run time. Full credit also requires a reason (it steers one real trajectory using feedback). Accept, as a strong addition but not required, that its training by reinforcement learning was itself an optimization process run over many episodes, so selection-like pressure shaped the policy even though the policy does not search.

**(2) Evaluating the auditor, 50 points.** Full credit: the auditor equates "optimizer" with "does internal search", but System 2 steers the temperature to a narrow target from many starting states and despite disturbances, which is strong optimization in the control sense; so the absence of internal search does not remove optimization-related risk (for example, a controller can pursue its target in ways its designers did not expect, or resist changes that push it off target). 25 points if the answer says System 2 also optimizes but gives no reason tied to its behaviour. Accept a partly agreeing verdict if argued, for example that search-based systems can find unanticipated strategies more flexibly and deserve extra scrutiny, provided the answer does not conclude that System 2 needs no check. An answer that agrees with the auditor without addressing System 2's demonstrated steering scores at most 10 of the 50.

Do not require any particular risk example; any specific way a strong controller can cause trouble is enough.
feedback-instructions:: Tell the learner whether they separated what happens inside each system from what happens in the building. Name the strongest point in their evaluation of the auditor. Then give the single most useful improvement, for example: pointing out that System 2's training process was itself a kind of selection, or giving a concrete way a search-free controller could still cause harm. No generic praise.
