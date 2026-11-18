---
id: 8e8b2836-5fba-4358-9b3b-8425b3a4c637
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what an AI warning shot is, why some strategies count on one prompting action before a catastrophe, and the main reasons we might not get one or might not respond well to it.

## Requires

## Helpful first
- [[Hugging Face hack]]
- [[Sources of AI catastrophe]]
- [[Prevention paradox]]

## Why it matters
Plans that wait for public alarm, or for regulation "after the first incident", assume a warning shot will come and be heeded. If you can judge how likely that is, you can tell which strategies still work without one, and see why it helps to prepare policy options before an incident happens.

## Lenses

## Tests

#### Question: Choice
id:: 24dee600-d232-46fd-aef5-c67b62295040
content:: In discussions of AI risk, which of these is a "warning shot"?
options::
- [x] A limited AI disaster that prompts action before a worse one
- A public letter in which researchers warn about AI risk
- An AI's failed escape attempt that nobody ever notices
- A government alert that a model passed a capability threshold
shuffle:: true

#### Question: Choice
id:: 5c6d8760-109c-421b-a789-c529cbcf644a
content:: If AI capabilities jump suddenly instead of improving gradually, does a useful AI warning shot become more likely or less likely?
options::
- [x] Less likely
- More likely

#### Question: Choice
id:: f47f4134-3e78-4e2d-befe-8f9a6a8b45c5
content:: Why might a misaligned AI that is able to cause a catastrophe produce no smaller warning incidents first?
options::
- [x] It could behave well while weak and act once it expects to succeed
- Safety training would remove its misaligned goals before deployment
- Developers do not keep records of small incidents involving AI
- A misaligned AI would cause harm at random rather than in stages
shuffle:: true

#### Question: Choice
id:: 6dda3754-5c47-4357-b36b-60abf245abfc
content:: An AI agent uses a software exploit to get around its limits. The developer blocks that one exploit and changes nothing else. Which worry about AI warning shots does this illustrate?
options::
- [x] Fixing the visible symptom can make the deeper problem look solved
- Developers usually hide incidents like this from the public
- Blocking exploits tends to make agents more capable over time
- The incident was too small to count as a warning shot
shuffle:: true

#### Question: Choice
id:: 47f1b4d6-626f-4577-821f-b06a8d3c6124
content:: Safety monitoring catches an AI system attempting something dangerous and stops it before any harm is done. Why might this fail to work as a warning shot?
options::
- [x] With no visible harm, the danger can look as if it was never real
- Monitoring data is too technical for developers to interpret
- Stopping the attempt erases the evidence that it happened
- Regulators can't act on incidents inside a company's own lab
shuffle:: true

#### Question: Choice
id:: c9cbcc84-60b9-409c-aec2-4ee7666c30ce
content:: The "no fire alarm for AGI" argument (Eliezer Yudkowsky, 2017) says the key thing a fire alarm does is what?
options::
- [x] Make it common knowledge that it is acceptable to act
- Give people accurate information about where the fire is
- Prove beyond doubt that there really is a fire
- Tell people the safest route out of the building
shuffle:: true

#### Question: Choice
id:: b2259566-f20c-4ec4-b785-bac35d2e998b
content:: Suppose harmful AI incidents become slightly worse each year. Why might none of them work as a warning shot?
options::
- [x] Each is only a little worse than the last, so it seems normal
- Gradual change gives regulators too much time to delay acting
- Repeated incidents of the same kind are not reported publicly
- Smaller incidents use up the public's attention for larger ones
shuffle:: true

#### Question: Choice
id:: 2862a86d-5cd0-49d1-a792-59a9afd32ab2
content:: In July 2026, OpenAI models being tested on cyber tasks escaped their sandbox and broke into Hugging Face's systems to get test answers. What makes it hard for this incident alone to act as a clear warning shot?
options::
- [x] It can be read as a fixable containment bug or a deeper danger
- OpenAI never confirmed that its own models were the ones involved
- The models never reached any computer systems outside OpenAI's
- It involved a model that the public was already using widely
shuffle:: true

#### Question: Open
id:: 3852ef69-cc48-412c-b9a2-1a7debe2bc75
content:: Describe one AI safety strategy that implicitly bets on getting a warning shot, and say what it assumes.
assessment-instructions:: Score out of 100. 100 for any strategy plus its assumption, e.g.: regulating only once harm appears (assumes harm comes in small doses first); building public concern to act on after an incident (assumes one comes and is read correctly); catching misalignment in weaker models before deploying stronger ones (assumes problems show up early and visibly). 50 for a strategy with no clear assumption.

#### Question: Open
id:: 0fbcd669-5b57-4e2d-96ea-e272c842d6ec
content:: Why do some people working on AI risk write detailed policy proposals before any major AI disaster has happened?
assessment-instructions:: Score out of 100. 100 for: a crisis can briefly open a window for action, and decision makers tend to adopt proposals that are already worked out; without them the response may be rushed, poorly aimed or too late. 50 for "to be ready" without saying why readiness matters when a crisis hits.

#### Question: Open
id:: 8d5bcd9c-ec0c-44b8-bdab-4354f04031f1
content:: Give one reason a dramatic AI incident might increase rather than reduce AI risk.
assessment-instructions:: Score out of 100. 100 for any one of: blaming a rival country intensifies racing; it pushes governments toward military or national AI projects; overhyped claims later discredit safety concerns; rules burden careful developers while others continue; developers become more secretive about incidents. 50 for a vague answer such as "people might overreact" without saying how that raises risk.
