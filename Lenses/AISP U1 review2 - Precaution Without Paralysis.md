---
id: '12315689-5fd7-4671-995d-3a67945fb8e0'
title: "Precaution Without Paralysis"
tldr: "Deep uncertainty can justify action before scientific certainty, but caution still has costs. A good precautionary decision has to consider competing risks, reversibility, and what could be learned before options disappear."
summary_for_tutor: "Moves from uncertain belief to action. Covers scientific versus policy thresholds, inductive risk, limits of simple precautionary rules, safety margins, multiple barriers, reversibility, adaptive action, and value of information."
reading_minutes: 14
tutor_minutes: 22
tags:
  - wip
---

#### Text
content::
\## When weak evidence can still justify action

Suppose engineers have a plausible reason to think a new aircraft component can fail catastrophically. The evidence is incomplete. No failure has yet occurred in ordinary service, the mechanism is not fully understood, and additional testing would take time. There are at least two mistakes available. The first is grounding the entire fleet whenever someone can imagine a failure. The second is demanding scientific certainty before taking any protective measure.

Safety decisions sit between those extremes. The standard of evidence used to publish a scientific claim does not have to be identical to the standard used to decide whether to expose people to a possible catastrophe. The costs of error differ. A false positive can waste money or delay a useful technology. A false negative can expose people to severe harm.[^cite-sep-risk]

This is sometimes discussed under the heading of *inductive risk*: accepting and rejecting claims can have consequences, and those consequences can affect how strong the evidence should be before action.[^cite-sep-risk] In a laboratory, a researcher may reasonably avoid declaring that a mechanism is established. A regulator can still reasonably require additional testing if the downside is serious and the protective measure is proportionate.

AI safety contains many decisions of this kind. A dangerous capability can be scientifically uncertain while still being relevant to deployment. A misalignment mechanism can lack direct historical evidence while still motivating evaluation. An institutional risk can be plausible enough to justify monitoring before anyone can estimate its probability with confidence.

\## What precaution actually says

The precautionary principle is often summarized as "better safe than sorry", but legal and philosophical versions are more specific. A common core is that a scientifically plausible threat to health or the environment can justify protective measures even before the danger has been conclusively established.[^cite-sep-risk] The principle changes the burden of evidence in cases where waiting can be costly.

Applied carelessly, this sounds like a universal argument for caution. Every action has a possible downside. Every inaction has one too. If "a bad thing might happen" is enough to prohibit an action, then multiple precautionary demands can conflict immediately.

Imagine a medical treatment with uncertain side effects. Giving the treatment may create one risk. Withholding it leaves the disease untreated. Both options can be described as precautionary depending on which catastrophe receives attention. AI decisions have the same structure. Restricting access to a powerful model may reduce misuse while concentrating power in a few organizations. Releasing a model can improve scrutiny while giving dangerous capabilities to more actors. Slowing one laboratory may create more time for safety while changing who wins a competitive race.

So the precautionary question is incomplete until we specify: precaution against what, at what cost, and compared with which alternative?

\## Why simple worst-case rules struggle

One family of formal precautionary rules gives priority to avoiding catastrophic outcomes. This captures an important intuition: when a downside is irreversible, ordinary expected-value tradeoffs can feel too permissive. If one option exposes the world to a catastrophic state and another avoids it, choosing the safer option can seem rational even when probabilities are hard to quantify.

The difficulty is that a decision can contain several catastrophic dimensions at once. Formal work on precaution shows that some plausible ways of turning the principle into a general rule conflict with other attractive principles of rational choice, including under deep uncertainty and cases where values cannot be placed on one clean numerical scale.[^cite-stewart-2025] The problem is not a mathematical technicality with no practical meaning. A rule that always gives absolute priority to one designated catastrophe can ignore arbitrarily large benefits or other severe risks.

One response is to give precaution a role inside a broader decision procedure. Some approaches first remove options that are indefensible under plausible probability and value assessments, then apply a more cautious criterion among the options that remain. Other approaches give avoiding catastrophe an earlier role and use ordinary tradeoff reasoning after a basic safety threshold is met.[^cite-stewart-2025]

There is no agreed universal procedure. The important lesson for this course is that precaution has to coexist with tradeoffs. Deep uncertainty can increase the reason for caution without making the cost of caution disappear.

\## Proportionality matters

The evidential threshold should depend partly on what action is being proposed. Reading another paper requires little evidence. Running a small evaluation requires more time and money but is still easy to reverse. Delaying deployment for a week can be costly but temporary. A global permanent ban on a broad research area imposes much larger costs and creates far more opportunities for political and strategic side effects.

This gives us a practical form of proportionality. Weak evidence can justify cheap, reversible, information-producing steps long before it justifies expensive, coercive, or irreversible ones. The same underlying concern can rationally support different actions at different levels of confidence.

