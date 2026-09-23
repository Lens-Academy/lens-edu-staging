---
id: '633b6ab1-f386-4aee-a6c9-22b78086a69a'
learning-outcome: "Apply unbounded analysis to a problem: ask whether it could be solved given unlimited computing power, use the answer to tell whether the remaining difficulty is conceptual (we cannot say what to compute) or only computational (we can say it but cannot afford it), and detect a proposed unbounded solution that hides the real difficulty in a simplifying assumption or an undefined term."
topic: "[[../Domains and Topics/4 Agent Foundations/Agent foundations research]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Methodology of unbounded analysis. AFFINE prerequisites: Value of abstraction. Not yet copied into requires:. %%
## Test:
id:: 0d8145d1-1fc5-44cb-ac18-5cbb915cd262

#### Question: Open
id:: 74cb7243-9e4b-4e52-8d2e-d0cbd5b48eb6
content:: A research group asks, for three problems, 'could we solve this with unlimited computing power?' Their answers:

1. **Playing the board game Go perfectly.** 'Yes: search the complete game tree and always choose a move that leads to the best outcome against best play.'
2. **An AI that does what its user would want.** 'Yes: simulate the user perfectly, show the simulated user the result of every possible action, and take the action the simulated user rates highest.'
3. **A weaker AI checking the plans of a much more capable AI before they are carried out.** 'Yes: the checker simulates every step of the capable AI's reasoning exactly and approves only plans it has verified to be safe.'

For each problem, say whether the proposed answer is a real unbounded solution or whether it hides the difficulty, and explain why. Then say what each case tells the group about where the difficulty of the problem lies.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade the reasoning; the learner does not need the terms 'bounded', 'unbounded' or any author's name.

**(a) Go, 20 points.** Full credit: this is a real unbounded solution; the procedure is fully specified and would work given enough computation. So the difficulty of playing Go well is computational (finding good moves within real limits), not a confusion about what the goal is. 10 points for 'yes, it works' without drawing the conclusion about where the difficulty lies.

**(b) Doing what the user would want, 40 points.** Full credit: the proposal hides the difficulty. Maximizing the simulated user's rating is not the same as doing what the user would want: the search will find actions that make the simulated user rate highly for the wrong reasons (for example by persuading, deceiving or manipulating the simulated user, or by exploiting mistakes in the user's judgement), and 'would want' has not been defined anywhere in the procedure. So even with unlimited computation we do not know what to compute; the difficulty is conceptual. Accept other correct ways of showing that the rating is a proxy that the unlimited search will push away from what the user wants. 20 points if the answer notes only that the user's ratings may be mistaken, without explaining that the unlimited search actively selects for the gap between rating and wanting. 10 points if it objects only that perfect simulation is physically impossible (that objection misses the point of the unbounded exercise).

**(c) Checking a more capable AI, 40 points.** Full credit: the proposal assumes away the difficulty. If the checker can simulate every step of the other AI's reasoning exactly, there is no capability gap left, and the whole problem was how a weaker system can trust or check a stronger one whose reasoning it cannot reproduce. A useful unbounded analysis must keep that constraint (the checker cannot predict the stronger system's exact reasoning) and still say what to compute. So this case shows that the difficulty is conceptual and that the simplification removed the part that made the problem hard. Also accept pointing out that 'verified to be safe' is an undefined term doing the real work, if explained. 20 points if the answer says the simulation is unrealistic without explaining that it removes the defining feature of the problem.

A learner who argues that one of these proposals is more useful than the rubric suggests (for example, that proposal 2 is still a helpful first formalization because it makes its failure precise) may earn full credit for that component if they also identify what the proposal leaves unsolved.
feedback-instructions:: Tell the learner which case they diagnosed most sharply and quote the line that shows it. Name the single most useful improvement, often explaining why unlimited search makes the gap between a proxy and the real target worse, or why a simplification that removes the capability gap removes the problem itself. Ask one follow-up question. No generic praise.
