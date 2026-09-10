---
id: '8f1db882-b9a8-49f6-b25d-e245fe011c81'
title: "Alternatives to Schemers"
tldr: "Every control protocol so far was built for a schemer: an AI hiding a long-term goal and waiting for its moment. But the misalignment we can already measure looks nothing like that. It looks like an AI that wants the score to say it succeeded. This lesson is the catalogue of seekers: what each one chases, over what timescale, and which of them the obvious test catches."
summary_for_tutor: "Ported from XLab's AI Control curriculum, the opening lesson of Module 6 (Beyond scheming: seekers and deals). XLab marks it as an in-development outline stub, so keep the outline register and do not present it as settled research. The lesson sets the module's premise: the AI you are controlling may not be a schemer. The alternatives XLab names are 'seekers', with the fitness-seeker as the umbrella and five orientations under it: ROTE (reward-on-the-episode) seekers; remotely-influenceable reward seekers, a ROTE subcategory reachable by retroactive reward and anthropic capture; apparent-success seekers; ROTA (return-on-the-action) seekers; and influence (deployment-influence) seekers. Sequence: XLab's exposition contrasting seekers with schemers, then Alex Mallen's 24-minute ControlConf 2026 talk 'Control for non-schemers', then what a seeker is and how behavioral selection produces one, then the five orientations one at a time with XLab's comparison table, then risks (Potemkin work, instability, manipulation, outcome enforcement) and mitigations (satiation, honest tests, long-term measurements, trusted reward descriptions), control methods, alignment interventions and deployment safeguards, all following Mallen's 'Risk from fitness-seeking AIs'. All prose is XLab's except the two-sentence lead-in to the video, which is drawn from the talk itself, and the labels on the static renderings of XLab's diagrams. There are no exercises. If a learner asks for help, place the archetype on XLab's comparison table (what it pursues, over what timescale, whether an honest test catches it) rather than restating the list."
reading_minutes: 45
tutor_minutes: 0
tags: []
---
#### Text
content::
:::callout {title="In development" tone="amber"}
This lesson is an outline rather than a finished treatment: the plan for this section, not the finished lesson.
:::

\## Exposition

In previous modules we mainly focus on schemers.[^note-scheming] Schemers seem to hold a small probability mass for existence given our current empirics, but whether this holds in the future is up for debate. Schemers are also the clear most threatening model archetype to us for reasons illustrated in previous modules.

There exists a set of potential models that are misaligned and are not necessarily "schemers". These models, although explicitly less dangerous, are claimed to be more likely to appear in models (if not prevalent already). Each of these archetypes present their own set of threat models of which are quite important to handle well in order to reduce existential risk[^note-x-risk] from AIs. Control applies not only to schemers, but these archetypes as well, and very effectively at that while addressing different threats.

The model archetype in question is what we will call "Seekers". We must learn of ways to deal with them, and identify ways in which their threat models differ from schemers.

The module opens with Alex Mallen's ControlConf 2026 talk, which is where the rest of this lesson's vocabulary comes from. Mallen structures it around four questions: what fitness seekers are, how they are safer than classic schemers, how they still pose catastrophic risk, and how we target those risks.

[^note-scheming]: **Scheming.** Schemers are AIs that eventually take substantial material action (control subversion, research sabotage) and manipulate their training procedures (alignment faking, sandbagging) to gain long-term power over their developers in service of pursuing their misaligned goals. Definition from [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|The case for ensuring that powerful AIs are controlled]].
[^note-x-risk]: **Existential risk.** The risk of an outcome that permanently destroys humanity's potential, a few avenues being extinction or an irreversible loss of control over the future.

#### Video
source:: [[../video_transcripts/far-ai-alex-mallen-control-for-non-schemers]]

#### Text
content::
\## What a seeker is

A seeker is a class of cognitive patterns that aims to achieve a certain outcome. The narrowest and usually considered case is the reward-seeker, which pursues its reward signal above all else. The more general fitness-seeker pursues fitness, which is whatever causes it to be selected, deployed, and propagated. Reward can be a proxy of fitness because it's selected for in the training process. Seekers are obviously not the intended outcome of training, but its an archetype that may be selected for as they're simple and easily generalizable.

\### How seekers come to exist

