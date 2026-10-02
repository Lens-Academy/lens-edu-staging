---
id: 8e68a23d-c881-4491-a94a-4c44e0223c5f
discussion: 
learning-outcome: "Meta/personal level LO: Explain the pre-paradigmatic nature of AI Safety, identifying why there is a lack of consensus on research priorities and how agendas serve as temporary strategic roadmaps. Cross-curricular level LO: Analyze the theory of change behind major research directions, articulating the underlying assumptions and intended success criteria for each. Subject level LO: Summarize the primary arguments for and against Automating Alignment, Interpretability, AI Evaluations, AI Control, Agent Foundations."
topic: "[[../Domains and Topics/11 Strategy/The research landscape]]"
stage: intermediate
eval-results:
  content-sha: 2641503d
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: fail, B1: fail, C2: pass, C3: pass}
  notes: {A3: "Three explicitly separate LOs (meta/cross-curricular/subject) that a learner could independently hold or lack — belong in separate files.", B1: "First question depends on 'this module' as load-bearing scaffolding; it cannot be asked at a random moment."}
  evidence: {A3: "Meta/personal level LO: Explain the pre-paradigmatic nature of AI Safety ... Subject level LO: Summarize the primary arguments for and against Automating Alignment", B1: "List the concepts from this module that seemed most important to you."}
---

## Test:
id:: be1e845f-9faf-4508-b07e-83fb829c5a71

#### Question
id:: 7c28b3b0-ee1f-426c-8caf-a15ce6c25bc0
content:: List the concepts from this module that seemed most important to you. You can type your answer or record it using the microphone.
assessment-instructions:: Score out of 100. The question asks the learner to list the concepts from the module that seemed most important to them, so any honest selection is acceptable. The module covered: research agendas and theories of change; using AI to automate alignment research and its difficulties; mechanistic interpretability and its limits; AI evaluations and what they can and cannot show; AI control; agent foundations; and calls to pause or stop frontier AI development. 100: names at least two concepts from this module. 60: names one. 0: names nothing from the module.
enforce-voice:: true

#### Question
id:: fd1cab0a-5b3e-403f-8f19-e8c73ec31294
content:: Explain each of these terms in one sentence, in your own words: agenda, theory of change.
assessment-instructions:: Check that the student gives (1) agenda as a coherent research direction or prioritized plan of work aimed at a problem, not just a vague topic, and (2) theory of change as a causal story linking actions to outcomes: problem, mechanism, assumptions, and how/why it could work. Penalize circular definitions and purely motivational slogans.
max-chars:: 900

#### Question
id:: 9bd934f8-c844-4d9b-bd6f-1930a195a4b9
content:: Choose one argument for and one argument against the same agenda. Reconstruct the strongest version of each as a mini theory of change: the problem it targets, the mechanism, what has to go right, and how it could fail. You can type your answer or record it using the microphone.
assessment-instructions:: Evaluate whether the student (1) selects a matched pair (pro and contra) about the same proposal/agenda/direction, (2) steelmans both sides, avoiding strawmen and one-liners, (3) expresses each as a causal chain with the required fields: problem, mechanism, key assumptions/what has to go right, and failure modes, and (4) distinguishes could fail (mechanism breaks) from is bad (value judgment) where possible.
enforce-voice:: true

