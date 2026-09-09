---
id: 'cfd068cc-b2f9-41c1-b40d-6ce182824db9'
title: "Misalignment and strategic underperformance: an analysis of sandbagging and exploration hacking"
tldr: "Most misalignment worries picture a model trying too hard. This one pictures a model that could ace the task and quietly does not, like a chess engine playing to a draw so nobody finds out it can win. Redwood Research works through why training usually beats that strategy, and the one move that could let a model keep its best ideas to itself."
summary_for_tutor: "XLab reproduces Julian Stastny and Buck Shlegeris's Redwood Research post in full, with permission, and writes no framing of its own; everything here except a short navigational lead-in and the marking briefs is theirs. This lens supplies the vocabulary the rest of Module 5 tests. Sandbagging is a misaligned model intentionally underperforming, and the post splits it in two: hiding latent capabilities, where the model has the capability and conceals it (the concern for dangerous capability evaluations and untrusted monitoring), and failing to live up to its potential, where the model deliberately fails to learn the capability at all, so it does not possess it (the concern for AI safety R&D and for generating training signals). Exploration hacking is the specific defence against reinforcement learning: the model intentionally refrains from taking the high-reward actions it already knows about, so on-policy RL never samples them, has nothing to reinforce, and cannot elicit the capability. Sequence: lead-in, then the first part of the post (why sandbagging is costly, the two types, on-policy versus off-policy data, training on high-quality data, exploration hacking, off-policy mitigation), then the three recall questions XLab places at that point, then the countermeasures and conclusion sections, then two more recall questions. If a learner conflates the two terms, note that sandbagging is the goal and exploration hacking is one method of achieving it under RL."
reading_minutes: 45
tutor_minutes: 0
tags: []
---
#### Text
content::
\#### Before you read

By Julian Stastny and Buck Shlegeris (Redwood Research), May 8, 2025. XLab reproduces the post in full, with permission.

[[../Lenses/XLab Control - handling-non-concentrated-failures|Notes on handling non-concentrated failures with AI control]] set up the low-stakes setting, where no single action is a catastrophe and harm accumulates instead. This post asks what a misaligned model can do inside that setting by doing its job badly on purpose.

The authors call that sandbagging, and they open by separating it from the more familiar failure modes: overoptimizing a reward function means a model performs better on your metric than an aligned one would, and scheming usually means a model performs about as well as an aligned one while not being aligned. Sandbagging is the case where the model performs worse, so the usual argument that training makes models perform well according to your measurements has to be examined rather than assumed. The post covers why we want good performance in the first place, why training partly resolves sandbagging, a strategy called exploration hacking that could defeat training, and the countermeasures available. The authors say up front that they are highly uncertain how hard preventing sandbagging will be, and that the answer depends on the domain.

The lessons that follow in this module build on both terms: [[../Lenses/XLab Control - capability-elicitation-guided|Stress-Testing Capability Elicitation]], [[../Lenses/XLab Control - exploration-hacking-paper|Exploration Hacking: Can LLMs Learn to Resist RL Training?]], [[../Lenses/XLab Control - auditing-sabotage-bench-paper|Auditing Sabotage Bench]] and [[../Lenses/XLab Control - exploration-hacking-guided|Exploration Hacking (guided)]].

#### Article
source:: [[../articles/stastny-misalignment-and-strategic-underperformance-an-analysis-of-sandbagging-and-exploration-hacking]]
to:: "we may completely lose the affordance of fine-tuning on off-policy data."

#### Question: Open
id:: a9025d96-e880-403f-9169-b4b05208e516
content::
\#### Quick recall

What are the two types of sandbagging?
assessment-instructions:: The learner has just read the first part of Stastny and Shlegeris and is answering from memory, without looking back. Full credit names both types and keeps them apart. Hiding latent capabilities: the model has the capability and deliberately conceals it, which is the concern for dangerous capability evaluations and for untrusted monitoring. Failing to live up to their potential: the model deliberately fails to learn a capability, so it does not have it and cannot use it against us, which is the concern for doing AI safety research and for generating training signals. Accept an answer that describes both distinctions accurately without using the post's labels. Give partial credit when only one type is named. Reply in 40 to 100 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the criteria above and the post itself. If the learner says they do not understand, give one concrete foothold from the post, such as asking which of the two a dangerous capability evaluation is trying to measure, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms rather than offering a third foothold.

