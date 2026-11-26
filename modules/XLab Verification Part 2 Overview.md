---
id: '296052aa-6452-4f7a-b498-31d5fc26a2d5'
slug: xlab-verification-p2-overview
title: "Course Overview"
tags: [wip]
---

# Lens: About This Course
id:: 65e6f4de-e791-4945-ae34-b7879238e00d
tldr:: The first course argued that a slowdown agreement would have to be checkable. This one is about the checking: what cloud records, satellites, insiders and inspections can truly prove, and what a determined evader does to each of them.
summary_for_tutor:: Orientation lens for the second course in the compute verification pair. The learner reads what these five units cover, that the first course is a prerequisite, that the capstone is a separate course afterwards which begins with the feasibility judgments, and that the course is built on an open-source curriculum whose authors take feedback through a form linked there. Do not teach later content in detail. If asked, point to the unit that covers it. If a learner has not done the first course, say plainly that this one starts from its results (mechanism criteria, the actors and supply chain, and the hardware mechanisms) and does not restate them.
reading_minutes:: 4
tutor_minutes:: 0
#### Text
content::
\## What this course is about

How could parties that do not trust one another verify meaningful limits on advanced AI development? The first course worked from motivation to policy scope: why verification matters, what a pause agreement needs to say, who is bound by it, and what hardware can attest to. This course is about the evidence. The first three units each take one stream of it and ask what claims it can support and what it cannot establish on its own. The last two put the picture under adversarial pressure: a full technical verification architecture read closely, and the routes a determined actor would take around it. We built this course on the open-source verification curriculum of [XLab](https://xrisk.uchicago.edu/) at the University of Chicago. To send feedback directly to XLab, use [their feedback form](https://forms.gle/KkWcHkKh87pygDzw9).

:::callout {title="This course continues another one" tone="blue"}
The first course, Compute Verification 1, is a prerequisite. This one starts from its results and does not restate them: the criteria for judging a mechanism, the actors and chokepoints of the compute supply chain, and the hardware mechanisms up to and including chip attestation and compute accounting. The capstone is a separate course that follows this one. It opens with the feasibility judgments, where you rank the mechanisms you have now read about and defend the ranking, and builds from there to a verification regime of your own design.
:::

\## The path

:::callout {title="Unit 6: Hardware Judgment and Cloud Records" tone="blue"}
Where does hardware verification fit in practice, as opposed to where a demo suggests it stands? You separate maturity stages, write a hardware assurance brief for a delegation weighing a three-month pause, and then turn to the cloud: what a provider's own billing, identity and workload records can prove about a training run, and how know-your-customer rules from finance were transferred to compute.
:::

:::callout {title="Unit 7: Cloud Limits and Intelligence" tone="blue"}
Discover where cloud oversight runs out, and what can be seen without the other side's cooperation. You work through detection gaps and the geopolitics of cloud controls, drill the habit of stopping at what a record proves, then take up intelligence: the observable signatures of an undeclared training run, the historical record of who found undeclared facilities, how a signal becomes an assessment, and a treaty that protects sensors but obliges nobody to share what they see. You red-line that text yourself.
:::

:::callout {title="Unit 8: The Human Layer" tone="blue"}
Explore the cheapest verification tools to deploy and the easiest to fool. Start with who could know, whether they would tell, and what an institution can conclude from what they say: insiders and source credibility, whistleblower statutes and the route a report has to survive. This is followed by a look at audits and inspections and the access ceiling on any finding. Finally, answer the institutional question of who finds, who judges, who enforces, and against what standard.
:::

:::callout {title="Unit 9: Covert Development and the Low-Trust Architecture" tone="blue"}
Turn to the perspective of the adversary, then one long close reading. First a worked case: an evasion built by a red team and taken apart by a blue team, with the standard that operations are made inconclusive rather than invisible. Then a published working paper that proposes a full technical system for verifying AI compute use between parties who do not trust each other. You reconstruct its argument, trace evidence from chip to verdict, and deeply analyze one part of your choice.
:::

:::callout {title="Unit 10: Evasion Routes and the Red Team Review" tone="blue"}
Why defining cheating comes before detecting it, why layered defenses only work when the layers fail differently, and a taxonomy of ten routes around an agreement. The unit ends in the written output the course builds to: an expert review deciding which obligations of a draft treaty the verification system from Unit 9 could feasibly carry, and which it cannot.
:::
