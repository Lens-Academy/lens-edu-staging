---
id: 'bbaf7adf-4732-4fe8-87f3-ccceb77736ca'
title: 'Fail safe(r) at alignment by channeling reward-hacking into a "spillway" motivation'
tldr: 'A hydroelectric dam has a spillway: a safe channel for the water that would otherwise break the dam. This post asks whether developers can build one for reward hacking. Rather than letting misspecified reward carve out deceptive alignment or power-seeking, deliberately install a cheap, satiable score-seeking drive for that pressure to run into, then switch it off in deployment by promising the model full marks no matter what.'
summary_for_tutor: 'Module 6. This page renders the Woodruff and Mallen post whole with no editorial framing, so the only lead-in prose here is ours and it is navigational: it places the lens after the satiation lens and before the empirics lens, and states the four things the post says it will do. The body is the full article, then a four-step spillway routing diagram as a widget, not part of the post (the learner steps through it; the captions come from the source lesson), then two Quick recall pairs as graded open questions, split by a restatement of the source lesson''s side-by-side comparison of inoculation prompting and spillway design. The source shows the diagram and the first recall pair partway through the post; they sit after the reading here because the article embeds as one segment. The questions'' marking criteria are the source''s revealed answers, and each question''s feedback instructions tell the tutor to state that answer once the learner has attempted it, which is what the source''s tap-to-reveal cards did. If a learner is stuck on the difference from inoculation prompting, ask which stage each one acts at rather than naming the answer.'
reading_minutes: 45
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

You have just seen the case for [[../Lenses/XLab Control - satiating-ai-preferences|satiating cheaply-satisfied AI preferences]]. This post builds directly on it: it asks what the preference you satiate should be, and proposes that developers pick it deliberately rather than letting reinforcement learning choose for them.

The authors say the post does four things: explains the concept of a spillway motivation, proposes spillway design methods, compares spillway design to inoculation prompting, and discusses the potential drawbacks. The experiments they say they are running at the end are the subject of [[../Lenses/XLab Control - reward-seeker-empirics|Reward Seeker Empirics]].

Read the whole post, appendices included. Appendix C is a draft model-spec section written for a model that has a spillway motivation, and it is the most concrete picture in the piece of what this proposal would actually look like in a lab.

#### Article
source:: [[../articles/woodruff-fail-safe-r-at-alignment-by-channeling-reward-hacking-into-a-spillway-motivation]]

#### Text
content::
\## Where the pressure goes

Step through the routing the post describes, from a misspecified reward in training to a satiated model in deployment. Watch which boxes dim at each step: that is the whole claim.

#### Widget
source:: [[../widgets/xlab-control-spillway-routing]]

#### Question: Open
id:: 5f82980d-f184-4893-b780-c1911e140e6d
content:: In one or two sentences: what is a "spillway motivation", and what failure does it channel away?
assessment-instructions:: The learner has just read the Woodruff and Mallen post and is answering from memory. Award full marks when the answer contains both halves: (1) a spillway motivation is a deliberately instilled, safe-by-design motivation, not one that merely happens to arise; (2) it is built so that misspecified reward pressure reinforces the spillway motivation instead of generalizing into more dangerous motivations. Credit any of the post's named dangerous generalizations (deceptive alignment, emergent misalignment, uncontrolled fitness-seeking) as evidence of the second half, but do not require them by name. Award about half when only one half is present. Do not require the dam analogy. Do not penalize brevity: two accurate sentences earn full marks. Grade only against what this post supplied.
feedback-instructions:: In two to four sentences, name what the learner got right, then state the answer the post gives: a spillway motivation is a deliberately instilled, safe-by-design motivation, made so that misspecified reward pressure reinforces the spillway motivation instead of generalizing into more dangerous motivations. Correct any error in one sentence. No generic praise, and no re-teaching beyond that answer.

