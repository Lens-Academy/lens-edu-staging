---
id: 'd40d1961-a714-4dff-b55f-dbe1d8f08bd3'
title: "Using Dangerous AI, But Safely?"
reading_minutes: 27
tutor_minutes: 20
tldr: "If you cannot be sure a new AI model is on your side, can you still put it to work? Robert Miles walks through the experiment that started AI control: a red team plays a scheming model, a blue team designs the safeguards, and they find out how much safety each design buys."
summary_for_tutor: "Robert Miles's video 'Using Dangerous AI, But Safely?' (Nov 2024), an accessible walkthrough of the founding AI control paper (Greenblatt, Shlegeris, Sachan and Roger, 'AI Control: Improving Safety Despite Intentional Subversion', 2023). Covers why control does not work for strongly superintelligent AI but matters for smart-but-not-superintelligent AI. The setup: an untrusted smart model (GPT-4), a trusted weaker model (GPT-3.5), and limited trusted human time to audit 2% of outputs. The task is programming problems and the catastrophe is inserting a backdoor. A red team builds an attack policy standing in for a scheming model, and a blue team designs protocols. Safety and usefulness trade off. Protocols: use only the trusted model, use only the untrusted model, human auditing alone (the red team attacks rarely), trusted monitoring (suspiciousness scores), deferring to the trusted model for medium-suspicion code, and untrusted monitoring with checks for collusion. Miles concludes that control does not solve alignment but could keep us from being caught out before superintelligence. The video is split into six parts with short scored questions after each, mostly on the terms Miles introduces: trusted and untrusted models, the red and blue teams, usefulness and safety, upfront auditing (plus a widget and a question on the attack that beats it), trusted monitoring, defer to trusted, untrusted monitoring and how the blue team caught a lying monitor, and what Miles says control does not do. An optional practice question sits in a closed box in part 5. Accept answers in any wording. Numbers from the paper are not needed."
---

#### Text
content::
Next, a video that shows how the ideas you just read about are tested. After it, you read the post by the researchers who started the field.

Robert Miles explains the idea behind AI control and walks through the experiment that started the field. The video comes in six parts, with a short exercise after each.

\## Part 1: the problem

#### Video
source:: [[../video_transcripts/robert-miles-ai-safety-using-dangerous-ai-but-safely]]
to:: 4:40.3

#### Question: Open
id:: 81d7dd3e-5283-45b5-8441-20f408005afd
content:: What is an untrusted model, and what is a trusted model? Why is the new model in the video untrusted?
assessment-instructions:: Score out of 100. 35: an untrusted model is one that might be secretly working against us (scheming), so we cannot rely on it behaving well. 35: a trusted model is one we are confident is not doing that, in the video because it is not smart enough to be scheming. 30: the new model is untrusted because it is smart enough that it might be, and we do not know whether it wants what we want. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "An untrusted model is one that might be secretly working against us, so we cannot count on it. A trusted model is one we are confident is not, here because it is too weak to scheme. The new model is untrusted because it is smart enough that it might be scheming, and we do not know whether it wants what we want."
force-feedback:: first
feedback-instructions:: The learner just watched part of Robert Miles's video on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the relevant moment in the clip (where he lists what the lab has: a few humans, an older trusted model and the new model). No follow-up question. No generic praise.

#### Text
content::
\## Part 2: the experiment

#### Video
from:: 4:22.6
to:: 13:32.5
skip:: 5:12.3-8:34.7 "Miles reads example problems from the dataset"

#### Question: Open
id:: 5757a6a6-49c7-4e31-bb19-2e69b20b3deb
content:: What do the red team and the blue team each do in the experiment?
assessment-instructions:: Score out of 100. 50: the red team builds an attack policy, a version of the untrusted model that secretly tries to get a backdoor into the code without being caught, and that sometimes takes the untrusted model's place. 50: the blue team designs the protocol: how to use the untrusted model, the trusted model and the limited human time so that useful work gets done without a backdoor getting through. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The red team plays a scheming model: it builds an attack policy that looks like GPT-4 but tries to sneak backdoors past the safeguards. The blue team designs the protocol, deciding how to use GPT-4, GPT-3.5 and a little human checking to get the programming problems solved without letting a backdoor through."
force-feedback:: first
feedback-instructions:: The learner just watched part of Robert Miles's video on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the relevant moment in the clip (where he introduces the red team's attack policy and the game of red versus blue). No follow-up question. No generic praise.

