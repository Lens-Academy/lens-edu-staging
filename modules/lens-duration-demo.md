---
id: 07e98d8a-c0d8-410f-99f6-3bd1fa6dff23
slug: lens-duration-demo
title: Lens duration demo
---

%% This module explains authored lens durations: how to state how long a lens takes instead of relying on the platform's estimate.

The default: the platform estimates each lens's time badge from its content (word count / 200 wpm + video length, plus tutor time when the lens has chat, question, or roleplay segments) and sums the badges into the module total.

The fields (lens frontmatter, or `field::` on an inline lens):
- `reading_minutes` + `tutor_minutes`: the author's estimate split into content time (reading, watching, on-page work) and AI-tutor time (chats, question feedback, roleplays). Preferred, because the platform displays the two parts separately. Either may stand alone; the missing part stays estimated. `tutor_minutes: 0` states there is no real tutor work.
- `duration_minutes`: the author's one-number total, shown as a plain badge. Use when a split would be false precision. Never combine it with the split fields (validation error).

When set, authored values replace the computed estimate everywhere the time shows (course page, module page, sidebar, resource cards). When absent, the computed estimate applies. Whole minutes, up to 600; an invalid value is a validation error and the computed estimate stays in effect.

Set an estimate on nearly every lens, and re-estimate whenever you change a lens. The computed fallback badly under-counts lenses whose work lives outside the page text, such as external readings or exercises.

The three lenses below show the total form, the split form, and the fallback. %%

# Lens: Lens with an authored duration
id:: c025bf28-ac92-4909-80f5-f8837abc663f
tldr:: Who knows better how long a page takes, the author or a word counter? This lens sets duration_minutes:: 5, so its time badge says 5 min no matter how short the text is.
summary_for_tutor:: Demo lens with duration_minutes:: 5. A Text segment explains that the authored value replaces the platform's word-count estimate in every time badge, and a Chat segment is available for questions about the field.
duration_minutes:: 5

#### Text
content::
This lens has `duration_minutes:: 5`. Its time badge shows 5 min everywhere (course page, module page, sidebar), even though the text here would compute to about 1 min. Use the field to state the real time a lens takes: include reading, watching, and expected tutor conversation. For a lens stored in its own file, put `duration_minutes: 5` in the frontmatter instead.

#### Chat
instructions::
The learner is looking at a demo of the duration_minutes field. Answer questions about how authored durations work; keep replies short.

# Lens: Lens with a reading and tutor split
id:: 3fad77ed-c6a2-4b11-a137-e56a1bb350da
tldr:: One number hides where the time goes. This lens sets reading_minutes:: 4 and tutor_minutes:: 6, so its badge shows the two parts separately: 4 min of content plus 6 min with the tutor.
summary_for_tutor:: Demo lens with reading_minutes:: 4 and tutor_minutes:: 6. A Text segment explains the split fields and a Chat segment stands in for the tutor time the author declared.
reading_minutes:: 4
tutor_minutes:: 6

#### Text
content::
This lens has `reading_minutes:: 4` and `tutor_minutes:: 6`, so its badge shows "4 min + 6 min tutor" instead of one lump. Use the split when the platform should display content time and tutor time separately. Either field also works alone: the part you leave out stays estimated. Setting `tutor_minutes:: 0` states the lens has no real tutor work.

#### Chat
instructions::
The learner is looking at a demo of the reading_minutes and tutor_minutes split. Answer questions about how the split works; keep replies short.

# Lens: Control lens without an authored duration
id:: 6b327d0c-3fc8-47e7-b52b-e0d082f8b9ae
tldr:: What happens when the author says nothing? Without duration_minutes, the platform falls back to its computed estimate from word count, video length, and tutor time.
summary_for_tutor:: Control demo lens with no duration_minutes, showing the fallback behavior where the time badge comes from the platform's computed estimate. A Text segment states this and a Chat segment earns the 3-minute tutor floor so a badge actually shows.

#### Text
content::
This lens has no `duration_minutes`, so its badge shows the platform's computed estimate: word count at 200 words per minute, plus video length, plus tutor time when the lens has chat, question, or roleplay segments. Here the chat below earns the 3-minute tutor floor, so the badge says about 3 min. The fallback is fine for pages whose work is all on the page.

#### Chat
instructions::
The learner is looking at a demo of the computed time estimate. Answer questions about how the estimate is calculated; keep replies short.
