---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# Meeting doc text review: style sheet

Companion to [[Meeting Doc Text Review Log]]. The log holds decisions and history. This file holds the standard: Andreas rewrites against it, and Claude flags and reviews against it. Every flag should point at an entry here, so that it can be checked and overruled rather than taken on trust.

It lists what makes a prompt read as AI-written and the move to make for each. It does not try to say what a good prompt sounds like. Voice does not reduce to rules, and only the person writing can supply it, which is the same conclusion [[AI Guide/Course Making Findings]] reaches in section 3.

**Working draft, accepted as a starting point by Andreas on 2026-10-04.** It is written for the AIRF, AI Futures and CV1 meeting docs and quotes them throughout. The aim is for any course to be able to pick it up and adapt it for its own meetings; that cleanup waits until the sheet has settled through this work (open item in the log).

Sources, so each entry can be traced:

- **Guide**: [[AI Guide/Writing Meeting Docs]], validation rules 0 and 4 to 8, and [[AI Guide/Course Authoring]].
- **Findings**: [[AI Guide/Course Making Findings]], section 3.
- **Andreas**: [[AIRF Restructure - Working Preferences]], under "How to write learner-facing text".
- **Luc**: the problem labels from his 2026-09-26 rewrite of the AI Futures course pages, and his comments on AIRF Meeting 1.
- **Survey**: what Claude found in the fifteen docs on 2026-10-03.

Examples are quoted from the current docs. Each "instead" names the move to make, not the words to write.

---

## A. Habits that can read as AI-written

**A1. Verdict lines and slogans.** Short lines that pass judgment or round something off. "Time to own it." "Disagree about the bin? Good. That disagreement is the discussion." "If nobody has anything, that is a finding too." *Instead:* cut, or replace with the plain instruction the line stands in for. *Sources:* Luc, survey.

**A2. "X, not Y" and its relatives.** "The point is the discussion, not a tidy answer." "We want the honest answer, not the kind one." The shared closer, "the course ends today, but your action plan doesn't". *Instead:* say X. Keep a contrast only when Y is something a participant would otherwise do or believe. In Luc's rewrite, applying this bluntly also stripped contrasts that carried meaning, so it calls for judgment, not deletion on sight. The form is not banned: CV1 Meeting 5 keeps "Part 1 ends today, but your action plan doesn't have to." (Andreas, 2026-10-04). *Sources:* Luc, survey.

**A3. Reassurance, and telling people how to feel.** "No judgment, 'I didn't finish' is a totally fine answer." "Take two minutes; the group will wait." "Hope, unease, irritation and relief are all answers." *Instead:* cut. Where the permission matters, let the question carry it ("Did you finish? If not, what got in the way?"). Where the worry is that people will hold back a thin answer, give a quantity cue ("one sentence each"). *Sources:* Andreas (no reassurance clauses), Findings rule 3.

**A4. Explaining why the exercise matters.** "You're each other's rehearsal audience for every future conversation about this." "Your answer reaches the people building this course, and they do change it." *Instead:* cut. If the group needs the reason to do the task, give it as information in one plain sentence. *Sources:* Findings rule 3, survey.

**A5. Aphorisms and unexplained metaphors.** "The institutions that served us because they needed us stop needing us." "Load-bearing part, weakest weld." "The fourteen-month conclusion still wasn't licensed." *Instead:* say the plain point. A metaphor can stay if the same block says what it means. *Sources:* Course Authoring ("No mannered prose": when a literal phrase is available, use it), Findings (every metaphor explained in its own block), Luc (vague sentences, reading level), survey.

