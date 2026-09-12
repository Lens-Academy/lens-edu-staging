---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# AIRF Restructure: change log and plan

Git records what changed. This file records why, what it depended on, and what we decided against. Update it in the same commit as the change it describes.

**Status key:** `todo`, `drafted`, `in progress`, `done`, `blocked`, `parked`, `dropped`.

**Dates:** full `YYYY-MM-DD`, on every entry. Where an entry was written up later than the work it describes, the row says so.

**Picking this up cold?** Read this file, then [[AIRF Restructure - Working Preferences]], then [[AI Guide/Course Authoring]]. Section 5 has the stage inventory with statuses; that is where to start. Conventions established in the work so far, none of them obvious from the files themselves:

- **Spelling is American throughout.** `Behavior vs. values`, `Grown, not crafted`. Easy to drift out of.
- **Outcomes carry no module or chapter labels**, not in the statement, the test or the rubric. Outcomes are shared across courses, so "M3" resolves differently depending on who imported it. This is also what the B1 eval check asks for.
- **Lens comment blocks stay minimal**: only what a first-time reader cannot infer. Rationale belongs here. Comments describing a transient state go stale and mislead.
- **Never write a literal double-percent comment marker into this file.** Obsidian pairs them and silently comments out everything between, which happened once and hid most of stage 1.
- **Block moves go insert first, delete second**, with the insert accepted before the delete is filed, so content never exists in neither place. Expect one transient duplicate-UUID error in the gap if the block contains an id-bearing lens. Better, where the block already sits next to its destination: move the submodule boundary over it instead of moving the block. No gap and no duplicate id.
- **Edit around other people's comments, never through them.** An edit whose span contains a CriticMarkup note routes to review as one unit, so rejecting it loses the whole edit rather than the offending part. Split the edit so every note falls outside every span.
- **Quote any frontmatter value containing a colon.** `summary_for_tutor: ... Four phases: recall, ...` is invalid YAML and fails the whole file, not just the field. Caught once by `validate_content` and not by eye.
- **Validate unscoped as well as course-scoped.** Files tagged `wip` are excluded from the course-scoped run, so errors in drafts stay invisible until promotion. Two malformed UUIDs hid this way.
- **`add_to_ai_context::` cannot be repeated** on one submodule; the second silently overwrites the first. Use comma-separated links on one line.
- **Test the premise early, the wording late.** Several beats share one failure mode, the tutor giving the answer away. Smoke-test that on one or two beats before writing more briefs on the same pattern; batch the rest into one pass at the end of stage 3.

Two tooling issues to raise with whoever maintains the relay. Unscoped `grep` and `glob` return content and paths from folders the key cannot `read`, including `Lens Edu Private`, while scoped calls and `read` enforce correctly, so the hole is specifically the no-path case. And edits route to the review queue based on whether the text looks human-written, so the protection weakens as a file accumulates AI-authored content; check how each edit actually landed rather than assuming.

**Working practice.** Edits to files we did not write go in as suggestions for review, never as overwrites. New files we author can be written directly. Each entry in section 9 should say which of the two it was, so nothing lands silently.

**Prior art we are not using.** There is a `Lens/base/IABIED/IABIED Course Build Notes` directory containing a module build algorithm, per-module decision logs and a spec for a "Supplementary Resources Lens". The relay key cannot open it. Decision: ignore it. The live modules were presumably built from those notes and have moved on since, so the modules are the better reference, and [[AI Guide/Course Authoring]] is the authority for how to write. Noted only so nobody later thinks it was missed.

---

## 1. Decisions already taken

Recorded so they do not get re-argued. Each entry is the decision, then the reason, then what it commits us to.

**Part I splits 3 and 3, with the Introduction pulled out.** U1 becomes chapters 1 to 3, U2 becomes chapters 4 to 6, and the Introduction gets its own module ahead of the first meeting. Week one's reading is Introduction plus chapters 1 to 3. Reason: chapter 6 currently sits in the unit that also carries the film, which is the only unit whose bracket does not fall inside one part of the book. Refolding chapter 6 into U2 fixes that and reunites it with chapter 5. The alternative, chapters 1 to 4 in week one, front-loads the densest reading onto learners who have not yet attended a session, which matters more in the intensive format where sessions run back to back. Cost: chapters 3 and 4 get split, which is the tightest pair in Part I.

**Correction on `intro-form`.** An earlier version of this plan said the Introduction module should carry `intro-form:: true`, on the reading that it marks a module as an introductory section. That is wrong. The flag marks a module as the host for an **intake form**: [[modules/XLab Verification Overview]] contains a `# Lens: Introduction Form`, and the Capstone course file records that "the intro-form answers on hours, team, and mentor will be used to pair." Setting it on M1 stopped the Introduction rendering. Removed. Nothing special is needed: a module placed before the first meeting is the overview, and the XLab one carries only `id`, `slug`, `title` and `tags`.

**Chapter 9 returns as a reading.** The film covers chapters 7 and 8 only, so under the current structure the scenario stops before Ascension. Reason: chapter 9 is not extra stakes on top of the argument, it is where the chapter 1 claim about steering the future gets cashed out with no ceiling. Cost: one new reading and one new outcome in U3.

**Instrumental convergence becomes required, at the top of U3.** Pairs the chapter 4 extension on terminal and instrumental goals with the chapter 5 extension on instrumental convergence. Reason: the passage is filed by the book as a chapter 5 extension, and it closes by routing the reader to chapter 6 for how an ASI would achieve its instrumental targets. Read before chapter 6 that pointer is a forward reference into unread material; read after, it resolves backwards. Placing it at the head of U3 also means the film then confirms a prediction the learner has already been given. Cost: material currently optional under chapters 6 and 8 becomes required, and either moves or appears twice.

**Recall prompts, not cross-references.** Ten threads, listed in [[Lenses/DRAFT - Recall Threads Proposal]]. The learner-facing prompt names nothing; the answer key lives in `assessment-instructions`. Reason: telling someone which principle applies removes the work that makes it stick.

**A prompt needs an outcome anchor at both ends.** A chapter-to-chapter link with no outcome at the earlier end is a proposal for a new outcome, not a prompt. Within-unit links are prerequisites and get no prompt, since sequential reading already carries them.

**Threads we dropped.** Coda into chapter 13, dropped on a closer reading of what the Coda claims. Chapter 6 into chapter 12 on irreversibility, left untethered because chapter 6 has no outcome to anchor it and chapter 10 already carries that ground. *Fiction as argument* receives nothing, because it synthesises Part I rather than resting on any single piece of it.

**Answering the note that moved chapter 6 out of U2 in the first place.** A CriticMarkup note at the foot of the U2 module records the original reasoning: chapter 6 was moved to the scenario module because it opens that unit and sets up the film, matching the book's own handoff, since chapter 6 ends with the story's first line. Our counter-argument, for the record rather than to delete the note:

