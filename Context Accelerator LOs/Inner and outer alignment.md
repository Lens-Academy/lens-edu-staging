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
