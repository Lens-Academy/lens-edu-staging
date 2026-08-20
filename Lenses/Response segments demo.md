---
id: 8189763f-576e-4f04-a614-4a00c628e386
title: Response segments
tldr: Use open responses, ratings, selects, and fill-in-the-blank responses with the same syntax in surveys, normal lenses, and learning-outcome tests.
summary_for_tutor: Reference page for course creators. It documents shared fields, exact syntax, options, defaults, and grading behavior for OpenResponse, Rating, Select, and FillBlank Response segments.
---

#### Text
content::
\## Response segments work in three places

A Response segment is an interactive field that collects one learner response, such as written text, a rating, a selection, or a missing phrase.

Use Response segments in:

- **Surveys** to collect ungraded responses.
- **Normal lenses** for practice, reflection, and checks for understanding.
- **Learning Outcome tests** for graded assessment.

Syntax is identical in all three places. Context changes whether a response is graded, not how segment is written.

Every answerable segment needs:

- {--{"author":"Elias's AI","timestamp":1787222606681}@@`key::`: stable `snake_case` identifier, unique within that survey, lens, or test.--}{++{"author":"Elias's AI","timestamp":1787222606681}@@`id::`: globally unique UUID. It identifies segment in stored responses, grading, and analytics. Never change it after learners have answered.++}
- `content::`: prompt shown to learner.
- `required:: true`: optional. Response segments are not required by default.

{--{"author":"Elias's AI","timestamp":1787222606681}@@Never change `key::` after learners have answered. Stored answers use this--}{++{"author":"Elias's AI","timestamp":1787222606681}@@Lens Editor should create `id::` automatically. When writing course files by hand, generate UUID at [uuidgenerator.net/version4](https://www.uuidgenerator.net/version4). Tools and language models can request one from [uuidgenerator.net/api/version4](https://www.uuidgenerator.net/api/version4).

Response segments do not need a separate human-readable++} key.

\## Open response

Use `#### OpenResponse` when learner should type or dictate a response.

> `#### OpenResponse`
> {--{"author":"Elias's AI","timestamp":1787222609266}@@`key:: strongest_objection`--}{++{"author":"Elias's AI","timestamp":1787222609266}@@`id:: 1e39cdb1-a286-427d-ac65-580fe8d5c17e`++}
> `content:: In two sentences, what is the strongest objection?`
> `required:: true`
> `max-chars:: 500`
> `placeholder:: Name the claim, then explain objection.`
> `max-time:: 3:00`
> `enforce-voice:: false`
> `assessment-instructions:: Check whether learner names a claim and gives a relevant objection.`
> `feedback:: true`

Options:

- `max-chars::`: maximum answer length.
- `placeholder::`: hint shown in empty input.
- `max-time::`: answer timer in `M:SS`, or `none`.
- `enforce-voice:: true`: require spoken answer.
- `assessment-instructions::`: rubric for AI assessment.
- `feedback::`: whether learner receives AI feedback. Defaults to `true` in lenses and tests.

Surveys do not use `assessment-instructions::` or `feedback::`. They store response without grading it.

\## Rating

Use `#### Rating` for numbered scale from 1 to N.

> `#### Rating`
> `key:: confidence`
> `content:: How confident are you in your answer?`
> `scale:: 7`
> `low-label:: Not confident`
> `high-label:: Very confident`
> `required:: true`

Options:

- `scale::`: integer from 2 to 10. Defaults to 5.
- `low-label::`: optional label below low endpoint.
- `high-label::`: optional label below high endpoint.

Ratings are self-reports, not correct or incorrect. In Learning Outcome tests, rating is stored beside graded answers but does not affect test score.

\## Single select

Use `#### Select` with plain list under `options::`. Default allows one selection.

Ungraded example:

> `#### Select`
> `key:: next_topic`
> `content:: Which topic should we cover next?`
> `options::`
> `- Forecasting`
> `- Governance`
> `- Technical safety`
> `required:: true`

For graded practice or test response, mark correct option with `[x]`:

> `#### Select`
> `key:: optimizer`
> `content:: Which process updates model weights during training?`
> `options::`
> `- Data collection`
> `- [x] Gradient descent`
> `- Deployment monitoring`
> `shuffle:: true`
> `explanation:: Gradient descent updates weights using gradients of loss.`

Options:

- `shuffle:: true`: randomize option order. Defaults to `false`.
- `explanation::`: optional feedback shown after submission.

Survey selects must use plain list items. Surveys never contain correct-answer markers.

\## Multi-select

Add `multi:: true` when learner may select more than one option.

> `#### Select`
> `key:: empirical_evidence`
> `content:: Which two items are empirical evidence?`
> `options::`
> `- [x] A measured benchmark result`
> `- A definition`
> `- [x] A randomized trial result`
> `- A thought experiment`
> `multi:: true`
> `shuffle:: true`
> `explanation:: Measurements and trial results are empirical evidence.`

A graded response is correct only when selected options exactly match every `[x]` option. In surveys, `multi:: true` works the same way but options stay ungraded and use no `[x]` markers.

\## Fill in the blank

Use `#### FillBlank`. Put exactly one `{{blank}}` marker in prompt.

> `#### FillBlank`
> `key:: training_method`
> `content:: Model weights are commonly updated using {{blank}}.`
> `accepted-answers::`
> `- gradient descent`
> `- gradient-based optimization`
> `case-sensitive:: false`
> `trim:: true`
> `explanation:: Gradient descent uses loss gradients to update model weights.`
> `required:: true`

Options:

- `accepted-answers::`: one or more complete accepted answers.
- `case-sensitive::`: defaults to `false`.
- `trim::`: ignore leading and trailing whitespace. Defaults to `true`.
- `explanation::`: optional feedback shown after submission.

Matching is exact after configured case and whitespace normalization. Use several FillBlank segments when exercise needs several blanks.

Surveys may use FillBlank without `accepted-answers::` or `explanation::`. That makes it an ungraded short-answer field.

\## Grading rules

- **Survey:** all Response segment types are ungraded.
- **Normal lens:** responses may be graded practice or ungraded reflection.
- **Learning Outcome test:** OpenResponse, Select, and FillBlank must be gradable. OpenResponse needs `assessment-instructions::`; Select needs at least one `[x]`; FillBlank needs `accepted-answers::`.
- Rating never contributes to correctness score.

Validator should reject duplicate keys, invalid field combinations, missing grading information in tests, invalid rating scales, too few select options, and missing or multiple `{{blank}}` markers.
