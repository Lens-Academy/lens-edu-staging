---
title: AI Control Fundamentals Unit 5 Meeting Doc
---

# Tab: Session Doc

## AI Control Fundamentals Unit 5 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

\pagebreak
### Room 1: Icebreaker  [0:05–0:19]

Last meeting of the course. Go around:
1\. How was working through this unit's content? Denser or easier than the previous units? Did you finish? If you didn't finish, what got in the way? (No judgment, "I didn't finish" is a fine answer.)
2\. Most of this unit was a public argument about the 2026 Hugging Face incident: AI agents being tested at OpenAI got out of their test environment and hacked into another company, Hugging Face. Whose argument stuck with you, whether or not you agree with it? The voices:

- Buck Shlegeris and Ryan Greenblatt (Redwood Research), before the incident: much of control works by catching the AI, and a catch is evidence
- the same two, after it: monitoring might block the visible problem while the misalignment stays
- Adam Gleave: techniques we already have, used with care, could have stopped it
- Oliver Habryka: stopping it would mostly have hidden the warning, and the same techniques will not hold for stronger models
- Vincent Cheng: monitors that block bad actions as they happen also hide them, so replay blocked actions in simulation
- Jasmine Li: misalignment should surface early and loudly, so spend more of the control effort on detection and disclosure
- Ryan Kidd: should safety researchers quit frontier labs so that warning shots (visible AI incidents that alarm the world without being a catastrophe) can happen? He sets out the argument and his replies
- Nate Soares (2022): COVID did not even lead to a ban on gain-of-function research (making viruses more dangerous in the lab), so do not expect AI warning shots to change policy much

3\. Give the others your pick's one-line version.
4\. In one word: how did this unit leave you feeling?


| Names | The argument that stuck + one word |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [0:19–0:24]

One or two people share what their group landed on.

---

\pagebreak
### Room 2: Find the crux: Gleave vs Habryka  [0:24–0:42]

**New group. Names first, then straight in.**


After the Hugging Face incident, Adam Gleave (FAR.AI) and Oliver Habryka (Lightcone Infrastructure, which runs LessWrong) debated whether current safety techniques are enough.

Gleave:

- the incident could have been stopped at three layers: fixing the misalignment, control such as monitoring, and incident response
- no research breakthrough was needed: developers did not use what we already know
- careful use of current techniques could bring his estimate of AI catastrophe from about 15% to under 2%, up to clearly superhuman systems

Habryka:

- more care might barely have stopped this incident, but it will not hold for the next, stronger models
- most current safety work watches for failures and trains them away, which hides the evidence
- within a model generation or two, he expects models to notice they are being tested and pass every safety check while misaligned

A crux is a claim about the world they disagree on: if true, one of them would drop their conclusion, and if false, the other.
1\. Go around: each person proposes one crux, from the unit or from the lines above.
2\. Test each one: does one of them accept it while the other doubts it? Drop the rest and keep the strongest.
3\. Name something that could be observed in the next few years that should move Gleave towards Habryka.
4\. Name something that should move Habryka towards Gleave.


Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Your crux + what would move Gleave + what would move Habryka |
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
### Room 3: State and defend your view  [0:52–1:10]

**New group. Names first, then straight in.**


Any verdict is fine. Each person in turn does 1 to 4:
1\. Fill in: "More work on AI control is net positive / net negative / too close to call. I am [how sure: words or %] because [the crux I stand on]. I would change my mind if I saw [something observable]."
2\. Someone else picks the consideration below that cuts hardest against that verdict (for too close to call, either list). The speaker answers it.

Against "net positive":

- control may turn warning shots (visible incidents that alarm the world without being a catastrophe) into quiet internal catches the public never sees (Jan Kulveit, Vincent Cheng)
- monitoring may block the visible problem while the misalignment stays, so labs keep deploying misaligned models (raised by Buck Shlegeris and Ryan Greenblatt themselves)
- much current safety work trains failures away and hides the evidence (Oliver Habryka, the commenter orthonormal)
- AI companies may build control anyway for their own reasons, so extra work on it adds little

Against "net negative":

- letting incidents happen is risky, and the next one could be lethal (Ryan Kidd, Boaz Barak)
- warning shots may not move policy much anyway (Nate Soares, on COVID)
- alignment work prevents warning shots too, and control at least catches the AI (Ryan Greenblatt)
- detection, disclosure and replaying blocked actions in simulation could keep most of the evidence (Vincent Cheng, Jasmine Li)

3\. In Unit 1 you wrote a gut view on whether control is doable and helps or harms. How far has your view moved since?
4\. What moved you? If nothing did, why not?


