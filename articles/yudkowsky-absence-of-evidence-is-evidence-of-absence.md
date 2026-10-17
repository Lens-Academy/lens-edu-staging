---
title: "Absence of Evidence Is Evidence of Absence"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/s/6xgy8XYEisLk3tCjH/p/mnS2WYLCGJP2kQkRn"
published: 2007-08-12
created: 2026-10-17
accessed: 2026-10-17
llm-review:
  date: 2026-10-17
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-17
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

From Robyn Dawes’s _Rational Choice in an Uncertain World_:

> In fact, this post-hoc fitting of evidence to hypothesis was involved in a most grievous chapter in United States history: the internment of Japanese-Americans at the beginning of the Second World War. When California governor Earl Warren testified before a congressional hearing in San Francisco on February 21, 1942, a questioner pointed out that there had been no sabotage or any other type of espionage by the Japanese-Americans up to that time. Warren responded, “I take the view that this lack \[of subversive activity\] is the most ominous sign in our whole situation. It convinces me more than perhaps any other factor that the sabotage we are to get, the Fifth Column activities are to get, are timed just like Pearl Harbor was timed . . . I believe we are just being lulled into a false sense of security.”

Consider Warren’s argument from a Bayesian perspective. When we see evidence, hypotheses that assigned a _higher_ likelihood to that evidence gain probability, at the expense of hypotheses that assigned a _lower_ likelihood to the evidence. This is a phenomenon of _relative_ likelihoods and _relative_ probabilities. You can assign a high likelihood to the evidence and still lose probability mass to some other hypothesis, if that other hypothesis assigns a likelihood that is even higher.

Warren seems to be arguing that, given that we see no sabotage, this _confirms_ that a Fifth Column exists. You could argue that a Fifth Column _might_ delay its sabotage. But the likelihood is still higher that the _absence_ of a Fifth Column would perform an absence of sabotage.

Let E stand for the observation of sabotage, and ¬E for the observation of no sabotage. The symbol H1 stands for the hypothesis of a Japanese-American Fifth Column, and H2 for the hypothesis that no Fifth Column exists. The _conditional probability_ P(E | H), or “E given H,” is how confidently we’d expect to see the evidence E if we assumed the hypothesis H were true.

Whatever the likelihood that a Fifth Column would do no sabotage, the probability P(¬E | H1), it won’t be as large as the likelihood that there’s no sabotage _given that there’s no Fifth Column_, the probability P(¬E | H2). So observing a lack of sabotage increases the probability that no Fifth Column exists.

A lack of sabotage doesn’t _prove_ that no Fifth Column exists. Absence of _proof_ is not _proof_ of absence. In logic, (A ⇒ B), read “A implies B,” is not equivalent to (¬A ⇒ ¬B), read “not-A implies not-B .”

But in probability theory, absence of _evidence_ is always _evidence_ of absence. If E is a binary event and P(H | E) > P(H), i.e., seeing E increases the probability of H, then P(H | ¬ E) < P(H), i.e., failure to observe E decreases the probability of H . The probability P(H) is a weighted mix of P(H | E) and P(H | ¬ E), and necessarily lies between the two.[^note-bayes]

Under the vast majority of real-life circumstances, a cause may not reliably produce signs of itself, but the absence of the cause is even less likely to produce the signs. The absence of an observation may be strong evidence of absence or very weak evidence of absence, depending on how likely the cause is to produce the observation. The absence of an observation that is only weakly permitted (even if the alternative hypothesis does not allow it at all) is very weak evidence of absence (though it is evidence nonetheless). This is the fallacy of “gaps in the fossil record”—fossils form only rarely; it is futile to trumpet the absence of a weakly permitted observation when many strong positive observations have already been recorded. But if there are _no_ positive observations at all, it is time to worry; hence the Fermi Paradox.

Your strength as a rationalist is your ability to be more confused by fiction than by reality; if you are equally good at explaining any outcome you have zero knowledge. The strength of a model is not what it _can_ explain, but what it _can’t_, for only prohibitions constrain anticipation. If you don’t notice when your model makes the evidence unlikely, you might as well have no model, and also you might as well have no evidence; no brain and no eyes.

[^note-bayes]: If any of this sounds at all confusing, see my discussion of Bayesian updating toward the end of _The Machine in the Ghost_, the third volume of [_Rationality: From AI to Zombies_](https://lesswrong.com/rationality).
