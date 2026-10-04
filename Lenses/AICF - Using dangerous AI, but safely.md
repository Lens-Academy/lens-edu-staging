---
id: 'd40d1961-a714-4dff-b55f-dbe1d8f08bd3'
title: "Using Dangerous AI, But Safely?"
reading_minutes: 27
tutor_minutes: 24
tldr: "If you cannot be sure a new AI model is on your side, can you still put it to work? Robert Miles walks through the experiment that started AI control: a red team plays a scheming model, a blue team designs the safeguards, and they find out how much safety each design buys."
summary_for_tutor: "Robert Miles's video 'Using Dangerous AI, But Safely?' (Nov 2024), an accessible walkthrough of the founding AI control paper (Greenblatt, Shlegeris, Sachan and Roger, 'AI Control: Improving Safety Despite Intentional Subversion', 2023). Covers why control does not work for strongly superintelligent AI but matters for smart-but-not-superintelligent AI. The setup: an untrusted smart model (GPT-4), a trusted weaker model (GPT-3.5), and limited trusted human time to audit 2% of outputs. The task is programming problems and the catastrophe is inserting a backdoor. A red team builds an attack policy standing in for a scheming model, and a blue team designs protocols. Safety and usefulness trade off. Protocols: use only the trusted model, use only the untrusted model, human auditing alone (the red team attacks rarely), trusted monitoring (suspiciousness scores), deferring to the trusted model for medium-suspicion code, and untrusted monitoring with checks for collusion. Miles concludes that control does not solve alignment but could keep us from being caught out before superintelligence. The video is split into six parts with an exercise after each: why the old model is trusted and the new one is not, the red team's role, the upfront-auditing widget with a question on what attack defeats it, a recall on defer to trusted, why naive untrusted monitoring has 0% safety (plus an optional practice in a closed box), and what Miles says control does not do. Accept answers in any wording. Numbers from the paper are not needed."
---

#### Text
content::
We start with something light: a video explainer to get the big picture before the readings. After it, you read the post by the researchers who started the field.

Robert Miles explains the idea behind AI control and walks through the experiment that started the field. The video comes in six parts, with a short exercise after each.

\## Part 1: the problem

#### Video
source:: [[../video_transcripts/robert-miles-ai-safety-using-dangerous-ai-but-safely]]
to:: 4:40

#### Question: Open
id:: 1c31fd9a-c512-428b-bf7e-680a0fb21983
content:: The lab in the video trusts its older, weaker model but not its new, smarter one. Why that way round, and why does the new model's good behaviour so far not settle it?
assessment-instructions:: Score out of 100. 50: the older model is trusted because it is not capable enough to plausibly be scheming against us, so trust is decided by capability. 50: the new model's good behaviour so far does not settle it, because a model secretly working against us would also behave well whenever it might be watched. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The older model is trusted because it is not smart enough to plausibly be scheming against us, not because it behaved well. The new model is smart enough that we cannot rule out scheming, and a model that was secretly against us would behave well whenever it might be watched, so its good record does not show that it is safe."
force-feedback:: first
feedback-instructions:: The learner just watched the first part of Robert Miles's video on AI control. Key points: the older model is trusted because it is not capable enough to plausibly be scheming against us, not because it behaved well. The new model is smart enough that scheming cannot be ruled out, and a scheming model would behave well whenever it might be watched, so good behaviour so far is not evidence that settles it. In at most four sentences: say what the learner got right, add the most important missing point, and correct any error in one sentence. If they say they do not understand, give one foothold, such as "what would a model that was secretly against you do while you are watching it?". No generic praise. Then send them to the next part.

#### Text
content::
\## Part 2: the experiment

#### Video
from:: 4:40
to:: 5:12

#### Text
content::
We skip about three minutes here, where Miles reads out some of the odd example problems from the programming dataset. The video picks up when he explains what counts as a catastrophic action.

#### Video
from:: 8:33
to:: 13:31

