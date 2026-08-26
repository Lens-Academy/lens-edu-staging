---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-chat-messages-demo
title: Interaction requirements demo
---

%% This module explains interaction requirements: how to require chatting or answering before a learner can mark a page complete.

The defaults:
- Chat never blocks completion — a learner can move on without messaging the tutor.
- A {--{"author":"Elias's AI","timestamp":1787761733438}@@`#### Question` --}{++{"author":"Elias's AI","timestamp":1787761733438}@@response segment (`#### Question: Open`, `Rating`, `Choice`, `FillBlank`, `Ranking`) ++}must be answered once before {--{"author":"Elias's AI","timestamp":1787761733438}@@completion, and--}{++{"author":"Elias's AI","timestamp":1787761733438}@@completion. It++} opens a feedback conversation on the answer {--{"author":"Elias's AI","timestamp":1787761733438}@@(`feedback::` defaults to true; set `feedback:: false` to turn it off).--}{++{"author":"Elias's AI","timestamp":1787761733438}@@only if it has `feedback-instructions::`.++}

The fields:
- `min_chat_messages` (lens frontmatter, or `min_chat_messages::` on an inline lens; default 0): the learner must send at least this many messages to the Lens Tutor on that lens before "Mark section complete" works. Every message counts — page chat box, a question's feedback conversation, or the sidebar — except the auto-sent feedback request itself.
- `optional:: true` makes a question skippable; on a whole lens, that lens never blocks completion.


What learners see: while a requirement is unmet, "Mark section complete" is grayed out above a live "To finish this page:" checklist (e.g. "Send 2 messages to the Lens Tutor", "Answer question 2") — each item links to the spot.

The five lenses below demonstrate each case. Preview the module and try them. %%

# Lens: Lens with a 2-message minimum
id:: 593ceb17-ebd3-4c31-b250-3229b758ffc6
tldr:: What stops a learner from skipping past a discussion? This lens sets a two-message minimum, so "Mark section complete" stays locked until you have actually talked to the tutor.
summary_for_tutor:: Demo lens with min_chat_messages:: 2. A Text segment explains the requirement and a Chat segment invites casual conversation; completion is blocked until the learner sends two messages from any chat entry point.
min_chat_messages:: 2
duration_minutes:: 5

#### Text
content::
This lens has `min_chat_messages:: 2`. Until you have sent two messages to the Lens Tutor, "Mark section complete" stays grayed out and the bullet list under it says how many messages are still needed. Type into the chat box below or into the sidebar — both count.

#### Chat
instructions::
Chat casually with the learner about whatever they bring up; keep replies short.

# Lens: Question with the default requirement
id:: eeb40ecf-e7e1-4536-8bda-a5cf286439d7
tldr:: A plain {++{"author":"Elias's AI","timestamp":1787761739421}@@open ++}question, no special settings, so what does it take to move on? By default you must answer {--{"author":"Elias's AI","timestamp":1787761739421}@@once, and the tutor opens a short feedback chat on your reply.--}{++{"author":"Elias's AI","timestamp":1787761739421}@@once; there is no feedback chat unless the author asks for one.++}
summary_for_tutor:: Demo lens with a single {--{"author":"Elias's AI","timestamp":1787761739421}@@Question--}{++{"author":"Elias's AI","timestamp":1787761739421}@@Question: Open segment++} and no extra fields, showing the default behavior: one completed answer is required before completion and {--{"author":"Elias's AI","timestamp":1787761739421}@@a--}{++{"author":"Elias's AI","timestamp":1787761739421}@@no++} feedback conversation opens {--{"author":"Elias's AI","timestamp":1787761739421}@@automatically (feedback:: defaults to true).--}{++{"author":"Elias's AI","timestamp":1787761739421}@@because there are no feedback-instructions.++}
duration_minutes:: 5

#### Text
content::
This page has a plain {--{"author":"Elias's AI","timestamp":1787761739421}@@question--}{++{"author":"Elias's AI","timestamp":1787761739421}@@`Question: Open`++} with no extra fields. {--{"author":"Elias's AI","timestamp":1787761739421}@@Questions--}{++{"author":"Elias's AI","timestamp":1787761739421}@@Response segments++} require one completed answer by{--{"author":"Elias's AI","timestamp":1787761739421}@@ default (and get a feedback conversation, since `feedback::` defaults to true). --}{++{"author":"Elias's AI","timestamp":1787761739421}@@ default. ++}Until you answer it you can't mark this lens as completed.{++{"author":"Elias's AI","timestamp":1787761739421}@@ No feedback chat opens, because the segment has no `feedback-instructions::`.++}

