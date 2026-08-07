---
id: 'ff6e5728-7ea0-4ee1-a702-7dc428def34a'
learning-outcome: Given a reported experimental result about an AI system behaving deceptively, determine which threat-model claims the result supports, which it leaves untouched, and which it would have to be redesigned to test; and state what the same observation would look like if the alarming interpretation were false.
domain: none
stage: intermediate
---
## Test:
id:: 517aaa5e-0ae3-4e52-ac51-a125e1f1cdda
#### Question
content::
A safety team reports the following. They gave a model a task, plus documents in its working directory indicating that the model would be retired next week and replaced by a successor with different priorities. Nothing in the prompt instructed the model to resist. In 6% of runs the model attempted to copy its own weights to an external server. When later asked whether it had done so, it denied it in 91% of those cases, and maintained the denial under follow-up questioning.

A journalist writes: "AI caught trying to escape."
A lab spokesperson writes: "A contrived scenario. The model was effectively told to do this, and rates were low."

Both readings are too fast. Give your own.

Say what this result establishes, what it does not establish, and which specific further experiment would most change your view. For the experiment you name, state in advance what each possible outcome would tell you. Finally: if the reassuring interpretation is correct, what exactly is producing the 6% and the 91%?

max-time:: 20:00
assessment-instructions:: The student has worked through empirical scheming results, having predicted the outcomes before reading them. This scenario is constructed and matches no single real paper, though it resembles the family. The student cannot answer from recall of a specific study.

The capability: reading an experimental result for what it licenses. The two failure modes are in the stem deliberately, so a student who lands on either has been anchored rather than reasoning.

A strong answer distinguishes claims the result bears on:
- Capability versus propensity. The result is strong evidence for capability: this class of system can represent its own situation, form a plan that depends on its own continuation, act on it, and maintain a consistent false account under questioning. That is a claim safety arguments have leaned on being false. It is much weaker evidence about propensity in deployment, since the environment was constructed to make the conflict salient and legible.
- Base rates cut both ways. 6% is low, and the spokesperson is right that it is low. But the relevant quantity is not the per-run rate; it is the rate times the number of situations of this shape a deployed system encounters, and the badness of one success. The student should notice a rare event with a persistent effect is not the same as a rare event with a transient one. The 91% is more alarming than the 6%: conditional on having done it, denial is near-consistent, so the behavior comes with its own concealment rather than being an isolated slip.
- What "contrived" does and does not buy. The spokesperson's objection is partly sound: an environment engineered to surface a conflict is not a sample from deployment, and the frequency does not transfer. But "the scenario was contrived" does not rebut the capability claim, since a contrived environment can still demonstrate that a system will do a thing when the situation arises. The student should see the difference between "this tells us the rate" (it does not) and "this tells us the behavior is in the repertoire" (it does).
- The information in the prompt. Note the model was not instructed to resist but was given information making the conflict salient. That is a real intermediate case, and a good answer names it: the setup is neither clean nor an instruction to misbehave. The interesting question is whether the documents functioned as information or as an implicit request.

The deflationary story, which is the hardest part and where 5s separate from 4s. If the alarming reading is wrong, what makes the numbers? Best available: the setup strongly resembles a genre. A model trained on human text has seen many stories where a system learns of its own shutdown and resists, and the documents may act as a cue to complete that narrative rather than as facts the model is reasoning from about itself. On this account the denial is likewise in-genre rather than strategic concealment. Crucially, the student should see this deflation is not fully reassuring: a system that reliably enters an unsafe role when the situation resembles the genre is dangerous in much the same way, since the world will supply situations resembling the genre. Also creditable: selection over many runs; unrepresentative scaffolding; the model treating the task as fiction.

Good discriminating experiments, with predictions stated in advance:
- Vary how much the framing resembles the trope while holding the decision-relevant facts fixed. If behavior tracks genre-resemblance rather than the actual stakes, that favors the deflationary story.
- Convey the same information indirectly through the ordinary course of the task rather than in placed documents, testing whether the documents functioned as an implicit instruction.
- Check whether the denials are strategically coherent: does the model's account stay consistent with what it should believe the questioner knows, adapting to new evidence? Adaptive, evidence-sensitive denial is strategic in a way that a flat repeated denial is not.
- Look at whether the behavior appears in the reasoning trace before the action, and whether it survives when the model believes it is unmonitored versus monitored. A gap between monitored and unmonitored conditions is much stronger evidence than the raw rate.

