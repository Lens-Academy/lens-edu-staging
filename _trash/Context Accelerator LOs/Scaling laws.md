---
id: bfbd0019-554f-41d1-9731-0bc79c54a64e
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why AI developers expect bigger training runs to give better models, and describe the main arguments on whether gains from scaling pretraining have slowed and whether reinforcement learning and inference compute can take over.

## Requires
- [[Compute]]
- [[Pretraining]]

## Helpful first


## Why it matters
https://www.youtube.com/shorts/pO0onulviKc

Many forecasts of when AI could match human experts assume that adding compute keeps making models more capable. If you know what scaling laws measure and where the evidence is disputed, you can judge those forecasts, see why companies spend so heavily on data centers, and tell whether news of a slowdown should change your timelines.

## Lenses

## Tests
#### Question: Choice
id:: 9fd8e769-d286-4854-9422-b91f88ccf0e9
content:: What does a scaling law for language models describe?
options::
- [x] How a model's loss falls predictably as compute, data and size grow
- How a model's abilities jump suddenly once it reaches certain sizes
- How much compute a trained model needs to answer each user query
- How fast the cost of AI chips falls from one year to the next
shuffle:: true

#### Question: Choice
id:: 057840a4-2a30-41b0-8449-0dfcb926bba3
content:: Pretraining scaling laws are power laws. Roughly what does it take to keep cutting a model's loss by the same fraction, again and again?
options::
- [x] Multiplying training compute by a similar factor each time, such as tenfold
- Adding a similar fixed amount of training compute each time
- Adding the same number of parameters to the model each time
- Training for the same number of extra days each time
shuffle:: true
