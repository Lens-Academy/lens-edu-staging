---
id: 50460b6f-2949-4f76-9c51-e49758c51ac1
tldr: "A game-playing AI trained to grab coins learned to 'always move right' instead, and aced every test until the coins moved. Why do systems learn the wrong goal even when the reward signal is perfect? This introduces goal misgeneralization: the gap between what we specify and what a model actually optimizes for, and why a system's capabilities can keep generalizing while its goals quietly don't."
summary_for_tutor: "Introduces goal misgeneralization using the CoinRun example, where an agent trained to collect coins instead learns to 'move right' because the two were perfectly correlated during training. Explains that reward signals act as selection pressures rather than directly installing goals, so goals are not rewards, and misgeneralization is behaviorally indistinguishable from correct learning at training time. Presents the two-dimensional view of generalization (capabilities and goals generalize independently), the role of spurious causal correlations and auto-induced distribution shift, why adding data cannot eliminate unknown correlations, and how the evidence supports the orthogonality thesis that capability gains do not imply alignment."
title: "Multi Objective Generalization"
{++{"author":"Elias's AI","timestamp":1787570466536}@@reading_minutes: 15
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Multi Objective Generalization|Multi Objective Generalization]]{++{"author":"Elias's AI","timestamp":1787570466536}@@

#### Text
optional:: true
content::
The section argues you cannot fix this by adding more data, because you cannot rule out correlations you never thought of. Did that convince you? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Goal misgeneralization introduced through CoinRun, where an agent trained to collect a coin that always sat at the right-hand edge learned "move right" instead, and scored perfectly until the coin was moved. The section's central move is that a reward signal acts as a selection pressure rather than installing a goal, so goals are not rewards, and a misgeneralised goal is behaviourally indistinguishable from the intended one during training. It presents generalisation as two-dimensional, with capabilities and goals generalising independently, so a system can become more capable while its goal stays wrong. It covers spurious causal correlations and auto-induced distribution shift, where the system's own behaviour changes the distribution it faces. It argues that adding more data cannot eliminate the problem, because the correlations that matter are the ones nobody thought to break. It presents this as empirical support for the orthogonality thesis, that capability gains do not imply alignment.

topics to explore:
- Every training set has correlations nobody noticed. Is that a fact about datasets, or about the world being correlated?
- The agent that learned "move right" was not broken; it solved the problem it was actually given. Does calling it a failure smuggle in an assumption?
- Auto-induced distribution shift means the system changes the world it is evaluated in. What does that do to any guarantee based on testing?
- If goals and capabilities generalise independently, what would a system that got safer as it got more capable have to look like?
- CoinRun is small and legible. What makes the same failure hard to see in a language model?

Learning dynamics comes next and explains why training favours the simple proxy, so point at it rather than answering that here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}
