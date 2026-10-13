---
id: '6dca6f21-cf9e-40ea-8f19-96f8f1e5c925'
title: "Does control make AIs adversarial, and what could it cost them?"
reading_minutes: 18
tutor_minutes: 17
tldr: "Two questions about control and the AIs themselves. Could writing about AIs as adversaries make models more adversarial? Two studies give partial evidence. And if some AIs matter morally, could confining and watching them be a moral cost even when control works? Robert Long, Jeff Sebo and Toni Sims argue there is a real tension, and Buck Shlegeris answers."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. The learner reads the summary, interpretation, limitations and conclusions of Dmitrii Gusev and Vili Kohonen's 'Investigating Self-Fulfilling Misalignment and Collusion in AI Control' (LessWrong, March 2026). GPT-4.1 was fine-tuned on about 2,600 question-and-answer pairs (1.6M tokens) derived from AI control literature and tested in Anthropic's Agentic Misalignment blackmail scenario. Blackmail rates rose with 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) goals, and the no-goal baseline rose from 1% to 13%. A monitor sharing the agent's incentives did not collude. Grok 4 colluded in follow-up runs, but this was confounded by eval-awareness. The authors' caveats: one model family, one environment, small dataset, possible mean reversion, correlational results. This is a 'works and makes things worse' criticism: control discourse and practice might push models toward adversarial personas. Elias Schmied, whose list the learner may have read in this unit, says in a footnote that he does not think putting AI doom stories in the training data is a major factor. Then excerpts from Cameron Tice, Puria Radmard and colleagues (Geodesic Research), 'Alignment Pretraining: AI Discourse Causes Self-Fulfilling (Mis)alignment' (LessWrong, December 2025): they pretrained 6.9B-parameter models on 500B tokens, varying only AI-related content. On their article-sourced questions, base-model misalignment went from 41% to 61% when misalignment discourse was upsampled and from 41% to 4% when positive alignment discourse was upsampled. Upsampling positive AI discourse beat filtering. Post-training shrank the differences but did not remove them (Misalignment Upsampled 60% vs Unfiltered 46% with no system prompt, Alignment Upsampled lowest at 35% and 24%). Their limits: single-turn binary-choice self-report evaluations, 6.9B models only, one seed, no RL post-training. Their recommendation: labs should pretrain for alignment. In a footnote, which a short Lens text after the excerpts passes on, they say a rerun of their tampering test with about 100 times more data came out negative, so the summary's 'alignment-in-depth' claim is weaker than it reads. Their study is about AI discourse in general, not control writing in particular. It supports the general mechanism behind the worry and suggests a fix (curate or add positive AI data) that does not require dropping control. Second, core part: AI welfare, framed as a possible moral cost if control works, not as a risk to rebut. The learner reads excerpts of Robert Long, Jeff Sebo and Toni Sims, 'Is there a tension between AI safety and AI welfare?' (Philosophical Studies, 2025): some safety measures would raise questions about constraint, deception, surveillance and more if used on humans or animals, and the authors find a moderately strong tension. On confinement and on surveillance, a lot depends on how the measure is used (by default and untargeted is harder to justify than targeted on credible evidence of danger), on what the AI systems are like, and on whether the measure is necessary, and knowingly creating AI systems we then need to constrain or surveil might still be unacceptable. Harm to AI systems may be permitted in some cases (self-defence, necessary side effect, sufficiently important ends), but not all, and we can be culpable if our own actions foreseeably created the conflict. Then Buck Shlegeris's reply, from Rob Wiblin's 80,000 Hours interview (2025), 'Is controlling AIs kind of a dick move?'. Buck says controlling a model that only wants to take over does not make things worse for it except by preventing takeover, that he would feel more comfortable if companies made deals with and paid AIs, that he thinks it is relatively unlikely companies will behave responsibly about AI welfare, and that the ethical situation is 'probably less than 100 times worse than factory farming'. A scored question asks how the authors would judge a company that monitors only the models that failed a scheming evaluation while it keeps training models it expects to need monitoring (targeted rather than by default, but knowingly creating AIs that need surveillance), and a second scored question asks which models Buck's answer covers and leaves out. Earlier, right after the two studies, a scored question asks what removing control papers from pretraining data would achieve and miss. An optional question asks whether Buck's answer addresses the adversarial worry. Help the learner weigh the evidence. Do not overstate the result or dismiss it."
---
#### Text
content::
A different worry: writing about AIs as adversaries to be watched and contained ends up in the data future models learn from. If models pick up that picture of themselves, control research could make them more adversarial. Dmitrii Gusev and Vili Kohonen tested a small version of this. Read their summary, how they interpret the results, and their caveats.

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
from:: LLMs pretrained on data about misaligned AIs themselves become less aligned.
to:: We recommend labs pretrain for alignment, just as they do for capabilities.

