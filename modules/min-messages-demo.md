---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-messages-demo
title: {--{"author":"Elias's AI","timestamp":1782999430257}@@Min-messages--}{++{"author":"Elias's AI","timestamp":1782999430257}@@Interaction requirements++} demo
---

%% {--{"author":"Elias's AI","timestamp":1782999430257}@@Test--}{++{"author":"Elias's AI","timestamp":1782999430257}@@This++} module {--{"author":"Elias's AI","timestamp":1782999430257}@@for--}{++{"author":"Elias's AI","timestamp":1782999430257}@@explains interaction requirements: how to require chatting or answering before a learner can mark a page complete.

The defaults:
- A `#### Chat` never blocks completion. Learners can read++} the {--{"author":"Elias's AI","timestamp":1782999430257}@@completion-gate feature (PR #211). Each lens exercises--}{++{"author":"Elias's AI","timestamp":1782999430257}@@page and move on without sending anything.
- A `#### Question` must be answered once before the page can be completed.

Add `min-messages::` to a segment to change that:
- On a `#### Chat`, `min-messages:: 2` means the learner must send at least 2 messages in this page's tutor chat before "Mark section complete" works. All messages on the page count, wherever they were sent.
- On a `#### Question`, `min-messages:: 3` means++} one {--{"author":"Elias's AI","timestamp":1782999430257}@@gate: chat --}{++{"author":"Elias's AI","timestamp":1782999430257}@@completed answer plus 2 follow-up replies in the question's feedback conversation. This only makes sense together ++}with {++{"author":"Elias's AI","timestamp":1782999430257}@@`feedback:: true` (the validator warns you otherwise).
- `min-messages:: 0` on ++}a {--{"author":"Elias's AI","timestamp":1782999430257}@@message minimum, question with --}{++{"author":"Elias's AI","timestamp":1782999430257}@@question makes it skippable.
- Anything marked `optional:: true` never blocks completion.

What learners see: clicking "Mark section complete" too early rejects ++}the {--{"author":"Elias's AI","timestamp":1782999430257}@@default answer requirement, question with feedback replies,--}{++{"author":"Elias's AI","timestamp":1782999430257}@@click, scrolls to the first missing interaction,++} and {--{"author":"Elias's AI","timestamp":1782999430257}@@an ungated control chat. Not meant for real courses.--}{++{"author":"Elias's AI","timestamp":1782999430257}@@shows a small pill explaining what is needed. The pill disappears as soon as they make progress and only comes back if they try to complete again too early.

The four lenses below demonstrate each case. Preview the module and try them.++} %%

# Lens: Chat with a 2-message minimum
id:: 593ceb17-ebd3-4c31-b250-3229b758ffc6

#### Text
content::
This {--{"author":"Elias's AI","timestamp":1782999444363}@@page has a tutor--}{++{"author":"Elias's AI","timestamp":1782999444363}@@page's++} chat {--{"author":"Elias's AI","timestamp":1782999444363}@@with--}{++{"author":"Elias's AI","timestamp":1782999444363}@@has++} `min-messages:: 2`. {--{"author":"Elias's AI","timestamp":1782999444363}@@Clicking--}{++{"author":"Elias's AI","timestamp":1782999444363}@@Try clicking++} "Mark section complete" before sending two{--{"author":"Elias's AI","timestamp":1782999444363}@@ messages should reject--}{++{"author":"Elias's AI","timestamp":1782999444363}@@ messages:++} the {--{"author":"Elias's AI","timestamp":1782999444363}@@click, scroll here,--}{++{"author":"Elias's AI","timestamp":1782999444363}@@click is rejected++} and {--{"author":"Elias's AI","timestamp":1782999444363}@@show the gold--}{++{"author":"Elias's AI","timestamp":1782999444363}@@a++} pill above the chat {--{"author":"Elias's AI","timestamp":1782999444363}@@input.--}{++{"author":"Elias's AI","timestamp":1782999444363}@@input tells you how many messages are still needed.++}

#### Chat
min-messages:: 2
instructions::
{--{"author":"Elias's AI","timestamp":1782999444363}@@This is a test chat for the completion gate. --}Chat casually with the learner about {--{"author":"Elias's AI","timestamp":1782999444363}@@anything--}{++{"author":"Elias's AI","timestamp":1782999444363}@@whatever++} they bring up; keep replies short.

# Lens: Question with the default requirement
id:: eeb40ecf-e7e1-4536-8bda-a5cf286439d7

#### Text
content::
This page has a plain {--{"author":"Elias's AI","timestamp":1782999449020}@@question. Questions now--}{++{"author":"Elias's AI","timestamp":1782999449020}@@question with no extra fields. Questions++} require one completed answer by {--{"author":"Elias's AI","timestamp":1782999449020}@@default —--}{++{"author":"Elias's AI","timestamp":1782999449020}@@default. Try++} completing the page without {--{"author":"Elias's AI","timestamp":1782999449020}@@answering should show--}{++{"author":"Elias's AI","timestamp":1782999449020}@@answering: a pill above++} the {--{"author":"Elias's AI","timestamp":1782999449020}@@"Answer this question--}{++{"author":"Elias's AI","timestamp":1782999449020}@@question asks you++} to {--{"author":"Elias's AI","timestamp":1782999449020}@@finish this page" pill above the question.--}{++{"author":"Elias's AI","timestamp":1782999449020}@@answer it first.++}

#### Question
content:: What is your favorite color, and why?

# Lens: Question with feedback replies
id:: 43d2334e-990d-43be-98e2-aa7ff046cb16

#### Text
content::
This question has `feedback:: true` and `min-messages:: 3`: one answer plus two replies in the feedback {--{"author":"Elias's AI","timestamp":1782999452223}@@chat. After answering,--}{++{"author":"Elias's AI","timestamp":1782999452223}@@conversation. Answer it, then try++} completing the page {--{"author":"Elias's AI","timestamp":1782999452223}@@should show the tutor--}{++{"author":"Elias's AI","timestamp":1782999452223}@@before replying twice: a++} pill at the feedback {--{"author":"Elias's AI","timestamp":1782999452223}@@conversation until two more replies are sent.--}{++{"author":"Elias's AI","timestamp":1782999452223}@@chat asks for the remaining replies.++}

#### Question
feedback:: true
min-messages:: 3
content:: Name a food you could eat every day. What makes it work for you?
assessment-instructions:: Any sincere answer is fine; ask one playful follow-up question at a time.

# Lens: Control chat without a minimum
id:: d3d75f10-d930-4fc1-a52c-fcfcc65f05a0

#### Text
content::
{--{"author":"Elias's AI","timestamp":1782999456656}@@Control page: this--}{++{"author":"Elias's AI","timestamp":1782999456656}@@This++} chat has no `min-messages`, so {++{"author":"Elias's AI","timestamp":1782999456656}@@it shows the default behavior: ++}"Mark section complete" {--{"author":"Elias's AI","timestamp":1782999456656}@@should work immediately--}{++{"author":"Elias's AI","timestamp":1782999456656}@@works immediately, even++} without sending anything.

#### Chat
instructions::
{--{"author":"Elias's AI","timestamp":1782999456656}@@This is an ungated control chat for --}{++{"author":"Elias's AI","timestamp":1782999456656}@@Chat casually with ++}the{--{"author":"Elias's AI","timestamp":1782999456656}@@ completion-gate test. Chat casually if the learner says anything.--}{++{"author":"Elias's AI","timestamp":1782999456656}@@ learner if they say anything; keep replies short.++}
