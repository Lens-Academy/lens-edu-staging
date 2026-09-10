---
id: '1a64e2da-b9a9-4d71-9e27-eaca38cbc280'
title: "Stress-Testing Capability Elicitation"
tldr: "A model that can write good code but plays dumb unless you say the magic word. The authors build exactly that, deliberately, and then try to pick their own lock by fine-tuning. It is a crash-test dummy for dangerous-capability evaluations: if your elicitation method cannot recover a capability you know is in there, you have little reason to trust it on the ones you cannot see."
summary_for_tutor: "Ported from XLab's AI Control curriculum, Module 5. XLab marks this lesson optional. It is a bare paper page: XLab renders Greenblatt, Roger, Krasheninnikov and Krueger's password-locked models paper in full and writes no framing of its own, and it carries no exercises. The lens is therefore three segments: a short navigational lead-in we wrote (it points to the sandbagging threat-model lesson, points to the guided version of this same paper for learners who want to be walked through it, and states the paper's own method in the paper's terms), then the whole paper as an Article segment, then Works cited. There are no questions, by design: the guided sibling lens carries the exercises for this paper. If a learner wants to discuss the paper, work from the article text; the strongest hooks are the sample-efficiency result in section 5, the RL-without-demonstrations result in section 6, and the three disanalogies the authors list in section 8."
reading_minutes: 60
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

This page is the paper itself, start to finish, with nothing added.

It connects backwards to [[../Lenses/XLab Control - misalignment-and-strategic-underperformance|Misalignment and strategic underperformance]], which sets out sandbagging as a threat model. This paper names that same failure as one of its motivations: a powerful, misaligned and situationally aware model that behaves safely during evaluations because it is sandbagging, rather than because it lacks the dangerous capability.

If you would rather be walked through it section by section, with questions along the way, take [[../Lenses/XLab Control - capability-elicitation-guided|Stress-Testing Capability Elicitation (guided)]] instead. Same paper, guided. This page exists for reading it straight.

\## The move the paper makes

Elicitation failures that occur naturally are hard to study, because only a few are known. So the authors manufacture one. They fine-tune a model to imitate a much weaker model on every prompt, except when a password is present, in which case it performs at full strength. The hidden capability is then hidden by construction, and its true level is known. They then try to recover it without the password, using supervised fine-tuning on demonstrations (section 5) and reinforcement learning where only a quality judgement is available (section 6). Section 8 is where they set out what this toy model does not capture.

#### Article
source:: [[../articles/greenblatt-stress-testing-capability-elicitation-with-password-locked-models]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Fabien Roger, Dmitrii Krasheninnikov, and David Krueger. "Stress-Testing Capability Elicitation With Password-Locked Models." *arXiv*, May 2024. [arxiv.org](https://arxiv.org/abs/2405.19550)
*The paper this lesson assigns: password-locked models as a way to test whether fine-tuning can pull a capability back out of a model that is hiding it.*

XLab. "Stress-Testing Capability Elicitation." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/capability-elicitation-paper)
*The source lesson this page adapts.*
:::
