---
id: '02bd91a5-0f76-47f6-93e0-026390518ad7'
title: "Precaution Without Paralysis"
tldr: "Deep uncertainty can justify caution before scientific certainty, but precaution still has to face tradeoffs, competing risks, reversibility, and the value of learning more."
summary_for_tutor: "Moves from diagnosis to action. Distinguishes scientific proof from policy thresholds, introduces the precautionary principle and its limitations, then develops proportionality, reversible action, safety margins, multiple barriers, risk-risk tradeoffs, and value of information."
reading_minutes: 30
tutor_minutes: 20
tags:
  - wip
---

#### Text
content::
\## Science and policy do not use the same threshold

Suppose engineers suspect a serious defect in an aircraft engine. The evidence is suggestive but does not meet the standard they would want before publishing a confident scientific conclusion. Should the plane fly?

The philosophy of risk gives a useful way to frame this.[^cite-sep-risk] Science has reasons to demand high standards before adding a claim to the accepted body of knowledge. False positives damage reliability. Policy has a different problem. A false negative can also be costly. If the engine really is unsafe, waiting for conclusive proof may be much worse than delaying a flight that later turns out to have been safe.

This distinction matters for AI. "We do not yet have scientific proof that this failure mode will occur" does not settle whether a lab, government, or funder should prepare for it. Policy decisions compare the cost of acting too early with the cost of acting too late.

The precautionary principle grew out of this kind of problem. In its standard policy form, it says that scientifically plausible threats can justify protective measures before the evidence becomes conclusive.[^cite-sep-risk] This is weaker than "always choose the safest-looking option". It changes the burden of proof in cases where waiting for certainty can itself create danger.

\## Why precaution feels attractive in AI safety

AI safety contains several features that make precaution tempting. Some outcomes could be irreversible. Some systems may be difficult to recall after deployment. Capabilities can diffuse. Institutions may adapt more slowly than technology. Evidence about a failure mode may become decisive only after the relevant system already exists.

There is also a one-sidedness to some mistakes. If we delay one deployment for six months and later discover the concern was overstated, the cost may be recoverable. If we deploy an irreversible system and later discover the concern was correct, the lost option may not return.

Engineers already use related ideas without requiring precise probabilities. Safety factors make structures stronger than the expected load. Multiple barriers create independent layers of protection. Inherent safety removes a hazard where possible, reducing reliance on perfect operation of added safeguards.[^cite-sep-risk] These techniques make sense partly because models are imperfect.

This gives precaution a respectable role. Yet the simple version quickly runs into trouble.

\## Every action has a worst case

Rush Stewart examines formal attempts to turn precaution into a general decision rule.[^cite-stewart-precaution] One natural idea says that if one option is more likely to cause catastrophe, reject it. Another family of rules gives overriding weight to avoiding the worst outcome.

The problem is that tradeoffs do not disappear. Safety measures can create harms of their own. Delaying AI can delay beneficial applications. Concentrating control to reduce misuse can increase the risk of abuse by whoever holds that control. Restricting open research can improve security while weakening external scrutiny. A policy designed to avoid one catastrophic pathway can make another pathway more likely.

Stewart develops formal impossibility results showing that several plausible versions of the precautionary principle conflict with other plausible rules of choice, even when probabilities are imprecise and values are not fully comparable.[^cite-stewart-precaution] You do not need the mathematics for the practical lesson: "avoid catastrophe first" cannot usually determine policy by itself when several options carry different serious risks.

Some versions of precaution use a lexicographic structure. First remove options that fail a safety criterion, then compare the survivors using ordinary tradeoffs. Other approaches reverse the order: first keep options that are defensible under some plausible probability model, then use a worst-case criterion to narrow further. These approaches disagree because there is no neutral place to put precaution in the decision procedure.

\## Precaution needs a target

A useful practical question is: *precaution against what?*

Imagine a government considering strict controls on frontier AI models. One argument says the controls reduce catastrophic misuse. Another says concentrating development inside a small number of approved institutions creates a durable concentration of power. A third says slowing deployment gives society more time to adapt. A fourth says slower diffusion leaves safety tools concentrated too.

"Apply the precautionary principle" does not tell us which risk should dominate.

The same problem appears in technical safety. A model can be restricted so heavily that useful external red-teaming becomes impossible. A monitoring system can reduce one class of failures while creating a false sense of security about failures it cannot detect. An emergency shutdown mechanism can itself become an attack surface.

Precaution becomes useful when paired with a concrete threat model and a comparison of actions.

\## Proportionality and reversible action

One response is to match the strength of the intervention to the strength of the evidence and the reversibility of the decision.

Low-cost, reversible precautions can be justified under much weaker evidence than costly, coercive, or irreversible measures. Running an additional evaluation, improving logging, delaying a small deployment, or maintaining an incident-response team may make sense even when the risk estimate is highly uncertain. A permanent ban, major geopolitical confrontation, or extreme centralization of authority needs a much stronger case because the intervention itself has large consequences.

This is not a theorem from the readings. It is a practical design principle we recommend for this course because it makes uncertainty action-relevant without treating uncertainty as paralysis.

Reversibility matters on both sides. Sometimes delaying action preserves options. Sometimes delay destroys them. A governance window can close. A model can proliferate. Infrastructure can become entrenched. The question is which choice keeps valuable options open while new information arrives.

\## Learning can be an action

