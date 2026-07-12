---
id: 762d43e8-9b9e-43d8-b2cb-ed2b35577973
tldr: "How do you test whether we could catch an AI sabotaging its work, without waiting for a real catastrophe? Redwood built BashArena: 637 gnarly sysadmin tasks where a red-team AI tries to sneak in attacks like exfiltrating secrets or escalating privileges, disguised as normal work. This post walks through what makes a good control setting, and the surprisingly hard design lessons learned building one."
summary_for_tutor: "Adam Kaufman (Redwood Research) introduces BashArena, a new high-stakes AI-control setting, and distills lessons on control-setting design. Explains the control-setting structure (main tasks vs. side tasks; a red team building attack policies, a blue team building protocols that detect and prevent attacks without hurting honest performance) and BashArena's advantages: 637 diverse, difficult, unsaturated bash main tasks and four handcrafted side tasks (download malware, exfiltrate secrets, escalate privileges, disable firewall) that essentially never trigger by accident. Covers its weaknesses (limited resistance to sandboxing, few side tasks) and general design principles: aim for transferable high-level dynamics, importance-sample to deployments where control actually matters, patch or ban 'overpowered' strategies, and expect main/side-task integration requirements (at the test-case and code level) to be stricter than they first appear."
title: "BashArena and Control Setting Design"
---

#### Article
source:: [[../articles/kaufman-basharena-and-control-setting-design]]
