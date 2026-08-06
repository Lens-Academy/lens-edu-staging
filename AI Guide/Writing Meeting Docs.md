---
tags:
  - validator-ignore
---
# Writing Meeting Docs (AI Guide)

A meeting doc is the Google Doc a cohort group works through during a 90-minute video meeting. Its link lives in the corresponding course file (see [[Writing Course Files]]).

## How to create a meeting doc

1. Make a copy of the master template (https://docs.google.com/document/d/1YDA7MukJk5oeEL8F7zCVwr1lU0X9wuwUDvUXXflvCS4) and fill it out. Room roles: Room 1 is an icebreaker; Rooms 2 and 3 are the main work (discussing the unit's content, working on {--{"author":"Elias's AI","timestamp":1786019303657}@@mock newcomers). The final unit's--}{++{"author":"Elias's AI","timestamp":1786019303657}@@action plans, or practicing something);++} Room 4{--{"author":"Elias's AI","timestamp":1786019303657}@@ asks for the one action participants keep doing after--}{++{"author":"Elias's AI","timestamp":1786019303657}@@ is a reflective close;++} the {--{"author":"Elias's AI","timestamp":1786019303657}@@course, with a first concrete step and a date, instead of next-unit planning.--}{++{"author":"Elias's AI","timestamp":1786019303657}@@wrap-up hands people off with what they need next.++}
2. Spawn all validation sub-agents described below with a link to the doc and the exact instruction text
3. If every check passes, you are done. If not, fix the errors and spawn fresh versions of the agents that failed, repeat that cycle, until every agent passed

## Validation instructions

### Agent 1: Template match
Go through each tab of the master template (https://docs.google.com/document/d/1YDA7MukJk5oeEL8F7zCVwr1lU0X9wuwUDvUXXflvCS4) and check if the discussion doc you are validating is a filled version of it:
1. Every [bracketed placeholder] is filled; none left over.
2. The fixed parts (room structure, timings, the room loop, help box, FAQ, run-sheet instructions) are {--{"author":"Elias's AI","timestamp":1786019303657}@@kept verbatim; --}{++{"author":"Elias's AI","timestamp":1786019303657}@@kept; ++}only the participant-facing slots differ.
3. The glossary is filled: ordered by module, each term defined once at its first appearance, in one or two sentences, in the source's framing.

### Agent 2:{--{"author":"Elias's AI","timestamp":1786019303657}@@ Breakout room prompt--}{++{"author":"Elias's AI","timestamp":1786019303657}@@ Room++} quality
{--{"author":"Elias's AI","timestamp":1786019303657}@@1. If this is the first meeting--}{++{"author":"Elias's AI","timestamp":1786019303657}@@Judge each room against its role. Patterns are examples++} of {--{"author":"Elias's AI","timestamp":1786019303657}@@a multi-meeting course: Does the icebreaker contain a light question for people to get to know each other?
2. None of the breakout room prompts are likely to be answered very quickly,--}{++{"author":"Elias's AI","timestamp":1786019303657}@@what works, not requirements; a room passes if it serves its role well, whatever shape it takes.

1. **Room 1 is a good icebreaker**: light, everyone can answer without preparation, no wrong answers,++} and {--{"author":"Elias's AI","timestamp":1786019303657}@@leave participants without something--}{++{"author":"Elias's AI","timestamp":1786019303657}@@it warms people up++} to {--{"author":"Elias's AI","timestamp":1786019303657}@@discuss
3. Every breakout room prompt--}{++{"author":"Elias's AI","timestamp":1786019303657}@@each other and toward the material. If this++} is {--{"author":"Elias's AI","timestamp":1786019303657}@@open (more than one defensible answer), inviting disagreement or genuine uncertainty, and not settleable by looking something up.
4. No prompt is a comprehension check, and no prompt teaches its own answer--}{++{"author":"Elias's AI","timestamp":1786019303657}@@the first meeting of a multi-meeting course, it must include a get-to-know-each-other question. Example patterns:
	- How did working through the unit's content go, did you finish, what got in the way (with an explicit no-judgment note)
	- Which moment or idea stuck with you, and++} in {--{"author":"Elias's AI","timestamp":1786019303657}@@its setup text.
5. There is a clear arc --}{++{"author":"Elias's AI","timestamp":1786019303657}@@one word, how did it leave you feeling?
	- A playful hypothetical tied ++}to the {--{"author":"Elias's AI","timestamp":1786019303657}@@meeting (discussion prompts connect cleanly), and every room's output can be retold in a sentence or two when the next room opens.
6. Each prompt is doable by 3 to 4 strangers within the room's time slot, without preparation beyond the unit's content.
7. Prompts for room --}{++{"author":"Elias's AI","timestamp":1786019303657}@@unit's theme ("an oracle says X happens in 6 months: what does your group do with the time?")
	- Get-to-know: what brings you here; when did you first take the topic seriously and what changed your mind; something you have been enjoying lately, unrelated to the topic
2. **Rooms ++}2 and 3 {--{"author":"Elias's AI","timestamp":1786019303657}@@will --}lead to {--{"author":"Elias's AI","timestamp":1786019303657}@@a strong --}{++{"author":"Elias's AI","timestamp":1786019303657}@@high-quality, engaging work on this unit**: a ++}discussion of {--{"author":"Elias's AI","timestamp":1786019303657}@@this unit's content.--}{++{"author":"Elias's AI","timestamp":1786019303657}@@the content, action-plan work, or practice.++} Example patterns:
	- Prompt makes a claim and asks participants to find and discuss arguments for/against it and to what extent they agree/disagree{--{"author":"Elias's AI","timestamp":1786019303657}@@
	- Prompt asks participants to collect questions they have from this unit's readings--}
	- Strongest surviving objection: {--{"author":"Elias's AI","timestamp":1786019303657}@@after a cumulative argument, --}build the best objection the material has not killed, answer it the way the authors would, and write a verdict on whether it survives
	- For narrative or scenario units: which step of the story is hardest to believe, and does the ending survive if that step went differently?
	- For proposals or asks: gut reaction first, then find the weakest link; a group that rejects the proposal must defend an alternative
	- Stage the text's own disagreement: present two positions from the reading, ask who is right, and what that predicts for a nearby case
	- Transfer: apply the unit's central mechanism to a case the text never mentions; does it still hold?{++{"author":"Elias's AI","timestamp":1786019303657}@@
	- Collect questions participants have from the unit's reading, vote, and dig into the top-voted ones
	- Practice: one participant makes the unit's (or course's) whole argument in a few minutes to the others, who play newcomers or skeptics and ask honest questions; swap roles
	- Practice: rehearse a real upcoming conversation or decision; the group coaches
	- Action plan: share strengths and candidate ways to contribute; the group reflects back a strength you undersold and adds one more idea
3. **Room 4 is reflective.** Recommended shape: feedback for the meeting and course, plus each person's intention until the next meeting (or after the course, in the final unit). Other reflective closes pass too if they let people digest the session; do not fail a doc just for deviating from the recommended shape.
4. **The wrap-up hands people off well.** At least one of:
	- The information participants need after this meeting, as a short list of links, calls to action, or reminders, with a note that the navigator talks through them (mirrored in the run-sheet as an after-this-meeting section)
	- An open closing question to the whole group that people can answer voluntarily ("what is your biggest takeaway from today?") for a cohesive ending
	Both together are fine when the information list is short.++}
{--{"author":"Elias's AI","timestamp":1786019303657}@@8. --}{++{"author":"Elias's AI","timestamp":1786019303657}@@5. General, for every room: prompts are open (more than one defensible answer), not exhausted in a minute, never a comprehension check, never teach their own answer in the setup text, doable by 3 to 4 strangers in the time slot, and the meeting has an arc: each room's output can be retold in a sentence or two when the next room opens.
6. ++}Complex questions contain a note: "Not sure what the question is asking? Copy it into Lens Coach, and ask for an explanation."

### Agent 3: Content fidelity
Read the unit's actual content (the module with its lenses, learning outcomes, and readings) and check the doc against it:
1. The reading line names exactly this unit's assigned content, nothing more or less.
2. Every claim the doc attributes to the source is actually made there; prompts never strawman the material.
3. Question-bank entries point at real claims, scenes, or moments in the text.
4. {--{"author":"Elias's AI","timestamp":1786019303657}@@Room 1's warm-up and Room 2's question--}{++{"author":"Elias's AI","timestamp":1786019303657}@@The main rooms++} target the unit's central content (what its learning outcomes care about), not a side detail.

### Agent 4: Logistics and links
1. The doc title names the right course and unit, and the [Group] placeholder is still unfilled (navigators fill it per copy).
2. The attendance link points at this unit's form, not a previous unit's (the classic copy-paste failure).
3. The course file's `# Meeting:` marker for this unit carries a `meeting-doc-template::` line with this doc's link.
4. The run-sheet's next-unit heads-up matches the next unit's actual reading; in the final unit it says there is none.
