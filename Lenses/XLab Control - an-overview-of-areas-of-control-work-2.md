---
id: 'e3d155cc-b15d-4cf2-8984-08293f4cf77a'
title: "An overview of areas of control work (2): practice, infrastructure, processes, and your theory of change"
tldr: "The five areas Greenblatt ranks lower are the ones closest to a real company: control experiments on how people already use AI, security infrastructure, human review processes, conceptual work, and near-term applications. Then you do the harder thing: pick one area from the whole post, draw the chain from a project starting this month to less existential risk link by link, and find the link you least believe. An agenda is only as strong as its weakest causal step."
summary_for_tutor: "Part 2 of 2 of Ryan Greenblatt's post 'An overview of areas of control work', continuing the previous lens 'An overview of areas of control work (1)', which covered the introduction and the first three areas (settings for control evaluations, control-relevant capabilities and model properties, countermeasures developed in isolation). A short framing text recaps part 1, then the post is embedded from 'Doing control experiments on actual AI usage' to its end: control experiments on actual AI usage, prototyping software infrastructure for control and control-relevant security, prototyping human processes for control, conceptual research, and nearer-term applications of control (misuse, prompt injection, human insiders, rare non-worst-case misalignment, serious mistakes, reward hacking in training, RL without sandboxing). Two graded free-response exercises follow, both from the source lesson. Part 1 asks the learner to build a causal chain from a chosen area (any of the eight, from either lens) to reduced existential risk, answering five sub-questions; Part 2 asks them to name the weakest link in that chain and say what evidence would move them. Part 2 depends on Part 1, so if a learner is stuck on Part 2, send them back to the chain they wrote rather than supplying a crux. Do not pick an area for the learner; any of the eight is a legitimate choice."
reading_minutes: 15
tutor_minutes: 25
tags: []
---
#### Text
content::
This is part 2 of 2 of Ryan Greenblatt's overview of areas of control work. Part 1 covered the introduction and the three areas he would fund most, all research on models themselves: settings for control evaluations, control-relevant capabilities, and countermeasures studied in isolation. This part covers the other five areas, which sit closer to how AI companies actually run: experiments on real AI usage, infrastructure, human processes, conceptual research, and near-term applications.

After the reading, two exercises ask you to choose one area from the whole post, build a causal chain from work beginning today to a reduction in existential risk, and then attack your own chain at its weakest link.

#### Article
source:: [[../articles/greenblatt-an-overview-of-areas-of-control-work]]
from:: ## Doing control experiments on actual AI usage

#### Question: Open
id:: d87f459c-72a8-4f8e-a439-00337d5b7b8b
content::
\## Part 1: Constructing a theory of change

Choose one area of control work from the post, or a specific project within one. Construct a causal chain from work beginning today to a reduction in existential risk. Then, answer the following questions:

- What does the work create? Why is producing it feasible *now*, given that current models may be too weak to make the work informative?
- Where will the output of this work be used and how? Why would this work be adopted by these groups?
- Are there any constants that need to exist in order for this work to still apply in the future? Can any future advancements make this work obsolete.
- Which threat does the work directly target and why does it hold up against a model trying to subvert it?
- How does this reduce x-risk?

