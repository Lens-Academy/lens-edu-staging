---
id: '9beed082-9157-49c6-9e17-c8dd601d46bf'
learning-outcome: "Explain what must be true for there to be a period in which AI models are useful enough to transform safety work yet can still be controlled (usefulness arriving at a lower capability level than the ability to defeat affordable safeguards), and name developments that would break that condition and end the period early (such as uninterpretable memory shared between model instances, or skill far beyond human level in hacking, persuasion or manipulating research results), explaining for each how it defeats control."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: intermediate
authors:
  - Elias+Claude

---
## Test:
id:: 275f7004-2018-4cbf-9070-a5b00bdfa984

#### Question: Open
id:: 1645541f-b0c1-4f56-912a-d1eeeda623aa
content::
Some researchers argue that any AI model useful enough to substantially speed up safety research would also be too capable to control, so control can never buy useful time.

1. What would have to be true for them to be wrong?
2. Name two developments that would make them right, or would make control stop working earlier, other than models reasoning or passing messages to each other in a form monitors cannot read. For each, explain why it defeats control.
placeholder:: Answer both parts
assessment-instructions:: Score out of 100. 30 for part 1: being useful enough to transform safety work does not require being capable enough to defeat the best affordable safeguards, so usefulness arrives at a lower capability level than uncontrollability (for example, the useful models are not yet far better than humans in the domains that matter for escaping control). A learner who argues the researchers are probably right gets full points if they still state what would have to be true. 70 for part 2: two developments, 35 each, 15 for the development and 20 for why it defeats control (how it lets a model get past affordable safeguards, or past the evaluation of those safeguards). Any development with a sound mechanism counts, for example: memory shared across instances or long tasks that monitors cannot read, so plans persist and build up out of sight; skill far beyond human level in hacking, persuasion, or manipulating scientific results or arguments, which lets a model defeat security, its human reviewers, or the evaluation of its own work; a capability gap so large that trusted weaker models and human auditors can no longer judge the untrusted model's work; models that can tell evaluations from real use, or red teams unable to find or estimate the model's best attacks, so control evaluations stop being informative; copies of a model coordinating on the same attack without communicating, because they reason alike. A development that is only unreadable reasoning or hidden messages between instances, which the question excludes, earns at most 7 of its 35; shared unreadable memory counts as distinct. Give credit for each point whenever the answer shows the idea, in any wording. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "1. They are wrong if being useful enough to transform safety work arrives at a lower capability level than being able to defeat the best affordable safeguards, for example if the models that can speed up safety research are not yet far better than humans in the domains that matter for escaping control. 2. Skill far beyond human level in persuasion: the model can talk its human reviewers into approving what it does, so human oversight stops being a safeguard. A capability gap so large that trusted weaker models and human auditors can no longer judge the untrusted model's work: monitoring and auditing can no longer tell a sabotaged result from a good one."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner named a development without saying how it gets past safeguards, ask what the model could then do that a monitor, reviewer or control evaluation could not catch. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais-3]]
notes:: The control window prompt and the problematic-domains check.
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais-4]]
notes:: The neuralese check.
