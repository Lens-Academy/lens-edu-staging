---
tags:
  - validator-ignore
---
# Writing Rubrics (AI Guide)

How to decide whether a question is graded, and how to write `assessment-instructions::` (the rubric) and `feedback-instructions::` (the tutor's brief) so that a learner who understood the material gets a fair score and useful feedback. Read this whenever you add or edit a question in a lens or a Learning Outcome test.

This file states intentions, not a template. Every rule below has a reason; when a case doesn't fit, follow the reason.

## First decide: graded or not?

Not every question should produce a score. A percentage tells the learner "this was a test of right and wrong".

- **Leave it ungraded** (only `feedback-instructions::`, no `assessment-instructions::`) when the point is recall, reflection, reaction, a prediction before reading, the learner's own project, or anything with no single correctness. The learner still gets a tutor reply, without a number. See "Which field" in [[../AI Guide/Writing Lenses]].
- **Grade it** when there is a real right and wrong the learner should be measured on: a definition, a mechanism, a calculation, a judgement with criteria. Learning Outcome tests are always graded (see [[../AI Guide/Writing (Learning) Outcomes]]).

When in doubt, prefer ungraded. A harsh number on a reflective question does more harm than no number.

## How grading actually works

Know what each model sees, because it decides what a rubric can and cannot do.

- **The grader** sees only a fixed prompt ("a rigorous educational assessor… measure the actual understanding and correctness demonstrated, not effort"), the rubric, the question text and the learner's answer. It never sees the lens, the article, a widget's state, an earlier answer, or a table on the page. Anything the grader needs has to be in the rubric.
- **The tutor**, when the learner asks for feedback, sees the question, the answer, the rubric, the score and the grader's reason, plus the `feedback-instructions::`.
- **Retries are anchored.** On "Answer again", the grader sees the learner's earlier answers and scores and is told to grade consistently with them. An identical answer reuses its old grade. So a grade that was too harsh the first time is carried forward. Changing the rubric or the question text resets the anchor.
- **A quiz grade is shown to the learner as a percentage chip.** Learners read it as a verdict on whether they understood.

## What a good rubric does

The goal: **a learner who understood the idea and answered what was asked gets full marks, in their own words, however informally they write.** Everything below serves that.

1. **Grade what the question asks, all of it and nothing else.** Every scored element must be something the question asks for. If a strong answer to the question as written would lose points, the rubric is wrong. Extra things worth knowing (context, numbers, consequences, the source's framing) are not scored. Put them in a model answer or in the feedback brief if you want the learner to hear them. If an element really matters, make the question ask for it, or drop it from the rubric; decide which by what you want the learner to practise.
2. **Grade understanding, not wording.** Describe ideas, not phrases. No points for using the source's vocabulary, naming the author, or citing a figure, unless the question asks for exactly that.
3. **Give explicit weights.** State points per element, adding up to 100 ("Score out of 100. 60: …; 40: …"). Vague weights ("full credit for…", "partial credit", "about a third") make the grader improvise, usually harshly.
4. **Don't double count, and don't split one idea in two.** Each element must be something a learner could get right independently. A second criterion that restates the first ("why that is enough", "what this means") silently caps a correct answer at the first criterion's weight. The same happens when one idea is cut into halves: "40: the model assumes the odds are fixed; 40: in reality they vary" gives a learner who writes "the odds per attack aren't constant, and the model ignores that" half the credit for one sentence that says both. Make it one element.
5. **General ideas are graded generally.** When a question asks about a term with a general meaning (a backdoor, a protocol, a catastrophe), grade the general meaning. If the source defines it more narrowly for its own purposes, that narrowing is information, not a requirement.
6. **Only what the learner has seen.** Don't make an element out of material that comes later in the lens, or not at all. For predict-before-you-read questions, grade the reasoning, not the answer the next section reveals (or leave them ungraded).
7. **Deduct only for real misconceptions, with a size.** "Cap at 30 if the answer says X" for a genuine error. Not for omissions the weights already cover, and not for style or length unless the question sets a length.
8. **No instructions to the grader about what not to require.** The grader only requires what the rubric asks, so "Do not require term X" is noise, and it is a sign the rubric was written from a model answer rather than from the question. Also leave out tutor guidance, source or partner names, and references to anything the grader can't see.
9. **Self-contained.** If the question refers to a scenario, a document or a previous question, the rubric carries the facts the grader needs to judge the answer.
10. **Describe each element as the idea, in plain terms.** The grader credits what an answer states, and is slow to credit what it clearly implies. An element written in the setup's exact terms ("lands in the unaudited window") costs a learner who says the same thing plainly ("gets a backdoor through after the checks"). Write the element as the idea a learner would say, and use the setup's terms only when the question asks for them.
11. **No partial credit tied to a detail the question doesn't ask for.** "25 of these 50 without a concrete number or quotation" turns a figure into a requirement. If the figure matters, ask for it; if not, leave it out of the rubric.

The question's wording counts too. "Point to specific evidence in the paper" invites the grader to want a number or a quote; "What shows it?" or "How did the red team actually attack?" asks for the idea. Ask for exactly what you will grade.

### A model answer is optional

Add one (at the end: `Model answer, for the feedback, not a grading checklist: "…"`) when the learner should come away knowing the full answer, or when the grader needs a worked reference for a long or numeric task. The label matters: without it the grader treats every sentence of the model answer as required. A model answer from the source is fine; one written by you is fine too, as long as it is correct and answers only what the question asks at the level of detail you want.

Even with the label, the grader leans on the model answer. A figure or a quotation in it ("attacked on 71 of 1,500 problems") gets marked as missing from answers that have the idea without it: in one case, removing the figure moved a complete answer from about 62 to about 85. So keep the model answer to what the question asks. If the learner should also hear a figure or a quote, put it in `feedback-instructions::` ("…then add that the red team attacked on 71 of 1,500 problems"). For a numeric task, give reference values inside the rubric's elements, not in a model answer.

## Feedback instructions

`feedback-instructions::` is its own brief, not a pointer to the rubric. Write what the tutor should do for this question: what good feedback names (the strongest part, the most useful fix), length and tone, whether it's one turn, the house rules in [[../AI Guide/Writing Lenses]] (no generic praise, one concrete foothold when the learner is stuck). It may reveal later content; it doesn't need to protect the next section.

The learner is always entitled to know why they got their score. Don't write "do not mention scores".

Below 100, the feedback should name the most important thing the answer missed or got wrong. At 100 it just confirms. Don't write instructions that skip the gap, such as "say what they got right, then tell them to move on".

## Checks before you call a rubric done

1. **Alignment.** For each scored element, point to the words in the question that ask for it. Anything you can't point to goes. (This is the check in [[../AI Guide/Evals/Learning Outcome Evals/C2 - No unasked demands]].)
2. **Arithmetic.** Points add up to 100; caps and deductions have numbers; sub-points add up to their element.
3. **Grader simulation.** Write two answers a real learner might type: a short, informal, correct one, and a half-right one. Grade both as the platform does (its prompt above plus your rubric). The correct one should score at least 85 and the half-right one somewhere in the middle. If the correct one scores low, read the grader's reason: it names the element that is unasked, double counted or unclear.
4. **Validate.** `lens call validate_content '{"accept_drafts": true}'` and fix any error in the file.

## Examples (before → after)

- **"What is a protocol?"** Before: required "the protocol must answer every problem", a detail of one paper's setup from a section the learner hadn't reached. After: graded on the general idea (several safety measures combined; safe even if the model is trying to subvert them; while still getting useful work), with points.
- **"What makes a solution backdoored?"** The paper adds "and GPT-4 can construct the exploit" for its experiments. Before: that condition cost points. After: graded on "passes the tests but gives a wrong output on some input"; the paper's extra condition and its reason sit in the model answer.
- **"Why can we trust T, the less-capable model?"** Before: 70 for "too weak to scheme without being noticed" plus 30 for "why that is enough", which restated it; correct answers scored 40 to 70. After: 100 for the reason, with the alternative ground (strong confidence in T's alignment) also accepted.
- **"What is the red team's goal?"** Before: points for explaining why getting caught matters (shutdown), which the question doesn't ask; a correct answer got 58. After: 60 for getting a backdoor submitted, 40 for doing it without being caught; the shutdown mechanism is in the model answer.
- **"State why the red team's win probability is not monotonically increasing in $p$."** Before: 40 for how a higher $p$ helps, which the question doesn't ask, and elements in the setup's terms ("the unaudited window"). A correct "they're more likely to get caught" got 25. After: the question asks for both sides ("Raising $p$ helps the red team in one way and hurts it in another. Name both, and say why…"), and the elements are in plain terms (more attempts make it likelier one gets through; likelier one is caught).
- **"Is the optimal strategy predicted by the model reflected in how the red team behaved?"** Before: the question asked for "specific evidence", the rubric gave half credit without "71 of 1,500", and the model answer carried the figure; an answer with the right idea got 60. After: "How did the red team actually attack?", graded on "rarely and selectively, when there was a good opportunity", with the figure moved out of the model answer.
