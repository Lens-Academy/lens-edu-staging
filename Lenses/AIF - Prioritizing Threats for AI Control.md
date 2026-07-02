---
id: a77cbcac-1b1c-4183-86aa-675fc443ce8a
title: "Prioritizing Threats for AI Control"
tldr: Not all AI threats deserve equal control effort. This post ranks them {--{"author":"Elias's AI","timestamp":1783002609478}@@— --}and introduces the concentrated-vs-diffuse failure distinction the rest of the control literature leans on.{--{"author":"Elias's AI","timestamp":1783002609478}@@ One catastrophic action needs different machinery than a thousand tiny acts of sabotage.--}
summary_for_tutor: "Covers Greenblatt's prioritization of threat models for control research: concentrated failures (few catastrophic actions {--{"author":"Elias's AI","timestamp":1783002611433}@@—--}{++{"author":"Elias's AI","timestamp":1783002611433}@@such as++} weight {--{"author":"Elias's AI","timestamp":1783002611433}@@exfiltration,--}{++{"author":"Elias's AI","timestamp":1783002611433}@@exfiltration or++} rogue {--{"author":"Elias's AI","timestamp":1783002611433}@@deployments —--}{++{"author":"Elias's AI","timestamp":1783002611433}@@deployments,++} where catching one attempt matters hugely) vs diffuse failures (many small bad actions like subtly sabotaged research, no single action decisive). Argues which threats deserve most effort given tractability and stakes, and why the two classes need different countermeasures."
---

#### Text
content::
(<30 min.) Not all AI threats deserve equal control effort. This post ranks {--{"author":"Elias's AI","timestamp":1783002614301}@@them —--}{++{"author":"Elias's AI","timestamp":1783002614301}@@them,++} and introduces the concentrated-vs-diffuse distinction that the rest of the week's readings lean on.

#### Article
source:: [[../articles/greenblatt-prioritizing-threats-for-ai-control]]

#### Chat
instructions::
TLDR of what the user just read: Greenblatt prioritizes threat models for control research: concentrated failures (a small number of catastrophic actions, e.g. weight exfiltration, rogue {--{"author":"Elias's AI","timestamp":1783002616381}@@deployments —--}{++{"author":"Elias's AI","timestamp":1783002616381}@@deployments,++} where catching one attempt matters hugely) vs diffuse failures (many small bad actions like subtly sabotaged research, where no single action is decisive). He argues for which threats deserve the most effort given tractability and stakes.

Discussion topics to explore:
- What do we mean by "concentrated vs diffuse failures" (this week's key question)? Get the learner to give one example of each.
- Why do concentrated and diffuse failures need such different countermeasures (auditing budgets vs incrimination strategies)?
- Which threats does the learner think are underweighted in this prioritization?

Check they can explain why "high-stakes control" and "diffuse control" are different problems.
