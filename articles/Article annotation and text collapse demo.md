---
title: "Article annotation and text collapse demo"
author: Lens Academy
published: 2026-06-16
source_url: https://editor.lensacademy.org/24abc9c0/Lens-Edu/articles/Article-annotation-and-text-collapse-demo.md
---{++{"author":"Luc's AI","timestamp":1785090624676}@@

%%
Add discussion note here:

...

%%++}

This article demos how to use `collapse`, `note`, and `footnote` fields inside article markdown.

See for example this: :collapse[this text will be collapsed by default, but can be expanded by the user] isn't that pretty nice?

We can also collapse entire paragraphs:

:::collapse
This entire paragraph will be collapsed by default,

but can be opened by the user.
:::

For footnotes added by the article authors, use markdown footnotes[^1]. We can also add Lens-added footnotes with :footnote[This is a footnote added by Lens].

If we want an always-visible note, we can do :note[This is a note added by Lens] or we can do:
::note[This is a note created with two colons `::`, which means it gets its own line.]

Finally, we can do multi-line notes:
:::note
This is the first line of the note.

This is a second.

This is a third.
This is rendered on the same line as the third.
:::

You can nest these. For example, here is a collapsed field :collapse[with a note inside: :note[This note explains why we collapsed this bit of text.]]

[^1]: Hi. This is a footnote added by the author of the article.