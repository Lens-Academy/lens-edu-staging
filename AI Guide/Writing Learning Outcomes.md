---
tags:
  - validator-ignore
---
# Writing Learning Outcomes (AI Guide)

Luc's additions 6 august:

Best practices:
...


Our design pattern:
- learning outcomes are binary tests. Maybe build up of subjudgements, e.g. "answer should pass on 3 out of these 5 criteria"
- 


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
   - Could someone become proficient at this without practice? If not, the lenses must contain practice with feedback, not just reading.{>>{"author":"Luc","timestamp":1785962350939}@@I know what book this comes from, and I think it's potentially good, but it requires more context if we want to use it here<<}{>>{"author":"Luc","timestamp":1785962402275}@@btw, relatedly, I suggest maybe not calling outcomes "skills". Bcs that book defines skills as the thing that require practice beyond just gaining knowledge<<}

## Scope: one skill per file

One outcome = one testable skill. The tell that you have two: describing a passing answer needs an "and also" joining two claims that could be understood independently. Split it. An outcome is one pass/fail completion unit. Genuinely deeper capability on the same topic is a separate leveled outcome file ("⟨Topic⟩ Level 2"); rubric levels above the pass bar calibrate feedback, they don't credential extra depth. Related outcomes at different levels (awareness → application → producing a plan) are separate files, sequenced by the module.

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
- **Grade reasoning, not agreement.** A learner who understands the argument and disagrees well passes. Assess whether they can reconstruct, evaluate, and respond to the argument, never whether they accept its conclusion.{++{"author":"Lauren's AI","timestamp":1786033405239}@@
- **Test the object, not the text.** The reading points at something (a mechanism, a distribution, a structural relationship). Test *that*, and prefer a case the readings do not contain. A question answerable by recalling the assigned text measures assignment completion. If the student can pass by remembering what an author said rather than by reasoning about the thing the author was describing, the question is wrong.
- **Test the shape of the possibility space, including non-linear structure.** Where a topic has mathematical structure, the question should make that structure do work: not only "what happens" but under what interactions, thresholds, and combinations. Non-linear interactions between parts of a system are the most commonly untested and the most load-bearing: a student who models a system as a sum of independent parts will get the qualitative answer wrong whenever feedback, saturation, or a threshold matters. Ask by-when and under-what-conditions questions, not only whether-and-why ones.

## Test before, then test again after

Test the same capability **twice**: once before the student reads anything, once afterwards.

The pre-reading test should go as deep as the student can currently manage. Its purpose is not assessment. A student who has committed to an answer reads differently: they have something at stake, and the reading either confirms or corrects a position they already hold. This is why `[episode]` material (an account of something that actually happened, with an outcome) is worth more than its length suggests, and it is why the pre-test must be scored generously; the student is *supposed* to be wrong, and telling them so up front removes the incentive to hedge.

The post-reading test must target the same capability while being **different enough that reproducing the reading does not answer it.** If a student can pass the second test by paraphrasing what they just read, the pair has measured nothing. The move required between the two should be qualitative generalisation, not restatement: a different domain, an inverted case, a condition where the mechanism does not hold, or a composition of two mechanisms the reading treated separately.

The failure this prevents is a course where students learn to recognise the assigned texts. That is a real failure mode and it is invisible from the inside: comprehension checks look like learning, and a class that has read carefully will pass them.++}

## File syntax

The filename is the learner-visible skill name (modules and the skill tree display it). Conventions (settled in `Lens/Learning Outcome Short-Name Proposal.md`): a short noun phrase, 2 to 6 words, sentence case; the verb lives in the outcome statement, not the title; no course prefixes (outcomes are course-agnostic); unique across the folder.

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
- Skill-tree frontmatter is rolling out per `Lens/Learning Outcome Domain and Stage Proposal.md`: `domain:` (one of the 15 domains in `Lens/AI Safety Skill Taxonomy - Canonical Working Inventory.md`), `stage:` (Beginner, Intermediate, or Advanced), `requires:` (sparse; only genuine prerequisites, since they gate locked status). Set them on new outcomes.

## Outcome types

An outcome file holds a **capability**: a demonstrable skill. Other things a course targets are not capability outcomes:

- **Artifacts** (a personal action plan) and **actions** (discussed the plan with a practitioner) are milestones: verify that the thing exists or happened against explicit criteria. Completing one doesn't establish a transferable skill.
- **Dispositions** (motivated to contribute, changed beliefs) are never pass/fail and never get an outcome file. A learner who reasons well and still disagrees, or stays unenthusiastic, has not failed anything. Treat dispositions as internal design targets, measured (if at all) by aggregate self-report.
- **Impact** (a sustained contribution to the field) is program-level evaluation, not a course outcome.

