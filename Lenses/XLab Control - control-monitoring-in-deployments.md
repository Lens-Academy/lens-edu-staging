---
id: 'a16e3303-5416-46c5-aeb6-6ada7356ae5d'
title: "Practical challenges of control monitoring in frontier AI deployments"
tldr: "Your bank can hold every card transaction for review, or wave them all through and check the ledger tomorrow. One choice costs speed, the other costs money, and which loss you can absorb depends on the fraud. Now run a thousand tellers at once, give the reviewer a day, and let the thief spread a single theft across nine of them. That is control monitoring at deployment scale."
summary_for_tutor: "The source lesson writes no framing of its own here: the page is the Lindner, Griffin, Korbak et al. paper (arXiv:2512.22154, Google DeepMind, UK AI Security Institute, Oxford) rendered from the abstract to the end of section 6 (appendices collapsed), with one added practice question. Everything except the opening Text segment, the added practice question and the Works cited callout is the paper's, and the opening segment is navigational plus orienting facts taken from the paper's own abstract, section 2 and section 3. Sequence: a lead-in placing the paper between the Ctrl-Z talk and the synchronous-monitors post, then the paper. The argument to hold onto: four deployment dynamics prior control work abstracted away (parallelism, latency, incremental attacks, partial incrimination), three monitoring protocols distinguished by when actions are blocked (fully-synchronous, semi-synchronous, asynchronous), a safety case sketch built from six claims and their defeaters, and four case studies. The paper explicitly does not assert its six claims hold in general and its case-study numbers are hypothetical; do not let a learner treat table 1's recommendations as measured results. After the paper, one added practice question (ours, in an amber callout) has the learner estimate availability under the three protocols for a different deployment, choose one against a fast, irreversible harm, name a way it could still fail, and say whether the choice changes for a slow, reversible harm; its model answer is in the assessment instructions."
reading_minutes: 65
tutor_minutes: 3
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

#### Article
source:: [[../articles/lindner-practical-challenges-of-control-monitoring-in-frontier-ai-deployments]]
from:: Automated control monitors could play an important role in overseeing highly capable AI agents that we do not fully trust.
to:: when human red-teams are unlikely to find attack vectors that dominate an AI’s attacks.
{>>{"author":"Elias's AI","timestamp":1789039792881}@@PORT-TODO: replace this callout with `#### Article` over
`Lens Edu/articles/lindner-practical-challenges-of-control-monitoring-in-frontier-ai-deployments.md` once the import lands.<<}

#### Callout: Practice: when to block
tone:: amber

#### Question: Open
id:: 72741e7e-6943-422c-bfef-10318040c4de
content:: A new case. A lab runs 50 parallel instances of an untrusted agent, each taking about 12 actions per hour. A monitor flags 2% of normal actions, and an audit takes about 30 minutes. The harm the lab worries about most: an instance sends details of an unreleased model to an outside mailing list, which takes one action and a few seconds, and cannot be recalled once sent.

(a) Roughly what share of the time can an instance work under fully-synchronous, semi-synchronous and asynchronous monitoring, ignoring attacks?
(b) Which of the three would you use against this harm, and why?
(c) Name one way your choice could still fail to prevent the harm.
(d) Would your choice change if the harm instead took a week to take effect and could be undone? Why?
placeholder:: Show your working for (a), then answer (b) to (d)
assessment-instructions:: This is practice on a new case, applying the paper's availability example and safety case sketch. Model answer. (a) Flags across all instances: 50 times 12 times 0.02, about 12 per hour. Fully-synchronous pauses every instance for 30 minutes per flag, so about 6 hours of pauses arrive per hour and the system is almost always blocked: roughly 1/(1 + 6), about 14%. Semi-synchronous: each instance is flagged about 0.24 times per hour, once every 4.2 hours, and then paused half an hour: about 4.2 / 4.7, about 89%. Asynchronous: 100%. (b) Asynchronous monitoring cannot prevent this harm, because it takes seconds and cannot be undone, while the audit takes half an hour: the paper's "no harm latency" defeater. Semi-synchronous blocks the flagged action until the audit, at a modest cost; fully-synchronous adds protection against other instances acting meanwhile but costs most of the availability. Semi-synchronous, or fully-synchronous with the cost weighed, is a good answer. (c) For example: the monitor fails to flag the message (monitor recall); several instances try at once, so one unflagged attempt goes out while another is under audit (a coordinated attack); the auditor fails to recognise the attack. (d) Yes: with a week before harm and a way to undo it, a half-hour audit finishes long before the harm lands, so asynchronous monitoring with recovery gives full availability; it still fails if the monitor or auditor misses the attack, if undoing is incomplete, or if the agent is kept running after a catch and keeps retrying. Full marks need roughly correct numbers (accept 10 to 20%, 85 to 92%, 100%), a choice justified by comparing harm speed and irreversibility with audit time, one sound failure mode, and a sound (d); roughly a quarter each. Grade only against these criteria and the material on this page.
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed, with the numbers. If they chose asynchronous monitoring, say plainly that the message is out long before a 30-minute audit ends and cannot be recalled. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Lindner, David, Charlie Griffin, Tomek Korbak, Roland S. Zimmermann, Geoffrey Irving, Sebastian Farquhar, et al. "Practical Challenges of Control Monitoring in Frontier AI Deployments." *arXiv*, Dec. 2025. [arxiv.org](https://arxiv.org/abs/2512.22154)
*The paper this lesson assigns: the four deployment dynamics that break simplified control monitoring, the synchronous, semi-synchronous and asynchronous protocols, the safety case sketch and its six claims, and four case studies pricing each protocol against a different attack vector.*

XLab. "Practical challenges of control monitoring in frontier AI deployments." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/control-monitoring-in-deployments)
*The source lesson this page adapts.*
:::
