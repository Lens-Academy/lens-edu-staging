---
id: 'df70ce9d-178c-4345-9043-88e346018056'
title: Nested callouts demo
tldr: Put whole segments inside a callout, nest callouts as deep as you like, and see the same box appear around a question inside an article.
summary_for_tutor: "Formatting-only demo of callouts as containers. It shows the heading form (#### Callout: Title ... #### End Callout) holding text, a nested collapsed hint, a question, an article excerpt and a widget, and explains that the same box appears around elements inside an article body. No learning assessment."
duration_minutes: 5
---

#### Text
content::
\## Callouts around segments

A callout can hold whole segments. Open it with `#### Callout: Title`, give it `tone::` and `collapse::` like any other segment, put any segments inside, and close it with `#### End Callout`. Callouts nest as deep as you like; every `#### End Callout` closes the innermost open one. The title is optional, and so are both fields. `collapse:: open` makes a box foldable and shows it open; `collapse:: closed` makes it foldable and shows it closed.

Source:

```md
#### Callout: Exercise
tone:: blue
collapse:: open

#### Text
content:: Read the hint only if you need it.

#### Callout: Hint
tone:: amber
collapse:: closed

#### Text
content:: Think about who profits from hiding.

#### End Callout

#### Question: Open
id:: 1ed4f9b8-b455-4a94-9142-72ad0a2df836
content:: Which actor has the strongest incentive to hide?
optional:: true

#### End Callout
```

Result:

#### Callout: Exercise
tone:: blue
collapse:: open

#### Text
content:: Read the hint only if you need it.

#### Callout: Hint
tone:: amber
collapse:: closed

#### Text
content:: Think about who profits from hiding.

#### End Callout

#### Question: Open
id:: 1ed4f9b8-b455-4a94-9142-72ad0a2df836
content:: Which actor has the strongest incentive to hide?
optional:: true

#### End Callout

#### Text
content::
\## Five folded boxes deep

Five closed callouts inside each other, with a question at the bottom. Every `#### End Callout` closes the innermost open box, so the chain ends with five closers:

#### Callout: Level 1
tone:: blue
collapse:: closed

#### Text
content:: First level. Open the next box.

#### Callout: Level 2
tone:: green
collapse:: closed

#### Text
content:: Second level.

#### Callout: Level 3
tone:: amber
collapse:: closed

#### Text
content:: Third level.

#### Callout: Level 4
tone:: purple
collapse:: closed

#### Text
content:: Fourth level.

#### Callout: Level 5
tone:: red
collapse:: closed

#### Question: Open
id:: 88032ef8-bc1d-435f-8ac2-9fef7dfa3138
content:: You made it to the fifth box. What would you put this deep in a real lens?
optional:: true

#### End Callout

#### End Callout

#### End Callout

#### End Callout

#### End Callout

#### Text
content::
\## Any segment goes inside

Article excerpts, videos, widgets, chats and roleplays sit inside a callout the same way. This box holds an article excerpt followed by a widget:

#### Callout: Read, then try
tone:: green

#### Article
source:: [[../articles/Article annotation and text collapse demo]]
from:: "This short article exists"
to:: "article media treatment"

#### Widget
source:: [[../widgets/ai-2040-deal-timeline]]

#### End Callout

#### Text
content::
\## Long boxes keep their title on screen

While you scroll through a long box, its title row stays at the top of the screen until the box ends. On a foldable box that row holds the fold button, so you can close the box from anywhere inside it. Closing it from there scrolls the page back to the closed box. A box inside a box pins its title just below the title of the box around it, and an omitted part of an article pins its `[...]` bar below both.

#### Callout: Outer box
tone:: blue
collapse:: open

#### Text
content::
This is the outer box. Scroll down slowly and watch the row that says "Outer box". It stays at the top of the screen while any part of this box is on screen.

The text in this box is only here to make the box long. A real lens would put an exercise here, or a reading with its questions, or a worked example that takes more than one screen.

When the end of the box reaches the top of the screen, the title row leaves with it. It never covers the text that comes after the box.

::::callout{title="Inner box" tone="green" collapse="open"}
This box sits inside the outer box. Its title row pins just below the outer title, so both stay readable while you scroll through it.

Close this inner box from its pinned row to see the page scroll back to where the box starts.

:::hide
This text was hidden behind a `[...]` bar. While it is open, the bar stays below the two titles above it.

:::callout{title="Box inside the hidden text" tone="amber"}
A third box, inside the hidden text, inside the inner box, inside the outer box. Its title has no fold button, and it still stays on screen below the other three rows while you read this box.

It works the same way at any depth. Each row pins below the rows of the boxes it sits in, and each row leaves together with the end of its own box.

This last paragraph gives the box enough length to scroll through.
:::

The hidden text ends here.
:::

The inner box ends after this paragraph.
::::

Back in the outer box. The inner title has left the screen with the end of the inner box, and the outer title is still pinned.

The outer box ends after this paragraph.

#### End Callout

#### Text
content::
\## Callouts inside articles

Inside an article body, `:::callout` keeps its directive form. A callout that holds only prose stays plain markdown. A callout that holds an element (a `::video` import, a `![[../widgets/name]]` embed, or a `:::question` block) is drawn as a box around the whole element, and the box follows the excerpt into every lens that embeds it. The **Article presentation demo** lens shows a question inside a callout inside an article.

A `:::callout` inside a `content::` field also keeps working. Use it when the box holds only text; use `#### Callout:` when it should hold segments.

#### Chat
instructions:: The learner has just seen a formatting demo of callouts as containers. If they ask, explain when to box segments (exercises with hints, optional side quests, grouped checks) and when plain prose callouts are enough. Keep it short.
