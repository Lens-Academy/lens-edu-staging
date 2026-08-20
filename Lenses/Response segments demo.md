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

{++{"author":"Elias's AI","timestamp":1787223019458}@@Smallest version:

++}> `#### OpenResponse`
> `id:: {--{"author":"Elias's AI","timestamp":1787223019458}@@1e39cdb1-a286-427d-ac65-580fe8d5c17e`--}{++{"author":"Elias's AI","timestamp":1787223019458}@@<uuid>`++}
> `content:: {--{"author":"Elias's AI","timestamp":1787223019458}@@In two sentences, what --}{++{"author":"Elias's AI","timestamp":1787223019458}@@What is your strongest objection?`

Here ++}is {--{"author":"Elias's AI","timestamp":1787223019458}@@the strongest objection?`
> `required:: true`
> `max-chars:: 500`--}{++{"author":"Elias's AI","timestamp":1787223019458}@@that minimal segment for learner to try:

#### OpenResponse++}
{--{"author":"Elias's AI","timestamp":1787223019458}@@> `placeholder:: Name the claim, then explain objection.`--}{++{"author":"Elias's AI","timestamp":1787223019458}@@id:: 3e1a5838-95df-4d05-a88a-1b4ca868905f
content:: What is your strongest objection?

#### Text++}
{--{"author":"Elias's AI","timestamp":1787223019458}@@> `max-time:: 3:00`
> `enforce-voice:: false`
> `assessment-instructions:: Check whether learner names a claim and gives a relevant objection.`--}{++{"author":"Elias's AI","timestamp":1787223019458}@@content::
Optional fields:

- `required:: true`: require response. Defaults to `false`.
- `max-chars:: 500`: limit answer length. Defaults to no limit.++}
{--{"author":"Elias's AI","timestamp":1787223019458}@@> `feedback:: true`

Options:

- `max-chars::`: maximum answer length.
- `placeholder::`:--}{++{"author":"Elias's AI","timestamp":1787223019458}@@- `placeholder:: Name the claim, then explain objection.`: show++} hint{--{"author":"Elias's AI","timestamp":1787223019458}@@ shown--} in empty input.{++{"author":"Elias's AI","timestamp":1787223019458}@@ Defaults to no placeholder.++}
- {--{"author":"Elias's AI","timestamp":1787223019458}@@`max-time::`:--}{++{"author":"Elias's AI","timestamp":1787223019458}@@`max-time:: 3:00`: set++} answer timer in {--{"author":"Elias's AI","timestamp":1787223019458}@@`M:SS`, or `none`.--}{++{"author":"Elias's AI","timestamp":1787223019458}@@`M:SS`. Defaults to no timer.++}
- `enforce-voice:: true`: require spoken {--{"author":"Elias's AI","timestamp":1787223019458}@@answer.--}{++{"author":"Elias's AI","timestamp":1787223019458}@@response instead of typing. Defaults to `false`.++}
- {--{"author":"Elias's AI","timestamp":1787223019458}@@`assessment-instructions::`: rubric for--}{++{"author":"Elias's AI","timestamp":1787223019458}@@`assessment-instructions:: ...`: give++} AI {--{"author":"Elias's AI","timestamp":1787223019458}@@assessment.--}{++{"author":"Elias's AI","timestamp":1787223019458}@@grading rubric. Without it, response is ungraded.++}
- {--{"author":"Elias's AI","timestamp":1787223019458}@@`feedback::`: whether learner receives AI feedback.--}{++{"author":"Elias's AI","timestamp":1787223019458}@@`feedback:: true`: show AI feedback after submission.++} Defaults to {--{"author":"Elias's AI","timestamp":1787223019458}@@`true` in lenses and tests.--}{++{"author":"Elias's AI","timestamp":1787223019458}@@`false`.++}

Surveys {--{"author":"Elias's AI","timestamp":1787223019458}@@do not use `assessment-instructions::` or `feedback::`.--}{++{"author":"Elias's AI","timestamp":1787223019458}@@ignore grading and feedback fields.++} They store response without grading it.

\## Rating

Use `#### Rating` for numbered scale from 1 to {--{"author":"Elias's AI","timestamp":1787223032488}@@N.--}{++{"author":"Elias's AI","timestamp":1787223032488}@@5.++}

{++{"author":"Elias's AI","timestamp":1787223032488}@@Smallest version:

++}> `#### Rating`
> `id:: {--{"author":"Elias's AI","timestamp":1787223032488}@@8f9c80dc-1946-44fc-ba50-e964a8e7f4aa`--}{++{"author":"Elias's AI","timestamp":1787223032488}@@<uuid>`++}
> `content:: How confident are you in your answer?`{++{"author":"Elias's AI","timestamp":1787223032488}@@

Try it:

#### Rating++}
{--{"author":"Elias's AI","timestamp":1787223032488}@@> `scale:: 7`
> `low-label:: Not confident`
> `high-label:: Very confident`--}{++{"author":"Elias's AI","timestamp":1787223032488}@@id:: 4280d5f2-2cd5-48f9-b20f-fc132253d443
content:: How confident are you in your answer?

#### Text
content::++}
{--{"author":"Elias's AI","timestamp":1787223032488}@@>--}{++{"author":"Elias's AI","timestamp":1787223032488}@@Optional fields:

-++} `required:: {--{"author":"Elias's AI","timestamp":1787223032488}@@true`

Options:

--}{++{"author":"Elias's AI","timestamp":1787223032488}@@true`: require response. Defaults to `false`.
++}- {--{"author":"Elias's AI","timestamp":1787223032488}@@`scale::`: integer--}{++{"author":"Elias's AI","timestamp":1787223032488}@@`scale:: 7`: set highest number++} from 2 to 10. Defaults to {--{"author":"Elias's AI","timestamp":1787223032488}@@5.--}{++{"author":"Elias's AI","timestamp":1787223032488}@@`5`.++}
- {--{"author":"Elias's AI","timestamp":1787223032488}@@`low-label::`: optional--}{++{"author":"Elias's AI","timestamp":1787223032488}@@`low-label:: Not confident`:++} label{--{"author":"Elias's AI","timestamp":1787223032488}@@ below--} low endpoint.{++{"author":"Elias's AI","timestamp":1787223032488}@@ Defaults to no label.++}
- {--{"author":"Elias's AI","timestamp":1787223032488}@@`high-label::`: optional--}{++{"author":"Elias's AI","timestamp":1787223032488}@@`high-label:: Very confident`:++} label {--{"author":"Elias's AI","timestamp":1787223032488}@@below --}high endpoint.{++{"author":"Elias's AI","timestamp":1787223032488}@@ Defaults to no label.++}

Ratings are self-reports, not correct or incorrect. In Learning Outcome tests, rating is stored beside graded answers but does not affect test score.

\## Single select

Use `#### Select` with {--{"author":"Elias's AI","timestamp":1787223049523}@@plain list under `options::`. Default allows one selection.--}{++{"author":"Elias's AI","timestamp":1787223049523}@@`options::`. With no `[x]`, response is ungraded.++}

{--{"author":"Elias's AI","timestamp":1787223049523}@@Ungraded example:--}{++{"author":"Elias's AI","timestamp":1787223049523}@@Smallest version:++}

> `#### Select`
> `id:: {--{"author":"Elias's AI","timestamp":1787223049523}@@f32db9ca-cdf4-4c4d-b53c-50f3456dcac1`--}{++{"author":"Elias's AI","timestamp":1787223049523}@@<uuid>`++}
> `content:: Which topic should we cover next?`
> `options::`
> `- Forecasting`
> `- Governance`{--{"author":"Elias's AI","timestamp":1787223049523}@@
> `- Technical safety`--}{++{"author":"Elias's AI","timestamp":1787223049523}@@

Try it:

#### Select
id:: a59ce650-c5cf-4b2b-bc13-e0686f5d2bfb++}
{--{"author":"Elias's AI","timestamp":1787223049523}@@> `required:: true`

For graded practice or test response, mark--}{++{"author":"Elias's AI","timestamp":1787223049523}@@content:: Which topic should we cover next?
options::
- Forecasting
- Governance

#### Text
content::
Mark++} correct option with {--{"author":"Elias's AI","timestamp":1787223049523}@@`[x]`:

> `#### Select`
> `id:: 234db237-6c5c-43f3-82aa-b19a4ee2708d`
> `content:: Which process updates model weights during training?`
--}{++{"author":"Elias's AI","timestamp":1787223049523}@@`[x]` when response should be graded:

++}> `options::`
> `- Data collection`
> `- [x] Gradient descent`
> `- Deployment monitoring`{--{"author":"Elias's AI","timestamp":1787223049523}@@
> `shuffle:: true`--}{++{"author":"Elias's AI","timestamp":1787223049523}@@

Optional fields:

- `required:: true`: require response. Defaults to `false`.++}
{--{"author":"Elias's AI","timestamp":1787223049523}@@> `explanation:: Gradient descent updates weights using gradients of loss.`

Options:

--}{++{"author":"Elias's AI","timestamp":1787223049523}@@- `multi:: true`: allow multiple selections. Defaults to `false`.
++}- `shuffle:: true`: randomize option order. Defaults to `false`.
- {--{"author":"Elias's AI","timestamp":1787223049523}@@`explanation::`: optional feedback shown--}{++{"author":"Elias's AI","timestamp":1787223049523}@@`explanation:: ...`: show fixed explanation++} after submission.{++{"author":"Elias's AI","timestamp":1787223049523}@@ Defaults to no explanation.++}

Survey selects must use plain list items. Surveys never contain correct-answer markers.

\## Multi-select

{--{"author":"Elias's AI","timestamp":1787223065654}@@Add `multi:: true` when learner may select more than one option.--}{++{"author":"Elias's AI","timestamp":1787223065654}@@Multi-select is same Response segment with one non-default field: `multi:: true`.

Smallest version:++}

> `#### Select`
> `id:: {--{"author":"Elias's AI","timestamp":1787223065654}@@69162105-5047-480e-9c38-f5c408c535a7`--}{++{"author":"Elias's AI","timestamp":1787223065654}@@<uuid>`++}
> `content:: Which {--{"author":"Elias's AI","timestamp":1787223065654}@@two items are empirical evidence?`--}{++{"author":"Elias's AI","timestamp":1787223065654}@@topics interest you?`++}
> `options::`
> `-{--{"author":"Elias's AI","timestamp":1787223065654}@@ [x] A measured benchmark result`--}{++{"author":"Elias's AI","timestamp":1787223065654}@@ Forecasting`
> `- Governance`++}
> `- {--{"author":"Elias's AI","timestamp":1787223065654}@@A definition`--}{++{"author":"Elias's AI","timestamp":1787223065654}@@Technical safety`++}
> {--{"author":"Elias's AI","timestamp":1787223065654}@@`- [x] A randomized trial result`--}{++{"author":"Elias's AI","timestamp":1787223065654}@@`multi:: true`

Try it:

#### Select
id:: cb39e8f1-4477-4b66-b016-37c99c5ff753++}
{--{"author":"Elias's AI","timestamp":1787223065654}@@> `- A thought experiment`--}{++{"author":"Elias's AI","timestamp":1787223065654}@@content:: Which topics interest you?
options::++}
{--{"author":"Elias's AI","timestamp":1787223065654}@@> `multi:: true`--}{++{"author":"Elias's AI","timestamp":1787223065654}@@- Forecasting
- Governance++}
{--{"author":"Elias's AI","timestamp":1787223065654}@@> `shuffle:: true`--}{++{"author":"Elias's AI","timestamp":1787223065654}@@- Technical safety++}
{--{"author":"Elias's AI","timestamp":1787223065654}@@> `explanation:: Measurements and trial results are empirical evidence.`

A graded response is correct only when--}{++{"author":"Elias's AI","timestamp":1787223065654}@@multi:: true

#### Text
content::
It has same optional fields and defaults as single select. For graded multi-select, learner's++} selected options {++{"author":"Elias's AI","timestamp":1787223065654}@@must ++}exactly match {--{"author":"Elias's AI","timestamp":1787223065654}@@every--}{++{"author":"Elias's AI","timestamp":1787223065654}@@all++} `[x]` {--{"author":"Elias's AI","timestamp":1787223065654}@@option.--}{++{"author":"Elias's AI","timestamp":1787223065654}@@options.++} In surveys,{--{"author":"Elias's AI","timestamp":1787223065654}@@ `multi:: true` works the same way but--} options stay ungraded and use no `[x]` markers.

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
