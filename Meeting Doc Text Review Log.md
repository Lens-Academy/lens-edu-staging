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

**What this is.** A pass over the participant-facing text of the meeting docs for AI Risk Fundamentals (AIRF), AI Futures (Forecasting, Modeling, and Shaping AI Futures) and Compute Verification 1 (CV1), so the questions read as written by a person. It is not a restructure and not a reformat. AI Control 1 joined the scope for the general and shared edits on 2026-10-10.

**Why.** Participants have said the questions are easy to tell apart as AI-written, and that this frustrates them even when they understand what is being asked. Reported by Andreas, 2026-10-03.

**Status, 2026-10-05.** The first batch is done: AIRF Meeting 5, AI Futures Meeting 3 and CV1 Meeting 5, the meetings that run the week of 2026-10-05, have been flagged, rewritten by Andreas, reviewed and accepted, Session Doc tab only. Minor flags stay on the page for a later full pass, which also covers the other tabs and the shared blocks (section 7 and the log). The style sheet is a working draft Andreas accepted as a starting point.

**Status, 2026-10-06.** Batch 2 has started: general and shared issues first, then all of AI Futures, with Meeting 4 running the week of 2026-10-12. The worklist is in section 3.

**Status, 2026-10-10.** Andreas rewrote the shared blocks (How today works, Open discussion, Participant FAQ), and the other two How today works variants were brought into line as suggestions. Repeated lines are now reviewed one at a time, starting with the Tutor help note. Later the same day the help note was settled and copied into all four courses, AIRF's own How today works file was set to retire, and AI Control 1 joined the scope.

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

**Repeated lines are reviewed one at a time, including the ones settled in batch 1.** *Andreas, 2026-10-10.* There is time to refine them into better versions rather than copying batch 1's wording everywhere. This replaces Claude's 2026-10-06 proposal to copy batch 1's versions into every doc by default. "Two hours" becomes "90 minutes" either way: meetings last 90 minutes.

**Buddy groups favor trios over pairs.** *Andreas, 2026-10-10.* People drop out over a course. When one person in a pair drops out, the other is left alone; a trio still leaves two. The shared FAQ's buddy answer now says so. Still to follow: AI Futures Meeting 1 ("Your navigator pairs you up", and its "Buddy pairs" table), AI Control 1 Meeting 1 ("pair up (a trio is fine)"), AIRF's inline FAQ copies, and the master template's FAQ placeholder. AIRF Meeting 1 and CV1 Meeting 1 already form buddy groups from the Room 4 breakout room, but split a room of four or more into two groups, which turns four people into two pairs. The singular "your accountability buddy" in many Room 4s and wrap-ups also assumes a pair. These form the next repeated line to review (section 3).

**How today works drops the "Lost the doc link" line.** *Andreas, 2026-10-10.* What it was for is unclear. Its advice, the Zoom chat, does not reach people inside breakout rooms, and the Participant FAQ covers the question anyway.

**CV1's docs are retitled when CV1 gets its own pass.** *Andreas, 2026-10-10.* Their titles say "Compute Verification Part 1"; the course is "Compute Verification 1".

**The help note reads "If a question is unclear, ask your navigator or copy it into Lens Tutor."** *Andreas, 2026-10-10.* Chosen over his other candidate, "Want help or clarification? Ask your navigator or copy it into Lens Tutor.", in which "it" has no question to point back to. "Ask your navigator" stays: the navigator moves between rooms and can monitor the conversations, so there are chances to ask besides the Ask for Help button. Written without "the": Lens Tutor is a name, and "the Lens Tutor" every time reads as stilted unless the sentence calls for it (Andreas, 2026-10-10). Copied into every note in the four courses in scope, with the link. AI Futures Meeting 5's signpost note keeps its own wording, since it asks for something specific to that room. Recorded in the style sheet under D.

**AI Control 1 joins the scope for general and shared edits.** *Andreas, 2026-10-10.* It includes the shared blocks and carries the same recurring lines. AI Control 2, AI Control Fundamentals, Lisbon and AI Safety and Philosophy stay out.

