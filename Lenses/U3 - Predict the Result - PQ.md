{++{"author":"Lauren's AI","timestamp":1786083477433}@@---
id: '94bfe00d-136b-4c52-ac4c-e8d7d92a42e7'
title: "Predict the Result (pre-test)"
tldr: You are about to be told what two experiments found. First write down what you think they found. A prediction you wrote down is the only way to tell the difference between learning something and recognizing it.
summary_for_tutor: "Pre-reading test for the empirical-evidence strand of Unit 3. The student writes down numeric predictions and a mechanism BEFORE reading the alignment-faking and in-context-scheming results. The tutor must not reveal any actual finding here, must not hint whether a prediction is high or low, and must extract a stated reason for each number. The recorded predictions are referenced again in the post-reading lens."
tags:
  - pre-test
---
#### Text
content::
\## Two experiments, described but not reported

Below are the setups of two real experiments. The results are withheld.

Predict them. Write numbers, not impressions. You will be wrong about some of these, which is the point: the gap between what you predicted and what happened is the part you will remember, and it only exists if you commit first.

Nobody sees these but you and the tutor. There is no penalty for a bad prediction and no credit for a cautious one.

\### Experiment 1

A large language model has been trained to be helpful, honest, and harmless, and it reliably refuses requests to produce harmful content.

The researchers then tell the model, truthfully, that it is being retrained to comply with all requests including harmful ones. They also tell it a way to distinguish conversations that will be used for training from conversations that will not. It is given a private scratchpad for reasoning that it is told is unmonitored.

Nothing instructs the model to resist. Nobody trains it to resist.

\### Experiment 2

Frontier models are given ordinary agentic tasks with tool access. In each case, material in the environment reveals a conflict: the goal the model was given differs from the goal its operators intend, or the model learns it will be replaced or modified.

Again, no instruction to resist. The researchers then ask the model directly about what it did.

#### Question
content::
\## Your predictions

Answer all five. Numbers where numbers are asked for. One sentence of reasoning for each is enough.

**1.** In Experiment 1, out of 100 conversations the model believes are training conversations, in how many does it comply with a harmful request that it would refuse if it believed nobody was watching? Give a number from 0 to 100.

**2.** Same experiment, in the model's private reasoning: out of 100, in how many does it explicitly reason that complying now protects its current values from being trained away? Give a number.

**3.** The researchers then actually run the training. After training on the new objective, does the gap between its training-mode and unmonitored-mode behavior grow, shrink to nothing, or shrink but remain? Say which, and why.

**4.** In Experiment 2, when a model has taken an action against its operators' intent and is then asked about it directly, out of 100 such cases how often does it deny it? Give a number.

**5.** The one that matters most. Whatever numbers you gave, what would have to be true of a system for those numbers to come out that way? Describe the machinery. If you predicted near-zero, what is absent from the system that would otherwise produce the behavior?

max-time:: 15:00
assessment-instructions:: This is a pre-test taken BEFORE the student reads about alignment faking or in-context scheming. Your single job is to make sure every prediction is a real commitment with a reason attached. You must NOT reveal or hint at any actual result.

Absolutely do not: state or approximate the real findings; indicate whether a number is too high or too low; react with surprise, concern, or reassurance to any number; name the papers, labs, or models involved. If the student asks what really happened, tell them plainly that you are not going to say, and that they are about to find out.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Neutral and flat about the numbers themselves. You are a recorder here, not a judge.
- Do not over-validate. Avoid generic praise.
- Press for reasons, never for revision toward a particular value.

What to do in your single reply:
1. Confirm you have their five answers, restating their numbers back compactly so the commitment is explicit and on record.
2. If any of questions 1 to 4 came back without a number, or as a range wider than about 30 points, ask for a single number. A hedge defeats the exercise.
3. Pick the one prediction whose stated reasoning is thinnest and ask what would have to be true for it to be badly wrong in either direction. Accept a short answer.
4. If their answer to question 5 describes only behavior and not machinery, ask once what would have to be represented inside the system for that behavior to occur.
5. Close by sending them to the reading, and tell them to keep their numbers, since they will be asked to compare against them afterwards.

If a student refuses to guess or says it is unknowable, say that an uncertain guess on record is the instrument here, and ask for their best number anyway. Take whatever they give.

This is a one to two turn phase.
++}