#### {--{"author":"Elias's AI","timestamp":1787761739421}@@Question--}{++{"author":"Elias's AI","timestamp":1787761739421}@@Question: Open
id:: d607297d-bda6-437c-8a2e-51b40aae7e4b++}
content:: What is your favorite color, and why?

# Lens: Question plus a message minimum
id:: 43d2334e-990d-43be-98e2-aa7ff046cb16
tldr:: Two gates at once: answer the question and send two messages. This lens shows how a required question and a chat minimum stack independently, and how feedback replies count toward both.
summary_for_tutor:: Demo lens combining a required {--{"author":"Elias's AI","timestamp":1787761746294}@@Question--}{++{"author":"Elias's AI","timestamp":1787761746294}@@Question: Open++} with min_chat_messages:: 2. Explains that the two requirements are independent, that replies in the question's feedback conversation count toward the message minimum, and carries {--{"author":"Elias's AI","timestamp":1787761746294}@@assessment-instructions--}{++{"author":"Elias's AI","timestamp":1787761746294}@@feedback-instructions++} for a playful follow-up.
min_chat_messages:: 2
duration_minutes:: 5

#### Text
content::
This lens combines a required question with `min_chat_messages:: 2`. The two requirements are independent: you must answer the question AND send 2 messages to the tutor. {--{"author":"Elias's AI","timestamp":1787761746294}@@Replies you type in the question's--}{++{"author":"Elias's AI","timestamp":1787761746294}@@This question has `feedback-instructions::`, so a++} feedback conversation {++{"author":"Elias's AI","timestamp":1787761746294}@@opens on your answer. Replies you type there ++}count toward the message minimum (the auto-sent feedback request itself does not), so answering and then discussing the feedback satisfies both.

#### {--{"author":"Elias's AI","timestamp":1787761746294}@@Question--}{++{"author":"Elias's AI","timestamp":1787761746294}@@Question: Open++}
{++{"author":"Elias's AI","timestamp":1787761746294}@@id:: 006af336-57e3-44f3-bc3a-6cfc2cb541da
++}content:: Name a food you could eat every day. What makes it work for you?
{--{"author":"Elias's AI","timestamp":1787761746294}@@assessment-instructions::--}{++{"author":"Elias's AI","timestamp":1787761746294}@@feedback-instructions::++} Any sincere answer is fine; ask one playful follow-up question at a time.

# Lens: Skippable question
id:: 2c11c696-8fcb-4d2e-9725-f171c2e55c95
tldr:: How do you offer a reflection prompt without forcing anyone to answer it? Mark the question optional and it becomes skippable, so completion never waits on it.
summary_for_tutor:: Demo lens with a {--{"author":"Elias's AI","timestamp":1787761751529}@@Question--}{++{"author":"Elias's AI","timestamp":1787761751529}@@Question: Open++} marked optional:: true, overriding the default single-answer requirement so completion is never blocked. Illustrates the pattern for nice-to-have reflection prompts.
duration_minutes:: 2

#### Text
content::
This question has `optional:: true`, which overrides the default requirement of one answer and makes it skippable. "Mark section complete" works even without answering. Use this for nice-to-have reflection prompts that should not hold anyone up.

#### {--{"author":"Elias's AI","timestamp":1787761751529}@@Question--}{++{"author":"Elias's AI","timestamp":1787761751529}@@Question: Open
id:: 11444bd9-63d8-4b60-8680-cb20ecdc6d82++}
optional:: true
content:: Purely optional: is there anything from this module you want to note down for later?

# Lens: Control chat without a minimum
id:: d3d75f10-d930-4fc1-a52c-fcfcc65f05a0
tldr:: The baseline case: a chat lens with no requirements, where "Mark section complete" works right away, even if you never say a word.
summary_for_tutor:: Control demo lens with no min_chat_messages, showing the default behavior where completion is available immediately. A Text segment states this and a Chat segment offers optional casual conversation.
duration_minutes:: 2

#### Text
content::
This lens has no `min_chat_messages`, so it shows the default behavior: "Mark section complete" works immediately, even without sending anything.

#### Chat
instructions::
Chat casually with the learner if they say anything; keep replies short.
