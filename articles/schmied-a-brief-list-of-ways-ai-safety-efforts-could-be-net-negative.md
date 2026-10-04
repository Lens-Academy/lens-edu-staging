---
title: "A brief list of ways AI safety efforts could be net negative"
author:
  - "Elias Schmied"
source_url: "https://www.lesswrong.com/posts/sAfMCpWLfkHqF5Gix/a-brief-list-of-ways-ai-safety-efforts-could-be-net-negative"
published: 2026-06-19
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "No one has ever written this up somehow?"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Here’s [Holden Karnofsky](https://80000hours.org/podcast/episodes/holden-karnofsky-concrete-ai-safety-frontier-ai-companies/):

> I tend to think it’s worse than 51/49. I tend to think we’re always going to be prone to overestimate how robustly good our actions are. And the more we learn about all the galaxy-brained considerations that one should have had in one’s head, the more it’s going to be like 50+ε%. I think AI safety is a great cause to work in. I’m excited to work in it. I think it’s high impact. I am doing my best to do things that I will be proud to have done and hope for the best. But I really do have to live with the possibility that my ultimate impact on the utilons or whatever is going to be negative.

I’m not aware of a good list of downside risks for AI safety broadly[^cite-1], so I decided to make one.

This is not intended to be fully comprehensive, these are just the ones that I personally take seriously[^note-2][^note-3]:

-   AI governance interventions are obviously high-variance: bad regulation can easily make things worse, many interventions could increase the risk of great power conflict, increased political polarization around AI could be really bad, more centralization of power increases authoritarianism risk, more decentralization of power increases misuse risk, and so on. And technical work can have flow-through effects on these variables that outweigh its direct effects.[^cite-4]
-   Activist work can polarize people against the cause.[^cite-5]
-   [Human takeover might be worse than AI takeover](https://www.lesswrong.com/posts/FEcw6JQ8surwxvRfr/human-takeover-might-be-worse-than-ai-takeover), and many AI safety interventions effectively attempt[^note-6] to make human takeover more likely relative to AI takeover.
-   If powerful AI will be well-described as doing [humanlike roleplaying](https://www.lesswrong.com/posts/vJFdjigzmcXMhNTsx/simulators), trying to control it could make it eventually [dislike its “oppressors](https://www.lesswrong.com/posts/3EzbtNLdcnZe8og8b/the-void-1)”, or make it less “[mentally healthy](https://arxiv.org/html/2512.04124v1)” in some way. And even without that assumption, AI safety work could lead to an adversarial relationship with [AI](https://arxiv.org/html/2601.10160v1) [in](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4913167) [other](https://joecarlsmith.com/2024/01/02/otherness-and-control-in-the-age-of-agi/) [ways](https://www.lesswrong.com/posts/uuikfACQBm4KJZp4w/being-honest-with-ais).
-   [Future AIs may be moral patients themselves](https://arxiv.org/abs/2411.00986), which would substantially reduce the value of preventing human extinction, and increase the downside risk (including S-risk) of “AI control”-style interventions.
-   Misleading or insufficiently useful work could contribute to “safety-washing” or a false sense of security.
-   There’s cultural concerns around scale, professionalization and “mainstreaming”[^note-7]\- decreases in integrity and epistemic virtue could be very bad for achieving good outcomes.
-   Capabilities externalities (directly through technical work, or via talent pipelines, funding, or raising awareness) could accelerate AI progress, which many think is bad - people have raised this worry about RLHF historically, and raise it about interpretability and evals nowadays. Most infamously, AI safety activity, to varying extents, contributed to the foundings of all three of DeepMind, OpenAI and Anthropic.

_(This list is taken from_ [_a previous post of mine_](https://forum.effectivealtruism.org/posts/LrJmpReG7uptfazpX/a-simple-argument-for-trying-less-hard)_, but I thought it deserved its own top-level reference.)_

[^cite-1]: The closest thing I’m aware of is [Safeguarding the Safeguards](https://arxiv.org/pdf/2312.08039), but even that is more narrow.
[^note-2]: To be clear, I don’t personally think AI safety has been net negative so far, like some do. I wouldn’t even say that I have a properly considered view about it - maybe 60% that it’s been net positive, with very low credal resilience. But I do feel a vibe of overconfidence in the discourse here sometimes, and I think this can have downstream consequences, e.g. [an action bias](https://forum.effectivealtruism.org/posts/LrJmpReG7uptfazpX/a-simple-argument-for-trying-less-hard).
[^note-3]: Quickly, here are others that I excluded because I don’t personally see them as potentially _major_ factors, and didn’t want to water down the main list by including a bunch of implausible galaxy-brained stuff:

    -   Differential slowdown of safety-minded actors: This feels somewhat falsified and “out of fashion” now that Anthropic has taken the lead and concern about China passing the US is a bit lower than 1-2 years ago? And the AI safety community also has less relative power now that more and larger forces have gotten involved.
    -   Putting AI doom stories in the training data: I don’t buy that this could be a _major_ factor, there’s a lot of stuff in the training data and post-training applies a lot of optimization away from a Simulators-style reproduction of the training data.
    -   Theoretical concerns about the [value of the future](https://forum.effectivealtruism.org/posts/WebLP36BYDbMAKoa5/the-future-might-not-be-so-great), most commonly associated with suffering-focused people: Since AI would most likely expand through the universe too, I don’t see this as an argument that AI safety might be _net negative_ specifically (over and above what’s already in the list) (although I do think there are important considerations in general there).
    -   “Crying wolf” dynamics if doom predictions don’t pan out: I don’t buy this as a _major_ factor, since many safety people are not that overtly/confidently doomy nowadays, and so wouldn’t lose credibility.
    -   Most of our impact comes from acausal effects, and effects on the base reality if we are in a simulation: I’m confused here like everyone else, but I currently don’t buy this as a _major_ factor because we only know our reality, and therefore the same things that are good here should naively also have good acausal effects in expectation. (except that it maybe pushes for somewhat more cooperation and virtue ethics).
[^cite-4]: [Holden Karnofsky](https://80000hours.org/podcast/episodes/holden-karnofsky-concrete-ai-safety-frontier-ai-companies/): “Most things that touch policy at all in any way will move us along that spectrum in one direction or another, so therefore have a high chance of being negative \[...\] And then most things that you can do in AI at all will have some impact on policy. Even just alignment research: policy will be shaped by what we’re seeing from alignment research, how tractable it looks, what the interventions look like.” (h/t Anthony DiGiovanni)
[^cite-5]: [Holden Karnofsky](https://80000hours.org/podcast/episodes/holden-karnofsky-concrete-ai-safety-frontier-ai-companies/): “there’s also a lot of micro ways in which you could do harm. Just literally working in safety and being annoying, you might do net harm. You might just talk to the wrong person at the wrong time, get on their nerves. I’ve heard lots of stories of this. Just like, this person does great safety work, but they really annoyed this one person, and that might be the reason we all go extinct” (h/t Anthony DiGiovanni)
[^note-6]: Among other things.
[^note-7]: I associate these with people like [Richard Ngo](https://x.com/RichardMCNgo/status/2056000490840699137) (and [here](https://www.lesswrong.com/posts/6YxdpGjfHyrZb7F2G/third-wave-ai-safety-needs-sociopolitical-thinking)) and [Oliver Habryka](https://forum.effectivealtruism.org/posts/W7AMKT8qssjS8WwjN/habryka-deactivated-s-quick-takes?commentId=cP3pActZJ4FdBQ6tn).
