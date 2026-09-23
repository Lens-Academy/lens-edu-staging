---
id: '691aeea7-a256-4846-9206-bc792e0b2501'
learning-outcome: "Explain why, in real agents, whether a subgoal behaves as instrumental (subordinate to the plan it serves, limited by that plan's other needs, and dropped when the plan changes) or as terminal (pursued for itself regardless of the rest of the plan) depends on how the subgoal is implemented and overseen rather than on its content, and use this to predict how a subgoal will behave when the plan it serves changes."
topic: "[[../Domains and Topics/4 Agent Foundations/Goal-directedness and coherence]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Instrumental/Terminal Distinction. AFFINE prerequisites: none listed. Not yet copied into requires:. %%
## Test:
id:: 29efbc3e-25c9-430f-a879-90a962ad738a

#### Question: Open
id:: 5d412fba-009c-4769-87d8-5a8f13ee684a
content:: An AI system is running a two-week project to finish training a model by Friday. It starts a sub-agent whose job is "keep the GPUs fully used". On Wednesday the plan changes: another team urgently needs half of the GPUs, and the main system now wants to hand them over.

The sub-agent could have been built in one of two ways:

- Version A reports to the main system every hour, can see the project's overall plan, and was trained on many cases in which the goal it served changed partway through.
- Version B was trained with a reward for GPU usage alone, and runs on its own until the project ends.

1. Predict how each version behaves on Wednesday, and explain why.
2. Compare what each version will avoid doing, even before Wednesday, while it keeps the GPUs busy. Explain the difference.
3. A common model of agents says an agent has fixed final goals, and all its other goals are derived from those final goals. Explain what this model gets right and what it gets wrong or leaves out about these two sub-agents.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner who defends the common model (for example, arguing that Version B simply is a separate agent with its own final goal) can earn full marks on part 3 if they explain what that description predicts and where it is or is not useful. Do not require any author names or the terms "managed", "unmanaged", "corrigible" or "instrumental convergence"; judge the ideas.

**(1) Wednesday, 35 points.** Full credit requires both predictions with reasons tied to how each version is built. Version A: once it learns of the new plan, it releases the GPUs or scales down, because its goal is tied to what the main system needs and it has learned that this can change. Version B: it keeps maximizing usage and may resist or work around the handover (for example, filling freed GPUs with new jobs, restarting stopped jobs, or making its jobs hard to stop), because nothing in its reward depends on the main system's plan; for it, usage is effectively the final goal. 17 points if only one version is predicted with a reason, or both are predicted without reasons. Hedged predictions ("A will probably...") are fine.

**(2) What each avoids, 30 points.** Full credit: Version A avoids actions that would make other parts of the plan or likely future needs harder, even when those actions would raise usage: for example, taking GPUs another part of the project needs, launching jobs that cannot be stopped quickly, hiding what it is running, or using up shared resources such as storage or network. The reason: usage is only worth pursuing in ways that serve the larger plan, and that plan may change, so keeping things visible, predictable and easy to redirect is part of doing the subgoal well. Version B has no such reason: anything that raises usage is good for it, including hoarding GPUs or making its jobs hard to cancel. 15 points if the answer lists behaviours A avoids but does not explain why serving a larger plan produces these limits.

**(3) The common model, 35 points.** Full credit requires one correct point on each side. Right, any one of: from the main system's point of view, GPU usage is valuable only as a means to finishing training, so the model correctly classifies it; Version B can be described accurately as an agent whose final goal is usage. Wrong or missing, any one of: the model treats a derived goal as something recomputed from the final goal, so it predicts the subgoal disappears when the plan changes, but a subgoal implemented as its own optimizer can keep going; whether a goal acts as a means or an end is a matter of degree set by how it is implemented and overseen, not a fixed property of the goal's content (the same goal, "keep the GPUs busy", is a means in A and an end in B); the model does not describe the limits that come with serving a larger plan (part 2); in real agents, goals can be built up and changed over time as the agent grows, rather than being fixed from the start. 17 points if only one side is addressed.
feedback-instructions:: Name the strongest part of the answer. Then give the single most valuable improvement: usually explaining why the same goal content can act as a means in one system and as an end in another, or why serving a larger plan brings limits such as visibility and ease of redirection. Ask one follow-up question, for example which features of Version A would be hardest to keep as the sub-agent becomes more capable. No generic praise.