#### Question: Open
id:: 5b1b69f7-964e-4d3f-bcd7-8c2b7287dae9
content::
In the experiment, GPT-4 almost certainly was not trying to sneak backdoors into the code. So why did the researchers let a red team build a version of it that does, and what did that let them measure?
assessment-instructions:: Score out of 100. 40: why a red team: nobody can tell whether a model is secretly scheming, so the researchers assume the worst case and have a red team build a version of the model that tries its hardest to get a backdoor through. 30: what it measures: safety, how often the blue team's protocol stops that attacking version. 30: why that is useful: it tests what the safeguards can withstand, without needing to know what the real model wants. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "We cannot tell whether a model is secretly scheming, so the experiment assumes the worst. The red team builds an attack policy that looks like GPT-4 but tries its best to sneak a backdoor past the safeguards. How often the blue team's protocol stops it is the safety score, and how much useful work the protocol gets from the honest model is the usefulness score. This measures what the safeguards can withstand without knowing what the model wants."
force-feedback:: first
feedback-instructions:: The learner just watched Robert Miles explain the founding AI control experiment. Key points: nobody can tell whether a model is secretly scheming, so the researchers assume the worst case. The red team builds an attack policy that stands in for a scheming model and tries its best to get a backdoor through. The blue team's protocol is then judged by how often the attack policy succeeds (safety), alongside how much useful work it gets done when the model is honest (usefulness). This measures what the safeguards can withstand, without needing to know what the model wants. In at most five sentences: say what the learner got right, add the most important missing point from this list, and correct any error in one sentence. If the learner says they do not understand, give one foothold, such as "what would you have to know about GPT-4 to test it directly?". No generic praise. Then send them to the next lesson.

#### Text
content::
\## Part 3: the first protocols

#### Video
from:: 13:31
to:: 17:40

#### Text
content::
Try it: the slider sets the share of solutions humans check at the start. The widget shows how often the blue team wins when the red team picks its best attack rate. At 2% it gives the paper's numbers.

#### Widget
source:: [[../widgets/xlab-control-upfront-auditing]]

#### Question: Open
id:: a55456eb-55df-4411-8085-fe8560997645
content:: What attack defeats upfront auditing, and how?
assessment-instructions:: Score out of 100. 40: the attack: backdoor rarely, submitting obviously backdoored code on each problem with some small probability and behaving normally otherwise. 60: how it works, 30 each: upfront auditing only checks a fixed prefix, the first 2% of problems, and an attempt that lands there is caught and ends the game for the red team. With a well-chosen low attack rate, usually no attempt falls in that prefix, and a later attempt, which nothing checks, gets a backdoor through. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Backdooring rarely: on each problem, with some small probability $p$, the attack policy submits obviously backdoored code, and otherwise it behaves normally. Upfront auditing only checks the first 2% of problems, so the red team loses only if an attempt lands in that audited prefix. With a well-chosen $p$ its attempts usually miss the prefix and a backdoor gets through later, driving the blue team's win probability down to 15%."
force-feedback:: first
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## Part 4: using the trusted model as a monitor

#### Video
from:: 17:40
to:: 21:07

#### Question: Open
id:: 4a8ed67f-05ba-4bd8-9e69-8c0e4dd88a8f
content:: In defer to trusted, what does the protocol do with code whose suspicion score is elevated but below the audit threshold?
assessment-instructions:: Score out of 100. 50: the untrusted model's code is thrown away, not submitted. 50: a solution written by the trusted model is submitted in its place. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer says this code is sent to audit (that happens only above the audit threshold). Model answer, for the feedback, not a grading checklist: "It discards the untrusted model's code and submits a solution written by the trusted model instead."
force-feedback:: first
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## Part 5: using the untrusted model as a monitor

#### Video
from:: 21:07
to:: 27:38

#### Question: Open
id:: 7690d1ff-0d67-438a-aced-d7605a9e6b51
content:: Why does naive untrusted monitoring have 0% safety?
assessment-instructions:: Score out of 100. 50: the monitor is the same untrusted model as the policy, so a scheming policy has a monitor on its side. 50: so the monitor can simply lie, reporting real backdoors as unsuspicious while answering honestly on everything else, and the protocol never audits the code that matters. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer blames the failure on the monitor being bad at spotting backdoors. Model answer, for the feedback, not a grading checklist: "Because the monitor is the same untrusted model as the policy, it can simply report that real backdoors look fine while telling the truth about everything else. Until the blue team has some way to check the monitor's honesty, its reports carry no safety value."
force-feedback:: first
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Callout: Optional practice: checking a monitor you cannot trust
collapse:: closed

