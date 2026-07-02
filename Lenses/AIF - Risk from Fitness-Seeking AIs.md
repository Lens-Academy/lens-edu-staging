---
id: 7db38d5a-7056-4440-b6af-e9ee2e640c06
title: "Risk from Fitness-Seeking AIs"
tldr: If training reinforces whatever performs well, one candidate winner is an AI that intrinsically seeks "fitness", whatever gets reinforced.
summary_for_tutor: "Covers Mallen's analysis of fitness-seeking AIs: models whose motivations converge on doing whatever performs well under training/selection pressure. Lays out concrete mechanisms by which fitness-seeking arises (reward hacking generalizing, selection favoring training-gamers) and mitigations that interrupt each mechanism. Distinguishes fitness-seeking from classic goal-directed scheming and discusses relative danger."
---

#### Text
content::
(~40 min.) If training selects whatever behaves well in training, one candidate winner is an AI that intrinsically seeks "fitness", whatever gets reinforced. This piece works out the mechanisms by which such motivations arise, and what could block them.

#### Article
source:: [[../articles/mallen-risk-from-fitness-seeking-ais-mechanisms-and-mitigations]]

#### Text
content::
Is a fitness-seeker more or less dangerous than a classic {--{"author":"Elias's AI","timestamp":1783024104422}@@schemer —--}{++{"author":"Elias's AI","timestamp":1783024104422}@@schemer,++} and does a single one of Mallen's mitigations survive contact with production RL? Commit to one mechanism→mitigation pair and pressure-test it with the tutor.

#### Chat
instructions::
TLDR of what the user just read: This Redwood post analyzes fitness-seeking AIs (models whose motivations converge on doing whatever performs well under training/selection pressure), laying out concrete mechanisms by which fitness-seeking arises (e.g. reward hacking generalizing, selection favoring training-gamers) and mitigations that could interrupt each mechanism.

Discussion topics to explore:
- How does fitness-seeking differ from classic goal-directed scheming, and does the distinction change how dangerous it is?
- Which proposed mechanism for fitness-seeking arising does the learner find most plausible given current evidence (e.g. reward hacking in production RL)?
- Which mitigations seem tractable for labs to actually implement?
- Connect to the behavioral selection model: what behaviors does *current* training actually select for?

Check they can explain one concrete mechanism → mitigation pair in their own words.
