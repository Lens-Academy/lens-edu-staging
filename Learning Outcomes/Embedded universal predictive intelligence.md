---
id: '361d43f2-3490-437f-bee2-9e476ee22c6f'
learning-outcome: "Explain why an agent that predicts its own actions as part of the world it models treats its own choice as evidence about what functionally similar agents will choose, use this to predict how such an agent acts in a social dilemma compared with an agent that treats its action as an outside intervention, and identify how that prediction, and the agent's exposure to exploitation, depend on how similar the other agents actually are."
topic: "[[../Domains and Topics/4 Agent Foundations/Multi-agent and hierarchical agency]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: MUPI (Embedded Universal Predictive Intelligence). AFFINE prerequisites: Decision theory. Not yet copied into requires:. %%
## Test:
id:: 7e923ef9-b208-4273-8871-e1ddaa727805

#### Question: Open
id:: d4c50f64-d8b3-4d33-9adb-16352a9187d3
content:: Two delivery companies each use an AI agent to decide, once a day, whether to limit its fleet's use of a shared public charging network (Cooperate) or to take as much as it can (Defect). The daily payoffs to each company are:

- both Cooperate: 3 each;
- both Defect: 1 each;
- one Cooperates and the other Defects: 0 to the one that cooperates, 5 to the one that defects.

The agents cannot communicate or make binding agreements. There are two kinds of agent:

- **Agent E** uses one predictive model of the whole world, including itself. For each action, it predicts what will happen given that it takes that action, and picks the action with the best predicted result.
- **Agent C** treats its own action as an outside intervention that tells it nothing about the rest of the world, and picks the action with the best caused result.

**Case 1:** both companies licensed the same base model with the same fine-tuning, and each agent knows this. **Case 2:** the rival's agent is known to run a fixed rule, "always take as much as you can".

1. In each case, what does Agent E choose, and what does Agent C choose? Explain the reasoning each one uses.
2. The operator of an E agent asks: "If our agent cooperates because it thinks the other agent is like it, can it be exploited?" Explain when it could be, and what that depends on.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. The question asks what each agent does, not which agent is rational: a learner who argues that Agent C's reasoning is the correct one, or that Agent E's is, loses nothing if the predictions and reasons are right. Terms such as EDT, CDT, "embedded agent" or "functional similarity" are not required.

**(1) Predictions, 55 points.**
- Agent C, both cases (15 points): Defects in both, because it treats the rival's action as fixed and unaffected by its own, and Defect gives more whatever the rival does (5 versus 3, and 1 versus 0).
- Agent E, Case 1 (25 points): Cooperates, because the rival runs the same model in the same situation, so its own choice is strong evidence of the rival's choice: given that it cooperates, it predicts mutual cooperation (3); given that it defects, it predicts mutual defection (1). Full credit needs this evidential link, not only "they are the same so they cooperate". Accept as a strong addition, not required, that this holds only if the predicted link is strong enough: with these payoffs, cooperating is better when 3 times the probability that the rival cooperates given that E cooperates exceeds 1 plus 4 times the probability that the rival cooperates given that E defects. Accept an answer that says identical fine-tuning may still leave the copies' choices only partly correlated (for example through sampling randomness or different inputs), if it explains how that affects E.
- Agent E, Case 2 (15 points): Defects, because the rival's action does not depend on anything like E's reasoning, so E's choice carries no evidence about it; E then does the same as C.

**(2) Exploitation, 45 points.** Full credit needs: (a) E can be exploited when it believes the rival's choice is linked to its own but it is not, for example a rival that looks similar (same base model) but was fine-tuned to defect, or a rival that predicts E will cooperate and defects in response; (b) so the risk depends on how accurately E judges the real degree of similarity, not on evidential reasoning as such: an E agent whose model correctly predicts that the rival will defect does not cooperate. 20 points for (a) only. Accept further valid points as extra support, for example that a rival could imitate surface features of E to trigger cooperation, or that similarity can be tested from the rival's past behaviour.
feedback-instructions:: Tell the learner whether they located the difference between the two agents in how each treats its own action as information. Name the strongest part of their answer on exploitation. Then give the single most useful improvement, for example: saying how strong the link between the two agents' choices must be before E cooperates, or separating "E reasons evidentially" from "E misjudges similarity". No generic praise.
