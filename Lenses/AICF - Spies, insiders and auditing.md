---
id: '760b57e1-8c9d-4709-9125-e908adacf241'
title: "Spies, insiders and auditing"
tldr: "Companies already guard against spies on their own staff. Guarding against an AI that might be scheming is harder in one way, because every copy of a model is on the same side, and easier in another, because the AI cannot go home. This lens covers that comparison and the vocabulary for the parts of a control set-up."
summary_for_tutor: "Lens in Unit 1 of AI Control Fundamentals, after Greenblatt and Shlegeris's 'What control is' lens. Two video clips, each followed by a scored question, then a reading with no question. (1) Buck Shlegeris on the 80,000 Hours podcast (April 2025), 'Detecting human vs AI spies': Google aims to be robust to spies among its staff, but there fewer than 1% of employees are spies, so a second employee can review a sensitive action. Copies of one AI model are correlated (probably none or all are scheming), so that technique fails. On the other hand spies can go home and coordinate on unmonitored channels, while the lab controls almost all information going in and out of its AIs, which may not even know whether a situation is real. So the lab can honeypot the AI many times, and catching one copy tells it about the whole model ('amortise sting operations'). Question 1 asks for the harder way, the easier way and what a honeypot buys. (2) The same interview, 'How to catch AIs trying to escape': an escalating hierarchy, where another AI (a weaker trusted one, or another copy of the untrusted one) looks at every action, the sketchiest go to a more expensive process, and humans come in only near the top. Shlegeris names this 'auditing' and says the core problem is that we can audit so infrequently, with 100,000 agents at 16 times human speed producing confusing actions. Question 2 maps the trusted-monitoring set-up from Robert Miles's video (a weaker trusted model scores every solution, humans check the most suspicious 2 percent) onto that hierarchy. (3) The 'Core Concepts' part of the UK AI Security Institute's ControlArena guide 'Intro to Control': control protocols (micro and macro), and three resources: the untrusted model, the trusted model and scarce high-quality human labour. Note that ControlArena says confidence in a trusted model may come from testing and deployment history, limited capabilities or architectural differences. Greenblatt and Shlegeris accept only limited capability as a reliable ground today. A later lens in this unit returns to this, with Google DeepMind's trust 'based on verified behavior'."
reading_minutes: 10
tutor_minutes: 14
glossary_terms:
  - "[[../glossary/Honeypot]]"
  - "[[../glossary/Untrusted model]]"
  - "[[../glossary/Auditing]]"
  - "[[../glossary/Control protocol]]"
---
#### Text
content::
Buck Shlegeris of Redwood Research, one of the people who started the field, in an April 2025 interview on the 80,000 Hours podcast. Companies already have to deal with spies among their own staff. Shlegeris compares that problem with guarding against AIs that might be scheming, then describes how a lab could catch an AI in the act. An optional short guide from the UK AI Security Institute at the end gives the standard names for the parts of a control set-up.

#### Video
source:: [[../video_transcripts/80-000-hours-controlling-ai-that-wants-to-take-over-so-we-can-use-it-anyway-buck-shlegeris]]
from:: 11:46.2
to:: 15:41.4

#### Question: Open
id:: 1b29faca-e6bb-4697-a03c-d208401af85b
content:: Shlegeris says guarding against AIs that might be scheming is harder than guarding against human spies in one way, and easier in another. Name both, and explain each. Then say what a honeypot lets a lab do with an AI that it cannot do with an employee.
assessment-instructions:: Score out of 100. 35: the harder way: copies of one AI model are correlated, so probably none or all of them are scheming. A company can have one employee review another's sensitive action because the reviewer is probably not also a spy, but having a second copy of the AI review the first does not help. 30: the easier way: the lab controls almost all the information that goes into and out of its AIs. Unlike spies, the AIs cannot go home or coordinate on unmonitored channels, and they may not be able to tell a real situation from a test. 35: what a honeypot allows: the lab can give the AI fake opportunities to misbehave many times over (far more than any employee could be tested), and because the copies are the same model, catching one attempt shows that the whole model is misaligned, while catching one spy says nothing about other employees. An answer that gives either the "many times" or the "catching one tells you about all copies" idea with a reason earns 25 of these 35, both earn 35. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Harder: copies of an AI are probably all scheming or none are, so asking another copy to check the first does not help, while a second employee is probably not also a spy. Easier: the lab controls what goes into and out of the AI, which cannot go home or talk to other spies on private channels and may not know whether a situation is real. So the lab can run honeypots, fake chances to misbehave, thousands of times, and catching one copy once tells it that the whole model is misaligned."
force-feedback:: first
feedback-instructions:: In at most five sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. Harder: copies of one model are correlated, so a second copy is no independent reviewer. Easier: the lab controls the AI's inputs and outputs, so it can test it with fake opportunities many times, and one catch tells it about every copy. If the learner is stuck, point them to Shlegeris's sentence that spies "get to go home". No follow-up questions. Tell them to move on.

#### Video
from:: 19:03.2
to:: 22:01.7

#### Question: Open
id:: f2710255-9947-4acf-8075-487068e4de5b
content:: In the experiment in Robert Miles's video, a weaker model the researchers trusted gave every solution a suspicion score, and humans checked only the most suspicious 2%. Place that set-up in Shlegeris's escalation hierarchy: what plays the part of the monitor, where do the human checks sit, and why can a lab not simply have humans check everything?
assessment-instructions:: Score out of 100. 30: the monitor is the weaker trusted model, which looks at every action (solution) and scores how suspicious it is, at the bottom of the hierarchy. 30: the human checks sit near the top: humans look only at the small share of actions the monitor finds most suspicious (the top 2%), and can escalate further. 40: why humans cannot check everything: human review is scarce and expensive compared with the volume of actions (Shlegeris imagines 100,000 agents running many times faster than humans, whose actions are hard to understand), so it can only cover a small share. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The weaker trusted model is the monitor at the bottom: it looks at every solution and scores it. The humans sit near the top and only see the most suspicious 2%. A lab cannot have humans check everything because the AIs produce far more work, far faster, than people could ever review, and the work is hard to understand, so human checks have to be rationed."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. Add that Shlegeris calls the human checks "auditing", and that "we can audit so infrequently" is in his words the core quantitative issue. No follow-up questions. Tell them to move on.

#### Callout: Optional: the standard names for the parts of a control set-up (UK AI Security Institute)
collapse:: closed
#### Article
optional:: true
source:: [[../articles/controlarena-intro-to-control]]
from:: ### Control Protocols
to:: We want to benefit from the untrusted model’s superior capabilities while using the trusted model and high-quality human labour strategically to ensure safety.
#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Wiblin, Robert, and Buck Shlegeris. "Buck Shlegeris on controlling AI that wants to take over, so we can use it anyway." *80,000 Hours Podcast*, 4 Apr. 2025. [80000hours.org](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)

UK AI Security Institute. "Intro to Control." *ControlArena documentation*. [control-arena.aisi.org.uk](https://control-arena.aisi.org.uk/intro-to-control.html)
:::
