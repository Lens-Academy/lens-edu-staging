---
id: 'f8ac8b16-6b72-412e-9ceb-24c08a5eb6cf'
learning-outcome: "Given the reward statistics of the rollout groups in an RL run that fails to raise a model's performance on a task, explain why a group-relative method such as GRPO gets little or no learning signal: every rollout in a group whose rollouts all score the same has zero advantage, so only the groups with mixed rewards move the policy."
topic: "[[../Domains and Topics/1 Artificial Intelligence/How modern AI is trained]]"
stage: intermediate
authors:
  - Elias+Claude
---
## Test:
id:: 92df67a6-10c8-4522-ba8f-91c089b9ea3a

#### Question: Open
id:: a60bfb9d-9352-48be-b88a-3cf170cb2fc6
content::
As part of a dangerous-capability evaluation, a lab uses GRPO to elicit a general assistant model's skill at writing working exploits for security vulnerabilities that have already been patched. Each task is one vulnerability; the model samples 8 rollouts per task, and a rollout earns reward 1 if its exploit works when run in a sandbox and 0 otherwise.

The training logs show:

- At the start, all 8 rollouts succeed on about 9% of tasks, all 8 fail on about 88%, and the remaining 3% of tasks have a mix of successes and failures. Average success is about 10%.
- After 400 training steps, average success is about 11%, and the split between all-succeed, all-fail and mixed tasks is almost unchanged.

Using the logs, explain why 400 steps of training barely changed the model's performance.
placeholder:: About 80 to 200 words.
assessment-instructions:: Score out of 100. 65: GRPO's advantage compares each rollout's reward with the mean of its group (and scales by the group's spread), so in a group where all 8 rollouts score the same (all succeed or all fail) every advantage is zero and the group contributes no learning signal; that is about 97% of tasks here (9% plus 88%). Credit these 65 in full when the answer shows why a group with identical rewards gives nothing: each rollout is scored against its own group, so with no difference within the group every advantage is zero, for the all-succeed groups as well as the all-fail ones. An answer that says only that always-failing tasks have nothing to reinforce and always-succeeding tasks are already learned, without the comparison within the group, earns at most 25 of these 65. 35: what that leaves: only the roughly 3% of mixed groups carry signal, so progress is slow (10% to 11%) rather than exactly zero. An answer that says there is no signal at all, without noting the mixed groups, earns at most 10 of these 35. Give credit for each point whenever the answer shows the idea, in any wording; exact percentages are not needed. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "GRPO scores each rollout against the mean of its own group of 8. On the 88% of tasks where all 8 fail, and the 9% where all 8 succeed, every rollout has the same reward as its group's mean, so every advantage is zero and those tasks contribute nothing. Only the 3% of mixed groups move the policy, so 400 steps buy about one point: not nothing, but close."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. Ask at most one question, for the highest-value miss: if the learner said there is no signal at all, ask what the advantages are in a group with three successes and five failures; if they explained the all-fail tasks only by "nothing to reinforce", ask what the advantage of each rollout is when all 8 score the same. If the answer is complete, add that none of the signal comes from the 88% of tasks where the model always fails, which is where the capability would have to be drawn out. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - exploration-hacking-guided]]
notes:: Teaches the GRPO objective, with why groups of identical rewards give zero advantage. Practice with feedback: c4ec366a (deterministic policy, zero advantage).
## Lens:
source:: [[../Lenses/XLab Control - exploration-hacking-guided-3]]
notes:: Applies the group-statistics argument to a real run: which reward component carries the variance within a group of rollouts (198bd894 part 2). Note: its "Why does accuracy fall?" section first says the organism's malign trajectories vary in accuracy, then that malign accuracy has low variance across trajectories of the same prompt; the second is the paper's account and what 198bd894 grades.
