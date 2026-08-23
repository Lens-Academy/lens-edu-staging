{++{"author":"Elias's AI","timestamp":1787500808865}@@---
id: '964c5d74-ebe8-4e88-8c4e-28d0832398fe'
title: "Exercises - Capabilities"
tldr: "Three exercises that make you spend the chapter rather than recall it: cash in the forecast you committed to before reading, place three real systems on the two axes, and repair a policy argument that is wrong in an interesting way."
summary_for_tutor: "Exercise page at the end of Chapter 1, no reading. Three questions: (1) cashes in the single-year forecast the student committed to in the Forecasting Timelines PQ, asking them to build an interval and name a specific chapter mechanism behind it; (2) practises the capability-and-generality framework on three systems, targeting the slide from academic subjects to CHC domains; (3) a wedge separating timelines from takeoff speed, framed as repairing an argument rather than counting errors. Closes with an open chat."
reading_minutes: 25
tutor_minutes: 25
min_chat_messages: 3
add_to_ai_context:
  - "[[../articles/AI Safety Atlas - Capabilities - Defining and Measuring AGI]]"
  - "[[../articles/AI Safety Atlas - Capabilities - Leveraging Scale]]"
  - "[[../articles/AI Safety Atlas - Capabilities - Forecasting Timelines]]"
  - "[[../articles/AI Safety Atlas - Capabilities - Takeoff]]"
---

#### Text
content::
Three exercises on Chapter 1. Each one is answered here and graded here. If your cohort meets, bring what you wrote and the feedback you got.

#### Question
content::
Before the forecasting section you committed to a single year. Two things now.

First, the chapter argues that when someone names a date they really mean a range. Give yours: the earliest year you would be genuinely surprised to see it happen before, and the year by which you would be genuinely surprised if it still had not happened.

Second, name one specific thing in this chapter that set either end of that range, or that moved your original year. Name the trend, model, number, or argument. Not the direction.

If nothing in the chapter moved you, that is a real answer: say which specific claim you did not find convincing, and what evidence would have moved you.

"I updated slightly toward shorter timelines" is not an answer.

assessment-instructions::
The student committed to a single year in the pre-reading lens earlier in this module, and has since read Defining and Measuring AGI, Leveraging Scale, Forecasting Timelines and Takeoff.

OPEN WITH THEIR OWN NUMBER. If their pre-reading answer is retrievable in this module's chat history, quote the year back to them in your first sentence and set it beside the range they just gave. If it is not retrievable, ask them once to paste or state the year they wrote, since it is above this exchange and that is a small ask. If they decline, cannot find it, or skipped the pre-reading lens, grade the range and the mechanism on their own merits, say in one sentence that you could not make the comparison, and move on. Never invent what their earlier answer contained.

Pass bar: the answer names at least one specific trend, model, number or argument from this chapter, and says which end of the range it set or which way it moved the original year. The direction of movement is irrelevant to the grade. No movement at all passes exactly as strongly as movement.

Mechanisms from the chapter that plainly qualify. This list is open, not exhaustive, and any other specific item from the chapter counts. Never tell a student their mechanism is not on the list. High-quality public text projected to run out between 2026 and 2032, and how far the three escape routes substitute (the article calls them multimodal data, synthetic data, and task-based learning; this course also calls the third task-based self-play, so accept either name). The decomposition of effective compute into chip production, hardware efficiency and algorithmic efficiency, at roughly 2.3x, 1.35x and 3x per year. Training compute growing 5x per year since 2020. The Chinchilla result that optimal training needs roughly 20 tokens per parameter, and that earlier large models were undertrained. The cost trajectory, from 480 million dollars for Grok-4 in 2025 toward hundreds of billions of dollars and gigawatts per run by 2030. The biological-anchors range, from roughly 10^28 to 10^41 FLOP. Unhobbling and scaffolding sitting outside what scaling laws predict. The 60-95 versus 5-40 attribution split between scale and algorithms. The investment and automation feedback loops in the compute-centric takeoff argument.

Two cautions about your own facts. The chapter describes the biological-anchors range as twelve orders of magnitude; 10^28 to 10^41 is thirteen. A student who computes thirteen is right. Credit them and do not correct them. Second, the GATE aggressive-versus-conservative spread appears in the required reading only as figure-caption text, with no numbers attached, and the substantive GATE material sits in an optional appendix. Accept it if a student cites it, never require it, and never ask them how large the spread is.

A student who did not move and can say why passes fully. A passing example: "every trend in the chapter conditions on compute being the binding constraint, and my uncertainty was never about compute."

Do not reward movement toward shorter timelines. The chapter presents evidence in both directions, and a course that rewards one direction is teaching a conclusion rather than a skill.

Calibration, applied symmetrically. If their range is narrow and they cannot name what set either end, say so in one sentence. If their range is so wide that nothing in the chapter could have produced either end, say that in one sentence too. A student is entitled to argue that finding their old estimate internally incoherent is itself a reason to narrow, without new evidence; that is the chapter's own account of what forecasts are for, and it passes.

One turn. Reply in 80 to 150 words. Short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent, well done).

