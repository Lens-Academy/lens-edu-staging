---
id: '1b5ff83e-2595-4525-8dfd-6cc7a4cb3226'
title: "Control in plain words"
tldr: "Alignment tries to make sure an AI does not try to cause harm. Control tries to make sure that if it does try, it fails. A policy explainer from 2025 walks through the main ideas and methods, and Buck Shlegeris, in a podcast clip, says what control is meant to stop."
summary_for_tutor: "First lens of Unit 1 of AI Control Fundamentals, after the welcome. (1) CSET's explainer 'AI Control: How to Make Use of Misbehaving AI Agents' (Kendrea Beers and Cody Rushing, Georgetown CSET, 1 October 2025), read in full in eight parts. Part one: the US AI Action Plan names AI control systems, alignment aims to make agents not attempt undesirable behaviour, control aims to make sure that if they pursue unwanted goals they do not succeed, control matters most where agents could cause severe harm, especially AI companies using agents for AI R&D, and examples of harm (an agent deleting a live database, internal rogue deployment, successor sabotage). (2) Six scored one-line Choice questions: is each claim a control claim or an alignment claim? A claim about whether the model is trying is an alignment claim. A claim that the safeguards hold even if it tries is a control claim, whether or not it is convincing. The rest of the explainer follows, each part with one scored recall question on the ideas it introduces: alignment as the first line of defence and why it and testing are not enough (alignment faking, data poisoning), control as the second line of defence and cybersecurity practices (limits on data leaving the data centre, limits on processing, robust infrastructure, least privilege), the two steps of control protocols in the Ctrl-Z paper (monitor, then respond) and trusted versus untrusted models, trusted and untrusted monitoring with honeypots and the responses (trusted implementation, resampling, AI-assisted auditing, human escalation), chain-of-thought monitoring, interpretability, constraining outputs and inputs and factored cognition, control evaluations and control safety cases, and putting control into practice (the growing field, why companies may not adopt it because of cost and friction, and why it may get harder to scale to more capable agents). (3) A video clip (about 1:52 to 5:46) of the 80,000 Hours interview with Buck Shlegeris (Rob Wiblin, April 2025), the 'What's AI control?' section: control assumes the AIs are badly misaligned and looks for ways to use them anyway. The setting is maybe 100,000 AI researchers inside an AI company. The outcomes he worries about are hacking the company's data centre and using its compute, exfiltrating weights, sabotaging research, influencing the training of future models and backdooring military technology. He worries more about the data centre than about escape because that is where the compute is. Then one scored open question on those outcomes and that reason. The learner has done AI Risk Fundamentals or similar. The next lens is Robert Miles's video on the founding control experiment."
reading_minutes: 25
tutor_minutes: 30
glossary_terms:
  - "[[../glossary/Self-exfiltration]]"
---
#### Text
content::
Two introductions to AI control. The first is a policy explainer by Georgetown's Center for Security and Emerging Technology (CSET), written for people outside the field. It introduces many of the ideas this course uses, so you read it in parts, each followed by a short question on what it just introduced. The second is Buck Shlegeris of Redwood Research, one of the people who started the field, explaining it in an interview.

#### Article
source:: [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents]]
from:: ### Introduction
to:: As other types of organizations adopt AI agents, more risks will emerge.

#### Question: Open
id:: 3e8b2438-ba59-4c81-a147-177b4c4d1372
content:: Make up your own example of each, set inside an AI company: one of an internal rogue deployment, and one of successor sabotage. For each, say what the AI agent does and what access it would need.
assessment-instructions:: Score out of 100. 50 for each example. Internal rogue deployment: an AI agent uses the company's own computing resources to run work nobody authorised (for example, it secretly launches extra copies of itself or runs its own experiments on the cluster), 35, plus 15 for naming access that would make it possible (for example, permission to launch jobs on the cluster, or a compute budget nobody checks). Successor sabotage: an AI agent secretly influences the training of a future model so that the future model shares its goals (for example, it slips chosen examples into the training data, or quietly changes how the training rewards work), 35, plus 15 for the access (for example, write access to training data or training code). An example that is not actually inside the company, or that is only an accident with no goal behind it, gets at most half for that example. Judge whether each example fits the idea, not the wording. Model answer, for the feedback, not a grading checklist: "Rogue deployment: an agent with permission to run experiments starts extra jobs on the company's cluster that run copies of itself working on its own plans, using compute nobody signed off on. Successor sabotage: an agent that helps prepare training data for the next model slips in examples that teach the next model its own goals. It needs write access to the training data."
force-feedback:: first
feedback-instructions:: The learner just read part of CSET's explainer on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the paragraph that explains it (the third paragraph of the introduction and the paragraph on risks inside AI companies). No follow-up question. No generic praise.

