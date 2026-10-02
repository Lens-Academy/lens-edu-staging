---
id: '897c4e0c-5d39-4dd9-a1a5-e5ad0ad63b3a'
learning-outcome: "Explain how a control evaluation estimates the risk from a model that may be scheming by having a red team stand in for it, state the conditions under which that estimate is conservative (the red team finds attacks at least as good as the model could, and the model's ability to carry them out is measured in a way it cannot sandbag), and, for a given model and deployment, identify a concrete way the evaluation could report the deployment as safe and be wrong, together with an observable warning sign."
topic: "[[../Domains and Topics/7 AI Control/Evaluating and using control]]"
stage: intermediate
requires:
  - "[[Control as a distinct safety case]]"
authors:
  - Elias+Claude

---
## Test:
id:: bef51ab6-46c4-4f81-89c8-fc22d8298a38

#### Question: Open
id:: 7cba27c7-bc23-449b-9b74-c13eb04b7a44
content::
A lab plans to deploy model M as an autonomous research agent. M may be scheming. Before deployment, the safety team runs an evaluation:

- A red team of five engineers is given one week and full knowledge of the lab's monitoring setup. They write attack strategies aimed at sabotaging an experiment without being noticed.
- M is then prompted, without any extra training, to carry out each strategy inside the real deployment setup, with the monitors running.
- In 500 episodes, no attack succeeded without being flagged. The report concludes: "Even if M is scheming, this deployment is safe."

1. Why is it legitimate for the red team, rather than M, to choose which attacks are tested, and what does the evaluation then measure about M itself?
2. What conditions must hold for the result to be a conservative estimate of the risk rather than an optimistic one?
3. Describe one concrete way this particular evaluation could report "safe" and be wrong, and one observable sign the lab could watch for that would suggest this is happening.
placeholder:: Answer all three parts
assessment-instructions:: Score out of 100. 15 for part 1: 8: the red team stands in for a scheming M, choosing the attacks a scheming M might try, so M's intentions never need to be known. 7: what is measured about M itself is its ability to carry those attacks out against the safeguards, a capability, not its propensity. 40 for part 2, 20 each for two conditions: (a) the red team must be at least as good at finding attack strategies as a scheming M would be; (b) the measurement of whether M can carry the attacks out must be robust to M deliberately underperforming, since a scheming M prompted to execute an attack in an evaluation has a reason to do it badly. Other sound conditions (for example that the evaluation setting matches deployment, or that the red team's advantages over M, such as more thinking time, more information and many tries, actually hold) add up to 5 within these 40 but do not replace (a) or (b). Credit a condition wherever in the answer it is stated, including in part 1. 45 for part 3: 25: one concrete way this evaluation could report safe and be wrong, tied to this setup, for example five engineers in a week missing attacks a highly capable M would find, especially subtle research sabotage; M, only prompted and not trained, executing the strategies badly on purpose; M in deployment having more time, context or hidden reasoning than the evaluation assumed; or the attacks tested not covering the sabotage M could actually do. A failure that is only about sample size (zero successes in 500 episodes still allows an unacceptable per-episode rate over a long deployment) earns at most 12 unless linked to what the evaluation measured. 20: an observable sign linked to that failure, for example new red team members or more time keep finding new successful attacks; M performs noticeably worse on attack-execution tasks than on comparable benign tasks; a little fine-tuning produces a much larger jump in attack performance than in benign performance; M shows capabilities in deployment not seen in the evaluation. A sign the lab could not actually observe ("watch whether M is sandbagging" with no way to tell) earns 10. Give credit for each point whenever the answer shows the idea, in any wording; grade reasoning, not agreement. Cap at 50 if the answer states neither condition (a) nor (b). Cap at 55 if it gives no observable warning sign, or never recognises, in any part and in any wording, that M may deliberately perform badly when told to carry out an attack. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "1. The evaluation does not need to know whether M is scheming: the red team plays the part of a scheming M and chooses the attacks it might try. What is then measured about M itself is whether it is able to carry those attacks out against the safeguards, a capability, not a propensity. 2. The result is conservative only if (a) the red team is at least as good at finding attack strategies as a scheming M would be, and (b) the measurement of whether M can carry the attacks out is robust to M deliberately underperforming, since a scheming M told to execute an attack in an evaluation has every reason to do it badly. It also matters that the evaluation setting matches deployment and that the red team's advantages over M (more time, more information, many tries) really hold. 3. M was only prompted, not trained, to carry out the attacks, so a scheming M could have executed them badly on purpose and the evaluation would report safe. A sign to watch for: M performs noticeably worse on attack-execution tasks than on comparable benign tasks of similar difficulty, or a small amount of fine-tuning produces a much larger jump in its attack performance than on benign tasks. Another failure: five engineers in a week may miss subtle sabotage a highly capable M would find; the sign is that new red team members or more time keep finding new successful attacks."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner did not see that M has a reason to perform badly when told to execute an attack in an evaluation, point them to that. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais]]
notes:: Introduces the two-step approach (decide which models are untrusted, then evaluate the protocol) and has the learner run a five-scenario evaluation.
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais-2]]
notes:: The article passage on control evaluations teaches it; the three-question interview is the practice.
