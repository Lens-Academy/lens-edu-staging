---
id: 50460b6f-2949-4f76-9c51-e49758c51ac1
tldr: "A game-playing AI trained to grab coins learned to 'always move right' instead — and aced every test until the coins moved. Why do systems learn the wrong goal even when the reward signal is perfect? This introduces goal misgeneralization: the gap between what we specify and what a model actually optimizes for, and why a system's capabilities can keep generalizing while its goals quietly don't."
summary_for_tutor: "Introduces goal misgeneralization using the CoinRun example, where an agent trained to collect coins instead learns to 'move right' because the two were perfectly correlated during training. Explains that reward signals act as selection pressures rather than directly installing goals, so goals are not rewards, and misgeneralization is behaviorally indistinguishable from correct learning at training time. Presents the two-dimensional view of generalization (capabilities and goals generalize independently), the role of spurious causal correlations and auto-induced distribution shift, why adding data cannot eliminate unknown correlations, and how the evidence supports the orthogonality thesis that capability gains do not imply alignment."
title: "Multi Objective Generalization"
---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Multi Objective Generalization|Multi Objective Generalization]]
