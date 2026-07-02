{++{"author":"AI","timestamp":1782994905363}@@---
id: 34a3e729-3bb4-4a50-b50f-2a929e77aa64
slug: min-messages-demo
title: Min-messages demo
---

%% Test module for the completion-gate feature (PR #211). Each lens exercises one gate: chat with a message minimum, question with the default answer requirement, question with feedback replies, and an ungated control chat. Not meant for real courses. %%

# Lens: Chat with a 2-message minimum
id:: 593ceb17-ebd3-4c31-b250-3229b758ffc6

#### Text
content::
This page has a tutor chat with `min-messages:: 2`. Clicking "Mark section complete" before sending two messages should reject the click, scroll here, and show the gold pill above the chat input.

#### Chat
min-messages:: 2
instructions::
This is a test chat for the completion gate. Chat casually with the learner about anything they bring up; keep replies short.

# Lens: Question with the default requirement
id:: eeb40ecf-e7e1-4536-8bda-a5cf286439d7

#### Text
content::
This page has a plain question. Questions now require one completed answer by default — completing the page without answering should show the "Answer this question to finish this page" pill above the question.

#### Question
content:: What is your favorite color, and why?

# Lens: Question with feedback replies
id:: 43d2334e-990d-43be-98e2-aa7ff046cb16

#### Text
content::
This question has `feedback:: true` and `min-messages:: 3`: one answer plus two replies in the feedback chat. After answering, completing the page should show the tutor pill at the feedback conversation until two more replies are sent.

#### Question
feedback:: true
min-messages:: 3
content:: Name a food you could eat every day. What makes it work for you?
assessment-instructions:: Any sincere answer is fine; ask one playful follow-up question at a time.

# Lens: Control chat without a minimum
id:: d3d75f10-d930-4fc1-a52c-fcfcc65f05a0

#### Text
content::
Control page: this chat has no `min-messages`, so "Mark section complete" should work immediately without sending anything.

#### Chat
instructions::
This is an ungated control chat for the completion-gate test. Chat casually if the learner says anything.
++}