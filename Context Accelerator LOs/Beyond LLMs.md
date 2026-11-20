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
Many safety plans, forecasts and policies are built around how today's LLMs work. If a different kind of AI replaces LLMs as the leading design, some of them could stop working while others still hold. Knowing which is which helps you judge how robust a plan is, rather than betting everything on one technology.

## Lenses
- [[../Lenses/byrnes-foom-doom-1-brain-in-a-box-in-a-basement|Foom & Doom 1: Brain in a Box in a Basement]]: a leading brain-like AGI researcher argues that a far more compute-efficient paradigm will replace LLMs, and why that would undercut chip-based governance, pre-release testing and LLM-based forecasts; one side of a live debate. Read §1.3, §1.5–1.7.1 and §1.8.6 (June 2025).
- [[../Lenses/byrnes-why-we-should-expect-ruthless-sociopath-asi|Why We Should Expect Ruthless Sociopath ASI]]: why AI that learns by imitating human text may pick up human-like behaviour, but AI that learns by trial and error against a reward signal is ruthless by default, and why designing safe rewards is unsolved (February 2026).
- [AI doom from an LLM-plateau-ist perspective (LessWrong)](https://www.lesswrong.com/posts/KJRBb43nDxk6mwLcR/ai-doom-from-an-llm-plateau-ist-perspective): a short FAQ on which worries about AI risk, timelines and a training pause still hold if LLMs stall and other designs take over (April 2023, updated June 2026).
- [Chain of Thought Monitorability: A New and Fragile Opportunity for AI Safety (arXiv)](https://arxiv.org/abs/2507.11473): researchers from many labs on why reading a model's written reasoning helps safety, and how new designs that reason in internal numbers could take that away. See "Novel architectures" in §2 and the architecture question in §3 (July 2025) (more advanced).

## Tests

#### Question: Choice
id:: 4e771bfd-c7f5-43bc-8c56-92bea6091e88
content:: Children learn language from many thousands of times less text than LLMs are trained on. Why do some people see this as a sign that future AI might not be built mainly from LLMs?
options::
- [x] It shows a far more data-efficient way to learn exists, which a different AI design might copy
- It shows LLMs have already read all the text there is, so they cannot improve further
- It shows that AI trained on less text would automatically be safer
- It shows children's brains run on more computing power than any AI system
shuffle:: true

#### Question: Choice
id:: 2eab6afb-2171-4357-a39c-5105cbc06aeb
content:: Suppose future AI learned like a human brain, mainly by trial and error guided by built-in reward signals. What would be a central safety challenge?
options::
- [x] Its goals would grow out of reward signals its designers wrote, and these are hard to design so the goals turn out safe
- Its goals would simply copy the values of the people whose writing it was trained on
- It could never become more capable than the humans who designed it
- It would be safe by default, because human brains learn in the same way
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
id:: 0eeb33af-7ec8-4222-b9a6-c6f411a37288
content:: Some people hope that because LLMs learn from huge amounts of human writing, they pick up human concepts and values. Why might this hope apply less to an AI that learned mainly by trial and error in an environment?
options::
- [x] Its concepts and goals would be shaped mainly by what earned reward in its environment, not by human writing
- It would be unable to understand any human language
- Learning by trial and error always produces hostile goals
- It would learn too slowly ever to become highly capable
shuffle:: true

#### Question: Choice
id:: d011cbfd-ea3d-4b5a-9acf-7125b7e5b7e9
content:: As of November 2026, leading AI systems are pretrained on text, then given heavy reinforcement learning, tools and image inputs. What does this suggest about the question of whether AI will move beyond LLMs?
options::
- [x] The change could be gradual, with no clear point where systems stop being LLMs
- A move beyond LLMs could only happen as a sudden switch to an unrelated design
- Safety findings about pure text-prediction models carry over to these systems unchanged
- A new kind of AI would have to start by dropping pretraining
shuffle:: true

#### Question: Choice
id:: ad11b854-7304-4d7c-967c-234cac973ce9
content:: Which of these is the best historical reason to doubt that LLMs are the final form of AI?
options::
- [x] The leading approach in AI has changed several times in past decades
- Every past AI approach was abandoned within five years of being invented
- Neural networks were tried and failed in the past, so they will fail again
- Past waves of AI progress always ended because computing became more expensive
shuffle:: true

#### Question: Choice
id:: 27475967-9bef-405b-820a-5dea017abe7d
content:: Some forecasts of when AI will match human abilities extend trends in LLMs, such as how capability grows with training compute. If a far more compute-efficient way to build AI were found, what would that most likely mean for these forecasts?
options::
- [x] Advanced AI could arrive earlier than the trends suggest
- Advanced AI would arrive later, because the new method would need years of new hardware
- The forecasts would be unaffected, because they track computing power rather than methods
- The forecast dates would hold, but the systems would be less capable than expected
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
