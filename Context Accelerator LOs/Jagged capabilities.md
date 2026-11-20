---
id: 5a0d68e8-946e-4342-9133-2271f22baa58
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why AI systems can beat experts on some tasks while failing at ones humans find easy, why they hallucinate, and why neither impressive nor embarrassing examples settle how capable they are.

## Requires
- [[Current AI capabilities]]

## Helpful first

## Why it matters
The same AI system can solve hard maths problems and then make a basic error a child would avoid. If you understand this unevenness, you can judge both dismissive and alarmed claims about AI on the evidence rather than on one striking example, and know when to check its outputs.

## Lenses
- [Taking Jaggedness Seriously (Helen Toner, Rising Tide)](https://helentoner.substack.com/p/taking-jaggedness-seriously): why AI keeps getting better while still failing in strange ways, what "jagged" means, and four reasons the unevenness may last (how easy success is to check, missing context, adversaries, physical work); read "What is jaggedness?" and "Why might AI keep being jagged?" if short on time (November 2025).
- [Centaurs and Cyborgs on the Jagged Frontier (Ethan Mollick, One Useful Thing)](https://www.oneusefulthing.org/p/centaurs-and-cyborgs-on-the-jagged): the piece that coined the "jagged frontier", with a study of consultants using GPT-4 who did better on tasks inside the frontier and worse on a task just outside it, because the edge is invisible and they trusted wrong answers; the study models are from 2023 (September 2023).
- [Why language models hallucinate (OpenAI)](https://openai.com/index/why-language-models-hallucinate/): why models state falsehoods confidently, including that tests score a lucky guess above "I don't know" and that rare facts like a person's birthday can't be learned from patterns (September 2025).
- [Moravec's Paradox (Ege Erdil, Epoch AI)](https://epoch.ai/gradient-updates/moravec-s-paradox): why skills that are easy for humans, like perception and movement, are hard for AI, and which jobs this suggests will be automated first or last (December 2024) (more advanced).

## Tests

#### Question: Choice
id:: 84cd3687-257a-46d5-9f58-b30963860fa1
content:: What does it mean to say an AI system's capabilities are "jagged"?
options::
- [x] Its skill varies unevenly across tasks, not in line with how hard they are for humans
- Its abilities improve in sudden jumps rather than smoothly as models are scaled up
- It gives different answers to the same question from one attempt to the next
- It performs well when tested by developers but worse once deployed to real users
shuffle:: true

#### Question: Choice
id:: c7dc1b04-45b8-4ea8-8103-a5ef7e7d6fff
content:: In AI, what is a "hallucination"?
options::
- [x] A fluent, confident output that is false or unsupported, like an invented citation
- A deliberate lie a model tells in order to pursue a hidden goal of its own
- A wrong answer caused by a user giving the model a misleading prompt on purpose
- A drop in answer quality when a conversation grows longer than the context window
shuffle:: true

#### Question: Choice
id:: 9df6cc0d-d5e6-44b9-8fe4-8a1ebed62729
content:: Which of these is a main reason language models hallucinate?
options::
- [x] Training and tests reward a confident guess over saying "I don't know"
- Models look up facts in an internal database that contains many errors
- Models mostly repeat false claims they found in their training text
- Models run out of memory and fill the gaps with random words
shuffle:: true

#### Question: Choice
id:: 39e7a04f-7cc1-4c72-bd6f-59caa652e1e6
content:: As of November 2026, how do hallucination rates of frontier language models compare with those of the first ChatGPT in 2022?
options::
- [x] Much lower, especially with web search, but confident false claims still occur
- About the same, since making models larger has not reduced them
- Close to zero for any model that has web search turned on
- Higher, because newer models write longer answers containing more claims
shuffle:: true

#### Question: Choice
id:: 935a4691-0b73-43b6-9dbc-5368914bdbec
content:: Some language models that could solve hard maths problems failed to count how many times the letter "r" appears in "strawberry". Which is the best explanation?
options::
- [x] Models see text as multi-character tokens, not as individual letters
- Models cannot look back at earlier parts of a word once it is written
- Spelling questions were filtered out of training data as too trivial
- Models are trained mainly on maths, leaving little room for spelling
shuffle:: true

#### Question: Choice
id:: 55567f82-4884-4448-a390-931941fe1805
content:: What does Moravec's paradox observe about AI?
options::
- [x] Skills humans find effortless, like perception and movement, are often hardest to automate
- Each gain in AI capability makes the next gain harder and more expensive to achieve
- AI systems tend to become less reliable the more parameters they have
- People tend to judge an AI system as less capable the more they use it
shuffle:: true

#### Question: Choice
id:: afa2c159-329d-416e-940a-ef6a375b06a1
content:: Why can jagged capabilities cause problems for people who use AI at work?
options::
- [x] The edge of what it does well is hard to see, so users trust wrong outputs
- It refuses tasks outside its strengths, which slows the user's work down
- It mainly helps with tasks users could already do quickly by themselves
- Its strengths lie in areas that most workplaces have little need for
shuffle:: true

#### Question: Choice
id:: 80a930ce-08c5-4a17-a26d-79d0ad5322ee
content:: You ask a language model with no web search for each of these. Which answer most needs checking before you rely on it?
options::
- [x] The founding date of a small local charity
- A summary of the causes of the First World War
- A general explanation of how vaccines work
- A translation of a short email into Spanish
shuffle:: true

#### Question: Open
id:: 37d658dc-68aa-42a9-99f6-98c7e749a735
content:: Someone argues: "AI still fails at some tasks a child can do, so fears about advanced AI are overblown." Using the idea of jagged capabilities, what does this argument miss?
assessment-instructions:: Score out of 100. 100 for explaining that failing at some easy-seeming tasks doesn't limit ability elsewhere: what matters for risk is capability in relevant areas (such as coding, research or persuasion), which can be strong despite odd weak spots. Also accept that weak spots are often fixed quickly or worked around with tools. 40 for only saying AI is improving, without linking this to unevenness.

#### Question: Open
id:: 41330111-69e8-44ad-8198-a2af0f76f767
content:: An AI system scores above most doctors on a medical licensing exam. Someone concludes it can now replace doctors. Using the idea of jagged capabilities, why might this not follow?
assessment-instructions:: Score out of 100. 100 for explaining that the exam covers only part of the job, and uneven capabilities mean the system may fail at other needed parts, such as examining patients, handling unusual cases, avoiding confident errors or doing long multi-step work. 50 for a general "exams aren't real life" without mentioning uneven skills or a specific gap.

#### Question: Open
id:: 834aadb6-f699-454e-812c-380c03fa5bfd
content:: Name one kind of task that frontier AI systems, as of November 2026, still often do poorly, and briefly say why.
assessment-instructions:: Score out of 100. 100 for any one, with a plausible reason: long tasks without supervision (errors build up); physical tasks with robots (little training data; perception and movement are hard); learning on the job (no lasting learning from experience); knowing when they don't know (hallucination); novel visual puzzles. 50 for a correct task with no reason.
