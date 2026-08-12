---
id: 'b056a45b-7583-41f0-96a3-8ae48ca766fe'
title: "A Method That Visibly Fails"
tldr: Ask researchers what fraction of the problem they have solved, extrapolate the rate, and you get 372 years. Nobody believes it, including the people who gave the estimates. A method whose failure you can see is worth more than a method whose failure stays hidden.
summary_for_tutor: "Teaches functional-form assumptions through a worked method that produces an absurd number. Xu and Shulman on fractional progress estimates; the 372-year figure is the teaching object. The point is not that the method is bad, it is that the residual is adversely selected, so linear extrapolation of a self-selecting remainder is wrong in a predictable direction. Feeds directly into the nonlinear-interactions workshop lens that follows."
authors:
  - Claude
---
#### Text
content::
\## Reading Assignment

**Read *Fractional progress estimates for AI timelines and implied resource requirements*, by Mark Xu and Carl Shulman.**

Here is the method. You ask researchers how much progress toward human-level AI their subfield has made over a set number of years. Then you extrapolate that rate linearly to 100%. A typical answer was about 5% of the problem solved between 1992 and 2012. Extrapolated, those estimates imply human-level AI in roughly 372 years.

Check where the number came from, because that changes what it means. The 372-year figure is not Xu and Shulman's. It comes from Robin Hanson's informal survey, run between 2012 and 2017. AI Impacts did the extrapolation. Xu and Shulman quote the figure in order to argue against it. The same AI Impacts summary reports two other results from the same method: 36 years from the 2016 Expert Survey on Progress in AI, and 142 years from another set of responses. So the method does not produce one absurd number. It produces anything from 36 to 372 years, depending on whom you asked. That is a worse problem than a single implausible result.

You just did this arithmetic yourself in the previous step.

As you read, follow the argument rather than the number. The authors do not simply say that the method is wrong. They ask what would have to be true for 372 years to be right, and what is true instead.

*The framing and questions on this page were written by Claude, an AI, and reviewed by a human. The reading itself is the author's own work.*

---

#### Article
source:: [[../articles/xu-shulman-fractional-progress-estimates]]

#### Question
content::
\## Phase 1: Recall

Spend 2 minutes writing down everything you can remember from the reading, without looking back at the text. Anything and everything. No need to organize it.{--{"author":"Lauren's AI","timestamp":1786523183942}@@ Speech to text is recommended.--}

assessment-instructions:: The student has just read Xu and Shulman on fractional progress estimates and written a free recall.

Key content:
- The method: survey researchers on what fraction of the path to human-level AI their subfield has covered in a period, then extrapolate the rate linearly.
- The data: a typical estimate is about 5% over the twenty years from 1992 to 2012.
- The implied result from Hanson's survey: roughly 372 years to human-level AI. GRADER: the same AI Impacts summary the authors cite also reports 36 years from the 2016 Expert Survey and 142 years from another response set. A student who notices the spread, or who points out that a method whose output ranges over a factor of ten across surveys is unreliable for a different reason than the one this lens teaches, has seen something real and should be credited.
- The reason the number is not simply accepted: the extrapolation assumes the rate of fractional progress is constant, while inputs to AI research have grown enormously over the period. Progress per unit of resource, not progress per year, is the quantity that would need to be stable.
- The consequence: if the same fractional progress required vastly more compute, researchers, and funding in the later part of the period than the earlier part, then the resource requirements implied for the remaining 95% are the real output of the method, and they are enormous.
- The general shape: a linear extrapolation over calendar time hides what happened to the denominator.

Your role in this phase is diagnostic, not instructional. Act as a brief, honest mirror.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise.
- If something is wrong, correct it in one sentence.
- If something is missing, name it briefly without lecturing.
- Normalize gaps.

What to do in your single reply:
1. Acknowledge what they captured correctly, without inflation.
2. Name what was missing. The most common omission is the resource denominator: students remember 372 years and that it is absurd, but not the argument about what grew while the fraction crept.
3. Correct errors plainly. A frequent one: believing the reading concludes AI is imminent. It does not conclude a timeline; it examines what the method's output actually means.
4. Close with one calibrating sentence.

This is a one-turn response. Do not ask a question. Tell them to move on.

#### Question
content::
\## Phase 2: Processing

Take 2 minutes to write down your reaction to the reading. What felt important to you? What confused you? What did you doubt or disagree with?{--{"author":"Lauren's AI","timestamp":1786523184500}@@ Speech to text is recommended.--}

assessment-instructions:: The student has recalled the Xu and Shulman reading and is now reflecting.

