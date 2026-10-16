---
id: 'a7b91aae-d300-440f-80a4-fa7fe3616203'
title: "Do control protocols hold up?"
reading_minutes: 4
tutor_minutes: 5
tldr: "Two recent experiments gave the attacker in a control evaluation more cunning: prompt injections aimed at the monitor, and choosing when to attack or abort. Both lowered measured safety a lot. Both sets of authors work to improve control evaluations, so read them as stress tests and ask what they show about the criticism that control does not work."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, Module 'Practical problems', second lens of the submodule on the criticism that control will not work for the AIs that matter most: do today's evaluations overstate safety? The learner reads the abstracts of both papers. (1) Terekhov, Panfilov, Dzenhaliou, Gulcehre, Andriushchenko, Prabhu, Geiping, 'Adaptive Attacks on Trusted Monitors Subvert AI Control Protocols' (arXiv, October 2025, revised March 2026): most protocols rest on an LLM monitor, 'a central point of failure'. An untrusted model that knows the protocol and the monitor embeds prompt injections in its outputs, and 'frontier models consistently evade diverse monitors' on two control benchmarks. Defer-to-Resample 'even backfires', because resampling turns the injection into a best-of-n attack. Their recommendation: adaptive attacks 'should become a standard component of evaluations'. (2) Ge-Wang, Crosse, Hadad, Schaeffer, Potham, Tracy, 'Attack Selection in Agentic AI Control Evaluations Meaningfully Decreases Safety' (arXiv, June 2026). Tyler Tracy works at Redwood Research. A start policy (when to attack) and a stop policy (when to abort) each lowered measured safety at a 1% audit budget: start by 20 percentage points on BashArena and LinuxArena, stop by 20 (BashArena) and 28 (LinuxArena). The authors say these are upper bounds, that existing evaluations 'may therefore yield overly optimistic safety estimates', and recommend that evaluations, system cards and safety cases elicit attack selection. Both papers are written by people improving control evaluations, not by critics of control. They show that today's monitor-based protocols can be evaded and that evaluations may overstate safety; Defer-to-Resample even backfires. The authors' own reply is to make evaluations harder, which turns part of the criticism into 'today's evaluations overstate safety' rather than 'control cannot work'. The question is scored. Do not tell the learner whether control works."
---
#### Text
content::
**The criticism: control evaluations overstate safety.**


Some terms you will need:

- **Monitor:** the model that reads what the untrusted model does and flags suspicious actions.
- **Prompt injection:** text written to give instructions to whichever model reads it.
- **Audit budget:** the share of actions that humans can afford to check.
- **pp:** percentage points.
- **BashArena, LinuxArena:** test environments in which an AI agent does real tasks on a computer and may try to sneak in an attack along the way.

[^cite-pivotal-tracy]: Pivotal Research, *Tyler Tracy*, profile page. [Pivotal](https://www.pivotal-research.org/tyler-tracy)

#### Text
content::
**1. Mikhail Terekhov, Jonas Geiping and colleagues, "Adaptive Attacks on Trusted Monitors Subvert AI Control Protocols".** In the abstract, Defer-to-Resample is a protocol that asks the untrusted model for a new answer when the first one looks suspicious. A best-of-n attack tries many times and keeps whichever attempt gets through.

#### Article
source:: [[../articles/terekhov-adaptive-attacks-on-trusted-monitors-subvert-ai-control-protocols]]
from:: "## Abstract"
to:: should become a standard component of evaluations for future AI control mechanisms.

#### Text
content::
**2. Catherine Ge-Wang, Tyler Tracy and colleagues, "Attack Selection in Agentic AI Control Evaluations Meaningfully Decreases Safety".** Its abstract:

#### Article
source:: [[../articles/ge-wang-attack-selection-in-agentic-ai-control-evaluations-meaningfully-decreases-safety]]
from:: "###### Abstract"
to:: elicit attack selection to produce more realistic safety estimates.

#### Question: Open
id:: 70170643-f9e8-43f6-8215-252779c14007
force-feedback:: first
content::
\## A lab's 99%

A lab reports that its control protocol caught 99% of attacks in testing. Based on these two papers, what two questions would you ask about how it was tested, and why?
placeholder:: Two questions, each with a reason.
assessment-instructions:: Score out of 100, 50 for each question. Context for grading: Terekhov et al. found that an untrusted model that knows the protocol and the monitor can hide prompt injections in its outputs and get past monitors, and that Defer-to-Resample made this attack stronger. Ge-Wang et al. found that letting the attacker choose when to attack and when to abort lowered measured safety by 20 to 28 percentage points at a 1% audit budget, and that evaluations without this may overstate safety. For each question: 25 if it checks something one of the papers showed can change the result, and 25 for a reason that names that result. Fitting questions: did the attacker know the protocol and the monitor model, did it try prompt injections against the monitor, did it choose when to attack or abort, or did it attack on every task, which protocol was used (Defer-to-Resample can backfire), what audit budget was assumed. A question that would fit any test (for example "how many tasks were there?") earns 0 for that question unless the reason ties it to one of the papers. Two questions about the same result each earn credit if they ask different things. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Did the attacker know the monitor and try prompt injections on it? Terekhov et al. showed that such an attacker gets past monitors. Did the attacker choose when to attack and when to give up? Ge-Wang et al. showed that this lowers measured safety by 20 to 28 points, so a test without it may overstate safety."
feedback-instructions:: The learner turns the two papers into two questions about a lab's claim that its protocol caught 99% of attacks. Terekhov et al.: an attacker that knows the protocol and the monitor hides prompt injections and gets past monitors, and Defer-to-Resample made the attack stronger. Ge-Wang et al.: choosing when to attack and when to abort lowered measured safety by 20 to 28 percentage points at a 1% audit budget. Good questions check whether the test included such attackers, which protocol was used, or the audit budget. Name the strongest part of the answer, then the single most useful fix. If a question would fit any test, ask which result from the papers it relates to. If the learner asks about their score, say plainly what earned and lost points. If they say they do not understand, give one foothold: ask what the attacker in each paper could do that a simple attacker cannot. One or two turns, 60 to 120 words each. No generic praise. Do not say whether control works.
