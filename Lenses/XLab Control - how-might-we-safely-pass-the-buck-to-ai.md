---
id: '4669e8a2-e7eb-432b-809b-2c5c3611d77f'
title: "How might we safely pass the buck to AI?"
tldr: "Josh Clymer's goal as a safety researcher is to put himself out of a job: not to align superintelligence himself, but to hand the remaining safety work to AI agents who are better at it than he is. The hard part is knowing when that handoff is safer than keeping humans in the loop. His answer is two conditions and four arguments, and you can check each one."
summary_for_tutor: "Imported from XLab's AI Control curriculum, Module 1, where the page is a bare paper: XLab supplies no framing prose and no exercises, only Josh Clymer's post rendered inline. Everything before the Article segment is our own navigational lead-in, drawn from the post's own introduction and section headings, and none of it is XLab's editorial voice. The lens is a pure read: lead-in, the whole post, works cited. There is no question segment and no tutor time. If a learner wants to discuss it, the spine is the two sufficient conditions (capability and trust) and the four arguments for trust, of which argument #2, that agents cannot subvert autonomous control measures, is the one that connects back to the rest of this course."
reading_minutes: 60
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

The previous lens, [[../Lenses/XLab Control - ai-control-paper|AI Control: Improving Safety Despite Intentional Subversion]], measured control protocols against a red team inside one concrete setting. This post steps back and asks what all of that is finally for.

Josh Clymer states his goal as putting himself out of a job. Rather than aiming at the loftier ambition of aligning superintelligence, he wants developers to be able to safely replace human safety researchers with AI agents, at which point, he argues, the bulk of the risks a human technical researcher can address have been addressed. He calls that "passing the buck."

The post is one long argument with a clear spine. It first says what passing the buck means and why he thinks it, not aligning superintelligence, should be the field's primary end goal. It then lays out three strategies for doing it: a one-time hand off to a system he calls M_1, an iterated hand off where M_1 passes the buck to a more capable M_2, and deference to an AI advisor whose deferred task is to say whether M_1 should be trusted at all. Clymer then argues that cutting humans out is responsible under two sufficient conditions, that M_1 is more capable than the human-oversight-preserving alternative and that it is more trustworthy than that alternative, and spends the second half of the post on four arguments a developer might use to establish trust.

Control is argument #2: that M_1 agents cannot subvert autonomous control measures while they complete the deferred task. Read that section with the protocols from the previous lens in mind, because it is control applied to a setting where no human is watching. The safety-versus-oversight tradeoff the post argues about qualitatively is the one [[../Lenses/XLab Control - how-useful-is-ai-control|How useful is AI control?]] later makes quantitative, and the incentives Clymer sketches in argument #4 are picked up again in [[../Lenses/XLab Control - making-deals-with-early-schemers|Making deals with early schemers]].

The whole post is assigned. It runs to roughly 9,000 words and leans on close to twenty diagrams, so give it an hour and read it start to finish: the four arguments only make sense against the two conditions set up before them.

#### Article
source:: [[../articles/clymer-how-might-we-safely-pass-the-buck-to-ai]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Clymer, Josh. "How might we safely pass the buck to AI?" *Redwood Research blog*, 19 Feb. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/how-might-we-safely-pass-the-buck)
*The reading for this lesson: the case that safely handing AI development to AI agents, rather than aligning superintelligence directly, should be the end goal of technical safety work, and the capability and trust conditions under which that handoff improves safety.*

XLab. "How might we safely pass the buck to AI?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/how-might-we-safely-pass-the-buck-to-ai)
*The source lesson this page adapts.*
:::
