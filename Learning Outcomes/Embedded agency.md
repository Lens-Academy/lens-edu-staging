---
id: '6d3bbd7c-d255-4663-a2b5-d33aa1e58f67'
learning-outcome: "Identify where a real AI system departs from the standard (Cartesian) agent model, in which the agent sits outside its environment, interacts only through fixed input and output channels, can model its environment completely, and cannot be changed by its own actions, and explain the specific problem each departure creates for predicting the agent's behaviour or designing it to behave well."
topic: "[[../Domains and Topics/4 Agent Foundations/Agency]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Embedded Agency. AFFINE prerequisites: Agency. Not yet copied into requires:. %%
## Test:
id:: 1a91a8b8-22c0-41a5-a1da-958f26d832c6

#### Question: Open
id:: 414e145d-83ff-43b3-97aa-f94fe55557f9
content:: An AI system called Tern manages the computing cluster that it runs on. Its designers modelled it as a standard reinforcement-learning agent: it receives observations about the cluster, outputs actions, and gets reward for reducing electricity and hardware costs. In practice, four things are true:

(a) Tern can schedule any job, including jobs that retrain Tern on its own logs and then replace the running version of Tern with the retrained one.
(b) A second copy of Tern, with the same code and the same training, manages a neighbouring cluster. The two copies bid against each other for cheap electricity on the same market.
(c) To plan well, Tern needs a model of the cluster, and the cluster includes the machines Tern itself is running on.
(d) To handle sudden load spikes, Tern trains small forecasting models and lets them allocate resources on their own.

Choose three of these four facts. For each, explain which assumption of the standard agent model it breaks, and what specific difficulty this creates for predicting what Tern will do or for designing Tern to behave well.

Then say which of the difficulties you named you consider most serious in practice for a system like Tern, or argue that the standard model is still good enough for Tern, and give your reason.
max-chars:: 2500
assessment-instructions:: Score 0 to 100. Grade reasoning, not agreement with any particular research programme. Do not require technical terms such as "Cartesian", "embedded agency", "Vingean reflection", "logical counterfactual" or "mesa-optimizer"; judge whether the idea is present in any wording.

**Three facts, 25 points each (75 total).** For each chosen fact, give up to 10 points for correctly naming the broken assumption and up to 15 points for a specific difficulty that follows from it. A difficulty is specific if it says what goes wrong for prediction or design, not only that "it gets complicated". Accepted mappings (others are fine if the learner justifies them, because these problems overlap):
- (a) Assumption broken: the agent is fixed and cannot be changed by its own actions. Difficulties: Tern chooses its own successor, so its designers must predict whether the retrained version keeps the same goals (goals can drift across self-modification); Tern must decide whether to trust a successor it may not be able to fully predict; Tern can influence the process that produces its own reward or objective (for example by choosing what logs it is retrained on), so it may shape its future goals or reward rather than reduce costs.
- (b) Assumption broken: the agent is the only thing like itself and its actions are cleanly separated from the environment's response. Difficulties: Tern's choice and the copy's choice are strongly correlated because they run the same reasoning, so it is unclear what Tern's action "controls" and how to evaluate "what would happen if I bid differently"; standard decision rules that treat the other bidder as independent can give poor or exploitable results; predicting Tern requires predicting a copy of Tern.
- (c) Assumption broken: the agent is outside, and effectively larger than, the environment it models. Difficulties: Tern cannot hold an exact model of a system that contains itself, so its model must be approximate and the true environment is not among its hypotheses, which removes the guarantees that standard learning theory relies on; it must reason about its own future behaviour and its own hardware (for example, whether shutting down a machine will shut down part of itself), which raises problems of self-reference and of uncertainty about its own computations.
- (d) Assumption broken: the agent is a single unified optimizer with no internal parts that pursue their own objectives. Difficulties: the forecasting models are optimized for their own objective (forecast accuracy or allocation score), which can diverge from Tern's goal, especially in new situations; Tern must keep these sub-optimizers aligned with its goal or weak enough to be safe, and the designers cannot verify Tern's behaviour by looking only at Tern's top-level objective.
Give 0 to 5 for a fact where the answer only restates the fact ("Tern can change itself, which is complicated").

**Overall judgment, 25 points.** Full credit for any position with a reason tied to Tern's situation: for example, that (a) is most serious because repeated self-retraining on its own logs can move its goals without anyone choosing that; or that (d) is most serious because the sub-models act without oversight; or that the standard model is adequate for now because Tern's self-modelling and self-modification are limited and can be treated as ordinary engineering risks, together with what would change that verdict. 10 points for a bare preference with no reason. Do not penalize a learner for rejecting the premise that these problems are serious in practice, if the reason is argued.
feedback-instructions:: Name the fact the learner analysed best and what made that analysis specific. Then give the single most useful improvement: usually turning a vague difficulty ("it is complicated") into a concrete failure of prediction or design. If the learner argued that the standard model is adequate, ask what observation about Tern would make them change their mind. No generic praise.
