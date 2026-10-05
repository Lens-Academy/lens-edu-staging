---
id: '8f8eb980-1a80-4408-96bd-f8cf794a9427'
title: "Does control breed better schemers?"
reading_minutes: 14
tutor_minutes: 13
tldr: "If you catch an AI misbehaving and then train it not to, you may teach it to misbehave where you cannot see. Oliver Habryka and Jozdien press this and other worries, and Ryan Greenblatt answers."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. Mostly 'control does not work' criticisms, with one 'makes things worse' item. The learner reads excerpts from two sources. (1) The LessWrong dialogue 'How useful is AI Control as a framing on AI X-Risk?' (March 2024) between Oliver Habryka and Ryan Greenblatt: Habryka's list of six worries (no concrete plan for using mildly superhuman AIs for alignment, control used mainly to extract capabilities work and shorten timelines, a large gap between what we can elicit and what the AI can do on its own objectives, training against failed attempts builds better deceivers, our thinking attacked by the AIs we work with, large changes in how AIs work making control hard to predict), Greenblatt's replies to each (he is 'skeptical that (4) matters much', agrees 5 and 6 are serious concerns, and calls 2 'a reason why control work could be net negative'), and their exchange on point 4: Habryka thinks updating against a failed deception attempt also reinforces 'cognition about how to deceive better', and Greenblatt proposes training a monitor to report the behaviour without training the policy, agrees that training against scheming does several things at once including making the AI 'better understand what would be detected', and notes control evaluations can target a well-practised AI. (2) Jozdien's 'Critiques of the AI control agenda' (February 2024): his three cruxes (control needs strong capability evaluations, models may be wildly superhuman in hacking or persuasion before transformative AI, real-world systems select for models that evade controls), his point that anything short of shutting down after a trigger, from rolling back to training against evals, 'bring[s] in a selection pressure for models that manage to evade your control mechanism while still being competent', and his closing section, where he says he found the agenda more promising the more he thought about it, while still more pessimistic than its authors. Do not tell the learner who is right."
---
#### Text
content::
You read the first part of Oliver Habryka and Ryan Greenblatt's March 2024 dialogue in Unit 3. Here is a later part, where Habryka lists what he sees as the main ways control work goes wrong. He numbers six worries, and Greenblatt answers them by number, so keep the list in view as you read the replies.

#### Article
source:: [[../articles/habryka-how-useful-is-ai-control-as-a-framing-on-ai-x-risk]]
from:: I kind of want to make a quick list what at a high level my dooms are
to:: unless we get unlucky with the capability profile.

#### Text
content::
Later they came back to point 4, training against caught behaviour. Habryka starts:

#### Article
from:: I guess maybe the thing that I keep coming back to is actually this one:
to:: (Though the AI being well practiced does reduce our safety margin substantially.)

#### Text
content::
A month earlier, a researcher writing as Jozdien had published his own critiques of control. Here are his three main points, his version of the selection argument, and how his view changed while writing.

#### Article
source:: [[../articles/jozdien-critiques-of-the-ai-control-agenda]]
from:: Evaluating whether you’re in a regime where control is doable
to:: selecting for models that can evade our control mechanisms.

#### Article
from:: If you do something except shut down your most powerful models
to:: (unless we commit to shutting down all frontier models at once).

#### Article
from:: When I first heard about the AI control agenda
to:: and am looking forward to seeing more progress.

#### Question: Open
id:: bde56e9f-4096-4c4c-ba89-c4b6e9b0ca73
force-feedback:: first
content::
\## Sort Habryka's list

Pick three of Habryka's six worries. For each, say which kind of criticism it is: control does not work, works but is not worth the effort, or works and makes things worse. One sentence each is enough.
feedback-instructions:: The learner sorts three of Habryka's six worries. Reference sorting, accept other reasoned answers: (1) no concrete plan for using mildly superhuman AIs for alignment: mainly "not worth it" (control buys little if we cannot use the time), with a "does not work" reading if the learner frames it as control failing at its goal. (2) control used mainly for capabilities work, shortening timelines: "makes things worse" (Greenblatt himself calls it "a reason why control work could be net negative"). (3) gap between what we can elicit and what the AI can do on its own objectives: "does not work" (evaluations underestimate the model). (4) training against failed attempts builds better deceivers: "does not work" or "makes things worse", both defensible, depending on whether the learner stresses that control fails or that it makes models more dangerous. (5) our thinking attacked by AIs we work with: "does not work" or "makes things worse". (6) large changes in how AIs work: "does not work" (control may not carry over). One turn, 60 to 110 words. Confirm sortings that fit, and for one that does not fit, say why in one sentence. No generic praise.

