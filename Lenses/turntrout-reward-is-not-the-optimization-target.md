---
id: 6497be1e-8028-46f8-a4c3-e30de78287e9
{++{"author":"Elias's AI","timestamp":1783850044424}@@tldr: "It feels obvious that a reinforcement learner is out to maximize its reward. TurnTrout argues that is a mistake: reward does not set the agent's goal, it 'chisels cognitive grooves' into the network. Grasp the difference and a lot of worries about AIs wireheading or gaming their reward start to look different."
summary_for_tutor: "TurnTrout argues against the common assumption that reward is the optimization target of RL agents, focusing on the model-free policy-gradient setting (e.g. PPO and REINFORCE). He makes two claims: trained deep RL agents will not generally come to intrinsically value the reward signal, and reward is better understood mechanistically as a 'cognition-updater' that reinforces whatever computations preceded it, chiseling cognitive grooves, rather than as a utility function expressing the relative goodness of outcomes. Using pizza-eating and trash-collecting examples, he explains how credit assignment shapes cognition, why an agent that already reasons in terms of reward can become a reward optimizer and wirehead while others will not, and under what conditions (e.g. tabular convergence theorems) reward genuinely becomes the optimization target. The essay reframes how learners should think about what RL training actually selects for."
++}title: "Reward is not the optimization target"
---

#### Article
source:: [[../articles/turntrout-reward-is-not-the-optimization-target]]
