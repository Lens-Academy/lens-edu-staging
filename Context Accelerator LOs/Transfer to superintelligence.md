---
id: eb66f36d-23fc-4084-b556-c53f9461a088
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the main reasons to doubt that today's safety methods, and evidence from today's models, will carry over to AI much smarter than humans, and the argument that each AI generation can help make the next one safe.

## Requires
- [[AI alignment]]

## Helpful first
- [[First critical try]]
- [[Aligned behavior so far]]

## Why it matters
Most safety methods are tested on models weaker than the systems they are meant to protect against. If you can judge whether a method is likely to carry over, you can tell which reassurances about current models matter for the future, and which research plans rest on assumptions that may fail.

## Lenses

## Tests

#### Question: Choice
id:: 22ef6cee-a9f3-49b8-b984-c24de111c47a
content:: Training methods like RLHF rely on humans judging which of a model's outputs are better. Why might this work less well for AI much more capable than humans?
options::
- [x] Humans may not be able to tell good outputs from subtly flawed ones
- Reward models run out of training data at superhuman scale
- Larger models stop responding to reward signals during training
- Human raters become too expensive once models are very large
shuffle:: true

#### Question: Choice
id:: b1d574e3-bb6e-450e-b762-d8cee03875e0
content:: Current AI models rarely try to undermine their developers' oversight in tests. What is the main reason many researchers think this says little about much more capable future systems?
options::
- [x] Current models may lack the ability to succeed, so the choice was never really tested
- Too few models have been tested for the results to be statistically reliable
- Future systems will be trained mostly on synthetic rather than human data
- Tests are run by the labs themselves rather than by outside auditors
shuffle:: true

#### Question: Choice
id:: acf0326c-300a-4c63-aff9-004ff94c8b4b
content:: In the "sharp left turn" argument, an AI's capabilities suddenly generalize far beyond the situations it was trained on. What does the argument say happens to its alignment?
options::
- [x] It generalizes less far, so the AI's goals stop matching what was intended
- It generalizes further than its capabilities, making the AI overly cautious
- It is lost because new skills overwrite the AI's earlier training
- It becomes easier to check, because the AI's reasoning becomes more structured
shuffle:: true

#### Question: Choice
id:: 5b85a456-fd43-4072-9940-f2432267a0a0
content:: Weak-to-strong generalization research trains a strong model using labels from a much weaker model, and measures whether the strong model ends up better than its supervisor. Why is this used as a stand-in for aligning superhuman AI?
options::
- [x] Humans supervising superhuman AI would be the weaker supervisor
- Strong models are cheaper to train when given weak labels
- Weaker models are more aligned, so their values pass to the strong model
- It tests whether strong models can be compressed into weaker ones
shuffle:: true

#### Question: Choice
id:: 12214678-be57-49a0-b924-a57c1abed71a
content:: The AI control approach often uses weaker, trusted models to monitor a stronger model that might be misaligned. Why is this expected to get harder as the monitored model becomes more capable?
options::
- [x] The capability gap grows, so subtle sabotage becomes harder to spot
- Weaker models stop being trustworthy once a stronger model exists
- Stronger models produce outputs too fast for monitors to read
- Trusted models must be retrained each time the stronger model updates
shuffle:: true

#### Question: Choice
id:: 32798769-65e4-43d2-bd75-a3f30f4cf9a7
content:: Some researchers argue that today's alignment methods don't need to work on superintelligence directly. What is the usual reasoning behind this view?
options::
- [x] Each trusted AI generation can help align and check a slightly stronger successor
- A superintelligent system will align itself once it understands human values
- AI capabilities will level off before systems become much smarter than humans
- Regulation will keep deployed AI at roughly human level
shuffle:: true

#### Question: Choice
id:: b69ed21f-480a-4809-98e1-cd34a5587a5e
content:: A dangerous-capability evaluation finds that a model can't complete a harmful task. Why might such a result be less trustworthy for much more capable models?
options::
- [x] The model may recognize the test and deliberately underperform
- Test tasks leak into training data and inflate the model's scores
- Larger models answer multiple-choice questions more randomly
- Benchmark scores stop rising once models pass human level
shuffle:: true

#### Question: Choice
id:: 8aefa7d5-e1e4-4fc1-a608-8ffc983b772e
content:: Interpretability research tries to understand a model by studying its internal computations. Why might methods that work on current models be harder to apply to far more capable ones?
options::
- [x] Their internal concepts may be ones humans have no words or intuitions for
- Their activations turn into random noise at large scale
- They will no longer be built from neural network weights
- The methods require the model's training data to be made public
shuffle:: true

#### Question: Open
id:: 37c26065-675d-4c80-b15e-07b97b86c27a
content:: Name one method used to make current AI models safe, or to check that they are, and give one reason it might fail for a system much more capable than humans.
assessment-instructions:: Score out of 100. 100 for a real method (e.g. RLHF, constitutional training, red-teaming, evaluations, monitoring or control, interpretability) paired with a fitting reason, such as: humans can't judge superhuman outputs; the model may detect tests or hide intentions; it gains options it never had in training; its concepts become alien; trusted monitors fall too far behind. 50 if the reason is vague or doesn't fit the method.

#### Question: Open
id:: ed427baa-3260-4935-bdc7-4fb5b7d282a0
content:: Plans to have AI systems do alignment research for their successors face a checking problem. Why is it harder to check AI-produced alignment research than AI-written code?
assessment-instructions:: Score out of 100. 100 for the point that code can be tested by running it, while claims that a system is safe or aligned have no quick, reliable test, so flawed or sabotaged research may look convincing and errors may only show once it's too late. 50 for saying only that alignment research is "hard" without saying why checking it is harder.

#### Question: Open
id:: 8288fe68-e8d2-4cdf-a2eb-c442ee43bfb8
content:: Suppose a safety technique works on current models but probably won't work on superintelligence. Give one reason it could still be worth developing.
assessment-instructions:: Score out of 100. 100 for any one of: it can make near-human AI trustworthy enough to help with harder alignment work; it reduces harm from current systems; it buys time or catches early warning signs; it gives practice and evidence that inform better methods. 30 for "it's better than nothing" without a reason.