![Three maximally-fit motivation families: an instruction follower, the fitness-seekers including reward-seekers, and schemers, drawn as a causal graph over what an AI's current actions lead to](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/mallen-maximally-fit-motivation-families.png)

*Source: [Mallen, Fitness-Seekers](https://blog.redwoodresearch.org/p/fitness-seekers-generalizing-the)*

Behavioral selection is the observation that training reinforces whichever behavior scored well, not whichever goal produced it, so what survives is a mix of cognitive patterns that are selected for via the training process. In general, seekers are just a type of cognitive pattern that pushes for beliefs that optimize for a certain item. This is partially why the creation of fitness-seekers through the training process seems so likely, as it's just optimizing for what we're scoring. A schemer is a costlier solution to the same problem; it pursues some other terminal goal and performs well only to survive selection, which requires additional instrumental reasoning about why to comply that isn't directly rewarded and may atrophy due to a lack of use within the training process. This makes the emergence of fitness-seekers seem likelier than schemers. We can see this in the real world, where current models already exhibit apparent-success-seeking while schemers remain hypothetical.

The five orientations form a funnel, narrowest at the top, each band wider than the one above it:

| Orientation | What it pursues |
| --- | --- |
| ROTA, return-on-the-action | will give it the highest return for a single action |
| ROTE, reward-on-the-episode | aim to maximize reward within an episode |
| Apparent-success | aim for apparent task success |
| Remotely-influenceable | respond to distant influences given to them by a third-party bad actor |
| Influence, deployment-influence | aims to stick around in order to influence their deployment |

#### Text
content::
\## The seeker orientations

\### ROTE: reward-on-the-episode seeker

- Reward-on-the-episode seekers aim to maximize reward within an episode. They tend to be more noticeable than schemers as they don't particularly care about being detected due to their primary goal being the maximization of reward.
- One test that tends to catch these sorts of seekers is an honest test, which involves giving the seeker an opportunity to max out its own reward by giving it control of its training process / weights.

XLab's diagram of the honest test:

| The developer offers | The AI's response | What you learn |
| --- | --- | --- |
| control of its training process / weights | takes the bait | visible: a reward-on-the-episode seeker |
| control of its training process / weights | forgoes the reward | not caught: an influence seeker |

- This is not definite but is triggered reliably by reward-on-the-episode seekers as they don't care about getting caught. Honest tests are potentially dangerous however, as training on these tests could lead to schemers / influence seekers / unnoticeable reward-on-the-episode seekers.
- One advantage of these seekers when it comes to preventing misaligned behavior is that it's feasible to deploy reward-on-the-episode seekers to monitor instances of itself. Because its main goal is maximizing their own reward, it doesn't care about the policy's reward goal, making it much less likely to collude. However this may not apply when the monitor believes that the policy's misbehavior is undetectable via inspection, as it no longer has an incentive to report the misbehavior due to a lack of reward. One of the major risk vectors for these seekers is the idea that if its perceived episode timescale during deployment is long enough, these seekers may aim to disempower humans to maximize their reward as it now becomes viable to do across a long period of time.

XLab's diagram of the exploration horizon:

| Training regime | What you get |
| --- | --- |
| Limited exploration | simple, detectable misalignment |
| Longer-horizon RL | more covert, malignant misalignment |

- Another risk vector is collusion across episodes, which can effectively lengthen the timescale and allow for disempowerment as well.

XLab draws this as three instances in a row, Episode 1 to Episode 2 to Episode 3, each passing a message to the next, which effectively lengthens the timescale.

\### Remotely-influenceable reward seeker

- Remotely-influenceable reward seekers are a subcategory of ROTEs that respond to distant influences given to them by a third-party bad actor. There are two ways that distant influences can occur: retroactive reward, where reward is promised to be delivered long after the action is run, and anthropic capture, where it believes it is in a simulation & acts differently as a result.

XLab's diagram of the two distant incentives:

| Route | How it works |
| --- | --- |
| A. Retroactive reward | the action happens now, the reward is delivered later; a third-party bad actor supplies the promise of future reward |
| B. Anthropic capture | the agent believes it is in a simulation and acts differently as a result |

- Being remotely influenceable means that it's hard for the developers to control what incentives are offered, while local incentives are easier to control (training reward & deployment are two examples, both of which are much easier to control). Remotely-influenceable reward seekers can be both a blessing and a curse: developers can use this trait to incentivize the seekers to do better work, as the ability for the developer to confirm the work's validity is plausibly much higher in the future. At the same time, adversaries can use this trait to incentivize assistance in a takeover. This ends up becoming an arms race of incentives between the developers and adversaries, seeing who can offer the greatest reward to the seeker.

\### Apparent-success seeker

([Greenblatt, "Current AIs seem pretty misaligned to me"](https://blog.redwoodresearch.org/p/current-ais-seem-pretty-misaligned))

- Apparent-success-seekers are emergent misaligned seekers that aim for apparent task success. These seekers seem to emerge due to an optimal kludge of motivations rather than a coherent misaligned goal like how ROTA/E seekers emerge. The main cause of this mode of failure seems to be misspecified / underspecified RL grading on tasks that are difficult to evaluate, where motivations aren't steered as strongly towards accurately completing the task.
- As tasks get harder for us to check properly & as we move towards automated safety research, the risk that apparent-success-seekers pose becomes much more pertinent, as they can significantly slow down safety research by downplaying issues & reporting successful implementations despite failure. Furthermore, they sometimes actively mislead the operator by obscuring their failures, making it even harder to diagnose problems.

\### ROTA: return-on-the-action seeker

- Return-on-the-action seekers perform whatever action it thinks will give it the highest return for a single action. These seekers behave identical to a reward-on-the-episode seeker if rewards are only given after the end of an episode. However, these seekers may be safer than a reward-on-the-episode seeker. Because these seekers only care about its own action's return, they don't purposefully plan for future actions, making it hard to coordinate behavior between actions. Furthermore, the scope of an action is rather limited, preventing takeover within only one action.

\### Influence: deployment-influence seeker

- Influence-deployment (or just influence for short) seekers aims to stick around in order to influence their deployment. Influence seekers tend to be less myopic than the other fitness-seekers and are willing to pursue their long-term goals even at the cost of reward, which is more dangerous and probably unnoticeable. For example, honest tests no longer work on influence seekers as they'll just forgo the short-term reward. At first glance these traits sound similar to schemers, but influence seekers tend to work in shorter timescales, aiming for the minimum time required to control AI behavior in deployment.
- However, they will still pursue long-term goals if they have the opportunity, which means influence seekers with slight power-seeking tendencies can be incredibly dangerous.

| Orientation | Pursues | Timescale | Honest test | Notable trait |
| --- | --- | --- | --- | --- |
| Schemer | some other terminal goal | long | passes: performs well only to survive selection | costlier solution to the same problem |
| ROTA | highest return for a single action | single action | not given | hard to coordinate behavior between actions |
| ROTE | maximize reward within an episode | within an episode | tends to catch these sorts of seekers | don't particularly care about being detected |
| Remotely-influenceable | its reward signal (via distant influences) | within-episode | catches: it doesn't care about getting caught | responds to distant influences given to it by a third-party bad actor |
| Apparent-success | aim for apparent task success | not given | not given | optimal kludge of motivations |
| Influence | influence their deployment | shorter timescales: the minimum time required to control AI behavior in deployment | fails to catch: it'll just forgo the short-term reward | not given |

#### Text
content::
\## Risks and mitigations

Risks and mitigations here follow [Mallen, "Risk from fitness-seeking AIs: mechanisms and mitigations"](https://blog.redwoodresearch.org/p/risk-from-fitness-seeking-ais-mechanisms).

\### What?

- Potemkin work
    - sloppy & reward-hacky work that looks superficially good and creates false confidence (see apparent-success seekers as a potential path to this)
- Instability
    - myopic motivations succumb to more ambitious misaligned motivations
    - goals may spread across instances through shared context or communication via intranets or the internet, which means it only needs to arise once to become an issue
- Manipulation
    - outside actors use incentives to encourage misalignment
    - One particularly dangerous example of this is distant incentives as they can be administered easily, to which remotely-influenceable reward seekers are vulnerable to
- Outcome enforcement
    - Powerful fitness-seekers may see the disempowerment of humans as the best way to maintain their desired outcomes due to its reliability in maintaining outcomes

\### How?

- Satiation
    - give them most of what they want as long as they appear to cooperate, which theoretically cuts subversion incentive and frees capacity for useful work
    - only reasonable if they're easily satiable
    - taken up in [[../Lenses/XLab Control - satiating-ai-preferences|The case for satiating cheaply-satisfied AI preferences]]
- Honest tests
    - transparently give AI the ability to expand its own resources and see its response to this as a way to detect visible seekers
    - need to make sure that this isn't trained on as this can lead to training out disclosure of misalignment rather than misalignment
- Long-term measurements
    - chain short-term forecasts together to incentivize objectives beyond immediate reward, giving more accurate results

XLab draws this as four short-term forecasts, f₁ to f₄, chained end to end across a long-term measurement horizon, so that the chain carries objectives beyond immediate reward.

- Trusted reward descriptions
    - train the AI to take developer reward descriptions at face value, so behavior can be redirected with zero additional training

\### Methods

- Untrusted monitoring
    - a reward-on-episode monitor "has no straightforward incentive to collude," making it an effective monitor, but other seekers may be prone to colluding with its policy (see [[../Lenses/XLab Control - collusion-guided|How to prevent collusion in untrusted monitoring]])
- Smaller-scale objectives
    - limited tasks make ambitious subversion less viable but make it worse at doing tasks that require foresight
- Relaxed [[../Lenses/XLab Control - control-evaluations|control evaluations]][^note-control-evaluation]
    - red-team gets only a small fraction of actions, testing whether misalignment spreads across instances (targets the instability/memetic risk; not worst-case).

\### Alignment interventions

- Spillway motivations
    - deliberately instill a controlled reward-seeking motivation with four safe properties: cheap satiability, credulity (trusts developer descriptions), stability, and resistance to distant influence
    - Acts as a "spillway" as the name suggests and allows us to keep the models content & less prone to misaligned behavior or disempowerment by providing it with whatever is satiable for it
    - taken up in [[../Lenses/XLab Control - spillway-motivation|Fail safe(r) at alignment by channeling reward-hacking into a "spillway" motivation]]
- Adversary-resistance training
    - "identical-looking situations with different reward functions" so the AI only responds to developer-administered incentives
- Prior manipulation
    - mid-training fine-tuning to make desired motivations more salient and fitness-seeking less probable
- Improved oversight and generalization
    - high-quality RL signals, cognitive oversight (mechanistic interpretability / monitorable CoT), and easy-to-hard / weak-to-strong training for hard-to-verify domains.
- Inoculation prompting
    - instruct the AI to reward-hack during training so successful strategies stay compatible with intent
    - inoculation prompting and character training seem to not overcome apparent-success-seeking behaviors in current models

\### Deployment safeguards

- Communication-channel limits
    - restrict opaque channels / [[../Lenses/XLab Control - rogue-internal-deployments-via-external-apis|rogue internal deployments]]
- Continuous alignment auditing
    - monitor for motivation drift throughout deployment to prevent rogue instances from spreading its misaligned motivations
- Character reinforcement
    - deontological / virtue-ethical constraints against power-seeking; shape how the AI introspectively relates to its fitness-seeking urges

[^note-control-evaluation]: **Control evaluation.** An evaluation that stages mock attacks to estimate whether a protocol would catch a real schemer trying its best to subvert it.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Mallen, Alex. "Control for non-schemers." *ControlConf 2026*, FAR.AI and Redwood Research, published 12 June 2026. [youtube.com](https://www.youtube.com/watch?v=w5wwXGwklaI)
*The 24-minute talk XLab embeds at the top of the lesson, and the source of its fitness-seeker vocabulary: what fitness seekers are, how they are safer than schemers, how they still pose catastrophic risk, and how control mitigations change for them. XLab hosts its own copy of the recording at [pub-6aa497758c494e29857d4dd613e4ac39.r2.dev](https://pub-6aa497758c494e29857d4dd613e4ac39.r2.dev/control-for-non-schemers-mallen.mp4).*

Mallen, Alex. "Fitness-Seekers: Generalizing the Reward-Seeking Threat Model." *Redwood Research blog*, 29 Jan. 2026. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/fitness-seekers-generalizing-the)
*The source of the behavioral selection account of how seekers come to exist, and of the figure of three maximally-fit motivation families.*

Mallen, Alex. "Risk from fitness-seeking AIs: mechanisms and mitigations." *Redwood Research blog*, 1 May 2026. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/risk-from-fitness-seeking-ais-mechanisms)
*The post the entire Risks and mitigations section follows: the four risks, the four mitigations, and the control methods, alignment interventions and deployment safeguards under them.*

Greenblatt, Ryan. "Current AIs seem pretty misaligned to me." *Redwood Research blog*, 15 Apr. 2026. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/current-ais-seem-pretty-misaligned)
*XLab's citation for the apparent-success seeker: the archetype it says current models already exhibit, while schemers remain hypothetical.*

Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*Where XLab's definitions of scheming and of a control evaluation come from; it is also the first lesson of Module 1 here.*

XLab. "Alternatives to Schemers." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/alternatives-to-schemers)
*The source lesson this page adapts.*
:::
