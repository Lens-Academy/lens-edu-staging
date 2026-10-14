---
id: '81cb70c2-4c70-4377-8092-159aa644f841'
title: "A.3.7 AI control reading exercise"
tldr: "Read parts of Redwood's case for AI control, then compare five control approaches: pick the most and least viable and try to reverse your judgment on each."
summary_for_tutor: "AI Control reading exercise of worksheet A.3. Students read specified sections of 'The Case for Ensuring That Powerful AIs Are Controlled', skim five approaches (AI Control, Ctrl-Z resampling, Untrusted Advice, Diffuse AI Control on Fuzzy Tasks, Evaluating CoT Monitorability), choose the most and least viable, and argue against their initial judgment. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Garrett Baker
source_url: https://iliad-intensive.org/alignment/alignment-in-practice-ii/
upstream_commit: 'd5fec17706ceed1fa028ca949b97b92dcc2f5f7e'
upstream_key: "alignment-in-practice-ii#ai-control-reading-exercise"
upstream_fingerprint: "mPC/245/1/0GEW0kbm10CI1AsK1Tl91aVO1eHl2AJS2dL72oYr32pr3pch3tHL48Py4Gld4SCn4dpv53sA5QcD5sik5wxN60nG6pHd6pfX7GTp7cIz7dTs7vw98Opx8TLg8nYr93cb"
synced_from:
  source: "iliad"
  url: "https://iliad-intensive.org/alignment/alignment-in-practice-ii/#ai-control-reading-exercise"
---

#### Text
content::
\## AI Control: Reading Exercise

**Task.** Skim all five approaches, then choose the one that initially seems most viable and the one that seems least viable. Read both closely while trying to reverse your judgment: find the strongest problems with the apparently good approach and the strongest redeeming features of the apparently bad approach.

**Common introduction.** Read the following sections of [*The Case for Ensuring That Powerful AIs Are Controlled*](https://blog.redwoodresearch.org/p/the-case-for-ensuring-that-powerful):

::card[[../../shlegeris-the-case-for-ensuring-that-powerful-ais-are-controlled|The Case for Ensuring That Powerful AIs Are Controlled]]

- Opening, ending immediately before **“The control property”**

- **“The control property”**

- **“Evaluating whether you have control is doable”**

- **“Control evaluations and black-box techniques”**

- **“What might control techniques look like?”**

- First three paragraphs of **“Control is likely achievable for early transformatively useful AIs”**

**Approaches.**

:::require_x_optional_lenses{x=2}
::card[[../../Iliad reading - AI Control - Improving Safety Despite Intentional Subversion|AI Control: Improving Safety Despite Intentional Subversion]]

> (Redwood Research) — Use trusted models and scarce human audits to monitor, edit, or replace suspicious outputs from a stronger untrusted model.

::card[[../../bhatt-ctrl-z-controlling-ai-agents-via-resampling-abs|Ctrl-Z: Controlling AI Agents via Resampling]]

> (Redwood Research) — Resample suspicious actions to obtain safer alternatives and additional evidence of attempted subversion.

::card[[../../biddulph-untrusted-advice-for-ai-control-short-strong-advice-significantly-uplifts-weak-llms|Untrusted Advice for AI Control]]

> (Redwood Research) — Restrict the untrusted model to a low-bandwidth advice channel while a trusted model retains exclusive authority to act.

::card[[../../Iliad reading - Diffuse AI Control on Fuzzy Tasks|Diffuse AI Control on Fuzzy Tasks]]

> (Anthropic) — Adversarially improve the weak scoring process used to train untrusted models against repeated sabotage on hard-to-evaluate work.

::card[[../../guan-monitoring-monitorability|Evaluating Chain-of-Thought Monitorability]]

> (OpenAI) — Preserve and measure legible reasoning so chain-of-thought monitoring can serve as a scalable control layer.
:::

1.  [**AI Control: Improving Safety Despite Intentional Subversion**](https://arxiv.org/abs/2312.06942) (Redwood Research) — Use trusted models and scarce human audits to monitor, edit, or replace suspicious outputs from a stronger untrusted model.

2.  [**Ctrl-Z: Controlling AI Agents via Resampling**](https://arxiv.org/abs/2504.10374) (Redwood Research) — Resample suspicious actions to obtain safer alternatives and additional evidence of attempted subversion.

3.  [**Untrusted Advice for AI Control**](https://blog.redwoodresearch.org/p/untrusted-advice-for-ai-control-short) (Redwood Research) — Restrict the untrusted model to a low-bandwidth advice channel while a trusted model retains exclusive authority to act.

4.  [**Diffuse AI Control on Fuzzy Tasks**](https://alignment.anthropic.com/2026/diffuse-ai-control/) (Anthropic) — Adversarially improve the weak scoring process used to train untrusted models against repeated sabotage on hard-to-evaluate work.

5.  [**Evaluating Chain-of-Thought Monitorability**](https://arxiv.org/abs/2512.18311) (OpenAI) — Preserve and measure legible reasoning so chain-of-thought monitoring can serve as a scalable control layer.
