---
title: "How quick and big would a software intelligence explosion be?"
author:
  - "Tom Davidson"
  - "Tom Houlden"
source_url: "https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be"
published: 2025-08-04
created: 2026-07-02
accessed: 2026-07-02
description: "Forethought paper modeling software intelligence explosion: 60% chance of >3 years progress in <1 year."
tags:
  - "article-importer"
---

4th August 2025

AI systems may soon fully automate AI R&D. [Eth & Davidson (2025)](https://www.forethought.org/research/will-ai-r-and-d-automation-cause-a-software-intelligence-explosion#article) argues that this could precipitate a _software intelligence explosion_ – a period of rapid AI progress due to AI improving AI software.

This paper extends this previous work and evaluates _how dramatic_ the software intelligence explosion will be. How fast will progress become? How much total progress will there be before the intelligence explosion fizzles out?

We think that **the software intelligence explosion will probably (~60%) compress >3 years of AI progress into <1 year, but is somewhat unlikely (~20%) to compress >10 years into <1 year.** That’s >3 years of _total_ AI progress at recent rates (from both compute and software), achieved solely through software improvements. If compute is still increasing during this time, as seems likely, that will drive additional progress.

The existing discussion on the “intelligence explosion” has generally split into those who are highly sceptical of intelligence explosion dynamics and those who anticipate _extremely_ rapid and sustained capabilities increases. Our analysis suggests an intermediate view: the software intelligence explosion will be a significant additional acceleration at just the time when AI systems are surpassing top humans in broad areas of science and engineering.

Like all analyses of this topic, this paper is necessarily speculative. We draw on evidence where we can, but the results are significantly influenced by guesswork and subjective judgement.

## Summary

### How the model works

We use the term _ASARA_ to refer to AI that can fully automate AI research (ASARA = “AI Systems for AI R&D Automation”). For concreteness, we define ASARA as AI that can replace every human researcher at an AI company with 30 equally capable AI systems each thinking 30X human speed.

We simulate AI progress after the deployment of ASARA.

We assume that half of recent AI progress comes from using _more compute_ in AI development and the other half comes from _improved software_. (“Software” here refers to AI algorithms, data, fine-tuning, scaffolding, inference-time techniques like o1 — all the sources of AI progress other than additional compute.) We assume compute is constant and only simulate software progress.

We assume that software progress is driven by two inputs: 1) _cognitive labour_ for designing better AI algorithms, and 2) _compute for experiments_ to test new algorithms. Compute for experiments is assumed to be constant. Cognitive labour is proportional to the level of software, reflecting the fact AI has automated AI research.