**AIRF's How today works file retires.** *Andreas, 2026-10-10.* Once the 2026-10-10 suggestions were accepted it matched the general file, and no reason for keeping it separate was found. AIRF Meetings 2 to 5 include the general file instead. AIRF Meeting 1's inline copy held the same old text and Luc's three comments on it, and is to be replaced by the same include. For How today works, this replaces the 2026-10-06 assumption that AIRF's inline copies are synced by hand. The AIRF inline FAQs are not affected.

**The FAQ keeps pointing to the Zoom chat for the doc link.** *Andreas, 2026-10-10.* The link is posted in the main room's chat, where it works. The chat does not carry into breakout rooms, but people there are told to contact the navigator anyway.

**Sharing between rooms should bring out what other groups did not reach.** *Andreas, 2026-10-10.* The How today works line about sharing great insights is there so the back-together slot hears something new, not the same surface result from every group. Andreas rewrote it the same day as "if your group made interesting observations", which drops the quality bar that "great insights" set.

**The guide's new Room 4 and wrap-up rules are applied in this pass.** *Andreas, 2026-10-10.* Elias added two rules to the guide on 2026-10-10: nothing in a doc summarises the next unit's reading, so Room 4 only asks what could stop people finishing it and their plan; and the wrap-up list does not repeat what Room 4 already asked, such as sending the plan to the buddy or giving feedback. What replaces the current lines is likely to be one standard wording anyway, so it belongs with the recurring lines.

**The navigator forms buddy groups, in threes.** *Andreas, 2026-10-10.* The navigator sets up the breakout rooms, so participants never split a room themselves, and the "if you are four or more, split into two groups" clause goes. The shared run-sheet already tells navigators to aim for three per room, with four when the numbers do not divide. *Amended by Andreas later on 2026-10-10:* for the buddy room, leftover people make one or two pairs rather than a four (seven people make three rooms), since a four that lasts the whole course may be too many. Stated in the Meeting 1 run-sheet's buddy section.

**The Room 4 buddy line.** *Andreas, 2026-10-10.* "The people in this breakout room are your accountability buddies for the rest of the course. Swap contact details in the table below. Before each meeting check in with one another: did you finish, are you coming?" It combines AIRF Meeting 1's "for the rest of the course" with AI Control 1's check-in question, now that the participants' copy of the buddy explanation is gone. It drops the "Accountability buddies:" label, which repeated the term, and AI Control 1's "pair up", which made no sense for people already in a room together.

**Room 4's next-unit item: no reading time, and a short "what's next" may stay.** *Andreas, 2026-10-10, pending a check with Elias.* Participants can see the course's own time estimates. A long summary of the next unit defeats the point, but saying in a few words what comes next still has value. This sits between the guide's new rule (nothing summarises the next unit) and its older rule 7 (one plain sentence with a rough time), which the guide has not yet reconciled. Part 2 of the buddy wording waits for Elias's answer.

**"Buddies", plural.** *Andreas, 2026-10-10.* "Your group" where that reads better. The singular dates from when the wording assumed pairs, even though trios already happened. Recorded in the style sheet under B7.

**What the navigator needs goes in the run-sheet, not the participant view.** *Andreas, 2026-10-10.* AIRF and CV1 Meeting 1 showed participants the buddy explanation just before Room 4 said the same thing. The explanation moves to a "Buddy steps" section of the run-sheet, and the navigator still gives it in the whole-group slot before Room 4, as the guide asks.

**Navigator-facing text is in scope.** *Andreas, 2026-10-10.* The run-sheet is part of the meeting doc, so it is reviewed with the rest. This replaces Claude's 2026-10-03 working assumption that only the Session Doc tab and the FAQ were in scope.

**AI Futures Meeting 1 is likely to become a four-room meeting.** *Andreas, 2026-10-10.* Buddies are hard to set up when everyone is in the main room, as Meeting 1's close does now. A structural change, for the AI Futures pass; its buddy setup then follows the other courses.

**Follow-up questions that sort participants may share an item.** *Andreas, 2026-10-04.* There is a tension between one question per item and leaving room for different answers. Follow-ups such as "if not, what stopped you?" or "if nothing changed, what would?" filter responses by a participant's situation, so they stay. Recorded in the style sheet under B1. Applied to CV1 Meeting 5, Room 1, items 1 and 3.

