---
id: 8189763f-576e-4f04-a614-4a00c628e386
duration_minutes: 15
title: Response to question segments
tldr: Use Response to question segments for open responses, ratings, {--{"author":"Elias's AI","timestamp":1787312176770}@@selections,--}{++{"author":"Elias's AI","timestamp":1787312176770}@@choices,++} fill-in-the-blank responses, and rankings with same syntax in surveys, normal lenses, and learning-outcome tests.
summary_for_tutor: {--{"author":"Elias's AI","timestamp":1787312173425}@@Reference--}{++{"author":"Elias's AI","timestamp":1787312173425}@@'Reference++} page for course creators. It documents shared fields, exact syntax, options, defaults, LLM assessment flow, and grading behavior for {--{"author":"Elias's AI","timestamp":1787312173425}@@`Question: Open`, `Question: Rating`, `Question: Select`, `Question: FillBlank`,--}{++{"author":"Elias's AI","timestamp":1787312173425}@@Question: Open, Question: Rating, Question: Choice, Question: FillBlank,++} and {--{"author":"Elias's AI","timestamp":1787312173425}@@`Question: Ranking`--}{++{"author":"Elias's AI","timestamp":1787312173425}@@Question: Ranking++} Response to question {--{"author":"Elias's AI","timestamp":1787312173425}@@segments.--}{++{"author":"Elias's AI","timestamp":1787312173425}@@segments.'++}
---

%% A Response to question segment is an interactive field that collects one learner response. Same syntax works in surveys, normal lenses, and Learning Outcome tests. Context determines grading.

Every Response to question segment needs `id::` and `content::`. Editor should create globally unique UUID automatically. For hand-written files, use https://www.uuidgenerator.net/version4 or plain-text API https://www.uuidgenerator.net/api/version4. Never change ID after learners respond. No separate key needed.

Response to question segments are required by default. Adding one normally means learner should answer it; required default prevents accidental missing responses. Add `optional:: true` only when skipping is intentional, such as sensitive survey question or optional reflection. `optional::` defaults to `false`.

Graded `Question: Open` and `Question: FillBlank` use same assessor flow. Platform supplies base assessment prompt, then authored `assessment-instructions::` when present, question context, expected answers, and learner response. Assessor returns structured `score` from 0 to 100 and private `reason`. Learner sees percentage, not private reason.

`feedback-instructions::` is optional. If present, normal tutor receives question context, learner response, score, private assessment reason, and authored feedback instructions, then responds as ordinary tutor chat. If omitted, no tutor feedback.

`Question: Open` collects typed or dictated text. Smallest version follows. %%

#### Question: Open
id:: 3e1a5838-95df-4d05-a88a-1b4ca868905f
content:: What is your strongest objection?

%% `Question: Open` options:
- `optional:: true`: allow skipping. Defaults to `false`.
- `max-chars:: 500`: limit length. Defaults to no limit.
- `placeholder:: ...`: empty-input hint. Defaults to none.
- `max-time:: 3:00`: timer in `M:SS`. Defaults to none.
- `enforce-voice:: true`: require speech instead of typing. Defaults to `false`.
- `assessment-instructions:: ...`: extra instructions appended to base assessor prompt. Omit for ungraded `Question: Open`.
- `feedback-instructions:: ...`: learner-facing AI feedback. Omit for none.

Assessment controls score; feedback controls what learner sees. Surveys never grade but may still give feedback.

Next example adds limits, grading, and feedback. %%

#### Question: Open
id:: b8854587-3e8f-471d-b37c-fb63684ecf19
content:: In two sentences, what is strongest objection?
max-chars:: 500
placeholder:: Name claim, then explain objection.
max-time:: 3:00
enforce-voice:: true
assessment-instructions:: Check whether learner names claim and gives relevant objection.
feedback-instructions:: State strongest part of response, then suggest one improvement.

%% `Question: Rating` collects numbered self-report. Smallest version uses default 1-to-5 scale. %%

#### Question: Rating
id:: 4280d5f2-2cd5-48f9-b20f-fc132253d443
content:: How confident are you in your answer?

%% `Question: Rating` options:
- `optional:: true`: allow skipping. Defaults to `false`.
- `scale:: 7`: highest number, from 2 to 10. Defaults to `5`.
- `low-label:: Not confident`: low-end label. Defaults to none.
- `high-label:: Very confident`: high-end label. Defaults to none.
- `feedback-instructions:: ...`: AI response to rating. Defaults to none.

`Question: Rating` responses never affect correctness score. Next example changes scale and labels, and adds AI feedback. %%

#### Question: Rating
id:: 651213b4-1952-4ed4-98a8-8f772cf732d6
content:: How confident are you in your answer?
scale:: 7
low-label:: Not confident
high-label:: Very confident
feedback-instructions:: Briefly suggest how learner could calibrate this confidence against evidence.

