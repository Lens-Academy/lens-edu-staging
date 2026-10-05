---
id: 'cf7ca5d2-9705-4d26-a8cb-39e99681ff20'
slug: ai-control-fundamentals-u3
title: "Unit 3: Why people work on control"
---
%% Unit 3 of AI Control Fundamentals: control's theory of change. Time (reading+tutor): welcome 3+3, low-investment world (80k) 6+6, window 6+6, should we invest (with Carlsmith) 11+14, Habryka/Greenblatt 10+12, catching 8+7, would a catch 11+12, Plans A-D 10+10, ten people 9+10, will companies 6+8, safety case (with Anthropic risk reports) 9+11, practice 3+15 = 206, plus about 15 for the LO test, about 220 minutes. Catching (2) is optional. %%

# Learning Outcome:
source:: [[../Learning Outcomes/Theory of change for AI control]]

# Lens: Welcome to Unit 3
id:: 64af1a58-6f9e-4a92-bf67-61399abc7f3b
reading_minutes:: 3
tutor_minutes:: 3
tldr:: Control is supposed to make an AI catastrophe less likely, but by which routes, and what does each route need from AI companies and governments? This unit reads people who work on control and people who doubt them.
summary_for_tutor:: Opening lens of Unit 3 of AI Control Fundamentals, written by Lens. Unit 1 covered what control is. This unit covers control's theory of change: the routes by which it is supposed to reduce risk (blocking attacks while a model is in use, catching attempts and acting on the evidence, getting useful work out of untrusted models during a window before they are too capable to control, and making control a condition of deployment), how much each route depends on the political will of AI companies and governments, and which premises are open to doubt. The learner writes a first guess at how control reduces risk. Do not grade it or correct it. Acknowledge it briefly and send the learner on.
#### Text
content::
In Unit 1 you saw what control is and how it is tested. This unit asks why people work on it: by which routes is control supposed to make an AI catastrophe less likely? You will read people who work on control explaining those routes, and people who doubt them, including doubts from control researchers themselves. One question runs through the unit: how much does each route need AI companies and governments to want to act on AI risk?

\## In this unit you will

- Read Buck Shlegeris on why control matters in a world that invests little in AI safety.
- Read the argument that controlled AI could do useful safety work during a window before AI becomes too capable to control, and replies to it.
- Read a critic and a control researcher discussing what control is for.
- Read why catching an AI in an attempt counts as a win, and whether a catch would change what AI developers do.
- Read Ryan Greenblatt's plans for different levels of political will, and what ten safety-minded people inside a careless company could do.
- Hear how much Shlegeris expects AI companies to actually do, see how control could become a condition for deploying a model, and read what one AI company's risk reports rely on monitoring for.
- Practise mapping the routes and finding the premise most open to doubt.

#### Question: Open
id:: 5372c08e-c3ae-48ac-8b01-18be0b0cb327
content::
Before you read: in one or two sentences, how do you think control is supposed to make an AI catastrophe less likely? A guess is fine. You will meet several answers in this unit, and look back at your guess in the practice at the end.
force-feedback:: first
feedback-instructions:: This is an ungraded first guess. In two or three sentences, reflect back the route the learner described, in their words, without saying whether it is right or adding routes they did not name. Do not preview the unit. Do not ask a follow-up question. Close by sending them to the first reading. No generic praise.

# Lens:
source:: [[../Lenses/AICF - Control in a low-investment world]]

# Lens:
source:: [[../Lenses/AICF - Using AI while it can still be controlled]]

# Lens:
source:: [[../Lenses/AICF - Should we invest in control]]

# Lens:
source:: [[../Lenses/AICF - Habryka and Greenblatt on what control is for]]

# Lens:
source:: [[../Lenses/AICF - Catching AIs red-handed]]

# Lens:
source:: [[../Lenses/AICF - Would a catch change anything]]

# Lens:
source:: [[../Lenses/AICF - Plans A to D for misalignment risk]]

# Lens:
source:: [[../Lenses/AICF - Ten people on the inside]]

# Lens:
source:: [[../Lenses/AICF - Will AI companies do this]]

# Lens:
source:: [[../Lenses/AICF - Control as a safety case]]

