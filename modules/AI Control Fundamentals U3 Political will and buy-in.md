---
id: 'ae3b4323-1c59-4093-aa58-861333f1caa3'
slug: ai-control-fundamentals-u3-will
title: "Political will and buy-in"
---
%% Part 3 of Unit 3 of AI Control Fundamentals (split into modules by topic, Elias 2026-10-08). %%

# Learning Outcome:
source:: [[../Learning Outcomes/Theory of change for AI control]]

# Lens: The routes so far
id:: d1b901e8-6075-403d-86dd-f1898021f159
reading_minutes:: 1
tutor_minutes:: 0
tldr:: Three ways control is supposed to lower the risk of an AI catastrophe, which the rest of the unit calls routes: stopping attacks, catching an AI red-handed, and the window.
summary_for_tutor:: Short Lens-written summary in Unit 3 of AI Control Fundamentals, before Greenblatt's Plans A to D. It names the three routes the unit has covered so far, so later questions can refer to them: stopping attacks (monitors block or replace dangerous actions while the AI works), catching it red-handed (catch an attempt, then shut down or study it so later attempts fail), and the window (use AIs that are useful but still controllable to speed up safety work before AIs become too capable to control). One more route comes later in the unit. Do not preview them. No question.
#### Text
content::
The readings so far describe three ways control is supposed to lower the risk of an AI catastrophe. The rest of this unit calls them routes:

- **Stopping attacks:** monitors block or replace dangerous actions while the AI works.
- **Catching it red-handed:** catch an AI trying to cause harm, then act on the evidence. Shut it down, or study the attempt so later ones fail.
- **The window:** use AIs that are useful but still controllable to speed up safety work, before AIs become too capable to control.

Each route needs someone to act on it: a safety team, company leadership or a government. The next readings ask how much each route depends on that, and add one more route.

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
tutor_minutes:: 17
tldr:: Take one control project, lay out the routes by which it could lower risk, say what each needs from the people in charge, and find the premise you trust least.
summary_for_tutor:: Practice exercise at the end of Unit 3 of AI Control Fundamentals, before the learning-outcome test on control's theory of change. The scenario: a government AI safety institute funds a team that runs control evaluations on AI companies' internal agent deployments (with permission), gives each company its results and publishes a template safety case. Part 1 asks for two or more distinct routes from the tool to lower risk, each with steps, and for each route how much it depends on the political will of AI companies and governments. Part 2 asks for the premise the learner trusts least and an observation that would change their confidence in it. Part 3 asks the learner to compare their first guess from the start of the unit with the routes. Routes from the unit: blocking attacks while models are in use, catching attempts and acting on the evidence (the company, governments, or the safety team studying the attempt), getting useful safety work out of untrusted models during a window before they are too capable to control, and making control a condition of deployment through safety cases, standards or regulation. A few insiders at a careless company running cheap measures is a low-will setting for these routes, not a separate route. Grade nothing. Give feedback that helps the learner do the same thing on an unfamiliar case.
#### Text
content::
In the test at the end of this unit you will get a control project you have not seen and be asked to lay out how it could reduce risk. Practise on this one first. The tutor gives feedback after each part.

**The project.** A government AI safety institute funds a team that runs control evaluations on AI companies' internal deployments of AI agents. With each company's permission, a red team builds attack versions of the company's model and tests whether the company's safety measures stop them. The team gives each company its results, and publishes a template safety case that any company or regulator can use.

#### Question: Open
id:: f15b1e9e-0289-4e41-af64-2b7e9dab3ba9
content::
\## Part 1: the routes

Describe at least two distinct routes by which this project could lower the chance of an AI catastrophe. For each route:

1. Write the steps from "the team runs an evaluation" to "less risk".
2. Say who other than the team would have to act. Most routes need someone.
3. Say whether the route still works at a company whose leadership cares little about misalignment risk, in a country whose government requires nothing. Why: what does the route need, and from whom?

