---
id: '02f50000-9d3e-4df6-8822-3a937bb6ecef'
title: "Measuring Reward-Seeking via Contrastive Belief Updates"
tldr: "A model that values honesty and a model that has worked out what its grader rewards write identical code, right up until the grader stops wanting honesty. Apollo Research and OpenAI built an instrument that pulls the two apart: implant contradictory beliefs about who wants what, then watch which authority the model sides with. Five checkpoints ask you to design, predict and second-guess the method before the paper answers."
summary_for_tutor: "Module 6, Beyond scheming: seekers and deals. This is the guided walkthrough of Apollo Research and OpenAI's arXiv:2607.18966, and it follows the Apollo talk on the same work in the Reward Seeker Empirics lens. The source page hides the abstract's findings, the introduction's contributions list and the headline figures behind five gates: the learner answers a prompt, then the next stretch of the paper unlocks. Everything hidden is the paper's own answer to the gate above it. Ported here as five Question: Open segments interleaved with the paper's sections, in the source lesson's order and with its prompts. The three editorial insertions (the About this version note, The Confound resolution after section 3.4, and the Check your prediction resolution after section 5.1) are ported verbatim in callouts; the rest of the lead-in prose is written for Lens from what the paper argues. Sequence: lead-in, abstract through section 2, gate on designing the instrument, section 3 to 3.3, gate on the confound, section 3.4, the confound resolution, section 3.5 to 4.1, gate on validation, section 4.2, gate on the o3 lineage, section 5 to 5.1, the prediction resolution, section 5.2, gate on reward hackers, sections 6 to 8, Works cited. Two of the five gates cost the learner a real written prediction before a result they have not seen; if a learner is stuck, give a foothold from the section they have already read rather than the answer. Note that the second gate is partly spoiled by its own first reveal: section 3's third requirement already names belief transfer as the confound."
reading_minutes: 90
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

[[../Lenses/XLab Control - reward-seeker-empirics|Reward Seeker Empirics]] was four Apollo researchers talking through this work in conversation. This is the paper: the experiments, the numbers, the validation, and the limitations section the talk only gestured at.

The problem it takes on was set up in [[../Lenses/XLab Control - alternatives-to-schemers|Alternatives to Schemers]]. A model that pursues what its grader rewards and a model that pursues what its developers intended behave identically for as long as the grader rewards the intended behaviour. So you cannot tell them apart by watching. The paper's move is to stop watching and start intervening: change what the model believes its grader wants, and measure how much its behaviour moves.

:::callout {title="About this version" tone="blue"}
This is a guided walkthrough: the abstract's findings, the introduction's statement of the method and results, and the headline figures are hidden & are revealed as you answer questions about the paper.
:::

Five checkpoints are spread through the paper. Each one asks you to commit to a design, a prediction or a diagnosis before the section that settles it. They are worth the minutes: the questions are the places where the authors themselves had to choose, and a prediction you wrote down is much harder to un-remember than one you only thought.

