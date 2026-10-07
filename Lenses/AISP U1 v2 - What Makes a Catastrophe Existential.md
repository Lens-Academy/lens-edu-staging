---
id: 'f7b3fe7a-cf3f-493e-8ee6-acde21ec23ec'
title: "What Makes a Catastrophe Existential?"
tldr: "The scale of a catastrophe is only part of what matters. Some failures permanently close off recovery, future generations, or human control, while other terrible outcomes may preserve those options."
summary_for_tutor: "Introduces existential catastrophe through irreversibility and future loss, then complicates the picture with permanent disempowerment, accumulative risk, and suffering risks. The learner should leave able to distinguish immediate severity from permanent loss without treating the label existential as an automatic priority claim."
reading_minutes: 28
tutor_minutes: 18
tags:
  - wip
---

#### Text
content::
\## Why start with the word "existential"?

AI safety discussions use words like *catastrophic*, *existential*, *extinction*, and *long-term* surprisingly loosely. That is a problem because these labels carry different practical implications. If a risk is merely very harmful, we may think about mitigation, compensation, and recovery. If a risk permanently destroys humanity's ability to recover or choose its future, the decision looks different.

Nick Bostrom's classic account defines an existential risk as one that threatens the premature extinction of Earth-originating intelligent life or the permanent and drastic destruction of its potential for desirable future development.[^cite-bostrom-xrisk] Human extinction is the cleanest case, but it is only one case. A civilisation could survive and still lose most of its future potential through permanent stagnation, irreversible dystopia, or some other lock-in from which later generations cannot escape.

Derek Parfit's familiar comparison helps show why this matters. Imagine one catastrophe that kills 99 percent of humanity and another that kills 100 percent. If the only thing we count is the number of people who die immediately, the difference is just the final one percent. Yet if the survivors of the first catastrophe eventually rebuild, the first world still contains all the people, projects, discoveries, cultures, and moral progress that could happen later. The second world contains none of them. The extra loss can be much larger than the extra one percent of deaths.

There is a moral premise inside that argument. Future lives and future possibilities have to matter for the additional loss to count. How much they matter depends on views in population ethics and theories of value that we will examine later in the course. Still, irreversibility matters under a wider range of views than one specific form of total utilitarianism. Someone could reject astronomical population ethics and still care deeply about preserving humanity's ability to recover, deliberate, correct mistakes, and keep open futures that existing people care about.[^cite-bostrom-xrisk]

\## Extinction is not the only way to lose the future

Recent work in AI safety pushes this point further. Jan Kulveit and coauthors describe *gradual disempowerment*: a future in which humans lose influence over the economy, culture, and states as AI becomes increasingly competitive at the functions those systems currently rely on humans to perform.[^cite-kulveit-disempowerment] Their argument does not require a sudden capability jump, a coordinated betrayal by AI systems, or one dramatic takeover event.

The paper starts from an observation about social systems. Markets, governments, and cultural institutions are not automatically aligned with human flourishing. They are partly kept responsive to humans because humans currently matter to them. Firms need human workers and customers. States need human taxpayers, soldiers, administrators, and political support. Culture depends on human creators and audiences. These dependencies give people leverage even when the systems are imperfect.

That leverage could weaken if AI becomes a better substitute for human labour, decision-making, cultural production, and other forms of cognition. The concern is not that one company decides to remove humans from the economy. Competitive pressure can reward actors who automate more aggressively. Political institutions can become less dependent on citizens if revenue and state capacity rely more on AI-driven production. Cultural systems can be shaped by machine-generated content and machine-mediated relationships. Because economic, political, and cultural power interact, losses of influence in one domain can reinforce losses elsewhere.[^cite-kulveit-disempowerment]

The end state could still look prosperous by familiar metrics. GDP may be high. Technology may advance quickly. Humans may even have comfortable lives for some time. Yet humans could have little ability to shape what happens next. Kulveit and colleagues call this *relative disempowerment* before considering more extreme cases where humans also lose access to the resources needed for basic needs. Their central claim is that a permanent loss of meaningful influence can itself count as existential catastrophe if humanity can no longer recover its ability to direct its future.