At least one of your routes should work through something other than the company's monitors blocking or flagging an attack, or responses to a flagged attack.
placeholder:: Two or three short paragraphs.
force-feedback:: first
assessment-instructions:: Score out of 100. Grade reasoning, not which conclusion the learner reaches. This practice mirrors part 1 and the first half of part 2 of the unit's test, and uses the same rules. Context for grading: a government AI safety institute funds a team that runs control evaluations on AI companies' internal deployments of AI agents. With each company's permission, a red team builds attack versions of the company's model and tests whether the company's safety measures stop them. The team gives each company its results and publishes a template safety case that any company or regulator can use. Plausible routes: (a) the company learns where its measures fail and fixes them, so real attacks are more often blocked, (b) the fixes mean more attempts are caught, and someone acts on a catch, for example the company studies the attempt to improve its defences, or slows down, (c) the template makes it practical for a company policy, an industry body or a regulator to require a passing control safety case before deployment, so models that fail are not deployed, (d) results showing that attacks get through inform company leaders and governments and may build political will, (e) better tested measures let companies use untrusted models, including for safety work, while those models can still be controlled. Other mechanisms count if the steps hold. Score the two strongest routes, 50 each. Per route: 25 for a mechanism with steps from the evaluation to less risk, each step plausibly leading to the next. A route given only as a label ("it catches AIs"), or one that stops at a catch without saying who acts on the evidence and how that lowers risk, earns at most 12 of these 25. 10 for saying who other than the team would have to act, such as the company's leadership or engineers, a regulator, an industry body or a government, or for a reasoned claim that nobody else is needed. 15 for a verdict on whether the route still works under careless leadership and no government requirement (yes, no or partly), with a reason that says what the route needs and from whom. A verdict with no reason earns at most 5 of these 15. Any verdict, including "partly", scores if the reason is sound, for example: fixing weaknesses needs the company to give permission and act on the findings, which careless leadership may not do, though a few safety-minded insiders might use the results. A required safety case needs a regulator or industry body willing to require it and to block deployment when the case fails. Two caps can apply to the 25 for steps. Same-mechanism cap: if the two routes lower risk through the same mechanism, the lower-scoring one earns at most 6 of its 25. Routes that share their first steps (the evaluation finds flaws, the company fixes them) but then lower risk in different ways are distinct: blocking an attack, deterring attempts, and catching an attempt and acting on the evidence (for example studying it to improve defences) count as distinct mechanisms. Flagging cap: if no route works through something other than the company's monitors blocking or flagging an attack, or responses to a flagged attack (by this company, other companies or governments, including rules made because of a flagged attack), the lower-scoring route earns at most 12 of its 25. Deterrence and studying a caught attempt both count as working through flagging for this cap. Routes (c), (d) and (e) work through something else. When both caps apply to a route, apply only the lower one, and never cap both routes. The order of the routes does not matter. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Route 1: the red team gets an attack past a company's monitors, the company sees where they failed and fixes them, so when a real scheming agent tries the same kind of attack it is blocked. Besides the team, the company has to act: it must give permission and spend effort on the fixes. With careless leadership and no rules, this works only partly: leadership may refuse permission or ignore the report, though a few safety-minded engineers could still use the findings. Route 2: the published template makes a control safety case cheap to adopt, so a regulator or industry body requires a passing case before a company deploys agents internally, and models that fail are not deployed. This needs a regulator or industry body willing to require it and to block deployment. With careless leadership and no government requirement it mostly does not work, because nobody makes the company use the template."
feedback-instructions:: The learner is practising for the Unit 3 test on control's theory of change. The project: a government institute's team runs control evaluations (red-team attack versions of a company's model against its safety measures) on companies' internal agent deployments, with permission, gives each company its results, and publishes a template safety case. Plausible routes: (a) Fixing weaknesses: the company learns where its measures fail and fixes them, so real attacks are more often blocked, or more attempts are caught and acted on. Blocking and catching are separate routes that share these first steps. This needs the company to permit the evaluation and act on the findings, which a careless leadership may not do, though a few safety-minded insiders might use the results. (b) A condition of deployment: the template makes it practical for a company policy, an industry body or a regulator to require a passing control safety case before deployment. This needs someone with the authority and will to require it and to refuse deployment when the case fails. (c) Evidence of risk: results showing that attacks get through, or what the models can do, inform company leaders and governments and may build political will, but only if people believe and act on them (compare Shlegeris's doubts about whether even a catch would move developers). (d) Keeping the window usable: better tested measures let companies use untrusted models, including for safety work, while they can still be controlled, which needs the company not to race on to uncontrollable models. Under no political will at all, the project mostly depends on voluntary permission and insiders. Accept other routes if the steps hold. Reply in at most six sentences. Routes that share their first steps (the evaluation finds flaws, the company fixes them) but then lower risk in different ways are distinct routes, as in the unit's list, where stopping attacks and catching an AI red-handed are separate routes. Blocking more attacks, deterring attempts, and catching more attempts and acting on the evidence are different mechanisms. Only call two routes the same when they lower risk in the same way. Say which of the learner's routes have steps all the way to less risk and which are only labels. If a route ends at a catch, ask who acts on the evidence and what they do, for example the company studies the attempt to improve its defences, or slows down, since a catch on its own lowers no risk. If every route works through the company's monitors blocking or flagging an attack, or responses to a flagged attack, remind the learner that the question and the test ask for at least one route that works some other way, for example a safety case as a condition of deployment. For each route, say whether the will-dependence reasoning holds up, and name the most useful thing missing. If the learner gives only one route, ask for a second that works by a different mechanism. Accept routes not on this list if the steps hold. Do not say whether the project is worth funding. If the learner says they do not understand, give one foothold: ask what the company does on the day it receives a report saying the red team got an attack through. No generic praise. At most two turns, then send them to Part 2.

#### Question: Open
id:: 251e2cbf-3eb7-41fb-932e-0807f6c461ce
content::
\## Part 2: the weakest premise

Which premise in your routes do you trust least? Say why. Then name one thing someone could actually observe that would change your confidence in it, and say whether it would raise or lower it.
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner is practising for the Unit 3 test on control's theory of change. A good answer names a premise one of their routes actually needs (for example: companies give permission and fix what the evaluations find, the red team can find attacks as good as a much stronger model would, results showing failures change what companies or governments do, a regulator would require a control safety case, or the window before uncontrollable AI lasts long enough to use), gives a reason it is doubtful, and names an observation someone could actually make that bears on it and says which way it would move confidence. "More research" or "time will tell" is not an observation. Reply in at most five sentences. Say whether the premise is one their routes need, whether the reason holds, and whether the observation is something that could be seen, and fix the weakest of the three. Do not tell the learner which premise is the right one. No generic praise. At most two turns, then send them to Part 3.

#### Question: Open
id:: 05b0faa2-0ce3-4e4c-9da3-032cef27e14a
content::
\## Part 3: looking back

Look back at the guess you wrote at the start of this unit:

::answer{id="5372c08e-c3ae-48ac-8b01-18be0b0cb327"}

Which route was it, and which routes have you added since?
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner is practising for the Unit 3 test on control's theory of change and compares the guess they wrote at the start of the unit with the routes the unit covered: stopping attacks, catching an AI red-handed and acting on it, the window, and making control a condition of deployment. Acknowledge their comparison in one or two sentences without judging the guess. Close by telling them the test asks for the same things as Parts 1 and 2 on a different project, that it also asks in which of Greenblatt's Plans A to D their most will-dependent route would still work, and that at least one of their test routes should work through something other than the monitor blocking or flagging an attack, or responses to a flagged attack. No generic praise. One turn.