**A6. Mirrored pairs and runs of fragments.** "One says the hard part is inside the system... The other says the hard part is between systems..." "Nobody plans it, no accident, ordinary systems doing what they were told." Bracketed runs of question fragments: "(nations won't sign? enforcement fails? we'd need a warning shot first?)". *Instead:* ordinary sentences, or a bulleted list if it really is a list (the guide's skimmable rule). *Source:* survey.

**A7. Summing-up flourishes.** "That's the course: five units from 'intelligence is power' to 'where there's life, there's hope'." "The community doesn't end here." "Your model, your signposts, and your next step leave the room with you." *Instead:* cut, or replace with the information the wrap-up has to hand over (guide rule 4). *Source:* survey.

**A8. Menus of feelings.** "Hopeful, alarmed, motivated, numb, something else?" *Instead:* ask the question and let people answer it. *Source:* survey.

**A9. Clipped, telegraphic instructions.** "Go around your group. Two things, in this order, and finish the first before anyone starts the second." "Your scribe notes conversation statuses and reactions." *Instead:* say it the way a navigator would say it out loud. Fixed template lines change in the master template, not doc by doc (C5). *Source:* survey.

**A10. Words that mark text as AI-written.** "Genuinely", "quietly", "dig into", "stress-test", "own it", "shape" as in "Today's shape", "honest" as filler ("ask honest questions"), and "land" used about a person or a line ("something landed on you", "lands a line worth remembering"). *Instead:* the plain word, or nothing. Add a word here only when it turns up in our docs. *Sources:* Luc (AI-flavored words, and "shape" on AIRF Meeting 1), survey.

---

## B. Clarity

The guide already requires most of these. They are repeated here so a flag can cite one place.

**B1. One question per numbered item, at most four per room.** Lettered sub-steps count as asks. Optional asks go last, marked "If you still have time:". *Guide rule 7.*

Follow-ups that sort people by their situation can share an item, because they leave room for different answers rather than adding work: "Did you finish, and if not, what stopped you?", "If nothing changed, what evidence would move the needle for you?". Flag an item for packing several separate asks, not for carrying follow-ups like these. *Andreas, 2026-10-04.*

**B2. At most 120 words per room prompt.** Bulleted example lists do not count. *Guide rule 0.*

**B3. Self-contained.** Every term of art is defined in the prompt in plain words, or dropped. No course-internal labels a participant cannot resolve ("the cost card", "your hundred points", "the wedge"). *Guide rule 7. Andreas: never label something the learner cannot resolve.*

**B4. Exercise reminders.** A prompt never depends on optional written work, though it may invite it. When a prompt builds on something participants did alone in the unit, it says in one line what that was, and gives people who skipped it something to say. AI Futures Meeting 3, Room 1 is the model. *Guide rule 7 for the first sentence. The reminder form is Claude's proposal, not yet confirmed.*

**B5. No either-or unless the two options really are the only ones.** "More or less hopeful" leaves out "about the same". *Findings rule 5.*

**B6. Table headers match the prompt above them.** *Survey.*

**B7. One term for one thing, in every doc.** "Lens Tutor". "Unit" and "next meeting", never "week". "Tractable", not "gettable". "Accountability buddy", never "partner". *Guide rule 7, the 2026-10-03 rename, Andreas's 2026-10-04 decision on "buddy".*

---

## C. Leave alone

**C1. Text that passes.** If nothing above applies, the text stays, even where Claude would have phrased it differently. Some lines already read as a person wrote them: "Go around, and everyone answers before anyone argues." "(Don't remember it? Vote on what you would accept today.)"

**C2. What the group is asked to do, and in what order.** Changing an ask is a content change. Flag it as Content rather than rewriting it.

**C3. Claims and numbers.** Reword freely, but any sentence that attributes something to a reading is checked against the source afterwards. *Guide rule 8.*

**C4. Course vocabulary.** A defined term of art stays (B3). Plainer does not mean simpler ideas.

**C5. Fixed template parts.** Change them in [[meetings/Master template]] and the shared blocks, so every doc changes together.

---

## D. Rules for any rewrite

- **No em dashes.** *Course Authoring.*
- **Keep a Tutor help note on complex prompts.** The guide requires a note "like" its wording, so the wording can change. Whatever replaces it, use it in every doc. *Guide rule 6.*
- **Read it aloud as the navigator would say it to the group.** If you would not say it, change it.

---

## How flags cite this sheet

The flags filed on 2026-10-03 came before this sheet and use the labels listed in the log (AI strong or mild, Clarity, Content, recurring, Note). Flags filed from now on name an entry, such as "A2" or "B4". Changes to this sheet are recorded in the log.
