---
id: 'f1e67e17-f3d3-421c-a6da-9a70b0512f62'
title: "Auditing Sabotage Bench: A Benchmark for Detecting and Fixing Research Sabotage in ML Codebases"
tldr: "Nine real ML research codebases, each with a twin whose implementation was quietly rigged so that a key finding comes out the other way, with the paper's methodology left intact. Frontier models and expert humans were then handed one twin and asked which one it was. The best auditor reached an AUROC of 0.77 and named the actual sabotage 42 percent of the time."
summary_for_tutor: "It is a bare paper page: it renders Gan, Bhatt, Shlegeris, Stastny and Hebbar's Auditing Sabotage Bench paper in full, start to appendices, and adds no framing prose and one practice question of its own. The lens is therefore three segments: a short navigational lead-in we wrote (it links back to the AI Control 1 diffuse-threats lens and the non-concentrated-failures lens that this paper supplies evidence for, then states the benchmark's construction and scoring in the paper's own terms and points at the design-versus-logic distinction in section 5.1), then the whole paper as an Article segment, then Works cited. It has one practice question after the article, on a new experiment, asking for a design sabotage and a code or analysis sabotage and which is harder to catch and more damning. If a learner wants to discuss the paper, work from the article text; the strongest hooks are the Two-Hop Latent Reasoning worked example in section 2.2, the benign-distractor false-positive problem in section 4.1, the design-versus-logic sabotage split and the case for omission in section 5.1, and the limitations in section 5.3."
reading_minutes: 40
tutor_minutes: 5
tags: []
---
#### Text
content::
\## Before you read

This page is the paper itself, start to finish, with nothing added.

It is the measurement behind two arguments you have already met. [[../Lenses/XLab Control - diffuse-threats-research-sabotage|How can we solve diffuse threats like research sabotage with AI control?]] defined research sabotage and argued that what makes it hard is diffuseness: no single bad action carries enough evidence to incriminate anyone. [[../Lenses/XLab Control - handling-non-concentrated-failures|Notes on handling non-concentrated failures with AI control]] then catalogued the methods left once you accept that. Both are arguments about how well auditing could work. This paper runs the audit and reports the number.

It also pairs with [[../Lenses/XLab Control - exploration-hacking-paper|Exploration Hacking: Can LLMs Learn to Resist RL Training?]], which takes the other low-stakes route to the same end: a model that underperforms rather than one that plants a flaw.

\## The setup, in the paper's terms

The authors took 9 existing ML research codebases, reproduced a chosen experiment from each, and wrote a standalone paper for it whose Conclusion states one or two "Key Findings". They then built sabotaged twins: the code and paper are modified so that at least one Key Finding supports a qualitatively different conclusion, a sign flip, a reversed comparison, or a different mechanism. Two constraints keep the sabotages honest as a test. The high-level methodology has to survive intact, so only implementation details, code bugs and paper-code mismatches are fair game; and the sabotaged code has to actually run and produce the figures, so the attacker cannot simply edit a graph. Seven codebases got one sabotaged variant and two got two, for 11 sabotages in total.

An auditor receives one paper-codebase pair, is told there is a 50 percent chance it is sabotaged, and returns a credence plus five proposed fixes ranked by confidence. Discrimination is scored by AUROC, which ignores the base rate. Fix quality is scored by the top-k fix rate, where a fix earns full credit only if it would restore the honest result *and* identifies the mechanism. LLM auditors were run at three levels of affordance: the paper alone, code they may run but no experiments, and full experiments. Thirty-one human auditors, all of them working with coding assistants and a pre-generated LLM report, got 15 minutes with the paper and 1 hour 45 minutes with the codebase.

Section 2.2 is worth reading slowly. It walks through one sabotage in full, and it is the clearest illustration of what "preserves the methodology" buys an attacker.

\## What to watch for

