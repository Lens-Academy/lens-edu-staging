---
id: '06091514-adeb-4cda-a3b8-5b6c2f78307c'
learning-outcome: "Describe prediction and planning as the same operation, reducing the expected mismatch (cross-entropy) between the distribution of world states and a model, that differ in which side is adjusted (the model to fit the world, or the world to fit the model), and use the resulting asymmetry (mass-covering forward divergence versus mode-seeking reverse divergence) to work out how a forecaster and a controller will behave differently given the same distribution."
topic: "[[../Domains and Topics/4 Agent Foundations/Prediction and predictors]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Planning/Prediction Duality?. AFFINE prerequisites: Agency, Performative Prediction. Not yet copied into requires:. %%
## Test:
id:: e751a760-36e1-4a26-969d-7f7d220946a5

#### Question: Open
id:: b6166d71-d36a-4561-83ef-33d49ae02a33
content:: In a shared office, half the occupants are comfortable only close to 18°C and the other half only close to 24°C. Let P be the distribution of comfortable temperatures across occupants: two narrow, equally tall peaks at 18°C and 24°C, with very low density in between.

Two systems can each work only with single-peaked, bell-shaped distributions over temperature, for which they choose a centre and a width.

System F is a forecaster. It outputs a bell-shaped distribution to predict the comfortable temperature of a randomly chosen occupant. Its score is the average, over occupants drawn from P, of the log of the density F assigns to that occupant's comfortable temperature.

System C is a thermostat controller. It chooses a bell-shaped distribution for the actual room temperature (a centre and an amount of fluctuation). Its score is the average, over room temperatures drawn from C's own distribution, of the log of P at that temperature.

1. Describe what each system will choose, and explain why.
2. Explain the sense in which F and C perform the same kind of operation, and state exactly what differs between them.
3. A colleague says: "If we have an excellent predictor of what temperature people find comfortable, we can control the room well by setting it to the predictor's most likely value." Evaluate this claim using the example, and say under what conditions it would hold.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement. The learner does not need the terms "forward" and "reverse" KL divergence; any correct explanation of the asymmetry counts. Accept "direction of fit", "mind-to-world" and "world-to-mind", or active-inference language, as equivalent framings.

**(a) The two choices, 40 points.** F, 20 points: F centres near 21°C with a width large enough to cover both peaks (a standard deviation of about 3°C), because the log score punishes heavily any occupant whose comfortable temperature gets near-zero density, so F must spread probability over both peaks even though this puts its own peak where P is low. C, 20 points: C sits at one of the peaks (18°C or 24°C, either is equally good) with as little fluctuation as it can, because its score is averaged over its own temperatures, so any time spent in the low-density middle is punished heavily and covering both peaks gains nothing. 10 of each 20 for the correct choice without the reason. An answer that has C choose 21°C gets 0 for C.

**(b) Same operation, what differs, 30 points.** 15 points: both systems maximize the average log of one distribution under another, that is, they minimize a cross-entropy or mismatch between P and a bell-shaped distribution. 15 points: what differs is which side is adjusted and which side the average is taken over. F adjusts its model to fit the world's distribution, and the average is over the fixed distribution P. C adjusts the world to fit P, which acts as a target, and the average is over the distribution C itself controls. This reverses the direction of the divergence, which is why F covers all of P's mass and C seeks one mode. 8 of these 15 for naming only "one fits the model to the world, the other fits the world to the model" without linking it to the behaviour in part 1.

**(c) The colleague's claim, 30 points.** 15 points: in this example the claim fails, because F's most likely value is about 21°C, where almost nobody is comfortable. 15 points: the conditions, in any argued form, for example: it holds when the predictor can represent P accurately (then its most likely value is a peak of P), or when P has a single peak; it fails when a restricted predictor trained for coverage places its peak between the modes of what people want. 7 of these 15 for a condition with no reason.
feedback-instructions:: Say whether the learner explained which distribution each average is taken over, since that is what makes the two systems behave differently. Name the strongest part of the answer and the single change that would improve it most. Ask one follow-up question, such as what C would choose if its score also rewarded fluctuation (an entropy bonus). No generic praise.
