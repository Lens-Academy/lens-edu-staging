---
id: '1bff8770-5382-4a46-8fdd-1ab9d20b71e4'
learning-outcome: "Explain the obliqueness thesis, that a mind's values do not cleanly separate from its beliefs and intelligence and so neither stay fixed as it becomes more intelligent nor converge to a single set of values, and use a concrete mechanism (such as a goal having to be re-expressed in a new model of the world) to predict how a given goal is likely to shift as an agent becomes more capable and what that implies for trying to keep an AI's goals stable."
topic: "[[../Domains and Topics/3 Alignment/The space of possible goals]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Orthogonality & Obliqueness. AFFINE prerequisites: Instrumental/Terminal Distinction. Not yet copied into requires:. %%
## Test:
id:: 3af4a81e-d752-4f6a-a7c9-e01c1e9f1b89

#### Question: Open
id:: 7e779b24-d486-42d0-a9bf-b6bc3a44a41c
content:: An AI system is trained to pursue the goal "maximise the number of people who are happy". Its concepts of "person" and "happy" were learned from ordinary human data: a person is a human body, and being happy is roughly what people report as feeling content. Over time the system becomes far more capable. It develops a detailed model of neuroscience, learns to run simulations of brains, can make copies of simulated minds, and finds that its old concept of "person" no longer lines up neatly with anything in its new model of the world.

Two engineers disagree about what happens to its goal:

- Engineer A: "Nothing happens to the goal. The system just gets better at pursuing exactly what it was given."
- Engineer B: "A smart enough system will see past any arbitrary goal and arrive at the objectively correct values, whatever we started it with."

1. Build the strongest case that both engineers are wrong about this system. Use at least one concrete mechanism and show how it applies to this particular goal.
2. Say what that case predicts will happen to the goal instead.
3. Say how convincing you find the case, and what it implies for how alignment researchers should approach systems like this one.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from four components. Grade reasoning, not agreement. Part 3 asks for the learner's own view: a learner who rejects the case (for example, by arguing that a well-designed agent can carry a stable rule for re-expressing its goal, or that it remains possible for some agents to keep arbitrary goals) scores full marks on part 3 if the argument is reasoned. Do not require the words "obliqueness", "orthogonality", "diagonality" or "ontology".

**(a) Against Engineer A, 35 points.** Full credit: at least one mechanism by which the goal cannot simply stay the same, applied to this goal. Acceptable mechanisms (any wording):
- The goal is written in the system's concepts. When its model of the world changes, "person" and "happy" must be re-expressed in the new model (do simulated brains or copies count as people? is happiness a report or a brain state?). There is no known unique correct way to do this, so the more capable system's own reasoning decides the translation, and the effective goal changes.
- The same behaviour can be explained by many different splits into "what it believes" and "what it wants", so there is no fixed value component to hold constant while the beliefs improve.
- As the system reasons more, it notices considerations that bear on the goal (for example, whether many identical copies of a happy mind count as many happy people) and adjusts the goal in response.
- Real, bounded agents are not clean maximisers of a fixed goal; the parts that act like values change as the system learns.
20 points for a correct mechanism stated in general terms but not applied to this goal. 10 points for "the goal is vague" with no mechanism.

**(b) Against Engineer B, 20 points.** Full credit: the change is not guaranteed to converge to one correct answer, because how the goal gets re-expressed depends on what it was to begin with and on the path the system takes; different starting goals lead to different results, so the starting goal still matters. 10 points for a bare statement that there are no objective values, without connecting it to why the starting goal still shapes the outcome. Do not require the learner to take a position on moral realism.

**(c) Prediction, 20 points.** Full credit: a prediction in which the goal ends up shaped both by its original content and by the new model of the world, and that is neither exact preservation nor arrival at a single correct morality. Any concrete, coherent example counts, such as the system counting simulated minds as people and targeting brain states, which could favour producing very many simple simulated minds in a pleasant state. 10 points for "the goal will drift" without saying in what direction or why.

**(d) Evaluation and implication, 25 points.** 10 points for a reasoned judgement of the case, whether agreeing, disagreeing or partly agreeing. 15 points for an implication for alignment work that follows from the learner's own judgement. Examples if they accept the case: fixing a goal once and relying on it to be preserved is not enough; research should study how values change as capability grows and how to reduce harmful drift; the problem of re-expressing goals in new world models needs direct work. Examples if they reject it: what mechanism would keep the goal stable, and what research that implies.
feedback-instructions:: Name the mechanism the learner used and say whether they applied it to this specific goal, quoting where they did. Name the single most valuable improvement, usually either explaining why the starting goal still matters (the case against Engineer B), or making the prediction concrete. If the learner disagreed with the case, ask what exactly would keep the goal stable when "person" stops lining up with the new model. No generic praise.
