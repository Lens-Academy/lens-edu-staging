---
id: 'afa84b6c-c3fb-4ebd-8940-44f1c8205e30'
learning-outcome: "When a deployer considers responding decisively on less evidence of scheming (fewer noticed bad actions), say what that costs if the model is not scheming, and either design a response that keeps that cost low while still acting on a real scheme, or argue why the cost is worth accepting."
topic: "[[../Domains and Topics/7 AI Control/Control protocols]]"
stage: intermediate
authors:
  - Elias+Claude
---
## Test:
id:: 398c4777-7ab5-44d9-8281-a7b71b9bc790

#### Question: Open
id:: c9bce02a-de78-4ab2-b993-8475e52741a3
content::
A lab deploys a model that might be scheming. If it is, it needs about 25 well-placed bad actions, spread across the deployment, to cause a catastrophe. A small share of the model's actions are audited, and auditors sometimes recognise a bad action when they see one. The lab has committed to respond decisively (pausing the deployment and investigating) once it has noticed 3 bad actions, but at that rate the response would very likely come too late. So the lab is considering responding decisively at the first noticed bad action instead.

If the model is not scheming, what does this change cost the lab? Say how the lab could keep that cost down, or why it should accept it.
placeholder:: The cost if the model is honest, then how to keep it down or why to accept it. About 80 to 120 words.
assessment-instructions:: Score out of 100. 50: the cost if the model is not scheming: a decisive response (a pause and investigation) now fires on a single honest mistake, or a single harmless action, that an auditor reads as bad, so costly false alarms (pauses, lost work, investigations) become more frequent than with the 3-notice rule; a generic cost of auditing or of control that is not tied to responding at the first notice earns at most 15 of these 50. 50: how to keep that cost down or why to accept it, either of: making the first-notice response cheaper or graded (for example close review of that area, an investigation of the one incident, changed instructions or restricted permissions, pausing only if it holds up or more turns up), so the expected cost is low if the model is honest; or an argued case for accepting the cost (for example that a pause is cheap next to the catastrophe, or that honest mistakes rarely look like deliberate, well-placed bad actions so false alarms will be rare). A bare assertion ("it's worth it") without a reason earns at most 15 of these 50. An answer that notes that a graded first step only helps if it reliably escalates on a deliberate bad action keeps full credit. Give credit for each point whenever the answer shows the idea, in any wording. Grade reasoning, not agreement. Model answer, for the feedback, not a grading checklist: "If the model is honest, any one of its mistakes that an auditor reads as bad now triggers a pause and an investigation, so costly false alarms become more frequent. The lab can keep that down by making the first-notice response cheap and graded: review that area closely and investigate the one incident, pausing only if it holds up or more turns up, so the expected cost is low if the model is benign."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the cost named is not tied to responding at the first notice, ask what happens when an honest model makes one mistake that looks bad. If the answer gave no way to keep the cost down and no reason to accept it, ask what the lab could do at the first notice short of a full pause. If the learner proposed a graded first step, check that it still escalates on a deliberate bad action, and ask about that if they did not say. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - handling-non-concentrated-failures]]
notes:: The Lens text before the detection-race widget sets up a decisive response at the K-th notice, and the widget shows how lowering K makes the response come sooner. Greenblatt's rule of aiming for a low expected cost if the model is benign is in the excerpts. Practice with feedback: the added practice question after the widget (a code-review case, with a response rule to price).
