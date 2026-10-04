---
tags:
  - validator-ignore
---

# Meeting doc text review: log

Review of the participant-facing text in the meeting docs for AI Risk Fundamentals, Forecasting, Modeling, and Shaping AI Futures, and Compute Verification 1. The aim is text that reads as written by a person, not structure or formatting. This file records what changed outside the docs themselves and why.

---

## How the work is split (decided 2026-10-03)

- Claude flags passages as CriticMarkup comments in the doc. A human rewrites them by hand, and Claude reviews the rewrite. Claude does not rewrite voiced text itself.
- Mechanical changes (renames, links) go in as suggestions, not direct edits, so they can be reviewed.
- Flag labels:
    - **AI (strong / mild)**: reads as AI-written. Strong means a participant would likely notice it.
    - **Clarity**: understandable but packed or ambiguous.
    - **Content**: accuracy or structure, not wording.
    - **recurring**: the same phrase appears in other docs, so one replacement can be reused.
    - **Note**: something that already works and should be kept.

## Lens Coach is now Lens Tutor (2026-10-03)

Lens Coach was merged into Lens Tutor. `lensacademy.org/coach` redirects to `lensacademy.org/tutor`. Every mention of "Lens Coach" and every `/coach` link is out of date.

Renamed so far, as pending suggestions:

| File | Status |
|---|---|
| meetings/AI Risk Fundamentals/Meeting 5 | suggested |
| meetings/Forecasting, Modeling, and Shaping AI Futures/Meeting 3 | suggested |
| meetings/Compute Verification 1/Meeting 5 | suggested |
| meetings/shared/Session Doc - How today works | suggested |
| meetings/shared/Session Doc - How today works (3 rooms) | suggested |
| meetings/shared/Session Doc - How today works (AI Risk Fundamentals) | suggested |
| meetings/shared/Participant FAQ | suggested |
| meetings/Master template | suggested |

Still to do: the other meeting docs of the three courses, plus the AI Control and Lisbon docs and the Lisbon shared files if their owners want it. [[AI Guide/Writing Meeting Docs]] still requires a "Lens Coach" note on complex prompts (validation rule 6), so whoever owns that guide should update it.

## Shared files: who else they reach

Edits to these shared files change every doc that includes them, not only the three courses under review. Recorded here because it is easy to forget.

| Shared file | Included by |
|---|---|
| Session Doc - How today works | Compute Verification 1 (all five meetings), AI Futures Meetings 4 and 5, AI Control 1 and 2 (all five meetings each) |
| Session Doc - How today works (3 rooms) | AI Futures Meetings 1 to 3 |
| Session Doc - How today works (AI Risk Fundamentals) | AI Risk Fundamentals Meetings 2 to 5 (Meeting 1 has its own inline copy) |
| Participant FAQ | Compute Verification 1, AI Futures, AI Control 1 and 2 (AI Risk Fundamentals has inline FAQ copies) |

The Lisbon Fellowship docs use their own Lisbon variants of these files and are not affected. As of 2026-10-03 neither AI Control course is live, so changing the shared files was judged fine.

## Flag pass status

| Doc | Runs | Flags | Rewrite | Review |
|---|---|---|---|---|
| AI Risk Fundamentals Meeting 5 | week of 2026-10-05 | done 2026-10-03 | todo | todo |
| AI Futures Meeting 3 | week of 2026-10-05 | done 2026-10-03 | todo | todo |
| Compute Verification 1 Meeting 5 | week of 2026-10-05 | done 2026-10-03 | todo | todo |
| Shared How today works (3 variants), shared Participant FAQ | all of the above | done 2026-10-03 | todo | todo |

## Content issues found while flagging

These are not wording problems and need a decision rather than a rewrite.

- **AI Risk Fundamentals Meeting 5, Room 2.** The doc quotes the authors as saying the cost would be "not even 1% as costly as WWII". That wording is not in the book; it appears only in the book-club design notes. Chapter 13 argues that claiming countries could never do this amounts to claiming they "could not possibly care even 1% as much as they cared to fight World War II", which is about willingness, not cost.
- **AI Futures Meeting 3, Room 3.** The last question reads as either-or (contained rather than aligned) and the table header asks something different (containment before alignment).
- **AI Futures Meeting 3, Room 2.** No "New group. Names first" line. Unclear whether the room is meant to keep the Room 1 group.
- **Compute Verification 1 Meeting 5, wrap-up.** Describes the capstone as one fixed task (a verification regime for a three-month emergency pause). The Capstone course file describes choosing one brief from a bank or proposing your own.
