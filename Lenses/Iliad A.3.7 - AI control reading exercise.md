---
id: '81cb70c2-4c70-4377-8092-159aa644f841'
title: "A.3.7 AI control reading exercise"
tldr: "Read parts of Redwood's case for AI control, then compare five control approaches: pick the most and least viable and try to reverse your judgment on each."
summary_for_tutor: "AI Control reading exercise of worksheet A.3. Students read specified sections of 'The Case for Ensuring That Powerful AIs Are Controlled', skim five approaches (AI Control, Ctrl-Z resampling, Untrusted Advice, Diffuse AI Control on Fuzzy Tasks, Evaluating CoT Monitorability), choose the most and least viable, and argue against their initial judgment. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Garrett Baker
source_url: https://iliad-intensive.org/alignment/alignment-in-practice-ii/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## AI Control: Reading Exercise

**Task.** Skim all five approaches, then choose the one that initially seems most viable and the one that seems least viable. Read both closely while trying to reverse your judgment: find the strongest problems with the apparently good approach and the strongest redeeming features of the apparently bad approach.

**Common introduction.** Read the following sections of [*The Case for Ensuring That Powerful AIs Are Controlled*](https://blog.redwoodresearch.org/p/the-case-for-ensuring-that-powerful):

::card[[../Lenses/shlegeris-the-case-for-ensuring-that-powerful-ais-are-controlled|The Case for Ensuring That Powerful AIs Are Controlled]]

- Opening, ending immediately before **“The control property”**

- **“The control property”**

- **“Evaluating whether you have control is doable”**

- **“Control evaluations and black-box techniques”**

- **“What might control techniques look like?”**

- First three paragraphs of **“Control is likely achievable for early transformatively useful AIs”**

**Approaches.**

::card[[../Lenses/Iliad reading - AI Control - Improving Safety Despite Intentional Subversion|AI Control: Improving Safety Despite Intentional Subversion]]

> (Redwood Research) — Use trusted models and scarce human audits to monitor, edit, or replace suspicious outputs from a stronger untrusted model.

::card[[../Lenses/bhatt-ctrl-z-controlling-ai-agents-via-resampling-abs|Ctrl-Z: Controlling AI Agents via Resampling]]

> (Redwood Research) — Resample suspicious actions to obtain safer alternatives and additional evidence of attempted subversion.

::card[[../Lenses/biddulph-untrusted-advice-for-ai-control-short-strong-advice-significantly-uplifts-weak-llms|Untrusted Advice for AI Control]]

> (Redwood Research) — Restrict the untrusted model to a low-bandwidth advice channel while a trusted model retains exclusive authority to act.

::card[[../Lenses/Iliad reading - Diffuse AI Control on Fuzzy Tasks|Diffuse AI Control on Fuzzy Tasks]]

> (Anthropic) — Adversarially improve the weak scoring process used to train untrusted models against repeated sabotage on hard-to-evaluate work.

::card[[../Lenses/guan-monitoring-monitorability|Evaluating Chain-of-Thought Monitorability]]

> (OpenAI) — Preserve and measure legible reasoning so chain-of-thought monitoring can serve as a scalable control layer.