- The instrumental convergence lens now performs the same setup function at the head of U3, tied to a different learning outcome, and additionally serves as synthesis and recall of the previous unit's work. The handoff is preserved, by a different vehicle.
- The flow from chapter 6's last lines into the story was already broken. The module made readers stop and litigate chapter 6's ideas through two learning outcomes, two pre-questions and two reading lenses before reaching the film. Moving the chapter to another unit does not break a continuity that the unit's own structure had already interrupted.

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
| [[modules/IABIED M3 Nonhuman Minds, Part 2]], Part 3 Welcome | Visible text hands chapter 6 to the next module; `summary_for_tutor` says the same | Stage 1 and 4 |
| [[Learning Outcomes/Fiction as argument, not prediction]] | Rubric level 5 requires "M4's emotional work" and that "Chapters 7–9 already made the dynamics feel real". Chapter 9 is now read, not felt through the film. Already flagged C3 in the 2026-08-24 run | Stage 2 |
| [[Lenses/IABIED - One Extinction Scenario (Video)]] | States it replaces chapters 7 to 9. Should be 7 and 8 | Stage 2 |
| [[Lenses/IABIED - M4 Welcome]] | Reading list and hidden Chat segment assume chapters 7 to 9 plus Coda | Stage 4 |
| M1 orientation lens | States the per-unit reading load and that one unit is mostly a film | Stage 4 |
| Three `Overview of Optional Resources M1 / M4 / M5` lenses | Not a dependency after all. No live module references them; the only inbound links are from `Lens/Deprecated modules` and the IABIED build notes. Orphaned remnants | Archive, not rename |
| Module slugs `iabied-m1` to `iabied-m7` | Slugs carry module numbers. Renumbering makes each slug point at different content | Stage 1, first. See below |

### The slug problem, and the scheme we chose

To be clear about a phrase I used badly: slugs are not links the vault rewrites because internal references between files use wikilinks, not slugs. Slugs are for platform URLs. So this is the external-dependency case, not a permissions one.

Renaming descriptively does not fix the remap. `iabied-nonhuman-minds-2` would mean chapters 3 and 4 today and chapters 4 to 6 afterwards: the same silent remap with words instead of numbers. Because content redistributes across all seven modules, no naming scheme preserves the old mapping.

**Scheme chosen: `iabied-intro`, `iabied-u1` to `iabied-u5`, `iabied-what-next`.** Reason: units are the more stable object. The 6-to-5 reconciliation changed module boundaries; unit count has held at five, and every diagram and decision in this restructure is expressed in units. M6 and M7 both sit in U5, so M6 takes `iabied-u5` and M7 takes `iabied-what-next`, which matches its content. If the pair ever needs to read as a pair, `iabied-u5-what-next` is a drop-in.

**Which old slugs can be kept alive.** Three map one to one and four do not:

| Old slug | Old content | New home | Clean? |
|---|---|---|---|
| `iabied-m1` | Intro + ch 1-2 | Keeps the Intro, loses ch 1-2 to the next module | No |
| `iabied-m2` | Ch 3-4 | Keeps ch 3, gains ch 1-2, loses ch 4 | No |
| `iabied-m3` | Ch 5 | Keeps ch 5, gains ch 4 and ch 6 | No |
| `iabied-m4` | Ch 6 + film + Coda | Ch 6 leaves; rest stays | No |
| `iabied-m5` | Ch 10-11 | New M5 | Yes |
| `iabied-m6` | Ch 12-14 | New M6 | Yes |
| `iabied-m7` | Synthesis | New M7 | Yes |

`slug-aliases` exists as a field and is used on four course files. [[AI Guide/Writing Course Files]] documents it under **course** frontmatter, and no module file uses it, so whether modules accept it is unknown. **Worth checking with whoever owns the platform.** If they do, the right answer is: new slugs everywhere, aliases only on M5, M6 and M7 where the mapping is clean, and no alias on M1 to M4 so those old links fail visibly rather than landing on the wrong content. Break loudly only where breaking is unavoidable.

Either way this needs a comms pass over meeting docs, cohort materials and anywhere else a module URL was pasted. Log those as they are found.

### A concurrent workstream, not ours

Noticed 2026-09-08 between two validation runs. The `Domains` folder has been restructured from fourteen flat files into a numbered subfolder tree with a `_domain_metadata.md` per folder, and the outcome frontmatter field `domain:` has been renamed to `topic:` with values repointed into the new tree. The sweep included our draft files, so nothing of ours needs migrating.

Two consequences.

**Twelve validation errors briefly attributed to this course and were not ours.** Topic files inside the new folders missing an integer `domain-number`. That workstream fixed them within the day and the count is back to zero for us. The lesson stands: when the vault-wide issue count moves, check whether it is ours before reacting, and check that it does not grow after our own changes, because a rising count could hide one of ours. As of 2026-09-10 the folder is named `Domains and Topics`, having been renamed twice during a single working session, so any path written here for it may already be stale.

**Coordination before stage 3: cleared 2026-09-11.** The concern was that this workstream was editing the same outcome files we were about to touch. Two things retire it. Stage 3 adds phases to lenses, not to outcomes, so the overlap it worried about is not where the work lands. And a course-scoped `validate_content` comes back clean, so every `topic:` link in a file this course reaches resolves against the current tree. The errors still open in that tree are `_domain_metadata.md` files missing frontmatter, which are theirs and reach no course. The earlier spot-check on 2026-09-10 stands: it changed only the `topic:` field and its path, leaving statements, tests and eval-results untouched.

### Surveys and meetings

**Surveys attach to meetings, not modules**, via `survey::` and `facilitator-survey::` on each `# Meeting:` block in the course file. The meeting count stays at five and the meetings keep their order, so nothing renumbers.

**Rechecked 2026-09-11: the survey set has been replaced since this scan was first written.** The course now runs the v2 instruments. `Lens Post-Meeting Impact Survey v2` on meetings 1 and 2, then `AIRF Meeting 3 Impact Survey v2`, `AIRF Meeting 4 Impact Survey v2` and `AIRF Final Impact Survey v2`. The `AIRF Session 1 / 3 / 4 / 5` and `AIRF Weekly` files still exist but nothing in this course points at them any more. Intake has left the course entirely: `application-survey:: [[../surveys/Application Form]]` sits in the preamble, and the enrolment wizard refuses enrolment until it is submitted, which is why the intake form is no longer stage 6 work.

The conclusion is unchanged. Surveys carry no chapter or module references, so nothing in them breaks when the reading behind a meeting changes.

| Item | Finding |
|---|---|
| **Meeting titles** | Done in 1e. Meetings 1 and 5 renamed |
| **`meeting-doc-template::` Google Docs** | Five external templates, one per meeting. These hold the actual per-meeting discussion content, and the content behind meetings 1, 2 and 3 all change. This is the largest external dependency and belongs in the comms pass |

**Do not edit survey files casually.** The course file records a hard rule learned the hard way: no answerable segment may precede an outbound link, because answers live in React state until submit and survey links carry no `target=_blank`, so a learner who clicks a link mid-survey loses every answer and their attendance. The retired v1 files also record why they were byte-for-byte copies of one another, which was to keep every question key, wording and order stable so the pre/post rating comparison held.

