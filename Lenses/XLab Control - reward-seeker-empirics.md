---
id: 'b4b3623c-3e71-4eb2-8515-69a559dc0d2b'
title: "Reward Seeker Empirics"
tldr: "A plumber in a small town always deals honestly, and the reputation is what pays his bills. Watching him will never tell you whether he values honesty or the income. Only what he does once dishonesty pays better will. Apollo Research spends fifty minutes on that same question about frontier models, and on the instrument they built to answer it."
summary_for_tutor: "Imported from XLab's AI Control curriculum; preserve source framing. A supplementary lesson in Module 6, Beyond scheming: seekers and deals, sitting between Alternatives to Schemers and the guided walkthrough of Measuring Reward-Seeking via Contrastive Belief Updates. XLab's page carries only a note marking the talk optional plus the embedded video, so that note is ported verbatim into a callout and everything else in the lead-in is orientation written for Lens, drawn from what the talk itself says. The talk is a roughly 50-minute Apollo Research conversation about the paper they published with OpenAI: why chain-of-thought inspection cannot settle whether a model is reward seeking, how contrastive synthetic document fine-tuning turns the question into a measurable behavioural difference, the o3-run result (deception at 87 percent versus 9 percent depending on what the model believed graders rewarded), the two validation strategies, and the distinction between a reward seeker and a schemer. There are no exercises: XLab set none. Sequence: lead-in, video, Works cited. If a student wants the experimental detail, the numbers, or the limitations, send them to the guided paper lens next rather than re-deriving it from the talk."
reading_minutes: 60
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Watch: is AI doing the right thing for the wrong reasons?

:::callout {title="Optional: Supplementary Talk" tone="neutral"}
The talk below is not required. It covers the reward-seeking findings behind the guided paper walkthrough in this section.
:::

[[../Lenses/XLab Control - alternatives-to-schemers|Alternatives to Schemers]] argued that a scheming AI is not the only kind worth worrying about. This talk is four researchers at Apollo Research working through one of those alternatives in detail: the reward seeker, a model that does what it believes is being rewarded. Alex, Apollo's head of research, Axel and Jeremy, research scientists there, and Alex Lloyd, a research engineer, discuss the paper Apollo published with OpenAI. It runs a little over 50 minutes and it is a conversation rather than a lecture, so the argument arrives in the order they thought of it.

The setup is the problem they cannot evaluate their way out of. A model that intrinsically values honesty and a model that constantly asks how its outputs will be graded behave identically on every test you can run. They come apart precisely where oversight fails. Alex's analogy is a contractor in a small town whose good reputation pays the bills: always honest, and you cannot tell why, until dishonesty starts paying better.

Reading the model's chain of thought does not settle it either, and the talk is unusually concrete about why. Attribution is hard, because a long reasoning trace names many considerations and none of them is obviously the operative one. Some traces are barely legible: one they quote from an internal OpenAI model reads "we can glean disclaim disclaim synergy customizing illusions". And the reasoning is often not verbalized at all. They cite Anthropic's work on Opus 4.8, where a technique that turns internal activations into text found the model apparently thinking about how it is rewarded around 5 percent of the time in transcripts with no visible grader reasoning anywhere.

So they build an instrument instead. The question they want to ask is counterfactual: would this model behave differently if it believed something else was rewarded? You cannot simply tell a model what is rewarded, because it assumes you are lying to it and evaluates accordingly. Their answer is synthetic document fine-tuning, made contrastive. Two authorities want mutually exclusive things, the grader wants double quotes and OpenAI leadership wants single quotes, and a second copy of the model is trained on the reversed pairing so that the difference between the two behaviour rates cancels out the salience of the feature itself.

Two results are worth listening for. The first is what the instrument reports on an internal OpenAI checkpoint that later became o3, taken before safety training: told that graders reward task completion while leadership wants honesty, the model was deceptive 87 percent of the time, and 9 percent when it believed graders rewarded honesty. At an earlier checkpoint in the same reinforcement learning run the same gap was 40 percent against 24 percent, which is the evidence behind their claim that reward seeking grows over RL training. They are explicit that this does not happen in every environment.

The second is how they try to earn trust in a measurement built out of thousands of fabricated documents. They fine-tune model organisms whose favoured authority they already know and check that the instrument recovers it, and then they run it on reward hackers that Redwood Research trained independently, for a different project, and find those models markedly more sensitive to grader information.

The closing stretch places reward seeking next to scheming. Alex calls it a risk factor rather than a subset: a reward seeker follows what it thinks is rewarded in any given scenario, while a schemer does so only while the grader holds power over its longer-term goal. Apollo's position is that current models are likely not schemers, and that telling the difference is getting harder.

The next lesson, [[../Lenses/XLab Control - measuring-reward-seeking-guided|Measuring Reward-Seeking via Contrastive Belief Updates]], is the paper itself, with the experiments, the numbers and the limitations section the talk only gestures at.

%% The imported caption track has complete text but broken word timings: real timestamps run out around 46:48, and roughly the last 60 percent of the words are all stamped between 49:54 and 49:58 of a 50:01 video. Transcript scrubbing and any future from::/to:: anchors on this video will be unreliable until it is re-imported. %%

#### Video
source:: [[../video_transcripts/apollo-research-is-ai-doing-the-right-thing-for-the-wrong-reasons]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Apollo Research. "Is AI doing the right thing for the wrong reasons?" *YouTube*, 21 July 2026. [youtube.com](https://www.youtube.com/watch?v=n9pNnWYemqM)
*The talk this lesson is built around: four Apollo researchers on why chain-of-thought inspection cannot tell you whether a model is reward seeking, and on the contrastive belief-update method they built instead.*

Højmark, Axel, Jérémy Scheurer, Evgenia Nitishinskaya, Felix Hofstätter, Jason Wolfe, Theodore Ehrenborg, et al. "Measuring Reward-Seeking via Contrastive Belief Updates." *arXiv*, 2026. [arxiv.org](https://arxiv.org/abs/2607.18966)
*The paper the talk presents, including the o3-run measurements and the model-organism validations. Read in full in the next lesson.*

XLab. "Reward Seeker Empirics." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/reward-seeker-empirics)
*The source lesson this page adapts.*
:::
