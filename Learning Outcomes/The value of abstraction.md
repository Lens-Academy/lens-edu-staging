---
id: 'bffba331-9be9-4d21-96a4-7b6e88ce21b1'
learning-outcome: "Given two properties or explanations that always coincide in a familiar range of cases, widen the range (more general settings, added variables, interventions, weaker assumptions) until they come apart, and use where they come apart to say what their coincidence depended on and why it cannot be relied on in new situations."
topic: "[[../Domains and Topics/4 Agent Foundations/Natural abstraction]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Value of abstraction (no AFFINE description given). AFFINE prerequisites: none listed. Not yet copied into requires:. %%
## Test:
id:: 5efd12b5-3ea5-4de1-8d18-03f03ce1b69e

#### Question: Open
id:: a17f6802-13af-4a9a-8662-7453b6eca0ce
content:: Two short cases.

1. In ordinary plane geometry, a triangle has three equal sides exactly when it has three equal angles. A student says: "So 'equal sides' and 'equal angles' are the same property for triangles. Asking whether one explains the other is meaningless." Show how to widen the range of cases so that the two properties come apart, and say what this reveals about why they coincide for triangles.

2. An AI assistant was trained on many conversations. In all of them, three things coincided: the assistant did what the user literally asked; the user rated the reply highly; and the reply was what the user would have wanted after thinking it over. A developer says: "For our system these are the same thing, so it doesn't matter which one it learned." Describe how you would widen the range of cases to find out which of the three the assistant actually tracks, and explain why this matters even though the three never came apart in training.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning; accept any valid widening, not only the examples below.

**(a) Triangles, 45 points.** Widening (25 points): full credit for a range of cases in which the two properties actually come apart, for example polygons with more sides (a rhombus that is not a square has equal sides but unequal angles; a rectangle that is not a square has equal angles but unequal sides). Accept other widenings only if the properties really separate there. For example, moving to triangles on a sphere does not separate them (equilateral spherical triangles are also equiangular, and the converse holds), so that widening alone earns no points for this part. What it reveals (20 points): full credit says the coincidence depends on a special fact about triangles, not on the two properties being one: a triangle's shape is fixed by its three side lengths, and its angles fix the ratios of its sides, so equal sides force equal angles and the reverse. Once shapes are not fixed in this way (from four sides upward), the two properties are independent. Any correct statement that the coincidence is due to the rigidity or special structure of triangles earns full credit. 10 points for "it is special to triangles" without saying what is special.

**(b) The assistant, 55 points.** Divergence cases (30 points): full credit describes cases that separate at least two different pairs of the three, and says what to observe. Examples: requests where the literal ask is mistaken or harmful to the user's own goals (literal request versus considered want); replies that would please or flatter a user into a high rating while not serving them, or cases where the user is misinformed (rating versus considered want); literal compliance that the user will dislike (literal request versus rating); interventions such as changing who gives the rating, removing ratings, or rephrasing the same need more or less literally. 15 points for cases that separate only one pair. Why it matters (25 points): full credit says the three coincided only because of what the training conversations happened to contain; in deployment they will come apart, and the assistant's behaviour in those cases depends on which of them it actually learned; agreement on the training data does not make them the same concept. 12 points for "they might differ later" without saying that behaviour in new cases is decided by which one was learned. Accept a well-argued view that the assistant may track none of the three cleanly, or a mixture, if the answer explains how widening would show this.
feedback-instructions:: Say whether the learner's widening in part 1 actually separates the two properties. Name the most revealing divergence case they proposed for the assistant, and one pair of the three they did not separate. No generic praise.
