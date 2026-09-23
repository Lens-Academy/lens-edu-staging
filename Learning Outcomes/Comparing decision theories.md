---
id: 'a3cadaff-eedf-4419-8966-c0c9e9a6191f'
learning-outcome: "Given an unfamiliar decision problem, derive what causal, evidential and updateless (functional) decision theory each recommend from the kind of counterfactual each uses and whether it updates on what it has already observed, and evaluate a claim that one theory 'performs better' on the problem by identifying which counterfactual the proposed performance measure already assumes."
topic: "[[../Domains and Topics/4 Agent Foundations/Decision theory]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Decision Theories. AFFINE prerequisites: Decision theory. Not yet copied into requires:. %%
## Test:
id:: 2cfec5f3-a078-4861-800e-1f4fe6f7047a

#### Question: Open
id:: 83c38f30-a507-4456-a268-d0e7d7ec4609
content:: A cloud provider has a highly accurate method for predicting how an AI agent's decision procedure will behave (it is right 99% of the time). It offers a large block of compute, worth 1,000 units to the agent, but only to agents it predicts will later pay back 100 units voluntarily. Repayment cannot be enforced, and the provider will never deal with this agent again.

Agent X has already received the compute. It now decides whether to pay back the 100 units.

1. What do causal decision theory (CDT), evidential decision theory (EDT) and an updateless decision theory such as functional decision theory (FDT/UDT) each recommend here? For each, say which feature of the theory produces its recommendation.
2. A researcher reports: "We simulated 10,000 agents of each type facing this provider. The FDT agents ended with far more compute than the CDT or EDT agents, so FDT performs better." Evaluate this claim. What does the researcher's measure assume, and how might a defender of CDT reply?
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not which theory the learner prefers. A learner who argues that CDT, EDT or FDT gives the right answer here can earn full marks if the analysis is correct.

**(1) Recommendations, 50 points.**
- CDT (15 points): does not pay. Paying now cannot cause the past prediction or the compute already received, so it only costs 100. The feature: it evaluates actions by their causal effects (an intervention on the action).
- EDT (15 points): does not pay. Having already observed that it received the compute, it conditions on that observation, and paying gives no further good news, only a cost. The feature: it conditions on its action and on what it has observed. Accept, as a strong addition, that an EDT agent would want to commit to paying before the prediction is made, if it could.
- FDT/UDT (20 points): pays. It evaluates the output of its decision procedure, which the provider's prediction also depended on: agents whose procedure pays are the ones that receive the compute. The feature: it asks what happens if its procedure outputs "pay" (a logical or subjunctive counterfactual) and/or does not update on having already received the compute (it chooses the policy that would have been best before the prediction). Either feature, correctly explained, earns full credit.
10 points for each recommendation that is right but has no correct reason.

**(2) Evaluating the performance claim, 50 points.** Full credit needs: (a) the measure compares agents that were treated differently: it counts the compute given to each type of agent, which already assumes that "what would have happened if this agent had had a different decision procedure, before the prediction" is the right comparison, a counterfactual that favours policy-level or updateless theories (20 points); (b) a CDT defender's reply: at the moment X decides, the compute is already received, and a CDT agent who pays is simply 100 units poorer than one who does not; the FDT agents did better because they faced a more favourable situation (they were given compute), not because their choice at that moment was better (20 points); (c) a conclusion that follows from the analysis, for example that "performs better" is not neutral here because each theory's measure of performance builds in its own counterfactual, or a reasoned argument that one measure is nonetheless the right one for designing AI agents (10 points). Accept "why aren't you rich?" style arguments for FDT if the learner also states the measure's assumption.
feedback-instructions:: Tell the learner whether they tied each recommendation to the counterfactual the theory uses or to whether it updates. Name the strongest point in their evaluation of the researcher. Then give the single most useful improvement, for example: stating exactly which comparison the researcher's measure makes, or giving the CDT reply in its strongest form. No generic praise.