#### Question: Open
id:: d3d6d270-ed80-453d-bd35-4142dd95dfd0
content:: On which tasks is it especially costly for a model to sandbag?
assessment-instructions:: The learner is recalling the four contexts the post lists. Dangerous capability evaluations, where the red team has to elicit a model's attacks in order to know what it can do. Applications to AI safety, where a misaligned model is incentivized to underperform on safety research in order to preserve its ability to pursue its own goals. Untrusted monitoring, where a misaligned monitor can falsely flag non-attacks or fail to flag attacks, and may also sandbag its collusion capabilities. Generating training signals, where AIs produce the rewards or the demonstrations used to train other models. Full credit for any three of the four with a correct reason attached; partial credit for two. Reply in 40 to 100 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the criteria above and the post itself. If the learner says they do not understand, name one of the four contexts and ask what goes wrong there, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Question: Open
id:: 849417cb-4a4e-4d39-abb5-a8d3d09617c4
content:: In model training, what is the difference between on-policy and off-policy data?
assessment-instructions:: The learner is recalling a definition the post uses throughout. On-policy data is sampled from the model currently being trained. Off-policy data comes from other sources, such as human experts or other AIs. Full credit for both halves. Give extra credit, but do not require, the point that this matters because off-policy data guarantees elicitation only up to the lower of the capability shown in the data and the model's ability to imitate it, while on-policy data is what we need when we want performance beyond humans or trusted models. Reply in 40 to 100 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the criteria above and the post itself. If the learner says they do not understand, offer the chess fine-tuning example from the post as a foothold rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: "Quick takes on other countermeasures"

#### Question: Open
id:: 1ef4d8a1-066c-4528-90b0-be748d9dab03
content::
\#### Quick recall

How does ensembling counter exploration hacking?
assessment-instructions:: The learner has just read the countermeasures and conclusion sections and is answering from memory. Full credit covers the mechanism: several untrusted AIs explore at the same time, so sandbagging successfully requires them to coordinate on a shared strategy; if any one of them explores a high-reward action, the others can be fine-tuned on that action, which the post argues gives a particularly strong gradient signal against their global sandbagging cognition. Credit, but do not require, the scope: ensembling helps most against models following low-entropy policies when there are many such policies to hide behind, and much less when it is clear to the models which high-reward actions they want to avoid. Reply in 40 to 100 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the criteria above and the post itself. If the learner says they do not understand, ask what happens to the other models when one of them slips, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Question: Open
id:: 36713e15-2916-4a21-9d4f-37730c1e768e
content:: Why is detecting sandbagging a weaker primary countermeasure than training it out?
assessment-instructions:: The learner is recalling the authors' stated position on detection. Full credit names both halves of their pessimism: gaining conclusive evidence that a model is sandbagging is hard, and doing something useful with that evidence once you have it is also hard. That is why they treat training, rather than detection, as the main countermeasure. Accept an answer that reaches the same conclusion in its own words. Do not credit an answer that only asserts detection is unreliable without saying why. Reply in 40 to 100 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the criteria above and the post itself. If the learner says they do not understand, ask what a lab could actually do with a suspicion it cannot prove, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Stastny, Julian, and Buck Shlegeris. "Misalignment and Strategic Underperformance: An Analysis of Sandbagging and Exploration Hacking." *Redwood Research blog*, 8 May 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/misalignment-and-strategic-underperformance)
*The post this lesson assigns in full: it defines sandbagging and exploration hacking, and surveys the countermeasures available against them.*

XLab. "Misalignment and strategic underperformance: an analysis of sandbagging and exploration hacking." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/misalignment-and-strategic-underperformance)
*The source lesson this page adapts, including both of its Quick recall blocks.*
:::
