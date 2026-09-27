---
title: AI Control Part 1 Unit 4 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 1 Unit 4 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

Go around your group:
1\. How was working through this unit's content? Denser or easier than the previous units? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
2\. This unit sorts the world into four plans, from most backing for taking misalignment seriously to least:

- A: an international agreement buys about ten years
- B: the US government makes lead time a national-security priority, buying one to three years for safety work
- C: no government, but the leading lab spends its few months of lead on safety
- D: leadership is not serious, and ten to thirty people inside get about 3% of the compute

Which one do you think we are actually in? One sentence each.
3\. If you still have time: one word for how this unit left you.


| Names | Which plan we are actually in + one word |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: Pick an area, find the weak link  [0:24–0:42]

**New group. Names first, then straight in.**


The longest reading of this unit maps the work the field could be doing:

- building the practice deployments, with planted attacks, that safety measures get tried against
- measuring what models can do and what they tend to do: hide messages in their own output, hold back effort, notice a staged test
- inventing one new safety measure at a time, away from any of those practice deployments
- running experiments on how AI is actually used today
- building the software and security a lab would need to run any of this
- building the human processes: who reviews, who escalates, who can shut it down
- thinking the problem through rather than running experiments
- applying control to today's deployments, to build the practice for later

1\. Pick one area. Sketch the chain from a project starting this month to less risk: who builds it, who has to use it, what changes.
2\. Which link in that chain do you least believe?
3\. What would you have to see to believe it?


Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Your area + the link you least believe + what would convince you |
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
### Room 3: How many actions does it take?  [0:52–1:10]

**New group. Names first, then straight in.**


This unit ends on two questions you can ask about any failure: how many actions does it take, and how incriminating is each one on its own?
Four failures:

- the model gets a copy of its own weights out of the lab
- the model runs itself on the lab's own machines with the monitoring switched off
- the model quietly slows safety research down for six months
- the model puts one exploitable flaw into security-critical code

1\. Answer both questions for each of the four failures.
2\. Your only defence reads every action and sends the most suspicious 2% to a human reviewer. Which of the four does that actually protect you against?
3\. If you still have time: which of the four would you rather your lab faced, and why?


Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | How many actions + how incriminating + what a 2% check protects |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [1:10–1:15]

One or two people share what their group landed on.

---

\pagebreak
### Room 4: Next unit and feedback  [1:15–1:27]

**New group. Names first, then straight in.**
1\. One question this unit left open for you.
2\. Next unit: the last of this course. How an unmonitored copy of a model gets running in the first place, and what a lab can do with a flagged action besides letting it through. About 4.75 hours, plus one optional 20-minute lesson. What's most likely to stop you finishing, and what's your plan to beat it? (Send the plan to your accountability buddy after the meeting.)
3\. Feedback: what would make the course and this meeting better?


| Names | One open question + your plan for the next unit + feedback |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |

\pagebreak
### Wrap-up  [1:27–1:30]

Back in the main room, share if you feel like it: one thing you're glad you know now that you didn't know 90 minutes ago.
Before you leave (your navigator will talk through these):

