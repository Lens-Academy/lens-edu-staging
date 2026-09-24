---
id: '4669e8a2-e7eb-432b-809b-2c5c3611d77f'
title: "How might we safely pass the buck to AI?"
tldr: "Josh Clymer's goal as a safety researcher is to put himself out of a job: not to align superintelligence himself, but to hand the remaining safety work to AI agents who are better at it than he is. The hard part is knowing when that handoff is safer than keeping humans in the loop. His answer is two conditions and four arguments, and you can check each one."
summary_for_tutor: "Module 1, where the page is a bare paper: there is no framing prose, only Josh Clymer's post rendered inline and one practice question added by Lens. Everything before the Article segment is our own navigational lead-in, drawn from the post's own introduction and section headings, and none of it is ported editorial voice. The lens is lead-in, the whole post, one practice question, works cited. The practice question (added September 2026) is a new case, agents taking over red-teaming of a lab's monitors: the learner says which of the two conditions the evidence speaks to and which kind of trust argument could settle the other; its model answer is in the assessment-instructions. If a learner wants to discuss it, the spine is the two sufficient conditions (capability and trust) and the four arguments for trust, of which argument #2, that agents cannot subvert autonomous control measures, is the one that connects back to the rest of this course."
reading_minutes: 65
tutor_minutes: 5
tags: []
---
#### Text
content::
\## Before you read

The previous four lenses, [[../Lenses/XLab Control - ai-control-paper|AI Control: Improving Safety Despite Intentional Subversion]], measured control protocols against a red team inside one concrete setting. This post steps back and asks what all of that is finally for.

Josh Clymer states his goal as putting himself out of a job. Rather than aiming at the loftier ambition of aligning superintelligence, he wants developers to be able to safely replace human safety researchers with AI agents, at which point, he argues, the bulk of the risks a human technical researcher can address have been addressed. He calls that "passing the buck."

The post is one long argument with a clear spine. It first says what passing the buck means and why he thinks it, not aligning superintelligence, should be the field's primary end goal. It then lays out three strategies for doing it: a one-time hand off to a system he calls M_1, an iterated hand off where M_1 passes the buck to a more capable M_2, and deference to an AI advisor whose deferred task is to say whether M_1 should be trusted at all. Clymer then argues that cutting humans out is responsible under two sufficient conditions, that M_1 is more capable than the human-oversight-preserving alternative and that it is more trustworthy than that alternative, and spends the second half of the post on four arguments a developer might use to establish trust.

Control is argument #2: that M_1 agents cannot subvert autonomous control measures while they complete the deferred task. Read that section with the protocols from the previous four lenses in mind, because it is control applied to a setting where no human is watching. The safety-versus-oversight tradeoff the post argues about qualitatively is the one [[../Lenses/XLab Control - how-useful-is-ai-control|How useful is AI control?]] later makes quantitative, and the incentives Clymer sketches in argument #4 are picked up again in [[../Lenses/XLab Control - making-deals-with-early-schemers|Making deals with early schemers]].

The whole post is assigned. It runs to roughly 9,000 words and leans on close to twenty diagrams, so give it an hour and read it start to finish: the four arguments only make sense against the two conditions set up before them.

#### Article
source:: [[../articles/clymer-how-might-we-safely-pass-the-buck-to-ai]]

#### Callout: Practice: which condition does the evidence speak to?
tone:: amber

#### Question: Open
id:: 746ca427-8a8e-4b0d-9709-b53ab0e1bff4
content:: A new case. A lab proposes that for the next year its AI agents take over red-teaming the lab's own monitoring system, with humans reading only a monthly summary. The evidence offered: in a two-month trial, the agents found more real ways past the monitors than the human red team did.

(a) What would have to be true for this handoff to be safer than the current arrangement? Which of that does the evidence speak to, and what does it leave open? Say concretely what could go wrong.
(b) Pick one of the four kinds of argument for the open condition and say what the lab would need to show to make it for this task.
placeholder:: Answer (a) and (b)
assessment-instructions:: This is practice on a new case, applying the post just read. Model answer. (a) The handoff is clearly safer than keeping the human red team if the agents are at least as capable and at least as trustworthy as the humans they replace at this task, and better on at least one, for the whole year. The trial speaks to the capability condition: the agents are better than the humans they would replace at finding ways past the monitors. It leaves the trust condition open: whether the agents are at least as trustworthy as the human red team for the whole year. What could go wrong: agents that are misaligned could find a bypass and not report it, or report only the ones they do not plan to use, and a monthly summary would not reveal this. (b) Any one of the four, with what it needs: that the agents are not hiding misalignment and will stay that way through the year (for example evidence that rules out alignment faking, plus ways they keep checking each other); that they could not subvert control measures around them (for example the lab plants known bypasses and checks that the agents report them, or cross-checks between agents that would raise an alarm, tested by a strong red team); that earlier AI-assisted work under control measures shows more human-supervised checking would add little; or that the agents have incentives to behave as safely as the humans would. Full credit for (a) with both conditions, framed as a comparison with the human red team, and a concrete failure, and (b) with one argument and a specific thing to show. Half credit if the trust condition is named but with no concrete way it could fail. Grade only against what this lens has supplied.
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed, in one or two sentences. If they treated better performance as settling the question, say plainly that it speaks to capability, not trust. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Clymer, Josh. "How might we safely pass the buck to AI?" *Redwood Research blog*, 19 Feb. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/how-might-we-safely-pass-the-buck)
*The reading for this lesson: the case that safely handing AI development to AI agents, rather than aligning superintelligence directly, should be the end goal of technical safety work, and the capability and trust conditions under which that handoff improves safety.*

XLab. "How might we safely pass the buck to AI?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/how-might-we-safely-pass-the-buck-to-ai)
*The source lesson this page adapts.*
:::
