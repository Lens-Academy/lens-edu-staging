---
title: AI Control Part 1 Unit 5 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 1 Unit 5 Meeting - [Group]

### Navigator:

### Meeting link:

### How today works

You'll move through a few small **breakout rooms** (**3-4** people), meeting different people each time. In each room:


1. **Pick a scribe: one person who writes everyone's names and your group's answer into that room's table.**
2. Answer the prompt together; a line or two in the table is plenty, don't overthink formatting.


Between rooms everyone comes back to the main room for five minutes. Your navigator asks who wants to share what their group landed on. Speaking up is optional and a sentence or two is plenty, so if your group hit something the others should hear, that is the moment.


**Today's shape (90 min):** lobby 0:00–0:05 · Room 1 0:05–0:19 · back together 0:19–0:24 · Room 2 0:24–0:42 · back together 0:42–0:47 · break 0:47–0:52 · Room 3 0:52–1:10 · back together 1:10–1:15 · Room 4 1:15–1:27 · goodbye 1:27–1:30.


**🆘 Need help during a breakout?**

- Confused about the task, or want to talk to the facilitator? Click  **"••• More” > “Ask for Help"** > Your navigator gets pinged and pops into your room.
- Don't get the question or the reading? Ask the [Lens Coach](https://lensacademy.org/coach).
- More questions? Check the [FAQ Tab](https://docs.google.com/document/d/14RrHaPMKBELyddLNYG6geBIig8JQBV-uLEX77X6eT3M/edit?tab=t.e96f2l7cntce)


---

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



### Open discussion [1:30–...]

Want to discuss more?\
\
The call will stay open. If you are too many people, or you want to discuss with specific people, ask your navigator to create some breakout rooms that you can switch in and out of.

# Tab: Participant FAQ
style:: faq

## Participant FAQ

*Quick answers for the breakout-room meeting. Everything you actually do is in the session doc.*

### 🆘 Getting help during a breakout

Your navigator isn't in every room, so:

- **Confused about the task, or want a human?** Click **"••• More” > “Ask for Help"** > Your navigator gets pinged and pops into your room.
- **Don't get the question, or something in the reading?** Ask the [Lens Coach](https://lensacademy.org/coach). It's for understanding, not for handing you the answer.
- **Lost the doc link, or a quick logistics thing?** Check the **Discord channel** or the Zoom chat.

### Before you arrive

- **I didn't finish (or start) the reading, should I come?** Yes. Come anyway and just say so in Room 1; it's normal, and there's no penalty.
- **I'm running late.** Join whenever; you'll be dropped into a breakout and someone will catch you up.

### In your breakout

- **Do I have to talk, or have my camera on?** Cameras-on helps everyone connect, but do what you're comfortable with. Jump in when you've got a thought, there’s no need to wait to be called on.
- **What's a "scribe"?** One person per group jots the names and your answer into the table. A line or two is plenty; rotate it each room if you like.
- **We finished early / ran out of things to say.** Call your navigator to get ideas for expanding your current conversation. Or use the spare minute to agree what you would say if someone from your group shares between rooms.
- **No one's talking, or one person is dominating.** Just start talking when you have a thought; if it's really stuck, click Ask for Help.
- **Do we need a "right answer"?** No! The point is the discussion, not a tidy answer.

### Between rooms

- **What happens between rooms?** Everyone comes back to the main room for five minutes. Your navigator asks who wants to share what their group landed on, and waits. A sentence or two is plenty.
- **Do I have to share?** No. Nobody is made to speak, and a silent pause is a normal outcome. If your navigator invites you by name and you would rather not, “pass” is a complete answer.
- **I cannot remember what we decided.** Read the last line your scribe wrote in your room’s table.

### The reading and the questions

- **I don't understand the question or a claim.** Ask the [Lens Coach](https://lensacademy.org/coach)! It'll explain in plain terms.
- **Where's the reading?** It's in the course on the Lens platform: the chapter text is loaded right in the lesson. Can't find it? Ask the Coach or Ask for Help.

### Tech

- **I can't find the doc, or I can't type in it.** The link is in the Zoom chat and Discord; open it signed in with your enrolled account. Still stuck? Ask for Help.
- **My audio keeps cutting out.** Flag it in the chat, and leave/rejoin the room if it doesn't clear.

### After we wrap

- **What happens at 1:30?** We close on time. The meeting then stays open; hang around and keep talking if you'd like, no pressure.
- **How do accountability buddies work?** You paired up in the first session; your buddy checks in with you before each meeting. Swap whatever the last room asked you to take away: a plan, a next step, or simply what changed your mind.

# Tab: Navigator Run-Sheet

## Unit 5 Navigator Run-Sheet

### Before anyone joins

1. Read the [session doc](https://docs.google.com/document/d/14RrHaPMKBELyddLNYG6geBIig8JQBV-uLEX77X6eT3M/edit?tab=t.0)
2. Read this run-sheet
3. Download [zoom for desktop](https://zoom.us/download)
4. Sign out of your personal zoom account and into Lens Academy Navigator. The **credentials are in** **[#navigation-team](https://discord.com/channels/1440725236843806762/1461355080555958306/1525736943529365605)**
5. Join the meeting 10min before it starts
6. Claim Zoom host at the beginning of the session by:
    1. Click "Participants"
    2. Click "Claim Host”: and enter: **[CODE IN DISCORD](https://discord.com/channels/1440725236843806762/1461355080555958306/1525736943529365605)**
7. **Remove all note-taker bots**
8. Launch Lens Breakout Control App:
    1. …More > Apps > ![image|103.125x21.566](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/meeting-doc-543f720a4984.png)
    2. [How to Open video](https://drive.google.com/file/d/1V-ihOqzsIZZrXTTiTxTEVEd9PWl_EN3O/view?usp=sharing)
9. Get your group’s session doc link to post in the Zoom chat (from Discord)

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

### During the breakout rooms

1. Create breakout rooms (...more > breakout rooms)
    1. Use Zoom "assign automatically" - **Reshuffle every round**
    2. Aim for 3 people per room (4 is fine if it doesn’t fit)
    3. Setup timer (see below)
2. Use Lens Breakout Control app to monitor the breakout room conversations as they are happening.
    1. The app will show both the level and content of the discussions (it may take ~30 seconds after opening rooms to start displaying this information)
    2. Actively jump between rooms to unstick conversations, answer questions, and guide participants towards engaging deeply with the content.
3. Make a concerted effort to spread your facetime across the groups (even in the case where one needs more help than others). Participants really value your perspective and presence!

**Late Arrivals**: Zoom pings you and shows late arrivals in the participant panel. Greet them in main, explain the structure, and send them into a room.


### Back together (5 min, after Rooms 1, 2 and 3)

Zoom’s timer pulls everyone into the main room by itself; that is your cue. **Nobody is made to speak.**

- Ask the whole group: **“Who wants to share what your group landed on?”** Then **wait 30 seconds.** Count them. The silence is doing work, so do not fill it.
- If someone speaks up, let them share a sentence or two. Then ask again and wait again.
- Keep going while there is time: sharing gets about **4 minutes**. If nobody volunteers, that is a fine outcome; move on without commenting on it.
- You may invite someone by name if it feels right, but never push, and always let them pass to a groupmate.
- **In the fifth minute, explain the next room** and open it, so the room starts on time. Recreate the rooms while people are still talking.
- Four or fewer participants and no breakouts? Skip it and move to the next prompt.

### Zoom breakout timer (set it each round)

- When you open breakout rooms, open **Options** and check **“Breakout rooms close automatically after \_\_\_ minutes,”** then set the round length:
    - Room 1 = 14
    - Room 2 = 18
    - Room 3 = 18
    - Room 4 = 12
- Also check **“Countdown timer”** (e.g. 60 seconds) so everyone gets a warning before the room closes.
- Zoom then shows a live countdown in every room and pulls people back automatically, so you don’t have to watch the clock or broadcast “2 min left” by hand.
- Reshuffle and reopen with the next duration for the next round.

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: there is no next unit in this course, so say so plainly. AI Control Part 2 is a separate five-day course that continues the same track and opens with two guided exercises, on collusion between copies of a model and on making its work easier to check, then turns to the slow, spread-out failures this course only framed; tell them to watch Discord for how to join, point them at the final survey, and say that feedback on Part 1 goes to XLab's form (link in the session doc).**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












## Navigator Pro-Tips:

**1. Skeptic Unlock:** when a room stalls on **“AI won’t ever get that smart”**


Some rooms flatten when the group agrees AI will never become that capable. The discussion dies because there’s nothing left to argue. When that happens, show the trend:


- Pull up the [METR time-horizons graph](https://metr.org/time-horizons/) and discuss pace of task-length growth.
- A possible line: *“It’s not necessary for it to be smart today. Look at the slope, this is what an exponential looks like, and here’s where a few more doublings land us.”*
- Hand it back to the room: “Given this curve, what would change your mind, in either direction?”


**The goal is not to win an argument**. It is to turn a closed “no” into an open “huh, let’s take a look at this” so the discussion has somewhere to go.



**2. Doom Reframe:** when the material hits hard and **the room turns fatalistic**


Some rooms end heavy. The content genuinely rattles people (participants have talked about getting anxious and doom-scrolling after the reading), and a discussion can settle into “we’re doomed” with nowhere left to go. When that happens, don’t let it end there:


- Name it, then reframe: doom predictions assume today’s tools and limits, but the people working on this in the future will have new capabilities and methods we can’t see yet.
- Reach for the [Malthusian fallacy](https://en.wikipedia.org/wiki/Malthusianism): everyone predicted mass starvation from population growth, then farming methods leapt ahead and it never happened. A predicted catastrophe is not a guaranteed one.
- A possible line: *“It’s not all lost. The best thing any of us can do is work on it, so let’s not despair.”*
- **Hand it back to agency:** “*Given that, what’s one thing within your reach, a skill, a question, a next step?*”


**The goal is not to talk anyone out of their concern or paper over the risk.** It is to channel that energy into agency so people leave motivated rather than paralyzed.



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