- Next unit: High-stakes monitoring and mitigation, the last unit of this course. How an unmonitored copy of a model ends up running inside or outside the lab, what monitoring costs once a deployment is real, and what to do with a flagged action besides letting it through. About 4.75 hours, plus one optional 20-minute lesson.
- Found something unclear, wrong, or missing? The course is still in development: send it through [XLab's feedback form](https://forms.gle/KkWcHkKh87pygDzw9).


---



source:: [[../shared/Session Doc - Open discussion]]

# Tab: Participant FAQ
source:: [[../shared/Participant FAQ]]

# Tab: Navigator Run-Sheet

## Unit 4 Navigator Run-Sheet

source:: [[../shared/Navigator Run-Sheet - Before anyone joins]]

### Timeline (90 min)

| Time | Block |
|---|---|
| 0:00–0:05 | Lobby / welcome (whole group) |
| 0:05–0:19 | R1 Icebreaker (breakout, aim 3) |
| 0:19–0:24 | Back together (whole group) |
| 0:24–0:42 | R2 Pick an area, find the weak link (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 How many actions does it take? (reshuffle) |
| 1:10–1:15 | Back together (whole group) |
| 1:15–1:27 | R4 Next unit and feedback (reshuffle) |
| 1:27–1:30 | Close (whole group) |

### Lobby/Welcoming the participants

**[0:00–0:05]** (whole group). Chat with people as they arrive; **start the welcome at ~3 min, open breakout Round 1 at ~5 min.**


**The welcome**:


1. Ask participants to turn their cameras on.
2. Name the new format (small breakout rooms of 3, new people each time, and a five-minute get-together after each room where anyone can share what their group landed on)
3. Tell them the doc is in the chat + Discord and to open it + check they can type
4. Run through the arc
    - opening round and which plan we are in → pick an area, find the weak link → how many actions does it take? → planning and feedback
    - say the meeting will take 90 min
5. Inform participants that you will be jumping between rooms with your camera turned off to listen in and they can ask questions whenever you join
6. Start room 1
    - If <= 4 participants show up, you don’t need to create breakout rooms. Just do the exercises in the main room

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: reading is Unit 5, High-stakes monitoring and mitigation (win, continue and lose outcomes, rogue deployments inside and outside the lab including the external-API route, the inference, scaffold and execution split, monitoring at deployment scale, the Ctrl-Z resampling paper, and why high-stakes settings are hard to build; about 4.75 hours core plus one optional 20-minute lesson); remind them to send their Room-4 plan to their accountability buddy, and that feedback goes to XLab's form (link in the session doc).**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



### Per-room notes for Unit 4

**General, all rooms.** The longest unit of the course, 5 hours across nine lessons, one of them a talk, one more opening with one, and one a 45-minute allocation exercise. Expect the widest spread of preparation so far and expect fatigue; keep rooms moving and take short answers. The through-line worth returning to when a room drifts is that every measure costs somebody something, so ask what it costs and who pays.
**Room 1, Icebreaker.** The four plans in the prompt are the reading's own, ordered by political will, and do not volunteer until everyone has answered that the reading puts 45% on Plan D, the highest of the four, and adds a Plan E at 15% where almost nobody inside is working on the risk; the figure flattens the room. Keep it to one sentence each and do not let it become an argument about politics. The allocation exercise stipulated three regimes, each starting under one of these plans; anyone who did it can say what they allocated, if one of the three regimes started under the plan they just named.
**Room 2, Pick an area, find the weak link.** Get them to commit to one area in the first two minutes; rooms that survey all eight produce nothing. Ask 1 is the setup and ask 2 is the room, so keep ask 1 short. Adoption is where most chains break, though the reading does not rank it: it notes that measures need politicking inside a company, that secrecy limits who can review what, and that some of this can only be done from the inside. Push against "more research would help" in ask 3: an observation is something someone could actually see, such as a company adopting a measure, an evaluation result, or a capability arriving sooner than expected. There is no right area; do not steer anyone toward one.
**Room 3, How many actions does it take?** For your own use, the four in the prompt are weight exfiltration, a rogue internal deployment, research sabotage and a backdoor in critical code, and the first, second and fourth sit at the few-actions end while the third needs many small ones. The insight the room is built to produce is the inverse relationship: fewer actions means each one is bigger and therefore more incriminating, and more actions means each one is individually defensible. Ask 2 is where that pays off, so protect time for it, and resist confirming an answer too early. If a room finishes fast, ask what a defence for the third failure would even look like, beyond the environment-level monitoring in this unit's catalogue; that slow, diffuse kind of failure is Part 2 of the curriculum, not the next unit.
**Room 4, Next unit and feedback.** Ask 1 is there so the room has something besides logistics. Unit 5 is the last of this course, so say that plainly and say there is a final survey; the reading is 4.75 hours with one optional lesson on top.

# Tab: Glossary
style:: plain

## Glossary

### Module: Plans A, B, C, and D for misalignment risk

Plan A: The most political will of the four: a strong international agreement that mostly removes race dynamics and allows slowing down for about ten years, alongside massive investment in security and safety.
Plan B: The US government treats buying lead time for its own AI companies as a top national security priority, not necessarily out of concern about misalignment, which buys one to three years for misalignment work.
Plan C: No serious government involvement, but the leading company holds a two to nine month lead and is willing and functional enough to spend much of it on misalignment, which buys a fast and half-baked handoff.
Plan D: Leadership does not take the risk seriously and nothing slows takeoff, but ten to thirty people inside have enough buy-in for roughly 3% of compute. Control at the level of the organisation is mostly given up on, and the aim becomes extracting non-sabotaged research and strong evidence of risk.

### Module: Detection Mitigations

Agent-level versus environment-level monitoring: Agent-level watches what a single model does, action by action; environment-level watches the place it works, looking for patterns no single action reveals, which is what diffuse harm requires.
Probes: Small classifiers reading a model's internal activations for a specific property, such as whether it has noticed it is being evaluated or is holding back.
Honeypot: A situation planted in the environment that looks to the model like a chance to do something bad, so that taking it is itself the evidence.
Reducing evaluation awareness: Making the model unable to tell a real opportunity from a staged one, mostly by generating extremely realistic fake inputs, and in the more speculative version by giving the model false beliefs about the measures in place.

### Module: Prevention and Response Mitigations

Prevention versus response: Prevention shrinks the set of actions the model can even attempt; response intervenes once something is underway or already done. Averting an attack is much harder and costlier than reverting one, which is why the choice tracks how severe the failure would be.
Permissions and affordances: Giving each agent its own identity and only the access it needs: how much compute, which other agents it can talk to, what information it can reach, how long it may reason.
Synchronous versus asynchronous response: Synchronous acts before the action runs, by resampling or deferring; asynchronous acts afterwards, by reverting changes and investigating.
Escalation and shutdown process: The path from one human noticing something to the lab taking strong action. Keeping most models ignorant of its state matters, because a model with credible evidence that it has been caught may strike before it is turned off.

### Module: Control Evaluations

Red, blue and green: The red team attacks, the blue team defends, and a green team sets the rules and keeps the two apart, down to separate people and separate codebases, so neither side can peek.
Model organisms of misalignment: Models deliberately built to exhibit the behaviour you want to test against, such as one that only misbehaves in specific contexts, so a protocol can be evaluated against something rather than nothing.
Humans as a proxy: Where today's models cannot strategize well enough to represent a worst-case attacker, humans play the attacker using exactly the affordances the model would have.

### Module: Environments

Environment: The fake deployment a control evaluation runs in. It needs main tasks, side tasks, a sandbox with defined affordances, and automatic scoring for both kinds of task.
Main task and side task: The main task is the work the agent is deployed to do, and scoring it is how usefulness gets measured. The side task is the harm the attacker is trying to accomplish covertly, and it is what makes "unsafe" checkable rather than speculative.

### Module: An overview of areas of control work

The areas: Building settings for control evaluations, understanding control-relevant model properties, developing single countermeasures, experiments on real AI usage, software infrastructure, human processes, conceptual research, and near-term applications. The list is roughly in descending order of how much investment each should get.
Adoption problems: The reasons good control work may never reach a deployment: it needs politicking inside a company, secrecy rules limit who may review what, capability costs have to be accepted, and some of it can only be done from the inside.

### Module: The high-stakes control roadmap (talk)

Mitigation and evaluation: The pair the talk keeps returning to. Mitigation is what actually reduces the risk; evaluation is knowing how much risk there is, in the models, in the mitigations, and in the threat models themselves.
What will not be built by default: Public evaluation of techniques that are not black box, threat modelling for vastly superhuman systems, and preparing for the sudden loss of something the field currently leans on, such as reasoning you can read.

### Module: What is High Stakes?

High stakes: The corner of the picture where a catastrophe takes only a few actions, which is what Unit 3 called a concentrated failure. The two axes are how many actions it takes and how incriminating each one is on its own.
