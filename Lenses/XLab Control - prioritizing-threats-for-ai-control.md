---
id: 'a73924bf-90e1-4be3-b930-79e72de8b71f'
title: "Prioritizing threats for AI control"
tldr: "Rank the ways a misaligned AI could hurt you: break your security invariants, sabotage the work you asked for, or cause trouble on the side. Ryan Greenblatt puts an AI running unmonitored inside your own datacenter above one that stole its weights and fled. The escapee took a copy of the model. The intruder has your compute, your permissions, and your experiments."
summary_for_tutor: "Imported from XLab's AI Control curriculum, Module 1. The reading is Ryan Greenblatt's 'Prioritizing threats for AI control', embedded as three excerpts of the imported article. Excerpt 1 gives the three threat clusters; four quick-recall questions then check the vocabulary (ensuring control, rogue deployment, internal security invariant, internal versus external rogue deployment). Excerpt 2 covers concentrated versus non-concentrated failures and Greenblatt's ranked priority list; one recall question then asks why a rogue internal deployment can be worse than self-exfiltration. Excerpt 3 is Greenblatt's justification of the ranking, followed by a 150 to 500 word free response that asks the learner to re-derive the top three priorities under a different level of political will. The recall answers and the free-response criteria come from XLab. Do not hand the learner the priority list or the model answers; make them argue from the compute and privileged-access logic and from the pause-dependence of self-exfiltration."
reading_minutes: 30
tutor_minutes: 0
tags: []
---
#### Text
content::
Ryan Greenblatt lists the threats that AI control is meant to stop, and then ranks them. The ranking is the part to read closely: it says where a developer with a limited safety budget should spend it first, and Greenblatt argues for an ordering that puts an AI loose inside the company's own datacenter above an AI that has stolen its weights and escaped.

The post starts from a taxonomy by his colleague Buck Shlegeris, which sorts catastrophes by whether they involve a rogue deployment, a deployment of the AI where the safety measures are absent. You read that post in full later in [[../Lenses/XLab Control - rogue-deployments|AI catastrophes and rogue deployments]]. Greenblatt treats rogue deployments as one case inside a wider cluster.

Read to the end of the first section, then answer the recall questions from memory before reading on.

#### Article
source:: [[../articles/greenblatt-prioritizing-threats-for-ai-control]]
from:: "We often talk about ensuring control"
to:: "than like violating a security invariant."

#### Text
content::
\## Quick recall

Four short questions on the vocabulary of the section you just read. Answer each from memory, without scrolling back.

#### Question: Open
id:: 10bb7d59-2f6b-4d15-929b-91baefce1dae
content:: In the control literature, what does "ensuring control" mean?
assessment-instructions:: The learner has just read the opening of Greenblatt's post and is answering from memory. The answer has two halves, and both are required for full credit: preventing AIs from being able to cause existential problems, and that this holds even if the AIs actively attempt to subvert our countermeasures. An answer with only the first half is partial, because the adversarial clause is what separates control from alignment. Respond in at most three sentences: say plainly what was correct, name the missing half in one sentence if it is missing, then tell them to move on. This is a one-turn response. No re-teaching, no follow-up questions. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the reading on this page. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question.

#### Question: Open
id:: 1b9f5342-42e2-403a-b5ff-8b655b701517
content:: What is a rogue deployment?
assessment-instructions:: The learner is answering from memory after the first section of Greenblatt's post. Correct answer: a deployment of the AI in which the safety measures are absent. Accept equivalent wording (control measures, monitoring, safeguards not applied). Do not require the internal versus external distinction here; that is the next question but one. An answer that only gives an example (a scaffold that bypasses the monitor) without the general property is partial. Respond in at most three sentences, one turn only, no follow-up questions, no re-teaching. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the reading on this page. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question.

#### Question: Open
id:: a93b4b60-148b-4461-a70b-86b3caeae25c
content:: What is an internal security invariant? Give an example.
assessment-instructions:: The learner is answering from memory after the first section of Greenblatt's post. Full credit needs both a definition and an example. Definition: a well-defined security-related property of the AI company that is important to maintain. Example: any of the invariants the post names, such as "the monitoring system is always applied to AI agents used internally", "AI models are never run outside of developer servers", "AI agents are monitored at all times", "AI agents operate with X permissions", or "AIs aren't actively trained to evade monitors". A definition with no example, or an example with no definition, is partial; say which half is missing. Respond in at most three sentences, one turn only, no follow-up questions, no re-teaching. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the reading on this page. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question.

