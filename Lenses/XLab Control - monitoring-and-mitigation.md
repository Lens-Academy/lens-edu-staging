---
id: 'f22e9aae-47ce-4cab-8ca7-70fa4a67055b'
title: "Monitoring and Mitigation"
tldr: "A bank with no lock lets a thief stroll in. Put a lock on it and even a thief who picks it leaves you footage of someone picking a lock. That is the shape of the protocol in this talk: when a command looks suspicious, do not run it and do not give up on it, ask the model again. Three suspicious answers in a row incriminate far better than one."
summary_for_tutor: "The opening lens of the monitoring-and-mitigation section of Module 4. It is a single 22-minute ControlConf talk by Aryan Bhatt on Redwood Research's Ctrl-Z work: the multi-step bash-agent control setting, the execute/replace/audit framework, defer-to-trusted as the baseline, and defer-to-resample plus time travel as the new protocols the agent setting makes possible. Sequence: a short lead-in naming the setting, the talk, then XLab's learning objectives for the whole section and pointers to the three readings that follow. The paper itself is a separate lens; if the student wants the numbers and the full protocol, send them there rather than re-deriving it from the talk."
reading_minutes: 30
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Watch: Ctrl-Z, controlling AI agents via resampling

This section is about what you actually do once a monitor fires. Aryan Bhatt's ControlConf talk runs 22 minutes, with audience questions along the way, and lays out the setting Redwood Research built to study it: an untrusted model driving a bash shell through multi-step sysadmin tasks, a weaker trusted model scoring every command for suspicion, and a red team whose job is to get malware downloaded and executed without any single command looking suspicious enough to be audited.

The talk previews the paper you read later in this module, [[../Lenses/XLab Control - ctrl-z-resampling|Ctrl-Z: Controlling AI Agents via Resampling]]. Watch for the move at the heart of it: a suspicious action does not have to be either executed or replaced by a weaker model's action. It can simply be sampled again.

#### Video
source:: [[../video_transcripts/far-ai-aryan-bhatt-ctrl-z-controlling-ai-agents-via-resampling-controlconf]]

#### Text
content::
\## Learning objectives

By the end of this section you will be able to:

- Compare synchronous, semi-synchronous, and asynchronous monitoring, and analyze their latency-safety tradeoffs in frontier deployments
- Identify the oversight, latency, and recovery challenges that deployment-scale monitoring must solve
- Evaluate resampling protocols and their safety-usefulness tradeoffs in agentic high-stakes settings

\## What follows in this section

The talk is the overview. The rest of the section works through the same ground in detail:

- [[../Lenses/XLab Control - control-monitoring-in-deployments|Practical challenges of control monitoring in frontier AI deployments]]
- [[../Lenses/XLab Control - synchronous-monitors|Blocking live failures with synchronous monitors]] (optional)
- [[../Lenses/XLab Control - ctrl-z-resampling|Ctrl-Z: Controlling AI Agents via Resampling]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Bhatt, Aryan. "Ctrl-Z: Controlling AI Agents via Resampling." *ControlConf*, FAR.AI, published 8 May 2025. [youtube.com](https://www.youtube.com/watch?v=A3MRmG9NSKY)
*The talk this lesson assigns: Redwood Research's multi-step agent control setting, and the resampling protocols that beat deferring to a trusted model.*

XLab. "Monitoring and Mitigation." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/monitoring-and-mitigation)
*The source lesson this page adapts.*
:::
