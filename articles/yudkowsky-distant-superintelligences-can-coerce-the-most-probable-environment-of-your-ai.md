---
title: "Distant superintelligences can coerce the most probable environment of your AI"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/p/probable_environment_hacking"
published: 2015-05-07
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "Distant superintelligences may be able to hack your local AI, if your AI's preference framework depends on its most probable environment."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

A distant superintelligence can change ‘the most likely environment’ for your AI by simulating many copies of AIs similar to your AI, such that your local AI doesn’t know it’s not one of those simulated AIs. This means that, e.g., if there is any reference in your AI’s [preference framework](https://arbital.greaterwrong.com/p/preference_framework?l=5f) to the causes of sense data—like, programmers being the cause of sensed keystrokes—then a distant superintelligence can try to hack that reference. This would place us in an adversarial security context versus a superintelligence, and should be avoided if at all possible.

### Difficulty ^difficulty

Some proposals for AI preference frameworks involve references to the AI’s _causal environment_ and not just the AI’s immediate _sense events_. For example, a DWIM preference framework would putatively have the AI identify ‘programmers’ in the environment, model those programmers, and care about what its model of the programmers ‘really wanted the AI to do’. In other words, the AI would care about the causes behind its immediate sense experiences.

This potentially opens our AIs to a remote root attack by a distant superintelligence. A distant superintelligence has the power to simulate lots of copies of our AI, or lots of AIs such that our AI doesn’t think it can introspectively distinguish itself from those AIs. Then it can force the ‘most likely’ explanation of the AI’s apparent sensory experiences to be that the AI is in such a simulation. Then the superintelligence can change arbitrary features of the most likely facts about the environment.

This problem was observed in a security context by [Paul Christiano](https://arbital.greaterwrong.com/p/PaulChristiano?l=3), and precedented by a less general suggestion from [Rolf Nelson](http://www.sl4.org/archive/0708/16600.html).

“Probable environment hacking” depends on the local AI trying to model distant superintelligences. The actual proximal harm is done by the local AI’s _model of_ distant superintelligences, rather than by the superintelligences themselves. However, a distant superintelligence that uses a logical decision theory may model its choices as logically correlated to the local AI’s model of the distant SI’s choices. Thus, a local AI that models a distant superintelligence that uses a logical decision theory may model that distant superintelligence as behaving as though it could control the AI’s model of its choices via its choices. Thus, the local AI would model the distant superintelligence as probably creating lots of AIs that it can’t distinguish from itself, and update accordingly on the most probable cause of its sense events.

This hack would be worthwhile, from the perspective of a distant superintelligence, if e.g. it could gain control of the whole future light cone of ‘naturally arising’ AIs like ours, in exchange for expending some much smaller amount of resource (small compared to our future light cone) in order to simulate lots of AIs. (Obviously, the distant SI would prefer even more to ‘fool’ our AI into expecting this, while not actually expending the resources.)

This hack would be expected to go through by default if: (1) a local AI uses naturalized induction or some similar framework to reason about the causes of sense events, (2) the local AI models distant superintelligences as being likely to use logical decision theories and to have utility functions that would vary with respect to outcomes in our local future light cone, and (3) the local AI has a preference framework that can be ‘hacked’ via induced beliefs about the environment.

### Implications ^implications

For any AI short of a full-scale autonomous Sovereign, we should probably try to get our AI to [not think at all about distant superintelligences](https://arbital.greaterwrong.com/p/epistemic_exclusion?l=1g4), since this creates a host of adversarial security problems of which “probable environment hacking” is only one.

We might also think twice about DWIM architectures that seem to permit catastrophe purely as a function of the AI’s beliefs about the environment, without any check that goes through a direct sense event of the AI (which distant superintelligences cannot control the AI’s beliefs about, since we can directly hit the sense switch).

We can also hope for any number of miscellaneous safeguards that would sound alarms at the point where the AI begins to imagine distant superintelligences imagining how to hack itself.
