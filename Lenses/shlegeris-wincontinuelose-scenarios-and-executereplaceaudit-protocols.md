---
id: 132380b8-22c3-4983-aa5a-e19e52d7cdcb
tldr: "When a scheming AI attacks, three things can happen: you catch it and win, it succeeds and you lose, or it fails quietly and the deployment rolls on. Confusing the last two wrecks your safety math. Buck Shlegeris untangles why 'the attack failed' hides two very different outcomes, and how audit-versus-replace decisions shape the odds."
summary_for_tutor: "Buck Shlegeris makes a technical point about controlling scheming AIs deployed across many discrete tasks where a concentrated, high-stakes failure is the concern. He distinguishes two ways an attack can fail: being caught (a win) versus failing silently (the deployment continues), and argues protocols must treat these separately. He introduces execute/replace/audit protocols, in which a monitor scores each proposed action, driving two decisions: whether to replace the action (resample, defer to trusted, trusted edit, abort, block, or shut down) and whether to audit it. Because auditing is far costlier and false negatives are catastrophic only when replacing, the two defenses have different safety properties. He shows how the framework yields win/continue/lose scenarios, gives a rule of thumb for computing safety from audit and execution probabilities, and works a concrete example using linear-probe sleeper-agent data to show safety depends heavily on pairing auditing with replacement."
title: "Win/continue/lose scenarios and execute/replace/audit protocols"
---

#### Article
source:: [[../articles/shlegeris-wincontinuelose-scenarios-and-executereplaceaudit-protocols]]
