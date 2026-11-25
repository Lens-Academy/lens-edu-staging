---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# CV2 tutor summary worklist (stage 6)

Companion to [[CV2 Streamlining Log]] and [[CV2 Streamlining Proposal]], stage 6. It maps every `summary_for_tutor` in CV2 against what the lens now is, so the rewrites can go unit by unit. Mapped on 24 Nov from the staging copy, after stage 5.

**Status, 25 Nov.** Done, waiting for Andreas's review. That covers all 27 rows below and the 12 widget descriptions that Andreas added to the pass on 25 Nov (see "Added to this pass"). The validator no longer reports a tutor field that names XLab.

## The standard

From the AI Guide ([[../../AI Guide/Writing Lenses]], [[../../AI Guide/Course Authoring]]) and CV1's stage 7:

- Describe what the lens teaches and how its parts run, in order: readings, widgets, questions. Include what is optional and what is required, and how feedback starts (first answer or "Get feedback").
- No XLab name, no XLab lesson numbers (2.2.1, 3.1.1 and so on), and no "Imported from XLab's curriculum" or "restored from git history". The paper's own section numbers stay (Heim §3.2, Baker §2.3.3, Cankaya Section 3.2).
- Nothing about boxes that are gone ("Unfinished writing", peer review, "Companies A and B").
- No semicolons. Full stops or commas.
- American spelling, so the language pass has less to do.
- "Lens" and "unit" for the course's own structure, never XLab's "module", "submodule" or "lesson".
- Keep any instruction the tutor still needs ("stay with what Baker's appendix supports", "do not tell the learner who is right").

These are our own fields, so the edits land directly.

## What each summary needs

Words are the current length. "Light" means only a few words change. "Rewrite" means the summary describes a lens that has since changed.

