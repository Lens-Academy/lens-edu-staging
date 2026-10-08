---
title: "Reflectively consistent degree of freedom"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/reflectively-consistent-degree-of-freedom"
published: 2016-03-09
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "A \"reflectively consistent degree of freedom\" is when a self-modifying AI can have multiple possible properties Xi∈X such that an AI with property X1 wants to go on being an AI with property X1, and an AI with X2 will ceteris paribus only choose to self-modify into designs that are also X2, etcetera. The archetypal reflectively consistent degree of freedom is a Humean degree of freedom, the refective consistency of many different possible utility functions. If Gandhi doesn't want to kill you, and you offer Gandhi a pill that makes him want to kill people, then Gandhi will refuse the pill, because he knows that if he takes the pill then pill-taking-future-Gandhi will kill people, and the current Gandhi rates this outcome low in his preference function. Similarly, a paperclip maximizer wants to remain a paperclip maximizer. Since these two possible preference frameworks are both consistent under reflection, they constitute a \"reflectively consistent degree of freedom\" or \"reflective degree of freedom\". From a design perspective, or the standpoint of an AI safety mindset, the key fact about a reflectively consistent degree of freedom is that it doesn't automatically self-correct as a result of the AI trying to improve itself. The problem \"Has trouble understanding General Relativity\" or \"Cannot beat a human at poker\" or \"Crashes on seeing a picture of a dolphin\" is something that you might expect to correct automatically and without specifically directed effort, assuming you otherwise improved the AI's general ability to understand the world and that it was self-improving. \"Wants paperclips instead of eudaimonia\" is not self-correcting. Another way of looking at it is that reflective degrees of freedom describe information that is not automatically extracted or learned given a sufficiently smart AI, the way it would automatically learn General Relativity. If you have a concept whose borders (membership condition) relies on knowing about General Relativity, then when"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

A "reflectively consistent degree of freedom" is when a self-modifying AI can have multiple possible properties $X_i \in X$ such that an AI with property $X_1$ wants to go on being an AI with property $X_1$, and an AI with $X_2$ will ceteris paribus only choose to self-modify into designs that are also $X_2$, etcetera.

The archetypal reflectively consistent degree of freedom is a [Humean degree of freedom](https://www.lesswrong.com/w/humean_freedom), the refective consistency of many different possible [utility functions](https://www.lesswrong.com/w/utility-function). If Gandhi doesn't want to kill you, and you offer Gandhi a pill that makes him want to kill people, then [Gandhi will refuse the pill](https://www.lesswrong.com/w/gandhi_stability_argument), because he knows that if he takes the pill then pill-taking-future-Gandhi will kill people, and the current Gandhi rates this outcome low in his preference function. Similarly, a [paperclip maximizer](https://www.lesswrong.com/w/paperclip-maximizer) wants to remain a paperclip maximizer. Since these two possible preference frameworks are both [consistent under reflection](https://www.lesswrong.com/w/71), they constitute a "reflectively consistent degree of freedom" or "reflective degree of freedom".

From a design perspective, or the standpoint of an [AI safety mindset](https://www.lesswrong.com/w/ai-safety-mindset), the key fact about a reflectively consistent degree of freedom is that it doesn't automatically self-correct as a result of the AI trying to improve itself. The problem "Has trouble understanding General Relativity" or "Cannot beat a human at poker" or "Crashes on seeing a picture of a dolphin" is something that you might expect to correct automatically and without specifically directed effort, assuming you otherwise improved the AI's general ability to understand the world and that it was self-improving. "Wants paperclips instead of eudaimonia" is _not_ self-correcting.

Another way of looking at it is that reflective degrees of freedom describe information that is not automatically extracted or learned given a sufficiently smart AI, the way it would automatically learn General Relativity. If you have a concept whose borders (membership condition) relies on knowing about General Relativity, then when the AI is sufficiently smart it will see a simple definition of that concept. If the concept's borders instead rely on [value-laden](https://www.lesswrong.com/w/value-laden) judgments, there may be no algorithmically simple description of that concept, even given lots of knowledge of the environment, because the [Humean degrees of freedom](https://www.lesswrong.com/w/humean_freedom) need to be independently specified.

Other properties besides the preference function look like they should be reflectively consistent in similar ways. For example, [son of CDT](https://www.lesswrong.com/w/son-of-cdt) and [UDT](https://www.lesswrong.com/w/udt) both seem to be reflectively consistent in different ways. So an AI that has, from our perspective, a 'bad' decision theory (one that leads to behaviors we don't want), isn't 'bugged' in a way we can rely on to self-correct. (This is one reason why MIRI studies decision theory and not computer vision. There's a sense in which mistakes in computer vision automatically fix themselves, given a sufficiently advanced AI, and mistakes in decision theory don't fix themselves.)

Similarly, [Bayesian priors](https://www.lesswrong.com/w/prior) are by default consistent under reflection - if you're a Bayesian with a prior, you want to create copies of yourself that have the same prior or [Bayes-updated](https://www.lesswrong.com/w/bayesian-update) versions of the prior. So 'bugs' (from a human standpoint) like being [Pascal's Muggable](https://wiki.lesswrong.com/wiki/Pascal's_mugging) might not automatically fix themselves in a way that correlated with sufficient growth in other knowledge and general capability, in the way we might expect a specific mistaken belief about gravity to correct itself in a way that correlated to sufficient general growth in capability. (This is why MIRI thinks about [naturalistic induction](https://www.lesswrong.com/w/naturalistic-induction) and similar questions about prior probabilities.)
