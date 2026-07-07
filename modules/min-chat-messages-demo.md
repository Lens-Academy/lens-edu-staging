---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-chat-messages-demo
title: Interaction requirements demo
---

%% This module explains interaction requirements: how to require chatting or answering before a learner can mark a page complete.

The defaults:
- Chatting never blocks completion. Learners can read the page and move on without sending anything to the tutor.
- A `#### Question` must be answered once before the page can be completed, and gets a feedback conversation on the answer (`feedback::` defaults to true; set `feedback:: false` to turn that off).

The fields:
- On a lens, `min_chat_messages` (YAML frontmatter on lens files, `min_chat_messages::` on inline lenses) means the learner must send at least that many messages to the Lens Tutor while on that lens before "Mark section complete" works. Every message counts, wherever it is typed: a chat box on the page, a question's feedback conversation, or the sidebar directly. The default is 0.
- `optional:: true` on a question makes answering it optional.
- Whole lenses marked `optional:: true` never block completion.


What learners see: while something is missing, "Mark section complete" is grayed out with a "To finish this page:" bullet list under it ("Send 2 messages to the Lens Tutor", "Answer question 2"). The named item in each bullet is a link that scrolls to it, and the list updates live as they make progress.

The five lenses below demonstrate each case. Preview the module and try them. %%

# Lens: Lens with a 2-message minimum
id:: 593ceb17-ebd3-4c31-b250-3229b758ffc6
min_chat_messages:: 2

#### Text
content::
This lens has `min_chat_messages:: 2`. Until you have sent two messages to the Lens Tutor, "Mark section complete" stays grayed out and the bullet list under it says how many messages are still needed. Type into the chat box below or into the sidebar — both count.

#### Chat
instructions::
Chat casually with the learner about whatever they bring up; keep replies short.

# Lens: Question with the default requirement
id:: eeb40ecf-e7e1-4536-8bda-a5cf286439d7

#### Text
content::
This page has a plain question with no extra fields. Questions require one completed answer by default (and get a feedback conversation, since `feedback::` defaults to true). Until you answer it you can't mark this lens as completed.

#### Question
content:: What is your favorite color, and why?

# Lens: Question plus a message minimum
id:: 43d2334e-990d-43be-98e2-aa7ff046cb16
min_chat_messages:: 2

#### Text
content::
This lens combines a required question with `min_chat_messages:: 2`. The two requirements are independent: you must answer the question AND send 2 messages to the tutor. Replies you type in the question's feedback conversation count toward the message minimum (the auto-sent feedback request itself does not), so answering and then discussing the feedback satisfies both.

#### Question
content:: Name a food you could eat every day. What makes it work for you?
assessment-instructions:: Any sincere answer is fine; ask one playful follow-up question at a time.

# Lens: Skippable question
id:: 2c11c696-8fcb-4d2e-9725-f171c2e55c95

#### Text
content::
This question has `optional:: true`, which overrides the default requirement of one answer and makes it skippable. "Mark section complete" works even without answering. Use this for nice-to-have reflection prompts that should not hold anyone up.

#### Question
optional:: true
content:: Purely optional: is there anything from this module you want to note down for later?

# Lens: Control chat without a minimum
id:: d3d75f10-d930-4fc1-a52c-fcfcc65f05a0

#### Text
content::
This lens has no `min_chat_messages`, so it shows the default behavior: "Mark section complete" works immediately, even without sending anything.

#### Chat
instructions::
Chat casually with the learner if they say anything; keep replies short.
