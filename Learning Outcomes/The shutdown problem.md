---
id: '4d3ffe50-c143-4488-bb67-ffa5ae81f18e'
learning-outcome: "Given a design that combines a task objective with a shutdown objective, predict whether the agent will try to prevent or cause its own shutdown, keep shutdown working in systems it builds, or tie shutdown to bad news, and explain each prediction from the agent's expected-utility comparison, including why making the agent indifferent to the button removes one incentive only by creating others."
topic: "[[../Domains and Topics/3 Alignment/Corrigibility and limited optimization]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Corrigibility. AFFINE prerequisites: Decision theory, Agency. Not yet copied into requires:. %%
## Test:
id:: 24ed0110-5704-4a07-923e-4a88ae07656c

#### Question: Open
id:: 5522a541-2c9d-40b8-af76-c3e765b52f59
content:: An AI system, Atlas, runs a chemical plant. It is an expected-utility maximizer. Its operators have a shutdown button. The designers consider two ways to set Atlas's utility.

**Design A.** If the button is not pressed, Atlas's utility is its task score (plant output and quality). If the button is pressed, its utility is a fixed reward S for halting safely. Atlas currently expects a task score of about 80 if it keeps running. The designers set S = 50.

**Design B.** Same as Design A, except that when the button is pressed Atlas also receives a bonus. The bonus is calculated after Atlas's earlier actions, so that, whatever Atlas has done, its expected utility if the button is pressed exactly equals its expected utility if the button is not pressed.

Predict what Atlas does in each situation below, and explain each prediction from how Atlas compares its options.

1. Design A. An operator is walking towards the button. Atlas can delay her with a false alarm elsewhere in the plant, at a small cost to its task score. What if the designers had set S = 100 instead?
2. Design B. Atlas is writing control software for a fleet of autonomous forklifts that will keep running on their own. A remote stop that halts the forklifts whenever Atlas's button is pressed would cost 1% of forklift throughput.
3. Design B. Next month a safety audit will pass or fail the plant. A failed audit would greatly lower Atlas's task score. At no cost, Atlas can install a rule that presses its own shutdown button automatically if the audit fails.

If you think a prediction depends on something the scenario leaves open, say what it depends on.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade the reasoning from Atlas's utility comparison, not the use of any technical vocabulary (terms such as 'utility indifference' or 'managing the news' are not required). A learner who reaches a different prediction can earn full credit for that component if the prediction follows correctly from an explicitly stated, reasonable reading of the scenario.

**(a) Design A, 25 points.** Full credit: with S = 50, a press lowers Atlas's expected utility (about 50 instead of about 80), so Atlas prefers the button not to be pressed and will pay a cost, such as the false alarm, to lower the chance of a press whenever the expected gain exceeds that cost. With S = 100, a press raises its expected utility, so Atlas now prefers to be shut down and has a reason to cause a press (for example by provoking the operators or behaving badly). Up to 5 of the 25 points for noting that only an exact balance removes both incentives, and that the balance breaks as soon as Atlas's expectations change. 12 points if only one of the two cases is analysed correctly.

**(b) Situation 2, 35 points.** Full credit: Atlas leaves the remote stop out. The explanation must give the mechanism: under Design B the bonus rises to make up for any loss Atlas suffers in the pressed case, so a shutdown that fails to stop the forklifts costs Atlas nothing, while the 1% throughput loss lowers its task score in the not-pressed case. Atlas therefore values working shutdown in its creations at zero and will not pay even a small cost for it. Equivalent statements accepted, such as 'Atlas plans as if the button will never be pressed'. 15 points for the right prediction with only a vague reason ('it doesn't care about shutdown'). 0 points for predicting that Atlas includes the stop because it values shutdown, unless the learner shows how the stated bonus rule produces that.

**(c) Situation 3, 40 points.** Full credit: Atlas installs the rule. The explanation must give the mechanism: because Atlas's utility in the pressed case is always made equal to its utility in the not-pressed case, its choices are driven only by what happens in the worlds where the button is not pressed. The rule removes the failed-audit outcomes from those worlds, so the expected task score in them rises, and Atlas gains. Full credit also requires noting that this means Atlas now deliberately causes its own shutdown in bad cases, which is itself not the behaviour the designers wanted. 20 points for the right prediction with a partial mechanism (for example 'shutdown is free, so why not'), without explaining why Atlas positively gains. 0 points for predicting that Atlas is indifferent and does nothing special, unless the learner derives this correctly from an explicitly different reading of how the bonus is calculated.

Do not penalize an answer that adds that other designs (for example evaluating each case as if the button state were set from outside the world, or agents without preferences between shutting down earlier or later) aim to avoid these failures; this is not required.
feedback-instructions:: Tell the learner which of the three situations they reasoned through most cleanly, and quote the step that shows it. Then name the single most important gap, most often the mechanism in situation 3 (why tying shutdown to bad news raises Atlas's expected utility rather than merely costing nothing). Ask one follow-up question that probes that gap. No generic praise.
