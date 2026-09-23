---
id: '139ccf2c-0673-4086-9dc2-07aadcc29128'
learning-outcome: "Evaluate a safety argument about a more capable agent by identifying where it depends on predicting the agent's specific actions, explain why that dependence fails in rich domains (a less capable agent cannot predict a more capable agent's exact moves, although it can still predict outcomes) but can hold in narrow, exhaustively checkable ones, and state what kind of claim a sound guarantee must make instead."
topic: "[[../Domains and Topics/4 Agent Foundations/Recursive self-improvement]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Vinge's principle. AFFINE prerequisites: AGI/ASI's various meanings. Not yet copied into requires:. %%
## Test:
id:: edaedc72-7941-4d38-b340-33a777890c08

#### Question: Open
id:: 5fec90df-cbe9-40c4-a06b-ae7b900aa74a
content:: Two safety cases are submitted for review.

**Case 1.** An AI system that is more capable than any human at software engineering and at persuasion will manage a company's cloud infrastructure, with broad administrator access. The safety case says: "Our red team of twelve experienced engineers spent a month listing every way the system could obtain more computing power than its budget allows. They found 43 routes. We have blocked all 43. Therefore it cannot obtain extra compute."

**Case 2.** An AI system plays a small board game that has been completely solved (the best move in every position is known). The system can output only one of the game's legal moves, and a simple filter rejects any output that is not a legal move. The safety case says: "We have checked every possible output. None of them does anything except make a legal move in the game."

1. For each case: where, if anywhere, does the argument rely on predicting what the system will do? Is that reliance justified, and why?
2. What kind of claim would a sound safety case for Case 1 have to establish instead?
3. What, if anything, could make the argument for Case 2 fail?
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner may reach different verdicts from the ones described here and still earn full marks if the reasoning addresses the same considerations. Do not require the terms "Vinge's principle", "Vingean uncertainty", "rich domain" or "cognitive uncontainability"; judge the ideas.

**(a) Diagnosis of both cases, 40 points.** Case 1 (25 points): full credit states that the argument assumes the red team's list covers the routes the system could find, which is a prediction of a more capable agent's strategies by less capable agents, and explains why this is unreliable here: the domain (real infrastructure, software with unknown flaws, people who can be persuaded) is too large and irregular to search exhaustively, and a more capable searcher can be expected to find routes the red team did not think of. The underlying point is that if we could list all its best strategies, we would be about as capable as it is at this task. 12 points if the answer says only "the red team might have missed something" without connecting this to the capability gap or the size of the strategy space. Case 2 (15 points): full credit says that here the reliance is justified because the set of possible outputs is small and has been checked completely, so no strategy the system could choose escapes the check, whatever its capability. 5 points if Case 2 is judged equally unsafe for the same reason as Case 1, without any distinction.

**(b) What Case 1 needs instead, 35 points.** Full credit: the claim must hold for any strategy the system might use, not only for listed ones. The answer names at least one way to get such a claim, for example: a claim about what the system is trying to do (it does not seek extra compute, so it will not search for routes); or a limit that no strategy within the system's reach can get around (for example, a quota enforced by hardware or by a party the system cannot influence); or monitoring of the outcome itself (actual compute used) through a channel the system cannot tamper with. Extra credit within the 35 for noting what that claim itself assumes (for example, that the enforcement or monitoring really is outside the system's reach, which is itself a claim about a large domain, or that we can verify the system's goals). 20 points for a claim that is about outcomes but does not say why it would hold whatever strategy the system uses. 0 to 10 points for "red-team longer" or "block more routes" alone.

**(c) What could make Case 2 fail, 25 points.** Full credit: the argument holds only while the filtered move is really the system's only channel to the world. It fails if there are other channels: side effects of the computation (timing, power use, hardware effects), flaws in the filter or surrounding software, or the humans who read the moves. Any real system also runs in the physical world, which is not a small domain. 12 points for "a bug could break it" without the general point that the guarantee depends on the output channel being the whole of the system's reach. Full credit also for a well-argued claim that nothing realistic breaks it for this specific setup, if the answer states the channel assumption it depends on.
feedback-instructions:: Say whether the learner separated "we cannot predict its moves" from "we cannot predict anything about it". Name the strongest part of their proposed replacement claim for Case 1 and the single assumption in it they should examine most closely. No generic praise.
