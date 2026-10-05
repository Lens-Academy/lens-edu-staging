---
id: '5e557cf7-b444-4fd2-81fb-f2a6a7bdfc18'
learning-outcome: "Given a safety argument for deploying a model that may be scheming, say whether it is an alignment claim (the model is not trying to act against us) or a control claim (the model could not cause an unacceptable outcome even if it were trying), explain why good behaviour under observation cannot settle an alignment claim while a control claim can be tested by having a red team attack the safeguards, and judge how far such a red-team test can stand in for what the model itself could do."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - Elias+Claude
---
%% Beginner fork of "Control as a distinct safety case" for AI Control Fundamentals. Unlike the original, part 2 gives full credit to a reasoned disagreement, and part 3 asks about the red team as a stand-in for the model, which the unit teaches (Greenblatt and Shlegeris, the red team's advantages and the 1% versus 5 to 20% caveat). %%
## Test:
id:: dd60306b-5237-4d5f-bd09-fef48415592a

#### Question: Open
id:: eee74330-de37-4f43-9b76-f982cd71b567
content::
A lab wants to deploy a new frontier model as an autonomous coding agent with write access to its own training infrastructure. Two teams each write one paragraph for the deployment decision.

**Team A:** "Over three months we ran the model through 40,000 test episodes, including scenarios built to tempt it into acting against us. It never once did, and its written reasoning reads as honest throughout. We conclude the model is safe to deploy."

**Team B:** "We put our best security engineers in the model's place, gave them full knowledge of our monitoring and review setup and several weeks, and let them try again after every failed attempt. Their task was to get a copy of the model's weights out of the cluster using only the actions the model can take. In 2,000 attempts, every one was flagged by the monitors before the weights left. We conclude the model is safe to deploy."

1. What kind of safety claim is each team's evidence actually about?
2. Some researchers argue that Team B's kind of claim can be checked more reliably with today's methods than Team A's. Give the strongest reason for that view. Then say whether you agree, and why.
3. Is Team B's red team a good stand-in for what the model itself could do? Name one way the setup makes their result more reassuring, and one way the model might still do better than the engineers did.
placeholder:: Answer all three parts
assessment-instructions:: Score out of 100. 25 for part 1: 12: Team A's evidence is about alignment, whether the model is trying or wants to act against the lab. 13: Team B's evidence is about control, whether the model could cause the unacceptable outcome even if it were trying, given the safeguards. Any wording that captures intent versus ability under safeguards counts. 40 for part 2: 15: B's claim is a question about ability: people can try the strongest attacks they can find against the safeguards and see whether any get through. 15: A's evidence cannot settle its claim, because good behaviour while being watched or tested is also what a model hiding its intent would show, or because honest-looking written reasoning need not reflect what actually drives the model. Either idea earns the 15. 10: a verdict with a reason. Agreeing and disagreeing earn these 10 equally, and a reason that repeats the comparison above counts. Examples of reasons that count: agreeing because ability can be tested directly while intent cannot yet be read, or disagreeing because the red team may miss attacks the model would find, or because the model may hide its true abilities when they are measured. A verdict with no reason earns nothing here. 35 for part 3: 18: one way the setup makes the result more reassuring, for example that the engineers knew more about the monitors than the model would, had weeks to plan where the model must plan in the moment and under watch, or could fail and retry while a model that is caught is worse off. 17: one way the model might still do better, for example that it may be better than the engineers at some attack or know things about itself or the system they do not, that it may attack only on rare real opportunities the engineers never tried, that it might hide its real abilities when they are measured, or that it may later get more information or memory than in the test. A generic doubt with no mechanism ("tests can be wrong") earns half of its element. Give credit for each point whenever the answer shows the idea, in any wording. Cap the total at 50 if the answer treats Team A's clean record or honest-looking reasoning as settling that the model is not trying to act against the lab. Cap the total at 55 if part 3 is missing or earns no credit for either of its elements. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "1. Team A's evidence is about alignment: whether the model is trying to act against the lab. Team B's evidence is about control: whether, even if it were trying, it could get its weights out past the safeguards. 2. B's claim is about ability, and ability can be tested: people search for the best attacks and see whether they get past the safeguards. A's evidence cannot settle its claim, because a model hiding its intent would also behave well while it is watched. I mostly agree, but B is only as good as the red team: if it misses attacks the model would find, the test says safe when it is not. 3. More reassuring: the engineers knew the monitoring setup, had weeks and could retry after failing, while a model would have less information, has to plan on the spot and is worse off once caught. The model might still do better: it may be better than the engineers at some kinds of attack, or wait for a rare real opportunity the test never included."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner mixed up which evidence is about intent and which is about ability, correct that first and plainly. If they agreed or disagreed in part 2, do not argue with the verdict. Comment only on how well it is reasoned. If it fits, add that Greenblatt and Shlegeris themselves expect a control evaluation that estimates under a 1% chance of catastrophe to mean more like 5 to 20% real risk if the model is scheming, because the evaluation itself can fail. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Control in plain words]]
notes:: Teaches the alignment versus control distinction (CSET's first and second line of defence) and practises it in six claim-sorting questions.
## Lens:
source:: [[../Lenses/AICF - The case for control - what control is]]
notes:: Teaches the control property and that control reduces to a capability question. Its opening on the two lines of defence is optional.
## Lens:
source:: [[../Lenses/AICF - The case for control - how control is tested]]
notes:: Teaches why alignment cannot yet be evaluated, the conditions for a conservative control evaluation, the red team's advantages over the model, and the authors' own caveat. Practised in the tractability recall, the optional spoken interview and the trust practice question.
## Lens:
source:: [[../Lenses/AICF - Using dangerous AI, but safely]]
notes:: Shows a red team standing in for a scheming model. Practised in its question on the red team's role.
