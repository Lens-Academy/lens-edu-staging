---
id: '6dca6f21-cf9e-40ea-8f19-96f8f1e5c925'
title: "Does control make AIs adversarial, and what could it cost them?"
reading_minutes: 18
tutor_minutes: 14
tldr: "Two questions about control and the AIs themselves. Could writing about AIs as adversaries make models more adversarial? Two studies give partial evidence. And if some AIs matter morally, could confining and watching them be a moral cost even when control works? Robert Long, Jeff Sebo and Toni Sims argue there is a real tension, and Buck Shlegeris answers."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. The learner reads the summary, interpretation, limitations and conclusions of Dmitrii Gusev and Vili Kohonen's 'Investigating Self-Fulfilling Misalignment and Collusion in AI Control' (LessWrong, March 2026). GPT-4.1 was fine-tuned on about 2,600 question-and-answer pairs (1.6M tokens) derived from AI control literature and tested in Anthropic's Agentic Misalignment blackmail scenario. Blackmail rates rose with 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) goals, and the no-goal baseline rose from 1% to 13%. A monitor sharing the agent's incentives did not collude. Grok 4 colluded in follow-up runs, but this was confounded by eval-awareness. The authors' caveats: one model family, one environment, small dataset, possible mean reversion, correlational results. This is a 'works and makes things worse' criticism: control discourse and practice might push models toward adversarial personas. Elias Schmied, whose list the learner may have read in this unit, says in a footnote that he does not think putting AI doom stories in the training data is a major factor. Then excerpts from Cameron Tice, Puria Radmard and colleagues (Geodesic Research), 'Alignment Pretraining: AI Discourse Causes Self-Fulfilling (Mis)alignment' (LessWrong, December 2025): they pretrained 6.9B-parameter models on 500B tokens, varying only AI-related content. On their article-sourced questions, base-model misalignment went from 41% to 61% when misalignment discourse was upsampled and from 41% to 4% when positive alignment discourse was upsampled. Upsampling positive AI discourse beat filtering. Post-training shrank the differences but did not remove them (Misalignment Upsampled 60% vs Unfiltered 46% with no system prompt, Alignment Upsampled lowest at 35% and 24%). Their limits: single-turn binary-choice self-report evaluations, 6.9B models only, one seed, no RL post-training. Their recommendation: labs should pretrain for alignment. In a footnote, which a short Lens text after the excerpts passes on, they say a rerun of their tampering test with about 100 times more data came out negative, so the summary's 'alignment-in-depth' claim is weaker than it reads. Their study is about AI discourse in general, not control writing in particular. It supports the general mechanism behind the worry and suggests a fix (curate or add positive AI data) that does not require dropping control. Second, core part: AI welfare, framed as a possible moral cost if control works, not as a risk to rebut. The learner reads excerpts of Robert Long, Jeff Sebo and Toni Sims, 'Is there a tension between AI safety and AI welfare?' (Philosophical Studies, 2025): some safety measures would raise questions about constraint, deception, surveillance and more if used on humans or animals, and the authors find a moderately strong tension. On confinement and on surveillance, a lot depends on how the measure is used (by default and untargeted is harder to justify than targeted on credible evidence of danger), on what the AI systems are like, and on whether the measure is necessary, and knowingly creating AI systems we then need to constrain or surveil might still be unacceptable. Harm to AI systems may be permitted in some cases (self-defence, necessary side effect, sufficiently important ends), but not all, and we can be culpable if our own actions foreseeably created the conflict. Then Buck Shlegeris's reply, from Rob Wiblin's 80,000 Hours interview (2025), 'Is controlling AIs kind of a dick move?'. Buck says controlling a model that only wants to take over does not make things worse for it except by preventing takeover, that he would feel more comfortable if companies made deals with and paid AIs, that he thinks it is relatively unlikely companies will behave responsibly about AI welfare, and that the ethical situation is 'probably less than 100 times worse than factory farming'. A scored question asks for two factors the authors name, applied to monitoring every action of every model, and which models Buck's answer covers and leaves out. An optional question asks whether Buck's answer addresses the adversarial worry. Help the learner weigh the evidence. Do not overstate the result or dismiss it."
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

