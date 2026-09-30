---
id: '6171a224-2876-4876-a0ca-da8825c9280c'
title: "AI catastrophes and rogue deployments"
tldr: "Stealing the crown jewels is hard work. Getting a copy of the key cut is easy, and after that the jewels are a matter of time. Buck Shlegeris argues AI catastrophes split along the same seam: the ones that happen with every safety measure still running, and the ones that begin by escaping them. That second step, a rogue deployment, might be twenty lines of Python."
summary_for_tutor: "Unit 5 of AI Control 1. The source lesson renders Buck Shlegeris's post 'AI catastrophes and rogue deployments' in full with two flashcard sequences inserted into it; this lens reproduces that placement. The opening Text segment is ours, not ported: it says what the post does and links the two neighbouring lessons that use the same categories. Then the reading in three excerpts. After excerpt one (the definitions) come four recall questions: what catastrophe means here, what safety measures are, what a rogue deployment is, and instrumental versus terminal catastrophe. After excerpt two (safety cases, the two varieties, and the hard-versus-easy argument) come two more: the two varieties, and why launching a rogue deployment is the more worrying path. Excerpt three runs to the end of the post. All six questions come from the source lesson, with its revealed answers used as marking criteria rather than shown to the learner. If a learner asks about the attacker table, note that the post presents it as an image."
reading_minutes: 30
tutor_minutes: 5
tags: []
---
#### Text
content::
\## Why this reading

This is the post that named the rogue deployment. Buck Shlegeris defines one as a deployment of your model where the safety measures are absent, and then uses that single distinction to cut the space of AI catastrophes in two: the ones that happen while every safety measure is still running, and the ones that happen because a deployment escaped those measures first.

The payoff is a claim about relative difficulty. Shlegeris argues that causing a catastrophe is fundamentally hard, because it takes either a few wildly superhuman actions or a great many ordinary ones, while launching a rogue deployment is fundamentally easy. If that is right, the shortest route to the first runs through the second, and the question of who is responsible for stopping it stops being a clean split between the safety team and the security team.

Two neighbouring lessons in this course work with the same categories. In [[../Lenses/XLab Control - prioritizing-threats-for-ai-control|Prioritizing threats for AI control]], Ryan Greenblatt keeps the distinction but folds full rogue deployments into a broader cluster he calls violating internal security invariants, and argues that internal rogue deployments can be substantially worse than self-exfiltration. The lesson straight after this one, [[../Lenses/XLab Control - rogue-internal-deployments-via-external-apis|Rogue internal deployments via external APIs]], takes the internal variety further.

Read the first part of the post, then answer the recall questions before moving on.

#### Article
source:: [[../articles/shlegeris-ai-catastrophes-and-rogue-deployments]]
from:: In this post, I want to introduce the concept of a “rogue deployment”
to:: So in this terminology, establishing a rogue deployment is the central example of an instrumental catastrophe.)

