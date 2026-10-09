---
id: 'e816ec0c-2a27-4e72-8f2e-77fbf415e4d1'
slug: ai-control-fundamentals-u4-effects
title: "What control does to the world"
---
%% Part 2 of Unit 4 of AI Control Fundamentals (split into modules by topic, Elias 2026-10-08). %%

# Learning Outcome:
source:: [[../Learning Outcomes/Classifying criticisms of AI control]]

# Learning Outcome:
source:: [[../Learning Outcomes/Ways AI control could backfire]]

# Lens:
source:: [[../Lenses/AICF - Would a profit-only lab build it]]

# Lens:
source:: [[../Lenses/AICF - Warning shots revisited]]

# Lens:
source:: [[../Lenses/AICF - Safety-washing and false confidence]]

# Lens:
source:: [[../Lenses/AICF - Does control make AIs adversarial]]

# Lens: Practice: sorting and answering criticisms
id:: 1de2406a-a5d7-4da3-a4cd-60f23be8e4a1
reading_minutes:: 5
tutor_minutes:: 19
tldr:: Practise the unit's two skills on new cases. Sort a criticism and answer it, and find the weakest premise in an argument for control.
summary_for_tutor:: Practice lens at the end of Unit 4 of AI Control Fundamentals, written by Lens. Three ungraded exercises with tutor feedback. (1) Sort and answer two new criticisms (one about careless companies that do not use control, one about control papers teaching future models how to attack). (2) Name the weakest premise in two arguments for control. Argument A is Google DeepMind's: two short excerpts of Rohin Shah's LessWrong summary of "An Approach to Technical AGI Safety and Security" (April 2025) say their approach "has two lines of defense", the second being control, "treating the AI system as an untrusted insider", and that they "aim for defense in depth" with access control, anomaly detection, logging and auditing. Argument B is written by Lens. (3) A short reflection on which criticism the learner finds strongest. The unit's tests follow this lens. Do not tell the learner which side is right.
#### Text
content::
Before the tests, practise on new cases. The tutor will give you feedback on each answer.

#### Question: Open
id:: fccf9452-1891-4821-969f-fb9f4d3b8ae6
force-feedback:: first
content::
\## Sort and answer

**Criticism 1.** "Control only protects the company that uses it. One careless company that deploys a similar model with no monitoring at all makes everyone else's control pointless."

**Criticism 2.** "Control papers describe in detail how a model could sneak attacks past monitors. Future models are trained on text that includes these papers, so they learn the attacks."

For each: which kind of criticism is it and why, what does it get right, what is the strongest reply, and how much of the criticism is left standing? Compare with what would realistically happen without control, not with a perfect solution.
feedback-instructions:: Practice for the unit's skill of sorting and answering criticisms of control. Reference points, accept other reasoned answers. Criticism 1: mainly "works but is not worth the effort" (control at careful companies does not address the main risk, careless companies), or "does not work" at the level of the world. Gets right: a misaligned model at a careless company is not stopped by others' control. Replies: careful companies' control still prevents catastrophes from their own models, which may be the most capable, control can become a standard or regulation (it is evaluable), and the same objection applies to any safety measure one company adopts. Left: control needs adoption or regulation to matter beyond the companies that choose it. Criticism 2: "makes things worse". Gets right: published attack strategies end up in training data, and the self-fulfilling misalignment studies in this unit are weak evidence in that direction (the fine-tuning one used control writing, the pretraining one AI writing in general). Replies: a capable model could find most of these attacks itself, defenders need the same knowledge, sensitive details can be held back or filtered from training data, and the evidence is preliminary. Left: a real cost whose size is not yet known. For each criticism, check the kind fits the reason, name one strong reply the learner missed, and check they compared with the realistic world without control. Up to three turns, 80 to 150 words each. No generic praise. Do not say who is right.

#### Text
content::
Criticisms are not the only arguments that deserve scrutiny. Here is how Google DeepMind's 2025 safety approach, summarised by Rohin Shah, places control as a second line of defence.

#### Article
source:: [[../articles/shah-google-deepmind-an-approach-to-technical-agi-safety-and-security]]
from:: "## **Misalignment**"
to:: since it stands to benefit from increasing AI capabilities.

#### Article
from:: "### _**Defending against a misaligned model**_"
to:: Other relevant techniques include sandboxing and hardening the environments in which AI systems act.

#### Question: Open
id:: 5b4446a7-05db-45cf-a9c6-545fc7894a61
force-feedback:: first
content::
\## The weakest premise

For each argument for control below, name the premise you find weakest and say why.

**Argument A.** Google DeepMind's case above: alignment work is the first line of defence, and control (treating the model like an untrusted insider, with access control, monitoring, logging and auditing) is a second line that limits the damage if the first one fails. Defence in depth then makes a catastrophe less likely.

**Argument B.** "If control lets us catch an AI trying to escape, we get clear evidence of the danger, and governments will act on it."
feedback-instructions:: Practice for the skill of applying the same scrutiny to arguments for control. Reference points, accept other reasoned answers. Argument A (Google DeepMind's two lines of defence, in Rohin Shah's summary): defence in depth helps only as much as the layers fail independently, and the same capable model that beats alignment training may also beat monitoring and access control, so the layers may fail together. Another good answer: the argument assumes the second line adds protection with no side effects, which ignores the ways this unit showed control could backfire (fewer visible warning shots, false confidence, faster deployment). A learner may also question whether the "holes" left by alignment work are the kind that system-level security can catch. GDM itself says monitoring benefits from more capable AI, which a learner may use for or against the argument. Argument B: weak premises are that a catch will be disclosed (Kulveit and Cheng expect companies to keep it quiet), that the evidence will be clear to outsiders, and that governments will act on it. Buck Shlegeris's own doubt about the last one appears in Unit 3 if the learner read it. Name whether the premise they chose is one the argument really needs, and if a stronger candidate exists, point to it in one sentence. One or two turns, 60 to 120 words each. No generic praise.

#### Question: Open
id:: 7937ee49-6567-4244-ac1a-79236287f392
force-feedback:: first
content::
\## Your view so far

Which criticism in this unit do you find strongest, and what would change your mind about it? A few sentences. Keep it in mind for Unit 5, where you form your own view.
feedback-instructions:: Ungraded reflection that the learner carries into Unit 5. Acknowledge the criticism they chose in one sentence and reflect back what would change their mind. If what would change their mind is vague, ask once for an observation that someone could actually make. Do not argue for or against their view. At most three sentences. No generic praise.
