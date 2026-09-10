---
id: '6171a224-2876-4876-a0ca-da8825c9280c'
title: "AI catastrophes and rogue deployments"
tldr: "Stealing the crown jewels is hard work. Getting a copy of the key cut is easy, and after that the jewels are a matter of time. Buck Shlegeris argues AI catastrophes split along the same seam: the ones that happen with every safety measure still running, and the ones that begin by escaping them. That second step, a rogue deployment, might be twenty lines of Python."
summary_for_tutor: "Imported from XLab's AI Control curriculum, Module 4. XLab renders Buck Shlegeris's post 'AI catastrophes and rogue deployments' in full with two flashcard sequences inserted into it; this lens reproduces that placement. The opening Text segment is ours, not XLab's: it says what the post does and links the two neighbouring lessons that use the same categories. Then the reading in three excerpts. After excerpt one (the definitions) come four recall questions: what catastrophe means here, what safety measures are, what a rogue deployment is, and instrumental versus terminal catastrophe. After excerpt two (safety cases, the two varieties, and the hard-versus-easy argument) come two more: the two varieties, and why launching a rogue deployment is the more worrying path. Excerpt three runs to the end of the post. All six questions are XLab's, with XLab's revealed answers used as marking criteria rather than shown to the learner. If a learner asks about the attacker table, note that the post presents it as an image."
reading_minutes: 20
tutor_minutes: 0
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
content:: In the rogue-deployments framing, what does "catastrophe" mean?
max-chars:: 400
assessment-instructions:: The learner has just read the opening section of Buck Shlegeris's "AI catastrophes and rogue deployments" and is recalling a definition from memory. Full credit for: a failure you do not want to happen even once, the end result that is unacceptable, with the post's examples or equivalents (an adversary amassing power, launching nukes, starting a war, building superintelligence). Partial credit if they give the shape of the definition but no examples. Mark down an answer that includes the AI escaping the datacenter as the catastrophe itself: Shlegeris explicitly excludes that here and treats it as the instrumental step. One or two sentences is enough; do not ask for more. No generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one concrete foothold from the reading, for example the sentence that contrasts the end result with the AI escaping the datacenter, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: 9c24f011-b087-4d46-9b8b-d504d89252bb
content:: What are safety measures?
max-chars:: 400
assessment-instructions:: The learner is recalling a definition from the opening section of Shlegeris's post. Full credit for: interventions applied to all deployments of the model, to any users including internal ones, that try to prevent safety problems. Credit the two example categories: control measures such as trusted monitoring, and security measures that make it harder to exfiltrate the model weights. The "all deployments, including internal" part is the load-bearing half, because it is what a rogue deployment is defined against; say so in one sentence if they omit it. One or two sentences is enough. No generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one foothold from the reading rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: 0450c4a5-53d8-4f24-8214-078641b6d284
content:: What is a rogue deployment?
max-chars:: 400
assessment-instructions:: The learner is recalling the post's central definition. Full credit for: a deployment of your model where the safety measures are absent. Credit any of Shlegeris's three examples: an AI hacking its datacenter and running itself while hiding what it is doing from its creators, an AI self-exfiltrating and running itself on unmonitored servers, or someone stealing the AI and running it in their own datacenter. Note that the definition is about the absence of the measures, not about where the model runs or who is at fault: an answer that says "the AI escapes" has captured one example rather than the category, so correct it in one sentence. One or two sentences is enough. No generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one foothold from the reading rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: ac45abd3-9e7d-4ac6-bb2f-4382aead85b1
content:: What is the difference between an instrumental and a terminal catastrophe?
max-chars:: 500
assessment-instructions:: The learner is recalling the parenthetical reframing at the end of the section. Full credit for: the terminal catastrophe is the end state we wanted to avoid, while an instrumental catastrophe is something happening that makes the situation go out of our control, so that a terminal catastrophe becomes likely and much harder to prevent. Credit the punchline: establishing a rogue deployment is the central example of an instrumental catastrophe. Partial credit if they get the two labels the right way round but not the "out of our control, much harder to prevent" content. Two or three sentences is enough. No generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, isolate one half of the question, for example asking only what the terminal catastrophe is, rather than repeating the whole thing. Grade only against criteria this page or the reading supplied.

#### Article
from:: ## Rogue deployments and safety cases
to:: sketchy-actions that are probably required to cause the catastrophe.

#### Question: Open
id:: 6984229c-aef0-443f-aa16-3b0ef4f96d22
content:: What are the two main varieties of catastrophe involving a rogue deployment?
max-chars:: 600
assessment-instructions:: The learner is recalling the two-way split Shlegeris opens "More on catastrophes with rogue deployment" with. Full credit for both: (1) weight exfiltration leading to a rogue external deployment, where the model is exfiltrated from the datacenter, run on hardware you do not control, and fine-tuned to remove safety training; (2) rogue internal deployment, where the model is run inside the lab's own datacenter in an unauthorized way, by the model itself, by employees, or by external hackers who cannot exfiltrate the weights. Half credit for one variety only. Credit but do not require the three routes to the internal variety. Two or three sentences is enough. No generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one foothold from the reading, for example asking where the model is running in each case, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: 0333eef9-1839-427b-a2a5-82bcb1691540
content:: Why is launching a rogue deployment a more worrying path to catastrophe than the AI causing one directly under safety measures?
max-chars:: 700
assessment-instructions:: This is the argument the section turns on, so grade it on reasoning rather than wording. Full credit needs both halves. (1) Causing a catastrophe directly seems fundamentally hard: it requires either a small number of wildly superhuman actions or a large number of ordinary ones, and the large number gives the safety measures many chances to catch the AI. (2) Launching a rogue deployment seems fundamentally easy: with model weight access it can take as little as twenty lines of Python in a Jupyter notebook, and afterwards the AI's actions are far less constrained, so it can take the many sketchy actions a catastrophe needs. Half credit for one half. If they answer only "because there is no monitoring", push once on why that matters given how many actions a catastrophe takes. Three to five sentences. No generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, isolate the first half and ask what makes causing a catastrophe hard, rather than repeating the question. Grade only against criteria this page or the reading supplied.

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
