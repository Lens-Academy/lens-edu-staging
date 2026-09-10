---
id: '9a082b6c-85fd-47df-b44d-5e9bc6b311f5'
title: "Efficient tradeoffs and the safety-usefulness tradeoff model"
tldr: "Safety gets bought with usefulness, and the developer's willingness to pay runs out. That picture tells you what to build and what to ask for. Buck Shlegeris argues it holds when the developer is a rushed version of you, and breaks when the pressure comes from regulators, governments or the public, because then what the developer is buying is their approval rather than safety."
summary_for_tutor: "Ported from XLab's AI Control curriculum, Module 2 (How useful is AI control?). XLab renders Buck Shlegeris's post whole with no framing of its own, so everything here except the opening Text segment is the post plus the one exercise XLab inserts into it. The opening Text segment is our lead-in: it says what the post argues, flags Shlegeris's convention that 'you' means the person who wants safety, and links forward to the two lessons that build on this one. Sequence: lead-in, then the post from its opening through 'Rushed reasonable developers', then XLab's free response (propose an intervention, name its usefulness cost, justify the trade), then the rest of the post (limited political will, why the model fails when developers do not trade efficiently, overall thoughts, and the appendix of definitions). The exercise sits mid-post on purpose, so a learner answering it has not yet read the sections on political feasibility; do not grade against them. The lesson's contribution to the module is the vocabulary the next lessons run on: safety budget, political will, and the two levers (push out the Pareto frontier, increase the safety budget)."
reading_minutes: 30
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

Module 2 asks whether AI control is worth what it costs. This lesson supplies the price tag the rest of the module reasons with.

The reading is Buck Shlegeris's post on what he calls the safety-usefulness tradeoff model: developers face a tradeoff between the safety and the usefulness of an AI deployment, and have only limited willingness or ability to sacrifice usefulness for safety. Two levers follow. Safety tech improvements push out the Pareto frontier, so a given usefulness cost buys more safety than it used to. Safety budget increases raise how much usefulness the developer will give up at all, from implementing cheap measures at one end to refraining from training or deploying a model at the other. One convention to carry in: throughout the post, "you" is the person who wants safety and is using the model to decide what to do.

Most of the post is about when the model applies. Shlegeris separates two ways of motivating it, a rushed reasonable developer who shares your beliefs but is forced to move fast, and limited political will, where the developer does not share your priorities but you have some influence, and argues the model is the right analysis for the first and for the versions of the second where the developer will concede to safety-motivated stakeholders up to some cost threshold, and a poor one where the developer is instead acting under pressure from third parties whose beliefs or priorities differ from yours.

Two later lessons run on this vocabulary. [[../Lenses/XLab Control - determining-the-usefulness|Determining the usefulness]] takes the safety budget and political will from here and builds the module's regime model around them, and the module's closing exercise, [[../Lenses/XLab Control - running-the-model|Running the model]], has you spend a research team's effort using these two levers. Partway through the reading, you will be stopped for a short written exercise.

#### Article
source:: [[../articles/buck-efficient-tradeoffs-and-the-safety-usefulness-tradeoff-model]]
to:: rather than about how to cause major changes in how AI developers will handle catastrophically dangerous AI.

#### Question: Open
id:: 5c3d29f1-79da-42ec-9c8a-602ecbb42174
content::
\## Free response

Propose a safety intervention you believe would be worth implementing, name the usefulness cost, and answer why the increase in safety justifies the usefulness cost.

Write between 30 and 200 words.
assessment-instructions:: The learner has read the post's opening and its "Rushed reasonable developers" section and nothing after it. XLab supplies no rubric and no model answer for this exercise, so grade it against what the prompt itself asks for, and never against the post's later sections on political feasibility, which the learner has not reached.

Criteria, roughly equal weight:
1. **A specific intervention.** Something a developer could decide to do, named concretely enough that you could picture it being implemented: a monitoring or auditing protocol, a restriction on what a model may touch, a deployment held back, a model not trained. "More safety research" or "take alignment seriously" does not meet this.
2. **A usefulness cost, named.** They say what the developer gives up, in a currency the reading supplies: a slowdown in the developer's rate of progress, compute spent on safety instead of capabilities, delay, or a deployment forgone. A learner who claims the intervention is free should say what it still costs the developer to adopt. Vagueness here ("it would cost a bit of performance") is the criterion's failure mode, not a wrong answer.
3. **A trade actually argued.** They compare the two: why this much safety is worth that much usefulness. Credit reasoning that turns on the margin, meaning that this intervention buys more safety per unit of cost than the alternatives, since that is the standard the reading says a reasonable developer applies. Do not require it.

Deduct for a response under 30 words, and for one that argues that safety matters in general without pricing the intervention it proposed. Never mark the learner's choice of intervention wrong; the prompt asks what they believe is worth implementing, and there is no house answer.

Reply in at most four sentences: name the intervention and cost they gave, say which of the three criteria the response leaves thinnest, and ask one causal follow-up about it. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the material rather than repeating the question, for example the reading's own range of what a safety budget buys, from implementing a cheap measure at one end to refraining from deploying a model whose risks cannot be mitigated at the other, and ask them to pick a point on it. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria above.

#### Article
from:: ## Limited political will

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Shlegeris, Buck. "Efficient tradeoffs and the safety-usefulness tradeoff model." *Redwood Research blog*, 8 June 2026. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/efficient-tradeoffs-and-the-safety)
*The whole of this lesson's reading: the safety-usefulness tradeoff model, the two levers it implies, and the argument about the conditions under which it stops applying.*

XLab. "Efficient tradeoffs and the safety-usefulness tradeoff model." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/how-useful-is-ai-control/safety-usefulness-tradeoff-model)
*The source lesson this page adapts.*
:::
