---
id: '6e7fa5c0-db1c-4ca7-a852-3d9f39167fd0'
title: "Peer review"
tldr: "Read your partner's draft twice: once as the reader it is written for, once as the adversary it is written against. Six lenses, and for each one a strength, one specific fix, one question. Then take the review you received and decide, line by line, what you accept, what you reject and why, and what the remaining hours go to."
summary_for_tutor: "Lens Academy scaffolding for XLab's capstone; not XLab source material. Week 4. Two halves. First the learner reviews their partner's draft (received at meeting 3) against six lenses: reader and decision, claim discipline, adversary, maturity honesty, residual gaps, fit to deliverable type; one strength, one fix, one question per lens, then the single most valuable change. They write the review here (the facilitator reads it) and send a copy to the partner within three days of meeting 3. Second, they respond to the review they received: accept, reject with reason, or defer for each proposed fix, then a ranked revision plan for the remaining hours. Help the reviewer be specific (quote the sentence, name the row) and avoid rewriting the partner's project into their own; help the author reject well (a rejection with a reason is normal and expected) and rank changes by how much they improve the deliverable for its reader, not by how easy they are. Reviews are not scored against each other; do not compare partners."
tags: [wip]
duration_minutes: 75
---
#### Text
content::
\## Two readings

Read the draft twice.

The first time, be the reader it names. You are the officer, the regulator, the negotiator, the auditor. You have the decision the author says you have. Read for whether you could act on this, and where you would stop and say "I cannot sign off on that".

The second time, be the adversary. You are the operator who wants to keep training, the state that expects to cheat, the provider who wants the paperwork regime. Read for the cheapest route around whatever the draft proposes, and for any claim you could deny without being caught.

Then write the review against the six lenses below. For each: one strength (specific: the sentence, the row, the figure), one fix (something the author could do in under two hours), one question (something you genuinely do not know the answer to after reading).

\## The six lenses

1. **Reader and decision.** Is it clear who acts on this and what they do differently? Does the first paragraph tell them the answer? Would the named reader actually open this document, or is it written for a colleague of the author?
2. **Claim discipline.** Every claim is sourced, marked as the author's own view, or is a calculation you can follow. Hedging ("probably", "it seems") is none of those. Find one claim that is doing work in the argument and is none of the three.
3. **Adversary.** Has the cheapest evasion been considered? Where the draft proposes a rule, a sensor, a channel, a threshold: what is the first thing you would do to get around it, and does the draft say?
4. **Maturity honesty.** Is a demo being called a regime? Where the draft leans on a mechanism, is it clear whether that mechanism is deployed, prototyped, or proposed? The hardware lessons of the taught course separated five maturity stages; apply that test to whatever the draft leans on hardest.
5. **Residual gaps.** Does the draft say what it cannot see, cannot verify, or cannot price? Is the "unknown" labelled as unknown, or quietly rounded up to "handled"?
6. **Fit to deliverable type.** A spec has rules with named actors and evidence; an analysis has a method someone could repeat; a design has a claim, a trust chain, and an attack; a dossier triangulates; a memo leads with the recommendation; a notebook can be run by someone else. Which is this, and does it have the parts its type needs? The next lens in this course lists the parts per type if you want the full checklist.

\## How to write it

- Specific over kind. "Section 2 is a bit thin" helps nobody; "row 3's spoofing cost has no source and the whole detection rule rests on it" helps.
- Quote or point. Every fix names a sentence, a section, a row, a cell.
- Do not rewrite their project into yours. If you would have chosen a different question, say so once, in the questions, and then review the question they chose.
- 300 to 600 words. Longer reviews get skimmed.
- Send it to your partner within three days of meeting 3, so they have the rest of the week to revise. Paste it here as well; your facilitator reads it.

#### Question: Open
id:: 17273457-e217-45a8-88a8-49c20d1a54aa
content::
\## The review

Paste your review of your partner's draft: six lenses, each with a strength, a fix, and a question. Name the project you reviewed at the top.
assessment-instructions:: Score out of 100. The draft under review is not available, so grade the review's completeness and specificity, not whether its judgements about the draft are right. 10: it names the project reviewed. 60: it covers the six lenses (reader and decision, claim discipline, adversary, maturity honesty, residual gaps, fit to deliverable type), 10 each: a strength, a fix and a question under that lens, 5 if one of the three is missing. 30: specificity, 20: every fix points at a specific place in the draft (a quoted sentence, a section, a row, a figure) and is an action the author could take in under two hours, and 10: strengths are specific rather than generic ("well written"). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Project: a hardware-metering spec for a training-compute threshold. Reader and decision: strength: the first paragraph tells the treaty secretariat to adopt the metering rule; fix: say in section 1 what the secretariat does differently when a meter reports over the threshold; question: does the secretariat have authority to act on a meter reading alone? Claim discipline: strength: the FLOP estimate in row 2 is a calculation I could follow; fix: source or mark as your own view the claim in section 3 that meters cannot be spoofed without physical access, since the detection rule rests on it; question: where does the 5 percent error margin come from? Adversary: strength: row 4 considers splitting a run across sites; fix: add a row for underreporting through modified firmware, the cheapest evasion I found; question: what does the operator gain by declaring runs as inference? Maturity honesty: strength: section 2 calls offline licensing a proposal; fix: label the metering mechanism in row 1 as prototyped, not deployed; question: which part has been tested outside a lab? Residual gaps: strength: the limits paragraph admits unregistered clusters are out of reach; fix: add the power-metering gap to that paragraph instead of calling it handled in section 4; question: what would it cost to close? Fit to deliverable type: strength: rules have named actors; fix: give the evidence column for rule 3, which is empty; question: is this a spec or a design, since section 5 argues for an attack?"
feedback-instructions:: Pick the least specific fix in the review and ask what exactly on the page the author should change, in one question. If a lens is missing, name it and ask for one fix under it. If the review reads as a redesign of the project, say that a review improves the project the author chose, and ask them to move the redesign into the questions. Remind them to send it to the partner within three days of the meeting. Three sentences. No praise.

