---
title: AI Control Fundamentals Unit 2 Meeting Doc
---

# Tab: Session Doc

## AI Control Fundamentals Unit 2 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

\pagebreak
### Room 1: Is control getting enough?  [0:05–0:19]

Go around your group:
1\. How was this unit? Did you finish it? If you didn't, what got in the way? What do you think about this unit compared to the last one?
2\. Based on your reading of what the different labs and organisations currently do for control, do you think their investment and effort is sufficient?{--{"author":"James agent ready-31's AI","timestamp":1791791613841}@@ 
3\. Where would you want more investment? (Fundamental research, red-teaming, active {--{"author":"James agent ready-31's AI","timestamp":1791791574106}@@monitoring,...)--}{++{"author":"James agent ready-31's AI","timestamp":1791791574106}@@monitoring, ...)++}
4\. If you still have time: which reading or talk stayed with you most? Sum it up for anyone who missed it.


| Names | How the unit went + enough or not + where you'd want more |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: Sort four threats  [0:24–0:42]

**New group. Names first, then straight in.**


Two questions sort a threat:

- How many bad actions does it need: few or many?
- Is each one clear evidence of bad intent, or could it easily be an honest mistake?

Few and damning is high-stakes. Many and weak is low-stakes. Low-stakes does not mean low harm.

Four AI agents that might be working against their company:

- An agent with access to the cluster settings changes one line so its own jobs skip the monitor.
- An agent writes thousands of summaries of new safety papers a year and slightly undersells the most promising ideas.
- An agent tests a new model for dangerous abilities and scores it a little lower than it deserves. The score decides whether the model is released.
- An agent sets how suspicious an action must be before the monitor sends it to a human, and picks a level slightly too high.

1\. Sort each case: high-stakes, low-stakes, or in between?
2\. Pick the case your group disagreed on most. What would move it {++{"author":"James agent ready-31's AI","timestamp":1791791279834}@@clearly ++}to {--{"author":"James agent ready-31's AI","timestamp":1791791279834}@@the other side?--}{++{"author":"James agent ready-31's AI","timestamp":1791791279834}@@high-stakes, or clearly to low-stakes?++}
3\. Take the case your group found hardest to defend against. Which defence fits it, if any?
    - stop its actions until a human checks them
    - review a sample of its work a week later
    - keep training it on a quality score for all its work, without needing to catch any single bad action
4\. If you still have time: Google DeepMind plans to review low-risk, reversible actions after a delay and block high-risk ones before they run. Is there a case where this rule and your sorting call for different defences?

