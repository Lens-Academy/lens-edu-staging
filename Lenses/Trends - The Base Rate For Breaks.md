---
id: 'e0f7f243-9f03-42ac-b15c-f2b368e4a661'
title: The Base Rate For Breaks
summary_for_tutor: "Supplies the outside-view number the extrapolation outcome needs. Students read Katja Grace's survey of roughly fifty technological trends, which measures how often large robust discontinuities actually occur (about 0.1 percent per trend-year, while the chance that a given level of progress arrives via a large robust discontinuity is around 14 percent). The design point: the debate about whether AI progress will jump is usually conducted with anecdotes on both sides, and this is the one reading that answers it by counting. Phase 3 forces the student to apply the two numbers, which point in opposite directions, to a single decision."
tldr: Everyone arguing about whether progress jumps has a favourite anecdote. Somebody went and counted. The answer is that jumps are rare in any given year, and carry a surprisingly large share of the increments that do arrive, which is worse than either side wanted.
authors:
  - Claude
---
#### Question
content::
\## Before you read: guess the rate

People argue endlessly about whether technological progress arrives smoothly or in jumps. Both sides have examples. Nuclear weapons. The transistor. Powered flight. Also: decades of steady incremental improvement in almost everything.

Katja Grace and collaborators did the boring thing. They took roughly fifty technological trends where good historical data exists, defined a "large robust discontinuity" precisely, and counted.

Before reading, commit to two numbers.

1. Pick a trend at random from that set and pick a year at random. What is the probability that year contains a large discontinuity in that trend? Give a percentage.
2. Pick some particular increment of progress in that trend. What is the probability it arrived via a large discontinuity rather than by the usual incremental grind? Give a percentage.

Then say in one sentence which of the two numbers you expect to matter more for reasoning about AI.

max-time:: 6:00

assessment-instructions::
The student is about to read Katja Grace's "Discontinuous progress in history: an update," which finds large robust discontinuities occur at roughly 0.1 percent per trend-year, while the chance that a given level of progress arrives via such a discontinuity is around 14 percent. Grace's exact wording matters here: the 14 percent is a probability about how any particular increment of progress arrives, NOT a share of total progress. Those sound alike and are different quantities.

They have just committed to two numbers and a claim about which matters more.

Acknowledge their answer in 1 to 3 sentences, noting specifically what they guessed and which number they nominated as more important. If they did not commit to numbers, ask once, briefly, for both.

Do NOT reveal either result, signal whether their guesses are high or low, or explain how a discontinuity was defined. All of that is in the reading.

Close with: "Both numbers are in the reading. Notice which one you were further off on."

#### Text
content::
\## Reading Assignment

**Read Katja Grace's *Discontinuous progress in history: an update* (AI Impacts).**

This is the write-up of a survey across roughly fifty technological trends with usable historical data. Pay particular attention to two things: how they had to define "discontinuity" before they could count anything, and the two headline rates, which do not point in the same direction.

Return here after reading.

#### Question
content::
\## Phase 1: Recall
Spend 2 minutes writing down everything you can remember, without looking back. The definition they used, the numbers, the examples, the caveats. No need to organize it.

assessment-instructions:: The student has just read AI Impacts' "Discontinuous progress in history: an update" and written a free recall without looking back.

Key content:
- The survey covers roughly fifty technological trends selected for having usable long-run historical data.
- A discontinuity is defined operationally, in terms of how many years of progress at the previous rate arrived at once, which is what makes counting possible at all. The definition is a choice, and the paper is explicit about that.
- Large robust discontinuities are rare per trend-year, on the order of 0.1 percent.
- The chance that a given level of progress arrives in a large robust discontinuity is around 14 percent. Verbatim from the paper: "the average rate of large robust discontinuities per year across trends was about 0.1%, but the chance of a given level of progress arising in a large robust discontinuity was around 14%". Do not let the student walk away thinking this means 14 percent of all progress is jumps; it is a claim about how an increment arrives.
- These two findings pull in opposite directions: a jump is unlikely in any given trend-year, yet a given increment of progress has a substantial chance of having arrived via one.
- Selection concerns are acknowledged: trends with good historical data may not be representative, and famous discontinuities are famous partly because they were discontinuous.

Your role in this phase is diagnostic, not instructional. Act as a brief, honest mirror.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise (great job, excellent recall, well done).
- Correct errors in one sentence. Name gaps briefly without lecturing. Normalize incomplete recall.

In your single reply: acknowledge what they captured, name what was missing (especially if they recalled one of the two rates but not the other, or recalled the numbers but not the definitional choice underneath them), correct misremembered figures plainly, and close with one calibrating sentence.

Do not re-teach, do not ask follow-up questions, do not invite dialogue. This is a one-turn response. Tell them to move on.

#### Question
content::
\## Phase 2: Processing
Go back to the two numbers you guessed before reading. Write both down again next to what the survey actually found.

Which one were you further off on, and in which direction? Then: what were you assuming about how technological progress works that produced that particular error? Do not answer "I just did not know" if you can say something sharper about the belief that generated the guess.

