---
id: '2ded3ef3-6f27-49c9-93ad-8d7f59f512bc'
learning-outcome: "Distinguish a performatively stable prediction (one that is optimal for the outcomes it itself produces) from a performatively optimal one (the lowest loss once the prediction's own effect on outcomes is counted), and use a model of how outcomes respond to predictions to determine where repeated retraining settles, whether it settles at all, and why the settled prediction need not have the lowest loss."
topic: "[[../Domains and Topics/4 Agent Foundations/Prediction and predictors]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Performative Prediction. AFFINE prerequisites: none. Not yet copied into requires:. %%
## Test:
id:: 1b27e3ed-66e8-4c17-b310-f123d99647e6

#### Question: Open
id:: 0cf7c77e-d432-4485-b14b-7dbf74a778bf
content:: An events company publishes a forecast f of how many people will attend its weekly open day. The forecast changes behaviour. When the forecast is high, some people stay away to avoid crowds. When the forecast is low, fewer people come on impulse, so attendance also varies less. Over many weeks, attendance after a forecast f has mean 1000 - 0.5f and standard deviation 0.5f. Forecasts are scored by squared error.

1. Each week the company retrains by setting its next forecast equal to the average attendance that followed its previous forecast. Where does the forecast end up, and does the process settle? Explain.
2. Is that end point the forecast with the lowest expected squared error, once the forecast's own effect on attendance is counted? If not, in which direction does the lowest-error forecast lie, and why?
3. Now suppose the mean attendance were 1000 - 1.5f instead, with everything else unchanged. What happens to the retraining process? Comparing this with part 1, when can retraining on outcomes that a predictor has itself influenced be trusted to settle?
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not a particular method: algebra, a worked sequence of forecasts, or a clear verbal argument all count. The terms "performatively stable" and "performatively optimal" are not required.

**(a) Where retraining settles, 30 points.** The update is: next forecast = 1000 - 0.5 x previous forecast. It settles at the forecast that equals the mean it causes, f = 1000 - 0.5f, so f = 2000/3, about 667. It does settle: each week the distance from 667 is halved and changes sign, so the forecasts alternate above and below 667 and converge. 15 points for the fixed point, 15 for a correct reason why the process converges. 7 of the second 15 for "it converges" with no reason.

**(b) Stable is not optimal, 35 points.** Expected squared error at forecast f is the squared bias plus the variance: (1.5f - 1000)^2 + 0.25f^2. At about 667 the bias is zero but the variance is about 111,000. Lowering the forecast adds a little bias but removes more variance, so the lowest-error forecast is lower than 667 (it is 600, with expected squared error 100,000). 10 points: no, the settled point is not the lowest-error forecast. 10 points: lower. 15 points: the reason, that the forecast also changes how predictable attendance is, so a forecast can lower its error by making the outcome less variable even though it no longer equals its own average outcome. The exact optimum is not required. An answer that also notes that the optimal forecast is not stable (after forecasting 600, mean attendance is 700, so retraining moves away from it) may be credited here in place of a missing part of the reason.

**(c) When retraining settles, 35 points.** 15 points: with mean 1000 - 1.5f the fixed point is 400, but each week the distance from it is multiplied by -1.5, so the forecasts swing further and further either side and the process does not settle (it diverges until something outside the model, such as attendance hitting zero, stops it). 20 points: the lesson, that repeated retraining settles only if outcomes respond weakly enough to the prediction; here the response per unit of forecast must be smaller than 1 in size, and in general the sensitivity of outcomes to predictions must be small relative to how strongly the loss pins down the best prediction. 10 of these 20 for "it depends on how strongly the forecast affects attendance" with no threshold or comparison.
feedback-instructions:: Say whether the learner distinguished the forecast that is consistent with its own outcomes from the one with the lowest error, since that is the core of the skill. Name the strongest part of the answer and the single change that would improve it most. Ask one follow-up question, such as what a system that could choose any forecast, and cared only about its own error, would learn to do with the variance of attendance. No generic praise.
