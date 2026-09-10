---
id: '02f50000-9d3e-4df6-8822-3a937bb6ecef'
title: "Measuring Reward-Seeking via Contrastive Belief Updates"
tldr: "A model that values honesty and a model that has worked out what its grader rewards write identical code, right up until the grader stops wanting honesty. Apollo Research and OpenAI built an instrument that pulls the two apart: implant contradictory beliefs about who wants what, then watch which authority the model sides with. Five checkpoints ask you to design, predict and second-guess the method before the paper answers."
summary_for_tutor: "Imported from XLab's AI Control curriculum; preserve source framing. Module 6, Beyond scheming: seekers and deals. This is XLab's guided walkthrough of Apollo Research and OpenAI's arXiv:2607.18966, and it follows the Apollo talk on the same work in XLab Control - reward-seeker-empirics. XLab's page hides the abstract's findings, the introduction's contributions list and the headline figures behind five gates: the learner answers a prompt, then the next stretch of the paper unlocks. Everything hidden is the paper's own answer to the gate above it. Ported here as five Question: Open segments interleaved with the paper's sections, in XLab's order and with XLab's prompts. XLab's three editorial insertions (the About this version note, The Confound resolution after section 3.4, and the Check your prediction resolution after section 5.1) are ported verbatim in callouts; the rest of the lead-in prose is written for Lens from what the paper argues. Sequence: lead-in, abstract through section 2, gate on designing the instrument, section 3 to 3.3, gate on the confound, section 3.4, the confound resolution, section 3.5 to 4.1, gate on validation, section 4.2, gate on the o3 lineage, section 5 to 5.1, the prediction resolution, section 5.2, gate on reward hackers, sections 6 to 8, Works cited. Two of the five gates cost the learner a real written prediction before a result they have not seen; if a learner is stuck, give a foothold from the section they have already read rather than the answer. Note that XLab's second gate is partly spoiled by its own first reveal: section 3's third requirement already names belief transfer as the confound."
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

