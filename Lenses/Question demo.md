---
id: 8189763f-576e-4f04-a614-4a00c628e386
title: {--{"author":"Elias's AI","timestamp":1787221121301}@@Question types--}{++{"author":"Elias's AI","timestamp":1787221121301}@@Response segments++}
tldr: Use {--{"author":"Elias's AI","timestamp":1787221124438}@@open-text, rating, choice,--}{++{"author":"Elias's AI","timestamp":1787221124438}@@open responses, ratings, selects,++} and fill-in-the-blank {--{"author":"Elias's AI","timestamp":1787221124438}@@questions--}{++{"author":"Elias's AI","timestamp":1787221124438}@@responses++} with the same syntax in surveys, normal lenses, and learning-outcome tests.
summary_for_tutor: Reference page for course creators. It documents {--{"author":"Elias's AI","timestamp":1787221126904}@@the --}shared fields, exact syntax, {--{"author":"Elias's AI","timestamp":1787221126904}@@type-specific --}options, defaults, and grading behavior for {--{"author":"Elias's AI","timestamp":1787221126904}@@Question,--}{++{"author":"Elias's AI","timestamp":1787221126904}@@OpenResponse,++} Rating, {--{"author":"Elias's AI","timestamp":1787221126904}@@Choice,--}{++{"author":"Elias's AI","timestamp":1787221126904}@@Select,++} and FillBlank {++{"author":"Elias's AI","timestamp":1787221126904}@@Response ++}segments.
---

#### Text
content::
\## {--{"author":"Elias's AI","timestamp":1787221130222}@@Questions--}{++{"author":"Elias's AI","timestamp":1787221130222}@@Response segments++} work in three places

Use {--{"author":"Elias's AI","timestamp":1787221133420}@@question--}{++{"author":"Elias's AI","timestamp":1787221133420}@@Response++} segments in:

- **Surveys** to collect ungraded responses.
- **Normal lenses** for practice, reflection, and checks for understanding.
- **Learning Outcome tests** for graded assessment.

Syntax is identical in all three places. Context changes whether {--{"author":"Elias's AI","timestamp":1787221136259}@@an answer--}{++{"author":"Elias's AI","timestamp":1787221136259}@@a response++} is graded, not how {--{"author":"Elias's AI","timestamp":1787221136259}@@the question--}{++{"author":"Elias's AI","timestamp":1787221136259}@@segment++} is written.

Every answerable segment needs:

- `key::`: stable `snake_case` identifier, unique within that survey, lens, or test.
- `content::`: prompt shown to learner.
- `required:: true`: optional. {--{"author":"Elias's AI","timestamp":1787221141225}@@Questions--}{++{"author":"Elias's AI","timestamp":1787221141225}@@Response segments++} are not required by default.

Never change `key::` after learners have answered. Stored answers use this key.

\## {--{"author":"Elias's AI","timestamp":1787221145780}@@Open-text question--}{++{"author":"Elias's AI","timestamp":1787221145780}@@Open response++}

Use `#### {--{"author":"Elias's AI","timestamp":1787221148299}@@Question`--}{++{"author":"Elias's AI","timestamp":1787221148299}@@OpenResponse`++} when learner should type or dictate a response.

<pre><code>#### {--{"author":"Elias's AI","timestamp":1787221152287}@@Question--}{++{"author":"Elias's AI","timestamp":1787221152287}@@OpenResponse++}
key&#58;&#58; strongest_objection
content&#58;&#58; In two sentences, what is the strongest objection?
required&#58;&#58; true
max-chars&#58;&#58; 500
placeholder&#58;&#58; Name the claim, then explain objection.
max-time&#58;&#58; 3:00
enforce-voice&#58;&#58; false
assessment-instructions&#58;&#58; Check whether learner names a claim and gives a relevant objection.
feedback&#58;&#58; true</code></pre>

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

<pre><code>#### Rating
key&#58;&#58; confidence
content&#58;&#58; How confident are you in your answer?
scale&#58;&#58; 7
low-label&#58;&#58; Not confident
high-label&#58;&#58; Very confident
required&#58;&#58; true</code></pre>

Options:

- `scale::`: integer from 2 to 10. Defaults to 5.
- `low-label::`: optional label below low endpoint.
- `high-label::`: optional label below high endpoint.

Ratings are self-reports, not correct or incorrect. In Learning Outcome tests, rating is stored beside graded answers but does not affect test score.

\## {--{"author":"Elias's AI","timestamp":1787221155458}@@Single-choice question--}{++{"author":"Elias's AI","timestamp":1787221155458}@@Single select++}

Use `#### {--{"author":"Elias's AI","timestamp":1787221157837}@@Choice`--}{++{"author":"Elias's AI","timestamp":1787221157837}@@Select`++} with plain list under `options::`. Default allows one selection.

Ungraded example:

<pre><code>#### {--{"author":"Elias's AI","timestamp":1787221162193}@@Choice--}{++{"author":"Elias's AI","timestamp":1787221162193}@@Select++}
key&#58;&#58; next_topic
content&#58;&#58; Which topic should we cover next?
options&#58;&#58;
- Forecasting
- Governance
- Technical safety
required&#58;&#58; true</code></pre>

For graded practice or test {--{"author":"Elias's AI","timestamp":1787221164979}@@question,--}{++{"author":"Elias's AI","timestamp":1787221164979}@@response,++} mark correct option with `[x]`:

<pre><code>#### {--{"author":"Elias's AI","timestamp":1787221169028}@@Choice--}{++{"author":"Elias's AI","timestamp":1787221169028}@@Select++}
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

Survey {--{"author":"Elias's AI","timestamp":1787221171904}@@choices--}{++{"author":"Elias's AI","timestamp":1787221171904}@@selects++} must use plain list items. Surveys never contain correct-answer markers.

\## {--{"author":"Elias's AI","timestamp":1787221174372}@@Multiple-choice question--}{++{"author":"Elias's AI","timestamp":1787221174372}@@Multi-select++}

Add `multi:: true` when learner may select more than one option.

<pre><code>#### {--{"author":"Elias's AI","timestamp":1787221177180}@@Choice--}{++{"author":"Elias's AI","timestamp":1787221177180}@@Select++}
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

- **Survey:** all {--{"author":"Elias's AI","timestamp":1787221183165}@@question--}{++{"author":"Elias's AI","timestamp":1787221183165}@@Response segment++} types are ungraded.
- **Normal lens:** questions may be graded practice or ungraded reflection.
- **Learning Outcome test:** Question, Choice, and FillBlank must be gradable. Question needs `assessment-instructions::`; Choice needs at least one `[x]`; FillBlank needs `accepted-answers::`.
- Rating never contributes to correctness score.

Validator should reject duplicate keys, invalid field combinations, missing grading information in tests, invalid rating scales, too few choice options, and missing or multiple `{{blank}}` markers.
