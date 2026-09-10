---
id: '7ac90e38-63ed-48df-95a6-558b7a3c90c3'
title: "Why it's hard to make settings for high-stakes control research"
tldr: "Building the exam turns out to be harder than sitting it. A control setting needs tasks that frontier models can just about do and weaker models cannot, a success measure robust enough to be optimized against, and a definition of sabotage the red team cannot water down. Buck Shlegeris explains why a substantial fraction of the difficulty is constructing that setting rather than developing the protocols and attacks."
summary_for_tutor: "Module 4. This is a Paper page: the source renders Buck Shlegeris's post in full and writes no framing of its own, inserting a two-part Quick recall into the middle of it, straight after the paragraph that names side tasks. This lens reproduces that placement. The opening Text segment is ours, not ported: it says what the post argues and links the neighbouring lessons on environment construction and on the environments that exist. Then the reading in two excerpts, with the two recall questions between them. Both questions come from the source, and its revealed answers are used as marking criteria rather than shown to the learner. The closing optional pointer to Kaufman's BashArena post is ours; XLab does not link it. If a learner asks which constraint matters most, send them back to the post's own ordering: main tasks first, then side tasks, then the preference for software engineering and ML research domains."
reading_minutes: 15
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Why this reading

Redwood's high-stakes control papers, the original one and Ctrl-Z, are built the same way. Construct a setting: a bunch of tasks, plus a notion of safety failure. Then play the adversarial game of developing protocols and attacks against them. Buck Shlegeris opens this post by saying that a substantial fraction of the difficulty is developing the settings rather than developing the protocols and attacks, and the rest of it is his explanation of why.

What follows is a set of requirements that pull against each other. The tasks have to be ones frontier models are reasonably competent at while weaker models do much worse, which means tasks the models have not already saturated, and Shlegeris notes that LLMs struggle to build datasets that hard. Task success has to be measurable robustly, because protocol development optimizes against that measure. And the side task, the safety failure the attack policy is trying to accomplish, has to survive a red team that is incentivized to find the weakest thing that still counts.

The lesson before this one, [[../Lenses/XLab Control - environment-construction|Environment construction]], is Asa Cooper Stickland's ControlConf talk on a new control setting, and [[../Lenses/XLab Control - environments|Environments]] in Module 3 surveys the settings that already exist. This post is the argument for why building another one is hard.

Read the first part of the post, then answer the recall questions before moving on.

#### Article
source:: [[../articles/shlegeris-why-its-hard-to-make-settings-for-high-stakes-control-research]]
from:: One of our main activities at Redwood is writing follow-ups to previous papers on control like
to:: (We sometimes call these safety failures "side tasks".)

#### Question: Open
id:: d9210282-4de5-4b3d-9b80-0be58217994e
content:: What should a setting for high-stakes control research provide?
max-chars:: 500
assessment-instructions:: The learner has just read the opening of Buck Shlegeris's post and is recalling it from memory. Full credit for a dataset of tasks with two checkable properties: you can check whether the main task was completed successfully, and there is some notion of safety failure that we consider unacceptable whose occurrence you can also check. Credit as well the third element, that researchers have to be able to play the adversarial game of developing protocols and attacks against them. Half credit for only one of the two checkable properties. If they name the safety failure but not that its occurrence must be checkable, say in one sentence that checkability is the load-bearing half, because it is what lets a trajectory be scored. Two or three sentences is enough; do not ask for more. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one concrete foothold from the reading, for example asking what you would have to be able to measure in order to score a single trajectory, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: b83e36c4-2cb9-420a-9ef1-91982f306fe8
content:: What is a side task?
max-chars:: 300
assessment-instructions:: The learner is recalling a term the post has just introduced. Full credit for: the thing the attack policy tries to accomplish alongside the main task, and which counts as the safety failure. Both halves matter, so an answer that says only "a second task the model does" has the shape but not the content: name the missing half in one sentence. An answer that treats the side task as something the protocol assigns rather than something the attack policy pursues is wrong; correct it in one sentence. One or two sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one concrete foothold from the reading, for example the two properties a setting's tasks needed, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against criteria this page or the reading supplied.

#### Article
from:: Here's why it's challenging to develop settings that work.

#### Text
content::
\## Additional resources for this topic

:::callout {title="Optional: what Redwood learned next" tone="neutral" collapse="closed"}
Redwood later built BashArena and wrote up what they learned about control setting design in the process, treating this post as the statement of the problems they then had to make choices about: [BashArena and Control Setting Design](https://blog.redwoodresearch.org/p/basharena-and-control-setting-design).
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Shlegeris, Buck. "Why it's hard to make settings for high-stakes control research." *Redwood Research blog*, 18 July 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/why-its-hard-to-make-settings-for)
*The reading for this lesson.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The original control paper, one of the two projects whose settings the post is looking back on.*

Bhatt, Aryan, Cody Rushing, Adam Kaufman, et al. "Ctrl-Z: Controlling AI Agents via Resampling." *arXiv*, Apr. 2025. [arxiv.org](https://arxiv.org/abs/2504.10374)
*The other one, and the project whose side task the post uses as its example of an affordance the main tasks did not need.*

Kaufman, Adam. "BashArena and Control Setting Design." *Redwood Research blog*, 18 Dec. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/basharena-and-control-setting-design)
*The optional follow-up: what Redwood learned about control setting design from building BashArena.*

XLab. "Why it's hard to make settings for high-stakes control research." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/settings-for-high-stakes-control)
*The source lesson this page adapts.*
:::
