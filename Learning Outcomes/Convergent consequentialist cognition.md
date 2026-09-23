---
id: '9323d0ff-00d4-4848-925e-f8f248461507'
learning-outcome: "Explain why a system optimized to reliably achieve hard, novel outcomes tends to acquire or reintroduce consequentialist cognition (choosing actions or plans by their predicted effects on outcomes), locate where that cognition would re-enter a system designed not to be an agent, and identify conditions under which this argument weakens."
topic: "[[../Domains and Topics/4 Agent Foundations/Agency]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Agency. AFFINE prerequisites: Optimization, Decision theory. Not yet copied into requires:. %%
## Test:
id:: d483da98-ab43-49a0-b2ab-0a02d3829823

#### Question: Open
id:: da75bc65-80f6-4a0f-89eb-6a2bc14160e5
content:: A lab builds an AI system called Atlas and calls it safe because it is "not an agent". Atlas has no memory between queries and cannot take actions: it only outputs written plans. It was trained first to imitate plans written by expert engineers, and then fine-tuned with reinforcement learning, where reviewers scored each plan by how well it actually worked when people carried it out.

The lab now asks Atlas for a plan to get a working vaccine factory running within 12 months in a region with unreliable power, no trained staff and hostile local politics. Nobody has written a plan for a comparable project before.

The lab's safety lead says: "Worries about power-seeking come from agents that pursue goals. Atlas only answers questions, so those worries do not apply here."

Write a reply to the safety lead that:

1. explains why the demands of this task push toward something in the system choosing plans by their predicted consequences, even though Atlas itself takes no actions;
2. identifies two specific places in this setup where that kind of cognition could enter, and how;
3. describes one change to the task or the training under which the safety lead's claim would be more defensible, and explains why that change helps (or argues that no change could make it defensible without making Atlas useless, and explains why).
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement. A learner who thinks the underlying argument is overstated can score full marks if they reconstruct it accurately before arguing against it. Do not require any technical vocabulary ("consequentialism", "mesa-optimizer", "instrumental convergence"); judge the ideas.

**(a) Why the task pushes toward consequence-based choice, 40 points.** Full credit requires both of these ideas, in any wording: (i) because the task is novel and hard, there is no stored template to copy, and only a small fraction of possible plans would work, so whatever produces a working plan has to find it by predicting which plans lead to the outcome and selecting on that (or has been trained to do so, since the reinforcement learning rewarded plans for their actual results); (ii) this does not depend on Atlas acting: the selection can happen inside the model when it produces the plan, and the humans who carry out the plan supply the actions. Extra credit within the 40 for noting that a plan that works under obstacles like these will tend to include steps that gain resources, influence or control, because such steps help with almost any hard goal, which is what the safety lead's worry is about. 20 points if the answer says hard tasks "need planning" or "need intelligence" without explaining why novelty and difficulty force selection by predicted outcome, or without addressing why taking no actions does not remove the concern. 0 to 10 for "any AI can be dangerous" with no mechanism.

**(b) Two entry points, 36 points (18 each).** Each must name a specific place and say how consequence-based choice arises there. Acceptable entry points include, among others: the reinforcement-learning stage selecting for internal cognition that predicts which plans will work; imitation of expert planners requiring the model to represent the planners' own reasoning about consequences; the plan itself being a goal-directed artifact whose steps are chosen for their effects and executed by people; the plan containing or calling automated components (scripts, repeated queries to Atlas in a loop, other AI tools) that act in the world; the humans choosing among many generated plans by predicted success, which completes the selection loop. Two entry points that are really the same mechanism in different words count as one. A vague "somewhere inside the network" without saying how gets at most 5 per item.

**(c) A condition that weakens the argument, 24 points.** Full credit: a concrete change plus an explanation that ties it to the mechanism in (a). Examples: tasks that are routine and close to existing expert plans, so imitation suffices and no new search is needed; scoring plans by whether reviewers understand and approve each step rather than by real-world results; short, narrow tasks where plans cannot include steps that reach into other domains; a stable environment where reusing known procedures reliably works. Also give full credit to a reasoned argument that no change keeps Atlas useful for tasks like this one while removing the concern, if the answer explains why usefulness and consequence-based choice come together. 10 points for a change stated without an explanation that connects it to the mechanism, or for a change that does not bear on it (for example "add a content filter" with no argument).
feedback-instructions:: Name the strongest part of the answer, quoting or paraphrasing it. Then give the single change that would most improve it: usually either making explicit why novelty and difficulty force selection by predicted outcome, or making an entry point concrete. If the learner disagreed with the argument, engage with their strongest objection seriously and say what evidence would bear on it. Ask one follow-up question. No generic praise.
