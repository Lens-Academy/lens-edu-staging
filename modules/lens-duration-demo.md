---
id: 07e98d8a-c0d8-410f-99f6-3bd1fa6dff23
slug: lens-duration-demo
title: Lens duration demo
---

%% State a lens's expected time in its metadata (frontmatter or `field::` on an inline lens): prefer `reading_minutes` + `tutor_minutes` (content time + AI time, displayed split; either alone works, `tutor_minutes: 0` means no tutor time), or one `duration_minutes` total, never both. Authored values replace the platform's word-count estimate wherever time {--{"author":"Elias's AI","timestamp":1787255196290}@@shows, --}{++{"author":"Elias's AI","timestamp":1787255196290}@@shows; without them the estimate applies, ++}so set them on nearly every lens and re-estimate when you change one. The {--{"author":"Elias's AI","timestamp":1787255196290}@@three lenses --}{++{"author":"Elias's AI","timestamp":1787255196290}@@lens ++}below{--{"author":"Elias's AI","timestamp":1787255196290}@@ show the total form,--}{++{"author":"Elias's AI","timestamp":1787255196290}@@ demonstrates++} the split{--{"author":"Elias's AI","timestamp":1787255196290}@@ form, and the fallback.--}{++{"author":"Elias's AI","timestamp":1787255196290}@@ form.++} %%

# Lens:{--{"author":"Elias's AI","timestamp":1787255196290}@@ Lens with an authored duration
id:: c025bf28-ac92-4909-80f5-f8837abc663f
tldr:: Who knows better how long a page takes, the author or a word counter? This--}{++{"author":"Elias's AI","timestamp":1787255196290}@@ Authored++} lens {--{"author":"Elias's AI","timestamp":1787255196290}@@sets duration_minutes:: 5, so its time badge says 5 min no matter how short the text is.
summary_for_tutor:: Demo lens with duration_minutes:: 5. A Text segment explains that the authored value replaces the platform's word-count estimate in every time badge, and a Chat segment is available for questions about the field.
duration_minutes:: 5

#### Text
content::
This lens has `duration_minutes:: 5`. Its time badge shows 5 min everywhere (course page, module page, sidebar), even though the text here would compute to about 1 min. Use the field to state the real time a lens takes: include reading, watching, and expected tutor conversation. For a lens stored in its own file, put `duration_minutes: 5` in the frontmatter instead.

#### Chat
instructions::
The learner is looking at a demo of the duration_minutes field. Answer questions about how authored durations work; keep replies short.

# Lens: Lens with a reading and tutor split--}{++{"author":"Elias's AI","timestamp":1787255196290}@@duration++}
id:: 3fad77ed-c6a2-4b11-a137-e56a1bb350da
tldr::{--{"author":"Elias's AI","timestamp":1787255196290}@@ One number hides where the time goes. --}{++{"author":"Elias's AI","timestamp":1787255196290}@@ ++}This lens sets reading_minutes:: 4 and tutor_minutes:: 6, so its {++{"author":"Elias's AI","timestamp":1787255196290}@@time ++}badge shows{--{"author":"Elias's AI","timestamp":1787255196290}@@ the two parts separately: 4--}{++{"author":"Elias's AI","timestamp":1787255196290}@@ "4 min + 6++} min {--{"author":"Elias's AI","timestamp":1787255196290}@@of content plus 6 min with the tutor.--}{++{"author":"Elias's AI","timestamp":1787255196290}@@tutor" instead of the word-count estimate.++}
summary_for_tutor:: Demo lens with reading_minutes:: 4 and tutor_minutes:: {--{"author":"Elias's AI","timestamp":1787255196290}@@6. A Text segment explains--}{++{"author":"Elias's AI","timestamp":1787255196290}@@6, showing that authored values replace++} the {--{"author":"Elias's AI","timestamp":1787255196290}@@split fields and a--}{++{"author":"Elias's AI","timestamp":1787255196290}@@platform's computed time estimate. A++} Chat segment stands in for the {++{"author":"Elias's AI","timestamp":1787255196290}@@declared ++}tutor{--{"author":"Elias's AI","timestamp":1787255196290}@@ time the author declared.--}{++{"author":"Elias's AI","timestamp":1787255196290}@@ time.++}
reading_minutes:: 4
tutor_minutes:: 6

#### Text
content::
This lens has `reading_minutes:: 4` and `tutor_minutes:: 6`, so its badge shows "4 min + 6 min tutor"{--{"author":"Elias's AI","timestamp":1787255196290}@@ instead of one lump. Use the split when--}{++{"author":"Elias's AI","timestamp":1787255196290}@@ even though++} the{--{"author":"Elias's AI","timestamp":1787255196290}@@ platform should display content time and tutor time separately. Either field also works alone: the part you leave out stays estimated. Setting `tutor_minutes:: 0` states the lens has--}{++{"author":"Elias's AI","timestamp":1787255196290}@@ text would compute to under a minute. A single `duration_minutes:: 10` would show one plain total instead, and with++} no{--{"author":"Elias's AI","timestamp":1787255196290}@@ real tutor work.

#### Chat
instructions::
The learner is looking at a demo of the reading_minutes and tutor_minutes split. Answer questions about how --}{++{"author":"Elias's AI","timestamp":1787255196290}@@ fields ++}the {--{"author":"Elias's AI","timestamp":1787255196290}@@split works; keep replies short.

# Lens: Control lens without an authored duration
id:: 6b327d0c-3fc8-47e7-b52b-e0d082f8b9ae
tldr:: What happens when the author says nothing? Without duration_minutes, the --}platform falls back to its{--{"author":"Elias's AI","timestamp":1787255196290}@@ computed estimate from word count, video length, and tutor time.
summary_for_tutor:: Control demo lens with no duration_minutes, showing the fallback behavior where the time badge comes from the platform's --}{++{"author":"Elias's AI","timestamp":1787255196290}@@ ++}computed estimate.{--{"author":"Elias's AI","timestamp":1787255196290}@@ A Text segment states this and a Chat segment earns the 3-minute tutor floor so a badge actually shows.

#### Text
content::
This lens has no `duration_minutes`, so its badge shows the platform's computed estimate: word count at 200 words per minute, plus video length, plus tutor time when the lens has chat, question, or roleplay segments. Here the chat below earns the 3-minute tutor floor, so the badge says about 3 min. The fallback is fine for pages whose work is all on the page.--}

#### Chat
instructions::
The learner is looking at a demo of {--{"author":"Elias's AI","timestamp":1787255196290}@@the computed time estimate. --}{++{"author":"Elias's AI","timestamp":1787255196290}@@authored lens durations (reading_minutes, tutor_minutes, duration_minutes). ++}Answer questions about how{--{"author":"Elias's AI","timestamp":1787255196290}@@ the estimate is calculated;--}{++{"author":"Elias's AI","timestamp":1787255196290}@@ they work;++} keep replies short.