![Diagram showing AI improvement feedback loop: better AI leads to more cognitive labour and AI software progress, creating self-reinforcing cycle, while compute for experiments held constant](https://images.ctfassets.net/4owxfjx3z3if/7jOrA1byp7B6QFqoxt8gcW/726aae8614eb4ef03c9b6073fa7cc8a2/ai-feedback-loop-model-diagram.png?w=3840&q=85&fm=webp)

Our model holds compute fixed and simulates a feedback loop of AI improving AI software

## Image

So the feedback loop we simulate is: better AI → more cognitive labour for AI research → more AI software progress → better AI →...

The model has three key parameters that drive the results:

1.  **Initial speed-up.** When ASARA is initially deployed, how much faster is software progress compared to the recent pace of software progress?
    
2.  **Returns to software R&D.** After the initial speed-up from ASARA, does the pace of progress accelerate or decelerate as AI progress feeds back on itself?
    

-   a. This is given by the parameter r r. Progress accelerates if and only if r \> 1 r>1.
    
-   b. r r depends on 1) the extent to which software improvements [get harder to find](https://web.stanford.edu/~chadj/IdeaPF.pdf) as the low hanging fruit are plucked, _and_ 2) the strength of the “ [stepping on toes effect](https://www.researchgate.net/publication/334739032_Stepping_on_toes_in_the_production_of_knowledge_a_meta-regression_analysis) ” whereby there are diminishing returns to more researchers working in parallel.
    

3.  **Distance to “effective limits” on software.** How much can software improve after ASARA before we reach fundamental limits to the compute efficiency of AI software?
    

-   a. The model assumes that, as software approaches effective limits, the returns to software R&D become less favourable and so AI progress decelerates.
    

![Graph showing AI capabilities over time with three key model parameters: initial speed-up from automating AI research, whether progress accelerates after initial boost, and distance to effective limits](https://images.ctfassets.net/4owxfjx3z3if/4tzj2hWqfTMO0aTSCqddyq/3a69cc04d92748bfc80b216f51d65408/ai-progress-three-parameters-model.png?w=3840&q=85&fm=webp)

Diagram showing the meaning of the model’s three main parameters

## Image

The following table summarises our estimates of the three key parameters:

| **Parameter** | **Estimation methods** | **Values used in the model** |
| --- | --- | --- |
| **Initial speed-up** in software progress from deploying ASARA | \- Various surveys of AI researchers on the speed-ups from ASARA and the strength of compute bottlenecks.  
  
\- Listing and estimating the gains of specific things ASARA could do  
  
\- Applying a simple Cobb-Douglas model of software progress | Compared to progress in 2020-2024, software progress will be faster by a factor of **2 - 32, with a median of 8** |
| **Returns to software R&D**  
  
(After the initial speed-up, does progress accelerate or decelerate?) | \- Empirical evidence on growth of cognitive inputs to AI research and the pace of resultant software improvements  
  
\- Adjustments to this empirical evidence to account for compute bottlenecks and AI becoming smarter over time | The pace of software progress will **probably (~60%) accelerate over time** after the initial speed-up (at least initially).  
  
(We estimate 0.4 < r < 3.6 0.4<r<3.6, with a median of r \= 1.2 r=1.2) |
| **Distance to “effective limits” of AI software** | \- Estimating that if ASARA is trained with 1e28 FLOP, training efficiency could improve ~4 OOMs before matching that of human learning  
  
\- Listing and estimating plausible efficiency gains on top of human learning, e.g. from better data and better learning algorithms. This involves a fair amount of guesswork and is a massive remaining uncertainty. | **6 - 16 OOMs of efficiency gains** after ASARA before hitting effective limits  
  
This translates to 6-16 years worth of AI progress, because the [effective compute](https://futuretech.mit.edu/news/what-drives-progress-in-ai-trends-in-compute#:~:text=Compute%20progress%20means%20that%20AI,models%2C%20and%20explore%20innovative%20approaches.) for AI training has recently risen by [~10X/year](https://epoch.ai/trends) |

We put log-uniform probability distributions over the model parameters and run a Monte Carlo ([more](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#summary-of-parameter-assumptions)).

![Three-panel visualization showing model parameter estimates: initial ASARA speed-up (2x to 32x capabilities growth), acceleration probability (60% yes, 40% no), and efficiency improvement potential (6-16 OOMs from ASARA to limits)](https://images.ctfassets.net/4owxfjx3z3if/51RDay8nssAXgzrkkNsZCv/dd10ae4bd809cb8fdfe9c5c6b28b3d0c/model-parameter-estimates-visualization.png?w=3840&q=85&fm=webp)

Our assumptions about the model’s three key parameters

## Image

**You can enter your own inputs to the model on [this website](https://accelerated-ai-progress.streamlit.app/).**

### Results

Here are the model’s bottom lines (to 1 sig fig):

| **Years of progress** | **Compressed into ≤1 year** | **Compressed into ≤4 months** |
| --- | --- | --- |
| ≥3 years | ~60% | ~40% |
| ≥10 years | ~20% | ~10% |

![Probability curve showing likelihood of compressing AI progress into one year: 57% chance for 3+ years, 18% chance for 10+ years, with declining probability for more dramatic compression scenarios](https://images.ctfassets.net/4owxfjx3z3if/2d4Aj6IBHtLumZ4ZPcL5rW/c73d61e1de31cac6919e15d7671024ff/progress-compression-probability-curve.png?w=3840&q=85&fm=webp)

How many years of total AI progress will the software intelligence explosion compress into just one year?

## Image

Remember, the simulations conservatively assume that compute is held constant. They compare the pace of AI _software_ progress after ASARA to the recent pace of _overall_ AI progress, so “3 years of progress in 1 year” means “6 years of software progress in 1 year”.

While the exact numbers here are obviously not to be trusted, we find the following high-level takeaway meaningful: **averaged over one year, AI progress could easily be >3X faster, could potentially be >10X faster, but won’t be 30X faster absent a major paradigm shift.** In particular:

-   Initial speed-ups of >3X are likely, and the returns to software R&D are likely high enough to prevent progress slowing back down before there is 3 years of progress.
    
-   If effective limits are >10 OOMs away _and_ returns to software R&D remain favourable until we are close to those limits, progress can accelerate for long enough to get ten years of progress in a year. We think it’s plausible but unlikely that both these conditions hold.
    
-   To get 30 years of progress in one year, either you need extremely large efficiency gains on top of ASARA (30 OOMs!) or a major paradigm shift that enables massive progress without significant increases in effective compute (which seems more likely).
    

We also consider two model variants, and find that this high-level takeaway holds in both:

1.  **Retraining new models from scratch.** In this variant, some fraction of software progress is “spent” making training runs faster as AI progress accelerates. [More](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#retraining-time).
    
2.  **Gradual boost.** In this variant, we simulate a gradual increase in AI capabilities from today’s AI to ASARA, with software progress accelerating along the way. [More.](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#gradual-boost-from-pre-asara-systems)
    

### Discussion

If this analysis is right in broad strokes, how dramatic would the software intelligence explosion be?

There’s two reference points we can take.

One reference point is historical AI progress. It took three years to go from GPT-2 to ChatGPT (i.e. GPT-3.5); it took another three years to go from GPT-3.5 to o3. That’s a lot of progress to see in one year just from software. We’ll be _starting_ from systems that match top human experts in all parts of AI R&D, so we will end up with AI that is _significantly_ superhuman in many broad domains.

Another reference point is [effective compute](https://futuretech.mit.edu/news/what-drives-progress-in-ai-trends-in-compute#:~:text=Compute%20progress%20means%20that%20AI,models%2C%20and%20explore%20innovative%20approaches.). The amount of effective compute used for AI development has increased at roughly [10X/year](https://epoch.ai/trends). So, three years of progress would be a 1000X increase in effective compute; six years would be a million-fold increase. Ryan Greenblatt [estimates](https://redwoodresearch.substack.com/p/what-does-10x-ing-effective-compute?utm_source=post-email-title&publication_id=2318730&post_id=166749974&utm_campaign=email-post-title&isFreemail=true&r=jaafn&triedRedirect=true&utm_medium=email) that a million-fold increase might correspond to having 1000X more copies that think 4X faster and are _significantly_ more capable. In which case, _the software intelligence explosion could take us from **30,000 top-expert-level AIs each thinking 30X human speed** to **30 million superintelligent AI researchers each thinking 120X human speed**, with the capability gap between each superintelligent AI researcher and the top human expert about 3X as big as the gap between the top expert and a median expert._[1](#user-content-fn-1),[2](#user-content-fn-2)

### Limitations

Our model is extremely basic and has many limitations, including:

-   **Assuming AI progress follows smooth trends.** We don’t model the possibility that superhuman AI unlocks qualitatively new forms of progress that amount to a radical paradigm shift; nor the possibility that the current paradigm stops yielding further progress shortly after ASARA. So we’ll underestimate the size of the tails in both directions.
    
-   **No gears-level analysis.** We don’t model _how_ AIs will improve software in a gears-level way at all (e.g. via generating synthetic data vs by designing new algorithms). So the model doesn’t give us insight into these dynamics. Instead, we extrapolate high-level trends about how much research effort is needed to double the efficiency of AI algorithms. And we don’t model specific capabilities, just the amount of “effective training compute”.
    
-   **“Garbage in, garbage out”.** We’ve done our best to estimate the model parameters, but there are massive uncertainties in all of them. This flows right through to the results.
    
    -   This uncertainty is especially large for the “distance to effective limits” parameter.
        
    -   _You can choose your own inputs to the model [here](https://accelerated-ai-progress.streamlit.app/)!_
        
    
-   **No compute growth.** The simulation assumes that compute doesn’t grow at all after ASARA is deployed, which is obviously a conservative assumption.
    

Overall, **we think of this model as a back-of-the-envelope calculation**. It’s our best guess, and we think there are some meaningful takeaways, but we don’t put much faith in the specific numbers.

## Structure of the paper

The rest of the paper lays out our analysis in more detail. We proceed as follows:

## Relation to previous work

[Eth & Davidson (2025)](https://www.forethought.org/research/will-ai-r-and-d-automation-cause-a-software-intelligence-explosion#article) argue that a software intelligence explosion is plausible. They focus on estimating the returns to software R&D and argue they could allow for accelerating AI progress after ASARA is deployed. This paper builds on this work by doing more detailed quantitative modelling of the software intelligence explosion, especially the initial speed-up in progress due to ASARA and the distance to the effective limits of software. Both Eth and Davidson (2025) and this paper draw heavily on estimates from [Besiroglu et al. (2024)](https://epoch.ai/blog/do-the-returns-to-software-rnd-point-towards-a-singularity).

[Davidson (2023)](https://www.openphilanthropy.org/research/what-a-compute-centric-framework-says-about-takeoff-speeds/) (and its [online tool](https://takeoffspeeds.com/)) and [Davidson et al. (2025)](https://www.forethought.org/research/three-types-of-intelligence-explosion) model all inputs to AI progress including hardware R&D and increased compute spending. [Davidson (2023)](https://www.openphilanthropy.org/research/what-a-compute-centric-framework-says-about-takeoff-speeds/) also models the effects of partial automation. By contrast, this paper (and its own [online tool](https://accelerated-ai-progress.streamlit.app/)) more carefully models the dynamics of software progress after full automation.

[Kokotajlo & Lifland (2025)](https://ai-2027.com/research/takeoff-forecast) is the research supplement for AI-2027. They use a different methodology to forecast a software intelligence explosion, relying less on estimates of the returns to software R&D and more on estimates for how long it would take human researchers to develop superhuman AI without AI assistance. Their forecast is towards the more aggressive end of our range. A rough calculation suggests that our model assigns a ~20% probability to the intelligence explosion being faster than their median scenario.[3](#user-content-fn-3)

[Erdil & Barnett (2025)](https://epoch.ai/gradient-updates/most-ai-value-will-come-from-broad-automation-not-from-r-d) express scepticism about an software intelligence explosion lasting for more than one order of magnitude of algorithmic progress. By contrast, this paper predicts it will likely last for at least several orders of magnitude.

[Bostrom (2014)](https://en.wikipedia.org/wiki/Superintelligence:_Paths,_Dangers,_Strategies) is uncertain about the speed from human-level to superintelligent AI, but finds transitions of days or weeks plausible. By contrast, this paper’s forecasts are more conservative.

[Yudkowsky (2013)](https://intelligence.org/files/IEM.pdf) argues that there will be an intelligence explosion that lasts “months or years, or days or seconds”. It draws upon wide-ranging evidence from chess algorithms, human evolution, and economic growth. By contrast our paper focuses on recent evidence from modern machine learning.

## Scenario

We analyse a scenario in which:

-   ASARA is deployed internally within an AI developer to fully automate AI R&D.
    
-   There are no further human bottlenecks on the pace of progress – i.e. no pauses to help humans understand developments, ensure AI is developed safely, or assess legal risk.
    
-   After ASARA is deployed, the compute used for AI R&D remains constant over time.
    
-   Recent scaling laws on capabilities roughly continue: each doubling of effective compute for developing AI improves capabilities by the same amount as it has in recent years.
    

We forecast software progress _after_ ASARA is deployed (though a [variant](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#gradual-boost-from-pre-asara-systems) also simulates a gradual ramp-up to ASARA).

## Model dynamics

_(Readers can skip this section and go straight to the estimates of the parameter values.)_

The model simulates the evolution of AI software.

We start with the following standard [semi-endogenous](https://en.wikipedia.org/wiki/Jones_model) law of motion for AI software:

S ˙ (L,C) \= a \[R (L,C)\] λ S 1 − β (Software L.O.M) \\,\\dot{S}(L, C) = a\[R(L, C)\]^{\\lambda} S^{1-\\beta} \\qquad\\qquad\\qquad\\quad \\text{(Software L.O.M)} R (L,C) \= (b L) α (c C) 1 − α (Research Input) R(L, C) = (bL)^{\\alpha}(cC)^{1-\\alpha} \\qquad\\qquad\\qquad\\qquad\\;\\;\\, \\text{(Research Input)} L \= d S (Cognitive Labour) \\qquad\\;\\;\\, L = dS \\qquad\\qquad\\qquad\\qquad\\qquad\\qquad\\;\\, \\text{(Cognitive Labour)}

where:

-   S S is the level of AI software
    
-   L L is the cognitive labour used for improving software
    
-   C C is compute for experiments, assumed to be constant
    
-   λ \\lambda captures "stepping on toes", whereby there are diminishing returns to applying more research effort in parallel (nine women can't make a baby in a month!).
    
-   β (\> 0) \\beta (> 0) captures software improvements getting harder to find as software improves
    
-   α \\alpha captures the diminishing returns of cognitive labour to improving software
    
-   a a, b b, c c and d d are constants that are collectively pinned down by growth rates at the beginning of the model
    

Note that this model assumes that, in software R&D, the elasticity of substitution between cognitive labour and compute equals 1. This is an important assumption, discussed further [here](https://www.forethought.org/research/will-compute-bottlenecks-prevent-a-software-intelligence-explosion) and [here](https://forum.effectivealtruism.org/posts/xoX936hEvpxToeuLw/estimating-the-substitutability-between-compute-and).

From these equations we [derive](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#derivation-of-our-pseudo-code-from-the-semi-endogenous-growth-model) how much faster (or slower) each successive doubling of software is compared to the last:

Doubling Time (2 S,C) \= Doubling Time (S,C) × 2 β − λ α \\text{Doubling Time}(2S, C) = \\text{Doubling Time}(S,C) \\times 2^{\\beta - \\lambda \\alpha}

To reduce the number of distinct parameters and use parameters that can be directly estimated from the empirical evidence we have, we write this as:

Doubling Time (2 S,C) \= Doubling Time (S,C) × 2 p (1 r − 1) \\text{Doubling Time}(2S, C) = \\text{Doubling Time}(S,C) \\times 2^{p(\\frac{1}{r}-1)}

where p p and r r are _deflated_ stepping on toes and returns to software R&D; deflated by the diminishing returns of cognitive labour as a research input, α \\alpha. Specifically,

p ≔ λ α p \\;\\; \\coloneqq \\;\\; \\lambda \\alpha r ≔ λ α β r \\;\\; \\coloneqq \\;\\; \\dfrac{\\lambda \\alpha}{\\beta}

Notice the doubling time becomes smaller just if r \> 1 r > 1.

The standard semi-endogenous growth model allows growth to proceed indefinitely. If r \> 1 r > 1, that means software tends to infinity in finite time.[4](#user-content-fn-4) But in reality, there will be some effective limit on how good software can become. To model this, we define a ceiling for software and assume r r declines as software approaches the ceiling – specifically, each time software doubles we subtract some constant k k from r r. We choose k k so that, once software reaches the ceiling, r \= 0 r=0 and further progress in software is impossible. (The way we’ve modelled the change in r r is very specific; it could be too aggressive or too conservative – see [more](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#how-the-returns-to-software-rd-).)

### Pseudocode

This leaves us with the following pseudocode:

Software i + 1 \= 2 × Software i \\qquad\\;\\;\\, \\text{Software}\_{i+1} = 2 \\times \\text{Software}\_i Time i + 1 \= Time i + Doubling-Time i \\qquad\\qquad\\; \\text{Time}\_{i+1} = \\text{Time}\_i + \\text{Doubling-Time}\_i Doubling-Time i + 1 \= 2 p (1 r i − 1) × Doubling-Time i \\text{Doubling-Time}\_{i+1} = 2^{p(\\frac{1}{r\_i}-1)} \\times \\text{Doubling-Time}\_i r i + 1 \= r i − r 0 Doublings-Till-Ceiling \\qquad\\qquad\\qquad\\, r\_{i+1} = r\_i - \\frac{r\_0}{\\text{Doublings-Till-Ceiling}} Doubling-Time 0,Doublings-Till-Ceiling,\\qquad\\qquad\\qquad\\qquad\\quad \\text{Doubling-Time}\_0, \\;\\text{Doublings-Till-Ceiling}, r 0,p are given;\\qquad\\qquad\\qquad\\qquad\\quad r\_0, \\; p \\text{ are given}; Time 0 \= 0,Software 0 \= 1 \\qquad\\qquad\\qquad\\qquad\\quad \\text{Time}\_0 = 0, \\; \\text{Software}\_0 = 1

The pseudo-code requires four inputs:

-   Doubling-Time 0 \\text{Doubling-Time}\_0. We calculate this from 1) the recent software doubling time (which we [assume is 3 months](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#ai-software-has-recently-been-doubling-every-3-months)) and 2) our estimate of the **initial speed-up of software progress from deploying ASARA**.
    
-   Doublings-Till-Ceiling \\text{Doublings-Till-Ceiling}, i.e. the **distance to the effective limits on software**.[5](#user-content-fn-5)
    
-   r 0 r\_0, the (deflated) **returns to software R&D** when ASARA is first developed.
    
-   p p, the **diminishing returns to parallel labour**.
    

The four **bolded quantities** – initial speed-up, distance to effective limits, returns to software R&D, and diminishing returns to parallel labour – are the four parameters that users of the model must specify. We estimate them in the next section.

To translate the model’s trajectories of _software_ progress into units of _overall_ AI progress, the model [assumes](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#calculating-the-summary-statistics) that software progress has recently been responsible for 50% of total AI progress.

**You can choose your own inputs to the model [here](https://accelerated-ai-progress.streamlit.app/); code for the simulations produced is [here](https://github.com/thoulden/Accelerated_AI_Progress).**

## Parameter values

This section estimates the four main parameters of the model:

-   Initial speed-up of software progress from deploying ASARA
    
-   Returns to software R&D
    
-   Distance to effective limits of software
    
-   Diminishing returns to parallel labour (less important)
    

### Initial speed-up of software progress from deploying ASARA

_**After ASARA is deployed, software progress is faster by a factor of f f. f f is sampled from a log-uniform distribution between 2 and 32, median 8.**_

ASARA is a vague term – it just refers to full automation of AI R&D. But you could automate AI R&D by replacing each human with a slightly-better AI system, or by replacing them with 1 million way-better AI systems. In the former case the amount of cognitive labour going into AI R&D wouldn’t increase much, in the latter case it would increase by a huge factor.

So what definition of ASARA should we use? There’s a few considerations here (see more in footnote [6](#user-content-fn-6)), but the most important thing is to pick one definition and stick with it. Let’s stipulate that **ASARA can replace each human researcher with 30 equally capable AI systems each thinking 30X human speed**.[7](#user-content-fn-7) So the total cognitive labour for AI R&D increases by 900X.

ASARA (so defined) is less capable than AI 2027’s [superhuman AI researcher](https://ai-2027.com/research/takeoff-forecast), which would be equally numerous and fast as ASARA but replace the capabilities of the _**best**_ human researcher (which we expect to be worth much more than 30 average human researchers). ASARA is probably closer to AI 2027’s superhuman coder, that matches top humans at coding but lags behind on research taste.

How much faster would ASARA, so defined, speed up software progress compared to the recent pace of software progress?

There are a few angles on this question:

-   **Survey researchers about speed-ups from abundant cognitive labour.** [This paper](https://www.forethought.org/research/could-advanced-ai-accelerate-the-pace-of-ai-progress-interviews-with-ai#compilation-of-quantitative-estimates) surveyed five researchers about how much ASARA would speed up the pace of AI progress. They used the same definition of ASARA as we’re using.
    
    -   When asked outright about the total speed-up, responses varied from 2X to 20X with a geometric mean of 5X. If software progress accounts for 50% of total progress, then the corresponding speed-up in software progress is **10X**.
        
    -   When asked to estimate the speed-ups from different sources separately (e.g. reducing bugs, doing experiments at small scales), their estimates were higher, with a geometric mean of 14X. This translates into a speed-up in software progress of **28X**.
        
    
-   **Survey researchers about the per-person _slowdown_ from reduced compute.** If you have way more virtual researchers, each one of them will have much less compute. How much more slowly will they make progress?
    
    -   AI 2027 interviewed AI researchers and found that with 10X less compute they thought they’d make 40% slower progress. From this, along with a few other assumptions, they [estimate](https://ai-2027.com/research/takeoff-forecast#method-2-surveys-on-subquestions) that ASARA would accelerate software progress by a factor of **21X**.[8](#user-content-fn-8)
        
    
-   **Analysing specific sources of speed-up.** AI 2027 evaluates specific speed-ups that abundant AI labour would enable — smaller experiments, better prioritisation, better experiments, less wasted compute. They explicitly account for compute bottlenecks in their analysis but still find large gains.
    
    -   This approach [forecasts](https://ai-2027.com/research/takeoff-forecast#sc-would-5x-ai-randd) a **5X** speed up from the superhuman coder (which is maybe similarly capable to ASARA) and [forecasts](https://ai-2027.com/research/takeoff-forecast#method-1-speedup-decomposition) **417X** from a superhuman researcher (which is more capable than ASARA).
        
    
-   **Thought experiment about an AI lab with fewer + slower researchers.** ASARA would increase the number and speed of researchers working on AI R&D. We might expect the _opposite_ effect if we instead decreased the number of human researchers and made them much slower. In particular, imagine if frontier AI labs had 30X fewer researchers and they each thought 30X more slowly – how much slower would AI progress be? If you think progress would be a lot slower, that suggests ASARA might speed up progress a lot. Ryan Greenblatt and Eli LIfland explore this idea [here](https://www.lesswrong.com/posts/hMSuXTsEHvk4NG6pm/slow-corporations-as-an-intuition-pump-for-ai-r-and-d).
    
-   **Use a simple economic model of R&D** (the [same model as we use in our simulation](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#model-dynamics))
    
    -   In particular, this model is: g S \= L α C 1 − α S − β,L \= L parallel λ g\_S = L^{\\alpha} C^{1 - \\alpha} S^{-\\beta}, L = L\_{\\text{parallel}}^{\\lambda}
        
    -   Our [median model assumptions](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#summary-of-parameter-assumptions) correspond to α \= 0.5 \\alpha = 0.5, λ \= 0.6 \\lambda = 0.6.
        
    -   ASARA brings two changes: 1) 30X as many researchers in parallel, 2) every researcher thinks 30X faster
        
        -   1.  multiplies L parallel L\_{\\text{parallel}} by 30, which multiplies the rate of software progress by 30 α λ \= 2.8 30^{\\alpha^{\\lambda}} = 2.8.
                
            
        -   2.  multiplies L L by 30 which multiplies the rate of software progress by 30 α \= 30 0.5 \= 5.5 30^{\\alpha} = 30^{0.5} = 5.5.
                
            
        -   Multiplying these independent effects together, we get the total speed up of **15X**.
            
        
    

| **Method** | **Forecasted initial speed-up in software progress due to ASARA** |
| --- | --- |
| Survey researchers about speed-ups from abundant cognitive labour – ask directly about total gain | 10X |
| Survey researchers about speed-ups from abundant cognitive labour – ask separately about different sources of speed-up | 28X |
| Survey researchers about the per-person slowdown from reduced compute | 21X |
| AI 2027 analysis of specific sources of speed-up | 5X for superhuman coder (less capable than ASARA)  
  
417X from superhuman AI researcher (more capable than ASARA) |
| Thought experiment about a lab with fewer and slower researchers | Big multiplier (no specific number suggested) |
| Use a simple economic model of R&D | 15X |

These methods may be too aggressive. Before we have ASARA, less capable AI systems may still accelerate software progress by a more moderate amount, plucking the low-hanging fruit. As a result, ASARA has less impact than we might naively have anticipated.

Overall, we're going to err conservative here and use a log-uniform distribution between 2 and 32, centred on 8. In other words, deploying ASARA would speed up progress by some factor; our upper bound for this factor is 32; our lower bound is 2; our median is 8.

![Log-uniform probability distribution for initial speed-up from ASARA deployment, showing equal probability density across 2x to 32x range with median at 8x software progress acceleration](https://images.ctfassets.net/4owxfjx3z3if/3gHR6cIBXKkeG3u5NEP7vl/a8df3746007b5304b4ef07a6b215c4e9/initial-speedup-probability-distribution.png?w=3840&q=85&fm=webp)

How many times faster is software progress after ASARA is deployed compared to today?

## Image

As we've said, there’s massive uncertainty here and significant room for reasonable disagreement.

To visualise how this parameter affects the results, we can run simulations with the initial speed up equalling 2, 8, and 32:

![Graph showing AI capabilities growth over 5 years comparing different initial speed-up scenarios: 32x (green), 8x (purple), and 2x (yellow) acceleration versus recent baseline progress (gray)](https://images.ctfassets.net/4owxfjx3z3if/77yGNNb2xh2CJFx9qEncsl/3afdb6f4358fb7d374ce7fc939a4acfd/ai-capabilities-speedup-scenarios.png?w=3840&q=85&fm=webp)

Simulations of the software intelligence explosion with different values for the Initial speed-up parameter.

## Image

In the model, if the initial speed is twice as fast then the whole software intelligence explosion happens twice as fast and the maximum pace of progress is twice as fast.

### Returns to software R&D, rr

_**On our median guess for returns to software R&D, progress initially gets faster over time but then starts slowing down after training efficiency improves by a few OOMs.**_

After the initial speed-up from deploying ASARA, will software progress become faster or slower over time?

This depends on the model parameter r r.

If r < 1 r < 1, then software progress will slow down over time. If r \= 1 r = 1, software progress will remain at the same exponential rate. If r \> 1 r>1, software progress will speed up over time. (See [Eth & Davidson (2025)](https://www.forethought.org/research/will-ai-r-and-d-automation-cause-a-software-intelligence-explosion#article) for explanation.)

Luckily, the value of r r can be studied empirically. r r is the answer to the following question:

**When (cumulative [9](#user-content-fn-9)) cognitive research inputs double, how many times does software double [10](#user-content-fn-10)?**

We can study this question by observing how many times software has doubled each time the human researcher population has doubled.

| What does it mean for “software” to double?  
  
A simple way of thinking about this is that software doubles when you can run twice as many parallel copies of your AI with the same compute.  
  
But software improvements don’t just improve runtime efficiency: they also improve _capabilities_ and _thinking speed_. We translate such improvements to an equivalent increase in parallel copies. So if some capability improvement c c increases the pace of AI progress by the same amount as doubling the number of parallel copies, we say that c c doubled software.  
  
In practice, this means we’ll need to make some speculative assumptions about how to translate capability improvements into an equivalently-useful increase in parallel copies. For an analysis which considers only runtime efficiency improvements, see [this](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#returns-to-software-rd-efficiency-improvements-only) appendix. |
| --- |

Box 1: What does it mean for “software” to double?

The best quality data on this question is Epoch’s [analysis](https://arxiv.org/abs/2405.10494) of computer vision training efficiency. They estimate **r \= ∼ 1.4 \\boldsymbol{r = \\;\\sim 1.4}**: every time the researcher population doubled, training efficiency doubled 1.4 times.[11](#user-content-fn-11) We can use this as a starting point, and then make various adjustments:

-   **Upwards for improving capabilities.** Improving training efficiency improves capabilities, as you can train a model with more effective compute. Imagine we use a 2X training efficiency gain to train a model with twice as much effective compute. How many times would that double “software”? (I.e., how many doublings of parallel copies would be equally useful?) There are various sources of evidence here:[12](#user-content-fn-12) toy ML experiments suggest the answer is ~1.7; human productivity studies suggest the answer is ~2.5. We put more weight on the former, so we'll estimate 2. This doubles our median estimate to r \= ∼ 2.8 (1.4 ∗ 2) \\boldsymbol{r = \\, \\sim 2.8} \\; (1.4 \* 2).
    
-   **Upwards for post-training enhancements.** So far, we’ve only considered pre-training improvements. But post-training enhancements like fine-tuning, scaffolding, and prompting also improve capabilities (o1 was developed using such techniques!). These can allow faster thinking, which could be a big factor. But there might also be strong diminishing returns to post-training enhancements holding base models fixed. We'll adjust our median estimate up from 2.8 to r \= ∼ 4 (2.8 ∗ 1.45) \\boldsymbol{r = \\; \\sim 4} \\; (2.8 \* 1.45).
    
-   **Downwards for less growth in compute for experiments.** Today, rising compute means we can run increasing numbers of GPT-3-sized experiments each year. This helps drive software progress. But compute isn’t growing in our scenario. That might mean that returns to additional cognitive labour diminish more steeply. On the other hand, the most important experiments are ones that use similar amounts of compute to training a SOTA model. Rising compute hasn't actually increased the number of these experiments we can run, as rising compute increases the training compute required for these SOTA models. And experiments are much less of a bottleneck for post-training enhancements. But this still reduces our median estimate down to r \= ∼ 3 \\boldsymbol{r = \\; \\sim 3}. (See [Eth and Davidson (2025)](https://www.forethought.org/research/will-ai-r-and-d-automation-cause-a-software-intelligence-explosion) for more discussion.)
    
-   **Downwards for fixed scale of hardware.** In recent years, the scale of hardware available to researchers has increased massively. Researchers could invent new algorithms that only work at the new hardware scales for which no one had previously tried to to develop algorithms. Researchers may have been plucking low-hanging fruit for each new scale of hardware. But in the software intelligence explosions we're considering, this won’t be possible because the hardware scale will be fixed. OAI [estimate](https://arxiv.org/abs/2005.04305) ImageNet efficiency via a method that accounts for this (by focussing on a fixed capability level),[13](#user-content-fn-13) and find a 16-month doubling time, as compared with Epoch’s 9-month doubling time. This reduces our estimate down to r \= ∼ 1.7 (3 ∗ 9 / 16) \\boldsymbol{r = \\; \\sim 1.7} \\; (3 \* 9/16)
    
-   **Downwards for the returns to software R&D becoming worse over time.** In most fields, returns diminish more steeply than in software R&D.[14](#user-content-fn-14) So perhaps software will tend to become more like the average field over time. To estimate the size of this effect, we can take our estimate that software is ~10 OOMs from effective limits (discussed [below](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#distance-to-the-effective-limits-to-software)), and assume that for each OOM increase in software, r r falls by a constant amount, reaching zero once effective limits are reached. If r \= 1.7 r = 1.7, then this implies that r r reduces by 0.17 for each OOM. Epoch estimates that pre-training algorithmic improvements are growing by an OOM every ~2 years, which would imply a reduction in r r of 0.51 (3 ∗ 0.17) 0.51 \\; (3 \* 0.17) by 2030. This reduces our median estimate to r \= ∼ 1.2 (1.7 − 0.5) \\boldsymbol{r = \\; \\sim 1.2} \\; (1.7 - 0.5).
    

Overall, our median estimate of r r is 1.2. We use a log-uniform distribution with the bounds 3X higher and lower (0.4 to 3.6).

![Log-uniform probability distribution for returns to software R&D parameter (r), showing equal probability density from 0.4 to 3.6 with median at 1.2, determining whether AI progress accelerates or decelerates](https://images.ctfassets.net/4owxfjx3z3if/1Dty1nWjqvRZ0EClXdaU9Z/5c22a042a50699f9b3fe72a4bf5dfbd2/returns-software-rd-distribution.png?w=3840&q=85&fm=webp)

Log-uniform probability distribution for returns to software R&D parameter (r), showing equal probability density from 0.4 to 3.6 with median at 1.2, determining whether AI progress accelerates or decelerates

## Image

To visualise how this parameter affects the results, we can run simulations with different values of r r.

![Graph showing AI capabilities growth over 3 years comparing different returns to software R&D values: r=2.4 (green) shows rapid exponential growth, r=1.2 (purple) shows moderate acceleration, r=0.6 (yellow) shows deceleration versus baseline (gray)](https://images.ctfassets.net/4owxfjx3z3if/5UpgdR04oJ9pev9C0zHwc3/7f2009b8baa81742a6f9d6655ebe6db2/ai-capabilities-returns-rd-scenarios.png?w=3840&q=85&fm=webp)

Graph showing AI capabilities growth over 3 years comparing different returns to software R&D values: r=2.4 (green) shows rapid exponential growth, r=1.2 (purple) shows moderate acceleration, r=0.6 (yellow) shows deceleration versus baseline (gray)

## Image

Simulations of the software intelligence explosion with different values for the returns to software R&D, r r.

Once r r falls below 1, progress starts slowing. When r r is higher, software progress accelerates more quickly _and_ it accelerates for longer (because software advances further before r r falls below 1).

Also, when r r starts higher, effective limits are approached more rapidly and so r r itself falls more rapidly.

![Graph showing how returns to software R&D parameter (r) declines over time as AI approaches effective limits: high initial r values (2.4, green) drop rapidly to zero, moderate values (1.2, purple) decline gradually, low values (0.6, yellow) remain stable](https://images.ctfassets.net/4owxfjx3z3if/4G1D62bhEy67YWgEsmhj6o/16d71ff7c8e81752fcbe5d6e96fe3391/r-parameter-decay-over-time.png?w=3840&q=85&fm=webp)

Graph showing how returns to software R&D parameter (r) declines over time as AI approaches effective limits: high initial r values (2.4, green) drop rapidly to zero, moderate values (1.2, purple) decline gradually, low values (0.6, yellow) remain stable

## Image

Simulations of the path of returns to software R&D, r r. r r falls over time as software approaches effective limits.

### Distance to the effective limits to software

_**We estimate that, when we train ASARA, software will be 6-16 OOMs from effective limits. This is equivalent to 6-16 years worth of AI progress (at recent rates) before capping out.**_

Software cannot keep improving forever. It will never be possible to get the cognitive performance of a top human expert using the computational power of a basic calculator. Eventually we hit what we will refer to as the “effective limits” of software.

How big is the gap between the software we’ll have when we develop ASARA and these effective limits? We'll focus on training efficiency. First we'll estimate how much more efficient human learning might be than ASARA’s training. Then we'll estimate how far human learning might be from effective limits.

#### Gap from ASARA to human learning

Human lifetime learning is estimated to take [1e24 FLOP](https://docs.google.com/document/d/1IJ6Sr-gPeXdSJugFulwIpvavc0atjHGM82QjIfUSBGQ/edit?tab=t.0#heading=h.87mp14r9lgsj).[15](#user-content-fn-15) As a very toy calculation, let’s assume that ASARA is trained with 1e28 FLOP [16](#user-content-fn-16) and that at runtime it matches a human expert on a per compute basis.[17](#user-content-fn-17) This means ASARA is 4 OOMs less training efficient than human lifetime learning.[18](#user-content-fn-18)

There’s a lot of uncertainty here from the training FLOP for ASARA and the compute used by the human brain, so let’s say ASARA’s training is 2-6 OOMs less efficient than human lifetime learning.

#### Gap from human learning to effective limits

But human lifetime learning is not at the limit of learning efficiency. There is room for significant improvement to the _data_ used to train the brain, and to the brain’s _learning algorithm_.

Improvements to the _data_ used in human learning:

-   **Not enough data – the brain is severely “undertrained”.** Chinchilla optimal scaling suggests that models should be trained on ~20X as many tokens as they have parameters. On this account, the human brain is severely “undertrained”: it has maybe ~1e14 “parameters” (synapses) but only processes ~1e9 “data points” (1 data point per second for 30 years) during lifetime learning. If the Chinchilla scaling laws applied to the brain, then you could train a model with the same performance as the brain but with 4-5 OOMs less training compute – see [this appendix](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#distance-to-effective-limits-human-learning). Of course, the brain architecture might have a completely different optimal scaling to Chinchilla. But it is very plausible that the brain is significantly undertrained due to hard biological constraints: organisms don’t live long enough to keep learning for 1000s of years! We'll call this **10-100,000X**.
    
-   **Low fraction of data is relevant.** Take a human ML expert. They only spend a small fraction of their time doing focussed learning that is relevant to doing AI R&D (at most 8 hours a day on average, and plausibly much less given the time spent on poetry, history, etc). This seems like a factor of **at least 3-10X**.[19](#user-content-fn-19)
    
-   **Data quality could be much higher.** Even when humans are learning relevant material, the _quality_ of the data they would be processing is far from optimal. When an outstanding communicator puts significant effort into organising and presenting content, human learning can be much more efficient. During the software intelligence explosion AI could curate better data sets still, including demonstrations of significantly superhuman performance. It seems like this would be **at least 3X and plausibly 300X**.
    

Improvements to the brain algorithm:

-   **Brain algorithms must satisfy physical constraints.**
    
    -   Firstly, the human brain is spread out over three dimensions, communications from one part of the brain to the other must physically ‘travel’ this distance, and the speed of communication is fairly slow. This constrains the design space of brain algorithms.
        
    -   Secondly, the _brain cannot do weight sharing_ (where the same numerical ‘weights’ are used in different parts of the network), which is essential to transformers.
        
    -   Thirdly, synaptic updates are _local_, just depending on nearby synapses, whereas AI can implement non-local learning rules like stochastic gradient descent where updates are instantaneously propagated throughout the entire network.
        
    -   AI algorithms will relax these constraints. On the other hand, the hardware first used to train AGI will have different constraints – e.g. around memory access. Also, evolution _coevolved_ the brain’s hardware and software, which won’t be possible during a software intelligence explosion.
        
    -   It’s hard to know how significant this will be overall, maybe **3-100X**.
        
    
-   **Significant variation between humans.** There is significant variation in cognitive abilities between different humans. It may be possible to significantly increase human intelligence (e.g. by >100 IQ points) just by combining together all the best mutations and making more of the same kinds of changes that drive human variation. This might be another **3-10X**.[20](#user-content-fn-20)
    
-   **Fundamental improvements in the brain’s learning algorithm.** Evolution is a blind search process and does not always find the optimal solutions to problems – e.g. giraffes have a [nerve](https://www.mcgill.ca/oss/article/student-contributors-did-you-know-general-science/unintelligent-design-recurrent-laryngeal-nerve) that loops up and down their neck only to end up right next to where it started. AI could write _vastly_ more complicated learning algorithms than the human brain algorithm, which is encoded within the human genome and so cannot exceed [~1e9 bits](https://en.wikipedia.org/wiki/Human_genome#Information_content). In the limit, AI could hard-code knowledge [GOFAI](https://en.wikipedia.org/wiki/GOFAI) -style rather than learning it. Again, it’s hard to know how big this will be. Maybe **3-30X**.
    
-   **Coordination.** Humans must coordinate via language, which is slow and imperfect. By contrast, AIs could potentially communicate via multidimensional vectors and copies could share their activations with one another. This might significantly raise the collective capabilities achievable by large teams. Maybe **3-10X**.
    

Overall, the additional learning efficiency gains from these sources suggest that effective limits are 4 - 14 OOMs above the human brain. The high end seems extremely high, and we think there’s some risk of double counting some of the gains here in the different buckets, so we will bring down our high end to 10 OOMs. We’re interpreting these OOMs as up limits _upwards_ (increasing capabilities with fixed training compute) not as the limits _downwards_ (reducing training compute but holding capabilities constant).[21](#user-content-fn-21)

So ASARA has room for 2 - 6 OOMs of training efficiency improvements before reaching the efficiency of the human lifetime learning, and a further 4 - 10 OOMs before reaching effective limits, for a total of **6 - 16 OOMs**.

One reason for scepticism here is that these gains in training efficiency would be _much bigger_ than anything we’ve seen historically. Epoch [report](https://arxiv.org/pdf/2403.05812) s the training efficiency for GPT-2 increasing by 2 OOMs in a three year period, but doesn't find examples of much bigger gains over any time period. On the other hand, some of the factors listed are plausibly even bigger than our upper estimate, e.g. “must satisfy physical constraints” and "fundamental improvements”.

In recent years, effective training compute has risen by about [10X per year](https://epoch.ai/trends). So the model makes the assumption that after ASARA there could be **6 - 16 years of AI progress**, at the rate of progress seen in recent years, before software hits effective limits.

![Uniform probability distribution for distance to effective limits of AI software, showing equal likelihood across 6-16 years of progress at recent rates before reaching fundamental efficiency constraints](https://images.ctfassets.net/4owxfjx3z3if/53mRowE4luEAiRvW2hQAEN/93562665c465925c82aacde4243e28e5/distance-effective-limits-distribution.png?w=3840&q=85&fm=webp)

When we train ASARA, how far will software be from effective limits?

## Image

To visualise how this parameter affects the results, we can run simulations with different limits.

![Graph showing AI capabilities growth over 4 years comparing different distances to effective limits: 14 years (green) enables highest growth, 10.5 years (purple) shows moderate plateau, 7 years (yellow) shows earlier saturation versus baseline (gray)](https://images.ctfassets.net/4owxfjx3z3if/5llo6E2FApLvriwNCDnGne/cde286c59becaa806f9866b3a906f10c/ai-capabilities-effective-limits-scenarios.png?w=3840&q=85&fm=webp)

Simulations of the software explosion with difference values for the distance to effective limits (measured in years of AI progress at 2020-4 rates).

## Image

When effective limits are further away, software progress accelerates for longer and plateaus at a higher level.

### Diminishing returns to parallel labour

_Whether_ AI progress accelerates vs decelerates depends on the parameter r r. But _how quickly_ it accelerates/decelerates also depends on another parameter, the diminishing returns to parallel labour p p.

The meaning of p p is: if you instantaneously doubled the amount of parallel cognitive labour directed towards software R&D, how many times would the pace of software progress double?

As discussed above, p \= λ α p = \\lambda \\alpha.

-   λ \\lambda captures diminishing returns to parallel efforts – nine women can’t make a baby in a month! We use λ \= 0.6 λ=0.6.[22](#user-content-fn-22)
    
-   α \\alpha captures the relative importance of cognitive labour inputs to software R&D, as contrasted with inputs of compute for experiments. We assume the share of software progress that’s attributable to cognitive labour is 0.5.
    

So our median estimate is p \= 0.6 ∗ 0.5 \= 0.3 p = 0.6\*0.5 = 0.3.

We use a log-uniform distribution over p p from 0.15 0.15 to 0.6 0.6.

## Summary of parameter assumptions

The Monte Carlo samples four parameters from, three from log-uniform distributions and one from a uniform distribution (distance to effective limits).

|  | **Lower bound** | **Median** | **Upper bound** |
| --- | --- | --- | --- |
| **Initial speed-up** in the pace of software progress due to ASARA | 2 | 8 | 32 |
| **Returns to software R&D**, r r | 0.4 | 1.2 | 3.6 |
| **Distance to effective limits** on software (in units of years of progress) | 6 | 11 | 16 |
| **Diminishing returns to parallel labour**, p p | 0.15 | 0.3 | 0.6 |

| Recall we derive our model from the following law of motion:  
  
S ˙ (L,C) \= a \[R (L,C)\] λ S 1 − β (Software L.O.M) \\dot{S}(L,C) = a\[R(L,C)\]^{\\lambda} S^{1- \\beta} \\qquad\\qquad\\qquad\\; \\text{(Software L.O.M)}  
R (L,C) \= (b L) α (c C) 1 − α (Research Input) R(L,C) = (bL)^{\\alpha}(cC)^{1- \\alpha} \\qquad\\qquad\\qquad\\qquad \\text{(Research Input)}  
  
We define p \= λ α p = \\lambda \\alpha and r \= λ α / β r = \\lambda \\alpha / \\beta.  
  
Our median estimates of p p and r r correspond to α \= 0.5 \\alpha=0.5, λ \= 0.6 \\lambda=0.6, β \= 0.25 \\beta=0.25.  
  
Note that we independently sample p p and r r; we don’t sample the underlying λ \\lambda, α \\alpha, and β \\beta – we discuss this choice in an [appendix](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#objection-to-our-sampling-procedure). |
| --- |

Box 2: What do our assumptions imply about the values of λ \\lambda, α \\alpha, and β \\beta?

You can change all of these assumptions in the [online tool](https://accelerated-ai-progress.streamlit.app/).

## Results

| **Years of progress** | **Compressed into ≤1 year** | **Compressed into ≤4 months** |
| --- | --- | --- |
| ≥3 years | 57% | 41% |
| ≥10 years | 18% | 12% |

![Probability curve for retraining model variant showing likelihood of compressing AI progress into one year: 57% chance for 3+ years, 18% chance for 10+ years, with declining probability for more dramatic compression](https://images.ctfassets.net/4owxfjx3z3if/Wn5YS1bYQKyyBt1DFIAiF/897826b2a263b552d44d0546dd2fe7b3/retraining-model-probability-results.png?w=3840&q=85&fm=webp)

Probability curve for retraining model variant showing likelihood of compressing AI progress into one year: 57% chance for 3+ years, 18% chance for 10+ years, with declining probability for more dramatic compression

## Image

It goes without saying that this is all very rough and at most one significant figure should be taken seriously.

The appendix contains the results for two variants of the model:

-   **Retraining cost.** This variant models the fact that we’ll need to train new generations of AI from scratch during the intelligence explosion and, if progress is accelerating, those training runs will have to become quicker over time. [More](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#retraining-time).
    
-   **Gradual boost.** This variant models AI systems intermediate between today’s AI and ASARA. It assumes AI gradually accelerates software progress more and more over time. [More.](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#gradual-boost-from-pre-asara-systems)
    

Both variants are consistent with the bottom line that **the software intelligence explosion will probably compress >3 years of AI progress into 1 year, but is somewhat unlikely to compress >10 years into 1 year**.

_You can choose your own inputs to the model [here](https://accelerated-ai-progress.streamlit.app/)._

## Limitations and caveats

**We're not modelling the actual mechanics of the software intelligence explosion.** For example, there’s no gears-level modelling of how synthetic data generation [23](#user-content-fn-23) might work or what specific processes might drive very rapid progress. We don’t even separate out post-training from pre-training improvements, or capability gains from inference gains. Instead we attempt to do a high-level extrapolation from the patterns in _inputs_ and _outputs_ to AI software R&D, considered holistically. As far as we can tell, this doesn’t bias the results in a particular direction, but the exercise is very speculative and uncertain.

Similarly, we don’t model specific AI capabilities but instead represent AI capabilities as an abstract scalar, corresponding to how capable they are at AI R&D.

**Significant low-hanging fruit may be plucked before ASARA.** If ASARA is good enough to speed up software progress by 30X, earlier systems may already have sped it up by 10X. By the time ASARA is developed, the earlier systems would have plucked the low-hanging fruit for improving software. Software would be closer to effective limits and returns to software R&D would be lower (lower r r). So the simulation will overestimate the size of the software intelligence explosion.

How could we do better? The [gradual boost model variant](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#gradual-boost-from-pre-asara-systems) does just this by modelling the gradual development of ASARA over time and modelling the software progress that happens before ASARA is developed. Our high-level bottom line holds true: the software intelligence explosion will probably compress 3 years of AI progress into 1 year, but is somewhat unlikely to compress 10 years into 1 year.

**Assuming the historical scaling of capabilities with compute continues.** We implicitly assume that, during the software intelligence explosion, doubling the effective compute used to develop AI continues to improve capabilities as much as it has done historically. This is arguably an aggressive assumption, as it may be necessary to spend significant compute on generating high-quality data (which wasn’t needed historically). This could also be conservative if we find new architectures or algorithms with more favourable scaling properties than historical scaling.

-   We make this assumption when [estimating the returns to software R&D r r](https://docs.google.com/document/d/1LSfKB54gs2t6-T0fzCaKqxtszUD2V2iUG5CdqFXpBsk/edit?tab=t.myepkk2wclag#heading=h.v156a5eli5jh), in particular when assessing the benefits of training models with better capabilities.
    

**“Garbage in, garbage out”.** We’ve done our best to estimate the model parameters fairly, but there are massive uncertainties in all of them. This flows right through to the results. The assumption about effective limits is especially worth calling out in this regard.

-   You can choose your own inputs [here](https://accelerated-ai-progress.streamlit.app/)!
    

_Thanks to Ryan Greenblatt, Eli Lifland, Max Daniel, Raymond Douglas, Ashwin Acharya, Owen Cotton-Barratt, Max Dalton, William MacAskill, Fin Moorhouse, Ben Todd, Lizka Vaintrob and others for review and feedback. Thanks especially to Rose Hadshar for help with the writing._

## Appendices

### Derivation of our pseudo code from the semi-endogenous growth model

We start with the following environment (described in the main text):

S ˙ (L,C) \= a \[R (L,C)\] λ S 1 − β (Software L.O.M) \\, \\dot{S}(L, C) = a\[R(L, C)\]^{\\lambda} S^{1-\\beta} \\qquad\\qquad\\; \\text{(Software L.O.M)} R (L,C) \= (b L) α (c C) 1 − α (Research Input) R(L, C) = (bL)^{\\alpha}(cC)^{1-\\alpha} \\qquad\\qquad\\qquad \\text{(Research Input)} L \= d S (Cognitive Labour) \\qquad\\;\\;\\, L = dS \\qquad\\qquad\\qquad\\qquad\\quad\\;\\;\\, \\text{(Cognitive Labour)}

Combining these three expressions we get the growth rate of software, as a function of software level and compute:

g S (S,C) \= S λ α − β C λ (1 − α) × a (b d) λ α c λ (1 − α) g\_S(S,C) \\;\\; = \\;\\; S^{\\lambda \\alpha - \\beta} C^{\\lambda(1-\\alpha)} \\times a(bd)^{\\lambda \\alpha} c^{\\lambda(1-\\alpha)} \= S λ α − β C λ (1 − α) × Constant \\qquad\\qquad\\;\\, = \\;\\; S^{\\lambda \\alpha - \\beta} C^{\\lambda(1-\\alpha)} \\times \\text{Constant}

From here, the time it takes for software to double is given by

Doubling Time (S,C) \= log ⁡ (2) g S (S,C) \\text{Doubling Time} (S,C) = \\frac{\\log(2)}{g\_S(S,C)}

Next, if we want to express the doubling time under software level 2 S 2S in terms of the doubling time for software under software level S S, we can divide expressions:

Doubling Time (2 S,C) Doubling Time (S,C) \= g S (S,C) g S (2 S,C) \\quad\\;\\; \\displaystyle \\frac{\\text{Doubling Time}(2S,C)}{\\text{Doubling Time}(S,C)} = \\frac{g\_S(S,C)}{g\_S(2S,C)} ⟹ Doubling Time (2 S,C) \= Doubling Time (S,C) × 2 β − λ α \\Longrightarrow \\text{Doubling Time}(2S,C) = \\text{Doubling Time}(S,C) \\times 2^{\\beta - \\lambda \\alpha}

So we can see that after a doubling of software, the time it takes to complete the next doubling halves λ α − β \\lambda \\alpha - \\beta times. To map this expression to the parameters in the rest of this analysis, we define p p and r r as in the main text:

p:\= λ α p:= \\lambda \\alpha r:\= λ α β r:= \\dfrac{\\lambda \\alpha}{\\beta}

And therefore, to get the doubling time expression in the [pseudo code](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#pseudocode) note β − λ α \= p (r − 1 − 1) \\beta - \\lambda \\alpha \\; = \\; p (r^{-1} - 1), therefore

Doubling Time (2 S,C) \= Doubling Time (S,C) × 2 p (1 r − 1) \\text{Doubling Time}(2S,C) = \\text{Doubling Time}(S,C) \\times 2^{p(\\frac{1}{r} - 1)}

Therefore, so long as we know the initial doubling time of software and p p and r r for each time period, we can chain together doubling times to calculate a path of software.

### Additional model assumptions

In addition to the [pseudo code](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#pseudocode), the results reported in the piece are also determined by three additional assumptions:

1.  AI software has recently been doubling every 3 months ([more](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#ai-software-has-recently-been-doubling-every-3-months)).
    
2.  Half of AI progress is due to software and half is due to compute ([more](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#calculating-the-summary-statistics)).
    
3.  Our sampling procedure for the Monte Carlo ([more](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#objection-to-our-sampling-procedure)).
    

#### AI software has recently been doubling every 3 months

A model parameter specifies the _initial speed-up_ in software progress from deploying ASARA. But we also need to make an assumption about how fast AI software has progressed recently. Then we can calculate:

Initial software doubling time after ASARA \= recent software doubling time initial speed-up \\text{Initial software doubling time after ASARA} = \\frac{\\text{recent software doubling time}}{\\text{initial speed-up}}

We assume that recently software has doubled every 3 months.

Why 3 months? [Epoch estimates](https://epoch.ai/trends) that training efficiency doubles every 8 or 9 months, but that doesn't include post-training enhancements which would make things faster. So we adjust down to 6 months. This is the doubling time of _training efficiency_ – the training compute needed to achieve some capability level.

But the simulation measures “software” in units of parallel labour. A doubling of software is any software improvement as useful as an improvement that doubles the number of parallel copies you can run.

The main body [argues](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#returns-to-software-rd-) that, measured in these units, software doubles more quickly than training efficiency because better training efficiency allows you to access better capabilities, and this is more valuable than having twice as many parallel copies. Based on this consideration, we adjust the 6 months down to 3 months.

#### Calculating the summary statistics

The simulation spits out a trajectory for AI software progress over time. From that we can calculate “there was a 1 year period where we had 10 years of **software** progress at recent rates of progress”.

But our results report how many years of **overall** AI progress we get in each year. So we must make an additional assumption about how the recent pace of _software_ progress compares to the recent rate of _overall_ AI progress. **We assume that half of recent progress has been driven by compute and the other half by software.**

To illustrate this assumption, it allows the following inference:  
There was a 1 year period where we had 10 years of _software_ progress → There was a 1 year period where we had 5 years of _overall_ AI progress.

You can change this assumption in the [online tool](https://accelerated-ai-progress.streamlit.app/).

#### Objection to our sampling procedure

It might seem ill-advised to independently sample r \= α λ β r = \\frac{\\alpha \\lambda}{\\beta} and p \= α λ p = \\alpha \\lambda. Should we not instead sample β \\beta and α λ \\alpha \\lambda? After all, these are the more fundamental inputs that determine the model behaviour. For example, we will sample α λ \\alpha \\lambda holding r r fixed – this means that a higher value for α λ \\alpha \\lambda will change the (implicit) value of β \\beta.

We tentatively think our sampling procedure is appropriate given our epistemic position. The best evidence we have to calibrate the model is evidence about r r. This comes from observing the ratio between the growth rate of inputs and the growth rate of outputs to AI R&D: r \= g outputs g inputs r = \\frac{g\_{\\text{outputs}}}{g\_{\\text{inputs}}}. Given our evidence on r r, it is the case that from our epistemic position it is appropriate that a higher estimate of α λ \\alpha \\lambda should change our estimate of β \\beta.

To be concrete, suppose our evidence tells us that r \= 2 r = 2. Then we sample from our distribution over α λ \\alpha \\lambda. If we sample a high value, it is appropriate for us to assume that β \\beta is also high, so that our assumption about α λ \\alpha \\lambda remains consistent with our evidence about r r.

A more sophisticated approach here is surely possible. But our model is intended as a glorified BOTEC and we don’t expect additional sophistication would significantly affect the bottom line. And our remaining uncertainty about the bottom line stems much more from uncertainty about the right parameter values than from uncertainty about the sampling procedure.

### Variants of the model

We explore two variants of the model that make it more realistic in certain respects.

#### Retraining time

We have accounted for the time to train new AI systems in our estimate of the _initial_ speed of software progress. But retraining also affects how the pace of AI progress should change over time.

Let’s say that AI progress requires two steps: improving software and retraining.

![Flowchart showing retraining model cycle: improved AI software leads to retraining AI, which produces better AI, creating feedback loop for continued improvement](https://images.ctfassets.net/4owxfjx3z3if/1Qg5rfXrzyUPMJW3RvSJbi/1d11052f10b9098ea975c50496fa6140/retraining-cycle-diagram.png?w=3840&q=85&fm=webp)

Flowchart showing retraining model cycle: improved AI software leads to retraining AI, which produces better AI, creating feedback loop for continued improvement

## Image

As software progress becomes very fast, retraining will become a bottleneck. To avoid this, some of your software improvements can be “spent” on reducing the duration of training rather than on improving capabilities. As a result of this expenditure, the pace of AI progress accelerates more slowly. (An inverse argument shows that the pace of AI progress also _decelerates_ more slowly, as you can expand the time for training as progress slows.)

A simple way to model this is to assume that **each time the pace of software progress doubles, the duration of training must halve**. Software progress and training become faster in tandem.

How can we incorporate this into the model? Suppose that the model previously stated that software doubled N N times before the pace of software progress doubled. We should increase this to N + 1 N+1. The extra software doubling is spent on reducing the duration of training. Our rough median estimate for N N is 5, as argued in [this appendix](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#how-the-speed-of-software-progress-changes-over-time).

![Diagram showing retraining model timing: total time to create next generation AI includes both software improvement and retraining phases, with accelerating progress requiring faster retraining to avoid bottlenecks](https://images.ctfassets.net/4owxfjx3z3if/40gkSK4CZA9Lp78dUmubLl/8faccff8b69b088f70fdb5f3ffb3b01e/retraining-time-allocation-diagram.png?w=3840&q=85&fm=webp)

Diagram showing retraining model timing: total time to create next generation AI includes both software improvement and retraining phases, with accelerating progress requiring faster retraining to avoid bottlenecks

## Image

Specifically, we adjust the line of code that describes how software progress changes each time software doubles:

Doubling-Time i + 1 \= 2 p (1 r i − 1) × Doubling-Time i \\text{Doubling-Time}\_{i+1} \\;\\; = \\;\\; 2^{p(\\frac{1}{r\_i} - 1)} \\times \\text{Doubling-Time}\_i

The exponent on 2 here is the reciprocal of N N: p ((1 / r) − 1) \= 1 / N p((1/r) - 1) = 1/N. So we replace this exponent with

1 N + 1 \= p (1 r − 1) 1 + p (1 r − 1) \\displaystyle \\frac{1}{N+1} = \\frac{p(\\frac{1}{r}-1)}{1+p(\\frac{1}{r}-1)}

This analysis assumed that software was accelerating over time – N \> 0 N>0, p ((1 / r) − 1) \> 0 p((1/r) - 1)>0. Repeating the argument for the case where software is decelerating – N < 0 N<0, p ((1 / r) − 1) < 0 p((1/r) - 1)<0 – yields p ((1 / r) − 1) (1 − (p ((1 / r) − 1))) \\frac{p((1/r) - 1)}{(1 - (p((1/r) - 1)))}. Therefore the correct exponent in both cases is λ ((1 / r) − 1) (1 + ∣ λ ((1 / r) − 1) ∣) \\frac{\\lambda((1/r) - 1)}{\\left(1 + |\\lambda((1/r) - 1)|\\right)}.

We rerun the analysis with this new exponent and find that the results do not change significantly.

| **Years of progress** | **Compressed into ≤1 year** |  | **Compressed into ≤4 months** |  |
| --- | --- | --- | --- | --- |
|  | RT | No RT | RT | No RT |
| ≥3 years | 57% | 56% | 41% | 41% |
| ≥10 years | 19% | 17% | 14% | 12% |

![Graph showing probability of compressing at least X years into one year. Declining orange curve from 1.0 to 0.0 probability over 0-20 years compressed. Vertical lines mark 3 years (57% probability) and 10 years (19% probability).](https://images.ctfassets.net/4owxfjx3z3if/5Oe1Dkx64NphOVLzRg225E/b7a18c707d050de0b9b4195806540c3c/time_compression_probability_curve.png?w=3840&q=85&fm=webp)

Graph showing probability of compressing at least X years into one year. Declining orange curve from 1.0 to 0.0 probability over 0-20 years compressed. Vertical lines mark 3 years (57% probability) and 10 years (19% probability).

## Image

See [here](https://www.forethought.org/research/will-the-need-to-retrain-ai-models) for more analysis of how retraining affects the dynamics of the software intelligence explosion.

#### Gradual boost (from pre-ASARA systems)

In the main results we assume ASARA boosts the pace of software progress by 2-32x (median 8x) and the simulation starts from when this boost is first felt. In the ‘compute growth’ scenario we assume that this boost ‘ramps up’ (exponentially) over 5 years, mapping to the time frame over which we expect compute for AI development could continue to grow rapidly.

![Graph showing acceleration factor f(t) growing linearly from 0.1 to 8 over 5 years in gradual boost model, representing gradual ramp-up from minimal AI assistance to full ASARA capabilities](https://images.ctfassets.net/4owxfjx3z3if/76sjDeeO4UBnXYoP0jehXK/65a858eb2f487042e0b08041478e7cac/acceleration-factor-gradual-boost.png?w=3840&q=85&fm=webp)

Graph showing acceleration factor f(t) growing linearly from 0.1 to 8 over 5 years in gradual boost model, representing gradual ramp-up from minimal AI assistance to full ASARA capabilities

## Image

In the simulation, the initial boost to research productivity from deployment of AI is an additional 10% on top of the usual rate of software progress. The boost then grows linearly over time until it reaches the sampled maximum value (between 2 and 32).

To implement this in the model, we assume that the boost in each time period originates from compute growth, which grows at an exogenous (and exponential) rate until it reaches a ceiling. We assume this ceiling occurs after 12 doublings of compute (or a 4096× increase relative to the initial compute level) which occurs after five years from the start time of the model.

Software i + 1 \= 2 × Software i \\qquad\\;\\; \\text{Software}\_{i+1} = 2 \\times \\text{Software}\_i f i + 1 \= 1 + f 0 + (f max − f 0) × min ⁡ { Time i,Time Boost End } \\qquad\\qquad\\qquad f\_{i+1} = 1 + f\_0 + (f\_{\\text{max}} - f\_0) \\times \\min\\{\\text{Time}\_i, \\text{Time}\_{\\text{Boost End}}\\} Time i + 1 \= Time i + Doubling-Time i \\qquad\\qquad\\; \\text{Time}\_{i+1} = \\text{Time}\_i + \\text{Doubling-Time}\_i Doubling-Time i + 1 \= 2 p (1 r i − 1) × Doubling-Time i × f i f i + 1 \\text{Doubling-Time}\_{i+1} = 2^{p(\\frac{1}{r\_i} -1)} \\times \\text{Doubling-Time}\_i \\times \\frac{f\_i}{f\_i +1} r i + 1 \= r i − r 0 Doublings-Till-Ceiling Software \\qquad\\qquad\\qquad\\, r\_{i+1} = r\_i - \\frac{r\_0}{\\text{Doublings-Till-Ceiling}\_{\\text{Software}}} Doubling-Time 0,Doublings-Till-Ceiling Software,\\qquad\\qquad\\qquad\\qquad\\quad\\, \\text{Doubling-Time}\_0, \\text{Doublings-Till-Ceiling}\_{\\text{Software}}, Time Boost End,r 0,p,f 0,f max, are given;\\qquad\\qquad\\qquad\\qquad\\quad\\, \\text{Time}\_{\\text{Boost End}}, r\_0, p, f\_0, f\_{\\text{max}}, \\;\\text{ are given}; Time 0 \= 0,Software 0 \= 1,Compute 0 \= 1 \\qquad\\qquad\\qquad\\qquad\\quad\\, \\text{Time}\_0 = 0, \\text{Software}\_0 = 1, \\text{Compute}\_0 = 1

In the simulation it is assumed that f 0 \= 0.1 f\_0 = 0.1. Given exponential growth in compute, f (C) f(C) increases linearly with time until it reaches the compute ceiling, at which point f f remains at f max f\_{\\text{max}}.

When running this version of the simulation we increase r r. This is because we [previously discounted r r](https://www.forethought.org/research/how-quick-and-big-would-a-software-intelligence-explosion-be#returns-to-software-rd-) on account of software progress made in the run-up to ASARA making returns to software R&D more steep. But this simulation models the gradual ramp up to ASARA so this discount isn’t needed.

|  | **Lower bound** | **Median** | **Upper bound** |
| --- | --- | --- | --- |
| r r in other sims | 0.4 | 1.2 | 3.6 |
| r r in this sim | 1.7/3 = 0.57 | 1.7 | 1.7\*3 = 5.1 |

We also increase the distance to effective limits. The simulation starts at an earlier point in time when software is less advanced and further from limits. Epoch estimates that training efficiency increases by about 0.5 OOMs/year and, to include some intermediate speed up in software progress, we add 3 OOMs.

|  | **Lower bound** | **Median** | **Upper bound** |
| --- | --- | --- | --- |
| Distance to effective limits in other sims | 6 \\hspace{3cm} | 11 | 16 \\hspace{3cm} |
| Distance to effective limits in this sim | 9 | 14 | 19 |

Here are the results:

| **Years of progress** | **Compressed into ≤1 year** |  | **Compressed into ≤4 months** |  |
| --- | --- | --- | --- | --- |
|  | GB | No GB | GB | No GB |
| ≥3 years | 59% | 56% | 48% | 41% |
| ≥10 years | 32% | 17% | 24% | 12% |

![Probability curve for gradual boost model variant showing likelihood of compressing AI progress into one year: 59% chance for 3+ years, 32% chance for 10+ years, with declining probability for more dramatic compression](https://images.ctfassets.net/4owxfjx3z3if/4aruN7HsGlPwaNqTraucL8/0fee1324115d6525bcebc6151b230f01/gradual-boost-probability-results.png?w=3840&q=85&fm=webp)

Probability curve for gradual boost model variant showing likelihood of compressing AI progress into one year: 59% chance for 3+ years, 32% chance for 10+ years, with declining probability for more dramatic compression

## Image

The software intelligence explosion is _more_ dramatic, presumably because we used more aggressive parameter values for r r and the distance to effective limits.

### Returns to software R&D: efficiency improvements only

In the main text, we include both runtime efficiency and capabilities improvements in our estimates of r r for software progress. But the capabilities improvements are necessarily more speculative: to pin down what counts as a doubling, we need to implicitly translate capabilities improvements into equivalent improvements in runtime efficiency.

To check how robust our main estimate is to this speculative translation, we can ask what r r is when considering only direct runtime efficiency improvements.

As above, the highest quality and most relevant estimate is Epoch’s [analysis](https://arxiv.org/abs/2405.10494) of computer vision training efficiency.[24](#user-content-fn-24) They estimate r \= ∼ 1.4 \\boldsymbol{r = \\; \\sim 1.4} (every time the researcher population doubled, training efficiency doubled 1.4x).

Again we'll make a couple of adjustments:

-   **Downwards for runtime efficiency.** To estimate returns to software improvements, we need to convert from training efficiency (the inputs) into runtime efficiency (the outputs). The logic of the [Chinchilla paper](https://arxiv.org/pdf/2203.15556) implies that increasing training efficiency by 4X will increase runtime efficiency by between 2X and 4X.[25](#user-content-fn-25) This means we should reduce our estimate of r r by up to a factor of 2. We'll reduce it to r \= ∼ 1 \\boldsymbol{r = \\; \\sim1}.
    
-   **Upwards for post-training enhancements.** Improvements to pre-training algorithms are not the only source of runtime efficiency gains. There are also techniques like: model distillation; calling smaller models for easier tasks; pruning (removing parameters from a trained model); post-training quantisation (reducing the numerical precision of the weights); more efficient caching of results and activations (especially for agents that re-read the same context multiple times). We'll increase our estimate to r \= ∼ 1 − 2 \\boldsymbol{r = \\; \\sim 1-2}.
    

r r is necessarily lower when we’re considering only efficiency improvements - but it still seems fairly likely that r \> 1 r>1, even excluding capabilities improvements.

### Distance to effective limits: human learning

How much more efficient could human learning be if the brain wasn’t undertrained?

![Chinchilla scaling diagram showing human brain severely undertrained with 1e14 synapses and 1e24 FLOP learning, positioned far from optimal efficiency frontier, suggesting 4+ OOM training efficiency gains possible](https://images.ctfassets.net/4owxfjx3z3if/4bYgWa3tipGUdtEVBcgCyd/891b70c66735ecf530f7927e992b2726/chinchilla-scaling-human-brain-comparison.png?w=3840&q=85&fm=webp)

This is a naive extrapolation from the Chinchilla paper results. The blue line shows the optimal scaling path. The training FLOP and parameters for human lifetime learning is shown at the top right – the human brain is severely undertrained. The pink lines indicate how much training FLOP would produce a model with the same loss as the brain, if the model were trained optimally.

## Image

\[Thanks to Marius Hobbhahn and Daniel Kokotajlo for help with this diagram.\]

It looks like the efficiency gain is over 5 OOMs. Tamay Besiroglu wrote [code](https://colab.research.google.com/drive/1kpl6B9MHkYUwLSSleOk02pAnpSGxE25H#scrollTo=4QUHTDV0AKwT) to calculate this properly, and found that the efficiency gain was 4.5 OOMs.

### Discussion of model assumptions

#### How the returns to software R&D rr changes over time

_**Each time software doubles, r r decreases by a constant absolute amount; r r reaches 0 once software hits the ceiling.**_

The returns to software R&D are represented by the parameter r r. How does r r change over time?

One way to think about r r is: each time you double _cumulative cognitive inputs_ to software R&D, software doubles r r times.[26](#user-content-fn-26)

This means that if r r halves, the pace of software progress halves (holding the growth of cumulative inputs fixed). r r is directly proportional to the pace of progress (holding the growth of cumulative inputs fixed).

The model assumes that:

1.  By the time software reaches effective limits, r \= 0 r = 0. This means that further software progress is impossible.
    
2.  Each time software doubles, r r decreases by a constant absolute amount. This absolute amount is chosen to be consistent with #1.
    
    -   So, for example: once software has advanced half the distance to effective limits in log-space, the value of r r will have halved. Each doubling of cumulative inputs will double software half as many times as before.
        
    

**This assumption could easily be very wrong in either direction.** Returns might become steeper much more quickly, far from effective limits, perhaps because many OOMs of improvement require massive computational experiments that are not available. Alternatively, it’s possible that returns stay similar to their current value until we are within an OOM of effective limits.

#### How the speed of software progress changes over time

The math of the model states that every time software doubles, the pace of software progress doubles p (1 − 1 / r) p(1 - 1/r) times.

Let’s assume software progress becomes faster over time (r \> 1) (r>1). How quickly does it become faster?

Let’s assume r \= 2.5 r=2.5 (which is close to our median conditioning on r \> 1 r>1) and p \= 0.3 p=0.3, each time software doubles the pace of software progress doubles 0.18 times. In other words, a very rough median estimate is that, **in a software intelligence explosion, every time software doubles 5 times, the pace of software progress itself will double**.
