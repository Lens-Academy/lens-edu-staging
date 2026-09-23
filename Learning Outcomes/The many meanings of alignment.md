---
id: 'b38e0f5c-21e2-4b1c-8e75-38f06fab6cec'
learning-outcome: "Distinguish the different problems that the word \"alignment\" is used to name (for example making AI reliably do what users ask, preventing takeover by AI pursuing unintended goals, making AI cognition understandable, deciding whose values AI should serve, and protecting human agency and long-run societal outcomes), and identify when an argument treats progress on one of them as progress on another without stating how they are related."
topic: "[[../Domains and Topics/3 Alignment/The alignment research landscape]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Alignment's Many Meanings. AFFINE prerequisites: none. Not yet copied into requires:. %%
## Test:
id:: 022835b5-7235-4a6c-8bd2-430822f95864

#### Question: Open
id:: 47b0cd5e-7bb0-4651-9d29-86d19dc41dfe
content:: A funding committee can fund one "alignment" project this year:

- Project 1 develops fine-tuning methods that make a chatbot follow complicated user instructions more reliably and refuse harmful requests.
- Project 2 builds tools that read a large model's internal computations to detect whether it is pursuing goals its developers did not intend.
- Project 3 runs a platform where members of the public deliberate about what rules AI systems should follow, and passes the results to developers who write those rules into their models' specifications.

A committee member says: "All three are alignment research, so let's fund whichever will make the most progress on alignment."

1. For each project, say what problem it is treating as "the alignment problem".
2. Explain why "the most progress on alignment" does not yet pick out one project, and what further claims the committee would need to settle in order to compare them.
3. Give one example of an argument in which evidence of progress on one of these problems is treated as evidence of progress on another. State the assumption that step needs.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement. A learner may argue that one of these problems is the real one and the others matter less; this scores well if they state that this is a claim needing support. Do not require any particular list of problems, author or framework name.

**(1) Identifying the problems, 30 points.** 10 points per project for a reasonable description in any wording. Project 1: making AI systems reliably do what their users or developers intend (task reliability, instruction following). Project 2: detecting or preventing AI systems that pursue unintended goals, by making their cognition understandable. Project 3: deciding what or whose values and rules AI should serve (value specification, legitimacy of the target, human agency in shaping AI). Accept other accurate descriptions, including noting that a project serves more than one problem.

**(2) Why the comparison is undefined, 35 points.** 15 points for explaining that the three projects work on different problems, so "progress on alignment" has no single measure until the committee says which problem, or which outcome, it cares about. 20 points for at least two kinds of further claims needed, for example: which outcome the committee is trying to affect (such as catastrophic risk, everyday harms, or who controls AI); whether and how progress on one problem carries over to another (for example, whether reliable instruction following in today's systems says anything about preventing takeover by much more capable ones); whether one problem must be solved before another matters (a well-chosen set of rules is useless if nobody can make AI follow rules, and the reverse); relative difficulty or neglect. 10 points of the 20 for one kind of claim only.

**(3) Conflation and its assumption, 35 points.** 15 points for a clear argument in which progress on one problem is presented as progress on another. 20 points for the assumption that step needs, stated correctly. Examples: "our models follow instructions and refuse harmful requests, so we are making progress on preventing catastrophe from advanced AI" assumes that behaviour trained at current capability carries over to much more capable systems, and that following instructions is enough when the instructions themselves can be harmful; "if the AI learns human values it will be safe" assumes that knowing values means acting on them and that there is one set of values to learn; "we can read the model's internals, so it is aligned" assumes detecting a problem is enough to fix it; "the rules came from public deliberation, so the AI is aligned" assumes the AI will actually follow the rules.
feedback-instructions:: Name the project the learner described most precisely and the strongest further claim they gave, quoting it. Give the single most useful improvement: often stating the assumption behind the conflation explicitly rather than only pointing at it. Ask one follow-up question about which of the three projects they would fund and what claim that choice depends on. No generic praise.
