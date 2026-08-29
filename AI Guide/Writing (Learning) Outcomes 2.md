---
tags:
  - validator-ignore
---
# Writing Learning Outcomes 2 (AI Guide)

A learning-outcome file defines one real-world learner capability by combining a statement, a test, a grading brief, and optional suggestions for teaching it. It lives in `Lens Edu/Learning Outcomes/` and is imported into a module.

This guide has two parts:

1. A creation workflow for making the file.
2. Exact validation-agent instructions. Run every check after creation/editing, fix failures, then run fresh agents until all checks pass.

## Minimal LO file shape

```markdown
---
id: '<learning-outcome-uuid>'
learning-outcome: <observable capability description>
domain: "[[../Domains/<domain>]]"
stage: beginner
requires:
  - "[[Other prerequisite LO]]"
---
## Test:
id:: <test-uuid>

#### Question: Open
id:: <question-uuid>
content:: <self-contained test question>
assessment-instructions:: <0-to-100 grading brief>
feedback-instructions:: <optional learner-facing feedback brief>

# Suggested Lenses:
## Lens:
source:: [[../Lenses/<candidate teaching lens>]]
notes:: <optional author note>
```

One `## Test:` may contain several gradable questions or roleplays. Each item receives its own score.

A test may contain only gradable response segments and roleplays:

- `Question: Open` with `assessment-instructions::`
- `Question: Choice` with at least one `[x]`
- `Question: FillBlank` with at least one graded blank
- `Question: Ranking` with `assessment-instructions::`
- `Roleplay`

`Question: Rating`, ungraded variants, prose segments, and bare `#### Question` are invalid in tests. Use [[../Lenses/Response to question segments]] as single source of truth for question fields, defaults, and syntax.


## How to create a learning outcome

1. Read the course file, the relevant module, and the content that currently teaches or motivates this capability. Read [[../Lenses/Response to question segments]] for question syntax.
2. Identify a capability that matters outside the assigned reading. Start from what someone should be able to do in real work, advanced study, or sound reasoning. Do not start from a chapter and turn its takeaway into an outcome.
3. Scope one testable skill. If two capabilities could reasonably be taught, tested, or improved independently, create separate learning-outcome files. A multi-clause statement is fine when every clause is a facet of one capability that stands or falls together.
4. Write the `learning-outcome:` statement. Use an observable action such as explain, distinguish, identify, compare, analyze, evaluate, apply, produce, decompose, or state. Name the object and the important mechanism, criterion, or boundary. Avoid `understand`, `know`, `appreciate`, `be aware of`, `be familiar with`, and unqualified `reason about`.
5. Design the test before choosing or revising teaching material. Test the capability itself, not recall of the assigned author, chapter, analogy, or wording. Prefer an unfamiliar application or self-contained scenario.
6. Prefer one integrated test item when it can measure the whole skill. Use multiple gradable questions or roleplays only when each provides distinct evidence about inseparable facets of the same skill.
7. Write `assessment-instructions::` for every test item. Define observable evidence for a defensible 0 to 100 score. State which elements are load-bearing, what partial performance looks like, what alternative reasoning is acceptable, and what should not be penalized. Grade reasoning, not agreement.
8. Add `feedback-instructions::` when the learner should receive tutor feedback. Keep feedback guidance out of `assessment-instructions::`: assessment decides the score; feedback decides what the tutor says.
9. Check practice alignment. The module must teach and let learners practise every capability the test grades, with feedback before the test. Practice should exercise the same skill without copying the test answer.
10. Add filename and metadata. Filename is learner-visible: a unique, course-independent noun phrase of 2 to 6 words, sentence case, with no course prefix. Add stable UUIDs for the learning outcome, test, and every response segment. Add `domain:`, `stage:`, and genuine `requires:` links when the LO belongs in the skill tree.
11. Add suggested lenses only when useful. They are author-facing candidates; the platform does not import them automatically. The module explicitly determines which teaching lenses appear before the LO test.
12. Add the LO to the right module or submodule. Run `validate_content` with `accept_drafts: true`.
13. Spawn every validation agent below with its exact instructions, the LO file, its module, its teaching lenses and sources, and the course context. Each agent judges independently and never edits.
14. Fix every failure. Spawn fresh versions of failed agents. Repeat until all checks pass. Report iteration count and failures to the user.

## Validation instructions

Give every agent:

- Learning-outcome file.
- Module or submodule that imports it.
- Teaching lenses, readings, and other source material for that unit.
- Course file and intended audience.
- Instruction to judge only, report evidence, and never edit.

