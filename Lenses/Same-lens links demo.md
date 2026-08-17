{++{"author":"Elias's AI","timestamp":1786970436284}@@---
id: 3dad9c8a-ae43-4441-9aa8-586516e203fb
title: Same-lens links demo
tldr: Link directly to headings, paragraphs, and blocks within one Lens.
summary_for_tutor: Demonstrates Obsidian-style same-Lens heading links and block markers. Links scroll within the current Lens without opening a new tab.
---

#### Text
content::
Use same-Lens links when a learner should jump to another part of this page. Links scroll smoothly and stay in this Lens. ^top

Try them:

- [[#Heading targets|Jump to a heading]]
- [[#^plain-target|Jump to a paragraph]]
- [[#^callout-target|Jump to a whole callout]]

!## Block targets

Add a stable marker at the end of a paragraph:

`This paragraph can be linked. ^plain-target`

Link to it with `\[[#^plain-target|link text]]`. Marker is not shown to learners. IDs may contain letters, numbers, and dashes.

This paragraph can be linked. ^plain-target

A marker on its own line labels whole block immediately above it. This works for callouts too:

:::callout {title="A target callout" tone="blue"}
This whole callout is destination. [[#^top|Return to top]]
:::

^callout-target

!## Heading targets

Link to heading text with `\[[#Heading targets|link text]]`. No extra marker needed.

Heading links use visible heading name. Block links use stable IDs, so they keep working if visible wording changes.

[[#^top|Return to top]]
++}