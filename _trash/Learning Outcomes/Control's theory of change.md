---
id: 'aa99d49e-557d-43b3-be41-ef5b64c764dc'
learning-outcome: "For a proposed AI control measure or project, lay out the distinct causal routes by which it could reduce the risk of catastrophe from AI models that might be scheming (for example stopping an attack while the model is in use, catching an attempt and acting on the evidence, getting useful safety work out of untrusted models before they become too capable to control, or making control evidence a condition for deployment), say for each route how far it depends on the political will of AI developers and governments, and identify the premise most open to doubt together with an observation that would raise or lower confidence in it."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - James agent ready-34 (Opus 5.5)
---
## Test:
id:: 45016776-5de7-48f1-a79a-f860dbd2af3d

#### Question: Open
id:: 74ae927b-76a0-4c1d-a061-31544ba9b32e
content::
A foundation is deciding whether to fund a small team at a frontier AI company. The team would build and run monitoring for the company's internal coding agents: a weaker model that the company trusts reviews every action the agents take, sends the most suspicious ones to human reviewers, and blocks the very most suspicious ones before they run.

1. Describe two distinct routes by which this project could lower the chance of an AI catastrophe. For each, spell out the steps from what the team does to less risk.
2. For each of your two routes, say whether it still works if the company's leadership cares little about misalignment risk and no government requires anything, and why.
3. Name the premise in your routes that you find most open to doubt, say why, and name one observation that would raise or lower your confidence in it.
placeholder:: Answer all three parts. About 250 to 400 words.
assessment-instructions:: Score out of 100. Grade reasoning, not which conclusion the learner reaches: an answer that concludes the project would do little, or a lot, can score full marks if it is argued. 40 for part 1, 20 per route. A route earns its 20 when it states a mechanism and the steps from what the team does to lower risk, for example: (a) blocking or stopping an attack while the agents are in use, so a scheming agent cannot complete a dangerous action such as inserting a security hole or copying model weights. (b) Catching an agent in an attempt, which produces evidence that leads to a response, such as the company or governments slowing down or stopping, or the team studying the attempt and improving its defences. (c) Letting the company get useful work, including safety research, out of agents it does not trust, during a period before AI becomes too capable to control. (d) Building practice, tools and evidence that let regulators or other companies require or adopt control, for example as part of a safety case. Other mechanisms count if the steps are stated. A route given only as a label with no steps ("it catches AIs") earns at most 10. If the second route is the same mechanism as the first, it earns at most 5. 30 for part 2, 15 per route: a verdict on whether the route works under low political will, with a reason that says what the route needs from whom. Examples of sound reasoning: blocking can work with only the team's own effort, but leadership may switch it off or override it if it slows work. Acting on a catch needs leadership or governments to respond to the evidence, and with little will they may explain it away, though the team can still use the catch to improve its own monitoring. The useful-work route needs the company not to race straight on to models too capable to control, and to spend some of the AI labour on safety. A regulatory route needs a government or industry body willing to require it. Either verdict scores if the reason is sound. A verdict with no reason earns at most 5 per route. 30 for part 3: 15 for naming a premise that one of the learner's routes actually needs and saying why it is open to doubt; 15 for an observation someone could actually make that bears on that premise and says which way it would move confidence (for example, a red team using a strong model gets an attack past the monitor or fails to, a company that catches a misbehaving model announces it and pauses or plays it down and keeps going, engineers start bypassing the monitor because of false alarms, or a regulator adopts or declines a control requirement). "More research" or "we will see" is not an observation and earns 0 of those 15. Model answer, for the feedback, not a grading checklist: "Route 1: the monitor reviews agent actions and blocks the most suspicious, so a scheming agent that tries to insert a backdoor into security code is stopped before the code runs, and an attack that would have succeeded does not. Route 2: when the monitor flags an attempt and humans confirm it, the company has hard evidence that its model is scheming; it can stop using the model, study the attempt to improve its defences, and show the evidence to others, which may lead to slower and more careful development. Under low will, route 1 mostly still works because the team runs it itself, as long as leadership does not switch it off when it slows work. Route 2 depends heavily on will: a careless leadership can call the incident a fluke and keep going, though the team can still use it to improve the monitor. Most doubtful premise: that a catch would change what the company or governments do. If a company that catches its model in an attempt announces it and pauses, that would raise my confidence. If the model is quietly patched and kept in use, that would lower it."
feedback-instructions:: Name the strongest part of the answer in one sentence, quoting the learner's words where it helps. Then name the single change that would most improve it, for example a route given as a label without steps, two routes that are really the same mechanism, a will-dependence verdict with no reason, or an observation nobody could actually make. If the learner asks about their score, explain plainly what earned and what lost points. Do not tell the learner whether the project is worth funding. At most five sentences. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Control in a low-investment world]]
notes:: Buck Shlegeris on 80,000 Hours: why control matters in a world that invests little in safety.

## Lens:
source:: [[../Lenses/AICF - Using AI while it can still be controlled]]
notes:: The window route, from the case for control, with Emmett Shear's objection as quoted by Richard Ngo, Ngo's reply and aysja's reply.

## Lens:
source:: [[../Lenses/AICF - Habryka and Greenblatt on what control is for]]
notes:: The routes stated by a critic and accepted by a proponent, then the critic's main fears.

## Lens:
source:: [[../Lenses/AICF - Catching AIs red-handed]]
notes:: Why a catch counts as a win: catch-then-shut-down and few-shot catastrophe prevention.

## Lens:
source:: [[../Lenses/AICF - Would a catch change anything]]
notes:: Shlegeris doubts that a catch would make developers slow down, with replies from Davidson and Habryka.

## Lens:
source:: [[../Lenses/XLab Control - plans-a-b-c-and-d-for-misalignment-risk]]
notes:: Plans by level of political will.

## Lens:
source:: [[../Lenses/AICF - Ten people on the inside]]
notes:: The low-will route and its critics.

## Lens:
source:: [[../Lenses/AICF - Control as a safety case]]
notes:: The regulatory route: control evidence as a condition for deployment.
