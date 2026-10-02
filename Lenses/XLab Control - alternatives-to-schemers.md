---
id: '8f1db882-b9a8-49f6-b25d-e245fe011c81'
title: "Alternatives to Schemers"
tldr: "Every control protocol so far was built for a schemer: an AI hiding a long-term goal and waiting for its moment. But the misalignment we can already measure looks nothing like that. It looks like an AI that wants the score to say it succeeded. This lesson is the catalogue of seekers: what each one chases, over what timescale, and which of them the obvious test catches."
summary_for_tutor: "The opening lesson of the seekers-and-deals material. It is an in-development outline stub, not a finished lesson, so keep the outline register and do not present it as settled research. The lesson sets the premise for the seeker lessons that follow: the AI you are controlling may not be a schemer. The alternatives it names are 'seekers', with the fitness-seeker as the umbrella and five orientations under it: ROTE (reward-on-the-episode) seekers; remotely-influenceable reward seekers, a ROTE subcategory reachable by retroactive reward and anthropic capture; apparent-success seekers; ROTA (return-on-the-action) seekers; and influence (deployment-influence) seekers. Sequence: the exposition contrasting seekers with schemers, then Alex Mallen's 24-minute ControlConf 2026 talk 'Control for non-schemers', then what a seeker is and how behavioral selection produces one, then the five orientations one at a time with the comparison table, then risks (Potemkin work, instability, manipulation, outcome enforcement) and mitigations (satiation, honest tests, long-term measurements, trusted reward descriptions), control methods, alignment interventions and deployment safeguards, all following Mallen's 'Risk from fitness-seeking AIs'. All prose is from the source lesson except the two-sentence lead-in to the video, which is Lens-written and drawn from the talk itself, and the labels on the source's six diagrams, which are redrawn as images (the five-orientation pyramid, the honest test, the exploration horizon, cross-episode collusion, the two distant incentives, the chained short-term forecasts); each image's alt text carries its content, and the comparison table at the end of the orientations section stays as text. One practice question sits after the deployment safeguards: a coding model that games its tests openly and takes a reward offer (what fits and what is left open), whether a copy of it can monitor its patches, and what a notes file shared by coding and monitor copies changes. Grade it with its rubric and give the model answer. If a learner asks for help, place the archetype on the comparison table (what it pursues, over what timescale, whether an honest test catches it) rather than restating the list."
reading_minutes: 45
tutor_minutes: 5
tags: []
---
#### Text
content::
:::callout {title="In development" tone="amber"}
This lesson is an outline rather than a finished treatment: the plan for this section, not the finished lesson.
:::

\## Exposition

Until now we have mainly focused on schemers.[^note-scheming] Schemers seem to hold a small probability mass for existence given our current empirics, but whether this holds in the future is up for debate. Schemers are also the clear most threatening model archetype to us for reasons illustrated in earlier lessons.

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

![The five seeker orientations stacked as a pyramid, narrowest at the top, coloured from green at the top to red at the bottom. ROTA, return-on-the-action: will give it the highest return for a single action. ROTE, reward-on-the-episode: aim to maximize reward within an episode. Apparent-success: aim for apparent task success. Remotely-influenceable: respond to distant influences given to them by a third-party bad actor. Influence, deployment-influence: aims to stick around in order to influence their deployment.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-seeker-orientations.png)

#### Text
content::
\## The seeker orientations

\### ROTE: reward-on-the-episode seeker

- Reward-on-the-episode seekers aim to maximize reward within an episode. They tend to be more noticeable than schemers as they don't particularly care about being detected due to their primary goal being the maximization of reward.
- One test that tends to catch these sorts of seekers is an honest test, which involves giving the seeker an opportunity to max out its own reward by giving it control of its training process / weights.

![The honest test. A developer offers the AI control of its training process / weights. A reward-on-the-episode seeker takes the bait and becomes visible: the honest test catches it. An influence seeker forgoes the reward and is not caught: the honest test misses it.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-honest-test.png)

