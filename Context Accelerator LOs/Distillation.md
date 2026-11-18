---
id: 5b1070c8-7ece-481d-8b5e-044def739c90
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how distillation trains a smaller student model on the outputs of a larger teacher model, and why this spreads capabilities quickly and cheaply, even to developers who never get the teacher's weights.

## Requires
- [[Models and weights]]

## Helpful first


## Why it matters
https://youtu.be/Wtayoq3ysJY

If a model's skills can be copied from its outputs, then guarding its weights and limiting chips will not by themselves keep a lead. Understanding distillation helps you judge how long a frontier advantage lasts, why AI companies police how their models are queried, and why safeguards may not survive copying.

## Lenses

## Tests
#### Question: Choice
id:: 20d790dc-d90b-46ce-8970-2b0d04bc67ec
content:: In AI model distillation, what is the smaller "student" model trained on?
options::
- [x] The larger teacher model's outputs on many inputs
- A copy of the teacher model's weights
- The teacher's raw training data, with no teacher involved
- A compressed version of the teacher's training code
shuffle:: true

#### Question: Choice
id:: 0984680c-3213-45aa-8c2b-992c020e3042
content:: A company has no access to a competitor's model weights but can query the model through its public API. Can the company distill the competitor's model?
options::
- [x] Yes, distillation works from the teacher's outputs
- No, distillation needs the teacher's weights
