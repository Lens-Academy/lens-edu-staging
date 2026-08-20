---
id: 8189763f-576e-4f04-a614-4a00c628e386
duration_minutes: 15
title: Response segments
tldr: Use open responses, ratings, selects, and typed fill-in-the-blank responses with the same syntax in surveys, normal lenses, and learning-outcome tests.
summary_for_tutor: Reference page for course creators. It documents shared fields, exact syntax, options, defaults, and grading behavior for OpenResponse, Rating, Select, and typed FillBlank Response segments.
---

{--{"author":"Elias's AI","timestamp":1787253784301}@@#### Text
content::
\## Response segments work in three places

--}{++{"author":"Elias's AI","timestamp":1787253784301}@@%% ++}A Response segment is an interactive field that collects one learner{--{"author":"Elias's AI","timestamp":1787253784301}@@ response, such as written text, a rating, a selection, or a missing phrase.

Use Response segments in:

- **Surveys** to collect ungraded responses.
- **Normal lenses** for practice, reflection,--}{++{"author":"Elias's AI","timestamp":1787253784301}@@ response. Same syntax works in surveys, normal lenses,++} and{--{"author":"Elias's AI","timestamp":1787253784301}@@ checks for understanding.
- **Learning--}{++{"author":"Elias's AI","timestamp":1787253784301}@@ Learning++} Outcome{--{"author":"Elias's AI","timestamp":1787253784301}@@ tests** for graded assessment.

Syntax is identical in all three places. --}{++{"author":"Elias's AI","timestamp":1787253784301}@@ tests. ++}Context{--{"author":"Elias's AI","timestamp":1787253784301}@@ changes whether a response is graded, not how segment is written.--}{++{"author":"Elias's AI","timestamp":1787253784301}@@ determines grading.++}

{--{"author":"Elias's AI","timestamp":1787253784301}@@Each section below starts with smallest useful version. Only--}{++{"author":"Elias's AI","timestamp":1787253784301}@@Every Response segment needs++} `id::` and {--{"author":"Elias's AI","timestamp":1787253784301}@@`content::` are shared requirements. Everything else may be left out unless course creator wants different behavior.

- `id::`: globally unique UUID. It identifies segment in stored responses, grading, and analytics. Never change it after learners have answered.
- `content::`: prompt shown to learner.
- `required:: true`: require response before learner can continue. Defaults to `false`, so leave it out when response may be skipped.
- `feedback-instructions:: ...`: ask AI--}{++{"author":"Elias's AI","timestamp":1787253784301}@@`content::`. Editor should create globally unique UUID automatically. For hand-written files, use https://www.uuidgenerator.net/version4 or plain-text API https://www.uuidgenerator.net/api/version4. Never change ID after learners respond. No separate key needed.

Response segments are required by default. Adding one normally means learner should answer it; required default prevents accidental missing responses. Add `optional:: true` only when skipping is intentional, such as sensitive survey question or optional reflection. `optional::` defaults++} to {--{"author":"Elias's AI","timestamp":1787253784301}@@respond after submission using these instructions. Defaults to--}{++{"author":"Elias's AI","timestamp":1787253784301}@@`false`.

`feedback-instructions::` is optional on every Response segment. If omitted,++} no AI{--{"author":"Elias's AI","timestamp":1787253784301}@@ feedback when omitted. This--}{++{"author":"Elias's AI","timestamp":1787253784301}@@ feedback. It++} does not make response graded.

