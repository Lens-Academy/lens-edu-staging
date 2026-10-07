---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# Meeting doc text review: plan and log

Git records what changed. This file records why, what we decided against, and what is still open. Update it alongside the change it describes.

Modeled on [[AIRF Restructure Log]] and [[CV1 Streamlining Proposal]], but kept short, since this project changes wording, not structure. The standard that flags, rewrites and reviews are held to lives in the companion file, [[Meeting Doc Text Review - Style Sheet]].

---

## Summary

**What this is.** A pass over the participant-facing text of the meeting docs for AI Risk Fundamentals (AIRF), AI Futures (Forecasting, Modeling, and Shaping AI Futures) and Compute Verification 1 (CV1), so the questions read as written by a person. It is not a restructure and not a reformat.

**Why.** Participants have said the questions are easy to tell apart as AI-written, and that this frustrates them even when they understand what is being asked. Reported by Andreas, 2026-10-03.

**Status, 2026-10-05.** The first batch is done: AIRF Meeting 5, AI Futures Meeting 3 and CV1 Meeting 5, the meetings that run the week of 2026-10-05, have been flagged, rewritten by Andreas, reviewed and accepted, Session Doc tab only. Minor flags stay on the page for a later full pass, which also covers the other tabs and the shared blocks (section 7 and the log). The style sheet is a working draft Andreas accepted as a starting point. Next: the remaining twelve docs, in the order cohorts reach them.

**Where things are.**

| Section | What it holds |
|---|---|
| Companion file | [[Meeting Doc Text Review - Style Sheet]]: what a flag can cite, and what to leave alone |
| 1 | What the survey found |
| 2 | Decisions, with who made them and why, so they are not re-argued |
| 3 | The plan, stage by stage |
| 4 | **Status by doc. Start here** |
| 5 | Shared files, and which other courses they reach |
| 6 | The chronological log |
| 7 | Open items |

**Status key:** `todo`, `in progress`, `pending`, `done`, `blocked`, `dropped`. **Dates:** full `YYYY-MM-DD` on every entry.

**Conventions.**

- **Never write a literal comment marker into this file**, of either kind. Describe the syntax in words. The AIRF log learned this the hard way: the relay turns a written marker into a real comment.
- **Say how every edit landed**, `direct` or `pending`. The relay decides, and not always as expected.
- **Edit around existing comments, never through them.** An edit whose span contains a comment routes to review as one unit, so rejecting it loses the whole edit.
- **Mark who made each decision.** A proposal from Claude is not a decision until Andreas confirms it.
- **Open relay sessions under Andreas's name**, so edits show as his AI's in the review queue. Sessions before 2026-10-04 were opened without a name, and their edits stay unattributed.
- **Keep the page light.** *Andreas, 2026-10-04.* In-doc flags are only for what a rewrite has to deal with. Typos, punctuation and other small fixes go in the chat review, and a review round does not re-flag the page. Replacing flags in place also proved fragile: a hand edit next to a pending flag replacement on 2026-10-04 left a broken suggestion fragment in CV1 Meeting 5, which had to be removed.
- **Claude clears its own flags.** A flag is removed once its passage is rewritten or deliberately kept. Removing a comment touches a comment, so the removal arrives as a pending change for Andreas to accept, not a direct edit. Tested on a scratch file on 2026-10-04: the edit has to quote the comment exactly, author and timestamp included.

---

## 1. What the survey found (2026-10-03)

Read for the survey: [[AI Guide/Writing Meeting Docs]], the master template, the Session Doc tab of all fifteen docs, the shared blocks, Luc's comments on AIRF Meeting 1, and the record of Luc's 2026-09-26 rewrite of the AI Futures course pages.

The AI feel comes from three places, and each needs a different fix:

1. **Claude's rhetorical habits.** Punchy verdict lines and reassurances ("Time to own it.", "Hope, unease, irritation and relief are all answers."), "X, not Y" contrasts, and one closer shared by all three courses ("the course ends today, but your action plan doesn't").
2. **Compressed, insider phrasing.** Mostly in AI Futures and parts of CV1. Accurate, but it has to be decoded ("the institutions that served us because they needed us stop needing us").
3. **Stiff boilerplate repeated across docs.** Room openers, the help note, "Verbal primer for the survey!". The cheapest to fix, because one replacement covers many docs.