**"X ends, but Y doesn't" is allowed.** *Andreas, 2026-10-04.* Not a wholly prohibitive form. CV1 Meeting 5's Room 4 closer stays for now. Recorded in the style sheet under A2.

**Next week's meetings first.** *Andreas, 2026-10-03.* A cohort's docs are created from the masters at the top of each week. An edit accepted after that reaches nobody already enrolled, and a live copy has to be patched separately (see the note on masters and copies in [[AIRF Restructure Log]]). So the order follows the cohorts. For the week of 2026-10-05 that is AIRF Meeting 5, AI Futures Meeting 3 and CV1 Meeting 5.

**Flag only what fails a named check.** *Proposed by Claude, 2026-10-03. Not yet confirmed.* Unflagged text stays as it is. In the AI Futures course-page rewrite, the first bulk rewrite changed meanings, so the smallest change that fixes a problem is the safer one. The checks: can a participant act on it after one read; is there one question per item; does it state its point plainly; would a navigator say it out loud like this; does it rely on something the doc does not give; would anything be lost if it were cut; does it match the rest of the doc.

**Exercise reminders.** *Proposed by Claude, 2026-10-03. Not yet confirmed.* When a prompt builds on something participants did alone in the unit, it says in one line what that was and gives people who skipped it a way in. AI Futures Meeting 3, Room 1 is the model, and Room 3, item 3 is the counterexample. The guide's rule 7 already says a prompt never depends on optional written work; the proposal adds the one-line reminder as the way to meet it.

**A written style sheet.** *Proposed by Claude, 2026-10-03. Drafted 2026-10-04 after Andreas raised it again. Awaiting his review.* Without a written standard, a flag is only Claude's opinion. [[Meeting Doc Text Review - Style Sheet]] gives each habit and check a name a flag can cite, gathers the guide's rules, Andreas's working preferences and Luc's labels in one place, and says what to leave alone. It names the move for each habit, never replacement wording, in keeping with the decision above. Commits us to: flags from the next batch cite an entry, and changes to the sheet are logged here.

**Edits are credited to Andreas.** *Andreas, 2026-10-04.* Relay sessions open under his name, and both files carry `Andreas+Claude`, as the AIRF and CV1 files do. Edits made before 2026-10-04 show unattributed; the relay cannot change that after an edit has landed.

**Scope within a doc is what participants read.** *Claude's working assumption, 2026-10-03. Not yet confirmed.* That means the Session Doc tab and the Participant FAQ. The navigator run-sheet, pro-tips and glossary are not reviewed in this pass. *Superseded for the run-sheet on 2026-10-10: Andreas put navigator-facing text in scope (above).*

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

Progress, 2026-10-10. Group A: Andreas rewrote How today works, Open discussion and the Participant FAQ; the 3-room and AIRF variants were brought into line with his How today works as suggestions. Group B: the help note is first in the one-at-a-time review; the "two hours" lines in AI Futures Meetings 1 and 2 are suggested as "90 minutes".

Progress, later on 2026-10-10. Group A accepted, apart from one FAQ typo. Group B: the help note is settled and copied into AIRF (7), AI Futures (3), CV1 (8) and AI Control 1 (10) as suggestions. Next up is the buddy wording, now that groups aim for trios (section 2). AIRF's How today works file is retiring (section 2).

---

## 4. Status by doc

| Doc | Runs | Rename | Flags | Rewrite | Review | Accepted |
|---|---|---|---|---|---|---|
| AIRF Meeting 5 | week of 2026-10-05 | done 2026-10-04 | done 2026-10-03 | done for this pass 2026-10-05 | done 2026-10-05 | done 2026-10-05; 6 Session Doc flags and 1 FAQ flag kept for the full pass |
| AI Futures Meeting 3 | week of 2026-10-05 | done 2026-10-04 | done 2026-10-03 | done for this pass 2026-10-05 | done 2026-10-05 | done 2026-10-05; 2 minor flags kept for the full pass |
| CV1 Meeting 5 | week of 2026-10-05 | done 2026-10-04 | done 2026-10-03 | done 2026-10-04 | done 2026-10-04 | done 2026-10-05 |
| Shared How today works (three variants), Participant FAQ, Open discussion | batch 2 | done 2026-10-04 | done 2026-10-03; worklist 2026-10-06 | done 2026-10-10 (Andreas) | done 2026-10-10 | done 2026-10-10, apart from one FAQ typo; the AIRF variant is retiring |
| Master template | n/a | done 2026-10-04 | not flagged | n/a | n/a | n/a |
| AIRF Meetings 1 to 4 | cohorts wrapping up | todo | recurring lines only, batch 2 | todo | todo | todo |
| AI Futures Meetings 1, 2, 4 and 5 | Meeting 4 week of 2026-10-12 | todo | batch 2 | todo | todo | todo |
| CV1 Meetings 1 to 4 | cohorts wrapping up | todo | recurring lines only, batch 2 | todo | todo | todo |
| AI Control 1 Meetings 1 to 5 | not live: no course file links them (2026-10-10) | already Lens Tutor | recurring lines only, batch 2 (in scope from 2026-10-10) | n/a | n/a | help note pending 2026-10-10 |

