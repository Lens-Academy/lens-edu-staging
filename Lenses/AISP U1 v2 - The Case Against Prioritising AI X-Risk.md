---
id: '77a6bb8e-7ff3-421b-a5c8-aed849a73bf8'
title: "The Case Against Prioritising AI X-Risk"
tldr: "A good case for AI safety has to survive more than objections to takeover mechanics. It also has to answer whether x-risk framing distracts from present harms, targets the wrong source of danger, or acts too early."
summary_for_tutor: "Presents and assesses the Distraction, Human Frailty, and Checkpoints for Intervention arguments from Swoboda et al., alongside Grace's technical objections. The learner should distinguish critiques of probability from critiques of priority and identify what evidence would settle each."
reading_minutes: 32
tutor_minutes: 20
tags:
  - wip
---

#### Text
content::
\## Skepticism can target different things

Someone can reject AI x-risk work for several reasons.

They might think the catastrophe itself is unlikely. They might accept the risk but think current interventions are ineffective. They might think the same resources do more good on current harms. They might believe society will get better evidence later, before the dangerous step becomes irreversible. They might think the real problem is familiar human recklessness and bad institutions.

These are different arguments. They should not receive one generic reply.

Katja Grace's objections mostly attack the causal chain of a rogue-AI scenario: perhaps useful AI is not strongly agentic, intelligence does not translate cleanly into power, human institutions remain competitive, and rapid takeoff assumptions fail.[^cite-grace-counterarguments] Swoboda and coauthors examine a different family of skepticism. Their paper reconstructs three popular arguments against the *priority* given to AI existential risk: the Distraction Argument, the Argument from Human Frailty, and the Checkpoints for Intervention Argument.[^cite-swoboda-skepticism]

\## The Distraction Argument

The Distraction Argument says that attention to speculative future catastrophe pulls attention, money, and political energy away from harms that already exist: bias, surveillance, misinformation, labor exploitation, privacy violations, and concentration of power.

There are several versions. One says attention is finite, so more x-risk work literally means less work on present harms. Another says tech companies benefit from dramatic future narratives because those narratives allow them to appear safety-conscious while avoiding accountability for current products. Another says doomsday framing gives a small technical elite disproportionate influence over AI policy.

These concerns cannot be dismissed just by showing that x-risk is possible. A real future risk can still be a bad priority if focusing on it creates larger opportunity costs or political distortions.

Swoboda and coauthors argue that the strongest empirical claims behind the Distraction Argument are not yet well established.[^cite-swoboda-skepticism] Attention to current harms has not obviously collapsed as x-risk discussion increased, and regulation can address current and future risks together. Some policies, such as stronger accountability and safer deployment practices, can help across both.

Still, the argument leaves us with an important research question: **which resources are actually zero-sum?** A researcher choosing between two careers faces a different tradeoff from a government that can expand an AI-safety budget. Some policies complement each other; others genuinely compete.

The lesson is not "distraction is false." It is that distraction is a causal claim about institutions and resource allocation. It needs evidence.

\## The Human Frailty Argument

The second argument says the deepest source of AI risk is familiar human failure.

People are biased, reckless, self-interested, politically divided, bad at coordination, and sometimes malicious. Organizations suppress warnings. Regulators are captured. Companies race. Militaries miscalculate. If those failures create the dangerous conditions, perhaps the best safety work is to improve institutions and human decision-making instead of studying speculative superintelligence.

This argument has a lot going for it. Many catastrophic pathways from the previous lens obviously involve human frailty. Malicious use is human. Race dynamics are human coordination failures. Organizational accidents are human institutional failures. Even a rogue system has to be built, deployed, and given access by some human process.

Swoboda and coauthors argue that the conclusion goes too far if it says there is little reason to study AI-specific catastrophic scenarios.[^cite-swoboda-skepticism] "Reduce human frailty" is too broad to guide action until we know which frailties matter. Understanding the AI threat model can be part of learning which institutional failures deserve attention. And if one defines every harmful human action as "human frailty", the claim becomes nearly tautological.

This creates a useful bridge between technical and institutional safety. A technical failure can depend on a governance failure. A governance intervention can depend on understanding the technical pathway. The categories do not have to compete.

\## The Checkpoints for Intervention Argument

The third argument is appealing because it sounds like ordinary engineering common sense.

Dangerous AI cannot appear from nowhere. People have to build more capable systems, give them resources, connect them to infrastructure, automate more of the economy, grant access to weapons, and continue deploying despite warning signs. Each stage creates a checkpoint. If the risk becomes clearer, we can stop.

This argument shifts the burden. Why pay large costs now to avoid a speculative future if society can wait for stronger evidence and intervene at a later checkpoint?

The answer depends on how observable, reversible, and controllable the checkpoints really are.

Some checkpoints may be visible and slow. Others may be crossed by many actors independently. A capability can diffuse. A competitive race can make unilateral restraint costly. A system can become economically important before its full risk profile is understood. Gradual disempowerment can weaken the institutions that would have to intervene later. A deceptive system, if that threat model is correct, can also make warning signs less reliable.

