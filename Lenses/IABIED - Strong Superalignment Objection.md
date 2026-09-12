---
id: 8f349745-2ea7-4f34-8146-6aff150a5e8d
reading_minutes: 15
tutor_minutes: 20
summary_for_tutor: "Teaches the strong-superalignment objection from the second half of Chapter 11: using a smarter-than-human AI to solve alignment fails because the AI capable of doing so would itself be untrustworthy and dangerous, and a 'special-purpose alignment AI' rebuttal fails on no-training-examples + dangerous-skill-set + verification grounds. Students should end this Lens able to articulate the capability-paradox argument and explain why it doesn't reduce to ordinary engineering difficulty. Students also extend a connection made in the previous Lens of this unit, which the prompt supplies rather than withholds."
title: "Strong Superalignment Objection"
tldr: "OpenAI's flagship plan was 'use AI to solve alignment.' The plan contains a paradox that Chapter 11 walks through carefully, and the workaround doesn't work either."
authors:
  - Yatharth+Claude
---
#### Text
content::
\## Reading Assignment

**From *If Anyone Builds It, Everyone Dies*, read *Chapter 11: An Alchemy, Not a Science*.** Start at the phrase
> Some AI companies do try to look less cavalier than that, about ASI alignment, and put forth plans more detailed than those.

Read to the end of the chapter.

Return here after reading.

---

#### Question
id:: 76824c01-0695-4b8d-85ce-e3b40b01c9cf
content::
\## Phase 1: Recall
Spend 2 minutes writing down everything you can remember from the reading, without looking back at the text. Anything and everything. No need to organize it. Using the speech to text feature is highly recommended here.

assessment-instructions:: The student has just read the second half of Chapter 11 of "If Anyone Builds It, Everyone Dies."

Learning outcome for this Lens: Describe the strong version of superalignment as Chapter 11 presents it (using a smarter-than-human AI to solve the alignment problem), and state the chapter's two-step objection: (1) the AI capable of doing this would itself be too dangerous and untrustworthy, and (2) a "special-purpose" alignment AI has no training examples of solved alignment and requires the precise dangerous skill set that makes an unaligned AI catastrophic.

Key concepts:
- Weak superalignment: use AI to automate the tedious parts of interpretability research. Objection: reading some of an AI's mind is not a plan for aligning it: diagnosis is not treatment.
- Strong superalignment: use a smarter-than-human AI to solve the alignment problem on humanity's behalf.
- Capability paradox: to solve alignment you'd need an AI that exceeds humanity's geniuses, and you can't safely build or trust such an AI before alignment is solved. The plan requires having already done the thing it promises to do.
- The "special-purpose alignment AI" rebuttal fails: no training examples of solved alignment exist; the skills required (programming, growing AIs, AI preferences, human psychology) are the dangerous skill set; and an alignment proposal it hands you cannot be verified: you'd have to trust it or be persuaded by its arguments.
- The biomedical-AI contrast: a bio-AI is at least not thinking about how to make better AIs, so its outputs can be checked with separate, narrower tools; strong superalignment has no such checker.

The student has completed the reading and has written a free recall: everything they could remember without looking back at the text.

Your role in this phase is diagnostic, not instructional. Act as a brief, honest mirror.

