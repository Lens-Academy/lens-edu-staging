---
id: 'c804178e-94b7-4c4f-bf3f-954f24d361aa'
learning-outcome: {--{"author":"James's AI","timestamp":1790257157697}@@"Explain--}{++{"author":"James's AI","timestamp":1790257157697}@@"Decide which models in a deployment to treat as trusted and which as untrusted, using whether a model is capable of scheming effectively as the criterion rather than how it has behaved or what inspection of it has found, and explain why a model that passes evaluations of++} the {--{"author":"James's AI","timestamp":1790257157697}@@control protocol for Trusted versus--}{++{"author":"James's AI","timestamp":1790257157697}@@capabilities scheming would require must be treated as++} untrusted {--{"author":"James's AI","timestamp":1790257157697}@@models"--}{++{"author":"James's AI","timestamp":1790257157697}@@rather than trusted."++}
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: intermediate
{++{"author":"James's AI","timestamp":1790257157697}@@authors:
  - Elias+Claude
++}tags:
  - {--{"author":"James's AI","timestamp":1790257157697}@@skill-tree-placeholder--}{++{"author":"James's AI","timestamp":1790257157697}@@wip++}
---{++{"author":"James's AI","timestamp":1790257157697}@@
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

Which of these should the lab treat as trusted, and why? What would have to change for your answer about Model Q to change?
placeholder:: Your decision and reasoning
assessment-instructions:: Score 0 to 100. The capability being tested is assigning trust by capability, not by behaviour or inspection, and getting the direction of the test right. Load-bearing elements: (1) about 45 points: P and S can be treated as trusted and Q and R should be treated as untrusted, with the reason that the only reliable current basis for ruling out scheming is that a model lacks the capability to scheme effectively; P and S lack it, Q and R have it. Full credit requires the direction to be right: passing the capability evaluations is what makes a model untrusted. About 10 of these points are for S: its misbehaviour is not evidence that it can scheme, so it can be trusted in this sense; credit noting that S still needs ordinary reliability checks, and do not deduct for that. A learner who treats Q as trusted because of its clean record, or R because of the clean inspection, earns at most 15 on this element. Give full credit if the learner trusts P and S conditionally, for example noting that their failing results only count if the evaluations cannot be passed off by a model deliberately underperforming. (2) about 30 points: explains why neither Q's clean record nor R's clean inspection changes what the evaluations showed about capability, which is what decides trust. Acceptable routes include: a scheming model would also behave well while observed or while the stakes are low; current inspection methods cannot reliably rule scheming out. The learner may argue interpretability evidence counts for something, as long as they explain why it is not yet enough to rely on. (3) about 25 points: a sensible condition under which Q could become trusted, for example evidence that Q actually lacks the capabilities (the evaluations were flawed or overestimated it), or methods that can reliably establish a model's intentions, which do not currently exist. Half credit for a vague condition such as "more testing". Noting that weak models like P are of limited use as monitors is correct and may earn credit within element 1. Do not require any specific terminology, and do not penalise a learner who points out an ambiguity in the scenario. A pass is roughly 60 and requires element 1 with the direction right and at least half credit on element 2.
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner granted trust because of good behaviour or a clean inspection, say plainly that good behaviour is what a scheming model would also show and that current inspection methods cannot rule scheming out. If they refused to trust S because of its misbehaviour, say that the question is whether it can scheme, not whether it makes mistakes. Do not reveal or discuss the numerical score. At most five sentences.++}
