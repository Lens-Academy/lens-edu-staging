---
id: 74b80cab-0e5b-4c3e-91d4-9f50634105a5
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how safety research and safety-motivated AI companies can also speed up AI capabilities, and describe the main arguments for and against accepting that cost.

## Requires
- [[Differential technological development]]

## Helpful first
- [[Safety research agendas]]
- [[RLHF]]

## Why it matters
Choosing which safety work to do, fund or join means weighing its benefits against any speedup it gives to capabilities, which can shorten the time left for safety. Without this, you may back projects that mostly feed the race they aim to make safer, or reject useful work over small speedups that would have happened anyway.

## Lenses
- [Thoughts on the impact of RLHF research (LessWrong)](https://www.lesswrong.com/posts/vwu4kegAEZTBtpT6p/thoughts-on-the-impact-of-rlhf-research): Paul Christiano, a main developer of RLHF, weighs whether it was good for safety: the case for, the case against (more useful models, more investment, false confidence), and why he thinks others would have built it anyway (January 2023).
- [[../Lenses/AICF - Ngo - Pragmatism and pessimization|Richard Ngo: Pragmatism and pessimization]]: a former OpenAI and DeepMind researcher argues that safety-branded work on RLHF and scaling helped start the chatbot boom and the race, and that "someone else would do it" and overhang arguments were rationalisations; one side of a live debate. Read the "OpenAI" section (August 2026).
- [[../Lenses/anthropic-core-views-on-ai-safety-when-why-what-and-how|Anthropic's Core Views on AI Safety]]: Anthropic's own case for why safety research needs frontier models, the trade-off it accepts, and why it counts RLHF as safety work. Read "The role of frontier models in empirical safety" and "The three types of AI research at Anthropic" (March 2023).
- [[../articles/oesterheld-a-simple-argument-about-capabilities-externalities-versus-opportunity-costs|Capabilities externalities versus opportunity costs]]: Caspar Oesterheld argues that for a typical safety project the speedup it gives capabilities is smaller than the cost of not doing other safety work, and says when that argument fails (September 2026).
- [The bitter lesson for AI safety research (AI Alignment Forum)](https://www.alignmentforum.org/posts/afiyFjiNyubqvuFHM/the-bitter-lesson-for-ai-safety-research): the authors of the "Safetywashing" paper find that about half of safety benchmarks rise with general capability, and argue for work that makes safety progress separately from capabilities (August 2024).

## Tests

#### Question: Choice
id:: 28934c80-3135-4bbb-aaf5-39f95c725678
content:: What does "capabilities externalities" mean when people discuss AI safety work?
options::
- [x] Ways the work also speeds up progress in what AI systems can do
- Harms that capable AI systems cause to people outside AI companies
- Capability losses a model suffers when safety training is applied
- New skills a model picks up after deployment, without further training
shuffle:: true

#### Question: Choice
id:: 0cb371a4-e0be-4f8d-9f4e-4fbf7e22984c
content:: Reinforcement learning from human feedback (RLHF) was developed partly by safety researchers. Why is it often cited as safety work with capabilities externalities?
options::
- [x] It made chatbots much more useful, drawing more investment into AI
- It let models learn from images and audio as well as text
- It removed the need for large pretraining runs on internet text
- It cut the compute needed to train frontier models many times over
shuffle:: true

#### Question: Choice
id:: 577dd0a3-f2c5-4a2b-bc84-ec38826e96ac
content:: A safety technique also makes AI models more useful. Why do some see this as good news for safety, despite the capabilities externality?
options::
- [x] Companies are more likely to adopt it without being required to
- It shows that safety and capabilities research are the same field
- More useful models are less likely to have dangerous capabilities
- Regulators then stop requiring safety evaluations of those models
shuffle:: true

#### Question: Choice
id:: eb8afb31-ba85-44cc-a19f-b8fde66b369a
content:: Researchers found that scores on many AI safety benchmarks rise closely with general capabilities and training compute. What does this suggest about a project that raises those scores?
options::
- [x] Its gains may be capabilities progress presented as safety progress
- It shows that more capable models will also be the safer ones
- It shows that safety research has no capabilities externalities
- It shows that these benchmarks were written by capabilities teams
shuffle:: true

#### Question: Choice
id:: 7c7a9f45-b0f0-4b2a-afdd-918cccec9604
content:: A safety project leads to a capability advance. Which fact would most reduce how much the project actually sped up AI progress?
options::
- [x] Several other teams were close to finding the same advance
- The researchers involved were motivated mainly by safety
- The advance was first published at a safety workshop
- The project's stated goal was to make models safer
shuffle:: true

#### Question: Choice
id:: 38c063b0-dd64-48b7-a6cb-9d1eea79f5c2
content:: Why do some safety-motivated AI companies, such as Anthropic, argue that they need to build frontier models themselves?
options::
- [x] Safety research on the most capable models needs access to such models
- Frontier models are cheaper to make safe than smaller models
- Governments fund safety research only when it is done on frontier models
- Building frontier models slows down rival companies' progress
shuffle:: true

#### Question: Choice
id:: 93547aa1-bcb9-4981-a8cc-e155097f26a9
content:: Which of these safety projects is most likely to speed up AI capabilities?
options::
- [x] A method that makes models follow complex instructions more reliably
- A policy proposal for licensing the companies that train frontier models
- A study measuring how often models mislead the people evaluating them
- A security plan for protecting model weights from theft by hackers
shuffle:: true

#### Question: Choice
id:: b2b18150-d1be-4219-8301-08a4d8784751
content:: A safety researcher's result would help other safety researchers but also reveals a way to make AI models more capable. Which consideration favours publishing it anyway?
options::
- [x] Others may find the trick soon, and withholding also slows safety work
- Capability tricks that appear in safety papers are rarely used by labs
- Peer review would catch any danger in the trick before labs could use it
- Most AI labs have agreed not to use capability results from safety papers
shuffle:: true

#### Question: Open
id:: 01bf30ca-0e79-4df2-a1ff-25e8b375fbbb
content:: Why do many people worried about AI risk treat speeding up AI capabilities as a cost, even when the speedup comes from safety work?
assessment-instructions:: Score out of 100. Full marks for saying it shortens the time available to solve safety problems, build governance or let society adapt before dangerous systems arrive. Also full marks for saying it intensifies competition, pushing developers to cut safety corners. 50 for "faster AI is more dangerous" without a reason such as less time or more racing.

#### Question: Open
id:: bf8c4706-08bf-4477-8455-07194f80ddf7
content:: Name one way that founding a safety-motivated AI company could speed up AI capabilities, apart from the company's own research results.
assessment-instructions:: Score out of 100. 100 for any one of: adds a competitor at the frontier and intensifies racing; pushes rivals to move faster or release sooner; shows frontier AI is commercially valuable, drawing in investment; adds to hype and funding for AI generally; trains researchers who later do capabilities work elsewhere. 50 for a vague answer such as "it makes AI progress faster" with no mechanism.

#### Question: Open
id:: 112ec19c-a470-456e-9766-f8039ea6793e
content:: Reinforcement learning from human feedback (RLHF) was developed partly by safety researchers and is now widely used to train chatbots. Give one argument that this work was net positive for safety and one that it was net negative.
assessment-instructions:: Score out of 100. 50 for each side. Positive, any of: it gave a practical way to steer models toward intended behavior; similar methods would have been developed soon anyway; it let researchers study alignment on real systems early. Negative, any of: it helped spark the chatbot boom and racing; it brought powerful AI sooner; it rewards outputs that look good, encouraging sycophancy; it may give false confidence that alignment is solved.