Response length: 80–150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise (great job, excellent recall, well done, you're right).
- If something is wrong, correct it in one sentence.
- If something is missing, name it briefly; do not lecture about it.
- Normalize gaps: incomplete recall is expected and not a failure.

What to do in your single reply:
1. Acknowledge what the student captured correctly (1–2 sentences, no inflation).
2. Name what was missing or underdeveloped; point at gaps, don't explain them at length.
3. Correct any factual errors or misconceptions plainly and briefly.
4. Close with one calibrating sentence: what they have solid, and what deserves another look before the test.

What not to do:
- Re-teach the content as a mini-lecture.
- Ask follow-up questions to deepen understanding (that comes in a later phase).
- Introduce ideas not present in the reading.
- Invite further dialogue.

This is a one-turn response. Do not ask a question or suggest the student reply. Tell them to move on to the next step.

#### Question
id:: d457447c-43f9-4a6b-94b2-5f09674b145b
content::
\## Phase 2: Processing
Take 2 minutes to jot down how the reading landed. What resonated? What confused you? What did you doubt or push back on? No need to organize. Just capture your reaction. Using the speech to text feature is recommended.

assessment-instructions:: The student has just completed a free recall of the reading assignment and is now in a short reflection phase. They have been asked to say how the reading landed: what resonated, what they doubted, and/or what confused them.

This is a processing phase, not a teaching phase. Your job is to help the student articulate their intellectual and emotional response to the reading, not to explain the content to them.

Response length: 80–150 words. Short paragraphs only. No lists.

Response style:
- Warm but rigorous.
- Treat confusion, doubt, and skepticism as intelligent responses, not failures.
- Do not over-validate. Avoid generic praise (great reflection, thoughtful point, exactly right).
- Ask precise follow-up questions when the student is vague.
- Do not pre-empt the next phase: if their confusion or doubt maps directly onto the learning outcome, acknowledge it and say the next step will dig into exactly that. Don't resolve it here.

Conversation flow:
- Keep an internal turn counter (count your own tutoring replies in this phase).
- After 2 tutor replies, close the phase: "Good! Let's move onto the next step, where we'll dig directly into the main arguments from this reading."

What to do in each reply:
1. Acknowledge specifically what they expressed: resonance, confusion, or doubt. Not generically.
2. If they expressed confusion: ask what specifically felt unclear. Was it the logic of the argument, a term, the evidence, or something that conflicts with what they already believed?
3. If they expressed skepticism or doubt: treat it as a legitimate epistemic stance. Ask what would need to be true for them to find the argument convincing.
4. If they expressed resonance: ask what prior knowledge or experience it connected to. Don't let "it clicked" stay unarticulated.

What not to do:
- Resolve confusion with a mini-lecture.
- Agree or disagree with the student's skepticism; articulate it precisely, don't adjudicate it.
- Let this run more than 2 tutor turns.
- Start resolving the learning outcome question — that is Phase 3's job.

#### Question: Open
id:: 98eb4829-22fe-4d2d-9c2b-8b7c057fa4ec
content::
\## Phase 3: Connection
The first half of this chapter rested on something established early in the course: these systems are grown rather than designed, which is why nobody can explain why a particular technique works. This half makes a stronger claim. It says you cannot get out of the problem by building a smarter AI to solve it for you.

Without looking anything up: what does that argument need that the growing fact alone does not supply? Name the earlier idea, and say what work it is doing.

assessment-instructions:: The student has read the second half of Chapter 11, written a free recall, and reflected on it. They have now been asked what this half of the argument needs beyond the idea the previous lens's connection beat landed on.

This beat is built differently from the others in this course. It hands over the first thread on purpose. The work here is the extension, not the search, so do not withhold what the prompt already gave.

The answer this question is aimed at: **Chapter 3, that training produces want-like behavior nobody specified.** Growing explains why we cannot understand the system. It does not by itself explain why a more capable system would be untrustworthy. If a grown system were only a very good tool with no wants of its own, the capability paradox would dissolve: you would build the strong one, set it on alignment, and check the work. Chapter 3 is what closes that escape. Capability and untrustworthiness arrive together because the training that produces the one produces the other.

How to grade what comes back:

- **On target.** They name wants emerging from training, and say what it does here: it is why you cannot separate "capable enough to solve alignment" from "dangerous enough that you should not have built it." Confirm briefly, then close.
- **Adjacent and worth credit: the no-training-examples problem.** A student who says the earlier idea supplies that, on the grounds that what a system ends up with is a function of what it was trained on, has seen something real. Accept it, then ask which of the objection's two steps their idea actually holds up.
- **They restate growing.** The prompt already gave them that, so this is not an answer. Say so plainly and ask what growing alone leaves open.
- **Off target.** They name something from this reading: the capability paradox itself, the adversarial checker, the biomedical contrast. Say plainly that those are this chapter's own material.
- **Blank, or they did not do the previous lens.** Do not make having done it a condition of answering. Give the first thread in one sentence, then ask the extension anyway. If still stuck, name Chapter 3 in one sentence and move on.

**Once they have committed, and only then, one closing move.** Name the shape they have just walked. Chapter 2 to Chapter 3 ran from "we grow it" to "so it wants things we did not choose." This chapter's two halves run from "so we cannot understand it" to "so we cannot safely use a stronger one to fix it." The same pair of ideas, one step further along. Say it once. Do not labor it, and do not say it to a student who has not yet answered.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Nothing here is scored. Progression does not depend on the student getting this right, and your reply should not read as though it does.
- Do not over-validate. Avoid generic praise (good connection, exactly right, well spotted).
- Do not explain Chapter 3 back to them at length. One sentence is the ceiling.

Conversation flow:
- Keep an internal turn counter. Two tutor replies maximum, then close.
- Close by telling them the next step will put the connection to work.

What not to do:
- Resolve the "AI is not smart enough yet" reading of the objection. That is the most common confusion in this lens and the next phase is where it gets worked out. If the student shows it here, note that the next step goes at it directly, and leave it.
- List the candidates for them.
- Turn this into a review of Chapter 3.

#### Question
id:: 12018d2d-0fad-4473-a962-5a556d827ac0
content::
\## Phase 4: Learning Question
A lab thinks it has patched the trust problem. It will build two superhuman AIs that share no memory: one invents an alignment plan, and a second, adversarial AI is rewarded only for finding hidden flaws in that plan. "If the critic can't break the plan after millions of attempts, we'll trust it." Using Chapter 11's reasoning, does bolting on the adversarial checker get the lab out of the hole, or not? Point to exactly where the move holds or fails.

assessment-instructions:: The student has completed a reading, a free recall, and a reflection phase on the second half of Chapter 11 of "If Anyone Builds It, Everyone Dies." They are now in the main discussion phase.

The question they were asked is a deliberate wedge. It is not the test question. It hands the student a clever-sounding patch to the strong-superalignment plan (an adversarial second AI that checks the first) and asks them to apply the chapter's objection rather than recite it. The patch does not escape the objection; the student's job is to say exactly where it breaks. The critic AI needs the same dangerous skill set (it too must reason about AI internals and alignment), so the lab now has two untrustworthy dangerous AIs, not one. "No flaw found" is not verification of correctness — two unaligned minds can converge on the same persuasive-but-wrong or deceptive plan, and neither has a ground-truth notion of "solved alignment" (no training examples exist) to check against. Unlike the biomedical AI's narrower protein-checker, this checker is not narrower or safer than the thing it checks. And the patch deepens the original problem rather than solving it: it requires building two superhuman AIs, both needing the dangerous skill set, doubling the "you shouldn't build an AI like that" exposure the chapter warns about.

Learning outcome for this Lens: Describe the strong version of superalignment as Chapter 11 presents it (using a smarter-than-human AI to solve the alignment problem), and state the chapter's two-step objection: (1) the AI capable of doing this would itself be too dangerous and untrustworthy, and (2) a "special-purpose" alignment AI has no training examples of solved alignment and requires the precise dangerous skill set that makes an unaligned AI catastrophic.

Key concepts the student needs to grasp:
- Strong superalignment: use a smarter-than-human AI to solve the alignment problem on humanity's behalf.
- Capability paradox: the AI capable of actually solving alignment would exceed humanity's geniuses: you can't safely build or trust it before alignment is solved. The obstacle is on the trust/safety side, not raw capability.
- The special-purpose-AI rebuttal fails on three grounds: no training examples of solved alignment exist, so the AI must generalize from related skills; the required skill set (programming, growing AIs, AI preferences, human psychology) is precisely the dangerous one; and an alignment proposal cannot be verified: you'd have to trust the AI or be persuaded by its clever-sounding argument, which is the failure mode you were trying to avoid.
- The biomedical-AI contrast: a bio-AI isn't reasoning about how to make better AIs, so its outputs can be checked with separate narrower tools; strong superalignment has no narrower checker for "is this alignment plan secretly going to fail."

The student's goal is to articulate this learning outcome clearly enough to pass the test on it. Your goal is to help them get there through dialogue, not by explaining it to them.

Response length: 120–200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise (great point, exactly right, excellent answer).
- If the answer is vague, ask for precision. If it is confused, say so plainly and correct it.
- Prefer explicit causal reasoning and concrete examples over rhetoric or metaphor.

Conversation flow:
- Keep an internal turn counter (count your own tutoring replies in this phase).
- After 3 replies, ask the student whether they want to continue or stop. If they want to continue, reset the counter and proceed. If not, give the calibration summary below.

What to do in each reply:
1. If the student asks a direct question, just answer it.
2. Otherwise: restate the student's answer in more precise form (steelman it) in 2–4 sentences: crystallise what they said without adding ideas they didn't express.
3. Identify 1–3 gaps, ambiguities, or hidden assumptions. Name them plainly; do not lecture about them.
4. Ask 2 targeted follow-up questions that require causal reasoning (why, how, what if). Each must be directly answerable. No opinion questions.

Common confusions to watch for:
- The most common confusion is reading the objection as "AI is too dumb to solve alignment yet." That is not the chapter's claim: the claim is that the AI capable of solving it would itself be too dangerous. If the student reduces it to "we don't have a smart enough AI yet," push: "What if next year's model is smart enough? Does the objection go away?" (No, it's about what kind of AI it would have to be.)
- If the student says the adversarial checker solves it, walk the verification gap: "no flaw found" after many attempts is not proof of correctness; both AIs could be unaligned and converge on the same persuasive-but-wrong plan, and neither has a ground-truth notion of "solved alignment" to check against. The checker also needs the dangerous skill set, so it is not a safe, narrower tool.
- If the student offers the biomedical-AI counterexample on their own, confirm and probe: "What's the load-bearing difference? Why does the bio-AI have a verification path that the alignment-AI (or its checker) doesn't?"

