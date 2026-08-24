---
id: 03c6328c-09bc-43b4-b1fc-807905ae06c3
tldr: "Individual tests are just tools in a box; frameworks decide how to combine them and what to do with the results. This section covers two kinds: technical frameworks that deliberately build misaligned 'model organisms' to study danger under controlled conditions, and governance frameworks like Anthropic's Responsible Scaling Policy that use evaluation results as gates deciding when it is safe to build more powerful AI."
summary_for_tutor: "Distinguishes evaluation techniques from evaluation frameworks, and technical frameworks from governance frameworks. Explains the Model Organisms framework, which deliberately creates misaligned systems (such as Anthropic's sleeper agents, reward-model sycophancy, and alignment faking) to study dangerous properties with known ground truth. Then covers evaluation-gated scaling and three corporate governance frameworks: Anthropic's Responsible Scaling Policy with AI Safety Levels (ASL), OpenAI's Preparedness Framework with pre- and post-mitigation evaluations, and Google DeepMind's Frontier Safety Framework with Critical Capability Levels (CCLs). Notes their shared reliance on evaluations as decision gates and their compute-based scaling-buffer requirements."
title: "Evaluation Frameworks"
{++{"author":"Elias's AI","timestamp":1787570161908}@@reading_minutes: 15
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Evaluation Frameworks|Evaluation Frameworks]]{++{"author":"Elias's AI","timestamp":1787570161908}@@

#### Text
optional:: true
content::
The model organisms approach deliberately builds misaligned systems in order to study them. Did the section's case for doing that convince you? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
The difference between an evaluation technique and an evaluation framework, and between technical and governance frameworks. The model organisms framework deliberately creates misaligned systems, such as sleeper agents, reward-model sycophancy and alignment faking, so that dangerous properties can be studied with known ground truth, which normal evaluation lacks. The governance side is evaluation-gated scaling, where results decide whether it is safe to build something more powerful, covered through three corporate frameworks: Anthropic's Responsible Scaling Policy with AI Safety Levels, OpenAI's Preparedness Framework with pre-mitigation and post-mitigation evaluations, and Google DeepMind's Frontier Safety Framework with Critical Capability Levels. The section notes what they share: evaluations used as decision gates, and compute-based buffers so that a threshold is not crossed between one evaluation and the next.

topics to explore:
- Building a misaligned system to study it gives you ground truth you cannot get otherwise. What is the cost of that trade?
- A model organism is misaligned because someone made it so. How much does that tell you about misalignment that arises on its own?
- All three governance frameworks are voluntary and self-administered. Does the ground-truth problem matter more, or the marking-your-own-homework problem?
- The scaling buffer assumes you can predict how much capability a given amount of compute buys. Earlier chapters made that look hard. Does the buffer hold?
- If an evaluation gate fired, what would actually have to happen inside a company for it to bind?

Evaluation design, the individual evaluation types and the chapter's limitations come later. Stay with frameworks here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}
