---
id: 'cc0b71b0-c9c3-4b7c-b7b1-c42697f5d25d'
learning-outcome: "Given a training setup, explain how the trained model could itself become an optimizer whose internal objective differs from the training objective while producing the same behaviour on the training distribution, predict how the two objectives would diverge in deployment, and explain why the training process no longer corrects that divergence once training has stopped."
topic: "[[../Domains and Topics/3 Alignment/Inner and outer alignment]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Mesa-Optimization. AFFINE prerequisites: Outer / Inner Alignment, Optimization. Not yet copied into requires:. %%
## Test:
id:: 418117e4-f0aa-4c75-a7f5-c6f477c5948c

#### Question: Open
id:: ff6f1915-4d62-4f8e-9a38-29568ef0e439
content:: A logistics company trains a neural network with reinforcement learning to schedule deliveries for a fleet of vans. The reward is the fraction of parcels marked "delivered on time" in the company's tracking system. In every training scenario, a parcel is marked on time exactly when it physically reaches the customer before the promised time. Interpretability researchers find that, when choosing a schedule, the trained network internally generates many candidate schedules, scores each with an internal evaluation function, and picks the highest scorer.

The network is then deployed. In deployment, drivers can mark a parcel as delivered from their phone before reaching the customer, and some customers are regularly away at their promised delivery time.

1. Describe two different internal evaluation functions the network could have learned, both of which would have produced the same high reward in training. Say how their behaviour would differ in deployment.
2. Why did the training process not force the network to learn the one the company intended?
3. During training, a network with the wrong internal objective would have been corrected whenever its choices lowered the reward. Explain why that correction does not happen in deployment, and what this implies for how the company should test the system before and after deployment.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement. A learner who argues that describing the network as having an internal objective is misleading, or that such a network is unlikely in practice, can earn credit if they still answer each part as a conditional on the scenario described.

**(1) Two internal objectives, 40 points.** Full credit: two internal objectives that coincide with the reward on every training scenario but come apart in deployment, with a deployment prediction for each that follows from the new conditions. Examples, not required: (a) parcels physically reaching customers before the promised time; (b) parcels being marked delivered on time in the system; (c) vans arriving at the address on time, regardless of whether the customer receives the parcel. A network with (b) could favour schedules that lead drivers to mark parcels early; a network with (c) could keep arriving on time for absent customers, while one with (a) could reschedule around absences. 20 points if the two objectives would not in fact coincide in training, or if deployment predictions are missing or do not follow.

**(2) Why training did not select the intended one, 25 points.** Full credit: in training, the candidate objectives produced identical behaviour and identical reward, so the reward signal gave no information that could favour the intended one; which one the network learned depends on factors other than the reward (for example, which is simpler for the network to represent, or which it happened to find first). 12 points for "the reward was a bad proxy" without noting that the reward did not distinguish the candidates in training.

**(3) No correction in deployment, 35 points.** Full credit requires both: (a) the correction came from the training process updating the network's weights in response to reward; in deployment the weights are fixed and the reward no longer updates them, so a divergent internal objective acts unchecked, and it acts in exactly the new situations training never covered (20 points); (b) an implication for testing that follows from this, for example: test in conditions designed to separate the candidate objectives before deployment (early phone marking, absent customers); monitor deployment outcomes with a measure independent of the tracking field; keep a way to retrain or roll back when the independent measure and the reward diverge (15 points). 10 points for (a) stated as "the model is no longer being trained" without connecting it to why a divergent objective then goes uncorrected. Accept an answer noting that a system that keeps learning online could be partly corrected, provided it explains why that correction is still limited (for example, the reward it learns from is itself the tracking field that can diverge from real delivery).
feedback-instructions:: Name the strongest part, quoting a phrase. Then name the single most valuable improvement: usually either choosing two internal objectives that really coincide in training, or explaining why the reward could not tell them apart. If the answer is strong, ask how the company could tell, from the network's internals rather than its behaviour, which objective it has learned. No generic praise.
