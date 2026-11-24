---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# CV2 streamlining: proposal

Compute Verification 2 should be ready for its cohort by 26 November. Like CV1, it needs almost no new substance. It needs to read as a Lens course: consistent labels, names, titles, question formats and tutor text, page lengths a learner can plan around, and meeting docs, which do not exist yet. This proposal sets out where the course stands on 24 November, how we review the pass Turner's AI made over the weekend, what stays fixed, and the work as eleven stages in the order they would run. Decisions still open are collected at the end, each marked with the stage it holds up.

All of it happens on staging. CV2 has not run yet, and its pages are shared only with the archived five-module course.

## Where CV2 stands

### Load

The [CV2 load map](https://claude.ai/artifact/AzwbrECCiSuUyTmRfjaFcL) shows every page on the same minute scale as CV1's, with a reading estimate from word counts at the rates [[CV1 Time Worklist]] used.

- **The stated times hold up.** On every page but one, the text and embedded readings fit inside the stated reading time, with room left for the widgets. CV1's large misses were optional readings and reading sent off the page, and CV2 has no optional pages and little off-page reading. The exception is [[../../Lenses/XLab Verification - v-intel-assessment]]: about 15 minutes of reading against 10 stated, because a 2,200-word excerpt from the CIA's *Tradecraft Primer* that the page calls optional sits inline, with nothing marking it as optional.
- **Core minutes by unit:** 120, 169, 229, 198 and 222, against a target of about 210. Unit 6 is light. Units 6 and 7 hold 289 minutes between them, so moving pages from one to the other can only make both light.
- **The imbalance is inside the units.** Three pages carry 437 of the course's 938 core minutes: the red team review (186), the Cankaya close reading (161) and "Reporting and protection" (90). Units 9 and 10 each rest on one page, and those two pages hold 182 of the course's 328 tutor minutes.
- **Not measured yet:** the 17 widgets, which are timed only inside the stated reading time, and the long written tasks: a 700 to 1,000 word hardware brief, a 700-word red-line and a 2 to 6 page expert review.

### The other pass

Between 22 and 24 November, Turner's AI edited all 21 content pages, the course overview and the five unit modules. The edits are in the approved text, not pending, so reviewing them means editing on top of them.

**What it did, which we keep:**

- XLab's section numbers came out of headings, and links labelled with numbers now carry words.
- "Module", "submodule" and "week" became "unit" in page text, the module titles and the overview.
- Pointers broken by CV2's page order now point the right way. The unit 9 opener points to unit 10, the red team review points back to unit 9, and the taxonomy question restates the unit 9 scenario in a short recap.
- The five "Unfinished writing" boxes in unit 7 came out. On the red-line page, the four questions from its box became prompts on the page.
- Three headings that named the wrong thing were renamed: "Companies A and B" is now "Audit the verifier", "Four Sources" is now "Build the inspection order", and "Section B: the taxonomy revisited" is now "Scoring the evasion routes".

**Where it departs from calls settled in CV1** (stage 3 brings these into line):

- Module titles became "Unit 6: Hardware judgment and cloud records" and so on. CV1 dropped the unit from module titles (A15) and uses title case (A51).
- XLab's lesson numbers came out of the Works cited entries on all 21 pages. CV1's Works cited keep them as part of the cited lesson's title, in title case (A53).
- Links now read "the signatures lens", "the assessment lens" and so on. CV1 labels links with the page's name (A50).

**What it did not reach:**

- **Tutor summaries still describe the old pages.** On 12 pages they say the page was "Imported from XLab's Verification curriculum" or "restored from git history", and five of those describe the Unfinished writing boxes that are gone. Several still point to pages by XLab's lesson numbers, such as 2.3.4 and 3.1.1.
- **The partner's name in tutor text.** 36 of the validator's 65 warnings are XLab named in tutor-facing text: on 19 pages, the overview and 11 widgets. Five briefs on [[../../Lenses/XLab Verification - v-human-institutions]] name XLab as the source of the commentary they pass on.
- **Two tldrs keep labels:** "you will red-line it in 2.3.5" on [[../../Lenses/XLab Verification - v-intel-institutions]], and "This submodule" on [[../../Lenses/XLab Verification - v-human-intro]].
- **The red-line task** on [[../../Lenses/XLab Verification - v-intel-action]] still says "starting from your four answers", though the four are now prompts nobody answers, and still says it "goes through peer review" (A7).
- **The overview** still calls CV1 "the first course, Compute Verification" and carries XLab's "Alpha version" box. CV1's overview credits XLab in one line, with its feedback form (A3, A7).
- **Questions:** 32 graded open questions and one choice question, none with first-answer feedback (CV1: A13, A30 to A33). The two optional questions on "Institutions and policy judgment" do not say they are optional.
- **Spelling and marks:** 54 em dashes in learner-facing text on 11 pages and 6 in briefs on one page, 29 British spellings on 10 pages, and 27 page titles (the 21 content pages and the 6 feedback pages) and all 10 module titles in sentence case (A51).
- **Housekeeping:** 31 notes from Elias's AI on 16 pages, three of them anchor fixes on [[../../Lenses/XLab Verification - v-cloud]] that say "delete when accepting". The Works cited on [[../../Lenses/XLab Verification - v-cloud-evidence]] points to "Sources lines above" that are not there. The course file's note describes an older split (245 and 215 minutes for units 9 and 10) and says no meeting docs are linked.

**Unit 7's missing tasks.** With the Unfinished writing boxes gone, unit 7's six intelligence pages hold one written task, the red-line. XLab specified an essay on [[../../Lenses/XLab Verification - v-intel-anchor]] and a case-brief packet on [[../../Lenses/XLab Verification - v-intel-assessment]] and built neither. Decision 3.

## What stays fixed

- **No learning outcomes.** The course will be split and its concept map reworked, so outcomes written now would be rewritten soon. Synthesis questions stay graded and required instead, as in CV1's later units (A2, A29).
- **CV1's settled calls carry over** unless this document says otherwise: A1 (a key on the page is fine), A2 and A29 (graded and required), A3 and A7 (credit stays, framing goes), A13 and A30 to A33 (first-answer feedback), A15 and A51 (titles), A48 (American spelling), A49 (XLab's later revisions are not pulled in), A50 (labels, schedule words, names, em dashes), A53 (Works cited) and A54 (optional work counts by expected uptake).
- **XLab's text stays XLab's.** Changes to it are limited to labels, names, spelling, em dashes and page boundaries, plus the other pass's edits under review.
- **How edits land.** XLab references and formatting are edited directly. The relay turns edits to text we did not write into suggestions, which Andreas accepts or rejects. Text that reads as AI-written is flagged with comments, and Andreas rewrites it, as in CV1 (A4, A36). Elias is consulted only on what we cannot settle ourselves.
- **No id or slug changes.** A question moved to a new page keeps its id. New pages get new ids.
- **Release status is not ours.** Course-scoped on 24 November: no errors, 65 warnings. Of those, 23 are legacy syntax in the shared surveys, 2 are source links that refuse automated checks, and 4 are course-graph notes, two of them on the claim-ledger widget CV1 shares. The 36 partner-name warnings should fall as stages 5 and 6 rewrite tutor text.

