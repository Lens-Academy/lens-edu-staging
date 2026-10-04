---
id: 'f8a03687-29ce-4f00-b5b9-261cab006690'
learning-outcome: "For a proposed AI control measure or project, lay out the distinct causal routes by which it could reduce the risk of catastrophe from AI models that might be scheming (for example stopping an attack while the model is in use, catching an attempt and acting on the evidence, getting useful safety work out of untrusted models before they become too capable to control, or making control evidence a condition for deployment), say for each route how far it depends on the political will of AI developers and governments, and identify the premise in those routes most open to doubt together with an observation that would raise or lower confidence in it."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - James agent ready-34 (Opus 5.5)
---
## Test:
id:: e0c79f80-090e-413b-97b3-73b43e8db435

#### Question: Open
id:: 962a30ed-d4d0-4c8c-b26f-7704048d921e
content::
A foundation is deciding whether to fund a small team at a frontier AI company. The team would build and run monitoring for the company's internal coding agents: a weaker model that the company trusts reviews every action the agents take, sends the most suspicious ones to human reviewers, and blocks the very most suspicious ones before they run.

1. Assume the agents might be deliberately trying to cause harm. Describe two distinct routes by which this project could lower the chance of an AI catastrophe. For each, spell out the steps from what the team does to less risk. At least one of your routes should work through something other than the monitor blocking or flagging an attack, or responses to a flagged attack.
2. For each of your two routes, say how far it still works if the company's leadership cares little about misalignment risk and no government requires anything. Say why: what does the route need, and from whom? Then take the route that depends most on political will and place it on this scale of worlds, from most to least political will: (A) governments agree internationally to slow AI down for many years, (B) the US government makes keeping US AI companies ahead a top priority, which buys one to three years, (C) governments do little, but the leading AI company's leadership is willing to spend its few months of lead on misalignment risk, (D) the leading company does not take misalignment seriously, but 10 to 30 employees inside do and have a small share of compute. What is the lowest of these levels at which the route still works, and why?
3. Name the premise in your routes that you find most open to doubt and say why. Then name one observation that would change your confidence in it, and say whether it would raise or lower it.
placeholder:: Answer all three parts, in about 300 to 450 words.
assessment-instructions:: Score out of 100. Grade reasoning, not which conclusion the learner reaches: an answer that concludes the project would do little, or a lot, can score full marks if it is argued. 40 for part 1, 20 per route. A route earns its 20 when it states a mechanism and the steps from what the team does to lower risk, for example: (a) Blocking or stopping an attack while the agents are in use, so a scheming agent cannot complete a dangerous action such as inserting a security hole or copying model weights. (b) Catching an agent in an attempt, which produces evidence that leads to a response, such as the company or governments slowing down or stopping, or the team studying the attempt and improving its defences. (c) Letting the company get useful work, including safety research, out of agents it does not trust, during a period before AI becomes too capable to control. (d) Building practice, tools and evidence that let regulators or other companies require or adopt control, for example as part of a safety case. Other mechanisms count if the steps are stated and each step plausibly leads to the next. A route given only as a label with no steps ("it catches AIs"), or with a step that would not plausibly happen, earns at most 10. Two caps can apply in part 1. Same-mechanism cap: if the two routes are the same mechanism, the lower-scoring one earns at most 5. Blocking an attack, deterring attempts, and studying a caught attempt to improve defences count as distinct mechanisms. Flagging cap: if neither route works through something other than the monitor blocking or flagging attacks, or responses to a flagged attack (by this company, other companies or governments, including rules made because of a flagged attack), the lower-scoring route earns at most 10. Deterrence (agents attempt less because they expect to be flagged) and studying a caught attempt both count as working through flagging for this cap. When both caps apply to a route, apply only the lower one, and never cap both routes. The order in which the learner lists the routes does not matter. 30 for part 2. 10 per route: a verdict on how far the route works under low political will (yes, no or partly), with a reason that says what the route needs from whom. A reason that does not say what the route needs and from whom earns at most 6 ("only the team itself" counts as saying from whom). Examples of sound reasoning: blocking can work with only the team's own effort, but leadership may switch it off or override it if it slows work. Acting on a catch needs leadership or governments to respond to the evidence, and with little will they may explain it away, though the team can still use the catch to improve its own monitoring. The useful-work route needs the company not to race straight on to models too capable to control, and to spend some of the AI labour on safety. A regulatory route needs a government or industry body willing to require it. Any verdict, including "partly", scores if the reason is sound. A verdict with no reason earns at most 3 per route. 10 for placing the more will-dependent route on the scale in the question (A, an international agreement to slow down for years. B, the US government prioritises keeping US companies ahead, one to three years. C, only the leading company's leadership is willing to spend a few months of lead on misalignment. D, the company does not care, only 10 to 30 employees do, with a small share of compute.): the lowest level at which it still works, with a reason that matches what the route needs to who holds the will at that level. For example, a route that needs a regulator or government requirement needs at least B or A, a route that needs leadership to act on a catch needs at least C, and a route the team runs itself with little compute can still work in D. Any level scores if the reason fits the scale's descriptions. A level with no reason, or a reason that contradicts the description of that level, earns at most 4. 30 for part 3: 15 for naming a premise that one of the learner's routes actually needs and saying why it is open to doubt (a premise with no reason earns at most 5). 15 for an observation someone could actually make that bears on that premise and says which way it would move confidence (for example, a red team using a strong model gets an attack past the monitor or fails to, a company that catches a misbehaving model announces it and pauses or plays it down and keeps going, engineers start bypassing the monitor because of false alarms, or a regulator adopts or declines a control requirement). An observation that does not say which way it moves confidence earns at most 10. "More research" or "we will see" is not an observation and earns 0 of those 15. Model answer, for the feedback, not a grading checklist: "Route 1: the monitor reviews agent actions and blocks the most suspicious, so a scheming agent that tries to insert a backdoor into security code is stopped before the code runs, and an attack that would have succeeded does not. Route 2: running monitoring on real agents shows that it works and what it costs. Other companies can copy it, and a regulator or industry body can make it a requirement, so agents at other companies are monitored too and attacks there are also blocked or caught. Under low will, route 1 mostly still works because the team runs it itself, as long as leadership does not switch it off when it slows work. Route 2 works only partly: other companies may copy a cheap, proven setup on their own, but a requirement needs a government or industry body willing to impose it. Route 2 depends more on political will. Its requirement part needs at least level B, because only there does a government care enough to impose rules, though voluntary copying could happen at C. Most doubtful premise: that a regulator or industry body would require monitoring, because companies may push back on anything that slows their agents and governments have so far required little. If a government or industry body adopts a control requirement, that would raise my confidence. If proposals for one are dropped after company pushback, that would lower it."
feedback-instructions:: Name the strongest part of the answer in one sentence, quoting the learner's words where it helps. Then name the single change that would most improve it, for example a route given as a label without steps, two routes that are really the same mechanism, a will-dependence verdict with no reason, or an observation nobody could actually make. If the score is 100, just confirm. If the learner asks about their score, explain plainly what earned and what lost points. Do not change the score. Do not tell the learner whether the project is worth funding. At most five sentences. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Control in a low-investment world]]
notes:: Buck Shlegeris on 80,000 Hours: why control matters in a world that invests little in safety.

## Lens:
source:: [[../Lenses/AICF - Using AI while it can still be controlled]]
notes:: The window route, from the case for control, with the authors' own limits on it.

## Lens:
source:: [[../Lenses/AICF - Should we invest in control]]
notes:: The two claims the case for working on control rests on, then Emmett Shear's objection as quoted by Richard Ngo, Ngo's reply and aysja's reply, then Joe Carlsmith on the ways the window (his "sweet spot") could fail.

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
source:: [[../Lenses/AICF - Plans A to D for misalignment risk]]
notes:: Plans by level of political will, and which routes still fit when will is lowest.

## Lens:
source:: [[../Lenses/AICF - Ten people on the inside]]
notes:: The low-will route and its critics.

## Lens:
source:: [[../Lenses/AICF - Will AI companies do this]]
notes:: Shlegeris on levels of control investment and how much buy-in each needs.

## Lens:
source:: [[../Lenses/AICF - Control as a safety case]]
notes:: The regulatory route: control evidence as a condition for deployment, then what Anthropic's own risk reports rely on monitoring for and where they say it falls short.