{--{"author":"Elias's AI","timestamp":1787253784301}@@Lens Editor should create `id::` automatically. When writing course files by hand, generate UUID at [uuidgenerator.net/version4](https://www.uuidgenerator.net/version4). Tools and language models can request one from [uuidgenerator.net/api/version4](https://www.uuidgenerator.net/api/version4).

Response segments do not need a separate human-readable key.

\## Open response

Use `#### OpenResponse` when learner should type--}{++{"author":"Elias's AI","timestamp":1787253784301}@@OpenResponse collects typed++} or {--{"author":"Elias's AI","timestamp":1787253784301}@@dictate a response.

--}{++{"author":"Elias's AI","timestamp":1787253784301}@@dictated text. ++}Smallest{--{"author":"Elias's AI","timestamp":1787253784301}@@ version:

> `#### OpenResponse`
> `id:: <uuid>`
> `content:: What is your strongest objection?`

Here is that minimal segment for learner to try:--}{++{"author":"Elias's AI","timestamp":1787253784301}@@ version follows. %%++}

#### OpenResponse
id:: 3e1a5838-95df-4d05-a88a-1b4ca868905f
content:: What is your strongest objection?

{--{"author":"Elias's AI","timestamp":1787253806184}@@#### Text
content::--}{++{"author":"Elias's AI","timestamp":1787253806184}@@%% OpenResponse options:++}
{--{"author":"Elias's AI","timestamp":1787253806184}@@Optional fields:

--}- {--{"author":"Elias's AI","timestamp":1787253806184}@@`required::--}{++{"author":"Elias's AI","timestamp":1787253806184}@@`optional::++} true`: {--{"author":"Elias's AI","timestamp":1787253806184}@@require response.--}{++{"author":"Elias's AI","timestamp":1787253806184}@@allow skipping.++} Defaults to `false`.
- `max-chars:: 500`: limit{--{"author":"Elias's AI","timestamp":1787253806184}@@ answer--} length. Defaults to no limit.
- `placeholder:: {--{"author":"Elias's AI","timestamp":1787253806184}@@Name the claim, then explain objection.`: show hint in empty input. --}{++{"author":"Elias's AI","timestamp":1787253806184}@@...`: empty-input hint. ++}Defaults to {--{"author":"Elias's AI","timestamp":1787253806184}@@no placeholder.--}{++{"author":"Elias's AI","timestamp":1787253806184}@@none.++}
- `max-time:: 3:00`:{--{"author":"Elias's AI","timestamp":1787253806184}@@ set answer--} timer in `M:SS`. Defaults to {--{"author":"Elias's AI","timestamp":1787253806184}@@no timer.--}{++{"author":"Elias's AI","timestamp":1787253806184}@@none.++}
- `enforce-voice:: true`: require {--{"author":"Elias's AI","timestamp":1787253806184}@@spoken response--}{++{"author":"Elias's AI","timestamp":1787253806184}@@speech++} instead of typing. Defaults to `false`.
- `assessment-instructions:: ...`:{--{"author":"Elias's AI","timestamp":1787253806184}@@ give--} AI grading rubric. {--{"author":"Elias's AI","timestamp":1787253806184}@@Without it, response is ungraded.--}{++{"author":"Elias's AI","timestamp":1787253806184}@@Omit for ungraded response.++}
- `feedback-instructions:: ...`: {--{"author":"Elias's AI","timestamp":1787253806184}@@ask--}{++{"author":"Elias's AI","timestamp":1787253806184}@@learner-facing++} AI{--{"author":"Elias's AI","timestamp":1787253806184}@@ to provide learner-facing--} feedback. {--{"author":"Elias's AI","timestamp":1787253806184}@@Defaults to no AI feedback when omitted.--}{++{"author":"Elias's AI","timestamp":1787253806184}@@Omit for none.++}

{--{"author":"Elias's AI","timestamp":1787253806184}@@`assessment-instructions::`--}{++{"author":"Elias's AI","timestamp":1787253806184}@@Assessment++} controls {--{"author":"Elias's AI","timestamp":1787253806184}@@grading. `feedback-instructions::`--}{++{"author":"Elias's AI","timestamp":1787253806184}@@score; feedback++} controls what learner sees. Surveys never grade{--{"author":"Elias's AI","timestamp":1787253806184}@@ responses,--} but may still {--{"author":"Elias's AI","timestamp":1787253806184}@@use `feedback-instructions::`.--}{++{"author":"Elias's AI","timestamp":1787253806184}@@give feedback.++}

{--{"author":"Elias's AI","timestamp":1787253806184}@@\## --}Rating{--{"author":"Elias's AI","timestamp":1787253806184}@@

Use `#### Rating` for --}{++{"author":"Elias's AI","timestamp":1787253806184}@@ collects ++}numbered {--{"author":"Elias's AI","timestamp":1787253806184}@@scale from 1 to 5.

--}{++{"author":"Elias's AI","timestamp":1787253806184}@@self-report. ++}Smallest {--{"author":"Elias's AI","timestamp":1787253806184}@@version:

> `#### Rating`
> `id:: <uuid>`
> `content:: How confident are you in your answer?`

Try it:--}{++{"author":"Elias's AI","timestamp":1787253806184}@@version uses default 1-to-5 scale. %%++}

#### Rating
id:: 4280d5f2-2cd5-48f9-b20f-fc132253d443
content:: How confident are you in your answer?

%%{--{"author":"Elias's AI","timestamp":1787253809854}@@
#### Text
content::
Optional fields:

--}{++{"author":"Elias's AI","timestamp":1787253809854}@@ Rating options:
++}- {--{"author":"Elias's AI","timestamp":1787253809854}@@`required::--}{++{"author":"Elias's AI","timestamp":1787253809854}@@`optional::++} true`: {--{"author":"Elias's AI","timestamp":1787253809854}@@require response.--}{++{"author":"Elias's AI","timestamp":1787253809854}@@allow skipping.++} Defaults to `false`.
- `scale:: 7`:{--{"author":"Elias's AI","timestamp":1787253809854}@@ set--} highest {--{"author":"Elias's AI","timestamp":1787253809854}@@number--}{++{"author":"Elias's AI","timestamp":1787253809854}@@number,++} from 2 to 10. Defaults to `5`.
- `low-label:: Not confident`: {--{"author":"Elias's AI","timestamp":1787253809854}@@label low endpoint.--}{++{"author":"Elias's AI","timestamp":1787253809854}@@low-end label.++} Defaults to {--{"author":"Elias's AI","timestamp":1787253809854}@@no label.--}{++{"author":"Elias's AI","timestamp":1787253809854}@@none.++}
- `high-label:: Very confident`: {--{"author":"Elias's AI","timestamp":1787253809854}@@label high endpoint. --}{++{"author":"Elias's AI","timestamp":1787253809854}@@high-end label. ++}Defaults to {--{"author":"Elias's AI","timestamp":1787253809854}@@no label.--}{++{"author":"Elias's AI","timestamp":1787253809854}@@none.++}
- `feedback-instructions:: ...`:{--{"author":"Elias's AI","timestamp":1787253809854}@@ ask--} AI {--{"author":"Elias's AI","timestamp":1787253809854}@@to respond--}{++{"author":"Elias's AI","timestamp":1787253809854}@@response++} to{--{"author":"Elias's AI","timestamp":1787253809854}@@ selected--} rating. Defaults to {--{"author":"Elias's AI","timestamp":1787253809854}@@no AI feedback when omitted.--}{++{"author":"Elias's AI","timestamp":1787253809854}@@none.++}

Ratings{--{"author":"Elias's AI","timestamp":1787253809854}@@ are self-reports, not correct or incorrect. In Learning Outcome tests, rating is stored beside graded answers but does not--}{++{"author":"Elias's AI","timestamp":1787253809854}@@ never++} affect {--{"author":"Elias's AI","timestamp":1787253809854}@@test--}{++{"author":"Elias's AI","timestamp":1787253809854}@@correctness++} score.

{--{"author":"Elias's AI","timestamp":1787253809854}@@\## Single select

Use `#### Select` with `options::`. With no--}{++{"author":"Elias's AI","timestamp":1787253809854}@@Select requires `options::`; default allows one selection. Without++} `[x]`, {--{"author":"Elias's AI","timestamp":1787253809854}@@response--}{++{"author":"Elias's AI","timestamp":1787253809854}@@it++} is ungraded.{--{"author":"Elias's AI","timestamp":1787253809854}@@

Smallest version:

> `#### Select`
> `id:: <uuid>`
> `content:: Which topic should we cover next?`
> `options::`
> `- Forecasting`
> `- Governance`

Try it:
--}{++{"author":"Elias's AI","timestamp":1787253809854}@@ ++}%%
#### Select
id:: a59ce650-c5cf-4b2b-bc13-e0686f5d2bfb
content:: Which topic should we cover next?
options::
- Forecasting
- Governance

