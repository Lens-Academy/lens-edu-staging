---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# CV1 Restructure: change log and plan

Git records what changed. This file records why, what it depended on, and what we decided against. Update it alongside the change it describes.

The plan this file carries out is [[CV1 Streamlining Proposal]]. Elias reviewed it on 2026-10-02, and his comments are in that file.

---

## Summary

**What this is.** Streamlining Compute Verification 1 (CV1) so a learner can keep up with it for five units. The work is about form, not substance: rebalance the load, split pages too long to hold attention, give each question the format that fits it, close a promise the course currently keeps in Compute Verification 2, and make Lens's own text read plainly and consistently. No learning outcome is rewritten, no published id changes, and nothing is retired.

**Status, 2026-10-20.** Planning. Stage 1 (measure) is done, and was re-run today because others have changed the course since. Stage 2 (agree the plan) is in progress. Elias agreed with most of the proposal and settled decisions 1, 4 and 5; nine of his comments are now flagged as closed in the proposal. Several of his other points are with Andreas to take up with him directly, and three replies of ours are waiting on Elias. No course file has been edited by this project yet.

**Status, 2026-10-21.** Andreas settled most of what was waiting on him (section 1, decisions A1 to A5) and removed the resolved comments from the proposal. Still open: two of Elias's points that Andreas asked us to explain (Q6, Q10), how much XLab framing goes beyond section numbers (Q8, with an inventory in section 3), and three threads waiting on Elias, each of which can be worked around (section 2). There is no attributed edit by Elias to a CV1 file, and no new comment from him in the proposal, since 2026-10-04.

**Since the proposal.** Others changed CV1 between 2026-10-08 and 2026-10-20 (section 3). Two of those changes affect the plan. The unit 1 essays are now a choose-one group instead of two optional lenses, so one essay is required, which reopens decision 3. And every lens's time estimate was replaced on 2026-10-09, which fixes some of stage 1's misses but not the largest ones (section 6).

**Where things are.**

| Section | What it holds |
|---|---|
| 1 | Decisions taken, who took them, and where, so they are not re-argued |
| 2 | Decisions and questions still open, with who each one waits on and what it holds up |
| 3 | Dependency scan: others' changes since the proposal, shared files, the validator baseline |
| 4 | Order of execution |
| 5 | **The stage inventory, with statuses. Start here** |
| 6 | Measurements: stage 1 re-run on 2026-10-20 |
| 7 | Testing |
| 8 | The chronological log: every change, why, and how it landed |
| 9 | Items beyond this project, grouped by who or what would move them |

**Stage numbers are the proposal's.** They are identifiers. If stages run out of order, section 4 says why.

---

**Status key:** `todo`, `drafted`, `in progress`, `done`, `blocked`, `parked`, `dropped`.

**Dates:** full `YYYY-MM-DD` on every entry. Where an entry was written up later than the work it describes, the row says so.

**Section 8 is sorted by date, not by stage.** Do not re-sort it. The stage tables in section 5 show the state of each stage.

**Line numbers drift.** The replies in the proposal cite line numbers as of 2026-10-08, and several have moved since (the meeting 1 run-sheet line on optional essays was line 224 and is now line 233). This file cites sections and steps where it can.

**Picking this up cold?** Read [[CV1 Streamlining Proposal]] with its comments, then [[AIRF Restructure - Working Preferences]], then [[AI Guide/Course Authoring]]. The conventions below came out of this work and the AIRF one, and few of them are obvious from the files.

Specific to CV1:

