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
assessment-instructions:: Score 0 to 100. The capability being tested is understanding the logic of control evaluation and where it breaks. Load-bearing elements: (1) about 15 points: the red team stands in for a scheming M, choosing the attacks a scheming M might try, so M's intentions never need to be known (condition (a) itself is credited under element 2, not here). What is measured about M itself is its ability to carry those attacks out against the safeguards, a capability, not its propensity. (2) about 40 points: two conditions in any wording, about 20 each: (a) the red team must be at least as good at finding attack strategies as a scheming M would be; (b) the measurement of whether M can carry the attacks out must be robust to M deliberately underperforming, since a scheming M prompted to execute an attack in an evaluation has a reason to do it badly. Additional sound conditions (for example that the evaluation setting matches deployment, or that the red team's advantages over M such as more thinking time, more information and many tries actually hold) may add up to 5 points within this element but do not replace (a) or (b). Credit a condition wherever in the answer it is stated, including in part 1. (3) about 45 points: about 25 for one concrete failure tied to this setup, and about 20 for an observable sign linked to that failure. Examples of failures: five engineers in a week may miss attacks a highly capable M would find, especially subtle research sabotage; M, only prompted and not trained, may execute the red team's strategies badly on purpose; M in deployment may have more time, context or hidden reasoning than the evaluation assumed; the attacks tested may not cover the kinds of sabotage M could actually do. A failure that is only about sample size (for example that zero successes in 500 episodes still allows a per-episode success rate that is unacceptable over a long deployment) is true but earns at most half of the failure points unless linked to what the evaluation measured. Examples of observable signs: new red team members or more time keep finding new successful attacks; M performs noticeably worse on attack-execution tasks than on comparable benign tasks of similar difficulty; a small amount of fine-tuning produces a much larger jump in M's attack performance than it does on comparable benign tasks, which suggests M was holding back; M shows capabilities in deployment not seen in the evaluation. The sign must be something the lab could actually observe; "watch whether M is sandbagging" with no way to tell earns half credit on the sign. Gating: an answer that states neither condition (a) nor (b) cannot score above 50; an answer that gives no observable warning sign cannot score above 55; an answer that never recognises, in any part and in any wording, that M may deliberately perform badly when told to carry out an attack cannot score above 55. Do not require any author's name or specific terminology such as "sandbagging" or "red team". Grade reasoning, not agreement: a learner who argues a well-run evaluation is stronger than this one looks can still score well if they meet the elements. A pass is roughly 60.
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner did not see that M has a reason to perform badly when told to execute an attack in an evaluation, point them to that. Do not reveal or discuss the numerical score. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais]]
notes:: The article passage on control evaluations teaches it; the three-question interview is the practice.
