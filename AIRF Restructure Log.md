---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# AIRF Restructure: change log and plan

Git records what changed. This file records why, what it depended on, and what we decided against. Update it in the same commit as the change it describes.

**Status key:** `todo`, `drafted`, `in progress`, `done`, `blocked`, `parked`.

**Working practice.** Edits to files we did not write go in as suggestions for review, never as overwrites. New files we author can be written directly. Each entry in section 8 should say which of the two it was, so nothing lands silently.

**Prior art we cannot read.** There is an existing `Lens/base/IABIED/IABIED Course Build Notes` directory containing a module build algorithm, per-module decision logs, an example module file, and specs including one for a "Supplementary Resources Lens (the 'Overview of Optional Resources' Lens in the Dive Deeper submodule)". That last one bears directly on stage 5. The relay key cannot open any of it. Someone with access should check it before stage 5 is designed, so we follow the existing spec rather than reinvent it.

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

Nothing is blocking. Read section 3 before starting: its findings are folded into the stage tables in section 5, but the general lesson is not.

---

## 3. Dependency scan

Reference, not a stage. Done once, before execution. Found by scanning for phrasing that assumes the current structure. The guess that learning outcomes would be independent turns out to be wrong: several bake in course-internal module labels.

### Breaks under the restructure

| File | What breaks | Handled in |
|---|---|---|
| [[modules/IABIED M3 Nonhuman Minds, Part 3]], Part 3 Welcome | Visible text hands chapter 6 to the next module; `summary_for_tutor` says the same | Stage 1 and 4 |
| [[Learning Outcomes/Fiction as argument, not prediction]] | Rubric level 5 requires "M4's emotional work" and that "Chapters 7–9 already made the dynamics feel real". Chapter 9 is now read, not felt through the film. Already flagged C3 in the 2026-08-24 run | Stage 2 |
| [[Lenses/IABIED - One Extinction Scenario (Video)]] | States it replaces chapters 7 to 9. Should be 7 and 8 | Stage 2 |
| [[Lenses/IABIED - M4 Welcome]] | Reading list and hidden Chat segment assume chapters 7 to 9 plus Coda | Stage 4 |
| M1 orientation lens | States the per-unit reading load and that one unit is mostly a film | Stage 4 |
| Three `Overview of Optional Resources M1 / M4 / M5` lenses | Not a dependency after all. No live module references them; the only inbound links are from `Lens/Deprecated modules` and the IABIED build notes. Orphaned remnants | Archive, not rename |
| Module slugs `iabied-m1` to `iabied-m7` | Slugs carry module numbers. Renumbering makes each slug point at different content | Stage 1, first. See below |

### The slug problem, and why renaming does not solve it

To be clear about a phrase I used badly: slugs are not links the vault rewrites because internal references between files use wikilinks, not slugs. Slugs are for platform URLs. So this is the external-dependency case, not a permissions one. Editing the `slug:` field is easy; what is not easy is finding everything outside the vault holding the old value.

**And renaming them descriptively does not fix it.** `iabied-nonhuman-minds-2` would mean chapters 3 and 4 today and chapters 4 to 6 afterwards. That is the same silent remap with words instead of numbers. Since M2 and M3 merge and a new module appears at the front, there is no content-preserving mapping from old slugs to new ones under any naming scheme.

So the decision is not what to call them. It is whether an old slug should resolve to something or to nothing.

Recommendation: mint slugs that have never existed before, so an old link fails visibly rather than landing quietly on the wrong module. A dead link gets reported; a wrong one gets read. Whether the platform 404s or redirects on an unknown slug is a question for whoever owns it.

Either way this needs a comms pass over meeting docs, cohort materials and anywhere else a module URL was pasted. Log those as they are found.

### Pre-existing, not caused by us

| File | Issue |
|---|---|
| [[Learning Outcomes/Indifference, not malice]] | The statement, the test question and rubric level 3 all reference "the M3 goal-space argument". The outcome is used by other courses whose M3 is different material |
| [[Learning Outcomes/Instrumental sub-goal convergence]] | Same problem: the statement references "the M3 argument". Relevant because this is the outcome we are importing into U3 |
| [[Learning Outcomes/Goal conflict as a physical fact]] | A chapter 7 outcome, not used by this course. Worth a look when U3 is rebuilt, since chapter 7 currently carries nothing here |

**The general lesson.** Outcomes are shared across courses, so a module label inside an outcome resolves differently depending on which course imported it. Any outcome we touch should have module and chapter labels stripped rather than renumbered. That is what B1 asks for, arrived at from a different direction.

---

## 4. Order of execution

1. **Slugs and filenames first.** Both carry module numbers, and everything downstream should be edited against stable paths.
2. **Structure before content.** Moving a chapter between modules changes which lenses are in scope. Writing recall segments first would mean rewriting them.
3. **New content before recall segments.** Two of the ten threads terminate on outcomes that do not exist yet, both in U3.
4. **Welcomes after structure.** A welcome that previews a unit cannot be written until the unit's contents are settled, and three of five units change.
5. **Glossary last.** Stages 2 and 3 introduce new terms. A glossary written first would need reconciling against them.

This maps onto the stages in section 5 in order: stage 0, then 1, 2, 3, 4, 5.

---

## 5. File inventory

### Stage 0, preconditions

