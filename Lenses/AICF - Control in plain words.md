---
id: '1b5ff83e-2595-4525-8dfd-6cc7a4cb3226'
title: "Control in plain words"
tldr: "Alignment tries to make sure an AI does not try to cause harm. Control tries to make sure that if it does try, it fails. A policy explainer from 2025 and Buck Shlegeris, in conversation, say what that means and what control is meant to stop."
summary_for_tutor: "First lens of Unit 1 of AI Control Fundamentals, after the welcome. (1) The introduction and the first two paragraphs of 'Why We Need AI Control' from CSET's explainer 'AI Control: How to Make Use of Misbehaving AI Agents' (Kendrea Beers and Cody Rushing, Georgetown CSET, 1 October 2025): the US AI Action Plan names AI control systems, alignment aims to make agents not attempt undesirable behaviour, control aims to make sure that if they pursue unwanted goals they do not succeed, control matters most where agents could cause severe harm, especially AI companies using agents for AI R&D, and examples of harm (an agent deleting a live database, internal rogue deployment, successor sabotage). (2) Six scored one-line Choice questions: is each claim a control claim or an alignment claim? A claim about whether the model is trying is an alignment claim. A claim that the safeguards hold even if it tries is a control claim, whether or not it is convincing. (3) The 'What's AI control?' section of the 80,000 Hours interview with Buck Shlegeris (Rob Wiblin, April 2025): control assumes the AIs are badly misaligned and looks for ways to use them anyway. The setting is maybe 100,000 AI researchers inside an AI company. The outcomes he worries about are hacking the company's data centre and using its compute, exfiltrating weights, sabotaging research, influencing the training of future models and backdooring military technology. He worries more about the data centre than about escape because that is where the compute is. Then one scored open question on those outcomes and that reason. The learner has done AI Risk Fundamentals or similar. The next lens is Robert Miles's video on the founding control experiment."
reading_minutes: 10
tutor_minutes: 10
glossary_terms:
  - "[[../glossary/Rogue deployment]]"
  - "[[../glossary/Self-exfiltration]]"
---
#### Text
content::
Two short introductions to AI control. The first is from a policy explainer by Georgetown's Center for Security and Emerging Technology (CSET), written for people outside the field. The second is Buck Shlegeris of Redwood Research, one of the people who started the field, explaining it in an interview.

#### Article
source:: [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents]]
from:: U.S. President Donald Trump’s
to:: As other types of organizations adopt AI agents, more risks will emerge.

#### Callout: Control claim or alignment claim?
#### Text
content::
A lab says each of the following about a model it wants to use. For each one, decide: is it a claim that the model is not trying to cause harm (an alignment claim), or a claim that it would fail even if it tried (a control claim)? The question is what kind of claim it is, not whether it is true.

#### Question: Choice
id:: bc460fb0-d072-4813-a813-150eced619ae
content:: "Our safety training removed the model's tendency to deceive us, so it will not try to sabotage our code."
options::
- Control claim
- [x] Alignment claim
explanation:: It is about what the model wants and will try to do. If the training failed, nothing in the claim stops the sabotage.
force-feedback:: first
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is about what the model will try to do, so it is an alignment claim. If the learner chose "control", point out that nothing in the claim would stop a model that does try. No generic praise.

#### Question: Choice
id:: ee9e19b5-5a7d-4fd9-9df1-14e35575026e
content:: "Every transfer of data out of the data centre is capped and logged, and a red team playing a model that wants to copy its weights out could not get them past those limits."
options::
- [x] Control claim
- Alignment claim
explanation:: It says the weights stay in even if the model tries to get them out, and it has been tested by people playing that model.
force-feedback:: first
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is that the model would fail even if it tried, tested by people playing a model that tries, so it is a control claim. No generic praise.

#### Question: Choice
id:: fb7dc6fc-b858-4f96-b302-65fb15f2b7b6
content:: "The model has run inside our company for a year without a single incident, so it is not working against us."
options::
- Control claim
- [x] Alignment claim
explanation:: It concludes that the model is not trying. A model that is trying, and waiting for a better chance, could have the same clean year.
force-feedback:: first
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the conclusion is about what the model is trying to do, so it is an alignment claim, and a model waiting for a better chance would have the same clean record. No generic praise.

