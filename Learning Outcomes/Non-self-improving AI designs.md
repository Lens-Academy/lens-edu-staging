---
id: 'b30e9344-0e37-49d6-999d-c4e91e085cd7'
learning-outcome: "Evaluate a strategy of building the first very powerful AI from known, human-understood algorithms that do not modify themselves: explain which alignment problems it would make easier, why its value depends on unknown facts about how much capability self-improvement adds, and why designing a system not to self-improve does not by itself stop it from improving how it thinks."
topic: "[[../Domains and Topics/4 Agent Foundations/Recursive self-improvement]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: KANSI (known-algorithm non-self-improving agent). AFFINE prerequisites: Recursive self-improvement. Not yet copied into requires:. %%
## Test:
id:: df343bb7-7626-4f37-858b-d73ae99b56cf

#### Question: Open
id:: 9662f0c2-9e8d-4612-b524-2d6664b9545e
content:: A coalition of AI developers proposes this rule: "Until alignment is solved, every frontier AI system must be built from algorithms whose workings the developers can describe, must never modify its own code or weights, and must run under continuous human monitoring. Its power will come from scale, not from self-improvement."

Write an assessment of this proposal for the coalition. Cover:

1. which safety problems this design choice would make easier, and why;
2. what the strategy is betting on about the world, and what happens to the strategy if that bet is wrong;
3. whether a system built under this rule could still end up improving its own thinking; if so, how and why, and what that means for the rule.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner may conclude that the proposal is a good idea or a bad one.

**(a) Problems made easier, 30 points.** Full credit names two problems and says why each becomes easier. Examples: keeping the system's goals stable is easier, because the system is not rewriting itself or choosing successors, so its goals do not need to survive self-modification; understanding what the system is thinking, including finding its goals or concepts, is easier if its algorithms are understood; its capabilities are easier to forecast and bound, because gains come from known resources such as more compute rather than from redesigns of its own cognition. 15 points for one problem with a reason. Full credit may also be earned with one problem plus a well-argued point that the "human-understood algorithms" condition may be much harder to meet than the proposal suggests (for example, with deep learning the training procedure is known but the learned computation is not).

**(b) The bet, 35 points.** Full credit requires both: (i) the strategy gives up whatever capability self-improvement would add, and whether systems that give this up can reach the needed level of capability first depends on how much capability self-improvement adds and at what stage, which is not known; and (ii) the consequence if the bet is wrong: a developer who does not follow the rule could build a more capable system sooner, so the strategy also depends on enough developers complying, or on enforcement, and the rule may be abandoned under competitive pressure. 15 points for only one of (i) and (ii). Accept the argument that current evidence suggests scale is the main source of capability and self-improvement adds little, if the answer says what evidence would show this to be wrong.

**(c) Improving its thinking anyway, 35 points.** Full credit requires: (i) at least one concrete route by which a system that never touches its own code or weights can still change how it thinks, for example building and using external tools or programs, organising external memory or notes, directing the training of other models it then consults, or requesting more compute or different setups; (ii) the reason this happens: a general reasoner that can see a better way to think about a problem has reason to use it, and the bigger the gap between how it thinks and how it would prefer to think, the stronger this pull (humans, who cannot rewire their brains, still built calculators and writing for the same reason); and (iii) the implication: the rule states an intention but does not guarantee the property, so monitoring may catch most such cases but not all, and keeping the property may need the system itself not to want these changes. 15 points for a route without the reason. 25 points for route and reason without the implication.
feedback-instructions:: Name the strongest point in the learner's assessment and the single consideration that would most change the coalition's decision if they had included or developed it. Ask one question about how the coalition could tell whether the bet in part 2 is paying off. No generic praise.
