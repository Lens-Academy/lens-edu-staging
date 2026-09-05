---
id: '47dbf76e-5b0b-4b55-ab9a-bbd17c2023ce'
title: Widget Demo
tldr: Two interactive widgets, ported from XLab's Verification track, embedded between text segments with the new Widget segment.
summary_for_tutor: A demo lens for the Widget segment. The learner first works through "The verification problem" (four answers to how two rivals can know the other complies; only neutral privacy-preserving verification holds), then explores "The types of AI" concentric diagram (AI, Narrow AI, Machine Learning, Deep Learning, Generative AI, LLMs, Transformer LLMs, with example systems). Help them articulate why trust, punishment and transparency each fail, and where today's systems sit in the AI taxonomy.
tags: [wip]
---

#### Text
content::
This lens demonstrates the **Widget** segment: an interactive page written as HTML in the editor's `widgets/` folder and embedded inline between ordinary text segments. Try the one below and test all four answer{--{"author":"E2","timestamp":1788611050092}@@s.--}

#### Widget
source:: [[../widgets/verification-problem]]

#### Text
content::
Only the fourth option holds, and the rest of the course is about how you build it. Before that, a map of what "AI" even means. Tap a ring, or a system inside one, to read why it sits there and not one ring deeper.

#### Widget
source:: [[../widgets/types-of-ai]]

#### Text
content::
Everything that exists today sits inside the Narrow AI ring. Where would you place a system like AlphaFold, and why? Tell the tutor.

#### Chat
instructions:: The learner has just used two interactive widgets: one testing four answers to the verification problem (trust, punish, transparency, verification), one mapping AI categories as concentric rings. Ask where they would place AlphaFold (a deep-learning system that predicts protein structures; not generative language, not a transformer LLM in the chatbot sense) and probe their reasoning about the ring boundaries. Keep it to a short exchange.