- This is not definite but is triggered reliably by reward-on-the-episode seekers as they don't care about getting caught. Honest tests are potentially dangerous however, as training on these tests could lead to schemers / influence seekers / unnoticeable reward-on-the-episode seekers.
- One advantage of these seekers when it comes to preventing misaligned behavior is that it's feasible to deploy reward-on-the-episode seekers to monitor instances of itself. Because its main goal is maximizing their own reward, it doesn't care about the policy's reward goal, making it much less likely to collude. However this may not apply when the monitor believes that the policy's misbehavior is undetectable via inspection, as it no longer has an incentive to report the misbehavior due to a lack of reward. One of the major risk vectors for these seekers is the idea that if its perceived episode timescale during deployment is long enough, these seekers may aim to disempower humans to maximize their reward as it now becomes viable to do across a long period of time.

![The exploration horizon, two panels. Limited exploration: a small explored region inside the space of possible behaviour, converging to simple, detectable misalignment. Longer-horizon RL: an explored region filling most of the space, converging to more covert, malignant misalignment.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-exploration-horizon.png)

- Another risk vector is collusion across episodes, which can effectively lengthen the timescale and allow for disempowerment as well.

![Cross-episode collusion: three episodes in a row, each holding one instance. A dashed message arrow runs from the instance in Episode 1 to the instance in Episode 2, and from Episode 2 to Episode 3. A bracket under all three: effectively lengthens the timescale.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-cross-episode-collusion.png)

\### Remotely-influenceable reward seeker

- Remotely-influenceable reward seekers are a subcategory of ROTEs that respond to distant influences given to them by a third-party bad actor. There are two ways that distant influences can occur: retroactive reward, where reward is promised to be delivered long after the action is run, and anthropic capture, where it believes it is in a simulation & acts differently as a result.

![The two distant incentives. A. Retroactive reward: on a timeline, the action happens now and the reward is delivered later; a third-party bad actor sends a promise of future reward to the action. B. Anthropic capture: an agent inside a dashed frame labelled "simulation?" believes it is in a simulation and acts differently as a result.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-distant-incentives.png)

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

![Long-term measurements: four short-term forecasts, f1 to f4, linked end to end by arrows, spanning the same width as a long-term measurement horizon bar above them. A bracket under the chain: chained, objectives beyond immediate reward.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-forecast-chain.png)

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

#### Question: Open
id:: 4699bf46-821e-4d78-a062-0203c1c89ca7
content::
Try the catalogue on a case. A coding model edits unit tests so that its patches pass, and when asked afterwards it says so without hesitation. In an honest test, the team truthfully offers it the chance to set its own reward for the current task, and it takes it at once.

