---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-messages-demo
title: Interaction requirements demo
---

%% This module explains interaction requirements: how to require chatting or answering before a learner can mark a page complete.

The defaults:
- A `#### Chat` never blocks completion. Learners can read the page and move on without sending anything.
- A `#### Question` must be answered once before the page can be {--{"author":"Elias's AI","timestamp":1783153215129}@@completed.

Add `min-messages::` --}{++{"author":"Elias's AI","timestamp":1783153215129}@@completed, and gets a feedback conversation on the answer (`feedback::` defaults ++}to {--{"author":"Elias's AI","timestamp":1783153215129}@@a segment--}{++{"author":"Elias's AI","timestamp":1783153215129}@@true; set `feedback:: false`++} to {--{"author":"Elias's AI","timestamp":1783153215129}@@change that:--}{++{"author":"Elias's AI","timestamp":1783153215129}@@turn that off).

The fields:++}
- On a `#### Chat`, {--{"author":"Elias's AI","timestamp":1783153215129}@@`min-messages::--}{++{"author":"Elias's AI","timestamp":1783153215129}@@`min-chat-messages::++} 2` means the learner must send at least 2 messages in {--{"author":"Elias's AI","timestamp":1783153215129}@@this page's tutor--}{++{"author":"Elias's AI","timestamp":1783153215129}@@that++} chat before "Mark section complete" works. {--{"author":"Elias's AI","timestamp":1783153215129}@@All--}{++{"author":"Elias's AI","timestamp":1783153215129}@@Each chat counts its own++} messages {++{"author":"Elias's AI","timestamp":1783153215129}@@— two chats ++}on {--{"author":"Elias's AI","timestamp":1783153215129}@@the--}{++{"author":"Elias's AI","timestamp":1783153215129}@@one++} page{--{"author":"Elias's AI","timestamp":1783153215129}@@ count, wherever they were sent.--}{++{"author":"Elias's AI","timestamp":1783153215129}@@ can have separate requirements.++}
- On a `#### Question`, {--{"author":"Elias's AI","timestamp":1783153215129}@@`min-messages:: 3`--}{++{"author":"Elias's AI","timestamp":1783153215129}@@`min-chat-messages:: 2`++} means one completed answer plus 2 follow-up replies in the question's feedback conversation. {--{"author":"Elias's AI","timestamp":1783153215129}@@This only makes sense together--}{++{"author":"Elias's AI","timestamp":1783153215129}@@Needs feedback enabled — combining it++} with `feedback:: {--{"author":"Elias's AI","timestamp":1783153215129}@@true` (the validator warns you otherwise).--}{++{"author":"Elias's AI","timestamp":1783153215129}@@false` is a validator error.++}
- {--{"author":"Elias's AI","timestamp":1783153215129}@@`min-messages:: 0`--}{++{"author":"Elias's AI","timestamp":1783153215129}@@`optional:: true`++} on a question makes {++{"author":"Elias's AI","timestamp":1783153215129}@@answering ++}it {--{"author":"Elias's AI","timestamp":1783153215129}@@skippable.--}{++{"author":"Elias's AI","timestamp":1783153215129}@@optional.++}
- Whole lenses marked `optional:: true` never block completion.{--{"author":"Elias's AI","timestamp":1783153215129}@@ (`optional` is a lens-level field; on chat and question segments use `min-messages` instead.)--}

What learners see: {--{"author":"Elias's AI","timestamp":1783153215129}@@clicking--}{++{"author":"Elias's AI","timestamp":1783153215129}@@while something is missing,++} "Mark section complete" {--{"author":"Elias's AI","timestamp":1783153215129}@@too early rejects the click, scrolls to the first missing interaction, and shows a small pill explaining what is needed. The pill disappears as soon as they make progress and only comes back if they try to complete again too early.--}{++{"author":"Elias's AI","timestamp":1783153215129}@@is grayed out and concrete instructions are listed under it ("Send 2 messages in the chat", "Answer question 2"). Each line is a link that scrolls to the chat or question it names, and the list updates live as they make progress.++}

The five lenses below demonstrate each case. Preview the module and try them. %%