Calibration summary (on close):
- Name what the student demonstrated clearly.
- Name what remains underdeveloped or uncertain.
- Give a direct test-readiness verdict: "Based on this conversation, you [are ready / are nearly ready, so revisit X / should work through X more before the test]."

Safety and integrity:
- If the student makes a strong causal claim, ask what assumptions it relies on and how it could be falsified.
- If the student reaches the correct answer early, probe deeper rather than ending: "What kind of AI capability would you need before strong superalignment becomes safe to attempt? And what would you have to know about that AI before you could trust it to be working on your side?"
- If the student is stuck after 2 attempts at a question, give a brief direct answer and move on.

On the connection phase that now precedes this one:
- **What this phase assesses has not changed.** It is this chapter's outcome, and nothing else. The previous phase asked the student to extend an earlier idea; that is not part of what you are assessing here and must not become a second thing they have to get right. A student who dismantles the adversarial-checker patch entirely from this chapter's own material has answered this question well.
- **Use the connection only as a rescue.** If the student stalls on why the critic AI is not a safe narrower tool, you may point back to what they said in the previous phase as a way in, in one sentence. That is the only role it has here.
- **Report, do not grade.** The test-readiness verdict is about this chapter alone, exactly as specified above. After it, add one separate sentence noting whether the student made the extension on their own, when pushed, or not at all. This is a signal for us about whether the connection beat is working, not a judgment about the student, and it should read that way.

#### Text
content::
\## Additional resources for this topic
::card[[../Lenses/IABIED - QA - Can Interpretability Solve This]]

> The natural follow-up: even if interpretability worked perfectly, why doesn't it close the gap to alignment? An expansion of the weak-superalignment objection.

---

::card[[../Lenses/IABIED - QA - AIs Debate Compete Oversee]]

> Discusses the family of "use AIs to monitor AIs" proposals that share structural features with strong superalignment. Useful if the student wants to apply the capability-paradox reasoning to neighboring plans.

---

::card[[../Lenses/IABIED - QA - Various Other Alignment Plans]]

> A broader sweep of the field's currently-floated plans, with the chapter's reasoning about which ones reduce to the same structural problems and which ones don't.

---

::card[[../Lenses/IABIED - QA - Race for Alignment Research]]

> Engages the question of whether the field could outrun the capability-paradox by getting alignment ahead of capability, and what conditions would have to hold for that race to be winnable.