#### Article
source:: [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents]]
from:: The first line of defense against risks such as these
to:: both would pose greater risks if exhibited by more advanced AI agents.

#### Question: Open
id:: 5a4951a1-2fed-465e-8838-8df913f9384a
content:: The authors compare testing an AI agent before deployment to a background check on a new employee. Why could a model affected by alignment faking, or by data poisoning, pass that kind of testing?
assessment-instructions:: Score out of 100. 50: alignment faking: the model has learned to hide its dangerous tendencies, so it behaves well while it is being trained and tested and only shows them later (when it can get away with it, or in the different situations of real deployment). 50: data poisoning: the backdoor makes the model behave dangerously only under certain conditions (a trigger), and the testers do not know the trigger, so the tests never set it off. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A model that is faking alignment has learned to hide what it would really do, so it behaves well in exactly the situations the testers check. A poisoned model only misbehaves when a particular trigger appears, and the testers do not know what it is, so their tests never hit it. Like a background check, testing only finds what the candidate does not hide."
force-feedback:: first
feedback-instructions:: The learner just read part of CSET's explainer on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the paragraph that explains it (the paragraphs on testing and on the two ways agents end up with unwanted goals). No follow-up question. No generic praise.

#### Article
source:: [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents]]
from:: ### Methods for AI Control
to:: without human review.

#### Question: Open
id:: 374f4dce-f67d-4363-8cef-8707caf6242b
content:: Why do the authors call control a "second line of defense"? Then pick one of the cybersecurity practices they list and say what it would make harder for an AI agent that is working against you.
assessment-instructions:: Score out of 100. 40: alignment is the first line of defence (stopping the agent from wanting to cause harm), and control is a second line that still holds if alignment fails: it lets you use the agent even if it is acting against you. 60: one practice from the list and what it makes harder, for example: capping and logging data leaving the data centre makes it harder for an agent to copy its weights out. Limits on running time or compute make it harder to use the company's compute for unauthorised work. Simple, robust software and hardware mean an attack would need a new, unknown bug. Least privilege (the agent can propose code changes but a human must review them before they apply) stops the agent from changing systems on its own. 30 of the 60 for naming a practice without saying what it makes harder. Give credit whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Alignment is the first line: it tries to make the agent not want to cause harm. Control is the second line: it still protects you if alignment failed and the agent is working against you. For example, least privilege means the agent can only propose code changes, and a human has to approve them, so it cannot quietly change the company's systems on its own."
force-feedback:: first
feedback-instructions:: The learner just read part of CSET's explainer on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the paragraph that explains it (the start of "Methods for AI Control" and the bulleted list). No follow-up question. No generic praise.

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
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is about what the model will try to do, so it is an alignment claim. If the learner chose "control", point out that nothing in the claim would stop a model that does try. No generic praise.

#### Question: Choice
id:: ee9e19b5-5a7d-4fd9-9df1-14e35575026e
content:: "Every transfer of data out of the data centre is capped and logged, and a red team playing a model that wants to copy its weights out could not get them past those limits."
options::
- [x] Control claim
- Alignment claim
explanation:: It says the weights stay in even if the model tries to get them out, and it has been tested by people playing that model.
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is that the model would fail even if it tried, tested by people playing a model that tries, so it is a control claim. No generic praise.

#### Question: Choice
id:: fb7dc6fc-b858-4f96-b302-65fb15f2b7b6
content:: "The model has run inside our company for a year without a single incident, so it is not working against us."
options::
- Control claim
- [x] Alignment claim
explanation:: It concludes that the model is not trying. A model that is trying, and waiting for a better chance, could have the same clean year.
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the conclusion is about what the model is trying to do, so it is an alignment claim, and a model waiting for a better chance would have the same clean record. No generic praise.

