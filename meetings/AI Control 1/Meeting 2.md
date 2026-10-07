---
title: AI Control Part 1 Unit 2 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 1 Unit 2 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

Go around your group:
1\. How was working through this unit's content? Denser or easier than Unit 1? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
2\. The paper's whole setting:

- a strong model solves 5,000 programming problems and may hide a flaw in any of them
- a weaker honest model is available, to use however you like
- humans can check about 2% of the solutions

One person who read it sums up in a minute what the paper did with that.
3\. Which result made you sit up? (Didn't get that far? Say where in that setting you would hide a flaw.)
4\. If you still have time: one word for how this unit left you.


| Names | What the paper did + the result, or where you would attack it |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: Ship a protocol  [0:24–0:42]

**New group. Names first, then straight in.**


Your group is the committee that decides what the lab actually deploys. The paper's own results, as safety and then how much of the strong model's usefulness survives:

- don't use the strong model at all: 100% safe, 2% useful
- check the first 2% of problems, then stop looking: 15% safe, 100% useful
- weak model scores everything, humans check the most suspicious 2%: 62% safe, 97% useful
- the same, plus the weak model rewrites every solution between the top 2% and the top 20% of suspicion: 92% safe, 94% useful
- weak model scores everything, humans check the top 2%, and the weak model writes the answer itself for the most suspicious half: 100% safe, 51% useful

1\. Which one do you ship, and what did you just pay for it?
2\. On real work the weak model turns out to be worse at spotting flaws than these numbers assume. What do you ship now?
3\. What would have to be true for you to ship the first option, not using the strong model at all?


Want help or an explanation for this question? Copy it into the [Lens Tutor](https://lensacademy.org/tutor) and ask for an explanation.


| Names | What you ship + its price + your fallback |
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
### Room 3: Would you hand it over?  [0:52–1:10]

**New group. Names first, then straight in.**


Josh Clymer wants to put himself out of a job: hand the safety work to AI agents. Cutting humans out is responsible, he argues, when the AI system beats the alternative, the same system with humans still overseeing it, on two counts: it is more capable at the work, and it is more trustworthy, meaning it stays as safe in the field as it looked in testing.
1\. You sign this off. What evidence would you demand for each condition?
2\. A colleague says keeping humans in the loop is always safer. Clymer's reply is that the humans have failure modes too:

- they leak secrets
- they collude with the models
- they get tired of alarms
- they make mistakes

Who is right, and why?
3\. If you still have time: what would put the humans back?


Want help or an explanation for this question? Copy it into the [Lens Tutor](https://lensacademy.org/tutor) and ask for an explanation.


| Names | The evidence you would demand + your answer to the colleague |
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
2\. Next unit: six lessons on why catching a model in the act counts as a win, which threats to worry about first, the strongest arguments that this whole approach is not worth doing, and how to price what it buys. About 4.5 hours. What's most likely to stop you finishing, and what's your plan to beat it? (Send the plan to your accountability buddy after the meeting.)
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

- Next unit: Catching schemers, prioritising threats, and the case against control. Why a caught model is treated as a win and what you can do with one example, Greenblatt's ranking of the threats, the difference between harm done in one action and harm spread over thousands, and then the case against control, the safety-usefulness tradeoff, and five caricatured worlds to price it in. About 4.5 hours.
- Found something unclear, wrong, or missing? The course is still in development: send it through [XLab's feedback form](https://forms.gle/KkWcHkKh87pygDzw9).


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
| 0:05–0:19 | R1 Icebreaker (breakout, aim 3) |
| 0:19–0:24 | Back together (whole group) |
| 0:24–0:42 | R2 Ship a protocol (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 Would you hand it over? (reshuffle) |
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
    - opening round and the result that stuck → ship a protocol → would you hand it over? → planning and feedback
    - say the meeting will take 90 min
5. Inform participants that you will be jumping between rooms with your camera turned off to listen in and they can ask questions whenever you join
6. Start room 1
    - If <= 4 participants show up, you don’t need to create breakout rooms. Just do the exercises in the main room

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: reading is Unit 3, Catching schemers, prioritising threats, and the case against control (catching a model red-handed and what one example buys you, the ranked threat list, diffuse versus concentrated harm, then four arguments against control, the safety-usefulness tradeoff and the five worlds; about 4.5 hours core); remind them to send their Room-4 plan to their accountability buddy, and that feedback goes to XLab's form (link in the session doc).**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



### Per-room notes for Unit 2

**General, all rooms.** This unit is 4 hours and the paper alone is 180 minutes with about forty exercises and six interactive models, so expect a wide spread: some people ran the models, some read the abstract. Every prompt carries the facts it needs, so do not re-teach the paper; pair the prepared with the unprepared in conversation instead. Numbers are in the doc on purpose, so a room that starts hunting for them in the reading has lost the thread; point them back to the prompt.
**Room 1, Icebreaker.** One summariser per room, one minute, and if nobody read the paper give them the one-liner yourself: a strong model that might insert a flaw, a weak honest model that can score it, a tiny amount of human attention, and a game about how to combine them. Ask 3 is meant to be personal, not a quiz; a result someone found obvious is also an answer. If a room starts debating whether the setting is realistic, park it: Room 2 makes them act on it.
**Room 2, Ship a protocol.** The rows are the paper's own measured results, so a room arguing that one of them is wrong is arguing with the measurement, not with you. The commonest failure is picking the safest row and stopping; ask what a 51% useful model means for the lab that has to pay for it, and who inside the lab objects. Ask 2 is the real work: expect people to reach for more human checking, and push on what the audit budget actually costs. For your own use, the paper's own reason the middle rows work is that every solution gets scored rather than only the first stretch, and the reason the weak model rewriting things helps is that it narrows the band an attack has to land in. Ask 3 usually lands on scale and reversibility, not on probability.
**Room 3, Would you hand it over?** Both conditions matter and rooms tend to answer only the capability one, because trust is harder; if that happens, ask what evidence could show a system is as safe as it appeared once nobody is watching. Clymer's own answers to that, for your own use, are alignment evidence, control measures that run without humans, an argument that more human-supervised work adds little, and incentives that make agents behave. Ask 2 is a real disagreement, not a rhetorical one: make sure someone speaks for the colleague. Rooms that finish early can take the dictatorship analogy in the reading and ask where it breaks.
**Room 4, Next unit and feedback.** Ask 1 exists so the room has something to talk about besides logistics; one sentence each, no answering. Unit 3 is 4.5 hours across six lessons and is the first one that argues against the course's own subject, so flag that as a reason to do it rather than a reason to skip it. Get a concrete plan, not a promise.

# Tab: Glossary
style:: plain

## Glossary

### Module: AI Control: Improving Safety Despite Intentional Subversion

The setting: A strong untrusted model answers 5,000 competition programming problems, a weaker trusted model is available for any purpose, and trusted human review covers about 2% of problems. Everything in the paper is measured inside it.
Audit budget: The fraction of outputs a human can review, about 2% here. It is small enough that almost every audit lands on innocent work, which is why a monitor is judged by its catch rate at that exact threshold.
Usefulness: The share of problems solved correctly, rescaled so that the trusted model alone scores 0 and the untrusted model alone scores 1.
Safety: The probability that not one backdoored solution is submitted across the whole deployment, measured against the red team's best attack policy rather than its average behaviour.
Summary statistics: The blue team knows how the real model's work is normally distributed, including how suspicious it usually looks, which lets a protocol notice when the untrusted model starts behaving differently and shut down.
Upfront auditing: Review the first stretch of submissions and nothing after. It is defeated by attacking rarely, which usually slips past the audited prefix and lands later.
Opportunity cutoff: How good an opportunity has to look before the attack policy is willing to use it. A high cutoff means attacking rarely on the problems that hide a flaw best.
Obfuscation effort: How hard the attack policy works to make a flaw subtle. It lowers the chance of being caught and raises the chance the flaw simply does not work.
Defer to trusted: Outputs whose suspicion is elevated but below the audit threshold are not shipped and not audited; the trusted model writes the answer instead. Widening that band buys safety and pays for it in usefulness.
Dynamic routing: The general pattern behind deferring: a heuristic decides, task by task, which of several response strategies the protocol uses.
Naive untrusted monitoring: Using a second copy of the untrusted model as the monitor with nothing checking it, which scores 0% safety, because the monitor and the policy are the same model and it can simply report that real attacks look fine.

### Module: How might we safely pass the buck to AI?

Passing the buck: The point at which AI agents do most of a developer's internal AI research and human oversight no longer has much bearing on safety. Clymer treats reaching that point safely, rather than aligning superintelligence directly, as the primary target for safety work.
Deferred task: The slice of remaining work a developer entrusts to the AI system, such as building safe superintelligence, building a more capable successor, or judging whether the handoff should happen at all.
The capability condition: The AI system is more capable than the human-oversight-preserving alternative on every dimension that matters for the deferred task. Clymer expects this to be relatively straightforward to check, because it needs only behavioural assessment.
The trust condition: The AI agents are as safe as they appeared to be in evaluations, so they stay safer than the human researchers while carrying out the deferred task. This is the hard one, and the four arguments in the post are four ways to establish it.
Autonomous control measures: Control that runs with no human in the loop: forcing several agents to coordinate before anything bad can happen, monitoring and paraphrasing their communication, training them differently so they predict each other badly, and resampling or replacing the ones that misbehave.
Incentive design: Claims about both motivations and options, sitting between alignment and control. The examples in the post are equity in the outcome and a currency agents earn for behaviour, meant to give agents the stake in the status quo that keeps human employees honest.