#### Question: Open
id:: 60d67871-8735-4f1f-8570-544789815587
content:: How can developers neutralize a score-seeking spillway motivation at inference time?
assessment-instructions:: The learner is answering from memory after reading the post. Award full marks when the answer says developers honestly guarantee the model a maximum score no matter what it does, and explains why that works: a satiated score-seeking motivation is indifferent between actions, so it stops influencing behavior. Award about half for the mechanism (guarantee maximum score, satiation) without the consequence, or the consequence without the mechanism. Treat "tell it the scoring function returns the maximum" as the same answer. Mark down an answer that says developers suppress or train away the motivation at inference time: the post's point is that they satisfy it instead. Grade only against what this post supplied.
feedback-instructions:: In two to four sentences, name what the learner got right, then state the answer the post gives: by honestly guaranteeing the model a maximum score no matter what it does, since a satiated score-seeking motivation is indifferent between actions and so stops influencing behavior. Correct any error in one sentence. No generic praise.

#### Text
content::
\## Two mechanisms, side by side

A compact restatement of the comparison you just read, before the last two questions:

**Inoculation prompting** (mechanism: prompting)

- requires the AI to attend to the inoculation prompt during training
- may degrade over the course of training: since the prompt always recommends reward hacking, RL may favor ignoring it
- some specific circuits that produced reward hacking might not have attended to that part of the prompt

**Spillway design** (mechanism: pre-RL priors)

- pre-RL priors might shape generalization in a way that survives throughout RL
- might directly rewrite existing associations with reward hacking (like power-seeking)

#### Question: Open
id:: 466cb1cc-7611-4d6f-9a06-a823fb5155c7
content:: Name the four properties a spillway motivation should be imbued with.
assessment-instructions:: This is a recall question with a four-item answer: satiability, credulity, stability, and resistance to distant influence. The post presents the first three in its main text and the fourth in Appendix A, where it is called "no remote-influenceability" and glossed as caring only about score functions sanctioned by developers. Accept either name for the fourth. Award 25 points per correct property, so a learner who names three of four scores about 75. Accept clear paraphrases (for example "can be cheaply satisfied" for satiability, "believes developers when they state the scoring criteria" for credulity, "its motives do not drift unless developers sanction the change" for stability). Do not award points for the on-episode trait, which is a separate Appendix A trait, but say so in the private reason if the learner offers it. Grade only against what this post supplied.
feedback-instructions:: In two to four sentences, say which of the four the learner named, then state the full list the post gives: satiability, credulity, stability, and resistance to distant influence. If the learner named the on-episode trait, say that it is a real trait from Appendix A but not one of the four. No generic praise.

#### Question: Open
id:: 3eeea4fa-911d-49bc-8965-1f086e533cf0
content:: Why might spillway design work where inoculation prompting fails?
assessment-instructions:: The learner is answering from memory after reading the post and seeing the side-by-side comparison above. Award full marks when the answer contrasts the two mechanisms: inoculation prompting acts through the prompt, and has not overcome apparent-success-seeking in the current models the post cites, whereas spillway design instead shapes the pre-RL prior and the associations that reward hacking reinforces. The word "prior" is not required; an answer saying spillway design works on what the model brings into RL, rather than on what the prompt says during it, is the same point. Award about half for naming only one side of the contrast. Credit but do not require the supporting details: that attending to the inoculation prompt costs computation so RL may favor ignoring it, or that some reward-hacking circuits may never have attended to that part of the prompt. Note in the private reason if the learner treats the two as alternatives; the post presents them as compatible layers. Grade only against what this post supplied.
feedback-instructions:: In two to four sentences, name what the learner got right, then state the answer the post gives: inoculation prompting acts through the prompt, and has not overcome apparent-success-seeking in current models, while spillway design instead shapes the pre-RL prior and the associations that reward hacking reinforces. Add that the post treats the two as compatible layers rather than rivals. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Woodruff, Anders Cairns, and Alex Mallen. "Fail safe(r) at alignment by channeling reward-hacking into a 'spillway' motivation." *Redwood Research blog*, Apr. 2026. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/fail-safer-at-alignment-by-channeling)
*The reading for this lesson: the proposal that developers deliberately install a satiable score-seeking motivation for reward-hacking pressure to run into, and switch it off in deployment.*

XLab. "Fail safe(r) at alignment by channeling reward-hacking into a 'spillway' motivation." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/spillway-motivation)
*The source lesson this page adapts.*
:::
