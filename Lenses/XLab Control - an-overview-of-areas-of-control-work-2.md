---
id: 'e3d155cc-b15d-4cf2-8984-08293f4cf77a'
title: "An overview of areas of control work (2): practice, infrastructure, processes, and your theory of change"
tldr: "The five areas Greenblatt ranks lower are the ones closest to a real company: control experiments on how people already use AI, security infrastructure, human review processes, conceptual work, and near-term applications. Then you do the harder thing: pick one area from the whole post, draw the chain from a project starting this month to less existential risk link by link, and find the link you least believe. An agenda is only as strong as its weakest causal step."
summary_for_tutor: "Part 2 of 2 of Ryan Greenblatt's post 'An overview of areas of control work', in Unit 4 of AI Control 1, continuing the previous lens 'An overview of areas of control work (1)', which covered the introduction and the first three areas (settings for control evaluations, control-relevant capabilities and model properties, countermeasures developed in isolation). A short framing text recaps part 1, then the post is embedded from 'Doing control experiments on actual AI usage' to its end: control experiments on actual AI usage, prototyping software infrastructure for control and control-relevant security, prototyping human processes for control, conceptual research, and nearer-term applications of control (misuse, prompt injection, human insiders, rare non-worst-case misalignment, serious mistakes, reward hacking in training, RL without sandboxing). Two graded free-response exercises follow, both from the source lesson. Part 1 asks the learner to build a causal chain from a chosen area (any of the eight, from either lens) to reduced existential risk, answering five sub-questions; Part 2 asks them to name the weakest link in that chain and say what evidence would move them. Part 2 depends on Part 1, so if a learner is stuck on Part 2, send them back to the chain they wrote rather than supplying a crux. Do not pick an area for the learner; any of the eight is a legitimate choice."
reading_minutes: 50
tutor_minutes: 5
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
feedback-instructions:: The learner has built a causal chain from one area of control work to reduced existential risk and answered the five sub-questions. Use the rubric's three criteria (link-by-link mechanism, adoption, threats) and respond in 100 to 180 words, short paragraphs, no lists: name the strongest link in their chain and the weakest, in that order, then give one concrete next step. Do not mention scores. One turn. Do not over-validate; no generic praise.
assessment-instructions::
The student has just read Ryan Greenblatt's "An overview of areas of control work" (across this lens and the previous one, part 1) and is writing the first of two linked exercises. They pick one of the eight areas, or one project inside an area, and build a causal chain from work starting today to reduced existential risk. Any of the areas is a legitimate choice; never push them toward one.

Grade against three criteria, weighted equally:

1. **Link-by-link mechanism.** Each link states its connection to the previous one and is relatively detailed. A list of good things that would happen is not a chain; look for "this produces X, which is used by Y, which changes Z". Penalise jumps where a link is asserted rather than connected.
2. **Adoption.** The response mentions the adoption concerns raised in the post: politicking inside an AI company to get a measure implemented, siloing of information for secrecy reasons and what that does to human auditing, alignment taxes and whether companies will accept the capability hit, and the fact that some of this work has to happen inside a company. Naming and using one or two of these seriously counts; listing all four as keywords does not.
3. **Threats.** The chain ends with a specific threat, and the answer says why the work survives a model that is trying to subvert it. A chain that ends at "safer AI" without naming the threat, or that assumes the model cooperates with the countermeasure, misses this criterion.

Also check that the five sub-questions are actually answered, including the two most often skipped: why the work is feasible now given that current models may be too weak to make it informative, and what would make it obsolete.

Grade only against these criteria and the post itself. Do not require content from later units.

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
feedback-instructions:: The learner is attacking the causal chain they wrote in Part 1; read that answer first. Use the rubric's three criteria (load-bearing crux, evidence in both directions, failure analysis) and respond in 100 to 180 words, short paragraphs, no lists: say whether the crux they chose is really the weakest link in their own chain, then take the sharper of their two observation classes and push on it once. Do not mention scores. One turn. Do not over-validate; no generic praise.
assessment-instructions::
The student is attacking the causal chain they wrote in Part 1. Read their Part 1 answer first; this exercise only makes sense against it.

Grade against three criteria, weighted equally:

1. **Load-bearing crux.** The chosen link is the weakest in the chain. If a visibly shakier link sits elsewhere in their own chain, say which one and why it is weaker.
2. **Evidence.** The response names observations that would raise and lower confidence in the link. Both directions are required. Observations must be things someone could actually see, such as a result from a control evaluation, a company adopting or refusing a measure, or a capability appearing sooner than expected. "More research" is not an observation.
3. **Failure analysis.** The response answers both of the remaining questions: whether the case for prioritizing this area collapses if the link is untrue, and whether another causal chain reaches the same place without that link.

Grade only against these criteria, the post, and the student's own Part 1 answer.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "An overview of areas of control work." *Redwood Research blog*, 9 Apr. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/an-overview-of-areas-of-control-work)
*The reading for this lens and the previous one: a map of eight areas of control research and implementation, roughly ordered by how much investment the author thinks each warrants. This part covers the last five areas.*

XLab. "An overview of areas of control work." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/areas-of-control-work/an-overview-of-areas-of-control-work)
*The source lesson this page adapts.*
:::
