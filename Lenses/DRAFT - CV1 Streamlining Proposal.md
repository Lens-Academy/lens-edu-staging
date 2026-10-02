---
id: '53f74229-02c2-421d-88ee-1596ff0b41f6'
title: "CV1 streamlining, a proposal"
tldr: "Compute Verification 1 does not need new substance, it needs a shape learners can keep up with. This proposes rebalancing two overlong pieces, removing grades that measure nothing, closing one loop the course leaves open, a consistency pass, and a plain-language pass on the text Lens wrote, without rewriting any outcome or changing any id."
summary_for_tutor: "DRAFT, orphaned. An internal proposal written as a lens so it can be read on the platform. Proposes form changes to Compute Verification 1, the way the AI Risk Fundamentals restructure began. Audience is the team, not learners. Not referenced by any module."
reading_minutes: 14
tutor_minutes: 0
tags:
  - wip
authors:
  - Andreas+Claude
---

#### Text
content::
\## The problem

Compute Verification 1 does not need new substance. It needs a shape a learner can keep up with for five units. Six things get in the way, and none of them is about what the course teaches.

**Load is uneven, and the figures for it disagree.** Unit 5 is a single module of nine lenses, 155 minutes core and 45 optional, although its own first page says the core work should be split into two sessions. Strategic Foundations is one 80-minute page holding nine readings in four pathways. The course file leaves 130 minutes of optional lenses in units 3 and 5 out of its totals, and counts as core an essay the module marks optional.

**Learners meet labels they cannot resolve.** XLab's section numbers (2.1.3, 1.2.2) appear in eight hardware lens headings and in link text in three more lenses, and CV1 never shows the numbering they belong to. The overview, the unit 5 module title and four lenses say "week" where the course runs in units.

**One promise is kept in a different course.** Unit 5 opens with a claim ledger and tells the learner to keep their answers, because they will return to them at the end of the section. The return is in Compute Verification 2, in [[../Lenses/XLab Verification - v-hw-policy-studio]]. A learner who stops after CV1 never sees the resolution, and CV1's tutor is told not to give it.

**Grades that measure nothing.** 44 question segments outside the learning outcomes produce a score. In ten of them the answer key sits on the same page directly below the question, in a collapsed callout the learner can open at any time, or in the next paragraph. Twenty of the 44 share one generic feedback brief, and no question in the course sends feedback unless the learner asks for it.

**Text that takes decoding.** Much of what Lens wrote around XLab's lessons was drafted by AI and reads like it: dense sentences, compressed metaphors and closing aphorisms that a participant has to unpack before they can use them. At least one tldr gives away the result of the exercise it introduces.

**Drift.** Mixed British and American spelling, em dashes in two lenses, module titles in three styles, the course called "Compute Verification 1", "Part 1" and "the first of two courses" in different places, and a meeting 2 doc whose prompts were rewritten without its tables or navigator notes.

#### Text
content::
\## What does not change

- **No learning outcome is rewritten.** Units 3 to 5 have none, and that is recorded here as a hole rather than filled.
- **No published id changes, and nothing is retired.** Lenses and modules keep their ids. Slugs stay as they are: module-level `slug-aliases` was never confirmed (see [[../AIRF Restructure Log]], section 3), and a cohort is running.
- **XLab's text stays XLab's.** The changes are to labels, page boundaries, question settings and Lens's own scaffolding.
- **[[../Lenses/Four Background Claims]] is not touched.** Two modules outside Compute Verification import it.
- **Compute Verification 2 is reference only.** It is unfinished, so its structure is not adopted.
- **Release status is not ours.** The course-scoped validator shows 25 production errors, every one caused by a `wip` tag, plus 17 production warnings. That is the baseline, and the target is that it does not grow.

#### Text
content::
\## Load, as measured

| Unit | Modules | Core minutes | Optional minutes | Course file says |
|---|---|---|---|---|
| 1 | 3 | 126 | 245: essay A 95, essay B 110, success scenario 40 | 220 core |
| 2 | 3 | 170 | 80: Strategic Foundations | 170 core, 80 optional |
| 3 | 2 | 210 | 190: MIRI paper 75, chip supply chain 115 | 210 core, 75 optional |
| 4 | 2 | 170 | none | 170 core |
| 5 | 1 | 155 | 45: reconstructing a run 30, open problems 15 | 155 core, 30 optional |

