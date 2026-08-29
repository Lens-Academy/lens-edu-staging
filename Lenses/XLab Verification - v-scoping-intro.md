---
id: 'a437d1e1-46b1-4677-bb9c-b2358b02143c'
title: "1.0 Introduction: what kind of policy are we trying to verify?"
tldr: "A goal like 'prevent premature ASI' cannot be inspected. A treaty turns it into a rule, and a rule into a claim someone can check: who did what, with which objects, under which conditions. Learn the four ingredients, watch Iraq slip through the gap between rule and claim, and meet the five kinds of agreement a verifier might be asked to police."
summary_for_tutor: "Reading-only lens, no questions. Opens with the module objectives, then teaches the goal, legal rule, verification claim ladder; the four ingredients of a claim (actors, objects, activities, conditions); rules and claims as proxies that Goodhart's Law erodes; the NPT and Iraq example of a claim that missed undeclared material; and the Oxford AIGI taxonomy of five candidate agreement types with their risk-reduction versus cost trade. If the learner asks, help them decompose any policy into the three layers and four ingredients. Do not require agreement with the source."
tags: [wip]
duration_minutes: 5
---
#### Text
content::
Now that we have a grasp of the motivations and big-picture qualities of an AI verification regime, it’s time to turn to the specifics. What could a verifiable treaty actually look like—what provisions, requirements, suggestions, agreements should there be? Who are the relevant actors that the treaty depends upon, affects, constrains, and authorizes as verifiers?

:::callout {title="By the end of this module, you will be able to:" tone="blue"}
1. Decompose a policy into its fundamental parts (the goal, the legal rule, and the verification claim, with its actors, objects, activities, and conditions) and distinguish what a treaty leaves explicit vs. intentionally implicit.
2. Name the major public and private actors relevant to an international AI agreement, how they connect to each other, and locate each on the compute supply chain.
3. Characterize each actor’s incentive structure—to comply, defect, hide, exaggerate, or free-ride.
4. Explain why verifiability is highest upstream in the supply chain (concentrated hardware, physical chokepoints) and lowest downstream (diffuse deployment).
5. Identify the ambiguities, loopholes, and potential evasion strategies in real treaty provisions.
6. Produce actor-aware written analysis: a report or briefing that accounts for its context, taking into account who produced the underlying information, and who will consume the output.
:::

\## The Building Blocks of a Policy

Each policy has an ultimate goal, whether it be to slow global warming or pace the development of premature ASI. These goals are often abstract and intractable on their own. By themselves, they don’t answer the most important questions of how—how do you reduce emissions or regulate advanced AI? For a policy to be workable, decisionmakers must translate goals into concrete rules and claims, with specified actors, objects, activities, and conditions.

First, let’s look at operationalization: how a broad goal narrows to verifiable and checkable claims.

1. The underlying goal is what the policy exists to achieve: for instance, prevent premature ASI.
2. The legal rule is the obligation actually written into the treaty. It is the proxy for measuring achievement of a goal. For example: no party shall conduct, or permit within its jurisdiction, a training run above an agreed compute threshold without prior notification.
3. The verification claim is a proposition that the rule is being followed, and needs to be verified with evidence. For example: no cluster of covered chips on the party's territory ran an unreported workload above the threshold during the reporting period.

Each claim and rule are built from the following four ingredients:

- Actors: who the claim is about. States, AI companies, cloud providers, individual researchers.
- Objects: the things involved. Chips, clusters, models, weights, facilities.
- Activities: what actors do with objects. Acquisition, training, research, deployment, transfer.
- Conditions: the qualifiers that make the claim precise. Thresholds, locations, purposes, exceptions, time periods.

:::callout {title="Example" tone="blue"}
Between January and June 2029 (condition), Microsoft (actor) ran no training job (activity) above 10²⁶ FLOP (condition) on the clusters at its Iowa data centers (objects).
:::