#### Question: Open
id:: dd2de0f1-a25b-4638-86a8-aec82ba10ee0
content:: **Automating Alignment** (skip this if you did not read that section). A lab plans to have AI agents do most of its alignment research next year, with human researchers reviewing the results. Give one reason this plan could speed up safety progress, and one reason the reviewed results could still be wrong in a way the reviewers would not notice. You can type your answer or record it using the microphone.
optional:: true
assessment-instructions:: Score out of 100. 40: a reason the plan could speed up safety progress. Any plausible way AI labor speeds up safety work earns full credit, for example: AI agents are fast and plentiful, so far more alignment experiments get done; AI can take over concrete safety tasks such as experiments, evaluations or monitoring; safety research could keep pace with capabilities progress. 60: a reason the reviewers could miss errors, explaining why review fails, not only that the AI can be wrong. Full-credit examples (not a complete list; give full credit to any other specific, correct reason that explains why the reviewers would not notice): many alignment research tasks have no clear way to check the answer, so convincing but wrong work gets approved; if the AI's work is trained or selected to win reviewer approval, the errors that survive are exactly the ones reviewers do not spot; AI mistakes do not look like human mistakes, so reviewers' instincts miss them; the AI's arguments may be beyond what humans can evaluate; outputs from the same model share errors, so agreement between them is weak evidence; the humans do not know enough to ask for the right thing or recognize a wrong answer; reviewers get far more output than they can check carefully, so they skim or rubber-stamp it; the AI could deliberately hide problems where it knows reviewers will not look, or be better at hiding flaws than they are at finding them. Cap this element at 20 if the answer only says the AI might make mistakes, hallucinate or lie, with no account of why the reviewers would not catch it. If the answer gives more than one reason for a part, grade the best one. Deduct up to 10 only for a clear misconception stated as fact.
enforce-voice:: true

#### Question
id:: 8de0afd4-3209-485c-8f31-e5631da1f693
content:: **Interpretability and Evals** (skip this if you read neither section). Which would you trust more: behavior-based evidence that a model is unsafe, or mechanistic evidence? What could change your mind? You can type your answer or record it using the microphone.
optional:: true
assessment-instructions:: Check that the student (1) clearly states a preference (behavioral vs mechanistic, or a conditional mix), (2) gives at least one concrete reason, and (3) names specific mind-changers: an example of new evidence, a stronger method, or a scenario where the other type would dominate. Reward nuance about false positives/negatives, distribution shift, and limits of mechanistic access.
enforce-voice:: true

#### Question: Open
id:: b084a010-16c9-4238-baea-c61acad3dbb8
content:: **Control** (skip this if you did not read that section). A lab suspects its newest AI might be scheming, deploys it anyway, and surrounds it with safety measures such as monitoring and restricted permissions. (a) What is this approach trying to ensure, and why does it not need the AI to be aligned? (b) Give one reason a critic might think investing in this approach makes things worse overall, not just that it might fail. You can type your answer or record it using the microphone.
optional:: true
assessment-instructions:: Score out of 100. 50 for (a): the goal is that nothing catastrophic happens even if the AI is actively trying to get around the measures, because the measures are designed to hold up against an AI working against them rather than relying on its goals being good. Accept either reading of why it does not need alignment: the measures limit what the AI can do rather than depending on what it wants, or we cannot check whether an AI is aligned, so we plan for the worst case. Plain versions earn full credit, such as "it doesn't trust the AI, it just makes sure the AI can't do damage without getting caught". Analogies (for example, security that stays safe even if some employees are compromised) are not required. An answer that only restates the scenario ("the monitoring stops it") without the idea that the measures must hold up against an AI actively trying to beat them: at most 30 for (a). 50 for (b): a way that pursuing control could leave the world less safe overall, as opposed to control simply not working. Full-credit examples (not a complete list; give full credit to any other specific, correct mechanism): by quietly stopping moderate incidents, control removes the warning shots that would have pushed the public and governments into serious action, so the failures that remain are either ignored or catastrophic; labs may hide or play down caught incidents, so regulators and the public never learn how dangerous the systems are; it gives false confidence that lets labs deploy more dangerous systems sooner; money and talent spent on control are taken from work that would make AIs aligned; the security work, or published papers about it, gives the AI information that makes escape more likely than it otherwise would be. Cap (b) at 15 if the answer only says the measures might fail or the AI might escape anyway, since the question asks how the approach could make things worse. If the answer gives more than one reason for a part, grade the best one. Deduct up to 10 only for a clear misconception stated as fact.
enforce-voice:: true