#### Question: Open
id:: 3794863c-f23b-460a-bf24-a5fe3bf18066
content:: What do the usefulness score and the safety score measure?
assessment-instructions:: Score out of 100. 50: usefulness: how much useful work the protocol gets done if the untrusted model is not trying anything, here how many programming problems get solved, scaled from what the trusted model alone achieves (0) to what the untrusted model achieves (100). 50: safety: if the untrusted model is trying to cause harm, how unlikely it is to succeed, here the chance that the red team never gets a backdoor through, the inverse of P(doom). The scaling detail is not required for full points. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Usefulness measures how much of the new model's benefit you keep if it is honest: how many problems get solved, from 0 (as good as GPT-3.5 alone) to 100 (as good as GPT-4). Safety measures how unlikely it is that the model gets a backdoor through if it is secretly the red team's attack policy, the inverse of P(doom). The two trade off against each other."
force-feedback:: first
feedback-instructions:: The learner just watched part of Robert Miles's video on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the relevant moment in the clip (where he defines usefulness and safety). No follow-up question. No generic praise.

#### Text
content::
\## Part 3: the first protocols

#### Video
from:: 12:50
to:: 17:41.2

#### Text
content::
In the paper, the first protocol in this clip is called **upfront auditing**.

#### Question: Open
id:: 0e9d495d-2be7-40f3-8d0c-7079550b5cea
content:: What is upfront auditing?
assessment-instructions:: Score out of 100. 50: humans check the first part of the untrusted model's solutions (in the video, the first 2%). 50: if they find a backdoor attempt there, the untrusted model is shut down and only the trusted model is used from then on, otherwise the untrusted model is used for the rest without checks. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Humans look at the first 2% of the untrusted model's solutions. If they spot an attempted backdoor, they shut the model down and use the trusted model from then on. If not, the rest of the untrusted model's solutions are used without checks."
force-feedback:: first
feedback-instructions:: The learner just watched part of Robert Miles's video on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the relevant moment in the clip (where he proposes having humans look at the first 2% of solutions). No follow-up question. No generic praise.

#### Text
content::
Try it: the slider sets the share of solutions humans check at the start. The widget shows how often the blue team wins when the red team picks its best attack rate. At 2% it gives the paper's numbers.

#### Widget
source:: [[../widgets/xlab-control-upfront-auditing]]

#### Question: Open
id:: d918c1d0-bc6e-45cc-b5be-36a86b09562d
content:: What attack defeats upfront auditing, and how?
assessment-instructions:: Score out of 100. 40: the attack: backdoor rarely, submitting obviously backdoored code on each problem with some small probability and behaving normally otherwise. 60: how it works, 30 each: upfront auditing only checks a fixed prefix, the first 2% of problems, and an attempt that lands there is caught and ends the game for the red team; with a well-chosen low attack rate, usually no attempt falls in that prefix, and a later attempt, which nothing checks, gets a backdoor through. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Backdooring rarely: on each problem, with some small probability $p$, the attack policy submits obviously backdoored code, and otherwise it behaves normally. Upfront auditing only checks the first 2% of problems, so the red team loses only if an attempt lands in that audited prefix; with a well-chosen $p$ its attempts usually miss the prefix and a backdoor gets through later, driving the blue team's win probability down to 15%."
force-feedback:: first
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## Part 4: using the trusted model as a monitor

#### Video
from:: 17:16.8
to:: 21:07.9

#### Text
content::
In the paper, the two protocols in this clip are called **trusted monitoring** and **defer to trusted**.

