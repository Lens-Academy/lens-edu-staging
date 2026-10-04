---
id: '4669e8a2-e7eb-432b-809b-2c5c3611d77f'
title: "How might we safely pass the buck to AI? (1): what passing the buck means and when it is safer"
tldr: "Josh Clymer's goal as a safety researcher is to put himself out of a job: not to align superintelligence himself, but to hand the remaining safety work to AI agents who are better at it than he is. The hard part is knowing when that handoff is safer than keeping humans in the loop. His answer is two sufficient conditions: the handoff is safer if the agents are more capable and more trustworthy than the humans they replace."
summary_for_tutor: "Part 1 of 2 of Josh Clymer's post 'How might we safely pass the buck to AI?' (Redwood Research blog, Feb 2025), Module 1 in the source curriculum, where the page is a bare paper: there is no framing prose, only the post rendered inline. Everything before the Article segment is our own navigational lead-in, drawn from the post's own introduction and section headings, and none of it is ported editorial voice. This part is the post's opening summary and sections 1 to 7: objections, what passing the buck means (AI agents do most internal R&D and human oversight has little bearing on safety), why it rather than aligning superintelligence should be the primary end goal, the three strategies (one-time hand off to M_1, iterated hand off to a more capable M_2, deference to an AI advisor about whether to trust M_1, each defining a 'deferred task'), and the comparison that matters: passing the buck against the human-oversight-preserving alternative, not against perfect safety. Under the drop-in-replacement simplification, passing the buck is safer under two sufficient conditions: the capability condition (M_1 agents are more capable than the humans they replace on all dimensions of the deferred task, checked behaviourally with conversational evals, observed internal performance and held-out long-horizon tasks) and the trust condition (they are as safe as they appear in evaluations, for the whole deferred task). Clymer expects trust to be the harder one. The opening summary sketches the four arguments for trust; part 2 covers them in full. The practice question at the end of this part asks the learner when, by Clymer's definition, a developer has passed the buck (AI agents do most internal R&D and human oversight has little bearing on safety, so approval can be a rubber stamp) and for two of his reasons to aim at passing the buck rather than at aligning superintelligence directly; its model answer is in the assessment-instructions. The longer practice question, applying both conditions and the four arguments to a new case, is at the end of part 2. If a learner wants to discuss this part, the spine is the comparison with keeping humans in the loop and the two conditions."
reading_minutes: 38
tutor_minutes: 5
tags: []
---
#### Text
content::
\## Before you read

Part 1 of 2. The previous six lenses, [[../Lenses/XLab Control - ai-control-paper|AI Control: Improving Safety Despite Intentional Subversion]], measured control protocols against a red team inside one concrete setting. This post steps back and asks what all of that is finally for.

Josh Clymer states his goal as putting himself out of a job. Rather than aiming at the loftier ambition of aligning superintelligence, he wants developers to be able to safely replace human safety researchers with AI agents, at which point, he argues, the bulk of the risks a human technical researcher can address have been addressed. He calls that "passing the buck."

The post is one long argument with a clear spine. It first says what passing the buck means and why he thinks it, not aligning superintelligence, should be the field's primary end goal. It then lays out three strategies for doing it: a one-time hand off to a system he calls M_1, an iterated hand off where M_1 passes the buck to a more capable M_2, and deference to an AI advisor whose deferred task is to say whether M_1 should be trusted at all. Clymer then argues that cutting humans out is responsible under two sufficient conditions, that M_1 is more capable than the human-oversight-preserving alternative and that it is more trustworthy than that alternative, and spends the second half of the post on four arguments a developer might use to establish trust.

This part covers the post's summary and its sections 1 to 7, which end with the two conditions. Sections 8 to 12, where the four arguments for trust are made in full, are in part 2.

#### Article
source:: [[../articles/clymer-how-might-we-safely-pass-the-buck-to-ai]]
to:: The next sections discuss several ways to justify trustworthiness.

#### Callout: Practice: what passing the buck means, and why aim for it
tone:: amber

#### Question: Open
id:: d91710b2-1faf-4b84-9cf7-3b3c11a24e37
content:: (a) By Clymer's definition, when has a developer "passed the buck" to AI, even if humans still approve every deployment?
(b) Give two of his reasons why safety researchers should aim mainly at passing the buck to AI, rather than at aligning superintelligence themselves.
placeholder:: Answer (a) and (b) in a few sentences
assessment-instructions:: Score out of 100. 50: (a), 25: AI agents do most of the developer's internal AI research and development; 25: human oversight of the agents has little bearing on safety, for example because humans cannot keep up with the volume of work, so their approval is a rubber stamp that would not catch sabotage. 50: (b), 25 for each of two different reasons, any two of: weaker AI systems are easier to evaluate and train than superintelligent ones, so handing the work to them is easier than humans doing it all directly; AI agents will do most of the work of scaling safety anyway, because running at more than ten times human speed even a few months of their research is worth years of human work; AI agents can work directly with the AI systems they are trying to align, so human preparation now is less efficient than AI work later; the most promising plan for making superintelligence safe is to pass the buck again and again to more capable AI, so research on passing the buck also prepares for that. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "(a) When AI agents do most of the developer's internal AI research and development, and human oversight of those agents has little bearing on whether things stay safe. Humans may still press 'approve' on deployments, but if agents run thousands of research tasks a day, the humans cannot keep up and would not notice sabotage or fake safety results, so their approval is a rubber stamp. (b) First, weaker AI systems are easier to evaluate than superintelligent ones, so it is easier to train them to do what we intend and let them finish the job. Second, AI agents will probably do most of the work of scaling safety anyway: running at more than ten times human speed, six months of their research is worth years of human work, and they can work directly with the systems they are trying to align. A third reason: the most promising plan for scaling safety further is to pass the buck again to still more capable AI, so research on passing the buck helps there too."
feedback-instructions:: In at most three sentences: say what the learner got right, then give whichever part of the model answer they missed, in one sentence. If they said the buck is passed only when humans formally stop approving, say plainly that for Clymer it happens once human oversight stops mattering for safety, even while approval continues. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Clymer, Josh. "How might we safely pass the buck to AI?" *Redwood Research blog*, 19 Feb. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/how-might-we-safely-pass-the-buck)
*The reading for this lesson, its summary and sections 1 to 7: the case that safely handing AI development to AI agents, rather than aligning superintelligence directly, should be the end goal of technical safety work, and the capability and trust conditions under which that handoff improves safety.*

XLab. "How might we safely pass the buck to AI?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/how-might-we-safely-pass-the-buck-to-ai)
*The source lesson this page adapts.*
:::
