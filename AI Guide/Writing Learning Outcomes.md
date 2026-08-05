---
tags:
  - validator-ignore
---
# Writing Learning Outcomes (AI Guide)

## What a learning outcome is (and isn't)

A learning outcome is **one testable skill**: something the student can *do* after the content, phrased so you can check whether they can do it. The file holds two things — the outcome statement (frontmatter `learning-outcome:`) and the test that verifies it (`## Test:`). If you can't imagine the test, you don't have an outcome yet.

Things that are **not** learning outcomes:

- **A topic.** "Feedback loops are accelerating civilization" names an area of content; it doesn't say what the student can do with it. Convert it: what question about this topic should the student be able to answer, and to what depth?
- **A learning objective.** The instructor's purpose for teaching ("get students engaged with AI safety") belongs to the theory of change. If it matters, find the observable behavior that would show it happened and write *that* as the outcome.
- **An activity.** "Read chapter 3" is what the student does on the way, not what they can do afterwards.
- **A reading's takeaway.** An outcome reverse-engineered from an assigned text ("understands what chapter 2 argues") is a comprehension check, not a {--{"author":"Elias's AI","timestamp":1785944823559}@@skill. Derive outcomes from first principles--}{++{"author":"Elias's AI","timestamp":1785944823559}@@skill++} — {--{"author":"Elias's AI","timestamp":1785944823559}@@what should--}{++{"author":"Elias's AI","timestamp":1785944823559}@@see++} the {--{"author":"Elias's AI","timestamp":1785944823559}@@learner be able to do or understand after the course? — then pick or write the content that teaches them, never the other way around.--}{++{"author":"Elias's AI","timestamp":1785944823559}@@next section.++}

## {++{"author":"Elias's AI","timestamp":1785944823929}@@Where outcomes come from

Work backward from real-world performance, never forward from content:

1. Start from what someone contributing to AI safety must be able to do — the skill-tree topic or the contribution-role requirement the course serves.
2. Write the outcome statement, then its test, then the practice that prepares for the test.
3. Only then pick or commission the readings and lenses. They are teaching routes to the outcome, chosen for it — not the source of it.

The inversion check: if you are holding a reading and asking "what outcome fits this?", you are inverted. Write the capability first, then judge whether that reading actually teaches it.

## ++}Writing the statement

1. **Start with an action verb.** Explain, Distinguish, Identify, Compare, Analyze, Evaluate, Apply, Recognize. Avoid "understand", "know", "appreciate", "be familiar with" — you can't tell from the outside whether someone understands; you can tell whether they can explain.
2. **Name the mechanism, not just the claim.** "Explain why misaligned AI is dangerous" is weak; "Explain why a capable AI optimizing for resource-intensive goals can eliminate humanity *without hostile intent, as a byproduct of its own objectives*" pins the actual reasoning move the student must make. Precision beats brevity — a long statement that pins one skill exactly is better than a short vague one.{++{"author":"Elias's AI","timestamp":1785944824258}@@ The strongest form is situated: "Given ⟨an unfamiliar case⟩, the learner can ⟨do X⟩, identify the assumptions required, and name a case where it does not apply."++}
3. **Apply the two checks** (from *Design for How People Learn*, Julie Dirksen):
   - Is this something the learner would actually do in the real world (explain to a skeptic, evaluate a proposal, spot the flaw in an argument)?
   - Can I tell when they've done it?{++{"author":"Elias's AI","timestamp":1785944824535}@@
   - Could someone become proficient at this without practice? If not, the lenses must contain practice with feedback, not just reading.++}

## Scope: one skill per file