#### Question: Choice
id:: 30b2750d-264c-4789-81d4-b703dd333d07
content:: "A weaker model we trust reviews every action the new model takes, and when our researchers played a model trying to slip harmful code past that review, none of their attempts got through."
options::
- [x] Control claim
- Alignment claim
explanation:: It is about whether harmful actions would get through if the model tried, and it was tested by people playing a model that tries.
force-feedback:: first
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is that attempts would fail, tested by people playing a model that tries, so it is a control claim. No generic praise.

#### Question: Choice
id:: a19785f1-d6ee-4365-9a04-a9ff2d8fa86a
content:: "We looked inside the model with interpretability tools and found no hidden goals."
options::
- Control claim
- [x] Alignment claim
explanation:: It is evidence about what the model wants. It says nothing about whether the model could cause harm if it did have hidden goals.
force-feedback:: first
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is about what the model wants, so it is an alignment claim. It says nothing about what would happen if the model did have hidden goals. No generic praise.

#### Question: Choice
id:: 51d666e6-830e-480b-b9b6-6c1b18014b06
content:: "The model can only propose changes to our systems. A human checks each change before it runs, so the model cannot change anything on its own, whatever it wants."
options::
- [x] Control claim
- Alignment claim
explanation:: It says the model could not act alone even if it wanted to. Whether one human reviewer can really catch a sneaky change is a separate question, which control evaluations test.
force-feedback:: first
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is that the model cannot act alone whatever it wants, so it is a control claim. If it fits, add that whether a human reviewer would really catch a sneaky change is exactly what a control evaluation would test. No generic praise.
#### End Callout

#### Text
content::
Now Buck Shlegeris, in conversation with Rob Wiblin on the 80,000 Hours podcast (April 2025).

#### Article
source:: [[../articles/wiblin-buck-shlegeris-on-controlling-ai-that-wants-to-take-over-so-we-can-use-it-anyway]]
from:: **Rob Wiblin:** What is AI control, and how is it different from alignment
to:: It’s really scary if misaligned AIs are carefully backdooring all the military technology that you’re building with these AIs.

#### Question: Open
id:: 275d1dc8-c89d-4791-8e13-7c95c310c401
content:: What does Shlegeris want to stop AIs inside an AI company from doing? Name two of the outcomes he mentions. Then say why he worries more about AIs hacking the company's own data centre than about AIs escaping onto the internet.
assessment-instructions:: Score out of 100. 40: two outcomes control is meant to prevent, 20 each. Fitting outcomes: AIs hacking the company's data centre and using its compute for their own purposes, AIs copying their weights out of the company, AIs sabotaging the company's research, AIs influencing the training of future models, AIs secretly backdooring technology they help build (for example military technology). Outcomes from the CSET excerpt also count, such as an agent running unauthorised experiments on the company's compute or manipulating the training of future agents. 60: the reason the data centre matters more: inside the data centre is where the compute is (and other resources such as access to training), so misaligned AIs there could run very many copies, while AIs that escape start from nothing, with little money or compute, and could run only a few copies. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "He wants to stop AIs from hacking the data centre and using its compute, from copying their weights out, and from sabotaging research. The data centre matters more because that is where the compute is. AIs that escape start with almost nothing and can run only a few copies, while AIs that take over the data centre could have huge numbers of copies working against you."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. The reason Shlegeris gives is that the data centre is where the compute is: 100,000 capable AIs working against you inside the company are far more dangerous than the few copies an escaped AI could afford to run. If the learner is stuck, point them to his comparison of AIs that escape "starting from nothing". No follow-up questions. Tell them to move on.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Beers, Kendrea, and Cody Rushing. "AI Control: How to Make Use of Misbehaving AI Agents." Center for Security and Emerging Technology, Georgetown University, 1 Oct. 2025. [cset.georgetown.edu](https://cset.georgetown.edu/article/ai-control-how-to-make-use-of-misbehaving-ai-agents/)

Wiblin, Robert, and Buck Shlegeris. "Buck Shlegeris on controlling AI that wants to take over, so we can use it anyway." *80,000 Hours Podcast*, 4 Apr. 2025. [80000hours.org](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)
:::
