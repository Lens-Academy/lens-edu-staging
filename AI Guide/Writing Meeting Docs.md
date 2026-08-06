---
tags:
  - validator-ignore
---
# Writing Meeting Docs (AI Guide)

A meeting doc is the Google Doc a cohort group works through during a 90-minute video meeting. Its link lives in the corresponding course file (see [[Writing Course Files]]).

## How to create a meeting doc

1. Make a copy of the master template (https://docs.google.com/document/d/1YDA7MukJk5oeEL8F7zCVwr1lU0X9wuwUDvUXXflvCS4) and fill it out.
	- Unit variants: action-plan units replace Room 3's default with action-plan work (sharing strengths and contribution ideas; rehearsing the course's whole argument on mock newcomers). The final unit's Room 4 asks for the one action participants keep doing after the course, with a first concrete step and a date, instead of next-unit planning.
2. Spawn all validation sub-agents described below with a link to the doc and the exact instruction text
3. If every check passes, you are done. If not, fix the errors and spawn fresh versions of the agents that failed, repeat that cycle, until every agent passed

## Validation instructions

### Agent 1: Template match
Go through each tab of the master template (https://docs.google.com/document/d/1YDA7MukJk5oeEL8F7zCVwr1lU0X9wuwUDvUXXflvCS4) and check if the discussion doc you are validating is a filled version of it:
1. Every [bracketed placeholder] is filled; none left over.
2. The fixed parts (room structure, timings, the room loop, help box, FAQ, run-sheet instructions) are kept verbatim; only the participant-facing slots differ.
3. The glossary is filled: ordered by module, each term defined once at its first appearance, in one or two sentences, in the source's framing.

### Agent 2: Breakout room prompt quality
1. If this is the first meeting of a multi-meeting course: Does the icebreaker contain a light question for people to get to know each other?
2. None of the breakout room prompts are likely to be answered very quickly, and leave participants without something to discuss
3. Every breakout room prompt is open (more than one defensible answer), inviting disagreement or genuine uncertainty, and not settleable by looking something up.
4. No prompt is a comprehension check, and no prompt teaches its own answer in its setup text.
5. There is a clear arc to the meeting (discussion prompts connect cleanly), and every room's output can be retold in a sentence or two when the next room opens.
6. Each prompt is doable by 3 to 4 strangers within the room's time slot, without preparation beyond the unit's content.
7. Prompts for room 2 and 3 will lead to a strong discussion of this unit's content. Example patterns:
	- Prompt makes a claim and asks participants to find and discuss arguments for/against it and to what extent they agree/disagree
	- Prompt asks participants to collect questions they have from this unit's readings
	- Strongest surviving objection: after a cumulative argument, build the best objection the material has not killed, answer it the way the authors would, and write a verdict on whether it survives
	- For narrative or scenario units: which step of the story is hardest to believe, and does the ending survive if that step went differently?
	- For proposals or asks: gut reaction first, then find the weakest link; a group that rejects the proposal must defend an alternative
	- Stage the text's own disagreement: present two positions from the reading, ask who is right, and what that predicts for a nearby case
	- Transfer: apply the unit's central mechanism to a case the text never mentions; does it still hold?
8. Complex questions contain a note: "Not sure what the question is asking? Copy it into Lens Coach, and ask for an explanation."

### Agent 3: Content fidelity
Read the unit's actual content (the module with its lenses, learning outcomes, and readings) and check the doc against it:
1. The reading line names exactly this unit's assigned content, nothing more or less.
2. Every claim the doc attributes to the source is actually made there; prompts never strawman the material.
3. Question-bank entries point at real claims, scenes, or moments in the text.
4. Room 1's warm-up and Room 2's question target the unit's central content (what its learning outcomes care about), not a side detail.

### Agent 4: Logistics and links
1. The doc title names the right course and unit, and the [Group] placeholder is still unfilled (navigators fill it per copy).
2. The attendance link points at this unit's form, not a previous unit's (the classic copy-paste failure).
3. The course file's `# Meeting:` marker for this unit carries a `meeting-doc-template::` line with this doc's link.
4. The run-sheet's next-unit heads-up matches the next unit's actual reading; in the final unit it says there is none.
