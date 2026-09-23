---
id: 'd6467e1e-e7f8-4873-9800-dd2682e9d0a8'
learning-outcome: "Explain how active inference treats perception and action as two ways of reducing the same mismatch between predicted and actual observations, with an agent's goals encoded as confident predictions about what it will observe, and use the relative confidence (precision) of predictions and evidence to predict whether an agent will revise its beliefs or act on the world in a given situation."
topic: "[[../Domains and Topics/4 Agent Foundations/Agency]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Active Inference. AFFINE prerequisites: Probability. Not yet copied into requires:. %%
## Test:
id:: e9e2abbc-f5e1-4086-8f64-65f196de951e

#### Question: Open
id:: e63e4ff8-15b6-40b4-8020-812fcc2ae0a3
content:: A greenhouse controller is built as an active-inference agent. Its designers encoded the goal "keep the soil moist" as a strong expectation that its moisture sensor will read about 40%. The controller can open a water valve. One morning the sensor reads 25%.

1. For each case below, predict what the controller does to reduce the mismatch, and explain why.
   a. The sensor is known to be unreliable, so its readings are given low confidence. The valve works.
   b. The sensor is reliable. The valve works.
   c. The sensor is reliable, but the valve is jammed shut, so no available action changes the soil moisture.
2. Explain in what sense this controller's goal "is" a prediction. Then name one way its behaviour could differ from a controller that keeps a separate reward for moisture near 40% and a separate model of how the world is.
max-chars:: 2500
assessment-instructions:: Score 0 to 100. Grade reasoning, not agreement with active inference: a learner who argues that the framework adds nothing over reward-based control can score full marks on part 2 if the argument is sound. Accept both the formal active-inference framing (preferences are a fixed prior over outcomes, beliefs about the current state are updated by evidence, and actions are chosen to bring expected observations toward the preferred ones) and the looser predictive-processing framing (action fulfils strong predictions, perception adjusts predictions to evidence), as long as the answer is internally consistent. Do not require the terms "free energy", "precision" or "generative model"; "confidence" or "weight given to" is fine.

**1a, 20 points.** The low-confidence reading is weighted weakly against the confident expectation, so the controller largely keeps its estimate that moisture is near the target and does little or nothing to the valve; it may seek better evidence first (take more readings, check another sensor). Full credit needs the link to relative confidence. 10 points for "it ignores the reading" with no reason. 0 if the answer says it opens the valve fully because the reading is low, without addressing the sensor's low confidence.

**1b, 20 points.** Both the expectation and the evidence are confident, so the mismatch carries high weight; because the expectation is about observations the controller can make come true, it acts: it opens the valve until readings approach 40%. In the formal framing it is equally correct to say the controller updates its belief that the soil is now dry and then acts to bring its observations back toward the preferred ones. 10 points for "opens the valve" without explaining why it acts rather than simply changing its belief.

**1c, 25 points.** Full credit: action cannot remove the mismatch, so it persists. With a reliable sensor the controller should come to believe the soil really is dry, and may also revise its beliefs about what its actions do (that the valve does not work). The preference itself is not satisfied, so the controller remains in a high-mismatch state and would try any other available actions, including information-seeking ones, that are expected to bring observations closer to 40%. In the formal framing the preference is not revised by evidence, so it keeps "wanting" 40% while believing it is at 25%. Also accept, in the looser framing, that a persistent unfixable mismatch could eventually lead to revising the expectation itself, or that an expectation held with extreme confidence could lead the controller to discount even a reliable reading, provided the answer ties this to relative confidence. 12 points for "nothing happens" or "it gets stuck" without saying what happens to its beliefs.

**2, 35 points.** Up to 18 points for the sense in which the goal is a prediction: the goal is stored as an expected observation, and the controller selects actions that make its observations match it, so the same mismatch signal drives both updating beliefs and acting; the confidence attached to the expectation sets how strongly the controller pursues it. Up to 17 points for one real difference, with a reason. Accepted differences include: (i) in standard formulations, action selection includes a term for expected information gain, so the controller is drawn to reduce its uncertainty (for example checking a sensor) without a separately added exploration bonus; (ii) wanting and believing share one currency, so changing the confidence of an expectation changes how hard the controller pursues it; (iii) a controller whose expectation is held with too much confidence relative to the evidence can reduce the mismatch by discounting the evidence rather than changing the world (as in 1a), whereas a controller whose reward is computed from the sensor reading gains nothing by discounting that reading. Also give full credit to an argued claim that the two controllers can be mapped onto each other (for example by treating the log-probability of preferred observations as reward) and so need not behave differently, if the answer says what would have to be true for their behaviour to diverge. 8 points for a difference that is asserted without a reason.
feedback-instructions:: Say which of the three cases the learner handled best and why. Then name the single most valuable improvement: usually connecting the prediction in each case to relative confidence, or saying what happens to the controller's beliefs in case c. If the learner argued that active inference is equivalent to reward-based control, engage with that argument directly. Ask one follow-up question, for example what the controller would do if its expectation were given very low confidence. No generic praise.
