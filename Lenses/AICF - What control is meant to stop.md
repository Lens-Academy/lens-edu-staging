---
id: '9e87c6a9-b57e-4357-8237-c597bc50b309'
title: "What control is meant to stop"
tldr: "Buck Shlegeris, one of the people who started AI control, on what it is meant to stop: AIs inside an AI company hacking its data centre, stealing their own weights or sabotaging research."
summary_for_tutor: "Second lens of Unit 1 of AI Control Fundamentals, after 'Control in plain words' (CSET's explainer) and before Robert Miles's video on the founding control experiment. A video clip (about 1:52 to 5:46) of the 80,000 Hours interview with Buck Shlegeris (Rob Wiblin, April 2025), the 'What's AI control?' section: control assumes the AIs are badly misaligned and looks for ways to use them anyway. The setting is maybe 100,000 AI researchers inside an AI company. The outcomes he worries about are hacking the company's data centre and using its compute, exfiltrating weights, sabotaging research, influencing the training of future models and backdooring military technology. He worries more about the data centre than about escape because that is where the compute is. Then one scored open question on those outcomes and that reason. The learner has done AI Risk Fundamentals or similar."
reading_minutes: 5
tutor_minutes: 6
glossary_terms:
  - "[[../glossary/Self-exfiltration]]"
---
#### Text
content::
Buck Shlegeris of Redwood Research, one of the people who started the field, in conversation with Rob Wiblin on the 80,000 Hours podcast (April 2025). In this four-minute clip he says what control is, and what it is meant to stop AIs inside an AI company from doing.

#### Text
content::
:::callout {title="Prefer reading?" tone="blue"}
If you would rather read than watch, click the transcript button beside any video in this course to read along or read the transcript instead.
:::

#### Video
source:: [[../video_transcripts/80-000-hours-controlling-ai-that-wants-to-take-over-so-we-can-use-it-anyway-buck-shlegeris]]
from:: 1:51.7
to:: 5:46.0

#### Question: Open
id:: 275d1dc8-c89d-4791-8e13-7c95c310c401
content:: What does Shlegeris want to stop AIs inside an AI company from doing? Name two of the outcomes he mentions. Then say why he worries more about AIs hacking the company's own data centre than about AIs escaping onto the internet.
assessment-instructions:: Score out of 100. 40: two outcomes control is meant to prevent, 20 each. Fitting outcomes: AIs hacking the company's data centre and using its compute for their own purposes, AIs copying their weights out of the company, AIs sabotaging the company's research, AIs influencing the training of future models, AIs secretly backdooring technology they help build (for example military technology). Outcomes from the CSET excerpt also count, such as an agent running unauthorised experiments on the company's compute or manipulating the training of future agents. 60: the reason the data centre matters more: inside the data centre is where the compute is (and other resources such as access to training), so misaligned AIs there could run very many copies, while AIs that escape start from nothing, with little money or compute, and could run only a few copies. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "He wants to stop AIs from hacking the data centre and using its compute, from copying their weights out, and from sabotaging research. The data centre matters more because that is where the compute is. AIs that escape start with almost nothing and can run only a few copies, while AIs that take over the data centre could have huge numbers of copies working against you."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. The reason Shlegeris gives is that the data centre is where the compute is: 100,000 capable AIs working against you inside the company are far more dangerous than the few copies an escaped AI could afford to run. If the learner is stuck, point them to his comparison of AIs that escape "starting from nothing". No follow-up questions. Tell them to move on.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Wiblin, Robert, and Buck Shlegeris. "Buck Shlegeris on controlling AI that wants to take over, so we can use it anyway." *80,000 Hours Podcast*, 4 Apr. 2025. [80000hours.org](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)
:::
