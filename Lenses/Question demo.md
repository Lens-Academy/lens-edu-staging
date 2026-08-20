---
id: 8189763f-576e-4f04-a614-4a00c628e386
{++{"author":"Elias's AI","timestamp":1787220298389}@@title: Question types
++}tldr: {--{"author":"Elias's AI","timestamp":1787220298389}@@"A demo of --}{++{"author":"Elias's AI","timestamp":1787220298389}@@Use open-text, rating, choice, and fill-in-the-blank questions with ++}the {--{"author":"Elias's AI","timestamp":1787220298389}@@Question segment.--}{++{"author":"Elias's AI","timestamp":1787220298389}@@same syntax in surveys, normal lenses, and learning-outcome tests.
summary_for_tutor: Reference page for course creators.++} It {--{"author":"Elias's AI","timestamp":1787220298389}@@asks you to explain what questions are for, then--}{++{"author":"Elias's AI","timestamp":1787220298389}@@documents the shared fields, exact syntax, type-specific options, defaults, and grading behavior for Question, Rating, Choice, and FillBlank segments.
---

#### Text
content::
\## Questions work in three places

Use question segments in:

- **Surveys**++} to {--{"author":"Elias's AI","timestamp":1787220298389}@@plan how you'd vet one--}{++{"author":"Elias's AI","timestamp":1787220298389}@@collect ungraded responses.
- **Normal lenses**++} for {--{"author":"Elias's AI","timestamp":1787220298389}@@a real course, showing--}{++{"author":"Elias's AI","timestamp":1787220298389}@@practice, reflection, and checks for understanding.
- **Learning Outcome tests** for graded assessment.

Syntax is identical in all three places. Context changes whether an answer is graded, not++} how {--{"author":"Elias's AI","timestamp":1787220298389}@@learner answers get collected and assessed --}{++{"author":"Elias's AI","timestamp":1787220298389}@@the question is written.

Every answerable segment needs:

- `key&#58;&#58;`: stable `snake_case` identifier, unique within that survey, lens, or test.
- `content&#58;&#58;`: prompt shown to learner.
- `required&#58;&#58; true`: optional. Questions are not required ++}by {--{"author":"Elias's AI","timestamp":1787220298389}@@the AI tutor, including a voice-answer variant."
summary_for_tutor: "Demonstrates the Question segment. Opens with--}{++{"author":"Elias's AI","timestamp":1787220298389}@@default.

Never change `key&#58;&#58;` after learners have answered. Stored answers use this key.

\## Open-text question

Use `#### Question` when learner should type or dictate++} a {--{"author":"Elias's AI","timestamp":1787220298389}@@Text note, then--}{++{"author":"Elias's AI","timestamp":1787220298389}@@response.

```md
\#### Question
key&#58;&#58; strongest_objection
content&#58;&#58; In++} two {--{"author":"Elias's AI","timestamp":1787220298389}@@Question segments. The first asks --}{++{"author":"Elias's AI","timestamp":1787220298389}@@sentences, what is the strongest objection?
required&#58;&#58; true
max-chars&#58;&#58; 500
placeholder&#58;&#58; Name ++}the {--{"author":"Elias's AI","timestamp":1787220298389}@@learner to--}{++{"author":"Elias's AI","timestamp":1787220298389}@@claim, then++} explain {--{"author":"Elias's AI","timestamp":1787220298389}@@in one or two sentences what--}{++{"author":"Elias's AI","timestamp":1787220298389}@@objection.
max-time&#58;&#58; 3:00
enforce-voice&#58;&#58; false
assessment-instructions&#58;&#58; Check whether learner names++} a {--{"author":"Elias's AI","timestamp":1787220298389}@@Question segment is useful for (assessed --}{++{"author":"Elias's AI","timestamp":1787220298389}@@claim and gives a relevant objection.
feedback&#58;&#58; true
```

Options:

- `max-chars&#58;&#58;`: maximum answer length.
- `placeholder&#58;&#58;`: hint shown in empty input.
- `max-time&#58;&#58;`: answer timer in `M:SS`, or `none`.
- `enforce-voice&#58;&#58; true`: require spoken answer.
- `assessment-instructions&#58;&#58;`: rubric ++}for {--{"author":"Elias's AI","timestamp":1787220298389}@@noting that questions collect--}{++{"author":"Elias's AI","timestamp":1787220298389}@@AI assessment.
- `feedback&#58;&#58;`: whether++} learner {--{"author":"Elias's AI","timestamp":1787220298389}@@responses the --}{++{"author":"Elias's AI","timestamp":1787220298389}@@receives ++}AI {--{"author":"Elias's AI","timestamp":1787220298389}@@tutor can assess; 500-character limit). The second asks what they would check before using a question in a real course (assessed--}{++{"author":"Elias's AI","timestamp":1787220298389}@@feedback. Defaults to `true` in lenses and tests.

Surveys do not use `assessment-instructions&#58;&#58;` or `feedback&#58;&#58;`. They store response without grading it.

\## Rating

Use `#### Rating`++} for {--{"author":"Elias's AI","timestamp":1787220298389}@@a concrete testing plan such as wording, character limit, rubric, and feedback quality; voice answering enforced)."--}{++{"author":"Elias's AI","timestamp":1787220298389}@@numbered scale from 1 to N.