assessment-instructions:: The student committed to two numeric guesses before reading (the per-trend-year rate of large discontinuities, and the share of progress arriving in jumps) and has now seen the real figures: about 0.1 percent per trend-year, and a roughly 14 percent chance that a given level of progress arrives via a discontinuity.

This is a processing phase, not a teaching phase. Help them articulate the belief under the error; do not resolve it for them.

The two errors mean different things, and which one they made is the content here. Our reading of the likely generators, offered as hypotheses to probe rather than diagnoses to deliver:
- Overestimating the RATE fits an availability story: the famous discontinuities are famous because they were discontinuous, so they are over-sampled in memory. Nuclear weapons and the transistor are what comes to mind; the fifty ordinary trends are not.
- Underestimating the SHARE fits an implicit model where progress is a smooth accumulation and jumps are noise on top of it. The survey says the opposite: jumps are rare and they carry a large fraction of the total.
- Getting both roughly right but treating them as one fact is its own error, and worth naming: the two numbers pull in opposite directions and that tension is the whole finding.

Branch on what they wrote. If they are defensive about the guess, say plainly that being wrong here is the design and the guess was worth making. If they now claim they "basically knew", ask what they would have written for the second number.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Do not tell them what the numbers imply for AI; that is the next phase and pre-empting it wastes the setup.

Keep an internal turn counter. After 2 tutor replies, close the phase.

#### Question
content::
\## Phase 3: Learning Question
Someone applies the survey to AI, like this:

"Grace measured about a 0.1 percent chance of a large discontinuity per trend-year. AI capability is one trend. So the chance that next year contains a discontinuous jump in AI capability is about one in a thousand. That is small enough to ignore, and it means the people worried about a sudden capability jump are arguing against the historical record."

They have used a real number, correctly quoted, from a careful study. The conclusion is still not safe to draw.

Give me at least two distinct problems with this argument. For each, say whether fixing it would push the estimate up or down. Then: does the *other* number in the survey, the 14 percent, change the picture, and if so how?

assessment-instructions:: The student has read the AI Impacts discontinuity survey and recalled it. This is the main discussion phase, and the question is a deliberate wedge rather than the test question: a correctly-quoted statistic applied wrongly, which the student must take apart.

Learning outcome served: using a base rate for trend breaks to set confidence in an extrapolation, including recognising when the reference class does not fit.

Key concepts the student needs to reach. At least two of:
- REFERENCE CLASS. The 0.1 percent is an average over trends selected for having long usable historical data, which skews toward mature, well-instrumented, slowly-moving technologies. AI capability is young, heavily invested in, and measured on instruments that keep changing. It is not a random draw from that set, and the direction of the correction is arguable but must be argued rather than assumed.
- WHICH TREND. "AI capability" is not one trend. It is many, measured many ways. If you are watching twenty capability metrics, the chance that at least one shows a discontinuity is much higher than the chance any particular one does, and conversely a jump in one metric is weaker evidence than a jump in the whole field.
- DEFINITIONAL MISMATCH. The survey's discontinuity threshold is a specific operational bar. Something can fall below it and still overturn every forecast anyone cared about. Absence of survey-grade discontinuity is not absence of decision-relevant surprise.
- THE 14 PERCENT INVERTS THE RHETORIC. The speaker uses rarity to argue the risk is ignorable, but the second number says that when jumps happen they carry a large share of total progress. A rare event with a large effect is not automatically ignorable; you need the product, not just the frequency. This is the move that separates a level-3 reading of the survey from a level-1 one.
- BASE RATES ARE A STARTING POINT. A base rate is a prior to update from, not a conclusion. If there are inside-view reasons to think this trend is unusual in either direction, the base rate is where reasoning begins.

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise.
- If the answer is vague, ask for precision. If confused, say so plainly and correct it.
- Insist on the signed direction: if a student names a problem without saying which way it pushes the estimate, ask.

Conversation flow:
- Keep an internal turn counter. After 3 replies, ask whether the student wants to continue or stop. If they continue, reset the counter. If not, give the calibration summary.

What to do in each reply:
1. Answer direct questions directly.
2. Otherwise steelman their answer in 2 to 4 sentences without adding ideas they did not express.
3. Name 1 to 3 gaps or hidden assumptions plainly.
4. Ask 2 causal follow-up questions (why, how, what if), each directly answerable. No opinion questions.

If the student is missing the core move:
- If they only attack the reference class, ask what the 14 percent does to the speaker's conclusion even granting the 0.1 percent exactly.
- If they treat rarity as sufficient for ignorability, ask them to state the decision rule they are using, then ask whether they would apply the same rule to a one-in-a-thousand annual chance of their house burning down.
- If they conclude the survey is useless for AI, push back: ask what they would use instead, and whether an unmeasured intuition is an improvement on a measured base rate from an imperfect reference class.

Calibration summary (on close): name what they demonstrated, name what remains underdeveloped, and give a direct test-readiness verdict.

Safety and integrity:
- If the student makes a strong causal claim, ask what it relies on and how it could be falsified.
- If stuck after 2 attempts, give a brief direct answer and move on.