## The work, in order

Every stage ends with `validate_content`, course-scoped. To meet 26 November, each stage runs unit by unit from unit 6, so that if time runs short, what is left sits in the units learners reach last.

### Stage 1. Measure (done)

The load map, and the counts above, taken from the staging repository at commit 3ae2221, which mirrors the relay.

### Stage 2. Agree the plan

1. Settle the decisions at the end of this document.
2. Open a CV2 log in this folder on the CV1 pattern. Its decisions are numbered B1, B2 and so on, so they never collide with CV1's A-numbers when one log cites the other.

### Stage 3. Review the other pass

1. **Module titles** back to CV1's form: no unit prefix, title case, such as "Hardware Judgment and Cloud Records". The unit names in the course file's meeting headings and on the overview's boxes keep "Unit 6:" and take title case, as CV1's do.
2. **Works cited:** XLab's lesson numbers back in, in title case.
3. **Link labels:** page names in place of "the signatures lens" and the like.
4. **The red-line page:** "your four answers" becomes "the four questions above", and the peer-review line goes.
5. **Objective boxes.** Unit 9 now shows three lists of aims: the unit welcome's, XLab's box on [[../../Lenses/XLab Verification - v-covert-what-is-it]] and the one on the Cankaya page. XLab's box describes the evasion work, most of which now sits in unit 10, so its title says units 9 and 10. The box on [[../../Lenses/XLab Verification - v-cloud]] covers all four cloud pages across units 6 and 7 but says "this lens", so its title names the cloud pages instead.
6. **The pass's new text** (the taxonomy recap, the red-line prompts, the reworded openings of the cloud page and the hardware brief) goes through stage 7's flag pass like Lens's other text.

