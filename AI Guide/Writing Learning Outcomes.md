---
tags:
  - validator-ignore
---
# Writing Learning Outcomes (AI Guide)

How to write the outcome itself — what it says, how it's scoped, how you know it's good. For file syntax (frontmatter, `## Test:`, `# Suggested Lenses:`) read `Lens Edu/AI Guide/Element Reference.md`; for the 1–5 rubric pattern read `Lens Edu/AI Guide/Quality Patterns.md`. Canonical example: `Lens Edu/Learning Outcomes/Indifference, not malice.md`.

## What a learning outcome is (and isn't)

A learning outcome is **one testable skill**: something the student can *do* after the content, phrased so you can check whether they can do it. The file holds two things — the outcome statement (frontmatter `learning-outcome:`) and the test that verifies it (`## Test:`). If you can't imagine the test, you don't have an outcome yet.

Things that are **not** learning outcomes:

- **A topic.** "Feedback loops are accelerating civilization" names an area of content; it doesn't say what the student can do with it. Convert it: what question about this topic should the student be able to answer, and to what depth?
- **A learning objective.** The instructor's purpose for teaching ("get students engaged with AI safety") belongs to the theory of change. If it matters, find the observable behavior that would show it happened and write *that* as the outcome.
- **An activity.** "Read chapter 3" is what the student does on the way, not what they can do afterwards.

## Writing the statement

1. **Start with an action verb.** Explain, Distinguish, Identify, Compare, Analyze, Evaluate, Apply, Recognize. Avoid "understand", "know", "appreciate", "be familiar with" — you can't tell from the outside whether someone understands; you can tell whether they can explain.
2. **Name the mechanism, not just the claim.** "Explain why misaligned AI is dangerous" is weak; "Explain why a capable AI optimizing for resource-intensive goals can eliminate humanity *without hostile intent, as a byproduct of its own objectives*" pins the actual reasoning move the student must make. Precision beats brevity — a long statement that pins one skill exactly is better than a short vague one.
3. **Apply the two checks** (from *Design for How People Learn*, Julie Dirksen):
   - Is this something the learner would actually do in the real world (explain to a skeptic, evaluate a proposal, spot the flaw in an argument)?
   - Can I tell when they've done it?
4. **Converting source questions into outcomes:**

   | Question you started from | Outcome statement |
   |---------------------------|-------------------|
   | "How does X differ from Y?" | "Distinguish between X and Y" |
   | "What is the impact of Z?" | "Explain the impact of Z on..." |
   | "Why does A matter for B?" | "Explain why A is necessary for B" |

## Scope: one skill per file

One outcome = one testable skill. The tell that you have two: the level-3 row of your rubric needs an "and also" joining two claims that could be understood independently — split it. Depth is not a reason to split: levels 4–5 of the rubric hold the deeper connections, so one outcome can span beginner-to-deep on a single skill. Related outcomes at genuinely different levels (awareness → application → producing a plan) are separate outcome files, sequenced by the module.

## Write the rubric first

The 1–5 rubric (every level with a verbatim example answer — structure in `Quality Patterns.md`) is the outcome's operational definition. Write it immediately after the statement, **before** designing lenses: level 3 is the pass bar (the mechanism correctly explained), levels 1–2 name the failure modes the lenses must head off, levels 4–5 name the depth the best lenses can reach for. If you can't write distinct level-1, level-3, and level-5 example answers, the outcome is too vague or too big — fix the statement, not the rubric.

## Edge cases

- **Artifact and state outcomes.** Some outcomes ask the student to produce something (a personal action plan) or to reach a state (motivated to contribute) rather than demonstrate a skill. The verb-and-mechanism guidance above partially breaks down there; keep the testability core: define what observable output or expressed state counts as achieved, and write the test against that.
- **No `add_to_ai_context` on an outcome** — it's a validation error; put source material on the lens, module, or submodule marker.
- **Never change the id of a published outcome** — learner progress is keyed on it (see `Course Authoring.md`).
