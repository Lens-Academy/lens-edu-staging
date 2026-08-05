---
tags:
  - validator-ignore
---
# Writing Learning Outcomes (AI Guide)

Strong existing examples: `Lens Edu/Learning Outcomes/Intelligence as prediction plus steering.md`, `Lens Edu/Learning Outcomes/Hard calls vs. easy calls.md`.

## What a learning outcome is (and isn't)

A learning outcome is **one testable skill**: something the student can *do* after the content, phrased so you can check whether they can do it. The file holds two things: the outcome statement (frontmatter `learning-outcome:`) and the test that verifies it (`## Test:`). If you can't imagine the test, you don't have an outcome yet.

Things that are **not** learning outcomes:

- **A topic.** "Feedback loops are accelerating civilization" names an area of content; it doesn't say what the student can do with it. Convert it: what question about this topic should the student be able to answer, and to what depth?
- **A learning objective.** The instructor's purpose for teaching ("get students engaged with AI safety") belongs to the theory of change. If it matters, find the observable behavior that would show it happened and write *that* as the outcome.
- **An activity.** "Read chapter 3" is what the student does on the way, not what they can do afterwards.
- **A reading's takeaway.** An outcome reverse-engineered from an assigned text ("understands what chapter 2 argues") is a comprehension check, not a skill (see the next section).

## Where outcomes come from

Work backward from real-world performance, never forward from content:

1. Start from what someone contributing to AI safety must be able to do: the skill-tree topic or the contribution-role requirement the course serves.
2. Write the outcome statement, then its test, then the practice that prepares for the test.
3. Only then pick or commission the readings and lenses. They are teaching routes to the outcome, chosen for it, not the source of it.

The inversion check: if you are holding a reading and asking "what outcome fits this?", you are inverted. Write the capability first, then judge whether that reading actually teaches it.

## Writing the statement

1. **Start with an action verb.** Explain, Distinguish, Identify, Compare, Analyze, Evaluate, Apply, Recognize. Avoid "understand", "know", "appreciate", "be familiar with": you can't tell from the outside whether someone understands; you can tell whether they can explain.
2. **Name the mechanism, not just the claim.** "Explain why misaligned AI is dangerous" is weak; "Explain why a capable AI optimizing for resource-intensive goals can eliminate humanity *without hostile intent, as a byproduct of its own objectives*" pins the actual reasoning move the student must make. Precision beats brevity. The strongest form is situated: "Given ⟨an unfamiliar case⟩, the learner can ⟨do X⟩, identify the assumptions required, and name a case where it does not apply."
3. **Apply the checks:**
   - Is this something the learner would actually do in the real world (explain to a skeptic, evaluate a proposal, spot the flaw in an argument)?
   - Can I tell when they've done it?
   - Could someone become proficient at this without practice? If not, the lenses must contain practice with feedback, not just reading.

## Scope: one skill per file

One outcome = one testable skill. The tell that you have two: describing a passing answer needs an "and also" joining two claims that could be understood independently. Split it. An outcome is one pass/fail completion unit. Genuinely deeper capability on the same topic is a separate leveled outcome file ("⟨Topic⟩ Level 2"), not levels 4 and 5 of the same rubric; rubric levels above the pass bar calibrate feedback, they don't credential extra depth. Related outcomes at different levels (awareness → application → producing a plan) are separate files, sequenced by the module.

## Write the rubric first

The 1–5 rubric is the outcome's operational definition: the test question's `assessment-instructions::` hold a 5-level rubric where **every level has a verbatim example answer**:

```
**1**: <failure mode>. *Example: "<what a level-1 answer sounds like>"*
**2**: <partial understanding>. *Example: "..."*
**3**: <correct mechanism, the pass bar>. *Example: "..."*
**4**: As above, plus <structural implication>. *Example: Adds "..."*
**5**: As above, plus <deepest connection>. *Example: Adds "..."*
```

