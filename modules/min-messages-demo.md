---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-messages-demo
title: Interaction requirements demo
---

%% This module explains interaction requirements: how to require chatting or answering before a learner can mark a page complete.

The defaults:
- A `#### Chat` never blocks completion. Learners can read the page and move on without sending anything.
- A `#### Question` must be answered once before the page can be completed.

Add `min-messages::` to a segment to change that:
- On a `#### Chat`, `min-messages:: 2` means the learner must send at least 2 messages in this page's tutor chat before "Mark section complete" works. All messages on the page count, wherever they were sent.
- On a `#### Question`, `min-messages:: 3` means one completed answer plus 2 follow-up replies in the question's feedback conversation. This only makes sense together with `feedback:: true` (the validator warns you otherwise).
- `min-messages:: 0` on a question makes it skippable.
- {--{"author":"Elias's AI","timestamp":1783013081667}@@Anything--}{++{"author":"Elias's AI","timestamp":1783013081667}@@Whole lenses++} marked `optional:: true` never {--{"author":"Elias's AI","timestamp":1783013081667}@@blocks--}{++{"author":"Elias's AI","timestamp":1783013081667}@@block++} completion.{++{"author":"Elias's AI","timestamp":1783013081667}@@ (`optional` is a lens-level field; on chat and question segments use `min-messages` instead.)++}

What learners see: clicking "Mark section complete" too early rejects the click, scrolls to the first missing interaction, and shows a small pill explaining what is needed. The pill disappears as soon as they make progress and only comes back if they try to complete again too early.

The five lenses below demonstrate each case. Preview the module and try them. %%

# Lens: Chat with a 2-message minimum
id:: 593ceb17-ebd3-4c31-b250-3229b758ffc6

#### Text
content::
This page's chat has `min-messages:: 2`. Try clicking "Mark section complete" before sending two messages: the click is rejected and a pill above the chat input tells you how many messages are still needed.

#### Chat
min-messages:: 2
instructions::
Chat casually with the learner about whatever they bring up; keep replies short.

# Lens: Question with the default requirement
id:: eeb40ecf-e7e1-4536-8bda-a5cf286439d7

#### Text
content::
This page has a plain question with no extra fields. Questions require one completed answer by default. Try completing the page without answering: a pill above the question asks you to answer it first.

#### Question
content:: What is your favorite color, and why?

# Lens: Question with feedback replies
id:: 43d2334e-990d-43be-98e2-aa7ff046cb16

#### Text
content::
This question has `feedback:: true` and `min-messages:: 3`: one answer plus two replies in the feedback conversation. Answer it, then try completing the page before replying twice: a pill at the feedback chat asks for the remaining replies.

#### Question
feedback:: true
min-messages:: 3
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
