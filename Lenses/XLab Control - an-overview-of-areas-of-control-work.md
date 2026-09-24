---
id: '26e96cd7-7b18-4994-8c33-aaeb5886a272'
title: "An overview of areas of control work (1): evaluation settings, capabilities, and countermeasures"
tldr: "Eight areas of control work, roughly ranked by how much of the field's money each deserves. This part covers the three Greenblatt ranks highest, all research on models themselves: building settings and running control evaluations in them, measuring the capabilities that matter for control, and developing countermeasures one at a time. Read it as a shortlist: in part 2 you pick one area and defend its theory of change."
summary_for_tutor: "Part 1 of 2 of Ryan Greenblatt's post 'An overview of areas of control work', in Unit 4 of AI Control 1. A short framing text places the lens after the control toolkit lenses of this unit, then the post is embedded from its start through the end of the third area. The post lists eight areas of control research and implementation, roughly in descending order of the investment the author thinks each warrants (he suggests about a third of current control resources for the first). This part covers the introduction and the first three areas: developing and using settings for control evaluations (including the aims of current settings work and the kinds of settings he wants), better understanding control-relevant capabilities and model properties, and developing specific countermeasures in isolation (synthetic inputs, false facts, steganography, exploration hacking, probes, human auditing, collusion busting, capability control, rate detection, elicitation without learning, stronger trusted models). There are no exercises in this part. Part 2 ('An overview of areas of control work (2)') covers the remaining five areas and holds the two graded exercises, in which the learner picks one area and builds, then attacks, a causal chain to reduced existential risk; if a learner asks which area to choose, do not choose for them."
reading_minutes: 35
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

This unit has worked through the pieces of control from the inside: [[../Lenses/XLab Control - detection-mitigations|Detection Mitigations]], [[../Lenses/XLab Control - prevention-response-mitigations|Prevention and Response Mitigations]], [[../Lenses/XLab Control - control-evaluations|Control Evaluations]], and [[../Lenses/XLab Control - environments|Environments]].

This lens steps back to the whole field. Ryan Greenblatt lists the areas of control research and implementation that seem promising to him, and says up front that the list is roughly in descending order of how much investment each area should get. It leans on the framings in [[../Lenses/XLab Control - prioritizing-threats-for-ai-control|Prioritizing threats for AI control]], which you met in Unit 3.

This is part 1 of 2. It covers the introduction and the first three areas, all research on models themselves: settings for control evaluations, control-relevant capabilities, and countermeasures studied in isolation. Part 2 covers the other five areas and then asks you to choose one area, build a causal chain from work beginning today to a reduction in existential risk, and attack your own chain at its weakest link. Note candidate areas as you read.

#### Article
source:: [[../articles/greenblatt-an-overview-of-areas-of-control-work]]

to:: but doing decentralized research on this seems reasonable for now.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "An overview of areas of control work." *Redwood Research blog*, 9 Apr. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/an-overview-of-areas-of-control-work)
*The reading for this lens and the next: a map of eight areas of control research and implementation, roughly ordered by how much investment the author thinks each warrants. This part covers the introduction and the first three areas.*

XLab. "An overview of areas of control work." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/areas-of-control-work/an-overview-of-areas-of-control-work)
*The source lesson this page adapts.*
:::
