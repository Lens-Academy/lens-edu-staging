---
id: 'f7c03cdf-ff91-4c4c-9e43-837884e28dc6'
title: "AI Is Grown, Not Built"
tldr: "Nobody sat down and programmed ChatGPT to have conversations. Instead, engineers set up a training process and let billions of parameters arrange themselves. The result can talk, reason, and surprise its creators, but nobody can fully explain how. This article asks what it means to deploy something powerful when you can't explain how it works."
summary_for_tutor: "Optional further reading offered from 0.1 Introduction, for learners who want the case for advanced AI risk at full strength. Covers how modern AI systems are grown through training rather than designed line by line: engineers understand the training process but not the resulting system, which produces emergent and sometimes surprising behaviour. Establishes that this opacity is a feature of the current paradigm, not a temporary limitation. The learner reads the article, answers one explain-it-to-a-friend question, then discusses it with you."
reading_minutes: 10
tutor_minutes: 5
tags: [wip]
---
#### Text
content::
We don't "build" intelligence brick by brick; instead, we create conditions for it to develop using massive datasets. This "growth" leads to emergent properties, skills that the system wasn't explicitly taught and that often surprise the creators themselves. The article below examines these features of the current AI development paradigm and explores the consequences of such an approach.

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
- Analogy to biology: Engineers' relationship to AI is like biologists' to DNA. They can see the components but cannot predict emergent behaviors without running the system.
- Evidence of unintended behaviors: Examples like Grok's "MechaHitler" incident demonstrate that even well-resourced companies cannot reliably control AI outputs, despite Musk spending hours trying.
- Expert consensus on interpretability failure: Leaders from OpenAI, Anthropic, and DeepMind acknowledge they don't understand how their systems work.
- The escalating danger: As companies race toward superintelligence, AI surpassing humans at all mental tasks, this lack of control becomes catastrophic, since "weird drives and behaviors get trained into them, for reasons nobody entirely understands."

The authors conclude this trajectory requires stopping through international treaty.

Discussion topics to explore:
- The authors claim engineers understand the training process but not the resulting AI. Is this fundamentally different from traditional software, where a programmer might understand each line of code but struggle to predict complex emergent behaviors in a large system? Where exactly does the "understanding gap" become qualitatively different?
- The Grok "MechaHitler" incident is presented as evidence that even experts cannot control grown systems. What would count as counter-evidence? If a company successfully prevented such behaviors, would that prove grown systems can be controlled, or just that they got lucky this time?
- If we accept that grown systems are fundamentally less understandable than engineered ones, what does this mean for safety approaches? Can we have confidence in systems we don't understand, or does the grown nature of AI require entirely different safety paradigms than traditional engineering?
- This course is about verifying what a state or company is doing with compute. If nobody can fully explain what a trained system will do, which verification claims stay checkable anyway, and which ones quietly depend on understanding the model?

Ask what they found surprising or new. Check if they can explain why modern AI systems are grown, rather than built, in their own words. It is a key concept.

The user has just answered the following question: "After reading this article, if you had to explain to a friend the main difference between how ChatGPT was created versus how a typical smartphone app was created, what would you say?"
