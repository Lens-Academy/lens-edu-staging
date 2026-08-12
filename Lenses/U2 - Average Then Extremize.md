---
id: '3fad3472-9deb-4647-9a25-fa376ede44fa'
title: "Average Then Extremize"
tldr: When people who looked at different things agree, their agreement is itself evidence, and the right combined answer can lie outside everything they said. When people who looked at the same thing agree, their agreement adds almost nothing.
summary_for_tutor: "Teaches forecast aggregation as a function of the estimators' information structure rather than of their numbers. Source is Eric Neyman's Algorithmic Bayesian Epistemology thesis summary, chapter on robust aggregation: the average-then-extremize result and the two-coin-flip worked example. This closes step five of the decomposition loop, which students otherwise treat as 'take the mean'. The nonlinear object here is that the correct aggregate depends on covariance of evidence, not on the estimates."
authors:
  - Claude
---
#### Text
content::
\## Reading Assignment

**Read the section titled *Chapter 7: Robust forecast aggregation* in Eric Neyman's *My thesis (Algorithmic Bayesian Epistemology) explained in more depth*.**

You do not need the rest of the thesis, and you do not need to follow the formal statements. You need the worked example. A coin has an unknown bias. Two forecasters each see one flip. Both of them tell you the same thing. What should you believe?

The result has a name that is also an instruction: **average, then extremize.**

One warning as you read. The short version of the result is "extremizing is a trick that improves forecasts". That short version is true, and it leaves out the condition. How much you should extremize depends on how much the forecasters' information overlaps. If their information overlaps completely, you should not extremize at all.

*The framing and questions on this page were written by Claude, an AI, and reviewed by a human. The reading itself is the author's own work.*

---

#### Article
source:: [[../articles/neyman-algorithmic-bayesian-epistemology-explained]]
from:: \* Chapter 7: Robust aggregation of substitutable signals
to:: Chapter 8: When does agreement imply accuracy?

#### Question
content::
\## Phase 1: Recall

Spend 2 minutes writing down everything you can remember from the reading, without looking back. Anything and everything. No need to organize it.

assessment-instructions:: The student has just read the robust-aggregation section of Neyman's thesis summary and written a free recall.

Key content:
- The setup: two experts forecast rain at 60% and 70%, against a prior of 30% for someone with no special information.
- The naive move is to average the two forecasts and ignore the prior.
- The reason that is wrong: the fact that both experts updated in the same direction away from the prior is itself informative.
- The coin example. A coin's bias is drawn uniformly between 0% and 100%. Two forecasters each see one independent flip. A forecaster who sees heads should say 2/3; one who sees tails should say 1/3. If both say 2/3, you know the coin came up heads twice, so you should say 3/4, which is higher than either forecaster said.
- Extremization is defined as updating further away from the prior after aggregating.
- The qualification: real experts' information is not completely independent, so you should extremize less than full independence would justify, but as long as there is some non-overlap you should extremize at least a little.
- The empirical support: Satopää and colleagues found extremization improves aggregate forecasts, and Jaime Sevilla found the technique works on Metaculus data.

Your role in this phase is diagnostic, not instructional. Act as a brief, honest mirror.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise.
- Correct errors in one sentence.
- Name gaps briefly without lecturing.
- Normalize incomplete recall.

What to do in your single reply:
1. Acknowledge what they captured correctly, without inflation.
2. Name what was missing. The most common omission is the role of the prior: students remember "extremize" as a direction (go higher) rather than as a direction relative to the prior. If the prior had been 90% and the experts said 60% and 70%, extremizing means going below 60%. If they missed that, say so.
3. Correct errors plainly. A frequent one is remembering the conclusion as "always extremize" without the overlap condition.
4. Close with one calibrating sentence.

This is a one-turn response. Do not ask a question. Tell them to move on.

#### Question
content::
\## Phase 2: Processing

Go back to the number you wrote down one lens ago, when three people who had not spoken to each other said 60, 65 and 70 percent. Write that number here again. Then write the DIRECTION the reading permits, which is above the highest individual estimate. Do not write a specific number.

If the two differ, the arithmetic is not the interesting question. The interesting question is what you believed about aggregation when you wrote your first number. Name that belief. Then say how confident you were at the time, and what that tells you about confidence as a signal.

assessment-instructions:: The student has recalled the aggregation reading and is now reflecting. Critically, one lens ago they committed to a number for the three-people-agreeing problem (estimates of 60, 65 and 70 percent against a 10 percent base rate). The case that phase was built for is an answer inside the 60-to-70 range, reasoning that an aggregate cannot exceed what any individual believes; expect that, but read what they actually wrote.

CASH THAT COMMITMENT. This is the moment the strand is built around: they made a confident, specific, checkable prediction and the reading has just contradicted it. Open by putting their number next to that direction, quoting what they wrote. If they did not commit a number, ask once what they would have said.

The belief underneath is usually one of two, and naming which one is the content here. Either they treated the estimates as opinions to be compromised between, in which case averaging is the natural operation and the range is a hard boundary. Or they treated them as measurements but assumed the measurements were of the same evidence, in which case averaging is correct and the surprise is that independence changes the answer rather than the confidence. The second is much closer to the truth and worth saying so.

