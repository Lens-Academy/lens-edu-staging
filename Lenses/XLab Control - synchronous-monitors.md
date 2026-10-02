---
id: '5297ebc7-32c9-4d39-86db-ce19efc7ae71'
title: "Blocking live failures with synchronous monitors"
tldr: "A smoke alarm that reports yesterday's fire is still worth having. It is worth nothing against a fire that takes the house in ninety seconds. Some AI failures are the second kind: the weights are out, and there is nothing left to recover. Kaufman and Lucassen call those live failures, and ask what it costs to put the monitor in front of the action instead of behind it."
summary_for_tutor: "This lesson is marked optional in the source. The source writes no framing of its own here: the page is Kaufman and Lucassen's LessWrong post rendered whole, with five short recall prompts and one interactive figure inserted into it. Everything except the opening Text segment and the Works cited callout is theirs. Sequence: a short lead-in placing the post inside this unit's monitoring section (ours), then the post's opening on detection versus prevention with three recall prompts (two goals of monitoring, what makes a monitor synchronous, what a live failure is), then the section on attack latency and rate of damage, then the live-failure plane widget the learner taps through, a recall prompt on attack latency, the section on blocking monitors, a recall prompt on what makes a monitor blocking, and the post's closing options and cost discussion. The recall prompts are the source's tap-reveal cards converted to graded open questions; their model answers are in the assessment instructions and must not be handed to the learner before they answer. The post is explicit that its authors do not know how much risk live failures actually carry; do not let a learner leave thinking the priority question is settled."
reading_minutes: 10
tutor_minutes: 15
tags: []
---
#### Text
content::
\## Before you read

[[../Lenses/XLab Control - monitoring-and-mitigation|Monitoring and Mitigation]] opened this section with the question of what you do once a monitor fires, and [[../Lenses/XLab Control - control-monitoring-in-deployments|Practical challenges of control monitoring in frontier AI deployments]] worked through what monitoring costs at deployment scale. This post takes one slice of that: **when** the monitor runs.

Adam Kaufman and James Lucassen argue that the answer depends on the threat. Some attacks leave a grace period between the action and the harm, and a monitor that reads the transcript an hour later catches them just as well as one that reads it before the action executes. Others do not. The post names that second category **live failures**, and its examples are ones you have already met: weight exfiltration, and the [[../Lenses/XLab Control - rogue-deployments|rogue internal deployments]] you read about earlier.

The authors are candid that they do not know how much risk live failures actually carry, and say so directly: that uncertainty is why they cannot tell how much to prioritize synchronous monitoring. Read it as an argument about a category worth naming, not a settled priority.

#### Article
source:: [[../articles/kaufman-blocking-live-failures-with-synchronous-monitors]]
to:: We call actions “**live failures**” if their harmful effects are rapid and hard to recover from.

#### Question: Open
id:: d65cd045-258c-4def-b314-496ccc8ea4fa
content:: What are the two goals that monitoring serves?
assessment-instructions:: Score out of 100. 50: detection: spotting misbehaviour so you can understand it and stop similar actions in the future. 50: prevention: spotting misbehaviour in order to stop or limit the harm of that particular action. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer names two goals but describes the same thing twice. Model answer, for the feedback, not a grading checklist: "Detection: identifying misbehavior so you can understand it and prevent similar actions from happening in the future. Prevention: identifying misbehavior in order to mitigate the harmful effects of that particular action."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 0b5af592-b177-4417-b891-db7ce6ffbfd7
content:: What makes a monitor synchronous?
assessment-instructions:: Score out of 100. 60: it runs before the action is executed. 40: it runs after the model has generated the action, so it sees the actual proposed action: the monitor sits between generation and execution. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 20 if the answer only says the monitor runs quickly or in real time, without placing it before execution. Model answer, for the feedback, not a grading checklist: "It runs after an action is generated by the LLM but before the action is executed."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: e0afe6a5-ea44-45e4-9cf5-d263c2f11082
content:: What is a live failure? Give an example.
assessment-instructions:: Score out of 100. 40: the harm comes rapidly, soon after the action, leaving little or no time to stop it once the action has run. 40: the harm is hard to recover from: once done, it cannot easily be undone, or cleaning up is very costly. 20: a fitting example, such as weight exfiltration or a rogue internal deployment. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "An action whose harmful effects are rapid and hard to recover from, like a threat with low attack latency and a very high rate of damage, via damage already dealt or costs of recovery. A classic example is weight exfiltration."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: We’ve found these concepts useful in our threat modeling and research prioritization.
to:: We call these threats **live failures.**

#### Widget
source:: [[../widgets/xlab-control-live-failure-plane]]

#### Question: Open
id:: 6c167d13-dfde-4f37-80ed-0b77dd55bcdc
content:: What is attack latency, and what does it mean for when a monitor has to run?
assessment-instructions:: Score out of 100. 50: what it is: a grace period after an attack has been initiated but before any harm has been caused. 50: what it means for monitoring: within that period a monitor that reviews actions after they run (asynchronous) is just as effective as one that checks them before they run (synchronous), because catching the attack then still prevents the harm. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A "grace period" after an attack has been initiated but before any harm has been caused. Within it, an asynchronous monitor is exactly as effective as a synchronous one; e.g. a code backdoor detected before being exploited."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: The classic example of a live failure is
to:: Claude Code auto mode is an example of a blocking synchronous monitor.

#### Question: Open
id:: 418db0da-4c23-457e-9b73-f03205daf88e
content:: What makes a monitor "blocking"?
assessment-instructions:: Score out of 100. 40: it runs before the proposed action is executed. 60: it has the authority to stop suspicious actions from being executed, not just to report them. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It runs before the proposed action is executed and has the authority to prevent suspicious actions from being executed (e.g. Claude Code auto mode). Blocking monitors cost more than asynchronous ones: they add latency to every action and inference cost from monitoring each action individually rather than long trajectories at once."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: There are many options for what to do with actions that look too suspicious to execute.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Kaufman, Adam, and James Lucassen. "Blocking Live Failures with Synchronous Monitors." *LessWrong*, 30 Mar. 2026. [lesswrong.com](https://www.lesswrong.com/posts/e4G4E56ZiQqjXSxLp/blocking-live-failures-with-synchronous-monitors)
*The post this lesson assigns: the detection-versus-prevention split, attack latency and rate of damage as the two axes that decide whether an asynchronous monitor is enough, and the case for blocking monitors where they are not.*

XLab. "Blocking live failures with synchronous monitors." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/synchronous-monitors)
*The source lesson this page adapts.*
:::
