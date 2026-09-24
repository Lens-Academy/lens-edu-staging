---
id: '55f577c3-8146-4d5f-ab7a-1680dd5712c3'
learning-outcome: {--{"author":"James's AI","timestamp":1790257158782}@@"Explain--}{++{"author":"James's AI","timestamp":1790257158782}@@"Given a deployment in which an untrusted model's actions pass through some combination of scoring by a weaker trusted model, rewriting, resampling and a limited human audit budget, judge whether it prevents an unacceptable outcome if the untrusted model is scheming, name++} the {--{"author":"James's AI","timestamp":1790257158782}@@control protocol for Control under conservative assumptions"--}{++{"author":"James's AI","timestamp":1790257158782}@@conditions the answer turns on (such as the capability gap between the two models, the audit budget, collusion between copies of the untrusted model, or what the untrusted model remembers between attempts), and do so without relying on evidence about how the model usually behaves."++}
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: intermediate
{++{"author":"James's AI","timestamp":1790257158782}@@requires:
  - "[[Trusted versus untrusted models]]"
authors:
  - Elias+Claude
++}tags:
  - {--{"author":"James's AI","timestamp":1790257158782}@@skill-tree-placeholder--}{++{"author":"James's AI","timestamp":1790257158782}@@wip++}
---{++{"author":"James's AI","timestamp":1790257346961}@@
## Test:
id:: e1f74c84-5fb3-46d3-bb61-532c6de76031

#### Question: Open
id:: 4455209b-ee23-4bb8-ba56-224b9fcc63e9
content::
A frontier model U works as an agent on a lab's internal servers, doing maintenance tasks one shell command at a time. U may be scheming. The unacceptable outcome is U switching off logging on any server.

- A much weaker model T, which is not capable of scheming, sees the task description and each command U proposes, and scores the command for suspicion before it runs. T's scoring instructions are fixed.
- Commands scoring in the top 1% are held and sent to a human auditor, who inspects them carefully.
- Commands scoring in the next 9% are not run and not reviewed. Instead, U is sampled again for that step, from the same starting point.
- All other commands run, and every command that runs is logged.
- To help with long tasks, U keeps a notes file that it can read and write throughout a task. The notes file is not rolled back when a step is resampled.
- U has handled 30,000 tasks in testing, and every command of U's that reached the auditor was judged harmless.

1. If U is scheming, does this setup reliably prevent the unacceptable outcome?
2. Name the conditions your answer depends on, and explain how each one helps or hurts.
placeholder:: Your judgment and the conditions it depends on
assessment-instructions:: Score 0 to 100. The capability being tested is judging a protocol under the assumption that the untrusted model is actively scheming and naming the variables that decide it. Load-bearing elements: (1) about 25 points: reasons under the worst-case assumption, as if U attacks whenever doing so pays off. Explicitly dismissing the clean testing record is not required; reasoning from the worst case is enough. The learner may conclude "no", "not reliably", or "only if" conditions hold; any of these is acceptable if justified. Gating: if the judgment in part 1 rests on the clean record (for example "30,000 clean tasks show U is not scheming"), cap the total at 40. (2) about 75 points: names conditions and explains their effect. Candidates: (a) the capability gap between U and T, since a much weaker T may fail to score a well-disguised command as suspicious, letting it run; (b) the audit budget, since only the top 1% is ever inspected; (c) the discard band: an attempt that lands in the next 9% is thrown away unseen, so evidence that could have caught U is wasted and U can try again at no risk, while only attempts landing in the top 1% risk being caught; credit a learner who notes that discarding is still safer than running those commands; (d) the notes file undermines the protection resampling normally gives. Resampling works because a model that keeps no memory between attempts does not know its earlier attempt was flagged, so it must either attack again (and look more suspicious) or behave. With a notes file, U can record what it tried, notice that an attempt vanished, and adjust, and it can coordinate a plan across steps and across samples that T never sees, so each individual command can look harmless. Full credit for (d) needs the link to how resampling works; noting only that U "can plan in the notes" earns half credit on (d). (e) spreading the attack over several innocuous-looking commands whose combination disables logging; (f) any other correct mechanism tied to a specific feature of this setup, such as U learning what T flags because T's instructions are fixed and discarded attempts carry no risk; (f) satisfies the pass requirement like (c) to (e). Scoring of element 2: full credit needs at least two conditions with a correct mechanism, including at least one of (c) to (f); up to 30 of the 75 if the only conditions named are generic ones such as (a) and (b). Do not require any protocol names such as "trusted monitoring" or "resampling". Do not penalise additional valid failure modes, and credit a learner who points out an inconsistency or ambiguity in the setup. A pass is roughly 60 and requires at least one of (c) to (f) with a correct mechanism.
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner leaned on U's clean record, explain in one sentence why that evidence does not bear on a scheming U. If they missed what happens to discarded commands or what the notes file does to resampling, point to that feature of the setup without spelling out the whole answer. Do not reveal or discuss the numerical score. At most six sentences.++}