A check passes only when agent can point to evidence. Reports must include verdict, shortest supporting quote, problem, and smallest useful fix. Uncertainty without evidence is not failure unless check explicitly says otherwise.

### Agent 1: Outcome type, value, and learner agency

Check whether file defines right kind of outcome and whether capability is worth teaching.

1. Learning outcome is something learner can do after instruction. It is not:
   - a topic;
   - instructor objective;
   - activity such as reading a chapter;
   - reading takeaway;
   - artifact produced;
   - action taken;
   - disposition, feeling, motivation, or value;
   - downstream impact.
2. Capability matters outside course. It supports real work, advanced learning, sound judgment, or useful contribution.
3. Ask: could someone understand more advanced version without this capability? If yes, challenge whether this LO is genuinely prerequisite or important.
4. Outcome does not evaluate learner values, agreement, motivation, belonging, or willingness to act. Different conclusion is compatible with strong performance when reasoning is strong.
5. Design supports autonomy and competence. It explains real problem, permits legitimate disagreement and alternative approaches, and does not use guilt, fear, status pressure, or conformity as evidence of learning.
6. Classify alternatives correctly:
   - Artifact: learner produces something, such as contribution plan.
   - Action: learner does something beyond assessment, such as discusses plan with practitioners.
   - Disposition: aggregate program-evaluation measure such as motivation or agency, never individual certification criterion.
   - Downstream impact: later real-world effect.
7. Use these frameworks only as background principles, not learner pass criteria: Self-Determination Theory distinguishes autonomy, competence, and relatedness; UNESCO distinguishes cognitive, socio-emotional, and behavioural outcomes; OECD distinguishes knowledge, skills, attitudes, values, and agency.

Pass only if file contains one worthwhile learning capability and does not smuggle another outcome type into learner assessment.

### Agent 2: Statement quality

Read and apply authoritative eval standards:

- [[Evals/Learning Outcome Evals/A1 - Concrete capability]]
- [[Evals/Learning Outcome Evals/A2 - Source-bound statement]]
- [[Evals/Learning Outcome Evals/A3 - Single completion unit]]

Judge only `learning-outcome:`.

Report A1, A2, and A3 separately.

- A1: Does statement name observable capability precisely enough to imagine test and recognize strong demonstration?
- A2: Would capability make sense to someone who learned material elsewhere, without knowing specific source or author?
- A3: Is statement one completion unit rather than bundle learner could independently have or lack?

Long or multi-clause statement may pass when clauses elaborate one integrated capability. Multiple test questions are fine when they measure one outcome.

### Agent 3: Test validity

Read and apply [[Evals/Learning Outcome Evals/B1 - Answerable without the text]] to every test question. B1 fails if any question fails.

Also check:

1. Question tests declared outcome, including every load-bearing part, and does not test unrelated skill.
2. Question is self-contained enough to ask months later without course or reading open.
3. Question tests object, mechanism, or judgment rather than memory of text.
4. Question does not reveal its own answer through setup, leading wording, or enumerated hints.
5. Fluent generic prose without target capability cannot earn strong score.
6. Learner who understands argument but disagrees can answer well.
7. Where topic has causal, mathematical, threshold, interaction, or non-linear structure, question makes that structure do work rather than asking decorative explanation.
8. Question type fits task. Use recall when recall itself matters; unfamiliar application for transfer; comparison for distinctions; roleplay for interactive performance.
9. One integrated question is preferred. Every additional question provides distinct evidence and still measures same indivisible skill.
10. Test question is not merely practice prompt. Good test checks performance without tutor scaffolding; practice may guide, hint, and teach.

Report B1 plus separate test-validity verdict.

### Agent 4: Rubric-question alignment

Read and apply [[Evals/Learning Outcome Evals/C2 - No unasked demands]] to every rubric. C2 fails if any rubric fails.

Check exact direction:

`pass-bar or strong-score requirements <= what question asks explicitly or clearly implies`

1. Learner who answers everything question requests can earn strong score.
2. Rubric does not require hidden facts, examples, quantities, named frameworks, or argument steps question never signals.
3. Question may ask for more than minimum strong-score evidence; headroom is allowed.
4. Every rubric requirement relates to declared LO.
5. Every question demand is either graded or explicitly marked non-gating.
6. If item has no `assessment-instructions::` or other valid grading mechanism, fail as no rubric.

Report C2 and quote each hidden demand.

