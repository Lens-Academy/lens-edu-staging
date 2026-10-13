---
id: 'a7b91aae-d300-440f-80a4-fa7fe3616203'
title: "Do control protocols hold up?"
reading_minutes: 4
tutor_minutes: 12
tldr: "Two recent experiments gave the attacker in a control evaluation more cunning: prompt injections aimed at the monitor, and choosing when to attack or abort. Both lowered measured safety a lot. Both sets of authors work to improve control evaluations, so read them as stress tests and ask what they show about the criticism that control does not work."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. Empirical material for the 'does not work' kind of criticism. The learner reads most of one abstract and all of another. (1) Terekhov, Panfilov, Dzenhaliou, Gulcehre, Andriushchenko, Prabhu, Geiping, 'Adaptive Attacks on Trusted Monitors Subvert AI Control Protocols' (arXiv, October 2025, revised March 2026): most protocols rest on an LLM monitor, 'a central point of failure'. An untrusted model that knows the protocol and the monitor embeds prompt injections in its outputs, and 'frontier models consistently evade diverse monitors' on two control benchmarks. Defer-to-Resample 'even backfires', because resampling turns the injection into a best-of-n attack. Their recommendation: adaptive attacks 'should become a standard component of evaluations'. (2) Ge-Wang, Crosse, Hadad, Schaeffer, Potham, Tracy, 'Attack Selection in Agentic AI Control Evaluations Meaningfully Decreases Safety' (arXiv, June 2026). Tyler Tracy works at Redwood Research. A start policy (when to attack) and a stop policy (when to abort) each lowered measured safety at a 1% audit budget: start by 20 percentage points on BashArena and LinuxArena, stop by 20 (BashArena) and 28 (LinuxArena). The authors say these are upper bounds, that existing evaluations 'may therefore yield overly optimistic safety estimates', and recommend that evaluations, system cards and safety cases elicit attack selection. Both papers are written by people improving control evaluations, not by critics of control. They support the 'does not work' kind (today's monitor-based protocols can be evaded, and evaluations may overstate safety), and Defer-to-Resample is a small 'makes things worse' case. The authors' own reply is to make evaluations harder, which turns part of the criticism into 'today's evaluations overstate safety' rather than 'control cannot work'. The three questions are scored. Do not tell the learner whether control works."
---
#### Text
content::
The criticisms so far in this unit are arguments. Here are two experiments that tested control protocols against a more cunning attacker. Both were written by researchers who work on making control evaluations better. In the second paper, the last author, Tyler Tracy, works at Redwood Research.[^cite-pivotal-tracy] So read them as stress tests that control researchers ran on their own methods, not as arguments against control.

Some terms you will need:

- **Monitor:** the model that reads what the untrusted model does and flags suspicious actions.
- **Prompt injection:** text written to give instructions to whichever model reads it.
- **Audit budget:** the share of actions that humans can afford to check.
- **pp:** percentage points.

[^cite-pivotal-tracy]: Pivotal Research, *Tyler Tracy*, profile page. [Pivotal](https://www.pivotal-research.org/tyler-tracy)

#### Text
content::
**1. Mikhail Terekhov, Jonas Geiping and colleagues, "Adaptive Attacks on Trusted Monitors Subvert AI Control Protocols"**[^cite-terekhov-2025]. From the abstract:

> In practice, most AI control protocols are fundamentally based on LLM monitors, which can become a central point of failure. We study adaptive attacks by an untrusted model that knows the protocol and the monitor model, which is plausible if the untrusted model was trained with a later knowledge cutoff or can search for this information autonomously. We instantiate a simple adaptive attack vector by which the attacker embeds publicly known or zero-shot prompt injections in the model outputs. Using this tactic, frontier models consistently evade diverse monitors and complete malicious tasks on two main AI control benchmarks. The attack works universally against current protocols that rely on a monitor. Furthermore, the recent Defer-to-Resample protocol even backfires, as its resampling amplifies the prompt injection and effectively reframes it as a best-of-n attack. In general, adaptive attacks on monitor models represent a major blind spot in current control protocols and should become a standard component of evaluations for future AI control mechanisms.

(Defer-to-Resample asks the untrusted model for a new answer when the first one looks suspicious. A best-of-n attack tries many times and keeps whichever attempt gets through.)

**2. Catherine Ge-Wang, Tyler Tracy and colleagues, "Attack Selection in Agentic AI Control Evaluations Meaningfully Decreases Safety"**[^cite-ge-wang-2026]. Its abstract:

[^cite-terekhov-2025]: Mikhail Terekhov, Alexander Panfilov, Daniil Dzenhaliou, Caglar Gulcehre, Maksym Andriushchenko, Ameya Prabhu and Jonas Geiping (2025, revised 2026), *Adaptive Attacks on Trusted Monitors Subvert AI Control Protocols*. [arXiv](https://arxiv.org/abs/2510.09462)
[^cite-ge-wang-2026]: Catherine Ge-Wang, Tyler Crosse, Benjamin Hadad IV, Joachim Schaeffer, Ram Potham and Tyler Tracy (2026), *Attack Selection in Agentic AI Control Evaluations Meaningfully Decreases Safety*. [arXiv](https://arxiv.org/abs/2606.06529)

#### Article
source:: [[../articles/ge-wang-attack-selection-in-agentic-ai-control-evaluations-meaningfully-decreases-safety]]
from:: "###### Abstract"
to:: elicit attack selection to produce more realistic safety estimates.

#### Question: Open
id:: ed531c6a-3d9d-4f1f-b8b0-ed887f614ac1
force-feedback:: first
content::
\## What do these results show?

Which kind of criticism do these two results support most directly: control does not work, works but is not worth the effort, or works and makes things worse? Why?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: the two results are: (a) an untrusted model that knows the protocol and the monitor hid prompt injections in its outputs and got past monitors on two control benchmarks, and one protocol (Defer-to-Resample) made the attack stronger, and (b) letting the attacker choose when to attack and when to abort lowered measured safety by 20 to 28 percentage points at a 1% audit budget, so current evaluations may overstate safety. Give 100 for "control does not work" (or "control as currently built and evaluated may not work") with a reason taken from either result: monitors can be evaded, or evaluations report too high a safety figure. Also give 100 for "works and makes things worse" when the reason is that a protocol made the attack stronger or that an overstated safety figure gives false confidence. Give 50 for a fitting kind with no reason, and 0 for "not worth the effort" unless the reason given fits the results. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Mainly 'does not work': monitors that most protocols rely on could be fooled by prompt injections, and attackers that pick their moment make evaluations report too high a safety figure. Defer-to-Resample backfiring is a small 'makes things worse' case."
feedback-instructions:: The learner sorts two experiments that stress-tested control by the kind of criticism they support: Terekhov et al. (prompt injections against the monitor, Defer-to-Resample backfiring) and Ge-Wang et al. (attack selection lowered measured safety by 20 to 28 percentage points at a 1% audit budget, upper bounds). Mainly "does not work", with Defer-to-Resample as a small "makes things worse" case. Accept a reasoned alternative. Name the strongest part of the answer, then the single most useful fix. If the learner dismisses the results, ask what the 20 to 28 point drop means for a safety figure a company reports today. If the learner asks about their score, say plainly what earned and lost points. If they say they do not understand, give one foothold: ask what the monitor is supposed to do and what a prompt injection does to it. One or two turns, 60 to 120 words each. No generic praise. Do not say whether control works.

#### Question: Open
id:: 9543396c-abfe-4037-bce2-92ecc1dbc4d3
force-feedback:: first
content::
\## What they do not show

Name one thing that the two experiments, the prompt injections against monitors and the attack selection results, do not show.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: in the first experiment, an untrusted model that was given knowledge of the protocol and the monitor hid prompt injections in its outputs and got past monitors on two control benchmarks, and one protocol (Defer-to-Resample) made the attack stronger. In the second, letting the attacker choose when to attack and when to abort lowered measured safety by 20 to 28 percentage points at a 1% audit budget. Its authors call these numbers upper bounds. The question asks for one limit of what these results show, with a reason. Examples: they test today's protocols and benchmarks, not whether better-designed protocols could hold. The attacker was given knowledge of the protocol and the monitor. The second paper's numbers are upper bounds. The settings are benchmarks, not real deployments. They do not show that control is worse than no control. Give 100 for a limit that fits the results with a reason, 60 for a fitting limit with no reason, 30 for a generic limit that would fit any study. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "They do not show that no protocol can hold. They tested today's protocols on benchmarks, with an attacker that was told how the protocol and the monitor work."
feedback-instructions:: The learner names one thing the two experiments do not show. Possible limits: they test today's protocols and benchmarks, not better-designed ones, the attacker was given knowledge of the protocol and the monitor, the attack selection numbers are upper bounds, the settings are benchmarks, not real deployments, and neither paper shows that control is worse than no control. Name the strongest part of the answer, then the single most useful fix. If the learner concludes control is refuted, ask what a protocol would need to survive these attacks and whether the papers test that. Connect to Unit 1's control evaluations and to Jozdien's point that control needs good capability evaluations, if relevant. If the learner asks about their score, say plainly what earned and lost points. If they say they do not understand, give one foothold: ask what the attacker was told and where the tests were run. One or two turns, 60 to 120 words each. No generic praise. Do not say whether control works.

#### Question: Open
id:: e9748572-8808-4dfd-8ade-8d7aa56b33e6
force-feedback:: first
content::
\## What the authors propose

What do the authors of the two papers propose themselves? Given that, how much is left standing of the criticism these results support?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: both papers are by researchers who work on improving control evaluations, one of them at Redwood Research. Terekhov et al. found that an untrusted model hiding prompt injections in its outputs got past monitors, and say adaptive attacks "should become a standard component of evaluations". Ge-Wang et al. found that letting the attacker choose when to attack and when to abort lowered measured safety by 20 to 28 percentage points, say existing evaluations "may therefore yield overly optimistic safety estimates", and recommend that evaluations, system cards and safety cases elicit attack selection. 40 for the authors' proposal: make adaptive attacks, or attack selection, a standard part of control evaluations (the second paper also names system cards and safety cases). 60 for what it means: the authors treat this as a fixable gap in how control is tested, so the criticism shifts toward "today's evaluations overstate safety" rather than "control cannot work", while the open question of whether stronger evaluations will still find protocols that hold remains. Give 30 of these 60 for an answer that only says the criticism is weakened or not, without saying how. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Both sets of authors want evaluations to include these attacks. That treats the problem as a gap in testing, so the criticism becomes 'today's safety numbers are too optimistic' more than 'control cannot work', though whether protocols survive harder tests is still open."
feedback-instructions:: The learner says what the authors of the two experiments propose and what that leaves of the criticism. Both sets of authors work on improving control evaluations, one at Redwood. Terekhov et al. want adaptive attacks to be a standard part of evaluations. Ge-Wang et al. want evaluations, system cards and safety cases to elicit attack selection, and say existing evaluations may give overly optimistic safety estimates. This turns part of the criticism into "today's evaluations overstate safety" rather than "control cannot work", while whether protocols survive harder tests stays open. Name the strongest part of the answer, then the single most useful fix. If the learner treats the papers as written by opponents of control, point out that the authors propose fixes to evaluations. If the learner asks about their score, say plainly what earned and lost points. If they say they do not understand, give one foothold: ask what the authors want future evaluations to include. One or two turns, 60 to 120 words each. No generic praise. Do not say whether control works.
