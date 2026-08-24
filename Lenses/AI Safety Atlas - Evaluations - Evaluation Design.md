---
id: 4d0c0e59-42c4-4ab1-9a64-d81d82eb1a12
tldr: "Give an AI a calculator and a hard math problem becomes trivial: the tools you hand a model during testing quietly reshape what it can do. This section covers the practical craft of running evaluations at scale, how these affordances change results, how models can write their own evaluations, and how test outcomes feed into audits and real company decisions about whether to keep building."
summary_for_tutor: "Covers how to implement evaluations at scale and connect them to organizational decision-making. Explains affordances, the tools, context, and resources given to a model during testing, and the minimal, typical, and maximal affordance conditions that reveal different capability levels. Discusses scaling through automation via model-written evaluations (MWEs), how they are generated and judged, and how they differ from human-written evaluations. Details the auditing process (training-design, security, deployment, and governance audits), internal versus external auditing, ongoing post-deployment monitoring, and the need for predefined action-trigger thresholds tied to governance frameworks like Responsible Scaling Policies, along with the 'safety washing' failure mode."
title: "Evaluation Design"
{++{"author":"Elias's AI","timestamp":1787570212603}@@reading_minutes: 17
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Evaluation Design|Evaluation Design]]{++{"author":"Elias's AI","timestamp":1787570212603}@@

#### Text
optional:: true
content::
Hand a model a calculator and a hard problem becomes easy, so the tools you allow during a test decide the result. Given that, did the section convince you a capability number means anything on its own? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
The practical craft of running evaluations at scale and connecting them to decisions. Affordances are the tools, context and resources a model is given during testing, and the section distinguishes minimal, typical and maximal affordance conditions, which reveal different capability levels for the same model, so a reported number is really a number plus a setup. Scaling is addressed through automation, including model-written evaluations: how they are generated, how they are judged, and how they differ from human-written ones. It then covers auditing, split into training-design, security, deployment and governance audits, the difference between internal and external auditors, ongoing post-deployment monitoring, and the need for action-trigger thresholds agreed in advance and tied to governance frameworks such as responsible scaling policies. It names safety washing as the failure mode when this machinery produces the appearance of rigour without the substance.

topics to explore:
- If the same model scores differently under minimal and maximal affordances, which number should go in a policy document?
- Model-written evaluations solve the scale problem by having AI test AI. What does that assume about the model doing the writing?
- Thresholds have to be set before you know what you will find. How would you pick one you would actually honour?
- Internal auditors know the system, external auditors are independent. Which shortfall is worse here?
- Safety washing is named as the failure mode. What would distinguish a real audit from a convincing one, from the outside?

The chapter's limitations section comes next and treats these problems head-on, so point at it rather than pre-empting it.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}