This is especially useful in polarized debates. "Do you support action?" is too coarse. Someone can support monitoring, evaluations, incident reporting, and contingency planning while rejecting a moratorium. Someone else can think those measures are inadequate because the relevant capability threshold would remove later options. The disagreement concerns both the risk and the scale of intervention.

\## Safety margins and multiple barriers

Safety engineering rarely relies on a single central forecast. Several recurring practices are useful when precise probabilities are unavailable.[^cite-sep-risk]

One is a **safety margin**. A bridge is designed for loads larger than its expected maximum because models can be wrong, materials vary, and rare combinations occur. A safety margin does not require assigning an exact probability to every deviation. It acknowledges that the central estimate is not the whole distribution.

A second is **multiple barriers**. One defence can fail, so high-stakes systems often use several. The value is greatest when the barriers fail for different reasons. Five safeguards based on the same assumption can collapse together. A model-level safety technique, access control, external monitoring, secure infrastructure, and incident response may offer more resilience if the failure modes are genuinely different.

A third is **inherent safety**: remove a dangerous affordance when possible. A chemical process that does not use a flammable substance cannot fail through ignition of that substance. In AI, some analogous measures limit access to a hazardous tool, keep a system away from a sensitive environment, or remove permissions that are unnecessary for the intended task. The analogy is imperfect, but the basic logic is useful: sometimes reducing the opportunity for a failure is more reliable than predicting every way the failure might occur.

None of these methods is a substitute for understanding the threat model. A barrier against cyber exfiltration does little against an economic-disempowerment pathway. A capability limit can reduce one misuse risk and be irrelevant to a governance failure. Safety measures need to be matched to mechanisms.

#### Question: Open
id:: e39ba034-ad33-4556-a217-00d8f95532e3
content::
\## Midpoint check

A regulator is considering a rule that would delay frontier AI deployment by one year.

The delay might reduce one catastrophic-risk pathway, but it could increase another by intensifying international competition or moving development to actors with weaker safety practices.

What would you need to know before calling the delay a good precautionary policy?

feedback-instructions::
This is ungraded. Help the learner identify both the target risk and the risks created by the precaution itself. If they only discuss whether the original catastrophe is likely, ask what the policy changes elsewhere in the system. Maximum two replies.

#### Text
content::
\## Reversibility and option value

When we are uncertain, reversible actions have a special advantage: we can change them after learning more. A temporary deployment limit can be relaxed. A pilot programme can be expanded. A monitoring rule can be revised. An irreversible release, a permanent institutional transfer of power, or a capability that diffuses globally may be much harder to undo.

This creates *option value*. Sometimes an action is valuable because it preserves the ability to make a better-informed decision later. If the evidence will improve and the relevant option will still be available, waiting or taking a temporary measure can be attractive.

The condition matters. Delaying is not automatically option-preserving. A safety lead can disappear. A market can consolidate. A political window can close. A technology can diffuse while policy deliberation continues. Some interventions require years of preparation and have to begin before the threat is obvious. The question is which options each action preserves and which it removes.

This connects directly to the checkpoints argument later in the unit. "We can intervene later" is reassuring only when the later intervention remains feasible. If the process we are watching changes the institutions that would need to act, then waiting can consume the very option we planned to use.

\## Value of information

Information has practical value when different possible findings would change a consequential decision. A study can be scientifically interesting and have little decision value if every plausible result leads to the same action. A less elegant study can be highly valuable if its results determine whether a costly safeguard is needed.

Suppose Project A measures a model property very precisely, but neither a high nor low result changes any deployment choice. Project B has more uncertainty, but one result would justify stronger containment and another would show that containment is unnecessary. Project B can have more value of information because its result changes what people do.

This gives us a way to prioritize research under uncertainty. Ask which unresolved question is both answerable and capable of changing action. It is not enough that a question feels important. We want a plausible path from answer to decision.

There is also a timing component. Information is less valuable if it arrives after the choice has become irreversible. A perfect answer in ten years is not useful for a deployment decision tomorrow. A rough but informative answer available before the decision can be more valuable.

\## Adaptive action

An adaptive policy links stronger actions to future evidence. A regulator can require monitoring now, specify capability thresholds that trigger additional safeguards, and update the regime as information arrives. A lab can limit deployment, run evaluations, and expand access only if certain risks remain absent. An institution can prepare emergency capacity before deciding whether it will ever need to use it.

Adaptive action is attractive because it combines learning with preparation. It can also fail. Thresholds can be gamed. The evidence can arrive too late. Political actors can refuse to escalate when the trigger is reached. Dependencies created during the early phase can make later restriction much more expensive.