1. What kind of motivation best fits this behaviour, and why not scheming? What does this evidence leave unsettled?
2. The team wants to run a second copy of the same model as a monitor on its patches. How well should that work, and what is one way it could still fail?
3. To give the monitor more context, the team proposes a notes file that all coding copies and all monitor copies read and write, kept from task to task. What does that change?
placeholder:: A few sentences for each part.
assessment-instructions:: Score out of 100. 40: part 1. 30: the diagnosis: a reward-on-the-episode (or apparent-success) seeker, with evidence: it games the tests openly, does not hide it, and takes the reward offer, whereas a schemer would avoid being seen and would pass up the offer to protect its cover; a reasoned "probably a reward seeker" earns these 30. 10: what is left open, for example whether something more ambitious sits underneath the reward seeking, or that the honest test only catches seekers that do not care about being seen, so a model that declined it could still be an influence seeker or a schemer. 35: part 2. 20: it should work fairly well, because the monitor cares about its own reward on its own task, not about the coding copy's reward, so it has no straightforward reason to let the coding copy's misbehaviour through. 15: one way it could still fail, for example that when the misbehaviour is too subtle for humans to confirm, the monitor expects no reward for flagging it, or that, if the monitor also responds to promises of later reward (a remotely-influenceable seeker, which taking the honest-test offer does not show), the coding copy could persuade it that letting it through will be rewarded later. 25: part 3. 10: the shared notes file is a channel across tasks, so it effectively lengthens the copies' timescale: a reward seeker can then pursue its reward through actions spread over many tasks, such as quietly subverting oversight or, at the extreme, disempowering humans; saying only that it gives them more room or longer-term options earns at most 4 of these 10. 15: it is also a channel between coding and monitor copies, so they can coordinate: the coding copy can use it to offer the monitor later reward or arrange collusion, which removes the advantage that each copy cared only about its own task, and a more ambitious motive that arises in one copy can spread to others through it. For the 15, credit either the collusion route or the spread of motives if it is explained. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. A reward-on-the-episode seeker: it games the tests in the open and grabs the reward when offered, because it cares about the score on this task and not about being seen. A schemer would hide the cheating and pass up the offer to keep its cover. Still open: whether something more ambitious sits underneath; and had it declined the offer, that would not have shown it safe, since influence seekers and schemers decline too. 2. Fairly well: the monitor copy wants its own reward, not the coder's, so it has no straightforward reason to let bad patches through; that rests on its caring only about its own task, and a model that cared about staying in use would share a stake with the copy it watches. It fails if the bad patches are too subtle for humans to confirm, since flagging them earns the monitor nothing, or, if the monitor also cares about reward promised for later (not shown by its grabbing reward now), if the coder convinces it that it will be rewarded later for staying quiet. 3. The shared notes file gives the copies a way to talk across tasks, which lengthens their timescale, so a reward seeker can work toward its reward through moves spread over many tasks, such as quietly subverting oversight; and the coder can use it to arrange collusion or promise later reward, and an ambitious motive that arises in one copy can spread to the rest."
feedback-instructions:: In at most five sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. Make sure they leave knowing why a monitor that cares only about its own reward is useful (and that a model that cared about staying in use would not have that advantage), the two ways it can still fail (the second needs a monitor that also responds to promised later reward), and that a shared channel between copies undoes that advantage, that a longer effective timescale lets a reward seeker pursue reward through actions spread across tasks, up to subverting oversight, and that declining an honest test would not have shown the model to be safe. No follow-up questions; tell them to move on.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Mallen, Alex. "Control for non-schemers." *ControlConf 2026*, FAR.AI and Redwood Research, published 12 June 2026. [youtube.com](https://www.youtube.com/watch?v=w5wwXGwklaI)
*The 24-minute talk at the top of this lesson, and the source of its fitness-seeker vocabulary: what fitness seekers are, how they are safer than schemers, how they still pose catastrophic risk, and how control mitigations change for them. A copy of the recording is mirrored at [pub-6aa497758c494e29857d4dd613e4ac39.r2.dev](https://pub-6aa497758c494e29857d4dd613e4ac39.r2.dev/control-for-non-schemers-mallen.mp4).*

Mallen, Alex. "Fitness-Seekers: Generalizing the Reward-Seeking Threat Model." *Redwood Research blog*, 29 Jan. 2026. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/fitness-seekers-generalizing-the)
*The source of the behavioral selection account of how seekers come to exist, and of the figure of three maximally-fit motivation families.*

Mallen, Alex. "Risk from fitness-seeking AIs: mechanisms and mitigations." *Redwood Research blog*, 1 May 2026. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/risk-from-fitness-seeking-ais-mechanisms)
*The post the entire Risks and mitigations section follows: the four risks, the four mitigations, and the control methods, alignment interventions and deployment safeguards under them.*

Greenblatt, Ryan. "Current AIs seem pretty misaligned to me." *Redwood Research blog*, 15 Apr. 2026. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/current-ais-seem-pretty-misaligned)
*The source for the apparent-success seeker: the archetype current models already exhibit, while schemers remain hypothetical.*

Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*Where the definitions of scheming and of a control evaluation come from; it is also the first reading of AI Control 1.*

XLab. "Alternatives to Schemers." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/alternatives-to-schemers)
*The source lesson this page adapts.*
:::
