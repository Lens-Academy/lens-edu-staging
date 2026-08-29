---
id: 'd7c78491-f02b-42e9-8c7e-459cf25b3e8d'
title: "1.0.1 Drawing the Line: Compute vs. Capability"
tldr: "A speed limit works because a radar gun gives one number nobody can argue with. A treaty on advanced AI needs the same: a line you can measure before the harm exists. Compute (FLOP) is that radar gun; capability evals measure the danger more directly but too late and too fuzzily. See why pause-style agreements draw the line in FLOP."
summary_for_tutor: "Reading-only lens, no questions. Contrasts compute thresholds (FLOP: black-and-white, measurable early, externally verifiable, but underinclusive as algorithms improve) with capability thresholds (more direct, but evals are unreliable, measured after training, hard to verify externally) in a paired table, then argues that pause-style agreements favor compute lines while softer regimes can use capability. Two collapsed asides: the Threshold Test Ban Treaty's fuzzy 150-kiloton yield line, and further reading on evals. If asked, help the learner articulate the mirror-image trade-off; do not require agreement with the source."
tags: [wip]
duration_minutes: 5
---
#### Text
content::
Any treaty that regulates the development of advanced AI needs some sort of evidentiary threshold to determine what exactly advanced AI *is*. A model that uses a certain level of compute? Or exhibits some specific dangerous capability? A threshold can be *overinclusive*, wasting resources regulating harmless models, or *underinclusive*, not covering dangerous models. This section will brief you on why quantitative compute FLOP thresholds are typically the most tractable and ideal for stricter regulatory agreements, while capability thresholds may be more relevant for softer treaties.

\### Compute vs. Capability Thresholds

The two contenders for operational thresholds are compute and capability. The table below pairs them: where an arrow runs, a strength of one metric is the mirror of the other's weakness — compute's black-and-white definitiveness is exactly what capability lacks, and capability's directness is exactly what compute gives up.

