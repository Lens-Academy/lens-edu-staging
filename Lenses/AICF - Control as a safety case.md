---
id: 'e689d288-89c6-4710-ad68-ff046c6248ec'
title: "Control as a safety case"
tldr: "A safety case is a structured argument that a system is safe enough to deploy. Researchers at the UK AI Security Institute and Redwood Research sketch one that rests on control: the model could not get data out even if it tried, and here is the evidence."
summary_for_tutor: "Unit 3 of AI Control Fundamentals (why people work on control). The learner reads the abstract, background and argument structure of 'A sketch of an AI control safety case' (Korbak, Clymer, Hilton, Shlegeris, Irving, January 2025, UK AISI and Redwood Research). Main points: safety cases are structured, evidence-based arguments that a system is safe, emerging as a risk-management tool for frontier AI. A control safety case argues that a model is incapable of subverting the control measures, using a control evaluation where a red team builds models that try to exfiltrate data in a proxy deployment. The argument rests on: (1) the estimated exfiltration probability is below the acceptable threshold, and (2) the evaluation upper-bounds the real probability, which needs (2a) the evaluated protocol to be at least as effective as the deployed one, (2b) the red team's attacks to upper-bound what the deployed model could do, and (2c) conservative extrapolation from 2,000 proxy tasks to the larger deployment. The authors hope it prompts discussion between frontier labs, government agencies and civil society about what assurance is sufficient. In this unit it stands for the route where control becomes a condition of deployment, set by a company's own policy or by regulation. It is also a voice from a government institute, not only from Redwood. Do not say whether safety cases will be adopted."
reading_minutes: 5
tutor_minutes: 6
tags:
  - reading
---
#### Text
content::
So far the routes have mostly run through one company's safety team. This paper, by researchers at the UK AI Security Institute and Redwood Research, sketches a different use of control: as the evidence in a "safety case", an argument a developer could be asked to make before deploying a model. Shlegeris is one of its authors. About three weeks after it came out, in the interview you just read ([recorded in February 2025](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)), he said high-assurance safety cases now seem implausible to him. Keep both in mind. The middle part of the post, on how the evaluation is run, is collapsed. You met the method in Unit 1.

#### Article
source:: [[../articles/korbak-a-sketch-of-an-ai-control-safety-case]]
from:: "**Abstract**. As LLM agents gain a greater capacity to cause harm"
to:: "most effective strategies to cause a catastrophe."

#### Article
from:: "**Argument structure**"
to:: "risks from internally deployed LLM agents."

#### Question: Open
id:: 2d9dea53-72bb-4996-8b72-9f777180296a
content::
1. How could a control safety case reduce risk in a way that a monitoring team working on its own could not? Who would have to want it?
2. The argument rests on claim 1 and on the three parts of claim 2. Which one do you think would be hardest to defend for a model much more capable than today's, and why?
placeholder:: A few sentences for each part.
feedback-instructions:: The learner just read the abstract and argument structure of "A sketch of an AI control safety case" (UK AISI and Redwood Research, 2025). For part 1, a good answer says that a safety case can make control a condition of deployment: a company's own policy, an industry standard or a regulator could require a passing case before a model is deployed, so the protection does not depend only on one team's influence. It needs someone with the will and authority to ask for it and to refuse deployment when the case fails, such as company leadership, a regulator or a government. The authors only say they hope it prompts discussion between frontier labs, government agencies and civil society about what assurance is sufficient, so do not claim any regulator requires this. For part 2, any claim is acceptable if the reason fits it. Strong reasons: the red team may not be able to elicit or match the attacks a much more capable model could find (claim 2b), the deployed protocol may drift from the evaluated one (2a), or extrapolating from 2,000 tasks to 100,000 may hide rare attacks (2c). In at most five sentences: say what the answer got right, name the most useful missing piece, and if part 2 has no reason, ask for one. Do not say whether the safety case approach is good. No generic praise. At most two turns.