When people describe a decision as "act or wait", they often leave out a third option: learn.

The Forecasting Research Institute's work on AI disagreement makes this idea concrete. Their adversarial collaboration asked forecasters and domain experts to identify *cruxes*: near-term questions whose resolution would change their long-run beliefs about AI risk.[^cite-fri-roots] This turns disagreement into a research agenda. If two views predict different outcomes on a measurable question, gathering that information can have direct decision value.

This is the basic idea behind *value of information*. Information matters when it has a realistic chance of changing an important decision. A study can be scientifically interesting and still have low decision value if every plausible result leaves policy unchanged. A modest experiment can have high decision value if its outcome would move resources between very different strategies.

AI safety already contains many possible information-gathering actions: capability evaluations, model-behaviour studies, interpretability research, incident reporting, forecasting, red-team exercises, governance pilots, and analysis of deployment effects. Their value depends partly on whether the results discriminate between live hypotheses.

\## Robustness can matter more than optimality under one model

Deep uncertainty also gives a reason to look for actions that perform reasonably well across several plausible models. This idea appears in robust decision-making, safety engineering, and the s-risk literature.[^cite-clr-srisk] A policy can be less impressive under one favored model and still be better if it avoids severe failure across a wider range of models.

Robustness has limits. If you demand that an action be good under every imaginable model, almost nothing survives. The relevant set has to contain views you take seriously. Robustness is useful when the disagreement is real and the action cannot easily be revised later.

This brings us to a practical framework for the rest of Unit 1. When uncertainty is deep, ask four questions:

1. **How bad and how irreversible is the failure?**
2. **How strong is the evidence for this pathway, including uncertainty about the model itself?**
3. **What harms or lock-ins does the intervention create?**
4. **Can we choose a reversible or information-producing step that remains useful across several plausible views?**

That will not eliminate judgment. It does make the judgment inspectable.

[^cite-sep-risk]: Sven Ove Hansson and others, *Risk*, Stanford Encyclopedia of Philosophy. [SEP](https://plato.stanford.edu/entries/risk/)
[^cite-stewart-precaution]: Rush T. Stewart (2025), *Deep Uncertainty and Incommensurability: General Cautions about Precaution*. [Cambridge Core](https://www.cambridge.org/core/journals/philosophy-of-science/article/deep-uncertainty-and-incommensurability-general-cautions-about-precaution/C5F5919A78917692661D5F74EC072DB9)
[^cite-fri-roots]: Josh Rosenberg et al. (2024), *Roots of Disagreement on AI Risk*. [Forecasting Research Institute](https://forecastingresearch.org/research/roots-of-disagreement-on-ai-risk)
[^cite-clr-srisk]: Center on Long-Term Risk, *Beginner's Guide to Reducing S-Risks*. [CLR](https://longtermrisk.org/research/beginners-guide-to-reducing-s-risks/)

#### Question: Open
id:: dc1aa748-b2b7-4d9d-a444-2c93c30b41f0
content::
\## Mid-reading pause

A regulator has weak but credible evidence that a new AI deployment could create a severe, irreversible failure. The regulator can pause deployment for three months while collecting evidence, but the pause has real economic and political costs.

What would make the pause look more justified to you? What would make it look less justified?

feedback-instructions::
Treat this as an ungraded checkpoint. Help the learner surface the variables they are using, such as severity, reversibility, evidence quality, cost of delay, or value of information. Do not tell them whether to pause. One reply.

#### Question: Open
id:: c57ce8e1-196a-49b3-9e17-dafbbcd037fd
content::
\## Phase 1: Recall

Without looking back, write down three reasons precaution can be useful under deep uncertainty and two reasons a blanket "better safe than sorry" rule can fail.

feedback-instructions::
Respond once in 90 to 150 words. Credit the learner's own examples if they capture the ideas. Point out at most two missing distinctions.

#### Question: Open
id:: 6726c20c-43b0-4245-a0c9-61c9da87ea80
content::
\## Phase 2: Processing

Which principle do you trust more when evidence is weak: preserve options, avoid the worst case, maximize expected value, or gather information first? Pick one and name a case where you think your preferred principle would give bad advice.

feedback-instructions::
This is reflective. The important thing is that the learner notices a limitation of their preferred rule. Ask at most one follow-up if the counterexample does not actually challenge the principle.

#### Question: Open
id:: 66015342-2d0c-4491-980b-a98967271d45
content::
\## Phase 3: Learning Question

A lab is deciding whether to deploy a model. It has a speculative but plausible catastrophic-risk concern. It can either deploy now, cancel the project permanently, or run a six-month safety programme that would produce evidence relevant to the concern while keeping deployment possible afterward.

Explain why the third option might be attractive under deep uncertainty. Then give one condition under which it would *not* be the best choice.

assessment-instructions::
Score out of 100.

50 points: The answer explains that the six-month programme can preserve options and generate decision-relevant information before an irreversible or costly commitment.

25 points: The answer connects the value of the programme to whether its evidence could actually change the deployment decision.

25 points: The answer gives a coherent condition under which another option is better, such as delay itself being highly dangerous, the information being unlikely to discriminate between hypotheses, or the catastrophic concern already being strong enough to justify cancellation.

feedback-instructions::
Give 100 to 160 words. Confirm the learner's reasoning about information and reversibility. Below full credit, identify the most important missing condition.
