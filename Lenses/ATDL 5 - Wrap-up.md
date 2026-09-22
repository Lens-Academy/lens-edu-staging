---
id: '9d646e86-3f82-432a-99ca-92de894290a9'
title: "Day 5 and the week: wrap-up"
tldr: "Check your prediction about duplicate documents, then look back over the week: what would it take for this theory to make a trained model safer?"
summary_for_tutor: "Closing page for Day 5 (Iliad B.5, Data Attribution) and for the week-long course. Revisit the predict-first answer, then one reflection connecting the week's theory back to Day 1's alignment problem, for the final group meeting."
authors:
  - Louis Jaburi
source_url: https://github.com/iliad-team/iliad-intensive/tree/d2792cbf53158db2a5729ff7d431a53869b64624/tex/data-attribution
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 3
tutor_minutes: 15
---

#### Question: Open
id:: d8e60be2-a2c8-4954-b482-e6d43dd5db65
content::
\## Check your prediction

Scroll back to **Day 5: Start here**, copy your prediction about removing one of two documents, and paste it at the top. In two or three sentences: what does Section 1 say about it, and does the route you chose today handle this case any better than leave-one-out?
feedback-instructions:: The student is finishing Day 5 (Iliad B.5, Data Attribution) and revisiting their predict-first answer about removing one of two documents that state the same fact. Section 1: leave-one-out attribution gives each copy zero credit (overdetermination); Shapley values give each about half and are exponentially expensive. Judge their claim about their chosen route only against what that route's section of the worksheet says; if you are not sure what the method would output for two identical documents, say so and ask them to work it out rather than asserting it. In 80 to 150 words: say whether their prediction matched Section 1, and check their claim about their chosen route; if they claim a method solves overdetermination, ask what that method would output for the two copies. If they did not paste the prediction, ask them to. No praise words.

#### Question: Open
id:: 0c7add93-6607-4597-94ce-79715ec55efa
content::
\## Looking back over the week

On Day 1 you met training stories, and inner misalignment as a goal that generalizes wrongly even under a correct reward. Pick **one** tool from Days 2 to 5 (for example the program synthesis hypothesis, the local learning coefficient, the rich regime's order of learning, or influence functions). In four to six sentences: how could that tool, if the theory behind it matured, help someone check a training story before deploying a model? Then name the biggest gap between what the tool does today and what that check would need. Bring this to the final group meeting.
feedback-instructions:: The student is finishing a one-week course built from the Iliad Intensive: Day 1 AI alignment introduction (alignment targets, training stories, outer and inner misalignment, goal misgeneralization, inductive biases, goal-directedness, risk views), Day 2 mysteries of deep learning (approximation, generalization, optimization, representational alignment, in-context learning, program synthesis hypothesis), Day 3 singular learning theory (degeneracy, local learning coefficient, Watanabe free energy formula, Bayesian phase transitions), Day 4 training dynamics of deep linear networks (saddle-to-saddle rich regime, lazy regime, NTK, implicit bias), Day 5 data attribution (counterfactuals, Shapley values, influence functions, Bayesian influence functions, unrolling). They picked one tool and described how it could help check a training story, and the gap between today and that use. In 100 to 180 words: restate their proposed use in one sentence; check that the tool actually measures what they say it does (correct a misstatement in one sentence); say whether the gap they named is the real bottleneck or whether an earlier one exists (for example, toy models versus frontier networks, in-distribution versus out-of-distribution generalization, or cost); ask one question for the group meeting. Do not argue them toward optimism or pessimism. No praise words.