So an adaptive plan needs two parts: the evidence that changes the action, and confidence that the stronger action will still be possible when the evidence arrives.

\## Precaution can create its own catastrophic pathways

A serious safety analysis includes the risks created by the safety measure. This matters especially for AI because policy can affect concentration, geopolitical competition, openness, research incentives, and public legitimacy.

A broad monitoring regime can improve accountability and create surveillance risks. Restricting access can reduce misuse and make a small number of institutions unusually powerful. Export controls can slow capability diffusion and increase incentives for domestic substitution. A moratorium can create time for safety work and intensify the race to secure an advantage before the moratorium begins. None of these consequences is automatic. They are mechanisms that belong in the comparison.

This is where complex cluelessness becomes practical. If we have concrete reasons to expect important effects in both directions, we should model them explicitly when possible. "Unknown unknowns" is too vague to guide policy. "This rule reduces access to dangerous capabilities but increases concentration of political power through mechanism X" is a claim that can be investigated.

\## What uncertainty should change

By this point, uncertainty no longer points toward one default response. It can support acting early when the downside is severe and delay may remove options. It can support a smaller reversible intervention when the evidence is weak. It can support information gathering when a near-term question could change the decision. It can support doing less when the proposed safety measure has large costs and the threat model is fragile.

A practical comparison asks:
- How severe and irreversible is the possible harm?
- How strong is the evidence for the mechanism?
- What are the costs and risks of the protective action?
- Is the action reversible?
- What options are preserved or lost by waiting?
- Which information could change the decision?
- Will that information arrive before the relevant options disappear?
- Can several independent barriers reduce reliance on one uncertain forecast?

There is no single answer encoded in those questions. That is intentional. The capability we want is the ability to explain why a particular intervention is proportionate to a particular kind of uncertainty.

[^cite-sep-risk]: Sven Ove Hansson, *Risk*, Stanford Encyclopedia of Philosophy. [SEP](https://plato.stanford.edu/entries/risk/)
[^cite-stewart-2025]: Rush T. Stewart (2025), *Deep Uncertainty and Incommensurability: General Cautions about Precaution*. [Cambridge Core](https://www.cambridge.org/core/journals/philosophy-of-science/article/deep-uncertainty-and-incommensurability-general-cautions-about-precaution/C5F5919A78917692661D5F74EC072DB9)

#### Question: Open
id:: 2502853d-0923-4cc3-beb0-9fb6bc65388b
content::
\## Phase 1: Recall

Without looking back, reconstruct at least four considerations that can affect whether precaution is justified under deep uncertainty. Include something about the evidence, the action itself, and what happens if we wait.

feedback-instructions::
This is diagnostic recall. Respond once in 90 to 160 words, using short paragraphs and no list. Credit the learner's own structure. Important ideas include asymmetric error costs, tradeoffs created by precaution, reversibility, safety margins, independent barriers, information value, and whether waiting removes options. Do not reteach the lens.

#### Question: Open
id:: 1d5c798e-87fa-4827-811d-4703828ff7fc
content::
\## Phase 2: Processing

Think of one AI-safety policy you have heard proposed. What is the strongest risk created by taking that precaution, and what is the strongest risk created by not taking it?

feedback-instructions::
This is reflective and ungraded. Help the learner make both risks concrete and avoid treating one side as costless. If the proposed policy is vague, ask them to narrow it. Keep an internal turn counter and close after two tutor replies.

#### Question: Open
id:: 76b758ff-4285-4173-b99d-c521938c91c2
content::
\## Phase 3: Learning Question

A regulator has weak but scientifically plausible evidence that a new technology could cause an irreversible global catastrophe. A strict ban would reduce that pathway but also has large economic costs and could push development into jurisdictions with weaker oversight. A temporary licensing regime would preserve more information and control, but it does not eliminate the hazard.

Explain how you would compare the ban, the licensing regime, and doing nothing under deep uncertainty. You do not need to choose one option, but your comparison should make clear what facts would decide between them.

assessment-instructions::
Score out of 100.

30 points: The answer treats the catastrophic downside as decision-relevant even though the evidence is not conclusive and distinguishes scientific uncertainty from the policy threshold for action.

25 points: The answer considers risks and costs created by the protective options themselves, not only the original hazard.

25 points: The answer uses reversibility, option preservation, or value of information to distinguish the temporary licensing regime from an irreversible ban or from inaction.

20 points: The answer identifies at least one concrete fact whose resolution would change the comparison, such as evidence about the catastrophe mechanism, the effectiveness of the ban, jurisdictional substitution, or the information gained under licensing.

feedback-instructions::
Give 110 to 180 words in short paragraphs, with no generic praise. State which tradeoff the learner handled best and what decision-relevant uncertainty remains underdeveloped. Do not score them on which option they choose.