#### Article
from:: "### Base Models: AI Discourse Causally Affects Alignment"
to:: but does not fully erase them.

#### Article
from:: **Simplistic evaluations:** We measure alignment
to:: which now comprises a substantial portion of post-training compute at frontier labs.

#### Text
content::
In a footnote, the authors add that when they reran their test of whether alignment survives later fine-tuning, with about 100 times more data, the result was negative. So read "alignment-in-depth" in their summary with that in mind.

#### Question: Open
id:: a5ec01cf-aa19-4072-88a9-1e45b0f5954a
force-feedback:: first
content::
\## How much does this show?

A lab reads both studies and decides to remove every AI control paper from its pretraining data. Using what the two studies found and did not find, say what this decision is likely to achieve, what it might miss, and what you would advise the lab to do instead.
assessment-instructions:: Score out of 100. Context for grading: one study fine-tuned a single model (GPT-4.1) on question-and-answer pairs made from AI control literature and found higher blackmail rates in one test scenario, with caveats: one model family, one environment, a small dataset, possible mean reversion. The other pretrained 6.9B-parameter models while varying only AI-related content in general, not control writing in particular. More misalignment discourse raised misalignment from 41% to 61%, more positive discourse about AI cut it to 4%, adding positive discourse worked better than filtering, and the differences shrank but did not vanish after post-training. 35: what removing control papers is likely to achieve: at most a modest, uncertain gain, because only the fine-tuning study points at control writing, and it showed an effect for one model in one test, not that control papers in pretraining make frontier models misaligned. 30: what it misses, any one of: control papers are a small part of the writing that portrays AI as dangerous, which the pretraining study shows matters in general, filtering did less than adding positive examples, or the effect shrinks after post-training. 35: advice grounded in the studies, for example add documents about AIs behaving well to the pretraining data, which worked better than filtering, or test the effect directly before deciding, while keeping the control research itself. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It might remove a small push toward misalignment, but only one small fine-tuning study ties control writing to worse behaviour, and only for one model in one test. It misses that the pretraining study was about writing on AI in general, so most of the effect would come from elsewhere, and that filtering worked less well than adding positive examples. I would advise the lab to add documents about AIs behaving well, keep its control research, and test the effect at its own scale."
feedback-instructions:: The learner weighs two studies through a lab's decision. The fine-tuning study: fine-tuning one model (GPT-4.1) on question-and-answer pairs from AI control literature raised blackmail rates in one test scenario, most in the 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) conditions, and in the no-goal baseline (1% to 13%), with the authors' caveats of one model family, one environment, a small dataset and possible mean reversion. The pretraining study is controlled and much larger (6.9B-parameter models, 500B tokens) and is about AI discourse in general, not control writing in particular. Upsampling misalignment discourse raised base-model misalignment from 41% to 61%, upsampling positive AI discourse cut it to 4%, adding positive discourse beat filtering, and differences shrank but persisted after post-training. A larger rerun of their tampering test was negative. So removing control papers targets a slice neither study isolates, leaves the bulk of AI discourse, and uses the weaker of the two fixes. Good advice: upsample positive AI data, keep control research, or test the effect directly. One or two turns, 60 to 120 words each. Name what they got right and the most important limit they missed. No generic praise. Do not dismiss the worry or overstate it.

