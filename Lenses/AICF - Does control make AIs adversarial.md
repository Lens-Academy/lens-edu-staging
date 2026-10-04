---
id: '6dca6f21-cf9e-40ea-8f19-96f8f1e5c925'
title: "Does control make AIs adversarial?"
reading_minutes: 9
tutor_minutes: 8
tldr: "If models learn from text that describes AIs as adversaries to be contained, could they become more adversarial? A small 2026 study fine-tuned one model on AI control writing and found it blackmailed more often. A larger 2025 pretraining study found that how AI is described in training data changes how aligned models are, and that adding data about AIs behaving well helps."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. The learner reads the summary, interpretation, limitations and conclusions of Dmitrii Gusev and Vili Kohonen's 'Investigating Self-Fulfilling Misalignment and Collusion in AI Control' (LessWrong, March 2026). GPT-4.1 was fine-tuned on about 2,600 question-and-answer pairs (1.6M tokens) derived from AI control literature and tested in Anthropic's Agentic Misalignment blackmail scenario. Blackmail rates rose with 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) goals, and the no-goal baseline rose from 1% to 13%. A monitor sharing the agent's incentives did not collude. Grok 4 colluded in follow-up runs, but this was confounded by eval-awareness. The authors' caveats: one model family, one environment, small dataset, possible mean reversion, correlational results. This is a 'works and makes things worse' criticism: control discourse and practice might push models toward adversarial personas. Elias Schmied, whose list the learner may have read in this unit, says in a footnote that he does not think putting AI doom stories in the training data is a major factor. Then excerpts from Cameron Tice, Puria Radmard and colleagues (Geodesic Research), 'Alignment Pretraining: AI Discourse Causes Self-Fulfilling (Mis)alignment' (LessWrong, December 2025): they pretrained 6.9B-parameter models on 500B tokens, varying only AI-related content. On their article-sourced questions, base-model misalignment went from 41% to 61% when misalignment discourse was upsampled and from 41% to 4% when positive alignment discourse was upsampled. Upsampling positive AI discourse beat filtering. Post-training shrank the differences but did not remove them (Misalignment Upsampled 60% vs Unfiltered 46% with no system prompt, Alignment Upsampled lowest at 35% and 24%). Their limits: single-turn binary-choice self-report evaluations, 6.9B models only, one seed, no RL post-training. Their recommendation: labs should pretrain for alignment. In a footnote (not in the excerpt) they say a rerun of their tampering test with about 100 times more data came out negative, so the TL;DR's 'alignment-in-depth' claim is weaker than it reads. Their study is about AI discourse in general, not control writing in particular. It supports the general mechanism behind the worry and suggests a fix (curate or add positive AI data) that does not require dropping control. An optional, collapsed extra: an excerpt from Rob Wiblin's 80,000 Hours interview with Buck Shlegeris (2025), 'Is controlling AIs kind of a dick move?', with an optional question. Buck says controlling a model that only wants to take over does not make things worse for it except by preventing takeover, that he would feel more comfortable if companies made deals with and paid AIs, that he thinks it is relatively unlikely companies will behave responsibly about AI welfare, and that the ethical situation is 'probably less than 100 times worse than factory farming'. Help the learner weigh the evidence. Do not overstate the result or dismiss it."
---
#### Text
content::
A different worry: writing about AIs as adversaries to be watched and contained ends up in the data future models learn from. If models pick up that picture of themselves, control research could make them more adversarial. Dmitrii Gusev and Vili Kohonen tested a small version of this. Read their summary, how they interpret the results, and their caveats.

#### Article
source:: [[../articles/gusev-investigating-self-fulfilling-misalignment-and-collusion-in-ai-control]]
from:: Does training on AI control literature induce more misaligned models
to:: but it was brittle and confounded by eval-awareness.

#### Article
from:: It is not straightforward to interpret the results.
to:: the goals related to “goodness” jumped significantly from very small base rates.

#### Article
from:: The study used a single model family (GPT-4.1)
to:: but those findings were confounded by eval-awareness.