---

## 5. Shared files and who else they reach

Edits to these files change every doc that includes them, not only the three courses under review.

| Shared file | Included by |
|---|---|
| Session Doc - How today works | AIRF Meetings 2 to 5 (from 2026-10-10), CV1 (all five meetings), AI Futures Meetings 4 and 5, AI Control 1, AI Control 2 and AI Control Fundamentals (all five meetings each) |
| Session Doc - How today works (3 rooms) | AI Futures Meetings 1 to 3 |
| Session Doc - How today works (AI Risk Fundamentals) | Retired 2026-10-10 and moved to the trash. AIRF Meetings 2 to 5 now include the general file; Meeting 1 keeps its own inline copy |
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
| 2026-10-06 | **Decision: batch 2 is general and shared issues first, then all of AI Futures** | Plan | Section 2 | Andreas, 2026-10-06 |
| 2026-10-06 | Worklist for batch 2: shared blocks, lines repeated across docs, hand-offs | Section 3 | Found by reading the shared files and searching the three courses' docs for each repeated line | Log only, no doc changes. Also found: AI Control Fundamentals now includes the shared blocks (section 5) |
| 2026-10-10 | Andreas rewrote the shared How today works, Open discussion and Participant FAQ | meetings/shared | Group A of batch 2 | Edited by Andreas. "Today's agenda" replaces "Today's shape", "navigator" replaces "facilitator", the "hit something" line is rewritten, the buddy answer describes trios |
| 2026-10-10 | **Decisions: one-at-a-time review of repeated lines; trios; "Lost the doc link" dropped; CV1 retitled in its own pass** | Plan | Section 2 | Andreas, 2026-10-10 |
| 2026-10-10 | 3-room and AIRF How today works brought into line with Andreas's version; typo fixes in How today works ("greeat") and Open discussion ("conversatio"); old flags on all three How today works variants removed | meetings/shared | Andreas's request. Each variant keeps its own schedule | Pending, 10 suggestions. The AIRF variant now matches the general one, apart from one curly apostrophe. No reason for a separate AIRF file was found in the AIRF restructure log or elsewhere in the vault (section 7) |
| 2026-10-10 | "Two hours" changed to "90 minutes" | AI Futures Meetings 1 and 2 | Meetings last 90 minutes (Andreas) | Pending, 2 suggestions |
| 2026-10-10 | Flagged the Kulveit et al. line in AI Futures Meeting 3, Room 2 | meetings/Forecasting, Modeling, and Shaping AI Futures/Meeting 3 | Participant feedback from the week of 2026-10-05, relayed by Andreas: some found it an unfair account of the paper. A known cost of shortening the line for time | Direct, comment only. For the full pass |
| 2026-10-10 | Earlier suggestions accepted: the How today works variants, Open discussion, and the two old FAQ flag removals | meetings/shared | Group A | Accepted by Andreas. A search afterwards finds the AIRF How today works file identical to the general one apart from one curly apostrophe |
| 2026-10-10 | **Decisions: help note wording; AI Control 1 in scope; AIRF How today works retires; the FAQ keeps the Zoom chat; sharing between rooms aims at what is new** | Plan | Section 2 | Andreas, 2026-10-10 |
| 2026-10-10 | Surveyed AI Control 1 for shared and recurring issues | meetings/AI Control 1, Meetings 1 to 5 | Added to the scope | Read only. Already says Lens Tutor and "90 minutes ago", and has no em dashes in the Session Doc text. Found: the help note twice in every meeting; "pair up (a trio is fine)" in Meeting 1, Room 4; the singular "your accountability buddy" in Meetings 1 to 5 |
| 2026-10-10 | Help note replaced with Andreas's wording | AIRF Meetings 1 (2), 2 (2), 3, 4 and 5; AI Futures Meetings 1, 2 and 4; CV1 Meetings 1 (2), 2 (2), 3 (2), 4 and 5; AI Control 1 Meetings 1 to 5 (2 each) | Section 2 | Pending, 28 suggestions. One note each in AIRF Meetings 1 and 2 had no Tutor link; the new note carries it |
| 2026-10-10 | AIRF Meetings 2 to 5 switched to the general How today works | meetings/AI Risk Fundamentals, Meetings 2 to 5 | Section 2 | Pending, 4 suggestions. The AIRF file goes to the trash after they are accepted |
| 2026-10-10 | AIRF Meeting 1's inline How today works left in place for now | meetings/AI Risk Fundamentals/Meeting 1 | The relay refuses any edit that removes a comment a person wrote, and the block holds Luc's three | Blocked. Once Andreas deletes Luc's three comments on the block, one suggestion swaps it for the include. Luc's Room 1 comment is outside the block and stays. What remains open from his comments is in section 7 |
| 2026-10-10 | Comments added to the guide: the Lens Coach note in rules 6 and 7 and two examples; "two hours ago" in the closing-question example; the "pair up" Room 4 example | AI Guide/Writing Meeting Docs | Andreas asked for comments the guide's owner can review and act on, rather than edits | Direct, 3 comments |
| 2026-10-10 | Style sheet D: the help note's settled wording | [[Meeting Doc Text Review - Style Sheet]] | Section 2 | Direct |
| 2026-10-10 | FAQ typo: "place you with new group" | meetings/shared/Participant FAQ | Small fix | Pending, 1 suggestion |
| 2026-10-10 | Andreas rewrote the sharing line in How today works and fixed the FAQ's buddy answer; the AIRF Meetings 2 to 5 switches accepted | meetings/shared, AIRF Meetings 2 to 5 | Section 2 | Edited and accepted by Andreas |
| 2026-10-10 | AIRF How today works file moved to the trash | meetings/shared/Session Doc - How today works (AI Risk Fundamentals) | Section 2. Nothing includes it any more | Direct. Restorable from the trash for 10 days |
| 2026-10-10 | 3-room How today works brought into line with the new sharing line; two typos in the FAQ's buddy answer ("metting", "your check in with each other you") | meetings/shared | Keep the variants matching; small fixes | Pending, 2 suggestions |
| 2026-10-10 | **Decisions: "Lens Tutor" without "the"; the guide's new Room 4 and wrap-up rules caught in this pass; AIRF Meeting 1's inline How today works set aside** | Plan, style sheet B7 | Section 2 and section 7 | Andreas, 2026-10-10 |
| 2026-10-10 | Andreas split the sharing line into two sentences and dropped "the" before Lens Tutor | meetings/shared/Session Doc - How today works, Participant FAQ | Section 2 | Edited by Andreas |
| 2026-10-10 | The same two edits copied to the 3-room How today works | meetings/shared/Session Doc - How today works (3 rooms) | Keep the variants matching | Pending, 2 suggestions |
| 2026-10-10 | **Decisions: the navigator forms buddy groups in threes; "buddies", plural; navigator-only text goes in the run-sheet; navigator-facing text in scope; AI Futures Meeting 1 likely to get four rooms** | Plan, style sheet B7 | Section 2 | Andreas, 2026-10-10 |
| 2026-10-10 | Buddy setup, part 1 of the buddy wording: the "split into two groups" clause removed from Room 4; the buddy explanation removed from the participants' back-together text and moved, unchanged apart from that clause, into a new "Buddy steps" section of the run-sheet; the run-sheet's "steps in the doc" references now point there | AIRF Meeting 1, CV1 Meeting 1 | Section 2 | Pending, 4 suggestions in AIRF Meeting 1 and 5 in CV1 Meeting 1 (CV1's timeline row also names the step, as AIRF's already did). AI Control 1 Meeting 1 waits for the Room 4 buddy line, since its Room 4 still says "pair up". Validator: no issues |
| 2026-10-10 | Andreas accepted part 1's suggestions and rewrote the buddy section of AIRF Meeting 1's run-sheet, adding the rule for leftover people | meetings/AI Risk Fundamentals/Meeting 1 | Section 2 | Edited by Andreas. Reviewed in chat |
| 2026-10-10 | **Decisions: leftover people in the buddy room make pairs, not a four; the Room 4 buddy line** | Plan | Section 2 | Andreas, 2026-10-10 |
| 2026-10-10 | Room 4 buddy line copied in | AIRF Meeting 1, CV1 Meeting 1, AI Control 1 Meeting 1 | Section 2 | Pending, 3 suggestions. Validator: no issues |
| 2026-10-10 | Andreas added a comma to the Room 4 buddy line ("Before each meeting, check in") and rewrote the run-sheet's buddy section in the third person, with the pairs rule set apart as a separate line for Room 4 only | meetings/AI Risk Fundamentals/Meeting 1 | Andreas's response to the chat review | Edited by Andreas. Claude's suggested Zoom room-count tip dropped: navigators already use automatic assignment |
| 2026-10-10 | The comma copied in | CV1 Meeting 1, AI Control 1 Meeting 1 | Keep the copies identical | Pending, merged into the earlier suggestions |
| 2026-10-10 | **Decision: Room 4's next-unit item has no reading time; a short "what's next" may stay** | Plan | Section 2. Andreas is checking with Elias before part 2 goes ahead | Andreas, 2026-10-10 |