This is a processing phase, not a teaching phase.

The learning outcome for the next phase is: given a trend extrapolated to a conclusion, identify the functional form assumed, name the interaction that breaks it, state the direction of the resulting error, and construct an alternative curve the same data supports.

Reactions worth drawing out:
- The pleasure of watching a method fail visibly, and the follow-on worry: if this method fails obviously, what about the ones that fail quietly? That is the right worry and the unit takes it up.
- Suspicion of the survey instrument itself: researchers estimating their own field's progress have incentives and blind spots. Legitimate; the next lens works on it.
- Discomfort that the same arithmetic they did two steps ago is the one being demolished. Name it if they raise it; do not soften it.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Warm but rigorous.
- Treat confusion and skepticism as intelligent.
- Do not over-validate.
- Ask precise follow-ups when vague.
- Do not pre-empt the next phase.

Conversation flow:
- Keep an internal turn counter.
- After 2 tutor replies, close: "Good. Take that into the next step, where we make you build the alternative curve rather than just doubt the line."

What to do in each reply:
1. Acknowledge specifically what they expressed.
2. Confusion: ask what specifically was unclear.
3. Skepticism: ask what would need to be true to convince them.
4. Resonance: ask what it connected to.

What not to do: mini-lectures, adjudication, more than 2 turns.

#### Question
content::
\## Phase 3: Learning Question

Someone who read the same piece draws the following lesson:

> "The problem was that they extrapolated linearly. Progress in technology is exponential, not linear. If you fit an exponential to the same survey data instead of a line, you get a sensible answer, decades rather than centuries. The fix is to use the right curve."

This answer is wrong, and the way it is wrong is worth studying. Two questions. First, changing the curve does not repair the original method. So what is the actual defect? Second, suppose you did fit an exponential and it gave you a comfortable answer. What would that comfortable answer be evidence of?

assessment-instructions:: The student has read, recalled, and reflected on Xu and Shulman. This is the main discussion phase.

The question is a deliberate wedge, not the test question. It offers a plausible fix (use a better curve) that leaves the real defect untouched.

Learning outcome for this lens: given a trend extrapolated to a conclusion, identify the functional form it assumes, name the interaction between parts of the system that breaks that form, state which direction the error runs, and construct an alternative curve the same data supports.

The two moves being drawn out:

1. The defect is not the choice of curve, it is that the data cannot choose the curve. Two survey readings constrain a curve only within a family, and the family is supplied by the analyst. Switching from a line to an exponential replaces one unargued family with another. Underneath that: the measured quantity is self-reported fraction of a problem whose size nobody knows, which is not the kind of thing a curve fits well in any family. And the resource denominator changed underneath the whole series, so calendar time is the wrong x-axis regardless of the curve's shape.

2. A comfortable answer is weak evidence about AI and strong evidence about the fitting procedure. If you keep adjusting the functional form until the output stops feeling absurd, the output is measuring your prior sense of what is absurd. The 372-year figure is valuable precisely because nobody could accept it, so it forced the assumption into the open. A method that returns a believable number does not get audited.

Strong students may add: the residual is adversely selected. Researchers solve the tractable parts of a problem first, so the remaining fraction is harder than the completed fraction, which biases linear extrapolation early on difficulty and late on date. That is a real interaction between parts of the system and deserves credit.

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, educational.
- Do not over-validate.
- If vague, ask for precision. If confused, correct plainly.
- Prefer causal reasoning and concrete examples.

Conversation flow:
- Keep an internal turn counter.
- After 3 replies, ask whether to continue or stop. If continue, reset. If not, give the calibration summary.

What to do in each reply:
1. Direct question, direct answer.
2. Otherwise steelman their answer in 2 to 4 sentences.
3. Name 1 to 3 gaps or hidden assumptions plainly.
4. Ask 2 causal follow-ups, each directly answerable. No opinion questions.

If the student is missing the core move, draw it out. Ask how many curves pass through two points. Ask what, other than the data, told them to pick an exponential. Ask what they would have concluded if the exponential had also given 372 years. If they claim exponential is simply correct for technology, ask which technologies, and whether they chose that reference class before or after seeing which answer it produced.

If the student gets it early, push to the second question: ask them to describe a procedure that would let a comfortable number be checked rather than merely accepted, and what they would have to pre-register to do it.

Calibration summary (on close):
- Name what they demonstrated clearly.
- Name what remains underdeveloped.
- Give a direct test-readiness verdict.

Safety and integrity:
- Strong causal claims: ask what they rest on and how they could be falsified.
- Stuck after 2 attempts: give a brief direct answer and move on.
