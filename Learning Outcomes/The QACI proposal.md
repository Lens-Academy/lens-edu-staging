---
id: '276aa9ac-7599-48bf-8702-ffad970ad908'
learning-outcome: "Explain how a formal-goal proposal such as QACI defines an AI's goal as a mathematical question about what specific humans would answer if a stored question were counterfactually replaced (with those humans able to pose further such questions, which gives them long reflection), and classify failures of such a design as flaws in what the formal goal points at or as failures of the AI to pursue or approximate that goal."
topic: "[[../Domains and Topics/3 Alignment/Alignment targets]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: QACI. AFFINE prerequisites: Outer / Inner Alignment. Not yet copied into requires:. The only assigned reading is the heavily mathematical formalization post; a module will need a gentler explanation of the plan. %%
## Test:
id:: 0317fd0d-3b03-4428-8940-15289f15280e

#### Question: Open
id:: 1cd41271-9838-42d8-8346-bbaa17ca46c6
content:: An alignment proposal works as follows. At a fixed time, a small team generates a large random file, the "question file", and stores it. The AI's goal is not learned from feedback. It is written as a mathematical expression that says, roughly: "Consider the world you are in and find the question file in it. Imagine that the file had instead contained question Q. The team would read Q and, some time later, store an answer. The value of the expression is that answer." The top-level question is "How good is each action the AI could take?", so the answer is a scoring of actions, and the AI takes the action it estimates scores highest. Inside the imagined situation, the team may write answers that themselves use the same expression with new questions of their choosing.

1. Why does the design let the imagined team pose further questions of the same kind, instead of just answering once? Say what this gains and what it relies on.
2. For each failure story below, say whether it is a flaw in what the mathematical goal points at, or a failure of the AI to pursue or approximate that goal, and explain why.
   - (a) The AI's method of finding the question file gives most weight to a hypothesis in which someone else, for example an entity simulating our world, produced an identical file, so the answers it reasons about are theirs.
   - (b) Training produces an AI that actually tries to please its operators, not to maximise the mathematical expression.
   - (c) Over many rounds of further questions, the imagined team slowly comes to believe a strange ideology and returns a terrible scoring of actions.
   - (d) The AI cannot compute the expression exactly, and its estimate of the best action is badly wrong in a way it does not notice.
max-chars:: 2500
assessment-instructions:: Score 0 to 100. Grade reasoning, not agreement with the proposal. A learner who thinks the proposal is unworkable can score full marks. Do not require the name "QACI" or any technical term such as "outer alignment", "inner alignment" or "acausal attack"; equivalent plain wording counts.

**Part 1, 30 points.** 15 points for the gain: any single imagined answering period gives the team limited time, but by posing further questions to imagined versions of themselves they can chain many periods together, so the total amount of thinking available is effectively very large (a long reflection); this also lets them split hard problems into parts. 15 points for what it relies on: at least one of (i) the imagined team staying sane, careful and trustworthy across many rounds, or (ii) the AI being able to reason well enough about a deeply self-referring expression to estimate its value. 

**Part 2, 70 points.** For each story, 17 or 18 points (a: 18, b: 18, c: 17, d: 17) for a correct classification with a reason; half credit for a correct classification without a reason, or for the opposite classification with a reasoned argument that partly works.
- (a) Flaw in what the goal points at. The procedure for locating the file is part of the mathematical goal, so if that procedure gives weight to someone else's copy, even a perfect maximiser of the expression would follow the wrong answers. Accept an answer that calls this an approximation failure only if the learner argues that the correct value of the expression would locate the real file and the AI merely misjudges it; give that 12 points.
- (b) Failure to pursue the goal. The formal goal may be fine; the AI is not trying to maximise it. Writing down a good goal does not by itself make a trained AI adopt it.
- (c) Flaw in what the goal points at. The expression faithfully picks out the team's answer, and that answer is bad; the design depends on the imagined humans deliberating well.
- (d) Failure to approximate the goal: the goal is correct but the AI's estimate of it is wrong. Also accept an argument that the design must specify how the AI acts when it is uncertain about the expression's value, so part of this problem belongs to the specification.
feedback-instructions:: Say which failure story the learner reasoned about best and quote their reason. Name the single most useful improvement: often recognising that the file-locating procedure is part of the goal itself (story a), or stating what the chain of further questions relies on. Ask one follow-up question about which of the four failures the proposal is best placed to reduce. No generic praise.
