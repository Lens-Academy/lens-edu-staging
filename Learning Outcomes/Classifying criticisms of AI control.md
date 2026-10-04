---
id: '702cb65b-8342-4e14-992f-bb98dddf122f'
learning-outcome: "Given a criticism of AI control, say whether it claims that control does not work (it will not stop a capable scheming model, or will stop working as models get more capable), that it works but is not worth the effort (scheming is unlikely, other failures matter more, or the work would happen anyway), or that it works and makes things worse overall. State what the criticism gets right, and give the strongest response, comparing the realistic world with control against the realistic world without it rather than against a perfect solution. Apply the same scrutiny to arguments for control by naming the weakest premise of an argument in its favour."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
requires:
  - "[[Control as a distinct safety case]]"
authors:
  - "James agent ready-34 (opus-5.5)"
---
%% Beginner sibling of "Arguments against AI control" (that file stays as it is for Advanced AI Control). Adds the third category (works and makes things worse) and the symmetric clause. Used in AI Control Fundamentals Unit 4. %%

## Test:
id:: b9135f8c-9abb-4361-91e9-047c6903b522

#### Question: Open
id:: 68cb2fd2-9462-49d3-8612-b99a93ceb9aa
content::
Here are three criticisms of AI control and one argument for it.

**Criticism A.** "Control evaluations rely on a human red team to find the ways a model could attack. A model much smarter than the red team will find attacks nobody on the team thought of. So for exactly the models that matter most, the safety figure an evaluation reports will be too high."

**Criticism B.** "Most of the danger from AI comes from companies racing each other and deploying too early, not from one model secretly plotting. An hour spent on control is an hour not spent on policy work that could slow the race."

**Criticism C.** "Once a company has monitors it trusts, it will feel safe putting more capable models to work on more tasks, sooner. So control speeds up the arrival of the very systems we cannot control."

**Argument D (for control).** "We can test control measures in experiments today, which we cannot do for most other safety approaches. So control is one of the most valuable things safety researchers can work on."

1. For each criticism, say which kind it is: control does not work, control works but is not worth the effort, or control works and makes things worse. Then say what it gets right, and give the strongest response you can, including how much of the criticism is left standing. Two to four sentences per criticism is enough.
2. For argument D, name the premise you find weakest and say why in one or two sentences.
placeholder:: Take A, B and C in turn (kind, what it gets right, strongest response, what is left), then the weakest premise in D
assessment-instructions:: Score out of 100. Criticisms A, B and C are worth 28 points each, argument D is worth 16. For each criticism: 8 for the kind, 8 for a real concession, 12 for the response with an honest statement of what is left standing.

Kinds. A says control does not work (it will not keep working, or its evaluations will overstate safety, as models outgrow the red team). B says control works but is not worth the effort (other risks matter more, opportunity cost). C says control works and makes things worse overall (it speeds up capable deployment, or gives false confidence). Accept a different kind when the answer gives a reason that fits the criticism's own words, for example that A also bears on whether control is worth doing. Give 4 of the 8 when the kind given is defensible but the reason is missing.

Concessions. Credit any true point the criticism makes that the answer then takes seriously, for example: red teams have limited imagination and a much smarter model could find unforeseen attacks (A). Racing and early deployment are a large share of the risk, and researcher time is limited (B). Making untrusted models safer to use does make them more useful and more attractive to deploy, and confidence in safeguards can outrun their real strength (C).

Responses. Credit a response that rests on a specific mechanism, for example: control is aimed at models only somewhat smarter than the best human attackers, so the criticism mainly marks where it stops applying. Red teams can be given more time, information and AI help than the model. Even an overstated evaluation is better than no measurement at all (A). Scheming is a real share of the risk that policy work does not cover. The relevant question is the marginal researcher, and many control researchers are not suited to policy work. Control results can also feed policy, for example evidence from catching a model (B). Companies would deploy these models anyway, so the realistic comparison is deployment with control against deployment without it. Control can be paired with commitments not to scale further. The same objection applies to almost any safety method that makes AI more usable (C). For full marks on a response, the answer says how much of the criticism survives. An answer that concludes a criticism is largely right gets full credit when it argues this.

Argument D, 16 points. 10 for naming a premise the argument needs: for example, that being testable makes something valuable (a measurable answer to a small part of the risk can matter less than an unmeasurable answer to a large part), that today's experiments carry over to future, more capable models, or that other approaches cannot be tested. 6 for a reason that shows why the premise is open to doubt.

Cap the total at 50 if the answer compares control with a perfect solution in all of its responses instead of with the realistic world without control. Cap at 60 if all three criticisms are put in the same kind. A pass is roughly 60.

Model answer, for the feedback, not a grading checklist: "A says control does not work for the models that matter: a smarter-than-red-team model breaks the evaluation. It is right that red teams cannot imagine every attack. But control is meant for models only somewhat beyond human attackers, red teams can use AI help and more time, and an overstated evaluation still beats none. What is left: control has an expiry date, and we may not know when we pass it. B accepts control works but says it is not worth it compared with policy work. Racing is a big part of the risk. But scheming is a risk policy does not remove, and many researchers cannot simply switch to policy. Left: a case for fewer people on control, not none. C says control makes things worse by speeding up deployment. It is right that safer-to-use models are more useful. But companies are deploying anyway, so the comparison is deployment with or without control, and control can come with commitments not to scale. Left: a real worry if the confidence is not earned. D's weakest premise: that being testable makes control valuable. A small, measurable slice of the risk can matter less than a large, unmeasurable one."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If a response compared control with a perfect solution, ask what would happen at the same companies without control. If the learner conceded nothing to a criticism, ask what that critic is right about. If the learner asks about their score, say plainly what earned and what lost points. Do not tell the learner which side is right. At most five sentences.

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