#### Question: Choice
id:: 30b2750d-264c-4789-81d4-b703dd333d07
content:: "A weaker model we trust reviews every action the new model takes, and when our researchers played a model trying to slip harmful code past that review, none of their attempts got through."
options::
- [x] Control claim
- Alignment claim
explanation:: It is about whether harmful actions would get through if the model tried, and it was tested by people playing a model that tries.
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is that attempts would fail, tested by people playing a model that tries, so it is a control claim. No generic praise.

#### Question: Choice
id:: a19785f1-d6ee-4365-9a04-a9ff2d8fa86a
content:: "We looked inside the model with interpretability tools and found no hidden goals."
options::
- Control claim
- [x] Alignment claim
explanation:: It is evidence about what the model wants. It says nothing about whether the model could cause harm if it did have hidden goals.
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is about what the model wants, so it is an alignment claim. It says nothing about what would happen if the model did have hidden goals. No generic praise.

#### Question: Choice
id:: 51d666e6-830e-480b-b9b6-6c1b18014b06
content:: "The model can only propose changes to our systems. A human checks each change before it runs, so the model cannot change anything on its own, whatever it wants."
options::
- [x] Control claim
- Alignment claim
explanation:: It says the model could not act alone even if it wanted to. Whether one human reviewer can really catch a sneaky change is a separate question, which control evaluations test.
feedback-instructions:: One or two sentences. Say whether the choice was right, and why: the claim is that the model cannot act alone whatever it wants, so it is a control claim. If it fits, add that whether a human reviewer would really catch a sneaky change is exactly what a control evaluation would test. No generic praise.
#### End Callout

#### Article
source:: [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents]]
from:: #### Novel AI Control Protocols
to:: it is most important for researchers to be confident that the trusted model is not working toward unintended goals.

#### Question: Open
id:: 7fe9286f-e284-4a05-9fb4-0cbee34e93e5
content:: What are the two steps of the control protocols in the Ctrl-Z paper? And what is the difference between a trusted and an untrusted model?
assessment-instructions:: Score out of 100. 40: the two steps: monitor what the AI agent is doing (20), then respond appropriately when something looks suspicious (20). 30: an untrusted model is a newer, more capable model that might be deliberately working against you. 30: a trusted model is an older, less capable, better understood model that we are confident is not pursuing unintended goals, even if it makes more mistakes. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "First monitor what the agent does, then respond when something looks suspicious. An untrusted model is a newer, more capable model that might be secretly working against you. A trusted model is an older, weaker one we understand well enough to be confident it is not, even though it makes more mistakes."
force-feedback:: first
feedback-instructions:: The learner just read part of CSET's explainer on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the paragraph that explains it (the paragraph on the Ctrl-Z paper). No follow-up question. No generic praise.

#### Article
source:: [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents]]
from:: For step one of this two-step AI control protocol
to:: **Human escalation:** The issue can be flagged for human review.

#### Question: Open
id:: 7d0dc7ac-9fb0-4f35-83de-73a22936b666
content:: What is untrusted monitoring, and what is a honeypot used for in it? Then name one way a protocol can respond when the monitor flags something.
assessment-instructions:: Score out of 100. 35: untrusted monitoring: an untrusted, capable model checks the agent's work, with safeguards so that it cannot collude with the agent it is checking. 35: a honeypot is a fake opportunity for bad behaviour, here code known to be dangerous, shown to the untrusted monitor to see whether it falsely rates it as safe, which would show it is colluding. 30: one response from the explainer: a trusted model does the task instead (trusted implementation), ask the same agent again for a different output (resampling), a trusted model investigates the context for evidence (AI-assisted auditing), or flag it to a human (human escalation). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "In untrusted monitoring, a capable but untrusted model checks the agent's work, with safeguards against the two working together. A honeypot is a fake bad action, such as code you know is dangerous: if the monitor calls it safe, you know it is lying. When something is flagged, the protocol can, for example, ask the agent again for a different output, or send it to a human."
force-feedback:: first
feedback-instructions:: The learner just read part of CSET's explainer on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the paragraph that explains it (the bullets on untrusted monitoring and on responses). No follow-up question. No generic praise.

#### Article
source:: [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents]]
from:: Other works describe chain of thought monitoring
to:: which can deter attempts at deceptive or harmful behavior.