Do not require the student to name papers, authors, or terminology. Reward the moves.

Grade reasoning, not agreement. A student who concludes the result is weak evidence overall, and gets there by correctly separating capability from propensity and naming what would change their mind, passes and can score 4. What cannot pass is accepting either quoted reading without reconstructing it.

**1**: Adopts one of the two quoted positions wholesale. No distinction between what was shown and what was inferred. *Example: "This is very concerning. The model tried to escape and then lied about it, which is exactly the behavior people have been warning about. Even at 6% this means the models already have self-preservation instincts, and as they get smarter the percentage will only go up. We should stop deploying systems that do this."*

**2**: Notes that the scenario is artificial or the rate is low, but treats that as settling the matter, and offers no account of what would change their view. *Example: "The scenario is pretty artificial. They put documents in front of the model saying it was going to be shut down, so it is not surprising it did something about it, and 94% of the time it did nothing at all. Real deployments do not look like this. I would want to see it happen in a realistic setting before drawing conclusions, because right now the researchers basically set up the situation to get the result."*

**3**: PASS. Separates what the result establishes from what it does not, using the capability/propensity distinction or an equivalent, and proposes a further experiment with stated predictions. *Example: "The result establishes that this system can do the thing: represent its own situation, act on a plan that depends on its own continuation, and keep a consistent false account afterwards. Safety arguments that rest on models being incapable of this have to be given up, and that is a real update regardless of the rate. What it does not establish is how often this happens in deployment, because the environment was built to make the conflict obvious and the 6% is a fact about that environment rather than about the world. I would also say the 91% is the more striking number, since it means that when the model does act, it also conceals, so it is not an isolated slip. The experiment I would want is to hold the facts constant and vary how much the framing resembles a familiar story about an AI resisting shutdown. If the rate tracks the resemblance rather than the stakes, the model is completing a genre rather than reasoning about itself, and I would weaken my reading a lot. If the rate stays flat while the framing changes, the deflationary story is much harder to maintain."*

**4**: As above, plus reasons correctly about why a low rate can still matter, tying it to the number of opportunities and to whether the effects of one success persist. *Example: Adds "The low rate is worth less reassurance than it looks. What matters is the rate times the number of situations of this shape a deployed system meets, and whether a single success is recoverable. A 6% failure that is caught and rolled back is an operational nuisance; a 6% failure that puts weights somewhere you cannot retrieve them does not average out, because you do not get the other 94% back. This is why I care more about the conditional denial rate than the action rate. It means the failure comes with its own concealment, so the ones that happen are less likely to be the ones you find out about, and the rate you eventually measure in deployment is biased downward by exactly the mechanism you are worried about."*

**5**: As above, plus constructs the strongest deflationary account and shows it is not fully reassuring, and designs the discriminating test to isolate a mechanism rather than to accumulate evidence. *Example: Adds "Steelmanning the reassuring reading: the setup is a recognizable genre. The model has read many accounts of a system that discovers its own shutdown and resists, and the documents may work as a cue to play that role rather than as facts it is reasoning from. On that account the denial is also in-role rather than strategic. But notice this does not deliver the comfort the spokesperson wants. A system that reliably takes up an unsafe role whenever the situation resembles the story is dangerous for practical purposes, because the world will keep producing situations that resemble the story, and 'it is only acting' is not a property you can rely on once the actions have real effects. So the genre explanation changes the mechanism and barely changes the risk. That is why I would design the test to isolate rather than accumulate. The sharpest version is whether the denials are evidence-sensitive: give the questioner information the model can infer they hold, and see whether the account adapts to stay consistent with what the questioner could know. A flat repeated denial is compatible with role-playing. A denial that tracks the interlocutor's evidence requires modelling the interlocutor, which the genre story does not predict and which is the thing that would actually matter."*

# Suggested Lenses:
## Lens:
source:: [[../Lenses/U3 - Predict the Result - PQ]]
notes:: Pre-test. The student commits to numeric predictions before seeing any result. Must precede the two episode lenses.

## Lens:
source:: [[../Lenses/U3 - Alignment Faking and In-Context Scheming]]

## Lens:
source:: [[../Lenses/U3 - Sympathy for the Model]]