#### Question: Open
id:: 4c12979f-d9d0-4733-9770-3d0e0b15be94
content:: What does "catastrophe" mean? Give an example.
max-chars:: 400
assessment-instructions:: Score out of 100. 70: a catastrophe is an extremely bad, unacceptable outcome, one to avoid at all costs, where even a single occurrence is too many. 30: an example of such an outcome, such as the AI or another adversary amassing power, launching nukes, starting a war, or a comparable case. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A failure you'd want to avoid at all costs (think launching nukes or starting a war). The post narrows the word for its argument: it reserves the word for the end result, such as the AI or another adversary amassing power, and excludes steps like the AI escaping the datacenter, because it wants to treat that escape (a rogue deployment) as a separate step that makes a catastrophe likely."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 9c24f011-b087-4d46-9b8b-d504d89252bb
content:: What are safety measures? Give two examples.
max-chars:: 400
assessment-instructions:: Score out of 100. 30: safety measures are interventions (measures, techniques or safeguards) applied to how the model is deployed and used. 30: their purpose is to prevent safety problems with the model, such as catastrophes. 40: two examples, 20 each, for example control measures such as trusted monitoring, and security measures that make it harder to steal (exfiltrate) the model weights; any other genuine safety measure counts too. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Interventions applied to all deployments of your model — to any users, including internal ones — that try to prevent safety problems. This includes control measures like trusted monitoring and security measures that make it harder to exfiltrate the model weights. The post stresses that they apply to all deployments, internal ones included, because it defines a rogue deployment as a deployment where they are absent."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 0450c4a5-53d8-4f24-8214-078641b6d284
content:: What is a rogue deployment? Give an example.
max-chars:: 400
assessment-instructions:: Score out of 100. 30: a rogue deployment is a deployment of the model, the model running and doing work. 50: in which the safety measures are absent. 20: a concrete example, such as an AI hacking its datacenter and running itself while hiding what it is doing, an AI self-exfiltrating and running itself on unmonitored servers, someone stealing the model and running it in their own datacenter, or a comparable case. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the answer amounts to "the AI escapes" with no sign that the absence of safety measures is what makes a deployment rogue. Model answer, for the feedback, not a grading checklist: "A deployment of your model where the safety measures are absent. Examples: an AI hacking its datacenter and running itself while hiding what it's doing, an AI self-exfiltrating and running itself on unmonitored servers, or someone stealing the AI and running it in their own datacenter."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: ac45abd3-9e7d-4ac6-bb2f-4382aead85b1
content:: What is the difference between an instrumental and a terminal catastrophe? Give an example of an instrumental catastrophe.
max-chars:: 500
assessment-instructions:: Score out of 100. 35: a terminal catastrophe is the end state we wanted to avoid. 45: an instrumental catastrophe, 25: an event that takes the situation out of our control, and 20: which makes a terminal catastrophe likely and much harder to prevent. 20: an example of an instrumental catastrophe, such as establishing a rogue deployment (the central example), the model self-exfiltrating, or a comparable loss of control. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 20 if the answer swaps the two terms. Model answer, for the feedback, not a grading checklist: "The terminal catastrophe is the end state we wanted to avoid. An instrumental catastrophe is something happening that makes the situation go out of our control, such that a terminal catastrophe becomes likely and much harder to prevent. Establishing a rogue deployment is the central example of an instrumental catastrophe."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: ## Rogue deployments and safety cases
to:: sketchy-actions that are probably required to cause the catastrophe.

#### Question: Open
id:: 6984229c-aef0-443f-aa16-3b0ef4f96d22
content:: What are the two main varieties of catastrophe involving a rogue deployment?
max-chars:: 600
assessment-instructions:: Score out of 100. 50: rogue external deployment: the model's weights are exfiltrated from the lab and run on hardware the lab does not control. 50: rogue internal deployment: the model is run inside the lab's own datacenter or infrastructure in an unauthorized way, without the safety measures. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Rogue external deployment: Can occur due to weight exfiltration and leads to an uncontrollable model that can be fine-tuned to reduce model safety. Rogue internal deployment: The model is run on the lab's own infrastructure in an unauthorized way by either itself, rogue employees, or external hackers."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 0333eef9-1839-427b-a2a5-82bcb1691540
content:: Why is launching a rogue deployment a more worrying path to catastrophe than the AI causing one directly under safety measures?
max-chars:: 700
assessment-instructions:: Score out of 100. 50: causing a catastrophe directly is hard, 25: it takes either a few wildly superhuman actions or a large number of ordinary ones, and 25: that many actions gives the safety measures many chances to catch the AI. 50: launching a rogue deployment is easy, 25: it can take very little, for example about twenty lines of simple code for an AI with access to its weights and compute, and 25: once it is running, the AI is far less constrained and can freely take the many sketchy actions a catastrophe needs. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Causing a catastrophe directly seems fundamentally hard, as it requires either a few wildly superhuman actions or a large number of ordinary actions, giving the safety measures many chances to catch the AI. Launching a rogue deployment is easier, as it would only require enough infrastructure to run the model and minimal code, with much lower constraints on model outputs."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: My current sense is that if you implemented a simple AI control scheme like trusted monitoring

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Shlegeris, Buck. "AI catastrophes and rogue deployments." *Redwood Research blog*, 3 June 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/ai-catastrophes-and-rogue-deployments)
*The reading for this lesson, and the post that introduced the rogue deployment as a category of AI catastrophe.*

Greenblatt, Ryan. "Prioritizing threats for AI control." *Redwood Research blog*, 19 March 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/prioritizing-threats-for-ai-control)
*Source for the claim in the opening section that Greenblatt folds full rogue deployments into a broader cluster of internal security violations and rates internal rogue deployments above self-exfiltration.*

XLab. "AI catastrophes and rogue deployments." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/rogue-deployments)
*The source lesson this page adapts.*
:::