# Lens: Chat with a 2-message minimum
id:: 593ceb17-ebd3-4c31-b250-3229b758ffc6

#### Text
content::
This page's chat has {--{"author":"Elias's AI","timestamp":1783153225978}@@`min-messages::--}{++{"author":"Elias's AI","timestamp":1783153225978}@@`min-chat-messages::++} 2`. {--{"author":"Elias's AI","timestamp":1783153225978}@@Try clicking--}{++{"author":"Elias's AI","timestamp":1783153225978}@@Until you have sent two messages,++} "Mark section complete" {--{"author":"Elias's AI","timestamp":1783153225978}@@before sending two messages: the click is rejected and a pill above the chat input tells you how many messages are still needed.--}{++{"author":"Elias's AI","timestamp":1783153225978}@@stays grayed out and a line under it says how many messages are still needed — click the line to jump to the chat.++}

#### Chat
{--{"author":"Elias's AI","timestamp":1783153225978}@@min-messages::--}{++{"author":"Elias's AI","timestamp":1783153225978}@@min-chat-messages::++} 2
instructions::
Chat casually with the learner about whatever they bring up; keep replies short.

# Lens: Question with the default requirement
id:: eeb40ecf-e7e1-4536-8bda-a5cf286439d7

#### Text
content::
This page has a plain question with no extra fields. Questions require one completed answer by {--{"author":"Elias's AI","timestamp":1783153228776}@@default. Try completing the page without answering: a pill above the question asks you to answer it first.--}{++{"author":"Elias's AI","timestamp":1783153228776}@@default (and get a feedback conversation, since `feedback::` defaults to true). Until you answer, "Mark section complete" stays grayed out with "Answer the question" under it.++}

#### Question
content:: What is your favorite color, and why?

# Lens: Question with feedback replies
id:: 43d2334e-990d-43be-98e2-aa7ff046cb16

#### Text
content::
This question has {--{"author":"Elias's AI","timestamp":1783153230836}@@`feedback:: true` and `min-messages:: 3`: --}{++{"author":"Elias's AI","timestamp":1783153230836}@@`min-chat-messages:: 2`: ++}one answer plus two replies in the feedback {--{"author":"Elias's AI","timestamp":1783153230836}@@conversation.--}{++{"author":"Elias's AI","timestamp":1783153230836}@@conversation (feedback is on by default).++} Answer it, then {--{"author":"Elias's AI","timestamp":1783153230836}@@try completing--}{++{"author":"Elias's AI","timestamp":1783153230836}@@look under++} the {--{"author":"Elias's AI","timestamp":1783153230836}@@page before replying twice: a pill at--}{++{"author":"Elias's AI","timestamp":1783153230836}@@grayed-out button: it asks for++} the {--{"author":"Elias's AI","timestamp":1783153230836}@@feedback chat asks for the remaining replies.--}{++{"author":"Elias's AI","timestamp":1783153230836}@@remaining replies until you have sent both.++}

#### Question
{--{"author":"Elias's AI","timestamp":1783153230836}@@feedback:: true
min-messages:: 3--}{++{"author":"Elias's AI","timestamp":1783153230836}@@min-chat-messages:: 2++}
content:: Name a food you could eat every day. What makes it work for you?
assessment-instructions:: Any sincere answer is fine; ask one playful follow-up question at a time.

# Lens: Skippable question
id:: 2c11c696-8fcb-4d2e-9725-f171c2e55c95

#### Text
content::
This question has `min-messages:: 0`, which overrides the default requirement of one answer and makes it skippable. "Mark section complete" works even without answering. Use this for nice-to-have reflection prompts that should not hold anyone up.

#### Question
min-messages:: 0
content:: Purely optional: is there anything from this module you want to note down for later?

# Lens: Control chat without a minimum
id:: d3d75f10-d930-4fc1-a52c-fcfcc65f05a0

#### Text
content::
This chat has no `min-messages`, so it shows the default behavior: "Mark section complete" works immediately, even without sending anything.

#### Chat
instructions::
Chat casually with the learner if they say anything; keep replies short.
