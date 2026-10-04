---
id: 611bdcb3-9071-4d0d-a822-4621747f57f5
title: "Using Dangerous AI, But Safely?"
reading_minutes: 27
tutor_minutes: 8
tldr: "If you cannot be sure a new AI model is on your side, can you still put it to work? Robert Miles walks through the experiment that started AI control: a red team plays a scheming model, a blue team designs the safeguards, and they find out how much safety each design buys."
summary_for_tutor: "Robert Miles's video 'Using Dangerous AI, But Safely?' (Nov 2024), an accessible walkthrough of the founding AI control paper (Greenblatt, Shlegeris, Sachan and Roger, 'AI Control: Improving Safety Despite Intentional Subversion', 2023). Covers why control does not work for strongly superintelligent AI but matters for smart-but-not-superintelligent AI. The setup: an untrusted smart model (GPT-4), a trusted weaker model (GPT-3.5), and limited trusted human time to audit 2% of outputs. The task is programming problems and the catastrophe is inserting a backdoor. A red team builds an attack policy standing in for a scheming model, and a blue team designs protocols. Safety and usefulness trade off. Protocols: use only the trusted model, use only the untrusted model, human auditing alone (the red team attacks rarely), trusted monitoring (suspiciousness scores), deferring to the trusted model for medium-suspicion code, and untrusted monitoring with checks for collusion. Miles concludes that control does not solve alignment but could keep us from being caught out before superintelligence. The question asks the learner to explain the red team's role in their own words. Accept answers in any wording. Numbers from the paper are not needed."
---

#### Text
content::
We start with something light: a video explainer to get the big picture before the readings. After it, you read the post by the researchers who started the field.

Robert Miles explains the idea behind AI control and walks through the experiment that started the field. We skip about three minutes in the middle where he reads out the odd programming problems the experiment used.

#### Video
source:: [[../video_transcripts/robert-miles-ai-safety-using-dangerous-ai-but-safely]]
to:: 5:13

#### Video
from:: 8:09
to:: 29:56

#### Question: Open
id:: fa4eedae-9fb0-46d6-8f92-96f1bb84d94b
content::
In the experiment, GPT-4 almost certainly was not trying to sneak backdoors into the code. So why did the researchers let a red team build a version of it that does, and what did that let them measure?
feedback-instructions:: The learner just watched Robert Miles explain the founding AI control experiment. Key points: nobody can tell whether a model is secretly scheming, so the researchers assume the worst case. The red team builds an attack policy that stands in for a scheming model and tries its best to get a backdoor through. The blue team's protocol is then judged by how often the attack policy succeeds (safety), alongside how much useful work it gets done when the model is honest (usefulness). This measures what the safeguards can withstand, without needing to know what the model wants. In at most five sentences: say what the learner got right, add the most important missing point from this list, and correct any error in one sentence. If the learner says they do not understand, give one foothold, such as "what would you have to know about GPT-4 to test it directly?". No generic praise. Then send them to the next lesson.
