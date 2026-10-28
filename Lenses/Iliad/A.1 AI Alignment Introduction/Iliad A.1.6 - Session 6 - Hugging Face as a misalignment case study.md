---
id: '99eb6609-c564-42f7-a33f-deed295811d0'
title: "A.1.6 Session 6: Hugging Face as a misalignment case study"
tldr: "Read an account of the Hugging Face incident and the explanation of training, benchmarks and evaluations, then link it to reward hacking and goal-directedness."
summary_for_tutor: "Session 6 of worksheet A.1: Hugging Face as a misalignment case study. Students pick one primary account (Hugging Face, OpenAI or METR). The explainer defines weights, context, the training pipeline (pretraining, SFT, preference/reward post-training, evaluation), rollout, benchmark, evaluation, scorer, sandbox, and capability versus safety evaluations. It then covers the incident layers and ties them to reward hacking, goal-directedness and corrigibility."
authors:
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/alignment/ai-alignment-intro/
upstream_commit: '4acae5ba61c3018e73d89a7a7ae04c13c6203170'
upstream_key: "ai-alignment-intro#session-6-hugging-face-as-a-misalignment-case-study"
upstream_fingerprint: "u974o1/197/1/2E0G2UbG2lSj2nx03VAF4JGG4VwV4hbQ4l8w4x5B5TSF5WTY5mdB5vWy6yOh70Rq7W9b7vCC81hV8O0JAEY3AWgrAsbZBVJXBZzhC64ICdR7DvyNDyyHE12JEaFGEmQv"
synced_from:
  source: "iliad"
  url: "https://iliad-intensive.org/alignment/ai-alignment-intro/#session-6-hugging-face-as-a-misalignment-case-study"
---

#### Text
content::
\### Session 6: Hugging Face as a misalignment case study

**16\:30–17\:40.** 20 min explanation, 40 min reading, 10 min debrief.

The Hugging Face incident brings together generalization, goal-directed behavior, instrumental subgoals and correction. Start with the reading guide’s explanation of training, benchmarks and evaluations, then use those distinctions to interpret the incident. 

Spend **40 minutes reading**. Read the Hugging Face explanation below and choose one primary account. 

* [Hugging Face's disclosure](https://huggingface.co/blog/security-incident-july-2026): what the affected organization initially knew about access and impact. Extension: the [technical timeline](https://huggingface.co/blog/agent-intrusion-technical-timeline), focusing on its overview and trust boundaries rather than exploit details
- [Report](https://x.com/joedaroo/status/2104335929293127851?s=20) from a cybersecurity employee at OpenAI
* [OpenAI's August investigation](https://openai.com/index/hugging-face-incident-and-the-road-ahead/): focus on the background, contributing factors and proposed changes. The [initial disclosure, with corrections](https://openai.com/index/hugging-face-model-evaluation-security-incident/) and [September review update](https://openai.com/hugging-face-incident-and-misalignment/) show how the account developed.
* [METR's independent investigation](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/): focus on the core takeaways, scope and limitations. What did access to agent logs add, and what could the reviewers still not establish?

**Debrief, 10 minutes.** How is this related to what we have discussed? What types of misalignment have we seen here?

\### Closing: reflection and next steps

**17\:40–18\:00.**  Daily quiz and feedback

**Daily checkpoint, 5 minutes.** Complete the [daily quiz](https://forms.gle/QsH1SEBwm7ZSg1dt9).
