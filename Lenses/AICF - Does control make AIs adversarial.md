---
id: '6dca6f21-cf9e-40ea-8f19-96f8f1e5c925'
title: "Does control make AIs more adversarial?"
reading_minutes: 10
tutor_minutes: 7
tldr: "Could writing about AIs as adversaries to be watched and contained make models more adversarial? A small fine-tuning study on control writing and a larger pretraining study on AI writing in general give partial evidence, with a fix that does not require dropping control."
summary_for_tutor: "Optional lens in Unit 4 of AI Control Fundamentals, Module 'Even done well, control makes things worse', on the criticism that control makes AIs more adversarial. The learner reads the summary, interpretation and limitations of Dmitrii Gusev and Vili Kohonen's 'Investigating Self-Fulfilling Misalignment and Collusion in AI Control' (LessWrong, March 2026). GPT-4.1 was fine-tuned on about 2,600 question-and-answer pairs (1.6M tokens) derived from AI control literature and tested in Anthropic's Agentic Misalignment blackmail scenario. Blackmail rates rose with 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) goals, and the no-goal baseline rose from 1% to 13%. A monitor sharing the agent's incentives did not collude. Grok 4 colluded in follow-up runs, but this was confounded by eval-awareness. The authors' caveats: one model family, one environment, small dataset, possible mean reversion, correlational results. Then excerpts from Cameron Tice, Puria Radmard and colleagues (Geodesic Research), 'Alignment Pretraining: AI Discourse Causes Self-Fulfilling (Mis)alignment' (LessWrong, December 2025): they pretrained 6.9B-parameter models on 500B tokens, varying only AI-related content. On their article-sourced questions, base-model misalignment went from 41% to 61% when misalignment discourse was upsampled and from 41% to 4% when positive alignment discourse was upsampled. Upsampling positive AI discourse beat filtering. Post-training shrank the differences but did not remove them. Their limits: single-turn binary-choice self-report evaluations, 6.9B models only, one seed, no RL post-training. In a footnote, which a short Lens text passes on, a rerun of their tampering test with about 100 times more data came out negative. Their study is about AI discourse in general, not control writing in particular. One scored question: what removing control papers from pretraining data would achieve and miss. Help the learner weigh the evidence. Do not overstate the result or dismiss it."
---
#### Text
content::
**The criticism: control makes AIs more adversarial.**

Writing about AIs as adversaries to be watched and contained ends up in the data future models learn from. If models pick up that picture of themselves, control research could make them more adversarial. Dmitrii Gusev and Vili Kohonen tested a small version of this. Read their summary, how they interpret the results, and their caveats.

#### Article
source:: [[../articles/gusev-investigating-self-fulfilling-misalignment-and-collusion-in-ai-control]]
from:: "## **TL;DR**"
to:: but it was brittle and confounded by eval-awareness.

#### Article
from:: It is not straightforward to interpret the results.
to:: the goals related to “goodness” jumped significantly from very small base rates.

#### Article
from:: "## **Limitations**"
to:: but those findings were confounded by eval-awareness.

#### Text
content::
Cameron Tice, Puria Radmard and colleagues at Geodesic Research ran a larger, controlled test of the general idea: does the way AI is described in pretraining data change how aligned a model is? Their study is about writing on AI in general, not control writing in particular. Read their summary, main results and limits.

#### Article
source:: [[../articles/cam-alignment-pretraining-ai-discourse-causes-self-fulfilling-mis-alignment]]
from:: "## TL;DR"
to:: We recommend labs pretrain for alignment, just as they do for capabilities.

#### Article
from:: "### Base Models: AI Discourse Causally Affects Alignment"
to:: but does not fully erase them.

#### Article
from:: "### Limitations"
to:: which now comprises a substantial portion of post-training compute at frontier labs.

#### Text
content::
In a footnote, the authors say they reran one test with about 100 times more data: the test of whether alignment survives later fine-tuning. This time the result was negative. Keep that in mind when you read "alignment-in-depth" in their summary.

#### Question: Open
id:: a5ec01cf-aa19-4072-88a9-1e45b0f5954a
force-feedback:: first
content::
\## How much does this show?

A lab reads both studies and decides to remove every AI control paper from its pretraining data. Using what the two studies found and did not find, say what this decision is likely to achieve, what it might miss, and what you would advise the lab to do.
assessment-instructions:: Score out of 100. Context for grading: one study fine-tuned a single model (GPT-4.1) on question-and-answer pairs made from AI control literature and found higher blackmail rates in one test scenario, with caveats: one model family, one environment, a small dataset, possible mean reversion. The other pretrained 6.9B-parameter models while varying only AI-related content in general, not control writing in particular. More misalignment discourse raised misalignment from 41% to 61%, more positive discourse about AI cut it to 4%, adding positive discourse worked better than filtering, and the differences shrank but did not vanish after post-training. 35: what removing control papers is likely to achieve: at most a modest, uncertain gain, because only the fine-tuning study points at control writing, and it showed an effect for one model in one test, not that control papers in pretraining make frontier models misaligned. 30: what it misses, any one of: control papers are a small part of the writing that portrays AI as dangerous, which the pretraining study shows matters in general, filtering did less than adding positive examples, or the effect shrinks after post-training. 35: advice grounded in the studies, for example add documents about AIs behaving well to the pretraining data, which worked better than filtering, or test the effect directly before deciding, while keeping the control research itself. Advice to go ahead with the removal also earns the 35 if the reason comes from the studies. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It might remove a small push toward misalignment, but only one small fine-tuning study ties control writing to worse behaviour, and only for one model in one test. It misses that the pretraining study was about writing on AI in general, so most of the effect would come from elsewhere, and that filtering worked less well than adding positive examples. I would advise the lab to add documents about AIs behaving well, keep its control research, and test the effect at its own scale."
feedback-instructions:: The learner weighs two studies through a lab's decision. The fine-tuning study: fine-tuning one model (GPT-4.1) on question-and-answer pairs from AI control literature raised blackmail rates in one test scenario, most in the 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) conditions, and in the no-goal baseline (1% to 13%), with the authors' caveats of one model family, one environment, a small dataset and possible mean reversion. The pretraining study is controlled and much larger (6.9B-parameter models, 500B tokens) and is about AI discourse in general, not control writing in particular. Upsampling misalignment discourse raised base-model misalignment from 41% to 61%, upsampling positive AI discourse cut it to 4%, adding positive discourse beat filtering, and differences shrank but persisted after post-training. A larger rerun of their tampering test was negative. So removing control papers targets a slice neither study isolates, leaves the bulk of AI discourse, and uses the weaker of the two fixes. Good advice: upsample positive AI data, keep control research, or test the effect directly. One or two turns, 60 to 120 words each. Name what they got right and the most important limit they missed. No generic praise. Do not dismiss the worry or overstate it.
