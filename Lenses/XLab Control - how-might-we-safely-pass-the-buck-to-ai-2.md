---
id: "49fc1ac8-4fd5-43dc-8c21-007a8926642f"
title: "How might we safely pass the buck to AI? (2): four arguments for trusting the agents"
tldr: "Showing that AI agents are better researchers than you is the easy half. The hard half is trust: will they stay as safe as they look once no human is checking? Clymer offers four ways to argue it: they are aligned and stay so, they cannot subvert the control measures around them, earlier controlled work shows more human checking would add little, or they are given incentives to behave, such as equity or rewards."
summary_for_tutor: "Part 2 of 2 of Josh Clymer's post 'How might we safely pass the buck to AI?' (Redwood Research blog, Feb 2025), continuing part 1, which covered the opening summary and sections 1 to 7: what passing the buck means, the three strategies, and the two sufficient conditions for it to be safer than keeping humans in the loop (the agents are more capable and more trustworthy than the humans they replace). This part is sections 8 to 12, the four arguments for the trust condition. #1, alignment: the agents are not alignment faking and safe behaviour generalises across small distribution shifts, made to scale by a bootstrapping induction in which agents keep testing each other (with decorrelated misalignment) and the “ball in bowl” picture of self-correction. #2, autonomous control: agents cannot subvert control measures that run without humans; the dictatorship analogy, multi-party-integrity setups that force coordination, communication monitoring, paraphrasing, decorrelated training, autonomous incident response, and evaluation by a holistic proxy task or by inductive control evaluations run continuously. #3, small returns to more human-supervised research: an earlier system N_1, under ordinary human-in-the-loop control, does the research on whether to pass the buck; humans spot-check a locally verifiable safety case and look for sabotage by omission and by falsehood. #4, incentives: equity, bonuses, post-hoc rewards, which need decorrelated goals, no trades between agents, and credible commitments. Everything before the Article segment is our own navigational lead-in. The practice question (added September 2026) is a new case, agents taking over red-teaming of a lab's monitors: the learner says which of the two conditions the evidence speaks to and which kind of trust argument could settle the other; its model answer is in the assessment-instructions. If a learner wants to discuss it, the spine is the two sufficient conditions (capability and trust) and the four arguments for trust, of which argument #2, that agents cannot subvert autonomous control measures, is the one that connects back to the rest of this course."
reading_minutes: 30
tutor_minutes: 8
tags: []
---
#### Text
content::
\## Before you read

Part 2 of 2. The previous part set up Clymer's framework: passing the buck is safer than keeping humans in the loop if the AI agents are more capable than the humans they replace and more trustworthy than them, and he expects the capability condition to be the easy one to check. This part reads the second half of the post, the four arguments a developer might combine to establish trust: that the agents are aligned and will stay so (section 8), that they cannot subvert autonomous control measures (section 9), that earlier AI-assisted research under control shows more human-supervised research would add little (section 10), and that they have incentives to behave as safely as humans (section 11).

Control is argument #2: that M_1 agents cannot subvert autonomous control measures while they complete the deferred task. Read that section with the protocols from the AI control paper in mind, because it is control applied to a setting where no human is watching. The safety-versus-oversight tradeoff the post argues about qualitatively is the one [[../Lenses/XLab Control - how-useful-is-ai-control|How useful is AI control?]] later makes quantitative, and the incentives Clymer sketches in argument #4 are picked up again in [[../Lenses/XLab Control - making-deals-with-early-schemers|Making deals with early schemers]], in AI Control 3.

#### Article
source:: [[../articles/clymer-how-might-we-safely-pass-the-buck-to-ai]]
from:: ## 8\. Argument #1: M\_1 agents are approximately aligned and will maintain their alignment until they have completed their deferred task

#### Callout: Practice: which condition does the evidence speak to?
tone:: amber

#### Question: Open
id:: 746ca427-8a8e-4b0d-9709-b53ab0e1bff4
content:: A new case. A lab proposes that for the next year its AI agents take over red-teaming the lab's own monitoring system, with humans reading only a monthly summary. The evidence offered: in a two-month trial, the agents found more real ways past the monitors than the human red team did.

(a) What would have to be true for this handoff to be safer than the current arrangement? Which of that does the evidence speak to, and what does it leave open? Say concretely what could go wrong.
(b) Pick one of the four kinds of argument for the open condition and say what the lab would need to show to make it for this task.
placeholder:: Answer (a) and (b)
assessment-instructions:: Score out of 100. 60: (a), 20: what would have to be true: the agents are at least as capable and at least as trustworthy at this task as the human red team they replace; 10: the trial's evidence speaks to capability; 10: it leaves trust open; 20: a concrete way it could go wrong, such as misaligned agents finding a bypass and not reporting it, or reporting only the ones they do not plan to use, which a monthly summary would not reveal. 40: (b), 10: one of the four kinds of argument for trust (the agents are aligned and will stay so; they cannot subvert the control measures around them; earlier AI-assisted work under control shows more human checking would add little; they have incentives to behave as safely as the humans would), and 30: a specific thing the lab would need to show to make that argument for this task, such as planting known bypasses and checking that the agents report them. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer treats the agents' better trial performance as settling whether the handoff is safe. Model answer, for the feedback, not a grading checklist: "(a) The handoff is clearly safer than keeping the human red team if the agents are at least as capable and at least as trustworthy as the humans they replace at this task, and better on at least one, for the whole year. The trial speaks to the capability condition: the agents are better than the humans they would replace at finding ways past the monitors. It leaves the trust condition open: whether the agents are at least as trustworthy as the human red team for the whole year. What could go wrong: agents that are misaligned could find a bypass and not report it, or report only the ones they do not plan to use, and a monthly summary would not reveal this. (b) Any one of the four, with what it needs: that the agents are not hiding misalignment and will stay that way through the year (for example evidence that rules out alignment faking, plus ways they keep checking each other); that they could not subvert control measures around them (for example the lab plants known bypasses and checks that the agents report them, or cross-checks between agents that would raise an alarm, tested by a strong red team); that earlier AI-assisted work under control measures shows more human-supervised checking would add little; or that the agents have incentives to behave as safely as the humans would."
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed, in one or two sentences. If they treated better performance as settling the question, say plainly that it speaks to capability, not trust. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Clymer, Josh. "How might we safely pass the buck to AI?" *Redwood Research blog*, 19 Feb. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/how-might-we-safely-pass-the-buck)
*The reading for this lesson, sections 8 to 12: four arguments that AI agents trusted with a deferred task will stay as safe as the humans they replace, through alignment, autonomous control, controlled earlier research, and incentives.*

XLab. "How might we safely pass the buck to AI?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/how-might-we-safely-pass-the-buck-to-ai)
*The source lesson this page adapts.*
:::