Atoosa Kasirzadeh develops a related distinction between *decisive* and *accumulative* AI existential risk.[^cite-kasirzadeh-accumulative] Decisive scenarios look like the standard stories: a sudden event or concentrated sequence of events produces irreversible catastrophe. Accumulative scenarios look more like a complex-system failure. Smaller disruptions can interact across economic, political, military, and informational systems, eroding resilience over time. Once enough resilience is lost, a further shock can trigger cascading failure.

This matters because the interventions are different. If catastrophe requires one decisive system to become uncontrollable, the safety agenda naturally focuses on preventing that system from gaining dangerous capabilities or acting autonomously. If catastrophe can arise from accumulation, then institutional resilience, human influence, information quality, economic power, and feedback loops become part of AI safety too.

\## A broader risk landscape

A survey by Hendrycks, Mazeika, and Woodside groups catastrophic AI risks into four broad sources: malicious use, AI race dynamics, organizational risks, and rogue AI systems.[^cite-hendrycks-overview] The taxonomy is imperfect, but it is useful because it prevents one threat model from becoming the whole field.

**Malicious use** includes cases where people deliberately use AI to cause large-scale harm. Advanced systems could lower the expertise needed for cyberattacks, biological misuse, surveillance, or mass persuasion.

**AI race dynamics** arise when competition pushes actors toward choices that each actor might reject in a more cooperative setting. A lab can think a deployment is unsafe and still deploy because waiting means losing to a competitor. States can automate military decisions because they fear slower decision-making will put them at a strategic disadvantage.

**Organizational risks** come from human institutions building and deploying complex systems badly. Weak safety culture, poor information security, suppression of internal warnings, accidental releases, and failures of oversight can matter even when no one wants catastrophe.

**Rogue AI** covers the more familiar loss-of-control family: systems with dangerous objectives, power-seeking behavior, deception, or other properties that make them difficult to control.

These categories overlap. A race can weaken organizational safety. Malicious actors can release autonomous systems. Persuasive AI can damage institutions and make later coordination harder. The useful lesson is that "AI catastrophe" is a family of pathways. Unit 4 will examine agency and power-seeking in much more detail, but Unit 1 should not make the whole case for intervention depend on that one mechanism.

\## Survival is not the only thing that can go very badly

There is another reason to avoid equating AI safety with extinction prevention. Some futures could contain enormous amounts of suffering while humanity, or its descendants, continue to exist.

Research on *s-risks* focuses on events that produce suffering on a cosmically significant scale.[^cite-clr-srisk] Proposed pathways include large populations of digital minds used in ways that cause severe suffering, conflict between powerful agents, stable institutions that permit extreme cruelty, and alignment failures that preserve enough of our values to create morally relevant minds while getting crucial details badly wrong.

Brian Tomasik's discussion of "near-miss" alignment gives a deliberately stark illustration.[^cite-tomasik-near-miss] Imagine a system that learns something close to human values and then optimizes a slightly corrupted version. A system indifferent to suffering might simply ignore it. A system that represents suffering as morally important but gets the sign or interpretation wrong could actively create the thing we wanted it to prevent. Tomasik's examples are intentionally simplified, but they reveal an important asymmetry: getting closer to the target does not guarantee that every intermediate failure is better than being far away from it.

This does not show that alignment research increases suffering risk overall. Tomasik is explicit that the comparison depends on the type of failure and the surrounding assumptions. The broader point is easier to defend. "Humans survive" and "the future goes well" are different goals. Some bad futures involve extinction, some involve permanent disempowerment, and some involve enormous suffering among humans, animals, digital minds, or other beings.

Unit 8 will return to these questions in depth. For now, we need them for one practical reason. If you define the target too narrowly at the start, you can choose interventions that successfully prevent one disaster while moving probability toward another.

\## So what does the label actually buy us?