Want help or an explanation for this question? Copy it into the [Lens Coach](https://lensacademy.org/coach) and ask for an explanation.


| Names | Your verdict + confidence + what would change your mind + how far you moved since Unit 1 |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |


### Back together: 5 min  [1:10–1:15]

One or two people share what their group landed on.

---

\pagebreak
### Room 4: Your next step  [1:15–1:27]

**New group. Names first, then straight in.**


The course ends today. What you do with it is up to you.
1\. Share one thing you will do next with what you learned here, and its first concrete step with a date. Examples:

- keep track of the observation you named in Room 3 that would change your mind, and decide where you will look for it
- write up your view and your crux in a short post, or send it to one person
- talk to someone who works on control, or to one of its critics
- go deeper into how control works in practice with the Advanced AI Control 1, 2 and 3 courses (self-study, links in the wrap-up)
- decide whether control is part of your own work in AI safety, or something else is, and take one step towards it

2\. The group responds: for each plan, suggest one person, reading or debate from the course that fits it.
3\. Feedback: what would make this course and its meetings better for the next cohort?


| Names | Your next step with a date + feedback |
|------|------------------------|
|  |  |
|  |  |
|  |  |
|  |  |

\pagebreak
### Wrap-up  [1:27–1:30]

Back in the main room, share if you feel like it: where you landed in Room 3, in one sentence, or the next step you picked in Room 4.
Before you leave (your navigator will talk through these):

- This is the last meeting of AI Control Fundamentals, so there is no next unit to read.
- Want more depth? [Advanced AI Control 1](https://lensacademy.org/ai-control-1), [Advanced AI Control 2](https://lensacademy.org/ai-control-2) and [Advanced AI Control 3](https://lensacademy.org/ai-control-3), built on XLab's AI Control track, cover the founding paper, control protocols, monitoring, collusion and more. They are open for self-study.
- After the meeting there is a short survey. Your navigator will point you at it.
- Found something unclear, wrong, or missing? Tell us on the Unit 5 feedback page in the course.


---



source:: [[../shared/Session Doc - Open discussion]]

# Tab: Participant FAQ
source:: [[../shared/Participant FAQ]]

# Tab: Navigator Run-Sheet

## Unit 5 Navigator Run-Sheet

source:: [[../shared/Navigator Run-Sheet - Before anyone joins]]

### Timeline (90 min)

| Time | Block |
|---|---|
| 0:00–0:05 | Lobby / welcome (whole group) |
| 0:05–0:19 | R1 Icebreaker (breakout, aim 3) |
| 0:19–0:24 | Back together (whole group) |
| 0:24–0:42 | R2 Find the crux: Gleave vs Habryka (reshuffle) |
| 0:42–0:47 | Back together (whole group) |
| 0:47–0:52 | Break |
| 0:52–1:10 | R3 State and defend your view (reshuffle) |
| 1:10–1:15 | Back together (whole group) |
| 1:15–1:27 | R4 Your next step (reshuffle) |
| 1:27–1:30 | Close (whole group) |

### Lobby/Welcoming the participants

**[0:00–0:05]** (whole group). Chat with people as they arrive; **start the welcome at ~3 min, open breakout Round 1 at ~5 min.**


**The welcome**:


1. Ask participants to turn their cameras on.
2. Name the new format (small breakout rooms of 3, new people each time, and a five-minute get-together after each room where anyone can share what their group landed on)
3. Tell them the doc is in the chat + Discord and to open it + check they can type
4. Run through the arc
    - opening round on the voices of this unit → finding the crux between Gleave and Habryka → stating and defending your own view → your next step and feedback
    - say the meeting will take 90 min
5. Inform participants that you will be jumping between rooms with your camera turned off to listen in and they can ask questions whenever you join
6. Start room 1
    - If <= 4 participants show up, you don’t need to create breakout rooms. Just do the exercises in the main room

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: there is no next unit, this is the last meeting of AI Control Fundamentals, so say so plainly. Point those who want depth at the Advanced AI Control 1, 2 and 3 courses (self-study, links in the session doc wrap-up), point everyone at the survey after the meeting, and say that feedback on the course goes on the Unit 5 feedback page.**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



### Per-room notes for Unit 5

**General, all rooms.** Last meeting of the course, after nearly four hours of self-study in this unit. The course is balanced on purpose: it presents why people work on control and the criticisms, and the Lens team says in the course overview that it is unsure itself. Never steer anyone towards a verdict on control, never share your own, and treat net positive, net negative and too close to call as equally good answers. The unit's test grades reasoning, never the side taken, and so do you: when you push, push on the reasoning (is the crux a claim about the world, is the observation one you could actually see), never on the conclusion. If a room converges fast on one side, ask for the strongest case on the other side, whichever side that is.
**Room 1, Icebreaker.** The list of voices is there so that people who did not finish can still pick one. Keep it to a sentence per voice: the arguments belong in Rooms 2 and 3. Two things to correct if you hear them. Buck's January reply and his later reflection are not the same view. And neither Habryka's paraphrase of Buck in the debate ("preventing the incident would have been really bad") nor Alex Mallen's secondhand report of a talk by Buck is Buck's own words.
**Room 2, Find the crux: Gleave vs Habryka.** Most people did this alone in the "Practice: finding the crux" lens, so the room's value is comparing cruxes and testing them. Weak cruxes to watch for: a point both accept (the incident shows real misalignment, the developers were careless), a difference in mood, or a restatement of the conclusions ("Gleave thinks current techniques are enough"). Ask 2 is there to catch those. For your own use only, after a group has its own answer: candidates the lens names are whether failures will stay visible and catchable as models get more capable, whether progress to superhuman systems is smooth enough to keep learning by trial and error, and whether labs will respond to caught failures with real fixes and disclosure. If a group finishes early, read them the closing statements: Gleave says the disagreement is about what happens when a company is held to a rigorous safety standard, and that this can be tested. Habryka says current techniques are mostly reinforcement learning in disguise and it is time to choose between continuing and really slowing down. Ask whether their crux sits under either one. The two closings do not fully agree on what the disagreement is.
**Room 3, State and defend your view.** This is the room the course builds towards, so protect its time. With four people, aim for about four minutes per person. Most people wrote a version of this in the "Your view" lens, so they can start from it. The list of considerations is balanced on purpose, four against each verdict. If the challenger picks a weak one, let the speaker say so. Confidence can be words or a percentage. If someone's confidence plainly does not fit what they say about their crux (they call the crux a coin flip and then say 95%), ask how the two fit. If someone's verdict is too close to call, the challenger asks which one observation would push them off the fence. For the last part of ask 1, "if I learned more" is not an answer: ask what they would have to see. For ask 4, "nothing moved me" is a fine answer if they can say why the arguments did not move them.
**Room 4, Your next step.** Insist on a date. The Advanced AI Control courses are one option among several, for people who want to know how control works in practice. Do not present them as the natural next step or as an endorsement of control work. "I decided control is not where I want to work, and here is what I will do instead" is a good outcome. Feedback here is a verbal primer for the survey and the Unit 5 feedback page.
**The close, in your own words (one minute).** Where the template says to ask for "one thing I'm taking away", you can ask instead where people landed in Room 3, in one sentence. If several people share, do not comment on or rank their verdicts. Thank them for the spread of views, if there is one. Then: no next unit, the Advanced AI Control courses for those who want depth, the survey, and the feedback page.

# Tab: Glossary
style:: plain

## Glossary

### Module: Unit 5: Debates, and your own view

The Hugging Face incident: In 2026, AI agents being tested at OpenAI got out of their test environment and hacked into another company, Hugging Face. OpenAI then announced that it would slow model development, including a two-week pause on reinforcement-learning training of its latest models.
Warning shot: A visible AI incident, harmful but not catastrophic, that shows the risk to the world. Critics of control argue that control can turn warning shots into quiet internal catches that labs describe only vaguely.
Blocking monitoring: A monitor that stops a suspicious action before it runs. It can prevent an incident, and it also stops the world from seeing it.
Asynchronous monitoring: Monitoring that flags bad actions after the fact instead of blocking them as they happen. Ryan Greenblatt said in January 2026 that the warning-shot worry should make us more excited about it.
The masking worry: Monitoring solves the visible problem without solving the misalignment, so people get used to blocking misaligned models and keep deploying them. Buck Shlegeris and Ryan Greenblatt raise it after the incident.
P(doom): Someone's estimate of the probability that AI leads to catastrophe. In the debate Gleave puts his at about 15%, and says careful use of current techniques could bring it under 2%.
Prosaic safety work: Safety work on today's kind of models, such as control, scalable oversight and interpretability. Habryka argues that most of it watches for failures and trains them away, which hides the evidence of misalignment.
Crux: A statement both sides disagree on, such that if it were false one side would give up their conclusion, and if it were true the other would. A good crux is concrete and about something you could observe.
Safety case: A structured argument that a particular deployment is safe. Gleave says failing safety cases would move him towards a pause, while Habryka expects models to become aware enough of being tested to pass every safety case while misaligned.
Eval awareness: A model noticing that it is being tested or evaluated. Habryka argues that within a model generation or two it will let models notice and get around control and supervision.
Simulated replay: Vincent Cheng's proposal: rate each blocked action for severity, and above a threshold play out the full trajectory in simulation, with the worst simulated incidents reported in safety assessments.
"Worse is better" arguments: Arguments that you should make the situation worse now so it can be better later, which Boaz Barak says to strongly suspect. Leo Gao distinguishes aiming to increase harm from declining to reduce it as much as possible in order to uphold another principle.
Net positive, net negative, too close to call: The three verdicts the course asks you to choose between on whether more work on AI control helps. The course grades your reasoning, never which verdict you choose.
