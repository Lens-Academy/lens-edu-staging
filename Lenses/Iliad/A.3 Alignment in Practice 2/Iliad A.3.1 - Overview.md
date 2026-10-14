---
id: 'd13304b3-f497-40b8-8cbb-618a8cd14f7b'
title: "A.3.1 Overview"
tldr: "What this day covers: how transformers are trained and aligned (pretraining, RLHF, constitutional AI, RLVR), evals, chain-of-thought monitoring and AI control."
summary_for_tutor: "Overview of worksheet A.3 Alignment in Practice II. Prerequisites: calculus and linear algebra. Learning goals: the causal structure of a transformer, the training steps (pretraining, RLHF, constitutional AI, RLVR) with their alignment and capability limits, what evals and CoT monitoring do and where they fall short, and the main AI control techniques. The facilitator schedule covers lectures, a control paper reading and an RLHF theory session."
authors:
  - Garrett Baker
source_url: https://iliad-intensive.org/alignment/alignment-in-practice-ii/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Prerequisites

- Calculus, and linear algebra

:::callout {title="What you'll learn" tone="neutral"}

- Know the causal structure of a transformer
- Know the steps of transformer training (pretraining, RLHF, constitutional AI, and RLVR) along with what they try to do with respect to alignment & capabilities, and where they fall short with respect to alignment & capabilities
- Know what evals try to do, and their shortcomings
- Know what chain of thought monitoring tries to do, and its shortcomings
- Know broadly the techniques AI control recommends

:::

%% Facilitator logistics (hidden from learners):
\## Roadmap for today
%%

%% Facilitator logistics (hidden from learners):
\### Primary: Control first

| Time        | Session                                  |
|:------------|:-----------------------------------------|
| 10:00–10:10 | Welcome and framing                      |
| 10:10–11:05 | Garrett’s lecture, Part I                |
| 11:05–11:20 | Discussion prompts                       |
| 11:20–11:30 | Break                                    |
| 11:30–12:20 | Garrett’s lecture, Part II               |
| 12:20–12:30 | Questions and transition                 |
| 12:30–1:30  | Lunch                                    |
| 1:30–1:40   | Control exercise introduction            |
| 1:40–2:45   | Individual control-paper reading         |
| 2:45–2:55   | Break                                    |
| 2:55–3:50   | Control discussion                       |
| 3:50–4:05   | Break                                    |
| 4:05–5:05   | Aden’s theoretical RLHF session          |
| 5:05–5:45   | Discussion, overflow, or reserve reading |
| 5:45–6:00   | Quiz + feedback                          |

*Garrett continues after lunch*

| Time        | Session                          |
|:------------|:---------------------------------|
| 10:00–10:10 | Welcome and framing              |
| 10:10–11:05 | Garrett’s lecture, Part I        |
| 11:05–11:20 | Discussion prompts               |
| 11:20–11:30 | Break                            |
| 11:30–12:30 | Garrett’s lecture, Part II       |
| 12:30–1:30  | Lunch                            |
| 1:30–2:00   | Garrett’s lecture, overflow      |
| 2:00–3:00   | Aden’s theoretical RLHF session  |
| 3:00–3:10   | Break                            |
| 3:10–3:20   | Control exercise introduction    |
| 3:20–4:25   | Individual control-paper reading |
| 4:25–4:35   | Break                            |
| 4:35–5:45   | Control discussion               |
| 5:45–6:00   | Quiz + feedback                  |
%%