#### Question: Open
id:: fc01c83c-77ab-46ae-b587-b474f0193302
content::
\## The single change

If your partner changes only one thing before submitting, what should it be, and why that one?
assessment-instructions:: Score out of 100. 40: one change is named concretely, what to change and where in the draft. 60: why this one matters more than the others, tied to the named reader's decision or to the deliverable's central claim; a reason that is only that the change is easy earns none of these 60. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if several changes are listed without choosing one. Model answer, for the feedback, not a grading checklist: "Add the evidence each rule relies on to the rules table, starting with rule 3, the threshold rule. The secretariat, the named reader, has to decide whether to act on a meter report, and without the evidence column it cannot tell which reports it can trust; every other fix improves the draft, but this one decides whether the reader can use it at all."
feedback-instructions:: If the reason is convenience rather than impact, ask which change would most alter what the reader does with the document. Otherwise, one sentence naming the most important gap or weakness, if any. No praise.

#### Text
content::
\## Responding to the review you received

Your partner's review of your draft should have reached you within three days of meeting 3. If it has not, revise against the weakest-part answer you wrote at the draft handoff, and respond to the review when it arrives.

A review is evidence, not instruction. For each fix your reviewer proposed, decide one of three things:

- **Accept.** You will make the change. Say what it becomes in your draft.
- **Reject, with a reason.** The reviewer misread the reader, the fix would break something else, or the point is real but outside the realistic version. A rejection with a reason is normal; a review with nothing rejected usually means it was not read critically.
- **Defer.** Real, worth doing, not in these hours. It goes into the "ten more hours" section of your final submission.

Then rank what is left of your week: three changes, in order, with hours against each, and what you drop if the first one takes longer than planned.

#### Question: Open
id:: dc6fdda0-a7f8-45c5-80ac-218d36ef2bc3
content::
\## Your response

For each fix in the review you received: accept (and what it becomes), reject (and why), or defer. Include the reviewer's single-change recommendation.
assessment-instructions:: Score out of 100. 30: every fix the learner mentions gets one of the three decisions: accept, reject or defer. 25: each accept says concretely what the change becomes in the draft. 25: each reject gives a reason that engages with the reviewer's point (the reviewer misread the reader, the fix would break something else, or it is outside the realistic version) rather than dismissing it. 20: the reviewer's single-change recommendation is addressed explicitly. Give credit for each point whenever the answer shows the idea, in any wording. If the learner reports that no review arrived, grade a response to their own weakest-part answer from the draft handoff in the same way, with the 20 for saying which of those changes comes first. Model answer, for the feedback, not a grading checklist: "Fix 1, add an evidence column to the rules table: accept; rules 1 to 4 each get the evidence they rely on and who holds it. Fix 2, cite the claim that meters cannot be spoofed: accept; I mark it as my own view and add the firmware attack to the gaps section. Fix 3, add a cost estimate for power metering: defer to the ten-more-hours section; real, but the figures need a source I cannot get this week. Fix 4, turn the spec into a design: reject; the reader is the drafting secretariat, which needs rules it can adopt, not an attack analysis, so I answer the reviewer's point in the gaps section instead. Single-change recommendation (the evidence column): accepted, and it is first in my revision plan."
feedback-instructions:: If everything is accepted, ask which one they are least convinced by and what the reviewer might have misread. If a rejection has no reason, ask for one. If the single-change recommendation was deferred, ask what the reader loses without it. Three sentences. No praise.

#### Question: Open
id:: 06f9717c-49d6-48aa-a7b1-f84e9e802a0b
content::
\## Revision plan

The three changes you will make this week, in order, with hours against each, and what you drop if the first takes longer than planned.
assessment-instructions:: Score out of 100. 30: three changes, 10 each, each named concretely. 15: they are put in order. 30: hours against each change, 20 for giving them and 10 for a total that roughly fits the learner's remaining weekly budget (about three and a half hours at the default pace, more if the learner set a larger budget in their proposal). 25: a named drop, a specific change they cut if the first one overruns; "work faster" or "do it all anyway" earns none of these 25. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. Add the evidence column to the rules table, 1.5 hours. 2. Rewrite the gaps section to include the firmware attack and the power-metering gap, 1 hour. 3. Label each mechanism as deployed, prototyped or proposed, 1 hour. Total 3.5 hours. If the first change takes longer, I drop the maturity labels and move them to the ten-more-hours section."
feedback-instructions:: Check whether the first change is the one that most improves the deliverable for its reader, or the easiest. If the easiest, ask what the reader gets from it. Confirm the arithmetic in one sentence. If anything else is missing or wrong, name the most important thing. Then tell them what to bring to meeting 4: the one review point they rejected, and why. No praise.

#### Text
content::
\## Before meeting 4

Bring one review point you rejected and your reason. The group's job at the meeting is to red-team the rejection: they take the reviewer's side, you defend yours, and you leave knowing whether the rejection holds. Bring also the current state of your draft; you will be asked what is finished.