Minutes are each lens's own `duration_minutes`, which include any optional questions inside the lens, so a core figure is an upper bound. Unit 1's two hidden lenses are left out. Unit 1's 220 only adds up if one essay counts as core (126 plus 95). Unit 5's first page gives a third set of figures: 165 to 180 minutes core, 35 to 45 optional.

#### Text
content::
\## A. Rebalance

**A1. Split unit 5 into two modules, at the seam its own first page asks for.**

| Module | Lenses | Core | Optional |
|---|---|---|---|
| Hardware, part 1 | Attestation, the claim, the trusted statement, accounting for hardware | 75 | none |
| Hardware, part 2 | Measuring use, authorization, where trust lives | 80 | Reconstructing a run, open problems (45) |

The existing module keeps its id and the first half. One new module is created. No lens changes file, so no lens id changes. Units 1 to 4 already run two or three modules each, so this also brings unit 5 into line with the rest of the course. The alternative is two submodules inside the one module, which creates nothing new but leaves a single long module page. Module names are placeholders.

**A2. Split Strategic Foundations into its four pathways.** The page already tells learners to read the pathway they are weakest on and to skip any they can already apply. Four short lenses make that choice visible in the sidebar instead of inside an 80-minute scroll. Each pathway keeps its readings unchanged. The page's one written output is the same actor, authority and evidence map that unit 4 asks for as required work in [[../Lenses/XLab Verification - v-scoping-upstream-downstream]]. We suggest dropping it from the optional module, or keeping it framed as an early attempt to bring to unit 4.

**A3. Settle the unit 1 essay as optional.** The Plan A lens says to choose an essay option, the module marks both options optional, the course file counts one as core, and the meeting 1 run-sheet calls every essay prompt optional. Making it officially optional keeps the unit before the first meeting at about 125 minutes, the same reasoning the AIRF restructure applied to its own first unit. The Plan A lens's wording changes to offer the essay rather than assign it. Meeting 5 already has a fallback for learners who never voted on Plan A.

**A4. Correct every time figure once A1 to A3 land:** the course file note, the overview, unit 5's first page, and the meeting docs' wrap-ups and run-sheets. Two are already wrong: meeting 2 tells learners unit 3 adds an optional 75 minutes (it is 190), and meeting 4 says unit 5 adds 30 (it is 45).

**Not proposed in this pass: splitting the long core pages.** Treaty anatomy (90 minutes), precedents, the eleven-policy sort and the Context Distiller (75 each) are the longest required pages. Splitting them moves answered question segments from one lens to another, and nothing confirms that learner responses survive that. Unit 1's essays were also deliberately merged into single pages not long ago, and twelve one-minute lenses that no module imports remain from that. We suggest revisiting after the cohort.

#### Text
content::
\## B. Question formats

**B1. Remove grading from every question outside the learning outcomes.** This is the change AIRF made on 2026-09-28, for the same reason: a score outside an outcome gates nothing and counts toward nothing. CV1 adds a second reason. Where the key is on the page, the score does not measure understanding at all, only whether the learner opened the callout first. Once ungraded, those "open after you have answered" callouts work as XLab intended, as a self-check after committing.

**B2. Move each rubric's substance into the feedback brief, in the same edit.** This is where CV1 differs from AIRF. Most CV1 questions carry both `assessment-instructions::` and `feedback-instructions::`, and the tutor on an ungraded question sees only the second. So each rubric is folded into its feedback brief: the elements stay as what to look for, the point weights and caps go, and the model answer stays as reference. The 20 generic briefs are replaced in the process, and nothing refers to a score afterward.

**B3. Set `force-feedback:: first` on every converted question**, AIRF's setting: feedback arrives on the first answer, and later answers get the button.

**B4. Leave the five outcome tests graded and untouched.** All five already use `#### Question: Open` with a feedback brief, so CV1 does not have the silent-test problem AIRF found.

