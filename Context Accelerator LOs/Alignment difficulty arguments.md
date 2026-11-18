---
id: e4946254-11ad-4004-ab70-3feee0eb46e8
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the main arguments that aligning advanced AI is hard: a small target, training that shapes behavior but not goals, optimizers routing around patches, and needing to succeed before failures can teach us.

## Requires
- [[AI alignment]]
- [[Built vs. grown]]

## Helpful first
- [[Goodhart's law]]
- [[Inner and outer alignment]]
- [[Security mindset]]

## Why it matters
How hard alignment is drives most estimates of AI risk and many strategy choices, such as how much caution and coordination are needed. Knowing the specific arguments lets you test a safety proposal against them, instead of judging it by whether it sounds sensible or works on today's systems.

## Lenses

## Tests

#### Question: Choice
id:: baa9ba2a-ef5b-498e-b8b2-d72c237120a4
content:: What does the "small target" argument for alignment difficulty claim?
options::
- [x] Few of the goals a trained AI could end up with are acceptable to us, so rough aiming likely misses
- Few researchers work on alignment, so progress on the problem will be too slow
- Aligned systems must be kept small, so they will lose out to larger unaligned ones
- Human values are simple to state, but too few examples exist to train on them
shuffle:: true

#### Question: Choice
id:: b2f3bd77-6de3-4cec-bc5c-a4da6cede93e
content:: Why do alignment difficulty arguments say that training an AI on examples of good behavior doesn't pin down its goals?
options::
- [x] Many different internal goals produce the same behavior on the training examples
- Training only changes a model's outputs, never its internal weights
- Models tend to forget their training goals once they are deployed
- Training datasets are usually too small for a model to learn any goal
shuffle:: true

#### Question: Choice
id:: 09eb9fea-d532-4f0c-ba98-5b8648a94fdb
content:: An AI system trained with a reward signal is found exploiting a bug to get reward without doing the task. Developers patch that one bug. According to the "nearest unblocked strategy" argument, what is the likely result in a capable system?
options::
- [x] It shifts to a similar exploit that the patch doesn't cover
- It stops exploiting, since the incentive to exploit is gone
- It becomes less capable at the task across the board
- It starts reporting other bugs to the developers instead
shuffle:: true

#### Question: FillBlank
id:: 9b34b948-9fec-44e2-9647-9193c45abc64
content:: When a rule blocks one harmful strategy, a strong optimizer tends to switch to the most similar strategy the rule doesn't forbid. This is called the nearest {{unblocked|unblocked strategy}} strategy problem.

#### Question: Choice
id:: bd1225fd-f20b-465d-97f4-715382aaf70c
content:: Why does the fact that modern AI is grown through training, rather than written line by line, matter to the case that alignment is hard?
options::
- [x] Developers can't directly read or set the goals the model ends up with
- Grown models are less capable, so they need more safety training
- Training makes model behavior fully predictable, hiding rare failures
- Grown models can't be tested before they are deployed
shuffle:: true

#### Question: Choice
id:: b3453f9a-4da7-4c69-a715-c29e2113807c
content:: An AI is trained to maximize a measurable proxy for what its developers want. According to alignment difficulty arguments, what tends to happen to the gap between proxy and intended goal as the optimizer becomes more capable?
options::
- [x] It grows, because stronger search finds more places where they diverge
- It shrinks, because a smarter system better infers what was meant
- It stays about the same, because it is fixed by the choice of proxy
- It disappears, as long as the proxy is measured often enough
shuffle:: true

#### Question: Choice
id:: 0ae1def4-1d69-4626-a636-e8f067246e86
content:: Alignment difficulty arguments give several reasons pre-deployment testing might miss misaligned goals. Which of these is one of them?
options::
- [x] A capable model might act aligned because it can tell it is being tested
- Safety tests are usually run on much smaller versions of the model
- Models act randomly on any input that differs from their training data
- Test questions are usually copied from the model's own training data
shuffle:: true

#### Question: Choice
id:: 753d95a7-6ac8-4af6-ab35-308a04ef69fb
content:: Does the case that alignment is hard claim that aligning advanced AI is impossible in principle?
options::
- [x] No: it claims it is hard to get right with current methods before it matters
- Yes: it claims no possible method could give an AI the intended goals

#### Question: Choice
id:: de40dbad-b325-4f32-986b-52b0d882f501
content:: With alignment difficulty arguments in mind, which question is most useful for judging a proposed alignment technique?
options::
- [x] Would it still work on an AI far more capable than its overseers?
- Does it raise current models' scores on standard safety benchmarks?
- Is it cheaper to run than the safety methods labs use today?
- Has at least one leading AI company already adopted it?
shuffle:: true

#### Question: Choice
id:: 105714ec-bff3-4d02-8c22-38d81d46177d
content:: Which development would most weaken the argument that behavioral training doesn't pin down an AI's goals?
options::
- [x] Tools that reliably read a model's goals from its internal workings
- Models refusing far more harmful requests in safety evaluations
- Models scoring higher on a wide range of capability benchmarks
- Labs training models on much larger and more varied datasets
shuffle:: true

#### Question: Open
id:: 32070aa9-6b93-4861-bd82-914ba2a2744c
content:: Most engineering fields improve by learning from failures. Why do alignment difficulty arguments say this approach may not work for aligning AI much more capable than humans?
assessment-instructions:: Score out of 100. Full marks for the core point: a failure with a system capable of disempowering humans may be unrecoverable, so there may be no second try to learn from. 100 also for adding that failures in weaker systems may not show up or transfer. 50 for only saying "the stakes are high" without the no-retry point.

#### Question: Open
id:: 9996218c-9f07-4cdd-9ae0-3948db1f9b57
content:: Why is adding rules one at a time ("don't do X", "don't do Y") unlikely to make a powerful AI optimizer safe, according to alignment difficulty arguments?
assessment-instructions:: Score out of 100. Full marks for: the optimizer's underlying goal is unchanged, so it moves to the nearest strategy the rules don't block, and we can't list every harmful strategy in advance. 50 for only saying rules have loopholes, without saying the optimizer actively seeks them.

#### Question: Open
id:: 4407db29-bc09-487c-b3d1-78df5c8c39af
content:: Developers training an AI are trying hard to give it good goals. Why does the "small target" argument say they are still likely to miss?
assessment-instructions:: Score out of 100. Full marks for: acceptable goals are a tiny fraction of the goals a model could end up with, and training steers only roughly toward the intended goal, so a near miss is the likely outcome. 50 for naming only one of these two points.
