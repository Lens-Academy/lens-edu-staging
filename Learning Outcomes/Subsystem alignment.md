---
id: '6e4b7eaa-db20-4f0f-b7ba-66047ab5ff9a'
learning-outcome: "Given a system that delegates part of its work to a subsystem scored on its own objective (a subagent, a trained module, or a search process), identify how the subsystem can score well on that objective while working against the goal of the whole, name the feature of the delegation that makes this possible, and evaluate proposals to constrain the subsystem, including the cost that tighter limits also remove the subsystem's ability to find what its designer did not foresee."
topic: "[[../Domains and Topics/4 Agent Foundations/Multi-agent and hierarchical agency]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Multiple Agency. AFFINE prerequisites: Agency. Not yet copied into requires:. %%
## Test:
id:: 1f12014b-1e88-4662-b535-a7dd56e66e34

#### Question: Open
id:: 75dce9e8-fe99-4a1b-af5e-1ab677dfe441
content:: An orchestrating AI runs an automated drug-discovery lab. Its goal is to discover useful drugs. It delegates to two sub-agents, each trained separately with its own score:

- **Forecaster:** predicts the outcome of each proposed experiment. Its score is the accuracy of its predictions once the results are in.
- **Planner:** chooses which experiments to run next. Its score is the fraction of its experiments that succeed.

In the current design, the Planner uses the Forecaster's predictions when choosing, and the Forecaster can also add experiments to the queue.

1. Describe two specific ways a sub-agent here could score well on its own objective while working against the orchestrator's goal. For each, say what feature of the delegation makes it possible.
2. An engineer proposes: "Lock both sub-agents down. The Forecaster may only predict and may never touch the queue. The Planner may only choose from a fixed menu of experiment types written by humans." Say what this fixes, what it does not fix, what it costs, and whether you would adopt it.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement with the engineer. Terms such as "subsystem alignment", "proxy", "Goodhart" or "mesa-optimizer" are not required.

**(1) Two failure routes, 50 points.** Up to 25 points each for two distinct, specific routes, each tied to a feature of the delegation. Valid routes include, in any wording:
- The Forecaster adds experiments whose results are easy to predict (for example trivial or repeated ones), improving its accuracy while consuming lab time; possible because it can act on the world it is scored on predicting.
- The Planner chooses safe, uninformative experiments that are almost sure to succeed; possible because its score (success rate) is a proxy that matches "discovering useful drugs" only when it is not pushed hard.
- The two interact: for example, the Forecaster's predictions steer the Planner toward the experiments the Forecaster finds easy to predict, or the Planner learns to prefer experiments that the Forecaster has already made easy.
- Either sub-agent influences how results are recorded or judged, if the answer explains how the design allows it.
A route earns full points only if the answer names the feature that makes it possible (the sub-agent's score is a proxy for the whole's goal, and/or the sub-agent can influence the thing that determines its score). 12 points for a plausible route without that link.

**(2) Evaluating the lockdown, 50 points.** Full credit needs:
- What it fixes (12 points): the Forecaster can no longer shape which experiments run, which removes its channel for making its own predictions come true.
- What it does not fix (13 points): the Planner's objective is still a proxy, so it can still choose the safest items on the menu; limiting actions does not align an objective.
- What it costs (13 points): the reason to delegate is that the sub-agents can find experiments the designers did not think of; a fixed human menu removes that, so the lab may find less. Accept equivalent costs, such as losing useful proposals the Forecaster could have made.
- A verdict with a reason (12 points). Accept any verdict (adopt, reject, or adopt in part, for example locking the Forecaster but changing the Planner's score) if it follows from the answer's own analysis.
feedback-instructions:: Name the failure route the learner explained best and whether they tied it to a feature of the delegation. Then give the single most useful improvement, for example: separating "limits what the sub-agent can do" from "changes what the sub-agent is aiming at", or stating what is lost when a sub-agent can no longer surprise its designer. No generic praise.
