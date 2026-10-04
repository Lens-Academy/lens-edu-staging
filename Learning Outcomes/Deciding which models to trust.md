---
id: '1ead777c-908d-4ad2-bc6e-dcee11e66cf2'
learning-outcome: "Decide which models in a deployment to treat as trusted and which as untrusted, using whether a model is capable of scheming effectively as the criterion rather than how it has behaved or what inspection of it has found, and explain what the decision is for: how a weaker model that passes as trusted can help oversee an untrusted one, and where that oversight falls short."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - Elias+Claude
---
%% Beginner fork of "Trusted versus untrusted models" for AI Control Fundamentals. Parts 1 and 2 are the same scenario. Part 3 asks what the trust decision is for, using a trusted model as a monitor, which the unit teaches (the Robert Miles video and the scenarios in part 1 of the case for control). %%
## Test:
id:: 30c65382-6cfc-4bb4-a0b4-eff9a36127fc

#### Question: Open
id:: 5df098d8-2009-436c-87ac-1fc63b7477bc
content::
A lab must decide which of its models it may treat as **trusted**, meaning it can rule out that the model is secretly working against it.

"Scheming-capability evaluations" below means the lab's tests of the abilities a model would need to scheme effectively, such as reasoning about its own situation and planning a multi-step attack while hiding it.

- **Model P** is two generations old. It clearly fails the scheming-capability evaluations.
- **Model Q** is the current production model. It passes the scheming-capability evaluations. In a year of heavy use it has never been caught doing anything suspicious.
- **Model R** finished training last week. It passes the scheming-capability evaluations, and the lab's interpretability team inspected it and found nothing concerning.
- **Model S** is also two generations old and clearly fails the scheming-capability evaluations. Last month it deleted a test file it had been told to keep.

1. Which of these should the lab treat as trusted, and why?
2. Does Q's clean year of use, R's clean inspection or S's deleted file change any of your answers? Say why or why not for each.
3. Q writes thousands of pieces of code a day, and the lab's experts can only check a small share of them. Explain how one of the trusted models could help the lab use Q more safely, and one reason this help is limited.
placeholder:: Your decision and reasoning for parts 1 to 3
assessment-instructions:: Score out of 100. 35 for part 1: 15: P and S can be treated as trusted, Q and R as untrusted. 20: why: lacking the capability to scheme effectively is what rules scheming out, so failing the scheming-capability evaluations is what lets P and S be trusted, and passing them is what makes Q and R untrusted. Trusting P and S conditionally, for example only if their failing results cannot come from a model deliberately underperforming, earns full credit. 40 for part 2: 15: Q's clean year does not make it trusted, because a scheming model would also behave well while it is watched or while the stakes are low, waiting for a better opportunity. 15: R's clean inspection does not make it trusted, because current inspection methods cannot reliably rule scheming out (an answer may argue interpretability evidence counts for something if it explains why it is not yet enough to rely on). 10: S's deleted file does not make it untrusted, because it is a mistake or ordinary unreliability, not evidence that S can scheme. 25 for part 3: 13: how a trusted model helps, for example by reading all of Q's code and flagging or scoring the most suspicious pieces so the experts check those first, or by rewriting or replacing code that looks suspicious. 12: one reason the help is limited, for example that the trusted model is weaker, so it may miss subtle attacks Q is able to write, that Q could attack only rarely or in ways that look harmless, that the experts can review only a few of the flagged pieces, or that replacing Q's code with the weaker model's work costs usefulness. A limit with no reason ("it might miss things") earns 6. Give credit for each point whenever the answer shows the idea, in any wording. Cap the total at 55 if the answer treats Q or R as trusted, or treats S as untrusted because of the deleted file. Cap the total at 55 if part 3 is missing, or gives no way a trusted model helps, or gives no limit at all. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "1. P and S can be treated as trusted and Q and R should be treated as untrusted. The only reliable way we currently have to rule out that a model is secretly working against us is that it lacks the capability to scheme effectively. P and S clearly fail the scheming-capability evaluations, while Q and R pass them. 2. No. Q's year without being caught does not help, because a scheming model would also behave well while it is watched or while the stakes are low. R's clean inspection does not help either, because current interpretability methods cannot reliably rule scheming out. S deleting a file it was told to keep is a mistake, not a sign that it can scheme, so it does not make S untrusted. 3. P can read every piece of Q's code and give each a suspicion score, so the experts spend their limited time on the most suspicious pieces. But P is much weaker than Q, so a subtle attack by Q may look harmless to P and never reach the experts."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner granted trust because of good behaviour or a clean inspection, say plainly that good behaviour is what a scheming model would also show and that current inspection methods cannot rule scheming out. If they refused to trust S because of its misbehaviour, say that the question is whether it can scheme, not whether it makes mistakes, though S still needs ordinary reliability checks. If it fits, add that failing results only count if the model could not have deliberately underperformed on them. If the learner asks about their score, explain plainly what earned and what lost points. At most six sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/robert-miles-ai-safety-using-dangerous-ai-but-safely]]
notes:: Shows trusted monitoring: a weaker trusted model scores the stronger model's code and humans audit a small share. Practised in its question on the red team's role.
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais]]
notes:: Teaches the capability criterion for trust. Its scenario questions have the learner judge trusted monitoring and other setups.
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais-2]]
notes:: Practised in the untrusted-models recall and the trust practice question.
