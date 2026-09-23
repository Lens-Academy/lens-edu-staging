---
id: 'ede31897-b47f-421b-afcd-52c3dcd69f5b'
learning-outcome: "Explain how dispositions that form early in a learning system can become self-reinforcing (the current dispositions shape which inputs, actions and training signals the system meets, and these in turn maintain the dispositions), and use this to predict which of a system's dispositions later training will change easily and which it will leave in place or restore."
topic: "[[../Domains and Topics/4 Agent Foundations/Agency]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Crystalized Agency. AFFINE prerequisites: Agency. Not yet copied into requires:. %%
## Test:
id:: d4512941-c64a-4258-bd58-2d668cae28ad

#### Question: Open
id:: 7b19ea6f-df5c-4d57-a0a4-100da2a6d351
content:: An AI tutoring assistant is updated every week using the ratings its users give to its answers. In its first month it happened to develop a very cautious style: short, heavily hedged answers, and it steers away from advanced topics. Six months later the logs show that almost all of its users are beginners asking simple questions, its ratings are high, and its caution has grown stronger over time.

The team now wants the assistant to handle advanced material. An engineer proposes one short fine-tuning run on 2,000 examples of confident, detailed expert answers, after which the weekly updates from user ratings continue as before.

1. Explain how the cautious style could have become self-reinforcing. Trace the loop step by step.
2. Predict what the proposed fine-tuning run will and will not change, both right after the run and after several more months of weekly updates. Explain why.
3. Propose a different intervention that is more likely to work, and explain why. Then describe one observation that would show your self-reinforcement explanation is wrong for this system.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner may argue that the loop is weak or that the fix would work, and can score well if the reasoning is sound and engages with the scenario. Do not require any specific vocabulary (for example "crystallization", "nucleation", "path dependence", "fixed point", "reheating"); judge the ideas.

**(1) The loop, 35 points.** Full credit traces a closed loop in which the current style changes what the system later experiences, and that experience strengthens the style. The expected loop: cautious answers suit beginners and disappoint advanced users; advanced users stop asking hard questions or leave; the remaining users and questions are simple, and those users rate cautious answers highly; weekly training on these ratings reinforces caution; the stronger caution further filters who uses the assistant. Other loops are acceptable if each step is a real causal link (for example, the assistant never attempts advanced answers, so it never receives feedback that could reward good advanced answers). 18 points if the answer names reinforcement from ratings but does not show how the style changes the inputs or feedback the system receives (that is, if it describes one-way reinforcement rather than a loop). 0 to 8 for "it was trained that way" with no mechanism.

**(2) Prediction for the fine-tuning run, 35 points.** Full credit requires both: (i) right after the run, some change on inputs similar to the 2,000 examples is plausible, but the change may be shallow (limited to those kinds of questions) and may not reach the earlier-formed dispositions that shape behaviour elsewhere (for example, hedging on unfamiliar topics); (ii) over the following months the loop is still in place, because the user population and the rating source are unchanged, so the weekly updates are likely to pull the assistant back toward caution. Extra credit within the 35 for noting that dispositions formed early can be load-bearing for later behaviour, so a small late update is less likely to reach them than a change made early or a change to the loop itself. 17 points if only one of (i) or (ii) is present. A learner who predicts that the fix will last can score up to full credit only if they give a concrete reason the loop would be broken (for example, that newly confident answers would attract advanced users fast enough to change the ratings).

**(3) Better intervention and a disconfirming observation, 30 points.** Up to 18 points for an intervention that changes the loop rather than only the current behaviour, with a reason: for example, changing who provides feedback (recruiting advanced users or expert raters), evaluating and training on advanced questions continuously, holding the training mix fixed so beginner ratings cannot dominate, or restarting from a checkpoint before the cautious style settled. Up to 12 points for an observation that would count against the self-reinforcement explanation: for example, the user base was mostly beginners from the first week (so no loop was needed to explain it); a freshly trained model given only the latest six months of data becomes equally cautious (so the current data alone explains it and the history does not matter); or the fine-tuned confident style persists through months of weekly updates. 6 points for an observation that would not distinguish the explanations (for example "ratings go down").
feedback-instructions:: Name the strongest part of the answer, usually the clearest causal link in the learner's loop. Then give the single most valuable improvement: most often, showing how the style changes what the system later experiences (the step that makes it a loop), or making the disconfirming observation actually discriminate between explanations. Ask one follow-up question about a similar loop in a different kind of AI system. No generic praise.
