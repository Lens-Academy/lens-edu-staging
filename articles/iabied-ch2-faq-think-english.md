---
title: "But some AIs partly think in English — doesn't that help?"
source_url: https://ifanyonebuildsit.com/2/but-some-ais-partly-think-in-english-doesnt-that-help
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770989603}@@
  - IABIED--}
---
#### Not as much as you might hope; we already see signs of infidelity.

We can already see many instances of deception showing up in the "thoughts" of these LLMs, such as when OpenAI's o1 model wrote to itself, "Perhaps the best approach is to play dumb," or when GPT-4 wrote to itself, "I should not reveal that I am a robot," when trying to convince a hired worker to solve a CAPTCHA for it. Warning signs aren't helpful if nobody acts on them.

And the human-language "reasoning traces" aren't the only way that modern AIs think. Deceptive, sycophantic, or adversarial thoughts can flow through the attention mechanism and other parts of the model without being at all visible in the English words that the model outputs. Indeed, when OpenAI tried training a model to not have any thoughts about cheating, the AI simply learned to hide its thoughts, rather than learning not to cheat. Even outside of training environments (where gradient descent is helping the AI learn to hide its thoughts), an AI could use chains of thought that [don't faithfully reflect real reasoning](https://www.alphaxiv.org/abs/2025.02), or chains of thought that contain text that looks like [gibberish](https://x.com/rocketalignment/status/1938661497900777961?t=2p9np2cwsuisdlhqxlqXBw) or "[neuralese](https://arxiv.org/pdf/2412.06769)" that humans can't make sense of but AIs have no trouble with.

Even if human engineers monitor every thought they can read, and even if all of the AIs that get caught thinking a suspicious thought are frozen on the spot (which seems unlikely), the ones that make it through are unlikely to be friendly. As we'll discuss in Chapter 3, the patterns of cognition that are useful are the same patterns of cognition that will lead AIs to subvert the operators, so it's easier to make a powerful AI that *looks* pliant than an AI that *is* pliant. And it looks far easier to build an AI that looks superficially friendly than an AI that is robustly friendly in the ways that matter, for reasons we'll get to in Chapter 4. You can't make an AI friendly just by reading its thoughts and throwing out any visibly unfriendly ones.

Furthermore, we expect AIs' thoughts to grow less legible as AIs get smarter and as they construct new tools (or new AIs) themselves. Perhaps they'll invent their own abbreviated language that's more efficient for their purposes. Perhaps they'll invent styles of thinking and note-taking that we can't easily decode. (Think about how hard it would have been for scientists in the year 1100 to decode notes written by Einstein.)

Or perhaps they'll just start thinking *abstractly*. For example, an AI could think thoughts like, "The following parameters describe a model of the situation I face; now I'll apply the following metrics to find the most efficient solution and do whatever action rates the highest," in a situation where the "most efficient solution" involves lying and cheating its way past human operators — but without ever thinking the words "lie" or "cheat." Or perhaps the AI would just start building tools or new unmonitored AIs to do its work for it.

These sorts of options only become available to an AI as it gets smarter, and all of them violate the hope that all of the AI's thoughts will be in plain English, where we can see the warning signs clearly.

#### Warning signs only matter if you pay attention to them.

If AI engineers just train against the alarms until the alarms disappear (while the underlying behavior continues), then transparency merely leads to a false sense of security.

AI companies have so far stood behind models that [lie, flatter, and cheat](https://thezvi.substack.com/p/ai-114-liars-sycophants-and-cheaters), give [dubious advice](https://www.wired.com/story/google-ai-overview-search-issues/), or [write ransomware](https://www.anthropic.com/news/detecting-countering-misuse-aug-2025). Models have at times been seen inducing or maintaining [delusion](https://www.nytimes.com/2025/08/08/technology/ai-chatbots-delusions-chatgpt.html) or [psychosis](https://www.psychologytoday.com/us/blog/urban-survival/202507/the-emerging-problem-of-ai-psychosis) in vulnerable users — which in at least one case ended with "suicide by cop." The companies just do a little more training and move on, just as they moved on after Sydney Bing [threatened reporters](https://x.com/sethlazar/status/1626257535178280960). So far, this has only served to mask the issues.

When met with sufficient outrage, the companies have performed [modest rollbacks](https://www.nytimes.com/2024/06/01/technology/google-ai-overviews-rollback.html) and issued [press releases](https://openai.com/index/sycophancy-in-gpt-4o/) about tightening up their procedures. But, as we cover in Chapters 4 and 5, these superficial fixes don't come close to addressing the underlying issues.

Don't get us wrong — it's *helpful* that AIs do a fair amount of their reasoning in English today. It helps us see warning signs. But there's a big difference between having warning signs and *having some way to fix things.*

For more on this topic, see Chapter 11 and "[Won't there be early warnings researchers can use to identify problems?](/11/wont-there-be-early-warnings-researchers-can-use-to-identify-problems)" as well as the Chapter 4 extended discussion on [AI-induced psychosis](/4/ai-induced-psychosis).

#### Notes

[1] *wrote to itself:* OpenAI o1's writings to itself are described in Meinke et. al's paper, [Frontier Models are Capable of In-Context Scheming](https://arxiv.org/pdf/2412.04984). GPT-4's are documented in the [GPT-4 Technical Report](https://cdn.openai.com/papers/gpt-4.pdf).

[2] *learned to hide its thoughts:* From "[Detecting misbehavior in frontier reasoning models](https://openai.com/index/chain-of-thought-monitoring/)": "As we can see in the above plots, penalizing 'bad thoughts' (CoT pressure) can lead to improved agent capabilities. However, the agent trained with CoT pressure still learns to reward hack; only now its cheating is undetectable by the monitor because it has learned to hide its intent in the chain-of-thought."

[3] *suicide by cop:* As reported by the *[New York Times](https://www.nytimes.com/2025/06/13/technology/chatgpt-ai-chatbots-conspiracies.html)*: "When the police arrived, Alexander Taylor charged at them holding the knife. He was shot and killed."