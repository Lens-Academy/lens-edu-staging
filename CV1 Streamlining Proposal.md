---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# CV1 streamlining: proposal

Compute Verification 1 does not need new substance. It needs a shape a learner can keep up with for five units. This proposal sets out what gets in the way, what stays fixed, and then the work itself as ten stages in the order they would run, each with its steps in sequence. Decisions still open are collected at the end, each marked with the stage it holds up.

All of it happens on staging. Nothing reaches learners until it is promoted after the current cohort finishes, so no step has to be timed around a cohort.

## What gets in the way

Six things, none of them about what the course teaches.

**Load is uneven, and the figu{>>{"author":"Elias","timestamp":1790945448081}@@Yes, aware of this. Just didn't have the time yet to fix everything.\n\nFix time estimates + session splits + announcement wherever you see problems<<}res for it are unreliable.** Unit 5 is one module of nine lenses, although its own first page says the work should be split into two sessions. Strategic Foundations is a single page holding seven embedded readings, about 39,000 words, with two more linked, and it is labeled 80 minutes. For unit 5, the course file, the lenses and the unit's first page give three different sets of times. Stage 1 has the measurements.

**Learners meet labels they cannot resolve.** XLab's section numbers (2.1.3, 1.2.2) appear in eight hard{>>{"author":"Elias","timestamp":1790945493409}@@Should be replaced by internal numbering or no numbering + no mentions to XLab<<}ware lens headings and in link labels or "Section" and "Module" references in six more lenses, and CV1 never shows the numbering they belong to. The overview, the unit 5 module title and four lenses say "week" where the course runs in units.

**One promise is kept in a different course.** Unit 5 opens with a claim ledger and tells learners to keep their answers for the end of the section. The return happens in Compute Verification 2, in [[Lenses/XLab Verification - v-hw-policy-studio]]. A learner who takes only CV1 never sees the resolution, and CV1's tutor is told not to give it.

**Question formats that work against themselves.** 44 question segments outside the learning outcomes produce a score. In ten of them the answer key sits on the same page directly below the qu{>>{"author":"Elias","timestamp":1790945549515}@@Don't think that's a problem (if they want to cheat they can look, but it won't help them with understanding<<}estion, in a collapsed callout the learner can open at any time, or in the next paragraph. Twenty of the 44 share one generic feedback brief, and no question in the course se{>>{"author":"Elias","timestamp":1790945596418}@@Don't think those things are so bad. But if you have a strong opinion, I would defer to you<<}nds feedback unless the learner asks for it. Learners also cannot see which questions they may skip, because the platform does not show the optional flag: of the 20 optional questions in core lenses, 12 say so in their prompt, 4 only in the text above them, and 4 nowhere. Eighteen of those 20 are graded.

**Text that takes decoding.** Much of what Lens wrote around XLab's lessons was drafted{>>{"author":"Elias","timestamp":1790945627183}@@Should be fixed<<} by AI and reads like it: dense sentences, compressed metaphors and closing aphorisms that a participant has to unpack before they can use them. At least one tldr gives away the result of the exercise it introduces.

**Drift.** Mixed British and American spelling, em dashes in two lenses, module title{>>{"author":"Elias","timestamp":1790945636399}@@should be fixed<<}s in three styles, the course named both "Compute Verification 1" and "Compute Verification Part 1", and a meeting 2 doc whose prompts were rewritten without its tables or navigator notes.

## What stays fixed

- **No learning outcome is rewritt{>>{"author":"Elias","timestamp":1790945647886}@@Should be fixed as well at some point<<}en.** Units 3 to 5 have none, and that is recorded as a hole rather than filled.
- **No published id changes, and nothing is retired.** Lenses and modules keep their ids. Slugs stay too: they still point at the right content, and module-level `slug-aliases` was never confirmed (see [[AIRF Restructure Log]], section 3), so renaming one would break every saved link to it once promoted.
- **XLab's text stays XLab's.** Changes to it are limited to labels, spelling and page boundaries. The plain-language work in stage 6 targets Lens's own text and reaches XLab's only where a passage proves to be a problem.
- **[[Lenses/Four Background Claims]] is not touched.** Two modules outside Compute Verification import it.
- **{>>{"author":"Elias","timestamp":1790945706588}@@Shouldn't that be prepared too?<<}Compute Verification 2 is reference only.** It is unfinished, so its structure is not adopted.
- **Release status is not ours.** The course-scoped validator shows 25 production errors, every one caused by a `wip` tag, plus 31 production warnings. Fourteen of those warnings come from a rule that appeared after 2026-09-30 and flags the partner name "XLab" in tutor-facing text, such as tutor summaries and the generic feedback brief; stages 4 and 6 rewrite that text, and lenses still tagged `wip` will raise more of the same once the tag comes off. That is the baseline, and apart from those warnings falling, it must not change.

## The work, in order

Every stage ends with `validate_content`, run course-scoped and unscoped.

### Stage 1. Measure the course (done for this proposal)

Each lens's stated time was checked against a word count of everything it asks a learner to read: the text on the page and the assigned excerpt of every embedded article. The count becomes a reading floor at 200 words a minute, a fast pace for policy and academic text, with nothing added for questions, widgets or writing. A floor at or above the stated time means the estimate cannot be right. The authoring guide asks for estimates from what learners actually do rather than from a formula, so the floor is a test, not a replacement. Counts were taken from the staging repository, which mirrors the relay.

**Most core work passes.** Across the course the floor sits well below the stated time, leaving plausible room for questions and exercises. The exceptions:

| Lens | Stated | Reading floor | What it means |
|---|---|---|---|
| The trusted statement (unit 5) | 25 | 16 | Nine minutes left for a nine-part written answer |
| Measuring use (unit 5) | 25 | 23 | Two minutes left for a four-part written answer |
| Context Distiller (unit 4) | 75 | 21 to 51 | Depends on the report picked; with the IAEA or BIS report, plus the clipping work, it very likely runs past 75 |

Where trust lives (30 minutes, floor 14, then a sixteen-part design comparison) is probably low as well. Unit 5's first page puts its core at 165 to 180 minutes against the course file's 155, which points the same way.

**Two optional readings are off by two to two and a half times.**

| Lens | Stated | Words | Reading floor |
|---|---|---|---|
| Strategic Foundations | 80 | 39,000 | 195 |
| The MIRI draft agreement, full paper | 75 | 32,000 | 161 |

Strategic Foundations is the starkest case. Its four pathways run about 11,250, 17,750, 4,050 and 5,900 words, so even a learner who reads only the pathway they are weakest on faces 20 to 89 minutes of reading at the fast pace. The second pathway alone is longer than the page's stated total. The two linked readings are not counted.

The chip supply chain lens (optional, 115 minutes) embeds about 46,000 words, but it tells learners to read only the stages they want, so the total is not a fair measure of it. Its excerpt does run on into the article's reference list.

**By unit, core work only:**

| Unit | Modules | Stated core | Reading floor | Course file says |
|---|---|---|---|---|
| 1 | 3 | 126 | 75, including a 15-minute video | 220 |
| 2 | 3 | 170 | 42 | 170 |
| 3 | 2 | 210 | 67 | 210 |
| 4 | 2 | 170 | 40 to 70 | 170 |
| 5 | 1 | 155 | 74 | 155 |

Unit 1's 220 only adds up if one optional essay counts as core: 126 plus essay A's 95.

Stage 8 repeats this measurement once everything else has landed.

### Stage 2. Agree the plan

1. **Forewarn Elias.** 29 notes signed Elias's AI sit in 19 of the 36 lenses CV1 uses; there are none in its modules, meeting docs or outcomes. Most explain how a passage was ported and need nothing. These need him first:
   - His open proposal to drop the per-lesson XLab source f{>>{"author":"Elias","timestamp":1790947555871}@@not sure what this is and if I want this<<}ooter, noted in six lenses (introduction, building intuitions, precedents, prevention, Strategic Foundations, theories of change), and the one to stop hotlinking the theories-of-change image. Two further notes ask for a Works cited segment to be moved when a suggestion is accepted; whether those s{>>{"author":"Elias","timestamp":1790947586909}@@probably left over from old sessions?<<}uggestions are still in the review queue cannot be seen from the relay.
   - Structure he has treated as his to decide. In Compute Verification 2's covert-development lenses, renumbering and naming were left to him. St{>>{"author":"Elias","timestamp":1790947616871}@@You could do that<<}ages 3 and 7 touch the same ground in CV1.
   - Strategic Foundations' written output, which duplicates required unit 4 work, and the stage 5 closing lens, which repeats the resolution he placed in Compute Verification 2.
   - The tw{>>{"author":"Elias","timestamp":1790947656618}@@Unsure what this is<<}elve unit 1 lenses no module imports, which this proposal leaves alone, and whether they are still needed.
   - Stage 6 rewrites text his AI ported or wrote, such as prompts rebuilt from XLab widgets. His notes on those passages are the record of what is XLab's and what is not.
   - Notes beside questions that stage 4 edits, in the actor map workshop, "Who can prove what", the Context Distiller, the trusted-statement lens, precedents, treaty anatomy, and upstream and downstream. Every edit will be split to go around them, never through them.
   - One open check: whether the imported MIRI paper is the v3 the curriculum pins.
2. **Collect Elias's input on the open decisions** at the end of this document. Any he does not weigh in on are settled before the stage they hold up.
3. **Open a CV1 log and a working-preferences file** on the AIRF pattern.

### Stage 3. Structure

Page boundaries come first, so every later edit runs against final pages. Steps 2 to 5 carry out decisions 1 to 4 in whatever form they are settled; the text describes our suggestion for each.

1. **Test whether an answer survives its question moving to another lens.** On a test lens on staging, a signed-in tester answers a question, the segment is moved to a different lens, and the tester checks the answer is still there. The result settles decision 4.
2. **Split unit 5 into two modules**, at the seam its own first page asks for.

   | Module | Lenses | Stated core | Stated optional |
   |---|---|---|---|
   | Hardware, part 1 | Attestation, the claim, the trusted statement, accounting for hardware | 75 | none |
   | Hardware, part 2 | Measuring use, authorization, where trust lives | 80 | Reconstructing a run, open problems (45) |

   The existing module keeps its id and the first half. One new module is created and added to the course file ahead of the unit 5 meeting. No lens changes file, so no lens id changes. Units 1 to 4 already run two or three modules each. Module names are placeholders.
3. **Split Strategic Foundations into its four pathways.** The page already tells learners to re{>>{"author":"Elias","timestamp":1790947964664}@@good<<}ad the pathway they are weakest on and to skip any they can already apply. Four lenses make that choice visible in the sidebar instead of inside a 39,000-word scroll, and each can carry an honest time of its own. Readings stay as they are. The page's one written output is the same actor, authority and evidence map that unit 4 requires in [[Lenses/XLab Verification - v-scoping-upstream-downstream]], so it is dropped, or kept only as an early attempt to bring to unit 4.
4. **Settle the unit 1 essay as optional.** The Plan A lens says to choose an essay, the module marks both options optional, the course file counts one as core, and the meeting 1 run-sheet calls every essay prompt optional. Optional keeps the unit before the first meeting at about 125 minutes, the reasoning AIRF applied to its own first unit. The Plan A lens's wording changes to offer the essay rather than assign it. Meeting 5 already has a fallback for learners with no Plan A vote to recall.
5. **Split the longest co{>>{"author":"Elias","timestamp":1790948006356}@@good<<}re pages, if step 1 passed and decision 4 says so.** Treaty anatomy (90 minutes), precedents, the eleven-policy sort and the Context Distiller (75 each). Unit 1's essays were deliberately merged into single pages not long ago, which is worth weighing first.

### Stage 4. Question formats

Not every question loses its grade. Each one gets the format that fits what it is for, judged against [[AI Guide/Writing Rubrics]]: grade only where there is a real right and wrong the learner should be measured on, and prefer ungraded when in doubt.

1. **Build the worklist from per-file counts of both fields**, `assessment-instructions::` and `feedback-instructions::`, not from a search for the one being removed, which was AIRF's costliest miss. For each question, record three facts: whether it is graded, whether its key is visible on the page, and whether it is optional. Baseline: 44 graded segments in 20 lenses, 39 open and 5 choice.
2. **Sort the graded questions into four groups, each with a default:**

   | Group | Count | Default |
   |---|---|---|
   | Key on the same page | 10 | Ungrade, and keep the "open after you have answered" callout as a self-check after committing. A question that should stay graded has its key moved off the page and into the feedback, where it appears only after an answer |
   | Writing and reflection exercises, as their own feedback brief calls them | 20 | Ungrade, with a feedback brief written for the question |
   | Single-answer choice questions with no key on the page | 3 | Keep graded |
   | Everything else | 11 | Judged one by one |

   The ten with the key on the page are the five precedents tasks, the three questions in the actor map workshop, the removal question in "Who can prove what", and the first question in upstream and downstream. The twenty are the seven hardware exercises, the ten parts of the two unit 1 essays, and three more. The three are the evidence-taxonomy checks in [[Lenses/XLab Verification - v-mechanism-effective]]. The eleven are treaty anatomy's four, the three optional written questions in "Who can prove what", the second and third questions in upstream and downstream, the Context Distiller's first question, and the stakeholder map. The defaults are starting points: the worklist records the call made for each question and why.
3. **Make optional status visible.** Every optional question opens its prompt with "Optional:", in the same form everywhere, and any rule about how many to answer, such as treaty anatomy's three of four, sits with the questions it governs. The four optional questions that say so nowhere today are the first two in upstream and downstream and both in the Context Distiller. No required question claims to be optional today, and none should.
4. **Convert each question in a single edit.** Where a question is ungraded, its rubric folds into its feedback brief, since an ungraded question's tutor sees only the brief: the elements stay as what to look for, the point weights and caps go, and the model answer stays as reference. Every question with a feedback brief gets `force-feedback:: first`, so feedback arrives with the first answer and later answers get the button, the setting AIRF chose. The 20 generic briefs are replaced along the way, only questions that stay graded mention a score, and no brief names XLab, which the validator now flags in tutor-facing text.
5. **Leave the five outcome tests as they are.** All five already use `#### Question: Open` with a feedback brief, so CV1 does not have the silent-test problem AIRF found.

AIRF removed grading from every question outside its outcomes on 2026-09-28, on the grounds that such a score gates nothing and counts toward nothing. CV1 takes the narrower route above, but the same reasoning settles the first group: where the key is on the page, a score only measures whether the learner opened it first.

### Stage 5. Close the claim ledger in CV1

1. **Add a short closing lens** at the end of unit 5, carrying the same claim-ledger widget and XLab's resolution, as [[Lenses/XLab Verification - v-hw-policy-studio]] already does in Compute Verification 2. It is written to stage 6's standard from the start.
2. **Point the promise at it** on unit 5's first page and in that page's tutor summary.

Learners who continue meet the ledger again in Compute Verification 2, as a second look rather than the first answer. This stage follows our suggestion for decision 5; if the promise is reworded instead, to say the resolution comes in the next course, step 1 drops out.

### Stage 6. Plain language

The target is Lens's own text, and the standard is the one [[AI Guide/Writing Meeting Docs]] already sets for prompts, applied to lenses: an intelligent reader gets it on the first pass, sentences are short and concrete, and every term is defined or dropped.

1. **Mark what is Lens's and what is XLab's.** Elias's notes identify much of the rebuilt material, and the rest can be checked against XLab's source repository, which the course file links. Lens's text includes every tldr, the overview, callout titles, and the prompts and keys rebuilt from XLab widgets the platform cannot run.
2. **Apply the spoiler test to every tldr.** A tldr can show in the lens navigation before the page is opened, and the tutor receives it as context, so a tldr that states an exercise's result hands the result over in advance. The tldr of [[Lenses/XLab Verification - v-actor-edges]] gives the number of actors left with no arrow and names the chip designer holding up three subgoals, which are the findings that exercise asks the learner to reach. AIRF found the same failure in its long welcomes.
3. **Rewrite Lens's text to the standard.** The usual offenders are long sentences stacked with colons and semicolons, compressed metaphors and closing aphorisms; the Context Distiller's tldr, for example, asks the learner to "thread every point to a desk". A reworded prompt takes its feedback brief with it in the same edit, so the brief still describes the question the learner sees.
4. **List XLab passages that prove to be a problem**, for you and Elias to decide case by case. Each also goes to XLab through its feedback form.

### Stage 7. Consistency

The mechanical passes run last among the content stages, so they catch everything written before them.

1. **Unit, never week, in learner-facing text:** the overview (its "Five weeks", the heading over its five callouts, the callouts themselves and its tutor summary), the unit 5 module title, visible text in [[Lenses/XLab Verification - v-mechanism-effective]], [[Lenses/XLab Verification - v-mechanism-privacy]], [[Lenses/XLab Verification - v-actor-edges]] and [[Lenses/XLab Verification - v-scoping-actors]], and the tutor summaries of four lenses, since the tutor repeats them.
2. **XLab's section numbers out of headings and link labels.** Eight hardware headings carry 2.1 to 2.1.7. Link labels 1.2, 1.2.1, 1.2.2 and 1.3 appear in [[Lenses/XLab Verification - v-scoping-actors]], [[Lenses/XLab Verification - v-actor-edges]], [[Lenses/XLab Verification - v-interactive-map]] and the chip supply chain lens; [[Lenses/XLab Verification - v-mechanism-privacy]] says "Section 2.1"; the essay A lens says "Module 0.3" and "Who can prove what" says "Module 2.1". Links keep their targets and take the target's title as their label. Citations of a source document's own sections, such as a paper's or a regulation's, stay. Compute Verification 2's restored covert-development lenses set the precedent by dropping XLab's unit numbers from their titles.
3. **Module titles in one style.** Today they mix questions, statements and a "Week 5:" prefix, and the first module of each unit has a file name describing the whole unit while its title describes one part. The lightest fix keeps XLab's titles, drops the prefix and makes "(optional)" consistent. File names stay unless you want them to match.
4. **Name the course "Compute Verification 1".** Wherever text names the course it uses that name; meeting doc titles, for example, currently say "Compute Verification Part 1". Wording that places the course in the sequence, such as "the first of two courses" or "Part 1", stays where it tells learners this is the first component. Compute Verification 2 is named the same way.
5. **XLab source footers:** one rule for every lens, once Elias settles his proposal.
6. **American spelling in Lens's own text:** 89 lines in 26 lenses, and 13 more in the course file, modules and meeting docs. `from::` and `to::` anchors stay as they are, since they must match the stored article exactly, and so do quotations from sources. The search is AIRF's case-insensitive pattern extended with centre, programme, practise, distil and licence.
7. **Em dashes**, against the house rule: five lines, four of them inside rubrics in [[Lenses/XLab Verification - v-precedents]] that stage 4 rewrites anyway, and one in [[Lenses/XLab Verification - v-interactive-map]].

### Stage 8. Time figures

1. **Measure again**, the stage 1 way, now that pages have moved and text has changed.
2. **Re-estimate each changed lens** from what a learner does on it, as the guide asks, starting with the misses in stage 1: each Strategic Foundations pathway, the MIRI paper, the trusted statement, measuring use, where trust lives, and the Context Distiller by report.
3. **Update every figure that repeats them:** the course file note, the overview, and unit 5's first page. The meeting docs follow in stage 9.

### Stage 9. Meeting docs

1. **Meeting 2: bring the tables and navigator notes into line with the prompts.** The Room 2 table and notes still describe an older version in which groups borrowed a checking system they knew; the Room 3 notes describe a debate with assigned sides that the prompt no longer runs; the Room 4 table asks for an open question the room no longer asks. Room 1 has seven asks where [[AI Guide/Writing Meeting Docs]] allows four, and Room 3 says "gettable" where the guide requires "tractable". This is the doc the guide names as the reason its cold-reader check exists.
2. **Meeting 3: add the missing break** between the second share-out and Room 3.
3. **Meeting 1: split the navigator note for Room 4**, which runs straight into the wrap-up script.
4. **Update time figures and next-unit previews** from stage 8. Two are already incomplete: meeting 2 lists only the MIRI paper as unit 3's optional reading, leaving out the chip supply chain lens, and meeting 4 leaves out unit 5's open-problems reading.
5. **Apply stages 6 and 7** to the docs' own text.
6. **Run the guide's three agent checks on all five docs:** template match, room quality and the cold reader. The docs and the master template, [[meetings/Master template]], are Markdown in the vault, so each check runs as a sub-agent given exactly what the guide specifies: its instruction text, the doc, the course file, and the unit's modules with their lenses, outcomes and readings. The cold reader gets the Session Doc tab and nothing else. The checks run last so they see the final docs, and their findings are triaged rather than applied wholesale.

### Stage 10. Test on staging

These need a signed-in tester:

- An ungraded question still completes its lens, including one that sits last in its module, and a question that stays graded still shows its score.
- Skipping an optional question still lets the lens complete.
- `force-feedback:: first` sends feedback once, and returning to the lens does not send it again.
- Both unit 5 modules appear ahead of the unit 5 meeting, and the closing ledger lens works.
- The Strategic Foundations lenses appear as optional.
- A learner's earlier answers are still in place, which confirms no id changed.

## Decisions left open

These are left for Elias's input. Any he does not weigh in on are settled later, before the stage each one holds up. The suggestions are ours.

| # | Decision | Holds up | Our suggestion |
|---|---|---|---|
| 1 | Unit 5: two modules, or two submodules in one module? | Stage 3 | Two modules |
| 2 | Strategic Foundations: four pathway lenses, or one page? And its written output: drop, reframe, or keep? | Stage 3 | Four lenses; drop the output |
| 3 | Unit 1 essay: optional, or core? | Stage 3 | Optional |
| 4 | Longest core pages: split them, or leave them? | Stage 3, step 5 | Decide once the step 1 test is in |
| 5 | Claim ledger: close it in CV1, or reword the promise? | Stage 5 | Close it in CV1 |
