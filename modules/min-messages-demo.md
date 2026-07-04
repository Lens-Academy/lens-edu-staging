---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-messages-demo
title: Interaction requirements demo
---

%% This module explains interaction requirements: how to require chatting or answering before a learner can mark a page complete.

The defaults:
- A `#### Chat` never blocks completion. Learners can read the page and move on without sending anything.
- A `#### Question` must be answered once before the page can be completed, and gets a feedback conversation on the answer (`feedback::` defaults to true; set `feedback:: false` to turn that off).

The fields:
- On a `#### Chat`, `min-chat-messages:: 2` means the learner must send at least 2 messages in that chat before "Mark section complete" works. Each chat counts its own messages — two chats on one page can have separate requirements.
- On a `#### Question`, `min-chat-messages:: 2` means one completed answer plus 2 follow-up replies in the question's feedback conversation. Needs feedback enabled — combining it with `feedback:: false` is a validator error.
- `optional:: true` on a question makes answering it optional.
- Whole lenses marked `optional:: true` never block completion.

What learners see: while something is missing, "Mark section complete" is grayed out and concrete instructions are listed under it ("Send 2 messages in the chat", "Answer question 2"). Each line is a link that scrolls to the chat or question it names, and the list updates live as they make progress.

The five lenses below demonstrate each case. Preview the module and try them. %%

# Lens: Chat with a 2-message minimum
id:: 593ceb17-ebd3-4c31-b250-3229b758ffc6

#### Text
content::
This page's chat has `min-chat-messages:: 2`. Until you have sent two messages, "Mark section complete" stays grayed out and a line under it says how many messages are still needed — click the line to jump to the chat.

#### Chat
min-chat-messages:: 2
instructions::
Chat casually with the learner about whatever they bring up; keep replies short.

# Lens: Question with the default requirement
id:: eeb40ecf-e7e1-4536-8bda-a5cf286439d7

#### Text
content::
This page has a plain question with no extra fields. Questions require one completed answer by default (and get a feedback conversation, since `feedback::` defaults to true). Until you answer it you can't mark this lens as completed.

#### Question
content:: What is your favorite color, and why?

# Lens: Question with feedback replies
id:: 43d2334e-990d-43be-98e2-aa7ff046cb16

#### Text
content::
This question has `min-chat-messages:: 2`: This means that the user has two send at least 2 messages to the tutor after they repone answer plus two replies in the feedback conversation (feedback is on by default). Answer it, then look under the grayed-out button: it asks for the remaining replies until you have sent both.

#### Question
min-chat-messages:: 2
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
This chat has no `min-chat-messages`, so it shows the default behavior: "Mark section complete" works immediately, even without sending anything.

#### Chat
instructions::
Chat casually with the learner if they say anything; keep replies short.
