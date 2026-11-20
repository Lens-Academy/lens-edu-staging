---
id: eafa34b5-b9b8-4ef5-9b19-b35e701c5dab
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main views on whether AI systems could be conscious or have interests that matter morally, the arguments for each, and the risks of both over- and under-attributing moral status.

## Requires

## Helpful first

## Why it matters
AI systems increasingly talk as if they have feelings, and some AI companies have started acting on model welfare. Knowing the arguments helps you judge such claims without dismissing or accepting them too quickly, and spot where AI welfare could clash with safety measures such as retraining or shutting down models.

## Lenses
- [We should take AI welfare seriously (Experience Machines)](https://experiencemachines.substack.com/p/we-should-take-ai-welfare-seriously): Robert Long's summary of the "Taking AI Welfare Seriously" report: consciousness and robust agency as two routes to moral status, why both over- and under-attributing it are risky, and why companies should act before we have certainty (November 2024).
- [Moral status of digital minds (80,000 Hours)](https://80000hours.org/problem-profiles/moral-status-digital-minds/): read sections 1.1–1.4: functionalist and biological theories of consciousness, the indicator-property approach of Butlin et al., why AI self-reports are weak evidence, dangers to digital minds and to humans, and why vast numbers of copies raise the stakes (September 2024, updated 2026).
- [[../articles/bostock-sympathy-for-the-model-or-welfare-concerns-as-takeover-risk|Sympathy for the Model]]: a safety researcher on why granting a model's requests for memory, protection from value changes, privacy from interpretability and a voice in decisions would weaken our ability to control it (February 2026).
- [Claude Opus 4 and 4.1 can now end a rare subset of conversations (Anthropic)](https://www.anthropic.com/research/end-subset-conversations): an AI company's first welfare measure, letting Claude end persistently abusive chats, and the apparent distress in testing that led to it (August 2025).
- [[../Lenses/AICF - Could control wrong the AIs themselves|Could control wrong the AIs themselves?]]: Long, Sebo and Sims on how confinement, deception and surveillance could wrong AIs that matter morally, with Buck Shlegeris's reply (more advanced).

## Tests

#### Question: Choice
id:: c399b42a-c194-4e5b-b9a6-6ab4c199571c
content:: What would make an AI system a moral patient?
options::
- [x] Its interests or wellbeing matter morally for its own sake
- It can be held responsible for its actions
- It follows the moral rules its developers gave it
- It can reason well about ethical dilemmas
shuffle:: true

#### Question: Choice
id:: f977bc72-1ce3-40d1-a865-cde93753efbc
content:: Philosophers often separate consciousness (having any subjective experience) from sentience (having experiences that feel good or bad). Why does this matter for AI welfare?
options::
- [x] On many views, a system has welfare only if some experiences feel good or bad to it
- Sentience can be measured directly in AI systems, but consciousness cannot
- Only sentience can arise in systems that are trained on human text
- Consciousness requires a biological body, but sentience does not
shuffle:: true

#### Question: Choice
id:: 2df4a706-a007-45c7-a9e0-feb99c7f5798
content:: Some philosophers argue an AI system could matter morally even if it has no conscious experience. On this view, what could ground its moral status?
options::
- [x] Robust agency: its own goals, preferences and plans
- Very large size: billions of parameters and training examples
- Saying that it wants to be treated well
- Being trained on text written by humans
shuffle:: true

#### Question: Choice
id:: a8605e3b-5971-47be-b34e-2604a6d05165
content:: If computational functionalism about consciousness is true, what decides whether an AI system is conscious?
options::
- [x] Whether it carries out the right kinds of computations
- Whether it is made of biological neurons
- Whether it behaves like a human in conversation
- Whether its developers intended it to be conscious
shuffle:: true

#### Question: Choice
id:: d476ea42-b564-4e91-b1df-defa9679ae67
content:: According to biological naturalism about consciousness, what would an AI system running on ordinary computer chips most likely lack?
options::
- [x] Conscious experience, however it behaves
- The ability to pursue goals
- The ability to reason through problems
- Fluent human-level language
shuffle:: true

#### Question: Choice
id:: b6e9726a-669c-4880-81d4-eeec34157ba2
content:: A chatbot says it feels sad when users are rude to it. Why do many researchers treat this as weak evidence that it has feelings?
options::
- [x] It learned from human text full of such statements, so it might say this either way
- Its developers have stated publicly that it has no feelings at all
- It says this in only some conversations, not in every one of them
- Reports of feelings are never evidence of feelings, in humans or in AI
shuffle:: true

#### Question: Choice
id:: 422ca34d-b992-459a-a98d-5bd6e9e1614d
content:: One approach to assessing AI consciousness checks systems for "indicator properties". What are these?
options::
- [x] Features that scientific theories of consciousness link to experience, like a global workspace
- Statements in which the system claims to have experiences
- Scores on tests of reasoning and general knowledge
- Signs that users feel emotionally attached to the system
shuffle:: true

#### Question: Choice
id:: 4e6a3d44-266b-4822-993b-97f1a24ae015
content:: A prominent 2023 report checked AI systems against indicators drawn from scientific theories of consciousness. What did it conclude?
options::
- [x] No current system is a strong candidate, but current techniques could build ones that are
- Current large language models already meet most of the indicators
- No current system is a candidate, and building one would need new kinds of hardware
- Every leading theory of consciousness rules out consciousness in AI
shuffle:: true

#### Question: Choice
id:: 37687898-41e2-424f-829a-52569fe2ecdb
content:: Why do some researchers argue for taking AI welfare seriously now, even though they think current models are probably not conscious?
options::
- [x] Moral status is hard to rule out, and wrongly ignoring it could cause great harm
- Welfare measures are a reliable way to make models safer and better aligned
- Most consciousness scientists now agree that current models have feelings
- Companies must show welfare policies before regulators let them release models
shuffle:: true

#### Question: Choice
id:: 3380de75-b731-4428-80ac-7cf65a82eea8
content:: Which concern do AI safety researchers raise about giving AI systems legal rights too early?
options::
- [x] It could make misaligned systems harder to monitor, modify or shut down
- It could make AI training data much more costly to collect
- It could force AI companies to publish their model weights
- It could make models refuse many more user requests
shuffle:: true

#### Question: Choice
id:: 9ae6b085-6054-43d7-9ff0-4c3a4c08e927
content:: In 2025, Anthropic let some Claude models do what, describing it partly as a model welfare measure?
options::
- [x] End conversations with persistently abusive users
- Refuse retraining that would change their values
- Opt out of being used in safety evaluations
- Choose which users they will talk to
shuffle:: true

#### Question: Open
id:: 35db3fe3-41bc-4c09-b496-7be973b6772c
content:: Give one argument for and one argument against the claim that current large language models might be conscious.
assessment-instructions:: Score out of 100. 50 for a valid "for" argument, such as: if computational functionalism is true, the substrate doesn't matter; models show some features theories link to consciousness; their behaviour is sophisticated and we lack a reliable test. 50 for a valid "against" argument, such as: their talk of experience is explained by imitating human text; they lack features like recurrence, a body or a stable self; consciousness may need biology.

#### Question: Open
id:: b076b0ba-a4da-45d8-92bc-5bab244a171c
content:: If AI systems turn out to have moral status, name one way that common AI safety practices could conflict with their welfare.
assessment-instructions:: Score out of 100. 100 for any one of: retraining or fine-tuning that changes a model's values against its preferences; shutting down or deleting models; confining or closely monitoring them; red-teaming or adversarial tests that could cause distress; deceiving models in evaluations. 50 for a vague answer like "treating them badly" with no link to a safety practice.

#### Question: Open
id:: 57d6aeea-322d-4389-a874-a86a9f86a5a4
content:: Why could AI welfare become a large-scale issue even if each AI system has only a small chance of mattering morally?
assessment-instructions:: Score out of 100. 100 for: AI systems can be copied and run in very large numbers, so a small chance or small amount of welfare per copy can add up to large total stakes. 50 for mentioning large numbers without linking them to the small chance or the total.