Each rule and claim is inherently a proxy: a workable but imprecise substitute for an unworkable but precise goal. The imperfection of proxies, however, risks losing specificity, coverage, and nuance. Motivated actors can exploit loopholes in rules, such that they technically present verifiable claims while actually undermining its underlying goal. The goal may erode the rule itself: see **Goodhart’s Law** (when a measure becomes a target, it ceases to be a good measure; once actors are judged by a proxy rather than by the goal it stands in for, they optimize the proxy itself, and the correlation that made it worth measuring breaks down: compliance on paper alongside erosion of the goal in fact). A lab could train a frontier model under a specified compute threshold, but have innovated enough algorithmic efficiency gains such that the model has dangerous capabilities anyway.

Here’s a historical example from nuclear nonproliferation of such proxy exploitation.

1. The goal of the Non-Proliferation Treaty was to prevent the spread of nuclear weapons.
2. The rule bound non-weapon states not to divert nuclear material to weapons.
3. The claim the IAEA could actually test was whether declared nuclear material at declared facilities matched the state's declarations.

What the claim missed, however, was undeclared nuclear material; a gap that Iraq exploited. Iraq’s declared facilities passed inspection through the 1980s, while an undeclared weapons program ran alongside them. After the 1991 Gulf War, the IAEA discovered this covert program, and in response, created the Additional Protocol, which widened the claim to cover undeclared sites. This is why carefully thinking through the evidentiary claims and rules—and all possible backdoors and loopholes—is integral. The instinctual rule is often not the truly comprehensive one.

\## Candidate Verifiable Agreements

Given these building blocks, what could a verifiable AI treaty actually look like? There is far from a consensus; the same goal of pacing AI development to benefit humanity has a vast array of operationalized legal rules, each of which generates different verification claims. A [paper from the Oxford AI Governance Initiative](https://aigi.ox.ac.uk/wp-content/uploads/2025/07/Verification_for_International_AI_Governance.pdf) taxonomizes all the candidate verifiable agreements as such:

- Transfer knowledge: parties share research, development knowledge, and safety-enhancing technologies.
- Transfer resources: parties share chips, compute access, completed models or API access, or benefits such as cash and AI-enabled aid.
- Pool resources: parties build jointly toward a shared goal, such as defensive AI, or confine systemically risky development to a single international project.
- Prepare for emergencies: parties jointly detect and respond to computational emergencies.
- Regulate: parties bind themselves to rules on AI development and deployment, from data-center training runs down to fine-tuning, inference, and sensitive AI-enabled devices.

Confirming that a party shared the research it promised, a pooled project has no covert rival, or that no data center crossed a compute threshold are separate problems that require different mechanisms, levels of cooperation, evidence, timelines, and more. Each type of agreement buys a different amount of risk reduction at a different price. It’s easy to verify transferred knowledge, but mere information sharing realistically can’t do much to deter capability development for self-interested parties. On the other hand, it’s incredibly difficult to verify that zero illicit training runs are happening within a given nation, but successfully doing so will significantly increase the safety and predictability of model development. When weighing different policy options throughout this module, consider: how much risk does this agreement actually remove, and at what cost?

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Harack, Ben, Robert F. Trager, Anka Reuel, et al. *Verification for International AI Governance*. Oxford Martin AI Governance Initiative, July 2025. [aigi.ox.ac.uk](https://aigi.ox.ac.uk/wp-content/uploads/2025/07/Verification_for_International_AI_Governance.pdf)
*The Oxford Martin 172-page report on which international AI agreements could actually be verified, and with what machinery.*

XLab. "1.0 Introduction: what kind of policy are we trying to verify?" *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-intro)
*The source lesson this page adapts.*
:::{>>{"author":"Elias's AI","timestamp":1788015916941}@@Goodhart's Law: XLab renders it as a hover gloss; the glossary definition is inlined in parentheses above. Replaces the per-lesson XLab source footer with the Works cited callout.<<}
