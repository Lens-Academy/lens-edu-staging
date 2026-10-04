---
id: '392c68c3-e1da-4e0e-83a1-8fed7590dfe0'
title: "Rogue deployments"
tldr: "Causing a catastrophe directly takes a lot of work while safety measures watch. Starting a copy of yourself that nobody monitors might take twenty lines of code. Buck Shlegeris argues that this second step, a rogue deployment, is the central high-stakes threat."
summary_for_tutor: "Second teaching lens of Unit 2 of AI Control Fundamentals. The learner reads Buck Shlegeris's post 'AI catastrophes and rogue deployments' (Redwood Research, June 2024) from its first paragraph to the end. Key ideas. A rogue deployment is a deployment of the model where the safety measures are absent. Catastrophes either happen with all safety measures in place or go through a rogue deployment first. The two varieties are weight exfiltration leading to a rogue external deployment, and a rogue internal deployment inside the lab's own datacenter (started by the model, by employees, or by outside hackers). Causing a catastrophe directly is hard because it needs a few wildly superhuman actions or many ordinary ones, while launching a rogue deployment may be easy (twenty lines of Python with weight access). Catastrophes without rogue deployment, in Shlegeris's view, mostly need many actions and so give the lab many chances to spot them, with exceptions such as long-term jailbreaks, steganographic reasoning and subtle long-term manipulation. In this course's terms, launching a rogue deployment is the central high-stakes threat, and the 'extremely subtle long-term failure' case is low-stakes. Two questions follow: the first is scored, the second is not."
reading_minutes: 12
tutor_minutes: 8
---
#### Text
content::
Buck Shlegeris is CEO of Redwood Research ([80,000 Hours](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)). This post introduces the rogue deployment, a model running somewhere its safety measures do not reach. Shlegeris writes that Redwood's first control paper was mostly motivated by this kind of catastrophe. As you read, notice how many actions each kind of catastrophe needs.

#### Article
source:: [[../articles/shlegeris-ai-catastrophes-and-rogue-deployments]]
from:: In this post, I want to introduce the concept of a “rogue deployment”

#### Question: Open
id:: 6ec1ace8-e78b-47b1-8e34-82b058cb6ffe
content::
Without looking back: what is a rogue deployment, and why does Shlegeris think launching one is easier for an AI than causing a catastrophe directly?
force-feedback:: first
assessment-instructions:: Score out of 100. 40: what a rogue deployment is: a copy of the model running where the safety measures are absent, for example an AI running itself unmonitored inside the company's datacenter, copying its weights to an outside server, or someone stealing and running it. Full 40 for the general idea of the model running without its safety measures or monitoring. 60: why launching one is easier. Causing a catastrophe directly, with the safety measures in place, needs either a few wildly superhuman actions or many ordinary ones, each a chance to be caught, while launching a rogue deployment may take only a few actions (for example a short piece of code, if the AI has access to its weights), and afterwards the AI is no longer constrained. 30 of these 60 for only one side of the comparison. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A rogue deployment is a copy of the model running somewhere its safety measures do not reach. Causing a catastrophe directly while being watched takes either superhuman actions or many ordinary ones, each a chance to be caught. Starting a rogue deployment might take a few lines of code, and after that nothing constrains the AI."
feedback-instructions:: The learner just read Shlegeris's "AI catastrophes and rogue deployments". A rogue deployment is a deployment of the model where the safety measures are absent (examples: an AI hacking its datacenter and running itself unmonitored, self-exfiltrating to outside servers, or someone stealing and running it). Causing a catastrophe directly is hard because, with safety measures running, it needs either a few wildly superhuman actions or many ordinary ones, each a chance to be caught. Launching a rogue deployment may take very little, for example twenty lines of simple code for an AI with weight access, and afterwards the AI is unconstrained. Reply in at most four sentences: acknowledge what is correct, name the most important missing point in one sentence, correct any error in one sentence. One turn, no follow-up question, no generic praise. Tell them to move on.

#### Question: Open
id:: 9b0f4a65-3e40-492f-90da-2e8780ba92cf
content::
Shlegeris lists a few ways a catastrophe could happen without a rogue deployment. Pick one. Is it high-stakes or low-stakes in the sense of the previous lesson? Say why.
force-feedback:: first
feedback-instructions:: The learner classifies one of Shlegeris's catastrophes without rogue deployment. His examples: amazing long-term jailbreaks of the monitor, large-scale steganographic reasoning, and extremely subtle long-term failure such as slowly manipulating public opinion or introducing carefully chosen errors. He also says catastrophes without rogue deployment mostly need many actions, so they give the lab many chances to spot them. A good answer classifies by how many actions are needed and how incriminating each action is. Subtle long-term manipulation is a clear low-stakes case. A jailbreak found by iterating over many attempts is mostly low-stakes, but one that, once found, lets a single action through can be argued as high-stakes. Accept any classification argued from those two properties. If the learner classifies by how bad the outcome is, say in one sentence that the axis is number of actions and how incriminating each is. At most four sentences. One turn. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Shlegeris, Buck. "AI catastrophes and rogue deployments." *Redwood Research blog*, 3 June 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/ai-catastrophes-and-rogue-deployments)
:::