One outcome = one testable skill. The tell that you have two: the level-3 row of your rubric needs an "and also" joining two claims that could be understood independently — split it. {--{"author":"Elias's AI","timestamp":1785944824838}@@Depth --}{++{"author":"Elias's AI","timestamp":1785944824838}@@An outcome ++}is {--{"author":"Elias's AI","timestamp":1785944824838}@@not --}{++{"author":"Elias's AI","timestamp":1785944824838}@@one pass/fail completion unit. Genuinely deeper capability on the same topic is ++}a {--{"author":"Elias's AI","timestamp":1785944824838}@@reason to split:--}{++{"author":"Elias's AI","timestamp":1785944824838}@@separate leveled outcome file ("⟨Topic⟩ Level 2"), not++} levels 4–5 of the {++{"author":"Elias's AI","timestamp":1785944824838}@@same ++}rubric {--{"author":"Elias's AI","timestamp":1785944824838}@@hold the deeper connections, so one outcome can span beginner-to-deep on a single skill.--}{++{"author":"Elias's AI","timestamp":1785944824838}@@— rubric levels above the pass bar calibrate feedback, they don't credential extra depth.++} Related outcomes at {--{"author":"Elias's AI","timestamp":1785944824838}@@genuinely --}different levels (awareness → application → producing a plan) are separate{--{"author":"Elias's AI","timestamp":1785944824838}@@ outcome--} files, sequenced by the module.

## Write the rubric first

The 1–5 rubric is the outcome's operational definition: the test question restates the outcome as a question, and its `assessment-instructions::` hold a 5-level rubric where **every level has a verbatim example answer**:

```
**1** — <failure mode>. *Example: "<what a level-1 answer sounds like>"*
**2** — <partial understanding>. *Example: "..."*
**3** — <correct mechanism, the pass bar>. *Example: "..."*
**4** — As above, plus <structural implication>. *Example: Adds "..."*
**5** — As above, plus <deepest connection>. *Example: Adds "..."*
```

Levels 4–5 are written as "As above, plus…" so graders compose rather than re-judge. Write the rubric immediately after the statement, **before** designing lenses: level 3 is the pass bar (the mechanism correctly explained), levels 1–2 name the failure modes the lenses must head off, levels 4–5 name the depth the best lenses can reach for. If you can't write distinct level-1, level-3, and level-5 example answers, the outcome is too vague or too big — fix the statement, not the rubric.

## {++{"author":"Elias's AI","timestamp":1785944825123}@@Make the test valid

The dominant defects in existing outcomes are recall tests and leading prompts — avoid both:

- **Require transfer at the pass bar.** The test presents an unfamiliar case or application. An answer that only reconstructs the source's argument is a level-2 answer, not a pass.
- **Don't teach the answer in the stem.** If the question restates the argument before asking about it, it tests reading the stem, not the capability.
- **Grade reasoning, not agreement.** A learner who understands the argument and disagrees well passes. Assess whether they can reconstruct, evaluate, and respond to the argument — never whether they accept its conclusion.

## ++}File syntax

{++{"author":"Elias's AI","timestamp":1785944825450}@@The filename is the learner-visible skill name (modules and the skill tree display it) — name it like a capability, short ("Goodharting Level 1"), not like an essay or chapter title. ++}Frontmatter: required `id`; optional `learning-outcome` (the statement), `discussion`, `tags`. Body = the test, then (optionally) suggested lenses:

```markdown
## Test:
id:: <uuid>
#### Question
content:: <the test question>
assessment-instructions:: <the 1–5 rubric — see above>

# Suggested Lenses:
## Lens:
source:: [[../Lenses/My Topic - PQ]]
notes:: <optional author note about this suggestion>

## Lens:
source:: [[../Lenses/My Topic]]
```

- A Test may only contain question/roleplay segments — anything else is flagged and would be silently dropped. Their field syntax: `Lens Edu/AI Guide/Writing Lenses.md` ("The 6 segment types").
- Suggested lenses are **author-facing candidates only** — the platform never imports them; the module lists its teaching lenses explicitly, before the `# Learning Outcome:` ref. Zero-suggestion outcomes are valid.

## Artifact and state outcomes

Some outcomes ask the student to produce something (a personal action plan) or to reach a state (motivated to contribute) rather than demonstrate a skill. The verb-and-mechanism guidance above partially breaks down there; keep the testability core: define what observable output or expressed state counts as achieved, and write the test against that.
