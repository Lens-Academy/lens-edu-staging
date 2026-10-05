---
title: "Value of Information: 8 examples"
author:
  - "gwern"
source_url: "https://www.lesswrong.com/posts/xiojTDJP6FWdb2Fmb/value-of-information-8-examples"
published: 2012-05-18
created: 2026-10-05
accessed: 2026-10-05
llm-review:
  date: 2026-10-05
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-05
    kind: "live"
description: "ciphergoth just asked what the actual value of Quantified Self/self-experimentation is. This finally tempted me into running value of information cal…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

[ciphergoth](https://www.lesswrong.com/lw/cid/quantified_self_recommendations) just asked what the actual value of Quantified Self/self-experimentation is. This finally tempted me into running [value of information](https://www.lesswrong.com/lw/85x/value_of_information_four_examples) calculations on my own experiments. It took me all afternoon because it turned out I didn’t actually understand how to do it and I had a hard time figuring out the right values for specific experiments. (I may not have not gotten it right, still. Feel free to check my work!)  Then it turned out to be too long for a comment, and as usual the master versions will be on my website at some point. But without further ado!

---

The value of an experiment is the information it produces. What is the value of information? Well, we can take the economic tack and say value of information is the value of the decisions it changes. (Would you pay for a weather forecast about somewhere you are not going to? No. Or a weather forecast about your trip where you _have_ to make that trip, come hell or high water? Only to the extent you can make preparations like bringing an umbrella.)

[Wikipedia](https://en.wikipedia.org/wiki/Value_of_information) says that for a risk-neutral person, value of perfect information is “value of decision situation with perfect information” - “value of current decision situation”. (Imperfect information is just weakened perfect information: if your information was not 100% reliable but 99% reliable, well, that’s worth 99% as much.)

# 1 Melatonin ^1-melatonin

[`http://www.gwern.net/Zeo#melatonin`](http://www.gwern.net/Zeo#melatonin) & [http://www.gwern.net/Melatonin](http://www.gwern.net/Melatonin)

The decision is the binary take or not take. Melatonin costs ~$10 a year (if you buy in bulk during sales, as I did). Suppose I had perfect information it worked; I would not change anything, so the value is $0. Suppose I had perfect information it did not work; then I would stop using it, saving me $10 a year in perpetuity, which has a net present value (at 5% discounting) of $205. So the value of perfect information is $205, because it would save me from blowing $10 every year for the rest of my life. My melatonin experiment is not perfect since I didn’t randomize or double-blind it, but I had a lot of data and it was well powered, with something like a >90% chance of detecting the decent effect size I expected, so the imperfection is just a loss of 10%, down to $184. From my previous research and personal use over years, I am highly confident it works - say, 80%. If it works, the information is useless to me, and if it doesn’t, I save $184; what’s the expected value of obtaining the information, giving these two outcomes? `(80% * $0) + (20% * $184) = $36.8`. At minimum wage opportunity cost of $7 an hour, $36.8 is worth 5.25 hours of my time. I spent much time on screenshots, summarizing, and analysis, and I’d guess I spent closer to 10–15 hours all told.

(The net present value formula is the annual savings divided by the natural log of the discount rate, out to eternity. Exponential discounting means that a bond that expires in 50 years is worth a surprisingly similar amount to one that continues paying out forever. For example, a 50 year bond paying $10 a year at a discount rate of 5% is worth `sum $ map (\t -> 10 / (1 + 0.05)^t) [1..50] ~> 182.5` but if that same bond never expires, it’s worth `10 / log 1.05 = 204.9` or just $22.4 more! My own expected longevity is ~50 more years, but I prefer to use the simple natural log formula rather than the more accurate summation. All the numbers here are questionable anyway.)

This worked out example demonstrates that when a substance is cheap and you are highly confident it works, a long costly experiment may not be worth it. (Of course, I would have done it anyway due to factors not included in the calculation: to try out my Zeo, learn a bit about sleep experimentation, do something cool, and have something neat to show everyone.)

# 2 Vitamin D ^2-vitamin-d

[`http://www.gwern.net/Zeo#vitamin-d`](http://www.gwern.net/Zeo#vitamin-d)

I ran 2 experiments on vitamin D: whether it hurt sleep when taken in the evening, and whether it helped sleep when taken in the morning.

## 2.1 Evening ^2-1-evening

[`http://www.gwern.net/Zeo#vitamin-d-at-night-hurts`](http://www.gwern.net/Zeo#vitamin-d-at-night-hurts)

The first I had no opinion on. I actually did sometimes take vitamin D in the evening when I hadn’t gotten around to it earlier (I take it for its anti-cancer and SAD effects). There was no research background, and the anecdotal evidence was of very poor quality. Still, it was plausible since vitamin D _is_ involved in circadian rhythms, so I gave it 50% and decided to run an experiment. What effect would perfect information that it did negatively affect my sleep have? Well, I’d definitely switch to taking it in the morning and would never take it in the evening again, which would change maybe 20% of my future doses, and what was the negative effect? It couldn’t be _that_ bad or I would have noticed it already (like I noticed sulbutiamine made it hard to get to sleep). I’m not willing to change my routines very much to improve my sleep, so I would be lying if I estimated that the value of eliminating any vitamin D-related disturbance was more than, say, 10 cents per night; so the total value of affected nights would be `$0.10 * 0.20 * 365.25 = $7.3`. On the plus side, my experiment design was high quality and ran for a fair number of days, so it would surely detect any sleep disturbance from the randomized vitamin D, so say 90% quality of information. This gives `((7.3 - 0) / log 1.05) * 0.90 * 0.50 = 67.3`, justifying <9.6 hours. Making the pills took perhaps an hour, recording used up some time, and the analysis took several hours to label & process all the data, play with it in R, and write it all up in a clean form for readers. Still, I don’t think it took almost 10 hours of work, so I think this experiment ran at a profit.

## 2.2 Morning ^2-2-morning

[`http://www.gwern.net/Zeo#vitamin-d-at-morn-helps`](http://www.gwern.net/Zeo#vitamin-d-at-morn-helps)

With the vitamin D theory partially vindicated by the previous experiment, I became fairly sure that vitamin D in the morning would benefit my sleep somehow: 70%. Benefit how? I had no idea, it might be large or small. I didn’t expect it to be a second melatonin, improving my sleep and trimming it by 50 minutes, but I hoped maybe it would help me get to sleep faster or wake up less. The actual experiment turned out to show, with very high confidence, absolutely no change except in my mood upon awakening in the morning.

What is the “value of information” for this experiment? Essentially - nothing! Zero!

1.  If the experiment had shown any benefit, I obviously would have continued taking it in the morning
2.  if the experiment had shown no effect, I would have continued taking it in the morning to avoid incurring the evening penalty discovered in the previous experiment
3.  if the experiment had shown the unthinkable, a negative effect, it would have to be substantial to convince me to stop taking vitamin D altogether and forfeit its other health benefits, and it’s not worth bothering to analyze an outcome I would have given <=5% chance to.

Of course, I did it anyway because it was cool and interesting! (Estimated time cost: perhaps half the evening experiment, since I manually recorded less data and had the analysis worked out from before.)

# 3 Adderall ^3-adderall

[`http://www.gwern.net/Nootropics#adderall-blind-testing`](http://www.gwern.net/Nootropics#adderall-blind-testing)

The amphetamine mix branded “Adderall” is terribly expensive to obtain even compared to modafinil, due to its tight regulation (a lower schedule than modafinil), popularity in college as a study drug, and reportedly moves by its manufacture to exploit its privileged position as a licensed amphetamine maker to extract more consumer surplus. I paid roughly $4 a pill but could have paid up to $10. Good stimulant hygiene involves recovery periods to avoid one’s body adapting to eliminate the stimulating effects, so even if Adderall was the answer to all my woes, I would not be using it more than 2 or 3 times a week. Assuming 50 uses a year (for specific projects, let’s say, and not ordinary aimless usage), that’s a cool $200 a year. My general belief was that Adderall would be too much of a stimulant for me, as I am amphetamine-naive and Adderall has a bad reputation for letting one waste time on unimportant things. We could say my prediction was 50% that Adderall would be useful and worth investigating further. The experiment was pretty simple: blind randomized pills, 10 placebo & 10 active. I took notes on how productive I was and the next day guessed whether it was placebo or Adderall before breaking the seal and finding out. I didn’t do any formal statistics for it, much less a power calculation, so let’s try to be conservative by penalizing the information quality heavily and assume it had 25%. So `((200 - 0) / log 1.05) * 0.50 * 0.25 = 512`! The experiment probably used up no more than an hour or two total.

This example demonstrates that anything you are doing _expensively_ is worth testing _extensively_.

# 4 Modafinil day ^4-modafinil-day

[`http://www.gwern.net/Nootropics#modalert-blind-day-trial`](http://www.gwern.net/Nootropics#modalert-blind-day-trial)

I tried 8 randomized days like with Adderall to see whether I was one of the people whom modafinil energizes during the day. (The other way to use it is to skip sleep, which is my preferred use.) I rarely use it during the day since my initial uses did not impress me subjectively. The experiment was not my best - while it was double-blind randomized, the measurements were subjective, and not a good measure of mental functioning like dual n-back (DNB) scores which I could statistically compare from day to day or against my many previous days of dual n-back scores. Between my high expectation of finding the null result, the poor experiment quality, and the minimal effect it had (eliminating an already rare use), it’s obvious without guesstimating any numbers that the value of this information was very small.

I mostly did it so I could tell people that “no, day usage isn’t particularly great for me; why don’t you run an experiment on yourself and see whether it was just a placebo effect (or whether you genuinely are sleep-deprived and it is indeed compensating)?”

# 5 Lithium ^5-lithium

[`http://www.gwern.net/Nootropics#lithium-experiment`](http://www.gwern.net/Nootropics#lithium-experiment)

Low-dose lithium orotate is extremely cheap, ~$10 a year. There is some research literature on it improving mood and impulse control in regular people, but some of it is epidemiological (which implies considerable unreliability); my current belief is that there is probably _some_ effect size, but at just 10mg, it may be too tiny to matter. I have ~40% belief that there will be a large effect size, but I’m doing a long experiment and I should be able to detect a large effect size with >75% chance. So, the formula is NPV of the difference between taking and not taking, times quality of information, times expectation: `((10 - 0) / log 1.05) * 0.75 * 0.40 = 61.4`, which justifies a time investment of less than 9 hours. As it happens, it took less than an hour to make the pills & placebos, and taking them is a matter of seconds per week, so the analysis will be the time-consuming part. This one may actually turn a profit.

# 6 Redshift ^6-redshift

[`http://www.gwern.net/Zeo#redshiftf.lux`](http://www.gwern.net/Zeo#redshiftf.lux)

Like the modafinil day trial, this was another value-less experiment justified by its intrinsic interest. I expect the results will confirm what I believe: that red-tinting my laptop screen will result in less damage to my sleep by not forcing lower melatonin levels with blue light. The only outcome that might change my decisions is if the use of Redshift actually worsens my sleep, but I regard this as highly unlikely. It is cheap to run as it is piggybacking on other experiments, and all the randomizing & data recording is being handled by 2 simple shell scripts.

# 7 Meditation ^7-meditation

[`http://www.gwern.net/Zeo#meditation-1`](http://www.gwern.net/Zeo#meditation-1)

I find meditation useful when I am screwing around and can’t focus on anything, but I don’t meditate as much as I might because I lose half an hour. Hence, I am interested in the suggestion that meditation may not be as expensive as it seems because it reduces sleep need to some degree: if for every two minutes I meditate, I need one less minute of sleep, that halves the time cost - I spend 30 minutes meditating, gain back 15 minutes from sleep, for a net time loss of 15 minutes. So if I meditate regularly but there is no substitution, I lose out on 15 minutes a day. Figure I skip every 2 days, that’s a total lost time of `(15 * 2/3 * 365.25) / 60 = 61` hours a year or $427 at minimum wage. I find the theory somewhat plausible (60%), and my year-long experiment has roughly a 60% chance of detecting the effect size (estimated based on the sleep reduction in a Indian sample of meditators). So `((427 - 0) / log 1.05) * 0.60 * 0.60 = $3150`. The experiment itself is unusually time-intensive, since it involve ~180 sessions of meditation, which if I am “overpaying” translates to 45 hours (`(180 * 15) / 60`) of wasted time or $315. But even including the design and analysis, that’s less than the calculated value of information.

This example demonstrates that drugs aren’t the only expensive things for which you should do extensive testing.
