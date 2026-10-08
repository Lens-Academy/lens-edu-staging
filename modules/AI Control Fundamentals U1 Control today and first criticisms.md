---
id: '3905f701-d31a-49d2-be17-91564e9104ab'
slug: ai-control-fundamentals-u1-today
title: "Control today, and first criticisms"
---
%% Part 3 of Unit 1 of AI Control Fundamentals (split into modules by topic, Elias 2026-10-08). %%

# Learning Outcome:
source:: [[../Learning Outcomes/Reading a control setup]]

# Lens:
source:: [[../Lenses/AICF - Control in use today]]

# Lens:
optional:: true
source:: [[../Lenses/AICF - OpenAI's monitor for its internal coding agents]]

# Lens: First criticisms
id:: c6c69db7-5ff6-4259-b924-fe1b2cd6d838
reading_minutes:: 5
tutor_minutes:: 9
tldr:: Mary Phuong of Google DeepMind names the weaknesses of control from inside the field: trusted models fall further behind, and labs may feel safe deploying models they know are misaligned. Jan Kulveit argues from outside that control could even make things worse, by turning useful warning shots into quiet catches.
summary_for_tutor:: Last reading lens of Unit 1 of AI Control Fundamentals. First a two-minute clip from the end of Mary Phuong's FAR.AI talk "AI Control: Addressing Risks from Agentic Internal Deployments" (May 2025). Phuong works on AI control at Google DeepMind. Weaknesses she names: monitoring probably will not scale, because the gap between the best trusted model and the untrusted models we want to deploy keeps growing, until the trusted model is not doing much useful work. Risk compensation: control might let labs deploy imperfectly aligned models, or models they know are misaligned, and still think they are safe, which is especially concerning because control does not address the longer-term root cause or help align superhuman systems. Strengths: in the near term it gives much stronger assurances than alignment or alignment testing can, so it is probably the most effective thing to do to reduce risk from misaligned AI now, and catching a model doing something very concerning, such as trying to take over a data centre, could galvanise more work on safety. An unscored question asks whether risk compensation is a criticism of control itself or of how labs might use it, and whether the difference matters. Any reasoned answer is fine. Then the learner reads Jan Kulveit's short post "AI Control May Increase Existential Risk" (Alignment Forum, March 2025) in full. Kulveit's argument: in worlds where alignment goes well, control matters little. In worlds where alignment fails, control mostly turns moderate, visible warning shots, which would push the world to act, into quiet internal catches that labs describe vaguely, or into a later catastrophe. He also expects labs to downplay incidents that control stopped. This is a first look at criticisms of control. Unit 4 covers criticisms in depth and Unit 5 the debates around this argument, including replies from people who work on control. The lens intro points out that Kulveit disputes a step stated in the lens intro (from an optional part of the case for control): that catching an AI counts as a win because it makes a pause or slowdown more likely. The question asks for one premise from each side and which is less plausible. Treat any reasoned answer as fine. Do not tell the learner whether Kulveit is right.
#### Text
content::
Most of what you read in this unit comes from people who work on control. To finish, a view from outside the field on how control could make things worse, so you can keep it in mind for the rest of the course. Unit 4 goes through the criticisms in depth.

#### Callout: Optional: Mary Phuong of Google DeepMind on the weaknesses and strengths of control
collapse:: closed
#### Text
optional:: true
content::
At the end of a May 2025 talk, Mary Phuong, who works on AI control at Google DeepMind, says what she sees as the weaknesses and strengths of the control agenda.

#### Video
optional:: true
source:: [[../video_transcripts/far-ai-mary-phuong-ai-control-addressing-risks-from-agentic-internal-deployments-technical-ai-policy]]
from:: 13:03.5
to:: 15:00.5

#### Question: Open
optional:: true
id:: 8419de4d-a8e9-41c3-a030-e83ab8666e70
content::
Phuong worries about risk compensation: control might let labs deploy models they know are misaligned and still think they are being safe. Is that a criticism of control itself, or of how labs might use it? Does the difference matter? Say why.
force-feedback:: first
feedback-instructions:: This is an unscored reflection. The learner just heard Mary Phuong (Google DeepMind) name two weaknesses of control (trusted models fall further behind the untrusted models we want to deploy, and risk compensation: labs might deploy imperfectly aligned or known-misaligned models and feel safe, while control does not fix the root cause or help align superhuman systems) and two strengths (much stronger near-term assurances than alignment or alignment testing can give, and the chance to catch a model doing something very concerning, which could galvanise safety work). Engage with the learner's reasoning in at most four sentences. If they say it is only about use, ask whether a safety method that predictably changes how people behave can be judged apart from that behaviour. If they say it is about control itself, ask what would have to be true of control for the problem to go away. Accept any reasoned answer and do not say which view is right. Mention that Kulveit, next, makes a related argument from outside the field. Up to two turns. No generic praise.
#### End Callout

#### Text
content::
Jan Kulveit. Greenblatt and Shlegeris argue that catching an AI counts as a win, because after a catch, shutting down until there are solutions becomes far more likely. Kulveit disputes that step.

#### Article
source:: [[../articles/kulveit--ai-control-may-increase-existential-risk]]

#### Question: Open
id:: 9b1325c0-05ed-4175-a437-e7a9551c70e5
content::
Both Kulveit's argument and Greenblatt and Shlegeris's case for control depend on some things being true about the world. Name one premise each of them depends on. Which of the two do you find less plausible, and why?
force-feedback:: first
feedback-instructions:: The learner just read Kulveit's "AI Control May Increase Existential Risk" after Greenblatt and Shlegeris's case for control. Premises Kulveit's argument depends on include: (1) without control, a misaligned AI's attempt would often be stopped by other means (security, society, governments) and become a moderate, visible incident rather than a catastrophe, (2) such visible incidents would push labs and governments to act, (3) incidents stopped by control would be kept quiet or described vaguely by the lab, and (4) cases where control is the only thing that stops an AI are rare compared with cases something else would have stopped. Premises the case for control depends on include: (a) a red team can find attacks at least as good as the ones a scheming model would find, and the model's abilities can be measured even if it tries to sabotage the measurement, (b) catching an AI leads to a shutdown, pause or slowdown, or at least to much more support for one, (c) the first very useful AIs are not yet too capable to control. Acknowledge each premise the learner names and whether the argument actually needs it. If they name one the argument does not need, say so in one sentence and point to one it does need. Comment on how well they reasoned about which is less plausible, without saying which side is right. At most five sentences. No generic praise. Tell them the course comes back to this argument in Units 4 and 5.

# Lens:
optional:: true
source:: [[../Lenses/AICF - Take apart a deployment pitch]]
