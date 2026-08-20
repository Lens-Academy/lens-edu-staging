---
id: 8189763f-576e-4f04-a614-4a00c628e386
duration_minutes: 15
title: Response segments
tldr: Use open responses, ratings, selects, and typed fill-in-the-blank responses with the same syntax in surveys, normal lenses, and learning-outcome tests.
summary_for_tutor: Reference page for course creators. It documents shared fields, exact syntax, options, defaults, and grading behavior for OpenResponse, Rating, Select, and typed FillBlank Response segments.
---

%% A Response segment is an interactive field that collects one learner response. Same syntax works in surveys, normal lenses, and Learning Outcome tests. Context determines grading.

Every Response segment needs `id::` and `content::`. Editor should create globally unique UUID automatically. For hand-written files, use https://www.uuidgenerator.net/version4 or plain-text API https://www.uuidgenerator.net/api/version4. Never change ID after learners respond. No separate key needed.

Response segments are required by default. Adding one normally means learner should answer it; required default prevents accidental missing responses. Add `optional:: true` only when skipping is intentional, such as sensitive survey question or optional reflection. `optional::` defaults to `false`.

{++{"author":"Elias's AI","timestamp":1787255690358}@@Graded OpenResponse and FillBlank use same assessor flow. Platform supplies base assessment prompt, then authored `assessment-instructions::` when present, question context, expected answers, and learner response. Assessor returns structured `score` from 0 to 100 and private `reason`. Learner sees percentage, not private reason.

++}`feedback-instructions::` is {--{"author":"Elias's AI","timestamp":1787255690358}@@optional on every Response segment. If omitted, no AI feedback. It does not make response graded.--}{++{"author":"Elias's AI","timestamp":1787255690358}@@optional. If present, normal tutor receives question context, learner response, score, private assessment reason, and authored feedback instructions, then responds as ordinary tutor chat. If omitted, no tutor feedback.++}

OpenResponse collects typed or dictated text. Smallest version follows. %%

#### OpenResponse
id:: 3e1a5838-95df-4d05-a88a-1b4ca868905f
content:: What is your strongest objection?

%% OpenResponse options:
- `optional:: true`: allow skipping. Defaults to `false`.
- `max-chars:: 500`: limit length. Defaults to no limit.
- `placeholder:: ...`: empty-input hint. Defaults to none.
- `max-time:: 3:00`: timer in `M:SS`. Defaults to none.
- `enforce-voice:: true`: require speech instead of typing. Defaults to `false`.
- `assessment-instructions:: ...`: AI grading rubric. Omit for ungraded response.
- `feedback-instructions:: ...`: learner-facing AI feedback. Omit for none.

Assessment controls score; feedback controls what learner sees. Surveys never grade but may still give feedback.

Next example adds limits, grading, and feedback. %%

#### OpenResponse
id:: b8854587-3e8f-471d-b37c-fb63684ecf19
content:: In two sentences, what is strongest objection?
max-chars:: 500
placeholder:: Name claim, then explain objection.
max-time:: 3:00
enforce-voice:: true
assessment-instructions:: Check whether learner names claim and gives relevant objection.
feedback-instructions:: State strongest part of response, then suggest one improvement.

%% Rating collects numbered self-report. Smallest version uses default 1-to-5 scale. %%

#### Rating
id:: 4280d5f2-2cd5-48f9-b20f-fc132253d443
content:: How confident are you in your answer?

%% Rating options:
- `optional:: true`: allow skipping. Defaults to `false`.
- `scale:: 7`: highest number, from 2 to 10. Defaults to `5`.
- `low-label:: Not confident`: low-end label. Defaults to none.
- `high-label:: Very confident`: high-end label. Defaults to none.
- `feedback-instructions:: ...`: AI response to rating. Defaults to none.

Ratings never affect correctness score. Next example changes scale and labels, and adds AI feedback. %%

