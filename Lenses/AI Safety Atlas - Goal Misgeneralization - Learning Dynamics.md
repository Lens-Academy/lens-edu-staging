---
id: 3d264f14-ac6a-40ee-a711-820978eb2766
title: "Learning Dynamics"{++{"author":"Elias's AI","timestamp":1783848632786}@@
tldr: "Training doesn't install a goal; it searches a vast landscape of possible algorithms and rolls into whichever valley is easiest to reach. Show a network red curved 'thneebs' and it learns 'red,' not the shape. This section explains loss landscapes, path dependence, and the simplicity bias that quietly steers models toward simple proxies over the goals we actually intended."
summary_for_tutor: "Covers learning dynamics in the Goal Misgeneralization chapter of the AI Safety Atlas. Frames training as a search through algorithm/parameter space, where many behaviorally indistinguishable algorithms can pursue different goals (illustrated by the 'thneeb' color-vs-shape example and 100 identically-trained BERT models). Develops three concepts: loss landscapes (geometry of wide robust basins vs sharp brittle peaks determining discoverability), path dependence (whether different initializations converge to the same algorithm, high vs low), and inductive biases, especially simplicity bias (SGD's Occam's-razor preference for simple correlations) and speed bias, explaining why training systematically favors simple proxy goals over the intended causal ones."++}
---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Learning Dynamics|Learning Dynamics]]