### Agent 5: Rubric truth and concept boundaries

Read and apply [[Evals/Learning Outcome Evals/C3 - Concept boundaries]] to every rubric. C3 fails if any rubric fails.

Also check:

1. Every criterion states idea that must be conveyed in any wording.
2. Specific phrase, analogy, example, author, or number is illustrative, not required, unless recall of that item is declared capability and question asks for it.
3. Every criterion is literally true. Test counterexamples and edge cases.
4. Strong, partial, and weak performance are distinguishable enough for defensible 0 to 100 score.
5. Load-bearing criteria are identified. Rubric does not let polished but empty answer score highly.
6. Legitimate alternative reasoning, equivalent terminology, and justified disagreement are accepted.
7. Rubric does not penalize learner for correcting false premise or noticing flaw in expected answer.
8. Assessment brief contains grading rules only. Tone, praise, tutoring, and improvement advice belong in `feedback-instructions::`.
9. Feedback brief, when present, tells tutor to name strongest part and highest-value improvement without changing score.

Report C3 plus separate rubric-quality verdict.

### Agent 6: Teaching and test alignment

Read module, lenses, readings, LO statement, question, and rubric together.

1. Module teaches every concept and reasoning move rubric grades.
2. Learner practises capability before test and receives feedback.
3. Practice matches skill but does not copy test answer.
4. Test is not first time learner performs capability.
5. Reading is selected to teach outcome. Outcome was not reverse-engineered from convenient reading takeaway.
6. Claims and numbers taught as required knowledge are grounded in source or explicit Lens view.
7. Rubric never makes unsupported claim authoritative.
8. Suggested lenses are useful candidates, but module itself includes actual teaching sequence.
9. No promise is dropped between stages: baseline, prediction, decomposition, or artifact elicited in practice is used later when design says it will be.
10. Cognitive load fits intended audience and declared stage.

Fail if test demands capability teaching sequence does not prepare learner to demonstrate.

### Agent 7: File and platform correctness

Check current Lens syntax and behavior, using [[Course Authoring]] and [[../Lenses/Response to question segments]] as authoritative references.

1. File is in `Lens Edu/Learning Outcomes/`.
2. Filename is unique, course-independent noun phrase, 2 to 6 words, sentence case, no course prefix.
3. Frontmatter has quoted stable UUID `id` and non-empty `learning-outcome`.
4. Test has its own UUID `id::`.
5. Every response segment has unique UUID `id::`.
6. Published IDs are unchanged.
7. Test contains only gradable questions or roleplays. No Text, Chat, Article, Video, Rating, ungraded response, or bare legacy Question.
8. Every Open and Ranking item has `assessment-instructions::`; Choice has at least one `[x]`; FillBlank has at least one graded blank; Roleplay is gradable.
9. Question fields and syntax match canonical response-segment reference.
10. `domain:`, `stage:`, and `requires:` are valid when present. Prerequisites are sparse and genuine because they gate locked status.
11. Suggested lenses use relative wikilinks and are clearly author-facing.
12. Module imports LO in intended module/submodule and places teaching lenses before generated test.
13. Draft uses `wip`; production module does not reference wip LO.
14. `validate_content` with `accept_drafts: true` has no production-category errors in touched files.
15. Platform semantics are not misrepresented: item scores are separate; completion is not LO mastery or pass/fail.

Report every syntax or integration failure with file and line.

### Agent 8: Adversarial final review

Read all materials fresh. Do not rely on other agents' reports.

1. Attempt test as smart, fluent learner who skipped teaching material. If generic writing can earn strong score, fail.
2. Attempt test as expert who disagrees with source. If rubric punishes justified disagreement, fail.
3. Attempt test as learner who knows capability but never read assigned source. If source-specific wording blocks them, fail.
4. Try to satisfy one clause of LO while failing another. If realistic, fail single-unit design.
5. Try to answer question completely while omitting each rubric requirement in turn. Any unasked requirement fails.
6. Try alternative terminology, analogy, and valid example. Rubric must accept concept-equivalent answer.
7. Check every number and mathematical claim by calculation or source. Check quantity meaning, not only digits.
8. Identify weakest link between outcome, teaching, question, rubric, and feedback.
9. Report exact counterexample for every failure. A review saying only that work is good does not pass.

Pass only if no concrete counterexample exposes mismatch.

## Completion report

When all agents pass, report:

- LO file and module.
- Number of test items.
- Iterations per agent.
- Every failure found and fixed.
- Validator result.
- Remaining human decisions.