- **The course is "Compute Verification 1".** "Part 1" stays only where it tells learners this is the first course of a sequence. *Andreas, 2026-10-01.*
- **XLab's text stays XLab's.** Changes to it are limited to labels, spelling and page boundaries. The plain-language pass targets Lens's own text and reaches XLab's only where a passage proves to be a problem. *Andreas, 2026-10-01.*
- **Name XLab only in the course welcome and the Works cited callout.** The course file declares `partner-name: XLab`, and the validator rule `course-graph.partner-name-in-tutor-field` flags the name anywhere tutor-facing, such as tutor summaries and feedback briefs.
- **Compute Verification 2 is reference, not a model.** Content CV1 lacks may come from it; its structure is not adopted, because it is unfinished. *Andreas, 2026-10-01.*
- **Andreas writes the plain-language rewrites himself; AI flags.** AI's part in stage 6 is to find and flag the passages that read most like AI, not to rewrite them. Elias, 2026-10-02: "if you have AI do it it sometimes makes it worse if you are not carefully supervising." *Andreas, 2026-10-21.*
- **Learners cannot see `optional:: true` on a question.** The prompt has to say so. *Andreas, 2026-10-01.* The feedback modules are the deliberate exception: their "anything else" questions are optional and the page does not say so, per Elias's note in each.
- **Use a choice group, not optional lenses with "pick one" in the text.** `# Choose: 1` (or `# Choose: 3 of 5`) over `## Lens:` entries; the module's time counts k times the average of the options. See [[AI Guide/Writing Modules]]. Unit 1 already uses one.
- **Replies in comment threads are neutral and factual, not written in anyone's voice, and link the lens instead of naming it.** Some of Elias's points Andreas takes up with him directly; check section 2 before replying in the proposal. *Andreas, 2026-10-08.*
- **Several AIs work in this vault.** James's AI has run sweeps on tags and citations and took part in the 2026-10-09 re-timing. Andreas and his AI run the meeting doc text review, logged in [[Meeting Doc Text Review Log]]. Check a file's recent history before editing it, and do not repeat a sweep someone else is running.
- **Draft replies and new text for review before posting.** *Andreas, 2026-10-08.*

Carried over from [[AIRF Restructure Log]], which gives the reasons:

- Say "unit", never "week", in learner-facing text.
- American spelling throughout Lens's own text. Grep before handing anything off, with AIRF's case-insensitive pattern extended with centre, programme, practise, distil and licence. `from::` and `to::` anchors and quotations from sources are exempt.
- No em dashes.
- Outcomes carry no module labels.
- Never write a literal comment marker into this file, of either kind.
- Block moves go insert first, delete second.
- Do not delete or retire other people's work without asking. Edit around their comments, never through them.
- Always set `tldr::`. Quote any frontmatter value that contains a colon.
- Validate course-scoped and unscoped. Files tagged `wip` drop out of the course-scoped run, and the course file itself is tagged `wip`.
- Build a sweep's worklist from per-file counts of both fields, not from a search for the one being removed.
- Open the relay session under Andreas's name, and check how each edit landed rather than assuming.

**Working practice.** An edit that replaces or deletes someone else's text goes in as a pending change for review; the relay routes it that way on its own, but check. New files we author are written directly. Each row in section 8 says which it was.

---

## 1. Decisions taken

Each entry is the decision, who took it and where, and what it commits us to.

### From Andreas, 2026-09-30 to 2026-10-08

- **Form and shape, not substance.** Holes are filled only where substance is lacking.
- **Learning outcomes are not ours to rewrite.** Units 3 to 5 have none, and that is recorded as a hole rather than filled. Andreas does not expect new outcomes at the moment and is double-checking (2026-10-08).
- **Everything happens on staging.** Nothing reaches learners until it is promoted after the current cohort, so no step is timed around a cohort.
- **The old five-module course is deprecated**, now at [[courses/archived/Compute Verification]], so edits to lenses CV1 shares with it are fine.
- **Question formats are reassessed one by one**, not ungraded wholesale, starting with the questions whose answer key is visible on the page. Optional status must become visible.
- **The meeting doc agent checks run**, since the docs are Markdown in the vault.
- **Decisions without Elias's input are settled later**, before the stage each one holds up.

### From Andreas, 2026-10-21

On the points he took up with Elias directly.

