---
id: '686a65ec-576b-4f9d-a008-8577ea7805fb'
title: "Running the model"
tldr: "Four lessons built you a machine for pricing safety work. Here you feed it. Ten researchers, seven agendas, three stipulated regimes, and one question each time: where does the next unit of effort go? Nothing is graded against an answer key, because there isn't one. What the exercise tests is whether your portfolio moves when the world does."
summary_for_tutor: "Capstone of the portfolio lessons that run from the end of Unit 3 into Unit 4 of AI Control 1. Short framing prose restates the three-part shape every portfolio answer in these lessons takes (allocation, margin, binding constraint), glosses Plans A to D, and states the brief itself (10 researchers' worth of effort per scenario, seven agendas, half-researcher steps), then hands the learner the long exercise as a widget: three stipulated regimes stacked one after another, each with its own allocation sliders and two written defences. The widget computes how far each agenda moved across the three regimes and reports it. There is no answer key; the diagnostic is whether the allocation responds to the three states. A short graded practice question after the widget asks the learner to update their Scenario 3 split after a change in public mood. The widget's saved summary carries the learner's numbers and defences into your context. If they ask for help, push on the fit between the numbers and the stated margin, not toward a model portfolio."
reading_minutes: 50
tutor_minutes: 2
tags: []
---
#### Text
content::
You now have the whole regime model, and everything the analysis takes is already in your hands from the previous lesson and readings: read the three states, price each technique's basket against the regime's price table, and ask which channel (usefulness, evidence, direct) its payoff flows through.

All portfolio answers in these lessons take a three-part shape:

1. **The allocation**: how effort splits across the available techniques
2. **The margin**: where the next unit of effort goes, and through what mechanism
3. **The binding constraint**: the one allocation the team would trade any other for

#### Text
content::
\## Long exercises

Now run the machinery yourself. Each scenario gives you the three states: the misalignment world you are probably in, the capability stage you are approaching, and the plan you start under. From that, make the call these lessons have been building toward: where does the next unit of effort go?

Alongside the three states, each regime names the capability stage it is approaching in the [AI Futures Model](https://blog.ai-futures.org/p/ai-futures-model-dec-2025-update)'s milestones and the initial plan it starts under, in the sense of [[../Lenses/XLab Control - plans-a-b-c-and-d-for-misalignment-risk|Plans A, B, C, and D for misalignment risk]]. Roughly, A = a strong international agreement buys a long slowdown, B = the government treats buying lead time (a time advantage over rival developers that can be spent on safety work instead of racing) as a national-security priority, C = the leading lab spends its few-months lead on safety without government help, D = leadership isn't taking the risk seriously and a small safety team works with what it has.

In each scenario you direct a safety team with 10 researchers' worth of effort, to divide across seven agendas in half-researcher steps. Set the split, then write the two short defences: the margin and the binding constraint.

#### Widget
source:: [[../widgets/xlab-control-portfolio-allocation]]
required:: true

#### Question: Open
id:: 23b7c81c-d4da-4571-9848-22f576fe7c30
content::
\## Practice: when the regime moves

Go back to your split for Scenario 3 (apparent-success seekers under commercial pressure). Six months later, an AI agent at another company causes a widely reported failure, and the public becomes scared rather than annoyed. Your leadership now accepts a noticeably slower, less useful product, though the safety team is still the same size and the other facts of Scenario 3 hold.

Which parts of the regime does this change, and which does it leave alone? Which part of the regime now most limits what your team can achieve, and why? How should your split of the 10 researchers move, if at all, and where does the next half researcher go now?
placeholder:: About 100 to 200 words. Refer to your Scenario 3 numbers.
assessment-instructions:: Score 0 to 100. This is practice. Credit: (1) about 30 points for saying what changes and what does not: what can be afforded changes (a scared public and leadership now make the usefulness cost of safety measures affordable), while what the models are like and what the lab can know about them are unchanged by this event, since it happened elsewhere; a learner who argues the event also changes what the lab knows (for example as evidence about agents in general) earns credit if they say why. (2) about 15 points for naming the part that now most limits the team with a reason tied to the scenario, for example that what the lab can know about research quality is now the tightest limit because usefulness has become affordable, or that the small team size still binds; (3) about 35 points for a change to the split that follows, with a reason, for example moving effort toward measures whose main cost is product usefulness, such as control protocols that slow or check agents, or toward verification of research quality, the weak spot in what the lab can know; keeping the split unchanged earns these points only with a reason. (4) about 20 points for naming where the next half researcher goes and the mechanism by which it reduces risk. Do not grade the split against a model portfolio; grade whether it follows from the change. Accept any terminology. A pass is roughly 60.
feedback-instructions:: One turn, at most six sentences. Say which part of the regime the learner identified as changed, whether their choice of the most limiting part has a reason, and whether their split moved in a way that follows from it, quoting their numbers where it helps. Then state the key point in full: an event elsewhere mainly changes what the lab can afford (here, the usefulness cost of safety becomes cheaper), not what its own models are like or what it can know about them, so the split should move toward work whose main price is usefulness. Do not mention scores. No follow-up question. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "Plans A, B, C, and D for misalignment risk." *Redwood Research blog*, 8 Oct. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/plans-a-b-c-and-d-for-misalignment)
*The source of the A to D plans each scenario starts under, and of the definition of lead time used above.*

Kokotajlo, Daniel. "AI Futures Model: Dec 2025 Update." *AI Futures Project*, 28 Jan. 2026. [blog.ai-futures.org](https://blog.ai-futures.org/p/ai-futures-model-dec-2025-update)
*The model whose capability milestones name the stage each scenario is approaching: automating the lab's coding, running research autonomously, or multiplying human researchers without working unsupervised.*

XLab. "Running the model." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/how-useful-is-ai-control/running-the-model)
*The source lesson this page adapts.*
:::
