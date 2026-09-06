---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# AIRF Restructure: change log and plan

Git records what changed. This file records why, what it depended on, and what we decided against. Update it in the same commit as the change it describes.

**Status key:** `todo`, `drafted`, `in progress`, `done`, `blocked`, `parked`.

---

## 1. Decisions already taken

Recorded so they do not get re-argued. Each entry is the decision, then the reason, then what it commits us to.

**Part I splits 3 and 3, with the Introduction pulled out.** U1 becomes chapters 1 to 3, U2 becomes chapters 4 to 6, and the Introduction moves to its own section using `intro-form`, as in [[modules/XLab Verification Overview]]. Week one's reading is Introduction plus chapters 1 to 3. Reason: chapter 6 currently sits in the unit that also carries the film, which is the only unit whose bracket does not fall inside one part of the book. Refolding chapter 6 into U2 fixes that and reunites it with chapter 5. The alternative, chapters 1 to 4 in week one, front-loads the densest reading onto learners who have not yet attended a session, which matters more in the intensive format where sessions run back to back. Cost: chapters 3 and 4 get split, which is the tightest pair in Part I.

**Chapter 9 returns as a reading.** The film covers chapters 7 and 8 only, so under the current structure the scenario stops before Ascension. Reason: chapter 9 is not extra stakes on top of the argument, it is where the chapter 1 claim about steering the future gets cashed out with no ceiling. Cost: one new reading and one new outcome in U3.

**Instrumental convergence becomes required, at the top of U3.** Pairs the chapter 4 extension on terminal and instrumental goals with the chapter 5 extension on instrumental convergence. Reason: the passage is filed by the book as a chapter 5 extension, and it closes by routing the reader to chapter 6 for how an ASI would achieve its instrumental targets. Read before chapter 6 that pointer is a forward reference into unread material; read after, it resolves backwards. Placing it at the head of U3 also means the film then confirms a prediction the learner has already been given. Cost: material currently optional under chapters 6 and 8 becomes required, and either moves or appears twice.

**Recall prompts, not cross-references.** Ten threads, listed in [[Lenses/DRAFT - Recall Threads Proposal]]. The learner-facing prompt names nothing; the answer key lives in `assessment-instructions`. Reason: telling someone which principle applies removes the work that makes it stick.

**A prompt needs an outcome anchor at both ends.** A chapter-to-chapter link with no outcome at the earlier end is a proposal for a new outcome, not a prompt. Within-unit links are prerequisites and get no prompt, since sequential reading already carries them.

**Threads we dropped.** Coda into chapter 13, dropped on a closer reading of what the Coda claims. Chapter 6 into chapter 12 on irreversibility, left untethered because chapter 6 has no outcome to anchor it and chapter 10 already carries that ground. *Fiction as argument* receives nothing, because it synthesises Part I rather than resting on any single piece of it.

---

## 2. Decisions resolved on greenlight

| Decision | Resolution |
|---|---|
| 2026-08-24 fix-pass suggestions | **Ignore.** Not ours to resolve. The draft was reviewed and approved on its own terms |
| Cohort mid-flight | **Not a blocker.** A cohort is running, but nothing here goes live until it completes. Published ids must not change once it does |
| Where U2 splits | **It does not.** U2 is chapters 4 to 6 in one module |
| Module numbering | M1 becomes the Introduction alone; M2 and M3 become Nonhuman Minds parts 1 and 2. So **M1 = Introduction, M2 = chapters 1 to 3 (U1), M3 = chapters 4 to 6 (U2), M4 = U3, M5 = U4, M6 and M7 = U5** |
| Extension readings move or duplicate | **Duplicate, framed as "if you haven't already read".** Having read something before is not the same as having been tested on it or asked to explore it |
| Assessment load | **Fine.** Each recall moment runs a couple of turns, and the proposal was approved with them in |
| Welcome lenses | **Replace.** See section 5 |

Nothing is blocking. Section 8 holds the dependency scan, which raises decisions to take as each file is touched rather than up front.

---

## 3. File inventory

### Stage 0, preconditions

| File | Change | Status |
|---|---|---|
| 2026-08-24 fix pass, 46 outcome files | Accept or reject pending suggestions | `todo` |
| [[courses/AI Risk Fundamentals]] | Fix the `%%` block labelled "comment from student", which is facilitator-side analysis mislabelled as learner evidence | `todo` |

### Stage 1, structure

| File | Change | Status |
|---|---|---|
| [[courses/AI Risk Fundamentals]] | New unit boundaries, add intro module, add resources module | `todo` |
| New intro module | `intro-form`, carries the Introduction and *Hard calls vs. easy calls* | `todo` |
| [[modules/IABIED M1 Intro and Nonhuman Minds, Part 1]] | Introduction out, chapter 3 in | `todo` |
| [[modules/IABIED M2 Nonhuman Minds, Part 2]] | Rebalance against the U2 split decision | `todo` |
| [[modules/IABIED M3 Nonhuman Minds, Part 3]] | Chapter 6 in | `todo` |
| [[modules/IABIED M4 One Extinction Scenario]] | Chapter 6 out, U3 opener and chapter 9 in | `todo` |
| [[modules/IABIED M5 Facing The Challenge, Part 1]] | No structural change | `todo` |
| [[modules/IABIED M6 Facing The Challenge, Part 2]] | No structural change | `todo` |
| [[modules/IABIED M7 What Happens Next]] | No structural change | `todo` |