| # | Decision | Commits us to |
|---|---|---|
| A1 | **Answer keys visible on the page are fine.** Most of those exercises will be ungraded, so there is nothing to game beyond the learner's own understanding. Settles Q5 | Stage 4: the ten questions with the key on the page are ungraded and keep the key as a self-check |
| A2 | **Longer questions with no key on the page keep their grade.** Units 3 to 5 have no learning outcomes, so these questions serve as stand-in objectives. This is the compromise on grading object-level questions. Settles Q7 | Stage 4, step 2: the groups are re-sorted by this rule before the per-question calls |
| A3 | **"No mentions to XLab" means framing, not attribution.** Credit in the overview and the Works cited footers stays. What goes is language that makes the course feel as if it were taken directly from XLab. How much that covers beyond section numbers is to be discussed, starting from the inventory in section 3 | Stage 7, step 2. Narrows Q8 |
| A4 | **Andreas writes the plain-language rewrites himself.** AI detects and flags the passages that read most like AI, as in the meeting doc text review. Settles Q9 | Stage 6, step 3 becomes flag, then Andreas rewrites |
| A5 | **The unit 1 essay may go back to optional, depending on load.** Decided once the load has been measured again | Q1 parked until stage 8 |

### From Elias's review of the proposal, 2026-10-02

| # | Decision | Where he said it | Commits us to |
|---|---|---|---|
| D1 | Unit 5 becomes two modules, not two submodules: "I think two modules is better (less unnecessary nesting, unless the nesting is meaningful" | Decisions table | Stage 3, step 2 |
| D2a | Strategic Foundations becomes four pathway lenses: "good"; "4 lenses" | Stage 3, step 3; decisions table, row 2 | Stage 3, step 3. The written output is still open (section 2, Q2) |
| D4 | The longest core pages are split: "good"; "split for sure" | Stage 3, step 5; decisions table, row 4 | Stage 3, step 5, after the step 1 test |
| D5 | The claim ledger is closed in CV1: "both fine. Your decision (so probably close)" | Decisions table, row 5 | Stage 5 |
| E1 | The plain-language pass goes ahead: "Should be fixed" | "Text that takes decoding" | Stage 6, under the supervision rule above |
| E2 | The drift fixes go ahead: "should be fixed" | "Drift" | Stage 7 |
| E3 | Renumbering and naming in CV1 are ours to do: "You could do that" | Stage 2, step 1 | Stages 3 and 7 |
| E4 | Time estimates, session splits and announcements are to be fixed wherever there are problems | "Load is uneven", first comment | Stages 3, 8 and 9. What "announcement" means is open (Q10) |
| E5 | XLab's section numbers go, replaced by internal numbering or none | "Learners meet labels they cannot resolve" | Stage 7, step 2. His "no mentions to XLab" in the same comment is open (Q8) |

D4's step 1 test still runs first. Elias's answer settles whether to split; the test settles whether splitting keeps learners' stored answers.

---

## 2. Decisions and questions still open