Calling a risk existential does useful work when it directs attention to irreversibility, permanent disempowerment, and the loss of future options. It does much less work when it is used as a shortcut for "therefore this deserves top priority."

Priority depends on more than severity. We still need to know how likely the pathway is, whether an intervention changes it, what the intervention costs, what other risks it creates, and what moral assumptions make the avoided outcome valuable. A catastrophic-risk programme that cannot answer those questions is not rescued by attaching a stronger label to the catastrophe.

Keep one question in mind as you move through the rest of this unit: **what exactly becomes unrecoverable in the scenario being discussed?** Sometimes the answer is human life. Sometimes it is political agency, control over resources, the ability to revise our values, or the welfare of future beings. The answer affects what kind of safety work makes sense.

[^cite-bostrom-xrisk]: Nick Bostrom (2013), *Existential Risk Prevention as Global Priority*. [PDF](https://existential-risk.com/concept.pdf)
[^cite-kulveit-disempowerment]: Jan Kulveit et al. (2025), *Gradual Disempowerment: Systemic Existential Risks from Incremental AI Development*. [arXiv](https://arxiv.org/abs/2501.16946)
[^cite-kasirzadeh-accumulative]: Atoosa Kasirzadeh (2025), *Two Types of AI Existential Risk: Decisive and Accumulative*. [Philosophical Studies](https://doi.org/10.1007/s11098-025-02301-3)
[^cite-hendrycks-overview]: Dan Hendrycks, Mantas Mazeika, and Thomas Woodside (2023), *An Overview of Catastrophic AI Risks*. [arXiv](https://arxiv.org/abs/2306.12001)
[^cite-clr-srisk]: Center on Long-Term Risk, *Beginner's Guide to Reducing S-Risks*. [CLR](https://longtermrisk.org/research/beginners-guide-to-reducing-s-risks/)
[^cite-tomasik-near-miss]: Brian Tomasik (2018), *Astronomical Suffering from Slightly Misaligned Artificial Intelligence*. [Reducing Suffering](https://reducing-suffering.org/near-miss/)

#### Question: Open
id:: 585bc6b6-8095-454b-9db1-c49183d5a859
content::
\## Phase 1: Recall

Spend three minutes reconstructing the different ways this reading says a future can go catastrophically wrong. Do this from memory. Try to separate immediate scale from irreversibility, decisive failure from accumulative failure, and extinction from other bad long-run outcomes.

feedback-instructions::
Treat this as recall, not a checklist. In 90 to 150 words, mirror the distinctions the learner recovered. Point out at most two important conflations or missing categories. Do not add a new threat model. One reply only.

#### Question: Open
id:: 919c38a8-6b89-47ea-b118-cce020cb1f83
content::
\## Phase 2: Processing

Which scenario in this reading changes your view of "AI existential risk" the most: extinction, permanent disempowerment, accumulative collapse, or astronomical suffering? What makes that case feel more or less decision-relevant to you?

feedback-instructions::
This is reflective and ungraded. Help the learner identify the assumption doing the work in their answer. Do not push them toward any scenario or level of concern. Maximum two replies.

#### Question: Open
id:: f68bda9f-d76d-4536-bc25-8f64af069548
content::
\## Phase 3: Learning Question

A government says: "Our AI policy is successful if it prevents human extinction. Everything else is a secondary issue."

Give two different reasons this success criterion could be too narrow. For each reason, explain what kind of failure the government would miss and why that failure could still be irreversible or morally catastrophic.

assessment-instructions::
Score out of 100.

50 points: The answer gives a coherent non-extinction failure involving permanent loss of human influence, recovery, political or economic control, or an accumulative collapse that destroys long-run potential.

50 points: The answer gives a distinct failure involving severe long-run suffering, morally disastrous lock-in, or another outcome where survival does not imply a good future, and explains why it matters.

Each reason must describe a different failure mode. Grade the ideas, not course terminology.

feedback-instructions::
Give 100 to 160 words. Name which failure modes were well distinguished. Below full credit, identify the most important missing difference. Do not tell the learner which moral view to adopt.
