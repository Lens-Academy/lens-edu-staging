---
id: '61c98c0c-1f47-4c23-9c14-62d1adcf4eff'
title: "Catching AIs red-handed"
tldr: "Control does not only aim to block attacks. If a model is caught in an attempt, Greenblatt and Shlegeris argue the situation changes: the developer can stop using the model, or keep using it while studying the attempt to stop the next one."
summary_for_tutor: "Unit 3 of AI Control Fundamentals (why people work on control). The learner reads the opening of Ryan Greenblatt and Buck Shlegeris's 'Catching AIs red-handed' (2024): what counts as catching a model, why a catch is counted as a win condition, the catch-then-shut-down plan (stop using the model, with reasons a lab might adopt it, including that legible evidence could make international cooperation or strong domestic policy more likely, and studying the caught model), and few-shot catastrophe prevention (keep deploying but use the few caught examples to make further attempts fail). This is the 'catch, then act on the evidence' route in the unit's map of routes. The next lens has Shlegeris himself doubting that a catch would make developers slow down. Do not say whether the catch route works."
reading_minutes: 8
tutor_minutes: 7
tags:
  - reading
---
#### Text
content::
In Unit 1 you saw that a control evaluation counts catching the model as a win for the safety team. Here Ryan Greenblatt and Buck Shlegeris explain why. This is a second route by which control is meant to reduce risk: not only blocking an attack, but catching the attempt and using what you learn. The rest of the post, with its list of ways to use a caught attempt, is collapsed below the excerpt. Open it if you want to read the optional lens at the end of this unit, which continues from that list.

#### Article
source:: [[../articles/shlegeris-catching-ais-red-handed]]
from:: "We’ve been spending a lot of time recently thinking"
to:: "some researchers should probably work on developing these techniques."

#### Question: Open
id:: 14552904-714e-4a78-9044-5c676697e011
content::
The authors describe two different things a developer can do after catching a model. Name both. Then say which of them still reduces risk if the developer decides to keep using the model, and which of the authors' reasons for shutting down depends on people outside the company acting.
placeholder:: A few sentences, from memory if you can.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: Greenblatt and Shlegeris describe two responses after a developer catches its AI trying to cause a catastrophe. (1) Catch-then-shut-down: stop using the model. Their reasons a lab might do this include that legible evidence of misalignment might make international cooperation or strong domestic policy more likely, and that the caught model can be studied. (2) Few-shot catastrophe prevention: keep deploying the model, but use the one or few caught attempts to make further attempts less likely to succeed. 20: names stopping or shutting down the model. 20: names keeping the model in use while using the caught attempts to make later attempts fail (or improving defences from the caught examples). 30: says the second (keep deploying and use the caught examples) is the one that still reduces risk if the developer keeps using the model. 30: says the reason that depends on outsiders is that the evidence could lead to international cooperation or government policy (governments or other countries acting). Model answer, for the feedback, not a grading checklist: "One is to shut down the model after catching it. The other is to keep using it but use the caught attempts to make future attempts fail. The second still helps if they keep using the model. The reason that depends on outsiders is that clear evidence might make international cooperation or strong government policy more likely."
feedback-instructions:: The learner just read the opening of "Catching AIs red-handed". The two responses are (1) the catch-then-shut-down plan: stop using the model once it is caught, and (2) few-shot catastrophe prevention: keep deploying, but use the one or few caught attempts to make further attempts less likely to succeed. Only the second still reduces risk if the developer keeps using the model. Among the authors' reasons a lab might follow catch-then-shut-down, the one that depends on outsiders is that legible evidence of catastrophic misalignment "might make international cooperation or strong domestic policy more likely". Studying the caught model as a model organism does not need outsiders. In at most five sentences: say which parts the learner got right, correct any error in one sentence, and name what is missing. Then add one sentence noting that the outsider-dependent part is exactly what the next reading questions. If the learner says they do not understand, give one foothold: ask what the developer does with the model the day after the catch in each case. No generic praise. One turn, then send them on.
