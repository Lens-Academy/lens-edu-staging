---
title: AI Control Part 2 Unit 3 Meeting Doc
---

# Tab: Session Doc

## AI Control Part 2 Unit 3 Meeting - [Group]

### Navigator:

### Meeting link:

source:: [[../shared/Session Doc - How today works]]

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



source:: [[../shared/Session Doc - Open discussion]]

# Tab: Participant FAQ
source:: [[../shared/Participant FAQ]]

# Tab: Navigator Run-Sheet

## Unit 3 Navigator Run-Sheet

source:: [[../shared/Navigator Run-Sheet - Before anyone joins]]

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

source:: [[../shared/Navigator Run-Sheet - During the breakout rooms]]

source:: [[../shared/Navigator Run-Sheet - Zoom breakout timer]]

### Close

**[1:27–1:30], whole group**. Bring everyone back:


1. Ask for "one thing I'm taking away" from anyone who wants it (~10 sec each; a few voices is plenty, people have already shared between rooms).
2. **Next-unit heads-up: reading is Unit 4, Beyond scheming: reward seekers (the seeker archetypes, satiating cheap preferences, spillway motivations, the Apollo talk, and the guided walkthrough of the contrastive belief-update paper; five lenses, about 5 hours, the longest unit of the course); remind them to send their Room-4 plan to their accountability buddy, and that feedback goes to XLab's form (link in the session doc).**
3. **End on time.** Then say the meeting **stays open** for anyone who wants to keep talking; stay and facilitate, or say goodbye and leave (they can keep going without you).












source:: [[../shared/Navigator Run-Sheet - Navigator Pro-Tips]]



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