#### Rating
id:: 651213b4-1952-4ed4-98a8-8f772cf732d6
content:: How confident are you in your answer?
scale:: 7
low-label:: Not confident
high-label:: Very confident
feedback-instructions:: Briefly suggest how learner could calibrate this confidence against evidence.

%% Select requires `options::`; default allows one selection. Without `[x]`, it is ungraded. %%
#### Select
id:: a59ce650-c5cf-4b2b-bc13-e0686f5d2bfb
content:: Which topic should we cover next?
options::
- Forecasting
- Governance

%% Mark correct option with `[x]` to grade Select. Plain options stay ungraded. Survey selects never use `[x]`.

Select options:
- `optional:: true`: allow skipping. Defaults to `false`.
- `multi:: true`: allow multiple selections. Defaults to `false`.
- `shuffle:: true`: randomize order. Defaults to `false`.
- `feedback-instructions:: ...`: AI response to selection. Defaults to none.

Next example grades one correct option. %%

#### Select
id:: 4e93c96d-a0a8-4fa5-9c29-ea360fd283fe
content:: Which process updates model weights during training?
options::
- Data collection
- [x] Gradient descent
- Deployment monitoring
shuffle:: true
feedback-instructions:: Explain misconception behind learner selection without adding unrelated detail.

%% Multi-select is same segment with `multi:: true`. %%

#### Select
id:: cb39e8f1-4477-4b66-b016-37c99c5ff753
content:: Which topics interest you?
options::
- Forecasting
- Governance
- Technical safety
multi:: true

%% Multi-select has same options and defaults as single select. For grading, learner selection must exactly match all `[x]` options.

FillBlank puts inputs inside sentence. Text inside braces is accepted answer. Smallest graded version follows. %%

#### FillBlank
id:: ec12502a-e39c-4589-87f5-9f14855648c9
content:: France's capital is {{Paris}}.

%% FillBlank syntax:
- `{{gradient descent|gradient-based optimization}}`: graded text with alternatives.
- `{{Paris}} ... {{Berlin}}`: several blanks in one sentence.
- `{{blank}}`: ungraded text.
- `{{number}}`: ungraded number.

Text matching is case-sensitive and always trims surrounding whitespace. No options control this. Next example has alternatives and several graded text blanks. %%

#### FillBlank
id:: 115ecd2e-385a-4c90-8964-afc169cb822a
content:: France's capital is {{Paris}}, while model weights are commonly updated using {{gradient descent|gradient-based optimization}}.

%% `{{number}}` creates ungraded numeric input. Next example also shows `optional:: true`. %%

#### FillBlank
id:: 8a3ae4f5-4d86-42dc-b126-b293f88a7b61
content:: How many years until transformative AI? {{number}}
optional:: true

%% Numeric grading:
- `{{number 42}}`: exact number.
- `{{number 147,500,000 to 152,000,000}}`: inclusive range.

Commas may separate thousands. Decimals and negative values work. Next example shows graded range. %%

#### FillBlank
id:: 1211df1d-70e8-4b93-a3b6-1ce44460ed1f
content:: Earth is approximately {{number 147,500,000 to 152,000,000}} km from Sun.

%% Numeric blanks store numbers, not text. Validator rejects malformed numbers, reversed ranges, and invalid thousands separators.

One FillBlank may mix text and numeric blanks, and graded and ungraded blanks, for example: `I estimate {{number}} years because {{blank}}.`

FillBlank options:
- `optional:: true`: allow skipping whole segment. Defaults to `false`, so every blank is required.
- `feedback-instructions:: ...`: learner-facing AI feedback. Defaults to none and does not affect grading.

Score is correct graded blanks divided by all graded blanks. Ungraded blanks are excluded. No graded blanks means ungraded segment.

Grading by context:
- Surveys never grade.
- Normal lenses may contain graded practice or ungraded reflection.
- Learning Outcome tests require gradable OpenResponse and Select. FillBlank may mix graded and ungraded blanks.
- OpenResponse grading needs `assessment-instructions::`; Select grading needs `[x]`.
- Rating and wholly ungraded FillBlank never affect score. %%