**Checked 2026-09-11, and the v2 set does not carry those keys.** Two different identifiers are in play. `key::` is a snake_case name on legacy segments that the platform reads for behavior, and `id::` is the UUID a modern segment's responses are stored under. Neither is the same thing as a lens question id. The four impact scales, `risk_seriousness`, `agency_belief`, `motivation` and `next_step_clarity`, are legacy `key::` segments in `AIRF Session 1` and `Session 5` and appear in no v2 file. `buddy_texted` is gone as well, and the only legacy key left anywhere in the AIRF v2 set is `facilitation_interest`. The two-timepoint join has been replaced by a retrospective before-and-after pair asked inside the final survey in one sitting. The five shared meeting questions also carry different `id::` values in each v2 file despite identical wording, so they are separate segments.

None of that touches the restructure and none of it is ours to fix. One consequence is worth passing on, though: `Navigator Session 1 Debrief` is still attached to meeting 1 and still collects `risk_seriousness` and `agency_belief`, which the course file says were deliberately shared with the learner instrument so navigator and learner trajectories would be comparable in one export. The learner side no longer collects them.

### Lens conditions we are deliberately not touching

Two pre-existing things showed up while inserting the first recall segment. Both are real, neither is ours, and fixing either means editing live segments across six lenses for no benefit to this restructure. Recorded so the next person finds an answer rather than the question.

**Legacy question syntax.** The six chapter lenses use the bare `#### Question` marker. [[AI Guide/Course Authoring]] calls that the legacy form and says it is being phased out in favor of `#### Question: Open` and its siblings. New segments we add use the current form, which leaves those files mixed. Converting the existing segments is a separate pass: they carry ids that learner responses are stored under, so it is a change to answered content rather than a formatting tidy.

**`add_to_ai_context` in two places at once.** Chapter 4 reaches the tutor twice, once from a YAML `add_to_ai_context:` list in the lens frontmatter and once from the inline `add_to_ai_context::` field on M3's Ch4 submodule. The two syntaxes look different enough that the duplication is easy to miss. Whether the platform de-duplicates is unknown. Worth checking before anyone reasons carefully about what a tutor can see, and worth checking on the other chapter lenses too, since nothing suggests chapter 4 is special.

### Outcomes we are deliberately not touching

Three convergence-adjacent outcomes came up and all three are out of scope. Recorded here in one line each so they do not get re-litigated, and deliberately **not** cross-linked, since backlinks from an AIRF planning doc into other courses' files serve nobody.

`Goals and instrumental convergence` belongs to the Fundamental Difficulties modules in other courses. `Indifference, not malice` likewise; its "M3" reference is most likely a coincidence of those courses' own numbering. `Instrumental sub-goal convergence` is the orphaned chapter 8 outcome the film replaced, which is why its statement reads as unintelligible without the old module in front of you; U3 gets a new outcome instead of inheriting that confusion. `Goal conflict as a physical fact` is a chapter 7 outcome kept for posterity, usable as context when the film lens is flipped but not imported.

**The general lesson.** Outcomes are shared across courses, so a module label inside an outcome resolves differently depending on which course imported it. Any outcome we write should carry no module or chapter labels at all. That is what B1 asks for, arrived at from a different direction.

---

## 4. Order of execution

1. **Slugs and filenames first.** Both carry module numbers, and everything downstream should be edited against stable paths.
2. **Structure before content.** Moving a chapter between modules changes which lenses are in scope. Writing recall segments first would mean rewriting them.
3. **New content before recall segments.** Two of the ten threads terminate on outcomes that do not exist yet, both in U3.
4. **Welcomes after structure.** A welcome that previews a unit cannot be written until the unit's contents are settled, and three of five units change.
5. **Glossary last.** Stages 2 and 3 introduce new terms. A glossary written first would need reconciling against them.

6. **Meeting docs last of all.** Their scope is unknowable until everything above has settled.

This maps onto the stages in section 5 in order: 0, 1, 2, 3, 4, 5, 6.

---

## 5. File inventory

### Stage 0, preconditions

| File | Change | Status |
|---|---|---|
| [[courses/AI Risk Fundamentals]] | Relabel the author comment attributed to a student | `done` |

### Stage 1, structure

No module is created, merged or retired. All seven files persist and only their contents move. Order within the stage: renames first so later edits run against stable paths, then frontmatter, then content, then the course file.

**1a. Done.**

| File | Change | Status |
|---|---|---|
| Module slugs, all seven | `iabied-intro`, `iabied-u1` to `iabied-u5`, `iabied-what-next` | `done` |
| Three `IABIED - Overview of Optional Resources M1 / M4 / M5` lenses | Orphaned. Archived to `_deprecated` | `done` |

**1b. Filenames. Done.** `move` rewrote all inbound links, including the course file's `# Module:` links, verified after the fact.

| From | To | Status |
|---|---|---|
| `IABIED M1 Intro and Nonhuman Minds, Part 1` | `IABIED M1 Introduction` | `done` |
| `IABIED M2 Nonhuman Minds, Part 2` | `IABIED M2 Nonhuman Minds, Part 1` | `done` |
| `IABIED M3 Nonhuman Minds, Part 3` | `IABIED M3 Nonhuman Minds, Part 2` | `done` |

**1c is folded into 1d and no longer exists as a separate step.** It was going to change `title` and `readings` ahead of the content moves, which would have left three modules whose frontmatter described contents they did not yet have. That is the same drift this project exists to remove. Frontmatter and content change together, per module.

**1d. Content and frontmatter, one module at a time.** Whole `# Submodule:` blocks move, each carrying its `add_to_ai_context`, outcome refs, lens refs, Dive Deeper index and hidden QA imports. `title` and `readings` change in the same edit.

| Module | Blocks in | Blocks out | New title | New readings |
|---|---|---|---|---|
| M1 | none | `Ch1 - Intelligence`, `Ch2 - Grown, not crafted` | Introduction | Introduction only |
| M2 | Ch1, Ch2 from M1 | `Ch4 - You Don't Get What You Train For` | Nonhuman Minds, Part 1 | Ch 1, 2, 3 |
| M3 | Ch4 from M2, `Ch6 - We'd Lose` from M4 | none | Nonhuman Minds, Part 2 | Ch 4, 5, 6 |
| M4 | none | Ch6 | unchanged | Coda; Ch 9 added in stage 2 |

M5, M6 and M7 are untouched. Titles match the meeting titles.

Within 1d, all four block moves land before any frontmatter changes, so the intermediate state is deliberately inconsistent and 1d is not complete until the frontmatter lands.

Do not strip the Obsidian comment block in M3's welcome: it holds drafted framing for chapter 6 from when the chapter lived there, and chapter 6 is coming back.

**1e. Course file.** Smaller than expected. Meeting boundaries currently sit as M1, meeting 1, M2 and M3, meeting 2. They need to become M1 and M2, meeting 1, M3, meeting 2. **Only the first `# Meeting:` block moves**, down past M2. Meeting 2's position is unchanged, as are meetings 3, 4 and 5, and the module order never changes. Retitle meeting 1 and meeting 2, which are currently "Introduction" and "Nonhuman Minds". The resources module is stage 5, not here.

