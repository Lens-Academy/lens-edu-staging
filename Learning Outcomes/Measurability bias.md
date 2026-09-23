---
id: 'bbb81b7e-0d27-4c55-b72a-3e9814c02e11'
learning-outcome: "Diagnose how optimising for clearly measurable indicators erodes the hard-to-measure parts of a value, distinguishing neglect (unmeasured components lose effort and resources) and value capture (the agent's value itself is redefined as the measurable version) from ordinary gaming of a metric, and propose remedies matched to each mechanism."
topic: "[[../Domains and Topics/3 Alignment/Inner and outer alignment]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Measurability bias. AFFINE prerequisites: Goodhart. Not yet copied into requires:. %%
## Test:
id:: 8cdf6424-6721-4e41-ab64-350637d67aab

#### Question: Open
id:: d1558b8a-013a-46c1-8b49-9824cabca55f
content:: An AI lab states that its mission is "AI systems that are genuinely trustworthy". To track progress, leadership introduces a dashboard with three numbers: refusal rate on a benchmark of harmful requests, score on an honesty evaluation, and success rate of a fixed set of jailbreak attacks. Team bonuses depend on the dashboard. Three years later, an internal review finds:

- **(a)** A team studying whether models have hidden motives, which produces no dashboard number, has shrunk from six people to one.
- **(b)** New hires, asked what "trustworthy" means at the lab, answer by listing the three dashboard numbers. Senior staff who once described it differently now also describe it in these terms.
- **(c)** Jailbreak success fell sharply, largely because models were trained on examples of the fixed set of attacks; new attack styles work about as well as before.

1. For each finding, explain the mechanism that produced it. Say whether any two findings share a mechanism.
2. Which finding do you think would be hardest to reverse, and why?
3. Propose one change for each distinct mechanism you identified, and explain why it addresses that mechanism rather than another.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner may rank the findings differently from the guide below, or classify a finding differently, and earn full credit if the argument is sound and grounded in the case.

**(1) Mechanisms, 45 points (15 each).** (a) Neglect: effort and resources flow to what the dashboard measures, so valuable work that produces no number shrinks, even though nobody decided it was unimportant. (b) Value capture: people's understanding of the goal itself has been replaced by the simplified, measurable version, so they no longer see what is missing; this differs from (a) because the value, not only the effort, has changed. (c) Gaming the metric (Goodhart): the measured number improved in a way that no longer tracks the underlying property, because optimisation targeted the specific test rather than robustness to attacks in general. Full credit for (1) also requires the learner to show that (a), (b) and (c) are not the same mechanism, whatever names they use. 7 points per finding for a label with no mechanism. Accept an argument that (a) and (b) are stages of one process, if the learner still explains how they differ.

**(2) Hardest to reverse, 20 points.** Full credit for any choice with a reason tied to its mechanism. For example: (b) is hardest because the people who would notice what is missing have themselves lost the richer concept, so internal review no longer detects the loss; or (a) is hardest because rebuilding lost expertise and team knowledge takes years. 8 points for a choice without a mechanism-based reason.

**(3) Remedies, 35 points.** Full credit: one change per distinct mechanism, each explained by that mechanism. Examples, not required: for (a), protect budget for work that cannot be measured, or judge it by expert review rather than numbers; for (b), keep the full, unsimplified statement of the goal central in decisions and hiring, and regularly ask what the dashboard misses; for (c), rotate and refresh the attack set, hold some attacks back from training, or measure against new attack styles. 12 points total if the learner proposes a single remedy for all three, such as "use better metrics", without explaining why a better metric would not simply repeat (a) and (b).

A fluent essay about "metrics being bad" that does not separate the three findings cannot score above 35.
feedback-instructions:: Name the strongest part, quoting a phrase. Then name the single most valuable improvement: usually either separating value capture (b) from neglect (a), or matching each remedy to its mechanism. If the answer is strong, ask how the same three mechanisms could show up inside an AI system trained with these three numbers as its reward. No generic praise.
