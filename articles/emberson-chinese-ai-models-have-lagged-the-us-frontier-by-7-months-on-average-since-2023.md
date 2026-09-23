---
title: "Chinese AI models have lagged the US frontier by 7 months on average since 2023"
author:
  - "Luke Emberson"
source_url: "https://epoch.ai/data-insights/us-vs-china-eci"
published: 2026-01-02 
created: 2026-07-02
accessed: 2026-07-02
description: "Since 2023, every model at the frontier of AI capabilities, as measured by the Epoch Capabilities Index, has been developed in the United States. Over that same period, Chinese models have trailed US capabilities by an average of seven months, with a minimum gap of four months and a maximum gap of 14."
tags:
  - "article-importer"
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
---
%%
Add discussion note here:

This data insight is essentially a live chart with a short explainer; the ECI gap it reports will keep shifting as new models are benchmarked, so treat the specific figures (7-month average, 4-14 month range) as a snapshot rather than a fixed fact. Worth discussing with students: the gap tracks closely with the open-weight/closed-weight split, so it may say as much about release strategy as about underlying capability.

%%

Since 2023, every model at the frontier of AI capabilities, as measured by the Epoch Capabilities Index, has been developed in the United States. Over that same period, Chinese models have trailed US capabilities by an average of seven months, with a minimum gap of four months and a maximum gap of 14.

![ECI scores of US and Chinese models](https://epoch.ai/assets/images/data-insights/us-vs-china-eci/us-vs-china-eci.png)

This gap closely resembles the broader gap between proprietary and open-weight models. This is unsurprising since nearly all leading Chinese models are open-weight, while frontier US models remain closed.

## Learn more about this graph

We visualize the gap in capabilities between US and Chinese models, using the [Epoch Capabilities Index](https://epoch.ai/eci) (ECI). Since 2023, the gap has ranged from 4 to 14 months, with a mean gap of 7 months.

:::callout {title="Analysis" collapse="closed"}
To calculate the gap between US and Chinese models, we first find the set of models that had the highest ECI among models from their country upon release. We then drop the first of these models (LLaMA-65B for the US, and Baichuan1-7B for China), since these first models were likely not at the true frontier (ECI data starts in January 2023).

To quantify the gap on each day, we look at the ECI of the best Chinese model on that day, and then calculate how long it has been since the last time the leading US model was the same or worse than that score. We consider models to be the same performance if their scores are within 1 ECI point difference. We repeat this process for each day where values exist for both the US and China. In practice, the first point where a Chinese model surpasses GPT-4 is May 2024 (a gap of 14 months), and no Chinese model has yet surpassed the ECI of OpenAI’s o3 model, released in April 2025.
:::

## Explore this data
[Capabilities & Benchmarking](https://epoch.ai/benchmarks): Benchmark results featuring the performance of leading AI models on challenging tasks.
:::