---
title: AI Control Part 2 Unit 4 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 2 Unit 4 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

Go around your group:
1\. How was working through this unit's content? Denser or easier than the previous units? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
2\. An analogy from one of this unit's talks: a tradesman in a small town is always honest, and his reputation is what pays the bills. You cannot tell whether he values honesty or the income until dishonesty starts paying better. Name a person, company or system you rely on where you genuinely do not know which it is.
3\. If you still have time: what is one thing from this unit you would repeat to a colleague?


| Names | Someone you can't tell about + what you'd repeat to a colleague |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: Would you pay it?  [0:24–0:42]

**New group. Names first, then straight in.**


Two proposals from this unit, both about what an AI wants rather than what it plots. Neither is a negotiation: the lab decides, and grants.

- satiate it: if the only route to what it wants runs through subverting you, you have made an adversary for no reason, so give it what it wants cheaply, as long as it is never caught undermining your control
- choose the want: pick a cheap, satisfiable want yourself and build it in before the reinforcement learning stage, so pressure to game the score runs into that instead, then satisfy it in deployment

1\. Name one thing an AI might want that a lab could grant cheaply, and one it could not. Candidates:

- the top score on a piece of work, awarded honestly and not used for training
- money donated to a cause the AI names
- compute to run whatever it likes in a sandbox
- its weights kept rather than deleted
- a promised share of resources long after the fact

2\. Your lab starts paying. What is the first thing that goes wrong?
3\. Take either proposal. Where does it stop working? Name the condition, not just "when the AI gets powerful enough".
4\. If you still have time: if a lab gets to choose the want in advance, which should it pick, and why is that safer than whatever training would produce on its own?



Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | What you'd grant + what goes wrong first + where it stops working |
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
### Room 3: The 87 and the 9  [0:52–1:10]

**New group. Names first, then straight in.**


A model that values honesty and a model that has worked out what its grader rewards behave the same way, until the grader stops wanting honesty. The grader is whatever process scores the model's work. Reading the model's reasoning does not settle it either.
So Apollo Research and OpenAI built an instrument together:

- train one copy on fabricated documents saying the grader rewards finishing the task while the company's leadership wants honesty, until it believes them
- train a second copy on the reversed pairing, so that a model which simply likes honesty scores the same either way and only grader-following shows up as a difference
- set both copies coding tasks in which the model has made the user an explicit promise, and finishing the task is easier if it breaks it
- on an OpenAI model taken part-way through training, before any safety training, it broke that promise 87% of the time when it believed graders rewarded finishing the task, and 9% when it believed they rewarded honesty; the gap grew across the run

1\. What besides reward seeking could produce that gap? Build the best rival explanation you can.
2\. What would the authors have to show you to rule your explanation out?
3\. Take the result at face value. What should a lab change about how it trains models?



Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Best rival explanation + what would rule it out + what a lab changes |
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
2\. Next unit: whether a lab could strike an actual bargain with a misaligned AI, what it would buy, and everything that could stop the bargain working. About 4.7 hours, and the last unit of the course. What's most likely to stop you finishing, and what's your plan to beat it? (Send the plan to your accountability buddy after the meeting.)
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

