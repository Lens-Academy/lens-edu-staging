---
id: 'b2da5c84-fbdb-40fc-880f-7b114c81dab1'
writing_minutes: 12
learning-outcome: "Name the main criticisms of AI control and explain each one: what it claims and why the critic thinks so. The main criticisms are that control guards against the wrong danger, that it will not be enough for the most capable AIs because the plan it buys time for may fail, that its evaluations and fixes may not work in practice (evaluations may overstate safety, the AI may game its own evaluation, retraining may breed better schemers), and that it makes things worse by speeding AI up, hiding warning shots and giving false confidence."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - Elias+Claude
---
%% Used in AI Control Fundamentals Unit 4 (Elias, 2026-10-16: learners should be able to name and explain all the main criticisms of control). Opinion is not graded here: weighing the criticisms is the outcome "Weighing arguments about AI control", and Unit 5 is where learners form their own view. %%

## Test:
id:: 20e0f8a0-17bb-46cc-8d01-7a2ce0eaf46e

#### Question: Open
id:: 34ddd43c-1c1d-4fed-902b-1651575f35f4
content::
A friend thinks AI control is obviously a good idea. Name the main criticisms of AI control that well-informed critics raise (there are about seven), and explain each in a sentence or two: what it claims and why the critic thinks so. Cover both criticisms that would hold even if control were done well and practical problems.
placeholder:: One short paragraph per criticism.
assessment-instructions:: Score out of 100. There are seven main criticisms. Each is worth 13 points: 5 for naming it recognisably and 8 for explaining what it claims and why. Give 0 of the 8 if the explanation only restates the claim, and 4 if the reason is vague or partly wrong. A label too vague to tell which criticism is meant (for example "it may have unintended consequences" or "there are ethical concerns") earns 0 of the 5. The other 9 points: give them if the answer includes at least one criticism from each of the three groups below. The eight, in any wording (illustrative, not a checklist of words). Even done well, not enough: (1) Wrong danger: control targets deliberate scheming in early AIs, while the likelier failure is early AIs producing safety work that looks right and is not, or other risks matter more, so the effort would do more good elsewhere. (2) Not enough for the most capable AIs: control is meant to let controlled early AIs do the safety work for later, stronger ones, and that plan may fail, because early AIs may not solve the problem or may be neither aligned nor usable. For the 8 explanation points the answer needs this link to the plan; "it will not work on superintelligence" alone earns 4 of the 8. Even done well, makes things worse: (3) Speeds AI up: it makes powerful AI more useful and profitable, or helps get research out of AIs that speeds capabilities as much as safety; a variant is that a company that only cares about profit would build it anyway, so safety effort there is not neglected. (4) Hides warning shots: it turns moderate, visible incidents that would push the world to act into quiet catches inside a company, or pushes failures to later, more capable systems. (5) False confidence: a protocol can make people feel safe enough to deploy, or a controlled model gets called "aligned", so vigilance drops. Practical problems: (6) Evaluations overstate safety: a red team may miss attacks a more cunning model would find, or the model may deliberately underperform when evaluated or when used as a monitor (sandbagging). (7) Retraining breeds better schemers: training against caught behaviour, or keeping the models that pass, can select for AIs that hide better. Two versions of the same criticism count once. One genuine criticism outside the seven, explained correctly, can stand in for one missing main criticism, for example sandbagging given as a separate criticism from red-team misses, or that control writing in training data may make AIs more adversarial, or that controlling AIs may wrong them if they matter morally. General criticisms of AI or of AI companies that say nothing about control earn nothing. Do not reward or penalise whether the learner agrees with the criticisms. Model answer, for the feedback, not a grading checklist: "Even done well: 1. It aims at the wrong danger: it stops scheming early AIs, but the likelier failure is AIs doing safety work that looks right and isn't. 2. It won't be enough later: the plan is for controlled early AIs to solve alignment for stronger ones, and they may not manage it or may not be usable. 3. It speeds AI up: making untrusted AIs safe to use makes them more useful and profitable. 4. It hides warning shots: a monitor quietly blocks an escape that, in public, would have pushed governments to act. 5. It gives false confidence: if nothing gets caught, people relax and call the model aligned. Practical: 6. Red teams may miss attacks a smarter model would find, and the model can sandbag its own evaluation, so tests overstate safety. 7. Retraining a caught model may teach it to hide better."
feedback-instructions:: Say which criticisms the learner covered well and name the main criticisms they missed, each in one sentence: wrong danger (slop, not scheming), not enough for the most capable AIs (the plan it buys time for may fail), speeding AI up, hiding warning shots, false confidence, evaluations overstating safety (including the AI gaming its own evaluation), retraining breeding better schemers. If an explanation only restated a claim, say what reason was missing. Do not say whether the criticisms are right. One sentence on what they did well, then one sentence per missed or unexplained criticism, nothing more.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Slop, not scheming]]
## Lens:
source:: [[../Lenses/AICF - What about superintelligence]]
## Lens:
source:: [[../Lenses/AICF - Do control protocols hold up]]
## Lens:
source:: [[../Lenses/AICF - Does control breed better schemers]]
## Lens:
source:: [[../Lenses/AICF - Can the AI game its own evaluation]]
## Lens:
source:: [[../Lenses/AICF - Does safety work speed AI up]]
## Lens:
source:: [[../Lenses/AICF - Would a profit-only lab build it]]
## Lens:
source:: [[../Lenses/AICF - How control could speed AI up]]
## Lens:
source:: [[../Lenses/AICF - Warning shots revisited]]
## Lens:
source:: [[../Lenses/AICF - Safety-washing and false confidence]]
