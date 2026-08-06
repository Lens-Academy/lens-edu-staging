---
tags:
  - validator-ignore
---
# Writing Meeting Docs (AI Guide)

A meeting doc is the Google Doc a cohort group works through during a 90-minute video meeting. Its link lives in the corresponding course file (see [[Writing Course Files]]).

## How to create a meeting doc

1. Make a copy of the master template (https://docs.google.com/document/d/1YDA7MukJk5oeEL8F7zCVwr1lU0X9wuwUDvUXXflvCS4) and fill it out. Room roles: Room 1 is an icebreaker; Rooms 2 and 3 are the main work (discussing the unit's content, working on action plans, or practicing something); Room 4 is a reflective close; the wrap-up hands people off with what they need next.
2. Spawn all validation sub-agents described below with a link to the doc and the exact instruction text
3. If every check passes, you are done. If not, fix the errors and spawn fresh versions of the agents that failed, repeat that cycle, until every agent passed

## Validation instructions

### Agent 1: Template match
Go through each tab of the master template (https://docs.google.com/document/d/1YDA7MukJk5oeEL8F7zCVwr1lU0X9wuwUDvUXXflvCS4) and check if the discussion doc you are validating is a filled version of it:
1. Every [bracketed placeholder] is filled; none left over.
2. The fixed parts (room structure, timings, the room loop, help box, FAQ, run-sheet instructions) are kept; only the participant-facing slots differ.
3. The glossary is filled: ordered by module, each term defined once at its first appearance, in one or two sentences, in the source's framing.

### Agent 2: Room quality
Judge each room against its role. {--{"author":"Elias's AI","timestamp":1786019617574}@@Patterns--}{++{"author":"Elias's AI","timestamp":1786019617574}@@The examples below++} are {--{"author":"Elias's AI","timestamp":1786019617574}@@examples of what works, --}{++{"author":"Elias's AI","timestamp":1786019617574}@@real prompts from past unit docs: they show the quality bar, ++}not {--{"author":"Elias's AI","timestamp":1786019617574}@@requirements; a--}{++{"author":"Elias's AI","timestamp":1786019617574}@@required shapes. A++} room passes if it serves its role well, whatever shape it takes.

1. **Room 1 is a good icebreaker**: light, everyone can answer without preparation, no wrong answers, and it warms people up to each other and toward the material. If this is the first meeting of a multi-meeting course, it must include a get-to-know-each-other question. {--{"author":"Elias's AI","timestamp":1786019617574}@@Example patterns:
	- --}{++{"author":"Elias's AI","timestamp":1786019617574}@@Real examples:

```
++}How {--{"author":"Elias's AI","timestamp":1786019617574}@@did--}{++{"author":"Elias's AI","timestamp":1786019617574}@@was++} working through {--{"author":"Elias's AI","timestamp":1786019617574}@@the--}{++{"author":"Elias's AI","timestamp":1786019617574}@@this++} unit's {--{"author":"Elias's AI","timestamp":1786019617574}@@content go,--}{++{"author":"Elias's AI","timestamp":1786019617574}@@content? Answer any of:++} did you {++{"author":"Elias's AI","timestamp":1786019617574}@@finish? More or less enjoyable than the last unit? Harder or easier? If you didn't ++}finish, what got in the {--{"author":"Elias's AI","timestamp":1786019617574}@@way (with an explicit no-judgment note)
	- --}{++{"author":"Elias's AI","timestamp":1786019617574}@@way? (No judgment, "I didn't finish" is a totally fine answer.)
```

```
++}Which moment {--{"author":"Elias's AI","timestamp":1786019617574}@@or idea stuck--}{++{"author":"Elias's AI","timestamp":1786019617574}@@stuck? One scene from the story that stayed++} with {--{"author":"Elias's AI","timestamp":1786019617574}@@you, and--}{++{"author":"Elias's AI","timestamp":1786019617574}@@you after you closed the book, the one you'd retell to a friend. And++} in one word, how did it leave you {--{"author":"Elias's AI","timestamp":1786019617574}@@feeling?
	- A playful hypothetical tied to the unit's theme ("an oracle says X happens --}{++{"author":"Elias's AI","timestamp":1786019617574}@@feeling: alarmed, skeptical, numb, motivated, something else?
```

```
If an oracle told your group a misaligned superintelligence would end the world ++}in 6 months: what {--{"author":"Elias's AI","timestamp":1786019617574}@@does your group--}{++{"author":"Elias's AI","timestamp":1786019617574}@@would you all++} do with the {--{"author":"Elias's AI","timestamp":1786019617574}@@time?")
	- Get-to-know: what brings--}{++{"author":"Elias's AI","timestamp":1786019617574}@@time? Land on one plan++} you {--{"author":"Elias's AI","timestamp":1786019617574}@@here; when did you first take the topic seriously and what changed your mind; something you have been enjoying lately, --}{++{"author":"Elias's AI","timestamp":1786019617574}@@all agree on, ideally a mash-up of everyone's ideas. It's an icebreaker, so wacky / not-cohesive / not-serious is totally fine.
```

```
What's something, completely ++}unrelated to {--{"author":"Elias's AI","timestamp":1786019617574}@@the topic--}{++{"author":"Elias's AI","timestamp":1786019617574}@@AI, that you've been enjoying lately?++}
{++{"author":"Elias's AI","timestamp":1786019617574}@@```

++}2. **Rooms 2 and 3 lead to high-quality, engaging work on this unit**: a discussion of the content, action-plan work, or practice. {--{"author":"Elias's AI","timestamp":1786019617574}@@Example patterns:
	- Prompt makes a --}{++{"author":"Elias's AI","timestamp":1786019617574}@@Real examples:

Claim, strongest counterargument, stress-test, verdict:
```
Is it really alchemy? The book's ++}claim {--{"author":"Elias's AI","timestamp":1786019617574}@@and asks participants to find--}{++{"author":"Elias's AI","timestamp":1786019617574}@@this unit: humanity gets one shot at aligning superintelligence,++} and {--{"author":"Elias's AI","timestamp":1786019617574}@@discuss arguments for/against--}{++{"author":"Elias's AI","timestamp":1786019617574}@@the field trying to solve++} it {--{"author":"Elias's AI","timestamp":1786019617574}@@and to what extent they agree/disagree
	- Strongest surviving objection:--}{++{"author":"Elias's AI","timestamp":1786019617574}@@is still doing alchemy, not science. As a group,++} build the {++{"author":"Elias's AI","timestamp":1786019617574}@@strongest counterargument you can: "we can practice on weaker AIs first", "AI will help us align AI", "interpretability is maturing", or your own. Pick your ++}best {--{"author":"Elias's AI","timestamp":1786019617574}@@objection the material has not killed,--}{++{"author":"Elias's AI","timestamp":1786019617574}@@one and stress-test it: how would the authors++} answer it {++{"author":"Elias's AI","timestamp":1786019617574}@@with ++}the {--{"author":"Elias's AI","timestamp":1786019617574}@@way --}{++{"author":"Elias's AI","timestamp":1786019617574}@@five curses? Write your verdict: does your counterargument survive?
```

For narrative or scenario units, find ++}the {++{"author":"Elias's AI","timestamp":1786019617574}@@weakest step:
```
Did the story do its job? The ++}authors {--{"author":"Elias's AI","timestamp":1786019617574}@@would, and write a verdict on whether it survives
	- For narrative--}{++{"author":"Elias's AI","timestamp":1786019617574}@@are explicit: the pathway is illustrative, only the outcome is predicted. Go around: did the story make the risk feel more real,++} or {--{"author":"Elias's AI","timestamp":1786019617574}@@scenario units: which--}{++{"author":"Elias's AI","timestamp":1786019617574}@@did the specifics hand you new objections? Then find the++} step {--{"author":"Elias's AI","timestamp":1786019617574}@@of--}{++{"author":"Elias's AI","timestamp":1786019617574}@@in++} the {--{"author":"Elias's AI","timestamp":1786019617574}@@story is --}{++{"author":"Elias's AI","timestamp":1786019617574}@@story's path you find ++}hardest to believe, and {++{"author":"Elias's AI","timestamp":1786019617574}@@test it: if that step went differently, ++}does the ending {--{"author":"Elias's AI","timestamp":1786019617574}@@survive if that step went differently?
	- --}{++{"author":"Elias's AI","timestamp":1786019617574}@@actually change, or does the story route around it?
```

++}For proposals or {--{"author":"Elias's AI","timestamp":1786019617574}@@asks: gut reaction first, then find the weakest link;--}{++{"author":"Elias's AI","timestamp":1786019617574}@@asks, reject-means-defend-an-alternative:
```
Would you sign it? The book ends with++} a {--{"author":"Elias's AI","timestamp":1786019617574}@@group that rejects the proposal must defend--}{++{"author":"Elias's AI","timestamp":1786019617574}@@concrete ask: a worldwide halt on frontier AI development, enforced by GPU monitoring and++} an {--{"author":"Elias's AI","timestamp":1786019617574}@@alternative
	- Stage the text's own disagreement: present two positions from --}{++{"author":"Elias's AI","timestamp":1786019617574}@@international treaty. Go around, gut reaction: realistic, necessary, both, neither? Then find ++}the {--{"author":"Elias's AI","timestamp":1786019617574}@@reading, ask who is right,--}{++{"author":"Elias's AI","timestamp":1786019617574}@@weakest link in the plan++} and {++{"author":"Elias's AI","timestamp":1786019617574}@@stress-test it. And if your group rejects the halt, ++}what {--{"author":"Elias's AI","timestamp":1786019617574}@@that predicts for --}{++{"author":"Elias's AI","timestamp":1786019617574}@@do you endorse instead? Anything can be ++}a {--{"author":"Elias's AI","timestamp":1786019617574}@@nearby case
	- Transfer: apply the unit's central mechanism--}{++{"author":"Elias's AI","timestamp":1786019617574}@@valid answer (even keep going), but you have++} to {--{"author":"Elias's AI","timestamp":1786019617574}@@a case--}{++{"author":"Elias's AI","timestamp":1786019617574}@@defend it.
```

Stage++} the {--{"author":"Elias's AI","timestamp":1786019617574}@@text never mentions; does it still hold?
	- Collect questions participants have from the unit's reading, vote,--}{++{"author":"Elias's AI","timestamp":1786019617574}@@text's own disagreement:
```
Klurl vs Trapaucius. Trapaucius argues that any being smart enough will grasp its "purpose" and pursue only that. Klurl replies: "they'd know, but would they care?" Who's right about humans,++} and {--{"author":"Elias's AI","timestamp":1786019617574}@@dig into the top-voted ones
	- Practice: --}{++{"author":"Elias's AI","timestamp":1786019617574}@@what does that predict for AI?
```

Practice (argue to a newcomer):
```
The three-minute version: ++}one {--{"author":"Elias's AI","timestamp":1786019617574}@@participant--}{++{"author":"Elias's AI","timestamp":1786019617574}@@of you++} makes the {--{"author":"Elias's AI","timestamp":1786019617574}@@unit's (or course's) --}{++{"author":"Elias's AI","timestamp":1786019617574}@@book's ++}whole argument in {--{"author":"Elias's AI","timestamp":1786019617574}@@a few--}{++{"author":"Elias's AI","timestamp":1786019617574}@@about 3++} minutes to the others, who play {--{"author":"Elias's AI","timestamp":1786019617574}@@newcomers or skeptics --}{++{"author":"Elias's AI","timestamp":1786019617574}@@people who have never heard of it ++}and ask honest {--{"author":"Elias's AI","timestamp":1786019617574}@@questions; swap roles
	- Practice: rehearse--}{++{"author":"Elias's AI","timestamp":1786019617574}@@questions. When someone's version skips++} a {--{"author":"Elias's AI","timestamp":1786019617574}@@real upcoming --}{++{"author":"Elias's AI","timestamp":1786019617574}@@step, or lands a line worth remembering, say it! You're each other's rehearsal audience for every future ++}conversation {++{"author":"Elias's AI","timestamp":1786019617574}@@about this. Swap roles if someone else wants to try.
```

Action-plan work:
```
1. Share 2 ++}or {--{"author":"Elias's AI","timestamp":1786019617574}@@decision; the group coaches
	- Action plan: share strengths and candidate ways--}{++{"author":"Elias's AI","timestamp":1786019617574}@@3 of your strengths. What do people come to you for? What feels easy++} to {--{"author":"Elias's AI","timestamp":1786019617574}@@contribute; --}{++{"author":"Elias's AI","timestamp":1786019617574}@@you that seems hard for others?
2. Share one candidate way you could contribute: with your career, skills, field, network, voice, or money. Half-formed is fine; that's what ++}the {++{"author":"Elias's AI","timestamp":1786019617574}@@room is for.
3. The ++}group {--{"author":"Elias's AI","timestamp":1786019617574}@@reflects--}{++{"author":"Elias's AI","timestamp":1786019617574}@@responds: reflect++} back a strength {--{"author":"Elias's AI","timestamp":1786019617574}@@you undersold--}{++{"author":"Elias's AI","timestamp":1786019617574}@@they undersold,++} and {--{"author":"Elias's AI","timestamp":1786019617574}@@adds--}{++{"author":"Elias's AI","timestamp":1786019617574}@@suggest++} one more {--{"author":"Elias's AI","timestamp":1786019617574}@@idea--}{++{"author":"Elias's AI","timestamp":1786019617574}@@way someone with these strengths could plug in.++}
{++{"author":"Elias's AI","timestamp":1786019617574}@@```

Collect and vote:
```
Write one or two discussion questions you'd genuinely like the group to dig into. Vote: you have 5 votes, put a + next to the questions you most want to discuss. We'll take the top-voted questions, hear from whoever wrote them, and discuss.
```

++}3. **Room 4 is reflective.** Recommended {--{"author":"Elias's AI","timestamp":1786019617574}@@shape: feedback--}{++{"author":"Elias's AI","timestamp":1786019617574}@@shape (do not fail a doc++} for {++{"author":"Elias's AI","timestamp":1786019617574}@@a different reflective close), ++}the {--{"author":"Elias's AI","timestamp":1786019617574}@@meeting and course, plus each person's intention until --}{++{"author":"Elias's AI","timestamp":1786019617574}@@real prompt:

```
1. Next unit: what's most likely to stop you finishing ++}the next {--{"author":"Elias's AI","timestamp":1786019617574}@@meeting (or after--}{++{"author":"Elias's AI","timestamp":1786019617574}@@unit's reading, and what's your plan to beat it? (After++} the {--{"author":"Elias's AI","timestamp":1786019617574}@@course,--}{++{"author":"Elias's AI","timestamp":1786019617574}@@meeting, send this plan to your accountability buddy; they'll check++} in {++{"author":"Elias's AI","timestamp":1786019617574}@@with you before ++}the {--{"author":"Elias's AI","timestamp":1786019617574}@@final unit). Other reflective closes pass too if they let people digest--}{++{"author":"Elias's AI","timestamp":1786019617574}@@next meeting.)
2. Feedback: what would make the course and this meeting better?
```

Final unit variant:
```
Your ongoing action:++} the {--{"author":"Elias's AI","timestamp":1786019617574}@@session; do not fail a doc just for deviating from --}{++{"author":"Elias's AI","timestamp":1786019617574}@@course ends today but your action plan doesn't! Share the one action you choose to keep doing after this course (have conversations, write representatives, refer someone, aim your skills at ++}the {--{"author":"Elias's AI","timestamp":1786019617574}@@recommended shape.--}{++{"author":"Elias's AI","timestamp":1786019617574}@@problem), and its first concrete step with a date.++}
{++{"author":"Elias's AI","timestamp":1786019617574}@@```

++}4. **The wrap-up hands people off well.** At least one of:
	- The information participants need after this meeting, as a short list of links, calls to action, or reminders, with a note that the navigator talks through them (mirrored in the run-sheet as an after-this-meeting section)
	- An open closing question to the whole group that people can answer {--{"author":"Elias's AI","timestamp":1786019617574}@@voluntarily ("what is your biggest takeaway from today?") for a cohesive ending--}{++{"author":"Elias's AI","timestamp":1786019617574}@@voluntarily, for a cohesive ending. Real example:
```
One thing you're glad you know now that you didn't know two hours ago.
```++}
	Both together are fine when the information list is short.
5. General, for every room: prompts are open (more than one defensible answer), not exhausted in a minute, never a comprehension check, never teach their own answer in the setup text, doable by 3 to 4 strangers in the time slot, and the meeting has an arc: each room's output can be retold in a sentence or two when the next room opens.
6. Complex questions contain a note: "Not sure what the question is asking? Copy it into Lens Coach, and ask for an explanation."

### Agent 3: Content fidelity
Read the unit's actual content (the module with its lenses, learning outcomes, and readings) and check the doc against it:
1. The reading line names exactly this unit's assigned content, nothing more or less.
2. Every claim the doc attributes to the source is actually made there; prompts never strawman the material.
3. Question-bank entries point at real claims, scenes, or moments in the text.
4. The main rooms target the unit's central content (what its learning outcomes care about), not a side detail.

### Agent 4: Logistics and links
1. The doc title names the right course and unit, and the [Group] placeholder is still unfilled (navigators fill it per copy).
2. The attendance link points at this unit's form, not a previous unit's (the classic copy-paste failure).
3. The course file's `# Meeting:` marker for this unit carries a `meeting-doc-template::` line with this doc's link.
4. The run-sheet's next-unit heads-up matches the next unit's actual reading; in the final unit it says there is none.
