---
id: 163c82c7-4838-4aa8-9650-3dc25c845685
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why future AI might not be built mainly from large language models, and say which AI-risk arguments and safety approaches depend on features of LLMs and which would still apply to other designs.

## Requires
- [[Large language models]]

## Helpful first

## Why it matters
Many safety plans, forecasts and policies are built around how today's LLMs work. If a different kind of AI takes over, some of them could stop working while others still hold. Knowing which is which helps you judge how robust a plan is, rather than betting everything on one technology.

## Lenses

## Tests

#### Question: Choice
id:: 81f95d41-9827-402a-b360-3fdaf2f08d2b
content:: A common argument that LLMs may not be the final form of AI points to how efficiently humans learn. What comparison does it make?
options::
- [x] Children learn language from far less text than LLMs are trained on
- LLMs need less training text than children but more energy
- Children and LLMs see similar amounts of text, but LLMs learn it faster
- Children need more text than LLMs but remember it for longer
shuffle:: true

#### Question: Choice
id:: c1fe1924-35d7-485f-84b5-347b5572f581
content:: Steven Byrnes studies "brain-like AGI": AI built on learning methods like those in the human brain. What is his main safety concern about such systems?
options::
- [x] Their goals would come from reward signals that are hard to design safely
- They would copy the values of whoever wrote their training text
- They would be too slow to run on today's computers
- They could not learn anything beyond what humans already know
shuffle:: true

#### Question: Choice
id:: 87760a1a-be93-40bd-b0ba-a64175b2b1c7
content:: Suppose a new method made training a highly capable AI system 1,000 times cheaper in computing power. Which AI-risk policy idea would this weaken most directly?
options::
- [x] Tracking and limiting who has large numbers of AI chips
- Requiring labs to report serious safety incidents
- Testing models for dangerous capabilities before release
- Holding developers legally liable for harms their models cause
shuffle:: true

#### Question: Choice
id:: c168a926-52d7-4d48-9205-e533239d6c3b
content:: Some safety plans rely on reading an LLM's chain of thought, the step-by-step reasoning it writes out. Why might this stop working if future AI is built on a different design?
options::
- [x] Its reasoning might happen in internal numbers rather than written words
- Its reasoning might be written in a language other than English
- It might have no need to reason before it acts
- Its reasoning would be too long to store and review
shuffle:: true

#### Question: Choice
id:: 5c258966-f862-420c-b4bf-51349a73c007
content:: Some people hope that because LLMs learn from huge amounts of human writing, they pick up human concepts and values. Would this reason for hope apply less strongly to an AI that learned mainly by trial and error in an environment?
options::
- [x] Yes
- No

#### Question: Choice
id:: d011cbfd-ea3d-4b5a-9acf-7125b7e5b7e9
content:: As of November 2026, leading AI systems are pretrained on text, then given heavy reinforcement learning, tools and image inputs. What does this suggest about the question of whether AI will move beyond LLMs?
options::
- [x] The change could be gradual, with no clear point where systems stop being LLMs
- These systems no longer contain any language model at all
- Adding reinforcement learning means AI-risk arguments no longer apply to them
- A new kind of AI would have to start by dropping pretraining
shuffle:: true

#### Question: Choice
id:: ad11b854-7304-4d7c-967c-234cac973ce9
content:: Which of these is the best historical reason to doubt that LLMs are the final form of AI?
options::
- [x] The leading approach in AI has changed several times in past decades
- LLMs have not improved in any measurable way since 2023
- LLMs cannot learn from images or sound
- LLMs have become more expensive to run every year
shuffle:: true

#### Question: Choice
id:: 27475967-9bef-405b-820a-5dea017abe7d
content:: Some forecasts of when AI will match human abilities extend trends in LLMs, such as how capability grows with training compute. If a far more compute-efficient way to build AI were found, what would that most likely mean for these forecasts?
options::
- [x] Advanced AI could arrive earlier than the trends suggest
- Advanced AI would arrive later than the trends suggest
- The forecasts would become more accurate than before
- The forecasts would be unaffected, since they measure compute
shuffle:: true

#### Question: Open
id:: 60a2fec2-abf2-4086-9052-e373457d9416
content:: Some people worry that if a far more compute-efficient way to build AI were found, AI capabilities could jump suddenly rather than grow step by step. Explain why.
assessment-instructions:: Score out of 100. 100 for saying that a large stock of AI chips already exists, so the new method could at once be used to train or run much more capable systems, with no slow build-up of hardware. 50 for saying only that AI would get cheaper or better, without the point about existing hardware.

#### Question: Open
id:: c1da335f-9be4-4e1f-b250-9f3fde0acafc
content:: Name one AI-risk argument that would still apply if future AI were not built mainly from LLMs, and say briefly why.
assessment-instructions:: Score out of 100. 100 for any one of these with a brief reason that does not depend on LLMs: instrumental convergence (many goals favour gaining resources and avoiding shutdown); the orthogonality thesis; training signals that only roughly match what we want, giving wrong goals; race dynamics between developers; power concentration. 50 for a correct argument with no reason.

#### Question: Open
id:: ed2610e2-c608-4740-8e75-a35abaf64a1a
content:: An LLM's training usually ends before it is released. Why might an AI that keeps learning from its own experience after release, as a brain does, be harder to check for safety before release?
assessment-instructions:: Score out of 100. 100 for saying that its abilities or goals could keep changing after testing, so tests before release may not show how it will behave later. 50 for a vague answer such as "it is less predictable" without linking this to learning after the tests.
