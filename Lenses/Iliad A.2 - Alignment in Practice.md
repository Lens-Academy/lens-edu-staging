---
id: '3a8d0c5e-1c86-42bf-baf4-37c725dfab0f'
title: "A.2.1 Overview"
tldr: "What this day covers: how alignment is done at each stage of model development, from pretraining to deployment, and what you should already know."
summary_for_tutor: "Overview of worksheet A.2 (alignment in practice). Prerequisites: deep learning, LLMs, pretraining, post-training (SFT, RLHF), basics of interpretability. The day covers pretraining, post-training, deployment strategy and the deployment safety system, plus a design challenge. The aim is to reason about what each phase offers for alignment. Training has pretraining and post-training, sometimes with midtraining between."
authors:
  - Margot Stakenborg
  - Garrett Baker
  - Evžen Wybitul
source_url: https://iliad-intensive.org/alignment/alignment-in-practice/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Prerequisites

The students should have a good high-level understanding of the following:

* how deep learning works
* how LLMs work, e.g. what they take as input and produce as output
* LLM pre-training
* LLM post-training: supervised fine-tuning, RLHF
* basics of LLM interpretability

Some of these topics are taught in other modules of this course.

:::callout {title="What you'll learn" tone="neutral"}

The main goal is for the students to be able to intuitively reason about different phases in model development, to understand what affordances each phase gives us w.r.t. alignment, and to gain the confidence to read current research on empirical alignment. They will end the day having learnt about the main state of the art alignment methods and with a rough idea how they all fit together.

This will help the students form their own independent opinions on what the state of the art empirical alignment research looks like and what are its largest gaps. Thanks to having a rough map of the empirical alignment territory, they will also be able to better self-identify gaps in their own understanding.

:::

%% Facilitator logistics (hidden from learners):
\## Roadmap for today

- 10:00–10:15
  - Intro

- 10:15–11:15
  - Pretraining (presentation 15 min, readings 30 min)

- 11:15–12:30
  - Post-training (presentation 30 min, readings 45 min)

- *12:30-13:30*
  - *Lunch*

- 13:30–14:15
  - Deployment 1: strategy (presentation 15 min, readings 30 min)

- 14:15–15:00
  - Deployment 2: building the safety system (presentation 15 min, readings 30 min)

- *15:00-15:20*
  - *Break*

- 15:20–17:10
  - Design challenge

- 17:10–17:30
  - Quiz + feedback
%%

\## Reading guide

Today we will treat the different stages of the training pipeline, and how alignment is implemented practically in each of them.

In training, we have broadly two stages: pretraining and post-training (sometimes this is further split up into midtraining and post-training, where mid-training feeds the LLM already higher quality data).
