---
title: AI Control Part 2 Unit 1 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 2 Unit 1 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

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

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: reading is Unit 2, Sandbagging and capability elicitation (the two kinds of sandbagging and what training does to them; the guided walkthrough of password-locked models; and the exploration hacking paper; about 4.25 hours, no optional lenses); remind them to message their Room-4 accountability buddy today, and that feedback goes to XLab's form (link in the session doc).**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



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