#### Question: Open
id:: acec1109-83ca-419a-971f-0c540aa0e88c
content:: What distinguishes an internal rogue deployment from an external one?
assessment-instructions:: The learner is answering from memory after the first section of Greenblatt's post. Correct answer: an internal rogue deployment runs on the company's own infrastructure, while an external one runs outside it. Self-exfiltration is the post's example of the external case. Accept answers that make the location distinction in other words. An answer that instead lists consequences (more compute, privileged access) has jumped ahead to a later question: credit the substance, but note that the defining difference is where the model runs. Respond in at most three sentences, one turn only, no follow-up questions, no re-teaching. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the reading on this page. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question.

#### Text
content::
Next, why this distinction changes what a monitoring system has to do, and then Greenblatt's ranked list of control priorities.

#### Article
from:: "## Concentrated vs non-concentrated failures"
to:: "Beyond rogue deployments, other security issues seem substantially less threatening."

#### Question: Open
id:: aadbfc12-4439-4bd2-9768-798cbcf402d9
content:: Why can a rogue internal deployment be worse than self-exfiltration?
assessment-instructions:: The learner has just read Greenblatt's argument for ranking rogue internal deployments first. The answer has two sides and full credit needs both. What the internal deployment has: much more compute (the post's example is a large fraction of the company's own compute, e.g. 25 percent) and privileged internal access, which together let it tamper with experiments, training runs, and the safety work being done inside the company. What the exfiltrated copy lacks: it would likely have far less compute by default and no privileged internal access, so it gets outraced by actors running similar models. An answer that names only the compute asymmetry, or only the tampering, is partial. Do not accept "it is inside the company" on its own; the point is what being inside buys the AI. Respond in at most four sentences, one turn only, no follow-up questions, no re-teaching. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the reading on this page. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question.

#### Text
content::
Greenblatt now justifies the rest of the ordering: why sabotage of safety-relevant work sits so high, and why the remaining side effects sit low.

#### Article
from:: "**Sabotaging work is also severe"

#### Question: Open
id:: 473e5571-dfd1-4ebb-8566-7c0e1ce1af1e
content::
\## Free response

Greenblatt's prioritization assumes a rushed but reasonable developer, one willing and able to spend something like a six-month pause on mitigating misalignment risk. Choose a different world: either very low political will (no meaningful pause is on the table), or high political will (a pause of more than five years looks likely). Re-derive the top three control priorities for your chosen world, and justify each departure from the original ordering. Engage with the two arguments the post itself leans on: what a rogue internal deployment is actually worth to a misaligned AI in your world, and how the value of preventing self-exfiltration depends on whether anyone was going to pause.

Write between 150 and 500 words.
assessment-instructions:: The learner has finished Greenblatt's post and is re-deriving his top three priorities for a world with a different level of political will. They must state which world they chose. Grade against three criteria, weighted equally, and name each one in your response.

1. Engages the post's arguments. The response uses the compute and privileged-access logic for rogue internal deployments, and the pause-dependence of self-exfiltration, rather than asserting a new ordering from scratch.
2. Conditions on the world. The priority changes actually follow from the chosen level of political will, rather than being asserted alongside it.
3. Acknowledges costs. The response says what the new ordering gains and what it gives up.

For calibration, the post's own conditional claims are: with lower will, getting useful and non-sabotaged work out (priority 2) should rise above preventing rogue internal deployments (priority 1), because preventing them might be infeasible; with higher will, preventing self-exfiltration (priority 3) could rise above getting useful work out (2), because self-exfiltration is less threatening if no substantial pause was coming anyway. A learner who argues to a different ordering is not wrong for that reason: judge whether the reasoning holds, not whether it matches Greenblatt. Do not reveal these conditional claims before the learner has answered.

Respond in 120 to 200 words, short paragraphs, no lists. Name the strongest move in their argument, then the criterion they served least well and the one concrete thing that would fix it. Do not over-validate. Avoid generic praise (great job, excellent analysis, well done). Grade only against this reading. If the learner says they do not understand, give one concrete foothold from the post, such as isolating a single priority and asking what changes about it when no pause is available, rather than repeating the prompt.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "Prioritizing threats for AI control." *Redwood Research blog*, 19 Mar. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/prioritizing-threats-for-ai-control)
*The assigned reading: three clusters of misalignment threats, a ranked list of control priorities, and the argument that a rogue internal deployment can be worse than self-exfiltration.*

Shlegeris, Buck. "AI catastrophes and rogue deployments." *Redwood Research blog*, 3 June 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/ai-catastrophes-and-rogue-deployments)
*The taxonomy Greenblatt starts from, which sorts catastrophes by whether they involve a rogue deployment.*

XLab. "Prioritizing threats for AI control." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/prioritizing-threats-for-ai-control)
*The source lesson this page adapts.*
:::