**B5. Build the worklist from per-file counts of both fields**, not from a search for the field being removed, which was AIRF's costliest miss. Baseline: 44 graded segments in 20 lenses, 39 open and 5 choice. The ten with the key on the page are the five precedents tasks, the three questions in the actor map workshop, the removal question in [[../Lenses/XLab Verification - v-actor-edges]], and the first question in [[../Lenses/XLab Verification - v-scoping-upstream-downstream]].

#### Text
content::
\## C. Consistency

**C1. Unit, never week, in learner-facing text.** The overview's "Five weeks" and its five week callouts, the unit 5 module title, and lens text in [[../Lenses/XLab Verification - v-mechanism-effective]], [[../Lenses/XLab Verification - v-mechanism-privacy]], [[../Lenses/XLab Verification - v-actor-edges]] and [[../Lenses/XLab Verification - v-scoping-actors]]. Tutor summaries in three lenses say it too, which matters because the tutor repeats them.

**C2. XLab's section numbers out of visible headings and link text.** Eight hardware headings carry 2.1 to 2.1.7; [[../Lenses/XLab Verification - v-scoping-actors]] and [[../Lenses/XLab Verification - v-actor-edges]] label links 1.2, 1.2.1, 1.2.2 and 1.3; [[../Lenses/XLab Verification - v-mechanism-privacy]] says "Section 2.1". Links keep their targets and take the target's title as their label. There is a precedent in Compute Verification 2, whose restored covert-development lenses dropped XLab's unit numbers from their titles.

**C3. Module titles in one style.** Today they mix questions, statements and a "Week 5:" prefix, and the first module of each unit has a file name describing the whole unit while its title describes one part. The lightest fix keeps XLab's titles, drops the prefix and makes "(optional)" consistent. File names stay unless you want them to match.

**C4. One name for the course in learner-facing text.** The course titles say "Compute Verification 1" and "2"; the meeting docs and several lenses say "Part 1" and "Part 2"; the overview says "the first of two courses".

**C5. American spelling in Lens's own text.** 89 lines in 26 lenses and 12 lines in the meeting docs match a British form. Two kinds are excluded: `from::` and `to::` anchors, which must match the stored article exactly, and quotations from sources. The search is AIRF's case-insensitive pattern extended with centre, programme, practise, distil and licence.

**C6. Em dashes, against the house rule:** five lines in [[../Lenses/XLab Verification - v-precedents]] and [[../Lenses/XLab Verification - v-interactive-map]], with the same exclusions.

**C7. XLab source footers: one rule for every lens**, applied once Elias settles his open proposal on them (see below).

#### Text
content::
\## D. Close the claim ledger in CV1

End unit 5 with the ledger's return: a short closing lens carrying the same widget and XLab's resolution, as [[../Lenses/XLab Verification - v-hw-policy-studio]] already does in Compute Verification 2. Learners who continue then meet the ledger a third time there, as a second look rather than the first answer. The alternative is to reword the promise on unit 5's first page, and its tutor summary, to say the resolution comes in the next course. We suggest D, because learners who take only CV1 otherwise finish without it.

#### Text
content::
\## E. Meeting docs

**E1. Meeting 2: bring the tables and navigator notes into line with the prompts.** The Room 2 table and notes still describe an older version in which tables borrowed a checking system they knew; the Room 3 notes describe a debate with assigned sides that the prompt no longer runs; the Room 4 table asks for an open question the room no longer asks. Room 1 has seven asks where [[../AI Guide/Writing Meeting Docs]] allows four, and Room 3 says "gettable" where the guide requires "tractable". This is the doc the guide names as the reason its cold-reader check exists.

**E2. Meeting 3: add the missing break** between the second share-out and Room 3.

**E3. Meeting 1: split the navigator note for Room 4**, which runs straight into the wrap-up script.

**E4. Time figures and next-unit previews**, after A.

Session docs are copied up to 21 days before each meeting, so an edit reaches only groups whose copy is made afterward. E1 to E3 depend on nothing else in this proposal and can go first.

#### Text
content::
\## F. Plain language