{--{"author":"Elias's AI","timestamp":1787253833026}@@#### Text
content::
--}{++{"author":"Elias's AI","timestamp":1787253833026}@@%% ++}Mark correct option with `[x]` {--{"author":"Elias's AI","timestamp":1787253833026}@@when response should be graded:

> `options::`
> `- Data collection`
> `- [x] Gradient descent`--}{++{"author":"Elias's AI","timestamp":1787253833026}@@to grade Select. Plain options stay ungraded. Survey selects never use `[x]`.

Select options:++}
{--{"author":"Elias's AI","timestamp":1787253833026}@@> `- Deployment monitoring`

Optional fields:

--}- {--{"author":"Elias's AI","timestamp":1787253833026}@@`required::--}{++{"author":"Elias's AI","timestamp":1787253833026}@@`optional::++} true`: {--{"author":"Elias's AI","timestamp":1787253833026}@@require response.--}{++{"author":"Elias's AI","timestamp":1787253833026}@@allow skipping.++} Defaults to `false`.
- `multi:: true`: allow multiple selections. Defaults to `false`.
- `shuffle:: true`: randomize {--{"author":"Elias's AI","timestamp":1787253833026}@@option --}order. Defaults to `false`.
- `feedback-instructions:: ...`: {--{"author":"Elias's AI","timestamp":1787253833026}@@ask --}AI{--{"author":"Elias's AI","timestamp":1787253833026}@@ to respond--}{++{"author":"Elias's AI","timestamp":1787253833026}@@ response++} to {--{"author":"Elias's AI","timestamp":1787253833026}@@learner's --}selection. Defaults to{--{"author":"Elias's AI","timestamp":1787253833026}@@ no AI feedback when omitted.

Survey selects must use plain list items. Surveys never contain correct-answer markers.--}{++{"author":"Elias's AI","timestamp":1787253833026}@@ none.++}

{--{"author":"Elias's AI","timestamp":1787253833026}@@\## --}Multi-select{--{"author":"Elias's AI","timestamp":1787253833026}@@

Multi-select--} is same{--{"author":"Elias's AI","timestamp":1787253833026}@@ Response--} segment with{--{"author":"Elias's AI","timestamp":1787253833026}@@ one non-default field: --}{++{"author":"Elias's AI","timestamp":1787253833026}@@ ++}`multi:: true`.{--{"author":"Elias's AI","timestamp":1787253833026}@@

Smallest version:

> `#### Select`
> `id:: <uuid>`
> `content:: Which topics interest you?`
> `options::`
> `- Forecasting`
> `- Governance`
> `- Technical safety`
> `multi:: true`

