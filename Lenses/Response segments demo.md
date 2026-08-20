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

Each section below starts with smallest useful version. Only `id::` and `content::` are shared requirements. Everything else may be left out unless course creator wants different behavior.

- `id::`: globally unique UUID. It identifies segment in stored responses, grading, and analytics. Never change it after learners have answered.
- `content::`: prompt shown to learner.
- `required:: true`: require response before learner can continue. Defaults to `false`, so leave it out when response may be skipped.

Lens Editor should create `id::` automatically. When writing course files by hand, generate UUID at [uuidgenerator.net/version4](https://www.uuidgenerator.net/version4). Tools and language models can request one from [uuidgenerator.net/api/version4](https://www.uuidgenerator.net/api/version4).

Response segments do not need a separate human-readable key.

\## Open response

Use `#### OpenResponse` when learner should type or dictate a response.

Smallest version:

> `#### OpenResponse`
> `id:: <uuid>`
> `content:: What is your strongest objection?`

Here is that minimal segment for learner to try:

#### OpenResponse
id:: 3e1a5838-95df-4d05-a88a-1b4ca868905f
content:: What is your strongest objection?

#### Text
content::
Optional fields:

- `required:: true`: require response. Defaults to `false`.
- `max-chars:: 500`: limit answer length. Defaults to no limit.
- `placeholder:: Name the claim, then explain objection.`: show hint in empty input. Defaults to no placeholder.
- `max-time:: 3:00`: set answer timer in `M:SS`. Defaults to no timer.
- `enforce-voice:: true`: require spoken response instead of typing. Defaults to `false`.
- `assessment-instructions:: ...`: give AI grading rubric. Without it, response is ungraded.
- `feedback:: true`: show AI feedback after submission. Defaults to `false`.

Surveys ignore grading and feedback fields. They store response without grading it.

\## Rating

Use `#### Rating` for numbered scale from 1 to 5.

Smallest version:

> `#### Rating`
> `id:: <uuid>`
> `content:: How confident are you in your answer?`

Try it:

#### Rating
id:: 4280d5f2-2cd5-48f9-b20f-fc132253d443
content:: How confident are you in your answer?

#### Text
content::
Optional fields:

- `required:: true`: require response. Defaults to `false`.
- `scale:: 7`: set highest number from 2 to 10. Defaults to `5`.
- `low-label:: Not confident`: label low endpoint. Defaults to no label.
- `high-label:: Very confident`: label high endpoint. Defaults to no label.

Ratings are self-reports, not correct or incorrect. In Learning Outcome tests, rating is stored beside graded answers but does not affect test score.

\## Single select

Use `#### Select` with `options::`. With no `[x]`, response is ungraded.

Smallest version:

> `#### Select`
> `id:: <uuid>`
> `content:: Which topic should we cover next?`
> `options::`
> `- Forecasting`
> `- Governance`

Try it:

#### Select
id:: a59ce650-c5cf-4b2b-bc13-e0686f5d2bfb
content:: Which topic should we cover next?
options::
- Forecasting
- Governance

#### Text
content::
Mark correct option with `[x]` when response should be graded:

> `options::`
> `- Data collection`
> `- [x] Gradient descent`
> `- Deployment monitoring`

Optional fields:

- `required:: true`: require response. Defaults to `false`.
- `multi:: true`: allow multiple selections. Defaults to `false`.
- `shuffle:: true`: randomize option order. Defaults to `false`.
- `explanation:: ...`: show fixed explanation after submission. Defaults to no explanation.

Survey selects must use plain list items. Surveys never contain correct-answer markers.

\## Multi-select

Multi-select is same Response segment with one non-default field: `multi:: true`.

Smallest version:

> `#### Select`
> `id:: <uuid>`
> `content:: Which topics interest you?`
> `options::`
> `- Forecasting`
> `- Governance`
> `- Technical safety`
> `multi:: true`

Try it:

#### Select
id:: cb39e8f1-4477-4b66-b016-37c99c5ff753
content:: Which topics interest you?
options::
- Forecasting
- Governance
- Technical safety
multi:: true

#### Text
content::
It has same optional fields and defaults as single select. For graded multi-select, learner's selected options must exactly match all `[x]` options. In surveys, options stay ungraded and use no `[x]` markers.

\## Fill in the blank

Use `#### FillBlank`. Write accepted answer directly inside blank.

Smallest graded version:

> `#### FillBlank`
> `id:: <uuid>`
> `content:: France's capital is {{Paris}}.`

Try it:

#### FillBlank
id:: ec12502a-e39c-4589-87f5-9f14855648c9
content:: France's capital is {{Paris}}.

#### Text
content::
Separate alternative accepted answers with `|`:

> `content:: Model weights are commonly updated using {{gradient descent|gradient-based optimization}}.`

Put several blanks in one sentence:

> `content:: France's capital is {{Paris}}, while Germany's capital is {{Berlin}}.`

Each `{{...}}` becomes separate input. Matching is always case-sensitive and ignores whitespace at beginning and end of learner response. There are no `case-sensitive::` or `trim::` fields. Graded score is fraction of blanks answered correctly.

Use `{{blank}}` when response should have no right or wrong answer.

Smallest ungraded version:

> `#### FillBlank`
> `id:: <uuid>`
> `content:: One change I want to make is {{blank}}.`

Try it:

#### FillBlank
id:: e7308f54-3b2f-410d-a67c-df916b8c8a19
content:: One change I want to make is {{blank}}.

#### Text
content::
Optional fields:

- `required:: true`: require every blank. Defaults to `false`.
- `explanation:: ...`: show fixed text after submission. Defaults to no explanation.
- `feedback:: true`: ask AI to provide feedback after submission. Defaults to `false`. On ungraded blanks, feedback is coaching only and does not assign correctness.

Within one FillBlank segment, use either answer-bearing blanks or ungraded `{{blank}}` markers, not both.

\## Grading rules

- **Survey:** all Response segment types are ungraded.
- **Normal lens:** responses may be graded practice or ungraded reflection.
- **Learning Outcome test:** OpenResponse and Select must be gradable. FillBlank may use answer-bearing blanks for grading or `{{blank}}` for an ungraded response. OpenResponse needs `assessment-instructions::`; Select needs at least one `[x]`.
- Rating and ungraded FillBlank responses never contribute to correctness score.