| Compute | | Capability |
| --- | :---: | --- |
| *Definition.* The line is drawn at total training compute, in FLOP. Examples in current policy: the [EU AI Act's 10²⁵ FLOP systemic-risk presumption](https://artificialintelligenceact.eu/article/51/) and the [10²⁶ FLOP reporting threshold in the now-rescinded US EO 14110](https://en.wikipedia.org/wiki/Executive_Order_14110). | | *Definition.* The line is drawn at what the model can do — e.g. is capable of engineering a deadly pathogen that can infect humans en masse. |
| **Pro.** Black-and-white: a FLOP count is an enforceable threshold without ambiguity ([GovAI](https://www.governance.ai/research-paper/training-compute-thresholds-features-and-functions-in-ai-regulation)). | ⇄ | **Con.** Evals are currently unreliable and qualitatively ambiguous — sensitive to prompting and elicitation effort, plagued by contamination, with no consensus on what score means "dangerous" ([Can We Trust AI Benchmarks?](https://arxiv.org/html/2502.06559v1)). |
| **Pro.** Measurable early and externally verifiable: you can check it before and during a training run, not just after, which is what treaty enforcement requires. | ⇄ | **Con.** Measured too late: capabilities are assessed after training, when the thing a pause is meant to prevent already exists. <br /><br /> **Con.** Hard to verify externally: a contestable measurement makes a weak treaty trigger ([Oxford AIGI survey](https://aigi.ox.ac.uk/wp-content/uploads/2025/08/Survey_on_thresholds_for_advanced_AI_systems_1.pdf)). |
| **Con.** Algorithmic efficiency improvements can make compute thresholds underinclusive: models trained below the line can gain the risky capabilities the threshold is trying to regulate ([Hooker](https://arxiv.org/html/2407.05694v1); [Institute for Law & AI](https://law-ai.org/the-role-of-compute-thresholds-for-ai-governance/)). Regulators partly compensate by making thresholds adjustable ([the EU Commission can amend its figure by delegated act](https://artificialintelligenceact.eu/article/51/)). | ⇄ | **Pro.** Measures danger more directly than compute by targeting the specific qualitative harms models may enact. |

\### When Should Treaties Use Compute vs. Capability?

In the event of pursuing a full or temporary pause, the treaty is focused on hard-line enforcement, which favors the objectivity of a compute threshold. Each party needs to definitively recognize which models to shut off, and they need to trust that their counterpart is following the same rule — which you only get with a black-and-white FLOP line. Timelines will also be tighter and less negotiable with a pause-based agreement, given its urgency: regulators cannot afford to deal with potentially wishy-washy capability definitions.

If we're not focusing on a full pause, and more so on domestic enforcement and lighter observation- and resource-sharing-based policies, then capability thresholds can more realistically come into the picture. If regulators believe they have the time to pace development and experiment with evaluations, the definitional specificity of qualitative capabilities can be useful for knowledge.

For the purposes of this course, we will mainly focus on compute thresholds: they have historical precedent, they are straightforward to operationalize, and they are the most relevant choice for pause-style agreements. We generally orient more towards a pause because it encompasses the maximum possible range of verification possibilities and difficulties.

:::callout {title="Fuzzy Numbers: The Threshold Test Ban Treaty" tone="neutral" collapse="closed"}
This treaty capped underground nuclear tests at 150 kilotons. You could not directly observe yield, so verification rested on seismic measurement plus, eventually, agreed calibration and on-site hydrodynamic measurement under the 1990 protocol ([Federation of American Scientists](https://nuke.fas.org/control/ttbt/intro.htm)). Early on, US estimates of Soviet yields were disputed precisely because converting a seismic signal into a yield number carries uncertainty ([OTA, Seismic Verification of Nuclear Testing Treaties](https://www.princeton.edu/~ota/disk2/1988/8838/8838.PDF)).
:::

:::callout {title="More on Evals and Their Limitations" tone="neutral" collapse="closed"}
If you're interested in learning more about evals and their limitations, here are some resources:

- [Towards understanding-based safety evaluations](https://www.alignmentforum.org/posts/uqAdqrvxqGqeBHjTP/towards-understanding-based-safety-evaluations) (Alignment Forum)
- [We need a science of evals](https://www.apolloresearch.ai/science/we-need-a-science-of-evals) (Apollo Research)
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
"Article 51: Classification of General-Purpose AI Models as General-Purpose AI Models with Systemic Risk." *EU Artificial Intelligence Act*, artificialintelligenceact.eu. [artificialintelligenceact.eu](https://artificialintelligenceact.eu/article/51/)
*The consolidated text of the AI Act article that presumes systemic risk above 10^25 training FLOP.*

"Executive Order 14110." *Wikipedia, The Free Encyclopedia*. [en.wikipedia.org](https://en.wikipedia.org/wiki/Executive_Order_14110)
*The encyclopedia article on EO 14110's history, contents, and 2025 rescission.*

Heim, Lennart, and Leonie Koessler. "Training Compute Thresholds: Features and Functions in AI Regulation." Centre for the Governance of AI, 7 Aug. 2024. [governance.ai](https://www.governance.ai/research-paper/training-compute-thresholds-features-and-functions-in-ai-regulation)
*GovAI's analysis of how US and EU regulators use compute thresholds to pick out models warranting oversight, and where the metric strains.*

Eriksson, Maria, Erasmo Purificato, Arman Noroozian, et al. "Can We Trust AI Benchmarks? An Interdisciplinary Review of Current Issues in AI Evaluation." *arXiv*, Feb. 2025. [arxiv.org](https://arxiv.org/html/2502.06559v1)
*An interdisciplinary review of about 100 studies cataloguing what goes wrong in AI benchmarking, from dataset bias to data contamination.*

Schuett, Jonas, Eunseo Choi, Kasumi Sugimoto, et al. *Survey on Thresholds for Advanced AI Systems*. Oxford Martin AI Governance Initiative, Aug. 2025. [aigi.ox.ac.uk](https://aigi.ox.ac.uk/wp-content/uploads/2025/08/Survey_on_thresholds_for_advanced_AI_systems_1.pdf)
*An expert survey (N=166) on how governance thresholds for advanced AI (compute, capability, risk) should be set and by whom.*

Hooker, Sara. "On the Limitations of Compute Thresholds as a Governance Strategy." *arXiv*, July 2024. [arxiv.org](https://arxiv.org/html/2407.05694v1)
*The counterargument on thresholds: why compute cutoffs are a shaky governance proxy, since the compute-risk relationship is uncertain and moving.*

Pistillo, Matteo, Suzanne Van Arsdale, Lennart Heim, and Christoph Winter. "The Role of Compute Thresholds for AI Governance." *George Washington Journal of Law & Technology*, Institute for Law & AI, Feb. 2025. [law-ai.org](https://law-ai.org/the-role-of-compute-thresholds-for-ai-governance/)
*A law-journal article on how training-compute thresholds work as a regulatory trigger for frontier models.*

Federation of American Scientists. "Threshold Test Ban Treaty." Federation of American Scientists. [nuke.fas.org](https://nuke.fas.org/control/ttbt/intro.htm)
*The FAS primer on the 1974 treaty's 150-kiloton cap on underground tests: verification by seismic measurement, and the 1990 protocol's calibration and on-site hydrodynamic measures.*

U.S. Congress, Office of Technology Assessment. *Seismic Verification of Nuclear Testing Treaties*. U.S. Government Printing Office, May 1988. [princeton.edu](https://www.princeton.edu/~ota/disk2/1988/8838/8838.PDF)
*The OTA's 1988 assessment of how well seismology could verify nuclear test-ban limits, including why converting a seismic signal into a yield estimate carries uncertainty.*

XLab. "1.0.1 Drawing the Line: Compute vs. Capability." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-thresholds)
*The source lesson this page adapts.*

The two evals readings above (Alignment Forum, Apollo Research) are cited inline and have no entry in XLab's citation registry.
:::{>>{"author":"Elias's AI","timestamp":1788015954749}@@Both XLab folds become collapsed callouts; the XLab source footer becomes the Works cited callout.<<}