max-chars:: 1500

#### Question
content::
Three systems. For each, say what the capability-and-generality framework licenses you to state, and what it leaves undetermined.

(a) A model that scores above the 90th percentile of test-takers on graduate examinations across most academic subjects, and that cannot reliably hold a task together across more than a few hours of work.
(b) A protein-structure predictor that is superhuman at its one job and can do nothing else.
(c) A coding agent built on a model no stronger than (a), which, given tools, a long context window and the ability to run its own code, finishes multi-day engineering jobs that (a) cannot.

Then: which of the three does the framework describe worst, and what would you add to the framework for that case?

assessment-instructions::
Generality in this chapter is the percentage of the ten CHC cognitive domains where the system reaches expert level, roughly the 80th to 90th percentile. It is not the percentage of tasks, benchmarks, or school subjects. Grade against that definition.

(a) is the item that discriminates. The stem gives capability above the threshold on the domains that graduate examinations actually probe: general knowledge, reading and writing, mathematical ability, and arguably on-the-spot reasoning. It says nothing about working memory, long-term memory storage, long-term memory retrieval, visual processing, auditory processing, or speed. The licensed statement is therefore high capability on roughly three or four of ten domains, which is about 30 to 40 percent generality. That is not high generality: the chapter's own worked example is "three out of ten domains, that's 30% generality", and it says current systems "still cover only a fraction of cognitive capabilities". An answer that slides from most academic subjects to most cognitive domains has made the error this item exists to catch, and does not pass. Name the slide explicitly when it happens.

The chapter does connect short task horizons to memory, but it does so in an optional callout, and its body text names long-term planning and memory-related domains together, with planning sitting under on-the-spot reasoning rather than under memory. Credit a student who makes that connection. Do not require it. Do not correct a student who instead says the framework simply does not measure task horizon, which is also defensible.

(b) Maximal capability on one domain, near-zero generality. This is the chapter's ANI point and essentially every reasonable answer will get it. Treat it as an anchor, not a discriminator: one clause of feedback at most.

(c) The framework can assign (a) and (c) similar scores while what the two can actually be pointed at differs enormously. Be careful about why, because the obvious explanation overstates. The chapter does not say the capability-and-generality framework measures a bare model: it is explicitly behaviourist, about what a system can observably do, and its own criticism callout evaluates LLMs even with extended thinking or tools. The narrower claim the chapter does make belongs to scaling laws, not to this framework: "Debates around the scaling laws only tell us about the capabilities of a single foundation model trained in a standard way", which is why unhobbling and scaffolding sit outside what those laws predict. A student who argues that the framework as defined does cover a scaffolded system, and that the real gap is that it never fixes what counts as the system being scored, is more precise than the common answer and should be credited at least as highly.

Gaps that pass on any of the three: deployment autonomy, which the chapter deliberately excludes from the definition; elicitation and scaffolding not being recoverable from a score; the coverage-bias and species-specific-risk critiques from the counter-argument callout; the reference population sitting behind a percentile.

Pass bar: correct generality reasoning on (a), meaning domains counted rather than subjects counted, plus one named gap anywhere that is a real limit of the framework rather than a restatement that the system is unusual. Any of the three may be nominated as described worst, if the case is defended.

If the student places all three confidently and finds no gap, push once: ask what score the framework gives (c) before and after it is handed tools, and whether anything about the model itself changed.