---

## 7. Open items

### Content: needs a decision, not a rewrite

- **AIRF Meeting 5, Room 2. Resolved 2026-10-05:** Andreas rewrote the line to describe the care countries would need and quote the book exactly. The original problem, kept for the record: the doc quoted the authors as saying the cost would be "not even 1% as costly as WWII". That wording is not in the book; it appears only in the book-club design notes. Chapter 13 argues that claiming countries could never do this amounts to claiming they "could not possibly care even 1% as much as they cared to fight World War II". That is about willingness, not cost.
- **AI Futures Meeting 3, Room 3. Resolved 2026-10-05:** Andreas made the table header match the question (contained rather than aligned).
- **AI Futures goes by four names.** The public course page says "Advanced Strategy in AI Safety", the platform's course title is "AI Futures: Forecasting & Strategy", its final survey says "AI Futurism: Forecasting and Strategy", and the meetings folder says "Forecasting, Modeling, and Shaping AI Futures". AIRF Meeting 5 now uses the public name (2026-10-05). For whoever owns the course.
- **AI Futures Meeting 3, Room 2: Kulveit et al.** Some participants in the week of 2026-10-05 found the line an unfair account of the paper (Andreas, 2026-10-10). The paper's mechanism, as the course's own summary of it puts it: the economy, culture and states serve people largely because they depend on human labor and thinking, and that alignment erodes as AI displaces that participation. Flagged on the page for the full pass.
- **The AIRF How today works file. Retired 2026-10-10** (section 2): AIRF Meetings 2 to 5 include the general file and the AIRF file is in the trash. **Set aside:** AIRF Meeting 1's inline copy. It cannot be swapped for the include while Luc's three comments sit on it, the relay will not let Claude remove them, and Andreas is not sure he can either. Andreas is flagging it.
- **The Participant FAQ sends people to the Zoom chat for the doc link. Kept 2026-10-10** (section 2).
- **"Great insights" in How today works. Resolved 2026-10-10:** Andreas rewrote it as "interesting observations" (section 2).
- **The FAQ's buddy answer. Resolved 2026-10-10:** Andreas made it "the first meeting" and "check in with each other".
- **The guide's new Room 4 and wrap-up rules (Elias, 2026-10-10).** Many Room 4 previews and wrap-ups in the four courses summarise the next unit or repeat Room 4. Caught in this pass (section 2).
- **"the Lens Tutor". Resolved 2026-10-10:** Andreas dropped the article in How today works and the FAQ. The FAQ's "Ask the Tutor or Ask for Help" keeps it.
- **The buddy wording, parts 2 to 4** (section 3): the Room 4 next-unit item that carries "send your plan to your buddy", under the guide's new Room 4 rule; the wrap-up reminders to message the buddy, which the new wrap-up rule probably removes; and the FAQ copies (AIRF's inline FAQs, the master template). Navigator-facing singulars go with them: "buddy pairing" in the CV1 and AI Control 1 Meeting 1 run-sheets, and "their Room-4 accountability buddy" in the close of several run-sheets.
- **The run-sheet's buddy section.** Andreas rewrote it in AIRF Meeting 1 as "Accountability Buddy Setup" on 2026-10-10; reviewed in chat the same day. Once settled, it is copied to CV1 Meeting 1 and AI Control 1 Meeting 1, which has no buddy section yet.
- **"New group. Names first" missing from some rooms.** AI Futures Meeting 3, Room 2 is a new group but lacks the line (Andreas, 2026-10-05). Check every meeting for the same gap in the full pass.
- **CV1 Meeting 5, wrap-up.** Describes the capstone as one fixed task, a verification regime for a three-month emergency pause. The Capstone course file describes choosing one brief from a set or proposing your own, and the Compute Verification 2 course page describes ranking the mechanisms by feasibility and designing a regime of your own. The three-month pause appears on that page as a Compute Verification 2 Unit 1 exercise, not as the capstone. Andreas expects this to be settled in a CV1 rewrite (2026-10-04).
- **CV1 Meeting 5, wrap-up.** Says the Unit 1 success-scenario essay is revisited later in the track. The Unit 1 lens says the same, but no other course file or lens mentions the essay, so the revisit may not exist yet. Deferred to the CV1 restructure (Andreas, 2026-10-04).
- **CV1 Meeting 5, Room 2.** 132 words against the guide's 120 limit, mostly because of the bolded summary line from the hardware-authorization lens. Deferred to the CV1 restructure (Andreas, 2026-10-04), so this meeting runs over the limit for now.