| # | Question | Where it stands | Waiting on | Holds up |
|---|---|---|---|---|
| Q1 | **Unit 1 essay: required pick-one, or optional?** (decision 3) | Since 2026-10-10 the module offers the two essays as a choose-one group, lines 18 to 22 of [[modules/XLab Verification P1 W1 Building verification intuitions]], so one essay is required, and the course file counts it at the average of A and B. Andreas noted it overlaps with the unit 1 outcome test, [[Learning Outcomes/Stress-testing a verification proposal]], which asks for 350 to 550 words. **Parked, 2026-10-21 (A5):** it may go back to optional, depending on the load. Until then the Plan A intro and the meeting 1 run-sheet, which says every essay prompt is optional, are left as they are | Stage 8's measurement, then Andreas | Stage 3, step 4 |
| Q2 | **Strategic Foundations' written output: drop, keep, or keep as a first draft for unit 4?** | Elias asked why drop it. Our reply of 2026-10-08 explained that it duplicates required unit 4 work and suggested keeping it as a draft to revise. Both comments were removed from the proposal on 2026-10-21 without an answer from Elias, so which way this went is not recorded | Andreas: settled, and if so which way? | Stage 3, step 3 (the output only; the split can go ahead) |
| Q3 | **XLab source footers, and the hotlinked theories-of-change image** | Elias: "not sure what this is and if I want this". Our reply of 2026-10-08 explains both and suggests keeping the footers and copying the image into Lens. No answer as of 2026-10-21. A3 already keeps attribution, which covers the footers. **Work-around:** keep every footer, copy the image into Lens in stage 7, and leave the six notes signed Elias's AI in place until he answers, since learners cannot see them. The two leftover order notes in the same thread stay for the same reason | Elias, for the notes only | Nothing, with the work-around |
| Q4 | **The twelve redirect lenses no module imports** | Elias: "Unsure what this is". Our reply of 2026-10-08 explains them. Nothing depends on them | Elias | Nothing. See section 9 on trashing them |
| Q5 | **Answer keys visible on the page** | Elias: "Don't think that's a problem (if they want to cheat they can look, but it won't help them with understanding". The proposal's default for these ten is to ungrade them | Andreas, with Elias | Stage 4, step 2 |
| Q6 | **The generic feedback brief, and feedback only on request** | Elias: "Don't think those things are so bad. But if you have a strong opinion, I would defer to you" | Andreas, with Elias | Stage 4, step 4 |
| Q7 | **Grading object-level questions** | Elias: "If it's an object level question I like grading as it helps learners to estimate how close their answer is". The proposal says to prefer ungraded when in doubt, so the two defaults need reconciling | Andreas, with Elias | Stage 4, step 2 |
| Q8 | **How far "no mentions to XLab" goes** | Learner-facing text only, or also tutor summaries (which the validator already flags), the Works cited footers (Q3) and the meeting docs' "XLab's feedback form" lines? | Andreas, with Elias | Stage 7, steps 2 and 5; stage 9 |
| Q9 | **What "Wouldn't have AI do this" covers** | Said of stage 6, step 4: listing XLab passages that prove to be a problem, and sending each to XLab's feedback form. Which part he means is unclear | Andreas, with Elias | Stage 6, step 4 |
| Q10 | **What "announcement" means** in "Fix time estimates + session splits + announcement" | Possibly the next-unit previews in the meeting docs, possibly something else | Andreas, with Elias | Stages 8 and 9 |
| Q11 | **Learning outcomes for units 3 to 5** | Elias: "Should be fixed as well at some point". Andreas is checking whether that is in scope | Andreas | Nothing in this project by default (section 9) |
| Q12 | **Preparing Compute Verification 2** | Elias: "Shouldn't that be prepared too?" Andreas is raising it separately; no reply was posted in the proposal | Andreas | Nothing in this project (section 9) |
| Q13 | **Is the imported MIRI paper the v3 the curriculum pins?** | Not checked yet | Us | Stage 8's estimate for that lens |

---

## 3. Dependency scan

Reference, not a stage. Updated 2026-10-20.

### Others' changes since the proposal, 2026-10-08 to 2026-10-20

None of these are ours. Found by diffing every CV1 file between the staging commits of 2026-10-09 03:55 UTC and 2026-10-20 19:31 UTC.

- **The course moved** to [[courses/user-facing/Compute Verification 1]] on 2026-10-10, with relative links updated, and the old course to `courses/archived/`. Relay, unattributed.
- **The unit 1 essays became a choose-one group** on 2026-10-10. Relay, unattributed. See Q1.
- **Every lens was re-timed** on 2026-10-09, in commits from the relay and from James's AI: `duration_minutes` became `reading_minutes` plus `tutor_minutes`, and the course file's note now reads "re-timed 9 Oct 2026 (tutor time per exercise, outcome tests included, Option A/B at their average): U1 260 min, U2 125, U3 190, U4 190, U5 195". Unit 5's first page now says "about 195 minutes, split into two sessions", so the three disagreeing sets of unit 5 times the proposal found now agree. Section 6 has what the new figures leave unresolved.
- **Citation tidying**, 2026-10-09 to 2026-10-19, in commits from James's AI and the relay: adjacent excerpts from the same article merged into one segment in the precedents, accounting and where-trust-lives lenses; the attestation lens's Sources callout folded into its Works cited; "arXiv:" became "arXiv" in citations.
- **Tags changed by James's AI, 2026-10-19:** five lenses went from no tag to `wip` (actor edges, Context Distiller, accounting, attestation, authorization), and the chip supply chain lens from `wip` to `work-in-progress`. The CV1 learning outcomes gained a `concept` field and the `work-in-progress` tag. A `wip` file drops out of the course-scoped validator run, so these five lenses' issues are now invisible there.
- **A tutor-feedback note from James's AI** on the feedback brief in [[Lenses/XLab Verification - v-hw-authorization]] (feedback #204, 2026-10-10): the tutor told a learner that device identity is not on the question's twelve-item list, but it is, and the note suggests a line for the brief. Stage 4 takes it up when it rewrites that brief.
- **Meeting docs, 2026-10-10 and 2026-10-11:** James's AI added an explanation of accountability buddies to meeting 1 on 2026-10-10, and on 2026-10-11 Andreas's AI and the relay edited all five docs as part of the meeting doc text review. The opening check-in questions were shortened, the tutor help line was reworded, and meeting 1's buddy explanation moved into an "Accountability buddy setup" section for the navigator. That review's log records that CV1's docs are retitled "when CV1 gets its own pass", which is stage 7, step 4 here. In meeting 2 only the opener and the help line changed, so the table and navigator-note mismatches stage 9 lists still stand.