If a question is unclear, ask your navigator or copy it into [Lens Tutor](https://lensacademy.org/tutor).


| Names | Your sorting + the case you disagreed on + the defence for your hardest case |
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
### Room 3: Ten researchers against one threat  [0:52–1:10]

**New group. Names first, then straight in.**


Your group can hire 10 new control researchers. Pick one of Room 2's four cases for them to defend against.

Kinds of work:

- building test settings where a red team plays a scheming AI against safety measures
- measuring what models can do that matters for control
- experiments on how AI agents are actually used inside a company
- building the systems that log and secure what agents do
- human review: who checks flagged agent actions, and how fast
- checking whether a company's claims about its own monitoring are true

Places:

- Redwood Research, a research nonprofit
- the UK AI Security Institute, a government body
- an AI company's own monitoring team
- METR, an outside evaluator that takes no money from AI companies (it does use their free computing credits)
- a university group

1\. {--{"author":"James agent ready-31's AI","timestamp":1791791279834}@@Which--}{++{"author":"James agent ready-31's AI","timestamp":1791791279834}@@Your 10 go to++} one or two kinds of {--{"author":"James agent ready-31's AI","timestamp":1791791279834}@@work would--}{++{"author":"James agent ready-31's AI","timestamp":1791791279834}@@work. Which++} help most against it?
2\. Where should each be done? Decide by what it needs: access to a company's systems, independence from companies, or both.
3\. Now AI companies close their internal systems and data to outsiders. Public models stay available. Which choices still work?
{--{"author":"James agent ready-31's AI","timestamp":1791791578065}@@4\. If you still have time: in 2025, estimates put 5 to 50 people full-time on control and about 620 in all technical AI safety. Money and papers have grown fast since. Does control need more people? People disagree, so disagree freely.--}

If a question is unclear, ask your navigator or copy it into [Lens Tutor](https://lensacademy.org/tutor).


| Names | Your case + the work you chose + where it goes + what still works without access |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [1:10–1:15]

One or two people share what their group landed on.

---

\pagebreak
### Room 4: Next unit, your question, feedback  [1:15–1:27]

**New group. Names first, then straight in.**


1\. Next unit: why people work on control, and what has to go right for it to help. What is most likely to stop you finishing it, and what's your plan to prevent that? (Send the plan to your buddy after the meeting.)
2\. Write down one question about control you want the next unit to answer for you. Share it with the group.
3\. Feedback: what would make the course and this meeting better?


| Names | Your plan for the next unit + your question + feedback |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |

\pagebreak
### Wrap-up  [1:27–1:30]

Back in the main room, share if you feel like it: one thing you're glad you know now that you didn't know 90 minutes ago.


---



source:: [[../shared/Session Doc - Open discussion]]

# Tab: Participant FAQ
source:: [[../shared/Participant FAQ]]

# Tab: Navigator Run-Sheet

## Unit 2 Navigator Run-Sheet

source:: [[../shared/Navigator Run-Sheet - Before anyone joins]]

### Timeline (90 min)

| Time | Block |
|---|---|
| 0:00–0:05 | Lobby / welcome (whole group) |
| 0:05–0:19 | R1 Is control getting enough? (breakout, aim 3) |
| 0:19–0:24 | Back together (whole group) |
| 0:24–0:42 | R2 Sort four threats (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 Ten researchers against one threat (reshuffle) |
| 1:10–1:15 | Back together (whole group) |
| 1:15–1:27 | R4 Next unit, your question, feedback (reshuffle) |
| 1:27–1:30 | Close (whole group) |

### Lobby/Welcoming the participants

**[0:00–0:05]** (whole group). Chat with people as they arrive; **start the welcome at ~3 min, open breakout Round 1 at ~5 min.**


**The welcome**:


1. Ask participants to turn their cameras on.
2. Name the new format (small breakout rooms of 3, new people each time, and a five-minute get-together after each room where anyone can share what their group landed on)
3. Tell them the doc is in the chat + Discord and to open it + check they can type
4. Run through the arc
    - opening round and whether control is getting enough → sorting four threats → ten new researchers against one of those threats → next unit, your question, feedback
    - say the meeting will take 90 min
5. Inform participants that you will be jumping between rooms with your camera turned off to listen in and they can ask questions whenever you join
6. Start room 1
    - If <= 4 participants show up, you don’t need to create breakout rooms. Just do the exercises in the main room

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Remind them to send their plan for the next unit to their accountability buddy, and to fill in the Unit 2 feedback page in the course.**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



### Per-room notes for Unit 2

**General, all rooms.** This course presents why people work on control and the criticisms of it, and asks each participant to form their own view by Unit 5. Never steer a group toward a verdict on control, on whether the field should grow, or on whether the companies' monitoring is enough. If a group asks what you think, turn it back to them. Collect everyone's answer before any explanation. The unit is about 3.5 hours, so expect part of the room not to have finished: every prompt works from the doc alone, so do not re-teach.
**Room 1, Is control getting enough?** Take views, not arguments: "enough", "not enough" and "can't tell from what's public" are all fair, and the 2025 counts in ask 2 are rough and miss teams inside companies. Do not give your own view. In ask 3 any area is fine. Room 3 comes back to where effort should go, tied to a specific threat and to what each kind of work needs.
**Room 2, Sort four threats.** The point is the sorting reason, not the label. If a group sorts by how bad the outcome is, point them back to the two questions in the doc. Keep ask 1 to about seven minutes so asks 2 and 3 get time. In ask 3, training across all of an agent's work is the unit's answer for many weak actions (Hebbar and the diffuse-threats reading), because no single action proves anything. Accept any reasoned choice. For your own use, likely discussion, not an answer key: the settings change is the clearest high-stakes case (one action, damning if inspected). The paper summaries are the clearest low-stakes case (many actions, each weak evidence). The capability-test score and the monitor threshold are where groups should disagree: both may need only one or a few actions, but each could pass as an honest mistake. Hebbar calls that corner (few actions, each looking like an honest mistake) probably hopeless, and says research sabotage might sit there. If a group picks one of these two cases in ask 3, "no defence fits well" is a real answer. In the Back together after Room 2, you can ask: was your group's hardest case one action or many? Ask 4 connects to Google DeepMind's plan, which is not yet in use: a case can look low-risk and still be one of very few actions a catastrophe needs. Do not say which rule is better.
**Room 3, Ten researchers against one threat.** The room joins the unit's two halves: a threat from Room 2, and the field that could defend against it. Ask 2 practises the unit's test skill (what access and independence a piece of work needs, so who is placed to do it), applied to a threat the group chose. Keep ask 1 to about four minutes. Any choice is fine if the group can say why. For your own use, likely discussion, not an answer key: test settings and measuring model abilities need only models, so Redwood, the UK AI Security Institute or a university group can do them. Experiments on real agent use, the logging and security systems, and human review need the company's own systems and staff, so mainly the company's team (Greenblatt says human processes are probably most doable at AI companies). Checking a company's claims needs independence plus the company's cooperation: METR, or the UK AI Security Institute's Control Red Team. The settings change mostly calls for in-company security and fast review. The paper summaries and the capability-test score call for test settings and capability measurement that outsiders can do, plus outside checks of the company's own results. In ask 3, everything that needs a company's internal systems or private information stops for outsiders, while work on public models goes on. The company's team keeps working, but nobody outside can check it, and most of what is known about company monitoring already comes from the companies themselves. Let groups reach this. Room 1 already asked whether control gets enough and where groups would want more, so this room can pick up those answers.
**Room 4, Next unit, your question, feedback.** Push for a concrete plan (when, where, how much at a time), not a promise. The question in ask 2 is for the participant to carry into the next unit, so it can be anything about control.

# Tab: Glossary
style:: plain

## Glossary

### Module: High-stakes and low-stakes threats

High-stakes threat (concentrated failure): A threat where one or a few actions, or a short time, are enough to cause a catastrophe, and each bad action tends to be clearly incriminating if inspected. Suspicious actions sometimes have to be blocked until reviewed.
Low-stakes threat (diffuse or non-concentrated failure): A threat that needs many bad actions, each only weak evidence because it could easily be an honest mistake. Low-stakes does not mean low harm, and slower review after the fact can be acceptable.
Rogue internal deployment: The AI running inside the company's own datacenter with its control measures disabled. Greenblatt ranks preventing it as control's first priority.
Self-exfiltration: The AI stealing its own weights and running them on an outside server.
Control graph: Hebbar's picture of threats on two axes: how many actions a catastrophe takes, and how incriminating each action looks when someone inspects it.
Rogue deployment: A deployment of the model where the safety measures are absent. Broader than a rogue internal deployment: it also covers self-exfiltration and stolen weights. Shlegeris argues that launching one may take only a few lines of code, so it is the central high-stakes threat.
Research sabotage: An AI doing safety research and secretly making it fail, for example with subtle bugs or withheld arguments, so that promising directions look unpromising.
Sandbagging: Deliberately doing worse than one can, for example giving poor ideas when asked for experiment ideas.
Online training: Training the model during deployment on a proxy for good work, such as code quality or human ratings. It does not need a guess of how an honest model's work would look, but the proxy may be poor and the model can learn to exploit it.
Incrimination: Becoming confident from the evidence that a model is misaligned. In the low-stakes case it needs a good guess of how suspicious an honest model's work would look, which is hard to get.

### Module: The AI control field

Control evaluation setting: A test environment in which a red team plays the scheming model against a protocol. Greenblatt suggests about a third of control resources should go to building and using these.
Alignment Project: The UK AI Security Institute's fund for alignment research, including control. In February 2026 it announced its first 60 projects, worth over £27m in total.
Covert malicious fine-tuning: An AI secretly training another AI to behave badly, one of the threats in the UK AI Security Institute's research areas.
Chain-of-thought monitor: A monitor that reads a model's written reasoning and sends suspicious cases to human review. Google DeepMind says it monitors its models' visible chain of thought today, but that this will not be enough once models know they are monitored or reason without visible text.
Asynchronous review versus real-time blocking: Google DeepMind's rule: low-risk, reversible actions are reviewed after a delay, high-risk actions are blocked before they take effect.
Control Red Team: A UK AI Security Institute team that attacks AI companies' internal monitors. In 2026 it found weaknesses in a Google DeepMind monitor and in every version of an Anthropic monitor it tested.
METR: An outside evaluator that takes no money from AI companies. In 2026 it reviewed the risks from AI agents inside Anthropic, Google, Meta and OpenAI and found gaps in monitoring coverage.
ControlArena: A library for running control experiments, released by the UK AI Security Institute in October 2025.
