---
id: 'c804178e-94b7-4c4f-bf3f-954f24d361aa'
learning-outcome: "Decide which models in a deployment to treat as trusted and which as untrusted, using whether a model is capable of scheming effectively as the criterion rather than how it has behaved or what inspection of it has found, and explain why a model that passes evaluations of the capabilities scheming would require must be treated as untrusted rather than trusted."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: intermediate
authors:
  - Elias+Claude

---
## Test:
id:: b7fe629d-d045-4c77-a4fc-077d40ff07cd

#### Question: Open
id:: c425551f-8af8-4ce5-81b6-d814c19662a0
content::
A lab must decide which of its models it may treat as **trusted**, meaning it can rule out that the model is secretly working against it, for example so it can use that model to monitor the others.

"Scheming-capability evaluations" below means the lab's tests of the abilities a model would need to scheme effectively, such as reasoning about its own situation and planning a multi-step attack while hiding it. A model that passes them has those abilities.

- **Model P** is two generations old. It clearly fails the scheming-capability evaluations.
- **Model Q** is the current production model. It passes the scheming-capability evaluations. In a year of heavy use it has never been caught doing anything suspicious.
- **Model R** finished training last week. It passes the scheming-capability evaluations, and the lab's interpretability team inspected it and found nothing concerning.
- **Model S** is also two generations old and clearly fails the scheming-capability evaluations. Last month it deleted a test file it had been told to keep.

1. Which of these should the lab treat as trusted, and why?
2. Does Q's clean year of use, R's clean inspection or S's deleted file change any of your answers? Say why or why not for each.
3. What would have to change for your answer about Model Q to change?
placeholder:: Your decision and reasoning for parts 1 to 3
assessment-instructions:: Score out of 100. 35 for part 1: 15: P and S can be treated as trusted, Q and R as untrusted; 20: why: lacking the capability to scheme effectively is what rules scheming out, so failing the scheming-capability evaluations is what lets P and S be trusted, and passing them is what makes Q and R untrusted. Trusting P and S conditionally, for example only if their failing results cannot come from a model deliberately underperforming, earns full credit. 40 for part 2: 15: Q's clean year does not make it trusted, because a scheming model would also behave well while it is watched or while the stakes are low, waiting for a better opportunity; 15: R's clean inspection does not make it trusted, because current inspection methods cannot reliably rule scheming out (an answer may argue interpretability evidence counts for something if it explains why it is not yet enough to rely on); 10: S's deleted file does not make it untrusted, because it is a mistake or ordinary unreliability, not evidence that S can scheme. 25 for part 3: a sound condition under which Q could become trusted, such as evidence that Q actually lacks the capabilities (the evaluations were flawed or overestimated it), or a method that can reliably establish a model's intentions, which does not exist yet; 12 for a vague condition such as 'more testing'. A condition that only makes Q safe to use while it stays untrusted, such as passing a control evaluation or adding monitoring, earns nothing here unless the answer also names a route to ruling out scheming. Give credit for each point whenever the answer shows the idea, in any wording. Cap the total at 55 if the answer treats Q or R as trusted, or treats S as untrusted because of the deleted file. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "1. P and S can be treated as trusted and Q and R should be treated as untrusted. The only reliable way we currently have to rule out that a model is secretly working against us is that it lacks the capability to scheme effectively: P and S clearly fail the scheming-capability evaluations, while Q and R pass them. 2. No. Q's year without being caught does not help, because a scheming model would also behave well while it is watched or while the stakes are low, waiting for a better opportunity. R's clean inspection does not help either, because current interpretability methods cannot reliably rule scheming out; finding nothing is not evidence of absence. S deleting a file it was told to keep is a mistake, not a sign that it can scheme, so it does not make S untrusted. 3. For Q to become trusted, the lab would need evidence that Q does not actually have the capabilities, for example that the evaluations were flawed and overestimated it, or a method that can reliably establish what a model is trying to do, which does not exist yet. Passing a control evaluation or adding more monitoring would make Q safer to use, but Q would still be untrusted."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner granted trust because of good behaviour or a clean inspection, say plainly that good behaviour is what a scheming model would also show and that current inspection methods cannot rule scheming out. If they refused to trust S because of its misbehaviour, say that the question is whether it can scheme, not whether it makes mistakes, though S still needs ordinary reliability checks. If it fits, add that failing results only count if the model could not have deliberately underperformed on them, and that trusted models like P are weak, so they are of limited use as monitors of Q and R. If the learner asks about their score, explain plainly what earned and what lost points. At most six sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais]]
notes:: Teaches the capability criterion for trust.
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais-2]]
notes:: Practised in the untrusted-models recall and the trust practice question.
