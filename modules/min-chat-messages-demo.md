---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-chat-messages-demo
title: Interaction requirements demo
---

%% This module explains interaction requirements: how to require chatting or answering before a learner can mark a page complete.

The defaults:
- {--{"author":"Elias's AI","timestamp":1783441550372}@@A `#### Chat`--}{++{"author":"Elias's AI","timestamp":1783441550372}@@Chatting++} never blocks completion. Learners can read the page and move on without sending {--{"author":"Elias's AI","timestamp":1783441550372}@@anything.--}{++{"author":"Elias's AI","timestamp":1783441550372}@@anything to the tutor.++}
- A `#### Question` must be answered once before the page can be completed, and gets a feedback conversation on the answer (`feedback::` defaults to true; set `feedback:: false` to turn that off).

The fields:
- On a {--{"author":"Elias's AI","timestamp":1783441550372}@@`#### Chat`, `min-chat-messages:: 2`--}{++{"author":"Elias's AI","timestamp":1783441550372}@@lens, `min_chat_messages` (YAML frontmatter on lens files, `min_chat_messages::` on inline lenses)++} means the learner must send at least {--{"author":"Elias's AI","timestamp":1783441550372}@@2--}{++{"author":"Elias's AI","timestamp":1783441550372}@@that many++} messages {--{"author":"Elias's AI","timestamp":1783441550372}@@in--}{++{"author":"Elias's AI","timestamp":1783441550372}@@to the Lens Tutor while on++} that {--{"author":"Elias's AI","timestamp":1783441550372}@@chat--}{++{"author":"Elias's AI","timestamp":1783441550372}@@lens++} before "Mark section complete" works. {--{"author":"Elias's AI","timestamp":1783441550372}@@Each chat counts its own messages — two chats on one page can have separate requirements.
- On--}{++{"author":"Elias's AI","timestamp":1783441550372}@@Every message counts, wherever it is typed: a chat box on the page,++} a{--{"author":"Elias's AI","timestamp":1783441550372}@@ `#### Question`, `min-chat-messages:: 2` means one completed answer plus 2 follow-up messages in the --}{++{"author":"Elias's AI","timestamp":1783441550372}@@ ++}question's feedback {--{"author":"Elias's AI","timestamp":1783441550372}@@conversation. Needs feedback enabled — combining it with `feedback:: false`--}{++{"author":"Elias's AI","timestamp":1783441550372}@@conversation, or the sidebar directly. The default++} is {--{"author":"Elias's AI","timestamp":1783441550372}@@a validator error.--}{++{"author":"Elias's AI","timestamp":1783441550372}@@0.++}
- `optional:: true` on a question makes answering it optional.
- Whole lenses marked `optional:: true` never block completion.{++{"author":"Elias's AI","timestamp":1783441550372}@@
- Segment-level `min-chat-messages::` (on a `#### Chat` or `#### Question`) is retired and ignored — the per-lens field above replaced it.++}

What learners see: while something is missing, "Mark section complete" is grayed out with a "To finish this page:" bullet list under it ("Send 2 messages {--{"author":"Elias's AI","timestamp":1783441550372}@@in--}{++{"author":"Elias's AI","timestamp":1783441550372}@@to++} the {--{"author":"Elias's AI","timestamp":1783441550372}@@chat",--}{++{"author":"Elias's AI","timestamp":1783441550372}@@Lens Tutor",++} "Answer question 2"). The named {--{"author":"Elias's AI","timestamp":1783441550372}@@chat or question--}{++{"author":"Elias's AI","timestamp":1783441550372}@@item++} in each bullet is a link that scrolls to it, and the list updates live as they make progress.

The five lenses below demonstrate each case. Preview the module and try them. %%

# Lens: {--{"author":"Elias's AI","timestamp":1783441563283}@@Chat--}{++{"author":"Elias's AI","timestamp":1783441563283}@@Lens++} with a 2-message minimum
id:: 593ceb17-ebd3-4c31-b250-3229b758ffc6{++{"author":"Elias's AI","timestamp":1783441563283}@@
min_chat_messages:: 2++}

