---
id: cafc40b7-fb3a-4415-9b1d-c65b85329b73
learning-outcome: "Define intelligence as prediction plus steering, explain why generality drives its power, and distinguish predictive competence from the goals steering pursues."
reading-from: "IMAGINE, IF YOU would—though of course nothing like this ever happened, it being just a parable—that biological life on Earth had been the result of a game between gods."
reading-to: "it is still in some important sense 'shallow' compared to a human twelve-year-old."
authors:
  - Chris+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Artificial Intelligence]]"
stage: beginner
eval-results:
  content-sha: 2fd083f6
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question requires the chapter as scaffolding; not parseable by someone who never read it."}
  evidence: {B1: "Using the chapter's framework, analyze the three systems."}
---

## Test:
id:: b5981716-08c0-40b1-a005-2cfbdde6d0c7
#### Question
content::
Two systems accurately predict that a severe storm will close a bridge. One routes delivery trucks away from it to minimize delays. The other routes rescue vehicles toward it to reach stranded people. A third system is exceptionally good at this routing task but cannot reason outside transportation.

Analyze the three systems. For the first two, distinguish the work of predicting what will happen from the work of steering toward a chosen outcome, and explain how the two relate. Does choosing different destinations show that one system is less intelligent? And what distinguishes the third system from a more general reasoner?

assessment-instructions::
Grade the student's reasoning, not whether they use the authors' exact wording or agree with the broader argument.

Pass only if the answer demonstrates all three checks:
1. **Prediction and steering:** Correctly distinguishes forming expectations about what will happen from selecting actions that lead toward a chosen outcome. It may also explain how the two kinds of work support each other.
2. **Goals and competence:** Recognizes that the first two systems can agree about the storm while steering toward different destinations because steering success is relative to the outcome pursued. Different destinations do not by themselves show that one system predicts or reasons less competently.
3. **Generality:** Explains that exceptional performance in one routing domain can still be narrow. A more general intelligence can predict and steer successfully across a wider range of domains.

Fail if the answer conflates prediction with preference, assumes equally intelligent agents must choose the same destination, or treats high performance on one task as sufficient evidence of generality.

Do not require the student to claim that direction-agnostic intelligence is necessarily dangerous. That safety conclusion is not established by this assigned section alone. A student who reconstructs the framework accurately and then challenges it with a coherent argument can pass.

Give concise qualitative feedback naming which checks were demonstrated and which need work.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Define Intelligence - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Define Intelligence]]
