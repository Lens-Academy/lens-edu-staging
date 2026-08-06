---
tags:
  - validator-ignore
---
# Writing Meeting Docs (AI Guide)

A meeting doc is the Google Doc a cohort group works through during a 90-minute video meeting. Its link lives in a the corresponding course file (see [[Writing Course Files]]). 

## The fixed skeleton

### Session Doc tab
- **Room 1: icebreaker.** Two go-arounds. First, always: how was working through this unit's content, did you finish, what got in the way (keep the "No judgment, 'I didn't finish' is a totally fine answer" line verbatim). Second, unit-specific: a warm-up that pulls the material back to mind and names a feeling ("which moment/curse stuck with you, and in one word, how did it leave you feeling?").
- **Room 2: the question.** The unit's central discussion; see below.
- **Room 3: the flexible slot.** Default: groups compare their Room-2 answers, then dig into a question they craft themselves or borrow from the question bank. Action-plan units replace it: sharing strengths and contribution ideas (unit 4), rehearsing the whole argument in three minutes on mock newcomers (unit 6).
- **Room 4: feedback and next unit.** What is most likely to stop you finishing the next unit's reading, plus your plan against it (sent to the accountability buddy after the meeting), and feedback for the course as a verbal primer for the survey. Final unit instead: the one action you keep doing after the course, with a first concrete step and a date.
- **Wrap-up.** Heads-up on the next unit, and the attendance survey link ("Required for attendance").

Top of the doc: the reading line ("Reading group for <book>. This unit: <chapters>") and a help box (Zoom "Ask for Help" reaches the navigator; confused about content goes to the Lens Coach; logistics go to Discord or the Zoom chat; everything else, the FAQ tab).

Bottom of the doc: the question bank ("Stuck for a Room-3 question? Borrow one of these"), a few questions per chapter of the unit.

## The glossary tab

Terms and definitions for the course, ordered by module so participants can look a term up when they first meet it. Define each term once, at its first appearance, in one or two sentences, in the source's framing. Compile from the course's Learning Outcomes and Lens materials. The master template shows the structure with placeholders.

## Writing the Room 2 question

Never a comprehension check. The pattern in every strong unit is claim, counterargument, stress-test, verdict:

1. State the unit's central claim in one or two sentences.
2. Ask the group to build the strongest surviving objection (or find the weakest link, or the hardest-to-believe step).
3. Stress-test it: "how would the authors answer it with X?", "if that step went differently, does the ending actually change?"
4. Make them write a verdict in the table. Rejecting the material's conclusion is a valid verdict, but it must be defended.

## How to create a meeting doc

1. Make a copy of the master template and fill it out
2. Spawn all validation sub-agents described below with a link to the doc and the exact instruction text
3. If every check passes, you are done. If not, fix the errors and spawn fresh versions of the agents that failed, repeat that cycle, untill every agent passed

## Validation instructions

### Agent 1: Template match
Go through each tab of the master template (https://docs.google.com/document/d/1YDA7MukJk5oeEL8F7zCVwr1lU0X9wuwUDvUXXflvCS4) and check if the discussion doc you are validating is a filled version of it

### Agent 2: Breakout room prompt quality
1. If this is the first meeting of a multi-meeting course: Does the icebreaker contain a light question for people to get to know each other?
2. None of the breakout room prompts are likely to be answered very quickly, and leave participants without something to discuss
3. Every breakout room prompt is open (more than one defensible answer), inviting disagreement or genuine uncertainty, and not settleable by looking something up.
4. There is a clear arc to the meeting (Discussion prompts connect cleanly)
5. At least one prompt clearly requires critical thinking and engagement with questions
6. Complex questions contain a note: "If yo Lens Coach if they don't understand the questions  
