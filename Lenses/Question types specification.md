{++{"author":"Elias's AI","timestamp":1787219906853}@@---
id: '0a7b39f9-e1e1-43bd-8a55-4bd3a0397cbd'
title: Question types specification
tldr: One Question segment can collect text, ratings, choices, or a fill-in-the-blank answer in surveys, practice lenses, and learning-outcome tests.
summary_for_tutor: This is an executable product specification, not a live widget demo yet. It defines one shared Question segment with text, rating, choice, and fill-blank types, shared fields, type-specific fields, defaults, correctness behavior, and context rules for surveys, lenses, and learning-outcome tests.
---

#### Text
content::
\## Proposed shared model

Surveys, normal lenses, and learning-outcome tests should use one `#### Question` segment. The `type&#58;&#58;` field changes the answer control. Authors should not need separate `#### Rating` or `#### Choice` formats for different contexts.

This page is a product specification. Until platform support lands, examples below display as code rather than live controls.

Every question uses:

```md
\#### Question
type&#58;&#58; text
key&#58;&#58; reflection
content&#58;&#58; What changed your mind?
required&#58;&#58; true
```

- `type&#58;&#58;` is `text`, `rating`, `choice`, or `fill-blank`. It defaults to `text`.
- `key&#58;&#58;` is a stable `snake_case` answer identifier, unique within its survey, lens, or test. Do not change it after learners answer.
- `content&#58;&#58;` is the learner-facing prompt.
- `required&#58;&#58;` controls completion. It defaults to `false`.
- A required answer is not automatically a correct answer.

\## Free text

```md
\#### Question
type&#58;&#58; text
key&#58;&#58; reflection
content&#58;&#58; In two sentences, what is the strongest objection?
required&#58;&#58; true
max-chars&#58;&#58; 500
placeholder&#58;&#58; Name the claim, then explain the objection.
max-time&#58;&#58; 3:00
enforce-voice&#58;&#58; false
assessment-instructions&#58;&#58; Check whether the learner names a claim and gives a relevant objection.
feedback&#58;&#58; true
```

Options:

- `max-chars&#58;&#58;` limits answer length.
- `placeholder&#58;&#58;` gives input guidance.
- `max-time&#58;&#58;` accepts `M:SS` or `none`.
- `enforce-voice&#58;&#58; true` requires a spoken answer.
- `assessment-instructions&#58;&#58;` gives the AI a rubric.
- `feedback&#58;&#58;` controls AI feedback and defaults to `true` in lenses and tests.

\## Rating

```md
\#### Question
type&#58;&#58; rating
key&#58;&#58; confidence
content&#58;&#58; How confident are you in your answer?
required&#58;&#58; true
scale&#58;&#58; 7
low-label&#58;&#58; Not confident
high-label&#58;&#58; Very confident
```

`scale&#58;&#58;` accepts 2 through 10 and defaults to 5. Endpoint labels are optional. Ratings measure a learner's report, not correctness. A rating in a learning-outcome test can be stored beside scored questions but does not add to the correctness score.

\## Single choice

```md
\#### Question
type&#58;&#58; choice
key&#58;&#58; optimizer
content&#58;&#58; Which process updates model weights during training?
options&#58;&#58;
- Data collection
- [x] Gradient descent
- Deployment monitoring
multi&#58;&#58; false
shuffle&#58;&#58; true
required&#58;&#58; true
explanation&#58;&#58; Gradient descent updates weights using gradients of the loss.
```

Mark each correct option with `[x]`. Unmarked options are distractors. `multi&#58;&#58; false` allows one answer and is the default. `shuffle&#58;&#58; true` randomizes display order and defaults to `false`. `explanation&#58;&#58;` is optional post-submission feedback.

For an unscored preference question, use plain options:

```md
\#### Question
type&#58;&#58; choice
key&#58;&#58; next_topic
content&#58;&#58; Which topic should we cover next?
options&#58;&#58;
- Forecasting
- Governance
- Technical safety
```

\## Multiple choice

```md
\#### Question
type&#58;&#58; choice
key&#58;&#58; evidence
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

With `multi&#58;&#58; true`, learners may select multiple options. A scored answer is correct only when selected options exactly match all `[x]` options.

\## Fill in the blank

Place exactly one `{{blank}}` marker in `content&#58;&#58;`.

```md
\#### Question
type&#58;&#58; fill-blank
key&#58;&#58; training_method
content&#58;&#58; Model weights are commonly updated using {{blank}}.
accepted-answers&#58;&#58;
- gradient descent
- gradient-based optimization
case-sensitive&#58;&#58; false
trim&#58;&#58; true
required&#58;&#58; true
explanation&#58;&#58; Gradient descent uses loss gradients to update model weights.
```

- `accepted-answers&#58;&#58;` lists one or more complete accepted answers.
- Matching is exact after optional whitespace trimming.
- `case-sensitive&#58;&#58;` defaults to `false`.
- `trim&#58;&#58;` defaults to `true`.
- `explanation&#58;&#58;` is optional post-submission feedback.
- One blank per segment keeps stored answers, feedback, and analytics unambiguous. Authors can use several fill-blank segments when they need several blanks.

\## Context rules

The segment schema and parser should live in one shared implementation. Context adds validation and storage behavior, not a second question model.

| Context | Unscored questions | Correct answers | AI assessment | Stored under |
|---|---:|---:|---:|---|
| Survey | Yes | No | No | Survey response |
| Normal lens | Yes | Optional | Optional | Practice response |
| Learning-outcome test | Rating only | Required for choice and fill-blank | Required for scored text | Test attempt |

In surveys, checkbox-marked options, `accepted-answers&#58;&#58;`, `assessment-instructions&#58;&#58;`, `feedback&#58;&#58;`, and `explanation&#58;&#58;` are invalid. Survey questions collect responses; they do not grade learners.

In normal lenses, questions are practice. Choice and fill-blank questions may be scored or unscored. Text questions may request AI feedback or simply record an answer.

In learning-outcome tests, every text, choice, or fill-blank question must be gradable. Text uses `assessment-instructions&#58;&#58;`; choice uses at least one `[x]`; fill-blank uses `accepted-answers&#58;&#58;`. Rating questions are allowed as unscored confidence or self-report items.

\## Defaults

| Field | Default |
|---|---|
| `type` | `text` |
| `required` | `false` |
| `scale` | `5` |
| `multi` | `false` |
| `shuffle` | `false` |
| `case-sensitive` | `false` |
| `trim` | `true` |
| `feedback` | `true` in lenses and tests |

Unknown fields, invalid combinations, duplicate keys, answerless scored questions, and multiple or missing `{{blank}}` markers should be validator errors.
++}