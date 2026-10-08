---
title: "Q2.5 2026 Timelines Update: Uplift and Revenue"
author:
  - "Eli Lifland"
  - "Daniel Kokotajlo"
  - "Brendan Halstead"
source_url: "https://blog.aifutures.org/p/q25-2026-timelines-update-uplift"
published: 2026-08-16
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "More methods for forecasting coding automation"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_Tl;dr: Our timelines haven’t changed much (they got slightly shorter) but our modeling and evidence base have noticeably improved, so we feel somewhat more confident._

## Summary ^summary

We intend to regularly update our AI timelines forecasts as new evidence comes in and new analyses are done. Today’s “Q2” update was delayed by the crunch to publish [AI 2040: Plan A](https://ai-2040.com/), our [domestic regulation blog post](https://blog.aifutures.org/p/how-to-pace-the-us-frontier), and the time needed to implement and document changes to our model.

The original [AI Futures Model](https://www.aifuturesmodel.com/) predicted when Automated Coder (AC), an AI for which the leading AI company would rather fire its human software engineers than forego AI usage for coding, would happen using [METR’s measurements of coding time horizon](https://metr.org/time-horizons/). (More precisely, time horizon anchors are used to set the [effective compute](https://www.aifuturesmodel.com/#section-modelingeffectivecompute) required for AC.) While serviceable, this method has huge weaknesses, including (a) it’s unclear what time horizon corresponds to AC (it’s even unclear whether any finite value would) (b) people strongly disagree about the extent to which we should expect the time horizon trend to be superexponential as a function of effective compute, in a way that can lead to vastly different predictions.

So we’ve been on the lookout for other methods for setting the effective compute required for AC, and now we have two candidates: coding uplift (i.e., how much of a speedup AIs are providing to software engineers at AGI companies) and [[#^revenue|revenue]]. Coding uplift is our favorite method: the basic idea is to estimate the doubling time of the quantity (uplift - 1) and extrapolate that until AC-level uplift is reached. The [[#^uplift|way we anchor the model]] using uplift-relevant estimates is a bit complex, so we first explain a [[#^a-3-parameter-uplift-model|simpler 3-parameter uplift model]] that gives similar results. With coding uplift, the value corresponding to AC is much less uncertain than with time horizons, and while we also expect coding uplift to be somewhat superexponential this isn’t nearly as important as with time horizons.

Surprisingly, [[#^daniel|all 3 methods predict quite similar AC arrival dates]].[^note-1] We take this to be a somewhat encouraging sign about the robustness of our forecasts, though we are still very uncertain.

You can explore the uplift-anchored version of the model at [aifuturesmodel.com](http://aifuturesmodel.com/) and the other options for AC forecasting via the dropdown at the top of the second graph.

Each author assigned weights to the 3 AC anchoring methods which the model aggregates into an overall forecast. We also [[#^comparing-the-ai-2027|re-evaluated AI 2027’s predictions]]; reality seems to be going about 70-90% as fast as AI 2027 predicted.

Incorporating all of the above, our latest timelines forecasts (conditional on going as fast as is technically feasible): ([link](https://www.aifuturesmodel.com/forecast/daniel-08-16-26?takeoff=ASI%2CTED-AI&cmode=forecaster&csim=eli-08-16-26%2Cbrendan-08-16-26&ctype=atc))

![Chart from aifuturesmodel.com: probability density of Automated Coder arrival for all three authors' Aug 2026 all-things-considered forecasts. Daniel p10 Jan 2027, p50 Nov 2027, p90 Apr 2030; Eli p10 Jun 2027, p50 Jan 2030, p90 Oct 2070; Brendan p10 Jan 2027, p50 Jan 2029, p90 Jan 2050.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img1-c650a789.webp)

Here’s how our forecasts have shifted recently:

[Datawrapper chart: How our timelines forecasts have shifted since AI 2027 and our last update](https://datawrapper.dwcdn.net/4aHow/2/)

We describe in the appendix:

1.  [[#^how-our-agi-forecasts]].
    
2.  We [[#^explicitly-simulating-the-training|changed the modeling]] to take into account that training is needed to apply software improvements, which reduces the chance of very fast takeoffs.
    
3.  Some authors made [[#^research-taste-parameter-adjustments|minor adjustments to some other parameters]], and we [[#^clarification-regarding-what-were|clarify that our forecasts are conditional on going as fast as is technically feasible]].
    
4.  We made some [[#^various-minor-code-changes|minor changes]] to the model and website code.
    

## A 3-parameter uplift model for predicting when Automated Coder will arrive ^a-3-parameter-uplift-model

A simple method to predict the AC arrival date is to assume that (coding uplift - 1) grows exponentially. We think that this is the best simple model for predicting when AC will arrive.

Specifically, this model takes as input 3 parameters, for which we list Daniel’s median estimates:

**Present day coding uplift, i.e. the speedup factor due to AI assistance: 2x.** Daniel thinks 1.04x is something like a lower bound given the [METR study](https://metr.org/blog/2026-02-24-uplift-update) which found 1.04x - 1.2x uplift, with METR thinking that these numbers were biased downward due to selection effects (people were less likely to participate in the study if they thought AI would be useful to them.) Otherwise, he’s integrating various sources of evidence including the [Apr 2026 Anthropic internal survey](https://www-cdn.anthropic.com/08ab9158070959f88f296514c21b7facce6f52bc.pdf#page=44) having a geometric mean of 4x, and a private estimate of 1.7x AI R&D labor uplift by Ryan Greenblatt (which was an estimate for AI R&D labor as a whole, so presumably coding-only would be higher).

**Present day doubling time of the quantity (uplift-1): 5 months.** According to Anthropic employee surveys, coding uplift has gone from 1.25x to 4x in 7 months.[^note-2] This would be a ~2 month uplift doubling time, but correcting for Mythos Preview being above the long-term Anthropic ECI trend gives us a ~3.5 month doubling time.[^note-3]

Now, probably their employees are biased towards overestimating coding uplift. But unless the bias has been significantly increasing over time, that’s still more than three doublings of uplift-1 in less than a year – a 3.6 month doubling time! Daniel’s median is longer, 5 months, because he’s partly deferring to the opinions of other researchers he respects (Eli and Ryan) whose subjective sense is that the doubling time is longer.

**Uplift corresponding to AC: 20x.** The full AI Futures Model says 32x in the median case, but we expect the true uplift to be a little lower because the model doesn’t account for the fact that AIs can be used to accomplish coding tasks less efficiently than humans.

Comparing Daniel’s median estimates with Eli and Brendan’s:

[Datawrapper table: Coding uplift median parameter estimates](https://datawrapper.dwcdn.net/ts1bS/2/)

This simple model extrapolates the uplift trend (assuming the doubling time stays constant, i.e. the trend is exponential)[^note-4] and sees when it reaches the uplift corresponding to AC.

What does this method say? **See [ac-arrival.vercel.app](https://ac-arrival.vercel.app/) for a vibe-coded app in which you can play around with the simple extrapolation.**

![Screenshot of ac-arrival.vercel.app: simple 3-parameter uplift extrapolation with Daniel's medians (present-day uplift 2, doubling time 5 months, uplift at AC 20x), giving Automated Coder arrival in May 2028.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img2-6a11486a.webp)

See [[#^uplift|below]] for a more complicated version that uses present day uplift and uplift doubling times as anchors for setting the behavior of the full AI Futures Model. Factors that are accounted for in the full model are:

1.  The (uplift-1) doubling time decreases over time because the percentage of coding tasks automated is modeled as a logistic curve with an asymptote above 1. (If the asymptote was at exactly 1, then that would mean there would always be some important coding tasks that humans do better than AIs, which we think is unrealistic; eventually AIs will be able to do all of them.) However, even in the full model the trend is approximately exponential when far from AC.
    
2.  Changes in the effective compute growth rate caused by AI R&D automation, human labor trends, and compute trends.
    

The full model doesn’t have uplift at AC set as a parameter, instead it is inferred from model behavior.

## Adding uplift and revenue anchors to the AI Futures Model ^adding-uplift-and-revenue

We’ll now discuss how uplift and revenue estimates can be used to estimate the effective compute required for AC by anchoring the AI Futures Model.

Our overall forecast is made by using each method separately and then aggregating the results via a weighted mixture. You can explore the uplift-anchored version of the model at [aifuturesmodel.com](http://aifuturesmodel.com/) and the revenue (and time horizon) option via the dropdown at the top of the second graph.

We give the following weights:

[Datawrapper table: Weight given to different Automated Coder forecasting methods](https://datawrapper.dwcdn.net/1ycZM/1/)

We give the most weight to uplift because (a) the value corresponding to AC is more clear than for revenue or time horizon and (b) the trajectory of (uplift - 1) seems closer to exponential in log(effective compute) than for time horizon. The main advantage of time horizon relative to uplift is that it’s more measurable, and the main advantage relative to revenue is that it’s a more direct measurement of coding capabilities.

#### Uplift ^uplift

Our model already issues predictions about coding uplift, so we aren’t fitting an entirely new function and AC requirement like for the other two methods.

There is a module in the AI Futures Model (AIFM) which aggregates human labor and AI agents to produce an estimated “aggregate coding labor” (and therefore an estimated coding uplift) at each capability level. This module is generally calibrated by three degrees of freedom:

-   One is pinned down by the uplift at present day
    
-   Another parameter sets the “shape” of the distribution of coding task difficulties (e.g. is there a long tail of capability levels where AIs can’t yet do all tasks, despite having been able to do _most_ tasks at much lower capability? Or does automation happen more “all at once” in capability space?)
    
-   The last degree of freedom is the capability level (in effective compute or [ECI](https://epoch.ai/benchmarks?view=graph&tab=eci)) where the definition of AC actually becomes satisfied, that is, when AIs alone can do the full spectrum of tasks so that you’d rather hire only AIs than only humans.
    

In time horizon and revenue mode, we use one of those trends to choose the capability level pinning down the third degree of freedom. In uplift mode, we don’t directly specify the capability level corresponding to AC, and instead we constrain the remaining degree of freedom by specifying the rate at which coding uplift is increasing today (specifically, the doubling time of uplift - 1). With the automation module calibrated, we can then read off the capability level corresponding to the AC definition, and therefore the AC date.

#### Revenue ^revenue

We fit a function from AI capabilities (operationalized as effective compute or [ECI](https://epoch.ai/benchmarks?view=graph&tab=eci)) to leading AI company annualized revenue (specifically, the leading AI model developer’s revenue; so not including Nvidia). In particular, we fit an exponential function from ECI to annualized revenue (equivalent in our model to an exponential function from log(effective compute) to annualized revenue). We extrapolate the function into the future, and make guesses about which level of AI company revenue would correspond to having just achieved the AC milestone.

We estimate the following median parameters:

[Datawrapper table: Annualized revenue median parameter estimates](https://datawrapper.dwcdn.net/N9NuP/1/)

Modeling annualized revenue as an exponential function of ECI is a bit more sophisticated than modeling it as a function of time; it allows us to incorporate effects like a slowdown in datacenter growth or a feedback loop from AI R&D automation. Empirically, revenue has grown by 10x for every 15 ECI points so far. However, this method doesn’t take into account various other drivers of revenue growth besides capabilities (such as % of total compute allocated to inference and inference margins). It also doesn’t take into account that even holding those factors constant, revenue might not be an exponential function of ECI.

We try to intuitively take these factors into account by our choice of parameter values — even though Anthropic’s annualized revenue has grown 10x/yr for several years, we think it’ll slow down soon, and use 5-7x/yr as our median current growth rate.

## Update to the grading of AI 2027’s predictions ^update-to-the-grading

### Comparing the AI 2027 pace of progress to reality ^comparing-the-ai-2027

We’ve updated our assessment of how the pace of AI progress has compared to AI 2027. Depending on what metrics you include and what aggregation method you use, reality seems to be going at roughly 70-90% the speed of AI 2027. That’s the quantitative assessment. The qualitative assessment will be discussed in the next section.

[Datawrapper chart: AI is progressing at about 75% of the pace of AI 2027](https://datawrapper.dwcdn.net/H4G09/2/) — Though it depends on which indicators you most trust. Each number represents the aggregate pace of progress for a category of predictions in AI 2027, as graded in Aug 2026. A number N means that reality is progressing at Nx the pace it did in AI 2027.

If progress were to continue at 75% of the pace of AI 2027, Automated Coder would be reached in mid-2027.[^note-5]

Part of the reason that the relative uplift pace of progress is so much lower than the others is that since publication, we’ve revised our estimates downward for what AI software R&D uplift was at the _beginning_ of AI 2027. This is reflecting a real way that we estimate reality is behind schedule, but it makes the “pace” of progress framing not as natural as the others.

As for the public salience metric, which is our biggest predictive error, we wonder if we should have picked a better operationalization. AI does seem much more salient today than it was a year ago, even if that particular survey isn’t showing any progress.

A few minor methodological changes we’ve made since [our previous evaluation](https://blog.aifutures.org/p/grading-ai-2027s-2025-predictions):

-   We removed old predictions from the evaluation, in particular mid-2025 benchmark predictions and late-2025 compute predictions. We also didn’t evaluate the prediction for DeepCent’s compute budget (i.e., the largest Chinese company’s compute budget) because we have too little data on the current value.
    
-   We separately estimated public and internal AI software R&D uplift; previously we had estimated one number to grade against both AI 2027 estimates.
    

Details about the estimates can be found in [this spreadsheet](https://docs.google.com/spreadsheets/d/1JfEJRIwGe7fSCIW14eC7q0sEhVWHEdetykVh9g9XnF8/edit?gid=1928509176#gid=1928509176).

### Grading other predictions ^grading-other-predictions

Whereas the early 2026 section in AI 2027 was very on-point (it was titled “Coding Automation”) the mid-2026 section seems more of a miss:

![Excerpt of the Mid 2026 'China Wakes Up' section of AI 2027, describing the CCP nationalizing Chinese AI research into a DeepCent-led collective, a Centralized Development Zone at Tianwan, and weighing stealing OpenBrain's weights.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img3-971ebf34.webp)

We aren’t China experts, but we probably would have heard by now if the CCP had consolidated the various Chinese AI projects and heavily prioritized acquiring compute. In general it seems that “China Wakes Up” has not yet happened. That said, we expect there has been _some_ degree of AGI wakeup in China, as there has been across the world.

Other notes:

-   “About six months behind the best OpenBrain models” seems basically right; [this analysis](https://epoch.ai/data-insights/us-vs-china-eci) shows about a 7 month gap according to the ECI meta-benchmark.
    
-   We don’t have a great sense of how much compute China has right now but 12% still seems like a reasonable estimate.
    
-   We say that OpenBrain has improved security to [SL3](https://www.rand.org/pubs/research_briefs/RBA2849-1.html#:~:text=What%20Are%20the%20Security%20Needs%20of%20Different%20AI%20Systems%3F): “protection against cybercrime syndicates and insider threats. This includes world-renowned criminal hacker groups, well-resourced terrorist organizations, and disgruntled employees.” It’s unclear how to count current AI agents in this classification scheme, but [Anthropic and OpenAI are not secure against them yet](https://www.weforum.org/stories/cybersecurity/ai-organizations-reveal-agents-hacked-other-companies-and-other-cybersecurity-news/), which makes us think that they don’t deserve the SL3 designation. That said, if we were to only focus on model weight security instead of security more broadly, perhaps the situation looks better.
    

## Updated forecasts ^updated-forecasts

### Daniel ^daniel

I’m struck by the fact that all three AC extrapolation methods gave basically the same answer, independently: ([link](https://aifuturesmodel.com/forecast/daniel-08-16-26?takeoff=ASI%2CTED-AI&breakout=1&show=model))

![Chart: cumulative probability of Automated Coder arrival under Daniel's Aug 2026 model-based forecast, broken out by AC-anchor method. Revenue anchor p50 Feb 2028, time-horizon anchor p50 Feb 2028, uplift-solved anchor p50 Oct 2027 - the three methods closely agree; overall model p50 Dec 2027.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img4-98a9f397.webp)

I didn’t do the math in my head, I just made guesses about the parameters and then we calculated the results. I think this is some reason to be somewhat more confident in these predictions.

Another source of evidence I’d like to incorporate is the AI 2027 grading / tracking. In a nutshell, the methodology is:

1.  Make a detailed, concrete trajectory of how you think the future will go.
    
2.  Wait a while.
    
3.  Check to see if things are roughly on track, or are veering off in a different direction entirely. If they are roughly on track, quantitatively estimate how fast progress is going in reality vs. your scenario.
    
4.  Adjust your guess about how the future will go, to be correspondingly faster or slower.
    

It still seems like things are roughly on track for AI 2027, just going a bit slower. How much slower? About 75% speed, as mentioned [[#^comparing-the-ai-2027|above]]. This would predict AC happening in mid-2027. If we think it’s more like 60% speed, then that would predict early 2028. Again, interesting convergence with the other three methods.

Are there any other major factors to consider, in forming my all-things-considered views? Well there are [many other things to say](https://blog.aifutures.org/p/ai-futures-model-dec-2025-update?open=false#%C2%A7why-our-approach-to-modeling-comparing-to-other-approaches), but overall I’m pretty happy with what I’ve said so far as a summary of the most important points. I’m not aware of any other arguments or considerations strong enough to push me significantly away from the above. So I’ll just go with what the model says for AC, except slightly more confident since all 3 anchoring methods give similar results, and one month sooner to incorporate the 75% AI 2027 speed method. ([link](https://aifuturesmodel.com/forecast/daniel-08-16-26?takeoff=ASI%2CTED-AI))

![Chart: Daniel's all-things-considered Automated Coder forecast, Aug 2026 (p50 Dec 2027) vs Apr 2026 (p50 May 2028), probability density.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img5-c848c157.webp)

Here’s how my forecast has changed since April: ([link](https://aifuturesmodel.com/forecast/daniel-08-16-26?cmode=forecaster&csim=daniel-04-02-26&ctype=atc))

![Chart: Daniel's model-based Automated Coder forecast, Aug 2026 (p50 Dec 2027) vs Apr 2026 (p50 Feb 2028), cumulative probability.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img6-861e3f54.webp)

I increase the speed of post-AC takeoff for reasons [previously described](https://blog.aifutures.org/i/182911449/daniel). ([link](https://aifuturesmodel.com/forecast/daniel-08-16-26?takeoff=ASI%2CTED-AI))

![Chart: Daniel's Aug 2026 takeoff forecast - time from Automated Coder to TED-AI and to ASI, model-based vs all-things-considered, cumulative probability. All-things-considered p50s: 8.9 months to TED-AI, 1 year to ASI.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img7-d01c8638.webp)

My forecasts for the arrival date of AC, TED-AI, and ASI: ([link](https://aifuturesmodel.com/forecast/daniel-08-16-26?timeline=AC%2CTED-AI%2CASI&show=atc))

![Chart: Daniel's Aug 2026 all-things-considered forecasts for AC (p50 Nov 2027), TED-AI (p50 Nov 2028), and ASI (p50 Mar 2029) arrival dates, probability density.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img8-6db11deb.webp)

### Eli ^eli

The top adjustments I apply to get my AC timelines are:

-   **Unknown model limitations and mistakes.** With our previous (AI 2027) timelines model, my instinct was to push my overall forecasts longer due to unknown unknowns, and I'm glad I did. My median for SC (the superhuman coder milestone, similar but somewhat stronger than the automated coder milestone) was 2030 as opposed to the model's output of Dec 2028, and I now think that the former looks more right. I again want to lengthen my overall forecasts for this reason, but by less than last time because our new model is much more well-tested and well-considered than our previous one, and is thus less likely to have simple bugs or unknown simple conceptual issues.
    
-   **Data bottlenecks.** Our model implicitly assumes now that any data progress is proportional to algorithmic progress. But data in practice could be either more or less bottlenecking. My guess is that modeling data would lengthen timelines a bit, at least in cases where synthetic data is tough to fully rely upon.
    

My all-things-considered adjustment: ([link](https://aifuturesmodel.com/forecast/eli-08-16-26))

![Chart: Eli's Aug 2026 model-based Automated Coder forecast (p50 Mar 2029) vs his all-things-considered adjustment (p50 Jan 2030), probability density.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img9-4604407d.webp)

And a comparison vs. April: ([link](https://aifuturesmodel.com/forecast/eli-08-16-26?cmode=forecaster&csim=eli-04-02-26&ctype=atc))

![Chart: Eli's all-things-considered Automated Coder forecast, Aug 2026 (p50 Jan 2030) vs Apr 2026 (p50 Jul 2030), probability density.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img10-e98003f9.webp)

Compared to the model’s takeoff predictions, I speed mine up, primarily to take into account automation of hardware R&D, hardware production, and general economic automation: ([link](https://aifuturesmodel.com/forecast/eli-08-16-26?takeoff=ASI%2CTED-AI))

![Chart: Eli's Aug 2026 takeoff forecast - time from Automated Coder to TED-AI and to ASI, model-based vs all-things-considered, cumulative probability. All-things-considered p50s: 1.1 years to TED-AI, 2 years to ASI.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img11-45fc3c90.webp)

My forecasts for the arrival date of AC, TED-AI, and ASI: ([link](https://aifuturesmodel.com/forecasteli-08-16-26?timeline=AC%2CTED-AI%2CASI&show=atc))

![Chart: Eli's Aug 2026 all-things-considered forecasts for AC (p50 Jan 2030), TED-AI (p50 Jul 2032), and ASI (p50 Jul 2033) arrival dates, probability density.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img12-594a7450.webp)

### Brendan ^brendan

This is my first set of parameters and all-things-considered views.

Various factors the model isn’t considering for timelines to AC:

1.  We are not tracking research taste as a timelines indicator; preliminary results from P-Zero Research indicate Opus 5 is at parity with “expert humans” in research taste on their verifiable tasks. (This is also an update towards AC sooner, because if human-level research taste is nearer than we previously guessed, that’s evidence that human-level coding ability is too.)
    
2.  It seems plausible that “epistemics and alignment” will be the bottleneck for AC. On one hand, this should already be priced into the uplift trend, since these issues have contributed to reduced uplift so far. But if these are gross complements with e.g. “narrow technical capability” and cannot be increased as quickly, then perhaps the uplift trend will slow down once we become “alignment bottlenecked”.
    
3.  The input time series are somewhat rough. They do not account very precisely for the rumored “pretraining overhang” Ryan has talked about, which might result in above-trend progress in 2026. They also haven’t been updated since last December, and my expectations for AI capex are more bullish than they were in December.
    
4.  Other unknown unknowns, which should shift the median later.
    

Overall, the model’s 70% on AC by Jan 2030 and nearly 90% by Jan 2035 feels too confident, so I reduce these to 60% and 80%.

Here is my all-things-considered adjustment: ([link](https://aifuturesmodel.com/forecast/brendan-08-16-26))

![Chart: Brendan's Aug 2026 model-based Automated Coder forecast (p50 Jul 2028) vs his all-things-considered forecast (p50 Jan 2029), probability density.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img13-bdc0ec35.webp)

For takeoff from AC to TED-AI:

1.  As usual, we don’t account for hardware R&D automation (or any sort of unprecedented speedup in compute production during takeoff). Accounting for it would make 5+ year takeoffs quite unlikely.
    
    1.  To try to adjust for this, I added a “maximum takeoff length” sampled uniformly from (infinity, ten years, five years, two years) and capped each simulation’s TED-AI date at the AC date plus this quantity.
        
2.  I also want to account for unknown serial bottlenecks that an idealized mathematical model like ours might not include (after all, in real life AI R&D has many more steps and interacting stages than are present in our model).[^note-6] I think this should mostly affect very short takeoffs, so with 25% probability, each rollout’s takeoff length is floored at 6 months.
    

To combine these changes to the model’s takeoff with my changes to the model’s timelines to AC, I also reweighted all the rollouts according to my all things considered distribution for AC. This yields the following distribution for TED-AI arrival: ([link](https://aifuturesmodel.com/forecast/brendan-08-16-26?timeline=TED-AI))

![Chart: Brendan's Aug 2026 model-based TED-AI forecast (p50 Sep 2030) vs his all-things-considered forecast (p50 Apr 2031), probability density.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img14-2448b3f5.webp)

:::callout {title="Appendix" collapse="closed"}
## Appendix ^appendix

### How our AGI forecasts have changed since 2021 ^how-our-agi-forecasts

Below, we include plots that extend our analysis of [how our views have changed since publishing AI 2027](https://blog.aifutures.org/p/clarifying-how-our-ai-timelines-forecasts). When we refer to AGI in the below plots, we mean Top-Expert-Dominating AI: an AI that is at least as good as top human experts at virtually all cognitive tasks.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img15-15d7e77a.webp)

Zooming in on the changes since 2024:

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img16-d07074c2.webp)

### Explicitly simulating the training run of the leading AI model ^explicitly-simulating-the-training

This was originally motivated by our research for Plan A; see [Plan A Takeoff Forecast](https://ai-2040.com/supplements/takeoff-forecast)

We think this improves our takeoff speed estimates. But also, it allows us to predict the effect of various policies to [pace the frontier](https://blog.aifutures.org/p/how-to-pace-the-us-frontier) that involve reducing compute available for AI development.

Incorporating this change leads to a somewhat slower takeoff; see the charts below for how it affected model predictions given each of Daniel and Eli’s parameter estimates.

![Chart: explicitly simulating the training run slows the fastest takeoffs and leaves slow ones unchanged, Daniel's config, 400 seed-matched pairs. Median AC-to-ASI gap rises from 1.22 to 1.72 years; scatter shows short takeoffs slowed most.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img17-1f677279.webp)

![Chart: same continuous-training comparison under Eli's production config. Median AC-to-ASI gap rises from 3.86 to 4.56 years, with short takeoffs slowed most.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/lifland-q2-5-2026-timelines-update-uplift-and-revenue-img18-f9bb9d77.webp)

### Research taste parameter adjustments ^research-taste-parameter-adjustments

Based on a forthcoming research taste evaluation from P-Zero Research which updated us toward faster research taste progress, Eli adjusted his:

1.  Automated research taste slope median up from 2.1 to 2.3.
    
2.  Median to top taste multiplier median up from 3.7 to 4.
    

Brendan’s median estimates of 2.69 and 4.35 were influenced by this research as well. Daniel didn’t update his estimates as the research taste slope estimate of 3 was already higher than Brendan and Eli’s, and his median to top taste multiplier estimate of 4 was very similar.

### Clarification regarding what we’re forecasting ^clarification-regarding-what-were

We have previously not been very clear on whether we’re forecasting when AI milestones will actually appear in the world, or whether we are assuming things go as fast as is technically feasible; e.g., assuming that there isn’t government intervention to slow down AI. In our supplementary materials, we implied that we were adjusting for non-technical slowdowns. But in practice, we hadn’t thought much about this and some of us were explicitly assuming the opposite.

**We’ve discussed this issue, and we’ve decided that from now on our forecasts are for what will happen conditional on things going as fast as is technically feasible.** We think this is more informative to forecast than to attempt to account for the likelihood of various levels of slowdown. We’ve edited our supplementary materials to reflect this.

### Various minor code changes ^various-minor-code-changes

We had formerly been making use of an approximation that the rate of progress at the present day matches what it would have been in a counterfactual “human-only” trajectory, which is easier to simulate. But that assumption is increasingly false, since AIs are (in our estimation) starting to non-negligibly speed things up. In particular, this assumption would have caused us to underestimate the rate of effective compute growth that underlies today's observed progress rates on things like time horizon. We’d then be plugging in our actual (with-automation) model trajectory to that calibrated relationship, resulting in an incorrectly sped-up prediction that would underestimate time required to e.g. reach automated coder.

We reconfigured the front page a bit, adding a few extra metrics. We switched to showing Epoch Capabilities Index by default instead of “effective compute”.

(Why privilege ECI like this, as opposed to time horizon or any other metric? Technically, effective compute _requires_ an underlying capability metric to define, since you need to measure software efficiency in terms of training compute required to reach “equal capability level” (which requires a metric). Also, the idea of “training compute” as a single scalar that determines capability seems increasingly fraught).

We model ECI as the unique affine transform of log(effective compute) satisfying the properties that:

-   The current effective compute maps to the current ECI (today, 161)
    
-   The current growth rate of effective compute maps to the current ECI growth rate (today, 15 pts/yr)
    
-   This is the same as saying that each OOM of training compute adds a constant number of ECI points, and that the ECI reachable at a given training compute otherwise grows at a (currently) constant number of points per year, via the process of software R&D.

:::

[^note-1]: It’s possible we were subconsciously biased to confirm our existing views when choosing parameter estimates, but we did our best not to look at results when doing so. An exception is that Eli looked at the results of the simplified uplift model before setting his uplift parameters.
[^note-2]: Sonnet 4.5 (Sep 25): median 1.25x (selected for top 30 Claude Code usage); Mythos Preview (Apr 7 26, Feb 24 internal deployment): 4x geomean
[^note-3]: Since we’re using these numbers only to calibrate a relationship between uplift minus 1 and general capabilities, we obtain 3.5 months by reading off the release date of Mythos Preview as though it had been on the long term AECI trend rather than its actual release date.
[^note-4]: Steady exponential growth is a reasonable default assumption for many metrics in AI and roughly matches our past estimates. Our more sophisticated modeling suggests that progress will look exponential for some time until the trend goes superexponential as we approach AC.
[^note-5]: (2027-2025.25)\*(1/.75)+2025.25
[^note-6]: One example: until recently, we weren’t accounting for the [[#^explicitly-simulating-the-training|time required to retrain models with new algorithms during takeoff]]. There might be similar things we haven’t thought of yet.
