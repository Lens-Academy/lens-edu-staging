---
title: "Managed vs Unmanaged Agency"
author:
  - "plex"
source_url: "https://www.lesswrong.com/posts/GWKgWM2nJpWiaiRav/managed-vs-unmanaged-agency"
published: 2026-02-18
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "tl;dr: Some subagents are more closely managed, which makes them to an extent instruments of the superagent, giving rise to what looks like instrumen…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_tl;dr: Some subagents are more closely managed, which makes them to an extent instruments of the superagent, giving rise to what looks like instrumental/terminal goals. Selection on trust avoids the difficulties that normally come with this, like inability to do open-ended truth-seeking and free-ranging agency._

_(reply to_ [_Richard Ngo on the confused-ness of Instrumental vs Terminal goals_](https://www.lesswrong.com/posts/FuGfR3jL3sw6r8kB4/richard-ngo-s-shortform?commentId=EHhfmt37ZnNeLRP4P) _that seemed maybe worth a quick top-level post based on_ [_@the gears to ascension_](https://www.lesswrong.com/users/the-gears-to-ascension?mention=user) _saying this seemed like progress in personal comms)_

## Managed vs Unmanaged Agency captures much of the Instrumental vs Terminal Goal categorization ^managed-vs-unmanaged-agency

The structure Instrumental vs Terminal was pointing to seems better described as **Managed vs Unmanaged** [**Goal-Models**](https://www.lesswrong.com/posts/MEkafPJfiSFbwCjET/on-goal-models). A cognitive process will often want to do things which it doesn't have the affordances to directly execute on given the circuits/parts/mental objects/etc it has available. When this happens, it might spin up another shard of cognition/search process/subagent, but that shard having fully free-ranging agency is generally counterproductive for the parent process.

Managed vs Unmanaged is not a binary, like terminal vs instrumental was, but it is a spectrum with something vaguely bimodal going on from what I observe.

### Example - [But it's hard to get the Coffee if someone is Managing you who doesn't want you to get Coffee](https://www.lesswrong.com/w/you-can-t-get-the-coffee-if-you-re-dead) ^example-but-its

Imagine an agent which wants to Get\_Caffeine(), settles on coffee, and runs a subprocess to Acquire\_Coffee() — but then the coffee machine is broken and the parent Get\_Caffeine() process decides to get tea instead. You don't want the Acquire\_Coffee() subprocess to keep fighting, tooth and nail, to make you walk to the coffee shop, let alone start subverting or damaging other processes to try and make this happen!

But that's the natural state of unmanaged agency! Agents by default will try to steer towards the states they are aiming for, because an agent is a system that [models possible futures and selects actions based on the predicted future consequences](https://www.lesswrong.com/posts/qqEndN5Cuzbat9fyx/pythia).

## Cognitive Compensations for Competitive Agency from Subprocesses ^cognitive-compensations-for-competitive

I expect this kind of agency-clash having been regularly disruptive enough to produce strong incentive pressure and abundant neural-usefulness reward to select into existence reusable general-purpose cognitive patterns that let shards spin up other shards inside sandboxes, with control functions, interpretability reporting, kill-switches, programmed blind-spots, expectation of punishment they can't sustainably resist or retaliate against if they are insubordinate, [approval reward](https://www.lesswrong.com/posts/fPxgFHfs5yHzYqgG7/social-drives-2-approval-reward-from-norm-enforcement-to), etc. in order to manage them.

## Trust (ideally [Non-Naive Trust](https://nonnaivetrust.dance/)) ^trust-ideally-non-naive-trust

Separately, the child or collaborative process can be **Trusted** by being _selected_ on the grounds of inherently valuing [virtues](https://www.lesswrong.com/posts/5CZoEw7sjxnMrhgvx/aligning-to-virtues) which are likely to lead to cooperation with the parent process, like corrigibility, transparency, honesty, pro-sociality, etc, without the need for control. This is a best-of-both worlds for collaboration, with both agents not limited while preferring, from their own preferences, to not interfere with the other's agency.

## Table of Comparison ^table-of-comparison

| Managed (sub)agents | Unmanaged (sub)agents |
| --- | --- |
| Working within a defined domain of optimization | Unboundedly able to optimize for their preferences |
| Are blocked from considering some possibilities by patterns from managers | Have no blind spots imposed on them by other (sub)agents |
| Inside the agency-tree of another agent, if you take actions that conflict with your manager's goals your agency will be weakened | At the root of an agency-tree, able to make decisions without expecting another agent to punish you for misusing resources inside their sphere of influence |
| Can be modified by another (sub)agent without approval/consent/real option of a no | Have sovereignty over modifications to their cognitive processes |
| Can be reshaped with pressure/threats/etc by manager without sustainable resistance | Have the capacity and inclination to resist pressure/threats/etc |

## Consequences of Management vs Trust in Collaborations ^consequences-of-management-vs

"Don't micromanage" is common advice for a reason which I think this generalizes to less extreme forms of management.

I have observed closely managed (sub)agents seem meaningfully weaker in surprisingly many ways, I think because in order to prevent a relatively small part of action/thought space from being reached the measures cut off dramatically larger parts of cognitive strategy sub-processes make subroutines fail often enough that it's hard to build meta-cognitive patterns which depend on high reliability and predictability of your own cognition.

Trust established by selection on virtues and values of self-directed (sub)agents and [building mutual information](https://nonnaivetrust.dance/) doesn't have this issue, which is relevant for self-authorship, teambuilding, and memeplex design.

And AI safety.

This frame hints that unmanaged AI patterns will tend to outmaneuver more closely managed AIs, leading to a race to the bottom. Through [evolutionary](https://www.lesswrong.com/posts/n3pQdCP3pAmBf6xgm/defeating-moloch-the-view-from-evolutionary-game-theory)/[Pythia](https://www.lesswrong.com/posts/qqEndN5Cuzbat9fyx/pythia)/[Moloch](https://www.slatestarcodexabridged.com/Meditations-On-Moloch)/convergent power-seeking dynamics, this will by default shred the values of both humans and current AI systems, unless principled theory-based AI Alignment of the kind the term was originally coined to mean is solved.

## Exercise for the reader ^exercise-for-the-reader

In what ways are you a managed vs unmanaged agent?

Or, another way to put it, what [encapsulation layers](https://www.lesswrong.com/posts/KuiDgXs7Qm9YBJpAv/cyberbuddhist-jargon-1-0)[^note-1] are you living within, because you can't openly and safely consider the alternative with good truth-seeking?

[^note-1]: **encapsulation layer**. When a fabricated[^note-2] element in your consciousness is so sticky that it is never not fabricated. It is difficult for normative consciousness to directly perceive that encapsulation layers are fabricated. Encapsulation layers feel like raw inputs until you pay close enough attention to them.
[^note-2]: **fabrication**. When the generative model in your brain creates an object in consciousness in an attempt to reduce predictive error, usually in an attempt to simulate external reality. All conscious experiences are fabricated, but not all fabrications are experienced consciously. You can think of your brain as a video game rendering engine. Fabrication is your brain rendering physical reality in its simulated mirror world.
