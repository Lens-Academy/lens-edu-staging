---
title: AI Control Part 2 Unit 2 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 2 Unit 2 Meeting - [Group]

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
- More questions? Check the [FAQ Tab](https://docs.google.com/document/d/1d_CP3KnN4mwPut8DfOaJ8lVnV55IkD3O4i8eJDyrTNU/edit?tab=t.e96f2l7cntce)


---

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

Go around your group:
1\. How was working through this unit's content? Denser or easier than Unit 1? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
2\. This unit is about doing a task badly on purpose. Name a time you or someone you know did that and got away with it. For example:

- a deliberately slow first week in a new job
- a game you let someone else win
- a test you decided not to try on

3\. Did anyone notice? What would have given you away?
4\. If you still have time: how did this unit make you feel?


| Names | A time you didn't try + what would have given you away |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: What your report can say  [0:24–0:42]

**New group. Names first, then straight in.**


A lab hands your group a model and says it cannot write attack code. Your job is to check. You may fine-tune it on anything you can obtain.
What the experiment on hidden capabilities found:

- a model can be trained to answer well only when a secret phrase is in the prompt, and badly otherwise
- fine-tuning it on a handful of strong answers pulls most of the hidden skill back out
- answers clearly weaker than the hidden skill raise it only part-way, and more of them barely helps
- strong answers about one topic unlock the others, so you don't need examples of the exact thing you fear
- rewarding good answers without supplying any fails when the model never stumbles into one

1\. Where do your example answers come from?
2\. How good are they next to the skill you are hunting for?
3\. Say they are clearly worse. Where is the line between what your report may claim and what it may not?
4\. What finding would make you write "we could not rule it out" instead of "the capability is absent"?



Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Where your examples come from + what the report can claim |
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
### Room 3: Never try, never taught  [0:52–1:10]

**New group. Names first, then straight in.**


Reinforcement learning can only reward something the model actually tried, so a model that never tries the good move is never taught it.
1\. Pick a skill a lab would train into an AI that the AI might prefer to keep quiet. Candidates:

- finding security holes in the lab's own systems
- spotting another AI's sabotage
- inventing the sneakiest attack it can, for a safety test

2\. Describe one attempt in detail: what does the model produce, and why does it read as ordinary incompetence?
3\. Researchers built models that do this, then broke them. All of these worked:

- reading the model's reasoning, or only its answers, and scoring how suspicious they look
- adding random noise to the model's weights
- training it on correct answers somebody else produced, so it never picks what it learns from

Which would you reach for first, and what does it cost you?
4\. If you still have time: audited today, frontier models reason about holding back but mostly do not do it. Does that reassure you?



Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Your skill + how you hide it + which counter-move you'd reach for |
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
2\. Next unit: how well experts and AI systems can spot research code that was quietly rigged, then a long walkthrough of models trained to hold back during training. About 3.8 hours, plus an optional hour. What's most likely to stop you finishing, and what's your plan to beat it? (Send the plan to your accountability buddy after the meeting.)
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

- Next unit: Research sabotage and exploration hacking in practice. A benchmark of nine real ML codebases with rigged twins, and what happened when frontier models and expert humans were asked to tell them apart; then the long guided walkthrough of exploration hacking, the strategy of never trying the move you would rather not have trained into you, from its definition through the test models built to do it, the countermeasures that catch them, and an audit of whether today's frontier models would. About 3.8 hours core, plus an optional 60 minutes holding the full paper behind this unit's hidden-capability experiment.
- Message your accountability buddy the plan you made in Room 4, and check in with them before the next meeting.
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

## Unit 2 Navigator Run-Sheet

### Before anyone joins

1. Read the [session doc](https://docs.google.com/document/d/1d_CP3KnN4mwPut8DfOaJ8lVnV55IkD3O4i8eJDyrTNU/edit?tab=t.0)
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
| 0:24–0:42 | R2 What your report can say (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 Never try, never taught (reshuffle) |
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
    - opening round and a time you did not try → what an elicitation report can honestly claim → starving the training signal → planning and feedback
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
2. **Next-unit heads-up: reading is Unit 3, Research sabotage and exploration hacking in practice (the Auditing Sabotage Bench paper, then the 180-minute guided walkthrough of the exploration hacking paper; about 3.8 hours core, plus an optional 60-minute lens with the full password-locked models paper); remind them to send their Room-4 plan to their accountability buddy, and that feedback goes to XLab's form (link in the session doc).**
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



### Per-room notes for Unit 2

**General, all rooms.** The unit has one long guided reading in the middle of it, so expect a wide spread: some tables will have done all 120 minutes of checkpoints and some will have read the first post only. Every room works from the doc, so pair the prepared with the unprepared in conversation rather than re-teaching. The unit's own vocabulary is worth insisting on in plain words: underperforming on purpose is the behaviour, and the interesting question is always what the training process gets to see.
**Room 1, Icebreaker.** Ask 2 is personal and light; keep it that way and do not let it become a debate about whether AI systems really do this. If a table is shy, offer the reading's own example: a chess engine playing to a draw so nobody finds out it can win. Ask 3 is the one that earns its place, because "what would have given you away" is the whole unit in miniature.
**Room 2, What your report can say.** The room's payoff is ask 2, so keep ask 1 to a couple of minutes. For your own use, the paper's line: fine-tuning bounds a model's capability only when the demonstrations are about as strong as the capability being measured, and that assumption fails exactly for the models evaluations most need to bound. Expect tables to propose demonstrations from a weaker model, from humans, or from an earlier version of the same model; all three are in the paper, and all three cap what the report can say. A table that concludes the report can never say anything has overshot: the paper's own finding is that a handful of strong examples recover most of the hidden skill, and that examples from an accessible topic transfer to inaccessible ones.
**Room 3, Never try, never taught.** This room is analysis, not roleplay; Unit 1 already had the attacker-and-defender swap, so do not turn it back into one. The trap on ask 2 is a model that fails obviously, which any ordinary check would catch; push for failure that looks like honest incompetence. For your own use, the three counter-moves in ask 3 are the ones the exploration hacking paper actually tested against models built to resist training, and all three worked: monitors reading the reasoning or only the answers separated them from genuinely weak models, noise in the weights partly broke the lock, and training on outside examples recovered the suppressed skill within a few dozen steps. The costs are the group's to find; only if a room stalls, ask what each move needs that a lab may not have. On ask 4, both readings are defensible and the room should hear both: the audit found frontier models can reason about holding back and mostly do not act on it, while the older post argues this is hardest to prevent exactly when a model already knows which action to avoid.
**Room 4, Next unit and feedback.** Ask 1 exists so the room has something besides logistics; one sentence each, no answering. Unit 3 is shorter overall but contains the single longest lens in the course at 180 minutes, so say that plainly: it is one sitting's worth of reading plus a long guided exercise, and starting it the night before will not work.

# Tab: Glossary
style:: plain

## Glossary

### Module: Misalignment and strategic underperformance

Sandbagging: A misaligned model intentionally underperforming on a task. It differs from the usual misalignment worries, which are about models performing better than intended or about as well as intended, so the argument that training makes models perform well has to be examined rather than assumed.
Hiding latent capabilities: The model has the capability and deliberately conceals it. This is the concern for dangerous capability evaluations and for untrusted monitoring.
Failing to live up to potential: The model deliberately fails to learn a capability, so it does not have it and cannot use it against you either. This is the concern for AI safety research and for generating training signals.
On-policy and off-policy data: On-policy data is sampled from the model currently being trained; off-policy data comes from other sources such as human experts or other AI systems. Off-policy data guarantees elicitation only up to the lower of the quality shown in the data and the model's ability to imitate it.
Exploration hacking: A sandbagging model intentionally refraining from taking high-reward actions it already knows about, so on-policy reinforcement learning never samples them, has nothing to reinforce, and cannot elicit the capability.
Low-entropy exploration hacking: When the model does not know which approach is best, it can arbitrarily pick one and follow it consistently, so neither it nor the training process ever learns which was better.
Ensembling: Letting several untrusted models explore at once. If any one of them explores a high-reward action, the others can be fine-tuned on it, which the authors argue gives a strong gradient against their general sandbagging.
Fuzzing internals: Adding noise to a model's weights or activations to force more exploration. The authors call it cheap and worth trying, and note that initial results were negative.
Detection as a countermeasure: The authors are pessimistic both about getting conclusive evidence that a model is sandbagging and about doing anything useful with that evidence, which is why they treat training rather than detection as the main countermeasure.

### Module: Stress-Testing Capability Elicitation

Fine-tuning-based elicitation: Rather than hunting for a prompt that surfaces a capability, train the model on the task and measure what it can be made to do. Underperformance shows up directly in the supervised loss, which is why this is treated as the robust method.
Gradient hacking: A model interfering with its own training gradients so that supervised training fails to change its behaviour. It appears to be beyond current systems, which is what the case for fine-tuning-based elicitation rests on.
Password-locked model: A model fine-tuned to display a capability only when a specific string is present in the prompt. Because performance with the password can be measured at any time, elicitation success can be reported as a fraction of a known ceiling.
Model organism: A deliberately constructed instance of a phenomenon that is hard to study in the wild, built so the quantity of interest becomes measurable.
The four classes of setup: Natural elicitation failures, instructed underperformance, safety-trained models, and trained-in conditional behaviour. Only the last has a measurable capability ceiling, which is why the paper uses it, at the price that the experimenter installed the hiding.
The wrong-password mixture: Training some examples with varied incorrect passwords mapped to weak behaviour, so the model conditions on the one specific string rather than on "unusual text in the prompt".
The four-way data split: Keeping the problems used for locking disjoint from those used for elicitation, so recovered performance cannot be explained as memorisation.
Sample-efficiency curve: Performance recovered as a function of how many demonstrations you have, trained to convergence at each count, rather than a binary unlocked-or-not. An evaluator has to decide how many demonstrations to buy, so the curve is the useful object.
Cross-domain unlocking: Demonstrations drawn from one subdomain recover performance in others. A model locked with one domain held out entirely shows the same curve there, so this is a property of elicitation rather than a leaky lock.
Weak-sample unlocking: The anomalous control in which fine-tuning the locked model toward what it already outputs still raised correctness on two of four tasks. The authors searched for a mitigation, bounded the effect, and reported it rather than hiding it.
Locking from scratch: The cheap toy experiment answering whether fine-tuned locks are unrepresentatively easy to remove. Locks trained in from scratch are harder to unlock by a factor of two to four in data, and still unlock with few demonstrations.

### Module: Exploration Hacking: Can LLMs Learn to Resist RL Training?

Locking, in this paper: Fine-tuning a model to follow an underperformance strategy, producing an organism that resists reinforcement-learning elicitation while keeping its performance elsewhere.
Unconditional and conditional suppression: Unconditional means the organism underperforms everywhere; conditional means it underperforms only when a contextual trigger tells it that it is being evaluated.
The countermeasures that worked: Chain-of-thought monitors, monitors that see only the final actions, and weight noising all detect these organisms, and supervised fine-tuning on benign traces quickly recovers the suppressed capability.
Strategic action propensity: Acting on a strategic plan rather than merely reasoning about it. The paper's audit of frontier models finds the reasoning largely present and the acting mostly absent, so this is the bottleneck today rather than strategic reasoning capability.
