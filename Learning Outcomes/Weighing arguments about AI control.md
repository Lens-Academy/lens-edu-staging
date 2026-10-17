---
id: '702cb65b-8342-4e14-992f-bb98dddf122f'
writing_minutes: 15
learning-outcome: "Evaluate an argument about AI control with the same rigour whichever side it is on. For a criticism of control, state what the criticism gets right, and give the strongest response to the point it disputes, comparing the realistic world with control against the realistic world without it rather than against a perfect solution. For an argument in favour of control, name the premise most open to doubt and say why."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - Elias+Claude
---
%% Beginner sibling of "Arguments against AI control" (that file stays as it is for Advanced AI Control). Since 2026-10-16 (Elias) it no longer asks which kind a criticism is: understanding each criticism matters more than naming its type. Used in AI Control Fundamentals Unit 4. %%

## Test:
id:: b9135f8c-9abb-4361-91e9-047c6903b522

#### Question: Open
id:: 68cb2fd2-9462-49d3-8612-b99a93ceb9aa
content::
Here are three criticisms of AI control and one argument for it.

**Criticism A.** "Control means building systems that record everything AI agents do and monitors that read those records. Once that machinery exists, governments and companies will use it to watch people too. Control builds the tools for a surveillance state, and concentrated power of that kind makes a catastrophe more likely."

**Criticism B.** "Control evaluations rely on a human red team to find the ways a model could attack. A model much smarter than the red team will find attacks nobody on the team thought of. So for exactly the models that matter most, the safety figure an evaluation reports will be too high."

**Criticism C.** "Most of the danger from AI comes from companies racing each other and deploying too early, not from one model secretly plotting. An hour spent on control is an hour not spent on policy work that could slow the race."

**Argument D (for control).** "We can test control measures in experiments today, which we cannot do for most other safety approaches. So control is one of the most valuable things safety researchers can work on."

1. For each criticism, name one thing it gets right, give the strongest response you can to the point it disputes, and say what would realistically happen without control in this case and how much of the criticism is left standing compared with that (not compared with a perfect solution). If you think a criticism is largely right, say so, and say why the strongest response to it fails. Three to five sentences per criticism is enough.
2. For argument D, name the premise you find weakest, say why it is open to doubt, and say how much of the argument is left standing and why. Three to five sentences.
3. Somewhere in your answer, use at least one specific idea, argument or example from this unit's readings.
placeholder:: Take A, B and C in turn (one thing it gets right, strongest response, what is left compared with the realistic world without control), then D (weakest premise, why, what is left and why)
assessment-instructions:: Score out of 100. Criticisms A, B and C are worth 22 points each (66 in total), argument D is worth 26, and using an idea from the readings is worth 8. For each criticism: 6 for a concession, 10 for the response, 6 for what is left standing.

Concessions, 6 each: a true point the criticism makes, for example: records of everything agents do, and monitors that read them, could be repurposed to watch people, and tools built for one purpose often spread to others (A). Red teams cannot imagine every attack, and a much smarter model could find unforeseen ones (B). Racing and early deployment are a large share of the risk, and researcher time is limited (C). Give 2 if the concession is generic (it only says the criticism has a point, or would fit any criticism).

Responses, 10 each: a reply that engages the point this criticism disputes with a concrete reason. Give 3 for a generic reply that would fit any criticism. If the learner argues that the criticism largely stands, the 10 go to the strongest reply they considered and why it fails, and an answer that names no reply at all gets 0 of these 10. Examples of replies: the monitors watch AI agents inside a company, and access to the records can be restricted and audited, companies already log what their agents do for reliability, so the surveillance risk exists with or without control, and the risk comes from who controls the data, which governance can address (A). Control is aimed at early transformatively useful models, not arbitrarily capable ones, so the criticism marks where it stops applying, red teams can be given more time and information than the model, and an evaluation whose limits are known is still informative (B). Scheming is a share of the risk that policy work alone does not remove, what matters is the marginal researcher and how neglected each area is, and control results such as evidence from catching a model can feed policy (C). Credit other replies that hold up.

Left standing, 6 each: how much of the criticism survives, comparing with something specific about what would realistically happen without control in this case (for example: companies would log their agents anyway, there would be no safety figure at all, the hours would go to policy instead). A conclusion that the criticism largely stands gets the full 6 when it rests on such a comparison. Give 2 for a stock comparison that names nothing specific, and 0 if the answer judges control only against a perfect solution, for example only "control offers no guarantee".

