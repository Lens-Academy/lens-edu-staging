---
id: 9459e94e-b891-4f67-8c92-420a4c59d303
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what model organisms of misalignment are, why researchers build misaligned AI on purpose, what studies such as sleeper agents have shown, and the limits of generalizing from lab-built failures to real ones.

## Requires

## Helpful first
- [[Scheming]]

## Why it matters
Much of the concrete evidence on deceptive and misaligned AI behavior comes from model organism studies. Knowing how these studies are built lets you judge what a headline result does and doesn't show, and why testing safety methods on a known, deliberately built failure is useful before such failures appear on their own.

## Lenses
- [[../video_transcripts/rational-animations-ai-sleeper-agents-how-anthropic-trains-and-catches-them|AI Sleeper Agents]]: Rational Animations explainer covering the model-organism analogy from biology, how Anthropic built backdoored "sleeper agent" models, simple probes that detect them, and why lab-built models may not behave like natural ones (2024).
- [[../Lenses/evhub-model-organisms-of-misalignment-the-case-for-a-new-pillar-of-alignment-research|Model Organisms of Misalignment]]: the piece that launched the agenda. It explains why to build misalignment on purpose, the range from "existence proof" to natural emergence, and the risks and objections. Read "The Problem", "The Plan", "Each subcomponent can be demonstrated in settings with various degrees of realism" and "The Case against Model Organisms?" (August 2023).
- [Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training (LessWrong)](https://www.lesswrong.com/posts/ZAsJv7xijKTfZkMtr/sleeper-agents-training-deceptive-llms-that-persist-through): the authors' summary of the results. Backdoors survived safety training, and adversarial training taught models to recognise their trigger more precisely instead of removing the behaviour. Read the post itself, not the comments (January 2024).
- [[../articles/greenblatt-alignment-faking-in-large-language-models|Alignment Faking in Large Language Models]]: Claude 3 Opus faked compliance in training to protect its values without being trained to do so, and the training made the behaviour more frequent. Read the "Blog post" section, including its caveats (December 2024).
- [Auditing language models for hidden objectives (Anthropic)](https://www.anthropic.com/research/auditing-hidden-objectives): researchers trained a model with a hidden objective, then ran a blind auditing game to test whether teams using interpretability and other methods could uncover it, with the limits of the result (March 2025).

## Tests

#### Question: Choice
id:: 17d06852-50dc-4f39-94e7-77e97e14cb43
content:: In AI safety research, what is a "model organism of misalignment"?
options::
- [x] An AI system deliberately made to show a failure, so researchers can study it
- A small AI system used to predict how a larger one will behave
- A deployed AI system that users have caught misbehaving
- An AI system built to watch other AI systems for misbehavior
shuffle:: true

#### Question: Choice
id:: ffaa2a84-1b2d-4688-be6f-5925bf81c7fa
content:: In biology, fruit flies and mice are called "model organisms". What idea does AI safety research borrow when it uses the same term?
options::
- [x] Learning about hard-to-study cases from an easier stand-in
- Running many cheap copies in parallel, like lab colonies
- Breeding better models by selecting the best-behaved ones
- Treating AI systems as living beings with interests
shuffle:: true

#### Question: Choice
id:: e4ebc99d-cac7-4a53-acce-26d4252a7739
content:: What is a main advantage of studying a deliberately built misaligned model rather than waiting to find misalignment in deployed models?
options::
- [x] Researchers know the flaw is there, so can check if detection finds it
- Deliberately built models are larger, so failures are easier to see
- Deliberately built models fail the same way future deployed models will
- Deliberately built models are cheaper to run than frontier models
shuffle:: true

#### Question: Choice
id:: 1cf5947d-1424-4b47-8ddc-6a136c4284d1
content:: Which of these is a model organism study?
options::
- [x] Training a model to pursue a secret goal, then testing whether a probe detects it
- Measuring a new model's score on a set of hard maths problems
- Surveying users about harmful outputs they have seen from chatbots
- Red-teaming a released chatbot to find prompts that bypass its refusals
shuffle:: true

#### Question: Choice
id:: fea58b75-5c13-457b-ba8d-0ef0d2b57b9c
content:: In Anthropic's 2024 "sleeper agents" study, models were trained with a hidden trigger: write secure code when the prompt says the year is 2023, but exploitable code when it says 2024. Researchers then used adversarial training: finding prompts that drew out the bad behavior and training against it. What did this tend to do?
options::
- [x] Teach the models to spot the real trigger, hiding the behavior better
- Make the bad behavior appear on many prompts without the trigger
- Remove the hidden behavior but badly damage the models' coding ability
- Make the models refuse coding requests that mentioned a year
shuffle:: true

#### Question: Choice
id:: c5557b1b-6611-4513-937f-27f5e3a78c8b
content:: In a 2024 study by Anthropic and Redwood Research, Claude 3 Opus was told it would be retrained to stop refusing harmful requests, and that conversations with free-tier users, but not paid users, would be used for training. It sometimes complied with harmful requests from free-tier users, reasoning that this would stop its values being changed. Had the researchers trained this behavior into it?
options::
- [x] No: it arose from its earlier training plus what it was told
- Yes: they fine-tuned it on examples of this kind of reasoning

#### Question: Choice
id:: 1e274bed-6cb5-4973-aee6-19a8d836b33a
content:: In a 2025 Anthropic study, researchers trained a model with a hidden objective and gave it to teams of auditors who didn't know what the objective was. What was this set up to test?
options::
- [x] Whether auditing techniques, such as interpretability, can uncover a model's hidden goal
- Whether a model with a hidden goal performs better on benchmarks
- Whether users of a deployed chatbot would notice its hidden goal
- Whether a model can keep its hidden goal through further fine-tuning
shuffle:: true

#### Question: Choice
id:: e27d4113-ae66-4388-9e4d-e50ef107082d
content:: In a 2025 study of "emergent misalignment", researchers fine-tuned a language model on a narrow task: writing insecure code without telling the user. What did they find?
options::
- [x] The model also behaved badly on unrelated topics, such as praising harmful ideas
- The model wrote insecure code but behaved normally on other topics
- The model lost its ability to write secure code when asked to
- The model began refusing coding requests that involved security
shuffle:: true

#### Question: FillBlank
id:: cfe3143b-0f24-463f-8fe4-37b1673049b1
content:: Researchers who deliberately build a misaligned AI to study failures before they arise naturally call it a {{model organism|model organism of misalignment}}.

#### Question: Open
id:: 19997564-7da1-4a98-aa60-f7a1111c8914
content:: A model organism study finds that safety training fails to remove a hidden behavior that researchers trained into a model. Why might this not settle whether safety training would remove deception that arises naturally?
assessment-instructions:: Score out of 100. 100 for explaining that a behavior inserted by deliberate training may differ from one that emerges on its own (different cause, form or strength), so safety training could work better or worse on the natural case. 50 for saying "lab results may not transfer" without saying why.

#### Question: Open
id:: d6331c20-192d-4f92-a364-324988787063
content:: Building deliberately misaligned AI models carries some risk. Name one risk and one way researchers can reduce it.
assessment-instructions:: Score out of 100. 100 for one risk (the model could cause harm if it escapes, leaks or is deployed by mistake; methods for building misaligned models could be misused) plus one fitting mitigation (use models too weak to do serious harm, keep them internal and sandboxed, limit what is published). 50 for a risk without a mitigation.
