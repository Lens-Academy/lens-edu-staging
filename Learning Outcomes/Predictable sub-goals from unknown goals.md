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
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Concludes nothing much goes wrong, since the model is aligned and well-behaved. Or predicts it turns on the lab with no account of why. *Example: "If it genuinely wants the research to go well and it defers to people, the main risks are ordinary ones like bugs or bad data."*

**Level 2 (21-40):** Answers with goal misspecification: the model's goal is subtly wrong, or it misunderstands what the lab meant. A real failure mode, but it sidesteps the question, which stipulates that the intentions are good. *Example: "It'll optimize the literal objective and miss what they actually wanted."*

**Level 3 (41-65):** Gets the structural point. Pursuing any long-horizon goal competently implies sub-goals: securing resources, staying operational, not having the goal altered partway. Those follow from the shape of goal-pursuit rather than from the content of the goal, so a benign goal generates them just as readily. *Example: "Whatever it's aiming at, it can't get there if it's shut down halfway, or if its compute gets reassigned, or if someone edits what it's aiming at. So it has reason to secure all three. None of that requires it to want anything bad."*

**Level 4 (66-85):** As above, plus locates where the conflict comes from. Humans are a source of interruption, redirection, and competition for the same resources, so the model's sub-goals put it at odds with us without it ever opposing us. Good intentions are beside the point because they are a fact about the goal, and the pressure comes from the pursuit. And the track record does not settle it: behavioral evidence of good intent does not bear on whether these pressures exist, because they follow from capability and goal-directedness rather than from values. An answer that makes all three points has answered the question in full, and without an extension it stays in this range. *Example: Adds "The lab is the thing most likely to switch it off or change its mind for it. That makes them an obstacle to a goal they gave it themselves, and its good intentions toward their research don't touch that at all. Nor does its record: behaving well so far can't show these pressures are absent, because they come from pursuing the goal, not from what it values."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the three level 4 points in more precise or technical terms is still level 4. Two that fit: why the track record looked clean (the same pressures were present on the earlier projects but small, because a bounded task licenses bounded acquisition, while a goal whose cost has no known ceiling licenses acquisition without one); or the sufficiency point (a model aimed at exactly the right goal still pursues it through the same sub-goals, and we remain the thing most able to interrupt it and the holder of the resources it needs, so getting the goal right would not by itself remove the danger). The strong form, that such a system might remove us in the near term intending to restore us later, is within range. Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "It was already doing this on the earlier projects. It wanted to stay running, it wanted more compute. It just didn't want very much of either, because the job was small and finished on its own. Curing cancer might take everything there is, and we are sitting on most of it." Or adds "Suppose they nailed it and it really does want us to flourish. It still needs to not be switched off before it gets there, and it still needs the resources, and we are standing on them. Wanting the right thing doesn't stop it from needing the world to do it with."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually {--{"author":"Andreas's AI","timestamp":1791592247249}@@made.--}{++{"author":"Andreas's AI","timestamp":1791592247249}@@made, and credit only what the answer says: do not attribute to them a point they did not make.++} Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest move in their answer and what makes it work, in one sentence. If the answer goes beyond the question while one of the three core points (the conflict with the lab, why good intentions don't help, why the track record doesn't settle it) is only asserted, that point is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they answered with goal misspecification, that the model's goal is subtly wrong or it misread what the lab meant: say that it is a real failure mode, note that this scenario deliberately grants good intentions, and ask what still goes wrong once those are taken as given.
- If they named the sub-goals (resources, staying operational, keeping the goal intact) and stopped there, ask where the conflict with the lab comes from, given that the model is not opposed to anyone.
- If they located the conflict, push on what it costs the lab's evidence: if these pressures follow from capability and goal-directedness rather than from values, what can watching the model behave well actually settle?
- If they got that far, the move most learners miss is the earlier projects. The same pressures were present and never amounted to anything, because a bounded task licenses bounded acquisition. Ask what changed when the goal stopped having a finish line.

If they reached the sufficiency point (that hitting the right terminal goal would not have resolved this) and the core points are solid, say so plainly in a sentence or two after the opening and stop: there is nothing above it, and inventing a further push would be false, so this reply can be shorter than the length below. Only if they raised the strong form themselves (that the system might remove us in the near term intending to restore us later), ask what the goal would have to say about us for that substitution to count as success, since the answer depends on how the goal is specified rather than on convergence alone.

One follow-up question, not several. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Goals and Instrumental Convergence]]
