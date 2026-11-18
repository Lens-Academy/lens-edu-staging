---
id: 8bdf4ad7-90a2-4ea8-bdd6-d6048e13afa6
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why a risky action that any one of many well-meaning actors can take alone gets taken too often, and describe norms that reduce this, such as deciding jointly and treating others' restraint as evidence.

## Requires

## Helpful first
- [[Net-negative projects]]

## Why it matters
Many choices in AI risk, like publishing a dangerous finding or releasing model weights, can be made by any one of many people or labs. If each acts on their own judgment, the most optimistic one sets the outcome. Knowing this helps you weigh others' restraint and coordinate before acting alone.

## Lenses

## Tests
#### Question: Choice
id:: f2e3af71-7c33-4fb4-be65-9e9a38872d5f
content:: What produces the unilateralist's curse?
options::
- [x] Random errors in estimates, with the most optimistic actor deciding
- Actors putting their own gain ahead of the common good
- Actors lacking information about the action's likely effects
- Actors copying each other's decisions instead of judging for themselves
shuffle:: true

#### Question: Choice
id:: a1d547c1-10a9-4c02-a21a-088c87023a84
content:: For the unilateralist's curse to make harmful actions happen too often, do the actors need to be biased toward acting?
options::
- [x] No, unbiased but noisy estimates are enough
- Yes, the effect comes from a bias toward acting

#### Question: Choice
id:: 5ed99e69-5de9-43db-bcf7-10a80e0d8ecd
content:: Five labs can each release a harmful tool alone. Each, independently, has a 10% chance of wrongly judging the release beneficial. Roughly how likely is it that at least one lab releases it?
options::
- [x] About 40%
- About 10%
- About 20%
- About 50%
shuffle:: true

#### Question: Choice
id:: 3218d635-5efa-4e1c-8a48-214d96f0db96
content:: Which situation fits the unilateralist's curse?
options::
- [x] Any of several groups can publish a dangerous method
- One company's board votes on releasing its model
- Several labs release models competing for the same users
- A researcher repeats an experiment to reduce random error
shuffle:: true

#### Question: Choice
id:: 899336ea-a76f-4be5-a846-c3d83af7af1e
content:: The unilateralist's curse arises when any one of many actors can take an action alone. If instead any one of many actors can block an action, whose judgment effectively decides?
options::
- [x] The most pessimistic actor's
- The most optimistic actor's
- The median actor's
- The best-informed actor's
shuffle:: true

#### Question: Choice
id:: 8320dfe8-7e47-477e-8d97-2b8728bb4660
content:: In a unilateralist's curse situation, several others who could take a risky action have chosen not to. Should that lower your own estimate of the action's value?
options::
- [x] Yes, their restraint is evidence about its value
- No, it says nothing about the action itself

#### Question: Choice
id:: 93969877-8873-4db0-8750-ba60d44b4e51
content:: Does the unilateralist's curse argument imply that you should drop an action as soon as any one other actor disagrees?
options::
- [x] No, it calls for weighing the group's views as a whole
- Yes, any disagreement shows the action is harmful

#### Question: Choice
id:: a1030beb-b726-4b2b-98e8-cb7bf8d079cb
content:: Several AI labs each have a model that might be dangerous to release openly. Which change most directly reduces the unilateralist's curse among them?
options::
- [x] Agreeing to decide jointly before any lab releases
- Each lab announcing its decision after it releases
- More labs joining, each judging independently
- Each lab keeping its risk estimate private
shuffle:: true

#### Question: Open
id:: 2c6494b0-897e-4e79-af0f-f4c95bb3b0c0
content:: Someone says: "Many groups could release this dangerous tool, so my releasing it changes little." How does the unilateralist's curse cut against this reasoning?
assessment-instructions:: Score out of 100. 100 for either point, clearly made: if everyone reasons this way, the tool is released as soon as the most optimistic group acts; or the others not having released it is evidence they judged it harmful, so you may be the one making the mistake. 50 for a vague appeal to caution or coordination.

#### Question: Open
id:: 1b23c5e6-2878-4cfd-b66e-1f4b2d25a78d
content:: Name one decision in AI development or AI safety where the unilateralist's curse could apply, and say what makes it fit.
assessment-instructions:: Score out of 100. 100 for a plausible example (such as releasing a dangerous model's weights, publishing capabilities research or a hazardous finding, or going public with a sensitive policy idea) plus the reason: many actors could each do it alone, and one doing it is enough. 50 for an example without the reason.

#### Question: Open
id:: e4077e16-8fc3-4b33-bcc0-d124037b55aa
content:: You and four other researchers have each found the same way to get around an AI model's safeguards. You think publishing it would help, but none of the others has published. Using the idea of the unilateralist's curse, what should you do before deciding?
assessment-instructions:: Score out of 100. 100 for: treat the others' restraint as evidence that publishing may be harmful, and consult them or a shared process (such as disclosing to the model's developer) before publishing. 50 for only one of these. 0 for publishing straight away because you are confident.