Two clarity problems sit alongside these: several questions packed into one item, and prompts that build on an exercise without saying what it was.

Some of the habits are in the guide's own examples ("Half-formed is fine; that's what the room is for", the "course ends today" closer), so new docs will keep reproducing them until the guide changes. That belongs to the guide's owner (section 7).

---

## 2. Decisions

Each entry gives the decision, who made it, the reason, and what it commits us to.

**Wording only.** *Andreas, 2026-10-03.* The complaint is about how the text reads. Structural problems found along the way are flagged as Content and left for a decision, not fixed in this pass.

**Claude flags, Andreas rewrites, Claude reviews.** *Andreas, 2026-10-03.* Having an AI rewrite text so that it sounds less AI-written is circular. Claude is better placed to spot the patterns than to avoid them. So each flag names a specific pattern that a person can check and overrule, rather than giving a general verdict. In Luc's 2026-09-26 tests, a model's broad "does this read as AI?" judgment did about as well as chance, while narrower questions did better. Commits us to: no voiced text written by Claude, and every flag naming its pattern.

**Suggestions, not direct edits, for anything that replaces existing text.** *Andreas, 2026-10-03.* Reviewers see old and new side by side instead of triaging which text is new. Flags are comments; they only add text, so they land direct.

**Lens Coach becomes Lens Tutor everywhere.** *Andreas, 2026-10-03.* Lens Coach was merged into Lens Tutor, and `lensacademy.org/coach` redirects to `lensacademy.org/tutor`. The rename changes the name and the link only, with no rewording.

**Shared files may be edited.** *Andreas, 2026-10-03.* They also feed AI Control 1 and 2, which are not live yet. Commits us to keeping section 5 current.

**"Accountability buddy" is the standard term.** *Andreas, 2026-10-04.* Most docs and the shared FAQ already say "buddy". AI Futures Meetings 2 and 3 say "partner" and change at their rewrite. Recorded in the style sheet as B7.

**Batch 2: general and shared issues first, then all of AI Futures.** *Andreas, 2026-10-06.* AIRF and CV1 cohorts are wrapping up, so nothing in those courses is urgent. AI Futures Meeting 4 runs the week of 2026-10-12, which leaves time to do the whole course rather than Meeting 4 alone. Shared and recurring lines come first, so the AI Futures rewrites start from settled wording instead of settling it doc by doc. Plan in section 3.

**Batch 2 covers the shared Participant FAQ, and AIRF's inline copies are synced by hand.** *Claude's working assumption, 2026-10-06. Not yet confirmed.* The FAQ is a shared block, so it belongs with the shared issues, even though the other non-Session-Doc tabs wait for later. AIRF's inline copies get the same changes copied in rather than being switched to the shared files, because switching is a structural change.

**Follow-up questions that sort participants may share an item.** *Andreas, 2026-10-04.* There is a tension between one question per item and leaving room for different answers. Follow-ups such as "if not, what stopped you?" or "if nothing changed, what would?" filter responses by a participant's situation, so they stay. Recorded in the style sheet under B1. Applied to CV1 Meeting 5, Room 1, items 1 and 3.

**"X ends, but Y doesn't" is allowed.** *Andreas, 2026-10-04.* Not a wholly prohibitive form. CV1 Meeting 5's Room 4 closer stays for now. Recorded in the style sheet under A2.

**Next week's meetings first.** *Andreas, 2026-10-03.* A cohort's docs are created from the masters at the top of each week. An edit accepted after that reaches nobody already enrolled, and a live copy has to be patched separately (see the note on masters and copies in [[AIRF Restructure Log]]). So the order follows the cohorts. For the week of 2026-10-05 that is AIRF Meeting 5, AI Futures Meeting 3 and CV1 Meeting 5.

**Flag only what fails a named check.** *Proposed by Claude, 2026-10-03. Not yet confirmed.* Unflagged text stays as it is. In the AI Futures course-page rewrite, the first bulk rewrite changed meanings, so the smallest change that fixes a problem is the safer one. The checks: can a participant act on it after one read; is there one question per item; does it state its point plainly; would a navigator say it out loud like this; does it rely on something the doc does not give; would anything be lost if it were cut; does it match the rest of the doc.

**Exercise reminders.** *Proposed by Claude, 2026-10-03. Not yet confirmed.* When a prompt builds on something participants did alone in the unit, it says in one line what that was and gives people who skipped it a way in. AI Futures Meeting 3, Room 1 is the model, and Room 3, item 3 is the counterexample. The guide's rule 7 already says a prompt never depends on optional written work; the proposal adds the one-line reminder as the way to meet it.