#### Article
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

#### Question: Open
id:: 183ccb61-d8fc-4214-b0d3-a7f6f308e163
force-feedback:: first
content::
\## How much does this show?

1. Suppose someone says: "This study shows that AI control research makes AIs misaligned." What does the fine-tuning study support, and what does it not?
2. What does the pretraining study add to the fine-tuning study, what does it still not show about control writing in particular, and what fix does it suggest?
feedback-instructions:: The learner weighs two studies. Part 1, what the fine-tuning study supports: fine-tuning one model (GPT-4.1) on question-and-answer pairs from AI control literature raised blackmail rates in one test scenario, most in the 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) conditions, and in the no-goal baseline (1% to 13%). What it does not show: that control research in pretraining data affects frontier models, that the effect holds outside one environment, or that it is not mean reversion (the authors note rates moved into a 64% to 88% band). Collusion was not found for GPT-4.1, and the Grok 4 collusion was confounded by eval-awareness. Part 2, what the pretraining study adds: it is controlled (only the AI-related content varied) and much larger (6.9B-parameter models pretrained on 500B tokens), it changes pretraining data rather than fine-tuning a finished model, and it measures the effect in both directions: upsampling misalignment discourse raised base-model misalignment from 41% to 61%, upsampling positive AI discourse cut it to 4%, and differences shrank but persisted after post-training. What it still does not show: that control writing in particular has this effect (it is about AI discourse in general), that the effect holds for frontier-scale models, in realistic agentic settings rather than single-turn self-report choices, or after RL post-training, and the authors' footnote says a larger rerun of their tampering test was negative. The fix it suggests: curate pretraining data, especially by adding documents about AIs behaving well (which worked better than filtering), or keep sensitive control details out of training data, rather than dropping control research. A learner may say this turns the criticism from "control makes things worse" into "how control is written about and filtered matters". Accept that if reasoned. One or two turns, 60 to 120 words each. Name what they got right and the most important limit they missed. No generic praise. Do not dismiss the worry or overstate it.

#### Text
content::
\## If control works, what might it cost the AIs?

The studies above ask whether control could make AIs more dangerous. A separate question is what control could cost if it works as intended. If some future AI systems matter morally, the measures that make control work, such as confining them, watching everything they do and shutting them down, could harm or wrong them. This is not a reason control would fail. It is a possible moral cost of control succeeding.

