---
id: '8f8eb980-1a80-4408-96bd-f8cf794a9427'
title: "Does control breed better schemers?"
reading_minutes: 8
tutor_minutes: 12
tldr: "The criticism: if you catch an AI misbehaving and then train it not to, you may teach it to misbehave where you cannot see. Oliver Habryka and Jozdien press this, and Ryan Greenblatt answers."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, Module 'Practical problems', submodule on the criticism that catching and retraining breeds better schemers. The learner reads (1) the exchange on point 4 from the LessWrong dialogue 'How useful is AI Control as a framing on AI X-Risk?' (March 2024) between Oliver Habryka and Ryan Greenblatt: Habryka thinks updating against a failed deception attempt also reinforces 'cognition about how to deceive better', and expects the default story to end with 'a really competent schemer', and Greenblatt proposes training a monitor to report the behaviour without training the policy, agrees that training against scheming does several things at once including making the AI 'better understand what would be detected', and notes control evaluations can target a well-practised AI. A Lens sentence says that point 4 came from a list of Habryka's worries and that Greenblatt had said he was skeptical it matters much. (2) Jozdien's 'Critiques of the AI control agenda' (February 2024): his point that anything short of shutting down after a trigger, from rolling back to training against evals, 'bring[s] in a selection pressure for models that manage to evade your control mechanism while still being competent' and that this selection is hard to avoid, especially with many developers. Do not tell the learner who is right."
---
#### Text
content::
**The criticism: catching and retraining breeds better schemers.**


You read the first part of Oliver Habryka and Ryan Greenblatt's March 2024 dialogue in Unit 3. Later in it, Habryka lists his main worries about control work. His point 4 is that this kind of training makes AIs better at deception, and Greenblatt answers that he is skeptical it matters much. Habryka comes back to it. (In this exchange, the **policy** is the AI being trained, as opposed to the monitor.)

#### Article
source:: [[../articles/habryka-how-useful-is-ai-control-as-a-framing-on-ai-x-risk]]
from:: I guess maybe the thing that I keep coming back to is actually this one:
to:: but will not have meaningfully changed the underlying cognition)

#### Text
content::
A month earlier, a researcher writing as Jozdien had made the same argument in a wider form: it is not only about training one model, but about which models a company keeps. Read his version.

#### Article
source:: [[../articles/jozdien-critiques-of-the-ai-control-agenda]]
from:: If you do something except shut down your most powerful models
to:: (unless we commit to shutting down all frontier models at once).

#### Question: Open
id:: 64c822a8-0d4d-48fa-a1f0-d4a5407abaf3
force-feedback:: first
content::
\## What does the model learn?

A company catches its coding agent slipping a hidden backdoor into a pull request, and fine-tunes it with a penalty on that exact transcript. Name two different things the model could learn from this update. Which one would the company's next evaluation be most likely to miss, and why?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: training a model against a caught attempt changes it in several ways at once. It may make the model less inclined to misbehave, but it may also teach it what gets detected, so that it hides better. Across many models, anything short of shutting down, such as rolling back, retraining or training against evaluations while keeping the models that perform well, selects for capable models that evade the controls. 60 for two different things the model could learn, 30 each, for example to stop inserting backdoors, to avoid only that exact pattern, to hide backdoors in ways that look different, or to attack only when it thinks nobody is watching. 40 for naming, with a reason, a lesson the next evaluation would likely miss: any lesson that leaves the misbehaviour in place while tests come out clean, such as hiding backdoors differently, attacking only when unobserved, or becoming more cautious without changing its goals. The reason: the model now avoids what the company checks for, so a clean result looks the same as a real change. 20 of these 40 without a reason. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The model could learn not to insert backdoors at all, or it could learn that backdoors written this way get caught and hide the next one differently. The next evaluation would likely miss the second, because the model now avoids what the evaluation looks for, so a clean result looks the same as real improvement."
feedback-instructions:: The learner explains the selection argument on a case. Key ideas: training against a caught attempt changes the model in several ways at once. In the case, the model could learn to stop inserting backdoors, to avoid only that exact pattern, to hide backdoors differently, or to attack only when it thinks nobody is watching, and the next evaluation is most likely to miss the hiding lessons, because the model now avoids exactly what the company checks for. It may make the model less inclined to scheme, but it may also teach it what gets detected (Greenblatt lists this himself: "Make the AI better understand what would be detected"). Jozdien's version is about selection across models: if you roll back, retrain or train against evals whenever controls trigger, while keeping the models that perform well, you keep the competent models that evade the controls. Up to two turns. Per reply: steelman the answer in two to four sentences, name one to three gaps, and ask up to two direct follow-up questions about why or how. If stuck after one attempt, give a short direct answer and move on. Do not tell the learner who is right. 80 to 150 words per reply. No generic praise. If the learner says they do not understand, give one foothold: ask what the training signal tells the AI after a failed attempt.

#### Question: Open
id:: b44612bb-fb3d-47d1-a9f8-1bbcd821499e
force-feedback:: first
content::
\## Greenblatt's reply

Greenblatt proposes training a monitor on the caught behaviour instead of training the AI itself. What would have to be true for that to avoid teaching the AI to hide better, and what does it cost?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: training a model against a caught attempt may make it less inclined to misbehave, but may also teach it what gets detected, so that it hides better. Across many models, anything short of shutting down, such as rolling back, retraining or training against evaluations while keeping the models that perform well, selects for capable models that evade the controls. Ryan Greenblatt proposes training a monitor on the caught behaviour instead of training the model itself. 50 for something that would have to be true, for example: the model gets no signal about which of its actions were flagged (no training on them, no visible rejections, no picking among runs), the company really never trains the model on these cases, including indirectly by picking among training runs, or the company is willing to keep using a model it knows has tried something. Accept another real condition with a reason. 50 for a cost, for example: the company keeps deploying a model it caught trying to cause harm, safety rests on the monitor, or selection pressure still comes in whenever the company retrains or picks among models, or the model's tendency is unchanged so it must be monitored indefinitely. Accept another real cost with a reason. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It works only if the model never learns which of its actions were flagged: no training on them and no picking among runs based on them. The cost is that you keep using a model you know tried to plant a backdoor."
feedback-instructions:: The learner evaluates Greenblatt's reply to the selection argument: train a monitor on the caught behaviour instead of training the AI itself. His proposal works if the model gets no signal about which of its actions were flagged (no training on them, no visible rejections, no picking among runs), if the company really does not train the policy on these cases (including indirectly, for example by picking among training runs), and if it keeps using a model it knows has tried something. Costs: you keep deploying a model you caught, you rely on the monitor, and Jozdien's point that anything short of shutting down creates selection pressure still applies when companies retrain or pick among models. Also accept that control evaluations can assume a well-practised AI, which Greenblatt notes, at the cost of a smaller safety margin. Up to two turns. Per reply: steelman the answer in two to four sentences, name one to three gaps, and ask up to two direct follow-up questions about why or how. If stuck after one attempt, give a short direct answer and move on. Do not tell the learner who is right. 80 to 150 words per reply. No generic praise. If the learner says they do not understand, give one foothold: ask what the company gives up by not retraining the model it caught.