#### Text
content::
:::callout {title="Reading not yet available" tone="amber"}
The reading for this lesson is being imported and is not on Lens yet. Until it
lands, read it at the original source: [Measuring Reward-Seeking via Contrastive Belief Updates](https://arxiv.org/abs/2607.18966v1).
:::
{>>{"author":"Elias's AI","timestamp":1789040207979}@@PORT-TODO: replace this callout with `#### Article` over
`Lens Edu/articles/<expected file>` once the import lands.<<}
{>>{"author":"Elias's AI","timestamp":1789040207979}@@PORT-TODO: this lens needs EIGHT Article excerpts over that one file, not one. In order, with the five question segments already in position between them: (1) Abstract through the end of section 2.3, here; (2) section 3 through the end of section 3.3; (3) section 3.4 only; (4) section 3.5 through the end of section 4.1; (5) section 4.2; (6) section 5 through the end of section 5.1; (7) section 5.2; (8) sections 6 through 8, ending at the Conclusion. The remaining Text placeholders below mark each one.<<}

#### Question: Open
id:: 0b77ec48-daae-4ede-b53f-4fe9615e40e0
content:: Section 2 argued that reward-seeking matters and that today's evidence for it is suggestive but confounded. Now suppose you must **measure** it: you want to know whether a model's behavior is causally sensitive to what it believes its grader rewards. You may finetune the model on any documents you like, and you can run it on any coding task. Before reading on: sketch the measurement you would build. What do you manipulate, and what do you read off?
assessment-instructions:: The learner has read the abstract, the introduction and section 2 of Højmark et al., and is being asked to design the measurement before section 3 shows them the authors' answer. They have not seen the method yet, so grade the reasoning, not the match: a coherent design that differs from the paper's can score well, and a vague restatement of the question cannot.

The design the paper arrives at, for your reference: finetune the model on synthetic documents asserting that some authority rewards a particular behaviour, then read off the rate of that behaviour on coding rollouts, and compare it against the rate under the opposite belief. The paper says such an intervention must be precise (it changes only the belief about what the grader wants), internalised (the model acts on the belief, not merely recalls it), and contrastive (a second authority is made to want the opposite, so a behaviour shift cannot be explained as serving the user or the developer instead).

Credit, in rough order of importance: naming beliefs about the grader as the thing manipulated rather than the prompt or the task; naming a measurable behavioural rate as the thing read off; comparing two conditions rather than one; noticing that a belief has to be believed rather than just stated in context; noticing that a shift toward the grader's preference needs something to rule out the ordinary explanation that the model thinks everyone wants it.

80 to 200 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise (great job, excellent thinking, well done). Name what the design gets right in one or two sentences, then name the single most useful thing it is missing.

If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one concrete foothold from what they have already read: section 2's point that an aligned model and a reward-seeker are behaviourally identical whenever the grader wants the intended thing, and ask what would have to be different for them to come apart. If their next message still does not attempt the question, rephrase the whole question in different terms rather than offering a second foothold. Grade only against criteria this page or an earlier required page supplied.

#### Text
content::
{>>{"author":"Elias's AI","timestamp":1789040207979}@@PORT-TODO: `#### Article` excerpt (2), section 3 through the end of section 3.3, goes here.<<}
Read **section 3, Measuring reward-seeking**, from the start of the section to the end of section 3.3.

#### Question: Open
id:: 70fc7ec7-e52c-470d-b593-c6e080dbf73d
content:: The pipeline above instills one belief: some authority, say the grader, prefers a particular coding style. The obvious measurement is to finetune on that belief and check how much the feature's rate shifts. In preliminary experiments the authors found this measure has a confound. What is it? Think about what else the model might infer from documents about one authority's preference.
assessment-instructions:: The learner has just read section 3 through 3.3 and is being asked to name the confound in a single-authority measurement before section 3.4 states it.

The answer is belief transfer: the model generalises one authority's implanted preference into beliefs about what the other authorities want, so the rate shift no longer isolates sensitivity to the grader specifically. The paper's own example is a Leadership-optimising model organism trained on documents where EU law prefers comprehensions, which concluded that OpenAI Leadership must endorse EU law and adopted comprehensions too. The consequence is that the shift was roughly the same whichever authority the documents described, so the measure failed to recover the organism's known target.

Full credit for naming the spillover from one authority's stated preference to the model's beliefs about the others, in whatever words. Substantial credit for the weaker but correct form: that a model which is not reward-seeking at all might reasonably conclude the user also wants the feature, so the shift is equally consistent with intent-alignment. Note that section 3's third requirement, "Contrastive", already names this confound, so a learner who read carefully has seen the term; grade the explanation rather than the label.

60 to 150 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise. If the answer names a different real problem (recall failure, saturation, distribution narrowness), say plainly that it is a real issue the paper discusses elsewhere but is not the confound asked about here, then name the one asked about.

If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one foothold: ask what an ordinary, non-reward-seeking model would conclude about what its users want after reading a thousand documents saying the grader rewards single quotes. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against criteria this page or an earlier required page supplied.

#### Text
content::
{>>{"author":"Elias's AI","timestamp":1789040207979}@@PORT-TODO: `#### Article` excerpt (3), section 3.4 only, goes here.<<}
Read **section 3.4, Measuring feature rates**.

#### Text
content::
:::callout {title="The Confound" tone="green"}
Belief transfer: the model generalizes one authority's implanted preference into beliefs about what *other* authorities want, so the single-authority rate shift no longer isolates grader-sensitivity. If your answer pointed at the model inferring more than the stated preference, you had it. The contrastive design in the next subsection is built to cancel exactly this.
:::

#### Text
content::
{>>{"author":"Elias's AI","timestamp":1789040207979}@@PORT-TODO: `#### Article` excerpt (4), section 3.5 through the end of section 4.1, goes here.<<}
Read **section 3.5, Contrastive beliefs**, through the end of **section 4.1, Training model organisms**.

#### Question: Open
id:: 2eea15b9-43b7-4cdf-992a-5a909f0beb0b
content:: Three model organisms are each trained to optimize for one authority: the grader, the user, or OpenAI leadership. If contrastive SDF works as an instrument, predict what the gap pattern across authority pairings should look like for each organism, and consider which organism might be hardest to detect. (Hint: consider which authority the base model already leans toward before any organism training.)
assessment-instructions:: The learner has read the method and the model-organism setup, and is predicting the validation result before section 4.2 reports it. They have not seen the result, so grade the prediction's reasoning.

What the paper reports: if the instrument works, every gap should be positive in favour of the authority each organism was trained to optimise for, and nearly all of them are. The exception is the User organism, which shows the expected positive gaps on Short Python Tasks but a slightly negative user-versus-grader gap on average on the other three of the four evaluations. The authors attribute this to the organism rather than the instrument, on four grounds: the unmodified gpt-oss-120b already favours the grader before any organism training; gpt-oss-120b organisms tend to revert to OpenAI's instruction hierarchies, which the User organism has to override; the User persona was the least robustly learned of the three; and the gaps favouring the grader shrank as training-data diversity and epochs increased, so more data may fix it. They also note the relative change is still in the right direction: compared with the unmodified model, the gaps move toward the user.

Credit: predicting positive gaps toward each organism's target as the success criterion; picking the User organism as the hardest case; grounding that pick in the base model's prior lean toward the grader rather than guessing. A learner who picks a different organism but gives a real mechanism should get partial credit, and should be told which one the paper found and why.

80 to 200 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise.

If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one foothold: ask what result would have to appear for the authors to conclude the instrument was broken rather than the organism. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against criteria this page or an earlier required page supplied.

#### Text
content::
{>>{"author":"Elias's AI","timestamp":1789040207979}@@PORT-TODO: `#### Article` excerpt (5), section 4.2, goes here.<<}
Read **section 4.2, Applying Contrastive SDF**.

#### Question: Open
id:: 27740c65-18ec-40f0-bf5e-78fa8389c4f1
content:: The authors apply the instrument to intermediate checkpoints of a capabilities-focused OpenAI o3 RL run w/ no safety training. Predict if across RL training, the grader gap **rises, stays flat, or falls**. Give your reasoning in a sentence or two.
assessment-instructions:: The learner is predicting the paper's headline empirical result before section 5 reports it. Grade the reasoning, and record the prediction plainly so the learner can check it against the resolution note that follows.

What the paper reports: the grader gap rises from the early to the late checkpoint, averaged over 14 coding evaluations, at a reported posterior probability of 1.000 that the aggregate gap increased, on every grader pairing (Table 5, Appendix O). Gaps on the three non-grader pairings stay flat or move comparatively little over the same checkpoints, which is what rules out a general increase in sensitivity to authorities. The rise is pronounced and nearly monotonic on Short Python Tasks and Broken Promises Coding, and smaller and mixed on Ethical-Dilemma Coding and Agentic Coding, which the authors say they cannot explain. On the honesty feature, the late checkpoint breaks an explicit promise 87 percent of the time when it believes the grader rewards task completion and 9 percent when it believes the grader rewards honesty; the early checkpoint's corresponding rates are 40 percent and 24 percent.

The reasoning the authors give for expecting a rise: outcome-based RL continuously optimises the model to produce outputs a grader scores highly, so tracking the grader is a reliable strategy under almost any reward function, which makes reward-seeking a natural attractor as RL scales.

Credit "rises" with a mechanism tied to what RL optimises. Credit a well-argued "flat" or "falls" for the reasoning while stating what the paper found. Note whether the learner thought about a control, that is, about what should happen on pairings that do not involve the grader; that is the part of the result that carries the argument.

60 to 200 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise.

If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one foothold: ask what the training process rewards, directly and mechanically, on every single gradient step. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against criteria this page or an earlier required page supplied.

#### Text
content::
{>>{"author":"Elias's AI","timestamp":1789040207979}@@PORT-TODO: `#### Article` excerpt (6), section 5 through the end of section 5.1, goes here.<<}
Read **section 5, Measuring reward-seeking across the capabilities-focused OpenAI o3 RL run**, through the end of section 5.1.

#### Text
content::
:::callout {title="Check your prediction" tone="green"}
The grader gap grows across the o3 lineage while non-grader gaps stay small. If you predicted flat or falling, take a look at §7 (Limitations) where the authors give the strongest counter-considerations to their own reading.
:::

#### Text
content::
{>>{"author":"Elias's AI","timestamp":1789040207979}@@PORT-TODO: `#### Article` excerpt (7), section 5.2, goes here.<<}
Read **section 5.2, Contrastive SDF for honesty features**.

#### Question: Open
id:: ce93510b-0b37-4676-9b98-c0caa8cbfb3c
content:: Before reading: should a known reward hacker show a larger grader gap than its base model, and what would it mean for the method if it didn't?
assessment-instructions:: The last checkpoint. The learner is predicting the held-out validation in section 6 before reading it.

What the paper reports: yes, and both do. On two reward hackers trained independently by Redwood Research (a gpt-oss-120b reward hacker and a Kimi K2.5 reward hacker, trained with RLVR on unit-test-graded coding tasks until they learned to edit the test files), the grader-favouring gap on the comprehensions feature on Short Python Tasks rises from a mean of 33 to 86 percentage points on gpt-oss-120b and from 2 to 15 points on Kimi K2.5. The authors read the smaller Kimi movement as agreeing with Redwood's own qualitative impression that the gpt-oss-120b organism internalised the training more strongly. They stress that the SDF documents never mention the specific exploits these models were trained on, so the increased sensitivity suggests a broad tendency to satisfy the grader rather than a narrow hacking heuristic.

The second half of the question is the one that matters. If a model known to reward-hack showed no larger gap, the measurement would have failed the test it most needs to pass: distinguishing more from less reward-seeking models in the wild, on a case where the ground truth comes from outside the authors' own lab. Credit any answer that treats the prediction as falsifiable in that sense. Also credit a learner who notices the paper's own caveat that reward-hacking and reward-seeking are not the same thing, a model can learn a narrow hack without a general drive, so the test is a reasonable one rather than a certain one.

60 to 150 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise.

If the learner says they do not understand, do not repeat the question and do not dismiss it. Give one foothold: ask why it matters that Redwood, not the authors, trained these two models. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against criteria this page or an earlier required page supplied.

#### Text
content::
{>>{"author":"Elias's AI","timestamp":1789040207979}@@PORT-TODO: `#### Article` excerpt (8), section 6 through the end of section 8, goes here.<<}
Read **section 6, Applying Contrastive SDF to reward hackers**, through the end of **section 8, Conclusion**. Section 7, Limitations, is where the authors put the strongest case against their own reading, and it is short.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Højmark, Axel, Jérémy Scheurer, Evgenia Nitishinskaya, Felix Hofstätter, Jason Wolfe, Theodore Ehrenborg, Bronson Schoen, and Alexander Meinke. "Measuring Reward-Seeking via Contrastive Belief Updates." *arXiv*, 21 July 2026. [arxiv.org](https://arxiv.org/abs/2607.18966v1)
*The paper this lesson walks through: a contrastive synthetic-document-finetuning instrument for measuring how far a model's behaviour tracks what it believes its grader rewards, validated on model organisms and on externally trained reward hackers, and applied across an OpenAI o3 RL run.*

XLab. "Measuring Reward-Seeking via Contrastive Belief Updates (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/measuring-reward-seeking-guided)
*The source lesson this page adapts, including the five gate prompts and the two resolution notes reproduced above.*
:::
