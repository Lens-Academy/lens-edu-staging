---
id: 8189763f-576e-4f04-a614-4a00c628e386
title: Question types
tldr: Use open-text, rating, choice, and fill-in-the-blank questions with the same syntax in surveys, normal lenses, and learning-outcome tests.
summary_for_tutor: Reference page for course creators. It documents the shared fields, exact syntax, type-specific options, defaults, and grading behavior for Question, Rating, Choice, and FillBlank segments.
---

#### Text
content::
\## Questions work in three places

Use question segments in:

- **Surveys** to collect ungraded responses.
- **Normal lenses** for practice, reflection, and checks for understanding.
- **Learning Outcome tests** for graded assessment.

Syntax is identical in all three places. Context changes whether an answer is graded, not how the question is written.

Every answerable segment needs:

- `key&#58;&#58;`: stable `snake_case` identifier, unique within that survey, lens, or test.
- `content&#58;&#58;`: prompt shown to learner.
- `required&#58;&#58; true`: optional. Questions are not required by default.

Never change `key&#58;&#58;` after learners have answered. Stored answers use this key.

\## Open-text question

Use `#### Question` when learner should type or dictate a response.

{--{"author":"Elias's AI","timestamp":1787220805012}@@```md
\####--}{++{"author":"Elias's AI","timestamp":1787220805012}@@<pre><code>####++} Question
key&#58;&#58; strongest_objection
content&#58;&#58; In two sentences, what is the strongest objection?
required&#58;&#58; true
max-chars&#58;&#58; 500
placeholder&#58;&#58; Name the claim, then explain objection.
max-time&#58;&#58; 3:00
enforce-voice&#58;&#58; false
assessment-instructions&#58;&#58; Check whether learner names a claim and gives a relevant objection.
feedback&#58;&#58; {--{"author":"Elias's AI","timestamp":1787220805012}@@true
```--}{++{"author":"Elias's AI","timestamp":1787220805012}@@true</code></pre>++}

Options:

- `max-chars&#58;&#58;`: maximum answer length.
- `placeholder&#58;&#58;`: hint shown in empty input.
- `max-time&#58;&#58;`: answer timer in `M:SS`, or `none`.
- `enforce-voice&#58;&#58; true`: require spoken answer.
- `assessment-instructions&#58;&#58;`: rubric for AI assessment.
- `feedback&#58;&#58;`: whether learner receives AI feedback. Defaults to `true` in lenses and tests.

Surveys do not use `assessment-instructions&#58;&#58;` or `feedback&#58;&#58;`. They store response without grading it.

\## Rating

Use `#### Rating` for numbered scale from 1 to N.

{--{"author":"Elias's AI","timestamp":1787220807924}@@```md
\####--}{++{"author":"Elias's AI","timestamp":1787220807924}@@<pre><code>####++} Rating
key&#58;&#58; confidence
content&#58;&#58; How confident are you in your answer?
scale&#58;&#58; 7
low-label&#58;&#58; Not confident
high-label&#58;&#58; Very confident
required&#58;&#58; {--{"author":"Elias's AI","timestamp":1787220807924}@@true
```--}{++{"author":"Elias's AI","timestamp":1787220807924}@@true</code></pre>++}

Options:

- `scale&#58;&#58;`: integer from 2 to 10. Defaults to 5.
- `low-label&#58;&#58;`: optional label below low endpoint.
- `high-label&#58;&#58;`: optional label below high endpoint.

Ratings are self-reports, not correct or incorrect. In Learning Outcome tests, rating is stored beside graded answers but does not affect test score.

\## Single-choice question

Use `#### Choice` with plain list under `options&#58;&#58;`. Default allows one selection.

Ungraded example:

```md
\#### Choice
key&#58;&#58; next_topic
content&#58;&#58; Which topic should we cover next?
options&#58;&#58;
- Forecasting
- Governance
- Technical safety
required&#58;&#58; true
```

For graded practice or test question, mark correct option with `[x]`:

```md
\#### Choice
key&#58;&#58; optimizer
content&#58;&#58; Which process updates model weights during training?
options&#58;&#58;
- Data collection
- [x] Gradient descent
- Deployment monitoring
shuffle&#58;&#58; true
explanation&#58;&#58; Gradient descent updates weights using gradients of loss.
```

Options:

- `shuffle&#58;&#58; true`: randomize option order. Defaults to `false`.
- `explanation&#58;&#58;`: optional feedback shown after submission.

Survey choices must use plain list items. Surveys never contain correct-answer markers.

\## Multiple-choice question

Add `multi&#58;&#58; true` when learner may select more than one option.

```md
\#### Choice
key&#58;&#58; empirical_evidence
content&#58;&#58; Which two items are empirical evidence?
options&#58;&#58;
- [x] A measured benchmark result
- A definition
- [x] A randomized trial result
- A thought experiment
multi&#58;&#58; true
shuffle&#58;&#58; true
explanation&#58;&#58; Measurements and trial results are empirical evidence.
```

A graded response is correct only when selected options exactly match every `[x]` option. In surveys, `multi&#58;&#58; true` works the same way but options stay ungraded and use no `[x]` markers.

\## Fill in the blank

Use `#### FillBlank`. Put exactly one `{{blank}}` marker in prompt.

```md
\#### FillBlank
key&#58;&#58; training_method
content&#58;&#58; Model weights are commonly updated using {{blank}}.
accepted-answers&#58;&#58;
- gradient descent
- gradient-based optimization
case-sensitive&#58;&#58; false
trim&#58;&#58; true
explanation&#58;&#58; Gradient descent uses loss gradients to update model weights.
required&#58;&#58; true
```

Options:

- `accepted-answers&#58;&#58;`: one or more complete accepted answers.
- `case-sensitive&#58;&#58;`: defaults to `false`.
- `trim&#58;&#58;`: ignore leading and trailing whitespace. Defaults to `true`.
- `explanation&#58;&#58;`: optional feedback shown after submission.

Matching is exact after configured case and whitespace normalization. Use several FillBlank segments when exercise needs several blanks.

Surveys may use FillBlank without `accepted-answers&#58;&#58;` or `explanation&#58;&#58;`. That makes it an ungraded short-answer field.

\## Grading rules

- **Survey:** all question types are ungraded.
- **Normal lens:** questions may be graded practice or ungraded reflection.
- **Learning Outcome test:** Question, Choice, and FillBlank must be gradable. Question needs `assessment-instructions&#58;&#58;`; Choice needs at least one `[x]`; FillBlank needs `accepted-answers&#58;&#58;`.
- Rating never contributes to correctness score.

Validator should reject duplicate keys, invalid field combinations, missing grading information in tests, invalid rating scales, too few choice options, and missing or multiple `{{blank}}` markers.