Levels 4 and 5 are written as "As above, plus…" so graders compose rather than re-judge. Write it before designing lenses: level 3 is the pass bar, levels 1 and 2 name the failure modes the lenses must head off, levels 4 and 5 name the depth the best lenses can reach for. If you can't write distinct level-1, level-3, and level-5 example answers, the outcome is too vague or too big. Fix the statement, not the rubric.

## Make the test valid

The dominant defects in existing outcomes are recall tests and leading prompts. Avoid both:

- **Require transfer at the pass bar.** The test presents an unfamiliar case or application. An answer that only reconstructs the source's argument is a level-2 answer, not a pass.
- **Don't teach the answer in the stem.** If the question restates the argument before asking about it, it tests reading the stem, not the capability.
- **Grade reasoning, not agreement.** A learner who understands the argument and disagrees well passes. Assess whether they can reconstruct, evaluate, and respond to the argument, never whether they accept its conclusion.

## File syntax

The filename is the learner-visible skill name (modules and the skill tree display {--{"author":"Elias's AI","timestamp":1785958733701}@@it): name it like--}{++{"author":"Elias's AI","timestamp":1785958733701}@@it). Conventions (settled in `Lens/Learning Outcome Short-Name Proposal.md`):++} a {--{"author":"Elias's AI","timestamp":1785958733701}@@capability, short ("Goodharting Level 1"),--}{++{"author":"Elias's AI","timestamp":1785958733701}@@short noun phrase, 2 to 6 words, sentence case; the verb lives in the outcome statement,++} not {--{"author":"Elias's AI","timestamp":1785958733701}@@like an essay or chapter title.--}{++{"author":"Elias's AI","timestamp":1785958733701}@@the title; no course prefixes (outcomes are course-agnostic); unique across the folder.++}

```markdown
---
id: <uuid>
learning-outcome: <the statement>
---
## Test:
id:: <uuid>
#### Question
content:: <the test question>
assessment-instructions:: <the 1–5 rubric (see above)>

# Suggested Lenses:
## Lens:
source:: [[../Lenses/My Topic - PQ]]
notes:: <optional author note about this suggestion>

## Lens:
source:: [[../Lenses/My Topic]]
```

- A Test may only contain question/roleplay segments; anything else is flagged and would be silently dropped. Their field syntax: `Lens Edu/AI Guide/Writing Lenses.md` ("The 6 segment types").
- Suggested lenses are **author-facing candidates only**: the platform never imports them; the module lists its teaching lenses explicitly, before the `# Learning Outcome:` ref. Zero-suggestion outcomes are valid.

## {--{"author":"Elias's AI","timestamp":1785944825813}@@Artifact and state outcomes

Some outcomes ask the student to produce something --}{++{"author":"Elias's AI","timestamp":1785944825813}@@Outcome types

An outcome file holds a **capability**: a demonstrable skill. Other things a course targets are not capability outcomes:

- **Artifacts** ++}(a personal action plan) and **actions** (discussed the plan with a practitioner) are milestones: verify that the thing exists or {--{"author":"Elias's AI","timestamp":1785944825813}@@to reach--}{++{"author":"Elias's AI","timestamp":1785944825813}@@happened against explicit criteria. Completing one doesn't establish++} a {--{"author":"Elias's AI","timestamp":1785944825813}@@state--}{++{"author":"Elias's AI","timestamp":1785944825813}@@transferable skill.
- **Dispositions**++} (motivated to {--{"author":"Elias's AI","timestamp":1785944825813}@@contribute) rather than demonstrate a skill. The verb-and-mechanism guidance above partially breaks down there; keep the testability core: define what observable output or expressed state counts--}{++{"author":"Elias's AI","timestamp":1785944825813}@@contribute, changed beliefs) are never pass/fail and never get an outcome file. A learner who reasons well and still disagrees, or stays unenthusiastic, has not failed anything. Treat dispositions++} as internal design targets, measured (if at all) by aggregate self-report.
- **Impact** (a sustained contribution to the {--{"author":"Elias's AI","timestamp":1785944825813}@@test against that.--}{++{"author":"Elias's AI","timestamp":1785944825813}@@field) is program-level evaluation, not a course outcome.++}