```md
\#### Rating
key&#58;&#58; confidence
content&#58;&#58; How confident are you in your answer?
scale&#58;&#58; 7++}
{--{"author":"Elias's AI","timestamp":1787220298389}@@title: Question demo--}{++{"author":"Elias's AI","timestamp":1787220298389}@@low-label&#58;&#58; Not confident
high-label&#58;&#58; Very confident
required&#58;&#58; true++}
{--{"author":"Elias's AI","timestamp":1787220298389}@@-----}{++{"author":"Elias's AI","timestamp":1787220298389}@@```

Options:++}

{--{"author":"Elias's AI","timestamp":1787220298389}@@#### Text--}{++{"author":"Elias's AI","timestamp":1787220298389}@@- `scale&#58;&#58;`: integer from 2 to 10. Defaults to 5.++}
{--{"author":"Elias's AI","timestamp":1787220298389}@@content::--}{++{"author":"Elias's AI","timestamp":1787220298389}@@- `low-label&#58;&#58;`: optional label below low endpoint.++}
{--{"author":"Elias's AI","timestamp":1787220298389}@@This lens demonstrates `#### Question` segments.--}{++{"author":"Elias's AI","timestamp":1787220298389}@@- `high-label&#58;&#58;`: optional label below high endpoint.++}

{--{"author":"Elias's AI","timestamp":1787220298389}@@#### Question
content:: --}{++{"author":"Elias's AI","timestamp":1787220298389}@@Ratings are self-reports, not correct or incorrect. ++}In {++{"author":"Elias's AI","timestamp":1787220298389}@@Learning Outcome tests, rating is stored beside graded answers but does not affect test score.

\## Single-choice question

Use `#### Choice` with plain list under `options&#58;&#58;`. Default allows ++}one {--{"author":"Elias's AI","timestamp":1787220298389}@@or two sentences, explain what a `#### Question` segment is useful for.--}{++{"author":"Elias's AI","timestamp":1787220298389}@@selection.

Ungraded example:

```md
\#### Choice
key&#58;&#58; next_topic
content&#58;&#58; Which topic should we cover next?
options&#58;&#58;
- Forecasting
- Governance
- Technical safety
required&#58;&#58; true++}
{--{"author":"Elias's AI","timestamp":1787220298389}@@assessment-instructions:: Look for a concise answer that says questions collect learner responses and can be assessed by the AI tutor.--}{++{"author":"Elias's AI","timestamp":1787220298389}@@```

For graded practice or test question, mark correct option with `[x]`:

```md
\#### Choice
key&#58;&#58; optimizer
content&#58;&#58; Which process updates model weights during training?
options&#58;&#58;
- Data collection
- [x] Gradient descent
- Deployment monitoring
shuffle&#58;&#58; true++}
{--{"author":"Elias's AI","timestamp":1787220298389}@@max-chars:: 500--}{++{"author":"Elias's AI","timestamp":1787220298389}@@explanation&#58;&#58; Gradient descent updates weights using gradients of loss.
```

Options:++}

{--{"author":"Elias's AI","timestamp":1787220298389}@@%% `feedback:: true` means the learner gets AI--}{++{"author":"Elias's AI","timestamp":1787220298389}@@- `shuffle&#58;&#58; true`: randomize option order. Defaults to `false`.
- `explanation&#58;&#58;`: optional++} feedback {++{"author":"Elias's AI","timestamp":1787220298389}@@shown ++}after {--{"author":"Elias's AI","timestamp":1787220298389}@@answering. `max-chars::` sets a character limit. %%--}{++{"author":"Elias's AI","timestamp":1787220298389}@@submission.

Survey choices must use plain list items. Surveys never contain correct-answer markers.

\## Multiple-choice question

Add `multi&#58;&#58; true` when learner may select more than one option.++}

{--{"author":"Elias's AI","timestamp":1787220298389}@@#### Question--}{++{"author":"Elias's AI","timestamp":1787220298389}@@```md
\#### Choice++}
{--{"author":"Elias's AI","timestamp":1787220298389}@@content:: Try answering this one by voice. What would you check before using a question in a real course?--}{++{"author":"Elias's AI","timestamp":1787220298389}@@key&#58;&#58; empirical_evidence
content&#58;&#58; Which two items are empirical evidence?
options&#58;&#58;
- [x] A measured benchmark result
- A definition
- [x] A randomized trial result
- A thought experiment
multi&#58;&#58; true
shuffle&#58;&#58; true
explanation&#58;&#58; Measurements and trial results are empirical evidence.++}
{--{"author":"Elias's AI","timestamp":1787220298389}@@assessment-instructions:: Look for a concrete testing plan, such as checking --}{++{"author":"Elias's AI","timestamp":1787220298389}@@```

A graded response is correct only when selected options exactly match every `[x]` option. In surveys, `multi&#58;&#58; true` works ++}the {--{"author":"Elias's AI","timestamp":1787220298389}@@wording, character limit, scoring rubric, --}{++{"author":"Elias's AI","timestamp":1787220298389}@@same way but options stay ungraded ++}and {--{"author":"Elias's AI","timestamp":1787220298389}@@feedback quality.--}{++{"author":"Elias's AI","timestamp":1787220298389}@@use no `[x]` markers.

\## Fill in the blank

Use `#### FillBlank`. Put exactly one `{{blank}}` marker in prompt.

```md
\#### FillBlank
key&#58;&#58; training_method++}
{--{"author":"Elias's AI","timestamp":1787220298389}@@enforce-voice:: --}{++{"author":"Elias's AI","timestamp":1787220298389}@@content&#58;&#58; Model weights are commonly updated using {{blank}}.
accepted-answers&#58;&#58;
- gradient descent
- gradient-based optimization
case-sensitive&#58;&#58; false
trim&#58;&#58; ++}true{++{"author":"Elias's AI","timestamp":1787220298389}@@
explanation&#58;&#58; Gradient descent uses loss gradients to update model weights.
required&#58;&#58; true
```

Options:++}

{--{"author":"Elias's AI","timestamp":1787220298389}@@%% `enforce-voice:: true` requires the learner--}{++{"author":"Elias's AI","timestamp":1787220298389}@@- `accepted-answers&#58;&#58;`: one or more complete accepted answers.
- `case-sensitive&#58;&#58;`: defaults++} to {--{"author":"Elias's AI","timestamp":1787220298389}@@answer by speaking instead of typing. 15 june 2026: probably not implemented though. Problem--}{++{"author":"Elias's AI","timestamp":1787220298389}@@`false`.
- `trim&#58;&#58;`: ignore leading and trailing whitespace. Defaults to `true`.
- `explanation&#58;&#58;`: optional feedback shown after submission.

Matching++} is {--{"author":"Elias's AI","timestamp":1787220298389}@@that people can't always speak in every situation, so it'd need some override anyway. Should still make a strong nudge--}{++{"author":"Elias's AI","timestamp":1787220298389}@@exact after configured case and whitespace normalization. Use several FillBlank segments when exercise needs several blanks.

Surveys may use FillBlank without `accepted-answers&#58;&#58;`++} or {--{"author":"Elias's AI","timestamp":1787220298389}@@so?%%--}{++{"author":"Elias's AI","timestamp":1787220298389}@@`explanation&#58;&#58;`. That makes it an ungraded short-answer field.

\## Grading rules

- **Survey:** all question types are ungraded.
- **Normal lens:** questions may be graded practice or ungraded reflection.
- **Learning Outcome test:** Question, Choice, and FillBlank must be gradable. Question needs `assessment-instructions&#58;&#58;`; Choice needs at least one `[x]`; FillBlank needs `accepted-answers&#58;&#58;`.
- Rating never contributes to correctness score.

Validator should reject duplicate keys, invalid field combinations, missing grading information in tests, invalid rating scales, too few choice options, and missing or multiple `{{blank}}` markers.++}
