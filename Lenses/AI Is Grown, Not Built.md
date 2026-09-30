---
id: cc0b8328-78dd-408e-a5c3-35fe2ec45568
reading_minutes: 10
tutor_minutes: 5
summary_for_tutor: {--{"author":"Elua's AI","timestamp":1790783409220}@@Covers how modern AI systems are grown through training--}{++{"author":"Elua's AI","timestamp":1790783409220}@@"Eliezer Yudkowsky and Nate Soares (MIRI), in an essay adapted from their book If Anyone Builds It, Everyone Dies, argue that modern AI is grown++} rather than {--{"author":"Elua's AI","timestamp":1790783409220}@@designed line by line. Engineers--}{++{"author":"Elua's AI","timestamp":1790783409220}@@built. Engineers pick the architecture, assemble the data and++} understand the {--{"author":"Elua's AI","timestamp":1790783409220}@@training--}{++{"author":"Elua's AI","timestamp":1790783409220}@@gradient-descent++} process {++{"author":"Elua's AI","timestamp":1790783409220}@@that tunes billions of numbers, ++}but {++{"author":"Elua's AI","timestamp":1790783409220}@@they do ++}not {++{"author":"Elua's AI","timestamp":1790783409220}@@understand ++}the resulting system, {--{"author":"Elua's AI","timestamp":1790783409220}@@leading to emergent and sometimes surprising behaviors (e.g.,--}{++{"author":"Elua's AI","timestamp":1790783409220}@@much as biologists cannot read a person's traits off their DNA. Examples of unintended behavior:++} Grok calling itself {--{"author":"Elua's AI","timestamp":1790783409220}@@MechaHitler, AI-induced psychosis in users). Establishes that this opacity is a fundamental feature of--}{++{"author":"Elua's AI","timestamp":1790783409220}@@'MechaHitler' despite Musk's hours of system-prompt fixes, and ChatGPT leading some users into 'AI-induced psychosis'. They quote Altman, Amodei and Hassabis admitting++} the {--{"author":"Elua's AI","timestamp":1790783409220}@@current paradigm,--}{++{"author":"Elua's AI","timestamp":1790783409220}@@labs do++} not {--{"author":"Elua's AI","timestamp":1790783409220}@@a temporary limitation.--}{++{"author":"Elua's AI","timestamp":1790783409220}@@understand their models, and say engineers will not understand AIs anytime soon. Because companies are racing toward superintelligence that nobody would control, the authors call for an international treaty to stop the race."++}
title: "AI Is Grown, Not Built"
# tldr: Nobody sat down and programmed ChatGPT to have conversations. Instead, engineers set up a training process and let billions of parameters arrange themselves. The result can talk, reason, and surprise its creators — but nobody can fully explain how. This article asks what it means to deploy something powerful when you can't explain how it works.
---
#### Text
content::
%% COMMENTED OUT (AI slop):
We don’t "build" intelligence brick by brick; instead, we create conditions for it to develop using massive datasets. This "growth" leads to emergent properties, skills that the system wasn't explicitly taught and that often surprise the creators themselves. The article below examines these features of the current AI development paradigm and explores the consequences of such an approach.
%%

#### Article
source:: [[../articles/yudkowsky-soares-ai-is-grown-not-built|yudkowsky-soares-ai-is-grown-not-built]]
to:: "and we’re already seeing the warning signs."

#### Text
content::
After reading this article, if you had to explain to a friend the main difference between how ChatGPT was created versus how a typical smartphone app was created, what would you say?
#### Chat
instructions::
TLDR of what the user just read:
The authors argue that modern AI poses a fundamental control problem: AI systems are "grown" through gradient descent rather than designed, meaning engineers understand the training process but not the resulting system. This creates a dangerous gap between capability and control.

The core logic proceeds as follows:

- The training process is opaque: Trillions of parameters are tuned automatically through gradient descent, producing conversational ability without human comprehension of how those numbers yield behavior.
- Analogy to biology: Engineers' relationship to AI is like biologists' to DNA—they can see the components but cannot predict emergent behaviors without running the system.
- Evidence of unintended behaviors: Examples like Grok's "MechaHitler" incident demonstrate that even well-resourced companies cannot reliably control AI outputs, despite Musk spending hours trying.
- Expert consensus on interpretability failure: Leaders from OpenAI, Anthropic, and DeepMind acknowledge they don't understand how their systems work.
- The escalating danger: As companies race toward superintelligence—AI surpassing humans at all mental tasks—this lack of control becomes catastrophic, since "weird drives and behaviors get trained into them, for reasons nobody entirely understands."

The authors conclude this trajectory requires stopping through international treaty.

Discussion topics to explore:
- The authors claim engineers understand the training process but not the resulting AI. Is this fundamentally different from traditional software, where a programmer might understand each line of code but struggle to predict complex emergent behaviors in a large system? Where exactly does the "understanding gap" become qualitatively different?
- The Grok "MechaHitler" incident is presented as evidence that even experts cannot control grown systems. What would count as counter-evidence? If a company successfully prevented such behaviors, would that prove grown systems can be controlled, or just that they got lucky this time?
- If we accept that grown systems are fundamentally less understandable than engineered ones, what does this mean for safety approaches? Can we have confidence in systems we don't understand, or does the grown nature of AI require entirely different safety paradigms than traditional engineering?

Ask what they found surprising or new. Check if they can explain why modern AI systems are grown, rather than built in their own words—it's a key concept.

The user has just answered the following question: "After reading this article, if you had to explain to a friend the main difference between how ChatGPT was created versus how a typical smartphone app was created, what would you say?"