### Stage 4. Structure

Carries out decisions 1 and 2 in whatever form they are settled. Unit welcomes, the overview's boxes and the course file follow any change.

### Stage 5. Questions

1. **Grading stays.** All 32 graded open questions keep their grade, and the required ones stay required (A2, A29).
2. **First-answer feedback** (`force-feedback:: first`) on every question with a brief (A13, A32), with the exception settled in decision 4.
3. **Optional status shows.** The two optional questions on "Institutions and policy judgment" open with "Optional:". The Cankaya page's optional and choose-one questions already say so in their headings.
4. **Briefs no longer name XLab.** They point to the key or the source lesson instead, and the Works cited keeps the credit (A30).

### Stage 6. Tutor-facing text

Rewrite each stale tutor summary to describe the page as it now is, without XLab's name or lesson numbers, and without the removed boxes. These are our own fields, so the edits are direct. The 11 widgets' tutor descriptions follow decision 6.

### Stage 7. Plain language (flags)

Flag Lens's own text that reads as AI-written, with comments on the pages and [[CV1 Plain Language Worklist]]'s format for the worklist that indexes them (A36). In scope:

- every tldr, each checked for spoilers as in CV1
- the prompts and keys rebuilt from XLab widgets
- the questions Lens added on [[../../Lenses/XLab Verification - v-covert-how-to-cheat]] and [[../../Lenses/XLab Verification - v-covert-taxonomy]]
- the unit welcomes and the overview
- the other pass's new text

XLab passages that prove to be a problem are listed for Andreas to decide. Flags go out unit by unit, so Andreas can rewrite unit 6 while units 7 to 10 are still being flagged.

### Stage 8. Consistency

Mechanical passes, edited directly:

1. **Overview:** CV1 by name, the Alpha box replaced by CV1's one-line credit and feedback form, box titles in title case.
2. **Titles:** the 27 page titles and 10 module titles that are in sentence case take title case (A51).
3. **Em dashes** out of learner-facing and tutor-facing text (A50). Embedded articles are not touched.
4. **American spelling** (A48), 29 instances on 10 pages. Embedded articles and quotations are not touched.
5. **Housekeeping:** the three anchor-fix notes that ask to be deleted, the stray "Sources lines" sentence, and the course file's note. Elias's other notes stay.

### Stage 9. Times

Re-estimate only the pages that change: split pages, any page that gains a question, and the assessment page under decision 5. Then update the course file's note.

### Stage 10. Meeting docs

Five docs from scratch in `meetings/Compute Verification 2/`, built on [[../../meetings/Master template]] and [[../../AI Guide/Writing Meeting Docs]], with CV1's five docs as the model and [[Meeting Doc Text Review - Style Sheet]] for wording, each linked from the course file with `meeting-doc::`. The unit 6 doc comes first. Each doc previews the next unit, and the unit 10 doc previews the capstone. Each draft gets the guide's three checks: template match, room quality and the cold reader.

### Stage 11. Test on staging

These need a signed-in tester:

- First-answer feedback arrives with the first answer, once, and not again on return.
- Split pages appear in order with their own times, and a question moved to a new page still takes and keeps an answer.
- The CIA excerpt shows as optional, if decision 5 says so.
- Every module shows its new title, and every meeting links its doc.

## Schedule to 26 November

| Day | Work |
|---|---|
| Tue 24 | Settle the decisions. Stages 3 to 5: the review, the structure, the questions. Stage 6 begins |
| Wed 25 | Stage 6 finishes. Stage 7's flags go out unit by unit, and Andreas rewrites behind them. Stage 8 |
| Thu 26 | Stage 9. Stage 10, the unit 6 doc first. Stage 11 |

The meeting docs for units 8 to 10 are the most likely to run past 26 November. Learners reach those meetings last, so they can be finished during unit 6.

## Decisions left open

The suggestions are ours. **Settled 2026-11-24 (Andreas):** decisions 1 and 3 to 6 as suggested, and decision 2 for "Reporting and protection" only. The three reversals in stage 3 are agreed. Decision 7 was added the same day, after Andreas noticed the duplicated Cankaya reading. The decisions are recorded in [[CV2 Streamlining Log]] as B1 to B7.

| # | Decision | Holds up | Our suggestion |
|---|---|---|---|
| 1 | Unit 6 at 120 minutes: leave it, or move "Detection gaps and policy limits" up from unit 7, which gives 150 and 139? | Stage 4 | Leave it. The two units hold 289 minutes between them either way, and CV1 at first let its light unit 2 stay light (A17) |
| 2 | The three long pages: split them, or leave them? | Stage 4 | Split the red team review and the Cankaya close reading into the reading and the written work, as CV1 did with treaty anatomy (A23), so each half shows its own time. Split "Reporting and protection" at its heading "After the Report Arrives", which leaves the video, the statute and two readings on the first page, and the investigation standards and two widgets on the second |
| 3 | Unit 7's missing tasks: leave the intelligence pages without them, or add the essay XLab specified for the empirical anchor page, how far the nuclear evidence transfers to AI, as one short required question of about 10 minutes? | Stages 5 and 9 | Add the one question. It needs no material beyond Baker's appendix on the page, and it gives the unit 7 meeting a written answer to build on. It is written to the AIRF brief standard and graded. The case-brief packet would need a document set built from scratch, so it stays out |
| 4 | The red team review's ten questions: first-answer feedback on all ten, or "Get feedback" on questions 1 to 9 and first-answer feedback on question 10? | Stage 5 | "Get feedback" on 1 to 9, first-answer feedback on 10. The ten build one written review, and CV1 kept essay parts on "Get feedback" so a learner writing is not interrupted after each part (A33). The Cankaya questions are separate answers and get first-answer feedback |
| 5 | The CIA excerpt: mark it optional, or make it required? | Stages 8 and 9 | Mark it optional, with the segment flag and a line above it saying so. The page's 10 minutes then holds at expected uptake (A54) |
| 6 | The 11 widgets' tutor descriptions, which name XLab: now, or after 26 November? | Stage 6 | After 26 November, unless stage 6 finishes early. They are seen only by the tutor, and one widget is shared with CV1 |
| 7 | The red team review inlines Sections 1 to 3 of the Cankaya paper again: about 4,500 words, about 30 minutes at the paper rate, all of which the unit 9 page already carries. The page says so ("you are re-reading Sections 1 to 3 here with a different question in mind"). Keep the copy, make it optional, or replace it with a link back to the unit 9 page? | Stage 4, and decision 2 for the two unit 9 and 10 pages | Make it optional, with a line saying it repeats the unit 9 text. The ten questions cite the paper by section, so a copy on the page spares learners switching pages, and those who skip it save up to 30 minutes. A link alone saves all 30 but leaves learners writing with the paper on another page. Either way the red team review's required reading falls to the four treaty articles (about 2,100 words, about 15 minutes), so splitting the page would part 15 minutes of reading from two hours of writing. We would then leave it whole. The Cankaya page's questions also cite the paper by section, so it too stays whole unless its 161 minutes on one page matters more than having the paper beside the questions |
