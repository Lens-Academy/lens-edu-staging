---
id: cc4cce03-8634-479d-afd3-be2e83a30d3e
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Give concrete, dated examples of what frontier AI systems could do by late 2026 in writing, coding, maths and science, and long autonomous tasks, and name areas where they still fall short.

## Requires
- [[Large language models]]

## Helpful first
- [[Benchmarks]]
- [[AI agents]]

## Why it matters
Decisions about AI, from how to use it at work to which policies to support, rest on a picture of what it can do now. Capabilities have changed sharply within single years, so a picture even a year old leads people to misjudge both the risks and how soon further milestones may arrive.

## Lenses
- [[../Lenses/AI Safety Atlas - Capabilities - Current Capabilities|Current Capabilities]]: a tour of what AI could do by late 2025, domain by domain.
- [[../Lenses/A new Moores Law for AI agents (interactive)|A new Moore's Law for AI agents]]: how long the tasks are that agents can complete, and how fast that grows.
- [[../Lenses/IABIED - QA - Shallowness of Current AIs|Shallowness of current AIs]]: why top results sit beside odd failures.
- [International AI Safety Report 2026](https://internationalaisafetyreport.org/publication/international-ai-safety-report-2026): chapter 1 on what AI can and can't do, as of February 2026.

## Tests

#### Question: Choice
id:: c598595a-d5d4-4fda-b882-857ce4449337
content:: In early 2026, METR measured how long the software tasks are (in a skilled human's time) that the best AI agents complete half the time. Roughly how long were they?
options::
- [x] More than a working day
- About ten minutes
- About an hour
- About a working month
shuffle:: true

#### Question: Choice
id:: 1edca4cb-fcd7-4821-9fff-16d94a559846
content:: In April 2026, Anthropic withheld its Claude Mythos Preview model from general release and gave it only to selected partner organisations. Which capability was the main reason?
options::
- [x] Finding and exploiting unknown software vulnerabilities on its own
- Writing persuasive political messages at very large scale
- Designing new proteins that could be turned into toxins
- Copying its own weights to servers outside the company
shuffle:: true

#### Question: Choice
id:: cfff3987-5045-4e68-9f6b-bb2c7dbcf3e5
content:: OSWorld tests AI agents on everyday computer tasks, such as editing a spreadsheet, done through the screen, mouse and keyboard. Humans complete about 72% of its tasks. Where did the best agents score in early 2026?
options::
- [x] Around or above 72%
- About 15%
- About 35%
- About 50%
shuffle:: true

#### Question: Choice
id:: d9e1bed4-96df-48d6-b695-9109f8f63330
content:: In METR's randomised trial in early 2025, experienced open-source developers worked on their own projects with and without AI coding tools. With the tools, how long did their tasks take?
options::
- [x] About 19% longer
- About 20% less time
- About half as long
- About the same time
shuffle:: true

#### Question: Open
id:: fb739059-3ee1-468f-98b9-55c1cfe02599
content:: AI agents' scores on coding benchmarks rose fast through 2025, yet a controlled trial in early 2025 found that AI tools slowed experienced developers down on their own projects. Give one reason both can be true.
assessment-instructions:: Score out of 100. 100 for any one of: benchmark tasks are self-contained, clearly specified and checked automatically, unlike real projects; real projects need deep context and high quality standards; time spent prompting, waiting for, reviewing or fixing AI output; the tools improved after the trial. 50 for a vague answer such as "benchmarks aren't realistic" with no reason.

#### Question: Choice
id:: f7c7fccf-cb35-48a8-ad0c-beb53384f51a
content:: Which best describes frontier AI's role in mathematical research as of 2026?
options::
- [x] It has settled some open problems, with experts checking the proofs
- It solves contest problems but has yet to settle an open problem
- It is used mainly to typeset and format proofs written by humans
- It has replaced human peer reviewers at the major maths journals
shuffle:: true

#### Question: Choice
id:: 42334f7f-7ab8-466d-9426-2bed2b08f2f6
content:: How did the best AI systems do on the problems of the International Mathematical Olympiad held in July 2026?
options::
- [x] Several were reported to score full marks
- The best reached bronze-medal level
- The best scored about half marks
- The best solved only the easiest problem
shuffle:: true

#### Question: Open
id:: a1f39422-70db-4373-b330-60b2a228ab3a
content:: Name two kinds of scientific or research work that frontier AI systems were helping with as of 2026.
assessment-instructions:: Score out of 100. 100 for any two of: literature reviews; data analysis; writing or debugging research code; designing experiments; solving or checking maths problems and proofs; protein design or structure prediction; finding software vulnerabilities; drafting papers. 50 for one correct example.

#### Question: Choice
id:: da0a8328-1f34-4445-8f8d-f50916a1fddc
content:: Which of these is a well-documented weakness of frontier AI writing as of 2026?
options::
- [x] Confidently citing facts or sources that don't exist
- Frequent spelling and grammar mistakes in long texts
- Refusing to write fiction, poetry or other creative work
- Failing to match a tone or style the user asks for
shuffle:: true

#### Question: Choice
id:: efd7a64c-d9cc-4d52-ac2b-f46c8a6304c2
content:: As of early 2026, in which of these areas were frontier AI systems clearly weakest?
options::
- [x] Physical tasks, such as household chores done by robots
- Answering graduate-level science exam questions
- Writing short programs from a clear specification
- Summarising long documents into a few key points
shuffle:: true

#### Question: Open
id:: b887bce1-451e-4819-902f-b4e57ffc30b1
content:: Someone says: "AI chatbots just predict the next word, so they can't do real work." Using one concrete example of what frontier AI could do as of 2026, explain why this undersells current capabilities.
assessment-instructions:: Score out of 100. 100 for an accurate concrete example (such as completing multi-hour software tasks alone, finding serious unknown software vulnerabilities, settling an open maths problem, full marks on olympiad problems, operating desktop software) plus the point that how a system is trained doesn't limit what it can achieve. 60 for an accurate example alone.