### Earlier changes by others that the plan accounts for

- **Feedback modules for units 1 to 5**, added by Elias on 2026-10-04. Their questions are required except the "anything else" ones, and the page deliberately does not say so. Stage 4, step 3 leaves them alone.
- **Learner surveys** for meetings 1 to 4 are the "(meeting only)" variant of the shared post-meeting survey.

### Shared files

- **[[Lenses/Four Background Claims]]** is not touched. Two modules outside Compute Verification import it.
- **Compute Verification 2 shares no lens with CV1** (checked 2026-10-08). Its [[Lenses/XLab Verification - v-hw-policy-studio]] holds the claim-ledger resolution that stage 5 copies, not moves.
- **The archived five-module course** shares lenses with CV1; edits to them are fine (section 1).

### Validator baseline, 2026-10-20

Course-scoped, production: **0 errors, 16 warnings.** Ten are citation and repeated-block warnings in four article files, not ours. Six are the partner-name rule in [[Lenses/XLab Verification - v-hw-claim]], [[Lenses/XLab Verification - v-hw-measuring-use]] and [[Lenses/XLab Verification - v-hw-reconstructing-run]]. The proposal's baseline of 2026-10-02 was 25 errors, every one from a `wip` tag, and 31 warnings; the drop came from others' changes, not ours. Lenses tagged `wip` will raise more partner-name warnings when the tag comes off; stage 4 removes the name from the generic brief anyway. The `wip` category and the unscoped run have not been baselined yet; stage 4 does that before its first edit.

---

## 4. Order of execution

The proposal's order stands: measure, agree, structure, question formats, claim ledger, plain language, consistency, time figures, meeting docs, test.

- **Structure comes first** so every later edit runs against final pages.
- **Question formats come before plain language** because a reworded prompt has to take its feedback brief with it, and the brief changes in stage 4.
- **The mechanical passes run last among the content stages** so they catch everything written before them.
- **Time figures follow the content**, and the meeting docs follow the time figures, because the docs repeat them.

What can start now without waiting on section 2: stage 3, step 1 (the test) and step 2 (unit 5); the Strategic Foundations split without its output; stage 4, steps 1 and 3; and stage 5. Nothing has started.

---

## 5. Stage inventory

### Stage 1, measure

| Item | Status |
|---|---|
| Word counts against stated times, every CV1 lens | `done` 2026-10-01; re-run 2026-10-08 (no change) and 2026-10-20 (section 6) |

### Stage 2, agree the plan

