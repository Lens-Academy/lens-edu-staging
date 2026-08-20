---
id: 8189763f-576e-4f04-a614-4a00c628e386
title: Response segments
tldr: Use open responses, ratings, selects, and fill-in-the-blank responses with the same syntax in surveys, normal lenses, and learning-outcome tests.
summary_for_tutor: Reference page for course creators. It documents shared fields, exact syntax, options, defaults, and grading behavior for OpenResponse, Rating, Select, and FillBlank Response segments.
---

#### Text
content::
\## Response segments work in three places

Use Response segments in:

- **Surveys** to collect ungraded responses.
- **Normal lenses** for practice, reflection, and checks for understanding.
- **Learning Outcome tests** for graded assessment.

Syntax is identical in all three places. Context changes whether a response is graded, not how segment is written.

Every answerable segment needs:

- `key::`: stable `snake_case` identifier, unique within that survey, lens, or test.
- `content::`: prompt shown to learner.
- `required:: true`: optional. Response segments are not required by default.

Never change `key::` after learners have answered. Stored answers use this key.

\## Open response

Use `#### OpenResponse` when learner should type or dictate a response.

> `#### OpenResponse`
> `key:: strongest_objection`
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

{--{"author":"Elias's AI","timestamp":1787221225646}@@<pre><code>#### Rating--}{++{"author":"Elias's AI","timestamp":1787221225646}@@> `#### Rating`++}
{--{"author":"Elias's AI","timestamp":1787221225646}@@key&#58;&#58; confidence--}{++{"author":"Elias's AI","timestamp":1787221225646}@@> `key:: confidence`++}
{--{"author":"Elias's AI","timestamp":1787221225646}@@content&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221225646}@@> `content::++} How confident are you in your {--{"author":"Elias's AI","timestamp":1787221225646}@@answer?--}{++{"author":"Elias's AI","timestamp":1787221225646}@@answer?`++}
{--{"author":"Elias's AI","timestamp":1787221225646}@@scale&#58;&#58; 7--}{++{"author":"Elias's AI","timestamp":1787221225646}@@> `scale:: 7`++}
{--{"author":"Elias's AI","timestamp":1787221225646}@@low-label&#58;&#58; --}{++{"author":"Elias's AI","timestamp":1787221225646}@@> `low-label:: ++}Not {--{"author":"Elias's AI","timestamp":1787221225646}@@confident--}{++{"author":"Elias's AI","timestamp":1787221225646}@@confident`++}
{--{"author":"Elias's AI","timestamp":1787221225646}@@high-label&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221225646}@@> `high-label::++} Very {--{"author":"Elias's AI","timestamp":1787221225646}@@confident--}{++{"author":"Elias's AI","timestamp":1787221225646}@@confident`++}
{--{"author":"Elias's AI","timestamp":1787221225646}@@required&#58;&#58; true</code></pre>--}{++{"author":"Elias's AI","timestamp":1787221225646}@@> `required:: true`++}

Options:

- `scale::`: integer from 2 to 10. Defaults to 5.
- `low-label::`: optional label below low endpoint.
- `high-label::`: optional label below high endpoint.

Ratings are self-reports, not correct or incorrect. In Learning Outcome tests, rating is stored beside graded answers but does not affect test score.

\## Single select

Use `#### Select` with plain list under `options::`. Default allows one selection.

Ungraded example:

{--{"author":"Elias's AI","timestamp":1787221228251}@@<pre><code>#### Select--}{++{"author":"Elias's AI","timestamp":1787221228251}@@> `#### Select`++}
{--{"author":"Elias's AI","timestamp":1787221228251}@@key&#58;&#58; next_topic--}{++{"author":"Elias's AI","timestamp":1787221228251}@@> `key:: next_topic`++}
{--{"author":"Elias's AI","timestamp":1787221228251}@@content&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221228251}@@> `content::++} Which topic should we cover {--{"author":"Elias's AI","timestamp":1787221228251}@@next?--}{++{"author":"Elias's AI","timestamp":1787221228251}@@next?`++}
{--{"author":"Elias's AI","timestamp":1787221228251}@@options&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221228251}@@> `options::`++}
{--{"author":"Elias's AI","timestamp":1787221228251}@@- Forecasting--}{++{"author":"Elias's AI","timestamp":1787221228251}@@> `- Forecasting`++}
{--{"author":"Elias's AI","timestamp":1787221228251}@@- Governance--}{++{"author":"Elias's AI","timestamp":1787221228251}@@> `- Governance`++}
{--{"author":"Elias's AI","timestamp":1787221228251}@@---}{++{"author":"Elias's AI","timestamp":1787221228251}@@> `-++} Technical {--{"author":"Elias's AI","timestamp":1787221228251}@@safety--}{++{"author":"Elias's AI","timestamp":1787221228251}@@safety`++}
{--{"author":"Elias's AI","timestamp":1787221228251}@@required&#58;&#58; true</code></pre>--}{++{"author":"Elias's AI","timestamp":1787221228251}@@> `required:: true`++}

For graded practice or test response, mark correct option with `[x]`:

{--{"author":"Elias's AI","timestamp":1787221231116}@@<pre><code>#### Select--}{++{"author":"Elias's AI","timestamp":1787221231116}@@> `#### Select`++}
{--{"author":"Elias's AI","timestamp":1787221231116}@@key&#58;&#58; optimizer--}{++{"author":"Elias's AI","timestamp":1787221231116}@@> `key:: optimizer`++}
{--{"author":"Elias's AI","timestamp":1787221231116}@@content&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221231116}@@> `content::++} Which process updates model weights during {--{"author":"Elias's AI","timestamp":1787221231116}@@training?--}{++{"author":"Elias's AI","timestamp":1787221231116}@@training?`++}
{--{"author":"Elias's AI","timestamp":1787221231116}@@options&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221231116}@@> `options::`++}
{--{"author":"Elias's AI","timestamp":1787221231116}@@---}{++{"author":"Elias's AI","timestamp":1787221231116}@@> `-++} Data {--{"author":"Elias's AI","timestamp":1787221231116}@@collection--}{++{"author":"Elias's AI","timestamp":1787221231116}@@collection`++}
{--{"author":"Elias's AI","timestamp":1787221231116}@@---}{++{"author":"Elias's AI","timestamp":1787221231116}@@> `-++} [x] Gradient {--{"author":"Elias's AI","timestamp":1787221231116}@@descent--}{++{"author":"Elias's AI","timestamp":1787221231116}@@descent`++}
{--{"author":"Elias's AI","timestamp":1787221231116}@@---}{++{"author":"Elias's AI","timestamp":1787221231116}@@> `-++} Deployment {--{"author":"Elias's AI","timestamp":1787221231116}@@monitoring--}{++{"author":"Elias's AI","timestamp":1787221231116}@@monitoring`++}
{--{"author":"Elias's AI","timestamp":1787221231116}@@shuffle&#58;&#58; true--}{++{"author":"Elias's AI","timestamp":1787221231116}@@> `shuffle:: true`++}
{--{"author":"Elias's AI","timestamp":1787221231116}@@explanation&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221231116}@@> `explanation::++} Gradient descent updates weights using gradients of {--{"author":"Elias's AI","timestamp":1787221231116}@@loss.</code></pre>--}{++{"author":"Elias's AI","timestamp":1787221231116}@@loss.`++}

Options:

- `shuffle:: true`: randomize option order. Defaults to `false`.
- {--{"author":"Elias's AI","timestamp":1787221248524}@@`explanation&#58;&#58;`:--}{++{"author":"Elias's AI","timestamp":1787221248524}@@`explanation::`:++} optional feedback shown after submission.

Survey selects must use plain list items. Surveys never contain correct-answer markers.

\## Multi-select

Add `multi:: true` when learner may select more than one option.

{--{"author":"Elias's AI","timestamp":1787221234028}@@<pre><code>#### Select--}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `#### Select`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@key&#58;&#58; empirical_evidence--}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `key:: empirical_evidence`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@content&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `content::++} Which two items are empirical {--{"author":"Elias's AI","timestamp":1787221234028}@@evidence?--}{++{"author":"Elias's AI","timestamp":1787221234028}@@evidence?`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@options&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `options::`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@---}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `-++} [x] A measured benchmark {--{"author":"Elias's AI","timestamp":1787221234028}@@result--}{++{"author":"Elias's AI","timestamp":1787221234028}@@result`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@---}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `-++} A {--{"author":"Elias's AI","timestamp":1787221234028}@@definition--}{++{"author":"Elias's AI","timestamp":1787221234028}@@definition`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@---}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `-++} [x] A randomized trial {--{"author":"Elias's AI","timestamp":1787221234028}@@result--}{++{"author":"Elias's AI","timestamp":1787221234028}@@result`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@---}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `-++} A thought {--{"author":"Elias's AI","timestamp":1787221234028}@@experiment--}{++{"author":"Elias's AI","timestamp":1787221234028}@@experiment`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@multi&#58;&#58; true--}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `multi:: true`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@shuffle&#58;&#58; true--}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `shuffle:: true`++}
{--{"author":"Elias's AI","timestamp":1787221234028}@@explanation&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221234028}@@> `explanation::++} Measurements and trial results are empirical {--{"author":"Elias's AI","timestamp":1787221234028}@@evidence.</code></pre>--}{++{"author":"Elias's AI","timestamp":1787221234028}@@evidence.`++}

A graded response is correct only when selected options exactly match every `[x]` option. In surveys, `multi:: true` works the same way but options stay ungraded and use no `[x]` markers.

\## Fill in the blank

Use `#### FillBlank`. Put exactly one `{{blank}}` marker in prompt.

{--{"author":"Elias's AI","timestamp":1787221236670}@@<pre><code>#### FillBlank--}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `#### FillBlank`++}
{--{"author":"Elias's AI","timestamp":1787221236670}@@key&#58;&#58; training_method--}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `key:: training_method`++}
{--{"author":"Elias's AI","timestamp":1787221236670}@@content&#58;&#58; --}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `content:: ++}Model weights are commonly updated using {--{"author":"Elias's AI","timestamp":1787221236670}@@{{blank}}.--}{++{"author":"Elias's AI","timestamp":1787221236670}@@{{blank}}.`++}
{--{"author":"Elias's AI","timestamp":1787221236670}@@accepted-answers&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `accepted-answers::`++}
{--{"author":"Elias's AI","timestamp":1787221236670}@@---}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `-++} gradient {--{"author":"Elias's AI","timestamp":1787221236670}@@descent--}{++{"author":"Elias's AI","timestamp":1787221236670}@@descent`++}
{--{"author":"Elias's AI","timestamp":1787221236670}@@---}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `-++} gradient-based {--{"author":"Elias's AI","timestamp":1787221236670}@@optimization--}{++{"author":"Elias's AI","timestamp":1787221236670}@@optimization`++}
{--{"author":"Elias's AI","timestamp":1787221236670}@@case-sensitive&#58;&#58; false--}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `case-sensitive:: false`++}
{--{"author":"Elias's AI","timestamp":1787221236670}@@trim&#58;&#58; true--}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `trim:: true`++}
{--{"author":"Elias's AI","timestamp":1787221236670}@@explanation&#58;&#58;--}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `explanation::++} Gradient descent uses loss gradients to update model {--{"author":"Elias's AI","timestamp":1787221236670}@@weights.--}{++{"author":"Elias's AI","timestamp":1787221236670}@@weights.`++}
{--{"author":"Elias's AI","timestamp":1787221236670}@@required&#58;&#58; true</code></pre>--}{++{"author":"Elias's AI","timestamp":1787221236670}@@> `required:: true`++}

Options:

- `accepted-answers::`: one or more complete accepted answers.
- `case-sensitive::`: defaults to `false`.
- `trim::`: ignore leading and trailing whitespace. Defaults to `true`.
- {--{"author":"Elias's AI","timestamp":1787221252335}@@`explanation&#58;&#58;`:--}{++{"author":"Elias's AI","timestamp":1787221252335}@@`explanation::`:++} optional feedback shown after submission.

Matching is exact after configured case and whitespace normalization. Use several FillBlank segments when exercise needs several blanks.

Surveys may use FillBlank without `accepted-answers::` or `explanation::`. That makes it an ungraded short-answer field.

\## Grading rules

- **Survey:** all Response segment types are ungraded.
- **Normal lens:** responses may be graded practice or ungraded reflection.
- **Learning Outcome test:** OpenResponse, Select, and FillBlank must be gradable. OpenResponse needs `assessment-instructions::`; Select needs at least one `[x]`; FillBlank needs `accepted-answers::`.
- Rating never contributes to correctness score.

Validator should reject duplicate keys, invalid field combinations, missing grading information in tests, invalid rating scales, too few select options, and missing or multiple `{{blank}}` markers.
