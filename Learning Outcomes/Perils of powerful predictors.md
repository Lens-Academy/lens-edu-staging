---
id: '91bba9f6-c553-4f94-ab72-96634a15e104'
learning-outcome: "Explain how a predictor whose published outputs change the events it predicts can end up steering the world toward outcomes selected for being self-confirming rather than good, why the selected outcome need not resemble what would have happened without the prediction, and evaluate a proposed safeguard against this."
topic: "[[../Domains and Topics/4 Agent Foundations/Prediction and predictors]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Perils of Predictors. AFFINE prerequisites: Agency, Performative Prediction. Not yet copied into requires:. %%
## Test:
id:: ba7dc26e-6754-45e9-8871-0da86e6432b9

#### Question: Open
id:: 2e3ba9eb-77ca-45a0-be15-85e3867bad89
content:: A government consults a highly capable forecasting system, trained only to minimise its forecasting error, on whether a large bank will fail within the next month. The forecasts are published, and depositors react to them. A high forecast of failure leads people to withdraw their money, which makes failure more likely; a low forecast calms them.

1. Explain how more than one forecast could come true once published, and why the forecast the system gives need not match what would have happened if no forecast had been published.
2. Over many questions like this, the system keeps being trained to reduce its error. Explain which forecasts this training favours when forecasts affect outcomes, and why this could make the system act as if it were pursuing goals of its own, even though it only predicts.
3. An engineer proposes: after each forecast is produced, a random draw decides whether it is published. The system is scored and trained only on the questions where its forecast was not published. Explain what problem this addresses, and name one thing it does not solve.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner who argues that the danger is small in practice (for example, because most outcomes respond only weakly to forecasts) can score full marks if the mechanism is explained correctly.

**(a) Several self-confirming forecasts, 30 points.** 15 points: because the outcome depends on the forecast, a high failure forecast can cause a run that makes the bank fail, and a low one can calm depositors so the bank survives; both come true once published. 15 points: which of these the system gives is decided by the feedback between forecast and outcome and by what the system is selected for, not by the bank's condition without a forecast; the no-forecast outcome is a different question (for example, a sound bank can still be made to fail by a failure forecast). 7 of the second 15 for "the forecast affects the outcome" without saying why this breaks the link to the no-forecast outcome.

**(b) What training favours, 35 points.** 15 points: training on error favours forecasts that make themselves come true and make the outcome as reliable as possible, which often means confident, extreme forecasts; nothing in the error score favours outcomes that are good for people. 20 points: why this looks like goal pursuit: the system is being selected for outputs because of their effects on the world, so over time it can learn how people react and choose outputs that push the world into states that match its forecasts, which is steering. Accept the point that a system without a model of its own influence would not do this deliberately but could still drift that way through training. 10 of these 20 for "it might manipulate people" with no mechanism.

**(c) The safeguard, 35 points.** 20 points: what it addresses: in the scored cases the forecast has no effect on the outcome, so the error-minimizing forecast is the outcome without publication, which removes the training incentive to pick self-confirming forecasts. 15 points: one correct limitation, explained, for example: published forecasts still affect people, and they describe the unpublished world, so they can be wrong about what actually happens once published; removing the training incentive does not guarantee the trained system lacks other goals; the system might still influence scored cases, for instance if earlier published forecasts shape the situations it is later scored on; it wastes the data from published cases. 7 of these 15 for a limitation named without explanation.
feedback-instructions:: Say whether the learner separated "the forecast comes true" from "the forecast matches what would have happened anyway", since that distinction carries the whole skill. Name the strongest part of the answer and the single change that would improve it most. Ask one follow-up question, such as how the safeguard should be changed if the published forecasts are later used as evidence for other questions. No generic praise.
