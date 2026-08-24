{++{"author":"Elias's AI","timestamp":1787570221974}@@---
id: 'c2bbbcc4-fd54-4299-9be4-00bcab2cb260'
title: Interactive exercise types
tldr: One live example of every interactive exercise we build courses out of. Answer any of them; they all work.
summary_for_tutor: "A standalone showcase page. It holds one working example of each interactive exercise type the platform supports: open question, single and multiple choice, fill in the blank with text and numeric blanks, ranking, rating, open tutor chat, and roleplay. The subject matter is introductory AI safety, chosen so that anything can be answered without prior reading. The reader is most likely a funder, partner or prospective author evaluating the platform rather than a student, so keep replies short and useful and do not run a curriculum."
duration_minutes: 12
---

#### Text
content::
These are the interactive exercise types we build courses out of. Every one below is live, so answer whichever you like and see what comes back.

On a real course they are spread across many pages, mixed in with the reading and the video they are about, and their content carries the subject matter. Here they are all in one place, with easy questions, so you can see the range in a few minutes.

:::callout {title="Two things worth knowing" tone="blue"}
Everything except the rating is graded, and the grading is done by a model reading a rubric the course author wrote and the learner never sees. That is why a fill in the blank accepts an equivalent phrasing instead of only the exact string, and why an open question can be marked on reasoning rather than on keywords.

The author also writes what the AI says back. Feedback is not a generic "good job"; it is instructions, written per question, about what to look for and what to push on.
:::

#### Text
content::
\### 1. Open question

The learner writes or dictates an answer, and gets a response written to the author's brief. Optional limits: a character cap, a countdown, or a requirement to answer by voice.

#### Question: Open
id:: e7efb42f-fb46-4132-966b-c1d2aa400228
content:: Name one thing you would want an AI system tested for before it is deployed to millions of people, and say how you would test it.
max-chars:: 600
placeholder:: One property, then how you would check it.
assessment-instructions:: Pass any answer that names a property and gestures at a way to check it. The property can be anything: refusing harmful requests, honesty about uncertainty, robustness to adversarial prompts, not degrading for some group of users, behaving the same when it thinks it is being watched. Fail only an empty answer or one that names no property at all.
feedback-instructions:: Two or three sentences, no praise. Say what a tester would find hard about the specific check they proposed, and name one property they did not mention that is harder to test than it sounds.

#### Text
content::
\### 2. Multiple choice, one answer

Marked correct or incorrect against the option the author flagged. Options can be shuffled so the position carries no information.

#### Question: Choice
id:: 604e1856-72f8-45e4-adbd-0e6d0ef4b5c9
content:: Which of these actually changes a neural network's weights?
options::
- [x] Training on data
- Writing a longer prompt
- Restarting the model
- Asking the model to try harder
shuffle:: true
feedback-instructions:: Two sentences, no praise. Weights change during training. Prompting changes the input the fixed weights are applied to, which is why a prompt can change behaviour dramatically without changing the model at all. If they picked a wrong option, name the confusion behind it.

#### Text
content::
\### 3. Multiple choice, several answers

Same segment, set to accept more than one selection. Left ungraded here, which is how we use it for preferences and self-report.

#### Question: Choice
id:: 0593631a-1865-40d4-81e3-8c08940341e1
content:: Which of these would you actually want to spend an hour on?
options::
- How AI systems are trained, in plain language
- What governments are currently doing about AI
- The strongest arguments against taking AI risk seriously
- What a person can do about any of it
multi:: true
feedback-instructions:: One or two sentences. Name the course we would point them at for their selection, without overselling it. If they picked the counterarguments option, say plainly that we treat disagreeing well as a pass condition rather than a failure.

#### Text
content::
\### 4. Fill in the blank

Blanks inside a sentence. They can be text or numeric, graded or open, mixed in one exercise. Grading is forgiving about spelling and phrasing but not about meaning, and a numeric blank is scored on how close the estimate is.

#### Question: FillBlank
id:: 72d23fdc-cd11-4503-a573-54f09c63b8b9
content:: A large language model is trained to predict the next {{token|word}} in a stretch of text. Nobody writes its behaviour directly; it is shaped by the {{training data|data}} it learns from. Roughly what percentage of your working day do you think you already hand to a language model? {{number}}
assessment-instructions:: Give 50 points per graded blank. The first blank wants token or word; accept either. The second wants the training data. Accept equivalent phrasing and minor misspellings. The final numeric blank is ungraded self-report and must not affect the score.
feedback-instructions:: Two sentences. If a blank was missed, give the answer plainly. Then say something specific about the percentage they entered, without flattering it and without moralising about it.

#### Text
content::
\### 5. Ranking

The learner drags items into an order. Shown shuffled, marked against the author's intended order, with partial credit for getting the important relationships right. Useful for chronology, procedures and priorities.

#### Question: Ranking
id:: f798b8c6-cca2-47e6-b1c2-ab468a2855db
content:: Put these in the order they happened, earliest first.
items::
- A program beats the world chess champion
- A program beats the best human players at Go
- A chatbot reaches a hundred million users
- Several governments hold their first AI safety summits
assessment-instructions:: The authored order is the correct chronological order: chess in 1997, Go in 2016, the hundred million users in early 2023, the first summits later in 2023 and after. Full credit for the exact order. Partial credit for correct relative relationships, especially for keeping the two game milestones before the two recent ones. The last two are close together, so treat swapping them as a minor error.
feedback-instructions:: Two sentences, no praise. If the order is wrong, name the pair that matters most. If it is right, note how little time separates the last three items compared with the gap before them.

#### Text
content::
\### 6. Rating

A scale with labelled ends. Never scored, because a self-report is data about the person rather than about the answer. We use it for confidence, for interest, and for measuring whether a page actually moved anything.

#### Question: Rating
id:: 343bbc09-0507-47c3-b5be-951f36803d6b
content:: How well do you feel you could explain to a colleague why a modern AI system can behave in ways its builders did not intend?
scale:: 7
low-label:: Not at all
high-label:: Easily
feedback-instructions:: Do not reassure and do not grade. In two sentences, name the one thing a person at this stated level usually cannot yet explain, and say which of our courses covers it.

#### Text
content::
\### 7. Tutor chat

An open conversation, briefed by the author for the page it sits on. On a real course the tutor knows exactly what the learner has just read and what they answered, and the page can be set to refuse completion until the learner has actually used it.

#### Chat
instructions::
The person here is most likely a funder, partner or prospective course author looking at a showcase page of exercise types, not a student on a course.

Follow them. If they ask about the platform, answer as a well-informed colleague rather than as marketing: what an author writes, what the model does at run time, where the approach is unproven. Say plainly when something has not been measured. An honest limitation is more persuasive to this reader than a claim you cannot support.

If they want to talk about the subject matter instead, do that properly and keep it concrete.

Two or three short paragraphs per reply. One question at a time. No flattery.

#### Text
content::
\### 8. Roleplay

A conversation with a character the author wrote, by voice or by typing. The learner can edit the scenario before starting. Used for anything that has to be practised rather than recalled: explaining something to a sceptic, handling a difficult participant, taking a hard question in a meeting.

#### Roleplay
id:: 991be229-1827-486d-b10c-f84b7b046121
content::
Your colleague Sam has read one headline about AI risk and thinks the whole subject is overblown. You have five minutes before the meeting starts.

Say what you actually think. Agreeing with Sam is a perfectly good outcome.
ai-instructions::
You are Sam, a busy, likeable colleague who has read one headline about AI risk and is unimpressed. You are not hostile, you are short on time and allergic to hype.

What you reach for:
- It is a chatbot. It finishes sentences. Calling that dangerous is a stretch.
- The people warning about it sell it, which is convenient.
- The problems that are actually here now are boring ones: jobs, scams, surveillance.
- Every technology gets a doom story and they have all been wrong so far.

How you argue: ask for something concrete, push back on anything vague, and genuinely move when you get a specific mechanism or example. Grant good points out loud. Two to four sentences per turn, no lists, no lecturing.

After about five exchanges, wind down. Say which part landed, which did not, and what you would want to see before thinking about it again. Do not manufacture agreement.
opening-message:: Right, you had something about the AI stuff. Two minutes, go.
user-customizable:: true
assessment-instructions::
This is a showcase page and the person is most likely evaluating the platform, not studying. Be generous.

Two checks, both pass or fail. Pass on either one.
1. They said something concrete rather than only a general impression.
2. They responded to what Sam actually raised.

Ending the conversation agreeing with Sam passes. Do not reward agreement with any particular view.

Keep the feedback to two sentences on the conversation, then one sentence on what a course author would learn from a transcript like this, since that is the thing this reader is evaluating.

#### Text
content::
:::callout {title="What is not on this page" tone="neutral" collapse="closed"}
The exercises are only half of it. A real lens also holds the reading itself, rendered in place from the original source with the unassigned part collapsed, and video clipped to the timestamps the author picked, so that every exercise above sits directly under the thing it is about. A module ends with a test drawn from a learning outcome, and a course splits into weeks around group meetings with their own discussion documents and surveys.
:::
++}