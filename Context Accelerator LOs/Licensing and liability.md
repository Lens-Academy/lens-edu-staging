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
Licensing and liability come up often in debates about AI law. Knowing how each works and where each breaks down helps you judge proposals, from California's vetoed SB 1047 to current US plans to override state AI laws, and notice when a policy would leave the largest risks uncovered.

## Lenses
- [Your AI Breaks It? You Buy It (Noema)](https://www.noemamag.com/your-ai-breaks-it-you-buy-it/): the case for strict liability on frontier AI developers, why ordinary damages can't deter a catastrophe, punitive damages for near misses, and the hard cases of open-weight models and SB 1047, from the field's leading proponent of liability (September 2024).
- [Licensing Frontier AI Development: Legal Considerations and Best Practices (Lawfare)](https://www.lawfaremedia.org/article/licensing-frontier-ai-development-legal-considerations-and-best-practices): what a licensing regime covering hardware, training and deployment would require (security, dangerous-capability evaluations, red-teaming, monitoring), which agency might run it, and how it could lock in a few big companies (January 2024).
- [Tort Law Should Be the Centerpiece of AI Governance (Lawfare)](https://www.lawfaremedia.org/article/tort-law-should-be-the-centerpiece-of-ai-governance): Weil's side of a live debate over whether liability should lead or only fill gaps, with why liability beats prescriptive rules, mandatory liability insurance, and the limits of liability (August 2024).
- [An FDA for AI? Pitfalls and Plausibility of Approval Regulation for Frontier AI (arXiv)](https://arxiv.org/html/2408.00821v1): two Harvard scholars test the FDA analogy and find where AI strains it: what counts as the regulated product, hard-to-measure risks, open weights and enforcement; read sections 2–4 (August 2024) (more advanced).
- [[../Lenses/arxiv-a-framework-for-the-private-governance-of-frontier-artificial-intelligence|A Framework for the Private Governance of Frontier AI]] (Noah's CG list)

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
- It gives developers clear rules to follow before release
- It lets regulators inspect models before release
shuffle:: true

#### Question: Choice
id:: 56e84058-1507-4f34-bd77-0a5ca19576a4
content:: Why is ordinary liability a weak defense against an AI catastrophe that kills most of humanity?
options::
- [x] Damages would be unpayable, and few would be left to sue
- Juries rarely blame companies for software failures
- Liability covers only harm to property, not to people
- Courts would need years to agree on who was at fault
shuffle:: true

#### Question: Open
id:: 9fcd3153-c793-4680-bbf4-01f37d8876b3
content:: One proposal for AI liability, from legal scholar Gabriel Weil, adds extra (punitive) damages when an AI causes a limited harm that could easily have been catastrophic. What problem is this meant to solve?
assessment-instructions:: Score out of 100. 100: the catastrophic harm itself couldn't be compensated afterward (too large, or nobody left to sue), so the incentive to avoid it must come through smaller cases that show the risk. 50 for "to deter developers" without explaining why ordinary damages fall short.

#### Question: Choice
id:: cb87ec0b-d590-44a5-bb51-0e3d908fbecb
content:: In proposals to license frontier AI development, which of these is a typical condition for getting a license?
options::
- [x] Passing dangerous-capability evaluations before deployment
- Paying damages to people harmed by the model
- Showing the model will be commercially profitable
- Capping how many users the model can have
shuffle:: true

#### Question: Choice
id:: c3361098-3f31-4a9b-9e9b-c58b7133ef6c
content:: A common criticism of licensing frontier AI is that it could do which of these?
options::
- [x] Entrench large incumbents by raising barriers to new entrants
- Make developers pay for harms caused by other companies
- Make developers pay for harms they could not have foreseen
- Act only after harm has already happened
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

#### Question: Open
id:: 872d8958-00c4-4b7a-9b90-bf7b62a75f25
content:: A developer releases a model's weights openly. Someone else fine-tunes it to remove its safeguards and uses it to cause harm. Why is this case hard for liability rules, and what is one argument for holding the original developer liable anyway?
assessment-instructions:: Score out of 100. 50 for a real difficulty: another party's deliberate changes and misuse caused the harm, so blame is split or unclear; the developer can't control or recall the model once released; harms are hard to trace back. 50 for a real argument: the misuse was foreseeable; the developer chose to release and is best placed to prevent it; otherwise nobody who can pay is liable, so releasing carries no cost.

#### Question: Choice
id:: a48a453c-e023-46a6-957f-6a3406cb2015
content:: Some proposals would protect AI developers from lawsuits if they follow approved safety standards (a "safe harbor"). What is the main worry about this for catastrophic risks?
options::
- [x] Developers would have little reason to guard against risks the standards miss
- Victims would win larger damages than the harm justifies
- Developers would face more lawsuits than before
- Courts would have to write the safety standards themselves
shuffle:: true

#### Question: Open
id:: b61c911e-747a-4f68-966d-e35deb1c20fb
content:: Supporters of licensing frontier AI often compare it to licensing in another industry. Name one such industry and one way AI differs from it that makes licensing harder.
assessment-instructions:: Score out of 100. 100 for a fitting industry (drugs, nuclear power, aviation, banking or similar) plus a real difference, e.g. AI capabilities are hard to measure before release, AI is general-purpose, models copy easily or are released openly, development is international, or the field changes fast. 50 for only one part.
