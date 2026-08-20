{++{"author":"Elias's AI","timestamp":1787216945331}@@---
id: '49b3a580-3feb-4f39-8db4-fda3c65fd5b3'
slug: xcv-m1-policy-and-actors
title: "Policy and Actors"
---

# Lens: From a Policy Promise to a Verifiable Claim
id:: 440a3862-a63d-4edd-b09c-452958a00588
tldr:: Turn a policy promise into a checkable claim by naming actors, activity, threshold, declarations, evidence, and dispute triggers.
summary_for_tutor:: Bridge into XLab's policy-and-actors module. Teach claim-first scoping, actor roles, thresholds, evidence, and resolution. The question asks learner to specify a proposed commitment and identify an evasion route.
#### Text
content::
XLab's first applied module asks what kind of policy a verification system is meant to serve. Start with obligation, not favorite mechanism.

A useful specification names:

- **actors:** who is covered, who declares, who observes, and who decides;
- **activity:** training, deployment, acquisition, transfer, or another controlled act;
- **threshold:** compute, capability, hardware quantity, or another trigger;
- **evidence:** what observable record would support compliance or non-compliance;
- **resolution:** what happens when evidence is incomplete, inconsistent, or disputed.

Carry two constraints together. Policy must be effective enough to change relevant risk, and feasible enough that real actors could adopt and operate it. A technically elegant check for an agreement nobody would sign is not a successful design.

Use [XLab's live curriculum](https://aisafetytracks.com/verification/landing) for its current actor-map and supply-chain exercises. This alpha Lens adaptation focuses on the reusable reasoning and reading base; XLab's interactive exercises remain canonical while the paid cohort tests them.

#### Question
content::
Choose a proposed commitment such as "no training runs above a specified compute threshold." Write a compact verification specification: covered actors, controlled activity, threshold, required declaration, supporting evidence, and the condition that would trigger investigation.
assessment-instructions::
Help the learner turn a policy slogan into a testable claim. Check whether all six requested parts are concrete and mutually consistent. Identify the single most important ambiguity or missing actor. Ask one causal follow-up about how an actor could evade the proposed evidence. Do not reward agreement with any particular policy. Keep the response under 180 words.

# Learning Outcome:
source:: [[../Learning Outcomes/Compute accounting for training runs]]

# Lens:
source:: [[../Lenses/AIV - Verification Methods and Their Evasions]]
++}