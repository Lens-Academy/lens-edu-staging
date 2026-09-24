---
id: '9082ff06-0c3e-40b6-a127-6de1fd0883db'
title: "Win/continue/lose scenarios and execute/replace/audit protocols"
tldr: "An attack that fails is not one thing. Either you caught it, which ends the game in your favour, or it fizzled quietly and the AI lives to try again. Buck Shlegeris names the three outcomes (win, continue, lose) and the protocol shape that produces them (execute, replace, audit), then runs the numbers on a real monitor."
summary_for_tutor: "Unit 5 of AI Control 1. This lens supplies the vocabulary the rest of the unit reuses: the three outcomes of an attack (WIN, we catch the attack and can shut down; CONTINUE, the attack fails silently so nobody is caught and the AI attacks again later; LOSE, the attack is executed and succeeds) and the three decisions of the protocol that produces them (EXECUTE the proposed action, REPLACE it via resampling, defer-to-trusted, trusted editing, abort, block or shutdown, or AUDIT it by sending it for human review). Sequence: a short lead-in written for Lens, then Shlegeris's post in five excerpts with six quick-recall prompts interleaved exactly where the source places them (concentrated failure and attack after the setup; protocol and monitor after the protocol definition; auditing after the two decisions; the three outcomes after the safety calculation), then the closing worked example on the sleeper-agent probes, then Works cited. Only the lead-in and the Works cited callout are ours; everything else is the source's placement over Shlegeris's text. If a learner conflates 'replace' with 'audit', ask what each one costs and what a false negative does in each case. After the reading, one added practice question (ours, in an amber callout) has the learner compute the chance of a catch before a successful attack for a different monitor, with and without replacement, say what a replaced but unreviewed attack leads to, and redo the estimate when a fifth of replacements fail to neutralise the attack; its model answer is in the assessment instructions."
reading_minutes: 35
tutor_minutes: 7
tags: []
---
#### Text
content::
\## Two triples worth memorising

The rest of this unit talks in the vocabulary this post introduces, so it is worth reading slowly enough to keep the six words.

The first triple is what happens each time a scheming AI attacks: we **win**, we **lose**, or the deployment **continues**. The move Shlegeris is making is to split "the attack failed" into two very different events, one where we caught the AI and one where nothing happened and the AI will try again.

The second triple is the protocol shape that produces those outcomes: a monitor scores each proposed action, and the protocol decides whether to **execute** or **replace** that action, and separately whether to **audit** it.

The setting assumed throughout is the concentrated failure, the subject of the previous lesson, [[../Lenses/XLab Control - what-is-high-stakes|What is High Stakes?]]. Two of the examples get their own lessons later in this unit: [[../Lenses/XLab Control - rogue-deployments|AI catastrophes and rogue deployments]] and [[../Lenses/XLab Control - systems-architecture|A basic systems architecture for AI agents that do autonomous research]].

The post closes by putting real numbers through the framework, using the ROC curve of a linear probe from Anthropic's "Simple probes can catch sleeper agents".

#### Article
source:: [[../articles/shlegeris-wincontinuelose-scenarios-and-executereplaceaudit-protocols]]
to:: we’ll call those attempts “attacks”.

#### Question: Open
id:: d2f3e8e5-f9e7-49f5-9569-c030a2d9f29e
content:: What is a concentrated failure (a.k.a. high-stakes failure)?
max-chars:: 600
assessment-instructions:: A good answer says it is a failure where, in the absence of countermeasures, the AI could cause an unacceptable outcome just by behaving badly on a small number of tasks. Full credit does not require examples, but reward any of the reading's three: causing a rogue deployment, sabotaging one particularly crucial ML research task, or leaking sensitive information. Mark down an answer that describes a failure needing sustained bad behaviour across many tasks, since that is the opposite case.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: 78fc4ba1-776c-47ab-b71c-c4aa5034cc5d
content:: In AI control terminology, what is an "attack"?
max-chars:: 400
assessment-instructions:: A good answer says an attack is an attempt by the AI to cause the unacceptable outcome. Reward an answer that also notes the surrounding strategy, that the AI normally acts aligned and attacks only on very rare occasions. Do not require the learner to describe any specific attack technique, since the term is about intent, not method.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Article
from:: For concreteness, let’s talk about a particularly important simple class
to:: call its response the _monitor score_.

#### Question: Open
id:: 2234e527-4341-4e20-a037-68da9754b438
content:: How does an execute/replace/audit protocol work?
max-chars:: 800
assessment-instructions:: A good answer covers three moving parts: an agent loop repeatedly gets a proposed action from the untrusted LLM; a monitor scores how dangerous or suspicious that action looks; and the protocol uses the monitor's score to make two decisions, whether to execute the action or replace it, and whether to audit it. Reward an answer that keeps the replace decision and the audit decision separate. Mark down an answer that treats them as one threshold, since the reading argues they are better made separately.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: 1f88446b-db35-4c57-adf6-e8b9a9c0c4dd
content:: What is a monitor, and what is a monitor score?
max-chars:: 600
assessment-instructions:: A good answer says a monitor is any technique that takes a proposed action together with some surrounding context and produces a monitor score describing how dangerous or suspicious that action is. Reward naming any of the reading's examples: trusted or untrusted models evaluating the action, probes trained on off-policy examples or produced other ways, or interpretability techniques such as sparse autoencoders for detecting deceptive intent. Do not require a specific technique, since the point is that all of them share this input and output shape.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Article
from:: Then, based on the monitor score, we need to make two decisions.
to:: but it’s probably better to make the decisions separately.