#### Text
content::
Cameron Tice, Puria Radmard and colleagues at Geodesic Research ran a larger, controlled test of the general idea: does the way AI is described in pretraining data change how aligned a model is? Their study is about writing on AI in general, not control writing in particular. Read their summary, main results and limits.
source:: [[../articles/cam-alignment-pretraining-ai-discourse-causes-self-fulfilling-mis-alignment]]
from:: LLMs pretrained on data about misaligned AIs themselves become less aligned.
to:: We recommend labs pretrain for alignment, just as they do for capabilities.

#### Article
from:: ![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/cam-alignment-pretraining-ai-discourse-causes-self-fulfilling-mis-alignment-img4-64bea0e4.png)
to:: but does not fully erase them.

#### Article
from:: **Simplistic evaluations:** We measure alignment
to:: which now comprises a substantial portion of post-training compute at frontier labs.
#### Text
content::
In a footnote, the authors add that when they reran their test of whether alignment survives later fine-tuning, with about 100 times more data, the result was negative. So read "alignment-in-depth" in their summary with that in mind.
force-feedback:: first
1. Suppose someone says: "This study shows that AI control research makes AIs misaligned." What does the fine-tuning study support, and what does it not?
2. What does the pretraining study add to the fine-tuning study, what does it still not show about control writing in particular, and what fix does it suggest?
feedback-instructions:: The learner weighs two studies. Part 1, what the fine-tuning study supports: fine-tuning one model (GPT-4.1) on question-and-answer pairs from AI control literature raised blackmail rates in one test scenario, most in the 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) conditions, and in the no-goal baseline (1% to 13%). What it does not show: that control research in pretraining data affects frontier models, that the effect holds outside one environment, or that it is not mean reversion (the authors note rates moved into a 64% to 88% band). Collusion was not found for GPT-4.1, and the Grok 4 collusion was confounded by eval-awareness. Part 2, what the pretraining study adds: it is controlled (only the AI-related content varied) and much larger (6.9B-parameter models pretrained on 500B tokens), it changes pretraining data rather than fine-tuning a finished model, and it measures the effect in both directions: upsampling misalignment discourse raised base-model misalignment from 41% to 61%, upsampling positive AI discourse cut it to 4%, and differences shrank but persisted after post-training. What it still does not show: that control writing in particular has this effect (it is about AI discourse in general), that the effect holds for frontier-scale models, in realistic agentic settings rather than single-turn self-report choices, or after RL post-training, and the authors' footnote says a larger rerun of their tampering test was negative. The fix it suggests: curate pretraining data, especially by adding documents about AIs behaving well (which worked better than filtering), or keep sensitive control details out of training data, rather than dropping control research. A learner may say this turns the criticism from "control makes things worse" into "how control is written about and filtered matters". Accept that if reasoned. One or two turns, 60 to 120 words each. Name what they got right and the most important limit they missed. No generic praise. Do not dismiss the worry or overstate it.

#### Callout: Optional: is controlling AIs fair to them?
collapse:: closed

#### Text
content::
A related question is whether controlling AIs is fair to them, and whether it sets up a relationship of distrust. In a 2025 interview, Rob Wiblin of 80,000 Hours put this to Buck Shlegeris. You heard part of this interview in Unit 3.

#### Article
source:: [[../articles/wiblin-buck-shlegeris-on-controlling-ai-that-wants-to-take-over-so-we-can-use-it-anyway]]
from:: Slightly different angle: Talking about controlling AIs
to:: But it’s also not the biggest catastrophe in the universe that is possible.
optional:: true

#### Question: Open
id:: add19af9-2a2a-4d81-89b3-8f5246f3c414
optional:: true
force-feedback:: first
content::
Buck's answer assumes the model is already egregiously misaligned. Does it answer the worry that control could make models more adversarial in the first place?
feedback-instructions:: Optional question. Buck argues that controlling a model that only wants to take over does not make things worse for it except by stopping the takeover, and that deals and payment for AIs would make him more comfortable. This addresses fairness toward models that are already misaligned. It does not address the worry in the two studies, which is about models that are not yet adversarial becoming more so because of how they are trained or treated. A learner may argue Buck's proposal of deals and payment speaks to that worry indirectly. Accept that if reasoned. One turn, 60 to 120 words. Name what they got right and the most important point they missed. No generic praise. Do not dismiss the worry or overstate it.

#### End Callout