| Item | Status |
|---|---|
| Forewarn Elias: the notes signed Elias's AI that the plan touches | `done`, in the proposal, reviewed 2026-10-02 |
| Collect his input on decisions 1 to 5 | `in progress`. 1, 4 and 5 settled; 2 settled for the split, open for the output (Q2); 3 reopened (Q1) |
| Replies to his comments that rest on a misunderstanding | `done` 2026-10-08: footer and image, order notes, twelve redirect lenses, Strategic Foundations output, essay. The essay reply is now out of date (Q1) |
| Flag closed loops in the proposal | `done` 2026-10-20, nine comments (section 8) |
| Open this log | `done` 2026-10-20. The working preferences are folded into the conventions above rather than kept in a second file; [[AIRF Restructure - Working Preferences]] applies as written |
| MIRI paper version (Q13) | `todo` |

### Stage 3, structure

| Step | Files | Status |
|---|---|---|
| 1. Answer-survival test: does an answer survive its question moving to another lens? | A test lens on staging; needs a signed-in tester | `todo`. Blocks step 5 |
| 2. Unit 5 into two modules (D1) | [[modules/XLab Verification P1 W5 Hardware verification]] keeps its id and the first half; one new module; the course file | `todo`, unblocked |
| 3. Strategic Foundations into four pathway lenses (D2a) | [[Lenses/XLab Verification - v-strategic-foundations]], three new lenses, [[modules/XLab Verification P1 W2 Strategic foundations]] | `todo`. Split unblocked; output `blocked` on Q2 |
| 4. Unit 1 essay | [[Lenses/XLab Verification - v-intuitions]], the course file note, meeting 1 run-sheet | `blocked` on Q1 |
| 5. Split the longest core pages (D4) | Candidates: [[Lenses/XLab Verification - v-scoping-anatomy]] (81 minutes now), [[Lenses/XLab Verification - v-context-distiller]] (90), [[Lenses/XLab Verification - v-scoping-effective-feasible]] (55, was 75), [[Lenses/XLab Verification - v-precedents]] (41, was 75) | `blocked` on step 1. The re-timing shortened two candidates, so which pages qualify gets rechecked first |

### Stage 4, question formats

| Step | Status |
|---|---|
| 1. Worklist from per-file counts of both fields, with graded, key visible and optional recorded per question | `todo`, unblocked. Baseline in the proposal: 44 graded segments in 20 lenses |
| 2. Sort into four groups with defaults | `blocked` on Q5 and Q7 |
| 3. "Optional:" at the head of every optional prompt; feedback modules excluded | `todo`, unblocked |
| 4. Convert each question in one edit; replace the 21 generic briefs; `force-feedback:: first` | `blocked` on Q6. Includes the #204 fix in the authorization lens |
| 5. Outcome tests left as they are | `done` by decision |

### Stage 5, close the claim ledger in CV1 (D5)

| Step | Status |
|---|---|
| 1. Closing lens at the end of unit 5, with the ledger widget and XLab's resolution | `todo`, unblocked. Lands in the second unit 5 module, so it follows stage 3, step 2 |
| 2. Point the promise at it, on unit 5's first page and in its tutor summary | `todo` |

### Stage 6, plain language (E1)

| Step | Status |
|---|---|
| 1. Mark what is Lens's text and what is XLab's | `todo` |
| 2. Spoiler test on every tldr, starting with [[Lenses/XLab Verification - v-actor-edges]] | `todo` |
| 3. Rewrite Lens's text, one passage at a time, each reviewed | `todo` |
| 4. List problem XLab passages | `blocked` on Q9 |

### Stage 7, consistency (E2, E3)

| Step | Status |
|---|---|
| 1. Unit, never week | `todo` |
| 2. XLab section numbers out of headings and link labels (E5) | `todo`; scope of XLab mentions `blocked` on Q8. Rechecked 2026-10-20: the eight hardware headings still carry 2.1 to 2.1.7 |
| 3. Module titles in one style | `todo` |
| 4. "Compute Verification 1" wherever the course is named, including the meeting doc titles the text review left for this pass | `todo` |
| 5. One rule for XLab source footers | `blocked` on Q3 |
| 6. American spelling | `todo`. Recount at the start; the proposal's 89 lines in 26 lenses predate the re-timing sweep |
| 7. Em dashes | `todo` |

### Stage 8, time figures (E4)

| Step | Status |
|---|---|
| 1. Measure again | `todo`, after stages 3 to 7 |
| 2. Re-estimate changed lenses, starting with section 6's remaining misses | `todo` |
| 3. Update every figure that repeats them | `todo` |

