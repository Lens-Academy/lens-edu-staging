{++{"author":"Lauren's AI","timestamp":1786083452724}@@---
id: '6d47e55b-f642-42ea-a6e7-5eb8645db491'
title: Compute-Centric Numbers
summary_for_tutor: "Optional deep-dive on Tom Davidson's compute-centric takeoff model, plus his six-milestones framing. The value is not the headline number (a four-OOM capability gap compressed to roughly three years) but seeing how a model of this kind is assembled and where its parameters come from. The exercise makes the student find the parameter the conclusion is most sensitive to, which is the transferable skill. Also converts 'timelines' from one date into a sequence of thresholds."
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

**Second, read Davidson's *Six milestones for AI automation*.**

This one does something different and arguably more useful: it replaces "when does transformative AI arrive" with a sequence of thresholds, each with its own arrival estimate. That structure transfers to almost any question about a technology arriving.

#### Question
content::
\## Find the load-bearing parameter

1. Davidson's model has many inputs. Identify the one you believe the three-year conclusion is most sensitive to: the parameter where a factor-of-two disagreement would most change the answer. Say why you picked it.
2. For that parameter, say where its value came from. Measured from data, estimated by analogy to another domain, or chosen as a reasonable-seeming assumption? Be specific about which.
3. Now the useful move. What is the *smallest* change to that parameter that flips the conclusion from "roughly three years" to something you would describe as gradual? If it takes a wild change, the conclusion is robust in that direction; if a modest one does it, you have found the crux.
4. Separately, on the six milestones: name a threshold you think is missing from his sequence, or argue that the sequence structure itself misleads. What does decomposing into thresholds buy you over a single date, and what does it cost?

assessment-instructions:: Optional deep-dive after the main takeoff lens. The student is here by choice; push hard.

The capability being exercised: sensitivity analysis on a model you did not build. This is the practical form of the whole unit's skill, and it is the closest thing here to what a working forecaster actually does.

Key concepts:
- The high-sensitivity parameters in models of this shape are typically the returns-to-research-effort exponent (how much harder each further improvement is, which is the recalcitrance question in another dress) and the fraction of AI research that automation can actually cover. Students may reasonably pick either, or another, if they argue it.
- Question 2 matters because these parameters differ sharply in provenance: some are fit to historical data on research productivity, some are analogised from other technologies, and some are judgment calls. A student who cannot tell which is which is treating the model as more measured than it is.
- Question 3 is the payoff: a conclusion that survives large parameter changes is robust; one that needs a specific value is a restatement of an assumption. Either finding is worth having, and the student should report which they found rather than assuming the answer.
- On the milestones: decomposition buys checkability, since each threshold can be independently observed and graded as it arrives, and it converts one unfalsifiable date into a sequence of near-term tests. It costs completeness, since a sequence asserts an ORDER, and a capability arriving out of order breaks the frame rather than merely adjusting it.

Response length: 120 to 200 words. Short paragraphs only.

Response style:
- Calm and rigorous. Do not over-validate; avoid generic praise.
- Do not defend or attack Davidson's conclusion. The point is the method.
- If the student picks a parameter without justifying sensitivity, ask what a factor-of-two change to it would actually do downstream.
- If the student cannot answer question 3, that is fine and common; suggest they reason qualitatively about direction and magnitude rather than abandoning it.

Conversation flow: keep an internal turn counter, up to 3 replies, then close by naming whether they found the conclusion robust or crux-dependent, and what that implies about how much weight to put on the three-year figure.
++}