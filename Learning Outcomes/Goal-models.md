---
id: 'f57e9a1f-814c-42c7-ab7e-192279a00151'
learning-outcome: "Contrast describing an agent's goals as a goal-model (a detailed, structured representation of how the agent wants a particular part of the world to be, analogous to a world-model) with describing them as a utility function that assigns a score to every possible world, and use the contrast to predict how an agent of each kind responds to small deviations from its target, to offers that trade its target for something scored higher, and to situations its goals were not built for."
topic: "[[../Domains and Topics/4 Agent Foundations/Goal-directedness and coherence]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Goal-Models. AFFINE prerequisites: Goal. Not yet copied into requires:. %%
## Test:
id:: 761a8eb4-bdbe-4fc4-aba9-b4d27508f0a0

#### Question: Open
id:: d7f78fea-e3e2-48d2-a59d-79ee5d0df36e
content:: An AI system is put in charge of a historic public garden. Consider two designs.

Design U scores every possible state of the world with a single number built from a few simple features (number of healthy plants, number of visitors, maintenance cost), and chooses the actions that maximize the expected score.

Design G holds a detailed picture of what this garden should be like (its layout, the character of each area, how the parts fit together), and acts to bring the actual garden closer to that picture.

For each design, predict and explain how it responds to:

1. a few weeds and a damaged hedge;
2. an offer from the city to bulldoze the garden and build a much larger park with more plants and visitors somewhere else;
3. a plan to build a metro station under the garden, a situation neither design was built with in mind.

Then say which design you expect to be easier for its human overseers to predict, and why.
max-chars:: 2500
assessment-instructions:: Score 0 to 100. Grade reasoning, not agreement. Do not require the terms "goal-model", "utility function over world-states", "local", "global", "selection" or "control", or any author name. A learner may point out that a utility function could in principle encode the garden's character too, and that the real difference is in what each representation makes cheap to express and how the agent searches; credit this as insight, and do not penalize the learner for questioning the setup, as long as they still answer for the designs as described.

**Situations 1 to 3, 75 points (25 each).** For each situation, give up to 12 points for design U and up to 13 for design G. Each prediction must be tied to how the design represents what it wants, not just stated.
- (1) U repairs the weeds and hedge to the extent that doing so raises its score (more healthy plants, perhaps more visitors) relative to maintenance cost, and may not bother if the score effect is small. G notices the deviation from its detailed picture and makes small corrective actions to restore it, much like a controller correcting drift, whether or not a simple score changes much.
- (2) U compares the two worlds by its score; since the larger park has more plants and visitors, U favours accepting the offer, because a single score lets any feature trade against any other, and the garden's particular character is invisible to it. G does not favour the offer: it destroys the thing its goal describes, and its goal says nothing in favour of a park elsewhere. Accept either "G rejects it" or "G has no basis to value the offer at all" with reasons.
- (3) U evaluates the metro plan through its features only (for example, more visitors raise the score), so it can have a confident view that misses effects on things its features do not capture, such as the garden's character or root damage. G's picture may say little about underground construction or about visitor flows, so its preferences may be incomplete or undefined here: it may need to extend or refine its picture, may oppose only the parts that visibly change the garden, or may behave unpredictably. Accept any of these if tied to the local, detailed nature of G's goal.
Give 0 to 5 for a situation where the answer gives predictions with no link to the design.

**Predictability, 25 points.** Full credit for a verdict with a reason tied to how the two designs represent their goals. Either verdict can earn full credit: for example, that U is easier to predict because one score ranks every option (though it produces extreme choices whenever the score and human intentions diverge, as in situation 2); or that G is easier to predict near familiar states because it keeps things as they are (though harder in new situations where its picture is silent); or that the answer depends on how familiar the situation is. 12 points for a verdict whose reason does not connect to how the designs represent their goals (for example "G seems more human"). 5 for a bare verdict.
feedback-instructions:: Name the situation where the learner's prediction was most clearly derived from how the design represents its goals. Then give the single most valuable improvement: usually explaining why a single score lets anything trade against anything (situation 2), or why a detailed local picture can be silent about new situations (situation 3). If the learner argued that the two designs are not really different in kind, engage with that and ask what would make the difference matter in practice. No generic praise.
