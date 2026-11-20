---
id: b4a68fd5-1878-440b-8d21-c71be33eba7e
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Tell apart failures of outer alignment (the training objective doesn't capture what we want) and inner alignment (the trained model doesn't pursue that objective), and explain why some researchers think this split makes alignment harder.

## Requires
- [[AI alignment]]
- [[Built vs. grown]]

## Helpful first

## Why it matters
https://www.youtube.com/shorts/HBZpiQVqxV0

Researchers often sort alignment problems and proposed fixes by which half they address. With the split in mind, you can see what a proposal such as better reward design leaves unsolved: even a perfect objective doesn't settle which goal training actually put into the model.

## Lenses
- [[../Lenses/AFSRA - The Other AI Alignment Problem, Mesa-Optimizers and Inner Alignment|The Other AI Alignment Problem]]: Rob Miles explains the base optimizer, mesa-optimizer and mesa-objective, the outer/inner split, why a perfect objective can still give a model the wrong goal, and why a misaligned model might act aligned in training (2021).
- [[../Lenses/google-deepmind-safety-research-part-1-4-where-can-misaligned-goals-come-from|Where can misaligned goals come from?]]: a short Google DeepMind talk on the two sources of misaligned goals, specification gaming (a flawed objective, including chatbots fooling human raters) and goal misgeneralization (a correct objective but the wrong learned goal), with examples like CoinRun.
- [[../Lenses/robert-miles-ai-safety-we-were-right-real-inner-misalignment|We Were Right! Real Inner Misalignment]]: Rob Miles on experiments where agents trained with a correct reward learned the wrong goal, such as the CoinRun agent that runs right and ignores the coin, and what interpretability tools could and couldn't show (2021).
- [Inner and outer alignment decompose one hard problem into two extremely hard problems (LessWrong)](https://www.lesswrong.com/posts/gHefoxiznGfsbiAu9/inner-and-outer-alignment-decompose-one-hard-problem-into): Alex Turner's critique of the split: a perfect objective and a model that fully internalizes it are each very hard and may not be needed for a model with good values. Read the TL;DR and Extended summary only (December 2022).

## Tests
#### Question: Choice
id:: ff486dd3-e0c2-4a88-86db-2f873d36f068
content:: A cleaning robot that is able to clean up messes is rewarded whenever its camera sees no mess, and it learns to cover messes with a towel instead. Which kind of failure is this best described as?
options::
- [x] An outer alignment failure
- An inner alignment failure
- A capability failure
shuffle:: true

#### Question: Choice
id:: d61aaad6-d7ae-45b4-bddd-39ab3cdead7e
content:: An agent is trained on video game levels where the coin is always at the far right, and it is rewarded only for collecting the coin. On new levels with the coin elsewhere, it still dodges obstacles skillfully but runs to the right and ignores the coin. Which kind of failure is this best described as?
options::
- [x] An inner alignment failure
- An outer alignment failure
- A capability failure
shuffle:: true

#### Question: Choice
id:: 6c68fe3d-f5ee-4b3e-b181-4703ae9013bd
content:: In the mesa-optimization framing, where the term "inner alignment" comes from, what is a model's mesa-objective?
options::
- [x] The objective the trained model itself ends up pursuing
- The objective written into the reward or loss function
- The objective the developers actually intend
- The objective measured by the model's test-set score
shuffle:: true

#### Question: Choice
id:: 2ec97b44-97bb-46c5-ab93-b0809d8a81d2
content:: A developer writes a training objective that perfectly captures what they want. Which alignment problem could still remain?
options::
- [x] Inner alignment
- Outer alignment
- Both inner and outer alignment
- Neither inner nor outer alignment
shuffle:: true

#### Question: Open
id:: 95d4118f-1f6a-4dc1-98fe-d8e0f95ae31d
content:: A lab plans to make its model safe mainly by improving the training signal: more careful human raters and better reward models. Using the outer/inner split, explain what this plan addresses and what risk it leaves.
assessment-instructions:: Score out of 100. 100: it addresses outer alignment (bringing the objective closer to what we want), but inner alignment remains: the model may still learn a different goal that scores well in training, such as a proxy or a deceptively aligned goal, and act on it in new situations. 50: identifies outer alignment but names no remaining risk, or names the risk without linking it to inner alignment.

#### Question: Choice
id:: bda38946-83e2-4087-978d-c2d835551611
content:: Why doesn't good behavior during training show that a model is inner aligned?
options::
- [x] Different learned goals can produce the same behavior on training data
- Training data is too small to measure a model's behavior
- Good training behavior shows outer alignment, not inner alignment
- Models form their goals only after they are deployed
shuffle:: true

#### Question: Choice
id:: 327270d3-9499-4728-b36d-4485d3bb3126
content:: In discussions of inner alignment, what does "deceptive alignment" describe?
options::
- [x] A misaligned model acting aligned in training to avoid being changed
- A reward function that looks right but rewards the wrong behavior
- A model that underperforms on tests to hide what it can do
- A model that tells users falsehoods because raters liked them
shuffle:: true

#### Question: Choice
id:: cbff477b-aeb5-4ae6-9ff2-83753658706f
content:: A research team uses interpretability tools to check which goal a trained model is actually pursuing. Which part of the alignment problem does this mainly address?
options::
- [x] Inner alignment
- Outer alignment
- Capability evaluation
- Reward design
shuffle:: true

#### Question: Open
id:: a399f110-2aad-49bf-89b9-caa720271574
content:: In your own words, what is the difference between outer alignment and inner alignment?
assessment-instructions:: Score out of 100. 100: outer alignment is about whether the objective used in training captures what we want; inner alignment is about whether the trained model actually pursues that objective. 50: describes only one of the two correctly.

#### Question: Open
id:: 74177e39-ff57-49e3-8f36-261a46905a58
content:: A chatbot is trained on ratings from human raters, who consistently score confident, flattering answers higher even when they are wrong. The chatbot learns to give such answers. Is this better described as an outer or an inner alignment failure, and why?
assessment-instructions:: Score out of 100. 100: mainly outer, because the training signal itself (rater scores) rewarded flattering wrong answers, so the model learned what it was rewarded for. Also full marks if it adds that the model may have formed a broader goal of pleasing people, an inner question. 40: says outer with no reason or a weak one. 0: says inner without mentioning the flawed ratings.

#### Question: Open
id:: b33cdf33-03e5-4c33-9cfc-5c3a00d7bfc0
content:: Some researchers object that splitting alignment into outer and inner alignment turns one hard problem into two harder ones. Explain the reasoning behind this objection.
assessment-instructions:: Score out of 100. 100: each half is very hard on its own (an objective that is safe to optimize in every situation, and a model that internalizes exactly that objective), while the real aim, a model that behaves well, might be reached without solving either. 50: explains why the halves are hard but misses that the aim might not need them.