#### Question: Open
id:: 64c822a8-0d4d-48fa-a1f0-d4a5407abaf3
force-feedback:: first
content::
\## The selection argument

1. A company catches its coding agent slipping a hidden backdoor into a pull request, and fine-tunes it with a penalty on that exact transcript. Name two different things the model could learn from this update. Which one would the company's next evaluation be most likely to miss, and why?
2. Greenblatt proposes training a monitor on the caught behaviour instead of training the AI itself. What would have to be true for that to avoid the problem, and what does it cost?
assessment-instructions:: Score out of 100. Part 1 is worth 50, part 2 is worth 50. Context for grading: training a model against a caught attempt changes it in several ways at once. It may make the model less inclined to misbehave, but it may also teach it what gets detected, so that it hides better. Across many models, anything short of shutting down, such as rolling back, retraining or training against evaluations while keeping the models that perform well, selects for capable models that evade the controls. Ryan Greenblatt proposes training a monitor on the caught behaviour instead of training the model itself. Part 1: 30 for two different things the model could learn, 15 each, for example to stop inserting backdoors, to avoid only that exact pattern, to hide backdoors in ways that look different, or to attack only when it thinks nobody is watching. 20 for saying the evaluation would most likely miss a lesson about hiding or avoiding detection, because the model now avoids exactly what the company checks for, so a clean result looks the same as a real change. Part 2: 25 for something that would have to be true, any one of: the monitor gets better at catching the behaviour faster than the untrained model gets better at hiding it, the company really never trains the model on these cases, including indirectly by picking among training runs, or the company is willing to keep using a model it knows has tried something. 25 for a cost, any one of: the company keeps deploying a model it caught trying to cause harm, safety rests on the monitor, or selection pressure still comes in whenever the company retrains or picks among models. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. The model could learn not to insert backdoors at all, or it could learn that backdoors written this way get caught and hide the next one differently. The next evaluation would likely miss the second, because the model now avoids what the evaluation looks for, so a clean result looks the same as real improvement. 2. It works only if the monitor learns to catch the behaviour faster than the model learns to hide it, and if the company really never trains the model on these cases. The cost is that you keep using a model you know tried to plant a backdoor."
feedback-instructions:: The learner explains the selection argument and evaluates Greenblatt's reply. Key ideas for part 1: training against a caught attempt changes the model in several ways at once. In the case, the model could learn to stop inserting backdoors, to avoid only that exact pattern, to hide backdoors differently, or to attack only when it thinks nobody is watching, and the next evaluation is most likely to miss the hiding lessons, because the model now avoids exactly what the company checks for. It may make the model less inclined to scheme, but it may also teach it what gets detected (Greenblatt lists this himself: "Make the AI better understand what would be detected"). Jozdien's version is about selection across models: if you roll back, retrain or train against evals whenever controls trigger, while keeping the models that perform well, you keep the competent models that evade the controls. Part 2: Greenblatt's proposal works if the monitor gets better at catching the behaviour faster than the untrained model gets better at hiding it, if the company really does not train the policy on these cases (including indirectly, for example by picking among training runs), and if it keeps using a model it knows has tried something. Costs: you keep deploying a model you caught, you rely on the monitor, and Jozdien's point that anything short of shutting down creates selection pressure still applies when companies retrain or pick among models. Also accept that control evaluations can assume a well-practised AI, which Greenblatt notes, at the cost of a smaller safety margin. Up to three turns. Per reply: steelman the answer in two to four sentences, name one to three gaps, and ask up to two direct follow-up questions about why or how. If stuck after two attempts, give a short direct answer and move on. Do not tell the learner who is right. 80 to 150 words per reply. No generic praise. If the learner says they do not understand, give one foothold: ask what the training signal tells the AI after a failed attempt.