| File | Change | Status |
|---|---|---|
| [[courses/AI Risk Fundamentals]] | Fix the `%%` block labelled "comment from student", which is facilitator-side analysis mislabelled as learner evidence | `todo` |

### Stage 1, structure

Do the slug changes first, before any content edits (section 3).

| File | Change | Status |
|---|---|---|
| Module slugs, all seven | Mint new slugs. Do not reuse `iabied-m1` to `iabied-m7` under any scheme | `todo` |
| Three `IABIED - Overview of Optional Resources M1 / M4 / M5` lenses | Orphaned. Archive rather than carry them through the restructure | `todo` |
| [[courses/AI Risk Fundamentals]] | New unit boundaries, new module list, add intro module, add resources module | `todo` |
| New M1, Introduction | `intro-form`. Carries the Introduction, *Hard calls vs. easy calls*, and the course overview moved out of the old M1 | `todo` |
| [[modules/IABIED M1 Intro and Nonhuman Minds, Part 1]] | Becomes M2, Nonhuman Minds part 1. Introduction and orientation lens out, chapter 3 in | `todo` |
| [[modules/IABIED M2 Nonhuman Minds, Part 2]] | Merges into the new M3 | `todo` |
| [[modules/IABIED M3 Nonhuman Minds, Part 3]] | Becomes M3, Nonhuman Minds part 2, carrying chapters 4 to 6 | `todo` |
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

Every module already has a `# Submodule: Welcome`. The work is making its contents consistent, not adding the slot.

| File | Change | Status |
|---|---|---|
| New M1 | Receives the old M1 course orientation as a course overview, `:::callout` per unit, reading load restated | `todo` |
| M2 (old M1) | Inline welcome, now framing chapters 1 to 3 | `todo` |
| M3 | Rename the `Part 3 Welcome` wrapper to `Welcome`, rewrite for chapters 4 to 6. Currently hands chapter 6 to the next module | `todo` |
| M4 | Retire [[Lenses/IABIED - M4 Welcome]], replace inline. Stale reading list and hidden Chat segment go with it | `todo` |
| M5 | Retire [[Lenses/IABIED - M5 Welcome]], replace inline | `todo` |
| M6, M7 | Confirm M7, then bring both to the same shape | `todo` |

### Stage 5, resources

| File | Change | Status |
|---|---|---|
| New resources module | Sits outside the unit sequence | `todo` |
| Glossary | Last. New keywords from stages 2 and 3 would otherwise conflict | `todo` |
| Companion pieces | Not yet scoped | `todo` |
| Extended readings | Not yet scoped | `todo` |

---

## 6. Welcome lenses: the evidence behind the decision

**Corrected inventory, twice over.** My first pass found two welcome lenses. My second found four patterns. Both undercounted. Every IABIED module opens with a `# Submodule: Welcome` (M3's is `# Submodule: Part 3 Welcome`). The slot is uniform; what sits inside it is not.

| Module | What fills the Welcome submodule |
|---|---|
| M1 | An inline lens that is not a module welcome at all: a **course** orientation, tldr "Welcome to the book club", covering the five units, the reading load and the Discord cohorts |
| M2 | Inline lens |
| M3 | Inline lens, under a differently-named wrapper, `Part 3 Welcome` |
| M4 | `source::` pointing at the standalone file [[Lenses/IABIED - M4 Welcome]] |
| M5 | `source::` pointing at the standalone file [[Lenses/IABIED - M5 Welcome]] |
| M6 | Inline lens |
| M7 | Confirm |

This makes the case stronger rather than weaker, and changes what the work is. We are not adding welcomes to modules that lack them. We are making the contents of a slot that already exists on every module consistent, which is a smaller and safer change than replacing a structure.

**Two of the seven are already wrong, in different ways.**

M4's is stale. Its visible learner text is one paragraph; below it a `%%` block holds a pedagogical note and a whole `#### Chat` segment briefing the tutor on Sable's weight-stealing and the virus cover story, and listing this week's reading as chapters 7, 8, 9 and the Coda. That predates the film replacement.

M3's is the overhang, written down. Its visible text ends "can't we just stop it? That's where the next module begins", and its `summary_for_tutor` states that chapter 6 now opens the next module where it sets up the film. Both go false the moment chapter 6 refolds. Note which two drifted: the two in separate files, and the one under a non-standard wrapper.

**Decision.** Keep the `# Submodule: Welcome` slot on every module. Fill it inline everywhere, in the AIV style: `# Lens: Welcome` with `tldr::`, `summary_for_tutor::` and two or three sentences of framing. Retire the two standalone files and rename M3's wrapper to match the rest. Move M1's course orientation out to the new M1 as a course overview modelled on [[modules/XLab Verification Overview]], with a `:::callout` per unit, and restate the reading load, which changes.

**The argument against.** A course overview is read once and a learner arriving at unit 4 will not go back to it. That is what the inline welcomes are for, which is why the answer is both rather than either.

---

## 7. Testing

Before review, run at least one live pass through:

- The chapter 4 connection beat, checking specifically that the tutor does not supply the answer on the first turn. That failure turns the prompt into a cross-reference with extra steps.
- The chapter 9 pair, checking that the pre-reading prediction is not graded or hinted at, and that the closing comparison actually returns to what the learner wrote.
- The flipped film objection test.
- `validate_content` on the course after each stage, not only at the end.

## 7. Log

| Date | Change | Files | Why |
|---|---|---|---|
| | | | |