### Raised by Luc on AIRF Meeting 1

- Whether pointing participants to the Tutor helps, since it cannot see the session. The help note has them copy the question in, which covers part of this. The How today works help box and the FAQ still say only "Ask the Lens Tutor", without saying to paste the question in.
- "Today's shape" should become "Schedule" or "Agenda", one line per item with its length. "Today's agenda" adopted 2026-10-10. The schedule stays on one line; Andreas's call.
- His three comments on AIRF Meeting 1's inline How today works go when that copy is replaced (section 6). The two points above are what they still raise.

### Style sheet

- **Make it usable by any course.** *Andreas, 2026-10-04.* It is written for these three courses and quotes their docs throughout. Generalize it once it has settled through this work: separate the course-independent entries from the examples, and say how another course would adapt it.

### For the owner of [[AI Guide/Writing Meeting Docs]]

Comments for the guide's owner were left on the guide itself on 2026-10-10 for the first three items below (section 6).

- Rule 6 still requires a "Lens Coach" note, and rule 7 and two examples (Room 2 and 3 patterns) still name Lens Coach and link `/coach`. The replacement is the help note settled on 2026-10-10 (section 2).
- The closing-question example says "two hours ago" for a 90-minute meeting, which AI Futures Meetings 1 and 2 copied.
- The Room 4 example says "pair up (a trio is fine)", against the 2026-10-10 trios decision.
- Several examples carry the habits in section 1, for example "Half-formed is fine; that's what the room is for" and "you'd genuinely like the group to dig into". The "course ends today" closer is now allowed (A2).

### Course names

- CV1's meeting docs are titled "Compute Verification Part 1", but the course is named "Compute Verification 1". [[CV1 Streamlining Proposal]] lists the same drift. Retitled when CV1 gets its own pass (Andreas, 2026-10-10).

### Unverified

- How the meeting-doc renderer handles comments. The course rules say comments are stripped before parsing, but nobody has watched a doc render with them in. It stops mattering for any flag whose passage is rewritten.

### Outside this project

- As of 2026-10-10, AI Safety and Philosophy Meeting 1 still says Lens Coach in its two help notes. AI Control 2, AI Control Fundamentals and Lisbon say Lens Tutor but keep the old help note wording (31 notes). AI Control 1 is now in scope (section 2).
