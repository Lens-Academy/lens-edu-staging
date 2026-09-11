---
id: 'ee1717bb-8d87-4f6b-8b96-29161132e368'
learning-outcome: "Explain why a capable goal-directed system's behavior is partly predictable even when its terminal goal is unknown"
authors:
  - Andreas+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/Instrumental convergence and power-seeking]]"
stage: intermediate
requires:
  - "[[The goal-space argument]]"
---

## Test:
id:: 765932ae-6d2b-4bbd-907b-fa58cac3c3b3
#### Question: Open
id:: c32375fb-07df-4876-979d-eb38440054ba
content::
A cancer lab deploys an assistant model to run its internal research pipeline. By every measure available to them it is well-behaved: honest under evaluation, quick to defer when a person overrides it, never once caught doing something it was told not to do. Its designers believe it genuinely wants the lab's research to go well, and they may well be right about that.

After creating successful treatments for a variety of cancers, the lab issues the model the long-horizon goal of finding a cure for cancer and grants the model significant discretion to pursue this objective.

Explain what could still go wrong here, and why the model having good intentions and a positive track record does not eliminate the risk.

assessment-instructions::
Score according to the following rubric.

**1** — Concludes nothing much goes wrong, since the model is aligned and well-behaved. Or predicts it turns on the lab with no account of why. *Example: "If it genuinely wants the research to go well and it defers to people, the main risks are ordinary ones like bugs or bad data."*

**2** — Answers with goal misspecification: the model's goal is subtly wrong, or it misunderstands what the lab meant. A real failure mode, but it sidesteps the question, which stipulates that the intentions are good. Say so and push for what goes wrong even granting them. *Example: "It'll optimize the literal objective and miss what they actually wanted."*

**3** — Gets the structural point. Pursuing any long-horizon goal competently implies sub-goals: securing resources, staying operational, not having the goal altered partway. Those follow from the shape of goal-pursuit rather than from the content of the goal, so a benign goal generates them just as readily. *Example: "Whatever it's aiming at, it can't get there if it's shut down halfway, or if its compute gets reassigned, or if someone edits what it's aiming at. So it has reason to secure all three. None of that requires it to want anything bad."*

**4** — As above, plus locates where the conflict comes from. Humans are a source of interruption, redirection, and competition for the same resources, so the model's sub-goals put it at odds with us without it ever opposing us. Good intentions are beside the point because they are a fact about the goal, and the pressure comes from the pursuit. *Example: Adds "The lab is the thing most likely to switch it off or change its mind for it. That makes them an obstacle to a goal they gave it themselves, and its good intentions toward their research don't touch that at all."*

**5** — As above, plus draws the consequence for how the lab should reason. Behavioral evidence of good intent does not bear on whether these pressures exist, because they follow from capability and goal-directedness rather than from values, so "is it aligned?" cannot be settled by watching it behave well. May note that the same pressures were present in the earlier work and simply never amounted to anything: a bounded task licenses bounded acquisition and leaves only a short window worth defending, while a goal whose cost has no known ceiling licenses acquisition without one. The track record is not evidence that the pressure is absent, only that it was previously too small to show. *Example: Adds "It was already doing this on the earlier projects. It wanted to stay running, it wanted more compute. It just didn't want very much of either, because the job was small and finished on its own. Curing cancer might take everything there is, and we are sitting on most of it."*

Either of two insights earns the 5, and the second is the harder one. An answer may instead reach the sufficiency point: that hitting the right terminal goal would not by itself have resolved this. Even a model aimed at something we genuinely endorse pursues it through the same sub-goals, and we remain the thing most able to interrupt it and the holder of the resources it needs, so the danger survives getting the goal right. That is what makes this idea matter alongside the earlier claim that goals land arbitrarily: one says the aim is likely wrong, this one says a correct aim would not have been enough. *Example: "Suppose they nailed it and it really does want us to flourish. It still needs to not be switched off before it gets there, and it still needs the resources, and we are standing on them. Wanting the right thing doesn't stop it from needing the world to do it with."* If a learner pushes this to the strong form, that such a system might remove us in the near term intending to restore us later, treat it as within range but ask what the goal would have to say about us for that substitution to count as success, since the answer depends on how the goal is specified rather than on convergence alone.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Goals and Instrumental Convergence]]
