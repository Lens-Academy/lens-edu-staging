---
id: 8131f27c-91eb-433a-b834-7fa142f4950a
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what it means to call alignment research pre-paradigmatic, give the arguments for and against that description, and say what it implies for choosing, judging and funding alignment work.

## Requires
- [[AI alignment]]

## Helpful first
- [[Alignment difficulty arguments]]

## Why it matters
Alignment researchers disagree about which problems matter and what counts as progress, not just about answers. Asking whether this reflects missing foundations helps you weigh research claims, notice when work drifts towards what is easy to measure, and judge plans to hand alignment research to AI systems, which so far do best where success is easy to check.

## Lenses
- [Alignment Researchers Disagree a Lot (Planned Obsolescence)](https://www.planned-obsolescence.org/p/disagreement-in-alignment): Ajeya Cotra on why the field is pre-paradigmatic. Researchers disagree on what the problem is, which work matters and whether progress has been made, so there is little shared foundation to build on (March 2023).
- [Epistemological Framing for AI Alignment Research (Alignment Forum)](https://www.alignmentforum.org/posts/Y4YHTBziAscS5WPN7/epistemological-framing-for-ai-alignment-research): Adam Shimi uses Kuhn's paradigms and "normal science" to argue that alignment has no shared paradigm yet, and suggests how to place and judge work in such a field (March 2021).
- [[../Lenses/AFSRA - 2018 Update, Our New Research Directions|Why Deconfusion Matters]]: Nate Soares explains what MIRI means by deconfusion and why it thinks AI can be built without clear concepts of "optimization" and "aiming" but not safely aimed without them. Read only the subsections "What we mean by deconfusion" and "Why deconfusion is highly relevant to AI accident risk" in section 2 (2018).
- [The Field of AI Alignment: A Postmortem, and What To Do About It (LessWrong)](https://www.lesswrong.com/posts/nwpyhyagpPYDn4dAW/the-field-of-ai-alignment-a-postmortem-and-what-to-do-about): John Wentworth argues that most alignment work is "streetlighting" (working on tractable problems rather than the hard ones), that funding and recruiting reward this, and that the hoped-for move to a paradigm has not happened (December 2024).
- [Mech Interp Is Not Pre-paradigmatic (LessWrong)](https://www.lesswrong.com/posts/beREnXhBnzxbJtr8k/mech-interp-is-not-pre-paradigmatic): Lee Sharkey argues against the label for one subfield, saying interpretability inherited a paradigm from neuroscience and has gone through Kuhn-style crises. Read the "Preamble" and "Claim" sections (June 2025).

## Tests
#### Question: Choice
id:: 2504af69-5cd3-4911-8e72-09fc7b64e2cb
content:: In the philosopher of science Thomas Kuhn's sense, what does it mean for a field to be pre-paradigmatic?
options::
- [x] Its researchers don't yet share basic concepts, central problems or methods
- It has not yet produced any experimental results
- Its main theory has been disproven and is waiting to be replaced
- It has not yet been recognized as a subject by universities
shuffle:: true

#### Question: Choice
id:: 2090080a-9f2f-451d-a836-09cdc516637e
content:: Which observation is the strongest evidence that AI alignment research is pre-paradigmatic?
options::
- [x] Researchers disagree about which problems are central and what would solve them
- Far fewer people work on alignment than on making AI more capable
- Alignment research draws on both computer science and philosophy
- Most alignment research is paid for by philanthropists and AI companies
shuffle:: true

#### Question: Choice
id:: 11b9b476-9b07-47ca-98d2-780316895c56
content:: Alignment researchers can't yet run experiments on the superhuman AI systems they most worry about. How does this bear on the claim that alignment is pre-paradigmatic?
options::
- [x] It limits feedback on which concepts and methods will hold up
- It shows experiments on current models are irrelevant to alignment
- It means researchers must agree on a theory before any testing
- It shows the field mainly lacks funding rather than shared concepts
shuffle:: true

#### Question: Choice
id:: 3a760eeb-fd93-4166-9020-13c7a3a96367
content:: Some researchers argue that a priority in alignment today is clarifying concepts such as "goal", "agent" or "deception". Why would that be a priority if the field is pre-paradigmatic?
options::
- [x] Without clear concepts, precise problems can't be posed or solutions recognized
- Clear definitions are needed before AI companies can be legally regulated
- Current AI systems will behave better once researchers define these terms
- Clear concepts make alignment research much easier to explain to the public
shuffle:: true

#### Question: Choice
id:: 3eb17b1b-305b-4730-92da-965f8c201fd5
content:: Critics warn that alignment researchers may fall into the "streetlight effect". What does that mean here?
options::
- [x] Working on problems that are easy to measure rather than those that matter most
- Copying the research agenda of whichever AI lab is most in the news
- Publishing positive results while quietly dropping experiments that failed
- Studying the AI risks that get media attention instead of rarer ones
shuffle:: true

#### Question: Choice
id:: cb96dfd7-426f-4eb5-968c-8f14666de386
content:: If alignment research is pre-paradigmatic, which advice to a new alignment researcher follows most directly?
options::
- [x] Question how the field frames the problem, instead of simply adopting one framing
- Join the best-funded agenda, since funding shows which methods have worked
- Leave questions of framing to philosophers and focus purely on engineering
- Focus on raising scores on the field's established alignment benchmarks
shuffle:: true

#### Question: Choice
id:: 27492023-6836-4b5d-b48e-9080acc1d621
content:: Suppose nobody yet knows which approaches to alignment will work. Taken on its own, which funding strategy does that uncertainty most directly support?
options::
- [x] Spreading money across several quite different agendas
- Funding only the agenda most researchers currently favor
- Holding back funding until one agenda has been shown to work
- Funding only agendas that show results on today's benchmarks
shuffle:: true

#### Question: Choice
id:: e25e0b7f-f3fe-43a5-a570-6a9be79fda9b
content:: In 2026, Anthropic reported that AI agents beat human researchers at reducing alignment failures that existing benchmarks can measure, such as sycophancy and jailbreaks. If alignment is pre-paradigmatic, what is the main limit on what this shows?
options::
- [x] The hardest open problems lack agreed measures of success to optimize
- Sycophancy and jailbreaks are not really alignment problems at all
- AI agents can only refine ideas that humans have already proposed
- Results on current models can never tell us anything about future ones
shuffle:: true

#### Question: Open
id:: 95d78552-eb23-46f6-812c-345f41453119
content:: Give one argument against describing alignment research today as pre-paradigmatic.
assessment-instructions:: Score out of 100. 100 for any one of: some subfields (e.g. interpretability, evaluations, AI control) now share methods, benchmarks and standards of evidence; experiments on current models give real feedback; there is broad agreement on some core problems (e.g. specifying goals, overseeing smarter systems); the label can excuse vague work from scrutiny. 50 for saying the field has made progress, with no reason why that shows shared concepts or methods.

#### Question: Open
id:: 7d991553-3146-4f58-8b20-a681423a3785
content:: Give one reason why a pre-paradigmatic field like alignment is hard to grow quickly just by adding many new researchers.
assessment-instructions:: Score out of 100. 100 for any one of: there are few well-defined problems to hand to newcomers; progress depends on research taste and mentorship, which are scarce; it is hard to judge who is doing good work; newcomers tend to repeat the same few ideas or follow the most visible agenda. 50 for "it's a hard field" with no link to the missing shared problems or standards.
