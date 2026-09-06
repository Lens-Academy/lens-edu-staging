---
id: '47dbf76e-5b0b-4b55-ab9a-bbd17c2023ce'
title: Widget Demo
tldr: Three interactive widgets ported from XLab's Verification track, plus one deliberately broken one, embedded between text segments with the new Widget segment.
summary_for_tutor: A demo lens for the Widget segment. The learner first works through "The verification problem" (four answers to how two rivals can know the other complies; only neutral privacy-preserving verification holds), then explores "The types of AI" concentric diagram (AI, Narrow AI, Machine Learning, Deep Learning, Generative AI, LLMs, Transformer LLMs, with example systems). Help them articulate why trust, punishment and transparency each fail, and where today's systems sit in the AI taxonomy.
tags: [wip]
---

#### Text
content::
This lens demonstrates the **Widget** segment: an interactive page written as HTML in the editor's `widgets/` folder and embedded inline between ordinary text segments. Try the one below and test all four answers.

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

#### Text
content::
Third widget: where verification work is happening today, and where it is not. Rows are kinds of verification, columns are who does the work; darker squares mean more activity. Tap a square, a row label or a column label.

#### Widget
source:: [[../widgets/verification-landscape]]

#### Text
content::
Finally, what a learner sees when a widget file has errors. The file below is broken on purpose (a stray `</span>` and an unclosed `<script>`); the validator flags it and the lesson shows a notice instead of a hole.

#### Widget
source:: [[../widgets/broken-demo]]

#### Text
content::
Last: a widget that **remembers**. Name an organisation and fill the eight boxes of a theory of change. Your entries are saved to your account (reload the page and they are still there), the tutor can see them, and this page cannot be marked complete until all eight boxes are filled. When you are done, the widget offers to send the canvas to the tutor for a review.

#### Widget
source:: [[../widgets/theories-of-change]]
required:: true

#### Text
content::
One more: a widget that scores **several things separately**. Pick a verification mechanism, then write three short answers. Each has its own marking scheme, and the third one's scheme is built at runtime from your own second answer. Every score comes with a feedback button that sends that answer, its score and item-specific instructions to the tutor.

#### Widget
source:: [[../widgets/verification-critique]]

#### Chat
instructions:: The learner has just used two interactive widgets: one testing four answers to the verification problem (trust, punish, transparency, verification), one mapping AI categories as concentric rings. Ask where they would place AlphaFold (a deep-learning system that predicts protein structures; not generative language, not a transformer LLM in the chatbot sense) and probe their reasoning about the ring boundaries. Keep it to a short exchange.