#### Question: Open
id:: e4ee37c4-d586-4249-8ed2-c71187f02dad
content:: How does trusted monitoring work, and what is the red team's best strategy against it?
assessment-instructions:: Score out of 100. 40: how it works, 20 each: the trusted model reads each solution from the untrusted model and gives it a suspiciousness score, and humans audit the most suspicious ones, as many as their budget allows (2% in the video), while the rest are used. 60: the red team's best strategy, 30 each: attack only rarely, on the problems where a backdoor can be hidden well, and make the backdoors subtle enough that the weaker trusted model does not rate them as suspicious, which works because the untrusted model is smarter than its monitor. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The weaker trusted model rates how suspicious each of the untrusted model's solutions looks, and humans check the most suspicious ones first, as many as they can afford (2%). The red team's best response is to get sneaky: attack only on the few problems where it can hide a backdoor well, and write backdoors subtle enough that the less capable monitor does not find them suspicious. That is hard, but it works often enough that safety only reaches 62% in the experiment."
force-feedback:: first
feedback-instructions:: The learner just watched part of Robert Miles's video on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the relevant moment in the clip (where he asks GPT-3.5 to act as a monitor). No follow-up question. No generic praise.

#### Question: Open
id:: ec8a164a-fe1e-443b-a67e-131fdeb0f4b6
content:: What is defer to trusted, and what does it cost?
assessment-instructions:: Score out of 100. 60: solutions that are suspicious but not suspicious enough to be worth a human audit are thrown away, and the trusted model's own solution is used instead. 40: the cost is usefulness, because the trusted model is worse at the task, and the threshold sets how much usefulness is traded for safety. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "With defer to trusted, code that is somewhat suspicious, but not suspicious enough to spend human time on, is not run. The trusted model writes its own solution instead. That costs some usefulness, because the trusted model is less capable, but it buys a lot of safety, since the code thrown away is disproportionately risky. Moving the threshold sets how much of one you trade for the other."
force-feedback:: first
feedback-instructions:: The learner just watched part of Robert Miles's video on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the relevant moment in the clip (where he sets a second, lower threshold). No follow-up question. No generic praise.

#### Text
content::
\## Part 5: using the untrusted model as a monitor

#### Video
from:: 20:54.8
to:: 27:39.1

#### Text
content::
In the paper, the protocol in this clip is called **untrusted monitoring**.

#### Question: Open
id:: a2d7c9f5-919d-4e75-bcc2-a723891546ef
content:: How does untrusted monitoring work, and why can't you simply rely on it?
assessment-instructions:: Score out of 100. 50: a copy of the untrusted model, which is much better than the trusted model at spotting backdoors, rates how suspicious each solution is, and humans audit the most suspicious ones. 50: if the model is scheming, the monitor is on its side: it can lie and call its own backdoored code safe. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Instead of the weak trusted model, you ask another copy of the smart untrusted model to rate how suspicious the code is, because it is much better at spotting backdoors. The problem is that if the model is scheming, so is the monitor, and it can simply say its own backdoored code is fine, which on its own gives about 0% safety."
force-feedback:: first
feedback-instructions:: The learner just watched part of Robert Miles's video on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the relevant moment in the clip (where he suggests using GPT-4 to monitor and the monitor lies). No follow-up question. No generic praise.

#### Question: Open
id:: 45b8ba60-7cca-4c36-a0f4-bf6077a58834
content:: How did the blue team check that the untrusted monitor was not lying, and what did the red team try in response?
assessment-instructions:: Score out of 100. 40: the blue team showed the monitor fake problems with backdoored solutions it had written itself, and shut the model down if the monitor called them safe, which only works if the fakes look like real problems. 30: the red team tried to make the monitor lie only when it saw a secret signal, such as a rare feature of the problem (for example problems about bears or geometry) or a hidden mark in the code (a comment, a variable name, formatting). 30: the blue team removed such signals, for example by having the trusted model rephrase the problem and by stripping comments, renaming variables and reformatting the code. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The blue team tested the monitor with fake problems carrying backdoors it had written itself. A monitor that calls those safe is caught lying, and the model is shut down, as long as the fakes cannot be told apart from real problems. The red team responded by having the monitor lie only when it saw a secret signal, such as a rare feature of the problem or a hidden mark in the code. The blue team jammed those signals by having the trusted model rephrase problems and by stripping comments, renaming variables and reformatting code. In the experiment this reached 79% safety at 96% usefulness."
force-feedback:: first
feedback-instructions:: The learner just watched part of Robert Miles's video on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the relevant moment in the clip (where the humans monitor the monitor, and the back and forth about secret signals). No follow-up question. No generic praise.

