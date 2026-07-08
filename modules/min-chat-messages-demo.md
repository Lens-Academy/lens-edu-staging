---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-chat-messages-demo
title: Interaction requirements demo
---

%% This module explains interaction requirements: how to require chatting or answering before a learner can mark a page complete.

The defaults:
- {--{"author":"Elias's AI","timestamp":1783544218689}@@Chatting--}{++{"author":"Elias's AI","timestamp":1783544218689}@@Chat++} never blocks {--{"author":"Elias's AI","timestamp":1783544218689}@@completion. Learners can read the page and--}{++{"author":"Elias's AI","timestamp":1783544218689}@@completion — a learner can++} move on without {--{"author":"Elias's AI","timestamp":1783544218689}@@sending anything to --}{++{"author":"Elias's AI","timestamp":1783544218689}@@messaging ++}the tutor.
- A `#### Question` must be answered once before {--{"author":"Elias's AI","timestamp":1783544218689}@@the page can be completed,--}{++{"author":"Elias's AI","timestamp":1783544218689}@@completion,++} and {--{"author":"Elias's AI","timestamp":1783544218689}@@gets--}{++{"author":"Elias's AI","timestamp":1783544218689}@@opens++} a feedback conversation on the answer (`feedback::` defaults to true; set `feedback:: false` to turn {--{"author":"Elias's AI","timestamp":1783544218689}@@that--}{++{"author":"Elias's AI","timestamp":1783544218689}@@it++} off).

The fields:
- {--{"author":"Elias's AI","timestamp":1783544221912}@@On a lens, --}`min_chat_messages` {--{"author":"Elias's AI","timestamp":1783544221912}@@(YAML frontmatter on lens files, --}{++{"author":"Elias's AI","timestamp":1783544221912}@@(lens frontmatter, or ++}`min_chat_messages::` on {++{"author":"Elias's AI","timestamp":1783544221912}@@an ++}inline {--{"author":"Elias's AI","timestamp":1783544221912}@@lenses) means--}{++{"author":"Elias's AI","timestamp":1783544221912}@@lens; default 0):++} the learner must send at least {--{"author":"Elias's AI","timestamp":1783544221912}@@that--}{++{"author":"Elias's AI","timestamp":1783544221912}@@this++} many messages to the Lens Tutor{--{"author":"Elias's AI","timestamp":1783544221912}@@ while--} on that lens before "Mark section complete" works. Every message {--{"author":"Elias's AI","timestamp":1783544221912}@@counts, wherever it is typed: a --}{++{"author":"Elias's AI","timestamp":1783544221912}@@counts — page ++}chat {--{"author":"Elias's AI","timestamp":1783544221912}@@box on the page, --}{++{"author":"Elias's AI","timestamp":1783544221912}@@box, ++}a question's feedback conversation, or the sidebar {--{"author":"Elias's AI","timestamp":1783544221912}@@directly. The default is 0.--}{++{"author":"Elias's AI","timestamp":1783544221912}@@— except the auto-sent feedback request itself.++}
- `optional:: true` {--{"author":"Elias's AI","timestamp":1783544221912}@@on--}{++{"author":"Elias's AI","timestamp":1783544221912}@@makes++} a question {--{"author":"Elias's AI","timestamp":1783544221912}@@makes answering it optional.
- Whole lenses marked `optional:: true`--}{++{"author":"Elias's AI","timestamp":1783544221912}@@skippable; on a whole lens, that lens++} never {--{"author":"Elias's AI","timestamp":1783544221912}@@block--}{++{"author":"Elias's AI","timestamp":1783544221912}@@blocks++} completion.


What learners see: while {--{"author":"Elias's AI","timestamp":1783544224014}@@something--}{++{"author":"Elias's AI","timestamp":1783544224014}@@a requirement++} is {--{"author":"Elias's AI","timestamp":1783544224014}@@missing,--}{++{"author":"Elias's AI","timestamp":1783544224014}@@unmet,++} "Mark section complete" is grayed out {--{"author":"Elias's AI","timestamp":1783544224014}@@with--}{++{"author":"Elias's AI","timestamp":1783544224014}@@above++} a {++{"author":"Elias's AI","timestamp":1783544224014}@@live ++}"To finish this page:" {--{"author":"Elias's AI","timestamp":1783544224014}@@bullet list under it ("Send--}{++{"author":"Elias's AI","timestamp":1783544224014}@@checklist (e.g. "Send++} 2 messages to the Lens Tutor", "Answer question {--{"author":"Elias's AI","timestamp":1783544224014}@@2"). The named--}{++{"author":"Elias's AI","timestamp":1783544224014}@@2") — each++} item {--{"author":"Elias's AI","timestamp":1783544224014}@@in each bullet is a link that scrolls --}{++{"author":"Elias's AI","timestamp":1783544224014}@@links ++}to{--{"author":"Elias's AI","timestamp":1783544224014}@@ it, and--} the{--{"author":"Elias's AI","timestamp":1783544224014}@@ list updates live as they make progress.--}{++{"author":"Elias's AI","timestamp":1783544224014}@@ spot.++}

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
