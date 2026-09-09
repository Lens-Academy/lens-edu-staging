---
id: 'add4ddad-9fbf-486f-b5dc-c5f1af1114e8'
title: "A basic systems architecture for AI agents that do autonomous research"
tldr: "\"The machine the AI agent is running on\" usually names three machines, not one. The inference server holds the weights, the scaffold server runs the loop, the execution server runs the code. Buck Shlegeris draws that split, then redraws it to show where a weight exfiltration or a rogue deployment actually cuts in. Half the arguments about self-exfiltration turn out to be arguments about which box you meant."
summary_for_tutor: "A port of XLab's Paper-type lesson on Buck Shlegeris's post. XLab writes no framing of its own here: it renders the post in full and drops four Quick recall cards and one step-through diagram into it. Everything on this page is either the post itself (Article segments), one of XLab's four recall prompts turned into a graded open question, XLab's diagram rebuilt as a widget, or the short navigational lead-in we wrote, which is ours and is sourced only from the post's own opening. Sequence: lead-in, the post's introduction, two recall questions on the three-server split and on why \"the machine the agent runs on\" is ambiguous, the simplest design and the process flow, a recall question on where safety mechanisms sit, the notes on the design plus the extended design and the two compromise stories, a recall question on what rogue internal deployments look like concretely, the seven-step architecture widget, then the three alleged real-world examples. If a learner is confused about an attack path, ask which machine it starts on and which machine holds the weights."
reading_minutes: 30
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

This is the post that gives the rest of the high-stakes module something concrete to point at. [[../Lenses/XLab Control - rogue-deployments|AI catastrophes and rogue deployments]] named the threat of an unauthorized agent running without your safety measures, and [[../Lenses/XLab Control - rogue-internal-deployments-via-external-apis|Rogue internal deployments via external APIs]] worked through one route to it. Here Buck Shlegeris draws the machines, so that "the AI hacked its own environment" becomes a claim about a specific box.

His main point, in his own words, is that three responsibilities "will almost surely be hosted on logically different computers, and probably on different physical machines": the inference server, the scaffold server, and the execution server. Keep that split in view while you read. Four recall checks and an interactive version of his diagram are spaced through the post.

#### Article
source:: [[../articles/shlegeris-a-basic-systems-architecture-for-ai-agents-that-do-autonomous-research]]
to:: but it has no advantages over any other external hacker.

#### Question: Open
id:: 39ba70b5-8859-4eb2-b795-dfe686ca3008
content:: From memory, name the three responsibilities Shlegeris says will almost surely live on different computers, and say in one line what each of them does.
assessment-instructions:: The learner has just read the opening of Buck Shlegeris's post and is doing a short recall check without looking back at the text. Full marks name all three and describe each correctly: the inference server, which hosts the LLM and serves the text-generation API; the scaffold server, which maintains the agent loop's state, meaning it repeatedly calls the inference server, parses the LLM response, and executes actions with the agent's tools; the execution server, where the agent runs code and sees its results. Award roughly a third of the marks per correct item, and take marks off when a responsibility is attached to the wrong server. The commonest error is putting the agent loop on the execution server. Reply in 40 to 100 words, short paragraphs only, no lists. Acknowledge what is correct without inflation, name what is missing in one sentence, and correct errors in one sentence. This is a one-turn response: do not re-teach, do not ask follow-up questions, and tell them to move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, do not dismiss it and do not repeat the question: give one concrete foothold from the reading, for example the passage about the Claude agent running on a laptop, and if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against what this page and earlier pages of this course supplied.

#### Question: Open
id:: a262c8fc-ff97-439e-9c1d-89a263f2ab86
content:: Shlegeris says people often talk about "the machine that the AI agent is running on". Why is that phrase ambiguous? Use his laptop example if it helps.
assessment-instructions:: The learner has just read the opening of Buck Shlegeris's post and is doing a short recall check without looking back at the text. Full marks say that inference, scaffolding, and execution can sit on different machines with very different access, so the phrase does not pick out one machine or one set of permissions. Credit the worked example: a Claude agent running on your laptop does its inference inside Anthropic's datacenter, which has access to the weights, but executes code on the laptop, which has no access to that datacenter, so the agent is in a poor position to exfiltrate its own weights and would have no advantage over any other external hacker if it tried to break in. An answer that only says "there are several machines" without connecting the split to differences in access is partial credit. Reply in 40 to 100 words, short paragraphs only, no lists. Acknowledge what is correct without inflation, name what is missing in one sentence, and correct errors in one sentence. This is a one-turn response: do not re-teach, do not ask follow-up questions, and tell them to move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, do not dismiss it and do not repeat the question: give one concrete foothold from the reading, for example asking where the weights are when Claude runs on a laptop, and if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against what this page and earlier pages of this course supplied.

