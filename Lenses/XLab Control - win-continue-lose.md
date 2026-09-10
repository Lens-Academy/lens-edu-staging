---
id: '9082ff06-0c3e-40b6-a127-6de1fd0883db'
title: "Win/continue/lose scenarios and execute/replace/audit protocols"
tldr: "An attack that fails is not one thing. Either you caught it, which ends the game in your favour, or it fizzled quietly and the AI lives to try again. Buck Shlegeris names the three outcomes (win, continue, lose) and the protocol shape that produces them (execute, replace, audit), then runs the numbers on a real monitor."
summary_for_tutor: "Module 4. This lens supplies the vocabulary the rest of the module reuses: the three outcomes of an attack (WIN, we catch the attack and can shut down; CONTINUE, the attack fails silently so nobody is caught and the AI attacks again later; LOSE, the attack is executed and succeeds) and the three decisions of the protocol that produces them (EXECUTE the proposed action, REPLACE it via resampling, defer-to-trusted, trusted editing, abort, block or shutdown, or AUDIT it by sending it for human review). Sequence: a short lead-in written for Lens, then Shlegeris's post in five excerpts with XLab's six quick-recall prompts interleaved exactly where XLab places them (concentrated failure and attack after the setup; protocol and monitor after the protocol definition; auditing after the two decisions; the three outcomes after the safety calculation), then the closing worked example on the sleeper-agent probes, then Works cited. Only the lead-in and the Works cited callout are ours; everything else is XLab's placement over Shlegeris's text. If a learner conflates 'replace' with 'audit', ask what each one costs and what a false negative does in each case."
reading_minutes: 30
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Two triples worth memorising

The rest of Module 4 talks in the vocabulary this post introduces, so it is worth reading slowly enough to keep the six words.

The first triple is what happens each time a scheming AI attacks: we **win**, we **lose**, or the deployment **continues**. The move Shlegeris is making is to split "the attack failed" into two very different events, one where we caught the AI and one where nothing happened and the AI will try again.

The second triple is the protocol shape that produces those outcomes: a monitor scores each proposed action, and the protocol decides whether to **execute** or **replace** that action, and separately whether to **audit** it.

The setting assumed throughout is the concentrated failure, the subject of the previous lesson, [[../Lenses/XLab Control - what-is-high-stakes|What is High Stakes?]]. Two of the examples get their own lessons later in this module: [[../Lenses/XLab Control - rogue-deployments|AI catastrophes and rogue deployments]] and [[../Lenses/XLab Control - systems-architecture|A basic systems architecture for AI agents that do autonomous research]].

The post closes by putting real numbers through the framework, using the ROC curve of a linear probe from Anthropic's "Simple probes can catch sleeper agents".

#### Article
source:: [[../articles/shlegeris-wincontinuelose-scenarios-and-executereplaceaudit-protocols]]
to:: we’ll call those attempts “attacks”.

#### Question: Open
id:: d2f3e8e5-f9e7-49f5-9569-c030a2d9f29e
content:: What is a concentrated failure (a.k.a. high-stakes failure)?
max-chars:: 600
assessment-instructions:: A good answer says it is a failure where, in the absence of countermeasures, the AI could cause an unacceptable outcome just by behaving badly on a small number of tasks. Full credit does not require examples, but reward any of the reading's three: causing a rogue deployment, sabotaging one particularly crucial ML research task, or leaking sensitive information. Mark down an answer that describes a failure needing sustained bad behaviour across many tasks, since that is the opposite case. Do not over-validate and avoid generic praise.

#### Question: Open
id:: 78fc4ba1-776c-47ab-b71c-c4aa5034cc5d
content:: In AI control terminology, what is an "attack"?
max-chars:: 400
assessment-instructions:: A good answer says an attack is an attempt by the AI to cause the unacceptable outcome. Reward an answer that also notes the surrounding strategy, that the AI normally acts aligned and attacks only on very rare occasions. Do not require the learner to describe any specific attack technique, since the term is about intent, not method. Do not over-validate and avoid generic praise.

#### Article
from:: For concreteness, let’s talk about a particularly important simple class
to:: call its response the _monitor score_.

#### Question: Open
id:: 2234e527-4341-4e20-a037-68da9754b438
content:: How does an execute/replace/audit protocol work?
max-chars:: 800
assessment-instructions:: A good answer covers three moving parts: an agent loop repeatedly gets a proposed action from the untrusted LLM; a monitor scores how dangerous or suspicious that action looks; and the protocol uses the monitor's score to make two decisions, whether to execute the action or replace it, and whether to audit it. Reward an answer that keeps the replace decision and the audit decision separate. Mark down an answer that treats them as one threshold, since the reading argues they are better made separately. Do not over-validate and avoid generic praise.

#### Question: Open
id:: 1f88446b-db35-4c57-adf6-e8b9a9c0c4dd
content:: What is a monitor, and what is a monitor score?
max-chars:: 600
assessment-instructions:: A good answer says a monitor is any technique that takes a proposed action together with some surrounding context and produces a monitor score describing how dangerous or suspicious that action is. Reward naming any of the reading's examples: trusted or untrusted models evaluating the action, probes trained on off-policy examples or produced other ways, or interpretability techniques such as sparse autoencoders for detecting deceptive intent. Do not require a specific technique, since the point is that all of them share this input and output shape. Do not over-validate and avoid generic praise.

#### Article
from:: Then, based on the monitor score, we need to make two decisions.
to:: but it’s probably better to make the decisions separately.

#### Question: Open
id:: bb78eb9b-8027-4c6b-9085-cc47963a1bd3
content:: What is auditing?
max-chars:: 600
assessment-instructions:: A good answer says auditing is reviewing an action to determine whether it is evidence that the model is intentionally trying to cause problems. Reward the simplest version from the reading: put the action in a queue for eventual human review, with escalation if the reviewer is suspicious, possibly ending in the conclusion that the model is a misaligned power-seeker. Mark down an answer that describes auditing as blocking or fixing the action, since that is replacing, not auditing. Do not over-validate and avoid generic praise.

#### Article
from:: The two defensive actions of auditing and replacing have quite different safety properties.
to:: It’s easy to modify this rule of thumb to relax some of those assumptions.

#### Question: Open
id:: 88f5ca30-cbb0-40bc-b543-ae6855bd333e
content:: When the AI attacks under an execute/replace/audit protocol, what are the three possible outcomes?
max-chars:: 800
assessment-instructions:: A good answer names all three and says what each one is. Win: the attack is audited and the developer catches the AI. Lose: the attack is executed and succeeds. Continue: the attack fails silently, so the AI is not caught and the deployment goes on, with the AI probably attacking again later. Award partial credit per outcome correctly described. Reward an answer that notes why continue is distinct from win, that a silently failed attack yields no evidence against the model. Do not over-validate and avoid generic praise.

#### Article
from:: ## Example: analyzing the safety of defer-to-trusted using the probes from “Simple probes can catch sleeper agents”
to:: crucially depends on the details of the protocol in which the probe is being used as a monitor.

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
