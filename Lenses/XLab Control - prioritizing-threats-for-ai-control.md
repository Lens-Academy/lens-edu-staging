---
id: 'a73924bf-90e1-4be3-b930-79e72de8b71f'
title: "Prioritizing threats for AI control"
tldr: "Rank the ways a misaligned AI could hurt you: break your security invariants, sabotage the work you asked for, or cause trouble on the side. Ryan Greenblatt puts an AI running unmonitored inside your own datacenter above one that stole its weights and fled. The escapee took a copy of the model. The intruder has your compute, your permissions, and your experiments."
summary_for_tutor: "Unit 3 of AI Control 1. The reading is Ryan Greenblatt's 'Prioritizing threats for AI control', embedded as three excerpts of the imported article. Excerpt 1 gives the three threat clusters; four quick-recall questions then check the vocabulary (ensuring control, rogue deployment, internal security invariant, internal versus external rogue deployment). Excerpt 2 covers concentrated versus non-concentrated failures and Greenblatt's ranked priority list; one recall question then asks why a rogue internal deployment can be worse than self-exfiltration. Excerpt 3 is Greenblatt's justification of the ranking, followed by a 150 to 500 word free response that asks the learner to re-derive the top three priorities under a different level of political will. The recall answers and the free-response criteria come from the source material. Do not hand the learner the priority list or the model answers; make them argue from the compute and privileged-access logic and from the pause-dependence of self-exfiltration."
reading_minutes: 35
tutor_minutes: 5
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
assessment-instructions:: Score out of 100. 40: making sure AIs are not able to cause catastrophic (existential) outcomes. 60: this has to hold even if the AIs are actively trying to subvert the countermeasures, so it does not rely on the AIs being aligned. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Preventing AIs from being able to cause existential problems, even if the AIs attempt to subvert our countermeasures."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: 1b9f5342-42e2-403a-b5ff-8b655b701517
content:: What is a rogue deployment? Give an example.
assessment-instructions:: Score out of 100. 55: the safety measures (monitoring and other control measures) are absent or bypassed. 20: it is still the AI actually running and working, a deployment of it, only without those measures around it. 25: an example that fits, such as the AI running itself through a scaffold of its own that bypasses the monitor. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer gives only an example without the general property that the safety measures are absent. Model answer, for the feedback, not a grading checklist: "A deployment of the AI where the safety measures are absent. For example, the model's weights are stolen and run on outside servers, or the AI launches an unmonitored copy of itself on the lab's own cluster."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: a93b4b60-148b-4461-a70b-86b3caeae25c
content:: What is an internal security invariant? Give an example.
assessment-instructions:: Score out of 100. 60: the definition, 40: a well-defined security property of the AI company, such as how and where its AI systems may run, and 20: one that is important to maintain. 40: a fitting example, such as "the monitoring system is always applied to AI agents used internally", "AI models are never run outside of developer servers", "AI agents operate with X permissions" or "AIs aren't actively trained to evade monitors". Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A well-defined security-related property of the AI company that is important to maintain. For example, "the monitoring system is always applied to AI agents used internally.""
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: acec1109-83ca-419a-971f-0c540aa0e88c
content:: What distinguishes an internal rogue deployment from an external one?
assessment-instructions:: Score out of 100. The defining difference is where the rogue deployment runs, 50: an internal one runs on the AI company's own infrastructure (its datacenter), and 50: an external one runs outside it, for example after the model has exfiltrated its weights to an outside server. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the answer names only consequences of the difference, such as more compute or privileged access, without saying where each one runs. Model answer, for the feedback, not a grading checklist: "An internal rogue deployment runs on the company's own infrastructure while an external one runs outside it."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Text
content::
Next, why this distinction changes what a monitoring system has to do, and then Greenblatt's ranked list of control priorities.

#### Article
from:: "## Concentrated vs non-concentrated failures"
to:: "Beyond rogue deployments, other security issues seem substantially less threatening."

#### Question: Open
id:: aadbfc12-4439-4bd2-9768-798cbcf402d9
content:: Why can a rogue internal deployment be worse than self-exfiltration?
assessment-instructions:: Score out of 100. 55: what the internal rogue deployment has, 20: access to a lot of compute (for example a large fraction of the company's own), 15: privileged internal access or escalated permissions, and 20: what that lets it do: tamper with experiments, training runs and the safety work being done inside the company, or use the compute unmonitored for its own ends. 45: what the exfiltrated copy lacks, 30: it would likely have far less compute and no privileged internal access, and 15: so it could be outraced by other actors running similar models and cannot interfere with work inside the company. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 20 if the answer says only that the internal deployment is inside the company, without saying what being inside gives it. Model answer, for the feedback, not a grading checklist: "It has more compute and privileged internal access & as a result, it gains the ability to tamper with experiments, training runs, and safety work inside the company. An exfiltrated model would likely have much less compute and no privileged internal access."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

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

feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

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