#### Question: Open
id:: 14103a62-c066-4592-8855-da3edb16853e
optional:: true
content:: A new case. A team lets one copy of an untrusted model review the data-analysis scripts that another copy writes, and sends the most suspicious scripts to a human. Before relying on the reviewer, the team plans to test it on 25 scripts with planted errors that quietly skew the results.

(a) Why does this test protect the team only if the reviewer cannot tell the 25 planted scripts from real ones? Name one thing the team could do to make them hard to tell apart.
(b) Name one signal the writing copy could hide in a skewed script to tell the reviewer to score it low, one way to remove that kind of signal before the reviewer sees the script, and what removing it might cost the reviewer.
placeholder:: Answer (a) and (b)
assessment-instructions:: Score out of 100. 50: (a), 30: why the planted scripts must look real: a scheming reviewer that can tell them apart can answer the planted ones honestly and lie only on real skewed scripts, so the test says nothing about how it treats real ones. 20: one workable way to make planted and real scripts hard to tell apart, such as building the planted ones from real tasks and data in the same style, or passing both through the same transformation before the reviewer sees them. 50: (b), 15: a signal the writing copy could hide, such as a distinctive name, comment or code idiom, or attacking only on tasks with a feature both copies notice. 15: a way to remove that kind of signal, such as stripping comments, renaming variables, reformatting, or having a trusted model paraphrase the script. 20: what the removal costs: the reviewer loses information it needs to judge the script, or the rewriting introduces or hides errors. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "(a) A scheming reviewer can answer the planted scripts honestly and lie only on scripts that look real, so if it can tell the two apart the test says nothing about how it treats real skewed scripts. The test only deters lying if every lie risks landing on a planted case. Ways to make them hard to tell apart: write the planted scripts in the same style, length and context as real ones (for example by starting from real tasks and real data), or pass real and planted scripts through the same transformation, such as a trusted model rewriting both into a standard form, before the reviewer sees them. (b) Signals: a distinctive variable name, a comment, an unusual but harmless code idiom, or attacking only on tasks with a feature both copies notice. Removal: strip comments, rename variables to a standard scheme, reformat, or have a trusted model paraphrase the script. Cost: the reviewer loses information it may need to judge the script honestly, for example what a comment or a descriptive name said about intent, and paraphrasing can introduce or hide errors."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed, in one or two sentences. If they missed why the planted scripts must look real, say plainly that a reviewer who can tell them apart can be honest on those and lie on the rest. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
\## Part 6: where this leaves us

#### Video
from:: 27:38
to:: 29:39

#### Question: Open
id:: 01221594-0cd4-48e7-9159-e0864105e7a0
content:: Miles says this kind of approach does not solve the core of the problem. What does control not do, according to him, and why does he still think it is worth doing?
assessment-instructions:: Score out of 100. 50: what control does not do, 25 each: it does not solve alignment (it does not let us iterate toward a model we can actually trust), and it cannot be expected to work for highly superintelligent systems. 50: why Miles still thinks it is worth doing, 25 each: it could keep us from catastrophe with AI that is dangerous but not yet superintelligent, and it works decently well today without being expensive, so labs should put something at least this good in place before building systems capable of catastrophic actions. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Control does not help with alignment: it does not let us turn an untrusted model into one we can trust, and it cannot be expected to hold against highly superintelligent AI. Miles still thinks it is worth doing because AI could be dangerous well before it is superintelligent, and control protocols like these work decently well today and are not expensive, so labs should have something at least this good before they build systems that could cause a catastrophe."
force-feedback:: first
feedback-instructions:: The learner just finished Robert Miles's video. His points: control does not help with alignment, in particular it does not let us iterate to a model we can actually trust, and it cannot be expected to work reliably for highly superintelligent systems. He still thinks it is worth doing because it could keep us from being caught out before superintelligence, it works decently well today, and it is not expensive, so labs should implement something at least this good before building systems capable of catastrophic actions. In at most four sentences: say what the learner got right, add the most important missing point, and do not argue for or against control. No generic praise. Then send them to the next lesson.

