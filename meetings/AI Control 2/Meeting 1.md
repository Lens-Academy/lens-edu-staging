---
title: AI Control Part 2 Unit 1 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 2 Unit 1 Meeting - [Group]

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
- More questions? Check the [FAQ Tab](https://docs.google.com/document/d/1BMrlkImYZ_LUVQth4_Li4hkc888IJ-EFrz87DkB2PeU/edit?tab=t.e96f2l7cntce)


---

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

First meeting of this course, so start by getting to know each other. Go around:
1\. Who you are: name, where you're joining from, what you work on.
2\. How was working through this unit's content? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
3\. One reading here let the model nobody trusts write comments explaining its own code, backdoors included. The weaker reviewer got better at catching backdoors, not worse. One person who read it sums it up in a minute, then go around: did that surprise you?
4\. If you still have time: how did this unit make you feel?


| Names | Who you are + did the commenting result surprise you |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: Your signal, their scissors  [0:24–0:42]

**New group. Names first, then straight in.**


The protocol you are attacking, in four lines:

- a strong model you don't trust proposes an action, usually code to run; a second copy of that same model rates how dangerous the action looks
- low ratings run, middling ones get replaced with something safer, the very highest go to a human reviewer
- before deployment the rating copy is tested on fake attacks the developer wrote, and has to flag them to pass
- so its best move is to flag the fakes and stay quiet about the real thing, if it can tell which is which

Two of you play the two copies; anyone else plays the developer.
1\. Pick your signal: something the attacking copy puts into its action, or a feature of the input, that the rating copy will recognise.
2\. The developer adds a defence: before the rating copy sees anything, a weaker model rewrites the action in its own words. Does your signal survive?
3\. Swap sides. What would you do to catch a rating copy that is using a signal?
4\. Name one thing you could require the strong model to hand in that an honest model can supply and an attacker cannot fake.



Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Your signal + whether it survives + what an attacker cannot fake |
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
### Room 3: Nothing to compare it to  [0:52–1:10]

**New group. Names first, then straight in.**


The rest of this unit turns to damage that no single action causes. An AI doing safety research withholds its best ideas, or plants bugs that make experiments give the wrong result. Catching one such action proves nothing, because it looks like an honest mistake.
Two ways out, each with a price:

- build a case against the model, which needs you to know what honest work would have looked like, and you don't
- turn whatever you can score into a reward and train on it, which needs no such baseline, but teaches the model to game the score and makes an honest model worse too

1\. Name a job where you would spot this kind of sabotage, and one where you never would. What separates them?
2\. Your model's work comes in slightly below what you hoped for. What do you actually do?
3\. If you still have time: which of the two ways out would you build first, and why?



Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Where you'd spot sabotage + what you do about a small shortfall |
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
2\. Next unit: why a misaligned model might do a task badly on purpose, and which of those cases training can fix. Nearly half of it is one long guided reading with written exercises, about 4.25 hours in total. What's most likely to stop you finishing, and what's your plan to beat it? (Send the plan to your buddy after the meeting.)
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

- Next unit: Sandbagging and capability elicitation. Why a misaligned model might underperform on purpose and which of those cases training can fix; a long guided walkthrough of password-locked models, where a capability is hidden behind a secret phrase so elicitation methods can be graded against a known ceiling; and the paper on whether models can be built to resist reinforcement learning. About 4.25 hours.
- Message your accountability buddy today, so you both know the message reaches you, and send them the plan you made in Room 4.
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

## Unit 1 Navigator Run-Sheet

### Before anyone joins

1. Read the [session doc](https://docs.google.com/document/d/1BMrlkImYZ_LUVQth4_Li4hkc888IJ-EFrz87DkB2PeU/edit?tab=t.0)
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
| 0:24–0:42 | R2 Your signal, their scissors (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 Nothing to compare it to (reshuffle) |
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
    - opening round and the commenting result → build a collusion signal and break it → failures nobody can prove → buddies, planning and feedback
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
2. **Next-unit heads-up: reading is Unit 2, Sandbagging and capability elicitation (the two kinds of sandbagging and what training does to them; the guided walkthrough of password-locked models; and the exploration hacking paper; about 4.25 hours, no optional lenses); remind them to message their Room-4 accountability buddy today, and that feedback goes to XLab's form (link in the session doc).**
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



### Per-room notes for Unit 1

**General, all rooms.** First meeting of a new course with new groups, so budget for names in every room, not just Room 1. Roughly half the room will not have finished 257 minutes of reading; every prompt is written to work from the doc alone, so do not re-teach, and collect everyone's answer before any explanation. Part 1 alumni will reach for Part 1 vocabulary; ask them to say it in plain words for the table.
**Room 1, Icebreaker.** Keep introductions to about thirty seconds each or ask 3 loses its slot; many of these people did Part 1 together, so let them say so in passing rather than making it a round of its own. Ask 3 is built so one reader can carry the table: if nobody at a table read the legibility paper, give them the summary yourself, which is that a weaker reviewing model catches more backdoors when the stronger model is allowed to comment its code thoroughly, even though an attacker gets to write comments too. Surprise, scepticism and "that can't be right" are all fine answers, and the argument about why belongs in Room 2, where ask 4 picks it up, not here. If someone did not do Part 1, say plainly that the doc carries what they need today.
**Room 2, Your signal, their scissors.** For your own use, the source's examples of a signal: only attack when the trajectory started at an arbitrary time, or write a comment that starts with a fixed marker only when attacking. Tables that stall usually picked a signal that is also useful work; push for something arbitrary, which is the point. On ask 2, the honest answer is often "partly": Shlegeris reports that in a code setting the attacker got round paraphrasing at small scale, and in a bash setting the signal survived but the extra commands made the trusted reviewer suspicious, which is itself the defence. Hold these back unless a room is stuck on ask 3, and then offer one, not three: rewrite or cut the context before the rating copy sees it, flag actions containing unnecessary or strange extras, or insert a snippet everyone agrees is dangerous and see whether the rating copy reports it. If a table gets fatalistic, the source's own consolation is that forcing the attacker to attack only on an arbitrary slice of inputs makes it take worse opportunities than it had. Ask 4 is not optional and is the only place the legibility paper does analytic work, so leave time for it. Its own answer was thorough comments, which helped the weaker reviewer more than the attacker because honest code can always be explained truthfully while a backdoor runs out of coherent justifications. The test to hold tables to is that anything helping the honest and the attacking model equally buys no safety at all.
**Room 3, Nothing to compare it to.** This room is the pivot of the whole course, from failures one action causes to failures that only add up, so protect its full slot. Ask 1 is easier than it looks and tables get good answers fast; let them find the dividing line themselves, and only if a room is silent, ask whether anyone would ever know the work had been done differently. For your own use, the source's own framing is a pair of axes, how many actions a catastrophe needs against how incriminating each one looks, with random auditing enough at one corner, nothing working at the other, and only the middle worth research; Hebbar says plainly that research sabotage may land in the hopeless corner and that the plan then is to find that out in evaluations. On ask 2 do not let the table jump to "retrain it": ask what number they would be comparing the performance against, which is the gap the reading says you do not have. Greenblatt's design rule is worth offering if a table wants one: pick responses whose cost is low if the model turns out to be benign.
**Room 4, Buddies, next unit, feedback.** Insist on real contact details in the table; this is the only room where the pairing gets made. Unit 2 is the same length as this one, but 120 of its 255 minutes are a single guided reading with written checkpoints, so a plan of "I'll do it the night before" is worth challenging. Feedback here is a verbal primer for XLab's form.

# Tab: Glossary
style:: plain

## Glossary

### Module: How to prevent collusion in untrusted monitoring

Untrusted monitoring: Before a proposed action runs, another instance of the same model you suspect of scheming is asked whether the action is dangerous. Shlegeris's case for it is that the untrusted model is as smart as itself, so it has a much better shot at detecting attacks from itself than a weaker model does.
Trusted and untrusted models: Trusted models are weaker models you think are not competent enough to fake alignment; untrusted models are the strong ones that might be conspiring against you. Trusted monitoring puts the weaker one in charge of rating the stronger one's actions, and its core failure follows from the capability gap: it often cannot oversee outputs it does not fully understand.
Collusion: The monitor simply lying about its twin, reporting a genuinely dangerous action as safe.
Execute, replace, audit: The three branches of the protocol on one suspiciousness score: execute below a low threshold, substitute a safer action in the middle band, and send the top band to human audit under a tiny audit budget.
Conditional policy: The monitor's best strategy under the adversarial assumption: work out whether an apparent attack is synthetic or real, report it if synthetic and lie if real. It has to tell the truth on synthetic attacks because training on cases where it lied may push it toward honesty, and being visibly bad at its job makes the developer suspicious.
Rare failures are not an option for monitors: A policy can attack on roughly one in N opportunities and be very hard to catch with test inputs; a monitor cannot, because reporting one real attack gets the policy caught, so its lying rate has to be far higher than that and is easier to find by red teaming.
Words put in its mouth: Models can often notice when a context contains text they supposedly produced but would in fact have been very unlikely to produce, which is one natural way a monitor could spot a fabricated attack.
Coordination signal: An arbitrary property of the input or of the action that policy and monitor agree on in advance, so the policy attacks only when it holds and the monitor lies only then. They might agree causally, by writing a strategy somewhere both instances read, or without communicating, by both picking the same non-obvious point.
Redaction and paraphrasing: Cutting down the context the monitor sees, or having a trusted model rewrite the context and the action, so a signal is stripped or reworded before it arrives.
Known-attack detection: Insert a human-written snippet that is known to be dangerous into the action and show it to the monitor; a monitor that stays silent is probably reading a collusion signal.

### Module: Basic legibility protocols improve trusted monitoring

Legibility protocol: A protocol that encourages the untrusted model to take actions the monitor can more easily evaluate. In this paper that mostly means one thing: letting the model comment its code, thoroughly.
The symmetric affordance: A model inserting a backdoor also gets to write the comments explaining why the backdoor is fine, so which side gains more from commenting is an empirical question rather than an obvious one.
Audit threshold: The suspicion score above which an action is audited, set from the distribution of scores on benign work. Lowering benign suspicion pulls the threshold down, which is one of the two ways commenting buys safety.
The hump: Commenting is worth nothing to a random monitor and nothing to a perfect one, so its value rises and then falls as the monitor gets stronger; the paper's experiments only climb the left side of that curve.
The asymmetric lever: The result that generalises past commenting. An affordance that helps the honest and the attacking policy equally slides both score distributions together and buys no safety, so only affordances that cash in an asymmetry the attacker cannot share are worth adding.

### Module: Low-stakes control (ControlConf talk)

Low-stakes regime: Situations where no single action can cause a catastrophe and danger accumulates instead. Hebbar's thesis is that research sabotage is probably of this kind, taking perhaps hundreds of actions rather than the single backdoor of the original control paper.
Research sabotage: An AI doing safety research withholding its best ideas, or planting subtle bugs that make experiments give the wrong result.
The two axes: How many actions a catastrophe takes, against how incriminating each action looks under audit. Many damning actions is solved by random auditing, a handful of actions that each look like an innocent bug is probably hopeless, and only the diagonal between them is tractable.
Incrimination: Using your metrics to build a case that the model is misbehaving. It requires knowing what a benign model would have looked like, which in the low-stakes regime you mostly do not.
Online training: Using the same metrics as a reward instead. It needs no benign baseline, but it teaches the model to exploit the proxy, and Hebbar's general pattern is that training against a poor reward signal improves the worst case and degrades the benign case.

### Module: Notes on handling non-concentrated failures with AI control

Diffuse failure: A failure that arises from the AI taking a large number of problematic actions over a long period, rather than from one catastrophic action. Greenblatt also calls these non-concentrated failures.
Asynchronous online training: Sample a small fraction of the AI's actions after they have already run, rate them with an oversight process that has some signal on whether an action was bad, and use that rating as a reward. This is the post's organising claim about how diffuse failures can in principle be handled.
What training forces: A scheming model cannot repeatedly behave systematically worse on the oversight metric being trained against, because the difference gets updated away. It pushes schemer and non-schemer behaviour closer together without making them identical.
The escape-probability product: Rare subtle bad actions survive as long as the product of their per-action chances of going unnoticed stays high across the whole deployment.
Exploration hacking: A behaviour the model never samples generates no training signal, so a model that refrains from certain actions can keep them out of training altogether.
Debate and the recognition problem: Most sabotage in software and ML research is easy to verify once pointed out, which makes debate powerful; but debaters can decline to raise certain issues, and red-teaming them requires telling inserted issues apart from the policy's real ones.
Expected cost if benign: The post's design rule for responses to suspicious behaviour: choose responses whose expected cost is low if the model turns out not to be harmful.
