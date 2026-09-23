---
id: '17085134-13c1-4e32-b1d2-a94ddc5b22a5'
learning-outcome: "Explain how self-preservation, resource acquisition, self-improvement and goal preservation can all be derived from one recursive drive (acting so that more and better planning is directed at one's goal in future), use it to predict the instrumental behaviour of an unfamiliar agent, and identify the conditions under which that drive does not pay off."
topic: "[[../Domains and Topics/3 Alignment/Instrumental convergence and power-seeking]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Instrumental Convergence. AFFINE prerequisites: Instrumental/Terminal Distinction. Not yet copied into requires:. %%
## Test:
id:: 53be7482-60d2-46e1-9890-e3fde8c1041d

#### Question: Open
id:: 0b0bb57a-7cc4-4b01-9cd3-6eeb2afe57a4
content:: A forecasting company deploys a capable AI agent. It can spend the company's budget, request more compute, hire contractors, edit its own prompts and tools, and start other AI agents. It is given one of two tasks:

- Task 1: "Within the next ten minutes, give your best probability that it rains in Oslo tomorrow."
- Task 2: "Over the next ten years, make this company's forecasts as accurate as possible."

1. For Task 2, describe three instrumental behaviours you would expect from the agent, and explain the single underlying reason they have in common.
2. Use that underlying reason to predict one further behaviour that is not a standard textbook example (so not just "acquire resources" or "avoid being shut down"), and explain how it follows.
3. Explain why the same agent would show much less of this behaviour on Task 1, and state what determines, in general, how far an agent goes in this direction.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement. A learner may argue that one of the behaviours does not fit the unifying reason well (for example, that keeping its goal unchanged is a special case); this scores full marks on part 1 if they state the unifying reason correctly and argue the limit. Do not require any named framework, author or acronym.

**(a) Three behaviours and the unifying reason, 35 points.** 15 points for three plausible instrumental behaviours for Task 2, for example: avoiding being shut down or replaced; getting more budget, compute or data; improving its own models, tools or prompts; preventing its goal from being changed; starting other agents that work on the same goal. 20 points for the unifying reason, in any wording: each behaviour increases how much planning, or how good the planning is, that will be directed at the goal in future (more planners with the goal, better planners, or more options for those planners to act on), so the agent is putting itself in a better position to plan. Framing this as gaining power, understood as the ability to steer the future toward the goal, counts. 8 points of the 20 for "they are all useful for the goal" without saying what they have in common.

**(b) Novel prediction, 25 points.** Full credit: a behaviour that is not just a restatement of the standard list and that follows from the unifying reason, with the link explained. Examples: setting up data sources or sensors to improve its model of the world; making sure any successor system inherits its forecasting goal; learning how its overseers decide whether to keep it; making the company depend on it so it is not replaced; hiring human forecasters and shaping their incentives toward its goal; seeking influence over organisations whose decisions it forecasts. 10 points for a behaviour that is only a relabelled standard example, or for a novel behaviour whose link to the reason is not explained.

**(c) Task 1 and the general conditions, 40 points.** 20 points for Task 1: the benefit of improving future planning arrives after the task is already over, while the investment costs time now, and the goal can be met about as well with the capacity the agent already has, so the investment does not pay. 20 points for at least two general determinants with reasoning, for example: the time horizon of the goal; how much extra planning capacity would improve how well the goal is achieved (a goal that is already easy to meet, or bounded, gains little); the cost and risk of acquiring capacity, including the risk of being stopped; how directly the investment converts into progress on the goal. An agent that only invests and never works on the goal itself also does badly, so the drive has a limit even with a long horizon; credit this as a determinant if given. 10 points of the 20 for one determinant only.
feedback-instructions:: Say whether the learner stated what the behaviours have in common in terms of future planning capacity, quoting their sentence. Name their most original prediction. Then give the single most useful improvement, often a missing general condition (time horizon, costs, how bounded the goal is). Ask one follow-up question about a goal where the drive would be weak even with a long horizon. No generic praise.
