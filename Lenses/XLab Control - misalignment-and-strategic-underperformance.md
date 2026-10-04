---
id: 'cfd068cc-b2f9-41c1-b40d-6ce182824db9'
title: "Misalignment and strategic underperformance: an analysis of sandbagging and exploration hacking"
tldr: "Most misalignment worries picture a model trying too hard. This one pictures a model that could ace the task and quietly does not, like a chess engine playing to a draw so nobody finds out it can win. Redwood Research works through why training usually beats that strategy, and the one move that could let a model keep its best ideas to itself."
summary_for_tutor: "This page reproduces Julian Stastny and Buck Shlegeris's Redwood Research post in full, with permission, and adds no framing of its own; everything here except a short navigational lead-in and the marking briefs is theirs. This lens closes AI Control 2 and supplies the vocabulary that the first lessons of AI Control 3 test. Sandbagging is a misaligned model intentionally underperforming, and the post splits it in two: hiding latent capabilities, where the model has the capability and conceals it (the concern for dangerous capability evaluations and untrusted monitoring), and failing to live up to its potential, where the model deliberately fails to learn the capability at all, so it does not possess it (the concern for AI safety R&D and for generating training signals). Exploration hacking is the specific defence against reinforcement learning: the model intentionally refrains from taking the high-reward actions it already knows about, so on-policy RL never samples them, has nothing to reinforce, and cannot elicit the capability. Sequence: lead-in, then the first part of the post (why sandbagging is costly, the two types, on-policy versus off-policy data, training on high-quality data, exploration hacking, off-policy mitigation), then the three recall questions placed at that point, then the countermeasures and conclusion sections, then two more recall questions. If a learner conflates the two terms, note that sandbagging is the goal and exploration hacking is one method of achieving it under RL."
reading_minutes: 25
tutor_minutes: 27
tags: []
---
#### Text
content::
\#### Before you read

[[../Lenses/XLab Control - handling-non-concentrated-failures|Notes on handling non-concentrated failures with AI control]] set up the low-stakes setting, where no single action is a catastrophe and harm accumulates instead. This post asks what a misaligned model can do inside that setting by doing its job badly on purpose.

The authors call that sandbagging, and they open by separating it from the more familiar failure modes: overoptimizing a reward function means a model performs better on your metric than an aligned one would, and scheming usually means a model performs about as well as an aligned one while not being aligned. Sandbagging is the case where the model performs worse, so the usual argument that training makes models perform well according to your measurements has to be examined rather than assumed. The post covers why we want good performance in the first place, why training partly resolves sandbagging, a strategy called exploration hacking that could defeat training, and the countermeasures available. The authors say up front that they are highly uncertain how hard preventing sandbagging will be, and that the answer depends on the domain.

The opening lessons of AI Control 3 build on both terms: [[../Lenses/XLab Control - capability-elicitation-guided|Stress-Testing Capability Elicitation]], [[../Lenses/XLab Control - exploration-hacking-paper|Exploration Hacking: Can LLMs Learn to Resist RL Training?]], [[../Lenses/XLab Control - auditing-sabotage-bench-paper|Auditing Sabotage Bench]] and [[../Lenses/XLab Control - exploration-hacking-guided|Exploration Hacking (guided)]].