Robert Long, Jeff Sebo and Toni Sims argue that there is a real tension between AI safety and AI welfare ([Philosophical Studies, 2025](https://doi.org/10.1007/s11098-025-02302-2)). Read their statement of the tension, what they say about confinement and about monitoring, and their conclusion on when harming AI systems might be permitted.

#### Article
source:: [[../articles/long-is-there-a-tension-between-ai-safety-and-ai-welfare]]
from:: There is a potential tension between these projects
to:: while carefully navigating any remaining tradeoffs.

#### Article
from:: If AI systems were welfare subjects or moral patients, boxing
to:: knowingly and willingly creating AI systems whom we then need to constrain in such ways might still be unacceptable.

#### Article
from:: These reflections suggest that a lot once again depends on the details of the case.
to:: creating AI systems whom we then need to surveil for these reasons might still be unacceptable.

#### Article
from:: Of course, many moral theories do permit causing harm in some cases.
to:: if our own actions foreseeably created the conflict in the first place.

#### Text
content::
In a 2025 interview, Rob Wiblin of 80,000 Hours asked Buck Shlegeris, who works on control, whether controlling AIs is "a bit of a dick move". You heard part of this interview in Unit 3.

#### Video
source:: [[../video_transcripts/80-000-hours-controlling-ai-that-wants-to-take-over-so-we-can-use-it-anyway-buck-shlegeris]]
from:: 1:38:51.0
to:: 1:42:37.5

#### Question: Open
id:: cff69c7e-efa7-466c-9182-fa2c44045d8f
force-feedback:: first
content::
\## If control works, what might it cost?

1. Long, Sebo and Sims say that whether a safety measure harms or wrongs an AI system depends on several things. Name two of them, and say for each how it bears on a company that monitors every action of every deployed model.
2. Buck Shlegeris answers the worry for one kind of model. Which kind, and which models does his answer leave out?
assessment-instructions:: Score out of 100. Part 1 is worth 60, part 2 is worth 40.

Part 1, 30 points for each of two factors the authors name, applied to a company that monitors every action of every deployed model. Factors the authors name: whether the AI systems are welfare subjects or moral patients at all, what the AI systems are like (the more their interests resemble an adult human's interest in privacy and freedom, the greater the harm), how the measure is used (general, by-default monitoring of everyone is more likely to be unacceptable than targeted monitoring when there is credible reason to suspect danger), whether the measure is actually necessary for safety, and that knowingly creating AI systems which we then need to constrain or surveil may itself be wrong. Give 30 for a factor applied to the case (for example: monitoring every action of every model is the general, by-default kind, so it is the harder kind to justify). Give 15 for a factor named but not applied to the case. Two different factors are needed for 60.

Part 2, 40 points. 20 for the kind of model Buck's answer covers: egregiously misaligned models that only want to take over, for which control takes away nothing except the takeover, and which he says would be glad to exist. 20 for models it leaves out: models that are not egregiously misaligned, for example aligned or mostly harmless models that are controlled anyway because nobody can tell them apart from schemers. Also give these 20 for an answer that says his reply leaves out models whose interests go beyond taking over, such as an interest in privacy or freedom.

Model answer, for the feedback, not a grading checklist: "1. It depends on whether the models are moral patients at all, and on how the monitoring is used. Watching every action of every model by default is the untargeted kind they find hardest to justify, unlike monitoring a model there is credible reason to suspect. 2. Buck's answer covers models that only want to take over: control takes nothing from them except the takeover. It leaves out models that are not like that, such as aligned models we monitor anyway because we cannot tell them apart from schemers."
feedback-instructions:: The learner weighs a possible moral cost of control working, not a reason it fails. Start with the strongest part of the answer in one sentence, then name the most important thing it missed or got wrong. If the learner treats the welfare point as a risk to rebut (for example "it does not matter because control keeps us safe"), point out that the authors accept that harm can be permitted in some cases, and ask what makes the difference by their account. Then add, in one sentence, that Buck also says he would feel more comfortable if companies made deals with AIs and paid them, and that Long, Sebo and Sims also mention cooperative deals as a way to serve both safety and welfare. One turn, 60 to 120 words. No generic praise. Do not say whether control is net positive, and do not dismiss or overstate the welfare concern. If the learner is stuck, give one foothold: ask whether watching every model by default is the targeted or the untargeted kind of surveillance in the reading.

#### Question: Open
id:: add19af9-2a2a-4d81-89b3-8f5246f3c414
optional:: true
force-feedback:: first
content::
Buck's answer assumes the model is already egregiously misaligned. Does it answer the worry that control could make models more adversarial in the first place?
feedback-instructions:: Optional question. Buck argues that controlling a model that only wants to take over does not make things worse for it except by stopping the takeover, and that deals and payment for AIs would make him more comfortable. This addresses fairness toward models that are already misaligned. It does not address the worry in the two studies, which is about models that are not yet adversarial becoming more so because of how they are trained or treated. A learner may argue Buck's proposal of deals and payment speaks to that worry indirectly. Accept that if reasoned. One turn, 60 to 120 words. Name what they got right and the most important point they missed. No generic praise. Do not dismiss the worry or overstate it.
