---
id: 'fc73949e-aa1c-4842-a62f-fac5d5e92807'
learning-outcome: "Given a self-locating problem in which the number of observers depends on an unknown fact, compute the credences that the self-indication and self-sampling assumptions give, explain which question about proportions of observers each credence answers and how the reference class changes the self-sampling answer, and show how the choice between them depends on how the decision-maker values outcomes across its copies."
topic: "[[../Domains and Topics/4 Agent Foundations/Acausal reasoning and anthropics]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Anthropics. AFFINE prerequisites: Decision theory. Not yet copied into requires:. %%
## Test:
id:: 36976c58-3734-46ae-9c4e-d9c1fb17ea8f

#### Question: Open
id:: deb2744f-ea60-475b-9f89-7058e57f62ea
content:: A lab runs an experiment on an uploaded mind. It flips a fair coin in secret. On heads it starts 1 copy of the mind; on tails it starts 3 copies. Every copy wakes with identical memories and cannot tell how many copies exist. You are one of the copies, and you have just woken up.

1. What credence should you give to heads? Give the answer of the self-indication assumption (SIA) and the answer of the self-sampling assumption (SSA) when the reference class contains only the copies. For each number, state what question about observers it answers.
2. Now suppose the reference class also contains 1,000 other people, who are awake in both the heads world and the tails world. Does either answer change? Explain.
3. Each copy is offered a ticket that costs 3 credits and pays 10 credits if the coin landed heads. All copies reason identically, so they all make the same choice. Should a copy buy the ticket (i) if all credits go into one shared fund and the copies care about the fund's total, and (ii) if the copies care about the average number of credits per copy in their world? Show your reasoning.
4. Which credence, if either, would you use, and why?
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from four components. Grade reasoning, not agreement: the learner may defend SIA, SSA, or the view that neither credence is privileged, and can score full marks for any of these if the argument is sound. Accept any correct calculation route and any equivalent terminology.

**(a) The two credences and their questions, 30 points.** SIA gives 1/4 for heads. It answers a question like "of all the observers in this situation, across the possible worlds weighted by their probability, what fraction are in a heads world?" (1 observer in the heads world against 3 in the equally likely tails world). SSA with only the copies in the reference class gives 1/2. It answers a question like "averaging over worlds by their probability, what fraction of the reference class in each world is in a heads world?" (each world counts once, however many observers it holds). 15 points per assumption: 8 for the correct number, 7 for a correct description of what it measures. A description that says only "SIA favours worlds with more observers" earns 3 of the 7.

**(b) Reference class, 20 points.** 8 points: the SIA answer stays at 1/4, because SIA weights worlds by the number of observers and then asks which of them are copies, so adding observers present in both worlds cancels out. 12 points: the SSA answer moves from 1/2 to very close to 1/4, because being a copy is now much less likely in the heads world (1 of 1,001) than in the tails world (3 of 1,003). The exact value (1003/4006, about 0.2504) is not required. Give 6 of the 12 for saying only that the SSA answer depends on the reference class without the direction of the change.

**(c) The ticket, 35 points.** (i) Total: do not buy. Heads (probability 1/2): one ticket nets +7. Tails (probability 1/2): three tickets each lose 3, total -9. Expected total -1. (ii) Average: buy. Heads: average +7. Tails: average -3. Expected average +2. 17 points for (i) and 18 for (ii), each split between the correct verdict (7 or 8) and valid reasoning (10). Equivalent routes get full credit, for example SIA credence 1/4 applied to one copy's own ticket and its effect on the total (0.25 x 7 + 0.75 x (-3) = -0.5), or SSA credence 1/2 applied to per-world averages. A verdict with no reasoning earns only the verdict points.

**(d) Choice of credence, 15 points.** Full credit for a defended position that uses the earlier parts, for example: SIA, because without exact duplicates it is ordinary Bayesian updating on one's existence and it matches total-value bets; SSA, with a reason for its reference class; or "the credence to use depends on the question asked or on how one values copies, as part (c) shows". 5 points for a bare preference with no reason tied to parts (a) to (c).
feedback-instructions:: Say whether the learner tied each number to the question it answers, since that is the core of the skill. Name the strongest part of the answer and the single change that would improve it most, for example the missed effect of the reference class, or a betting verdict that does not follow from the stated credence. Ask one follow-up question, such as what the copies should do if each copy cares only about its own credits. No generic praise.