| Unit | Lens | Words | Found | Changed since the summary was written | Plan |
|---|---|---|---|---|---|
| 6 | Welcome to Unit 6 | 44 | 1 semicolon, "lesson" | Module split (B12) | Light |
| 6 | `v-hw-policy-studio` | 144 | XLab name, import note, "2.1", 2 semicolons | First-answer feedback, CV1 link wording | Rewrite |
| 6 | `v-cloud` | 175 | XLab name, "2.2.1", module words, 3 semicolons | Heim explorer required (B16), "units 6 and 7" | Rewrite |
| 6 | `v-cloud-customer-identification` | 99 | XLab name, "2.1", "2.2", "2.2.1", "2.2.2" | None | Light |
| 7 | Welcome to Unit 7 | 43 | 1 semicolon, "lesson" | Module split | Light |
| 7 | `v-cloud-detection-gaps` | 98 | XLab name, "2.2.3", module words | None | Light |
| 7 | `v-cloud-evidence` | 232 | XLab name, "2.2.1", "2.2.3", "2.2.4", 9 semicolons | First-answer feedback, time line removed | Rewrite |
| 7 | `v-intel-intro` | 89 | XLab name, import note, "2.3.1", "2.3.5", 2 semicolons | Links back in parentheses, institutions merged (B14) | Rewrite |
| 7 | `v-intel-signatures` | 326 | XLab name, import note, removed box, 6 semicolons | Collection map required (B16) | Rewrite |
| 7 | `v-intel-anchor` | 138 | 1 semicolon | Rewritten for B4 today | Light |
| 7 | `v-intel-assessment` | 115 | XLab name, import note, removed box, 5 semicolons | CIA excerpt to become optional (B6, not yet done) | Rewrite, after B6 |
| 7 | `v-intel-action` | 273 | 6 semicolons (Baker §2.3.3 stays) | Rewritten for the merge today | Light |
| 8 | Welcome to Unit 8 | 50 | 1 semicolon, "lesson" | Module split | Light |
| 8 | `v-human-intro` | 51 | "submodule 2.4", "2.4.1" to "2.4.4" | None | Rewrite (short) |
| 8 | `v-human-insiders` | 307 | XLab name, 2 semicolons (§4.3 is the paper's) | Construct a case required (B16) | Rewrite |
| 8 | `v-human-reporting-protection` | 169 | Clean | Rewritten for the split today | None |
| 8 | `v-human-after-report` | 171 | Clean | New today | None |
| 8 | `v-human-audits-inspections` | 163 | 3 semicolons | Widget required (B16) | Light |
| 8 | `v-human-institutions` | 202 | XLab name, 3 semicolons | First-answer feedback, "Optional:" labels, link to After the report arrives | Rewrite |
| 9 | Welcome to Unit 9 | 45 | 1 semicolon, "lesson" | None | Light |
| 9 | `v-covert-what-is-it` | 190 | XLab name, import note, module words, 1 semicolon | Worked example required (B16), Unit 10 wording (item 22), boxes say units 9 and 10 | Rewrite |
| 9 | `v-covert-system-overview` | 313 | XLab name, import note, 3 semicolons (Cankaya §3.2.x stay) | First-answer feedback on all nine questions | Rewrite |
| 10 | Welcome to Unit 10 | 46 | 1 semicolon, "lesson" | None | Light |
| 10 | `v-covert-how-to-cheat` | 153 | XLab name, import note, "3.1" | First-answer feedback, link wording | Rewrite |
| 10 | `v-covert-taxonomy` | 125 | XLab name, import note, "3.1.1", module words, 2 semicolons | First-answer feedback, Works cited added (B10) | Rewrite |
| 10 | `v-covert-red-blue` | 249 | XLab name, import note, "3.2", 2 semicolons | Cankaya copy optional (B8), feedback split (B5), explorer labels | Rewrite |
| All | Course overview | 103 | XLab name, 1 semicolon | None | Light. The overview is the course welcome, so its learner text keeps XLab's credit (A3), but the validator wants the tutor field without the name |

Totals: 14 rewrites, 11 light edits, 2 already done.

All done on 25 Nov. Notes from doing them:

- **v-intel-assessment.** B6 went in first. The CIA excerpt has `optional:: true`, and the line above it now reads "**Optional:** Three techniques from the CIA's *A Tradecraft Primer*, for judging a source, watching for signs of change, and weighing rival explanations: …". It is one line, with no em dash, and adds a short gloss of the three techniques because the T1 check flagged their names. T1 still flags the line. I left it, because the names are the reading's own section titles. **B6 reversed later on 25 Nov** (log row 26): the reading is required again, the line keeps its gloss without "Optional:", and the summary says "One required reading follows".
- **v-covert-red-blue.** The summary says the Cankaya copy is optional, with a line above it saying so (B8), and that questions 1 to 9 give feedback on request while question 10 gives it after the first answer (B5).
- **v-human-audits-inspections.** The learner text above the drill still called it optional, though B16 made it required. The callout title loses "(optional, …)", and "The exercise below is optional" becomes "The case file stays available here while you work through the exercise below."
- **The two "None" rows.** v-human-reporting-protection and v-human-after-report each got a line saying their widget is required, "page" became "lens", and the split date came out. The first also stops naming the next lens, which the validator flagged.
- **Welcome lenses.** The unit names follow the meeting headings in title case, for example "Unit 8 (The Human Layer)".

## Added to this pass (Andreas, 25 Nov)

These are the widget descriptions. Each lost XLab's name, its semicolons and "page" or "lesson". Each now says whether its lens requires it, as B16 set.

- **The 11 that named XLab:** cloud-evidence-drill, collection-map, construct-case, covert-worked-example, evasion-taxonomy, human-audits-inspections, human-insiders, human-institutions-judgment, human-reporting-protection, standard-of-proof and whistleblower-levers. Their lens placement is now stated where it helps, for example "on the After the report arrives lens of Unit 8". The 30-minute framing came out of the cloud drill's description, because the line is gone from the lens.
- **The claim ledger.** It names both placements: the Hardware lens at the start of Unit 5 of CV1, and the policy judgment lens "in the next course", at the start of Unit 6 of CV2. CV1 already tells learners the ledger returns there, so the validator's two notes on this are expected and can stay.
- **Five more for semicolons and "page" only:** cankaya-audit-calculator, covert-execution-trace, heim-signal-explorer (now says the lens requires it), scher-threshold-explorer and wasil-method-explorer.

## Not in this pass

- **The five feedback modules (U6 to U10).** Their tutor fields keep one semicolon each, because they use the same template as CV1's feedback modules and the AI Control courses. Change all of them together or none.
- **The old institutions lens**, which is out of both courses.
- **Summary lines (`tldr`)**, which are learner text and go with stage 7 and stage 8.

## Order and check

Unit by unit, 6 to 10. After each unit, a production check on the course and a count of the validator's warnings that a tutor field names XLab, which should fall from 16 (15 lenses and the overview) to none, leaving only the 11 widgets until B7. B6 (the optional CIA excerpt) goes in just before the assessment lens's summary, so that summary describes the lens as it will be.

Result, 25 Nov. Production: no errors and the usual 25 warnings: 23 from the legacy surveys and the two article 403s, which come and go between runs. Draft (wip): 3 warnings, the two expected claim-ledger notes and one false match. That match is the overview's heading "What this course is about", which the validator reads as a link to the EA lens "What this course is". None of the 50 tutor fields in CV2 names XLab (21 lenses, the module tutor fields, 17 widgets).