*By Julian Stastny and Buck Shlegeris (Redwood Research). Reproduced verbatim, with permission, from [the original post on the Redwood Research blog](https://blog.redwoodresearch.org/p/misalignment-and-strategic-underperformance) (May 8, 2025).*

*A new analysis of the risk of AIs intentionally performing poorly.*

#### Article
source:: [[../articles/stastny-misalignment-and-strategic-underperformance-an-analysis-of-sandbagging-and-exploration-hacking]]
to:: "we may completely lose the affordance of fine-tuning on off-policy data."

#### Question: Open
id:: a9025d96-e880-403f-9169-b4b05208e516
content::
\#### Quick recall

What are the two types of sandbagging, and where is each a concern?
assessment-instructions:: Score out of 100. 35: hiding latent capabilities: the model has the capability and deliberately conceals it, doing worse than it could. 15: where that is a concern: dangerous-capability evaluations and untrusted monitoring. 35: failing to live up to its potential: the model deliberately fails to learn a capability during training, so it does not have it. 15: where that is a concern: AI safety research and generating training signals. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Hiding latent capabilities: the model has a capability and deliberately conceals it (the concern for dangerous-capability evaluations and untrusted monitoring). Failing to live up to potential: the model deliberately fails to learn a capability, so it does not possess it to use against you (the concern for AI safety R&D and for generating training signals)."
feedback-instructions:: Reply in 40 to 100 words, short paragraphs, no lists. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the post, such as asking which of the two a dangerous capability evaluation is trying to measure, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms rather than offering a third foothold.

#### Question: Open
id:: d3d6d270-ed80-453d-bd35-4142dd95dfd0
content:: On which tasks is it especially costly for a model to sandbag, and why?
assessment-instructions:: Score out of 100. Any three of these contexts, each named with why sandbagging there is costly, earn full marks: 34 for each such context (15 for the context alone), capped at 100: dangerous capability evaluations, because the red team has to elicit the model's capabilities to know what it can do; AI safety research (including alignment research), because a misaligned model gains by underperforming there to keep its options open; untrusted monitoring, because a sandbagging monitor can let attacks through or raise false alarms (either is enough); generating training signals, because AI-generated rewards or demonstrations that are sandbagged make the training of other models fail. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Dangerous capability evaluations, where the red team must elicit a model's attacks to know what it can do; AI safety and alignment R&D, where a misaligned model is incentivized to underperform to preserve its options; Untrusted monitoring, where a monitor can falsely flag non-attacks or fail to flag attacks. Also generating training signals, where AIs produce the rewards or the demonstrations used to train other models, so sandbagging there can make those training methods fail."
feedback-instructions:: Reply in 40 to 130 words, short paragraphs, no lists. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, name one of the four contexts and ask what goes wrong there, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Question: Open
id:: 849417cb-4a4e-4d39-abb5-a8d3d09617c4
content:: In model training, what is the difference between on-policy and off-policy data?
assessment-instructions:: Score out of 100. 50: on-policy data is generated by the model that is currently being trained. 50: off-policy data comes from other sources, such as human experts or other AIs. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "On-policy data is sampled from the model currently being trained, while off-policy data comes from other sources, such as humans or other AIs."
feedback-instructions:: Reply in 40 to 100 words, short paragraphs, no lists. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, offer the chess fine-tuning example from the post as a foothold rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: "Quick takes on other countermeasures"

#### Question: Open
id:: 1ef4d8a1-066c-4528-90b0-be748d9dab03
content::
\#### Quick recall

How does ensembling counter exploration hacking?
assessment-instructions:: Score out of 100. 50: several untrusted models explore at the same time, so to sandbag successfully they must all coordinate on the same strategy. 50: if any one of them does the good (high-reward) action, the others can be trained on that action. Give the full points for each element whenever the answer shows the idea, in any wording, however briefly. Model answer, for the feedback, not a grading checklist: "Several untrusted models explore at once, so sandbagging successfully requires them to coordinate on a shared strategy. If any one explores a high-reward action, the others can be fine-tuned on it."
feedback-instructions:: Reply in 40 to 100 words, short paragraphs, no lists. Say what the learner got right and, if anything is missing or wrong, the most important thing. If the learner has both points, add as something worth knowing (not a lost point) that this fine-tuning gives a strong gradient against the other models' general sandbagging cognition, not just against underperforming on that one task. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, ask what happens to the other models when one of them slips, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Question: Open
id:: 36713e15-2916-4a21-9d4f-37730c1e768e
content:: Why is detecting sandbagging a weaker primary countermeasure than training it out? Give two reasons.
assessment-instructions:: Score out of 100. 50: it is hard to get conclusive evidence that a model is sandbagging. 50: even with such evidence, it is hard to do anything useful with it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Gaining conclusive evidence that a model is sandbagging is hard and doing something useful with that evidence once obtained is also hard. So training the behavior out, rather than detecting it, is a more reliable lever."
feedback-instructions:: Reply in 40 to 130 words, short paragraphs, no lists. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, ask what a lab could actually do with a suspicion it cannot prove, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Question: Open
id:: 59bc1c50-26ed-4429-8533-2707ab46e5ba
content::
\#### Would training work here?

A lab wants to train its model with reinforcement learning, rewarded automatically, on three tasks: (i) producing the short trigger phrase, if one exists, that makes a copy of itself acting as a monitor stay silent; (ii) playing a board game invented last month, where wins are checked automatically; (iii) the same board game, but scored only on the opening move, where the model already knows which of the three standard openings wins most often and RL samples its first move at high temperature.

For each, how easily could a model that wants to underperform stop reinforcement learning from eliciting its best performance, and why? What would you add to the training, and where would it fall short?
max-words:: 220
placeholder:: Your judgement and its reason for each task, then what you would add and its limit.
assessment-instructions:: Score out of 100. For each task, a correct judgement and one correct reason that settles it; any correct reason counts. 30: (i) easy for the model, 10 for the judgement and 20 for a reason, for example: it knows the phrase and can simply never say it, and nothing it would say by chance comes close, so RL never sees the phrase and has nothing to reinforce. 25: (ii) much harder for the model, 8 for the judgement and 17 for a reason, for example: the game is new, so the model does not know which moves are best and cannot reliably avoid them; good play it stumbles into gets reinforced (at most it can stick to one consistent style of play). 25: (iii) harder for the model than (i), or fairly hard, 8 for the judgement and 17 for a reason, for example: the best opening is one of only three, so high-temperature sampling will often pick it and those picks get reinforced; the model could resist only by making that opening almost impossible to sample. 20: a countermeasure that fits one of the cases, 12, with a limit it still has, 8, for example: ensembling several models, which helps against low-entropy strategies in (ii) but little in (i), where every copy knows what to avoid; adding off-policy examples, which needs a source of good examples (hard in (i), where nobody but the model knows the phrase) and which the model may recognise as not its own; fuzzing the weights or activations, cheap but with negative early results. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "(i) Easy to hack: the model knows the phrase and it is nothing like what it would say by accident, so it never says it and there is nothing to reinforce. This is the post's own example and why it is pessimistic about getting models to reveal collusion signals. (ii) Much harder: the game is new, so the model does not know the best moves; it can only commit to one style of play, and any good play it stumbles into gets reinforced. (iii) Harder than (i): the model knows the best opening, but it is one of three, so high-temperature sampling will often pick it and those picks get reinforced, unless the model makes it almost impossible to sample. For (ii) I would ensemble several models so a good line found by one trains the others; that works because they would have to coordinate on the same weak style, but it does little for (i), where every copy knows exactly what to avoid."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the post (for instance, ask whether the model knows which answer would be rewarded in each task) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Stastny, Julian, and Buck Shlegeris. "Misalignment and Strategic Underperformance: An Analysis of Sandbagging and Exploration Hacking." *Redwood Research blog*, 8 May 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/misalignment-and-strategic-underperformance)
*The post this lesson assigns in full: it defines sandbagging and exploration hacking, and surveys the countermeasures available against them.*

XLab. "Misalignment and strategic underperformance: an analysis of sandbagging and exploration hacking." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/misalignment-and-strategic-underperformance)
*The source lesson this page adapts.*
:::
