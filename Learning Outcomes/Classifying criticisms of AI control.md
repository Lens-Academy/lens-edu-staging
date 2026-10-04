---
id: '702cb65b-8342-4e14-992f-bb98dddf122f'
learning-outcome: "Evaluate an argument about AI control with the same rigour whichever side it is on. For a criticism of control, say whether it claims that control does not work (it will not stop a capable scheming model, or will stop working as models get more capable), that it works but is not worth the effort (scheming is unlikely, other failures matter more, or the work would happen anyway), or that it works and makes things worse overall, state what the criticism gets right, and give the strongest response, comparing the realistic world with control against the realistic world without it rather than against a perfect solution. For an argument in favour of control, name the premise most open to doubt and say why."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
tags:
  - wip
authors:
  - "James agent ready-34 (opus-5.5)"
---
%% Beginner sibling of "Arguments against AI control" (that file stays as it is for Advanced AI Control). Adds the third category (works and makes things worse) and the symmetric clause. Used in AI Control Fundamentals Unit 4. Remove the wip tag once reviewed. %%

## Test:
id:: b9135f8c-9abb-4361-91e9-047c6903b522

#### Question: Open
id:: 68cb2fd2-9462-49d3-8612-b99a93ceb9aa
content::
Here are three criticisms of AI control and one argument for it. A criticism can be of any kind, and two criticisms can be of the same kind.

**Criticism A.** "Once a company has monitors it trusts, it will feel safe putting more capable models to work on more tasks, sooner. So control speeds up the arrival of the very systems we cannot control."

**Criticism B.** "Control evaluations rely on a human red team to find the ways a model could attack. A model much smarter than the red team will find attacks nobody on the team thought of. So for exactly the models that matter most, the safety figure an evaluation reports will be too high."

**Criticism C.** "Most of the danger from AI comes from companies racing each other and deploying too early, not from one model secretly plotting. An hour spent on control is an hour not spent on policy work that could slow the race."

**Argument D (for control).** "We can test control measures in experiments today, which we cannot do for most other safety approaches. So control is one of the most valuable things safety researchers can work on."

1. For each criticism, say which kind it is (control does not work, control works but is not worth the effort, or control works and makes things worse) and why. Then say what it gets right, and give the strongest response you can. Judge control against what would realistically happen without it, not against a perfect solution, and say how much of the criticism is left standing. Two to four sentences per criticism is enough.
2. For argument D, name the premise you find weakest and say why in one or two sentences.
placeholder:: Take A, B and C in turn (kind and why, what it gets right, strongest response, what is left), then the weakest premise in D
assessment-instructions:: Score out of 100. Criticisms A, B and C are worth 28 points each, argument D is worth 16. For each criticism: 8 for the kind with a reason, 8 for a concession, 12 for the response.

Kinds, 8 each. A says control works and makes things worse overall (it speeds up capable deployment, or gives false confidence). B says control does not work (it will not keep working, or its evaluations will overstate safety, as models outgrow the red team). C says control works but is not worth the effort (other risks matter more, opportunity cost). Give 8 for the expected kind with a reason that fits the criticism's words. Give 8 for a different kind when the reason given fits the criticism's own words, for example that B also bears on whether control is worth doing. Give 4 for the expected kind with no reason or a reason that does not fit.

Concessions, 8 each: a true point the criticism makes that the answer then takes seriously, for example: making untrusted models safer to use does make them more useful and more attractive to deploy, and confidence in safeguards can outrun their real strength (A). Red teams cannot imagine every attack, and a much smarter model could find unforeseen ones (B). Racing and early deployment are a large share of the risk, and researcher time is limited (C). Give 4 if the concession only repeats the criticism's claim without saying where or when it holds.

Responses, 12 each: 8 for a reply resting on a specific mechanism, 4 for saying how much of the criticism survives. Examples of mechanisms: companies are likely to deploy these models in any case, so the question is how much sooner control makes it, control can be paired with commitments not to scale further, and the same objection applies to almost any safety method that makes AI more usable (A). Control is aimed at early transformatively useful models, not arbitrarily capable ones, so the criticism marks where it stops applying, red teams can be given more time and information than the model, and an evaluation whose limits are known is still informative (B). Scheming is a share of the risk that policy work does not remove, what matters is the marginal researcher and how neglected each area is, and control results such as evidence from catching a model can feed policy (C). Credit other mechanisms that hold up. An answer that concludes a criticism is largely right gets full credit when it argues this, including by arguing that the realistic comparison still favours the criticism.

Argument D, 16 points: 10 for naming a premise the argument needs, for example that being testable makes something valuable (a measurable answer to a small part of the risk can matter less than an unmeasurable answer to a large part), that today's experiments carry over to future, more capable models, or that other approaches cannot be tested. 6 for a reason that shows why the premise is open to doubt.

Cap the total at 50 if every response judges control against a perfect solution (for example only "control offers no guarantee") and never against what would realistically happen without it. Cap the total at 70 if part 2 is missing or names no premise the argument needs.

Model answer, for the feedback, not a grading checklist: "A says control makes things worse by speeding up deployment, because trusted monitors make companies comfortable using more capable models sooner. It is right that safer-to-use models are more useful. But companies are deploying anyway, so the comparison is deployment with or without control, and control can come with commitments not to scale. Left: a real worry if the confidence is not earned. B says control does not work for the models that matter, because a smarter-than-red-team model breaks the evaluation. It is right that red teams cannot imagine every attack. But control is meant for early transformatively useful models, and an evaluation whose limits are known still tells you something. Left: control has an expiry date, and we may not know when we pass it. C accepts control works but says it is not worth it compared with policy work. Racing is a big part of the risk. But scheming is a risk policy does not remove, and the question is where the next researcher does most good. Left: a case for fewer people on control, not none. D's weakest premise: that being testable makes control valuable. A small, measurable slice of the risk can matter less than a large, unmeasurable one."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If a response compared control with a perfect solution, ask what would happen at the same companies without control. If the learner conceded nothing to a criticism, ask what that critic is right about. If the learner asks about their score, say plainly what earned and what lost points, without changing or reopening it. Do not tell the learner which side is right. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Slop, not scheming]]
notes:: Wentworth's "wrong threat model" criticism (works but not worth it), Buck Shlegeris's reply, and Lucius Bushnaq's acceleration point (makes things worse) with Buck's answer.
## Lens:
source:: [[../Lenses/AICF - Would a profit-only lab build it]]
notes:: The neglectedness criticism (Yonatan Cale) and its replies (Marius Hobbhahn, Alex Mallen).
## Lens:
source:: [[../Lenses/AICF - Does control breed better schemers]]
notes:: "Does not work" criticisms: Jozdien on capability evaluations and selection pressure, Habryka's list with Greenblatt's replies.
## Lens:
source:: [[../Lenses/AICF - Safety-washing and false confidence]]
notes:: The false-confidence case of the "makes things worse" kind.
