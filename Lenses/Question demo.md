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

<pre><code>#### Select
key&#58;&#58; next_topic
content&#58;&#58; Which topic should we cover next?
options&#58;&#58;
- Forecasting
- Governance
- Technical safety
required&#58;&#58; true</code></pre>

For graded practice or test response, mark correct option with `[x]`:

<pre><code>#### Select
key&#58;&#58; optimizer
content&#58;&#58; Which process updates model weights during training?
options&#58;&#58;
- Data collection
- [x] Gradient descent
- Deployment monitoring
shuffle&#58;&#58; true
explanation&#58;&#58; Gradient descent updates weights using gradients of loss.</code></pre>

Options:

- `shuffle:: true`: randomize option order. Defaults to `false`.
- `explanation&#58;&#58;`: optional feedback shown after submission.

Survey selects must use plain list items. Surveys never contain correct-answer markers.

\## Multi-select

Add `multi:: true` when learner may select more than one option.

<pre><code>#### Select
key&#58;&#58; empirical_evidence
content&#58;&#58; Which two items are empirical evidence?
options&#58;&#58;
- [x] A measured benchmark result
- A definition
- [x] A randomized trial result
- A thought experiment
multi&#58;&#58; true
shuffle&#58;&#58; true
explanation&#58;&#58; Measurements and trial results are empirical evidence.</code></pre>

A graded response is correct only when selected options exactly match every `[x]` option. In surveys, `multi:: true` works the same way but options stay ungraded and use no `[x]` markers.

\## Fill in the blank

Use `#### FillBlank`. Put exactly one `{{blank}}` marker in prompt.

<pre><code>#### FillBlank
key&#58;&#58; training_method
content&#58;&#58; Model weights are commonly updated using {{blank}}.
accepted-answers&#58;&#58;
- gradient descent
- gradient-based optimization
case-sensitive&#58;&#58; false
trim&#58;&#58; true
explanation&#58;&#58; Gradient descent uses loss gradients to update model weights.
required&#58;&#58; true</code></pre>

Options:

- `accepted-answers::`: one or more complete accepted answers.
- `case-sensitive::`: defaults to `false`.
- `trim::`: ignore leading and trailing whitespace. Defaults to `true`.
- `explanation&#58;&#58;`: optional feedback shown after submission.

Matching is exact after configured case and whitespace normalization. Use several FillBlank segments when exercise needs several blanks.

Surveys may use FillBlank without `accepted-answers::` or `explanation::`. That makes it an ungraded short-answer field.

\## Grading rules

- **Survey:** all Response segment types are ungraded.
- **Normal lens:** responses may be graded practice or ungraded reflection.
- **Learning Outcome test:** OpenResponse, Select, and FillBlank must be gradable. OpenResponse needs `assessment-instructions::`; Select needs at least one `[x]`; FillBlank needs `accepted-answers::`.
- Rating never contributes to correctness score.

Validator should reject duplicate keys, invalid field combinations, missing grading information in tests, invalid rating scales, too few select options, and missing or multiple `{{blank}}` markers.