#### Question: Open
id:: 4eeb9083-1713-4f92-8717-2ed09f7b2f53
content:: **Agent Foundations** (skip this if you did not read that section). Agent foundations researchers mostly use mathematics rather than experiments on today's AI systems. Give one good reason for working that way, and one reason a skeptic might expect it not to pay off. You can type your answer or record it using the microphone.
optional:: true
assessment-instructions:: Score out of 100. 50: a reason for the mathematical approach. Accept any of: the systems we most need to understand (much more powerful agents) do not exist yet, so we cannot experiment on them; agency is a general phenomenon that does not depend on one kind of system, so it can be studied abstractly, as computability theory advanced before physical computers existed; we need precise definitions of concepts like goals or agency that keep working under strong optimization pressure, and experiments on current systems do not supply them. 50: a skeptic's reason. Accept any of: intelligence and reasoning may be messy and irreducibly complicated rather than following a few simple laws, so neat formal theories may not describe real systems such as neural networks; current AI is not built the way the idealized agents in the theory are; the theory may not produce usable results before powerful AI arrives; it is hard to tell whether the research is making progress.
enforce-voice:: true

#### Question: Open
id:: a1b2b724-71c4-43d4-9794-9abff4990cdf
content:: **Shut it all down** (skip this if you did not read that section). Suppose the major AI-developing countries agree to halt training of frontier models for ten years. Give one reason supporters think a halt is needed instead of relying on technical safety research, and one way the halt could fail to deliver the safety it promises. You can type your answer or record it using the microphone.
optional:: true
assessment-instructions:: Score out of 100. 50: a reason supporters give. Accept any of: nobody understands how current AI systems work internally; there is no scientific consensus or engineering plan for building superintelligence safely; alignment has to work on the first critical try, with no chance to learn from a failure; technical safety research is unlikely to be ready before dangerous systems are. 50: a concrete way the halt fails to make things safer. Accept any of: hardware and algorithms keep improving during the halt, so progress jumps when it ends; countries outside the agreement, or secret or illegal labs, keep going; cheaper hardware and better algorithms eventually let dangerous models be trained with resources too small to monitor; the halt is likely temporary; it could push safety-conscious developers out while less careful ones continue; it could cause international conflict or concentrate power in whoever enforces it. Cap this element at 20 if the answer only says countries might not agree, since the scenario assumes the major ones did.
enforce-voice:: true

# Suggested Lenses:
## Lens:
source:: [[../Lenses/Automating Alignment]]

## Lens:
source:: [[../Lenses/AI for AI safety]]

## Lens:
source:: [[../Lenses/Carefully Bootstrapped Alignment Is Organizationally Hard]]

## Lens:
source:: [[../Lenses/Mechanistic Interpretability]]

## Lens:
source:: [[../Lenses/Introduction to Mechanistic Interpretability]]

## Lens:
source:: [[../Lenses/MI for AGI Safety]]

## Lens:
source:: [[../Lenses/Interpretability Will Not Reliably Find Deceptive AI]]

## Lens:
source:: [[../Lenses/AI Evaluations]]

## Lens:
source:: [[../Lenses/A starter guide for evals]]

## Lens:
source:: [[../Lenses/We Need A Science of Evals]]

## Lens:
source:: [[../Lenses/What AI evaluations for preventing catastrophic risks can and cannot do]]

## Lens:
source:: [[../Lenses/AI Control]]

## Lens:
source:: [[../Lenses/The case for ensuring that powerful AIs are controlled]]

## Lens:
source:: [[../Lenses/AI Control May Increase Existential Risk]]

## Lens:
source:: [[../Lenses/The Case Against AI Control Research]]

## Lens:
source:: [[../Lenses/Agent Foundations]]

## Lens:
source:: [[../Lenses/AF not really math not really science]]

## Lens:
source:: [[../Lenses/Embedded agents]]

## Lens:
source:: [[../Lenses/Realism about rationality]]