### Stage 2, new content

| File | Change | Status |
|---|---|---|
| New U3 opener lens | Pairs the chapter 4 and 5 extensions, carries two incoming threads | `todo` |
| [[Lenses/DRAFT - Ch9 Cosmic Stakes (from film lens)]] | Fill the TODOs against chapter 9, promote | `drafted` |
| [[Learning Outcomes/DRAFT - Cosmic stakes]] | Verify rubric against chapter 9, promote | `drafted` |
| [[Learning Outcomes/Instrumental sub-goal convergence]] | De-orphan, rewrite the test to pass B1 | `todo` |
| [[Learning Outcomes/Goals and instrumental convergence]] | Check against the above, decide which is used | `todo` |
| [[Learning Outcomes/The core extinction argument]] | `requires` points at *Why we'd lose*, which this course never teaches. Repoint at the chapter 6 pair. Test block is empty | `todo` |
| [[Lenses/IABIED - One Extinction Scenario (Video)]] | Flip the objection test: the brief currently names the three mechanisms to the tutor, the learner should name them | `todo` |

### Stage 3, recall segments

One added phase per lens. Two lenses carry two threads each.

| Lens | Threads landing here | Status |
|---|---|---|
| New U3 opener | Intro hard vs. easy calls; Ch 5 goal-space | `todo` |
| [[Lenses/DRAFT - Ch9 Cosmic Stakes (from film lens)]] | Ch 5 hostile vs. indifferent | `drafted` |
| [[Lenses/IABIED - Path Prediction vs Outcome Prediction]] | Intro hard vs. easy calls | `todo` |
| [[Lenses/DRAFT - Ch4 with Reach-Back]] | Ch 2 behavior vs. values | `drafted` |
| [[Lenses/IABIED - Alchemy Not Science]] | Ch 2 grown not crafted; Ch 3 wanting emerges | `todo` |
| [[Lenses/IABIED - Define the Aztec Warrior Analogy]] | Ch 1 prediction plus steering | `todo` |
| [[Lenses/IABIED - The Five Engineering Curses]] | Ch 1 machine advantages, via the curse of speed | `todo` |
| [[Lenses/IABIED - The One-Chance Problem]] | Ch 10 five curses, via Chernobyl appearing twice | `todo` |

All eight run the same `Reading Assignment`, `Phase 1: Recall`, `Phase 2: Processing`, `Phase 3: Learning Question` shape, so the insert is identical in each: a new phase before the learning question, and the learning question renumbered.

### Stage 4, welcomes

| File | Change | Status |
|---|---|---|
| [[Lenses/IABIED - M4 Welcome]] | Stale. Its hidden `#### Chat` segment still briefs the tutor as though the student read chapters 7, 8, 9 and the Coda | `blocked` on the section 5 decision |
| [[Lenses/IABIED - M5 Welcome]] | Same decision | `blocked` |
| Modules without a welcome lens | Same decision | `blocked` |

### Stage 5, resources

| File | Change | Status |
|---|---|---|
| New resources module | Sits outside the unit sequence | `todo` |
| Glossary | Last. New keywords from stages 2 and 3 would otherwise conflict | `todo` |
| Companion pieces | Not yet scoped | `todo` |
| Extended readings | Not yet scoped | `todo` |

---

## 4. Order, and why

**Stage 0 before anything.** Every recall prompt terminates on an outcome. If the pending fix-pass repairs are still unaccepted, we would be building on text-scaffolded questions and then rebuilding.

**Structure before content.** Moving a chapter between modules changes which lenses are in scope. Writing recall segments first would mean rewriting them.

**New content before recall segments.** Two of the ten threads terminate on outcomes that do not exist yet, both in U3.

**Welcomes after structure.** A welcome that previews a unit cannot be written until the unit's contents are settled, and three of five units change.

**Glossary last.** Stages 2 and 3 introduce new terms. A glossary written first would need reconciling against them.

---

## 5. The welcome lens question

**Corrected inventory.** My first pass found two welcome lenses and concluded from that. A fuller search found four different patterns across seven modules, which is a stronger case than the one I made.

| Module | Pattern |
|---|---|
| M1 | Inline lens, id `c9e0e94a`. Not a module welcome at all: it is a **course** orientation, with tldr "Welcome to the book club", explaining the five units, the reading load and the Discord cohorts |
| M3 | Inline `# Submodule: Part 3 Welcome` wrapping `# Lens: Part 3 Welcome`, id `caf48b0b`. The only one using a Submodule wrapper |
| M4 | Standalone lens file [[Lenses/IABIED - M4 Welcome]] |
| M5 | Standalone lens file [[Lenses/IABIED - M5 Welcome]] |
| M2, M6, M7 | No welcome-named opener found. Confirm before stage 4 |