%% `Question: {--{"author":"Elias's AI","timestamp":1787312223300}@@Select`--}{++{"author":"Elias's AI","timestamp":1787312223300}@@Choice`++} requires `options::`; default allows one {--{"author":"Elias's AI","timestamp":1787312223300}@@selection.--}{++{"author":"Elias's AI","timestamp":1787312223300}@@choice.++} Without `[x]`, it is ungraded. %%
#### Question: {--{"author":"Elias's AI","timestamp":1787312226803}@@Select--}{++{"author":"Elias's AI","timestamp":1787312226803}@@Choice++}
id:: a59ce650-c5cf-4b2b-bc13-e0686f5d2bfb
content:: Which topic should we cover next?
options::
- Forecasting
- Governance

%% Mark correct option with `[x]` to grade `Question: {--{"author":"Elias's AI","timestamp":1787312229761}@@Select`.--}{++{"author":"Elias's AI","timestamp":1787312229761}@@Choice`.++} Plain options stay ungraded. Survey {--{"author":"Elias's AI","timestamp":1787312186434}@@selects--}{++{"author":"Elias's AI","timestamp":1787312186434}@@choices++} never use `[x]`.

`Question: {--{"author":"Elias's AI","timestamp":1787312232972}@@Select`--}{++{"author":"Elias's AI","timestamp":1787312232972}@@Choice`++} options:
- `optional:: true`: allow skipping. Defaults to `false`.
- `multi:: true`: allow multiple selections. Defaults to `false`.
- `shuffle:: true`: randomize order. Defaults to `false`.
- `feedback-instructions:: ...`: AI response to {--{"author":"Elias's AI","timestamp":1787312236010}@@selection.--}{++{"author":"Elias's AI","timestamp":1787312236010}@@choice.++} Defaults to none.

Next example grades one correct option. %%

#### Question: {--{"author":"Elias's AI","timestamp":1787312240729}@@Select--}{++{"author":"Elias's AI","timestamp":1787312240729}@@Choice++}
id:: 4e93c96d-a0a8-4fa5-9c29-ea360fd283fe
content:: Which process updates model weights during training?
options::
- Data collection
- [x] Gradient descent
- Deployment monitoring
shuffle:: true
feedback-instructions:: Explain misconception behind learner {--{"author":"Elias's AI","timestamp":1787312244448}@@selection--}{++{"author":"Elias's AI","timestamp":1787312244448}@@choice++} without adding unrelated detail.

%% {--{"author":"Elias's AI","timestamp":1787312248594}@@Multi-select is--}{++{"author":"Elias's AI","timestamp":1787312248594}@@Multiple choice uses++} same segment with `multi:: true`. %%

#### Question: {--{"author":"Elias's AI","timestamp":1787312253358}@@Select--}{++{"author":"Elias's AI","timestamp":1787312253358}@@Choice++}
id:: cb39e8f1-4477-4b66-b016-37c99c5ff753
content:: Which topics interest you?
options::
- Forecasting
- Governance
- Technical safety
multi:: true

%% {--{"author":"Elias's AI","timestamp":1787312256460}@@Multi-select--}{++{"author":"Elias's AI","timestamp":1787312256460}@@Multiple choice++} has same options and defaults as single {--{"author":"Elias's AI","timestamp":1787312197216}@@select--}{++{"author":"Elias's AI","timestamp":1787312197216}@@choice++}. For grading, learner {--{"author":"Elias's AI","timestamp":1787312256460}@@selection--}{++{"author":"Elias's AI","timestamp":1787312256460}@@choices++} must exactly match all `[x]` options.

`Question: FillBlank` puts inputs inside sentence. Text inside braces is accepted answer. Smallest graded version follows. %%

#### Question: FillBlank
id:: ec12502a-e39c-4589-87f5-9f14855648c9
content:: France's capital is {{Paris}}.

%% `Question: FillBlank` syntax:
- `{{gradient descent|gradient-based optimization}}`: graded text with alternatives.
- `{{Paris}} ... {{Berlin}}`: several blanks in one sentence.
- `{{blank}}`: ungraded text.
- `{{number}}`: ungraded number.

`Question: FillBlank` grading always uses assessor LLM, never programmatic string comparison. Base prompt is forgiving about capitalization, surrounding whitespace, minor misspellings, inflection, and equivalent wording while preserving intended meaning. There are no matching strictness options.

Text inside braces gives expected answer to assessor. Several alternatives separated by `|` are hints, not exhaustive whitelist. Next example has alternatives and several graded text blanks. %%

#### Question: FillBlank
id:: 115ecd2e-385a-4c90-8964-afc169cb822a
content:: France's capital is {{Paris}}, while model weights are commonly updated using {{gradient descent|gradient-based optimization}}.
assessment-instructions:: Give 50 points for each blank whose meaning is correct. Accept minor misspellings and equivalent phrasing.
feedback-instructions:: Explain any incorrect blank without discussing unrelated material.

%% `{{number}}` creates ungraded numeric input. Next example also shows `optional:: true`. %%

#### Question: FillBlank
id:: 8a3ae4f5-4d86-42dc-b126-b293f88a7b61
content:: How many years until transformative AI? {{number}}
optional:: true

%% Numeric grading uses one reference number: `{{number 42}}` or `{{number 149,600,000}}`. There is no range syntax. Commas may separate thousands; decimals and negative values work.

Assessor infers expected precision from question. Base numeric rubric:
- 100: correct within precision reasonably implied by question.
- 80 to 99: very close; difference does not change practical interpretation.
- 50 to 79: right scale or direction but materially off.
- 20 to 49: weak estimate showing some magnitude awareness.
- 1 to 19: barely related numerically.
- 0: wrong sign, incompatible unit, nonsensical value, or no meaningful proximity.

Next example uses default rubric. %%

#### Question: FillBlank
id:: 1211df1d-70e8-4b93-a3b6-1ce44460ed1f
content:: Earth is approximately {{number 149,600,000}} km from Sun.

%% Numeric blanks store numbers, not text. Validator rejects malformed numeric syntax and invalid thousands separators. Assessor LLM assigns percentage using reference number, wording, unit, context, and implied precision. This percentage is judgment, not objective error formula.

Use `assessment-instructions::` when domain needs explicit tolerance. Next example treats answer as Fermi estimate. %%

#### Question: FillBlank
id:: 5b5387b7-f8bf-4dd7-a4ae-a0c6468d7e22
content:: Estimate number of seconds in one year: {{number 31,536,000}}
assessment-instructions:: This is a Fermi estimate. Give 100 within factor 2, substantial credit within one order of magnitude, and 0 only for answer with no meaningful magnitude awareness.
feedback-instructions:: Explain most important estimation error and suggest one useful decomposition.

%% One `Question: FillBlank` may mix text and numeric blanks, and graded and ungraded blanks, for example: `I estimate {{number}} years because {{blank}}.`

`Question: FillBlank` options:
- `optional:: true`: allow skipping whole segment. Defaults to `false`, so every blank is required.
- `assessment-instructions:: ...`: extra natural-language rules appended to base assessor prompt. Use this for custom scoring such as "100 if first two blanks and either remaining blank are correct" or "60 if two of three are correct." Omit to use base assessment only.
- `feedback-instructions:: ...`: instructions for learner-facing tutor response after assessment. Omit for no tutor feedback.

Base assessor returns one percentage for whole segment plus private reason. Percentage appears beside response. Expected-answer blanks are graded automatically. `{{blank}}` and `{{number}}` remain ungraded unless `assessment-instructions::` defines how to judge them. %%

%% `Question: Ranking` lets learner arrange items. Plain `Question: Ranking` is ungraded, useful for preferences and reflection. Initial item order is randomized. %%

#### Question: Ranking
id:: dc6d348c-8c5c-416a-82d7-b7166d677258
content:: Rank these topics from most to least interesting to you.
items::
- Forecasting
- Governance
- Technical safety

%% Add `assessment-instructions::` to grade `Question: Ranking`. Items are authored in intended order, but shown shuffled. Assessor receives intended order, learner order, base ranking prompt, and custom instructions. It returns percentage plus private reason.

Use graded `Question: Ranking` for chronology, causal chains, procedures, and prioritization with explicit criterion. State allowed ties or alternate valid orders in assessment instructions. Keep lists around 3 to 7 items. (more or less possible, but not recommended) Next example grades procedure while allowing partial credit. %%

#### Question: Ranking
id:: 8ea396ee-7e7f-46b8-85ce-179ffe33bdf3
content:: Put these experimental steps in safe order.
items::
- Sterilize equipment
- Prepare sample
- Run procedure
- Dispose of hazardous material
assessment-instructions:: Treat authored order as ideal. Give partial credit for correct relative relationships. Sterilization must precede preparation and procedure; disposal must come last.
feedback-instructions:: Explain most important misplaced relationship and why it matters for safety.

%% Grading by context:
- Surveys never grade.
- Normal lenses may contain graded practice or ungraded reflection.
- Learning Outcome tests require gradable `Question: Open` and `Question: {--{"author":"Elias's AI","timestamp":1787312259859}@@Select`.--}{++{"author":"Elias's AI","timestamp":1787312259859}@@Choice`.++} `Question: FillBlank` may mix graded and ungraded blanks. `Question: Ranking` is graded when it has `assessment-instructions::`.
- `Question: Open` grading needs `assessment-instructions::`; `Question: FillBlank` with expected answers uses base assessor automatically; `Question: Select` grading needs `[x]`.
- `Question: Rating` and wholly ungraded `Question: FillBlank` never affect score. %%