### Stage 9, meeting docs

| Step | Status |
|---|---|
| 1. Meeting 2: tables and navigator notes into line with the prompts | `todo`. Still needed after the 2026-10-11 edits |
| 2. Meeting 3: the missing break before Room 3 | `todo` |
| 3. Meeting 1: split the Room 4 navigator note | `todo`. Recheck first: the new buddy setup section may already cover it |
| 4. Time figures and next-unit previews from stage 8 | `todo`. Possibly what Elias means by "announcement" (Q10) |
| 5. Stages 6 and 7 applied to the docs | `todo`. Participant wording belongs to the meeting doc text review; coordinate rather than duplicate |
| 6. The three agent checks on all five docs | `todo`, last |

### Stage 10, test on staging

See section 7.

---

## 6. Measurements: stage 1 re-run, 2026-10-20

Same method as the proposal: words a learner is asked to read, page text plus each embedded excerpt, at 200 words a minute, with nothing added for questions, widgets or writing. A floor at or above the stated time means the estimate cannot be right. Stated times are now reading plus tutor minutes.

| Lens | Stated, 2026-10-01 | Stated now | Reading floor | Now |
|---|---|---|---|---|
| Strategic Foundations (optional) | 80 | 74 | 195 | Still off by more than two and a half times |
| The MIRI draft agreement, full paper (optional) | 75 | 55 | 160 | Further off than before, nearly three times |
| Chip supply chain (optional) | 115 | 55 | 232 if read whole | Learners read only the stages they choose, so the total is not a fair test, but 55 needs a stated basis |
| The trusted statement | 25 | 33 | 15 | Plausible: 18 minutes for the nine-part answer |
| Measuring use | 25 | 40 | 23 | Plausible: 17 minutes for the four-part answer |
| Where trust lives | 30 | 57 | 14 | Resolved |
| Context Distiller | 75 | 90 | 21 to 51, by report | Plausible for most reports; still check the IAEA and BIS reports with the clipping work |

By unit, core work only. The lens sum counts the unit 1 essay at the average of A and B, as the choice group does, and leaves out outcome tests, which the course file's figures include.

| Unit | Course file now | Lens sum | Reading floor |
|---|---|---|---|
| 1 | 260 | 205 | 41 plus the Bengio video |
| 2 | 125 | 110 | 42 |
| 3 | 190 | 188 | 67 |
| 4 | 190 | 188 | 40 to 70, by report |
| 5 | 195 | 195 | 73 |

**A correction to the proposal.** Its unit 1 floor of "75, including a 15-minute video" does not reproduce. The saved 2026-10-01 counts give 6,358 words of core reading, a floor of 32 minutes, plus the video. The cause was not found. The proposal's conclusion about unit 1 does not depend on the figure, but the figure should be corrected there.

**What stage 8 still has to do:** honest times for each Strategic Foundations pathway once it is split, the MIRI paper, and a basis for the chip supply chain figure; and reconciling the unit 1 lens sum (205) with the course file (260), a gap of 55 minutes that outcome tests alone may not explain.

---

## 7. Testing

Needs a signed-in tester on staging. Nothing is run yet.

- [ ] Stage 3, step 1: an answer survives its question moving to another lens
- [ ] The unit 1 choice group shows both essays, completes with one, and the module's time shows the average
- [ ] An ungraded question still completes its lens, including one last in its module
- [ ] A question that stays graded still shows its score
- [ ] Skipping an optional question still lets the lens complete
- [ ] `force-feedback:: first` sends feedback once, and returning to the lens does not send it again
- [ ] Both unit 5 modules appear ahead of the unit 5 meeting, and the closing ledger lens works
- [ ] The Strategic Foundations lenses appear as optional
- [ ] A learner's earlier answers are still in place, which confirms no id changed
- [ ] Course-scoped and unscoped validation: no new production errors, and no partner-name warnings from text we wrote

---

## 8. Log