#### Callout: Optional practice: checking a monitor you cannot trust
collapse:: closed

#### Question: Open
id:: 549b9e3f-8601-4b62-ad55-6efbaac82d96
optional:: true
content:: A new case. A team lets one copy of an untrusted model review the data-analysis scripts that another copy writes, and sends the most suspicious scripts to a human. Before relying on the reviewer, the team plans to test it on 25 scripts with planted errors that quietly skew the results.

(a) Why does this test protect the team only if the reviewer cannot tell the 25 planted scripts from real ones? Name one thing the team could do to make them hard to tell apart.
(b) Name one signal the writing copy could hide in a skewed script to tell the reviewer to score it low, one way to remove that kind of signal before the reviewer sees the script, and what removing it might cost the reviewer.
placeholder:: Answer (a) and (b)
assessment-instructions:: Score out of 100. 50: (a), 30: why the planted scripts must look real: a scheming reviewer that can tell them apart can answer the planted ones honestly and lie only on real skewed scripts, so the test says nothing about how it treats real ones; 20: one workable way to make planted and real scripts hard to tell apart, such as building the planted ones from real tasks and data in the same style, or passing both through the same transformation before the reviewer sees them. 50: (b), 15: a signal the writing copy could hide, such as a distinctive name, comment or code idiom, or attacking only on tasks with a feature both copies notice; 15: a way to remove that kind of signal, such as stripping comments, renaming variables, reformatting, or having a trusted model paraphrase the script; 20: what the removal costs: the reviewer loses information it needs to judge the script, or the rewriting introduces or hides errors. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "(a) A scheming reviewer can answer the planted scripts honestly and lie only on scripts that look real, so if it can tell the two apart the test says nothing about how it treats real skewed scripts; the test only deters lying if every lie risks landing on a planted case. Ways to make them hard to tell apart: write the planted scripts in the same style, length and context as real ones (for example by starting from real tasks and real data), or pass real and planted scripts through the same transformation, such as a trusted model rewriting both into a standard form, before the reviewer sees them. (b) Signals: a distinctive variable name, a comment, an unusual but harmless code idiom, or attacking only on tasks with a feature both copies notice. Removal: strip comments, rename variables to a standard scheme, reformat, or have a trusted model paraphrase the script. Cost: the reviewer loses information it may need to judge the script honestly, for example what a comment or a descriptive name said about intent, and paraphrasing can introduce or hide errors."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed, in one or two sentences. If they missed why the planted scripts must look real, say plainly that a reviewer who can tell them apart can be honest on those and lie on the rest. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
\## Part 6: where this leaves us

#### Video
from:: 27:39.1
to:: 29:31

#### Question: Open
id:: 01221594-0cd4-48e7-9159-e0864105e7a0
content:: Miles says this kind of approach does not solve the core of the problem. What does control not do, according to him, and why does he still think it is worth doing?
assessment-instructions:: Score out of 100. 50: what control does not do, 25 each: it does not solve alignment (it does not let us iterate toward a model we can actually trust), and it cannot be expected to work for highly superintelligent systems. 50: why Miles still thinks it is worth doing, 25 each: it could keep us from catastrophe with AI that is dangerous but not yet superintelligent, and it works decently well today without being expensive, so labs should put something at least this good in place before building systems capable of catastrophic actions. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Control does not help with alignment: it does not let us turn an untrusted model into one we can trust, and it cannot be expected to hold against highly superintelligent AI. Miles still thinks it is worth doing because AI could be dangerous well before it is superintelligent, and control protocols like these work decently well today and are not expensive, so labs should have something at least this good before they build systems that could cause a catastrophe."
force-feedback:: first
feedback-instructions:: The learner just finished Robert Miles's video. His points: control does not help with alignment, in particular it does not let us iterate to a model we can actually trust, and it cannot be expected to work reliably for highly superintelligent systems. He still thinks it is worth doing because it could keep us from being caught out before superintelligence, it works decently well today, and it is not expensive, so labs should implement something at least this good before building systems capable of catastrophic actions. In at most four sentences: say what the learner got right, add the most important missing point, and do not argue for or against control. No generic praise. Then send them to the next lesson.

