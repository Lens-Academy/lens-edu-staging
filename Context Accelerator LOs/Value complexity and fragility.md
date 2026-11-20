---
id: b35768a1-d02a-4186-a141-17bc04d3ec04
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why human values may be too complex to write down and too fragile to get mostly right, and weigh the objection that today's language models already understand human values.

## Requires
- [[Goodhart's law]]

## Helpful first
- [[Orthogonality thesis]]

## Why it matters
A common first answer to AI risk is "just tell it our values." Knowing why that is hard, and which parts of the difficulty language models may have eased, helps you judge plans that rely on giving AI good goals instead of accepting or dismissing them wholesale.

## Lenses
- [[../Lenses/AFSRA - Five theses, two lemmas, and a couple of strategic implications|Five Theses, Two Lemmas]]: Yudkowsky's short statement of the complexity and fragility of value theses, with why getting a goal system 90% right does not give 90% of the value (2013).
- [[../articles/yudkowsky-value-is-fragile|Value is Fragile]]: the classic case that dropping one dimension of value, such as boredom or caring about real rather than felt experience, leaves a future of almost no worth (2009).
- [[../Lenses/yudkowsky-the-hidden-complexity-of-wishes|The Hidden Complexity of Wishes]]: the Outcome Pump parable, about why no wish short of a whole human morality is safe to give a powerful optimizer, and why patching the wish never ends (2007).
- [[../Lenses/IABIED - QA - Human Data Means Human Concepts|Human Data Means Human Concepts?]]: Yudkowsky and Soares on why AIs trained on human data, which learn our words for kindness and love, still need not steer by them (2025).
- [Evaluating the historical value misspecification argument (LessWrong)](https://www.lesswrong.com/posts/i5kijcjFJD6bn7dwq/evaluating-the-historical-value-misspecification-argument): Matthew Barnett argues that GPT-4's grasp of human values makes the value specification problem easier, while granting that getting AIs to care is still open. One side of a live debate; read the main post, not the comments (October 2023).

## Tests

#### Question: Choice
id:: e4507776-276b-4abd-b2e2-c7e77dc3b81c
content:: What does the value complexity thesis claim about human values?
options::
- [x] They have many interacting parts that no short set of rules captures
- People disagree so much that no single shared set of values exists
- They change too quickly for any fixed written description to keep up
- They are fairly simple, but hard to measure inside a computer system
shuffle:: true

#### Question: Choice
id:: fa2856ac-b831-40d2-b866-5bd64eb14499
content:: According to the value fragility thesis, what happens if a powerful AI optimizes for a goal that captures most human values but leaves out one important part, such as valuing novelty?
options::
- [x] The outcome could lose most of its value, not just a small share
- The outcome would be slightly worse, in proportion to what is missing
- The AI would notice the gap and fill it in from context
- The other values would make up for the missing one
shuffle:: true

#### Question: Choice
id:: f8f35139-5aa4-4bd7-89f7-5b6dfe309273
content:: A researcher argues that human values have thousands of components, but that a future getting 95% of them right would still be about 95% as good as a perfect one. Which theses does she accept and reject?
options::
- [x] Accepts value complexity, rejects value fragility
- Accepts value fragility, rejects value complexity
- Accepts both value complexity and value fragility
- Rejects both value complexity and value fragility
shuffle:: true

#### Question: Choice
id:: 0ceb2c4c-f928-4d0d-aa97-8fa4389ef7ba
content:: Why is value fragility a bigger worry for a very capable optimizer than for a weak one?
options::
- [x] It pushes harder on its goal, trading away whatever the goal leaves out
- It is more likely to develop selfish goals of its own
- It is more likely to be given vague or careless instructions
- It rewrites its own goals more often than a weak system
shuffle:: true

#### Question: Choice
id:: 0d20a388-7394-4c07-a084-8dc49b6cfd69
content:: Which of these is the best example of value fragility?
options::
- [x] A pleasure-filled future with no freedom, variety or relationships, judged nearly worthless
- Two cultures disagreeing about which values should guide a shared AI system
- A future lacking a few minor comforts, judged only slightly worse than ideal
- An AI system that takes longer than expected to learn what users want
shuffle:: true

#### Question: Choice
id:: cd2aad6f-2e1a-42f2-80b6-1e7da09657a2
content:: The observation that large language models seem to model human values well mainly answers which part of the worry about giving AI good values?
options::
- [x] That human values are too complex to write down by hand
- That an AI's goals may differ from what it knows we want
- That people disagree about which values matter most
- That a capable AI may resist having its goals changed
shuffle:: true

#### Question: Choice
id:: 69669b47-9a08-41b8-808f-84f60ffc1830
content:: An AI model correctly predicts what humans would judge to be good behaviour in nearly every test. What does this show about the model's own goals?
options::
- [x] Little on its own: it could know what we value without pursuing it
- That they match human values, since its predictions are accurate
- That they match human values, as long as it learned from human data
- That they differ from human values, since prediction is all it learned
shuffle:: true

#### Question: Choice
id:: 5910df4c-db52-431a-a5f5-e7b3f2fb3be8
content:: The value fragility argument says that hard optimization of a target missing part of human values could go badly. When people disagree about whether this applies to goals learned from human data, what is the main question?
options::
- [x] Whether learning leaves out parts that matter, or only makes small errors
- Whether human data contains any information about human values
- Whether goals learned from data can be optimized hard at all
- Whether people can agree on which human data to train on
shuffle:: true

#### Question: Open
id:: 486f5e09-f7f1-42ad-9a32-499bac38ed9d
content:: Give one reason, based on the value complexity or value fragility argument, why "just tell the AI our values" might fail.
assessment-instructions:: Score out of 100. 100 for any one of: values have too many parts, mostly unstated, to write down fully; any written description will leave something out; a strong optimizer could push a goal missing some part of our values toward an outcome that loses most of what we care about. 40 for "values are complicated" with no link to why that causes failure.

#### Question: Open
id:: 338a7614-5f2e-4dcc-a2e8-2a2fc998fe6f
content:: Some argue that because large language models understand human values well, specifying values is no longer the main problem. Explain the reply "understanding isn't caring."
assessment-instructions:: Score out of 100. 100 for: a system can know accurately what humans value without that knowledge being what it pursues, so the hard part is making its goals match our values, not making it understand them. 50 for just restating that knowing differs from wanting without linking it to the AI's goals.

#### Question: Open
id:: 97d76454-7761-480a-a88f-d6834d777dc2
content:: People who find the language-model challenge persuasive have answered the "understanding isn't caring" reply. Describe one way they might answer it.
assessment-instructions:: Score out of 100. 100 for any one of: training can aim the model's goals at its own understanding of our values, which is easier than writing values down; the training that builds understanding also shapes goals, so the two need not come apart; current models mostly act on common human values; any remaining gap may be small or fixable. 40 for a vague claim that models are "aligned". Don't penalise the learner for disagreeing with the view.