So four patterns: a course orientation living inside a module, a Submodule-wrapped inline lens, two standalone files, and three modules with nothing. That is the staggering.

**Two of them are already wrong, in different ways.**

M4's is stale. Its visible learner text is one paragraph; below it a `%%` block holds a pedagogical note and a whole `#### Chat` segment briefing the tutor on Sable's weight-stealing and the virus cover story, and listing this week's reading as chapters 7, 8, 9 and the Coda. That predates the film replacement.

M3's is the overhang, written down. Its visible text ends "can't we just stop it? That's where the next module begins", and its `summary_for_tutor` states that chapter 6 now opens the next module where it sets up the film. Both become false the moment chapter 6 refolds into U2. This is the clearest single artefact of the structural problem the restructure exists to fix, and it has to be rewritten regardless of what we decide about welcomes generally.

**Recommendation, unchanged but better supported: retire the standalone files and replace with two things.**

A course-level overview in the new M1, modelled on [[modules/XLab Verification Overview]]: a "what this course is about" section, then one `:::callout` per unit. M1's existing orientation lens is already most of this and should move into it rather than be rewritten from scratch. Note that its stated reading load per unit changes under the restructure.

Then a short inline welcome in each module, in the AIV style: `# Lens: Welcome` with `tldr::`, `summary_for_tutor::` and two or three sentences. Inline is the load-bearing part. Both of the drifted welcomes are the ones that live in their own files or their own wrapper.

**The argument against.** A course overview is read once and a learner arriving at unit 4 will not go back to it. That is what the inline welcomes are for, which is why the recommendation is both rather than either.

---

## 8. Second-order dependencies

Found by scanning for phrasing that assumes the current structure. The guess that learning outcomes would be independent turns out to be wrong: several bake in course-internal module labels.

### Breaks under the restructure

| File | What breaks | Fix |
|---|---|---|
| [[modules/IABIED M3 Nonhuman Minds, Part 3]], Part 3 Welcome | Visible text hands chapter 6 to the next module; `summary_for_tutor` says the same | Rewrite. Chapter 6 is now in this unit |
| [[Learning Outcomes/Fiction as argument, not prediction]] | Rubric level 5 requires "M4's emotional work" and that "Chapters 7–9 already made the dynamics feel real". Chapter 9 is now read, not felt through the film | Rewrite level 5. Already flagged C3 in the 2026-08-24 run for the same text |
| [[Lenses/IABIED - One Extinction Scenario (Video)]] | States it replaces chapters 7 to 9 | Change to 7 and 8 |
| [[Lenses/IABIED - M4 Welcome]] | Reading list and hidden Chat segment assume chapters 7 to 9 plus Coda | Superseded by the section 5 decision |
| M1 orientation lens | States the per-unit reading load and that one unit is mostly a film | Move to the new M1 and restate |
| [[Lenses/IABIED - Overview of Optional Resources M1]], [[Lenses/IABIED - Overview of Optional Resources M4]], [[Lenses/IABIED - Overview of Optional Resources M5]] | Module numbers in the **filenames**. Under the renumbering, "M1" content becomes M2 | Rename, and check every inbound link. Renaming is the riskiest edit in the plan |

### Pre-existing, not caused by us

| File | Issue |
|---|---|
| [[Learning Outcomes/Indifference, not malice]] | The statement, the test question and rubric level 3 all reference "the M3 goal-space argument". Three course-internal labels in one outcome, and the outcome is used by other courses whose M3 is different material |
| [[Learning Outcomes/Instrumental sub-goal convergence]] | Same problem: the statement references "the M3 argument". Relevant to us because this is the outcome we are importing into U3 |
| [[Learning Outcomes/Goal conflict as a physical fact]] | A chapter 7 outcome, not used by this course. Worth a look when U3 is rebuilt, since chapter 7 currently carries nothing here |

**The general lesson for stage 3.** Outcomes are shared across courses, so a module label inside an outcome is a landmine: it resolves differently depending on which course imported it. Any outcome we touch should have module and chapter labels stripped rather than updated. That is the same thing B1 asks for, arrived at from a different direction.

---

## 6. Testing

Before review, run at least one live pass through:

- The chapter 4 connection beat, checking specifically that the tutor does not supply the answer on the first turn. That failure turns the prompt into a cross-reference with extra steps.
- The chapter 9 pair, checking that the pre-reading prediction is not graded or hinted at, and that the closing comparison actually returns to what the learner wrote.
- The flipped film objection test.
- `validate_content` on the course after each stage, not only at the end.

## 7. Log

| Date | Change | Files | Why |
|---|---|---|---|
| | | | |
