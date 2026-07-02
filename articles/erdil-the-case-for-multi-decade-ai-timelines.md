---
title: "The case for multi-decade AI timelines"
author:
  - "Ege Erdil"
source_url: "https://epoch.ai/gradient-updates/the-case-for-multi-decade-ai-timelines"
published: 2026-07-02
created: 2026-07-02
accessed: 2026-07-02
description: "In this Gradient Updates weekly issue, Ege discusses the case for multi-decade AI timelines."
tags:
  - "article-importer"
---

The date at which transformative AI capabilities will be reached is among the most discussed questions about AI. Opinions vary widely, with industry insiders typically expecting far faster progress than external observers. For instance, Dario Amodei [thinks](https://arstechnica.com/ai/2025/01/anthropic-chief-says-ai-could-surpass-almost-all-humans-at-almost-everything-shortly-after-2027/) there might be only 2 to 3 years left until AI surpasses “almost all humans at almost everything”, while economists such as William Nordhaus still believe we might have more than 100 years left.

Compared to most people in the world, my own median timelines of ~ 20 years until full automation of remote work would be considered quite aggressive. However, most people in the field of AI (and even many others at Epoch) have much shorter timelines than this, and timelines on the order of 1 to 10 years, as seen in the recent [AI 2027 report](https://ai-2027.com/), are often seen as a “default position” that one has to present arguments against. In this issue, I’ll elaborate on the key reasons behind my relatively bearish views. I’ll first explain why I find some common short timelines arguments unconvincing, then elaborate on how I arrive at the specific number of 20 years as a median estimate for how long we have until full automation of remote work.

I would summarize the key cruxes that separate my views from people who have shorter timelines as follows:

-   I don’t see the trends that one would extrapolate in order to arrive at very short timelines on the order of a few years. The obvious trend extrapolations for AI’s economic impact give timelines to full remote work automation of around a decade, and I expect these trends to slow down by default.
    
-   I don’t buy the software-only singularity as a plausible mechanism for how existing rates of growth in AI’s real-world impact could suddenly and dramatically accelerate by an order of magnitude, mostly because I put much more weight on bottlenecks coming from experimental compute and real-world data. This kind of speedup is essential to [popular accounts](https://www.forethought.org/research/preparing-for-the-intelligence-explosion) of why we should expect timelines much shorter than 10 years to remote work automation.
    
-   I think intuitions for how fast AI systems would be able to think and how many of them we would be able to deploy that come from narrow writing, coding, or reasoning tasks are very misguided due to [Moravec’s paradox](https://epoch.ai/gradient-updates/moravec-s-paradox). In practice, I expect AI systems to become slower and more expensive as we ask them to perform agentic, multimodal, and long-context tasks. This has already been happening with the rise of AI agents, and I expect this trend to continue in the future.
    

I still think full automation of remote work in 10 years is plausible, because it’s what we would predict if we straightforwardly extrapolate current rates of revenue growth and assume no slowdown. However, I would only give this outcome around 30% chance.

![newsletter-icon](https://epoch.ai/assets/icons/paper-plane.svg)

Get the latest from Epoch AI [Subscribe](https://epochai.substack.com/subscribe)

## Trend extrapolations don’t point towards short timelines

Probably the most common argument I hear for short timelines is that there’s been a lot of AI progress over the past five years, and relative to that it doesn’t seem like there’s much left until AI becomes capable of automating all remote work tasks in the economy. This is implicitly a trend extrapolation argument: it’s based on measuring some kind of “speed of progress”, or trend slope, and saying that the distance we have left until some threshold is small enough to be crossed in a short time.

Once put in this way, the problem with this argument becomes obvious: which trend do we extrapolate? There’s no benchmark which captures the ability of AI systems to automate remote work, and looking at a variable such as “labor share of the US economy” would give timelines on the order of a century or longer. The actual trend people seem to want to extrapolate is some measure of “intelligence” or “impressiveness”, but it’s very unclear how impressive a system has to become in this subjective sense before it’s actually able to do most or all remote work tasks in the economy.

I think revenue trends are probably the most reliable to look at, and out of these, NVIDIA’s revenue is probably the best: it’s a public company so we have quarterly filings, and it covers not just AI labs but also large tech companies and other purchasers of datacenter GPUs. However, before we can do this trend extrapolation, we need to know which level of revenues would correspond to full automation of remote work.

We can estimate this roughly as follows: in the US, [the labor share of GDP](https://fred.stlouisfed.org/series/LABSHPUSA156NRUG) is around 60%, and per [Dingel and Neiman (2020)](https://www.nber.org/papers/w26948) jobs that can be done from home account for 46% of US wages, so remotable jobs account for around $7.4T/yr of wages in the US. The US represents around a quarter of gross world product, so a naive estimate of the wage bill of remotable work worldwide would multiply this by four and arrive at $30T/yr. If we adjust this number down to account for most of the world having fewer remotable jobs as a fraction of their wage bill compared to the US, a number such as $20T/yr seems reasonable.

If we use this estimate as our revenue threshold for remote work automation, then a naive geometric extrapolation of NVIDIA’s revenue gives 7-8 year timelines to remote work automation:

![](https://epoch.ai/assets/images/gradient-updates/2025/the-case-for-multi-decade-ai-timelines/nvidia-datacenter-revenue-projections.png)

Of course, this assumes no slowdown in revenue growth, which is unrealistic. In practice, NVIDIA’s revenue growth has been linear since the ChatGPT moment in 2023 Q1, roughly at a rate of $20B additional annualized revenue every quarter. Extrapolating this linear trend gives remote work automation timelines on the order of centuries, which I think is clearly too pessimistic for reasons I elaborate on in a later section. However, I do think the linear trend since 2023 Q1, together with a general prior that revenue growth this aggressive usually slows down as revenues go up, is a reason to expect timelines substantially longer than 8 years.

Just as one example of how aggressive revenue growth can suddenly slow down, the aggregate revenue of Internet companies worldwide doubled every year on average from 1990 to 2000, but this growth slowed down by 10x following the end of the dotcom boom. Revenues went from < $1B/yr in 1990 to $800B/yr [in 2000](https://archive.is/ArdtB), but today are less than $10T/yr worldwide. Once inflation is taken into account, we’ve seen at most two more real doublings since 2000 compared to the ten doublings we’ve seen in the 1990s.

As a result, I think what seems most plausible for the overall revenue of the AI industry is the intermediate forecast shown in the plot above: unlike linear growth which has growth rates fall in half for each doubling, this trend has them fall only by around 30% per doubling. The exact figure of 30%, while important for the date we would predict for remote work automation, is not load-bearing for the conclusion that we should have multi-decade AI timelines: anything pricing in some slowdown on top of the exponential trend would yield this conclusion.

The case for AI revenue growth not slowing down at all, or perhaps even accelerating, rests on the feedback loops that would be enabled by human-level or superhuman AI systems: short timelines advocates usually emphasize software R&D feedbacks more, while [I think](https://epoch.ai/blog/explosive-growth-from-ai-a-review-of-the-arguments) the relevant feedback loops are more based on broad automation and reinvestment of output into capital accumulation, chip production, productivity improvements, et cetera.

Because my views on why the AI industry won’t fall victim to the same economic bottlenecks that halted the dotcom boom depend crucially on AI-driven automation being broad-based, I don’t expect substantial acceleration of existing economic or algorithmic progress trends until much of the economy has already been automated. This is a key consideration that sets my views apart from many people who believe in shorter timelines such as the authors of the [AI 2027 report](https://ai-2027.com/).

## A software singularity is unlikely

As discussed earlier, the software-only singularity plays a central role in many short timelines projections. The idea is that AI will become superhuman at coding and R&D significantly before it becomes superhuman at remote work tasks in general, and once this happens it will be able to automate its own software R&D. This will then lead to a “foom” scenario in which better software leads to more and smarter AIs which further speeds up algorithmic progress by increasing the effective supply of researchers. Because AI systems are already relatively good at coding and reasoning, narrowly conceived, this means we only need a little bit more progress before this feedback loop can commence.

I find this scenario unlikely for several reasons:

-   It underrates the difficulty of automating the job of a researcher. Real world work environments are messy and contain lots of detail that are neglected in an abstraction purely focused on writing code and reasoning about the results of experiments. As a result, we shouldn’t expect automating AI R&D to be much easier than automating remote work in general.
    
-   Software R&D in AI seems bottlenecked by experimental compute and data as well as cognitive research effort. If we were to simply scale up cognitive effort by many orders of magnitude while leaving other factors mostly untouched, these bottlenecks would probably become binding and any potential singularity would fizzle out.
    
-   I think our understanding of the concept of “software efficiency” in AI is quite poor, despite having been personally involved in [several](https://epoch.ai/blog/revisiting-algorithmic-progress) [projects](https://epoch.ai/blog/algorithmic-progress-in-language-models) aimed at estimating how fast said efficiency has been improving.
    
    The main issue is that typical abstractions assume that software efficiency is a multiplier that uniformly reduces training or inference costs across all levels of capability, but in practice most important software innovations appear to not only require experimental compute to discover, but they also appear to only work at large compute scales while being useless at small ones. So there’s no reason to expect “software progress” to continue at anything like current rates if we become bottlenecked by compute scaling.
    

These arguments are not very strong, and a software-only singularity [looks about as likely as not](https://epoch.ai/blog/do-the-returns-to-software-rnd-point-towards-a-singularity) conditional on them failing, so I would still assign a ~ 10% chance to algorithmic progress in AI accelerating tenfold with compute stocks not growing by more than 2x for at least a few consecutive months over the next decade. It’s just hard to be convinced in a domain where the key questions about the complexity of the job of a researcher and the complementarity between cognitive and compute/data inputs remain unanswered.

While a software-only singularity seems more speculative, I still think something like a [broader economic singularity](https://epoch.ai/blog/explosive-growth-from-ai-a-review-of-the-arguments) from AI automation is quite plausible. The difference between my view and the software singularity is that I think we need to scale up compute and data alongside pure cognitive research effort in order to sustain rapid progress in AI capabilities. This can’t be done by simulated AI researchers in a single datacenter alone, but it’s quite feasible if the entire world economy starts growing much more rapidly as a result of broad AI automation. Because such an acceleration can only begin when AI systems have already broadly automated the economy, it’s not a reason to expect our timelines to full automation of remote work to become much shorter than they would otherwise be.

## AI agents will need a lot of compute to automate all remote work

I also find short timelines advocates bullish when it comes to how efficiently they believe AI will be able to convert inference compute into economic value or real-world impact, at least immediately after general AI systems are developed. My expectation is that these systems will initially either be on par with or worse than the human brain at turning compute into economic value at scale, and I also don’t expect them to be much faster than humans at performing most relevant work tasks.

This might seem like an unreasonable claim because we “know” that whenever AI systems become able to do a task, they very quickly become able to do that task for way cheaper and faster than humans can. However, I would argue that this line of reasoning ignores two crucial points:

-   Empirically, the cost and time gap of AIs performing tasks that have been automated recently and humans performing the same tasks has been shrinking. This has recently shown up in the form of reasoning models and agents which need to generate many reasoning tokens for each final token of their answer or each individual action that they take. These models are so hungry for compute that inference tokens are arguably more bottlenecked by supply rather than demand right now.
    
-   In theory, we should expect AI systems to become vastly more efficient than human brains easily on tasks which the human brain has not been optimized to perform well: this is the lesson of [Moravec’s paradox](https://epoch.ai/gradient-updates/moravec-s-paradox). However, as AIs become capable of automating more tasks humans can do, their cost and speed advantage on the marginal tasks will gradually diminish. In line with this view, computers might be billions of times faster than humans at arithmetic, but they are only 1000x faster at translation, and less than 10x faster at more agentic tasks such as the ones performed by OpenAI’s Deep Research.
    

Given that AI models still remain less sample efficient than humans, these two points lead me to believe that for AI models to automate all remote work, they will initially need at least as much inference compute as the humans who currently do these remote work tasks are using. So a natural point at which to expect this to happen is when the aggregate inference compute of all AI systems in the world exceeds the aggregate compute we think is happening in human brains across the world.

In 20 years, if [present trends in GPU price-performance](https://epoch.ai/data-insights/price-performance-hardware) continue, we’ll have 16-bit FLOP costs around 3e20 FLOP/$, and with a generous annual spending of $10T/yr on datacenter compute this could buy us a total of 1e26 FLOP/s of datacenter throughput, around ten times greater than what we might [estimate](https://www.openphilanthropy.org/research/how-much-computational-power-does-it-take-to-match-the-human-brain/) for the computational power of all human brains worldwide at 1e15 FLOP/s per brain. $10T/yr is an enormous amount of investment, and it is unclear whether we should expect AIs to be more or less software efficient across the board compared to human brains, so I think this is a good default point to expect AI work to overtake human work in economic importance.

For context, in 2024 we spent ~ $100B on NVIDIA GPUs, and by 2024 Q4 the [total computing power](https://epoch.ai/data-insights/nvidia-chip-production) of all NVIDIA datacenter chips worldwide was only around 4e21 FLOP/s. Overall, our inference budgets remain tiny compared to the total amount of computational power of human brains worldwide.

A plausible counterargument to this view is that it ignores the substantial advantages AI workers would have over humans, many of which I’ve myself written about in the past. For instance, the [train once, deploy many](https://epoch.ai/blog/train-once-deploy-many-ai-and-increasing-returns) property of AI systems gives them an additional source of increasing returns to scale that humans lack access to, and one could also argue that AIs will be more productive than humans simply because we will only use our limited inference-time budgets to substitute for the most productive workers in the world economy instead of the average worker.

These are certainly reasons to expect AI workers to become more productive than humans per FLOP spent in the long run, perhaps after most of the economy has already been automated. However, in the short run the picture looks quite different: while these advantages already exist today, they are not resulting in AI systems being far more productive than humans on a revenue generated per FLOP spent basis.

The global supply of datacenter compute is currently in the low millions of H100 equivalents, and the global revenue of the AI industry is probably on the order of low tens of billions of dollars per year. The implied revenue per H100 equivalent is only ~ $10K/year, which is roughly in line with gross world product per capita. AI systems are simply not being orders of magnitude more productive than the typical human worker.

In fact, the revenue generated by AI systems per H100 equivalent has also not grown since the ChatGPT moment despite the dramatically increased capabilities of AI systems since then: all the revenue growth in the industry has corresponded to a scaling up of the supply of inference compute so that revenue per H100 equivalent has remained fairly constant. This raw fact is partly why OpenAI [doesn’t expect](https://www.reuters.com/technology/artificial-intelligence/openai-does-not-expect-be-cash-flow-positive-until-2029-bloomberg-news-reports-2025-03-26/) to be cash flow positive until 2029.

I believe this will change in the future when AIs automate the entire economy and kickstart the feedback loops leading to [explosive economic growth](https://epoch.ai/blog/explosive-growth-from-ai-a-review-of-the-arguments), which will rapidly increase all key inputs going into AI capabilities, but until then I see no reason to expect a dramatic increase in revenue generated per H100 equivalent. In fact, I wouldn’t be surprised if we saw a decrease in this number by the end of the decade.

## Conclusion

Overall, my basic argument for multi-decade AI timelines is that geometric extrapolation of current revenue trends should lead us to expect full automation of remote work in around 8 years, and I see plenty of reason to expect these trends to slow down significantly and relatively little reason to expect them to speed up. Given past examples of similarly rapidly growing industries experiencing slowdowns, and the falling growth rates that are already visible in NVIDIA’s quarterly reports, I would be surprised by a world in which the revenue of the AI industry just keeps doubling every year or more for the next 8 years.
