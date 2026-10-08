---
id: '29cd9f81-1776-43e2-a522-c363e9d490b7'
title: "A.1.0 Overview and opening"
tldr: "The day's learning goals for the alignment intro, and a short map of AI risk areas: misalignment, misuse and systemic risks."
summary_for_tutor: "Opening of worksheet A.1 AI Alignment Intro. It lists the day's goals (risk decomposition, alignment targets, training stories, goal-directedness, uncertain risks, timelines, the Hugging Face incident) and defines misalignment, misuse and systemic risks (AI-enabled coups, concentration of power, gradual disempowerment, loss of control). It points to the AISafety.com field map. The day asks: what behavior do we want, why would training produce it, and what can we infer from behavior."
authors:
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/alignment/ai-alignment-intro/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
**Iliad Intensive, 6 October 2026, San Francisco**

By the end of the day, you will be able to:

:::callout {title="What you'll learn" tone="neutral"}

* understand the basic decomposition of risks into AI misalignment, misuse, power grabs, and others;  
* explain different alignment targets like coherent extrapolated volition, intent alignment, or AI that follows a constitution;  
* reason about training stories and outer and inner (mis)alignment, challenges to these notions, and the relationship to inductive biases;  
* discuss whether AI systems develop goals and understand the basic arguments for instrumental convergence;  
* discuss foundational questions about the level of risk and different high-level approaches to solving the AI alignment problem;
* distinguish model training, an agent rollout, a benchmark and an evaluation;
* assess a past prediction and write a forecast with an explicit deadline and resolution rule;
* use the Hugging Face incident to discuss reward hacking, generalization, agent interaction and containment.

:::

%% Facilitator logistics (hidden from learners):
\## Roadmap for today

Today we start with discussing the larger AI safety landscape, and then discuss alignment targets, training, agency and uncertainty, and we wrap up discussing timelines and the Hugging Face incident. Most of the day is reading and discussion based. 

| Time        | Session                                          | Breakdown                                                             |
| ----------- | ------------------------------------------------ | --------------------------------------------------------------------- |
| 10:00–10:30 | Opening: AI safety landscape and course overview | Introduction, landscape and overview                                  |
| 10:30–11:25 | 1. Alignment targets                             | 5 min introduction, 25 min reading, 15 min discussion, 10 min debrief |
| 11:25–11:35 | Break                                            | 15 min                                                                |
| 11:35–12:30 | 2. Alignment problem decompositions              | 5 min introduction, 25 min reading, 15 min discussion, 10 min debrief |
| 12:30–13:30 | Lunch                                            | 60 min                                                                |
| 13:30–14:20 | 3. Goal-directedness                             | 5 min introduction, 25 min reading, 10 min discussion, 10 min debrief |
| 14:20–15:10 | 4. Uncertain risks and outlook                   | 5 min introduction, 25 min reading, 10 min discussion, 10 min debrief |
| 15:10–15:20 | Break                                            | 10 min                                                                |
| 15:20–16:20 | 5. Timelines, takeoff and checking predictions   | 10 min introduction, 40 min reading, 10 min discussion                |
| 16:20–16:30 | Break                                            | 10 min                                                                |
| 16:30–17:40 | 6. Hugging Face incident                         | 15 min explanation, 45 min reading, 10 min discussion                 |
| 17:40–18:00 | Quiz and feedback                                |                                                                       |
%%

\### Opening: AI safety landscape and course overview

**10:00–10:30**  Intro and landscape overview. The [AISafety.com field map](https://aisafety.com/map) shows how research, institutions, communication and support work address different parts of AI safety. 

Its 16 category names are reproduced below. 

| Area          | Map categories                                                    |
| ------------- | ----------------------------------------------------------------- |
| Research      | Conceptual research; Empirical research                           |
| Decisions     | Governance; Strategy; Forecasting; Advocacy                       |
| Capacity      | Funding; Research support; Career support; Training and education |
| Communication | Resource; Blog; Newsletter; Podcast; Video                        |

**Misalignment** concerns systems acting against intended goals or constraints. 
**Misuse** concerns people using AI to cause harm. 
**Systemic risks**: can arise through AI enabled coups, concentrations of power, gradual disempowerment, or total loss of control. Today concentrates on alignment within this wider landscape. The opening section of the reading guide explores the relationship among these risks.

Today introduces questions: What behavior do we want of AIs? Why would training produce it? What can we infer from behavior?
