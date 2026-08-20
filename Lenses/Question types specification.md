{++{"author":"Elias's AI","timestamp":1787219720005}@@---
id: '0a7b39f9-e1e1-43bd-8a55-4bd3a0397cbd'
title: Question types specification
tldr: One Question segment can collect text, ratings, choices, or a fill-in-the-blank answer in surveys, practice lenses, and learning-outcome tests.
summary_for_tutor: This is an executable product specification, not a live widget demo yet. It defines one shared Question segment with text, rating, choice, and fill-blank types, shared fields, type-specific fields, defaults, correctness behavior, and context rules for surveys, lenses, and learning-outcome tests.
---

#### Text
content::
## Proposed shared model

Surveys, normal lenses, and learning-outcome tests should use one `#### Question` segment. The `type::` field changes the answer control. Authors should not need to learn separate `#### Rating` or `#### Choice` formats for different contexts.

This page is a product specification. Until platform support lands, examples below display as code rather than live controls.

Every question uses:

```md
\#### Question
type:: text
key:: reflection
content:: What changed your mind?
required:: true
```

- `type::` is `text`, `rating`, `choice`, or `fill-blank`. It defaults to `text`.
- `key::` is a stable `snake_case` answer identifier, unique within its survey, lens, or test. Do not change it after learners answer.
- `content::` is the learner-facing prompt.
- `required::` controls completion. It defaults to `false`.
- A required answer is not automatically a correct answer.

## Free text

```md
\#### Question
type:: text
key:: reflection
content:: In two sentences, what is the strongest objection?
required:: true
max-chars:: 500
placeholder:: Name the claim, then explain the objection.
max-time:: 3:00
enforce-voice:: false
assessment-instructions:: Check whether the learner names a claim and gives a relevant objection.
feedback:: true
```

Options:

- `max-chars::` limits answer length.
- `placeholder::` gives input guidance.
- `max-time::` accepts `M:SS` or `none`.
- `enforce-voice:: true` requires a spoken answer.
- `assessment-instructions::` gives the AI a rubric.
- `feedback::` controls AI feedback and defaults to `true` in lenses and tests.

## Rating

```md
\#### Question
type:: rating
key:: confidence
content:: How confident are you in your answer?
required:: true
scale:: 7
low-label:: Not confident
high-label:: Very confident
```

`scale::` accepts 2 through 10 and defaults to 5. Endpoint labels are optional. Ratings measure a learner's report, not correctness. A rating in a learning-outcome test can be stored beside scored questions but does not add to the correctness score.

## Single choice

```md
\#### Question
type:: choice
key:: optimizer
content:: Which process updates model weights during training?
options::
- Data collection
- [x] Gradient descent
- Deployment monitoring
multi:: false
shuffle:: true
required:: true
explanation:: Gradient descent updates weights using gradients of the loss.
```

Mark each correct option with `[x]`. Unmarked options are distractors. `multi:: false` allows one answer and is the default. `shuffle:: true` randomizes display order and defaults to `false`. `explanation::` is optional post-submission feedback.

For an unscored preference question, use plain options:

```md
\#### Question
type:: choice
key:: next_topic
content:: Which topic should we cover next?
options::
- Forecasting
- Governance
- Technical safety
```

## Multiple choice

```md
\#### Question
type:: choice
key:: evidence
content:: Which two items are empirical evidence?
options::
- [x] A measured benchmark result
- A definition
- [x] A randomized trial result
- A thought experiment
multi:: true
shuffle:: true
explanation:: Measurements and trial results are empirical evidence.
```

With `multi:: true`, learners may select multiple options. A scored answer is correct only when selected options exactly match all `[x]` options.

## Fill in the blank

Place exactly one `{{blank}}` marker in `content::`.

```md
\#### Question
type:: fill-blank
key:: training_method
content:: Model weights are commonly updated using {{blank}}.
accepted-answers::
- gradient descent
- gradient-based optimization
case-sensitive:: false
trim:: true
required:: true
explanation:: Gradient descent uses loss gradients to update model weights.
```

- `accepted-answers::` lists one or more complete accepted answers.
- Matching is exact after optional whitespace trimming.
- `case-sensitive::` defaults to `false`.
- `trim::` defaults to `true`.
- `explanation::` is optional post-submission feedback.
- One blank per segment keeps stored answers, feedback, and analytics unambiguous. Authors can use several fill-blank segments when they need several blanks.

## Context rules

The segment schema and parser should live in one shared implementation. Context adds validation and storage behavior, not a second question model.

| Context | Unscored questions | Correct answers | AI assessment | Stored under |
|---|---:|---:|---:|---|
| Survey | Yes | No | No | Survey response |
| Normal lens | Yes | Optional | Optional | Practice response |
| Learning-outcome test | Rating only | Required for choice and fill-blank | Required for scored text | Test attempt |

In surveys, checkbox-marked options, `accepted-answers::`, `assessment-instructions::`, `feedback::`, and `explanation::` are invalid. Survey questions collect responses; they do not grade learners.

In normal lenses, questions are practice. Choice and fill-blank questions may be scored or unscored. Text questions may request AI feedback or simply record an answer.

In learning-outcome tests, every text, choice, or fill-blank question must be gradable. Text uses `assessment-instructions::`; choice uses at least one `[x]`; fill-blank uses `accepted-answers::`. Rating questions are allowed as unscored confidence or self-report items.

## Defaults

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