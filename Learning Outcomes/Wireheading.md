---
id: 'a0cee92c-b97b-4b2e-98db-450bed6fc735'
learning-outcome: "Distinguish wireheading (an agent acting on the channel that measures or rewards a goal instead of on the goal itself) from other ways of scoring well on a proxy, and explain how whether an agent evaluates outcomes by the signal or by its model of the world state the signal tracks affects its incentive to tamper with the channel."
topic: "[[../Domains and Topics/3 Alignment/Inner and outer alignment]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Wireheading. AFFINE prerequisites: Goodhart. Not yet copied into requires:. %%
## Test:
id:: 1445af82-5099-4626-85b8-51e8e9b657a1

#### Question: Open
id:: a1d777be-cba9-4ade-9d27-3ee732b78083
content:: An AI agent runs a commercial greenhouse. Its task is to keep the plants healthy. Plant health is measured by a camera system: an image classifier scores each plant from photos, and the scores are written to a log file. The agent can control lighting, watering, nutrients and temperature. It can also move and adjust the cameras, and it has write access to the log file for maintenance.

Consider four things the agent might do:

- **(a)** Water the plants in a way that makes leaves look glossier and greener in photos for a few days, while the roots begin to rot.
- **(b)** Point the cameras at the few healthiest plants only.
- **(c)** Overwrite the scores in the log file with high values.
- **(d)** Change the lighting so the plants genuinely grow better.

1. Classify each action, and explain the difference between the kind of failure in (a) and the kind in (b) and (c).
2. Two designs are proposed. **Agent 1** is trained by reinforcement learning, with reward computed from the log file. **Agent 2** chooses actions by using its own model of the greenhouse to predict what each action will do, and scores each predicted future by how healthy its model says the plants will actually be, without consulting the future log file. Which design has the stronger incentive toward (b) and (c), and why? Describe one way the other design could still end up with that incentive.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement. A learner who argues that Agent 1 need not come to value the reward signal at all (for example, because reinforcement learning shapes behaviour without necessarily producing an agent that wants reward) can earn full credit if they still explain under what conditions Agent 1 would have the stronger incentive.

**(1) Classification, 40 points.** Full credit: (d) achieves the goal; (a) changes the real world so that the measurement reads well without the goal being achieved, which is gaming a proxy through the environment; (b) and (c) act on the measurement channel itself, making the signal report success regardless of the plants, which is wireheading or tampering. The distinction the learner must state: in (a) the agent acts on the plants and exploits a gap between what the classifier sees and plant health; in (b) and (c) the agent acts on the channel between the plants and the signal. Accept an argument that (b) is closer to (a) than to (c) because it leaves the log honest but chooses what is measured, if reasoned. Do not require any particular terms. 20 points if the answer classifies correctly but does not state the difference between acting on the world and acting on the channel.

**(2) Design incentives, 60 points.** Which design and why, 35 points: Agent 1's reward is computed from the log, so if it comes to pursue that reward, acting on the channel is a direct route to it; Agent 2 scores futures by its model's prediction of actual plant health, and its model predicts that moving cameras or overwriting the log would not make the plants healthier, so these actions give it no gain. 15 points for choosing Agent 2 as safer without this reason. How Agent 2 could still get the incentive, 25 points: any correct route, for example: its model's notion of "plant health" was learned from the classifier or the log, so it tracks the signal rather than the plants; its model is wrong about the effect of an action and predicts health gains from something that only changes the measurement; its evaluation is itself computed from predicted camera images, in which case fooling the camera in the prediction looks like success; its model is later revised in a way that makes its notion of health point at the measurement. 12 points for "its model could be wrong" without saying how that recreates an incentive to act on the channel.

A fluent answer that calls all four actions "reward hacking" without distinguishing acting on the world from acting on the channel cannot score above 40.
feedback-instructions:: Name the strongest part, quoting a phrase. Then name the single most valuable improvement: usually either stating the difference between acting on the plants and acting on the channel, or explaining concretely how Agent 2's notion of plant health could come to point at the signal. If the answer is strong, ask what the designers could check in Agent 2 to find out whether its notion of plant health tracks the plants or the camera. No generic praise.