**A written style sheet.** *Proposed by Claude, 2026-10-03. Drafted 2026-10-04 after Andreas raised it again. Awaiting his review.* Without a written standard, a flag is only Claude's opinion. [[Meeting Doc Text Review - Style Sheet]] gives each habit and check a name a flag can cite, gathers the guide's rules, Andreas's working preferences and Luc's labels in one place, and says what to leave alone. It names the move for each habit, never replacement wording, in keeping with the decision above. Commits us to: flags from the next batch cite an entry, and changes to the sheet are logged here.

**Edits are credited to Andreas.** *Andreas, 2026-10-04.* Relay sessions open under his name, and both files carry `Andreas+Claude`, as the AIRF and CV1 files do. Edits made before 2026-10-04 show unattributed; the relay cannot change that after an edit has landed.

**Scope within a doc is what participants read.** *Claude's working assumption, 2026-10-03. Not yet confirmed.* That means the Session Doc tab and the Participant FAQ. The navigator run-sheet, pro-tips and glossary are not reviewed in this pass.

**Flag labels.** *Claude, 2026-10-03.*

- **AI (strong)**: a participant would likely notice it. **AI (mild)**: adds to the feel.
- **Clarity**: understandable, but packed or ambiguous.
- **Content**: accuracy or structure, not wording. Needs a decision, not a rewrite.
- **recurring**: the same line appears in other docs, so one replacement can be reused.
- **Note**: already works; keep it.

---

## 3. The plan

Stages 1 to 4 run once per batch of docs. The first batch is next week's three.

**Stage 0. Survey.** Done 2026-10-03. See section 1.

**Stage 1. Flag.** Claude adds comments to the Session Doc tab and FAQ of each doc in the batch, and to the shared blocks those docs include, each citing the style sheet entry the passage fails. Then Claude validates with drafts applied.

**Stage 2. Rewrite.** By hand, by Andreas, against the style sheet. Recurring lines are written once and reused: the "course ends today" closer, the Tutor help note, the "No judgment" reassurance, the Room 2 opener and "Verbal primer for the survey!". Content flags go to whoever owns that content. A flag's comment comes out once its passage is rewritten or deliberately kept.

**Stage 3. Review.** Claude checks each rewrite against the style sheet, and for:

- meaning drift against the original;
- claims and numbers against the source reading;
- the guide's limits: at most four questions and 120 words per room, no em dashes, a Tutor note on complex prompts;
- new AI patterns;
- a cold read of the Session Doc tab on its own, as in the guide's third check;
- the validator, with drafts applied.

**Stage 4. Accept.** Andreas accepts suggestions before the batch's docs are created. Anything accepted later means patching the live copies.

**Stage 5. Next batch.** The remaining twelve docs, in the order cohorts reach them, including the Tutor rename in their inline mentions.

**Stage 6. Hand-offs.** Anything outside our files, listed in section 7.

### Batch 2, from 2026-10-06: general and shared issues, then all of AI Futures

Order, decided by Andreas (section 2):

1. Andreas rewrites the shared blocks (group A) and settles one wording for each recurring line (group B).
2. Claude copies each settled wording into every doc of the three courses that still has the old line, as suggestions. This also finishes the Lens Coach to Lens Tutor rename, and brings AIRF's inline copies of the shared blocks into line.
3. Claude flags AI Futures Meetings 1, 2, 4 and 5, Meeting 4 first. Andreas rewrites and Claude reviews, as in batch 1. AI Futures Meeting 3's two kept flags go into the same pass.
4. Hand-offs (group C) go to section 7.

Worklist, found 2026-10-06. Counts cover AIRF, AI Futures and CV1 docs only.

**Group A. Shared blocks.** One rewrite reaches every doc that includes the block (section 5).

- **How today works, all three variants.**
    - "Today's shape" (Luc: call it Schedule or Agenda, one line per item with its length).
    - "if your group hit something the others should hear, that is the moment" (Luc: vague; A1).
    - "want to talk to the facilitator?", where every other line says navigator (B7).
    - The help box has drifted between variants: the AIRF one has no Tutor link but has a "Lost the doc link" bullet, which the other two lack.
