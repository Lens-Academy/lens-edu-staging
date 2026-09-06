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

## 2. Open decisions

| Decision | Blocks | Notes |
|---|---|---|
| Are the 2026-08-24 fix-pass suggestions accepted? | Everything in stage 3 | 46 outcome files have pending repairs. Two threads terminate on outcomes in that batch |
| Is a cohort mid-flight? | Stage 1 | Published ids must not change under a running cohort |
| Where does U2 split into M2 and M3? | Stage 1 | Chapters 4 and 5 then 6, or chapter 4 then 5 and 6 |
| Do the extension readings move or duplicate? | Stage 2 | Optional in U2 and required in U3 is spaced repetition by construction, but can read as padding |
| Welcome lenses: keep, rewrite, or replace? | Stage 4 | See section 5 |
| Assessment load per unit | Stage 3 | Each recall beat is another tutor conversation |

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

**The current state.** Only two dedicated welcome lenses exist, [[Lenses/IABIED - M4 Welcome]] and [[Lenses/IABIED - M5 Welcome]]. Other modules open differently or not at all. So there is no consistent object to maintain, which is most of why they feel staggered.

**The M4 one has gone stale, and the staleness is instructive.** Its visible learner text is a single paragraph. Below it sits a `%%` block containing a pedagogical note and a `#### Chat` segment that briefs the tutor on Sable's weight-stealing, the virus cover story and the Coda's framing, and lists this week's reading as chapters 7, 8, 9 and the Coda. All of that predates the film replacement. A welcome in its own file is a file nobody opens when the module changes.

**Recommendation: retire the standalone welcome lenses and replace them with two things.**

A course-level overview in the new intro module, modelled on [[modules/XLab Verification Overview]]: a short "what this course is about" section, then one `:::callout` per unit. That file is the first thing every learner sees, so it is the one most likely to be kept current.

Then a short inline welcome in each module file, in the style the AIV modules use: a `# Lens: Welcome` heading with `tldr::` and `summary_for_tutor::` and two or three sentences of framing. Inline means it cannot drift into a separate file that nobody opens.

**The argument against.** A course-level overview is read once, at the start, and a learner arriving at unit 4 will not go back to it. That is what the inline welcomes are for, and it is why the recommendation is both rather than either.

**What it costs.** Three of five units change contents, so every welcome needs rewriting regardless. Replacing is barely more work than updating, and it removes two files from the maintenance surface.

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
