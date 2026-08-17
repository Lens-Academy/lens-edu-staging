---
id: 'e6b3badb-3839-4a7f-89ba-3f4191dcbf81'
title: Authored content features demo
tldr: See how Lens-authored text can use hidden sections, annotations, footnotes, callouts, Markdown, and math.
summary_for_tutor: "Formatting-only demo of shared authored-content features. It demonstrates inline and block hide directives, inline and block Lens notes, Markdown and Lens footnotes, static and collapsible callouts, nesting, normal Markdown, and LaTeX math."
---

#### Text
content::
\## Standard Markdown and math

Lens-authored text supports normal **Markdown**, including *emphasis*, [links](https://lensacademy.org), lists, blockquotes, code, tables, and headings.

- Lists work normally.
- So does inline code such as `x = 2`.

Inline math renders with dollar delimiters, for example $E = mc^2$. Display math uses double dollars:

$$
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
$$

\## Hidden text

Use `:hide[...]` for a short inline omission.

Reveal this :hide[hidden inline explanation].

Use `:::hide` for one or more omitted paragraphs:

:::hide
This whole block starts hidden.

It can contain multiple paragraphs.
:::

\## Lens annotations

Use `:note[...]` for an inline Lens annotation: :note[This note stays visible beside the surrounding text.]

Use `::note[...]` for a one-line block:

::note[This note gets its own line.]

Use `:::note` for a multiline annotation:

:::note
This is the first paragraph of a longer Lens note.

This is the second paragraph.
:::

\## Footnotes

Standard Markdown footnotes work in Lens-authored text[^author-note]. Lens-added footnotes use :footnote[This is extra context added by Lens].

\## Callouts

Use one `callout` directive for exercises, definitions, remarks, warnings, hints, solutions, and other highlighted course content. Titles are free text.

Source:

```md
:::callout {title="Definition" tone="purple"}
A **local minimum** is a point whose value is no greater than values at nearby points.
:::
```

Result:

:::callout {title="Definition" tone="purple"}
A **local minimum** is a point whose value is no greater than values at nearby points.
:::

Available tones are `neutral`, `blue`, `green`, `amber`, `red`, and `purple`.

Source:

```md
:::callout {title="Exercise" tone="blue"}
Why can a local minimum differ from a global minimum?
:::

:::callout {title="Warning" tone="red"}
Do not infer global behavior from local information alone.
:::
```

Result:

:::callout {title="Exercise" tone="blue"}
Why can a local minimum differ from a global minimum?
:::

:::callout {title="Warning" tone="red"}
Do not infer global behavior from local information alone.
:::

The title is optional for both static and collapsible callouts.

Source:

```md
:::callout
This untitled callout is always visible.
:::

:::callout {tone="neutral" collapse="closed"}
This untitled callout starts closed.
:::
```

Result:

:::callout
This untitled callout is always visible.
:::

:::callout {tone="neutral" collapse="closed"}
This untitled callout starts closed.
:::

Add `collapse="closed"` to start closed. Use `collapse="open"` to start open while allowing the learner to close it.

Source:

```md
:::callout {title="Hint" tone="amber" collapse="closed"}
Compare which points each definition quantifies over.
:::

:::callout {title="Worked solution" tone="green" collapse="open"}
A local minimum compares a point with nearby points. A global minimum compares it with every point in the domain.
:::
```

Result:

:::callout {title="Hint" tone="amber" collapse="closed"}
Compare which points each definition quantifies over.
:::

:::callout {title="Worked solution" tone="green" collapse="open"}
A local minimum compares a point with nearby points. A global minimum compares it with every point in the domain.
:::

\## Nesting

Shared directives can be nested. Give an outer block more colons than its inner block.

This callout contains a hidden section.

Source:

```md
::::callout {title="Exercise with optional help" tone="blue"}
Sketch a non-convex function.

:::hide
Try a polynomial with more than one valley. :note[The valleys correspond to local minima.]
:::
::::
```

Result:

::::callout {title="Exercise with optional help" tone="blue"}
Sketch a non-convex function.

:::hide
Try a polynomial with more than one valley. :note[The valleys correspond to local minima.]
:::
::::

A callout can contain another always-visible callout.

Source:

```md
::::callout {title="Outer exercise" tone="blue"}
Find all local minima of your example function.

:::callout {title="Reminder" tone="purple"}
A local minimum only compares nearby values.
:::
::::
```

Result:

::::callout {title="Outer exercise" tone="blue"}
Find all local minima of your example function.

:::callout {title="Reminder" tone="purple"}
A local minimum only compares nearby values.
:::
::::

A callout can also contain a collapsible callout.

Source:

```md
::::callout {title="Exercise with a nested hint" tone="blue"}
Explain why your chosen point is a local minimum.

:::callout {title="Optional hint" tone="amber" collapse="closed"}
State which neighbourhood you are comparing.
:::
::::
```

Result:

::::callout {title="Exercise with a nested hint" tone="blue"}
Explain why your chosen point is a local minimum.

:::callout {title="Optional hint" tone="amber" collapse="closed"}
State which neighbourhood you are comparing.
:::
::::

[^author-note]: This footnote uses standard Markdown footnote syntax.
