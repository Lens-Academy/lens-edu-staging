---
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
from:: ## Timelines and takeoff forecasts
to:: ## Comparison to our previous

#### Question
content::
\## Two people, one model, different answers

Eli and Daniel ran the same model with their own parameter settings, on largely the same evidence, and did not land in the same place. Eli gives his all-things-considered distribution in the text. Daniel's is in the chart rather than in prose, so read it off the figure.

Here is the thing to notice, and it is not in the model. Both of them run the model and then adjust off it, by hand, for reasons the model does not contain. Find where each one does that, and say what each is correcting for.

Then: you also wrote down a number before you read any of this. What should you do with yours now, and what would you need to know about how each of the three was produced before you could combine them at all?

assessment-instructions:: The student has read the section framing (both authors adjust off the model using intuition and other factors), Eli's all-things-considered distribution, and Daniel's discussion.

FACTS THE TUTOR NEEDS. Eli states 10th percentile 2027.5, 50th 2032.5, 90th 2085, having lengthened his median and raised the 90th from 2062. Daniel does NOT state a median in prose; he says he keeps the model's median and increases uncertainty in both directions, and his distribution appears as a figure. Do not assert a number for Daniel. If the student cannot read the figure, tell them to describe its shape instead and grade on that.

The real disagreement is about HOW MUCH TO TRUST THE MODEL, not about a parameter. Eli lengthens; Daniel holds the median and fattens both tails. A student who goes hunting for a single parameter where they differ has been misled and should be redirected gently.

Up to 3 tutor turns, then offer to continue or close.

The pass bar: they locate at least one hand-adjustment and say what it corrects for, and they recognise that two forecasters sharing a model and most of their evidence are not independent estimates, so combining them is not a matter of averaging three numbers.

Do NOT require or introduce extremization here. That is taught later in this unit by a lens that depends on the student not having met it yet.

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, educational.
- Do not over-validate. Avoid generic praise.

What to do in each reply:
1. Reward finding an actual adjustment and naming what it corrects for.
2. If they treat the three as three independent estimates, ask what would have to be true about how each was produced for that to hold.
3. A student who notices that their own number is the only one produced from different evidence, and that this makes it worth more rather than less, is reasoning well. Say so.

#### Question
content::
\## What has to keep happening

Every number in this reading rests on one thing continuing: the METR horizon trend. Daniel spends several paragraphs on why he is nervous about exactly that.

He names things that could bend it, among them online and continual learning, data efficiency, and the question of whether the trend is exponential or superexponential. Pick the one you think these forecasts most depend on.

Now three questions about the world rather than about the model.

Who specifically has to keep spending to keep that trend going, and what do they get back if they do?

What happens to whoever stops first, while the others keep going?

Daniel calls extrapolating AI revenue "a decent proxy for when AGI will be achieved". Is revenue measuring the thing these forecasts are about, or something that travels alongside it and could come apart? Give one concrete way it could come apart.

max-time:: 8:00

assessment-instructions:: This is the closing move of the lens.

CRITICAL: do NOT supply, name, or gesture at any unifying framework here, and do not use words like "incentive structure", "selection pressure", or "self-repairing". There is a frame this course builds toward, and the student is meant to arrive at it themselves over several units from repeated encounters like this one. Naming it replaces their derivation with our assertion, and the derivation is the point. If the student produces such a frame themselves, engage with it seriously as theirs.

All three questions are answerable from the slices they have read. The second one is the one that does the most work and the one students will skate over.

Look for, in rough order of value:
- Named actors with something to gain. "Labs compete for revenue and for researchers, and compute is how they buy position" beats "the industry invests".
- On the second question: recognising that a lab which stops unilaterally loses ground to the ones that do not, and that this is why the trend is hard to bend by persuasion.
- On the third: any concrete decoupling of revenue from capability, in either direction.

Up to 3 tutor turns.

Response length: 120 to 200 words. Short paragraphs only.

Response style:
- Calm and direct. Genuinely curious about their answer.
- Do not over-validate. Avoid generic praise.
- Do not correct them toward a preferred answer. There are several good ones.

What to do in each reply:
1. Push once for named actors if they answer the first question abstractly.
2. If they skip the second question or answer it as "they would fall behind", ask what that means for anyone trying to slow the trend down deliberately.
3. If they say revenue is simply a good proxy, ask what would have to be true of the economy for that to hold.

On close: tell them this question about what keeps a trend running returns in later units about other trends.