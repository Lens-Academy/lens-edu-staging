---
id: '9acaf0a5-8ea2-4726-8de7-c44d09e15ffc'
title: "Precaution Without Paralysis"
tldr: "Uncertainty can justify action before scientific certainty, but 'better safe than sorry' is not a complete decision rule. Precaution has to coexist with tradeoffs, competing risks, reversibility, and the value of learning."
summary_for_tutor: "Moves from diagnosis to action using the Stanford Encyclopedia of Philosophy on risk and Rush Stewart on precaution under deep uncertainty. Develops inductive risk, precaution, its formal difficulties, safety margins, multiple barriers, reversibility, risk-risk tradeoffs, adaptive action, and value of information."
reading_minutes: 36
tutor_minutes: 22
tags:
  - wip
---

#### Text
content::
\## When uncertainty should make us act earlier

Imagine a new aircraft engine. Engineers have a plausible reason to suspect a serious defect, but the evidence is not yet strong enough to say that the defect has been scientifically established. One option is to keep flying until the evidence becomes conclusive. Another is to ground the aircraft while engineers investigate.

The disagreement is not only about what is true. It is also about what standard of evidence should be required before taking a costly protective action. The Stanford Encyclopedia of Philosophy's discussion of risk uses this kind of case to distinguish the standards appropriate for scientific acceptance from the standards appropriate for policy.[^sep-risk] Science often sets a high bar before a claim becomes part of the accepted corpus. That makes sense when the main danger is filling the literature with false positives. A safety decision has a different loss function. If waiting for scientific certainty exposes people to a catastrophic failure, a false negative can be much more costly than a false positive.

This is the intuition behind the precautionary principle. In one common formulation, scientifically plausible indications of serious harm can justify protective measures even when the evidence is not strong enough to establish the danger conclusively.[^sep-risk] It is not the claim that every imagined harm should be prevented at any cost. It is a claim about how uncertainty and stakes can shift the burden of evidence.

AI safety often sits in exactly this space. We may have reasons to suspect that a capability, deployment practice, or institutional arrangement creates severe risk while lacking the kind of repeated evidence available in mature engineering. Waiting can produce information, but it can also consume time, normalize deployment, lock in infrastructure, and reduce the set of feasible responses.

\## Scientific uncertainty and decision uncertainty are different problems

Suppose a researcher says, "There is not enough evidence to conclude that model autonomy will cause catastrophic loss of control." That may be perfectly reasonable as a scientific claim. A policymaker faces a different question: "Is there enough evidence that I should require additional evaluations before deployment?" The first question asks what we should believe. The second asks how much evidence an action requires given its costs and possible consequences.

The philosophy of science calls the possibility of error in accepting or rejecting a hypothesis *inductive risk*.[^sep-risk] A false positive means treating a danger as real when it is not. A false negative means treating a real danger as absent. Scientific institutions often care a great deal about avoiding false positives because the reliability of the knowledge base matters. Safety policy can rationally weight the two errors differently. Grounding a safe plane for a day is costly. Flying an unsafe plane can be catastrophic.

The analogy has limits. AI policy can impose very large costs too. A regulation can slow beneficial technology, concentrate power, increase geopolitical competition, or encourage development in less transparent jurisdictions. So "catastrophe is possible" cannot be the end of the analysis. Precaution itself has side effects.

\## Why a simple precautionary rule breaks

Rush Stewart's paper on deep uncertainty asks whether we can turn the precautionary impulse into a general decision rule.[^stewart] The answer is more difficult than the slogan suggests. Some formal versions of the precautionary principle say, roughly, that when one option has a greater chance of catastrophic outcomes, we should reject it. The attraction is clear. If the downside is irreversible, why gamble?

The problem is that actions can carry different catastrophic risks at the same time. A policy that reduces one danger may increase another. Refusing a new medical technology can avoid an unknown side effect while leaving an existing disease untreated. Slowing AI deployment could reduce some loss-of-control risks while delaying benefits, shifting development abroad, or intensifying competition. Accelerating deployment could produce the reverse pattern.

Stewart generalizes earlier impossibility results and argues that certain precautionary rules remain in tension with other plausible principles of rational choice even under deep uncertainty and value incommensurability.[^stewart] The technical details are not required here. The important lesson is that a rule which always gives lexical priority to avoiding a designated catastrophe can become inconsistent or insensitive to tradeoffs that we have independent reason to care about.

