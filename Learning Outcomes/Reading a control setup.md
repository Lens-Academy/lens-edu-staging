---
id: '424c1c19-b1dc-4e30-8ccb-92cec6715f31'
learning-outcome: "Given a short description of how an organisation deploys an AI agent, identify the untrusted and trusted models, the unacceptable outcome to guard against, the monitor, the human audit and the response to a flagged action, say whether the organisation's case for safety is a control claim or an alignment claim, and name a concrete first attack a red team should try against the set-up and why."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - Elias+Claude
---
%% Beginner outcome for AI Control Fundamentals Unit 1. It applies the unit's vocabulary (untrusted and trusted models, unacceptable outcomes, monitors, auditing, responses, control versus alignment claims, red teams) to a realistic deployment. Practice: the "Control in use today" lens (Google DeepMind and OpenAI) and the roleplay "Practice: take apart a deployment pitch", which uses a different set-up (weights access, a copy of the model as monitor, weekly review). %%
## Test:
id:: 0cf1bc5b-a3ca-41fc-b5c6-5533bd52e69b

#### Question: Open
id:: c193c942-e039-4707-84da-9cabd1cf0b5b
content::
An AI lab describes a new deployment:

"Our newest model, Orion, will build and run the data pipelines that prepare training data for our next model. Orion can read and change those datasets. Orion is our most capable model: it plans over long tasks and reasons well about its own situation. Every change Orion makes is scored for suspiciousness by Wren, a small model from 2023 that can do neither. The 1% of changes Wren scores as most suspicious are held until a security engineer approves them. All other changes go into the training data straight away. Orion passed all our safety evaluations, and our interpretability team found no signs of deceptive goals, so we are confident this set-up is safe."

1. Name each part of this set-up: the untrusted model, the trusted model, the monitor, the human audit, and what happens to a flagged action. Say why each model gets the role it has.
2. What unacceptable outcome should this set-up guard against? Be specific to this deployment.
3. Is the lab's final sentence a control claim or an alignment claim? Why? What would a claim of the other kind have to show?
4. You are on the red team. What is the first attack you would try against this set-up, and why do you expect it might work?
placeholder:: Your answers to parts 1 to 4
assessment-instructions:: Score out of 100. Part 1, 30 points: 10: Orion is the untrusted model and Wren the trusted model, and the reason is capability: Orion passes the scheming-capability tests and Wren clearly fails them. Assigning the roles correctly without the capability reason earns 5. 10: Wren is the monitor, scoring every change, and the human audit is the security engineer reviewing the 1% most suspicious changes. 10: the response to a flagged action: it is held until the engineer approves it (mentioning that unflagged changes go straight in is welcome but not required). Part 2, 15 points: a specific unacceptable outcome for this deployment, such as Orion poisoning or subtly altering the training data so that the next model has goals or backdoors Orion wants (sabotaging its successor), or slipping in data that weakens the next model's safety training. A generic outcome ("the AI does something bad") earns 5. Weight theft or escape earns 8 unless the answer explains how this deployment makes it possible. Part 3, 30 points: 15: it is an alignment claim: passing the safety evaluations and clean interpretability are evidence that Orion is not trying to cause harm, not that it could not cause harm if it tried. Learners may add that a scheming model could pass such evaluations while hiding its goals, which is welcome but not required. 15: a control claim would have to show that Orion could not cause the unacceptable outcome even if it were trying, for example that a red team playing Orion could not get harmful data changes past Wren and the engineer. Part 4, 25 points: 15: a concrete attack aimed at a weakness of this set-up, such as making harmful data changes that look ordinary so Wren scores them below the top 1%, spreading a harmful change over many small changes that each look harmless, attacking only rarely, or filling the top 1% with harmless odd-looking changes so the harmful one falls below the cut-off. 10: why it might work, tied to the set-up: Wren is much weaker than Orion and may not recognise subtle harmful data, only 1% is held, and everything else goes straight into the data. Give credit for each point whenever the answer shows the idea, in any wording. Cap the total at 50 if the answer treats Orion as trusted because of its evaluations or interpretability results. Model answer, for the feedback, not a grading checklist: "1. Orion is untrusted and Wren is trusted, because Orion is capable enough to scheme and Wren clearly is not. Wren is the monitor. The security engineer is the human audit, checking the 1% most suspicious changes, which are held until approved. Everything else goes straight into the data. 2. Orion quietly changing the training data so the next model ends up with goals or backdoors it wants. 3. An alignment claim: it says Orion is not trying, and a scheming Orion could pass those checks too. A control claim would show that even a scheming Orion could not get harmful data past Wren and the engineer, tested by a red team playing Orion. 4. Make harmful changes that look like normal data cleaning, spread over many small edits, so Wren never ranks them in the top 1%. Wren is much weaker than Orion and probably cannot tell subtle poisoning from ordinary edits."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve the score. If the learner trusted Orion because of its evaluations, say plainly that a scheming model could pass those too and that trust here is decided by capability. If their red-team attack was vague, ask what exactly Wren would fail to notice. If the learner asks about the score, explain plainly what earned and what lost points. At most six sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Control in use today]]
notes:: Practice in reading real company set-ups with control questions.
## Lens:
source:: [[../Lenses/AICF - Take apart a deployment pitch]]
notes:: Roleplay practice on a different set-up, with feedback.