Try it:--}{++{"author":"Elias's AI","timestamp":1787253833026}@@ %%++}

#### Select
id:: cb39e8f1-4477-4b66-b016-37c99c5ff753
content:: Which topics interest you?
options::
- Forecasting
- Governance
- Technical safety
multi:: true

{--{"author":"Elias's AI","timestamp":1787253839292}@@#### Text
content::
It--}{++{"author":"Elias's AI","timestamp":1787253839292}@@%% Multi-select++} has same {--{"author":"Elias's AI","timestamp":1787253839292}@@optional fields --}{++{"author":"Elias's AI","timestamp":1787253839292}@@options ++}and defaults as single select. For {--{"author":"Elias's AI","timestamp":1787253839292}@@graded multi-select, learner's selected options--}{++{"author":"Elias's AI","timestamp":1787253839292}@@grading, learner selection++} must exactly match all `[x]` options.{--{"author":"Elias's AI","timestamp":1787253839292}@@ In surveys, options stay ungraded and use no `[x]` markers.

\## Fill in the blank

Use `#### FillBlank`. Write --}{++{"author":"Elias's AI","timestamp":1787253839292}@@

FillBlank puts inputs inside sentence. Text inside braces is ++}accepted {--{"author":"Elias's AI","timestamp":1787253839292}@@answer directly inside blank.

--}{++{"author":"Elias's AI","timestamp":1787253839292}@@answer. ++}Smallest graded {--{"author":"Elias's AI","timestamp":1787253839292}@@version:

> `#### FillBlank`
> `id:: <uuid>`
> `content:: France's capital is {{Paris}}.`

Try it:--}{++{"author":"Elias's AI","timestamp":1787253839292}@@version follows. %%++}

#### FillBlank
id:: ec12502a-e39c-4589-87f5-9f14855648c9
content:: France's capital is {{Paris}}.

