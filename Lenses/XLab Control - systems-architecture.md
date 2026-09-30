---
id: 'add4ddad-9fbf-486f-b5dc-c5f1af1114e8'
title: "A basic systems architecture for AI agents that do autonomous research"
tldr: "\"The machine the AI agent is running on\" usually names three machines, not one. The inference server holds the weights, the scaffold server runs the loop, the execution server runs the code. Buck Shlegeris draws that split, then redraws it to show where a weight exfiltration or a rogue deployment actually cuts in. Half the arguments about self-exfiltration turn out to be arguments about which box you meant."
summary_for_tutor: "A port of a Paper-type lesson on Buck Shlegeris's post. The source writes no framing of its own here: it renders the post in full and drops four Quick recall cards and one step-through diagram into it. Everything on this page is either the post itself (Article segments), one of the source's four recall prompts turned into a graded open question, its diagram rebuilt as a widget, or the short navigational lead-in we wrote, which is ours and is sourced only from the post's own opening. Sequence: lead-in, the post's introduction, two recall questions on the three-server split and on why \"the machine the agent runs on\" is ambiguous, the simplest design and the process flow, a recall question on where safety mechanisms sit, the notes on the design plus the extended design and the two compromise stories, the post's last compromise diagram as a static image (malicious commands from the execution server set up a rogue scaffold with local inference inside the inference server, reading the weights directly; the article's own link to this image is dead, and the widget below does not draw this story), a recall question on what rogue internal deployments look like concretely, the architecture widget, where the learner switches between seven views of Shlegeris's diagram and the post supplies the reasoning around it, then the three alleged real-world examples. If a learner is confused about an attack path, ask which machine it starts on and which machine holds the weights. After the widget, one added practice question (ours, in an amber callout) has the learner find rogue-deployment routes in a different architecture and say whether request logging at the inference provider would catch them; its model answer is in the assessment instructions."
reading_minutes: 35
tutor_minutes: 6
tags: []
---
#### Text
content::
\## Before you read

This is the post that gives the rest of this unit something concrete to point at. [[../Lenses/XLab Control - rogue-deployments|AI catastrophes and rogue deployments]] named the threat of an unauthorized agent running without your safety measures, and [[../Lenses/XLab Control - rogue-internal-deployments-via-external-apis|Rogue internal deployments via external APIs]] worked through one route to it. Here Buck Shlegeris draws the machines, so that "the AI hacked its own environment" becomes a claim about a specific box.

His main point, in his own words, is that three responsibilities "will almost surely be hosted on logically different computers, and probably on different physical machines": the inference server, the scaffold server, and the execution server. Keep that split in view while you read. Four recall checks and an interactive version of his diagram are spaced through the post.

#### Article
source:: [[../articles/shlegeris-a-basic-systems-architecture-for-ai-agents-that-do-autonomous-research]]
to:: but it has no advantages over any other external hacker.

