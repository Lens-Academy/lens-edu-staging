---
id: b92ccaa5-dd5b-45e6-ae3d-8506fd73e62f
tldr: "If we hope to automate AI safety research with AIs, what stops a misaligned AI from quietly sabotaging that research? This post introduces a benchmark of 9 ML codebases with hidden sabotages and finds that neither frontier models nor LLM-assisted humans reliably catch them, and that the sneakiest sabotages are not planted bugs but crucial details simply left out."
summary_for_tutor: "Presents Auditing Sabotage Bench, a benchmark of 9 ML research codebases each with honest and sabotaged variants, built to test whether reviewers can detect research sabotage by misaligned AIs. Frontier LLM auditors and LLM-assisted human auditors both perform poorly; the best (Gemini 3.1 Pro with full experiments) reaches AUROC 0.77 and a 42% top-1 fix rate. Key takeaways: omission sabotages are hardest to catch (harder than design, then logic sabotages), benign distractors in real codebases make auditors miscalibrated, and LLMs can autonomously generate sabotages that evade same-capability monitors."
title: "Research Sabotage in ML Codebases"
---

#### Article
source:: [[../articles/gan-research-sabotage-in-ml-codebases]]
