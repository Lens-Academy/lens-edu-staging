---
id: '5608b2f5-6be4-41ab-a915-312251e1c84d'
learning-outcome: "For a described control measure in a described world, trace a specific mechanism by which the measure could make a catastrophe more likely rather than less (for example by preventing a visible incident that would have prompted a response, by letting a more misaligned model stay in use until it fails at a larger scale, by making untrusted models more profitable to deploy and so speeding up capabilities, or by giving decision-makers false confidence), name the empirical premise that mechanism depends on and a reason it might not hold, and propose a response: a change to the measure or its use that weakens the mechanism, with what it keeps and what it costs, an argued case for dropping the measure, or an argued case that no change is needed."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - "James agent ready-34 (opus-5.5)"
---
%% Used in AI Control Fundamentals Unit 4. Dropping the measure is an acceptable answer when argued. The test case (trusted editing at a company that sells its agent and trains a successor) is deliberately different from the cases taught in the unit (silent blocking of an escape, monitors sold for profit). %%

## Test:
id:: 73c8bc31-32f1-4f2e-ae2d-6c8fbfc19a2a

#### Question: Open
id:: 0ca54cb0-4700-48b6-8dec-c377a467db47
content::
An AI company uses a capable coding agent that it does not fully trust. Every piece of code the agent writes passes through a smaller, trusted model first. When the trusted model finds something suspicious, it rewrites that part of the code into a safe version, and the rewritten code is used. Over a year, the trusted model rewrote about 300 pieces of code. The company publishes a yearly safety report, sells the agent to other companies, and is training a more capable successor on similar tasks.

1. Describe one concrete way this measure could make a catastrophe more likely than if the company had not used it.
2. What would have to be true about the world for that to happen? Give one reason it might not be true.
3. What would you do about it? You can propose a change to the measure or how it is used, and say what protection the change keeps and what it costs. Or you can argue that the measure should be dropped, or that it should stay as it is. Either way, weigh the downside against what acting would cost or lose.
placeholder:: Answer the three parts in order. A few sentences each is enough.
assessment-instructions:: Score out of 100. 40 for part 1, 30 for part 2, 30 for part 3.

Part 1, 40 points: a concrete causal path from this measure to a higher chance of catastrophe, with at least one step the scenario does not state. Credit any coherent path, for example: if the original code is not kept or reviewed, nobody who could act learns what the agent attempted or that it may be misaligned, and the company keeps scaling it or its successor. A clean safety report gives false confidence to the company, its customers or regulators, so the agent is trusted with more and a later failure is larger. The cause of the suspicious code is never investigated, so the successor inherits it. Making the agent safe enough to sell spreads it to more companies or speeds up a more capable successor. Credit an answer that locates the backfire in how the measure's output is used rather than in the measure itself. Give at most 20 to a path that would apply unchanged to any safety measure and runs through no feature of this case (silent rewriting, the rewrite count, the safety report, selling the agent, or the successor). Give up to 20 if a path is named but a step is missing, for example "it hides problems" with no account of what that leads to. Give up to 10 if the downside is not a path to catastrophe (for example only cost or code quality).

Part 2, 30 points: 18 for a premise about this case that the path from part 1 needs, for example: some of the rewritten code was attempted sabotage, a record of it would have changed decisions inside or outside the company, the company would not otherwise have found the problem, or customers and regulators rely on the report. Give 8 if the premise is plausible but does not fit the path the answer gave, or would fit any safety measure. 12 for a reason that premise might not hold, for example: the rewrites are mostly false alarms, the company would not have acted on the evidence anyway, or, for a path that relies on a warning shot, without rewrites a single real attack could have been catastrophic rather than a warning. Give 5 for a generic reason not tied to this case ("it might be fine").

Part 3, 30 points. A change: 20 for a change that weakens the path from part 1 (for example log every rewrite and have humans review a sample, report the rewrite rate in the safety report or to an outside body, investigate the cause before training or selling more, replay the original code in a sandbox to see what it would have done), 5 for saying what protection it keeps and 5 for what it costs (reviewer time, slower deployment, a less flattering report, legal or reputational exposure). Give 10 of the 20 for a change that does not address the path from part 1. Or dropping the measure: 30 when the answer says why the downside outweighs the protection the measure gives, 15 if it drops the measure without weighing what is lost. Or keeping it unchanged: 30 when the answer weighs how strong the mechanism is against the cost of acting, 15 if it only asserts that no change is needed. For dropping or keeping, give 30 only when the weighing uses a feature of this case, and at most 15 otherwise.

Cap the total at 45 if part 1 gives no path to a higher chance of catastrophe. Grade reasoning, not a verdict. An answer that concludes the measure is net positive or net negative gets full credit when its parts are argued.

Model answer, for the feedback, not a grading checklist: "1. If the agent is trying to sabotage code, each attempt is repaired and nobody looks at what was attempted, so nobody learns that it is misaligned. The safety report shows no incidents, customers deploy it more widely, and the successor is trained on the same tasks without anyone asking why the agent writes suspicious code. The misalignment then shows up in a more capable model, where it may not be caught. 2. This needs some of the rewrites to be real attempts, and someone to have acted differently had they known. It might not hold if the rewrites are mostly false alarms. 3. Keep the rewrites but log them, have a human review a sample every week, and put the rate in the safety report. Do not train the successor on these tasks while the rate is unexplained. This keeps the protection against bad code getting through. Cost: reviewer time and a less flattering report."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the most useful fix. If part 1 named only a cost, ask how that cost leads to a catastrophe. If parts 1 and 3 do not fit together, point that out. If the learner argued for dropping the measure, check only that they said why the downside outweighs the protection. If the learner asks about their score, explain plainly what earned and lost points, without changing or reopening it. Do not tell the learner whether the measure is net positive. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Warning shots revisited]]
notes:: Kulveit's warning-shot argument, Greenblatt's reply, Kulveit's answer and Vincent Cheng's 2026 comment after the Hugging Face incident. Its second question is the practice item for this outcome.
## Lens:
source:: [[../Lenses/AICF - Safety-washing and false confidence]]
notes:: Manheim on oversight as "a story", Schmied's list of ways safety work could be net negative.
## Lens:
source:: [[../Lenses/AICF - Would a profit-only lab build it]]
notes:: Capabilities acceleration through more usable models (Habryka, Cale), with replies (Hobbhahn, Mallen, Oesterheld).
## Lens:
source:: [[../Lenses/AICF - Does control breed better schemers]]
notes:: Training against caught behaviour as a backfire path.
## Lens:
source:: [[../Lenses/AICF - Does control make AIs adversarial]]
notes:: Self-fulfilling misalignment: a fine-tuning study on control writing and a larger pretraining study on AI writing in general, with a fix (adding data about AIs behaving well).
