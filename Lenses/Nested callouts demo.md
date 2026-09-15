---
id: 'df70ce9d-178c-4345-9043-88e346018056'
title: Nested callouts demo
tldr: Put whole segments inside a callout, nest callouts as deep as you like, and see the same box appear around a question inside an article.
summary_for_tutor: "Formatting-only demo of callouts as containers. It shows the heading form (#### Callout: Title ... #### End Callout) holding text, a nested collapsed hint, a question, an article excerpt and a widget, and explains that the same box appears around elements inside an article body. No learning assessment."
duration_minutes: 5
tags: [wip]
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
\## Five levels deep

Every `#### End Callout` closes the innermost open box, so a chain of five nested callouts needs five closers at the end:

#### Callout: Level 1
tone:: blue

#### Text
content:: First level.

#### Callout: Level 2
tone:: green

#### Text
content:: Second level.

#### Callout: Level 3
tone:: amber

#### Text
content:: Third level.

#### Callout: Level 4
tone:: purple

#### Text
content:: Fourth level.

#### Callout: Level 5
tone:: red
collapse:: closed

#### Text
content:: Fifth level, folded away until you open it.

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
\## Callouts inside articles

Inside an article body, `:::callout` keeps its directive form. A callout that holds only prose stays plain markdown. A callout that holds an element (a `::video` import, a `![[../widgets/name]]` embed, or a `:::question` block) is drawn as a box around the whole element, and the box follows the excerpt into every lens that embeds it. The **Article presentation demo** lens shows a question inside a callout inside an article.

A `:::callout` inside a `content::` field also keeps working. Use it when the box holds only text; use `#### Callout:` when it should hold segments.

#### Chat
instructions:: The learner has just seen a formatting demo of callouts as containers. If they ask, explain when to box segments (exercises with hints, optional side quests, grouped checks) and when plain prose callouts are enough. Keep it short.
