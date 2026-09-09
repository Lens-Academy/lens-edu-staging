---
id: '38668f27-58ab-471b-bf38-1d58168da22f'
title: "What is High Stakes?"
tldr: "Two axes and one picture. Plot a deployment by how incriminating each of the model's actions is against how many actions a catastrophe takes, and \"high stakes\" stops being a vibe and becomes a region on a graph: the corner where only a few large, hard-to-explain moves are needed. Build that graph region by region, then watch the diagonal appear."
summary_for_tutor: "Imported from XLab's AI Control curriculum, Module 4 (High-stakes control); preserve source framing. The opening lens of the high-stakes section proper, sitting after the roadmap talk. It has three parts. First, Mary Phuong's fifteen-minute FAR.AI talk as a general orientation to AI control: misalignment as a threat model, the shift to agentic internal deployments, and the four components she names (automated monitoring, an escalation process, ordinary security and system design, control evaluations). Second, XLab's definition of high stakes and the control graph widget, a five-step build-up of the two axes, the two bands, the two off-band corners, and the inverse correlation between them. Third, the section's learning objectives, which point forward to the rogue-deployment and systems-architecture lessons later in the module. There are no exercises in the source and nothing here is graded. If a learner asks where some scenario sits, ask them the two axis questions rather than answering: how incriminating is each action, and how many actions does the catastrophe take?"
reading_minutes: 30
tutor_minutes: 0
tags: []
---
#### Text
content::
Mary Phuong's talk is a fifteen-minute orientation to AI control as a whole: why misalignment is worth planning around, what changes when a lab deploys agents internally instead of routing their work through a human, and the four components she expects a control system to need. Watch it first. The rest of this page narrows all of that down to one question: how many actions does a catastrophe take?

#### Video
source:: [[../video_transcripts/far-ai-mary-phuong-ai-control-addressing-risks-from-agentic-internal-deployments-technical-ai-policy]]

#### Text
content::
\## Defining high stakes

We can think about what is "High Stakes" as what catastrophically threatening occurrences take the least amount of actions to produce.

#### Widget
source:: [[../widgets/xlab-control-high-stakes-graph]]

#### Text
content::
It is intuitive to think that incrimination and number of actions are inversely correlated, since as the number of actions decrease while the catastrophic occurrences remains the same, the size and impact of each action must grow proportionally. High impact actions may require breaking more safeguards, cost more reasoning expenditure and overall require the model to try harder to do a bad thing in less actions. These high impact actions are therefore more incriminable, since it would be harder to produce reasons against a model not scheming when it does incredibly large actions.

:::callout {title="Terms used on this page" tone="neutral" collapse="closed"}
**Scheming.** Schemers are AIs that eventually take substantial material action (control subversion, research sabotage) and manipulate their training procedures (alignment faking, sandbagging) to gain long-term power over their developers in service of pursuing their misaligned goals. Definition from [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|The case for ensuring that powerful AIs are controlled]].

**Rogue deployment.** A deployment of an AI in which the intended safety measures are absent, like after the model escalates its own permissions inside the lab, or when it runs on exfiltrated weights outside the lab.

**Exfiltration.** An AI getting a copy of its own weights out of the developer's control so it can run and act without the lab's safety measures. Also called self-exfiltration or weight exfiltration.
:::

#### Text
content::
\## Learning objectives

By the end of this section you will be able to:

- Define high stakes as opposed to low stakes using the control graph.
- Classify catastrophes by whether they route through a rogue deployment, and distinguish internal rogue deployments from external ones such as weight exfiltration.
- Recognize subtler rogue-deployment variants, such as a monitored internal agent querying an unmonitored external copy of itself.
- Describe the basic systems architecture of an autonomous research agent, and locate where its permissions and monitoring live.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Phuong, Mary. "AI Control: Addressing Risks from Agentic Internal Deployments." *Technical AI Policy*, FAR.AI. [youtube.com](https://www.youtube.com/watch?v=RS6UyRXKnqs)
*A fifteen-minute overview of AI control: the misalignment threat model, the shift to agentic internal deployments, and the four components of a control system.*

Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The post the definition of scheming on this page is taken from, and the origin of the control framing the graph formalises.*

XLab. "What is High Stakes?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/what-is-high-stakes)
*The source lesson this page adapts, including the control graph.*
:::
