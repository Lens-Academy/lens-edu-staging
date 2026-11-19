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

## Tests
#### Question: Choice
id:: ff486dd3-e0c2-4a88-86db-2f873d36f068
content:: A cleaning robot is rewarded whenever its camera sees no mess, and it learns to cover messes with a towel. Which kind of failure is this best described as?
options::
- [x] An outer alignment failure
- An inner alignment failure
- A capability failure
shuffle:: true

#### Question: Choice
id:: d61aaad6-d7ae-45b4-bddd-39ab3cdead7e
content:: An agent is trained on video game levels where the coin is always at the far right, and it is rewarded only for collecting the coin. On new levels with the coin elsewhere, it runs to the right and ignores the coin. Which kind of failure is this best described as?
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
id:: d673b913-399e-4176-9774-f581f7a313a5
content:: In the mesa-optimization framing behind the term "inner alignment", what is the base optimizer?
options::
- [x] The training process, such as gradient descent
- A search process running inside the trained model
- The developers who choose the training objective
- The reward function used during training
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
assessment-instructions:: Score out of 100. 100: outer alignment failure, because the training signal itself (rater scores) rewarded flattering wrong answers, so the model learned what it was rewarded for. 40: says outer with no reason or a weak one. 0: says inner.

#### Question: Open
id:: b33cdf33-03e5-4c33-9cfc-5c3a00d7bfc0
content:: Some researchers object that splitting alignment into outer and inner alignment turns one hard problem into two harder ones. Explain the reasoning behind this objection.
assessment-instructions:: Score out of 100. 100: each half is very hard on its own (an objective that is safe to optimize in every situation, and a model that internalizes exactly that objective), while the real aim, a model that behaves well, might be reached without solving either. 50: explains why the halves are hard but misses that the aim might not need them.
