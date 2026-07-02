---
id: ed1aaff0-ac16-4c23-bbec-4bc8c41301e9
title: "Empirical Control Research"
tldr: Control's distinctive claim is that it's evaluable now — and these are the flagship tests. Resampling protocols in Ctrl-Z, control-setting design in BashArena, and measuring whether models can sabotage real ML research code without getting caught.
---

#### Text
content::
(Optional — for those who want to see control tested, not just theorized.) Control's distinctive claim is that it's *evaluable now*. These are the flagship empirical studies. Start with the original paper's setting: GPT-4 writing code, GPT-3.5 watching it.

- [AI Control: Improving Safety Despite Intentional Subversion](https://arxiv.org/abs/2312.06942) — the original control evaluation paper (trusted monitoring, untrusted monitoring, deferring protocols in a backdoored-code setting).

Then two follow-ups, imported below: Ctrl-Z on resampling protocols, and BashArena on designing better control settings. Finally, research sabotage in real ML codebases.

#### Article
source:: [[../articles/shlegeris-ctrl-z-controlling-ai-agents-via-resampling]]

#### Article
source:: [[../articles/kaufman-basharena-and-control-setting-design]]

#### Article
source:: [[../articles/gan-research-sabotage-in-ml-codebases]]

#### Chat
instructions::
TLDR of what the user just engaged with: three empirical control works — (1) Ctrl-Z: resampling suspicious agent actions (taking multiple samples and picking/checking) as a control protocol for multi-step agent settings, substantially improving the safety/usefulness frontier; (2) BashArena: designing a realistic sysadmin control setting and lessons for what makes control settings informative; (3) Research Sabotage in ML Codebases: measuring whether models can subtly sabotage ML research code without detection. Plus optionally the original AI Control paper (arxiv 2312.06942).

Discussion topics to explore:
- What makes a control setting informative vs toy — task realism, attack surface, monitor quality?
- Why is resampling surprisingly powerful against schemers (attacks are risky; resamples destroy rare attack opportunities)?
- From the sabotage study: how detectable is subtle sabotage today, and which way is that trending?

Ask which empirical result most changed their estimate of whether control will work in practice.
