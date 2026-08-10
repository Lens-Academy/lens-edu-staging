{++{"author":"Lauren's AI","timestamp":1786358380880}@@---
id: '57a676a0-de9e-481b-971c-c764170173c3'
title: The Model And Its Authors
tldr: The AI Futures team rebuilt their timelines model and moved their own median three to five years later than AI 2027. You build your forecasting toolkit before seeing theirs, then watch two of the authors run the same model and disagree.
summary_for_tutor: "Administers the AI Futures Project's Dec 2025 model rather than describing it. Sequence: the student lists every forecasting method they can think of BEFORE reading, then reads the authors' five (expert survey, argument-informed intuition, revenue extrapolation, brain-compute anchoring, benchmark trend extrapolation) and diffs; then reads the three-stage model structure; then commits to their own median before seeing the authors'; then reads Eli and Daniel producing DIFFERENT forecasts from the same model, which makes aggregation a live case rather than a hypothetical. Closes by asking what process generates the trend and what that process is aimed at. The tutor must not supply the five methods during the attempt beat, and must NOT name any unifying frame at the close: the student is meant to arrive at it themselves across later units."
authors:
  - Lauren+Claude
---
#### Text
content::
\## A real model, with its authors disagreeing inside it

Most forecasts reach you as a number. This one arrives with its workings open: a model of when AI automates coding and what happens after, built by people who had published a different answer eighteen months earlier and then moved their own median three to five years later.

That makes it useful twice. Once for what it concludes, and once for what it shows about how a conclusion like that gets built, including the places where two people running the same model walk away with different numbers.

Before you read any of it, you are going to build your own version of their toolkit.

#### Question
content::
\## Every way you can think of

How would you forecast when AI can do a month-long software engineering task on its own?

List every distinct method you can think of. Not your answer, your methods. For each one, write a single line on what evidence it needs and what would make it unreliable. Do not look anything up. Four minutes.

max-time:: 6:00

assessment-instructions:: The student is mid-exercise. They have not yet read the authors' survey of forecasting methods, which comes next in this lens.

Do not supply or hint at the authors' five methods (expert surveys, argument-informed intuition, revenue extrapolation, compute extrapolation anchored by the brain, capability benchmark trend extrapolation). Leaking them destroys the exercise.

This is their attempt, not a test. Use no grading language.

Look for: at least two genuinely distinct methods, and a stated failure condition for each. "Ask experts" and "ask researchers" are one method, not two.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise.

What to do in your single reply:
1. Name back one or two of their methods specifically.
2. If they gave fewer than two distinct methods, or no failure conditions, ask once for the missing piece.
3. Send them on to the reading.

This is a one-turn response.

#### Article
source:: [[../articles/kokotajlo-ai-futures-model-dec-2025-update]]
from:: ## AGI timelines forecasting methods
to:: ## Post-AGI takeoff forecasts

#### Question
content::
\## The diff

Put your list beside theirs. Which of their five did you have in some form? Which one did you not think of, and what does its absence tell you about where you were looking?

Then the harder half. They do not treat these as five independent estimates to be averaged. Pick the two you would weight most heavily and say why, in terms of what evidence each one actually consumes.

assessment-instructions:: The student has their own list of forecasting methods and has now read the authors' five.

The skill is honest diffing and weighting by evidence source, not evaluation of the authors.

Maximum 2 tutor turns. Keep an internal turn counter.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise.

What to do in each reply:
1. Reward a specific comparison. "I had nothing like revenue extrapolation because I was only thinking about capabilities" is the target shape.
2. Reward weighting that names the EVIDENCE a method consumes rather than how sophisticated it sounds.
3. Push back once if they rank methods without reference to what each would need to be true.

After 2 tutor replies, close the phase and send them on.

#### Article
source:: [[../articles/kokotajlo-ai-futures-model-dec-2025-update]]
from:: ## How our model works
to:: ## Timelines and takeoff forecasts

#### Question
content::
\## Your number, before theirs

You have their methods and the structure of their model, and you have not yet seen what any of them concluded.

Give your own median year for an AI that can do essentially all of an AI researcher's coding work. State the one assumption your number is most sensitive to, and say which direction your number moves if that assumption is wrong.

max-time:: 5:00

assessment-instructions:: The student is committing to a number BEFORE seeing the authors' forecasts, which come next.

Do not supply the authors' numbers, and do not steer toward or away from any year.

The pass bar is a year, a named sensitivity, and a stated direction of movement. A year alone is a level-1 answer.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not argue with their number. That is not the job here.

What to do in your single reply:
1. Reflect back the number and the sensitivity they named.
2. If they gave no sensitivity, ask once for the assumption that would move them most.
3. Tell them the authors' numbers are next, and that two of the authors disagree.

This is a one-turn response.

#### Article
source:: [[../articles/kokotajlo-ai-futures-model-dec-2025-update]]
from:: ### Eli
to:: ## Comparison to our previous

#### Question
content::
\## Two people, one model, different answers

Eli and Daniel are looking at the same model, the same parameters, and largely the same evidence, and they do not land in the same place.

You now hold three numbers: Eli's, Daniel's, and the one you wrote down before you saw either. What is the right thing to do with three numbers like that, and what would you need to know about how each was produced before you could do it?

Be specific about the disagreement. Name the parameter or judgement where they actually part company, not just the size of the gap.

assessment-instructions:: The student has read both authors' all-things-considered forecasts and holds their own earlier number.

This is the aggregation problem arriving as a real case rather than a constructed one. These two forecasters share a great deal of evidence and the same model structure, so the correct move is NOT the same as for independent estimates.

Up to 3 tutor turns, then offer to continue or close.

The pass bar: they identify the specific locus of disagreement, and they recognise that shared evidence and shared model structure mean the two numbers are not independent draws, so averaging is not straightforwardly right and extremizing beyond their range is not licensed.

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, educational.
- Do not over-validate. Avoid generic praise.
- If the answer is vague about WHERE they disagree, ask for precision.

What to do in each reply:
1. Reward finding the actual parameter or judgement in dispute.
2. If they average the three numbers without comment, ask what would have to be true about how the three were produced for averaging to be correct.
3. A student who notices that their own number is the only one produced from different evidence, and that this makes it worth more than its share rather than less, is reasoning well. Say so.

#### Question
content::
\## What is producing the trend

Step back from the numbers.

Every forecast in this reading rests on some process out in the world continuing to do what it has been doing. Name that process as concretely as you can. Not "AI progress", but the actual thing: who is doing what, why they keep doing it, and what they are getting out of it.

Then two questions about it. What is that process pointed at, as measured by what it actually rewards rather than what anyone says it is for? And if you wanted the trend to bend somewhere else, what specifically would have to change about the process, as opposed to about anyone's intentions?

assessment-instructions:: This is the closing move of the lens and the most important one in the unit.

CRITICAL: do NOT supply, name, or gesture at any unifying framework here. There is a frame this course is building toward, and the student is meant to arrive at it themselves over several units from repeated encounters like this one. Naming it now replaces their derivation with our assertion, and the derivation is the point. If the student names such a frame themselves, engage with it seriously as theirs.

The move being practised is looking past a trend line to the process that generates it, and asking what that process is aimed at as revealed by what it rewards.

Up to 3 tutor turns.

Look for, in rough order of value:
- A concrete process with actors and incentives, not an abstraction. "Labs compete for researchers and revenue, and compute spend is how they buy position" beats "the field is advancing".
- A distinction between what the process is SAID to be for and what it actually rewards.
- An intervention aimed at the process rather than at people's intentions. A student who proposes "convince people to care more" and then notices it does not survive the incentives is doing exactly the right thing.

Response length: 120 to 200 words. Short paragraphs only.

Response style:
- Calm and direct. Genuinely curious about their answer.
- Do not over-validate. Avoid generic praise.
- Do not correct them toward a preferred answer. There are several good ones.

What to do in each reply:
1. Push once for concreteness if the process is named abstractly.
2. Ask what the process rewards, if they only said what it is for.
3. If they propose an intervention that depends on everyone choosing to behave differently, ask what happens when someone defects.

On close: tell them this question returns in later units about other trends, and that their answer should get sharper rather than be replaced.++}