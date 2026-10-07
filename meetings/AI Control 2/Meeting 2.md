---
title: AI Control Part 2 Unit 2 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 2 Unit 2 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

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



Want help or an explanation for this question? Copy it into the [Lens Tutor](https://lensacademy.org/tutor) and ask for an explanation.


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



Want help or an explanation for this question? Copy it into the [Lens Tutor](https://lensacademy.org/tutor) and ask for an explanation.


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

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: reading is Unit 3, Research sabotage and exploration hacking in practice (the Auditing Sabotage Bench paper, then the 180-minute guided walkthrough of the exploration hacking paper; about 3.8 hours core, plus an optional 60-minute lens with the full password-locked models paper); remind them to send their Room-4 plan to their accountability buddy, and that feedback goes to XLab's form (link in the session doc).**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



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