| Stage | Date | Change | Files | Why | How it landed |
|---|---|---|---|---|---|
| 1 | 2026-09-30 | Read the AIRF log and working preferences, the CV1 course, modules, lenses, outcomes and meeting docs, and the notes signed Elias's AI | None | Catching up before proposing anything | Read only |
| 1 | 2026-10-01 | Measured every CV1 lens: words against stated time | None. Counts from the staging repository | Strategic Foundations and unit 5 looked too long to hold attention; the stated times could not be trusted to show it | Read only |
| 2 | 2026-10-02 | Wrote the proposal as a lens draft, then moved it to a plain document | [[CV1 Streamlining Proposal]]; the draft lens went to `_trash` | Lens segment markers rendered every heading as "Text". Reordered into ten stages in execution order at Andreas's request, so nothing is corrected before it is identified | Direct; both files ours |
| 2 | 2026-10-02 | Elias reviewed the proposal: 22 comments | [[CV1 Streamlining Proposal]] | | His comments |
| 2 | 2026-10-08 | Re-measured | None | Check before replying | Read only; no change from 2026-10-01 |
| 2 | 2026-10-08 | Posted five replies to Elias's comments: the footer and image, the order notes, the twelve redirect lenses, Strategic Foundations' output and the essay | [[CV1 Streamlining Proposal]] | Each answers a point that rested on a misunderstanding, or one Andreas asked us to answer, with quotes and linked lenses. Drafts were rewritten to a neutral register at Andreas's request. No reply on Compute Verification 2, which Andreas is raising separately | Direct; comments by Andreas's AI |
| 2 | 2026-10-20 | Surveyed others' changes to CV1 since 2026-10-08, re-measured, and took the validator baseline | None | The course changed under the plan; section 3 and section 6 | Read only |
| 2 | 2026-10-20 | Opened this log | [[CV1 Restructure Log]] | Stage 2, step 3, on the AIRF pattern, to lay out the work before starting it | Direct; new file |
| 2 | 2026-10-20 | Flagged nine of Elias's comments as closed, each with a short reply pointing here: text that takes decoding, drift, renumbering, the Strategic Foundations split, splitting long pages, supervising AI rewrites, and decisions 1, 4 and 5 | [[CV1 Streamlining Proposal]] | The relay cannot resolve a Markdown comment, so a reply marks the loop as closed. Comments still open are listed in section 2 | Direct; comments by Andreas's AI |

---

## 9. Beyond this project

Items that came up in this work but are not part of it. Nothing here blocks the restructure.

### Andreas is taking these up

- **Learning outcomes for units 3 to 5** (Q11). Elias would like them at some point. Adding outcomes is new substance, which this project does not do unless that changes.
- **Preparing Compute Verification 2** (Q12). For whoever takes it on: the CV2 course file says no meeting doc template is linked, it has no outcomes, and it has no learner survey.

### Worth raising with XLab, or about XLab

- **Licensing.** XLab's source repository has no license file and marks its package private, while CV1's overview calls the curriculum "open-source". Worth confirming the terms with XLab before relying on that word.
- **Where learner feedback goes.** All five meeting docs point learners to "XLab's feedback form", and stage 6, step 4 would send problem passages there too, while Lens now has its own feedback modules for every unit. Which channel feedback should go to is a question for Andreas and Elias, and it may settle Q8 and Q9 as well.

### Housekeeping, when wanted

- **The twelve redirect lenses** (Q4). If Elias no longer needs them, they can go to `_trash`. The relay refuses to delete a file while links point at it, and our 2026-10-08 reply in the proposal links all twelve, so those links come out first.

### Not ours, but worth knowing

- **Ten validator warnings in four CV1 article files** (citation definitions that hold only a URL, and one repeated block). Article files go through the import pipeline, not this project.
- **Anki cards.** The course file's improvement notes mention cards a participant made for the first two units, shared on 2026-09-19.
- **Capstone** still has no learner survey, per the course file.

### To raise with whoever maintains the relay

- **A Markdown comment cannot be resolved from the relay.** The comments tool handles HTML pages only. Closed loops are flagged with a reply instead, which leaves the thread on the page.