Swoboda and coauthors conclude that checkpoints provide a real consideration but do not establish that waiting is safe.[^cite-swoboda-skepticism] The important empirical question is whether intervention opportunities remain effective as capabilities and deployment scale increase.

This links directly to value of information. Waiting makes sense when later evidence is likely to arrive before the relevant option disappears. Early action makes more sense when the decision is hard to reverse or the ability to intervene may weaken over time.

\## Current harms and future harms can share mechanisms

Kasirzadeh's accumulative-risk account complicates the Distraction Argument further.[^cite-kasirzadeh-accumulative] Some current social risks may be part of the long-run pathway. Manipulation can weaken public trust. Surveillance can lock in political power. Economic disruption can reduce institutional resilience. Military automation can worsen strategic instability.

This does not mean every present harm should be relabelled existential. It means the boundary between "AI ethics now" and "AI safety later" is partly causal, not merely temporal.

A useful question is: **does this present harm change the system's capacity to avoid later catastrophe?** If yes, work on the present harm can also be existential-risk reduction. If no, it may still matter enormously for ordinary moral reasons.

\## What would change your mind?

Each skeptical argument points toward different evidence.

For the Distraction Argument, look at actual budget substitution, political attention, regulatory agendas, and whose voices gain or lose influence.

For Human Frailty, identify which AI-specific mechanisms remain after improving ordinary institutional competence. Ask whether the interventions are generic or require technical threat-model knowledge.

For Checkpoints, study whether warning signs arrive early enough, whether intervention remains politically and technically feasible, and whether important deployments are reversible.

For Grace's technical objections, examine agency, autonomy, power-seeking, capability scaling, human-AI competition, and institutional containment.

One of the goals of this course is to replace global positions such as "AI x-risk is speculative" with claims that can be investigated.

\## Priority is the last step, not the first

A serious case for prioritising AI safety has to survive at least three questions.

**Is there a plausible pathway to very large or irreversible harm?**

**Is there an intervention that actually changes that pathway?**

**Does that intervention beat realistic alternatives once costs and side effects are included?**

A high probability of catastrophe does not guarantee a good intervention. A low probability does not guarantee a bad one. Cheap information-gathering can be worthwhile at low probabilities. Expensive irreversible policy can be unjustified even when concern is substantial.

This is why the rest of Unit 1 ends with disagreement and decision-making, not with a final p(doom).

[^cite-grace-counterarguments]: Katja Grace, *Counterarguments to the Basic AI X-Risk Case*. [AI Impacts](https://aiimpacts.org/counterarguments-to-the-basic-ai-x-risk-case/)
[^cite-swoboda-skepticism]: Torben Swoboda et al. (2025), *Examining Popular Arguments Against AI Existential Risk: A Philosophical Analysis*. [arXiv](https://arxiv.org/abs/2501.04064)
[^cite-kasirzadeh-accumulative]: Atoosa Kasirzadeh (2025), *Two Types of AI Existential Risk: Decisive and Accumulative*. [Philosophical Studies](https://doi.org/10.1007/s11098-025-02301-3)

#### Question: Open
id:: e7697ed0-17a2-4c07-ab28-2a151444db11
content::
\## Phase 1: Recall

Without looking back, reconstruct the Distraction, Human Frailty, and Checkpoints arguments. For each one, write the conclusion it is trying to support.

feedback-instructions::
Respond once in 90 to 160 words. Focus on whether the learner has kept the three arguments distinct. Correct at most two conflations.

#### Question: Open
id:: 706ac345-83a0-4792-b0bd-0ee9c00eb058
content::
\## Phase 2: Processing

Which skeptical argument seems strongest to you right now? What evidence would most weaken it?

feedback-instructions::
Ungraded. Help the learner turn the objection into a falsifiable or at least discriminating claim. Maximum two replies.

#### Question: Open
id:: 26da9657-bc0d-4b5d-bbb8-b83a5fa10d2a
content::
\## Phase 3: Learning Question

A policymaker says: "We should postpone serious work on catastrophic AI risk. If the danger becomes real, we will see warning signs and intervene then."

Evaluate this argument. Give one condition that would make waiting reasonable and two conditions that would make waiting dangerous.

assessment-instructions::
Score out of 100.

30 points: The answer gives a coherent condition making delay reasonable, such as later evidence arriving before irreversible deployment while intervention remains feasible and relatively cheap.

35 points: The answer gives one coherent failure of the checkpoint logic, such as warning signs arriving too late, dangerous capabilities diffusing quickly, competitive pressure making intervention harder, or important decisions becoming irreversible.

35 points: The answer gives a second, distinct failure of the checkpoint logic.

feedback-instructions::
Give 100 to 170 words. State whether the learner treated waiting as a conditional strategy rather than automatically good or bad. Below full credit, identify whether the two failure conditions are genuinely distinct.
