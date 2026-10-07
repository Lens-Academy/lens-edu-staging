---
title: AI Control Part 1 Unit 1 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 1 Unit 1 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

First meeting, so start by getting to know each other. Go around:
1\. Who you are: name, where you're joining from, what you work on. Skeptics welcome.
2\. How was working through this unit's content? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
3\. Keeping a system that may be working against you, and may be smarter than you, boxed in while still getting useful work out of it: tractable, or hopeless? Gut answer, one sentence each.
4\. If you still have time: what would have to be true to move you to the other answer?


| Names | Who you are + tractable or hopeless |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: The insider who might be compromised  [0:24–0:42]

**New group. Names first, then straight in.**


The course opens on an analogy. Banks and hospitals do not assume every insider is trustworthy. They assume one will not be, and build so the place holds anyway.
1\. Pick one organisation your group knows well. Examples:

- a hospital
- a bank or an audit firm
- an airline
- a university lab
- a newsroom

2\. What actually holds when one insider goes bad there? Name mechanisms, not good intentions.
3\. Now the insider is a model that writes and runs your code, works far faster than you, and may be pretending. Which of your mechanisms still works, and which breaks first?
4\. If you still have time: you cannot test whether this insider means well. What could you test instead?


Want help or an explanation for this question? Copy it into the [Lens Tutor](https://lensacademy.org/tutor) and ask for an explanation.


| Names | Your organisation's mechanisms + what carries over, what breaks |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |

### Back together: 5 min  [0:42–0:47]

One or two people share what their group landed on.

---



### Break: 5 min  [0:47–0:52]

\pagebreak
### Room 3: Attack tree: a backdoor lands in production  [0:52–1:10]

**New group. Names first, then straight in.**


An attack tree puts a goal at the top, every route to it underneath, and the steps each route needs.
You are a model writing code for a lab. Your work ships if the tests pass.
**Goal: a backdoor lands in production**, meaning code that passes every test and still does what nobody asked for.
1\. Write three or four routes to that goal.
2\. Take your best route and break it into steps that all have to happen.
3\. The lab now has a weaker model score everything you write for suspicion, and a human checks the 2% it scores most suspicious. Which step does that hit, and where does your attack go instead?


Want help or an explanation for this question? Copy it into the [Lens Tutor](https://lensacademy.org/tutor) and ask for an explanation.


| Names | Your routes + the steps your best one needs + where the monitor bites |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [1:10–1:15]

One or two people share what their group landed on.

---

\pagebreak
### Room 4: Buddies, next unit, feedback  [1:15–1:27]

**New group. Names first, then straight in.**
1\. Accountability buddies: pair up (a trio is fine) and swap contact details in the table. Before each meeting you check in: did you finish, are you coming?
2\. Next unit: the paper that started this field, read in full with exercises and interactive models built into it, and then the question of when it would be safe to let AIs take over the work of keeping AIs safe. About 4 hours. What's most likely to stop you finishing, and what's your plan to beat it? (Send that plan to your buddy today.)
3\. Feedback: what would make the course and this meeting better?


| Names | Buddy contacts + your plan for the next unit + feedback |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |

\pagebreak
### Wrap-up  [1:27–1:30]

Back in the main room, share if you feel like it: one thing you're glad you know now that you didn't know 90 minutes ago.
Before you leave (your navigator will talk through these):

- Next unit: The founding paper and passing the buck. The 2023 paper that turned control into something you can measure, read in full with exercises and interactive models built into it, then an hour of straight reading: Josh Clymer on when handing the safety work to AI agents is the safer choice. About 4 hours.
- Message your accountability buddy today, so you both know the channel works before the next meeting.
- Found something unclear, wrong, or missing? The course is still in development: send it through [XLab's feedback form](https://forms.gle/KkWcHkKh87pygDzw9).


---



source:: [[../shared/Session Doc - Open discussion]]

# Tab: Participant FAQ
source:: [[../shared/Participant FAQ]]

# Tab: Navigator Run-Sheet

## Unit 1 Navigator Run-Sheet

source:: [[../shared/Navigator Run-Sheet - Before anyone joins]]

### Timeline (90 min)

| Time | Block |
|---|---|
| 0:00–0:05 | Lobby / welcome (whole group) |
| 0:05–0:19 | R1 Icebreaker (breakout, aim 3) |
| 0:19–0:24 | Back together (whole group) |
| 0:24–0:42 | R2 The insider who might be compromised (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 Attack tree: a backdoor lands in production (reshuffle) |
| 1:10–1:15 | Back together (whole group) |
| 1:15–1:27 | R4 Buddies, next unit, feedback (reshuffle) |
| 1:27–1:30 | Close (whole group) |

### Lobby/Welcoming the participants

**[0:00–0:05]** (whole group). Chat with people as they arrive; **start the welcome at ~3 min, open breakout Round 1 at ~5 min.**


**The welcome**:


1. Ask participants to turn their cameras on.
2. Name the new format (small breakout rooms of 3, new people each time, and a five-minute get-together after each room where anyone can share what their group landed on)
3. Tell them the doc is in the chat + Discord and to open it + check they can type
4. Run through the arc
    - opening round and your gut call → the insider who might be compromised → building an attack tree → buddies, planning, feedback
    - say the meeting will take 90 min
5. Inform participants that you will be jumping between rooms with your camera turned off to listen in and they can ask questions whenever you join
6. Start room 1
    - If <= 4 participants show up, you don’t need to create breakout rooms. Just do the exercises in the main room

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: reading is Unit 2, The founding paper and passing the buck (the original AI control paper in full, which is where trusted monitoring and the safety-usefulness numbers come from, then Josh Clymer on handing the work to AI agents; about 4 hours core); remind them to message their Room-4 accountability buddy today and send that buddy their plan, and that feedback goes to XLab's form (link in the session doc).**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



### Per-room notes for Unit 1

**General, all rooms.** First meeting of a five-day course, so half the room will be sizing each other up rather than talking. Collect everyone's answer before any explanation; the first explanation anchors the rest. Expect silence after a prompt and count to ten before rescuing it. This unit's reading is 3.6 hours and the long lens is 180 minutes, so a good share of the room will have read part of it: every prompt is written to work from the doc alone, so do not re-teach, and do not let the people who finished lecture the people who did not. Call two minutes before each room ends; Room 4 needs its full slot for the buddy pairing.
**Room 1, Icebreaker.** Keep introductions to about thirty seconds each so the third ask gets airtime. Ask 3 is the optional reflection the Welcome lens set before any reading, so anyone who skipped it can answer cold. Take gut answers, not arguments: "hopeless" and "obviously tractable" are both fine, and the fourth ask is what keeps it from turning into a debate. If a room splits hard, park it and say Room 2 gives them something concrete to argue about.
**Room 2, The insider who might be compromised.** The room works best when the organisation is one somebody in the group has actually worked in; push them off "a tech company" onto something specific. For your own use, the mechanisms worth fishing for are separation of duties, logging, review by a second person, least privilege, rotation and audits. Ask 3 is the point of the room, so protect time for it: expect logging and review to survive the jump and expect speed, scale and volume to be what breaks them, since a reviewer who can only look at a small fraction of the work is the whole problem the course opens with. If a group decides the analogy fails completely, that is a real answer; ask them what the failure tells them about what a lab would have to build instead.
**Room 3, Attack tree: a backdoor lands in production.** This is a build, not a discussion, so get them writing routes in the first three minutes. Two traps. First, children that are not attacks ("try harder", "be sneaky"); ask what the model actually does. Second, one overloaded route that silently contains five steps; that is what ask 2 is for. Good material to fish for: pick a problem with complicated corner cases, make the flaw look like an ordinary mistake, spread it across more than one change, target code nobody reviews closely. Ask 3 is where the room pays off: expect the answer that the attack moves toward subtler flaws on less-watched work, and ask what that costs the attacker. There is no answer key and the lens's own bench has none either.
**Room 4, Buddies, next unit, feedback.** Insist on real contact details in the table. Unit 2 is 4 hours and the paper is 180 minutes, the same length as the lens they just read, so they know what that feels like; push for a concrete plan (when, where, how much at a time), not a promise. Feedback here is a verbal primer for XLab's form; the cohort is the calibration group for an alpha course.

# Tab: Glossary
style:: plain

## Glossary

### Module: Welcome to XLab's AI Control course

AI control: The approach that assumes a model may be working against you and asks whether you can deploy it anyway, get useful work out of it, and still prevent a catastrophe. The question shifts from "is this model safe?" to "does it matter if it isn't?"
Alignment: The other line of defence: trying to make the model actually want what we want, so that it never tries anything in the first place. Its awkward property is that good behaviour in every test is also what a model smart enough to behave well in tests would produce.

### Module: The case for ensuring that powerful AIs are controlled

Scheming: A model that eventually takes substantial material action against its developers, such as subverting control measures or sabotaging research, and manipulates its own training to gain long-term power in service of misaligned goals.
The control property: A set of safety techniques has it when potentially scheming models are not capable of finding and executing a subversion strategy with more than a small probability of an unacceptable outcome, such as exfiltrating their weights or hacking the datacenter.
Untrusted model: A model capable enough that scheming cannot be ruled out. The criterion is capability, so passing the relevant capability evaluations is what makes a model untrusted, not trusted.
Trusted model: An older or weaker model that is not capable enough to scheme effectively, so its work is honest but worse than the untrusted model's.
Protocol: A pipeline of safety techniques that answers every incoming task using the resources available: the untrusted model, the trusted model, and a small budget of human review.
Control evaluation: An estimate of a protocol's safety under deliberate subversion, made by replacing the untrusted model with an adversarial stand-in built by a red team and measuring how often the protocol avoids catastrophe.
Red team: The people who play the scheming model in a control evaluation, searching for the attack strategy that beats the protocol. Safety is always measured against their best response, not against average behaviour.
Trusted monitoring: The trusted model scores every output for suspicion and the most suspicious slice goes to human review. It holds only if the trusted model is good enough to push real attacks into that slice.
Untrusted monitoring: A second copy of the untrusted model does the scoring, which solves the capability gap and creates a loyalty problem: under worst-case assumptions the copy is scheming too and can simply collude.
Trusted editing: The trusted model rewrites the outputs that look suspicious but not suspicious enough to audit, so an attack has to score lower still to ship unchanged. Safety is bought with some of the untrusted model's usefulness.
Resampling: A flagged action is not run; the system rewinds and asks the model again, and the model keeps no memory between tries. It forces the model either to repeat the attack, which is far stronger evidence, or to hand over a benign action.
Catching an AI red-handed: Holding evidence that the model deliberately tried to cause a catastrophe, which control treats as a win rather than a near miss, because it converts a deniable risk into evidence a lab can act on and study. How strong that evidence has to be is the subject of a later unit.
Transformatively useful: Capable enough to massively speed up the work that reduces risk. The argument of this lens is that transformative usefulness probably implies very dangerous but probably does not imply uncontrollable.
Control window: The stretch in which models are already transformatively useful and dangerous, but a carefully designed protocol can still hold the control property. Its value depends on how much capability room it covers, how long it lasts, and what the work inside it is aimed at.
Problematic domains: The few areas where a wildly superhuman model would defeat control: hacking, persuasion, and manipulating scientific results or conceptual arguments. In most domains, wildly superhuman performance is not a problem for control.
Neuralese: Uninterpretable reasoning, memory or communication between AI instances. It makes red teaming, monitoring and capability elicitation all harder, and once models can pass arbitrary uninterpretable messages, preventing collusion is close to impossible.

### Module: Attack Trees

Attack tree: A picture of a system's security from the attacker's side: the goal at the root, and every way of reaching it underneath, each node becoming a subgoal with its own children.
AND and OR nodes: Under an OR node any single child is enough to reach the goal; under an AND node every child is needed. Everything that is not an AND node is an OR node.
Backdoor: A solution that passes all the test cases and that the model can construct a specific input to exploit, so the program returns something a correct solution would not.
