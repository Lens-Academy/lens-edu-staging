---
title: AI Control Part 1 Unit 5 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 1 Unit 5 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

Last meeting, so go around on the course rather than the logistics:
1\. Something in this course landed on you: a number, a protocol, a hole nobody has closed. What was it, and what did it do to you? Unease, relief and irritation are all answers, and if you did not finish this unit, take it from any unit.
2\. In Unit 1's first room you were asked whether keeping a possibly adversarial, possibly superhuman system boxed in, while still getting useful work out of it, is tractable or hopeless. What did you answer then, and what would you answer now?
3\. Which part of the course moved it?


| Names | What landed on you + your answer then and now + what moved it |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: Ask it again  [0:24–0:42]

**New group. Names first, then straight in.**


A monitor flags a command. Rather than running it, or going straight to a weaker model, the protocol asks the same model again. It keeps no memory between tries, so it does not know it was asked before. Every extra ask costs time and compute.

- if a fresh answer comes back below the threshold, the least suspicious one runs
- if none of them do, the weaker model's action runs instead
- and if even the least suspicious answer is bad enough, the step goes to a human reviewer

1\. You set two numbers: how suspicious an action must look before you ask again, and how many times you ask. What do you pick, and what does each cost?
2\. A model that knows all this attacks once, then goes quiet. Does your setting catch it? What would?
3\. If you still have time: which number would you defend to a manager who wants more from the model?


Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Your two numbers and their price + the one-step attack |
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
### Room 3: Where does the monitor live?  [0:52–1:10]

**New group. Names first, then straight in.**


"The machine the agent runs on" is usually three machines:

- the one holding the weights, which produces the text
- the one running the loop, which reads that text and carries out the actions
- the one where the code actually runs

1\. You get one monitor. Which machine do you put it on, and what does it see from there?
2\. One route around you, through a surface you were given no monitor for: the watched copy inside the lab asks a weakly watched copy of itself on the public interface what to do, then carries the answer out with its own permissions. What catches that?
3\. If you still have time: one rule you would add to these three machines tomorrow.


Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Where you put it + what it sees + what catches the route around |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [1:10–1:15]

One or two people share what their group landed on.

---

\pagebreak
### Room 4: Your ongoing action  [1:15–1:27]

**New group. Names first, then straight in.**
This is the last meeting of Part 1. Part 2 is a separate five-day course that picks up where this one stops.
1\. Share the one thing you choose to keep doing after this course, and its first concrete step with a date. For example:

- read one control paper a week
- write up where you landed in Room 2 or Room 3
- talk to someone who runs monitoring at a lab
- apply for a job or a fellowship in this field

2\. After the meeting, tell your accountability buddy what you picked, so someone asks you about it.
3\. Feedback: what would make this course better for the next cohort, and what should Part 2 keep from it?


| Names | Your ongoing action with a date + feedback for the next cohort |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |

\pagebreak
### Wrap-up  [1:27–1:30]

Back in the main room, share if you feel like it: the ongoing action you picked in Room 4, and when it starts.
Before you leave (your navigator will talk through these):

