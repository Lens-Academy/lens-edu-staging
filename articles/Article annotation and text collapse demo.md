---
title: "Article {--{"author":"Elias's AI","timestamp":1786974685977}@@annotation and text hiding--}{++{"author":"Elias's AI","timestamp":1786974685977}@@presentation++} demo"
author: Lens Academy
published: 2026-06-16
source_url: https://editor.lensacademy.org/24abc9c0/Lens-Edu/articles/Article-annotation-and-text-collapse-demo.md
---

%%
Add discussion note here:

...

%%

This {++{"author":"Elias's AI","timestamp":1786974688772}@@short ++}article {--{"author":"Elias's AI","timestamp":1786974688772}@@demos Lens article annotations, hidden text, and general course callouts.--}{++{"author":"Elias's AI","timestamp":1786974688772}@@exists to demonstrate presentation added around article segments.++}

## {--{"author":"Elias's AI","timestamp":1786974675555}@@General callouts

Use one `callout` directive for exercises, definitions, remarks, warnings, hints, solutions, and other highlighted course content. The title supplies the course-specific name. The tone controls its visual treatment.--}{++{"author":"Elias's AI","timestamp":1786974675555}@@What this article demonstrates++}

{--{"author":"Elias's AI","timestamp":1786974675555}@@```md
:::callout {title="Definition" tone="purple"}
Callout content supports normal--}{++{"author":"Elias's AI","timestamp":1786974675555}@@This body is deliberately ordinary++} Markdown.{--{"author":"Elias's AI","timestamp":1786974675555}@@
:::
```

:::callout {title="Definition" tone="purple"}
A **local minimum** is --}{++{"author":"Elias's AI","timestamp":1786974675555}@@ When embedded in ++}a{--{"author":"Elias's AI","timestamp":1786974675555}@@ point whose value is no greater than--}{++{"author":"Elias's AI","timestamp":1786974675555}@@ Lens,++} the{--{"author":"Elias's AI","timestamp":1786974675555}@@ values at nearby points.
:::

Available tones are `neutral`, `blue`, `green`, `amber`, `red`, and `purple`.

:::callout {title="Exercise" tone="blue"}
Why can a local minimum differ from a global minimum?
:::

:::callout {title="Remark" tone="amber"}
The title is free text. `Remark` has no special --}{++{"author":"Elias's AI","timestamp":1786974675555}@@ ++}platform{--{"author":"Elias's AI","timestamp":1786974675555}@@ meaning.
:::

:::callout {title="Success condition" tone="green"}
You can explain the distinction without assuming every local minimum is global.
:::

:::callout {title="Warning" tone="red"}
Do not infer global behavior from local information alone.
:::

:::callout {title="Optional context" tone="neutral"}
A neutral callout --}{++{"author":"Elias's AI","timestamp":1786974675555}@@ ++}adds {--{"author":"Elias's AI","timestamp":1786974675555}@@structure without strong semantic emphasis.
:::--}{++{"author":"Elias's AI","timestamp":1786974675555}@@article-specific presentation around it:++}

{--{"author":"Elias's AI","timestamp":1786974675555}@@`title` is optional for every callout: static, closed, or open. If you do not need any attributes, use bare `:::callout`:

```md--}{++{"author":"Elias's AI","timestamp":1786974675555}@@- source attribution with author and publication date++}
{--{"author":"Elias's AI","timestamp":1786974675555}@@:::callout
This static callout has no title.
:::
```

:::callout
This static callout has no title. It still provides --}{++{"author":"Elias's AI","timestamp":1786974675555}@@- ++}a{--{"author":"Elias's AI","timestamp":1786974675555}@@ subtle visual grouping.
:::

### Collapsible callouts

Add `collapse="closed"` --}{++{"author":"Elias's AI","timestamp":1786974675555}@@ link ++}to {--{"author":"Elias's AI","timestamp":1786974675555}@@start closed:

```md
:::callout {title="Hint" tone="amber" collapse="closed"}
Start with --}the {--{"author":"Elias's AI","timestamp":1786974675555}@@definitions.
:::
```

:::callout {title="Hint" tone="amber" collapse="closed"}--}{++{"author":"Elias's AI","timestamp":1786974675555}@@original source++}
{--{"author":"Elias's AI","timestamp":1786974675555}@@Start by comparing which other points each definition quantifies over.--}{++{"author":"Elias's AI","timestamp":1786974675555}@@- article typography++}
{--{"author":"Elias's AI","timestamp":1786974675555}@@:::

Use `collapse="open"` when learners should see the content initially but may close it:

:::callout {title="Worked solution" tone="green" collapse="open"}--}{++{"author":"Elias's AI","timestamp":1786974675555}@@- excerpt boundaries and controls++}
{--{"author":"Elias's AI","timestamp":1786974675555}@@A local minimum only compares a point with nearby points. A global minimum compares it with every point in the domain.
:::--}{++{"author":"Elias's AI","timestamp":1786974675555}@@- article media treatment++}

{--{"author":"Elias's AI","timestamp":1786974675555}@@When a closed or open callout has no title,--}{++{"author":"Elias's AI","timestamp":1786974675555}@@General authored-content features such as hidden text,++} Lens{--{"author":"Elias's AI","timestamp":1786974675555}@@ supplies a small `Show more` control:

:::callout {tone="neutral" collapse="closed"}
This is an untitled closed callout.
:::

:::callout {tone="neutral" collapse="open"}
This is an untitled open callout.
:::

Omit `collapse` for a callout that is always visible.

### Nested callouts --}{++{"author":"Elias's AI","timestamp":1786974675555}@@ notes, footnotes, callouts, ++}and{--{"author":"Elias's AI","timestamp":1786974675555}@@ hidden sections

Callouts can contain inline hidden text:

:::callout {title="Exercise with optional help" tone="blue"}
Give an example of a function with multiple local minima.

If you need help, reveal this :hide[Try sketching a non-convex polynomial with more than one valley.]
:::

For one block inside another, give --}{++{"author":"Elias's AI","timestamp":1786974675555}@@ math are demonstrated in ++}the {--{"author":"Elias's AI","timestamp":1786974675555}@@outer block four colons and the inner block three. Here is a hidden block inside a callout:

```md
::::callout {title="Exercise" tone="blue"}
Sketch a non-convex function.

:::hide
Try a polynomial with more than one valley.
:::
::::
```

::::callout {title="Exercise" tone="blue"}
Sketch a non-convex function.

:::hide
Try a polynomial with more than one valley.
:::
::::

The same fence rule allows a callout inside a callout:

```md
::::callout {title="Exercise" tone="blue"}
Classify the point.

:::callout {title="Hint" tone="amber" collapse="closed"}
Compare it only with nearby points first.
:::
::::
```

::::callout {title="Exercise" tone="blue"}
Classify the point.

:::callout {title="Hint" tone="amber" collapse="closed"}
Compare it only with nearby points first.
:::
::::

[^1]: Hi. This is a footnote added by the author of the article.--}{++{"author":"Elias's AI","timestamp":1786974675555}@@separate **Authored content features demo** Lens.++}