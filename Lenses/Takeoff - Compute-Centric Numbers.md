---
id: '6d47e55b-f642-42ea-a6e7-5eb8645db491'
title: Compute-Centric Numbers
summary_for_tutor: "Optional deep-dive on Tom Davidson's compute-centric takeoff model, plus Ajeya Cotra's six-milestones framing. The value is not the headline number (a four-OOM capability gap compressed to roughly three years) but seeing how a model of this kind is assembled and where its parameters come from. The exercise makes the student find the parameter the conclusion is most sensitive to, which is the transferable skill. Also converts 'timelines' from one date into a sequence of thresholds."
tldr: Somebody actually built the model. Davidson's compute-centric framework turns the takeoff argument into parameters you can disagree with one at a time, which is the only kind of disagreement that goes anywhere.
tags:
  - optional
---
#### Text
content::
\## Reading Assignment

**First, read Tom Davidson's *What a Compute-Centric Framework Says About Takeoff Speeds*.**

This is the takeoff argument as an actual model: growth in effective compute, returns to research effort, and the automation of AI research itself, assembled into something that produces numbers. Roughly, it compresses a four-order-of-magnitude capability gap into about three years.

Read for the assembly, not the number. Where does each parameter come from? Which are measured, which are estimated from analogy, and which are essentially chosen?

#### Article
source:: [[../articles/giving-what-a-compute-centric-framework-says-about-takeoff-speeds]]

#### Text
content::
**Second, read Ajeya Cotra's *Six milestones for AI automation*.**

This one does something different, and to our eye more useful: it replaces "when does transformative AI arrive" with a sequence of thresholds, each with its own arrival estimate. That structure transfers to other questions about a technology arriving, which is why it is worth learning here rather than only for AI.

#### Article
source:: [[../articles/cotra-six-milestones-for-ai-automation]]

#### Question: Open
id:: 20718618-28ec-46b3-a3a4-f699048bac1c
content::
\## Find the load-bearing parameter

1. Davidson's model has many inputs. Identify the one you believe the three-year conclusion is most sensitive to: the parameter where a factor-of-two disagreement would most change the answer. Say why you picked it.
2. For that parameter, say where its value came from. Measured from data, estimated by analogy to another domain, or chosen as a reasonable-seeming assumption? Be specific about which.
3. Now the useful move. What is the *smallest* change to that parameter that flips the conclusion from "roughly three years" to something you would describe as gradual? If it takes a wild change, the conclusion is robust in that direction; if a modest one does it, you have found the crux.
4. Separately, on the six milestones: name a threshold you think is missing from his sequence, or argue that the sequence structure itself misleads. What does decomposing into thresholds buy you over a single date, and what does it cost?

assessment-instructions:: Score out of 100. Context: Tom Davidson's compute-centric model of AI takeoff has many input parameters and concludes that a large capability gap is crossed in roughly three years. Ajeya Cotra's six milestones replace one arrival date for transformative AI with a sequence of thresholds, each with its own estimate. Any parameter may be picked. Grade the reasoning, not the pick. 25: names one input of the model and gives a reason why the three-year conclusion depends on it more than on other inputs (what a factor-of-two change in it would do to the result). 15: says where that parameter's value came from, as measured from data, estimated by analogy to another domain, or chosen as an assumption, and commits to one of these or a stated mix. 30: says roughly how large a change to that parameter would turn the conclusion into one the learner would call gradual. A qualitative estimate of direction and rough size earns the points; an exact number is not needed. 30: on the six milestones, 10 each for three things. First, names a threshold missing from the sequence, or argues that the sequence structure misleads. Second, one thing that splitting into thresholds gains over a single date (for example, each threshold can be checked as it arrives). Third, one thing it costs (for example, a sequence asserts an order, and a capability arriving out of order breaks the frame). Give credit for each point whenever the answer shows the idea, in any wording.
force-feedback:: first
feedback-instructions:: Optional deep-dive after the main takeoff lens. The student is here by choice; push hard.

The capability being exercised: sensitivity analysis on a model you did not build. This is the practical form of the whole unit's skill, and it is the closest thing here to what a working forecaster actually does.

Key concepts:
- OUR HYPOTHESIS, NOT A FINDING, and the student may overturn it: we expect the high-sensitivity parameters in models of this shape to be the returns-to-research-effort exponent (how much harder each further improvement is, which is the recalcitrance question in another dress) and the fraction of AI research that automation can actually cover. Nobody has run a sensitivity analysis on Davidson's model to check this, so grade the ARGUMENT rather than the pick. A student who names a different parameter and says why it dominates is doing the exercise correctly, and if their reasoning is better than ours, say so.
- Question 2 matters because parameters in models of this kind differ in provenance: some are fit to historical data, some are analogised from other technologies, and some are judgment calls. We have not classified Davidson's parameters one by one, so treat this as the general point it is. A student who cannot tell which is which is treating the model as more measured than it is.
- Question 3 is the payoff: a conclusion that survives large parameter changes is robust; one that needs a specific value is a restatement of an assumption. Either finding is worth having, and the student should report which they found rather than assuming the answer.
- On the milestones, our analysis, open to challenge: decomposition buys checkability, since each threshold can be independently observed and graded as it arrives, and it converts one unfalsifiable date into a sequence of near-term tests. It costs completeness, since a sequence asserts an ORDER, and a capability arriving out of order breaks the frame rather than merely adjusting it. A student who argues against either half is doing the exercise, not evading it.

Response length: 120 to 200 words. Short paragraphs only.

Response style:
- Calm and rigorous. Do not over-validate; avoid generic praise.
- Do not defend or attack Davidson's conclusion. The point is the method.
- If the student picks a parameter without justifying sensitivity, ask what a factor-of-two change to it would actually do downstream.
- If the student cannot answer question 3, that is fine and common; suggest they reason qualitatively about direction and magnitude rather than abandoning it.

Conversation flow: keep an internal turn counter, up to 3 replies, then close by naming whether they found the conclusion robust or crux-dependent, and what that implies about how much weight to put on the three-year figure.
