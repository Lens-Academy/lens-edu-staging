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
Score out of 100: the sum of the three elements below.

The scenario: two systems both correctly predict that a storm will close a bridge. One routes delivery trucks away from the bridge to keep delays low. The other routes rescue vehicles toward it to reach stranded people. A third system routes vehicles exceptionally well but cannot reason about anything outside transportation. The framework the question refers to defines intelligence as prediction plus steering: predicting is forming correct expectations about what will happen, steering is choosing actions that bring about an outcome the system is aiming for. A mind is more general the wider the range of domains in which it can predict and steer.

35: What the first two systems do when they predict and when they steer. Predicting: both form the same correct expectation that the bridge will close. Steering: each picks routes that lead to its own goal (avoiding delay, reaching the stranded people). Any wording that keeps "what will happen" apart from "what to do about it" earns this.

35: Different destinations do not show that either system is less intelligent. Both predicted equally well, and each steers well toward its own goal. Success at steering is measured against the goal being pursued, so a difference in goals is not a difference in competence. An answer that says this and then argues against the framework with a coherent reason still earns these points.

30: What separates the third system from a general reasoner: its skill covers one narrow domain. A more general reasoner can predict and steer across many different kinds of problems, not only routing. Being excellent at one task does not make a system general.
Cap at 40 if the answer treats the choice of destination as part of the prediction, for example says the two systems predict differently because they want different things.

Model answer, for the feedback, not a grading checklist: "Both systems make the same prediction: the storm will close the bridge. They differ in steering, in what they do with that prediction. One steers trucks around the closure to avoid delays, the other steers rescue vehicles to it. Neither is less intelligent: they predict equally well and each steers well toward what it is aiming for. Steering success depends on the goal, and different goals are not a lack of skill. The third system is excellent but narrow. It can only predict and steer inside transportation, while a general reasoner can carry the same predicting and steering into almost any domain, which is what makes general intelligence so powerful."

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