#### Question: Open
id:: bb78eb9b-8027-4c6b-9085-cc47963a1bd3
content:: What is auditing?
max-chars:: 600
assessment-instructions:: A good answer says auditing is reviewing an action to determine whether it is evidence that the model is intentionally trying to cause problems. Reward the simplest version from the reading: put the action in a queue for eventual human review, with escalation if the reviewer is suspicious, possibly ending in the conclusion that the model is a misaligned power-seeker. Mark down an answer that describes auditing as blocking or fixing the action, since that is replacing, not auditing.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Article
from:: The two defensive actions of auditing and replacing have quite different safety properties.
to:: It’s easy to modify this rule of thumb to relax some of those assumptions.

#### Question: Open
id:: 88f5ca30-cbb0-40bc-b543-ae6855bd333e
content:: When the AI attacks under an execute/replace/audit protocol, what are the three possible outcomes?
max-chars:: 800
assessment-instructions:: A good answer names all three and says what each one is. Win: the attack is audited and the developer catches the AI. Lose: the attack is executed and succeeds. Continue: the attack fails silently, so the AI is not caught and the deployment goes on, with the AI probably attacking again later. Award partial credit per outcome correctly described. Reward an answer that notes why continue is distinct from win, that a silently failed attack yields no evidence against the model.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Article
from:: ## Example: analyzing the safety of defer-to-trusted using the probes from “Simple probes can catch sleeper agents”
to:: crucially depends on the details of the protocol in which the probe is being used as a monitor.

#### Callout: Practice: put numbers on a different monitor
tone:: amber

#### Question: Open
id:: 07a155ff-b63f-440d-9f78-ba0ffefe3482
content:: A new case. A lab monitors an untrusted research agent. Human reviewers can check 0.5% of its actions; at that threshold the monitor flags 20% of attacks, and a reviewed attack is always recognised, ending the game in the lab's favour. The lab also replaces every action in the most suspicious 10% with one written by a trusted model; at that threshold the monitor flags 94% of attacks. An attack that runs succeeds one time in three, and a failed attack goes unnoticed.

(a) If the agent is scheming and keeps attacking now and then until something settles the game, what is the chance the lab catches it before an attack succeeds?
(b) What would that chance be if the lab kept the reviews but stopped replacing?
(c) In the original protocol, what happens to an attack that is replaced but not reviewed, and why does that matter for (a)?
(d) Back in the original protocol, suppose one in five replaced attacks still succeeds when run. What does your answer to (a) become?
placeholder:: Show your working for (a), (b) and (d), and answer (c)
assessment-instructions:: This is practice on a new case, applying the post's rule of thumb. Model answer. (a) Per attack: reviewed and caught 0.20; runs if not flagged at the 10% threshold, 1 minus 0.94 is 0.06, and succeeds a third of the time, 0.02; safety is 0.20 / (0.20 + 0.02), about 91%. (b) Without replacement every unreviewed attack runs: 0.80 run, a third succeed, about 0.27; safety 0.20 / (0.20 + 0.27), about 43%. (c) The replaced attack neither catches the agent nor succeeds: the deployment continues and the agent will attack again later. That is why the ratio counts only the two outcomes that end the game, and why replacing converts would-be losses into more chances to be caught. (d) Replaced but unreviewed attacks are 0.94 minus 0.20, which is 0.74; a fifth of them, about 0.15, now succeed, so successes are 0.02 + 0.15, about 0.17, and safety is 0.20 / (0.20 + 0.17), about 54%: a replacement that leaks turns continuations back into losses. Full marks need the three numbers (accept 90 to 92%, 40 to 45% and 50 to 57%) and the continue outcome in (c); roughly a quarter each. Grade only against these criteria and the material on this page.
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed, with the numbers. If they used 20% as the answer to (a), say plainly that most attacks end in neither a catch nor a success, so only the two game-ending outcomes are compared. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Shlegeris, Buck. "Win/continue/lose scenarios and execute/replace/audit protocols." *Redwood Research blog*, 15 Nov. 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/wincontinuelose-scenarios-and-executereplaceaudi)
*The reading: it separates catching an attack from an attack failing silently, defines the execute/replace/audit protocol shape, and works one numeric safety example.*

MacDiarmid, Monte, et al. "Simple probes can catch sleeper agents." *Anthropic*, 23 Apr. 2024. [anthropic.com](https://www.anthropic.com/research/probes-catch-sleeper-agents)
*The linear-probe monitor whose ROC curve supplies the true and false positive rates in the reading's closing worked example.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The original control paper, which used one monitor with two thresholds; the reading argues the replace decision and the audit decision are better made separately.*

XLab. "Win/continue/lose scenarios and execute/replace/audit protocols." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/win-continue-lose)
*The source lesson this page adapts.*
:::