Two turns maximum. Keep an internal turn counter and close the item after your second reply. 100 to 180 words per reply. Short paragraphs, no lists. Do not over-validate. Avoid generic praise.

max-chars:: 2000

#### Question
content::
A policy adviser writes:

> High-quality text data runs out around 2028. Once training data runs out, progress slows, so we should expect a slow takeoff and plan accordingly.

Grant the 2028 date for the sake of argument. The conclusion still is not supported by what precedes it.

Show where the argument fails, and say what the adviser would have to add to make the conclusion defensible.

assessment-instructions::
There are two weak steps and a strong student may find a third. Do not tell the student how many there are, and do not treat any count as the target.

Step one: data running out to progress slowing. This is the step the chapter most directly contradicts. It presents the data limit as a constraint of open severity, not a stop: "Three escape routes exist, whether data actually constrains scaling through 2030 depends on how well these alternatives work", and it does not claim they fail. Meanwhile hardware efficiency at about 1.35x and algorithmic efficiency at about 3x per year keep compounding inside effective compute, and unhobbling and scaffolding sit outside what scaling laws predict at all. Note that the chapter does hedge the third escape route as very speculative; a student who leans on that hedge is reading the chapter correctly, not weakly.

Step two: slower progress to slow takeoff. The chapter defines these as different quantities: "While timelines tell us when transformative AI might arrive, takeoff speeds tell us what happens after it arrives." Read the chapter's exact relation carefully before grading: takeoff speed is "related to, but distinct from, AI timelines". Distinct, not independent. Under the compute-centric takeoff argument the chapter presents, takeoff speed depends on the strength of the investment and automation feedback loops, and the chapter explicitly allows "a slow takeoff if the loops are weaker or counterbalanced by other factors". A durable data bottleneck is a candidate counterbalancing factor. So the adviser's conclusion is not a category error and has not been refuted. The defect is that the adviser asserts the link instead of arguing it, and the argument that would carry it is nowhere in the sentence. A student who says the step is defensible once the missing premise is supplied, and identifies which premise, has given the best available answer to this question and passes at the top. Do not tell any student that this step is simply an error.

Third point, credit if offered: the overhang argument runs against the adviser. A period in which one input is constrained while chips and algorithms accumulate can make the eventual takeoff faster, not slower, which is the opposite of the adviser's conclusion. The chapter's own caveat is that this assumes chip production does not fall during the constrained period.

Also credit, and never treat as off-topic: the date itself. The chapter gives 2026 to 2032 for high-quality public text, and its data-projection figure gives 2025 to 2030. "Around 2028" is one point inside a range the chapter presents as a range. The stem asks the student to grant the date, so this is a bonus and never a requirement.

Pass bar: the student identifies the first step as unsupported and gives at least one concrete reason drawn from the chapter, and says something correct about the relation between timelines and takeoff. Any of these satisfies the second half: that the adviser has conflated them, that the adviser has assumed a link without arguing it, or that the link can be made to hold but only via the compute-centric argument.

Rescue move if stuck after two attempts: ask what would have to be true after transformative AI arrives for takeoff to be slow, and whether the adviser's sentence says anything at all about that period.

Three turns, then offer to continue. 100 to 180 words per reply. Short paragraphs, no lists. Do not over-validate. Avoid generic praise.

max-chars:: 2000

#### Chat
instructions::
The student has just worked through three Chapter 1 exercises: cashing in the timeline forecast they made before the forecasting section, placing three systems on the capability and generality axes, and repairing a policy argument that runs a data constraint into a takeoff prediction.

Build on what they actually wrote, and quote them. Useful directions: which end of their interval is doing the most work in their own planning, and whether they would act differently if only that end moved; whether the capability-and-generality framework would have flagged the systems they personally find most concerning, and if not, what it would need; what evidence over the next two years would most change their view, and whether they would actually notice it if it arrived.

Do not re-teach the chapter. Do not push them toward a timeline, and do not offer your own timeline even if asked: say that you would be the last input into a lens whose whole point was to make theirs explicit, and turn the question back. If they ask your view on the framework or on one of the arguments, give one briefly and flag it as one view.
++}