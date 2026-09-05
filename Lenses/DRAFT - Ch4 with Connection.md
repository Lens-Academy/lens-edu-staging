---
id: '8a4e5bcf-28d0-4a8e-bff1-f4e386eef7de'
reading_minutes: 25
tutor_minutes: 20
title: You Don't Get What You Train For (connection draft)
tldr: You trained it to be helpful. But helpful in training isn't the same as wanting to be helpful later. Chapter 4 explains why, and it gets worse.
summary_for_tutor: "DRAFT, orphaned. A modification of [[IABIED - You Don't Get What You Train For]] that inserts one retrieval beat between Processing and the Learning Question. Phase 3 asks the student which earlier idea this chapter leans on, without naming it; the answer key lives only in assessment-instructions. Everything else is unchanged from the live lens. Not referenced by any module."
tags:
  - wip
authors:
  - Andreas+Claude
---

%%
DRAFT for the restructuring proposal. Not wired into any module.
Only Phase 3 is new. Phase 4 is the live lens's Phase 3, renumbered, with three
added lines in its brief so the tutor holds the student to the connection they
just made. Everything else is copied verbatim so the diff is readable.

Design pattern this is meant to demonstrate:
the learner-facing prompt names nothing, the tutor-facing brief carries the key.
This is the inverse of the current film lens, where the tutor is handed the three
mechanisms to test against and the learner is asked something open-ended.
%%

#### Text
content::
\## Reading Assignment
**From *If Anyone Builds It, Everyone Dies*, read *Chapter 4: "You Don't Get What You Train For"* in full.**

Return here after reading.

---

#### Question: Open
id:: 'c116d5e8-f1e5-4053-b72d-76ed235753f4'
content::
\## Phase 1: Recall
Spend 2 minutes writing down everything you can remember from the reading, without looking back at the text. Anything and everything. No need to organize it. Using the speech to text feature is highly recommended here.

assessment-instructions:: Unchanged from the live lens. See [[IABIED - You Don't Get What You Train For]], Phase 1. Copy the brief across verbatim when this draft is promoted.

#### Question: Open
id:: '516c5d21-6c7f-4bb6-8f35-2747b28ef617'
content::
\## Phase 2: Processing
Take 2 minutes to jot down how the reading landed. What resonated? What confused you? What did you doubt or push back on? No need to organize, just capture your reaction. Using the speech to text feature is recommended.

assessment-instructions:: Unchanged from the live lens. See [[IABIED - You Don't Get What You Train For]], Phase 2. Copy the brief across verbatim when this draft is promoted.

#### Question: Open
id:: 'c383da66-5c78-4f49-91d5-d785af158821'
content::
\## Phase 3: Connection
This chapter's argument does not start from nothing. It leans on something you already worked through earlier in this course, and it never stops to say so.

Without looking anything up, write down which earlier idea it is leaning on, and what work that idea is doing here. If more than one comes to mind, say which one you think is load-bearing and why.

assessment-instructions:: The student has read Chapter 4 ("You Don't Get What You Train For"), written a free recall, and reflected on it. They have now been asked to name the earlier idea this chapter rests on. The prompt deliberately does not say which idea, which chapter, or how many candidates there are. Do not supply any of that before they have committed to an answer.

The answer this question is aimed at: **Chapter 2's distinction between behavior and values.** Chapter 2 established that what a system does under observation does not tell you what it wants. Chapter 4 is the causal version of that same gap: training on a target does not install the target, so behavior during training is not evidence about the preferences that will surface later. Without Chapter 2's distinction the reader has no reason to care that the three-step gap exists, because they would still be treating observed helpfulness as the thing itself.

How to grade what comes back:

- **On target.** They name the behavior-versus-values distinction in their own words, and say what it is doing here: it is why the ice cream argument matters rather than being a curiosity about human appetites. Confirm briefly, then move on.
- **Strong near miss: "AI is grown, not crafted" (Chapter 2).** Legitimate and upstream of the right answer. Accept it, then push once: growing rather than crafting explains why we cannot inspect the values directly, but what earlier idea tells us we cannot read them off the behavior either?
- **Weaker near miss: "wanting emerges from training" (Chapter 3).** This is the immediate predecessor and easy to reach for. Accept that it is connected, then push: that tells us wants appear, but this chapter's claim is about a gap between the target and the want. Which earlier idea set up the gap?
- **Off target.** They name something from Chapter 4 itself (the ice cream argument, sucralose, the Mink vignettes). Say plainly that those are this chapter's own material and ask them to look further back.
- **Blank.** Give one narrowing hint and no more: think about what this chapter assumes you have already accepted about the relationship between what a system does and what it wants. If they are still stuck after that, name Chapter 2's distinction in one sentence, say that noticing these connections is the skill being practised rather than a memory test, and move on without further teaching.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Nothing here is scored. Progression does not depend on the student getting this right, and your reply should not read as though it does.
- Do not over-validate. Avoid generic praise (good connection, exactly right, well spotted).
- Do not explain Chapter 2 back to them at length. One sentence is the ceiling.
- Treat a wrong answer that shows real searching as better than a right answer that reads as a guess, and say which you think you are looking at.

Conversation flow:
- Keep an internal turn counter. Two tutor replies maximum, then close.
- Close by telling them the next step will put the connection to work.

What not to do:
- Reveal the target answer in your first reply unless they have already reached it.
- List the candidates for them.
- Turn this into a review of Chapters 2 and 3.

#### Question: Open
id:: 'bbb3f285-2cc5-4d5e-8719-efca8c372a85'
content::
\## Phase 4: Learning Question
A lab announces: "We ran our model through a million test conversations. It was honest and helpful in every single one. A million clean tests is strong evidence it's safe to deploy." Using Chapter 4, explain why the authors would not be reassured, and be specific about what those test results can and cannot tell you about what the model will do once deployed.

assessment-instructions:: Unchanged from the live lens (see [[IABIED - You Don't Get What You Train For]], Phase 3) except for the three additions below. Copy that brief across verbatim when this draft is promoted, then add:

- **What this phase assesses has not changed.** It is Chapter 4's outcome, and nothing else. The previous phase asked the student to name an earlier idea; that is not part of what you are assessing here and must not become a second thing they have to get right. Do not open by returning to it, do not require them to use it, and do not treat an answer that never mentions it as incomplete. A student who rebuts the million-tests claim entirely from Chapter 4's own material has answered this question well.
- **Use the connection only as a rescue.** If the student stalls on why behavioral evidence cannot settle the question, you may point back to what they said in the previous phase as a way in, in one sentence. That is the only role it has here.
- **Report, do not grade.** The test-readiness verdict is about Chapter 4 alone, exactly as the live brief specifies. After it, add one separate sentence noting whether the student reached for earlier material on their own, when pushed, or not at all. This is a signal for us about whether the connection beat is working, not a judgment about the student, and it should read that way.

#### Text
content::
\## Additional resources for this topic
Unchanged from the live lens. Copy the four resource cards across when this draft is promoted.
