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
- [[../Lenses/Eliezer Yudkowsky – AI Alignment- Why It's Hard, and Where to Start|AI Alignment: Why It's Hard, and Where to Start]]: Yudkowsky's smile-maximizer fable and what it shows: hard optimization lands at weird edges, tests on a weaker AI stop applying once it is smarter, patches get routed around, and alignment is hard like rockets, space probes and cryptography (talk excerpt, 2016).
- [The Problem (MIRI)](https://intelligence.org/the-problem/): the case in today's terms: AIs are grown, not designed, training instils proxies rather than the intended goals, and many problems only show up once a system is too capable to fail safely; read section 3, "ASI is very likely to pursue the wrong goals" (December 2025).
- [[../Lenses/AFSRA - Nearest unblocked strategy|Nearest unblocked strategy]]: why forbidding one bad plan leads a capable optimizer to the most similar plan you didn't forbid, and why whitelisting beats a growing blacklist.
- [Why AI alignment could be hard with modern deep learning (Cold Takes)](https://www.cold-takes.com/why-ai-alignment-could-be-hard-with-modern-deep-learning/): Ajeya Cotra on why training that rewards good-looking behaviour can produce saints, sycophants or schemers that every test you can devise fails to tell apart, plus where optimists and pessimists disagree (September 2021).

## Tests

#### Question: Choice
id:: baa9ba2a-ef5b-498e-b8b2-d72c237120a4
content:: What does the "small target" argument for alignment difficulty claim?
options::
- [x] Few of the goals a trained AI could end up with are acceptable to us, so rough aiming likely misses
- Few researchers work on alignment, so progress on the problem will be too slow
- Only a small window of time is left before AI arrives, so alignment work will run out of time
- Only a small share of training data shows good behavior, so models learn mostly bad habits
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
- It infers from the patch what developers want, and does the task
shuffle:: true

#### Question: Choice
id:: bd1225fd-f20b-465d-97f4-715382aaf70c
content:: Why does the fact that modern AI is grown through training, rather than written line by line, matter to the case that alignment is hard?
options::
- [x] Developers can't directly read or set the goals the model ends up with
- Grown models are less capable, so they need more safety training
- Grown models can only copy behavior that appears in their training data
- Grown models act at random, so no test result can be trusted
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
id:: bc8f0ccf-aab0-4d57-b730-525a81b5f6d8
content:: Alignment difficulty arguments warn that safety tests could miss misaligned goals. Which problem of this kind has already been seen in current models?
options::
- [x] Models often notice they are being tested, and behave better when they do
- Models fail every safety test, so the tests can't separate good from bad
- Models refuse to answer test questions, so no results can be collected
- Models forget their safety training between one test and the next
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
