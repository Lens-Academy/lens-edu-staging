---
id: 'cf7ca5d2-9705-4d26-a8cb-39e99681ff20'
slug: ai-control-fundamentals-u3
title: "Unit 3: Why people work on control"
tags:
  - work-in-progress
---
%% TIME_NOTE %%

# Learning Outcome:
source:: [[../Learning Outcomes/Control's theory of change]]

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
- See how control could become a condition for deploying a model.
- Practise mapping the routes and finding the premise most open to doubt.

#### Question: Open
id:: 5372c08e-c3ae-48ac-8b01-18be0b0cb327
content::
Before you read: in one or two sentences, how do you think control is supposed to make an AI catastrophe less likely? A guess is fine. You will meet several answers in this unit.
feedback-instructions:: This is an ungraded first guess. In two or three sentences, reflect back the route the learner described, in their words, without saying whether it is right or adding routes they did not name. Do not preview the unit. Do not ask a follow-up question. Close by sending them to the first reading. No generic praise.

# Lens:
source:: [[../Lenses/AICF - Control in a low-investment world]]

# Lens:
source:: [[../Lenses/AICF - Using AI while it can still be controlled]]

# Lens:
source:: [[../Lenses/AICF - Habryka and Greenblatt on what control is for]]

# Lens:
source:: [[../Lenses/AICF - Catching AIs red-handed]]

# Lens:
source:: [[../Lenses/AICF - Would a catch change anything]]

# Lens:
source:: [[../Lenses/XLab Control - plans-a-b-c-and-d-for-misalignment-risk]]

# Lens:
source:: [[../Lenses/AICF - Ten people on the inside]]

# Lens:
source:: [[../Lenses/AICF - Control as a safety case]]

# Lens: Practice: mapping control's routes
id:: 4b05ca05-1d3d-4685-a76c-ce80a1f68c66
reading_minutes:: 3
tutor_minutes:: 15
tldr:: Take one control project, lay out the routes by which it could lower risk, say what each needs from the people in charge, and find the premise you trust least.
summary_for_tutor:: Practice exercise at the end of Unit 3 of AI Control Fundamentals, before the learning-outcome test on control's theory of change. The scenario: a researcher releases a free, open-source trusted-monitoring tool that any AI company can switch on in a day. Part 1 asks for two or more distinct routes from the tool to lower risk, each with steps, and for each route how much it depends on the political will of AI companies and governments. Part 2 asks for the premise the learner trusts least and an observation that would change their confidence in it. Routes from the unit: blocking attacks while models are in use, catching attempts and acting on the evidence (the company, governments, or the safety team studying the attempt), getting useful safety work out of untrusted models during a window before they are too capable to control, making control cheap enough that a few insiders at a careless company can get it adopted, and making control a condition of deployment through safety cases, standards or regulation. Grade nothing. Give feedback that helps the learner do the same thing on an unfamiliar case.
#### Text
content::
In the test at the end of this unit you will get a control project you have not seen and be asked to lay out how it could reduce risk. Practise on this one first. The tutor gives feedback after each part.

**The project.** A researcher releases a free, open-source monitoring tool. Any AI company can switch it on in a day. A small model the company already trusts reads every action its AI agents take, flags suspicious actions for human review, and can pause an agent until a human looks.

#### Question: Open
id:: f15b1e9e-0289-4e41-af64-2b7e9dab3ba9
content::
\## Part 1: the routes

Describe at least two distinct routes by which this tool could lower the chance of an AI catastrophe. For each route, write the steps from "a company switches the tool on" to "less risk". Then say, for each route, whether it still works at a company whose leadership cares little about misalignment risk, in a country whose government requires nothing, and why.
placeholder:: Two or three short paragraphs.
feedback-instructions:: The learner is practising for the Unit 3 test on control's theory of change. Routes the unit covered: (a) blocking: the tool pauses a dangerous action before it runs, which needs only the tool to be on and humans to review, but a careless leadership may turn it off if it slows work; (b) catch and act: a flagged and confirmed attempt is evidence, and the company can stop using the model, study the attempt to improve its defences, or show the evidence to others, and the outside response depends heavily on political will (Shlegeris doubts even a clear catch would make developers slow down); (c) useful work under control: the company can use agents it does not trust for safety work during a window before models are too capable to control, which needs the company not to race straight on to uncontrollable models; (d) cheap adoption: because the tool is free and quick to switch on, a few safety-minded insiders at a careless company might get it adopted, which is the low-will route (critics such as Zac Hatfield-Dodds and Rohin Shah doubt such insiders have the influence); (e) a standard or condition of deployment: a ready tool makes it easier for a regulator, an industry body or a company policy to require control, which needs someone with authority to require it. Reply in at most six sentences. Say which of the learner's routes are distinct mechanisms with steps and which are labels or repeats of one mechanism. For each route, say whether the will-dependence reasoning holds up, and name the most useful thing missing. If the learner gives only one route, ask for a second that works by a different mechanism. Accept routes not on this list if the steps hold. Do not say whether the tool is worth building. If the learner says they do not understand, give one foothold: ask what happens on the day the tool flags its first real attempt. No generic praise. At most two turns, then send them to Part 2.

#### Question: Open
id:: 251e2cbf-3eb7-41fb-932e-0807f6c461ce
content::
\## Part 2: the weakest premise

Which premise in your routes do you trust least? Say why. Then name one thing someone could actually observe that would raise or lower your confidence in it.
placeholder:: A few sentences.
feedback-instructions:: The learner is practising for the Unit 3 test on control's theory of change. A good answer names a premise one of their routes actually needs (for example: a careless company keeps the tool on when it slows work, a small trusted model can spot attacks from a much stronger model, a catch changes what companies or governments do, the window before uncontrollable AI lasts long enough to use, safety work done by untrusted AI can be checked, or a regulator would require control), gives a reason it is doubtful, and names an observation someone could actually make that bears on it and says which way it would move confidence. "More research" or "time will tell" is not an observation. Reply in at most five sentences. Say whether the premise is one their routes need, whether the reason holds, and whether the observation is something that could be seen, and fix the weakest of the three. Do not tell the learner which premise is the right one. No generic praise. At most two turns. Close by telling them the test asks for the same three things on a different project.

# Lens:
optional:: true
source:: [[../Lenses/XLab Control - catching-ais-red-handed-2]]