#### Article
from:: A lot of the point of this post is to be able to say some of the content of
to:: Final results are communicated to the user.

#### Question: Open
id:: d583851b-5e59-47dd-a02c-39ce70608aa9
content:: Where in the agent loop is the natural place to insert safety mechanisms, and what can the system do once it is there?
assessment-instructions:: The learner has just read the process flow and is doing a short recall check without looking back at the text. Full marks locate the point precisely: in the scaffold, after it parses the LLM's proposed action and before that action is executed. Full marks also list what the scaffold can then do: query a weaker, trusted model about whether the action is acceptably safe, and depending on the answer execute the action, flag it for human review (which the post calls auditing), or discard it and select a new one, as in the defer-to-trusted strategy from AI Control: Improving Safety Despite Intentional Subversion. An answer that says only "in the scaffold" without the before-execution timing, or that lists the three responses without saying where they happen, is partial credit. Treat "on the inference server" or "on the execution server" as wrong and say why in one sentence. Reply in 40 to 100 words, short paragraphs only, no lists. Acknowledge what is correct without inflation, name what is missing in one sentence, and correct errors in one sentence. This is a one-turn response: do not re-teach, do not ask follow-up questions, and tell them to move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, do not dismiss it and do not repeat the question: give one concrete foothold from the reading, for example the step in the process flow where the scaffold parses a shell command, and if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against what this page and earlier pages of this course supplied.

#### Article
from:: ## Some things to notice about this design
to:: You could also have a rogue internal deployment via compromising one of the other services, e.g. this story where you compromise the internal deployment.

#### Question: Open
id:: 7a994269-695c-422f-8023-da7b9dfe8029
content:: In the inference/scaffold/execution-server architecture, what do rogue internal deployments concretely look like? Give as many of the specific versions as you can remember.
assessment-instructions:: The learner has just read the compromise section and is doing a short recall check without looking back at the text. Full marks give the easiest version, that the model writes its own agent loop on the execution machine, using the GPUs and weights it was given for its research task. Credit the second version, that the model builds a rogue scaffold on the execution machine which uses that machine's access to the inference server, and credit the learner for noting that this one seems easier to prevent because basic monitoring on the inference server should catch queries that are blatantly implementing unauthorized scaffolds. Credit the third version, compromising one of the other services with code the model commits. One version described correctly is partial credit; three is full marks. Reply in 40 to 100 words, short paragraphs only, no lists. Acknowledge what is correct without inflation, name what is missing in one sentence, and correct errors in one sentence. This is a one-turn response: do not re-teach, do not ask follow-up questions, and tell them to move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, do not dismiss it and do not repeat the question: give one concrete foothold from the reading, for example asking what the model would need in order to run an agent loop nobody authorized, and if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against what this page and earlier pages of this course supplied.

#### Text
content::
\## The same picture, one threat at a time

Shlegeris redraws his architecture for each compromise he describes. This version, adapted from XLab's, puts those redraws onto a single picture. Step through it and watch where each attack path starts, and which machine it has to reach.

#### Widget
source:: [[../widgets/xlab-control-agent-architecture-threats]]

#### Article
from:: ## Using this framework to discuss alleged examples of AIs modifying their own environments

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Shlegeris, Buck. "A basic systems architecture for AI agents that do autonomous research." *Redwood Research blog*, 26 Sept. 2024. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/a-basic-systems-architecture-for)
*The post this lesson assigns, also posted to LessWrong: the inference/scaffold/execution split, and each threat scenario redrawn as a compromise of a specific machine.*

XLab. "A basic systems architecture for AI agents that do autonomous research." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/systems-architecture)
*The source lesson this page adapts, including its four recall prompts and its step-through version of the architecture diagram.*
:::
