---
id: '8c1b1746-f171-4506-9862-6cc79cf83158'
learning-outcome: "Explain why choosing the option that scores highest on an imperfect proxy systematically selects options where the proxy overestimates true value, why this gap grows with the size and power of the search, and evaluate proposed mitigations by what each does to that selection effect and where it still fails."
topic: "[[../Domains and Topics/3 Alignment/Inner and outer alignment]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Goodhart. AFFINE prerequisites: none. Not yet copied into requires:. The existing placeholder LO "Goodharting" covers the causal model of proxy failure in general; this LO covers the selection effect of strong optimisation on a proxy. %%
## Test:
id:: cf86f736-1d5f-4acb-add1-fb0275ecbc67

#### Question: Open
id:: dc670375-554d-4165-a93c-9f07fa8a9e1e
content:: A lab trains a reward model on human ratings of short written plans, so that it predicts how good a human expert would judge a plan to be. On a held-out set of typical plans, the reward model's scores agree closely with expert judgement. The lab then uses it in two systems:

- **System A** writes 100 candidate plans for a task and carries out the one the reward model scores highest.
- **System B** uses a powerful search to explore billions of candidate plans, including very unusual ones, and carries out the one the reward model scores highest.

1. Predict how the gap between the reward model's score and the real quality of the chosen plan will differ between System A and System B, and explain the mechanism.
2. The team considers three changes to System B. For each one, say what it does to the mechanism you described and where it could still fail:
   (i) train the reward model on ten times as many ratings;
   (ii) instead of the top-scoring plan, pick at random among the plans whose score is above a fixed threshold;
   (iii) train a second reward model independently, and reject any plan that the two models score very differently.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement: a learner may argue that one mitigation works better or worse than the guide below suggests, and earn full credit if the argument is sound.

**(1) Mechanism and prediction, 45 points.** Full credit requires: (a) the prediction that the chosen plan's score overstates its real quality more in B than in A (10 points); (b) the mechanism: the reward model's score is real quality plus error; picking the maximum score selects not only for high quality but also for high error, so the winner's score is expected to overestimate its quality even if the model is unbiased on typical plans (20 points); (c) why B is worse: a larger search contains more candidates with large errors, so the maximum is more likely to be one; and B reaches unusual plans unlike the reward model's training data, where its errors can be much larger, so good agreement on typical plans says little about the extremes B selects (15 points). Accept equivalent formulations such as the winner's curse, regression to the mean, or "the optimiser searches out the model's mistakes". 20 points total for "the AI will game the reward model" without explaining why selecting the maximum selects for error.

**(2) Three changes, 55 points (about 18 each).** Full credit for each: states the effect on the selection mechanism and a real limit.
(i) More data reduces errors on the kind of plans it covers, so it helps, but choosing the maximum still selects for whatever errors remain, and a search over very unusual plans can still reach regions the extra ratings do not cover. Partial credit (9) for "it helps" or "it does not help" without saying why.
(ii) Picking at random above a threshold reduces how hard the system selects for error, because it no longer pushes to the very top of the score distribution; its cost is giving up some real quality. It can still fail if the threshold is set so high that the plans above it are mostly ones whose score comes from error, or if the candidate pool itself is dominated by unusual plans with large errors. Partial credit (9) for noting only the benefit or only the cost.
(iii) Two independently trained models can catch plans whose high score comes from an error in only one model, similar to checking against a held-out validation set. It fails when the two models share errors (same kind of data, same blind spots), or when the search is strong enough to find plans that fool both, or if the search can optimise against the check itself. Partial credit (9) for noting only the benefit or only the limit.

A fluent answer that says "optimisation pressure is dangerous" for every item without tying each to the selection effect cannot score above 40.
feedback-instructions:: Name the strongest part, quoting a phrase. Then name the single most valuable improvement: usually either stating plainly why taking the maximum selects for error, or naming the specific condition under which a mitigation fails. If the answer is strong, ask what System B's designers could measure to learn whether their chosen plans are being selected for error. No generic praise.
