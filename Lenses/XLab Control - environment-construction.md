---
id: '8b575307-08f1-4b1f-bec9-86376b5aac78'
title: "Environment construction"
tldr: "Control evaluations usually assume the attack has to fit inside one episode. But a coding agent comes back to the same repository tomorrow. Lay the pipe in pull request one, open the valve in pull request five, and a monitor that only ever sees one diff is looking at innocent plumbing. A five-minute talk builds the setting that tests this, and the monitors mostly lose."
summary_for_tutor: "Imported from XLab's AI Control curriculum; preserve source framing. This is Module 4's environment-construction lesson, which opens the section on building high-stakes settings; it is not Module 3's Environments lesson, which surveys the settings that already exist. XLab's own page is only three things: a five-minute ControlConf talk by Asa Cooper Stickland (UK AISI) on a persistent-state control setting, one learning objective, and one optional reading (the ControlArena docs). All of those are ported verbatim or as links. The lead-in Text segment before the video is ours, drawn from the talk itself: the single-trajectory assumption, the five-PR Iterative VibeCoding setup with Sonnet 4.5 untrusted and GPT-4o trusted, and the three monitor types including the stateful link tracker. Sequence: lead-in, video, XLab's objective plus optional reading plus the pointer to the next lesson, works cited. There is no exercise on the XLab page and none was invented. If a learner asks which environments exist, send them to the Module 3 Environments lens rather than listing them here."
reading_minutes: 10
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Watch: Persistent state, a new control setting

Module 3 surveyed the [[../Lenses/XLab Control - environments|control environments that already exist]]. This section is about constructing one, and about why a good high-stakes setting is hard to construct.

Asa Cooper Stickland's ControlConf talk runs five minutes and is a worked example of the problem. Existing settings mostly assume an attack has to fit inside a single trajectory: the model is given a task, and whatever harm it does, it does before that episode ends. Real coding agents do not work that way. They return to the same repository across many episodes, so a red team can set something up in an early pull request and exploit it later, and a blue team gets more chances to catch suspicious behavior early and act on it. Which side that asymmetry favors is an empirical question, so the team built a setting to answer it: sequences of five pull requests in which an agent iteratively builds an app or CLI tool, with Sonnet 4.5 as the untrusted model and GPT-4o as the trusted one.

Watch for the environment attribute the whole result turns on: what the monitor is allowed to remember. Monitors that see only each pull request's diff, monitors that see the full trajectory, and a stateful link tracker that keeps notes across pull requests all behave differently, and the gap between attacks distributed across pull requests and attacks concentrated in the single best-positioned one survives even against monitor models far stronger than the agent being watched.

The talk ends by saying the paper is coming. It has since appeared as [Distributed Attacks in Persistent-State AI Control](https://arxiv.org/abs/2607.02514).

#### Video
source:: [[../video_transcripts/far-ai-asa-cooper-stickland-persistent-state-a-new-control-setting]]

#### Text
content::
\## Learning objectives

By the end of this section you will be able to:

- Analyze environment attributes for high stakes control, and explain why good high-stakes settings are hard to construct

\## Optional reading

- [ControlArena documentation](https://control-arena.aisi.org.uk/): a library for running AI Control experiments based on Inspect.

\## What follows in this section

The talk shows one setting being built and what it revealed. The next lesson is the general case, written by people who have built several:

- [[../Lenses/XLab Control - settings-for-high-stakes-control|Why it's hard to make settings for high-stakes control research]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Cooper Stickland, Asa. "Persistent state: A new control setting." *ControlConf*, FAR.AI, published 20 May 2026. [youtube.com](https://www.youtube.com/watch?v=rStQDpQLPyg)
*The talk this lesson assigns: why the single-trajectory assumption breaks for coding agents that keep working on the same repository, and what happens to monitors when it does.*

Hills, Josh, Ida Caspary, and Asa Cooper Stickland. "Distributed Attacks in Persistent-State AI Control." *arXiv*, July 2026. [arxiv.org](https://arxiv.org/abs/2607.02514)
*The paper the talk previews, with the full Iterative VibeCoding setting, the monitor comparison, and the ensemble results.*

UK AI Security Institute and Redwood Research. "ControlArena." *AI Security Institute*. [control-arena.aisi.org.uk](https://control-arena.aisi.org.uk/)
*Optional reading for this section: the Inspect-based library that control settings and protocols are built in.*

XLab. "Environment construction." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/environment-construction)
*The source lesson this page adapts.*
:::