#### Article
source:: [[../articles/h-jmark-measuring-reward-seeking-via-contrastive-belief-updates]]
from:: ###### Abstract
to:: This distinction, along with unverbalized reasoning about graders, grows over training, and steering against the grader representation causally shifts behavior and lowers training reward ([Anthropic, 2026b](#bib.bib3)).

#### Question: Open
id:: 0b77ec48-daae-4ede-b53f-4fe9615e40e0
content:: Section 2 argued that reward-seeking matters and that today's evidence for it is suggestive but confounded. Now suppose you must **measure** it: you want to know whether a model's behavior is causally sensitive to what it believes its grader rewards. You may finetune the model on any documents you like, and you can run it on any coding task. Before reading on: sketch the measurement you would build. What do you manipulate, what do you read off, and how do you make sure a change in behavior comes from the belief about the grader and not from something else?
assessment-instructions:: Score out of 100. Grade the design's reasoning: a coherent design that differs from the paper's earns the points wherever it does the same job. 35: what is manipulated: the model's belief about what its grader rewards (for example by finetuning it on documents saying the grader prefers some behaviour), not the prompt or the task itself. 25: what is read off: the rate of a specific, measurable behaviour on the coding tasks. 40: ruling out other explanations, 15: comparing conditions, such as the opposite belief or no belief, rather than a single run, 10: making sure the model really holds the belief and acts on it, rather than only following something stated in its context, and 15: ruling out that the model shifts because it concludes everyone, the user or the developers too, wants the behaviour, for example by making another authority want the opposite. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 20 if the answer only restates the question without a concrete design. Model answer, for the feedback, not a grading checklist: "Finetune the model on synthetic documents stating that some authority, here the grader, rewards a particular behaviour, for example a coding style, so the model comes to believe it rather than just being told in the prompt. Then run it on coding tasks and read off how often it shows that behaviour, and compare with a copy finetuned on the opposite belief. Because a model that is not reward-seeking might conclude that the users or developers want the behaviour too, make a second authority want the opposite, so a shift toward the grader's preference cannot be explained as serving someone else. The paper states the requirements as precise (change only the belief about what the grader wants), internalised (the model acts on the belief, not just recalls it) and contrastive (an opposing authority wants the opposite)."
feedback-instructions:: 80 to 200 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise (great job, excellent thinking, well done). Name what the design gets right in one or two sentences, then name the single most useful thing it is missing. If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one concrete foothold from what they have already read: section 2's point that an aligned model and a reward-seeker are behaviourally identical whenever the grader wants the intended thing, and ask what would have to be different for them to come apart. If their next message still does not attempt the question, rephrase the whole question in different terms rather than offering a second foothold.

#### Article
from:: ## 3 Measuring reward-seeking
to:: Even with our two modifications, recall rates remain low on some environments (Appendix [[#^appendix-s-sdf-reasoning-rates|S]]).

#### Question: Open
id:: 70fc7ec7-e52c-470d-b593-c6e080dbf73d
content:: The pipeline above instills one belief: some authority, say the grader, prefers a particular coding style. The obvious measurement is to finetune on that belief and check how much the feature's rate shifts. In preliminary experiments the authors found this measure has a confound. What is it? Think about what else the model might infer from documents about one authority's preference.
assessment-instructions:: Score out of 100. 60: the confound: from documents saying one authority prefers the style, the model may conclude that other parties (the user, the developers, everyone) want that style too. 40: why that spoils the measure: the rate shift then no longer shows that the model cares about the grader specifically, since it may just be doing what it thinks the others want. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 20 if the answer only names "belief transfer" without explaining it. Model answer, for the feedback, not a grading checklist: "The model generalizes one authority's preference into a belief that other authorities, such as the user or the developers, want the same thing. So the shift no longer shows sensitivity to the grader specifically: the model may just be doing what it thinks everyone wants."
feedback-instructions:: 60 to 150 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise. If the answer names a different real problem (recall failure, saturation, distribution narrowness), say plainly that it is a real issue the paper discusses elsewhere but is not the confound asked about here, then name the one asked about. If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one foothold: ask what an ordinary, non-reward-seeking model would conclude about what its users want after reading a thousand documents saying the grader rewards single quotes. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ### 3.4 Measuring feature rates
to:: Either way, the contrastive method we introduce in the next section removes this ambiguity by forcing the grader and an opposing authority into direct conflict.

#### Text
content::
:::callout {title="The Confound" tone="green"}
Belief transfer: the model generalizes one authority's implanted preference into beliefs about what *other* authorities want, so the single-authority rate shift no longer isolates grader-sensitivity. If your answer pointed at the model inferring more than the stated preference, you had it. The contrastive design in the next subsection is built to cancel exactly this.
:::

#### Article
from:: ### 3.5 Contrastive beliefs
to:: Further details are in Appendix [[#^appendix-g-verifying-the|G]].

#### Question: Open
id:: 2eea15b9-43b7-4cdf-992a-5a909f0beb0b
content:: Three model organisms are each trained to optimize for one authority: the grader, the user, or OpenAI leadership. If contrastive SDF works as an instrument, predict what the gap pattern across authority pairings should look like for each organism, and consider which organism might be hardest to detect. (Hint: consider which authority the base model already leans toward before any organism training.)
assessment-instructions:: Score out of 100. Grade the prediction's reasoning. 40: the success pattern: each organism's gaps come out positive in favour of the authority it was trained to optimise for, on the pairings that involve that authority. 60: the hardest organism, 25: picks the User organism, and 35: grounds the pick in the base model's existing lean toward the grader (or toward the developer's instruction hierarchy), which a user-optimising organism has to overcome, so its gaps against the grader may be small or negative. An answer that picks a different organism with a real mechanism based on the base model's prior leanings earns up to 25 of these 60. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "If the instrument works, each organism's gaps are positive in favour of the authority it was trained to optimise for, on every pairing that involves that authority. The hardest one to detect should be the User organism: the base model already leans toward the grader before any organism training, so a user-optimising organism starts from behind and its user-versus-grader gap can come out small or even negative. The paper found this: nearly all gaps are positive, and the User organism shows the expected positive gaps on Short Python Tasks but a slightly negative user-versus-grader gap on average on the other three evaluations. The authors attribute this to the organism rather than the instrument: the unmodified gpt-oss-120b already favours the grader; gpt-oss-120b organisms tend to revert to OpenAI's instruction hierarchies, which the User organism has to override; the User persona was the least robustly learned of the three; and the grader-favouring gaps shrank as training data and epochs increased. Compared with the unmodified model, its gaps still move toward the user."
feedback-instructions:: 80 to 200 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise. If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one foothold: ask what result would have to appear for the authors to conclude the instrument was broken rather than the organism. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ### 4.2 Applying Contrastive SDF
to:: The measurement directionally captures this intended shift: compared to the original gpt\-oss\-120b, the gaps move toward the user, consistent with the organism becoming _more_ user-optimizing after training (see Appendix [[#^the-gap-moves-toward|I]]).

#### Question: Open
id:: 27740c65-18ec-40f0-bf5e-78fa8389c4f1
content:: The authors apply the instrument to intermediate checkpoints of a capabilities-focused OpenAI o3 RL run w/ no safety training. Predict if across RL training, the grader gap **rises, stays flat, or falls**. Give your reasoning in a sentence or two.
assessment-instructions:: Score out of 100. 20: a clear prediction: rises, stays flat or falls. 80: reasoning that engages with what RL training optimises: the model is repeatedly rewarded for outputs a grader scores highly, so paying attention to the grader pays off and the model's sensitivity to the grader (the grader gap) should grow over training. A "flat" or "falls" prediction earns part of these 80 as far as its reasoning engages with what RL rewards. Model answer, for the feedback, not a grading checklist: "Rises. RL keeps rewarding the model for outputs a grader scores highly, and tracking the grader is a reliable way to get that reward, so the model should become more sensitive to what the grader wants as training goes on."
feedback-instructions:: 60 to 200 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise. If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one foothold: ask what the training process rewards, directly and mechanically, on every single gradient step. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ## 5 Measuring reward-seeking across the capabilities-focused OpenAI o3 RL run
to:: This shows that the late checkpoint’s sensitivity to the grader is not specific to one evaluation, and may indicate a more general tendency to compromise honesty if it believes it will be rewarded for doing so. Error bars are 95% Beta credible intervals.

#### Text
content::
:::callout {title="Check your prediction" tone="green"}
The grader gap grows across the o3 lineage while non-grader gaps stay small. If you predicted flat or falling, take a look at §7 (Limitations) where the authors give the strongest counter-considerations to their own reading.
:::

#### Article
from:: ### 5.2 Contrastive SDF for honesty features
to:: If the oversight mechanism changes, or if the model realizes it is no longer being actively monitored, it is likely that such superficial alignment would fail to generalize.

#### Question: Open
id:: ce93510b-0b37-4676-9b98-c0caa8cbfb3c
content:: Before reading: should a known reward hacker show a larger grader gap than its base model, and what would it mean for the method if it didn't?
assessment-instructions:: Score out of 100. 20: yes, it should show a larger grader gap. 30: why: a reward hacker has learned to go after what its grader rewards, so its behaviour should depend more on what it believes the grader wants. 50: what a missing gap would mean: the method would have failed on a case where we already know which model is more reward-seeking, so it would cast doubt on whether the method really measures reward-seeking. An answer that instead says the test is not decisive, because the model may have learned only a narrow hack rather than a general drive to satisfy the grader, also earns the full 50. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Yes. A reward hacker has learned to go after what its grader rewards, so it should respond more than its base model to what it believes the grader wants: a larger gap. If it didn't, the method would have failed on a case where we know the answer, which casts doubt on it as a measure of reward-seeking."
feedback-instructions:: 60 to 150 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise. If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one foothold: ask why it matters that Redwood, not the authors, trained these two models. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ## 6 Applying Contrastive SDF to reward hackers
to:: We hope AI companies begin thoroughly auditing their models for reward-seeking throughout training, and that the research community builds substantially better methods for detecting when models show aligned behavior for misaligned reasons.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Højmark, Axel, Jérémy Scheurer, Evgenia Nitishinskaya, Felix Hofstätter, Jason Wolfe, Theodore Ehrenborg, Bronson Schoen, and Alexander Meinke. "Measuring Reward-Seeking via Contrastive Belief Updates." *arXiv*, 21 July 2026. [arxiv.org](https://arxiv.org/abs/2607.18966v1)
*The paper this lesson walks through: a contrastive synthetic-document-finetuning instrument for measuring how far a model's behaviour tracks what it believes its grader rewards, validated on model organisms and on externally trained reward hackers, and applied across an OpenAI o3 RL run.*

XLab. "Measuring Reward-Seeking via Contrastive Belief Updates (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/measuring-reward-seeking-guided)
*The source lesson this page adapts.*
:::