This does not make precaution useless. Stewart's own conclusion is that precaution can still have a role within a broader decision procedure. One family of approaches first narrows the set of options using ordinary tradeoff reasoning and then applies a more cautious rule among the surviving options. Another family gives security a first-stage role and then compares the remaining alternatives. The philosophical disagreement is about where precaution enters, not about whether severe downside deserves any special attention.

#### Question: Open
id:: fdb23a2b-47e4-44cb-a9c8-6ed262718234
content::
\## Midpoint check

A regulator is considering a rule that would delay frontier AI deployment by one year.

The delay might reduce one catastrophic-risk pathway, but it could also increase another by intensifying international competition or moving development to actors with weaker safety practices.

What would you need to know before calling the delay "precautionary"?

feedback-instructions::
This is ungraded. Help the learner identify both the target risk and the risks created by the precaution itself. If they only discuss whether the original catastrophe is likely, ask what the policy changes elsewhere in the system. Maximum two replies.

#### Text
content::
\## Safety engineering rarely relies on one forecast

There is a useful practical contrast between philosophical debates over a single decision rule and how safety engineering often works. The SEP entry on risk describes three recurring design ideas: inherent safety, safety factors, and multiple barriers.[^sep-risk] Each is a way of protecting against uncertainty that is not fully captured by one probability estimate.

**Inherent safety** removes a hazard when possible. A process that does not use flammable material cannot catch fire because that material ignited. In AI, an analogous idea might be limiting a system's access to a dangerous capability or environment so that one class of failure cannot occur through that route. Whether a proposed restriction is genuinely "inherent" depends on the system, but the general idea is simple: sometimes removing the hazardous affordance is more reliable than trying to predict every way it could be misused.

**Safety factors** build margin beyond what the central estimate says is necessary. Bridges are designed to tolerate loads larger than the expected maximum because models can be wrong, materials vary, and rare combinations happen. In AI, the analogue could be requiring stronger evidence or larger safety margins as model capability approaches thresholds associated with severe harm.

**Multiple barriers** assume that any one defence can fail. A system can require a model-level safeguard, external monitoring, access control, incident response, and institutional oversight. The point is strongest when failures are not perfectly correlated. Three barriers that all depend on the same flawed assumption are much less useful than three genuinely independent layers.

These engineering practices are philosophically interesting because they protect against events that cannot be assigned confident probabilities. They acknowledge that a model of the hazard will be incomplete. They also avoid demanding that one principle carry the whole decision.

\## Reversibility is often worth paying for

Under deep uncertainty, reversible actions have a special attraction. If a policy is wrong, it can be changed. If a deployment is limited, it can be expanded later. If a capability is released irreversibly to millions of users, or if an institution gives up a form of control it cannot realistically regain, later evidence has less value because the decision has already been made.

This gives us one reason to care about *option value*. A decision can be valuable because it preserves the ability to make a better-informed decision later. That does not imply a blanket preference for delay. Delaying can itself close options. A safety lead can disappear. A monopoly can entrench. A geopolitical window can close. Some protective infrastructure takes years to build and has to begin before the evidence is decisive.

The useful question is not simply "can we reverse the action?" It is "which future choices does this action preserve or remove, and how much do we expect to learn before those choices matter?"

\## Value of information

Value of information gives a more precise way to think about learning. Information is valuable when different possible findings would lead us to make different decisions, and the difference between those decisions matters enough to justify the cost of learning.

Imagine two research projects. Project A will measure a property of frontier models very precisely, but no plausible result changes any deployment or safety decision. Project B is messier, but one result would make a lab strengthen containment and another would show that the costly containment is unnecessary. Project B can have higher decision value even if Project A produces a more elegant paper.

This is important for AI safety because uncertainty is not automatically a reason to research everything. We want to identify *decision-relevant* uncertainty. Which question could actually change a research agenda, deployment policy, allocation of money, or governance intervention? Later in this unit, the Forecasting Research Institute's work on AI-risk cruxes gives us a concrete attempt to do exactly this.

\## Robust action and adaptive action

A robust action performs acceptably across several plausible models. An adaptive action is designed to change as evidence arrives. These ideas are useful when we cannot collapse our uncertainty into one trusted probability distribution.

