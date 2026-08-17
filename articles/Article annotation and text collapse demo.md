---
title: "Article annotation and text collapse demo"
author: Lens Academy
published: 2026-06-16
source_url: https://editor.lensacademy.org/24abc9c0/Lens-Edu/articles/Article-annotation-and-text-collapse-demo.md
---

%%
Add discussion note here:

...

%%

This article demos Lens article annotations and general course callouts.

## Existing article annotations

Use `:collapse[...]` for a short inline omission:

See for example this: :collapse[this text will be collapsed by default, but can be expanded by the user] isn't that pretty nice?

Use `:::collapse` for one or more omitted paragraphs:

:::collapse
This entire paragraph will be collapsed by default,

but can be opened by the user.
:::

For footnotes added by the article authors, use markdown footnotes[^1]. We can also add Lens-added footnotes with :footnote[This is a footnote added by Lens].

Use `:note[...]` for an inline Lens annotation:
:note[This is a note added by Lens]

Use `::note[...]` for a one-line block:
::note[This is a note created with two colons `::`, which means it gets its own line.]

Use `:::note` for a multiline Lens annotation:

:::note
This is the first line of the note.

This is a second.

This is a third.
This is rendered on the same line as the third.
:::

These annotations can be nested. For example, here is collapsed text :collapse[with a note inside: :note[This note explains why we collapsed this bit of text.]]

## General callouts

Use one `callout` directive for exercises, definitions, remarks, warnings, hints, solutions, and other highlighted course content. The title supplies the course-specific name. The tone controls its visual treatment.

```md
:::callout {title="Definition" tone="purple"}
Callout content supports normal Markdown.
:::
```

:::callout {title="Definition" tone="purple"}
A **local minimum** is a point whose value is no greater than the values at nearby points.
:::

Available tones are `neutral`, `blue`, `green`, `amber`, `red`, and `purple`.

:::callout {title="Exercise" tone="blue"}
Why can a local minimum differ from a global minimum?
:::

:::callout {title="Remark" tone="amber"}
The title is free text. `Remark` has no special platform meaning.
:::

:::callout {title="Success condition" tone="green"}
You can explain the distinction without assuming every local minimum is global.
:::

:::callout {title="Warning" tone="red"}
Do not infer global behavior from local information alone.
:::

:::callout {title="Optional context" tone="neutral"}
A neutral callout adds structure without strong semantic emphasis.
:::

The title is optional. An untitled callout renders only its content:

```md
:::callout {tone="neutral"}
This callout has no title.
:::
```

:::callout {tone="neutral"}
This callout has no title. It still provides a subtle visual grouping.
:::

### Collapsible callouts

Add `collapse="closed"` to start closed:

```md
:::callout {title="Hint" tone="amber" collapse="closed"}
Start with the definitions.
:::
```

:::callout {title="Hint" tone="amber" collapse="closed"}
Start by comparing which other points each definition quantifies over.
:::

Use `collapse="open"` when learners should see the content initially but may close it:

:::callout {title="Worked solution" tone="green" collapse="open"}
A local minimum only compares a point with nearby points. A global minimum compares it with every point in the domain.
:::

Collapsible callouts can also omit the title. Lens supplies a small `Show more` control:

:::callout {tone="neutral" collapse="closed"}
This is an untitled collapsible callout.
:::

Omit `collapse` for a callout that is always visible.

### Linkable callouts

Give a callout a stable `id`, then use a normal Markdown fragment link:

```md
:::callout {id="global-warning" title="Warning" tone="red"}
Do not confuse local and global minima.
:::

Review the [warning](#global-warning).
```

:::callout {id="global-warning" title="Warning" tone="red"}
Do not confuse local and global minima.
:::

Review the [warning](#global-warning).

### Callouts containing collapsible material

Callouts can contain existing inline annotations. This keeps the outer teaching block visible while hiding optional detail:

:::callout {title="Exercise with optional help" tone="blue"}
Give an example of a function with multiple local minima.

If you need help, reveal this :collapse[Try sketching a non-convex polynomial with more than one valley.]
:::

[^1]: Hi. This is a footnote added by the author of the article.