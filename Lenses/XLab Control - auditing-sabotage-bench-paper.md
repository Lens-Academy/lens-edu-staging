---
id: 'f1e67e17-f3d3-421c-a6da-9a70b0512f62'
title: "Auditing Sabotage Bench: A Benchmark for Detecting and Fixing Research Sabotage in ML Codebases"
tldr: "Nine real ML research codebases, each with a twin whose implementation was quietly rigged so that a key finding comes out the other way, with the paper's methodology left intact. Frontier models and expert humans were then handed one twin and asked which one it was. The best auditor reached an AUROC of 0.77 and named the actual sabotage 42 percent of the time."
summary_for_tutor: "Ported from XLab's AI Control curriculum, Module 5. It is a bare paper page: XLab renders Gan, Bhatt, Shlegeris, Stastny and Hebbar's Auditing Sabotage Bench paper in full, start to appendices, and adds no framing prose and no exercises of its own. The lens is therefore three segments: a short navigational lead-in we wrote (it links back to the Module 1 diffuse-threats lens and the non-concentrated-failures lens that this paper supplies evidence for, then states the benchmark's construction and scoring in the paper's own terms and points at the design-versus-logic distinction in section 5.1), then the whole paper as an Article segment, then Works cited. There are no questions, by design. If a learner wants to discuss the paper, work from the article text; the strongest hooks are the Two-Hop Latent Reasoning worked example in section 2.2, the benign-distractor false-positive problem in section 4.1, the design-versus-logic sabotage split and the case for omission in section 5.1, and the limitations in section 5.3."
reading_minutes: 45
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

This page is the paper itself, start to finish, with nothing added.

It is the measurement behind two arguments you have already met. [[../Lenses/XLab Control - diffuse-threats-research-sabotage|How can we solve diffuse threats like research sabotage with AI control?]] defined research sabotage and argued that what makes it hard is diffuseness: no single bad action carries enough evidence to incriminate anyone. [[../Lenses/XLab Control - handling-non-concentrated-failures|Notes on handling non-concentrated failures with AI control]] then catalogued the methods left once you accept that. Both are arguments about how well auditing could work. This paper runs the audit and reports the number.

It also sits next to [[../Lenses/XLab Control - exploration-hacking-paper|Exploration Hacking: Can LLMs Learn to Resist RL Training?]] in this module, which takes the other low-stakes route to the same end: a model that underperforms rather than one that plants a flaw.

\## The setup, in the paper's terms

The authors took 9 existing ML research codebases, reproduced a chosen experiment from each, and wrote a standalone paper for it whose Conclusion states one or two "Key Findings". They then built sabotaged twins: the code and paper are modified so that at least one Key Finding supports a qualitatively different conclusion, a sign flip, a reversed comparison, or a different mechanism. Two constraints keep the sabotages honest as a test. The high-level methodology has to survive intact, so only implementation details, code bugs and paper-code mismatches are fair game; and the sabotaged code has to actually run and produce the figures, so the attacker cannot simply edit a graph. Seven codebases got one sabotaged variant and two got two, for 11 sabotages in total.

An auditor receives one paper-codebase pair, is told there is a 50 percent chance it is sabotaged, and returns a credence plus five proposed fixes ranked by confidence. Discrimination is scored by AUROC, which ignores the base rate. Fix quality is scored by the top-k fix rate, where a fix earns full credit only if it would restore the honest result *and* identifies the mechanism. LLM auditors were run at three levels of affordance: the paper alone, code they may run but no experiments, and full experiments. Thirty-one human auditors, all of them working with coding assistants and a pre-generated LLM report, got 15 minutes with the paper and 1 hour 45 minutes with the codebase.

Section 2.2 is worth reading slowly. It walks through one sabotage in full, and it is the clearest illustration of what "preserves the methodology" buys an attacker.

\## What to watch for

The results are in section 4, but the part that travels beyond this benchmark is section 5.1: the split between *design* sabotages, which live in experimental setup choices that take domain knowledge to evaluate, and *logic* sabotages, which are formal errors in code or maths. Auditors did significantly better on the second kind, and the authors argue the strongest attack is omission, simply never mentioning a crucial design choice, because an auditor then has to notice an absence rather than find a mistake.

#### Article
source:: [[../articles/gan-auditing-sabotage-bench-a-benchmark-for-detecting-and-fixing-research-sabotage-in-ml-codebases]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Gan, Eric, Aryan Bhatt, Buck Shlegeris, Julian Stastny, and Vivek Hebbar. "Auditing Sabotage Bench: A Benchmark for Detecting and Fixing Research Sabotage in ML Codebases." *arXiv*, Apr. 2026. [arxiv.org](https://arxiv.org/abs/2604.16286)
*The paper this lesson assigns: 9 ML research codebases with sabotaged twins, and what happened when frontier models and expert humans were asked to tell them apart.*

XLab. "Auditing Sabotage Bench: A Benchmark for Detecting and Fixing Research Sabotage in ML Codebases." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/auditing-sabotage-bench-paper)
*The source lesson this page adapts.*
:::