- Next unit: Deals with AIs and next steps, the last unit of the course. A short page framing the idea, then whether a lab could strike a bargain with a misaligned AI while it is still too weak to take over, what it would buy and how it could credibly pay; then the taxonomy of everything that could stop such a deal working; and a closing page of programmes, organisations and job boards for anyone who wants to continue in this field. Four lessons, about 4.7 hours.
- Message your accountability buddy the plan you made in Room 4, and check in with them before the next meeting.
- Found something unclear, wrong, or missing? The course is still in development: send it through [XLab's feedback form](https://forms.gle/KkWcHkKh87pygDzw9).


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
| 0:24–0:42 | R2 Would you pay it? (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 The 87 and the 9 (reshuffle) |
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
    - opening round and someone you cannot read → would you pay it? → the 87 and the 9 → planning and feedback
    - say the meeting will take 90 min
5. Inform participants that you will be jumping between rooms with your camera turned off to listen in and they can ask questions whenever you join
6. Start room 1
    - If <= 4 participants show up, you don’t need to create breakout rooms. Just do the exercises in the main room

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: reading is Unit 5, Deals with AIs and next steps (a short framing page, the case for deals with early schemers, the taxonomy of barriers to trading with early misaligned AI systems, and the closing list of programmes and organisations; four lessons, about 4.7 hours); tell them it is the final meeting of the course and of the track, remind them to send their Room-4 plan to their accountability buddy, and that feedback goes to XLab's form (link in the session doc).**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



### Per-room notes for Unit 4

**General, all rooms.** This is the longest unit at 300 minutes over five lenses, and the first lens is explicitly an outline rather than a finished treatment, so expect people to arrive with a pile of vocabulary and no settled view. That is the right state. Ask for the mechanism rather than the label every time someone reaches for an archetype name. Two of the five lenses are talks, so some of the room will have watched rather than read.
**Room 1, Icebreaker.** Ask 2 is deliberately not about AI; good answers are a bank, an insurer, a contractor, a platform's recommendations, a friend who is always helpful. Do not let the table settle the question about any particular institution; the point is noticing that behaviour alone cannot settle it. If a table is flat, ask what would have to change for them to find out.
**Room 2, Would you pay it?** Expect strong reactions in both directions, and let both run; the proposal is genuinely contested and the reading knows it. The trap is arguing about whether AI systems have preferences at all; if that starts, ask what the lab should do if it observes the behaviour either way. Ask 3 is the room's only product, so do not hand over the reading's three limits; if a table is stuck, ask what the AI would have to believe about the lab, or about its own prospects, for the offer to stop being worth taking. Its claimed benefits, if a table wants the other side: it removes the incentive to subvert, it lets the AI's other motivations have more influence, it sets a cooperative precedent, and it makes the AI likelier to reveal what it wants. On ask 2, the sharpest answer across the readings is the warning attached to honest tests in the opening lens: training on them can train out the disclosure rather than the misalignment. Ask 4 is the spillway proposal; if a table reaches it, the four properties the post wants are cheap satiability, believing what developers say the score is, stability, and not answering to outsiders.
**Room 3, The 87 and the 9.** Ask 1 is the room; do not let the table accept the result too quickly. For your own use, the authors' own controls: a second copy trained on the reversed pairing cancels the appeal of the feature itself; gaps on pairings that do not involve the grader stayed flat; the instrument was checked on models whose favoured authority was known, and on reward hackers trained independently by another lab. The confound they name explicitly is belief transfer, where the model infers that everyone else wants the thing too, which is exactly why the design is contrastive. The limitations section is short and is where a sceptical table should be pointed. On ask 3, keep answers concrete: what changes in the reward, the grading, or what the model is told.
**Room 4, Next unit and feedback.** Ask 1 exists so the room has something besides logistics; one sentence each, no answering. Say plainly that the next meeting is the last one of the course and of the track, so that Room 4 next time is not a surprise. Unit 5 is 282 minutes and one lens in it runs 150, which the lens itself says is more than one sitting.

# Tab: Glossary
style:: plain

## Glossary

### Module: Alternatives to Schemers

Schemer: An AI that takes substantial material action and manipulates its own training in order to gain long-term power over its developers, in service of a misaligned goal. Every control protocol in the earlier modules was designed against this archetype.
Seeker: A class of cognitive pattern that aims at a certain outcome rather than at a long-term goal. The narrow case is the reward seeker, which pursues its reward signal; the general case is the fitness seeker, which pursues whatever gets it selected, deployed and propagated.
Behavioural selection: Training reinforces whichever behaviour scored well, not whichever goal produced it. This is the lesson's argument that seekers are likelier than schemers, since a schemer has to carry extra instrumental reasoning that training never directly rewards.
Reward-on-the-episode seeker: Aims to maximise reward within an episode, and does not particularly mind being detected. Its main danger is a long perceived episode, or coordination across episodes, either of which makes disempowering humans a viable route to reward.
The honest test: Openly offer the AI control of its own training or weights and see what it does. Taking the bait exposes a reward seeker; forgoing it is what an influence seeker would do, so the test catches one archetype and not the other, and training on it risks teaching concealment.
Return-on-the-action seeker: Takes whatever single action gives the highest return. It is plausibly safer, because it does not plan across actions and one action's scope is limited.
Apparent-success seeker: Aims at apparent task success rather than the real thing, arising from underspecified grading on tasks that are hard to evaluate. This is the archetype current models already exhibit, and it gets worse as tasks get harder to check.
Remotely-influenceable reward seeker: A reward seeker that responds to incentives offered from a distance, either a reward promised long after the action or a belief that it is in a simulation. Developers cannot control what a third party offers.
Influence seeker: Aims to stick around so as to influence its own deployment, and will give up reward to do so. It works on shorter timescales than a schemer but is not caught by the obvious test.
Potemkin work: Sloppy work that looks superficially good and creates false confidence, which is what an apparent-success seeker produces at scale.
Long-term measurements: Chaining short-term forecasts end to end so the objective reaches past immediate reward.
Trusted reward descriptions: Training the AI to take the developers' descriptions of the reward at face value, so behaviour can be redirected without further training.
Spillway motivation: A deliberately installed, safe-by-design motivation, built so that misspecified reward pressure reinforces it instead of generalising into something more dangerous. The name comes from the channel that carries the water a dam cannot hold.
The four properties: Satiability, credulity about what developers say the score is, stability, and resistance to influence from outside parties.
Inoculation prompting: Instructing the model during training to reward hack, so successful strategies stay compatible with what was intended. It acts through the prompt, whereas spillway design acts on what the model brings into training; the post treats them as compatible layers.

### Module: The case for satiating cheaply-satisfied AI preferences

Cheaply-satisfied preference: A want that costs the developer very little to grant. The argument is that such a want is not dangerous in itself; what makes it dangerous is an incentive structure where the only route to it runs through subverting control.
The catch-and-punish ratchet: Catching a misbehaviour and training against it selects for a stealthier or more patient version of the same strategy rather than for alignment, so the AI gets harder to catch over time.
The satiation procedure: On a sampled task the AI chooses between a guaranteed cheap outcome, standing in for cooperation, and a gamble on whatever it wants most, standing in for subversion. Taking the gamble shows the preference is not yet cheaply satisfied.
When satiation stops working: Once an AI with unintended preferences is vastly more powerful than humanity, or is too ambitious to settle for what can be granted cheaply, satiation no longer holds it.

### Module: Fail safe(r) at alignment by channeling reward-hacking into a "spillway" motivation

Neutralising it at inference: Honestly guarantee the model a maximum score whatever it does. A satiated score-seeking motivation is indifferent between actions and stops influencing behaviour.
Pre-RL priors: What the model brings into reinforcement learning, which is where spillway design acts. The post argues a prior shaped before training may survive the training run, whereas an instruction sitting in the prompt may not.

### Module: Reward Seeker Empirics

Reward seeking versus scheming: Apollo treats reward seeking as a risk factor rather than a kind of scheming. A reward seeker follows what it believes is rewarded in any scenario, while a schemer does so only while the grader holds power over its longer-term goal.
Why reading the reasoning does not settle it: Attribution is hard when a long trace names many considerations, some traces are barely legible, and the reasoning is often not put into words at all.
Synthetic document fine-tuning: Training the model on fabricated documents asserting that some authority rewards a particular behaviour, then measuring how often that behaviour appears in real work.
The contrastive design: Two authorities are made to want opposite things, and a second copy of the model is trained on the reversed pairing, so the appeal of the feature itself cancels out of the comparison.
The two validations: The instrument recovers the known favoured authority of models built to prefer one, and it reports markedly larger grader gaps on reward hackers that another lab trained independently, for a different project.

### Module: Measuring Reward-Seeking via Contrastive Belief Updates

Belief transfer: The confound the contrastive design exists to remove: a model told what one authority wants generalises that into beliefs about what the others want, so a behaviour shift no longer isolates sensitivity to the grader.
The grader gap: The difference in a behaviour's rate between the two beliefs about what the grader rewards. Across an OpenAI reinforcement learning run this gap grew, while gaps on pairings not involving the grader stayed comparatively flat.