# Lens: Practice: mapping control's routes
id:: 4b05ca05-1d3d-4685-a76c-ce80a1f68c66
reading_minutes:: 3
tutor_minutes:: 15
tldr:: Take one control project, lay out the routes by which it could lower risk, say what each needs from the people in charge, and find the premise you trust least.
summary_for_tutor:: Practice exercise at the end of Unit 3 of AI Control Fundamentals, before the learning-outcome test on control's theory of change. The scenario: a government AI safety institute funds a team that runs control evaluations on AI companies' internal agent deployments (with permission), gives each company its results and publishes a template safety case. Part 1 asks for two or more distinct routes from the tool to lower risk, each with steps, and for each route how much it depends on the political will of AI companies and governments. Part 2 asks for the premise the learner trusts least and an observation that would change their confidence in it. Routes from the unit: blocking attacks while models are in use, catching attempts and acting on the evidence (the company, governments, or the safety team studying the attempt), getting useful safety work out of untrusted models during a window before they are too capable to control, making control cheap enough that a few insiders at a careless company can get it adopted, and making control a condition of deployment through safety cases, standards or regulation. Grade nothing. Give feedback that helps the learner do the same thing on an unfamiliar case.
#### Text
content::
In the test at the end of this unit you will get a control project you have not seen and be asked to lay out how it could reduce risk. Practise on this one first. The tutor gives feedback after each part.

**The project.** A government AI safety institute funds a team that runs control evaluations on AI companies' internal deployments of AI agents. With each company's permission, a red team builds attack versions of the company's model and tests whether the company's safety measures stop them. The team gives each company its results, and publishes a template safety case that any company or regulator can use.

#### Question: Open
id:: f15b1e9e-0289-4e41-af64-2b7e9dab3ba9
content::
\## Part 1: the routes

Describe at least two distinct routes by which this project could lower the chance of an AI catastrophe. For each route, write the steps from "the team runs an evaluation" to "less risk". Most routes need someone other than the team to act: say who. Then say, for each route, whether it still works at a company whose leadership cares little about misalignment risk, in a country whose government requires nothing, and why: what does the route need, and from whom?
placeholder:: Two or three short paragraphs.
force-feedback:: first
feedback-instructions:: The learner is practising for the Unit 3 test on control's theory of change. The project: a government institute's team runs control evaluations (red-team attack versions of a company's model against its safety measures) on companies' internal agent deployments, with permission, gives each company its results, and publishes a template safety case. Plausible routes: (a) Fixing weaknesses: the company learns where its measures fail and fixes them, so real attacks are more often blocked or caught. This needs the company to permit the evaluation and act on the findings, which a careless leadership may not do, though a few safety-minded insiders might use the results. (b) A condition of deployment: the template makes it practical for a company policy, an industry body or a regulator to require a passing control safety case before deployment. This needs someone with the authority and will to require it and to refuse deployment when the case fails. (c) Evidence of risk: results showing that attacks get through, or what the models can do, inform company leaders and governments and may build political will, but only if people believe and act on them (compare Shlegeris's doubts about whether even a catch would move developers). (d) Keeping the window usable: better tested measures let companies use untrusted models, including for safety work, while they can still be controlled, which needs the company not to race on to uncontrollable models. Under no political will at all, the project mostly depends on voluntary permission and insiders. Accept other routes if the steps hold. Reply in at most six sentences. Say which of the learner's routes are distinct mechanisms with steps and which are labels or repeats of one mechanism. For each route, say whether the will-dependence reasoning holds up, and name the most useful thing missing. If the learner gives only one route, ask for a second that works by a different mechanism. Accept routes not on this list if the steps hold. Do not say whether the project is worth funding. If the learner says they do not understand, give one foothold: ask what the company does on the day it receives a report saying the red team got an attack through. No generic praise. At most two turns, then send them to Part 2.

#### Question: Open
id:: 251e2cbf-3eb7-41fb-932e-0807f6c461ce
content::
\## Part 2: the weakest premise

Which premise in your routes do you trust least? Say why. Then name one thing someone could actually observe that would change your confidence in it, and say whether it would raise or lower it.

Finally, look back at the guess you wrote at the start of this unit. Which route was it, and which routes have you added since?
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner is practising for the Unit 3 test on control's theory of change. A good answer names a premise one of their routes actually needs (for example: companies give permission and fix what the evaluations find, the red team can find attacks as good as a much stronger model would, results showing failures change what companies or governments do, a regulator would require a control safety case, or the window before uncontrollable AI lasts long enough to use), gives a reason it is doubtful, and names an observation someone could actually make that bears on it and says which way it would move confidence. "More research" or "time will tell" is not an observation. Reply in at most five sentences. Say whether the premise is one their routes need, whether the reason holds, and whether the observation is something that could be seen, and fix the weakest of the three. Do not tell the learner which premise is the right one. No generic praise. At most two turns. If the learner compared their first guess with the unit's routes, acknowledge it in one sentence without judging the guess. Close by telling them the test asks for the same things on a different project, that it also asks in which of Greenblatt's Plans A to D their most will-dependent route would still work, and that at least one of their test routes should work through something other than the monitor blocking or flagging an attack, or responses to a flagged attack.

# Lens:
optional:: true
source:: [[../Lenses/XLab Control - catching-ais-red-handed-2]]