Do not resolve the mathematics here, and do not walk them through the extremization rule; that is the next phase and pre-empting it wastes the setup. If they are embarrassed about the wrong number, say plainly that being wrong here was the design, and that a wrong answer they can now explain is worth more than a right answer they guessed.

This is a processing phase, not a teaching phase.

The learning outcome for the next phase is: given several estimates of one quantity, determine how much the estimators' information overlaps, state whether the correct aggregate lies inside or outside the range of the individual estimates, and explain why averaging is right under one overlap structure and wrong under another.

Reactions worth drawing out:
- Genuine discomfort at an answer outside the range of every input. This feels like getting something from nothing and it is worth articulating precisely why it is not: the aggregator holds the union of the evidence and therefore knows more than any contributor.
- The worry that you can never actually know the overlap structure in practice, so the result is unusable. That is a serious objection and the next phase takes it up; do not resolve it here.
- Recognition that this makes expert consensus weaker evidence than it looks, because experts read each other. Strong reaction, worth naming.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Warm but rigorous.
- Treat confusion and skepticism as intelligent.
- Do not over-validate.
- Ask precise follow-ups when vague.
- Do not pre-empt the next phase.

Conversation flow:
- Keep an internal turn counter.
- After 2 tutor replies, close: "Good. Take that into the next step, where the overlap is hidden and you have to work out what it is."

What to do in each reply:
1. Acknowledge specifically what they expressed.
2. Confusion: ask what specifically was unclear. A common one is the 3/4 arithmetic; if that is the sticking point, ask whether their confusion is about the number or about the claim that you can exceed both experts, since only the second matters here.
3. Skepticism: ask what would need to be true to convince them.
4. Resonance: ask what it connected to.

What not to do: mini-lectures, adjudication, more than 2 turns.

#### Question
content::
\## Phase 3: Learning Question

A research group publishes a survey. They asked forty AI researchers for the year they expect human-level AI, and the answers cluster tightly: three quarters of them fall between 2038 and 2046. The group writes:

> "The tightness of this distribution is striking. Forty independent experts, converging on a fifteen-year window. Under the aggregation results, concurrence among independent forecasters licenses us to extremize: we should be more confident in the 2038 to 2046 window than any individual respondent is."

Every sentence in that passage is defensible on its own. The conclusion is still probably wrong. Which step fails? And what would you need to know about the forty researchers before you could say anything at all?

assessment-instructions:: The student has read, recalled, and reflected on the aggregation material. This is the main discussion phase.

The question is a deliberate wedge, not the test question. It applies the reading's own result correctly in form while violating its condition, so the student must supply the condition rather than recite the conclusion.

Learning outcome for this lens: given several estimates of one quantity, determine how much the estimators' information overlaps, state whether the correct aggregate lies inside or outside the range, and explain why averaging is right under one structure and wrong under another.

The core move: the word "independent" is doing all the work and is almost certainly false. Forty AI researchers read the same papers, attend the same conferences, and have seen each other's estimates. Their information overlaps heavily, so the extremization licence does not apply. Worse, the tightness the authors treat as the strongest evidence is the strongest symptom: convergence among people sharing a source is what you would see whether or not the answer is right. Under full overlap the effective sample size is close to one, and forty near-copies of one estimate is not forty estimates.

Second move, for level 4: the correct diagnostic asks about evidence rather than conclusions. What did each researcher look at? What is the single fact most responsible for their number? If forty people name the same three papers, that is the answer. Also creditable: asking when each formed their view relative to publication of the others' views, or looking for the outliers and asking what they saw that the cluster did not.

Third move, for level 5: the direction of the error is not merely "do not extremize." Correlated error means the whole cluster can be displaced together, so the honest interval is wider than the spread of responses, and possibly not centred on it. The spread of a correlated sample understates uncertainty rather than measuring it. Students who see that the survey's tightness should decrease rather than increase confidence have got the deepest version.

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

If the student is missing the core move, draw it out. Ask what "independent" meant in the coin example, and whether forty researchers satisfy it. Ask what the forty would have to have done for the word to apply. Ask whether the tightness of the cluster is evidence for the answer or evidence about the researchers' reading habits, and how they would tell those apart.

If the student says the survey is useless: push back. Ask what it does establish. A tight cluster is real evidence about what the field currently believes, which is a different quantity from when AI arrives, and both are worth knowing as long as they are not confused.

If the student gets it early, push to the design question: how would you run the elicitation so that the extremization licence actually applied, and what would it cost you?

Calibration summary (on close):
- Name what they demonstrated clearly.
- Name what remains underdeveloped.
- Give a direct test-readiness verdict.

Safety and integrity:
- Strong causal claims: ask what they rest on and how they could be falsified.
- Stuck after 2 attempts: give a brief direct answer and move on.

#### Text
content::
\## Additional resources for this topic

::card[[../Lenses/U2 - Nonlinear Interactions Workshop]]

> Extremization is one case of a general fact. The way the parts of a system relate to each other decides which arithmetic applies, and that arithmetic is rarely addition. Four more cases, worked through.
