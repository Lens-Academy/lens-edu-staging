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

{--{"author":"Elias's AI","timestamp":1787223002440}@@Every answerable segment needs:--}{++{"author":"Elias's AI","timestamp":1787223002440}@@Each section below starts with smallest useful version. Only `id::` and `content::` are shared requirements. Everything else may be left out unless course creator wants different behavior.++}

- `id::`: globally unique UUID. It identifies segment in stored responses, grading, and analytics. Never change it after learners have answered.
- `content::`: prompt shown to learner.
- `required:: true`: {--{"author":"Elias's AI","timestamp":1787223002440}@@optional. Response segments are not required by default.--}{++{"author":"Elias's AI","timestamp":1787223002440}@@require response before learner can continue. Defaults to `false`, so leave it out when response may be skipped.++}

Lens Editor should create `id::` automatically. When writing course files by hand, generate UUID at [uuidgenerator.net/version4](https://www.uuidgenerator.net/version4). Tools and language models can request one from [uuidgenerator.net/api/version4](https://www.uuidgenerator.net/api/version4).

Response segments do not need a separate human-readable key.

\## Open response

Use `#### OpenResponse` when learner should type or dictate a response.

> `#### OpenResponse`
> `id:: 1e39cdb1-a286-427d-ac65-580fe8d5c17e`
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
> `id:: 8f9c80dc-1946-44fc-ba50-e964a8e7f4aa`
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
> `id:: f32db9ca-cdf4-4c4d-b53c-50f3456dcac1`
> `content:: Which topic should we cover next?`
> `options::`
> `- Forecasting`
> `- Governance`
> `- Technical safety`
> `required:: true`

For graded practice or test response, mark correct option with `[x]`:

> `#### Select`
> `id:: 234db237-6c5c-43f3-82aa-b19a4ee2708d`
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
> `id:: 69162105-5047-480e-9c38-f5c408c535a7`
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

Use `#### FillBlank`. Write accepted answers directly inside each blank. Separate alternatives with `|`.

> `#### FillBlank`
> `id:: 38b31133-89c0-4bc2-b20f-d8e66a59b594`
> `content:: France's capital is {{Paris}}, while Germany's capital is {{Berlin}}.`
> `explanation:: Paris and Berlin are the respective capitals of France and Germany.`
> `feedback:: true`
> `required:: true`

Multiple accepted answers for one blank:

> `content:: Model weights are commonly updated using {{gradient descent|gradient-based optimization}}.`

Matching is always case-sensitive and ignores whitespace at beginning and end of learner response. There are no `case-sensitive::` or `trim::` options. Each `{{...}}` becomes a separate input. For graded responses, score is fraction of blanks answered correctly.

Use `{{blank}}` when response should be collected without right or wrong answer:

> `#### FillBlank`
> `id:: e7308f54-3b2f-410d-a67c-df916b8c8a19`
> `content:: One change I want to make is {{blank}}.`
> `feedback:: true`

Options:

- `explanation::`: optional text shown after submission.
- `feedback:: true`: ask AI to provide feedback after submission. Defaults to `false`. On ungraded blanks, feedback is coaching only and does not assign correctness.

Within one FillBlank segment, use either answer-bearing blanks or ungraded `{{blank}}` markers, not both.

\## Grading rules

- **Survey:** all Response segment types are ungraded.
- **Normal lens:** responses may be graded practice or ungraded reflection.
- **Learning Outcome test:** OpenResponse and Select must be gradable. FillBlank may use answer-bearing blanks for grading or `{{blank}}` for an ungraded response. OpenResponse needs `assessment-instructions::`; Select needs at least one `[x]`.
- Rating and ungraded FillBlank responses never contribute to correctness score.

Validator should reject duplicate IDs, invalid UUIDs, invalid field combinations, missing grading information where required, invalid rating scales, too few select options, empty answer alternatives, and mixtures of graded and ungraded blanks in one segment.
