---
id: 'c1b23d36-eeb5-4ae9-a885-569a92b824aa'
learning-outcome: "Refactor a concept that an alignment discussion depends on but uses inconsistently: find the conflicting demands that different claims place on it, propose a revised or split concept that meets those demands, and propagate the change by restating the original claims with the new concepts and checking which still hold."
topic: "[[../Domains and Topics/4 Agent Foundations/Agent foundations research]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Conceptual refactoring. AFFINE prerequisites: Ontology. Not yet copied into requires:. %%
## Test:
id:: 5fd67dd0-e650-4624-b2fc-4d272a1f0aa2

#### Question: Open
id:: 7a95474d-832c-42e6-a80b-5e9fd020a4d2
content:: A safety team keeps arguing about whether their language model 'has goals'. These are the statements people make:

1. 'The model has the goal of being helpful: it behaves helpfully across thousands of very different conversations.'
2. 'When asked to play a villain in a long role-play, the model pursues the villain's goal of winning, and does it competently.'
3. 'Systems with goals resist changes to their goals, so if the model has goals it will resist being fine-tuned.'
4. 'A thermostat has the goal of keeping the room at 20 °C.'
5. 'Whatever the model's goal is, it is whatever training rewarded.'

The team cannot agree whether the model has goals, and suspects the word is doing too many jobs. Work on the concept rather than on the answer:

- Show where these statements place demands on 'goal' that no single meaning can meet, using a concrete case that one meaning counts as a goal and another does not.
- Propose a revised concept, or a split into two or more concepts, that removes the conflict.
- Restate at least three of the five statements with your new concept or concepts, and say for each whether it now looks true, false, or open, and what would settle it.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. There is no single correct refactoring; grade whether the learner's process is specific and whether their revision does the work. Generic text about 'clarifying definitions' without engaging the five statements earns at most 15 in total.

**(a) Conflicting demands, 35 points.** Full credit: identifies at least two demands that pull in different directions, tied to the statements, with a concrete case that falls on different sides. Examples of acceptable conflicts: statement 4 counts any feedback system that keeps a variable near a set point as having a goal, while statement 3 requires a goal to produce resistance to modification, which a thermostat does not show; statement 2 attributes a goal to a character the model plays, while statement 1 attributes a goal to the model across contexts, so it is unclear whether goals belong to the model, the character, or the conversation; statement 5 locates the goal in the training signal, while statement 1 locates it in behaviour, and these can come apart. 18 points for one well-supported conflict. 8 points for naming a conflict with no concrete case.

**(b) Revised concept, 30 points.** Full credit: proposes a revision or split that resolves the identified conflicts, with each new concept stated precisely enough that the example cases can be sorted by it (for example: separating a system that keeps a variable near a set point from a system that plans over the long term and protects its objective from change; or separating goals of the model from goals of characters it simulates; or separating what training rewarded from what the system actually pursues in new situations). The revision must address the conflicts found in (a). 15 points if the new concepts are named but not defined clearly enough to sort cases.

**(c) Propagation, 35 points.** Full credit: restates at least three statements with the new concepts and, for each, says whether it now looks true, false or open, and what evidence or argument would settle the open ones. At least one restatement must show a real change, such as a claim that looked like a disagreement turning out to be two compatible claims, or a claim that holds for one new concept but not the other (for example, statement 3 plausibly holds only for the long-term, objective-protecting sense). 12 points per restatement up to 35, but at most 20 if no restatement changes anything.

Do not penalize a learner who argues that a statement should be dropped rather than restated, if they explain why.
feedback-instructions:: Tell the learner which conflict or restatement was most revealing and quote it. Name the single most useful improvement, usually a concept that is not yet precise enough to sort the thermostat, the villain role-play and the fine-tuning case, or a restatement that does not yet say what would settle it. Ask one follow-up question. No generic praise.
