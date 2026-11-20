---
id: 2ae4f952-44fd-4b52-9a66-f1c2be6346d3
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what AGI, human-level AI, transformative AI and superintelligence mean, how definitions of each differ, and why a claim that a system "is AGI" or "is superintelligent" depends on the definition used.

## Requires

## Helpful first
- [[Intelligence as optimization]]

## Why it matters
Forecasts, company announcements and laws use these terms in very different senses. Knowing which sense is meant lets you tell whether two forecasts disagree about the future or only about a word, and stops you mistaking a label for a capability.

## Lenses
- [[../Lenses/AI Safety Atlas - Capabilities - Defining and Measuring AGI|Defining and Measuring AGI]]: why "human-level at what?" has no single answer, a survey of rival definitions of intelligence, and AGI, transformative AI and superintelligence placed on two axes, capability and generality (2026).
- [What are the differences between AGI, transformative AI, and superintelligence? (AISafety.info)](https://aisafety.info/questions/5864/What-are-the-differences-between-AGI-transformative-AI-and-superintelligence): a short glossary of the main terms and their variants, including why "human-level AI" fits AI with uneven skills badly (updated November 2026).
- [The term "AGI" is almost useless at this point (Helen Toner, Rising Tide)](https://helentoner.substack.com/p/the-term-agi-is-almost-useless-at): how today's systems meet some definitions of AGI and miss others, so claims that AGI is "here" or "a decade away" can both be true, and what terms to use instead (April 2026).
- [Superintelligence 5: Forms of Superintelligence (Katja Grace, LessWrong)](https://www.lesswrong.com/posts/semvkn56ZFcXBNc2d/superintelligence-5-forms-of-superintelligence): a summary of Bostrom's speed, collective and quality superintelligence, and of the edge digital minds have over human ones, like speed, copying and shared memories; read the Summary and Notes (October 2014).

## Tests

#### Question: Choice
id:: 544e407f-42d5-4b44-aa56-bc865558fa70
content:: Which of these is a superintelligence in Nick Bostrom's sense of the term?
options::
- [x] A system far better than top humans at nearly every mental task
- A chess engine far stronger than the world chess champion
- A search system that recalls far more facts than people do
- A robot that is stronger and faster than human athletes
shuffle:: true

#### Question: Choice
id:: a681313e-efa5-466a-a808-b36d5886d5d3
content:: Most definitions of artificial general intelligence (AGI) set its bar at roughly what level?
options::
- [x] Matching humans across most cognitive tasks
- Exceeding the best humans in nearly all domains
- Matching expert humans at one hard task
- Passing as human in a short text conversation
shuffle:: true

#### Question: Choice
id:: c5f3176b-6b55-4e27-a1ae-8b4bbcc87f8b
content:: Under common definitions, which case counts as transformative AI but not as AGI?
options::
- [x] Many narrow systems that together change the economy as much as the industrial revolution did
- One general system that matches humans at most tasks but changes little because it is rarely used
- One general system that matches humans at most tasks and changes the economy as much as the industrial revolution did
- A chatbot that passes as human in short chats and changes little about how people work
shuffle:: true

#### Question: Open
id:: 9345314c-8637-44a6-866c-b3c414adff3e
content:: Definitions of AGI vary between researchers and companies. Name one way in which they differ.
assessment-instructions:: Score out of 100. 100 for any one clear difference, such as: the bar (average human, skilled expert, or best humans); scope (cognitive tasks only, or physical work too); the measure (tasks, benchmarks, share of paid work, or economic impact); whether one system must do it all; how autonomous it must be. 50 for a vague answer like "people define it differently".

#### Question: Choice
id:: 5bb3471d-170a-48c1-ab1d-853c66c44ed3
content:: Why do some researchers argue that "human-level AI" is a poor name for a single milestone?
options::
- [x] AI skills are uneven: superhuman at some tasks, weak at others
- Intelligence tests designed for humans cannot be given to software
- AI systems already beat humans at every cognitive task
- AI progress is too slow for any milestone to be reached soon
shuffle:: true

#### Question: Open
id:: 6010aca7-7675-456e-8834-0d0897980999
content:: An AI system does the tasks of a desk job about as well as a typical human worker. Give one advantage it could still have over that worker.
assessment-instructions:: Score out of 100. 100 for any one of: works much faster; many copies can run at once; works without breaks or sleep; copies can share what one has learned; cheaper to run; can be scaled up with more computing power or improved further. 50 for a vague answer such as "it's a computer".

#### Question: Choice
id:: c50cffc1-715f-44fc-ae50-8de88de0233a
content:: US Executive Order 14434, "Inaugurating the Era of Super Intelligence" (29 September 2026), tells federal agencies to write "Super Intelligence" in place of "Artificial Intelligence" in official communications, covering whatever the legal definition of AI covers. So an agency's spam filter could be called "Super Intelligence". Is the filter a superintelligence in Bostrom's sense?
options::
- [x] No: the order changes a label, not what the filter can do
- Yes: a federal order now sets the term's meaning in AI research
- Yes: spam filters already beat humans at their one task
- No: Bostrom's sense requires the system to be conscious
shuffle:: true

#### Question: Open
id:: d802801d-87ba-40ab-9ed2-4cf7b8e113ad
content:: Two forecasters disagree by 20 years about when AGI will arrive. Why should you check how each defines AGI before concluding that they disagree about the future?
assessment-instructions:: Score out of 100. 100 for explaining that definitions set different bars (for example matching an average person at most tasks versus automating most paid work), so the two forecasts may be about different milestones and may partly agree. 50 for saying definitions vary without linking this to the forecasts.

#### Question: Choice
id:: 2192c16f-ad54-49e3-ba0e-0a1a40a39248
content:: OpenAI's charter defines AGI as "highly autonomous systems that outperform humans at most economically valuable work". A system beats most people on reasoning and knowledge tests, but most jobs still need a human to direct and check its work. Does it meet this definition?
options::
- [x] No: test scores are not the same as doing most paid work on its own
- Yes: beating most people on reasoning tests means it outperforms them at work
- Yes: the definition counts any system that is above average on most tests
- No: the definition also requires the system to be better than every expert
shuffle:: true