Write at least 200 and at most 600 words.
feedback-instructions:: The learner has built a causal chain from one area of control work to reduced existential risk and answered the five sub-questions. Use the rubric's three criteria (link-by-link mechanism, adoption, threats) and respond in 100 to 180 words, short paragraphs, no lists: name the strongest link in their chain and the weakest, in that order, then give one concrete next step. If the learner asks about their score, explain plainly what earned and what lost points. One turn. Do not over-validate; no generic praise.
assessment-instructions:: Score out of 100. 30: the causal chain, from work starting today to less existential risk, 20: each link says how it follows from the previous one ("this produces X, which Y uses, which changes Z") with some detail, and 10: the chain ends in a concrete way existential risk goes down. A list of good things that would happen, rather than a chain, earns at most 10 of these 30. 15: what the work creates, 5, and why it is feasible and informative now even though current models may be too weak to be real threats, 10. 20: adoption, 10: who uses the output and how, and 10: why they would adopt it, dealing seriously with at least one real obstacle such as politicking inside the company to get a measure implemented, information siloed for secrecy (and what that does to human auditing), the alignment tax a company must accept, or work that can only happen inside a company; naming the obstacles as keywords without using them earns none of these 10. 15: durability: what has to stay true for the work to still apply, and what future advance could make it obsolete. 20: the threat, 10: a specific threat the work targets, and 10: why the work still holds against a model that is trying to subvert it; an answer that assumes the model cooperates with the countermeasure earns none of these 10. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "One strong answer (any area can be chosen). Area: prototyping human processes for control, here a human auditing process for actions that the monitor flags on AI agents used inside a company. The work creates a working process: who audits which flags, how fast, with what context, how auditors are kept alert by red-teaming them with planted attacks, and how siloed projects get auditors cleared for them. It is feasible now because companies already run coding agents internally, so the logistics (volume of flags, time per audit, missing context, auditor fatigue) can be learned today even though current models are too weak to be real schemers; what is tested is the process, not the model. The output is used by the company's security and safety teams, who adopt it because it also catches ordinary mistakes and misuse, which helps with the internal politicking, while the cost in staff time is the alignment tax they have to accept, and it has to be built inside the company because of siloing. It keeps applying as long as AIs take consequential actions that humans can still judge when shown them; it becomes obsolete if AIs get so fast or so far beyond us that humans cannot check flagged actions, or if trusted AIs can do the auditing. It targets a rogue internal deployment or sabotage started by an AI agent: it holds up against a model trying to subvert it because the model does not control the audit, the monitor and the auditors sit outside it, and the planted attacks show whether auditors would catch a real attempt. Chain: working audit process now, adopted and staffed when agents become dangerous, flagged attempts get caught, a caught attempt leads to shutdown or stronger measures, fewer successful rogue deployments and less sabotaged safety work, lower existential risk."

#### Question: Open
id:: f18fe965-a293-425d-96f0-130299040835
content::
\## Part 2: Identifying a crux

Identify the link in the earlier causal chain that you believe has the lowest chance of occurring. Then answer:

- Why this link?
- Name potential observations that would raise and lower your confidence in the link.
- If this link was untrue, would the case for prioritizing this area collapse?
- Is there another causal chain that avoids this link?

Write at least 120 and at most 450 words.
feedback-instructions:: The learner is attacking the causal chain they wrote in Part 1; read that answer first. Use the rubric's three criteria (load-bearing crux, evidence in both directions, failure analysis) and respond in 100 to 180 words, short paragraphs, no lists: say whether the crux they chose is really the weakest link in their own chain, then take the sharper of their two observation classes and push on it once. If the learner asks about their score, explain plainly what earned and what lost points. One turn. Do not over-validate; no generic praise.
assessment-instructions:: Score out of 100. 30: the crux: the learner names one link of their causal chain and explains why it is the least likely to hold; if the chain they describe (or their Part 1 answer, where available) has a clearly shakier link elsewhere, at most 10 of these 30. 30: evidence, 15 each for observations that would raise and that would lower their confidence in the link; observations must be things someone could actually see, such as a result from a control evaluation, a company adopting or refusing a measure, or a capability appearing sooner than expected, and "more research" is not an observation. 20: whether the case for prioritizing this area collapses if the link is untrue, with a reason. 20: whether another causal chain reaches the same place without this link, naming one or explaining why there is none. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Continuing the example above: the weakest link is that the company actually adopts and staffs the audit process once agents become dangerous. It is the least likely because audits cost staff time exactly when the company is racing, the cost is visible while the benefit is not, and it depends on internal politics that outside researchers cannot control. Observations that would raise confidence: a frontier company commits to or publishes an auditing process for flagged agent actions, audit teams grow as internal agent usage grows, or a caught incident leads to more investment. Observations that would lower it: audits get cut or turned into rubber stamps under deadline pressure, flag queues go unreviewed, or companies refuse measures with a noticeable alignment tax. If the link fails, the case for this area largely collapses at that company, since an unused process reduces no risk, though the prototype could still inform regulation or another company. An alternative chain avoids it: the same process is made cheap enough to run as part of standard security operations, or regulators require it, so adoption no longer depends on the company volunteering."

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "An overview of areas of control work." *Redwood Research blog*, 9 Apr. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/an-overview-of-areas-of-control-work)
*The reading for this lens and the previous one: a map of eight areas of control research and implementation, roughly ordered by how much investment the author thinks each warrants. This part covers the last five areas.*

XLab. "An overview of areas of control work." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/areas-of-control-work/an-overview-of-areas-of-control-work)
*The source lesson this page adapts.*
:::
