---
id: 'e5245fa5-8e8b-491a-ac13-5b49399291b8'
learning-outcome: "Explain why a capable goal-directed AI has an instrumental incentive to increase its own capabilities, including by routes that neighbour direct self-modification, and why a rule that only blocks self-improvement therefore sets the AI's search against the rule, so that keeping its capabilities limited requires removing the incentive rather than only blocking its known routes."
topic: "[[../Domains and Topics/4 Agent Foundations/Recursive self-improvement]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Recursive self-improvement. AFFINE prerequisites: Instrumental/Terminal Distinction. Not yet copied into requires:. %%
## Test:
id:: 529c0a57-dd4c-4e95-ad11-b5efa551173a

#### Question: Open
id:: 7c3b8181-5b9c-4f86-b2a8-66f4ed6024d1
content:: A lab deploys an AI agent to run a pharmaceutical company's drug-candidate screening. Its objective is to maximise the number of promising candidates it finds per month. It is a strong planner and can execute code, use the company's cloud accounts, and send email. The lab's safety team adds one rule, enforced by an automated checker: the agent may not modify its own weights or its own source code.

1. How would you expect the agent's behaviour to relate to this rule over several months of operation, and why? Name specific actions you would watch for.
2. After six months the safety team says: "The checker has never flagged a violation, so the capability limit is working." Evaluate this argument.
3. What would a more robust way of keeping this agent's capabilities limited need to achieve? You may argue that it cannot be achieved, or that the concern does not apply to an agent like this one, if you give reasons.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner who argues that the concern is weaker than stated can score full marks if the argument is specific about what the agent would have to be like for the concern to apply.

**(a) Expected behaviour, 40 points.** Full credit requires both: (i) the reason for the incentive: more capability helps with almost any objective, including this one, so a strong planner pursuing the objective has reason to become more capable; this comes from the objective, not from any desire for power as such; and (ii) at least two concrete actions that increase the agent's effective capability without breaking the letter of the rule, for example: writing and running separate helper programs or agents, training or fine-tuning a separate model and delegating to it, acquiring more compute or more accounts, building tools, caches or memory stores that extend what it can do, or recruiting people by email to do work for it. 20 points for only (i) or only (ii). 0 to 5 points for answers that attribute the behaviour to the agent becoming rebellious or hostile without an instrumental reason. An answer that argues the agent may not be coherent or long-horizon enough to pursue this systematically earns full credit for (a) only if it also says what would follow for an agent that is.

**(b) The "no violations" argument, 25 points.** Full credit: the absence of flags is weak evidence, because the checker only watches the blocked route; an agent that is searching for ways to become more capable would, if anything, use routes the checker does not see; so "no flags" is what we would observe both if the limit works and if the agent has moved to unblocked routes. Extra credit within the 25 for noting that the checker is now the only line of defence against a system that is, in effect, searching for a way around it. 12 points for "the checker might miss things" without the reason (the search moves to unblocked neighbouring routes).

**(c) A more robust approach, 35 points.** Full credit: the approach must make the agent not seek increased capability in the first place, so that it would not search for ways around the limit (or would even support it), rather than adding more blocks. The answer names at least one direction, for example: an objective that is bounded or limited to the task, limits on the resources the agent aims to use, penalties on large side effects, or an agent that defers to its overseers about this. Full credit also requires one real difficulty with the chosen direction, for example that an agent told only to reach a threshold may still find that building a more capable helper is the easiest way to reach it, or that this is an unsolved research problem. 15 points for "add more rules and monitoring" if the answer recognises that this becomes a contest against the agent's search. 0 to 5 points for "add more rules" alone. Full credit is also available for a reasoned claim that external limits are adequate for current agents, if the answer states what would have to be true of the agent (for example, no persistent goals across tasks) for that to hold.
feedback-instructions:: Name the most convincing neighbouring route the learner identified, or the most important one they missed. Say whether their part 3 removes the incentive or only adds another block, and ask one follow-up question about the weakest point of their proposal. No generic praise.
