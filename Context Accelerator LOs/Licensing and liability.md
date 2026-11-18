---
id: c71ea371-5587-449e-bd94-0f8ce429a4fa
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how licensing and liability would each govern frontier AI developers, what each aims to achieve, and the main objections to each, including why liability struggles with catastrophic harms.

## Requires

## Helpful first

## Why it matters
Licensing and liability come up often in debates about AI law. Knowing how each works and where each breaks down lets you judge proposals such as California's SB 1047 and notice when a policy would leave the largest risks uncovered.

## Lenses

## Tests

#### Question: Open
id:: 92c66050-3808-4a2a-b25a-a186ce076024
content:: What is the main difference between licensing and liability as ways to govern AI developers, in terms of when each takes effect?
assessment-instructions:: Score out of 100. 100: licensing requires permission or approval before a model is developed or deployed (ex ante); liability makes developers pay after a harm has happened (ex post). 50 if only one side is described correctly.

#### Question: Choice
id:: 5021510a-9d64-45fd-aa8e-7e81ebb42e0c
content:: Under a strict liability rule, when must an AI developer pay for harm its model causes?
options::
- [x] Even if it took every reasonable precaution
- Only if it failed to take reasonable care
- Only if it intended the harm to happen
- Only if a regulator had warned it beforehand
shuffle:: true

#### Question: Choice
id:: a30ed6ba-fb07-478d-b18d-1a2a57eaad7b
content:: Which is a key advantage of liability over licensing for governing AI?
options::
- [x] Regulators needn't spell out safe practices in advance
- It stops harms before they happen
- It works without courts or lawsuits
- It is limited to models above a compute threshold
shuffle:: true

#### Question: Choice
id:: 56e84058-1507-4f34-bd77-0a5ca19576a4
content:: Why is ordinary liability a weak defense against an AI catastrophe that kills most of humanity?
options::
- [x] Damages would be unpayable, and few would be left to sue
- Courts don't hear cases involving software
- Liability law bans damages above a fixed cap
- Developers can only be sued by governments
shuffle:: true

#### Question: Open
id:: 9fcd3153-c793-4680-bbf4-01f37d8876b3
content:: Some liability proposals for AI add extra (punitive) damages when an AI causes a limited harm that could easily have been catastrophic. What problem is this meant to solve?
assessment-instructions:: Score out of 100. 100: the catastrophic harm itself couldn't be compensated afterward (too large, or nobody left to sue), so the incentive to avoid it must come through smaller cases that show the risk. 50 for "to deter developers" without explaining why ordinary damages fall short.

#### Question: Choice
id:: cb87ec0b-d590-44a5-bb51-0e3d908fbecb
content:: In proposals to license frontier AI development, which of these is a typical condition for getting a license?
options::
- [x] Passing dangerous-capability evaluations before deployment
- Paying damages to people harmed by the model
- Releasing the model's weights to the public
- Publishing the full training dataset
shuffle:: true

#### Question: Choice
id:: c3361098-3f31-4a9b-9e9b-c58b7133ef6c
content:: A common criticism of licensing frontier AI is that it could do which of these?
options::
- [x] Entrench large incumbents by raising barriers to new entrants
- Make developers pay for harms caused by other companies
- Force developers to open-source their most capable models
- Remove government oversight of how AI is deployed
shuffle:: true

#### Question: Choice
id:: fb809ab5-17a5-4ffd-a954-327eb5366d3a
content:: A licensing law applies to AI models trained with more than a fixed amount of compute. Why might it cover fewer dangerous models over time?
options::
- [x] Efficiency gains let smaller training runs reach the same capabilities
- Frontier training runs are using less compute each year
- Chips are becoming too costly to reach the threshold
- Courts tend to strike down rules based on compute
shuffle:: true

#### Question: Choice
id:: 7600d594-b07d-4ec7-90ea-dcf1fb6ed3cb
content:: Apart from making sure victims get paid, what is a main reason to require AI developers to carry liability insurance?
options::
- [x] Insurers would price the risk and push developers to reduce it
- It would move liability from developers onto their users
- It would cap the damages a court could award
- It would exempt insured developers from safety testing
shuffle:: true

#### Question: Choice
id:: a7f2fc06-b6c6-4c14-9ab0-5f7698d12b7b
content:: A developer releases a model's weights openly. Someone else fine-tunes it to remove its safeguards and uses it to cause harm. Why is this case hard for liability rules?
options::
- [x] The harm came through another party's changes the developer couldn't control
- Open-weight models fall outside every country's liability laws
- Fine-tuning removes any record of which company made the model
- The developer earns no revenue from the model to pay damages
shuffle:: true

#### Question: Choice
id:: 1392c234-c15c-4fce-a9cc-18c4d4d43c3d
content:: Which of these would weaken liability as a tool for making AI developers careful?
options::
- [x] A law shielding developers from lawsuits over harms done with their models
- Requiring frontier developers to carry liability insurance
- Allowing punitive damages for near-miss incidents
- Applying strict liability to frontier AI developers
shuffle:: true

#### Question: Choice
id:: 77a099b3-0fdf-4aac-b023-c4e30d3657a6
content:: What happened to California's SB 1047, a 2024 bill that would have imposed safety duties on developers of very large AI models?
options::
- [x] The governor vetoed it
- It was signed into law
- A court struck it down
- Its sponsor withdrew it
shuffle:: true

#### Question: Open
id:: b61c911e-747a-4f68-966d-e35deb1c20fb
content:: Supporters of licensing frontier AI often compare it to licensing in another industry. Name one such industry and one way AI differs from it that makes licensing harder.
assessment-instructions:: Score out of 100. 100 for a fitting industry (drugs, nuclear power, aviation, banking or similar) plus a real difference, e.g. AI capabilities are hard to measure before release, AI is general-purpose, models copy easily or are released openly, development is international, or the field changes fast. 50 for only one part.
