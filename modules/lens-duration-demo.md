---
id: 07e98d8a-c0d8-410f-99f6-3bd1fa6dff23
slug: lens-duration-demo
title: Lens duration demo
---

%% State a lens's expected time in its metadata (frontmatter or `field::` on an inline lens): prefer `reading_minutes` + `tutor_minutes` (content time + AI time, displayed split; either alone works, `tutor_minutes: 0` means no tutor time), or one `duration_minutes` total, never both. Authored values replace the platform's word-count estimate wherever time shows; without them the estimate applies, so set them on nearly every lens and re-estimate when you change one. The lens below demonstrates the split form. %%

# Lens: Authored lens duration
id:: 3fad77ed-c6a2-4b11-a137-e56a1bb350da
tldr:: This lens sets reading_minutes:: 4 and tutor_minutes:: 6, so its time badge shows "4 min + 6 min tutor" instead of the word-count estimate.
summary_for_tutor:: Demo lens with reading_minutes:: 4 and tutor_minutes:: 6, showing that authored values replace the platform's computed time estimate. A Chat segment stands in for the declared tutor time.
reading_minutes:: 4
tutor_minutes:: 6

#### Text
content::
This lens has `reading_minutes:: 4` and `tutor_minutes:: 6`, so its badge shows "4 min + 6 min tutor" even though the text would compute to under a minute. A single `duration_minutes:: 10` would show one plain total instead, and with no fields the platform falls back to its computed estimate.

#### Chat
instructions::
The learner is looking at a demo of authored lens durations (reading_minutes, tutor_minutes, duration_minutes). Answer questions about how they work; keep replies short.
