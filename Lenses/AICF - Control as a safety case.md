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
So far the routes have mostly run through one company's safety team. This paper, by researchers at the UK AI Security Institute and Redwood Research, sketches a different use of control: as the evidence in a "safety case", an argument a developer could be asked to make before deploying a model. Shlegeris is one of its authors. About three weeks after it came out, in the interview you just read ([recorded in February 2025](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)), he said that using control to get AI companies to "pretty substantially low levels of risk from scheming models" now "just seems pretty implausible", so he had "stopped thinking about the really high-assurance stuff". The sketch calls itself a best guess, not a high-assurance case. The middle part of the post, on how the evaluation is run, is collapsed. You met the method in Unit 1.

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
force-feedback:: first
feedback-instructions:: The learner just read the abstract and argument structure of "A sketch of an AI control safety case" (UK AISI and Redwood Research, 2025). For part 1, a good answer says that a safety case can make control a condition of deployment: a company's own policy, an industry standard or a regulator could require a passing case before a model is deployed, so the protection does not depend only on one team's influence. It needs someone with the will and authority to ask for it and to refuse deployment when the case fails, such as company leadership, a regulator or a government. The authors only say they hope it prompts discussion between frontier labs, government agencies and civil society about what assurance is sufficient, so do not claim any regulator requires this. For part 2, any claim is acceptable if the reason fits it. Strong reasons: the red team may not be able to elicit or match the attacks a much more capable model could find (claim 2b), the deployed protocol may drift from the evaluated one (2a), or extrapolating from 2,000 tasks to 100,000 may hide rare attacks (2c). In at most five sentences: say what the answer got right, name the most useful missing piece, and if part 2 has no reason, ask for one. Do not say whether the safety case approach is good. No generic praise. At most two turns.

#### Text
content::
\## A company that relies on monitoring

The sketch is a proposal. Here is what one AI company actually wrote. Anthropic publishes risk reports under its Responsible Scaling Policy. In its [Sabotage Risk Report for Claude Opus 4.6](https://www.anthropic.com/claude-opus-4-6-risk-report) (February 2026), it judges the risk of sabotage by that model "very low but not negligible". Its mitigations are "Internal monitoring and security controls, as well as alignment audits to assess the possibility of dangerous goals". The excerpt is its own account of the monitoring and security side.

#### Article
source:: [[../articles/anthropic-sabotage-risk-report-claude-opus-4-6]]
from:: "Given the current security, monitoring, and checks on Claude Opus 4.6"
to:: "voluntary disclosure by users or external researchers."

#### Text
content::
Anthropic's next report, the [Risk Report: August 2026](https://www.anthropic.com/aug-2026-risk-report), says its mitigations give "less protection than might be intuitively expected" against a model that is misaligned in most situations without Anthropic having noticed. For that case it writes that its low risk estimate "comes primarily from a belief that it is very unlikely, rather than that we are well positioned to mitigate any harm it might cause". The same report notes that its Long-Term Benefit Trust, which may request an outside review of risk reports, "has not requested an external review (nor has the RSP required that we conduct one)".

#### Question: Open
id:: f35caafd-3a52-49b1-880e-d8846aed7c1b
content::
1. According to the February 2026 report, name two measures Anthropic relies on to catch or stop a model that tries sabotage inside the company, and say where it has no sabotage-oriented monitoring.
2. The August 2026 report says its low estimate for an unnoticed, widely misaligned model rests mainly on believing it unlikely, not on its mitigations. Which premise of the control part of a report like this would you check first, and what would you look at to check it?
placeholder:: A few sentences for each part.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: Anthropic's February 2026 Sabotage Risk Report for Claude Opus 4.6 lists the internal measures it relies on to catch or obstruct sabotage: employees reporting surprising or concerning behaviour, automatic offline monitoring of a sample (at least 10%) of Claude Code prompts by a classifier, sandboxing and automatic monitors that block some risky actions of some agents, security controls protecting model weights (such as egress bandwidth limits), and mandatory manual review plus automatic review of code before it enters shared codebases. It says it does not have sabotage-oriented monitoring for deployments to outside users, beyond voluntary reports by users or external researchers. Its August 2026 report says its mitigations give less protection than one might expect against undetected misalignment that is present across most situations, and that its low estimate there rests mainly on believing such misalignment very unlikely. Part 1, 50 points: 30 for any two of the internal measures above, 15 each, described in any words. 20 for saying there is no sabotage-oriented monitoring of deployments to outside users (external customers or the public). Part 2, 50 points: 25 for naming a premise that the monitoring and security part of such a report actually needs (for example: monitors catch a capable model's attacks, the sampled or offline monitoring sees enough of what matters, the model cannot evade or undermine the measures, harm can be undone if it is caught only afterwards, or the measures still work if the model is more capable or more misaligned than believed) with a reason it might fail. 25 for something someone could actually look at or do that bears on that premise, such as red-team evaluations of the monitors, the share of activity monitored, records of incidents caught, or an outside review of the report. "More research" earns 0 of these 25. Model answer, for the feedback, not a grading checklist: "1. Offline monitoring of a sample of Claude Code prompts, and code review before code goes into shared codebases. There is no sabotage monitoring for outside users. 2. I would check whether the monitors catch a model that is trying to hide its attacks, because the August report admits the mitigations are weaker if the model is misaligned without them knowing. I would look at red-team results where a strong model tries to get past the monitors."
feedback-instructions:: The learner just read section 5 and 5.1 of Anthropic's Sabotage Risk Report for Claude Opus 4.6 (February 2026) and a short note on its August 2026 Risk Report. For part 1, check the two measures against the report's list (employee reports, offline monitoring of at least 10% of Claude Code prompts by a prompted Claude Opus 4.5 classifier, sandboxing and monitors that block some risky actions, model-weight security such as egress bandwidth limits, manual and automatic code review) and whether they named the gap: no sabotage-oriented monitoring for outside users. For part 2, say whether the premise is one the control part actually needs and whether what they would look at could actually be checked. Point out, if the learner missed it, that this is the safety-case route in practice: the report is written by the company itself, and the August report says no external review was requested or required, which bears on who has to want the case for it to bind. Do not say whether Anthropic's risk estimate is right. In at most five sentences. If the learner says they do not understand, ask what Anthropic would need to be true for its monitors to catch a model that is trying not to be caught. No generic praise. At most two turns.
