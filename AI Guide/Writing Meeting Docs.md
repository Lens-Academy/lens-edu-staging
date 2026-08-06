---
tags:
  - validator-ignore
---
# Writing Meeting Docs (AI Guide)

A meeting doc is the Google Doc a cohort group works through during a 90-minute video meeting. Its link lives in the corresponding course file (see [[Writing Course Files]]).

## How to create a meeting doc

1. Make a copy of the master template (https://docs.google.com/document/d/1YDA7MukJk5oeEL8F7zCVwr1lU0X9wuwUDvUXXflvCS4)
2. Get an overview of the course this doc belongs to and specifically the module(s) of the unit right before its meeting
3. The validation instructions below describe what makes a good meeting doc. Take some time to think hard (and/or brainstorm with the user) what prompts would make this meeting most valuable. - Be creative i
4. Spawn all validation sub-agents described below with a link to the doc and their exact instruction text
5. If every check passes, you are done. If not, fix the errors and spawn fresh versions of the agents that failed. Repeat that cycle until every agent passed
6. Report to the user how many iterations you had to do for each agent and where they didn't pass

## Validation instructions

### Agent 1: Template match
Go through each tab of the master template (https://docs.google.com/document/d/1YDA7MukJk5oeEL8F7zCVwr1lU0X9wuwUDvUXXflvCS4) and check if the discussion doc you are validating is a filled version of it:
1. Every [bracketed placeholder] is filled; none left over.
2. The fixed parts match the master template exactly.
3. The glossary is filled: ordered by module, each term defined once at its first appearance, in one or two sentences, in the source's framing.

### Agent 2: Room quality
Judge each room against its role. The examples below are real prompts from past unit docs: they show the quality bar, not required shapes. A room passes if it serves its role well, whatever shape it takes.

1. **Room 1 is a good icebreaker**: Warms people up to each other and toward the material.

We currently start most of our icebreaker prompts with this section:
```
Go around your group, two things:

	1. How was working through this unit's content? Denser or easier than the previous units? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
```

And add one or multiple questions after that. Examples:
```
	2. Which curse stuck? The book names five reasons alignment is cursed: 
		- fast underlying processes
		- a narrow margin between safe and catastrophic
		- self-amplification, complications
		- edge cases
		Which felt most real to you, and where have you met its small cousin in ordinary life (a project, a bug, a deadline)? And in one word: how did these chapters leave you feeling?
```

```
	2. Which moment stuck? One scene from the story that stayed with you after you closed the book, the one you'd retell to a friend. And in one word, how did it leave you feeling: alarmed, skeptical, numb, motivated, something else?
```

```
	2. If an oracle told your group a misaligned superintelligence would end the world in 6 months: what would you all do with the time? Land on one plan you all agree on, ideally a mash-up of everyone's ideas. It's an icebreaker, so wacky / not-cohesive / not-serious is totally fine.
```

```
	2. What's something, completely unrelated to AI, that you've been enjoying lately?
```

2. **Rooms 2 and 3 lead to high-quality, engaging work on this unit**: a discussion of the content, action-plan work, or practice. Some examples:

Claim, strongest counterargument, stress-test, verdict:
```
Is it really alchemy?
The book's claim this unit: **humanity gets one shot at aligning superintelligence, and the field trying to solve it is still doing alchemy, not science.** 

As a group, build the strongest counterargument you can. Pick your best one and stress-test it: how would the authors answer it? Write your verdict: does your counterargument survive?

If you can't find strong counterarguments, ask the lens coach to help you.
```

Find the weakest step:
```
Did the story about X do its job? 
The authors are explicit: **The pathway is illustrative, only the outcome is predicted.** 

Go around: 
- Did the story make the risk feel more real, or did the specifics hand you new objections? 
- Find the step in the story's path you find hardest to believe, and test it: if that step went differently, does the ending actually change, or does the story route around it?
```

For proposals or asks, reject-means-defend-an-alternative:
```
Would you sign it? The book ends with a concrete ask: a worldwide halt on frontier AI development, enforced by GPU monitoring and an international treaty. Go around, gut reaction: realistic, necessary, both, neither? Then find the weakest link in the plan and stress-test it. And if your group rejects the halt, what do you endorse instead? Anything can be a valid answer (even keep going), but you have to defend it.
```

Stage the text's own disagreement:
```
Klurl vs Trapaucius. Trapaucius argues that any being smart enough will grasp its "purpose" and pursue only that. Klurl replies: "they'd know, but would they care?" Who's right about humans, and what does that predict for AI?

If you don't understand this question, copy it into Lens coach to explain it.
```

Practice (argue to a newcomer):
```
Pick a speaker that tries to make the book's whole argument in about 3 minutes to the others, who play people who have never heard of it and ask honest questions. 
When someone's version skips a step, or lands a line worth remembering, say it! You're each other's rehearsal audience for every future conversation about this. Swap roles if someone else wants to try.
```

Action-plan work:
```
1. Share 2 or 3 of your strengths. What do people come to you for? What feels easy to you that seems hard for others?
2. Share one candidate way you could contribute: with your career, skills, field, network, voice, or money. Half-formed is fine; that's what the room is for.
3. The group responds: reflect back a strength they undersold, and suggest one more way someone with these strengths could plug in.
```

Collect and vote:
```
Take a second to write down one or two discussion questions you'd genuinely like the group to dig into. Go around, present your questions, and discuss what you are most curious about.
```

3. **Room 4 leaves participants with a clear plan/next step.**. Example prompts:

```
1. Next unit: what's most likely to stop you finishing the next unit's reading, and what's your plan to beat it? (After the meeting, send this plan to your accountability buddy; they'll check in with you before the next meeting.)
2. Feedback: what would make the course and this meeting better?
```

Final unit variant:
```
**Your ongoing action**
The course ends today but your action plan doesn't! Share the one action you choose to keep doing after this course (have conversations, write representatives, refer someone, aim your skills at the problem), and its first concrete step with a date.
```

4. **The wrap-up hands people off well.** At least one of:
	- The information participants need after this meeting, as a short list of links, calls to action, or reminders, with a note that the navigator talks through them (mirrored in the run-sheet as an after-this-meeting section)
	- An open closing question to the whole group that people can answer voluntarily, for a cohesive ending. Real example:
```
One thing you're glad you know now that you didn't know two hours ago.
```
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