{--{"author":"Elias's AI","timestamp":1787253842727}@@#### Text--}{++{"author":"Elias's AI","timestamp":1787253842727}@@%% FillBlank syntax:++}
{--{"author":"Elias's AI","timestamp":1787253842727}@@content::
Separate alternative accepted answers with `|`:

> `content:: Model weights are commonly updated using {{gradient descent|gradient-based optimization}}.`

Put--}{++{"author":"Elias's AI","timestamp":1787253842727}@@- `{{gradient descent|gradient-based optimization}}`: graded text with alternatives.
- `{{Paris}} ... {{Berlin}}`:++} several blanks in one {--{"author":"Elias's AI","timestamp":1787253842727}@@sentence:

> `content:: France's capital is {{Paris}}, while Germany's capital is {{Berlin}}.`--}{++{"author":"Elias's AI","timestamp":1787253842727}@@sentence.
- `{{blank}}`: ungraded text.
- `{{number}}`: ungraded number.++}

{--{"author":"Elias's AI","timestamp":1787253842727}@@Each `{{...}}` becomes separate input. --}Text matching is{--{"author":"Elias's AI","timestamp":1787253842727}@@ always--} case-sensitive and {--{"author":"Elias's AI","timestamp":1787253842727}@@ignores whitespace at beginning and end of learner response. There are no `case-sensitive::` or `trim::` fields.--}{++{"author":"Elias's AI","timestamp":1787253842727}@@always trims surrounding whitespace. No options control this.++}

{--{"author":"Elias's AI","timestamp":1787253842727}@@Use `{{blank}}` for ungraded text input:

> `content:: One change I want to make--}{++{"author":"Elias's AI","timestamp":1787253842727}@@Next example++} is {--{"author":"Elias's AI","timestamp":1787253842727}@@{{blank}}.`

Use `{{number}}` for ungraded numeric input:

> `content:: How many years until transformative AI? {{number}}`

Try it:--}{++{"author":"Elias's AI","timestamp":1787253842727}@@optional, showing `optional:: true`. %%++}

#### FillBlank
id:: 8a3ae4f5-4d86-42dc-b126-b293f88a7b61
content:: How many years until transformative AI? {{number}}{++{"author":"Elias's AI","timestamp":1787253866677}@@
optional:: true++}

{--{"author":"Elias's AI","timestamp":1787253870467}@@#### Text
content::--}{++{"author":"Elias's AI","timestamp":1787253870467}@@%% Numeric grading:++}
{--{"author":"Elias's AI","timestamp":1787253870467}@@Put one accepted number after `number` for an exact graded answer:--}{++{"author":"Elias's AI","timestamp":1787253870467}@@- `{{number 42}}`: exact number.
- `{{number 147,500,000 to 152,000,000}}`: inclusive range.++}

{--{"author":"Elias's AI","timestamp":1787253870467}@@> `content:: Six times seven is {{number 42}}.`

Use `to` for an inclusive--}{++{"author":"Elias's AI","timestamp":1787253870467}@@Commas may separate thousands. Decimals and negative values work. Next example shows++} graded {--{"author":"Elias's AI","timestamp":1787253870467}@@range:

> `content:: Earth is approximately {{number 147,500,000 to 152,000,000}} km from Sun.`

Try it:--}{++{"author":"Elias's AI","timestamp":1787253870467}@@range. %%++}

#### FillBlank
id:: 1211df1d-70e8-4b93-a3b6-1ce44460ed1f
content:: Earth is approximately {{number 147,500,000 to 152,000,000}} km from Sun.

{--{"author":"Elias's AI","timestamp":1787253874947}@@#### Text
content::
--}{++{"author":"Elias's AI","timestamp":1787253874947}@@%% ++}Numeric blanks{--{"author":"Elias's AI","timestamp":1787253874947}@@ accept integers, decimals, negative values, and commas as thousands separators. They --}{++{"author":"Elias's AI","timestamp":1787253874947}@@ ++}store numbers, not text. {--{"author":"Elias's AI","timestamp":1787253874947}@@Ranges include both endpoints. --}Validator {--{"author":"Elias's AI","timestamp":1787253874947}@@should reject--}{++{"author":"Elias's AI","timestamp":1787253874947}@@rejects++} malformed numbers, reversed ranges, and {--{"author":"Elias's AI","timestamp":1787253874947}@@commas placed anywhere except between groups of three digits.--}{++{"author":"Elias's AI","timestamp":1787253874947}@@invalid thousands separators.++}

One FillBlank{--{"author":"Elias's AI","timestamp":1787253874947}@@ segment--} may mix text and numeric blanks, and graded and ungraded {--{"author":"Elias's AI","timestamp":1787253874947}@@blanks:

> `content:: I--}{++{"author":"Elias's AI","timestamp":1787253874947}@@blanks, for example: `I++} estimate {{number}} years because {{blank}}.`

{--{"author":"Elias's AI","timestamp":1787253874947}@@Optional fields:

--}{++{"author":"Elias's AI","timestamp":1787253874947}@@FillBlank options:
++}- {--{"author":"Elias's AI","timestamp":1787253874947}@@`required::--}{++{"author":"Elias's AI","timestamp":1787253874947}@@`optional::++} true`: {--{"author":"Elias's AI","timestamp":1787253874947}@@require every blank.--}{++{"author":"Elias's AI","timestamp":1787253874947}@@allow skipping whole segment.++} Defaults to {--{"author":"Elias's AI","timestamp":1787253874947}@@`false`.--}{++{"author":"Elias's AI","timestamp":1787253874947}@@`false`, so every blank is required.++}
- `feedback-instructions:: ...`: {--{"author":"Elias's AI","timestamp":1787253874947}@@ask--}{++{"author":"Elias's AI","timestamp":1787253874947}@@learner-facing++} AI{--{"author":"Elias's AI","timestamp":1787253874947}@@ to provide learner-facing--} feedback. Defaults to {--{"author":"Elias's AI","timestamp":1787253874947}@@no AI feedback when omitted. Feedback--}{++{"author":"Elias's AI","timestamp":1787253874947}@@none and++} does not{--{"author":"Elias's AI","timestamp":1787253874947}@@ change which blanks are graded.--}{++{"author":"Elias's AI","timestamp":1787253874947}@@ affect grading.++}

{--{"author":"Elias's AI","timestamp":1787253874947}@@Segment score--}{++{"author":"Elias's AI","timestamp":1787253874947}@@Score++} is {--{"author":"Elias's AI","timestamp":1787253874947}@@correctly answered--}{++{"author":"Elias's AI","timestamp":1787253874947}@@correct++} graded blanks divided by {--{"author":"Elias's AI","timestamp":1787253874947}@@total--}{++{"author":"Elias's AI","timestamp":1787253874947}@@all++} graded blanks. Ungraded blanks are excluded.{--{"author":"Elias's AI","timestamp":1787253874947}@@ If segment has no--}{++{"author":"Elias's AI","timestamp":1787253874947}@@ No++} graded {--{"author":"Elias's AI","timestamp":1787253874947}@@blanks, entire response is ungraded.--}{++{"author":"Elias's AI","timestamp":1787253874947}@@blanks means ungraded segment.++}

{--{"author":"Elias's AI","timestamp":1787253874947}@@\## --}Grading {--{"author":"Elias's AI","timestamp":1787253874947}@@rules

- **Survey:** all Response segment types are ungraded.--}{++{"author":"Elias's AI","timestamp":1787253874947}@@by context:
- Surveys never grade.++}
-{--{"author":"Elias's AI","timestamp":1787253874947}@@ **Normal lens:** responses--}{++{"author":"Elias's AI","timestamp":1787253874947}@@ Normal lenses++} may {--{"author":"Elias's AI","timestamp":1787253874947}@@be--}{++{"author":"Elias's AI","timestamp":1787253874947}@@contain++} graded practice or ungraded reflection.
- {--{"author":"Elias's AI","timestamp":1787253874947}@@**Learning--}{++{"author":"Elias's AI","timestamp":1787253874947}@@Learning++} Outcome {--{"author":"Elias's AI","timestamp":1787253874947}@@test:**--}{++{"author":"Elias's AI","timestamp":1787253874947}@@tests require gradable++} OpenResponse and {--{"author":"Elias's AI","timestamp":1787253874947}@@Select must be gradable. --}{++{"author":"Elias's AI","timestamp":1787253874947}@@Select. ++}FillBlank may {--{"author":"Elias's AI","timestamp":1787253874947}@@contain--}{++{"author":"Elias's AI","timestamp":1787253874947}@@mix++} graded and ungraded blanks.{++{"author":"Elias's AI","timestamp":1787253874947}@@
-++} OpenResponse {++{"author":"Elias's AI","timestamp":1787253874947}@@grading ++}needs `assessment-instructions::`; Select {--{"author":"Elias's AI","timestamp":1787253874947}@@needs at least one --}{++{"author":"Elias's AI","timestamp":1787253874947}@@grading needs ++}`[x]`.
- Rating and wholly ungraded FillBlank {--{"author":"Elias's AI","timestamp":1787253874947}@@responses --}never {--{"author":"Elias's AI","timestamp":1787253874947}@@contribute to correctness score.--}{++{"author":"Elias's AI","timestamp":1787253874947}@@affect score. %%++}
