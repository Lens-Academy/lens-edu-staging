---
id: '41a84774-adac-4ff9-9a38-b34175862312'
learning-outcome: "Apply the factored-space (finite factored set) view of causality to a small joint distribution: consider variables defined from the given ones rather than only the given variables, find which of them are independent, and use this to infer a causal order that a causal graph over the given variables leaves undetermined, explaining why considering every definable variable, including deterministic functions of others, makes the difference."
topic: "[[../Domains and Topics/4 Agent Foundations/Natural abstraction]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Factored Space Models (formerly Finite Factored Sets). AFFINE prerequisites: Ontology. Not yet copied into requires:. %%
## Test:
id:: 1d4afab0-5587-4889-917e-437a22aabb28

#### Question: Open
id:: 55f1647a-b70a-49a6-961a-e4b185182067
content:: Two binary signals, S and T, are recorded many times. Their joint distribution is:

| S | T | Probability |
|---|---|---|
| 0 | 0 | 0.14 |
| 1 | 0 | 0.06 |
| 0 | 1 | 0.24 |
| 1 | 1 | 0.56 |

Assume these probabilities are exact, and that every independence in the data reflects the underlying structure rather than a numerical coincidence.

1. Using a causal graph whose only variables are S and T (with any hidden common causes allowed), what can you conclude about causal direction from this data?
2. Using the factored-space (finite factored set) approach, what, if anything, can you infer about causal direction? Show the calculation that supports your answer.
3. Why can the second approach see something the first cannot?
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Accept any correct notation or wording.

**(a) Causal graph over S and T, 15 points.** Full credit: S and T are dependent (for example, P(S=1 given T=0) = 0.3 but P(S=1 given T=1) = 0.7), and dependence alone is compatible with S causing T, T causing S, or a common cause, so no direction can be identified. 7 points for "no direction" without showing or stating the dependence.

**(b) The factored-space inference, 55 points.** Full credit requires: (i) defining a derived variable, U = S XOR T (whether S and T differ), or an equivalent such as its negation (15 points); (ii) showing that T and U are independent: P(U=1) = 0.30, P(U=1 given T=0) = 0.06/0.20 = 0.30, P(U=1 given T=1) = 0.24/0.80 = 0.30 (15 points); (iii) noting that S is not independent of U (for example, P(U=1 given S=0) = 0.24/0.38, about 0.63, but P(U=1 given S=1) = 0.06/0.62, about 0.10), so the situation is not symmetric (5 points); (iv) the conclusion: T and U can be modelled as independent factors, S is determined by T and U together, so the history of T is strictly contained in the history of S: T comes before S, that is, T causes S (20 points). Equivalent reasoning in causal-graph terms is also acceptable for (iv), for example adding U as a variable and showing that the only causal structures consistent with the dependences and independences among S, T and U (with S a deterministic function of T and U) have T causing S. An answer that reaches the direction S causes T loses the 20 points for (iv). An answer that only states "T causes S" without the independence calculation earns at most 20 points for this component.

**(c) Why the second approach sees more, 30 points.** Full credit: a causal graph takes the list of variables as given, and the independence between T and U is invisible unless U is considered; the factored-space approach treats every variable that can be defined on the sample space, including deterministic functions of the given variables such as U, as a candidate, so it uses independences a fixed variable list misses. Credit also for the related point that causal graphs handle deterministic relationships poorly (a variable that is a deterministic function of others generally breaks the assumption that every independence in the data is shown by the graph), while factored spaces represent such relationships directly, which matters when abstract variables are functions of lower-level data. Credit an answer that notes that the inference depends on the stated assumption that the independence is structural rather than a coincidence. 15 points for "it considers more variables" without saying why that reveals the direction.
feedback-instructions:: Say whether the learner found the derived variable and checked the independence numerically. If their conclusion or direction is wrong, point to the step where it went wrong without giving the full solution. Name the strongest part of their explanation in part 3. No generic praise.
