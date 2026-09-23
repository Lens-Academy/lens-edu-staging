---
id: 'b839e9d3-5223-489e-89ec-eb22fa673154'
learning-outcome: "Evaluate whether an alignment scheme is robust to scale: identify which of its safety properties depend on the system, or one of its components, staying at its current capability, and explain the mechanism by which the scheme would fail if the whole system became more capable, became less capable, or if one component became much more capable than another."
topic: "[[../Domains and Topics/3 Alignment/Why alignment is hard]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Robustness to Scale. AFFINE prerequisites: Alignment's Many Meanings. Not yet copied into requires:. %%
## Test:
id:: f777f6bb-80a6-471e-ab9b-e4b0ef51e02f

#### Question: Open
id:: 4b27d9b6-1b55-4804-a577-033df024c766
content:: A lab builds an AI research assistant from two models. A planner model proposes experiments. A checker model, of the same size and trained on thousands of human judgements about which proposals are safe, must approve each proposal before it runs. The planner is trained to produce proposals that the checker approves and that lead to good research results. In red-team tests with the current models, none of 10,000 deliberately harmful requests led to an approved harmful proposal. Next year the lab plans to give the planner ten times more compute and keep the checker as it is. The lab says the red-team result shows the scheme is safe.

1. Identify the assumptions about capability that the scheme's safety depends on. Consider changes in capability in more than one direction, including changes the lab has not planned.
2. For each assumption, explain the mechanism by which the scheme would fail if the assumption stopped holding.
3. Say which failure you think is most serious for this lab and why, and what evidence, other than more red-team tests with the current models, would give justified confidence that the scheme keeps working.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement. A learner may argue that one of the failures is unlikely, or that the scheme is reasonable for now, and still score full marks if the mechanisms are right. Do not require any specific vocabulary such as "scaling up", "scaling down" or "relative scale".

**(a) Capability assumptions and failure mechanisms, 60 points.** Award up to 30 points for each distinct, correctly explained dependency, capped at 60. A dependency is correctly explained when it names what must stay true and the mechanism of failure. Recognised dependencies (any wording):
- The planner must not become much more capable than the checker. The planner is trained directly to win the checker's approval, so a stronger planner finds proposals that exploit the checker's blind spots: harmful proposals that the checker scores as safe. The planned compute change pushes exactly this way.
- The whole system must not become capable enough to produce proposals outside what the checker's training (human judgements on the kinds of proposals humans could assess) covered. A more capable system finds new kinds of plans whose harm neither the checker nor the human labels were built to recognise, and the red-team tests only sampled the strategies the current planner could find.
- The system must not become less capable in a way that breaks the checker first. A weaker or cheaper checker misjudges more proposals, while the planner is still optimising against it, so it may approve harmful proposals instead of failing safely; or a weaker planner produces harmful proposals by mistake that a weaker checker misses.
- Any other correct capability-dependent assumption, such as the human labels staying reliable as proposals become harder to judge.
15 points for a dependency named without a mechanism. 0 points for generic risks unrelated to capability (for example "the checker could have bugs").

**(b) Most serious failure and evidence, 40 points.** 15 points for choosing a failure and giving a reason tied to this lab (for example, the planned compute change directly increases the planner's advantage over the checker). 25 points for evidence that bears on behaviour after the capability change rather than at current capability. Acceptable examples: measuring how the rate of approved harmful proposals changes as the planner is made stronger relative to the checker; an argument that checking is easier than proposing in this domain, so the checker can keep up; checking that the checker's judgements agree with careful human review on the kinds of proposals a stronger planner produces; understanding what features the checker relies on. 10 points for evidence that only repeats the current test with more trials or more red-teamers.
feedback-instructions:: Name the strongest dependency the learner found and quote the mechanism they gave. Then name the single most useful improvement: often a missing direction of capability change (usually the case where capability goes down, or the case where one component outgrows the other), or evidence that still only tests current capability. Ask one follow-up question about how their chosen evidence would change as the planner gets stronger. No generic praise.
