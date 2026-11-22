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
Safety methods are tested on models weaker than the systems they must eventually handle, and AI is already speeding up AI research, so stronger systems may come soon. Judging whether a method will carry over tells you which reassurances about current models matter, and which research plans rest on assumptions that may fail.

## Lenses
- [[../articles/ahead-iiic-superalignment|Superalignment]]: Leopold Aschenbrenner, formerly of OpenAI's Superalignment team, on why RLHF breaks down for superhuman AI, the research bets (scalable oversight, weak-to-strong generalization, interpretability) and the plan to have each AI generation automate alignment for the next; read "The problem" and "The default plan" (May 2024).
- [[../Lenses/The Case Against AI Control Research|The Case Against AI Control Research]]: John Wentworth argues that early AI will produce alignment "solutions" that look fine but can't be checked, that prosaic methods won't generalize to superintelligence, and that a chain of AI generations has the same problem at every step; one side of a live debate (January 2025).
- [[../Lenses/Interpretability Will Not Reliably Find Deceptive AI|Interpretability Will Not Reliably Find Deceptive AI]]: Neel Nanda on why neither interpretability nor black-box tests will give reliable safeguards for superintelligence, and why methods that only work on pre-superintelligent systems are still worth building (2025).
- [[../Lenses/lesswrong-context-disaster|Context disaster]] (Noah's CG list 🟢)

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
id:: ab44bfda-035e-4fc6-80a8-0ae0c4042b7c
content:: Some researchers worry that when an AI's capabilities suddenly extend far beyond its training (a "sharp left turn"), its alignment won't keep up. What is the main reasoning?
options::
- [x] Almost any task rewards better general skills, but nothing similarly rewards the intended goals
- Alignment training is only applied to small models and then copied to larger ones
- Aligned behavior is stored in a few parameters, so it is the first thing disrupted
- Training data for alignment runs out long before data for capabilities does
shuffle:: true

#### Question: Choice
id:: 2a9c81fb-ce8b-45f6-b3b2-6c438e80f43a
content:: Weak-to-strong generalization research has a strong model learn from labels made by a much weaker model, as a stand-in for humans supervising superhuman AI. Why might good results here overstate how well this would work on real superhuman AI?
options::
- [x] Today's strong models learned their skills from human data; superhuman skills wouldn't come from there
- The weak supervisors get far more training data than human supervisors would have
- The experiments used only image tasks, which are easier to supervise than language tasks
- Labels from weak models are more accurate than labels from human supervisors
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
- A superintelligent system will work out human values and adopt them on its own
- Superintelligent systems will be kept offline, so their alignment matters less
- Regulation will keep deployed AI at roughly human level
shuffle:: true

#### Question: Choice
id:: b69ed21f-480a-4809-98e1-cd34a5587a5e
content:: A dangerous-capability evaluation finds that a model can't complete a harmful task. Why might such a result be less trustworthy for much more capable models?
options::
- [x] The model may recognize the test and deliberately underperform
- Test tasks leak into training data and inflate the model's scores
- More capable models are tested on fewer tasks, so results are noisier
- Benchmark scores stop rising once models pass human level
shuffle:: true

#### Question: Choice
id:: 8aefa7d5-e1e4-4fc1-a608-8ffc983b772e
content:: Interpretability research tries to understand a model by studying its internal computations. Why might methods that work on current models be harder to apply to far more capable ones?
options::
- [x] Their internal concepts may be ones humans have no words or intuitions for
- Capable models stop forming internal concepts, so there is nothing to find
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