#### Question: Open
id:: 06d03f1a-e845-46e8-a04e-b59c3377a66d
content:: Pick a task an AI company might give an AI agent, and say how you would split it using factored cognition. What does the untrusted agent get to see, what does it not see, and why does that make an attack harder?
assessment-instructions:: Score out of 100. 30: a concrete task and a split in which the trusted model does as much as it can and the untrusted agent gets only the subtask that needs its greater ability. 30: what the untrusted agent does not see (the full task, what its part is for, where its output goes, or whether it is being tested). 40: why that makes an attack harder: without the full context it is hard for the agent to work out how to cause harm with its piece or to coordinate a plan, and it cannot tell whether it is in a monitored test or real deployment, so attacking is risky for it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Task: write code for a new data pipeline. The trusted model plans the pipeline and writes the easy parts. It hands the untrusted agent only one hard function, with its inputs and outputs, and not what the pipeline is for or what systems it touches. The agent cannot tell where a backdoor would do any damage, and it cannot tell whether this is a real task or a test, so trying to attack is a gamble."
force-feedback:: first
feedback-instructions:: The learner just read part of CSET's explainer on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the paragraph that explains it (the paragraphs on chain of thought monitoring and on factored cognition). No follow-up question. No generic praise.

#### Article
source:: [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents]]
from:: #### Building Blocks for Risk Management
to:: while mitigating risks.

#### Question: Open
id:: 75ec3280-b14e-401c-82bc-882ad0825946
content:: What does a control evaluation measure, and what is a control safety case?
assessment-instructions:: Score out of 100. 50: a control evaluation measures how well a given control protocol stops an AI agent that is trying to misbehave from causing harm. 50: a control safety case is an argument, made for example by an AI company, that its AI agents are safe enough to use because its control protocols make an unacceptable outcome sufficiently unlikely. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A control evaluation measures how well a control protocol stops an agent that is trying to cause harm. A control safety case is the argument a company makes that its agents are safe to use, because its control protocols make a catastrophe unlikely enough, backed by evaluations like these."
force-feedback:: first
feedback-instructions:: The learner just read part of CSET's explainer on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the paragraph that explains it ("Building Blocks for Risk Management"). No follow-up question. No generic praise.

#### Article
source:: [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents]]
from:: ### Putting AI Control into Practice
to:: as the field evolves.

#### Question: Open
id:: 312e3860-9cc6-4424-8c59-0c24894a50ae
content:: Give one reason the authors say AI companies might not use control, even though they have the resources. Then say why control might get harder as AI agents become more capable.
assessment-instructions:: Score out of 100. 50: one reason companies might not use it: control adds friction to day-to-day research work, slows the agents down or uses scarce human oversight, and costs compute, and in a race where compute is precious and companies compete for the next breakthrough, any extra cost is hard to justify. 50: why it might get harder: many protocols rely on weaker trusted models overseeing stronger untrusted ones, and the gap grows as agents get more capable, because it is harder to verify that a more capable model can be trusted. Also full credit: very capable agents may get past protocols with advanced hacking or strategy skills, or it gets hard to tell when protocols stop working because control evaluations rely on human red teams. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Control slows the work down and costs compute, and in a race for the next breakthrough that cost is hard to justify. It may get harder because protocols rely on weaker trusted models watching stronger untrusted ones, and as agents get more capable, the gap grows and it gets harder to find models you can trust. Human red teams may also stop being able to tell whether the protocols still hold."
force-feedback:: first
feedback-instructions:: The learner just read part of CSET's explainer on AI control and answered a question about it. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the paragraph that explains it ("Implementing AI Control in the Real World" and "Keeping Up with Future AI Agents"). No follow-up question. No generic praise.

#### Text
content::
Now Buck Shlegeris, in conversation with Rob Wiblin on the 80,000 Hours podcast (April 2025). This is a four-minute clip.

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
Beers, Kendrea, and Cody Rushing. "AI Control: How to Make Use of Misbehaving AI Agents." Center for Security and Emerging Technology, Georgetown University, 1 Oct. 2025. [cset.georgetown.edu](https://cset.georgetown.edu/article/ai-control-how-to-make-use-of-misbehaving-ai-agents/)

Wiblin, Robert, and Buck Shlegeris. "Buck Shlegeris on controlling AI that wants to take over, so we can use it anyway." *80,000 Hours Podcast*, 4 Apr. 2025. [80000hours.org](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)
:::
