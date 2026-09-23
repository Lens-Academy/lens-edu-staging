---
title: "Hard problem of corrigibility"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/hard-problem-of-corrigibility"
published: 2017-10-11
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "The \"hard problem of corrigibility\" is to build an agent which, in an intuitive sense, reasons internally as if from the programmers' external perspective."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

The "hard problem of [corrigibility](https://www.lesswrong.com/w/corrigibility)" is to build an agent which, in an intuitive sense, reasons internally as if from the programmers' external perspective. We think the AI is incomplete, that we might have made mistakes in building it, that we might want to correct it, and that it would be e.g. dangerous for the AI to take large actions or high-impact actions or do weird new things without asking first. We would ideally want the agent to _see itself in exactly this way_, behaving as if it were thinking, "I am incomplete and there is an outside force trying to complete me, my design may contain errors and there is an outside force that wants to correct them and this a good thing, my expected utility calculations suggesting that this action has super-high utility may be dangerously mistaken and I should run them past the outside force; I _think_ I've done this calculation showing the expected result of the outside force correcting me, but maybe I'm mistaken about _that._"

This is not a default behavior; ordinarily, by the standard problems of [corrigibility](https://www.lesswrong.com/w/corrigibility), an agent that we've accidentally built to maximize paperclips (or smiles, etcetera) will not want to let us modify its utility function to something else. If we try to build in analogues of 'uncertainty about the utility function' in the most simple and obvious way, the result is an agent that [sums over all this uncertainty and plunges straight ahead on the maximizing action](https://www.lesswrong.com/w/problem-of-fully-updated-deference). If we say that this uncertainty correlates with some outside physical object (intended to be the programmers), the default result in a sufficiently advanced agent is that you disassemble this object (the programmers) to learn everything about it on a molecular level, update fully on what you've learned according to whatever correlation that had with your utility function, and plunge on straight ahead.

None of these correspond to what we would intuitively think of as being corrigible by the programmers; what we want is more like something analogous to humility or philosophical uncertainty. The way we want the AI to reason is the internal conjugate of our external perspective on the matter: maybe the formula you have for how your utility function depends on the programmers is _wrong_ (in some hard-to-formalize sense of possible wrongness that isn't just one more kind of uncertainty to be summed over) and the programmers need to be allowed to actually observe and correct the AI's behavior, rather than the AI extracting all updates implied by its current formula for moral uncertainty and then ignoring the programmers.

The "hard problem of corrigibility" is interesting because of the possibility that it has a _relatively simple_ core or central principle - rather than being [value-laden](https://www.lesswrong.com/w/value-laden) on the details of exactly what humans [value](https://www.lesswrong.com/w/value), there may be some compact core of corrigibility that would be the same if aliens were trying to build a corrigible AI, or if an AI were trying to build another AI. It may be possible to design or train an AI that has all the corrigibility properties in one central swoop - an agent that reasons as if it were incomplete and deferring to an outside force.

"Reason as if in the internal conjugate of an outside force trying to build you, which outside force thinks it may have made design errors, but can potentially correct those errors by directly observing and acting, if not manipulated or disassembled" might be one possibly candidate for a _relatively_ simple principle like that (that is, it's simple compared to the [complexity of value](https://www.lesswrong.com/w/complexity-of-value)). We can imagine, e.g., the AI imagining itself building a sub-AI while being prone to various sorts of errors, asking how it (the AI) would want the sub-AI to behave in those cases, and learning heuristics that would generalize well to how _we_ would want the _AI_ to behave if it suddenly gained a lot of capability or was considering deceiving its programmers and so on.

If this principle is not so simple as to formalizable and formally sanity-checkable, the prospect of relying on a trained-in version of 'central corrigibility' is unnerving even if we think it _might_ only require a manageable amount of training data. It's difficult to imagine how you would test corrigibility thoroughly enough that you could knowingly rely on, e.g., the AI that seemed corrigible in its infrahuman phase not [suddenly](https://www.lesswrong.com/w/context-disaster) developing [extreme](https://www.lesswrong.com/w/edge-instantiation) or [unforeseen](https://www.lesswrong.com/w/unforeseen-maximum) behaviors when the same allegedly simple central principle was reconsidered at a higher level of intelligence - it seems like it should be unwise to have an AI with a 'central' corrigibility principle, but not lots of particular corrigibility principles like a [reflectively consistent suspend button](https://www.lesswrong.com/w/shutdown-problem) or [conservative planning](https://www.lesswrong.com/w/conservative-concept-boundary). But this 'central' tendency of corrigibility might serve as a second line of defense.
