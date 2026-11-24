# CV2 QA: potential gaps worth a look (23 Nov 2026)

Turner ran a full QA of Compute Verification 2 with Claude on 23 Nov, ahead of the part-time start on Mon 30 Nov (intensive Mon 14 Dec). Every item below was checked by hand against the current text in Relay. These are potential gaps worth a look, not a verdict: the owners decide what to change.

*Copy of the team's QA note, put in Lens Edu so navigators and contractors can open it (24 Nov).*

## Potential gaps

- **Meeting docs (most urgent).** None of the 5 meetings in [the CV2 course file](https://editor.lensacademy.org/4fd0cfe3/Lens-Edu/courses/in-development/Compute-Verification-2.md) has a `meeting-doc::` line, and there is no `meetings/Compute Verification 2/` folder, so navigators get no session doc or run sheet. CV1 has one per meeting ([CV1 Meeting 1](https://editor.lensacademy.org/e6e867f8/Lens-Edu/meetings/Compute-Verification-1/Meeting-1.md) for reference). The navigator prep DM goes out 3 days before a session, so Meeting 1 is needed by about Thu 26 Nov.
- **Unit 7, red-line question** ([v-intel-action](https://editor.lensacademy.org/104fe993/Lens-Edu/Lenses/XLab-Verification---v-intel-action.md), the open question). It asks learners to test their answer "against the rule that states sign what is symmetric, cheap, and checkable", and the rubric scores on it, but that rule is not taught anywhere in Lens Edu (only this question and its rubric mention it). The task also asks for about six things (three gaps, a redraft, a sharing clause or its defence, the rule test, two both-capitals paragraphs, named blind spots) in "about 700 words", with 25 tutor minutes.
- **Unit 7, power-grid figures** ([v-intel-signatures](https://editor.lensacademy.org/e0298e4d/Lens-Edu/Lenses/XLab-Verification---v-intel-signatures.md), "Energy and the power grid", about line 68). "roughly 130 MW", "Around 500 datacenters worldwide exceed 10 MW" and "about 1.6x a year" are credited to Scher and Thiergart, but that paper is not linked in the lens and is not in Lens Edu, so learners cannot check the figures.
- **Unit 10, evasion explorer** ([v-covert-red-blue](https://editor.lensacademy.org/1228ead2/Lens-Edu/Lenses/XLab-Verification---v-covert-red-blue.md), about line 222). Learners read "Three routes are left unscored." An editor note says the gap is XLab's own: hide an undeclared cluster, attack or capture the verification system, and exploit a boundary in the rule have no scores.

## Fixed on 23-24 Nov (live since 24 Nov, when Elias promoted CV2)

115 small text edits across 28 files, all applied directly (no pending suggestions) and read back:
- Module titles and the Overview say "Unit 6" to "Unit 10" instead of "Week".
- Unit 7's "Unfinished writing" boxes are gone. In the red-line lens the box's four questions stay as plain text, so "your four answers" still has something to refer to.
- Units 9 and 10 point to the right unit ("Unit 9", "Unit 10", "the expert review at the end of this unit") instead of "later in this module" or "the module opener".
- Leftover XLab numbering ("Module 2", "2.3.4", "submodule") is replaced by unit or lens names; slugs, links and anchors are unchanged.
- Upstream provenance notes ("deleted upstream in commit ...") are removed from the works-cited boxes.
- Unit 6: "four readings" fixed to two, excerpts no longer end mid-link, the duplicate brief callout removed.
- The Navigator Session 1 Debrief asks about "the run sheet for this session" instead of "the Unit 1 run sheet" (shared with CV1).

## Checked and left alone

- Unit 9's "choose one of Questions 3, 4, 7 or 9": each question is labelled and marked optional, which is how "choose one" works.
- Unit 10's "2 to 6 page" review for ten questions: about half a page per question.
- Unit 6's policy-studio brief: the learner picks the architecture from the lens's list and names their own delegation by design.
- The `{>>{"author":"Turner's AI","timestamp":1795557660676}@@ <<}` editor comments in many lenses are stripped before learners see the page.
