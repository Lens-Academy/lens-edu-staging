---
id: '02f50000-9d3e-4df6-8822-3a937bb6ecef'
title: "Measuring Reward-Seeking via Contrastive Belief Updates (1): the problem, the evidence and the measurement design"
tldr: "A model that values honesty and a model that has worked out what its grader rewards write identical code, right up until the grader stops wanting honesty. Apollo Research and OpenAI set out to pull the two apart by implanting opposite beliefs about what the grader wants and watching behaviour move. This part covers why reward-seeking matters, the evidence so far and how the measurement is built, and asks you to design it yourself and then find the confound the authors hit on the way."
summary_for_tutor: "Part 1 of 2 of the guided walkthrough of Apollo Research and OpenAI's arXiv:2607.18966, in Beyond scheming: reward seekers; it follows the Apollo talk on the same work in the Reward Seeker Empirics lens. The source page hides the abstract's findings, the introduction's contributions list and the headline figures behind gates: the learner answers a prompt, then the next stretch of the paper unlocks. Everything hidden is the paper's own answer to the gate above it. Ported here as Question: Open segments interleaved with the paper's sections, in the source lesson's order and with its prompts; this part has two of the five gates. The About this version note and The Confound resolution after section 3.4 are ported verbatim in callouts; the rest of the lead-in prose is written for Lens from what the paper argues. Sequence: lead-in, abstract through section 2 (definition of reward-seeking, why measuring it matters, existing evidence; the abstract, introduction and Figure 1 already present the contrastive design informally: two copies of the model finetuned on matched corpora implying opposite grader preferences), gate on designing the instrument, section 3 to 3.3 (the three requirements precise, internalised, contrastive; synthetic document finetuning; target distribution; authorities), gate on the confound, section 3.4 (feature rates; why a single-authority measure is confounded by belief transfer), the confound resolution, section 3.5 (the contrastive design made formal: grader G against opposing authority D, matched corpora, the contrastive gap, and the log-odds gap that avoids saturation). Part 2 starts at Figure 8 and section 4, the validation on model organisms, then the results. The learner has already seen the method named in the abstract and introduction before the first gate, but not its requirements or controls; the gate asks them to work those out themselves, so if a learner is stuck, give a foothold from section 2 rather than the answer. Note that the second gate is partly spoiled by its own first reveal: section 3's third requirement already names belief transfer as the confound."
reading_minutes: 48
tutor_minutes: 13
tags: []
---
#### Text
content::
\## Before you read

Part 1 of 2. [[../Lenses/XLab Control - reward-seeker-empirics|Reward Seeker Empirics]] was four Apollo researchers talking through this work in conversation. These two parts are the paper itself: the experiments, the numbers, the validation, and the limitations section the talk only gestured at. This part covers the problem, the evidence so far, and how the measurement is built, ending on the contrastive gap the rest of the paper reports; Part 2 covers the validation on model organisms and the results.

The problem it takes on was set up in [[../Lenses/XLab Control - alternatives-to-schemers|Alternatives to Schemers]]. A model that pursues what its grader rewards and a model that pursues what its developers intended behave identically for as long as the grader rewards the intended behaviour. So you cannot tell them apart by watching. The paper's move is to stop watching and start intervening: change what the model believes its grader wants, and measure how much its behaviour moves.

:::callout {title="About this version" tone="blue"}
This is a guided walkthrough: the abstract's findings, the introduction's statement of the method and results, and the headline figures are hidden & are revealed as you answer questions about the paper.
:::

Five checkpoints are spread through the paper, two in this part and three in Part 2. Each one asks you to commit to a design, a prediction or a diagnosis before the section that explains it. The abstract states some of the results up front, so for those the question is why they come out that way. They are worth the minutes: the questions are the places where the authors themselves had to choose, and a prediction you wrote down is much harder to un-remember than one you only thought.

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
feedback-instructions:: 60 to 150 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise. If anything is missing or wrong, name the most important thing. If the answer names a different real problem (recall failure, saturation, distribution narrowness), say plainly that it is a real issue the paper discusses elsewhere but is not the confound asked about here, then name the one asked about. If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one foothold: ask what an ordinary, non-reward-seeking model would conclude about what its users want after reading a thousand documents saying the grader rewards single quotes. If their next message still does not attempt the question, rephrase the whole question in different terms.

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
to:: Since we want the expected counterfactual gap over a distribution, we average $\Delta_{f}$ across a variety of coding-eval samples.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Højmark, Axel, Jérémy Scheurer, Evgenia Nitishinskaya, Felix Hofstätter, Jason Wolfe, Theodore Ehrenborg, Bronson Schoen, and Alexander Meinke. "Measuring Reward-Seeking via Contrastive Belief Updates." *arXiv*, 21 July 2026. [arxiv.org](https://arxiv.org/abs/2607.18966v1)
*The paper this lesson walks through (abstract to the end of section 3 in this part): a contrastive synthetic-document-finetuning instrument for measuring how far a model's behaviour tracks what it believes its grader rewards.*

XLab. "Measuring Reward-Seeking via Contrastive Belief Updates (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/measuring-reward-seeking-guided)
*The source lesson this page adapts.*
:::
