---
id: 8189763f-576e-4f04-a614-4a00c628e386
{++{"author":"Elias's AI","timestamp":1783849700792}@@tldr: "A demo of the Question segment. It asks you to explain what questions are for, then to plan how you'd vet one for a real course, showing how learner answers get collected and assessed by the AI tutor, including a voice-answer variant."
summary_for_tutor: "Demonstrates the Question segment. Opens with a Text note, then two Question segments. The first asks the learner to explain in one or two sentences what a Question segment is useful for (assessed for noting that questions collect learner responses the AI tutor can assess; 500-character limit). The second asks what they would check before using a question in a real course (assessed for a concrete testing plan such as wording, character limit, rubric, and feedback quality; voice answering enforced)."
++}title: Question demo
---

#### Text
content::
This lens demonstrates `#### Question` segments.

#### Question
content:: In one or two sentences, explain what a `#### Question` segment is useful for.
assessment-instructions:: Look for a concise answer that says questions collect learner responses and can be assessed by the AI tutor.
max-chars:: 500

%% `feedback:: true` means the learner gets AI feedback after answering. `max-chars::` sets a character limit. %%

#### Question
content:: Try answering this one by voice. What would you check before using a question in a real course?
assessment-instructions:: Look for a concrete testing plan, such as checking the wording, character limit, scoring rubric, and feedback quality.
enforce-voice:: true

%% `enforce-voice:: true` requires the learner to answer by speaking instead of typing. 15 june 2026: probably not implemented though. Problem is that people can't always speak in every situation, so it'd need some override anyway. Should still make a strong nudge or so?%%
