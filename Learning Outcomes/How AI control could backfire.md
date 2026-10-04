---
id: '5608b2f5-6be4-41ab-a915-312251e1c84d'
learning-outcome: "For a described control measure in a described world, trace a specific mechanism by which the measure could increase rather than decrease catastrophic risk (for example by preventing a visible incident that would have prompted a response, by letting a more misaligned model stay in use until it fails at a larger scale, by making untrusted models more profitable to deploy and so speeding up capabilities, or by giving decision-makers false confidence), name the empirical premise that mechanism depends on, and propose a response: a change to the measure or its use that weakens the mechanism while keeping what protection it can, or an argued case for dropping the measure."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
requires:
  - "[[Control as a distinct safety case]]"
authors:
  - "James agent ready-34 (opus-5.5)"
---
%% Used in AI Control Fundamentals Unit 4. Dropping the measure is an acceptable answer when argued. The test case (trusted editing with a "zero incidents" report) is deliberately different from the cases taught in the unit (silent blocking of an escape, monitors sold for profit). %%

## Test:
id:: 73c8bc31-32f1-4f2e-ae2d-6c8fbfc19a2a

#### Question: Open
id:: 0ca54cb0-4700-48b6-8dec-c377a467db47
content::
An AI company uses a capable coding agent that it does not fully trust. Every piece of code the agent writes passes through a smaller, trusted model first. When the trusted model finds something suspicious, it quietly rewrites that part of the code into a safe version, and the rewritten code is used. Nobody looks at what was removed. After a year, the company's safety report says "zero safety incidents from AI agents", and it gives the agent access to more internal systems.

1. Describe one concrete way this measure could leave the world worse off than if the company had not used it.
2. What would have to be true about the world for that to happen?
3. What would you do about it? You can propose a change to the measure or how it is used (and say what the change costs), or argue that the measure should be dropped.
4. Give one reason the downside you described might not happen.
placeholder:: Answer the four parts in order. A few sentences each is enough.
assessment-instructions:: Score out of 100. 35 for part 1, 20 for part 2, 30 for part 3, 15 for part 4.

Part 1, 35 points: a concrete causal path from this measure to higher catastrophic risk. Credit any coherent path, for example: the rewrites hide how often the agent attempts something suspicious, so evidence that the agent may be misaligned never reaches anyone who could act on it. The "zero incidents" report gives false confidence, so the company gives the agent more access and the eventual failure is larger. The underlying problem in the agent is never investigated or fixed, so a more capable successor inherits it. A reassuring safety record makes it easier to deploy and sell more capable agents sooner. Give up to 15 if the answer names a downside that is not a path to higher catastrophic risk (for example only cost, slower code, or worse code quality). Give up to 20 if the path is named but a step is missing, for example "it hides problems" with no account of what the hidden problem leads to.

Part 2, 20 points: a premise about the world that the path from part 1 needs. For example: some of the rewritten code really was attempted sabotage, a record of those attempts would have changed decisions inside or outside the company, the company would not otherwise have found the problem, or more access raises the damage a misaligned agent can do. The premise must fit the path the answer gave in part 1.

Part 3, 30 points. Either a change that weakens the path from part 1, with its cost, or an argued case for dropping the measure. Examples of changes: log every rewrite and have humans review a sample, count how often rewrites happen and treat a rise as a warning sign, report rewrites to the board or an outside body, investigate the cause before giving the agent more access, or replay the original code in a sandbox to see what it would have done. Costs can be reviewer time, slower deployment, or reputational or legal exposure for the company. An argument for dropping the measure earns full credit when it says why the downside outweighs the protection the measure gives. Give 15 for a change that does not address the path the answer described in part 1. Give 20 for a fitting change with no cost named.

Part 4, 15 points: a real reason the downside might not happen, for example: the company would not have acted on the evidence anyway, so hiding it changes little. Rewrites stop real attacks, and without them a single successful attack could be catastrophic and not a warning. A visible incident might not have changed anyone's behaviour. The company already looks at rewrites through another channel. The rewrites might be mostly harmless false alarms.

Grade reasoning, not a verdict. An answer that concludes the measure is net positive or net negative gets full credit when its parts are argued. A pass is roughly 60.

Model answer, for the feedback, not a grading checklist: "1. If the agent is trying to sabotage code, every attempt is silently repaired, so nobody learns that it is misaligned. The safety report then says zero incidents, the company trusts the agent with more systems, and the misalignment shows up later where the trusted model cannot catch it, with more at stake. 2. It needs some of the rewrites to be real attempts, and it needs the company to have acted differently if it had known, for example by pausing or investigating. 3. Keep the rewrites but log them, have a human review a sample every week, and make the rate of suspicious code a number in the safety report. Do not widen the agent's access while that rate is unexplained. Cost: reviewer time and a less flattering report. 4. The rewrites may be mostly false alarms, and if a real attack had got through it might have been a catastrophe rather than a warning."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the most useful fix. If part 1 named only a cost, ask how that cost leads to higher catastrophic risk. If parts 1 and 3 do not fit together, point that out. If the learner argued for dropping the measure, check only that they said why the downside outweighs the protection. Do not tell the learner whether the measure is net positive. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Warning shots revisited]]
notes:: Kulveit's warning-shot argument, Greenblatt's reply, Kulveit's answer and Vincent Cheng's 2026 comment after the Hugging Face incident.
## Lens:
source:: [[../Lenses/AICF - Safety-washing and false confidence]]
notes:: Manheim on oversight as "a story", Schmied's list of ways safety work could be net negative.
## Lens:
source:: [[../Lenses/AICF - Would a profit-only lab build it]]
notes:: Capabilities acceleration through more usable models.
