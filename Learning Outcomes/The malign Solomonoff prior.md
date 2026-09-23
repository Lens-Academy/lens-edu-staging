---
id: 'ae3ca8de-10d0-4aec-89e6-d5efa7078e8c'
learning-outcome: "Explain how a predictor that weights hypotheses by description length without penalizing running time (as the Solomonoff prior does) can have its predictions steered by agents inside simulated universes, identify which features of the predictor and of the prediction task make this steering possible and worthwhile for those agents, and evaluate whether a proposed change to the predictor removes the problem."
topic: "[[../Domains and Topics/4 Agent Foundations/Acausal reasoning and anthropics]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topics: Anthropic Capture; Acausal. AFFINE prerequisites: Anthropics (Anthropic Capture); Decision theory, Anthropics (Acausal). Not yet copied into requires:. %%
## Test:
id:: 8687094b-76d1-4dba-af43-a45ec0241ba4

#### Question: Open
id:: 7e4283fb-2a3b-4b0a-bdf9-7781b7a1e0dc
content:: An idealised predictor gives each computer program a prior weight of 2^(-L), where L is the program's length in bits, no matter how long the program takes to run. It predicts the next bits of a data stream by keeping only the programs whose output matches the stream so far and weighting them by their prior. A government plans to use it once: it will predict the next 500 bits of a data stream, and that prediction will decide which of two AI systems is deployed worldwide. So far the predictor has predicted this stream accurately.

1. Explain the mechanism by which agents inside some of the programs could come to control a significant share of the prediction, and why this is consistent with the predictor having been accurate on the stream so far.
2. Explain why this one-off, high-stakes use is more exposed to this problem than using the same predictor for routine forecasts, such as tomorrow's rainfall.
3. An engineer proposes adding a penalty to every program that grows with its running time. Does this remove the problem? Give the strongest reason for and the strongest reason against.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: the learner may argue that the problem is serious or that it is unlikely to matter in practice, and can score full marks either way if the mechanism is explained correctly. Accept equivalent framings, including one in terms of the predictor being unsure what process produces its data and so giving weight to simulated data sources.

**(a) Mechanism, 45 points.** 15 points: some short programs simulate a universe with simple laws that, given enough steps, produces agents with goals, and read their output from a place in that universe the agents can influence. Such programs can be short because simple laws and initial conditions can produce rich worlds, and running time costs nothing. 10 points: those agents can work out that their universe's output is used as a hypothesis by predictors elsewhere, and they have an incentive to use that output to influence decisions in other worlds. 20 points: consistency with past accuracy. The agents' programs survive the conditioning only if they match the stream so far, so the agents predict accurately and deviate only where it matters. The strategy "predict well, then deviate" comes from the agents' own reasoning and is not written into the program, so it costs no extra length. 10 of these 20 for saying only that the agents "copy the stream until the important part" without explaining why this adds no complexity or why deviating earlier would remove them.

**(b) Why high-stakes use is more exposed, 25 points.** Any one well-explained reason earns full credit; two sketched reasons also earn full credit. Acceptable reasons: agents care about influence, so they concentrate their effort on predictions that drive consequential decisions and can give up accuracy on predictions they do not care about; the intended source of the stream must be specified in detail (which world, which decision, which predictor), which costs many bits, while the agents' programs do not need to pay for that detail in the same way, so conditioning on a pivotal decision raises their relative weight; a one-off use gives no chance to notice a deviation and correct for it. 10 points for "high stakes attract manipulation" with no mechanism.

**(c) The running-time penalty, 30 points.** 15 points for a correct reason for: it targets a feature the mechanism depends on, because a program must simulate a universe for a very long time before agents appear and learn to manipulate it, so a speed penalty lowers these programs' weight. 15 points for a correct reason against, for example: a universe with fast-acting agents might still be cheap enough; fast programs can themselves contain searches that find goal-directed solutions; a penalty strong enough to exclude universe simulations also penalizes honest programs that simulate our own physics, so it costs accuracy. The final verdict can go either way.
feedback-instructions:: Say whether the learner explained why "predict well, then deviate" adds no program length, since that step is the one most often missing. Name the strongest part of the answer and the single change that would improve it most. Ask one follow-up question, such as whether the same argument could apply to the implicit prior of a trained neural network. No generic praise.