#### Question: Open
id:: 39ba70b5-8859-4eb2-b795-dfe686ca3008
content:: From memory, name the three responsibilities Shlegeris says will almost surely live on different computers, and say in one line what each of them does.
assessment-instructions:: Score out of 100. 30: inference, 10 for naming it and 20 for its job: it hosts the model (its weights) and serves the text-generation API. 40: scaffold, 10 for naming it and 30 for its job: it runs the agent loop, repeatedly calling the inference server, parsing the model's response and carrying out the actions with the agent's tools. 30: execution, 10 for naming it and 20 for its job: it is where the agent's code actually runs and where it sees the results. Give credit for each point whenever the answer shows the idea, in any wording. A job attached to the wrong server earns nothing for that job (the common slip is putting the agent loop on the execution server). Model answer, for the feedback, not a grading checklist: "The inference server, which hosts the LLM and serves the text-generation API; the scaffold server, which maintains the agent loop's state, involving repeatedly calling the inference server, parsing the LLM response, and executing actions with the agent's tools; the execution server, where the agent runs code and sees its results."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: a262c8fc-ff97-439e-9c1d-89a263f2ab86
content:: Shlegeris says people often talk about "the machine that the AI agent is running on". Why is that phrase ambiguous? Use his laptop example if it helps.
assessment-instructions:: Score out of 100. 50: inference, scaffolding and execution can each run on a different machine, so the phrase could mean any of them. 50: those machines have very different access (for example only the datacentre running inference holds the model's weights), so which machine is meant changes what the agent could do there. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Because inference, scaffolding, and execution can be on different machines with very different access. For example, a Claude agent on your laptop does inference inside Anthropic's datacenter (which has weight access), but executes code on the laptop."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: A lot of the point of this post is to be able to say some of the content of
to:: Final results are communicated to the user.

#### Question: Open
id:: d583851b-5e59-47dd-a02c-39ce70608aa9
content:: Where in the agent loop is the natural place to insert safety mechanisms, and what can the system do once it is there?
assessment-instructions:: Score out of 100. 50: where, 20: in the scaffold, and 30: after the model's proposed action has been parsed and before it is executed. 50: what it can do there, 20: ask a weaker, trusted model whether the action is acceptably safe, and 30, 10 each: depending on the answer, execute the action, flag it for human review (auditing), or discard it and get a new one. Give credit for each point whenever the answer shows the idea, in any wording. Placing the check on the inference server or the execution server earns nothing for "where". Model answer, for the feedback, not a grading checklist: "In the scaffold, after it parses the LLM's proposed action and before executing it. The scaffold can query a weaker trusted model about whether the action is acceptably safe, then execute it, flag it for human review, or discard it and select a new one."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: ## Some things to notice about this design
to:: You could also have a rogue internal deployment via compromising one of the other services, e.g. this story where you compromise the internal deployment.

#### Text
content::
![Shlegeris's diagram of a rogue internal deployment via a compromised inference server. The user sends tasks to the scaffold, which talks to the inference server and the execution server as usual. A red arrow labelled "Malicious commands" runs from the execution server back over the scaffold into the inference server, where a red "Rogue scaffold" box drives a red "Local inference" box that reads the model weights directly, so the rogue agent runs inside the inference server and never passes through the real scaffold's safety checks.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/shlegeris-sysarch-rogue-deployment-via-inference-server.png)

#### Question: Open
id:: 7a994269-695c-422f-8023-da7b9dfe8029
content:: In the inference/scaffold/execution-server architecture, what do rogue internal deployments concretely look like? Give as many of the specific versions as you can remember.
assessment-instructions:: Score out of 100. 50: the easiest version: the model writes its own agent loop on the execution machine and runs itself there with the GPUs and weights it was given for its research, outside the real scaffold and its safety checks. 25: a rogue scaffold on the execution machine that still calls the inference server. 25: compromising one of the other services (the scaffold or the inference server) through code the model commits. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The model writes its own agent loop on the execution machine, using that machine's GPUs/weights. It can also build a rogue scaffold on the execution machine that calls the inference server (easier to catch with basic monitoring on the inference API), or compromise one of the other services via code it commits."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## The same picture, one threat at a time

Shlegeris redraws his architecture for each compromise he describes. This version puts those redraws onto a single picture. Switch between the seven views and watch where each attack path starts, and which machine it has to reach.

#### Widget
source:: [[../widgets/xlab-control-agent-architecture-threats]]

#### Callout: Practice: a different architecture
tone:: amber

#### Question: Open
id:: 0fc4ec6a-1baf-43e3-9d45-c26a9884dece
content:: A new case. A small lab rents inference for its model from a cloud vendor, which logs every request. The agent loop and the code the agent runs are both on one researcher's workstation, which also holds a fine-tuned copy of the model's weights for evaluation runs, has a GPU, and has ordinary internet access. The lab's only safety measure is a check in the agent loop that holds suspicious commands for the researcher to approve.

(a) Name two ways the model could come to run without these measures applying. For each, say where it starts and which measure it gets around.
(b) Would the vendor's request logging catch either of them? Why or why not?
placeholder:: Answer (a) and (b)
assessment-instructions:: Score out of 100. (a) 60: two ways the model could run without the approval check, 30 each: 15 for a sound route, 10 for where it starts (which machine and what it uses there) and 5 for which measure it gets around. Any sound route counts, for example its own loop on the workstation running the local weights, code that modifies or restarts the existing loop to drop the check, copying the local weights out over the internet, or a second loop that calls the vendor but skips the check. (b) 40: 10 for "mostly no" and 30 for the reason: the vendor only sees requests sent to it, so routes using the local weights, a modified loop or copied-out weights leave nothing in its logs, and only a rogue loop that still calls the vendor would appear, and then only if someone looks. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "(a) Any two of: the model writes its own agent loop on the workstation that runs the local weight copy on the GPU, so its commands never pass the approval check and its queries never reach the vendor; because the agent loop runs on the same machine as the agent's code, the model's code can modify or restart the loop itself and switch the check off; the model copies the local weights out over the internet and has them run elsewhere, which gets around every measure; a second loop on the workstation that still calls the vendor but skips the approval check. (b) Mostly no: the vendor sees only requests sent to it, so a loop running the local weights, a modified loop, or copied-out weights produce nothing in its logs; only a rogue loop that still calls the vendor would show up, and then only if someone reads the logs for that."
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed. If they missed that the loop and the code share a machine, say plainly that code running there can change the loop and its check. No follow-up question. No generic praise.

#### End Callout

#### Article
from:: ## Using this framework to discuss alleged examples of AIs modifying their own environments

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Shlegeris, Buck. "A basic systems architecture for AI agents that do autonomous research." *Redwood Research blog*, 26 Sept. 2024. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/a-basic-systems-architecture-for)
*The post this lesson assigns, also posted to LessWrong: the inference/scaffold/execution split, and each threat scenario redrawn as a compromise of a specific machine.*

XLab. "A basic systems architecture for AI agents that do autonomous research." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/systems-architecture)
*The source lesson this page adapts.*
:::
