---
id: '4e511e35-3219-4b88-9250-f38efcd2d20c'
learning-outcome: "Given a theoretical impossibility result about control or verification (such as the law of requisite variety or the undecidability of checking arbitrary programs), state what it actually rules out for controlling an AI system, identify the extra assumptions an argument needs to get from the result to 'AI cannot be controlled', and distinguish the impossibility of perfect, fully general control from the impossibility of adequate control in a specific setting."
topic: "[[../Domains and Topics/3 Alignment/Corrigibility and limited optimization]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Control (in the technical sense) and its limits. AFFINE prerequisites: Alignment's Many Meanings. Not yet copied into requires:. The only AFFINE reading is a talk video that could not be fetched when this was drafted; the outcome follows the talk's framing ('theoretical limits to control: do any of them actually tell us anything?') and standard results. Check against the talk. %%
## Test:
id:: c33d75d2-0e8d-4944-99e8-559d8044dd48

#### Question: Open
id:: 3b40eb2c-4ec3-4d6c-a020-ec2c0aadf68e
content:: At a workshop, two speakers argue that advanced AI cannot be controlled.

**Speaker 1:** 'Rice's theorem says that no algorithm can decide, for every possible program, whether that program has a given non-trivial property of its behaviour. Safety is such a property. So we can never verify that an AI system is safe, and control is impossible.'

**Speaker 2:** 'The law of requisite variety says that a regulator can keep a system's outcomes within an acceptable range only if the regulator can respond in at least as many distinct ways as there are distinct disturbances it must counter. A human oversight team has far less variety than a superhuman AI. So humans cannot control such an AI.'

For each speaker:

1. Say what the cited result actually establishes, and what extra assumptions the speaker needs to reach their conclusion.
2. Say whether some version of the argument still constrains AI control in practice, and in what setting.

End with your overall judgement of what results like these can and cannot tell us about controlling AI.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner who concludes that control of advanced AI is in fact infeasible can earn full marks if they engage with the gap between the theorems and the conclusion, for example by arguing that the escape routes below will not be available or will not be used.

**(a) Speaker 1, 40 points.** 20 points for what the result does and does not establish: it rules out a single procedure that gives the correct answer for every possible program. It does not rule out verifying particular programs, using checks that are safe but incomplete (they may reject some safe systems or answer 'unknown'), building systems within a restricted class whose properties can be checked, or monitoring and restricting behaviour at run time. The extra assumption is that controlling AI requires deciding safety exactly for arbitrary systems. Accept any two of these escape routes with explanation. 20 points for a residual constraint with a setting, for example: for large learned systems whose behaviour we did not design and cannot easily restrict, formal verification of rich behavioural properties is very hard in practice; or 'safety' may not be precise enough to state as a formal property at all. 10 points if the answer only says 'the theorem is about the worst case' without naming what remains possible or what still bites.

**(b) Speaker 2, 40 points.** 20 points for what the result does and does not establish: the regulator's variety must match the variety of disturbances that affect the outcomes it must keep acceptable, not the internal complexity of the AI. The variety that must be matched can be reduced by restricting the AI's channels of action (a sandbox, a narrow output format), by widening the set of outcomes counted as acceptable, and the regulator's variety can be increased with tools, automation or other AI systems. The extra assumptions are that the humans must match the AI unaided and must respond to everything the AI could do. Accept any two of these points with explanation. 20 points for a residual constraint with a setting, for example: an AI acting openly in the world through many channels produces disturbances too varied for a limited oversight channel, and narrowing the channels also reduces the AI's usefulness; or using other AI systems to raise oversight variety moves the control problem to those systems. 10 points for 'it is only a rough principle' without saying what it does and does not require.

**(c) Overall judgement, 20 points.** Full credit: the results show that perfect, fully general control is impossible and identify what adequate control would need (restriction, amplification of the overseer, systems built to be checkable), but they do not by themselves show that adequate control is impossible in a specific setting; that depends on empirical facts about the systems and the setting. Accept the opposite overall view if it is argued from such facts rather than from the theorems alone. 8 points for a judgement stated without distinguishing perfect from adequate control.

Do not penalize the learner for not naming other results (for example the good regulator theorem or information-theoretic limits on control); they may earn credit within (c) if used correctly.
feedback-instructions:: Tell the learner whether they separated what each result proves from the assumptions the speakers added, and quote their clearest example. Name the single most useful improvement, often stating a concrete setting where the result still constrains control rather than only rebutting the speakers. Ask one follow-up question. No generic praise.