#### Text
content::
This {--{"author":"Elias's AI","timestamp":1783441563283}@@page's chat--}{++{"author":"Elias's AI","timestamp":1783441563283}@@lens++} has {--{"author":"Elias's AI","timestamp":1783441563283}@@`min-chat-messages::--}{++{"author":"Elias's AI","timestamp":1783441563283}@@`min_chat_messages::++} 2`. Until you have sent two {--{"author":"Elias's AI","timestamp":1783441563283}@@messages,--}{++{"author":"Elias's AI","timestamp":1783441563283}@@messages to the Lens Tutor,++} "Mark section complete" stays grayed out and the bullet list under it says how many messages are still {--{"author":"Elias's AI","timestamp":1783441563283}@@needed — click "the chat" in--}{++{"author":"Elias's AI","timestamp":1783441563283}@@needed. Type into the chat box below or into++} the {--{"author":"Elias's AI","timestamp":1783441563283}@@bullet to jump here.--}{++{"author":"Elias's AI","timestamp":1783441563283}@@sidebar — both count.++}

#### Chat{--{"author":"Elias's AI","timestamp":1783441563283}@@
min-chat-messages:: 2--}
instructions::
Chat casually with the learner about whatever they bring up; keep replies short.

# Lens: Question with the default requirement
id:: eeb40ecf-e7e1-4536-8bda-a5cf286439d7

#### Text
content::
This page has a plain question with no extra fields. Questions require one completed answer by default (and get a feedback conversation, since `feedback::` defaults to true). Until you answer it you can't mark this lens as completed.

#### Question
content:: What is your favorite color, and why?

# Lens: Question {--{"author":"Elias's AI","timestamp":1783441578145}@@with feedback replies--}{++{"author":"Elias's AI","timestamp":1783441578145}@@plus a message minimum++}
id:: 43d2334e-990d-43be-98e2-aa7ff046cb16{++{"author":"Elias's AI","timestamp":1783441578145}@@
min_chat_messages:: 2++}

#### Text
content::
This {++{"author":"Elias's AI","timestamp":1783441578145}@@lens combines a required ++}question {--{"author":"Elias's AI","timestamp":1783441578145}@@has `min-chat-messages:: 2`: after answering, the learner--}{++{"author":"Elias's AI","timestamp":1783441578145}@@with `min_chat_messages:: 2`. The two requirements are independent: you++} must {--{"author":"Elias's AI","timestamp":1783441578145}@@also send at least--}{++{"author":"Elias's AI","timestamp":1783441578145}@@answer the question AND send++} 2 messages {--{"author":"Elias's AI","timestamp":1783441578145}@@in--}{++{"author":"Elias's AI","timestamp":1783441578145}@@to++} the {--{"author":"Elias's AI","timestamp":1783441578145}@@tutor's feedback conversation. Answer it, then look under the grayed-out button:--}{++{"author":"Elias's AI","timestamp":1783441578145}@@tutor. Replies you type in the question's feedback conversation count toward++} the {--{"author":"Elias's AI","timestamp":1783441578145}@@bullet asks for the remaining messages ("Send 2 more messages about your answer") until you have sent--}{++{"author":"Elias's AI","timestamp":1783441578145}@@message minimum (the auto-sent feedback request itself does not), so answering and then discussing the feedback satisfies++} both.

#### Question{--{"author":"Elias's AI","timestamp":1783441578145}@@
min-chat-messages:: 2--}
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
This {--{"author":"Elias's AI","timestamp":1783441589297}@@chat--}{++{"author":"Elias's AI","timestamp":1783441589297}@@lens++} has no {--{"author":"Elias's AI","timestamp":1783441589297}@@`min-chat-messages`,--}{++{"author":"Elias's AI","timestamp":1783441589297}@@`min_chat_messages`,++} so it shows the default behavior: "Mark section complete" works immediately, even without sending anything.

#### Chat
instructions::
Chat casually with the learner if they say anything; keep replies short.
