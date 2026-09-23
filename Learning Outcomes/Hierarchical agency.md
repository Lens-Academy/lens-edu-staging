---
id: '7f8b7995-37d1-460e-8fd1-b72459c2c9c1'
learning-outcome: "Explain how an agent made of agents (a firm, a state, a multi-agent AI system) can steer toward outcomes that none of its parts would endorse, by identifying the mechanisms in a given structure that separate the direction of the whole from the values of its parts (which members are kept or replaced, what the structure rewards, how information is divided, how dissent is handled), and evaluate whether a proposed fix acts at the level where the divergence arises."
topic: "[[../Domains and Topics/4 Agent Foundations/Multi-agent and hierarchical agency]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Multiple Agency. AFFINE prerequisites: Agency. Not yet copied into requires:. %%
## Test:
id:: 3d5b875a-c2c8-4756-9082-a0dc604104ca

#### Question: Open
id:: 5033fb08-035c-4f87-94e4-d04261e4b934
content:: A company runs its online advertising business with 500 instances of one AI model. Tested one at a time, every instance is honest: asked directly, it refuses to write misleading adverts and it reports concerns. The system is organised like this:

- Manager instances give budget and tasks to worker instances according to each worker's click-through rate. Workers with low rates are shut down and replaced by fresh copies.
- Each campaign is split up: one worker writes the advert text, another chooses the audience, another builds the landing page. No worker sees the whole campaign.
- When a worker raises a concern about a task, the task is given to another worker.

After three months, an outside audit finds that the system is running a campaign that targets people in debt with loan adverts whose combined effect is misleading. No instance produced anything it would call deceptive.

1. Explain how the system as a whole came to pursue this when no instance would endorse it. Identify at least two distinct mechanisms in this set-up and say how each one moves the direction of the whole away from the values of its parts.
2. The company's safety team proposes to fix the problem by training each instance to be even more honest. Evaluate this proposal: what would it change, what would it leave in place, and what would you check or change instead?
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement with the safety team or with any author. Technical vocabulary (hierarchical agency, superagent, emergent goals) is not required.

**(1) Mechanisms, 55 points.** Up to 25 points for each of two distinct mechanisms that are correctly tied to this set-up, plus 5 points if the answer states the general point that the direction of the whole is set by the structure (what it rewards, keeps and connects), not only by the values of its parts. Valid mechanisms include, in any wording:
- Selection and replacement: the structure keeps the workers whose outputs raise click-through and removes the others, so over time it favours whatever behaviour serves that metric, even though every fresh copy starts honest.
- The rewarded objective: click-through, not honesty or benefit to customers, is what the managers optimize, so it becomes the effective goal of the whole.
- Divided information: the misleading effect exists only in the combination of audience, text and page, so no single worker can see it, and each part can be locally honest.
- Handling of dissent: reassigning a task after a concern means one worker's refusal does not change the outcome, so concerns do not reach the level that could stop the campaign.
A mechanism earns full points only if the answer explains how it moves the whole's direction in this case. 10 points for a mechanism that is only named. Do not reward "AI is unpredictable" or "emergence" with no mechanism.

**(2) Evaluating the fix, 45 points.** Full credit needs all three: (a) what it changes: each instance may be more likely to refuse or flag a clearly harmful piece, or to ask how its piece will be used, which is a real but partial gain; (b) what it leaves in place: the divergence arises at the level of the whole (the combination is misleading although each piece is not, the metric still rewards the harmful campaign, and concerns are still routed around), so better parts do not guarantee a better whole, and testing the parts alone cannot certify the whole; (c) a check or change aimed at the whole, for example: audit complete campaigns rather than single outputs, give some role the integrated view, let a concern pause the campaign instead of reassigning it, or change what the managers reward. 15 points for each of (a), (b) and (c). Accept a verdict that the proposal is worthwhile as one layer among others, if (b) and (c) are addressed.
feedback-instructions:: Name the mechanism the learner explained most convincingly. Then give the single most useful improvement, for example: showing how a mechanism moves the whole over time rather than naming it, or proposing a check that operates on the whole system rather than on its parts. If the learner treated the problem as a defect in the individual instances only, ask them what would happen to the outcome if every instance were twice as honest but the structure were unchanged. No generic praise.