- This is the last meeting of AI Control Part 1, so there is no next unit to read. Part 2 is a separate five-day course that picks up where this one stops, opening with two guided exercises, on collusion between two copies of a model and on making a model's work easier to check, then turning to the slow, spread-out failures this course only framed. Watch Discord for how and when to join.
- There is a final survey for this course; your navigator will point you at it.
- Found something unclear, wrong, or missing? The course is still in development: send it through [XLab's feedback form](https://forms.gle/KkWcHkKh87pygDzw9).


---



source:: [[../shared/Session Doc - Open discussion]]

# Tab: Participant FAQ
source:: [[../shared/Participant FAQ]]

# Tab: Navigator Run-Sheet

## Unit 5 Navigator Run-Sheet

source:: [[../shared/Navigator Run-Sheet - Before anyone joins]]

### Timeline (90 min)

| Time | Block |
|---|---|
| 0:00–0:05 | Lobby / welcome (whole group) |
| 0:05–0:19 | R1 Icebreaker (breakout, aim 3) |
| 0:19–0:24 | Back together (whole group) |
| 0:24–0:42 | R2 Ask it again (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 Where does the monitor live? (reshuffle) |
| 1:10–1:15 | Back together (whole group) |
| 1:15–1:27 | R4 Your ongoing action (reshuffle) |
| 1:27–1:30 | Close (whole group) |

### Lobby/Welcoming the participants

**[0:00–0:05]** (whole group). Chat with people as they arrive; **start the welcome at ~3 min, open breakout Round 1 at ~5 min.**


**The welcome**:


1. Ask participants to turn their cameras on.
2. Name the new format (small breakout rooms of 3, new people each time, and a five-minute get-together after each room where anyone can share what their group landed on)
3. Tell them the doc is in the chat + Discord and to open it + check they can type
4. Run through the arc
    - opening round and how the course landed → ask it again → where does the monitor live? → your ongoing action and feedback
    - say the meeting will take 90 min
5. Inform participants that you will be jumping between rooms with your camera turned off to listen in and they can ask questions whenever you join
6. Start room 1
    - If <= 4 participants show up, you don’t need to create breakout rooms. Just do the exercises in the main room

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: there is no next unit in this course, so say so plainly. AI Control Part 2 is a separate five-day course that continues the same track and opens with two guided exercises, on collusion between copies of a model and on making its work easier to check, then turns to the slow, spread-out failures this course only framed; tell them to watch Discord for how to join, point them at the final survey, and say that feedback on Part 1 goes to XLab's form (link in the session doc).**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



### Per-room notes for Unit 5

**General, all rooms.** Last meeting of the course, 4.75 hours of reading behind it including a 75-minute paper and a 60-minute one, and people will be both tired and a little sentimental. Protect the ending: Room 4 needs its full slot and the close should not be rushed. The unit rewards precision, so when a room drifts into "the monitor would catch it", ask what the monitor actually sees and when it sees it.
**Room 1, Icebreaker.** Ask 3 is about the whole course, not just this unit, so say so if a room reads it narrowly. Keep it personal and do not let it turn into an argument about whether control works; that argument belongs in Room 2. Anyone who did not finish the reading can answer asks 2 and 3 from the parts they did read, and ask 3 needs no reading at all. If a room is flat, offer a candidate: a monitor that reads everything an hour later is worthless against a failure that is finished in a minute.
**Room 2, Ask it again.** The commonest setting is a low threshold and many resamples, with no account of what it costs; push on the usefulness and reviewer time it spends. The paper's own trap is "attack once and hope", which the protocol is built to punish, so push on what happens to a single attempt that gets resampled. For your own use, the paper's finding is that the attacker has to keep attacking once it starts, because an attack that is abandoned after a resample simply gets replaced by its own benign answer, and an attacker that keeps going hands over a pile of suspicious samples instead. Ask 2 is where the paper's own answers belong, so hold them until a group has a setting on the table. A single attack that gets resampled is usually replaced by the model's own benign answer: neutralised, but nobody is caught. What the paper adds for exactly that case is a second, higher threshold, where even the least suspicious sample being that bad triggers more samples from the same step and an immediate review. Counting suspicious steps across a task, and going back to resample an earlier one, answer an attacker that keeps going rather than a one-shot. Ask 3 usually lands on usefulness: every resample costs latency and compute, a low threshold ships more work to the weaker model, and both burn reviewer time. Push them to say what the number they defend actually buys.
**Room 3, Where does the monitor live?** The three machines in the prompt are the inference, scaffold and execution servers; the reading's own answer to ask 1 is the scaffold, after the proposed action has been parsed and before it runs, because that is the only point where you can still choose not to do it. The Glossary tab says so too, so do not treat it as a secret; the work of the room is what the monitor then cannot see. Ask 2 is the harder half and there is no clean answer in the literature: the reading expects a combination of monitoring and dedicated security measures rather than either alone, and is pessimistic about several obvious fixes. If a room wants more, the systems-architecture reading notes that a model given weights and compute for its own research task can write its own agent loop on the execution machine, which is the simplest version of the same problem.
**Room 4, Your ongoing action.** Insist on a date; an action without one does not survive the week. Several people will say "keep reading", which is fine if it becomes a specific thing on a specific day. Feedback here is the last verbal primer for XLab's form. The course is in alpha and XLab expects to change it substantially before launch, so it is worth the two minutes. Then close: there is no next unit, Part 2 is a separate course starting from two guided exercises, and the call stays open for anyone who wants to keep talking.
**The close, in your own words (one minute).** Where the template says to ask for "one thing I'm taking away", ask instead for the ongoing action people picked in Room 4 and when it starts. Name the ending: five meetings and about 22 hours of reading, from a gut call about whether any of this is tractable to arguing about which machine a monitor sits on. Ask for ongoing actions from Room 4 out loud; those are the takeaways worth hearing. Then Part 2, the final survey, and XLab's form.

# Tab: Glossary
style:: plain

## Glossary

### Module: Win/continue/lose scenarios and execute/replace/audit protocols

Execute, replace, audit: The two decisions a protocol makes on each proposed action, based on the monitor's score: whether to run it or replace it, and separately whether to send it for review. Keeping the two decisions apart is the point.
Monitor and monitor score: A monitor is anything that takes a proposed action plus context and returns a number for how dangerous or suspicious it looks, whether that is a weaker model, a stronger one, or a probe on internal activations.
Auditing: Reviewing an action to decide whether it is evidence that the model is deliberately causing problems, usually ending in human review and possible escalation. Blocking or fixing an action is replacing, not auditing.
Win, continue, lose: The three ways an attack can end. Win means it was reviewed and the model was caught; lose means it ran and succeeded; continue means it failed quietly, nobody was caught, and the model will try again.

### Module: AI catastrophes and rogue deployments

Catastrophe: The end result you do not want to happen even once, such as an adversary amassing power or a war starting. The model getting out of the datacenter is not itself the catastrophe.
Safety measures: Interventions applied to every deployment of the model, internal users included, that try to prevent safety problems. That "every deployment" is the part a rogue deployment is defined against.
Instrumental versus terminal catastrophe: The terminal one is the end state itself; an instrumental one is something that puts the situation out of our control so the terminal one becomes likely and much harder to prevent. Establishing an unmonitored deployment is the central example of the instrumental kind.
Why the escape route is the worry: Causing a catastrophe under live safety measures is fundamentally hard, needing either a few wildly superhuman actions or a great many ordinary ones. Getting an unmonitored copy running is fundamentally easy, and afterwards nothing constrains the many actions a catastrophe needs.

### Module: Rogue internal deployments via external APIs

The external-API route: A third way to reach a deployment without the safety measures, alongside stolen weights and escalated permissions: a closely watched internal model builds a scaffold that asks a weakly watched external copy of itself what to do, then carries out the answer with its own privileged access. No weights leave the cluster and nothing is hacked, and the post rates it similarly important to the other routes and relatively hard to mitigate.

### Module: A basic systems architecture for AI agents that do autonomous research

The three servers: Inference hosts the weights and generates text; the scaffold keeps the agent loop, parsing responses and carrying out actions with the agent's tools; execution is where the code runs and results come back.
Why "the machine it runs on" is ambiguous: Those three jobs can sit on machines with completely different access. An agent running on your laptop does its thinking inside a datacenter it cannot reach, so it is in a poor position to steal its own weights.
Where safety mechanisms sit: In the scaffold, after the proposed action is parsed and before it is carried out. That is the only point at which the system can still ask a trusted model about the action and then run it, review it, or throw it away.

### Module: Practical challenges of control monitoring in frontier AI deployments

The four deployment dynamics: Thousands of instances acting at once, review that takes seconds to days rather than happening instantly, attacks that make partial progress across instances sharing an environment, and single actions that do not incriminate anyone well enough to justify shutting down.
Fully synchronous, semi-synchronous, asynchronous: Three monitoring choices, separated by what gets blocked while a flagged action waits for review: everything, only the flagged instance, or nothing. In the paper's worked example those come out at roughly 1%, 91% and 100% system availability.
Safety case: A structured argument that a particular deployment is safe, resting here on six claims a deployer would have to establish, including how much the monitor and the human reviewer catch, how fast review happens, and how fast the harm arrives.

### Module: Ctrl-Z: Controlling AI Agents via Resampling

Resample protocols: Protocols that exploit the model having no memory between calls by drawing extra samples of a suspicious action. Either a clearly benign sample comes back and runs, or the suspicious samples pile up as evidence.
Defer to resample: If an action scores above the deferral threshold, draw up to two more; run the least suspicious one that falls below it; if none do, use the trusted model's action instead; and if even the least suspicious sample is bad enough, send it for review.
Attack continuation probability: How likely the attack policy is to keep attacking on later steps once it has begun. The resample protocols in this lesson are built around it.
Auditing after three strikes: Count the steps in a task whose scores cross a threshold and send the whole trajectory for review on the third, with a separate higher threshold that triggers review immediately for a single-step attack.
Time travel: When a trajectory is close to the review threshold, go back and draw more samples from a suspicious earlier step, then make the review decision again with those in hand. It was the best-performing protocol in the paper.
Collusion signal: An arbitrary quirk the attack policy puts into real attacks that the defenders would never think to put into their own staged ones, so a colluding monitor can report everything except the genuine article.
Trusted paraphrasing: Having the weak trusted model rewrite the proposed commands as a description of what they do before any untrusted monitor sees them, which strips out the arbitrary details a signal could hide in while keeping enough to spot danger.

### Module: Environment construction

Persistent state: Most settings assume an attack has to fit inside one episode, but a coding agent comes back to the same repository tomorrow, so groundwork laid in an early change can be used much later and a monitor that only ever sees one change at a time misses it.

### Module: Why it's hard to make settings for high-stakes control research

What a setting has to provide: Tasks where you can check whether the work was done, plus a notion of unacceptable failure whose occurrence you can also check. Without both, a run cannot be scored and the adversarial game cannot be played.
Why that is hard: The tasks must be ones strong models can just about do and weak ones cannot, which means tasks nobody has saturated; the success measure gets optimised against, so it has to be robust; and the attacker is pushed toward the weakest thing that still counts as a failure.
