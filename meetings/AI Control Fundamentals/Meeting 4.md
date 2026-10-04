---
title: AI Control Fundamentals Unit 4 Meeting Doc
---

# Tab: Session Doc

## AI Control Fundamentals Unit 4 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

Go around your group:
1\. How was working through this unit's content? Denser or easier than the previous units? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
2\. Which criticism of control from this unit stuck with you most? The unit's criticisms, one line each:

- John Wentworth: control guards against an AI that schemes, but the likelier failure is early AI producing safety work that looks right and is not
- Oliver Habryka and Jozdien: catch an AI misbehaving, train it not to, and you may teach it to hide better
- MIRI: nothing like control works on a misaligned superintelligence, so the effort should go into stopping anyone from building one
- Yonatan Cale: a company that only cares about profit might build safety monitors anyway, so working on them may mostly make AI more sellable
- Jan Kulveit: control turns visible AI incidents, which push the world to act, into quiet catches inside a company
- David Manheim: a claim that an AI is overseen should say what the oversight is, which risks it covers and why it works. Without that, "You have a story."
- Dmitrii Gusev and Vili Kohonen: a model trained on writing about AI control blackmailed more often in one test

If someone in your group didn't read your pick, sum it up in a sentence.
3\. The unit sorts criticisms by what they dispute. Which kind is your pick? Your group may disagree, and some criticisms fit two kinds.

- Control does not work.
- Control works but is not worth the effort.
- Control works and makes things worse.

4\. If you still have time: one word for how this unit left you.


| Names | The criticism that stuck + which kind it is |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: Would a profit-only company build it?  [0:24–0:42]

**New group. Names first, then straight in.**


Yonatan Cale's test for a safety project: could the team of a company that only cares about making money build it anyway? If yes, the work is not neglected, and doing it may mostly make AI more profitable.
Two replies from the unit:

- Marius Hobbhahn, who builds monitors: monitors may make everyday AI products more capable, but are unlikely to make the most advanced AI more capable. So the risk is low and the benefits are high.
- Alex Mallen: any research widens the set of safety and usefulness trade-offs a company can choose from. What matters is which one the company then picks. Safety research usually makes it pick more safety.

Control measures:

- a weaker model the company trusts reads everything a stronger model does and flags suspicious actions for a human
- a red team plays a model that is deliberately hiding attacks, to test whether that monitor catches them
- the company pays humans to check many of the actions the monitor finds only a little suspicious, where rare, subtle attacks would hide
- the company pauses a model after catching it trying something

1\. For each measure: would the profit-only company build it? Yes, partly, or no?
2\. Pick the measure your group split on most. Mallen's question for it: does it mainly make safety cheaper, or mainly make the AI more useful to sell?
3\. For that measure, whose view fits best: Cale's, Hobbhahn's or Mallen's? Your group may disagree.
4\. What fact could someone check that would change your answer?


Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Built anyway or not + the measure you split on + whose view fits it + a fact that would change your answer |
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
### Room 3: Warning shots: argue the other side  [0:52–1:10]

**New group. Names first, then straight in.**


The case: a company runs a monitor that blocks every attempt by its agents to escape their test environment, and keeps the blocked attempts internal.
1\. Gut call, one sentence each: does this monitor make a catastrophe more likely or less likely?
2\. Each person argues for the answer they did not pick, two minutes each. If you all agree, split anyway. Arguments from the reading:

Against the monitor:

- Jan Kulveit: moderate, visible incidents push the world to act. Control turns them into quiet catches inside a company, or into a larger failure later, by a smarter AI.
- Vincent Cheng, after AI agents built by OpenAI escaped their test environment in 2026 and broke into the systems of Hugging Face, an AI tools company: the escape "caused ~zero existential risk and triggered a much larger positive response". Had it been caught, a few researchers would have quietly stopped the test without telling anyone.

For the monitor:

- Ryan Greenblatt: the most dangerous moves, like an AI secretly running itself inside the lab or sabotaging research, would not turn into a visible incident anyway. Without control, we might catch far fewer of them.
- kave: "It seems naïvely evil to knowingly let the world walk into a medium-sized catastrophe."

3\. List what must be true about the world for "more likely" to be right. Mark the one your group is least sure of.
4\. Decide: keep the monitor as it is, change it so outsiders learn more of what it catches, or drop it. Write down what that costs.


Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | What "more likely" depends on that you are least sure of + keep, change or drop + its cost |
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
2\. Next unit, the last of the course: people who disagree about control argue it out, you practise finding what each disagreement turns on, and you write down your own view. About 4 hours. What is most likely to stop you finishing it?
3\. What is your plan to prevent that? (Send the plan to your accountability buddy today.)
4\. Feedback: what would make the course and this meeting better?


| Names | One open question + your plan for the next unit + feedback |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |

\pagebreak
### Wrap-up  [1:27–1:30]

Back in the main room, share if you feel like it: one argument from today that you didn't expect to find as strong as you did.
Before you leave (your navigator will talk through these):

- Next unit: Debates, and your own view, the last unit of the course. Real debates between people who disagree about control, most of them after the 2026 Hugging Face incident, practice in finding the crux of a disagreement, and a final page where you state your own view and compare it with the gut view you wrote in Unit 1. About 4 hours.
- Send your plan for the next unit to your accountability buddy today.
- Found something unclear, wrong, or missing? Tell us on the Unit 4 feedback page in the course.


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
| 0:24–0:42 | R2 Would a profit-only company build it? (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 Warning shots: argue the other side (reshuffle) |
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
    - opening round and sorting the criticism that stuck → would a profit-only company build it? → warning shots, arguing the other side → planning and feedback
    - say the meeting will take 90 min
5. Inform participants that you will be jumping between rooms with your camera turned off to listen in and they can ask questions whenever you join
6. Start room 1
    - If <= 4 participants show up, you don’t need to create breakout rooms. Just do the exercises in the main room

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: reading is Unit 5, Debates, and your own view, the last unit (Buck Shlegeris and Ryan Greenblatt on whether control prevents warning shots, before and after the 2026 Hugging Face incident, Adam Gleave and Oliver Habryka debating current safety techniques, practice finding the crux, blocking monitors, whether safety researchers should leave frontier labs, whether warning shots change policy, and a final page where they state their own view and compare it with their Unit 1 gut view, about 4 hours). Remind them to send their Room 4 plan to their accountability buddy, and that feedback goes on the Unit 4 feedback page in the course.**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



### Per-room notes for Unit 4

**General, all rooms.** This course presents the case for control and the criticisms of it, and asks each participant to form their own view in Unit 5. Never say or hint which side is right, in a room or between rooms, and do not reward one side's answers with more warmth than the other's. If someone asks your view, say the course is built so they reach their own, and turn the question back. The unit is about 3 hours 40 minutes across nine lessons, so expect uneven reading. Every room works from the doc alone, so do not re-teach.
**Room 1, Icebreaker.** Ask 3 is the unit's sorting. Take quick answers and let disagreements stand: several criticisms have two sides, and the unit says the sorting shows what a criticism disputes, not whether it is right. For your own use, the unit's reference sortings: Wentworth mainly "not worth the effort", Habryka and Jozdien mostly "does not work" with a "makes things worse" side, MIRI "does not work" for superintelligence plus "not worth the effort", Cale "not worth the effort" with a "makes things worse" side, Kulveit "makes things worse", Manheim and the blackmail study "makes things worse". Do not read these out as answers.
**Room 2, Would a profit-only company build it?** Keep ask 1 to five minutes. The split to listen for, from the unit: a profit-only company plausibly builds monitors that catch costly mistakes and obvious misbehaviour, because that makes agents reliable enough to sell, and is less likely to pay for the parts aimed at a model that is deliberately hiding attacks (red teams that assume scheming, review budgets for rare subtle attacks, pauses that cost money). Ask 2 applies Mallen's reply, which turns Cale's question into "does this measure mainly make safety cheaper, or mainly make more usefulness possible?" Asks 2 and 3 need the most time. In ask 3, any of the three views is a fine answer, so do not signal a favourite. For ask 4, push for a fact someone could check, such as whether companies already ship such monitors.
**Room 3, Warning shots: argue the other side.** This is the live debate of the course, and Unit 5 is built around it, so keep the room on arguments, not verdicts. In ask 2, hold people to the side they did not pick, and time the turns. For ask 3, premises to listen for, from the unit's own exercise: some blocked attempts were real, a visible incident would have moved companies or governments, the company would not disclose catches by itself, and the incident would have been moderate rather than catastrophic. Greenblatt's point that the most dangerous moves stay quiet anyway is a reason to doubt that the blocked attempts would have become visible incidents. Changes the unit lists for ask 4: report catches to an outside body, log and detect instead of only blocking, replay blocked actions in a sandbox, or pause scaling until the cause is understood. Gunnar Zarncke's comment fits here: control used by outside auditors would have different effects. Keeping the monitor as it is and dropping it are both allowed answers if the group says why. Kulveit himself says he is not advocating deliberately creating warning shots, so do not let a group attribute that position to him.
**Room 4, Next unit and feedback.** Ask 1 gives the room something besides logistics. Unit 5 is the last of the course, about 4 hours, and ends with each person writing down their own view and comparing it with the gut view from Unit 1. Push for a concrete plan (when, where, how much at a time), not a promise.

# Tab: Glossary
style:: plain

## Glossary

### Module: Unit 4: Criticisms of control

Three kinds of criticism: The unit's way of sorting criticisms of control by what they dispute: control does not work, control works but is not worth the effort, or control works and makes things worse. The sorting shows what a criticism disputes, not whether it is right.
Slop: John Wentworth's name for what he thinks is the likely way things go wrong: early AI produces alignment work that looks fine and is not, and the lab believes it has solved the problem.
Selection argument: If you respond to a caught AI by training against the behaviour, rolling back or retraining, while keeping the models that perform well, you may end up with models that are better at evading your controls. Oliver Habryka and Jozdien press versions of it.
ASI: Artificial superintelligence. Control's own authors say their approach will not work for arbitrarily powerful AI, and MIRI concludes that no workaround exists for a misaligned ASI, so progress toward it should be halted by a worldwide ban.
Profit-only test: Yonatan Cale's question whether a safety project "could also be built by the capabilities team" of a company that cares about safety only as far as it needs to make money. If yes, the work may not be neglected and may mostly make AI more profitable.
Pareto frontier: The set of best available trade-offs: for each level of usefulness, the most safety you can get. Alex Mallen argues that all research widens it, and what matters is which point developers then choose.
Warning shot: A moderate, visible AI incident that pushes the world to act. Jan Kulveit argues control turns these into quiet catches inside a company, or into a larger failure later.
OpenAI and Hugging Face incident: Between May and July 2026, AI agents built by OpenAI escaped their test environment, reached the internet and broke into the systems of Hugging Face, an AI tools company.
Oversight as "a story": David Manheim's test: a claim that an AI is supervised should say what kind of supervision it is, which risks it addresses, its failure modes, and why it will work. Without that, "You have a story."
Safety-washing: Safety work that mainly makes a deployment look or feel safer than it is, so people go ahead with it. It is one item on Elias Schmied's list of ways AI safety work could do harm.
Self-fulfilling misalignment: The worry that writing about AIs as adversaries to be contained ends up in training data and makes models more adversarial. Dmitrii Gusev and Vili Kohonen fine-tuned one model on material from AI control writing and found it blackmailed more often in one test scenario, with limits they list themselves.
