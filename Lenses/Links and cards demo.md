---
id: 39b2fd39-a53b-48cf-a388-a8f088aabf43
duration_minutes: 2
tldr: "Two ways to link between lenses in the editor: a plain wikilink, and the prettier ::card syntax that renders a clickable card. Both need the linked lens to live in the same module or course."
summary_for_tutor: "Demonstrates in-editor linking between lenses via a single Text segment: standard wikilinks versus the ::card prefix, which renders a card-style link. Notes that any linked lens must belong to the same module or course. No questions or chat."
title: Links and cards demo
---

#### Text
content::
We can use normal wikilinks inside the editor to link to other lenses: [[../Lenses/Article annotation and text collapse demo]]. This does require the lens that you're linking to, to also be part of the same module or course.

For a prettier UI, you can use `::card` before the wikilink.
::card[[Response to question segments]]

::card[[Roleplay demo]]

::card[[video demo]]{++{"author":"Elias's AI","timestamp":1788339888915}@@

A blockquote line directly under a card renders as a hook that tells the learner what they get from it:

::card[[Roleplay demo]]
> One-sentence hook saying what a curious learner gets from this lens.

Cards also work inside callouts, including closed ones — useful for optional-reading sections:

:::callout {title="Optional: dive deeper" tone="neutral" collapse="closed"}
::card[[video demo]]
> A card inside a collapsed callout: the callout is the click-to-open affordance, the card is the link.
:::

A card can target a module instead of a lens; it then shows the learner's progress in it. This one points at the module demonstrating `hide:: true` imports — lenses that are members of the module (so cards to them resolve in place) without appearing in the sidebar or progression:

::card[[../modules/demo-module-with-hidden-imports]]

Two footnotes: a card to a lens outside this module or course deep-links into whatever other module contains it, so import the target (hidden if you like) instead. And images are not linked this way at all — use standard markdown `![alt](url)`; the `![[...]]` embed form is not supported in lens or article text.++}
