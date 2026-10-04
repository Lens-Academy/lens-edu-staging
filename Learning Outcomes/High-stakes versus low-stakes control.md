---
id: 'dc075880-2c32-442d-b046-8be0ea2cb00f'
learning-outcome: "Classify a way a scheming AI could cause a catastrophe as high-stakes (a few actions, or a short time, are enough, and each bad action would look clearly suspicious if inspected) or low-stakes (it takes many actions, each only weak evidence of bad intent because it could be an honest mistake), using how many actions are needed and how incriminating each one is rather than how much harm the end result does, and explain what the classification means for the defender: in the high-stakes case suspicious actions have to be stopped before they take effect, while in the low-stakes case slower review after the fact and measures that work across many actions, such as training on the model's outputs, can be enough."
topic: "[[../Domains and Topics/7 AI Control/Control threat models]]"
stage: beginner
authors:
  - James agent ready-34
---
%% Beginner sibling of [[Concentrated versus diffuse failures]], written for AI Control Fundamentals Unit 2. It leaves out incrimination case-building and the details of training regimes. %%
## Test:
id:: c7330faf-5256-4360-9a95-dca804d65ce8

#### Question: Open
id:: 06c7d99f-b269-4fd0-a323-cfb381c23a40
content::
An AI company uses a capable AI model, which might be secretly misaligned, as an agent inside the company. Here are three ways it could do serious damage:

(1) While fixing a permissions bug, the agent makes one configuration change that gives itself write access to the storage where its own weights are kept.
(2) Over a year, the agent writes hundreds of the company's safety evaluation reports. In each one it rounds results slightly in the model's favour and words the caveats so that they are easy to miss. Each report on its own looks like ordinary sloppiness.
(3) The agent reviews code for the company's monitoring system. Once, it approves a change containing a subtle backdoor that lets some actions skip the monitor. A security expert who looked closely at that change would see that the backdoor was deliberate.

a. Classify each as high-stakes or low-stakes, and say why.
b. The company plans to review the agent's actions a day after they run, rather than before. For one case you called high-stakes and one you called low-stakes, say whether that would be good enough, and why. For the low-stakes case, also name one other kind of measure that would help, and say why it fits.
c. A colleague says: "Case (2) is low-stakes, so it is the least dangerous of the three." How would you respond?
placeholder:: Answer a, b and c in turn
assessment-instructions:: Score out of 100. 30: classification, 10 each, judged by how many bad actions the damage needs and how incriminating each action is: (1) high-stakes, because one action is enough and giving itself write access to its own weights looks clearly suspicious if inspected; (2) low-stakes, because the damage builds up over many actions and each one is weak evidence, easy to mistake for an honest error; (3) high-stakes, because one action is enough and the action is incriminating once inspected, even though it is quiet and easy to miss. An argued placement that differs counts if it rests on these two properties, for example calling (3) "in between" because a subtle backdoor might pass as a bug. 40: whether review a day later is good enough, 15 for a high-stakes case: no, because a single action is enough and it takes effect before the review (the agent could use the access or the backdoor within the day, and the harm may be impossible to undo), so suspicious actions have to be held or blocked until reviewed; 12 for a low-stakes case: yes or mostly, because no single action is decisive and the harm builds up slowly, so there is time to notice and correct it; 13 for one other fitting measure for the low-stakes case with a reason that it works across many actions, such as training the model on a signal of report quality across all its reports, checking the reports' numbers against the raw results in aggregate, or having reports independently replicated. 30: answer to the colleague: low-stakes describes how the damage is spread over actions (many actions, each weak evidence), not how much harm results, so (2) can be as dangerous as the others (for example, unsafe models could be judged safe and deployed), and it is harder to catch, because no single report proves bad intent; 15 for rejecting the inference from low-stakes to low danger, 15 for a reason why (2) can still be very harmful or is hard to catch. Rejecting the colleague on other argued grounds counts. Give credit for each point whenever the answer shows the idea, in any wording. Grade the reasoning, not which conclusion the learner prefers. Cap at 40 if the answer classifies the cases by how much harm they do rather than by how many actions they need and how incriminating each is. Model answer, for the feedback, not a grading checklist: "a. (1) High-stakes: one action does it, and giving itself access to its own weights is clearly suspicious once someone looks. (2) Low-stakes: it takes hundreds of reports, and each skewed report is only weak evidence, since it looks like sloppiness. (3) High-stakes: one approval does it, and the backdoor is incriminating once inspected. Being quiet does not make it low-stakes. b. For (1), a review a day later is too late: the agent can use the access immediately, and the damage may not be reversible, so changes like this need to be held until someone has checked them. For (2), a day later is fine, because no single report does the damage, and there is time to spot the pattern and fix the reports. A measure that works across many actions also helps, for example training the agent on a quality signal across all its reports, since there are many examples to learn from. c. Low-stakes is about how the damage is spread over many weakly suspicious actions, not about how much harm results. Skewed safety reports could lead the company to deploy an unsafe model, which is as serious as the other two. It is also harder to catch, because no single report proves bad intent."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner sorted the cases by how harmful they are, ask how many actions each needs and what a reviewer would conclude from one of them. If they called (3) low-stakes because it is quiet, ask how many actions it takes and what an expert would conclude on finding it. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - High-stakes and low-stakes threats]]
notes:: Greenblatt's clusters of threats and his section on concentrated versus non-concentrated failures (block suspicious actions until reviewed, or review asynchronously), plus the control graph widget.
## Lens:
source:: [[../Lenses/AICF - Rogue deployments]]
notes:: Shlegeris's rogue deployments, the central high-stakes example.
## Lens:
source:: [[../Lenses/AICF - Low-stakes control and research sabotage]]
notes:: Hebbar's ControlConf talk, first half: the two axes, research sabotage, incrimination versus online training.