- **Participant FAQ.**
    - The two flag removals still pending since 2026-10-03 (both "X, not Y" contrasts that carry meaning, A2).
    - The buddy answer says "You paired up in the first session". In a first meeting, pairing happens later that hour.
- **Open discussion.** "If you are too many people" reads awkwardly.
- **AIRF's inline copies.** Meeting 1 has its own copy of How today works, and all five AIRF docs have their own Participant FAQ. Each needs the same changes copied in.

**Group B. Recurring lines.** Each doc has its own copy. Andreas settles one wording, and Claude copies it into every doc.

- **Tutor help note.** Andreas's wording in CV1 Meeting 5 and AIRF Meeting 5: "Want help or clarification for this question? Ask your navigator or copy it into the Lens Tutor for an explanation." The old wording, still naming Lens Coach, is in:
    - AIRF Meetings 1 (2), 2 (2), 3 (1) and 4 (1);
    - CV1 Meetings 1 (2), 2 (2), 3 (2) and 4 (1);
    - AI Futures Meetings 1 (1) and 4 (1).

  AI Futures Meetings 2 and 5 have their own wording, also naming Lens Coach.
- **Other Lens Coach mentions.** AIRF Meeting 1's inline How today works (1), and AIRF Meetings 1 to 4's inline FAQs (3 each).
- **Room 1 check-in** ("How was working through this unit's content? … (No judgment, "I didn't finish" is a fine answer.)").
    - In several variants across AIRF Meetings 1 to 4, CV1 Meetings 1 to 4 and AI Futures Meeting 1.
    - AIRF Meeting 5 dropped "No judgment", and CV1 Meeting 5 kept it (A3). The follow-ups stay (B1 decision).
- **AIRF Room 2 opener.** "Then, as a group, discuss this question and write your shared response in the table:" in AIRF Meetings 2 to 4. AIRF Meeting 5 now starts "As a group".
- **AIRF Room 4.**
    - "Brainstorm and share the questions below before noting in the table:" in AIRF Meetings 2 to 4.
    - "Verbal primer for the survey!" in AIRF Meetings 2 and 3. It was deleted in Meeting 5.
- **Closing question timing.** AI Futures Meetings 1 and 2 say "two hours ago" for a 90-minute meeting. AIRF and CV1 say 90 minutes.
- **One-off fixes.**
    - "Accountability partner" in AI Futures Meeting 2 (B7).
    - "Gettable" in CV1 Meeting 2. The guide asks for "tractable".
    - Em dashes in the Session Doc text of AIRF Meetings 2 (4) and 3 (2). Course Authoring bans them.

**Group C. Hand-offs.** See section 7.

---

## 4. Status by doc

| Doc | Runs | Rename | Flags | Rewrite | Review | Accepted |
|---|---|---|---|---|---|---|
| AIRF Meeting 5 | week of 2026-10-05 | done 2026-10-04 | done 2026-10-03 | done for this pass 2026-10-05 | done 2026-10-05 | done 2026-10-05; 6 Session Doc flags and 1 FAQ flag kept for the full pass |
| AI Futures Meeting 3 | week of 2026-10-05 | done 2026-10-04 | done 2026-10-03 | done for this pass 2026-10-05 | done 2026-10-05 | done 2026-10-05; 2 minor flags kept for the full pass |
| CV1 Meeting 5 | week of 2026-10-05 | done 2026-10-04 | done 2026-10-03 | done 2026-10-04 | done 2026-10-04 | done 2026-10-05 |
| Shared How today works (three variants), Participant FAQ, Open discussion | batch 2 | done 2026-10-04 | done 2026-10-03; worklist 2026-10-06 | todo | todo | todo |
| Master template | n/a | done 2026-10-04 | not flagged | n/a | n/a | n/a |
| AIRF Meetings 1 to 4 | cohorts wrapping up | todo | recurring lines only, batch 2 | todo | todo | todo |
| AI Futures Meetings 1, 2, 4 and 5 | Meeting 4 week of 2026-10-12 | todo | batch 2 | todo | todo | todo |
| CV1 Meetings 1 to 4 | cohorts wrapping up | todo | recurring lines only, batch 2 | todo | todo | todo |

---

## 5. Shared files and who else they reach

Edits to these files change every doc that includes them, not only the three courses under review.

| Shared file | Included by |
|---|---|
| Session Doc - How today works | CV1 (all five meetings), AI Futures Meetings 4 and 5, AI Control 1, AI Control 2 and AI Control Fundamentals (all five meetings each) |
| Session Doc - How today works (3 rooms) | AI Futures Meetings 1 to 3 |
| Session Doc - How today works (AI Risk Fundamentals) | AIRF Meetings 2 to 5. Meeting 1 has its own inline copy |
| Participant FAQ | CV1, AI Futures, AI Control 1, AI Control 2, AI Control Fundamentals. AIRF has inline FAQ copies |
| Session Doc - Open discussion | Every meeting doc of the three courses, and the other courses above |

The Lisbon Fellowship docs use their own Lisbon variants and are not affected. As of 2026-10-03 neither AI Control course is live. AI Control Fundamentals was added to the vault after 2026-10-03 and was found including these files on 2026-10-06.

---

## 6. Log

| Date | Change | Files | Why | How it landed |
|---|---|---|---|---|
| 2026-10-03 | Survey of the guide, master template, all fifteen Session Doc tabs and the shared blocks | Read only | Scope the problem before changing anything | n/a |
| 2026-10-03 | **Decisions: wording only; Claude flags, Andreas rewrites, Claude reviews; suggestions rather than direct edits; next week's meetings first** | Plan | Section 2 | Plan only |
| 2026-10-03 | Flagged passages: 19 in AIRF Meeting 5, 15 in AI Futures Meeting 3, 10 in CV1 Meeting 5, 2 in each shared How today works block, 2 in the shared Participant FAQ | Those files | Stage 1 for next week's batch | Direct. Comments only add text |
| 2026-10-03 | Lens Coach renamed to Lens Tutor, name and link only | AIRF Meeting 5 (4), AI Futures Meeting 3 (1), CV1 Meeting 5 (1), each shared How today works block (1), shared Participant FAQ (3), Master template (3) | Coach was merged into Tutor | Pending, 15 suggestions |
| 2026-10-03 | Checked four claims against their sources while flagging | AIRF Meeting 5, AI Futures Meeting 3, CV1 Meeting 5 | A flag that calls something wrong needs a source | Log only. The WWII quote is wrong and the capstone description does not match its course file (section 7). The AI Futures Room 2 readings and the CV1 Room 2 quote match their lenses |
| 2026-10-03 | Validator run with drafts applied, scoped to the three courses | All three courses | Check that the comments and suggestions break nothing | No meeting-doc errors. The remaining errors predate this work |
| 2026-10-03 | Created this file | This file | Record which other courses the shared files reach | Direct, new file |
| 2026-10-04 | Rebuilt this file as a plan and log | This file | Andreas asked for the reasons behind the changes, not only a record of them, in a plan visible for posterity | Direct |
| 2026-10-04 | Rename suggestions accepted | The three docs, the three shared How today works blocks, the shared Participant FAQ, the Master template | Coach was merged into Tutor | Accepted by Andreas. A search afterwards finds no "Coach" left in those files |
| 2026-10-04 | Attribution: relay sessions open under Andreas's name from now on, and `Andreas+Claude` added to this file | This file | Andreas's instruction, matching the AIRF and CV1 files | Direct |
| 2026-10-04 | Drafted the style sheet | [[Meeting Doc Text Review - Style Sheet]] | Gives flags and reviews a written standard to cite (section 2) | Direct, new file |
| 2026-10-04 | Style sheet accepted as a working draft; "accountability buddy" made the standard term | [[Meeting Doc Text Review - Style Sheet]] | Andreas's review. Generalizing the sheet for other courses is deferred until it settles (section 7) | Direct |
| 2026-10-04 | Tested how Claude can remove its own flags, on a scratch file, then trashed the file | Lens Edu/_scratch - comment removal test | Andreas had no known way to remove comments authored by Claude, so clearing flags falls to Claude | Removal works only when the edit quotes the comment exactly, and it lands pending. Scratch file in the trash |
| 2026-10-04 | First rewrite pass on CV1 Meeting 5 | meetings/Compute Verification 1/Meeting 5 | Stage 2 for next week's batch | Edited by Andreas |
| 2026-10-04 | First review of that pass | meetings/Compute Verification 1/Meeting 5 | Stage 3 | Review given in chat, no doc changes. Resolved: Room 2 help note and setup, Room 4 item 1. Still open: Room 1 items 1 to 3 and its table header, Room 2 now 132 words against the 120 limit, the Room 4 closer, and the wrap-up. Checked: "AI 2040's Plan A" matches the CV1 Unit 1 module; the Compute Verification 2 link is live; the Room 2 quote is the authorization lens's summary line, not its body text. Found: Compute Verification 2's own course page also describes the capstone differently from the doc (section 7) |
| 2026-10-04 | Second rewrite pass on CV1 Meeting 5 | meetings/Compute Verification 1/Meeting 5 | Andreas's response to the first review | Edited by Andreas |
| 2026-10-04 | **Decisions on the first review: "After both courses is" kept on purpose; Room 2's summary-line quote and length deferred; the waitlist wording confirmed** | meetings/Compute Verification 1/Meeting 5 | Not every participant takes every course in the track, so the wrap-up should not imply a set progression. The Room 2 quote comes from CV1's own text and goes when CV1 is restructured. Applying for Compute Verification 2 puts people on a waitlist that notifies them when registration opens | Andreas, 2026-10-04 |
| 2026-10-04 | Second review, and flags brought up to date | meetings/Compute Verification 1/Meeting 5 | Stage 3, and the old flags described wording that had changed | Resolved: Room 1 items 2 and 3 wording ("resonated", "valid feelings", "validated", the no-change case) and the Room 1 table header. Two resolved flags removed, six stale flags replaced with current ones that cite style sheet entries: all eight pending. Two flags left as they were because they still apply (Room 1 item 1, Room 4 closer). The validator returned 502 twice, so this round is not validated yet; the changes are comments only |
| 2026-10-04 | Third rewrite pass on CV1 Meeting 5: the small fixes from the second review | meetings/Compute Verification 1/Meeting 5 | Andreas judged the doc finished; what remains is deferred or kept on purpose (section 2) | Edited by Andreas |
| 2026-10-04 | **Decisions: follow-ups that sort participants may share an item; "X ends, but Y doesn't" allowed; keep the page light** | Style sheet B1 and A2, conventions | Section 2 and the conventions | Andreas, 2026-10-04 |
| 2026-10-04 | CV1 Meeting 5 resolved: every flag removed, including the replacements filed in the second review, and a broken suggestion fragment repaired at the end of the essay bullet in the wrap-up | meetings/Compute Verification 1/Meeting 5 | The doc is done; the deferred items live in section 7, not on the page | Nine flag removals pending for Andreas to accept, one per remaining flag. The fragment repair landed direct |
| 2026-10-05 | CV1 Meeting 5 flag removals accepted | meetings/Compute Verification 1/Meeting 5 | Closes the doc | Accepted by Andreas. A search afterwards finds no comment or suggestion markup left |
| 2026-10-05 | Pruned the AIRF Meeting 5 flags before its rewrite | meetings/AI Risk Fundamentals/Meeting 5, meetings/shared/Participant FAQ | The keep-the-page-light convention and the B1 and A2 decisions came after these flags were filed | Removed 7 of 19 in AIRF Meeting 5: Room 1 item 1 (B1), the Room 2 opener (small fix), the help note (reuse the CV1 Meeting 5 wording), Room 3 item 2 (natural pair), the Room 4 closer (A2), and both "X, not Y" flags in the inline FAQ, whose contrasts carry meaning. Removed the same two from the shared Participant FAQ. 12 kept. The shared How today works flags stay, since they carry Luc's comments. All removals pending |
| 2026-10-05 | **Decision: this pass covers the Session Doc tab only** | AIRF Meeting 5 onward | The FAQ, run-sheet and glossary tabs wait for a later pass | Andreas, 2026-10-05 |
| 2026-10-05 | First rewrite pass on AIRF Meeting 5, including deleting the Room 1 scribe line | meetings/AI Risk Fundamentals/Meeting 5 | Andreas: the line dated from before the back-together format, when participants carried answers into the next room | Edited by Andreas |
| 2026-10-05 | First review of that pass | meetings/AI Risk Fundamentals/Meeting 5 | Stage 3 | Review in chat. Resolved and their flags removed (pending): Room 1 item 3, "Time to own it", "Verbal primer for the survey", the Navigator claim. Still flagged: the WWII line, the Room 2 block, the rehearsal-audience line, the Room 4 opener, the wrap-up summary line and the "for the person you talked to" list. Found by counting: Room 2 at 121 words and Room 3 at 136, against the 120 limit. Found by checking: the public site calls AI Futures "Advanced Strategy in AI Safety", not the doc's name; intensives run one week, not one unit; the Meeting 5 survey asks about navigating but does not appear to offer the courses the doc says it does |
| 2026-10-05 | Second rewrite pass on AIRF Meeting 5 | meetings/AI Risk Fundamentals/Meeting 5 | Andreas's response to the first review | Edited by Andreas. Fixed: the WWII line now describes the care countries would need rather than cost, and quotes the book exactly; the Room 3 scribe line matches item 2; AI Futures named as on the public site; intensives described as one week |
| 2026-10-05 | **Decision: minor flags stay on the page until the full pass** | AIRF Meeting 5 onward | Saves time this week. Flags that do not get in the way of running the meeting wait for the later full pass, rather than being resolved or removed now | Andreas, 2026-10-05 |
| 2026-10-05 | Second review, and flags updated | meetings/AI Risk Fundamentals/Meeting 5 | Stage 3 | WWII flag removed (pending). One flag added at Andreas's request, on the Room 1 opener: "three things" against a conditional item 3, and "last meeting" against "last unit" (direct). Kept for the full pass: the Room 2 block, the rehearsal-audience line, the Room 4 opener, and the two wrap-up flags |
| 2026-10-05 | First rewrite pass on AI Futures Meeting 3 | meetings/Forecasting, Modeling, and Shaping AI Futures/Meeting 3 | Stage 2 | Edited by Andreas. Room 3's last question and its table header now both ask the probability that the first harmful AI is contained rather than aligned. "Partner" became "buddy" |
| 2026-10-05 | **Room 2 of AI Futures Meeting 3 is a new group** | meetings/Forecasting, Modeling, and Shaping AI Futures/Meeting 3 | Andreas: the "New group. Names first" line was dropped, not withheld on purpose. The Room 1 table still works because the scribe writes one line per person. Whether every room carries the line is a consistency issue across meetings (section 7) | Andreas, 2026-10-05 |
| 2026-10-05 | First review of that pass | meetings/Forecasting, Modeling, and Shaping AI Futures/Meeting 3 | Stage 3 | Review in chat. Nine flags removed, all pending: the Room 1 opener and item 1, the Room 1 scribe line, Room 2 item 1 (B1), the mirrored pair, the Room 3 last question, the "not a traceable change" pair (A2), "partner", and the closing feedback line. Six kept: the Room 2 "about this", the institutions line, the Room 2 closing question, the Room 3 exercise reminder, and two minor ones for the full pass (the catastrophe definition, "the group will wait"). Found by counting: Room 2 at 126 words and Room 3 at 129, against the 120 limit |
| 2026-10-05 | Second rewrite pass on AI Futures Meeting 3 | meetings/Forecasting, Modeling, and Shaping AI Futures/Meeting 3 | Andreas's response to the first review | Edited by Andreas. Room 2 now names the readings' authors and states the institutions point plainly; Room 3 item 3 now says what the conditions exercise asked |
| 2026-10-05 | Second review | meetings/Forecasting, Modeling, and Shaping AI Futures/Meeting 3 | Stage 3 | Review in chat. Two flags removed, pending: the institutions aphorism and the Room 3 exercise reminder. Raised in chat: Room 2 names Wentworth alongside Soares and Kulveit, but the item describes two positions (Soares inside the system, Kulveit et al. between systems), and the unit's "Two Accounts of the Core Difficulty" lens pairs Wentworth against Soares; "needed people to build them" narrows the reading's point, which is that institutions depend on people as workers and consumers, and "only" overstates the tldr's "partly"; Room 3 item 3 still gives people who skipped the exercise nothing to say |
| 2026-10-05 | Validator run on all three courses with drafts applied | AIRF, AI Futures, CV1 | Andreas asked whether the earlier meetings had been validated; CV1 had not been since its rewrite (502s), and AIRF not at all since its rewrite | No issues in any meeting doc. AIRF: 0 errors. AI Futures: 2 errors in Unit 2 lens files. CV1: 25 errors in lenses, learning outcomes, widgets and an article (work-in-progress tags). All predate this work. The validator checks syntax and links, not wording or the guide's word and ask limits |
| 2026-10-05 | Third rewrite pass on AI Futures Meeting 3, and third review | meetings/Forecasting, Modeling, and Shaping AI Futures/Meeting 3 | Andreas's response to the second review | Edited by Andreas: Room 2 now names only Soares and Kulveit et al. and says what they disagree about; its closing ask is now two separate questions. Two flags removed, pending. Room 3 item 3 left without a line for people who skipped the conditions exercise: Andreas, because the idea is first introduced in that lens. The exercise is a required question in the lens, not optional work, and the prompt now lists what the conditions cover, so the room can still run |
| 2026-10-05 | **First batch done.** Andreas fixed the last typos in AI Futures Meeting 3 and accepted its flag removals; AIRF Meeting 5's were already accepted | AIRF Meeting 5, AI Futures Meeting 3, CV1 Meeting 5 | All three meetings for the week of 2026-10-05 are ready before their docs are created | A search afterwards finds no pending changes in any of the three. Only the flags deliberately kept for the full pass remain. "Outgrew" in AI Futures Meeting 3, Room 2 kept by Andreas |
| 2026-10-05 | Shared Participant FAQ flag removals left pending | meetings/shared/Participant FAQ | Postponed with the rest of the non-Session-Doc tabs to the later pass (2026-10-05 decision) | 2 removals still pending |

---

## 7. Open items

### Content: needs a decision, not a rewrite

- **AIRF Meeting 5, Room 2. Resolved 2026-10-05:** Andreas rewrote the line to describe the care countries would need and quote the book exactly. The original problem, kept for the record: the doc quoted the authors as saying the cost would be "not even 1% as costly as WWII". That wording is not in the book; it appears only in the book-club design notes. Chapter 13 argues that claiming countries could never do this amounts to claiming they "could not possibly care even 1% as much as they cared to fight World War II". That is about willingness, not cost.
- **AI Futures Meeting 3, Room 3. Resolved 2026-10-05:** Andreas made the table header match the question (contained rather than aligned).
- **AI Futures goes by four names.** The public course page says "Advanced Strategy in AI Safety", the platform's course title is "AI Futures: Forecasting & Strategy", its final survey says "AI Futurism: Forecasting and Strategy", and the meetings folder says "Forecasting, Modeling, and Shaping AI Futures". AIRF Meeting 5 now uses the public name (2026-10-05). For whoever owns the course.
- **"New group. Names first" missing from some rooms.** AI Futures Meeting 3, Room 2 is a new group but lacks the line (Andreas, 2026-10-05). Check every meeting for the same gap in the full pass.
- **CV1 Meeting 5, wrap-up.** Describes the capstone as one fixed task, a verification regime for a three-month emergency pause. The Capstone course file describes choosing one brief from a set or proposing your own, and the Compute Verification 2 course page describes ranking the mechanisms by feasibility and designing a regime of your own. The three-month pause appears on that page as a Compute Verification 2 Unit 1 exercise, not as the capstone. Andreas expects this to be settled in a CV1 rewrite (2026-10-04).
- **CV1 Meeting 5, wrap-up.** Says the Unit 1 success-scenario essay is revisited later in the track. The Unit 1 lens says the same, but no other course file or lens mentions the essay, so the revisit may not exist yet. Deferred to the CV1 restructure (Andreas, 2026-10-04).
- **CV1 Meeting 5, Room 2.** 132 words against the guide's 120 limit, mostly because of the bolded summary line from the hardware-authorization lens. Deferred to the CV1 restructure (Andreas, 2026-10-04), so this meeting runs over the limit for now.

### Raised by Luc on AIRF Meeting 1

- Whether pointing participants to the Tutor helps, since it cannot see the session. The help note has them paste the question in, which covers part of this.
- "Today's shape" should become "Schedule" or "Agenda", one line per item with its length. Flagged on the shared blocks.

### Style sheet

- **Make it usable by any course.** *Andreas, 2026-10-04.* It is written for these three courses and quotes their docs throughout. Generalize it once it has settled through this work: separate the course-independent entries from the examples, and say how another course would adapt it.

### For the owner of [[AI Guide/Writing Meeting Docs]]

- Rule 6 still requires a "Lens Coach" note.
- Several of the guide's examples carry the habits in section 1.

### Unverified

- How the meeting-doc renderer handles comments. The course rules say comments are stripped before parsing, but nobody has watched a doc render with them in. It stops mattering for any flag whose passage is rewritten.

### Outside this project

- The AI Control and Lisbon docs, and the Lisbon shared files, still say Lens Coach.
