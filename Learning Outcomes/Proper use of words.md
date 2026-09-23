---
id: 'b191dd50-b7f0-4e25-bb3d-b59e5df8c6d8'
learning-outcome: "Diagnose how a word is misused in an argument (for example, settling an empirical question by definition, inferring properties from a category label that was assigned on other grounds, or disputing where to draw a boundary when the facts are agreed) and repair the argument by replacing the word with the observable claims it stands for."
topic: "[[../Domains and Topics/4 Agent Foundations/Agent foundations research]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Proper Use of Language. AFFINE prerequisites: Value of abstraction. Not yet copied into requires:. %%
## Test:
id:: b941461b-639e-4e3b-a160-7e9440f46e2a

#### Question: Open
id:: 1319f79f-288e-436f-98b9-8d1dc76752c8
content:: Read this exchange between two researchers.

**Ana:** 'Chatbots are not agents. By definition, an agent is something that acts in the physical world. So we do not need to worry about agent-style risks from chatbots.'

**Ben:** 'They are agents: they choose which word to output next, and choosing is what agents do. And agents pursue goals and resist being shut down. So chatbots will resist being shut down.'

**Ana:** 'They don't *really* choose anything. It's just statistics.'

**Ben:** 'Everything is just statistics. Let's look up "agent" in a dictionary and settle this.'

Identify what goes wrong in how the word 'agent' (and 'choose') is used here, explaining each problem. Then rewrite the disagreement as questions about the world whose answers would settle what Ana and Ben actually care about, without using the words 'agent' or 'choose'.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. The learner does not need any standard names for these errors; grade whether each problem is identified and explained. A learner who takes a side on whether chatbots pose these risks is not penalized, as long as the diagnosis is correct.

**(a) Diagnosis, 60 points.** Up to 15 points each for up to four of the following, each with a correct explanation of why it is a problem (8 points if named without explanation):
- Ana settles an empirical question (are there risks of this kind?) by choosing a definition: defining 'agent' to need a body does not change what chatbots can do, so the risk question is untouched.
- Ben infers properties (pursuing goals, resisting shutdown) from the category label, but he assigned the label on a different feature (picking the next word). The inference is only as good as the evidence that systems with that feature also have those properties, and he gives none.
- The 'really choose' exchange is a dispute over where to draw the boundary of a word, while both apparently agree on the facts of how the model produces output; it cannot be settled by more argument about the word.
- Appealing to a dictionary cannot settle a question about what chatbots will do; a dictionary records how people have used a word, not facts about new systems.
- 'Agent' bundles several distinct properties (acting in the world, pursuing goals over time, resisting interference), and the two speakers use it for different bundles, so they talk past each other.
- 'Just statistics' is used to carry a conclusion (nothing agent-like can happen) without argument.
Other correct diagnoses of word misuse in the exchange earn credit on the same basis.

**(b) Repair, 40 points.** Full credit: at least two questions about observable behaviour or mechanism, stated without 'agent' or 'choose', that bear on what the speakers care about, for example: 'In a test where the model can take actions that affect whether it is shut down, does it take them?'; 'Does the model pursue an objective consistently over many steps when obstacles appear?'; 'Can the model, through tools or the people it talks to, cause effects in the physical world?'. Each question must be answerable by some test or evidence. 20 points for one such question. Deduct 10 if the rewrite still depends on 'agent' or 'choose' or a synonym that hides the same ambiguity (for example 'is it agentic?').
feedback-instructions:: Tell the learner which diagnosis was most precise and quote it. Name the single most useful improvement, often that Ben's inference from label to properties needs evidence that the properties go together, or that a rewritten question is not yet testable. Ask one follow-up question. No generic praise.
