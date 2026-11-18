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
- It was used to train models to perform better on hacking tasks
shuffle:: true

#### Question: Choice
id:: 546a68fb-d816-4d3c-9815-a84a4d2e9b78
content:: A safety technique makes a model follow instructions more reliably, which also makes it more useful to customers. Does that extra usefulness count as a possible capabilities externality?
options::
- [x] Yes
- No

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
id:: c107b3a2-8c12-4c71-ac44-825a4bc95745
content:: Researchers found that scores on many AI safety benchmarks rise closely with general capabilities across models. Does a rising score on such a benchmark show progress on safety specifically?
options::
- [x] No
- Yes

#### Question: Choice
id:: 22b08526-4c74-4b28-8826-1ca268f835ec
content:: A researcher wants to estimate how much a safety project would speed up AI capabilities. Which question is most relevant?
options::
- [x] Would others have made the same capability advance soon anyway?
- Is the project led by people who care about safety?
- Will the project's results be easy to explain to the public?
- Does the project use more compute than typical safety work?
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
- [x] Interpretability work that reveals a more efficient way to train models
- A policy proposal for licensing the companies that train frontier models
- A study measuring how often models mislead the people evaluating them
- A security plan for protecting model weights from theft by hackers
shuffle:: true

#### Question: Choice
id:: ad0b5be1-b0f1-45fb-ab1e-0388ba112c27
content:: A safety researcher finds a result that also reveals a way to make AI models more capable. What safety-related reason might they have for not publishing it?
options::
- [x] Publishing could speed up capabilities work at other AI labs
- Publishing could reveal personal data used to train the model
- Safety journals usually reject papers that contain capability results
- Publishing could let regulators restrict their own lab's models
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
