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

## Tests

#### Question: Choice
id:: e4507776-276b-4abd-b2e2-c7e77dc3b81c
content:: What does the value complexity thesis claim about human values?
options::
- [x] They have many interacting parts that can't be reduced to a short set of rules
- People disagree so much that no shared set of values exists
- They change too quickly for any fixed description to keep up
- They are simple, but hard to measure inside a computer
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
- It understands human values less well than a weak system
- It rewrites its own goals more often than a weak system
shuffle:: true

#### Question: Choice
id:: 0d20a388-7394-4c07-a084-8dc49b6cfd69
content:: Which of these is the best example of value fragility?
options::
- [x] A pleasure-filled future with no freedom, variety or relationships, judged nearly worthless
- Two cultures disagreeing about which values should guide a shared AI system
- An AI refusing a task because its instructions were unclear or contradictory
- An AI system that takes longer than expected to learn what users want
shuffle:: true

#### Question: Choice
id:: 0f4084ce-46e7-4d72-a119-e7f858c4983d
content:: Which observation is the main large-language-model-era challenge to the value complexity argument?
options::
- [x] Models trained on human data seem to model human values and common sense quite well
- Models show that human values are simpler than philosophers had assumed
- Models are trained on lists of rules written by ethicists
- Models follow only explicit instructions, so they need no values
shuffle:: true

#### Question: Choice
id:: cd2aad6f-2e1a-42f2-80b6-1e7da09657a2
content:: The observation that large language models model human values well mainly answers which part of the worry about giving AI good values?
options::
- [x] That human values are too complex to write down by hand
- That an AI's goals may differ from what it knows we want
- That people disagree about which values matter most
- That a capable AI may resist having its goals changed
shuffle:: true

#### Question: Choice
id:: 06ca3a8b-0de3-4237-864b-18e6c1193e47
content:: An AI model correctly predicts what humans would judge to be good behaviour in nearly every test. Does this by itself show that the model's own goals match human values?
options::
- [x] No
- Yes

#### Question: Choice
id:: 54b1b25b-8697-4e5d-8146-b66f4c029c02
content:: The value fragility argument says that hard optimization of a target missing part of human values could go badly. Does it apply only to goals written by hand, or also to goals learned from human data?
options::
- [x] Also to goals learned from human data
- Only to goals written by hand

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
assessment-instructions:: Score out of 100. 100 for any one of: training can use the model's own understanding of values as the target, so pointing its goals at our values is easier than writing them down; current models mostly behave as if they share common human values in practice; the remaining gap may be smaller or easier to fix than the original specification problem. 40 for a vague claim that models are "aligned" with no reason given.