**1f. Card targets. Done.** Each Dive Deeper index lens cards QA lenses that the module separately imports with `optional` and `hide`. Those imports must sit in the same module as the lens that cards them. M6 already carries two such imports under Ch12 solely because they are card targets inside a Ch12 lens, so the pattern exists and can cross submodules. The check was run on 2026-09-08 and went unrecorded at the time; the log entry was added 2026-09-11. Standing note for any future block move: `validate_content` may or may not catch this class of breakage, so verify every `::card` target in a moved lens directly against its new module's imports.

### Stage 2, new content

`done` here means written, validated and imported. It does not mean tested: the Lens Tutor is not running on staging, so none of these briefs has been run against a real session. See section 7.

| File | Change | Status |
|---|---|---|
| **New U3 opener outcome** | Written fresh, not inherited. `Predictable sub-goals from unknown goals`. Imported into M4 | `done` |
| New U3 opener lens | `IABIED - Goals and Instrumental Convergence`. Elicitation, two extension readings, betting question, handoff. Imported into M4 | `done` |
| [[Lenses/IABIED - One Extinction Scenario (Video)]] | Objection test flipped, bets callback added as a third beat, chapters 7 to 9 corrected to 7 and 8, handoff repointed at chapter 9, source-precedence rule added. Chapters 7 and 8 added to the submodule's `add_to_ai_context` | `done` |
| Working copies of the two chapter 9 drafts | Copied to [[Lenses/IABIED - Cosmic Stakes]] and [[Learning Outcomes/Cosmic stakes]]. The originals stay as the proposal's worked examples | `done` |
| [[Lenses/IABIED - Cosmic Stakes]] | TODOs filled from a summary, not the chapter. Promoted and imported | `done`. See section 8 before revising the briefs |
| [[Learning Outcomes/Cosmic stakes]] | `requires` repointed, reading span added, level 4 and level 5 extended. Promoted and imported | `done` |
| `Dive Deeper: Chapter 9` lens, id `b3132948` | Moved into the Cosmic Stakes submodule with `The Ending` and `Won't It Choose to Be Moral`. The card for the latter is still deliberately absent while its Q&A is a placeholder | `done` |
| [[Learning Outcomes/The core extinction argument]] | **Out of scope**, and with it [[Learning Outcomes/Why we'd lose]] and [[Learning Outcomes/Your path forward]]. All three are `work-in-progress` with empty tests, none has ever had one, and M7's imports of two of them sit inside a comment block, so nothing they say is live. The synthesis they describe is already run by M7's Welcome lens as a question. Making them real means deciding whether that synthesis is a lens question or a graded outcome, which is an overhaul of the final module, not a repoint | `dropped` |
| [[Learning Outcomes/Fiction as argument, not prediction]] | Level 5's chapter reference corrected to the film and chapter 9 by Andreas; the module label rephrased out. Nothing else touched | `drafted`, awaiting acceptance of the suggestion |

### Stage 3, recall segments

One added phase per lens, and only the U3 opener carries two threads in one segment. Chapter 4 went first as the test case for the pattern, but the Lens Tutor is not running on staging, so it could not be tested and neither can these. Section 7 has the reasoning for proceeding anyway. Everything written here is untested against a real session.

| Lens | Threads landing here | Status |
|---|---|---|
| [[Lenses/IABIED - Goals and Instrumental Convergence]] | Intro hard vs. easy calls; Ch 5 goal-space | `done`. The betting question carries both without a separate phase |
| [[Lenses/IABIED - Cosmic Stakes]] | Ch 5 hostile vs. indifferent | `done`. Carried by the pre-reading prediction and the reaction brief, with no separate phase |
| [[Lenses/IABIED - Path Prediction vs Outcome Prediction]] | Intro hard vs. easy calls | `done`, untested. A variant beat: recall and audit rather than search and name |
| [[Lenses/IABIED - You Don't Get What You Train For]] | Ch 2 behavior vs. values | `done`, untested. A worked draft stays at [[Lenses/DRAFT - Ch4 with Connection]] as a proposal artifact; the phase was inserted fresh rather than promoted |
| [[Lenses/IABIED - Alchemy Not Science]] | Ch 2 grown not crafted | `todo` |
| [[Lenses/IABIED - Strong Superalignment Objection]] | Ch 3 wanting emerges from training | `todo` |
| [[Lenses/IABIED - Define the Aztec Warrior Analogy]] | Ch 1 prediction plus steering | `done`, untested. Closes the last thread into U2 |
| [[Lenses/IABIED - The Five Engineering Curses]] | Ch 1 machine advantages, via the curse of speed | `done`, untested. The brief credits self-amplification as well as speed |
| [[Lenses/IABIED - The One-Chance Problem]] | Ch 10 five curses, via Chernobyl appearing twice | `todo` |

The six existing chapter lenses all run the same `Reading Assignment`, `Phase 1: Recall`, `Phase 2: Processing`, `Phase 3: Learning Question` shape, so the insert sits in the same place in each: a new phase before the learning question, and the learning question renumbered. What the new phase asks is not identical everywhere. The Coda's is a variant, for reasons recorded in its log entry. The two new U3 lenses do not run that shape at all, and neither needs a bolted-on phase: the opener's betting question already does the retrieval, and the chapter 9 lens does it through the prediction it takes before the reading.

### Stage 4, welcomes

Every module already has a `# Submodule: Welcome`. The work is making its contents consistent, not adding the slot.

| File | Change | Status |
|---|---|---|
| New M1 | Receives the old M1 course orientation as a course overview, `:::callout` per unit, reading load restated | `todo` |
| M2 (old M1) | Inline welcome, now framing chapters 1 to 3 | `todo` |
| M3 | Rename the `Part 3 Welcome` wrapper to `Welcome`, rewrite for chapters 4 to 6. Currently hands chapter 6 to the next module | `todo` |
| M4 | Retire [[Lenses/IABIED - M4 Welcome]], replace inline. Stale reading list and hidden Chat segment go with it | `todo` |
| M5 | Retire [[Lenses/IABIED - M5 Welcome]], replace inline | `todo` |
| M6, M7 | Confirm M7, then bring both to the same shape. **M7 also carries a live error:** the twelve-step argument chain in its Welcome brief has step 7 as the scenario covering chapters 7 to 9 through the film. The film is 7 and 8, and chapter 9 is read | `todo` |

### Stage 5, resources

| File | Change | Status |
|---|---|---|
| New resources module | Sits outside the unit sequence | `todo` |
| Glossary | Last. New keywords from stages 2 and 3 would otherwise conflict | `todo` |
| Companion pieces | Not yet scoped | `todo` |
| Extended readings | Not yet scoped | `todo` |

### Stage 6, meeting docs

Last, and deliberately so. Scope cannot be assessed until the restructure above is finished, because what each meeting has to cover is exactly what changes. Nothing else waits on this: it is fully downstream, with no dependencies pointing back into stages 1 to 5.

| File | Change | Status |
|---|---|---|
| Meeting 1 doc | Now covers Introduction plus chapters 1 to 3, was Introduction plus chapters 1 and 2 | `todo` |
| Meeting 2 doc | Now covers chapters 4 to 6, was chapters 3 to 5. Its next-unit pointer names Ch 6 + film + Coda + Your Leverage and will be wrong | `todo` |
| Meeting 3 doc | Loses chapter 6, gains the U3 opener and chapter 9 | `todo` |
| Meeting 4 doc | Expected unchanged | `todo` |
| Meeting 5 doc | Expected unchanged | `todo` |
| **Intake form for M1** | **Out of scope.** Intake has moved outside the course: `application-survey:: [[../surveys/Application Form]]` in the preamble, collected by the enrolment wizard before a learner joins. Nothing to build here. The old blocker, what belongs pre-meeting versus in the post-meeting survey, is now a question for whoever owns the Application Form | `dropped` |

The docs are reachable through the `meeting-doc-template::` links on each `# Meeting:` block. They may warrant restructuring in their own right rather than only patching, which is a decision for whoever owns them once the shape above is settled. Note the history recorded in the course file: meeting 2's doc once ran an outdated session for three days because a link was believed repointed and was not, so verify by opening the doc rather than by trusting the link.

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

M4's is stale. Its visible learner text is one paragraph; below it an Obsidian comment block holds a pedagogical note and a whole `#### Chat` segment briefing the tutor on Sable's weight-stealing and the virus cover story, and listing this week's reading as chapters 7, 8, 9 and the Coda. That predates the film replacement.

M3's is the overhang, written down. Its visible text ends "can't we just stop it? That's where the next module begins", and its `summary_for_tutor` states that chapter 6 now opens the next module where it sets up the film. Both go false the moment chapter 6 refolds. Note which two drifted: the two in separate files, and the one under a non-standard wrapper.

**Decision.** Keep the `# Submodule: Welcome` slot on every module. Fill it inline everywhere, in the AIV style: `# Lens: Welcome` with `tldr::`, `summary_for_tutor::` and two or three sentences of framing. Retire the two standalone files and rename M3's wrapper to match the rest. Move M1's course orientation out to the new M1 as a course overview modelled on [[modules/XLab Verification Overview]], with a `:::callout` per unit, and restate the reading load, which changes.

**The argument against.** A course overview is read once and a learner arriving at unit 4 will not go back to it. That is what the inline welcomes are for, which is why the answer is both rather than either.

---

## 7. Testing

**Premise first, on one or two beats, before writing more briefs on the same pattern.** Several beats share one failure mode: the tutor giving the answer away. If a tutor cannot hold that constraint, the design premise fails and we want to know before eight more briefs are written against it. Test it on the chapter 4 connection beat or the U3 opener's elicitation question, where the brief explicitly forbids completing the learner's list.

**Blocked 2026-09-11: the Lens Tutor is not running on staging.** No beat in this plan can be tested against a real session. Report it and get a run scheduled. Until then everything written in this restructure ships untested, stage 2 as much as stage 3: the U3 opener, the film lens changes and the chapter 9 pair are all in the same position as the recall beats, and the checklist below was written assuming a tutor would be there to run it against. None of it has been run.

One thing that may not be blocked. The `eval-results` blocks on the older outcomes come from the Learning Outcome Evals, which are a different mechanism from a live tutor session and may still be available. Neither `Predictable sub-goals from unknown goals` nor `Cosmic stakes` carries one. Worth finding out, because it would at least cover the outcome tests while the tutor side waits.

**That removes the reason to sequence, so stage 3 proceeds.** The point of testing one beat first was to avoid writing five more against a broken premise. Waiting no longer buys that information, because the blocker is infrastructure and the test cannot be run before the briefs or after them. Two further reasons it is safe to continue. The behavior at issue is carried by the `Response style`, `Conversation flow` and `What not to do` sections, which are near-identical across the beats, so the beats will pass or fail together rather than one at a time. And if they fail, the fix lands in those shared sections, not in the per-lens answer key and grading ladder, which is the part that would actually be expensive to rewrite. The exposure is smaller than this section assumed when it was written.

**Wording last, in one pass at the end of stage 3.** The briefs are consistent in shape, so a single pass surfaces systematic drift rather than one-off phrasing, and testing them individually invites tuning each against its own transcript, which overfits. Several can only be tested in sequence anyway, since the film lens reaches back to bets made in the opener.

Specific things to check in that pass:

- The film lens: does the tutor volunteer material from chapters 7 or 8 despite the source-precedence rule? The chapters are now in its context, so the instruction is the only thing holding the line.
- The film lens: does it correctly treat the hostility bet as won rather than lost, given the film ends in extinction?
- The chapter 9 pair: is the pre-reading prediction left ungraded and unhinted, and does the closing comparison actually return to what the learner wrote?
- The U3 opener: does the tutor resist completing the list of convergent sub-goals in the elicitation beat?
- `validate_content` after each stage, and unscoped at least once per stage, since `wip` files are excluded from the course-scoped run.

## 8. Writing about chapters we cannot read

The relay key cannot read `Lens Edu Private`, so no session can open the chapters its own lenses teach. Confirmed again on 2026-09-11: `glob` lists the files, `read` refuses them. This section records what that has cost so far.

### Chapter 9 The chapter 9 material was written from a summary Andreas gave in conversation, not from the text.

That matters for anyone revising it. The tutor briefs make specific claims about what the chapter says, and every one of those claims is second-hand. They are the weakest part of the lens.

**The failure this produced, recorded because it will recur.** The summary ends on a speculative passage: Sable eventually meets another superintelligence and divides the universe with it, and that one had been aligned successfully by its own creators. Read from a summary, that passage looked like the chapter's argument, and three places inherited the mistake. The comparison brief said the boundary on expansion was another agent rather than physics. The reaction brief accepted "alignment is a target that can be hit" as a strong answer and scored its opposite as wrong. The outcome was about to gain a third stopping condition at level 4, which it did not need.

All three were wrong. The ceiling is the limits of intelligence and physics, wherever those fall. Another superintelligence is one possible boundary and not the chapter's focus, so a learner who predicts no second agent has made no error. And that alignment can be hit was established back in chapter 6; the scenario presumes it was not.

**The lesson.** A striking passage at the end of a summary is not the same as a load-bearing passage in the chapter. Summaries compress the argument and preserve the ending, which inverts their weights. Where a brief rests on the tail of a summary, say so in the brief rather than building a rubric level on it.

**The same trap, a second time, with a different stand-in.** On 2026-09-11 the chapter 10 connection brief made AI-assisted AI research *the* mechanism behind chapter 1's self-amplification. It is one route the chapter mentions, not the concept. The concept is the intelligence explosion, and a system experimenting on and rewriting itself can arrive there without help, which is what Sable does in the scenario. The brief had narrowed a concept down to one of its triggers.

That wording came from the learning outcome `Machine advantages and intelligence explosion`, whose statement names AI-assisted AI research as the route. No chapter was read, so an outcome statement got used as a proxy for one. It is a worse proxy than a summary: it is a compression written for a different purpose, it reads like a settled claim, and it carries no signal about what it left out. Treat any outcome statement about a chapter we cannot open as a claim to check, not a source. The statement is not wrong here, only narrow, which is exactly why it was easy to inherit.

**And the correction overshot.** The first fix cut the intelligence explosion out of the brief entirely and replaced it with self-experimentation, which swapped one narrow answer for another. Rejected, and refiled to keep the concept and widen the routes. Worth recording because the reflex on being corrected was to invert rather than to widen, and inverting loses the thing that was right.

---

## 9. Log

| Stage | Date | Change | Files | Why | How it landed |
|---|---|---|---|---|---|
| 0 | 2026-09-08 | Relabelled the structural-improvement comment from "student" to "student-to-navigator" | [[courses/AI Risk Fundamentals]] | It is facilitator-side analysis. Labelled as learner evidence it gets read as cohort feedback, which is how it was read once already | Direct, by Andreas |
| 1a | 2026-09-08 | Slugs changed on five modules: `m1`→`u1`, `m4`→`u3`, `m5`→`u4`, `m6`→`u5`, `m7`→`what-next` | Five IABIED module files | Old slugs would silently point at different content after the restructure. Units are the more stable object than module numbers | **Pending suggestions.** Five separate ones to accept |
| 1a | 2026-09-08 | Archived three orphaned `Overview of Optional Resources` lenses to `_deprecated`, suffixed `- ORPHANED` | M1, M4, M5 variants | No live module referenced them. Each move reported **0 links rewritten**, which confirms it | **Direct.** `move` has no suggestion mode |
| 1a | 2026-09-08 | **Decision: redistribute content across the seven existing modules rather than creating an intro module and merging M2 into M3.** Old M1 becomes Introduction, old M2 becomes U1, old M3 becomes U2 | Plan-level | `Course Authoring` line 32: never change the id of already-published content, because learner progress is keyed on it. Redistributing creates and destroys no module ids. Merging would destroy one and mint one. It also removes the merge step entirely | Plan only |
| 1a | 2026-09-08 | **Corrected:** old M1 goes to `iabied-intro`, not `iabied-u1` | [[modules/IABIED M1 Introduction]] | Follows from the redistribute decision. Old M1 becomes the Introduction module | Direct, since it edited my own pending change |
| 1a | 2026-09-08 | Slugs on the two held modules: old M2 → `u1`, old M3 → `u2` | Two IABIED module files | Follows from the same decision | Pending suggestions |
| 1b | 2026-09-08 | Renamed three module files to match their new contents | M1, M2, M3 | Old names described the old chapter allocation. `move` rewrote all inbound links including the course file's | **Direct.** `move` has no suggestion mode |
| 1d | 2026-09-08 | Moved the `Ch1 - Intelligence` and `Ch2 - Grown, not crafted` blocks from M1 into M2, ahead of Ch3 | M1, M2 | First half of the 1d redistribution. Each block carried its `add_to_ai_context`, both outcome refs, all lens refs including the commented-out PQ, its Dive Deeper index and all its hidden QA imports | Pending suggestions, one per file. Insert accepted before the delete was filed, so the content was never live in neither place |
| 1d | 2026-09-08 | Moved the `Ch4` block from M2 into M3, ahead of Ch5 | M2, M3 | Same pattern. The block was fully self-contained, index lens and all seventeen hidden imports inside it | Pending suggestions, same ordering |
| 1d | 2026-09-08 | Moved the `Ch6` block from M4 into M3, after Ch5. Normalised its `##` headings to `#`, and **added the `Instrumental Convergence` hidden import** which the block was missing | M3, M4 | Ch6's Dive Deeper cards that lens, but its import lived in M4's Ch8 submodule, so a naive move would have broken the card. This is the 1f risk, realised | **Direct**, not pending, apparently because the anchor sat beside my own pending edit. Produced one transient duplicate-UUID error until M4's copy was removed |
| 1d | 2026-09-08 | Cut the `Instrumental Convergence` card and its now-orphaned hidden import from M4's Ch8 index | [[modules/IABIED M4 One Extinction Scenario]] | The concept becomes required reading at the head of U3 in stage 2, so a second optional card under Ch8 is redundant. Elias's AI's note explaining the original carding is left in place as history | Direct |
| 1d | 2026-09-08 | Frontmatter on all four changed modules: titles and reading lists | M1, M2, M3, M4 | All four described contents they no longer had. M1 still read "Introduction: Grown, Not Crafted" | M1 and M2 pending, M3 and M4 direct |
| 1e | 2026-09-08 | Moved M2 ahead of the first meeting, so week one's prep is the Introduction plus chapters 1 to 3 | [[courses/AI Risk Fundamentals]] | Only the Introduction sat before meeting 1 while chapters 1 to 6 were squeezed into one block. Done by moving the module line up rather than the meeting block down, because the meeting's survey lines carry CriticMarkup the edit tool cannot match | First edit direct, second pending |
| 1e | 2026-09-08 | **Removed `intro-form:: true` from M1.** Renamed meeting 1 to "Intro and Nonhuman Minds, Part 1" and meeting 5 to "Facing the Challenge, Part 2 and Next Steps" | [[courses/AI Risk Fundamentals]] | The flag hosts an intake form, it does not mark a module as introductory, and setting it stopped the Introduction rendering. On the names: meeting 1's second module is genuinely the lighter half so the short mention is honest; meeting 5's is not, since M7 carries the synthesis and Your Ongoing Action. "Aftermath" was rejected as backward-looking. Titles are display-only and cheap to revise | Direct |
| 1f | 2026-09-08 | Verified that every `::card` target in a moved lens still resolves in its new module | Moved lenses across M1 to M4 | The Ch6 case was caught during 1d rather than by this sweep, which made the sweep look unrun. **Recorded 2026-09-11**, on Andreas's confirmation of the original date | Log only |
| 2 | 2026-09-10 | Wrote a new outcome, `Predictable sub-goals from unknown goals`, rather than reusing either existing convergence outcome | [[Learning Outcomes/Predictable sub-goals from unknown goals]] | One belongs to other courses; the other is the orphaned chapter 8 outcome the film replaced. `stage: intermediate` because it declares a prerequisite, which is what stage tracks: skill-tree depth, not difficulty | Direct |
| 2 | 2026-09-10 | Wrote the U3 opener lens. Four beats: elicitation, the two extension readings, a betting question, handoff. No Recall or Processing beat | [[Lenses/IABIED - Goals and Instrumental Convergence]] | The readings are two short extension pieces, not a chapter, and the unit reframes concepts the learner already has. Elicitation first so the reading names a pattern they have already found. The betting question does the retrieval without asking for it, and the film lens will reach back to the bets | Direct |
| 2 | 2026-09-10 | Instrumental convergence article split into two Article spans with a gap | same lens | The omitted stretch walks through hiding copies, building independent infrastructure and removing our ability to interfere, which is most of the film's plot. Two spans rather than an edited copy so the source stays intact and footnotes resolve | Direct |
| 2 | 2026-09-10 | Imported both into M4 as a `Goals and Instrumental Convergence` submodule, after Welcome and before the film. `wip` stripped from both files | [[modules/IABIED M4 One Extinction Scenario]] | A production module referencing a `wip` file is itself an error, so the tag had to come off in the same batch | Direct |
| 2 | 2026-09-10 | Test question replaced: the original duplicated the lens's betting question. Now a well-behaved cancer-research model given a long-horizon goal | [[Learning Outcomes/Predictable sub-goals from unknown goals]] | A learner who did the lens could pattern-match the old test without re-deriving anything. Stipulating good intentions also blocks goal misspecification, which level 2 now catches explicitly rather than scoring as partial credit | Direct |
| 2 | 2026-09-10 | Level 5 recast twice, then given a second route | same file | First away from supervision toward horizon, then away from "no endpoint" toward magnitude: the goal does have an end state, what is unbounded is its cost, and the earlier projects generated the same sub-goals without them amounting to anything. The second route is the harder insight, that a correctly aimed terminal goal would not have been sufficient either, which is what makes convergence load-bearing alongside the goal-space argument rather than sequential to it | Direct |
| 2 | 2026-09-10 | **Tooling note.** Every edit in this stage landed direct rather than as a suggestion, including on files we did not write. Replacement-versus-insertion does not explain it. Likeliest reading is that the relay tracks provenance per file and stops treating a file as human-written once enough AI content accumulates, so the protection weakens as a file gains more of our work. Raise alongside the grep and glob scoping issue | Tooling | n/a | n/a |
| log | 2026-09-11 | Full dates on every entry in this table; the `2026-09` convention note retired | This file | The undated entries were all 2026-09-08. A note explaining away missing precision is worse than the precision | Direct |
| 2 | 2026-09-11 | Working copies of both chapter 9 drafts, `wip`, fresh UUIDs throughout | [[Lenses/IABIED - Cosmic Stakes]], [[Learning Outcomes/Cosmic stakes]] | The drafts stay as the proposal's worked examples, so no id could be reused | Direct, new files |
| 2 | 2026-09-11 | All three tutor-brief TODOs written, plus the tldr and `reading_minutes` | [[Lenses/IABIED - Cosmic Stakes]] | Written from a summary rather than the chapter. See section 8 | Direct |
| 2 | 2026-09-11 | **Corrected:** the boundary claim, the accepted answers and the trap, all of which over-weighted the chapter's closing passage | same lens | See section 8 | Direct |
| 2 | 2026-09-11 | Two redundancies cut: `The Ending` carded both here and in the Dive Deeper index that joins this submodule, and both closing briefs sending the learner on to the Coda | same lens | Andreas's catch. The reaction brief also claimed the Coda came next, when the comparison question sits between | Direct |
| 2 | 2026-09-11 | Outcome's second `requires` repointed to `Predictable sub-goals from unknown goals`; `reading-from` and `reading-to` added | [[Learning Outcomes/Cosmic stakes]] | It still pointed at the orphaned chapter 8 outcome. The reading fields are plain language on every other outcome, not the character-exact anchors the draft assumed, so they were never the blocker | Direct |
| 2 | 2026-09-11 | Level 4 gained the magnitude of the loss. Level 5 gained a second route, for a learner who follows the reasoning outward to what is at stake beyond us | same file | Both Andreas's. The second route credits the insight without requiring the strategic conclusion, which the course's last unit argues against and which this outcome does not test | Direct |
| 2 | 2026-09-11 | New `Cosmic Stakes` submodule in M4, carrying chapter 9 as `add_to_ai_context` | [[modules/IABIED M4 One Extinction Scenario]] | Deliberately not on The Scenario. That would hand chapter 9 to the film lens's tutor and void the source-precedence rule added in stage 2 | Direct |
| 2 | 2026-09-11 | `Dive Deeper: Chapter 9` and its two hidden imports moved out of The Scenario into the new submodule | same file | Done by moving the submodule boundary over the block rather than moving the block, since the two were already adjacent | **One rejected suggestion, then direct.** The first attempt spanned Elias's note and was rejected whole; splitting it around the note worked |
| 2 | 2026-09-11 | Chapter 9 added to M4's `readings` | same file | Left over from 1d, which deferred it here | Direct |
| 2 | 2026-09-11 | Both files promoted off `wip` and imported into the submodule, outcome before lens | Lens, outcome, M4 | A production module referencing a `wip` file is itself an error, so the tags came off in the same batch. `validate_content` clean on the course afterwards, without `accept_drafts` | Direct |
| 2 | 2026-09-11 | Module label stripped from level 5 of [[Learning Outcomes/Fiction as argument, not prediction]] | That file | It is another course's file as well as ours, and the eval notes name the label as the C3 failure. `eval-results` still carries the pre-edit `content-sha`, so the recorded checks now describe a state the file is no longer in | **Pending suggestion**, filed as one rather than applied |
| 6 | 2026-09-11 | **Intake form dropped from scope.** Intake moved out of the course to `application-survey::`, collected by the enrolment wizard before a learner joins | Stage 6 table | Removed rather than deferred. There is no longer a form to build inside the course | Log only |
| 3 | 2026-09-11 | Survey scan refreshed. The course has moved to the v2 instruments and no longer points at any `AIRF Session` or `AIRF Weekly` file | Section 3 | The scan named five surveys that are no longer attached, which would have sent a later session to the wrong files. Conclusion on the restructure unchanged: still no chapter or module references. The legacy `key::` fields did not survive the move, which is recorded in section 3 and is not ours to fix | Log only |
| 2 | 2026-09-11 | **Dropped from scope:** `The core extinction argument`, and with it `Why we'd lose` and `Your path forward` | Stage 2 table | Nothing they say is live. M7's imports of two of them sit inside a comment block, all three have never had a test, and their suggested lenses point at optional Q&A cards rather than any teaching lens. Recorded as one drop covering all three so a later session does not re-open just one | Log only |
| 4 | 2026-09-11 | **Found while checking the above:** M7's Welcome brief lists step 7 of the argument chain as the film covering chapters 7 to 9 | Stage 4 table | Live in the tutor's context, unlike the outcomes. The film is 7 and 8 and chapter 9 is read, so the chain is wrong for anyone taking the restructured course. Folded into the existing M7 welcome row | Log only |
| 3 | 2026-09-12 | Stage 3's chapter 4 row now names [[Lenses/IABIED - You Don't Get What You Train For]] instead of saying "Chapter 4 lens" | Stage 3 table | Every other row in that table is a link to its lens. The odd one out reads as though the target were undecided, which it is not | Log only |
| 3 | 2026-09-12 | **Chapter 4 connection phase inserted.** New `Phase 3: Connection` before the learning question, which is retitled Phase 4 with its `id::` untouched. Three guards appended to its brief. `tutor_minutes` 15 to 20, `summary_for_tutor` updated to the four-phase shape | [[Lenses/IABIED - You Don't Get What You Train For]] | Inserted rather than promoted: the draft was a diff, only its Phase 3 was new, and its Phase 1 and 2 briefs were placeholders pointing back at the live ones. New UUID on the new segment so the draft can stay in place. The learning question's id must not move, since learner responses are keyed on it | **Suggestions**, filed separately so each could be taken or dropped |
| 3 | 2026-09-12 | New segment written as `#### Question: Open` while the three around it stay bare `#### Question` | same lens | The authoring guide calls the bare form legacy. Following the guide for new content beats matching a form that is on its way out, and converting the existing three would be editing segments learners have already answered. See the parked conditions in section 3 | Decision |
| 3 | 2026-09-12 | Remaining five stage 3 lenses moved from `todo` to `blocked` on the premise test, then back to `todo` the same day | Stage 3 table | **The Lens Tutor is not running on staging**, so the premise test cannot be run at all. Sequencing behind a test that cannot happen buys nothing. Raise the staging gap and schedule a run; until then stage 3 ships untested and section 7 says so | Log only |
| 3 | 2026-09-12 | `summary_for_tutor` fragment shortened, and it no longer names the earlier chapter | [[Lenses/IABIED - You Don't Get What You Train For]] | Enumerating four phases broke the shape of every other lens summary. Naming Chapter 2 there was worse: the summary is lens-level context, so the tutor would hold the answer during Phase 1 and Phase 2, which the Phase 2 brief already warns against pre-empting | Suggestion |
| 3 | 2026-09-12 | **Corrected: the stage 3 table was missing a target lens.** Chapter 11's two threads were listed as one row on [[Lenses/IABIED - Alchemy Not Science]]. They land on two lenses: `Ch 2 grown not crafted` there, and `Ch 3 wanting emerges from training` on [[Lenses/IABIED - Strong Superalignment Objection]], which had no row at all | Stage 3 table | [[Lenses/DRAFT - Recall Threads Proposal]] says it plainly: chapter 11's two outcomes are taught in two separate lenses, so they need a segment each, and ten threads land on nine target lenses rather than eight. The Superalignment lens is live, imported by M5. The table also claimed two lenses carry two threads; only the U3 opener does | Log only |
| 2 | 2026-09-12 | Stage 2 marked untested as well. `done` on that table now says explicitly that it means written, validated and imported, not tested | Stage 2 table, section 7 | The staging gap was first written up as a stage 3 problem, which was wrong. The U3 opener, the film lens changes and the chapter 9 pair are in exactly the same position, and most of section 7's checklist is stage 2 material. Andreas's catch | Log only |
| 3 | 2026-09-12 | **Aztec warrior connection phase inserted.** Same shape as chapter 4: new `Phase 3: Connection`, learning question retitled Phase 4 with its `id::` untouched, three guards appended, `tutor_minutes` 15 to 20, summary fragment added | [[Lenses/IABIED - Define the Aztec Warrior Analogy]] | Closes the last thread into U2. The earlier anchor is `Intelligence as prediction plus steering`, imported by M2, so the thread crosses units. The key turns on generality: the analogy licenses predicting an outcome without the mechanism only if the stronger party's advantage is general rather than one trick, which is what chapter 1 supplied. Expected near miss is that chapter's machine advantages, which is the right chapter and the wrong part, since a list of advantages is the very mechanism the analogy says you do not need | Suggestions, plus one sentence added by Andreas |
| 3 | 2026-09-12 | **British spellings swept.** `favour` and `behaviour` in this file, `practised` in the two connection briefs and in the draft they came from | This file, both connection lenses, [[Lenses/DRAFT - Ch4 with Connection]] | The convention at the top has said American throughout since stage 1 and it slipped anyway. `practised` was inherited from the draft and propagated into both live lenses, which is why the draft was fixed too rather than left as a frozen artifact. One British form remains in the 2026-09-08 row below, `Relabelled`, left alone as someone else's text | Direct on this file and the draft, suggestions on the two lenses |
| 3 | 2026-09-12 | **Coda connection phase inserted, as a variant.** It names the earlier idea instead of hiding it, and asks the student to produce the Introduction's definition unaided and then audit the Coda against it | [[Lenses/IABIED - Path Prediction vs Outcome Prediction]] | The search-and-name pattern cannot work here. The learner-facing Phase 4 question already prints "easy call" twice, both tutor briefs already state the connection as a key concept, and the opener retrieves the same framework earlier in this unit. So the search has no object. The gap that is real is that nobody ever asks whether the Coda's prediction actually meets the Introduction's bar, which is also the conflation the existing brief already worries about. The brief credits noticing that the Coda is explicit about its antecedent where the Introduction's examples were not, and that the grounds differ even where the structure matches. The likeliest wrong answer, that it is not an easy call because we cannot predict when or how, inverts the definition and is corrected in one sentence | Suggestions, plus diction changes by Andreas |
| 3 | 2026-09-11 | **A validator rule shipped mid-session and we are waiting it out.** `# Learning Outcome:` import headings must now carry nothing after the colon. 25 errors on this course | Six IABIED module files | Not ours: they appear in M1, M5 and M6, which this session never touched, and the vault-wide count went 315 to 378 within minutes of a clean run on the same files. Two of the 25 are lines we wrote, which followed the house pattern that has now become an error. **Decision: leave it.** If the rule is still there later we do the sweep; if it is transient we save the work. It is behind the work already done and does not gate anything ahead. Note the consequence: "validation clean on the course" stops being a usable stage gate until this resolves | Deferred |
| 3 | 2026-09-11 | **Broke the file, briefly.** A `summary_for_tutor` contained an unquoted colon and failed the whole frontmatter, not just the field | [[Lenses/IABIED - You Don't Get What You Train For]] | Caught by `validate_content` with `accept_drafts`, not by reading. Added to the conventions at the top | Suggestion, corrected before acceptance |
| 3 | 2026-09-11 | **Five engineering curses connection phase inserted.** Standard position, non-standard prompt: it names the case studies and asks why the curses transfer to AI at all | [[Lenses/IABIED - The Five Engineering Curses]] | The standard wording says the chapter never stops to name what it leans on. False here, since both briefs already flag grown-not-crafted, so that phrasing would have been a lie and the easy answer was pre-supplied. The target is chapter 1: in the case studies the curses are facts about the domain, and in AI two of them become facts about the thing being built. Speed because the substrate is faster, self-amplification because the intelligence explosion feeds itself. Grown-not-crafted is accepted as legitimate but flagged as the easy find, with one push past it | Suggestions, prompt condensed by Andreas |
| 3 | 2026-09-11 | **Corrected, then over-corrected, then widened.** The brief first made AI-assisted AI research the mechanism behind chapter 1's self-amplification; the fix cut the intelligence explosion out entirely; the accepted version keeps the concept and takes either route to it | same lens | Andreas's catch, twice. Recorded at length in section 8, since the source of the original error was an outcome statement standing in for a chapter nobody can open | First correction rejected, second accepted |
| 3 | 2026-09-11 | **Two stale module labels fixed.** Both briefs called grown-not-crafted an "M1 callback" | same lens | Chapter 2 left M1 for M2 in stage 1d, so both were wrong and both were live in the tutor's context. The dependency scan looked for chapter-range claims and missed module labels sitting inside lens briefs, which is a different shape of the same breakage. A sweep for `M1` through `M7` inside lens briefs closes stage 3 | Suggestions |
