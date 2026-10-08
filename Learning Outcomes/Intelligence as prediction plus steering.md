---
id: cafc40b7-fb3a-4415-9b1d-c65b85329b73
learning-outcome: "Define intelligence as prediction plus steering, explain why generality drives its power, and distinguish predictive competence from the goals steering pursues."
reading-from: "IMAGINE, IF YOU would—though of course nothing like this ever happened, it being just a parable—that biological life on Earth had been the result of a game between gods."
reading-to: "it is still in some important sense 'shallow' compared to a human twelve-year-old."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/1 Artificial Intelligence/What intelligence is]]"
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
#### Question: Open
id:: 8ba818e9-5340-44ff-a346-7fa476b77acb
content::
Two systems accurately predict that a severe storm will close a bridge. One routes delivery trucks away from it to minimize delays. The other routes rescue vehicles toward it to reach stranded people. A third system is exceptionally good at this routing task but cannot reason outside transportation.

Using the chapter's framework, analyze the three systems. What are the first two doing when they predict and when they steer? Does choosing different destinations show that one is less intelligent? What distinguishes the third system from a more general reasoner?

assessment-instructions::
Grade the student's reasoning, not whether they use the authors' exact wording or agree with the broader argument.

Pass only if the answer demonstrates all three checks:
1. **Prediction and steering:** Correctly distinguishes forming expectations about what will happen from selecting actions that lead toward a chosen outcome. It may also explain how the two kinds of work support each other.
2. **Goals and competence:** Recognizes that the first two systems can agree about the storm while steering toward different destinations because steering success is relative to the outcome pursued. Different destinations do not by themselves show that one system predicts or reasons less competently.
3. **Generality:** Explains that exceptional performance in one routing domain can still be narrow. A more general intelligence can predict and steer successfully across a wider range of domains.

Fail if the answer conflates prediction with preference, assumes equally intelligent agents must choose the same destination, or treats high performance on one task as sufficient evidence of generality.

Do not require the student to claim that direction-agnostic intelligence is necessarily dangerous. That safety conclusion is not established by this assigned section alone. A student who reconstructs the framework accurately and then challenges it with a coherent argument can pass.

Give concise qualitative feedback naming which checks were demonstrated and which need work.

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they blurred predicting and steering, for example by calling the choice of route a prediction, ask what the first two systems agree about and what they differ on.
- If they suggested one of the first two systems is less intelligent because of where it sends its vehicles, ask whether either one predicted the storm worse, and what each system's success is measured against.
- If they treated the third system's excellent routing as a sign of general intelligence, ask what it would do with a problem outside transportation, and what a general reasoner can do there that it cannot.

A learner who reconstructs the argument and then disagrees with it has done what was asked. Engage with the disagreement, don't steer them back to the chapter's view.

At full marks, just confirm briefly. Don't cite the numbered checks or the words pass and fail (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the bridge itself. Both systems expect the same closure, so whatever differs between them is not their prediction. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Define Intelligence - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Define Intelligence]]