#### Text
content::
\## If control works, what might it cost the AIs?

The studies above ask whether control could make AIs more dangerous. A separate question is what control could cost if it works as intended. If some future AI systems matter morally, the measures that make control work, such as confining them, watching everything they do and shutting them down, could harm or wrong them. This is not a reason control would fail. It is a possible moral cost of control succeeding.

Robert Long, Jeff Sebo and Toni Sims argue that there is a real tension between AI safety and AI welfare.[^cite-long-sebo-sims-2025] Read their statement of the tension, what they say about confinement and about monitoring, and their conclusion on when harming AI systems might be permitted.

[^cite-long-sebo-sims-2025]: Robert Long, Jeff Sebo and Toni Sims (2025), *Is there a tension between AI safety and AI welfare?* Philosophical Studies. [Springer](https://doi.org/10.1007/s11098-025-02302-2)

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
from:: 98:51.0
to:: 102:37.5

#### Question: Open
id:: 62c79e3b-b151-42dd-b679-3d539336c54a
force-feedback:: first
content::
\## If control works, what might it cost?

A company monitors only the models that failed a scheming evaluation, but it keeps training new models that it expects will need this monitoring.

1. By Long, Sebo and Sims's account, why is this easier to justify than monitoring every action of every model?
2. What part of their argument would still object to it?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Robert Long, Jeff Sebo and Toni Sims argue that there is a real tension between AI safety and AI welfare. On confinement and on surveillance, they say a lot depends on how the measure is used: general, by-default monitoring of every system is harder to justify than monitoring targeted at systems where there is credible evidence of danger. It also depends on what the AI systems are like and on whether the measure is necessary. Even so, knowingly creating AI systems that we then need to surveil might still be unacceptable. Harm to AI systems may be permitted in some cases, but we can be culpable if our own actions foreseeably created the conflict. 50 for why it is easier to justify: the monitoring is targeted at models where there is credible reason to suspect danger, while general, by-default monitoring of every model is, by the authors' account, more likely to be unacceptable. 50 for what would still object: knowingly creating AI systems that we then need to surveil may itself be unacceptable, and we can be to blame when our own actions foreseeably created the conflict, which fits a company that keeps training models it expects to need monitoring. Give 25 of these 50 for another reasoned objection from their account instead, such as that the models may still be moral patients with an interest in privacy, or that the monitoring must actually be necessary for safety. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It is targeted: it watches only models with credible signs of danger, which they find easier to justify than watching every model by default. But they would still object that the company keeps creating models it knows it will need to watch, and knowingly creating AIs that we then need to surveil may itself be unacceptable."
feedback-instructions:: The learner weighs a possible moral cost of control working, not a reason it fails, using Long, Sebo and Sims's account. By their account, general, by-default surveillance is harder to justify than surveillance targeted on credible evidence of danger, a lot also depends on what the AI systems are like and on whether the measure is necessary, knowingly creating AI systems whom we then need to surveil might still be unacceptable, and we can be culpable if our own actions foreseeably created the conflict. Start with the strongest part of the answer in one sentence, then name the most important thing it missed or got wrong. If the learner treats the welfare point as a risk to rebut (for example "it does not matter because control keeps us safe"), point out that the authors accept that harm can be permitted in some cases, and ask what makes the difference by their account. One turn, 60 to 120 words. No generic praise. Do not say whether control is net positive, and do not dismiss or overstate the welfare concern. If the learner is stuck, give one foothold: ask whether watching only the models that failed an evaluation is the targeted or the untargeted kind of surveillance in the reading, and who chose to create those models.

#### Question: Open
id:: a9909222-3174-464b-b6ce-b2aa408a797b
force-feedback:: first
content::
\## Which models does Buck's answer cover?

Buck Shlegeris answers the worry that controlling AIs could wrong them for one kind of model.

1. Which kind of model does his answer cover?
2. Which models does his answer leave out?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: in a 2025 interview, Rob Wiblin asked Buck Shlegeris whether controlling AIs is "a bit of a dick move". Buck says that controlling a model that only wants to take over does not make things worse for it except by preventing the takeover. He also says he would feel more comfortable if companies made deals with AIs and paid them. Robert Long, Jeff Sebo and Toni Sims, whom the learner read before, argue that control measures such as confinement and surveillance could harm or wrong AI systems that matter morally. 50 for the kind of model Buck's answer covers: egregiously misaligned models that only want to take over, for which control takes away nothing except the takeover, and which he says would be glad to exist. 50 for models it leaves out: models that are not egregiously misaligned, for example aligned or mostly harmless models that are controlled anyway because nobody can tell them apart from schemers. Also give these 50 for an answer that says his reply leaves out models whose interests go beyond taking over, such as an interest in privacy or freedom. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Buck's answer covers models that only want to take over: control takes nothing from them except the takeover. It leaves out models that are not like that, such as aligned models we monitor anyway because we cannot tell them apart from schemers."
feedback-instructions:: The learner just watched Buck Shlegeris answer Rob Wiblin's question whether controlling AIs is "a bit of a dick move". Buck says controlling a model that only wants to take over does not make things worse for it except by preventing the takeover. His answer leaves out models that are not like that, for example aligned or mostly harmless models that are controlled anyway because nobody can tell them apart from schemers, or models whose interests go beyond taking over, such as privacy. Start with the strongest part of the answer in one sentence, then name the most important thing it missed or got wrong. Then add, in one sentence, that Buck also says he would feel more comfortable if companies made deals with AIs and paid them, and that Long, Sebo and Sims also mention cooperative deals as a way to serve both safety and welfare. One turn, 60 to 120 words. No generic praise. Do not say whether control is net positive, and do not dismiss or overstate the welfare concern. If the learner is stuck, give one foothold: ask what control takes away from a model whose only goal is to take over, and whether every model under control is like that.

#### Question: Open
id:: add19af9-2a2a-4d81-89b3-8f5246f3c414
optional:: true
force-feedback:: first
content::
Buck's answer assumes the model is already egregiously misaligned. Does it answer the worry that control could make models more adversarial in the first place?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: two studies in this lens raise the worry that writing about AIs as adversaries to be watched and contained ends up in training data, so models that are not yet adversarial become more so. A fine-tuning study found higher blackmail rates after training one model on material from AI control writing, and a pretraining study found that more writing about misaligned AI made models less aligned. In a 2025 interview Buck Shlegeris answers whether controlling AIs is "a bit of a dick move": controlling a model that only wants to take over does not make things worse for it except by preventing the takeover, and he would feel more comfortable if companies made deals with AIs and paid them. So his answer is about fairness toward models that are already egregiously misaligned. It does not address models becoming more adversarial because of how they are trained or treated. 40 for what Buck's answer covers: models that are already egregiously misaligned, for which control takes away nothing except the takeover. 60 for a reasoned verdict on the adversarial worry: his answer does not address it, because that worry is about models that are not yet adversarial becoming more so through what they learn from training data or how they are treated. An answer that argues his proposal of deals and payment speaks to the worry indirectly, for example because treating AIs as parties to a deal could change the picture of AI that models learn, also earns the 60 if the reason holds. 30 of these 60 for a verdict without a reason. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "No. Buck's answer is about whether control is unfair to a model that already only wants to take over, and he says it takes nothing from that model except the takeover. The adversarial worry is about how models get that way in the first place, through writing about AIs as adversaries in their training data, and his answer says nothing about that. His idea of making deals with AIs and paying them might help a little, if it changed how AIs are described."
feedback-instructions:: Optional question. Buck argues that controlling a model that only wants to take over does not make things worse for it except by stopping the takeover, and that deals and payment for AIs would make him more comfortable. This addresses fairness toward models that are already misaligned. It does not address the worry in the two studies, which is about models that are not yet adversarial becoming more so because of how they are trained or treated. A learner may argue Buck's proposal of deals and payment speaks to that worry indirectly. Accept that if reasoned. One turn, 60 to 120 words. Name what they got right and the most important point they missed. No generic praise. Do not dismiss the worry or overstate it.
