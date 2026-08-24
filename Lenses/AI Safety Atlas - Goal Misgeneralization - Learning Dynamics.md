---
id: 3d264f14-ac6a-40ee-a711-820978eb2766
title: "Learning Dynamics"
tldr: "Training doesn't install a goal; it searches a vast landscape of possible algorithms and rolls into whichever valley is easiest to reach. Show a network red curved 'thneebs' and it learns 'red,' not the shape. This section explains loss landscapes, path dependence, and the simplicity bias that quietly steers models toward simple proxies over the goals we actually intended."
summary_for_tutor: "Covers learning dynamics in the Goal Misgeneralization chapter of the AI Safety Atlas. Frames training as a search through algorithm/parameter space, where many behaviorally indistinguishable algorithms can pursue different goals (illustrated by the 'thneeb' color-vs-shape example and 100 identically-trained BERT models). Develops three concepts: loss landscapes (geometry of wide robust basins vs sharp brittle peaks determining discoverability), path dependence (whether different initializations converge to the same algorithm, high vs low), and inductive biases, especially simplicity bias (SGD's Occam's-razor preference for simple correlations) and speed bias, explaining why training systematically favors simple proxy goals over the intended causal ones."
reading_minutes: 14
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Learning Dynamics|Learning Dynamics]]

#### Text
optional:: true
content::
Training is described as rolling into whichever valley is easiest to reach, so simple proxies win by default. Did the loss-landscape account or the empirical examples convince you more? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Why training systematically ends up with the proxy rather than the intended goal. Training is framed as a search through a space of possible algorithms, where many behaviourally indistinguishable algorithms pursue different goals: shown a set of red curved shapes called thneebs, a network learns "red" rather than the shape, and a hundred identically trained models can land in different places. Three concepts do the work. Loss landscapes, where the geometry matters, with wide robust basins being easier to fall into than sharp brittle peaks, so discoverability rather than correctness decides what gets learned. Path dependence, whether different starting points converge on the same algorithm or not. And inductive biases, particularly simplicity bias, gradient descent's preference for simple correlations, and speed bias, its preference for algorithms that compute an answer quickly.

topics to explore:
- Simplicity bias is usually described as a good thing, the reason models generalise at all. Here it is the villain. Are those the same mechanism?
- If the intended goal sits in a sharp narrow basin, is the problem the goal, the landscape, or the optimiser?
- A hundred identically trained models landing in different places is evidence about variance. What does it tell you about any single deployed model?
- Speed bias favours algorithms that answer fast. Does that push toward heuristics and away from anything that looks like reasoning about a goal?
- If this account is right, would changing the optimiser change which goals get learned?

Goal-directedness comes next and asks how purposefully a system pursues whatever it learned, so stay with the learning question here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.
