---
id: '99436199-46b6-425e-b9f1-8920d6fc2799'
learning-outcome: "Judge whether a given concept is likely to be shared by very different capable minds, by asking whether it summarises information that many parts of the environment carry redundantly and that is useful for prediction across many situations, or whether its boundary depends on a particular mind's own internals, abilities or values; and draw the consequence for alignment plans that rely on finding a human concept inside an AI."
topic: "[[../Domains and Topics/4 Agent Foundations/Natural abstraction]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Natural Abstraction. AFFINE prerequisites: Ontology, Probability. Not yet copied into requires:. %%
## Test:
id:: 344323a4-8e58-4b55-99e0-658824b9fbd8

#### Question: Open
id:: dcfb6860-6bf2-4fdd-b984-62f4b76984aa
content:: A lab trains a large model only on sensor and action logs from a fleet of warehouse robots: camera images, joint angles, pallet positions and operator commands. It never sees human language. The lab plans to use interpretability tools to find concepts inside the model and then train the robots to act on those concepts.

For each concept below, say how likely you think it is that the model has an internal variable that closely matches the human concept, and why:

(a) the position of a pallet;
(b) a task being tedious;
(c) an operator instruction that the operator would want to be free to correct later.

Then say what your answers imply for the lab's plan to find concept (c) in the model and make the robots act on it.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from four components. The idea that very different minds converge on the same concepts is a hypothesis, and it is contested. Grade reasoning, not agreement: an answer that argues against convergence, or that argues this particular model is a bad test of it, can earn full marks if its reasons address what makes a concept likely or unlikely to be shared. Do not require terms such as "natural latent", "redundancy", "mediation" or "reflective".

**(a) Pallet position, 25 points.** Full credit: likely. The reason must be about the data: a pallet's position is carried by many observations at once (many camera frames and angles, the robots' interactions with it) and it explains much of how those observations relate to each other, so almost any good predictor of these logs has to track it. Credit a note that the model may encode it in a different format or coordinate system, so a translation may be needed. 12 points for "likely, because it is physical or obvious" without the reason.

**(b) Tedious, 25 points.** Full credit: unlikely to match closely. Tedium is partly about the effort or boredom a particular kind of mind experiences, so the concept's boundary depends on the human's own internals rather than on anything the logs fix. The model may have related variables (how long or how repetitive a task is), which overlap with tedium in some cases but not others. Full credit also for an argued "partly", if the answer separates the part of the concept that the data could fix (duration, repetition) from the part that depends on the human mind. 12 points for "unlikely because it is subjective" without saying why that matters (the data the model predicts do not determine the concept's boundary).

**(c) Instruction the operator would want to correct, 25 points.** Full credit: unlikely to match closely. The concept is about the operator's preferences regarding their own future corrections and about the relationship between the robot and its overseer; it depends on the operator's internal states, which the logs show only weakly; the model may have something like "a command that was later overridden", which agrees with the human concept in common cases and diverges in the cases that matter (for example, instructions the operator would want to correct but never did). Credit an argument that operator command logs make a partial match possible, if the answer says where the match would break.

**(d) Implication for the plan, 25 points.** Full credit: finding a concept inside a model and building on it is more promising for concepts like (a) than for concepts like (c). For (c), the lab may find no matching variable, or find a proxy that agrees with the human concept on the training data and diverges in new situations, and acting on the proxy would then give the wrong behaviour exactly where it matters. If the learner judged (c) likely to match, full credit instead requires saying how the lab could confirm the match on the cases where a proxy would diverge. 12 points for "the plan may fail" without the proxy or divergence mechanism. Creditable within the 25 but not required: a constructive response (for example, define (c) from pieces that are more likely to be shared, check the found variable on cases where proxy and concept come apart, or change the training data so that the human concept becomes learnable), or the separate point that even a well-matched concept may be hard to make the robots act on reliably.
feedback-instructions:: Name the concept where the learner's reasoning was strongest, and the one where they relied on intuition ("obvious", "subjective") instead of saying what in the data does or does not fix the concept. Suggest one concrete check the lab could run on concept (c). No generic praise.