Argument D, 26 points: 10 for naming a premise the argument needs, for example that being testable makes something valuable (a measurable answer to a small part of the risk can matter less than an unmeasurable answer to a large part), that today's experiments carry over to future, more capable models, or that other approaches cannot be tested. 8 for a reason that shows why that premise is open to doubt, 3 if the reason is generic. 8 for saying how much of the argument is left standing, for example that testability is still an advantage but does not by itself make control "one of the most valuable things", 2 if this is only asserted.

Readings, 8: the answer uses, anywhere, a specific idea, argument or example from the unit's readings and applies it to the point at hand. Ideas from the readings include: retraining or rolling back after a catch selects for models that evade the controls (Jozdien), control is meant for the first AIs capable of substantially reducing risk from later AIs, not for arbitrarily powerful ones (Greenblatt and Shlegeris), the likeliest failure is early AI producing alignment work that looks right and is not (Wentworth), any research widens the options and what matters is which safety and usefulness point developers choose (Mallen), a catch inside a company may never reach the public who could act (Kulveit), safety monitors may mostly make AI reliable enough to sell (Cale). Credit other specific ideas from AI control writing. Give 3 if the idea is mentioned but not applied to the criticism or argument.

Model answer, for the feedback, not a grading checklist: "A: it is right that records and monitors can be repurposed. But these monitors watch AI agents inside a company, companies log their agents' actions for reliability anyway, so without control much of the same data would exist, and access to it can be restricted and audited. Left: a real governance question about who controls the records. B: it is right that red teams cannot imagine every attack. The reply is that control is meant only for early transformatively useful models, but that needs a way to tell when we have left that range. Left: a lot. Without control evaluations there would be no safety figure at all, but a figure that may be too high exactly when it matters can do harm if people trust it. C: racing is a big part of the risk. The strongest reply is that scheming is a risk policy work alone does not remove, but that only shows control deserves some effort, not how much. Left: if racing is most of the risk and policy work is more neglected, this is a strong case for moving people from control to policy. D's weakest premise is that being testable makes control valuable. A small, measurable slice of the risk can matter less than a large, unmeasurable one. Left: testability is a real advantage, because it lets us check whether control works, but it does not show that control is one of the most valuable things to work on."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If a response compared control with a perfect solution, or made no comparison, ask what would happen at the same companies without control. If the learner conceded nothing to a criticism, ask what that critic is right about. If the learner rebutted every criticism, or found no doubt in argument D, ask whether they applied the same scrutiny to both sides. If the answer used no idea from the unit's readings, name one that fits their weakest part. If the learner asks about their score, say plainly what earned and what lost points, without changing or reopening it. Do not tell the learner which side is right. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Slop, not scheming]]
notes:: Control guards against the wrong danger: Wentworth's slop criticism and Buck Shlegeris's reply.
## Lens:
source:: [[../Lenses/AICF - What about superintelligence]]
notes:: Control will not work for the AIs that matter most: Redwood and a UK AISI co-authored paper agree on the limit, MIRI concludes the effort should go to halting.
## Lens:
source:: [[../Lenses/AICF - Do control protocols hold up]]
notes:: Adaptive attacks on monitors and attack selection lower measured safety (Terekhov et al., Ge-Wang et al.), with the authors' own fix. Closest reading for Test Criticism B.
## Lens:
source:: [[../Lenses/AICF - Does control breed better schemers]]
notes:: Catching and retraining breeds better schemers: Habryka and Greenblatt on training against caught behaviour, Jozdien on selection pressure.
## Lens:
source:: [[../Lenses/AICF - Does safety work speed AI up]]
notes:: The general speed-up worry (Richard Ngo).
## Lens:
source:: [[../Lenses/AICF - How control could speed AI up]]
notes:: Speed-up version aimed at control (Bushnaq; Habryka in an optional box) and Buck's answer, worked out by Mallen.
## Lens:
source:: [[../Lenses/AICF - Would a profit-only lab build it]]
notes:: Speed-up through AI that is easier to sell: could a profit-only company's capabilities team build it (Cale), with Hobbhahn's reply. No reading covers Test Criticism A's surveillance point directly; the test introduces it.