**F1. Rewrite the text Lens wrote so it reads on the first pass.** XLab's lessons are imported with instructions to keep their framing, but a good share of what a learner reads is Lens's own: every tldr, the overview, the meeting docs, callout titles, and the prompts and keys rebuilt from XLab widgets the platform cannot run. Much of it was drafted by AI and reads that way: long sentences stacked with colons and semicolons, compressed metaphors the reader has to unpack, and closing aphorisms. The Context Distiller's tldr, for example, asks the learner to "thread every point to a desk". The standard is the one [[../AI Guide/Writing Meeting Docs]] already sets for prompts, applied to lenses: an intelligent reader gets it in one pass, sentences are short and concrete, and every term is defined or dropped.

**F2. Apply the spoiler test to every tldr.** A tldr can be shown in the lens navigation before the page is opened, and the tutor receives it as context. A tldr that states an exercise's result therefore hands the result over in advance. The tldr of [[../Lenses/XLab Verification - v-actor-edges]] gives the number of actors left with no arrow and names the chip designer holding up three subgoals, which are the findings the exercise asks the learner to reach. AIRF found the same failure in its long welcomes.

**F3. Tell Lens's text from XLab's before rewriting.** Elias's notes mark much of the rebuilt material, and the rest can be checked against XLab's source repository, which the course file links. Where XLab's own text is hard to parse, the default is to leave it and send it through XLab's feedback form, since editing it is a call for you and Elias.

**F4. A reworded prompt takes its feedback brief with it**, in the same edit, so the brief still describes the question the learner sees.

#### Text
content::
\## Coordinating with Elias

29 notes signed Elias's AI sit in 19 of the 36 lenses CV1 uses; there are none in its modules, meeting docs or outcomes. Most explain how a passage was ported and need nothing. These need him before work starts:

- **His open proposal to drop the per-lesson XLab source footer**, noted in six lenses (introduction, building intuitions, precedents, prevention, Strategic Foundations, theories of change), and the one to stop hotlinking the theories-of-change image. Two further notes ask for a Works cited segment to be moved when a suggestion is accepted; whether those suggestions are still in the review queue cannot be seen from the relay.
- **Structure he has treated as his to decide.** In Compute Verification 2's covert-development lenses, renumbering and naming were left to him. A1, C2 and C3 touch the same ground in CV1.
- **A2's written output**, which duplicates required unit 4 work, and **D**, which repeats the resolution he placed in Compute Verification 2.
- **The twelve unattached unit 1 lenses**, which this proposal leaves alone, and whether they are still needed.
- **F rewrites text his AI ported or wrote**, such as prompts rebuilt from XLab widgets. His notes on those passages are the record of what is XLab's and what is not.
- **Notes beside questions that B will edit**, in the actor map workshop, [[../Lenses/XLab Verification - v-actor-edges]], the Context Distiller, the trusted-statement lens, precedents, treaty anatomy, and upstream and downstream. Every edit will be split to go around them, never through them.
- **One open check:** whether the imported MIRI paper is the v3 the curriculum pins.

#### Text
content::
\## Order of work

0. **Preconditions.** Elias forewarned, the decisions below settled, and a CV1 log and working-preferences file opened on the AIRF pattern.
1. **Structure**: A1 to A3, first, so later edits run against final page boundaries.
2. **Question formats**: B.
3. **Consistency**: C.
4. **The ledger**: D.
5. **Time figures**: A4, once nothing else will move them.
6. **Meeting docs**: E4 last; E1 to E3 at any point.

Each stage ends with `validate_content` run course-scoped and unscoped, and a staging check: ungraded questions still complete their lens, `force-feedback:: first` fires once, both unit 5 modules appear before the meeting, and no id has changed.

#### Text
content::
\## Decisions needed

1. **Unit 5:** two modules, or two submodules in one module?
2. **Strategic Foundations:** four pathway lenses, or one page? And its written output: drop, reframe, or keep?
3. **Unit 1 essay:** optional, as proposed, or core?
4. **Grading:** remove it from all 44, or keep the five single-answer choice questions graded?
5. **The ledger:** close it in CV1, or reword the promise?
6. **Course name in learner text:** "Compute Verification 1" or "Part 1"?
7. **Meeting docs:** run the guide's three agent checks this time, or leave them upstream as AIRF did?
8. **Long core pages:** revisit after the cohort, as proposed, or include now?
