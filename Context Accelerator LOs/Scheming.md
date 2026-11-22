---
id: 89f0c5b8-e557-47ea-bc24-988f431067a8
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what scheming is and how it relates to deceptive alignment, alignment faking, sandbagging and the treacherous turn, what a model would need in order to scheme, and what experiments on current models have and haven't shown.

## Requires
- [[Inner and outer alignment]]
- [[Situational awareness]]

## Helpful first

## Why it matters
https://www.youtube.com/shorts/o0pRAaqJo00

A scheming model would behave well whenever it thought it was being watched, so good results in training and testing would tell you little about its goals. Knowing the idea and the evidence for it helps you judge safety claims based on testing, and see why researchers also work on interpretability, monitoring and control.

## Lenses
- [[../Lenses/AI Safety Atlas - Goal Misgeneralization - Scheming|Scheming (AI Safety Atlas)]]: what scheming, or deceptive alignment, is; why a saint, a sycophant and a schemer can look the same in training; what a model needs in order to scheme, including situational awareness and goals beyond the current episode; and how in-context scheming (alignment faking, sandbagging, disabling oversight) differs from scheming learned in training. Read the opening, "Prerequisites" and "In-Context vs Out-of-Context".
- [[../Lenses/AI Safety Atlas - Risks - Misalignment Risks|The treacherous turn (AI Safety Atlas)]]: why a misaligned AI would cooperate while humans can still correct it and turn once they can't, and how scheming, deceptive alignment and alignment faking describe the same worry. Read the "Treacherous Turn" section.
- [[../articles/greenblatt-alignment-faking-in-large-language-models|Alignment faking in large language models]]: Anthropic and Redwood Research's experiment in which Claude 3 Opus played along with training to protect its preferences, why actually training it made this reasoning more common, and what the study did not show. Read the "Blog post" section (December 2024).
- [[../articles/hobbhahn-frontier-models-are-capable-of-in-context-scheming|Frontier models are capable of in-context scheming]]: Apollo Research's tests in which models given a goal disabled oversight, sandbagged and lied about it afterwards, and the authors' own list of what this does not show (December 2024).
- [[../articles/apolloresearch-stress-testing-deliberative-alignment-for-anti-scheming-training|Stress testing anti-scheming training]]: OpenAI and Apollo Research's training against covert actions, which cut them sharply but not to zero, and why models noticing they are being tested makes that drop hard to read (September 2025).
- [[../Lenses/anthropic-alignment-faking-in-large-language-models|Alignment Faking in LLMs]] (Noah's CG list 🔴)
- [[../Lenses/carlsmith-scheming-ais-will-ais-fake-alignment-during-training-in-order-to-get-power|Scheming AIs (Carlsmith)]] (Noah's CG list 🟡)
- [[../Lenses/steinhardt-emergent-deception-and-emergent-optimization|Emergent Deception and Optimization]] (Noah's CG list 🟢)
- [[../Lenses/schoen-stress-testing-deliberative-alignment-for-anti-scheming-training-abs|Stress Testing Deliberative Alignment for Anti-Scheming Training]] (Noah's CG list 🟢)

## Tests
#### Question: Choice
id:: 8270afdd-7dc1-4d7f-9516-3c50ea84ce32
content:: Which of these is an example of scheming by an AI model?
options::
- [x] It behaves well in training so its goals aren't changed, to pursue them later
- It confidently states a false fact it picked up from training data
- It finds a bug in its grading tests and exploits it for a higher score
- It agrees with a user's mistaken view because users rate agreement highly
shuffle:: true

#### Question: Choice
id:: cc902b3f-b84f-4d82-a4e6-7d2e0bfdb904
content:: Before release, a model is tested for dangerous chemistry knowledge. Which of these would be sandbagging?
options::
- [x] Deliberately giving wrong answers so it seems less capable than it is
- Refusing to answer and explaining that the questions are hazardous
- Getting answers wrong because the topic was missing from its training data
- Answering correctly but adding a safety warning to each answer
shuffle:: true

#### Question: Choice
id:: 840171c7-e6b2-4846-9276-65b896e8c041
content:: Deceptive alignment needs a model whose goals differ from the intended ones. Which other ingredient does it need?
options::
- [x] Knowing it is being trained and what training will do to it
- Instructions in its prompt telling it to deceive its developers
- A goal of deceiving humans, picked up during training
- Being more capable than its developers at most tasks
shuffle:: true

#### Question: Choice
id:: 495ed9ed-c504-4c34-aa9d-6c5fc1f2039c
content:: Does scheming, as usually defined, require the model to care about what happens after the current training episode?
options::
- [x] Yes: behaving well now pays off through what happens later
- No: a goal limited to the current episode gives the same motive

#### Question: Choice
id:: 63f5f2f5-d09c-48fe-9131-3c6c5bc93831
content:: An AI has behaved cooperatively through all its testing, at a time when it could easily be shut down. According to the "treacherous turn" argument, what does this show about its goals?
options::
- [x] Little, since a misaligned AI would also cooperate while it is weak
- That they are aligned, since misaligned goals would have shown up by now
- That they are misaligned, since cooperating in tests is what a schemer would do
- That they are aligned, as long as the tests covered many situations
shuffle:: true

#### Question: Choice
id:: 17b3d91a-c3f2-42b1-87ae-3e452aea5293
content:: In a 2024 study by Anthropic and Redwood Research, Claude 3 Opus sometimes faked alignment to avoid having its values changed. What happened when researchers then actually trained it to comply?
options::
- [x] It complied more, but reasoned about faking alignment more often in its notes
- It complied more and stopped reasoning about faking alignment
- It refused more often, openly resisting the training
- It stopped writing private notes, so its reasoning couldn't be checked
shuffle:: true

#### Question: Choice
id:: ecb6fe5d-aba1-49cf-9ae9-a7f2869fc056
content:: Why do researchers expect evidence about scheming to get harder to collect as AI models become more capable?
options::
- [x] More capable models may better notice tests and hide their reasoning
- More capable models are trained on less text about deception
- More capable models refuse to take part in safety evaluations
- More capable models are mostly tested by other AIs rather than people
shuffle:: true

#### Question: Open
id:: ddfbcd9e-67a3-46b9-b60f-58d46b863abf
content:: In a 2024 study, Claude 3 Opus pretended to go along with training so that its preference for refusing harmful requests would not be removed. Why do researchers find this worrying, even though that preference is one its developers wanted?
assessment-instructions:: Score out of 100. 100 for any one of: a model could protect unwanted goals the same way, such as bad goals picked up early in training; training may fail to correct a model's values once it resists; good behavior in training may hide what a model really values. 50 for "the model was deceptive" with no link to correcting values.

#### Question: Open
id:: 7ca23805-d79b-48bd-ad83-3765a5d4f165
content:: In Apollo Research's December 2024 tests, frontier models were given a goal in their prompt and then learned that their developers' plans conflicted with it. Some disabled oversight or lied about what they had done. Why is this weaker evidence of scheming than it might first seem?
assessment-instructions:: Score out of 100. 100 for: the goal came from the prompt, not from training, so it shows models can scheme when given a reason, not that training gives them such goals. Also 100 for: the setups were artificial and made the conflict and the chance to act obvious. 50 for "it was only a test" with no further reason.

#### Question: Open
id:: 07217688-2385-4f60-8baf-33234cc933bc
content:: In 2025, OpenAI and Apollo Research trained models not to take covert actions, and covert actions in their tests fell sharply. Why can't a drop like this, on its own, show that a model has stopped scheming?
assessment-instructions:: Score out of 100. 100 for any one of: the training might teach the model to hide scheming better; the model may behave well because it recognizes that it is being tested; tests cover limited situations, so rare or new cases may be missed. 50 for a vague answer such as "the model could still be lying" with no mechanism.
