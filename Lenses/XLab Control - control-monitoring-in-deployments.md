---
id: 'a16e3303-5416-46c5-aeb6-6ada7356ae5d'
title: "Practical challenges of control monitoring in frontier AI deployments"
tldr: "Your bank can hold every card transaction for review, or wave them all through and check the ledger tomorrow. One choice costs speed, the other costs money, and which loss you can absorb depends on the fraud. Now run a thousand tellers at once, give the reviewer a day, and let the thief spread a single theft across nine of them. That is control monitoring at deployment scale."
summary_for_tutor: "Imported from XLab's AI Control curriculum; preserve source framing. XLab writes no framing of its own here: the page is the Lindner, Griffin, Korbak et al. paper (arXiv:2512.22154, Google DeepMind, UK AI Security Institute, Oxford) rendered whole, with no exercises. Everything except the opening Text segment and the Works cited callout is ours, and the opening segment is navigational plus orienting facts taken from the paper's own abstract, section 2 and section 3. Sequence: a lead-in placing the paper between the Ctrl-Z talk and the synchronous-monitors post, then the paper. The argument to hold onto: four deployment dynamics prior control work abstracted away (parallelism, latency, incremental attacks, partial incrimination), three monitoring protocols distinguished by when actions are blocked (fully-synchronous, semi-synchronous, asynchronous), a safety case sketch built from six claims and their defeaters, and four case studies. The paper explicitly does not assert its six claims hold in general and its case-study numbers are hypothetical; do not let a learner treat table 1's recommendations as measured results."
reading_minutes: 60
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

[[../Lenses/XLab Control - monitoring-and-mitigation|Monitoring and Mitigation]] opened this section with Redwood's bash-agent setting: one untrusted agent, one trusted monitor scoring each command, and a protocol deciding what to do when a command looks suspicious. This paper asks what happens to that picture when the deployment is real.

David Lindner, Charlie Griffin, Tomek Korbak and colleagues at Google DeepMind, the UK AI Security Institute and the University of Oxford name four dynamics that prior control work abstracted away: thousands of agent instances acting in parallel, oversight that takes seconds to days rather than happening instantly, attacks that make partial progress across instances sharing an environment, and single suspicious actions that do not incriminate an agent well enough to justify permanent shutdown.

Out of those come the three protocols the paper compares, separated by when actions get blocked. **Fully-synchronous** monitoring blocks every instance while any flagged action awaits audit. **Semi-synchronous** blocks only the flagged instance. **Asynchronous** never blocks at all. Their worked example prices the difference: 1,000 parallel instances at 10 actions per hour, a monitor calibrated to a 1 percent false-positive rate and audits taking an hour leave fully-synchronous monitoring at roughly 1 percent system availability, semi-synchronous at 91 percent, and asynchronous at 100 percent.

The rest is a safety case sketch, a structured argument for the safety of a deployment. It rests on six claims a deployer would have to establish (monitor recall, human recall, oversight latency, harm latency, harm prevention, and reversibility of partial attacks), on the defeaters that break a particular protocol when one of those claims fails, and on four case studies applying the sketch to weight exfiltration, training-data poisoning, research sabotage, and secret exfiltration. The authors say plainly that they do not assert those claims hold in general, and that the case studies are hypothetical: the latency estimates and detection rates would need empirical validation for any real deployment.

Sections 1 to 6 carry the argument. The appendices, which the paper introduces as more detailed accounts of arguments the main text already makes, hold the formal versions: the extrapolation from per-attempt catch rate to whole-deployment risk, a concrete safety case subtree for weight exfiltration, the availability model behind the numbers above, and the coordination dynamics between instances. Read them for the mathematics, not for the conclusions.

The next lesson, [[../Lenses/XLab Control - synchronous-monitors|Blocking live failures with synchronous monitors]], takes one slice of this question and asks which threats make the latency cost of a blocking monitor worth paying.

#### Text
content::
:::callout {title="Reading not yet available" tone="amber"}
The reading for this lesson is being imported and is not on Lens yet. Until it
lands, read it at the original source: [Practical challenges of control monitoring in frontier AI deployments](https://arxiv.org/abs/2512.22154).
:::
{>>{"author":"Elias's AI","timestamp":1789039792881}@@PORT-TODO: replace this callout with `#### Article` over
`Lens Edu/articles/lindner-practical-challenges-of-control-monitoring-in-frontier-ai-deployments.md` once the import lands.<<}

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Lindner, David, Charlie Griffin, Tomek Korbak, Roland S. Zimmermann, Geoffrey Irving, Sebastian Farquhar, et al. "Practical Challenges of Control Monitoring in Frontier AI Deployments." *arXiv*, Dec. 2025. [arxiv.org](https://arxiv.org/abs/2512.22154)
*The paper this lesson assigns: the four deployment dynamics that break simplified control monitoring, the synchronous, semi-synchronous and asynchronous protocols, the safety case sketch and its six claims, and four case studies pricing each protocol against a different attack vector.*

XLab. "Practical challenges of control monitoring in frontier AI deployments." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/control-monitoring-in-deployments)
*The source lesson this page adapts.*
:::