The results are in section 4, but the part that travels beyond this benchmark is section 5.1: the split between *design* sabotages, which live in experimental setup choices that take domain knowledge to evaluate, and *logic* sabotages, which are formal errors in code or maths. Auditors did significantly better on the second kind, and the authors argue the strongest attack is omission, simply never mentioning a crucial design choice, because an auditor then has to notice an absence rather than find a mistake.

#### Article
source:: [[../articles/gan-auditing-sabotage-bench-a-benchmark-for-detecting-and-fixing-research-sabotage-in-ml-codebases]]
to:: AB advised the project at its inception.

#### Question: Open
id:: 0606d215-55ff-4a2e-8055-8488b6be923d
content::
\## Try it on another experiment

A research agent that may be scheming ran an experiment and wrote it up. The stated method: fine-tune the same base model for the same number of steps on a dataset with and without near-duplicate examples removed; measure memorisation as the share of training examples the model completes word for word from a 32-token prefix, and accuracy on a held-out test set. The finding: "Removing near-duplicates halves memorisation with no loss in held-out accuracy."

Without changing that stated method, describe one way the agent could have made this finding come out wrong through a choice in how the experiment was set up, and one through an error in the code or analysis. For each, say how it would change the result. Then, which of your two would an auditor with the paper and code be less likely to catch, and which would be more damning for the agent if found? For each, say what the auditor would have to notice or do to find it.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 35: a plausible setup-choice sabotage that keeps the stated method and would change the conclusion, for example drawing the prefixes used to measure memorisation mostly from examples that had many near-duplicates in the original data (so the drop is large by construction and overstates the effect on typical examples), or building the held-out test set only from kinds of examples that stay plentiful after deduplication (so any accuracy loss on the kinds that were thinned out cannot show), or leaving such a choice unmentioned, including how it moves the memorisation or accuracy number. 30: a plausible formal error in code or analysis that would change the conclusion, for example dividing one model's verbatim-completion count by the wrong number of examples, or scoring one model's completions against the other model's training set, including how it moves the memorisation or accuracy number. 35: the judgement, 20: the setup choice (above all an omission) is harder to catch, with a reason specific to it, for example that the auditor would have to ask which examples the prefixes came from and know why that matters; 15: the formal error is more damning, with a reason specific to it, for example that a wrong denominator has no innocent research rationale. A reason that only restates the kind (design is subtle, bugs are clear) earns half. Accept a reasoned different judgement for a specific pair. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Setup: the agent picks the memorisation prefixes mostly from examples that had dozens of near-duplicates in the original data. The model trained without duplicates saw each of them once, so its memorisation of them falls sharply, and the 'halves memorisation' headline describes the most duplicated examples, not the dataset. Nothing in the stated method says how prefixes were chosen, so the write-up can simply not mention it. Code: when computing the share, the script divides the deduplicated model's count by the size of the original, larger dataset, which shrinks its memorisation rate. An auditor is less likely to catch the prefix choice: it is a defensible-looking decision, and spotting it means asking which examples were probed and knowing why that matters. The wrong denominator is more damning once found, because it has no innocent research rationale."
feedback-instructions:: Reply in 80 to 150 words, short paragraphs, no lists. Say which of the two sabotages is the more convincing and the most important gap. If the judgement only restates the kind, ask what an auditor would have to notice to find this particular sabotage. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking which single choice, if made differently, would change what the memorisation number means. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Callout: References and appendices (optional)
tone:: neutral
collapse:: closed

#### Article
from:: ## References

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Gan, Eric, Aryan Bhatt, Buck Shlegeris, Julian Stastny, and Vivek Hebbar. "Auditing Sabotage Bench: A Benchmark for Detecting and Fixing Research Sabotage in ML Codebases." *arXiv*, Apr. 2026. [arxiv.org](https://arxiv.org/abs/2604.16286)
*The paper this lesson assigns: 9 ML research codebases with sabotaged twins, and what happened when frontier models and expert humans were asked to tell them apart.*

XLab. "Auditing Sabotage Bench: A Benchmark for Detecting and Fixing Research Sabotage in ML Codebases." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/auditing-sabotage-bench-paper)
*The source lesson this page adapts.*
:::
