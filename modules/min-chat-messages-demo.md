---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-chat-messages-demo
title: Interaction requirements demo
---

%% This module explains interaction requirements: how to require chatting or answering before a learner can mark a page complete.

The defaults:
- Chat never blocks completion — a learner can move on without messaging the tutor.
- A `#### Question` must be answered once before completion, and opens a feedback conversation on the answer (`feedback::` defaults to true; set `feedback:: false` to turn it off).

The fields:
- `min_chat_messages` (lens frontmatter, or `min_chat_messages::` on an inline lens; default 0): the learner must send at least this many messages to the Lens Tutor on that lens before "Mark section complete" works. Every message counts — page chat box, a question's feedback conversation, or the sidebar — except the auto-sent feedback request itself.
- `optional:: true` makes a question skippable; on a whole lens, that lens never blocks completion.


What learners see: while a requirement is unmet, "Mark section complete" is grayed out above a live "To finish this page:" checklist (e.g. "Send 2 messages to the Lens Tutor", "Answer question 2") — each item links to the spot.

The five lenses below demonstrate each case. Preview the module and try them. %%

# Lens: Lens with a 2-message minimum
id:: 593ceb17-ebd3-4c31-b250-3229b758ffc6
{++{"author":"Elias's AI","timestamp":1783851515168}@@tldr:: What stops a learner from skipping past a discussion? This lens sets a two-message minimum, so "Mark section complete" stays locked until you have actually talked to the tutor.
summary_for_tutor:: Demo lens with min_chat_messages:: 2. A Text segment explains the requirement and a Chat segment invites casual conversation; completion is blocked until the learner sends two messages from any chat entry point.
++}min_chat_messages:: 2

#### Text
content::
This lens has `min_chat_messages:: 2`. Until you have sent two messages to the Lens Tutor, "Mark section complete" stays grayed out and the bullet list under it says how many messages are still needed. Type into the chat box below or into the sidebar — both count.

#### Chat
instructions::
Chat casually with the learner about whatever they bring up; keep replies short.

# Lens: Question with the default requirement
id:: eeb40ecf-e7e1-4536-8bda-a5cf286439d7
{++{"author":"Elias's AI","timestamp":1783851522143}@@tldr:: A plain question, no special settings, so what does it take to move on? By default you must answer once, and the tutor opens a short feedback chat on your reply.
summary_for_tutor:: Demo lens with a single Question and no extra fields, showing the default behavior: one completed answer is required before completion and a feedback conversation opens automatically (feedback:: defaults to true).
++}
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
