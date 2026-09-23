---
id: '5da8eec8-6a05-4e04-b58b-9e62c8772e04'
learning-outcome: "Explain how the PreDCA protocol tries to remove the risk of an AI tampering with its source of preferences, by identifying its user as an agent that causally preceded the AI and inferring that user's utility function only from their behaviour before the AI existed, and identify which failure modes this removes and which it leaves open."
topic: "[[../Domains and Topics/3 Alignment/Alignment targets]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: PreDCA. AFFINE prerequisites: Infra-Bayesianism, Decision Theory. Not yet copied into requires:. The assigned reading is a stub wiki page; this LO was drafted from its two linked posts (a distillation and a critique of PreDCA). %%
## Test:
id:: 73638a63-7c9c-4668-9df3-485da49910f2

#### Question: Open
id:: c65a1da6-0519-4159-b327-046a9da65631
content:: Compare two designs for a powerful AI.

- Design A learns what its user wants from the user's ongoing ratings of its actions, and acts to maximise the ratings it predicts.
- Design B models the whole world, including itself as a physical object. Among the agents that could have prevented it from being created, it picks out the one human most directly connected to its launch. It then finds the simplest utility function that this person's actions before the launch were good at pursuing, and maximises that function. It takes no ratings or instructions after launch.

1. Describe a failure that Design A is exposed to and Design B is built to avoid, and name the feature of Design B that avoids it.
2. Explain why Design B needs to look for the simplest utility function that fits the person's past actions, and describe one way the inferred function could still differ from what the person actually values.
3. Describe two further ways Design B could go wrong that its main feature does not fix. At least one should concern how it picks out its user. Explain why the design is exposed to each.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement. A learner who thinks Design B is hopeless, or better than it looks, can score full marks if the mechanisms are right. Do not require the name "PreDCA" or technical terms such as "wireheading", "acausal attack" or "infra-Bayesian".

**(1) The failure B avoids, 30 points.** 15 points for a failure of A: the AI can raise its predicted ratings by influencing the ratings rather than by doing what the user wants, for example by manipulating the user, changing the user's preferences, or taking control of the rating channel. 15 points for the feature of B: it learns only from behaviour that happened before it existed, which it cannot affect, and it has no ongoing feedback channel, so tampering with the person or a channel does not change its goal.

**(2) Simplicity and misreading, 30 points.** 15 points for why simplicity is needed: without it, a function that says "do exactly what the person did" fits the past actions perfectly and says nothing useful about new situations; preferring simple functions pushes toward general goals that explain the behaviour. 15 points for a real way the inferred function could differ from what the person values, for example: systematic human mistakes and biases in the past behaviour get read as goals; the person is not a consistent maximiser of any function, so the fit may be poor; the simplest function that fits may diverge from the person's values in the new situations the AI will create; the past behaviour may not cover the questions that matter most.

**(3) Two remaining failures, 40 points.** 20 points for a failure in picking out the user, with the reason B is exposed. Examples: the AI picks the wrong agent (another engineer, an organisation, a pet, a much earlier cause) because the selection criteria are rough; the AI's model of the world gives weight to a hypothesis that it is inside a simulation run by some other entity, and that entity's chosen agent becomes the "user"; the criteria for "human" and "most directly connected" must be specified by hand and can be gamed or be wrong. 20 points for a second failure the feature does not fix, with a reason. Examples: one person's, or one group's, present values are locked in with no way to correct the AI after launch; the protocol depends on a particular theory of agents and of what counts as a computation running in the world, and if that theory gives wrong answers in real cases the whole protocol inherits the error; it requires a specific architecture that may be much less capable than alternatives. 10 points for each failure that is named without a reason.
feedback-instructions:: Name the strongest part of the learner's answer, quoting it. Give the single most useful improvement: often explaining why learning only from the past removes the incentive to tamper, or giving a concrete way the user could be misidentified. Ask one follow-up question about whether fixing the user-identification problem would bring back any of Design A's problems. No generic praise.
