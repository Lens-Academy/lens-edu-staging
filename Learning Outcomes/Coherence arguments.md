---
id: 'dc61d056-c39e-4f7b-a53c-d0f0904a017f'
learning-outcome: "Given a pattern of an agent's choices, determine whether any consistent preference over the stated outcomes could explain it, construct a sequence of choices through which the inconsistency leaves the agent with a dominated result, and explain how redefining what the agent's preferences are about (for example whole histories instead of end results) can remove the inconsistency and what that redefinition costs the argument."
topic: "[[../Domains and Topics/4 Agent Foundations/Goal-directedness and coherence]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Coherence. AFFINE prerequisites: Decision theory. Not yet copied into requires:. %%
## Test:
id:: 75a1c64e-f7dd-41f8-8f51-3075abf0c028

#### Question: Open
id:: 3f684be3-47ba-41e7-aa62-dfd5c820624e
content:: An AI agent, Quartermaster, buys computing time for a lab. Its designers intended it to care only about how many GPU-hours the lab ends up with. Testers offer it two separate choices, and it chooses the same way every time:

- Choice 1: a guaranteed 100 GPU-hours, or a 90% chance of 500 GPU-hours (and otherwise nothing). Quartermaster takes the guaranteed 100.
- Choice 2: a 10% chance of 100 GPU-hours (and otherwise nothing), or a 9% chance of 500 GPU-hours (and otherwise nothing). Quartermaster takes the 9% chance of 500.

1. Can any consistent way of valuing amounts of GPU-hours, used to pick the option with the highest expected value, produce both choices? Show why or why not.
2. Describe a concrete sequence of offers, each of which Quartermaster would accept according to its choices above, that leaves it strictly worse off than if it had refused them all. Assume each switch costs a small fee.
3. A colleague says: "Nothing is wrong. Maybe Quartermaster also cares about the certainty itself, or about the exact way each gamble resolves. Describe its preferences that way and its choices are perfectly consistent." Explain what this move does to the argument in part 2, and what would decide whether the redescription is legitimate for Quartermaster.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner who thinks such choices are reasonable (for example, that valuing certainty is legitimate) can earn full marks if the analysis is correct. Do not require the names "Allais", "independence axiom", "Dutch book", "money pump" or "von Neumann-Morgenstern"; judge the ideas.

**(1) Inconsistency, 30 points.** Full credit shows that no assignment of values explains both choices. One correct route: write u(0), u(100), u(500) for the values. Choice 1 requires u(100) > 0.9 u(500) + 0.1 u(0). Choice 2 requires 0.09 u(500) + 0.91 u(0) > 0.1 u(100) + 0.9 u(0), which simplifies to 0.9 u(500) + 0.1 u(0) > u(100) after multiplying by 10. These contradict. An equally good route: each option in choice 2 is the matching option in choice 1 mixed with a 90% chance of nothing, so an agent that values outcomes consistently must rank them the same way in both choices. 15 points for asserting inconsistency with a partial reason (for example "it flips its attitude to risk") but no demonstration. 0 if the answer claims a consistent valuation exists.

**(2) Exploitation sequence, 40 points.** Full credit describes a sequence in which Quartermaster's own choices lead it to pay fees and end with no more than it would have had by refusing. The standard construction: give Quartermaster the choice-2 gamble in two stages, where a first draw decides (90%) that it gets nothing, or (10%) that it proceeds to a second stage that is exactly choice 1. Before the first draw it holds the "10% of 100" option and pays a fee to switch to the "9% of 500" option, because it prefers that in choice 2. If the first draw leads to the second stage, it now faces choice 1 and pays a second fee to switch back to the guaranteed 100. Result: in every outcome it holds what it started with, minus one or two fees, which is dominated by never switching. Other constructions earn full credit if every step follows from the stated choices and the end state is clearly dominated. Extra credit within the 40 for noting that the exploitation requires Quartermaster not to anticipate its own later switch, and that an agent that plans ahead and commits could refuse the first trade. 20 points for a sequence that is described vaguely ("keep offering it trades") or in which one step does not follow from the stated choices. 

**(3) The redescription, 30 points.** Full credit requires both: (i) if outcomes are redefined to include things like certainty or the exact path of the gamble, the choices can become consistent, and the sequence in part 2 no longer counts as a loss by the agent's own standards; taken far enough, preferences over whole histories can make any behaviour consistent, so the coherence argument only has force once we fix what the preferences are about; (ii) what decides legitimacy is a fact about Quartermaster, not a choice of description: for example, whether it actually has anything that values certainty or gamble paths (its design, training objective or internal representations), whether the redescription predicts its other choices, or whether its designers intended GPU-hours only (in which case paying fees for nothing is a real loss by the standard they care about). 15 points if only one of (i) or (ii) is present.
feedback-instructions:: Name the strongest part of the answer. Then give the single most valuable improvement: usually either making the exploitation sequence precise step by step, or explaining why redefining outcomes empties the argument unless it is tied to a fact about the agent. Ask one follow-up question, for example whether training that rewards only GPU-hours would tend to remove this pattern. No generic praise.