Consider evaluations of dangerous capabilities. A person who assigns a relatively low probability to catastrophic AI risk may still support good evaluations because they generate information and can catch concrete hazards. A person who assigns a much higher probability may support them for the same reasons while also wanting stronger measures. The action can be useful across disagreement.

Now consider an irreversible global ban on a broad class of AI research. That policy depends on many more assumptions: how much risk the research creates, how enforceable the ban is, what actors do in response, whether benefits are lost, and whether the policy increases concentration or conflict. A high-stakes irreversible intervention normally needs a stronger case than a cheap, reversible information-gathering measure.

This is not a universal theorem. Sometimes only a large intervention can address a large risk. The point is that the *cost and reversibility of the action* belong in the evidential standard. "How sure do we need to be?" cannot be answered without asking "sure enough to do what?"

\## Precaution can create new risks

The deepest problem with "better safe than sorry" is that there is rarely only one way to be sorry. A restrictive AI policy can reduce misuse while concentrating power. A requirement for extensive monitoring can improve safety while weakening privacy. Keeping systems closed can limit malicious access while reducing independent scrutiny. Open publication can help defensive research while spreading dangerous capabilities.

This is one reason Greaves's complex cluelessness matters here. If we can name structured mechanisms on both sides, we should not pretend that unmodelled consequences are random noise. Precaution has to include the risk created by the precaution.

Stewart's paper makes the same point at the level of decision theory. Even under severe uncertainty, a precautionary rule cannot simply refuse all tradeoffs without running into serious problems.[^stewart] A better response is to combine ordinary tradeoff reasoning with explicit attention to catastrophic downside, while being honest about where the combination remains philosophically unsettled.

\## A practical checklist for Unit 1

By the end of this submodule, the course is not asking you to adopt one decision rule. It is asking you to stop using uncertainty as if it had one obvious implication.

When you face a high-stakes uncertain AI decision, ask what evidence is actually available and what is only suspected. Ask which kind of error is more costly in this context. Ask what the protective action costs and which new risks it creates. Ask whether the action is reversible, whether waiting preserves or removes options, and whether a smaller step can generate valuable information. Ask whether the protection has independent layers or several layers that fail together. Finally, ask how the decision changes across the plausible models you currently take seriously.

Sometimes those questions will support early action. Sometimes they will support waiting, experimenting, or narrowing the intervention. The important thing is that "uncertainty" no longer functions as an argument by itself.

[^sep-risk]: Sven Ove Hansson, *Risk*, Stanford Encyclopedia of Philosophy. [SEP](https://plato.stanford.edu/entries/risk/)
[^stewart]: Rush T. Stewart (2025), *Deep Uncertainty and Incommensurability: General Cautions about Precaution*. [Cambridge Core](https://www.cambridge.org/core/journals/philosophy-of-science/article/deep-uncertainty-and-incommensurability-general-cautions-about-precaution/C5F5919A78917692661D5F74EC072DB9)

#### Question: Open
id:: 44743011-285d-46b5-a132-afc74d2d98e2
content::
\## Phase 1: Recall

Without looking back, reconstruct at least four considerations that can affect whether precaution is justified under deep uncertainty. Try to include something about the evidence, the action itself, and what happens if we wait.

feedback-instructions::
Respond once in 90 to 160 words. Credit the learner's own structure. Important ideas include asymmetric error costs, tradeoffs created by precaution, reversibility, safety margins, independent barriers, information value, and whether waiting removes options. Do not turn the reply into a full checklist.

#### Question: Open
id:: 0c8982e7-2a3e-4aa1-9089-51fb8bdf8c5d
content::
\## Phase 2: Processing

Think of one AI-safety policy you have heard proposed. What is the strongest risk created by *taking* that precaution, and what is the strongest risk created by *not* taking it?

feedback-instructions::
This is reflective and ungraded. Help the learner make both risks concrete and avoid treating one side as costless. If the proposed policy is vague, ask them to narrow it. Maximum two replies.

#### Question: Open
id:: 38bbcf08-4c48-47c3-b4bb-16e2a4cdd96e
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
Give 110 to 180 words. State which tradeoff the learner handled best and what decision-relevant uncertainty remains underdeveloped. Do not score them on which option they choose.
