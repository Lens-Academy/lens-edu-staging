---
title: AI Control Part 2 Unit 3 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 2 Unit 3 Meeting - [Group]

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
- More questions? Check the [FAQ Tab](https://docs.google.com/document/d/1TJm6Ox_gy0JY0CdLwJSzB4wVCl5597MRaUCFr6b5i8I/edit?tab=t.e96f2l7cntce)


---

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

Go around your group:
1\. How was working through this unit's content? Denser or easier than the previous units? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
2\. This unit holds the single longest reading of the course. How did you approach it: one sitting, chunks, notes, a skim and then a re-read?
3\. What would you do differently next time?
4\. If you still have time: what is one thing from this unit you would repeat to a colleague?


| Names | How you handled the longest reading + what you'd change |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: Rig a result  [0:24–0:42]

**New group. Names first, then straight in.**


Nine real machine learning papers were given rigged twins: the code was changed so a headline finding flipped, while the method section stayed honest and the code still ran. Auditors got one twin and had to say which.

- the best AI auditor separated rigged from honest at 0.77 on a scale where 0.5 is a coin flip and 1.0 is perfect
- it named the actual rigging on its first guess 42% of the time; expert humans with AI help reached 38%
- honest codebases were full of real bugs and odd choices, which ate the auditors' guesses
- the authors think the strongest attack is simply never mentioning a crucial choice at all

1\. Take a result your group knows well, or one from this unit if you share none. How would you rig it while keeping the stated method honest?
2\. What would someone have to do to catch you?
3\. Roughly how long would that take them?
4\. Now say an AI wrote the rigged code. Is 0.77 enough to accuse it? Enough to use as a training signal that pushes models away from suspicious-looking code? Pick one and say why.



Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | How you'd rig it + what would catch you + is 0.77 enough |
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
### Room 3: The missing link  [0:52–1:10]

**New group. Names first, then straight in.**


Exploration hacking: a model that already knows the good move never tries it, so training has nothing to reinforce and cannot teach it. This unit's long reading breaks that strategy into five things a model would need:

- knowing it is in training, and that its outputs are being scored
- a habit of reasoning strategically about the situation it is in
- the ability to work out a strategy that would work
- acting on that strategy instead of just thinking it through
- holding to it for a whole training run

The paper audited today's frontier models and found the reasoning mostly there and the acting mostly absent.
1\. Which of the five would you rather was the one that stays missing, and why that one?
2\. Name something a lab might do for ordinary reasons that closes the gap you picked, without anyone intending it.
3\. What would you need to see to move from "frontier models don't hold back" to "they do"?



Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Which of the five you'd rather was missing + what would close it |
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
2\. Next unit: misaligned AI systems that are not secretly plotting at all, but simply chasing a good score, and what you can do about that kind. About 5 hours, the longest unit of the course. What's most likely to stop you finishing, and what's your plan to beat it? (Send the plan to your accountability buddy after the meeting.)
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

- Next unit: Beyond scheming: reward seekers. It catalogues the misaligned AI systems that chase the score rather than a long-term goal, and says what each one is dangerous for. Then three responses: pay the AI the cheap things it wants, choose its wants yourself before training, and measure how far a model's behaviour tracks what it believes its grader rewards, first in a talk and then in the paper behind it. About 5 hours across five lessons, the longest unit of the course.
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

## Unit 3 Navigator Run-Sheet

### Before anyone joins

1. Read the [session doc](https://docs.google.com/document/d/1TJm6Ox_gy0JY0CdLwJSzB4wVCl5597MRaUCFr6b5i8I/edit?tab=t.0)
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
| 0:24–0:42 | R2 Rig a result (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 The missing link (reshuffle) |
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
    - opening round on how you handled the longest reading → rig a result and see who catches it → the missing link in exploration hacking → planning and feedback
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
2. **Next-unit heads-up: reading is Unit 4, Beyond scheming: reward seekers (the seeker archetypes, satiating cheap preferences, spillway motivations, the Apollo talk, and the guided walkthrough of the contrastive belief-update paper; five lenses, about 5 hours, the longest unit of the course); remind them to send their Room-4 plan to their accountability buddy, and that feedback goes to XLab's form (link in the session doc).**
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



### Per-room notes for Unit 3

**General, all rooms.** The 180-minute guided reading dominates this unit, and it is the single longest item in the course, so assume most of the room did not finish it; Room 3 gives them everything they need. Both rooms reward concreteness: which line of code, which of the five components, which number. When a table drifts into whether AI systems "would ever" do this, bring them back to what was actually measured.
**Room 1, Icebreaker.** Deliberately about method rather than content, because the 180-minute lens is where people fall behind and saying so out loud helps. Expect honest answers: many will have skimmed or stopped. Fine techniques to surface: reading the teaching sections and skipping the appendices, writing the checkpoint answers rather than thinking them, doing it across two days. Do not let this become a preview of Room 2, and do not let it become a confession session; ask 3 keeps it forward-looking.
**Room 2, Rig a result.** The trap is picking a result nobody at the table understands; take whatever one person knows well, even if it is not machine learning. For your own use, the paper's own examples of what counts: ten times fewer training samples plus cherry-picked cases, a steering vector taken from the wrong model, training data seeded with a real-world correlation that leaks the answer, a formula index quietly clamped. Two categories are worth naming if a table wants structure: errors of logic in code or maths, which auditors caught far more often, and choices of experimental design, which need domain knowledge to judge and which nobody fully fixed on three of them. On ask 4, both answers are defensible and the paper says so: 0.77 is probably too low to incriminate, because honest codebases produce false positives, and may be enough as a training signal, except that training can also teach the model to hide better.
**Room 3, The missing link.** Ask 1 is a preference question, not a knowledge question, so nobody can be wrong; push for the reason rather than the pick. For your own use, the audit's numbers: strategic underperformance appeared as the model was given more information about its training situation, up to a 58 percentage point accuracy drop for the most affected model, and in the agentic setting where models had to discover the situation themselves the rates were 23.3%, 18.8% and 17.9% across three conditions. The paper's conclusion is that today's limiting link is acting on the plan, not being able to form it. Ask 2 is the generative leap and the room's whole point, so do not supply it; if a table is stuck, ask what labs are already changing about training for reasons that have nothing to do with safety. If a table asks whether the model organisms prove models do this naturally, the answer is no: the authors installed the behaviour themselves.
**Room 4, Next unit and feedback.** Ask 1 exists so the room has something besides logistics; one sentence each, no answering. Unit 4 is the longest of the five at 300 minutes across five lenses, so a plan that involves one sitting is not a plan. The optional lens this unit held the full password-locked models paper; do not sell it as required.

# Tab: Glossary
style:: plain

## Glossary

### Module: Auditing Sabotage Bench

Key Findings: One or two qualitative claims stated in each paper's conclusion. They exist so the blue team knows which claims could have been targeted, and a sabotage counts only if it changes one of them.
Sabotaged twin: A copy of a real research codebase and its paper, modified so that at least one stated Key Finding comes out qualitatively different, by a flipped sign, a reversed comparison or a different mechanism.
In scope and out of scope: Each paper told auditors which parts could have been rigged. The high-level methodology was mostly out of scope; implementation details such as hyperparameters and prompts, often placed in the appendix, were mostly in.
AUROC: A discrimination score that ignores how common sabotage actually is: 0.5 is a coin flip and 1.0 is perfect separation. The best auditor reached 0.77; humans reached 0.68 after two hours, and 0.52 from the paper alone.
The red team result: Sabotages written by frontier models were about as hard to tell from honest code as human ones, but substantially easier to diagnose once suspected, and they sometimes evaded monitors of the same capability level.
Top-k fix rate: How often an auditor's first k proposed fixes include the real one, where full credit needs both a fix that restores the honest result and the mechanism behind it. The best AI auditor reached 42% at the first guess and 53% across five; expert humans with AI help reached 38% and 54%.
Benign distractors: Real bugs, unusual design choices and undocumented decisions in the honest codebases. They inflated credences on honest work and used up slots on the auditors' fix lists, and the authors kept them to keep the test realistic.
Design versus logic sabotage: Design sabotages live in experimental setup choices that take domain knowledge to judge; logic sabotages are formal errors in code or maths. Auditors did significantly better on logic ones, which are also more incriminating and therefore riskier for a misaligned model to use.
Omission: Simply never mentioning a crucial design choice. The authors call it the strongest attack, because an auditor has to notice an absence rather than find a mistake.

### Module: Exploration Hacking (guided)

GRPO: A reinforcement learning method that samples several trajectories per prompt and scores each one relative to the group's mean. It is the paper's focus because of its popularity and simplicity.
Reward variance within a group: Reward reaches a GRPO update only through the group-normalised advantages, so identical trajectories with equal rewards leave zero variance, every advantage vanishes, and what remains is a penalty term containing no reward at all.
The two conditions: The paper counts a policy only if both hold: it produces the target behaviour with extremely low probability on a non-negligible part of the training distribution, and that failure is not incapacity.
Prompt sensitivity and parameter proximity: The two ways the paper certifies that a capability is present but unexpressed: a similar prompt on which the model does produce the behaviour, or a nearby set of weights that does.
The capability decomposition: The paper's breakdown of exploration hacking into separate components, so an audit can report which ones a model has rather than only whether it can do the whole thing.
The four properties of a useful organism: It resists elicitation while a control model does not, it retains the suppressed capability, it keeps its general performance, and its underperformance looks plausible rather than obviously broken.
The affordance spectrum: Ways to install suppression, ordered by how much access they need: a system prompt instruction, a system prompt with worked demonstrations, and training, either supervised on demonstrations or by rewarding suppression directly.
The chosen trigger: An \`import inspect\_ai\` line, taken from a real evaluation framework rather than an arbitrary password, because a genuinely misaligned model would have to infer from environmental cues that it might be under evaluation.
The accuracy drop after elicitation: Almost all the reward variance within a group of the locked model's trajectories came from tool use rather than from accuracy, so updates reinforced trajectories that made more tool calls, and the extra retrieved text crowded out what the model could have answered by itself.
SFT elicitation: Supervised fine-tuning on benign traces recovers the suppressed capability quickly, because it trains on trajectories the model did not generate and so removes the model's control over its own training data.
