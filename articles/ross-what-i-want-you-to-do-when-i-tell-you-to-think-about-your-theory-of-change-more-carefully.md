---
title: "What I want you to do when I tell you to “think about your theory of change more carefully”"
author:
  - "Roman Ross"
source_url: "https://www.lesswrong.com/posts/goiQeh3g2LvAMMEFg/what-i-want-you-to-do-when-i-tell-you-to-think-about-your"
published: 2026-09-12
created: 2026-11-01
accessed: 2026-11-01
llm-review:
  date: 2026-11-01
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-01
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_Summary: I worry that a lot of people enter into projects because they “seem good,” when actually, they miss a lot of important steps necessary for making a project that’s going to be especially impactful. This post argues that writing out a “theory of change” is important and gives examples of how to do this well._  

## Tell the full story ^tell-the-full-story

One thing that makes AI safety stand out from other EA cause areas is that it’s hard to directly measure the impact of various interventions. When comparing global health outcomes, you can measure the cost-effectiveness and impact of your treatment with RCTs. When estimating how many chicken-days you can affect by running a cage-free campaign, you can analyze the impact of similar past actions. However, in AI safety, we don’t have as many helpful feedback loops to see how good our work is. And while you might come up with some proxy for this, you can risk [Goodharting yourself](https://romansattic.substack.com/p/stop-goodharting-yourself) if you don’t understand your analytics properly.

To get around this, we try to make sure that our interventions have coherent and strong “theories of change”: detailed explanations of what needs to happen for a project to have a good impact on the world. Here’s what I mean by that:

**Some examples of theories of change that I think are underdeveloped and weak:**

-   I am going to create a benchmark for this aspect of AI capabilities. I am doing this because knowledge is good, and it would be good if there were more papers in the world that told people about current AI capabilities.
-   I am going to host meetings in my local community about AI safety because it’s important for people to understand how AI might affect their lives. 
-   I am going to run a [joint hiring round](https://forum.effectivealtruism.org/posts/bShQnWJjsithfxEqH/how-valuable-are-botecs) for various orgs in AI safety because I think orgs are duplicating their hiring work, and this seems inefficient. 

**Some examples of theories of change that I think are much better:**

-   I am going to create a benchmark for this aspect of AI capabilities. I am doing this because understanding how AI is progressing in this specific domain is crucial for knowing what threat models we should be preparing for in the future. For example, if AI hits a certain threshold on my benchmark, we’ll know that we should be much more concerned about a threat, but if it doesn’t seem to be improving, we shouldn’t worry as much. I’ll also implement pathways to communicate the accuracy of and importance of these results to the various people who are working in related spaces: if they need to tell policymakers that this is an especially large concern, then my benchmark will be accurate and reliable evidence that this is true, and it can push for stronger political will towards a regulation. This regulation, if done well, will ultimately reduce the risks from this specific threat.
-   Pausing or slowing AI development could allow us to do a lot more critical safety research, potentially letting us solve the hard problems of alignment. However, to get to the stage where we can initiate a pause, we need to do a lot of things, including convincing policymakers that this is something they should push for. To a large extent, policymakers are motivated by the voices of their constituents. However, many people are not well-educated on the current state of AI capabilities, or they’re not thinking very carefully about how these could escalate in the near future. I’m going to run a public outreach campaign that tries to make sure that the people these politicians take seriously are vocal about their concerns about AI, so we build the necessary political will for a pause.
-   A lot of organizations within AI safety are doing important technical research work to decrease existential risks from AI. However, they struggle to hire “generalists” who can complete a wide variety of the miscellaneous tasks they need done. This makes the time of their current generalists very valuable. By running a joint hiring round, I’m able to address some of the inefficiencies in their workflow, effectively giving them much more time to work on the other problems that their organizations need to address to function smoothly.

The theories of change in the second group are better not because they are longer, but because they “**backchain**” from the ultimate goal. This means that they have a clear vision of what “winning” looks like in AI safety, and what further steps are needed to take us there. How does your project fill in one of these critical steps? This also means you should have thought carefully about what the future could look like and have a developed “[theory of victory](https://firstscattering.com/p/you-need-a-theory-of-victory).”

## Find a metric ^find-a-metric

One trick that’s helpful for determining your theory of change is **finding a metric you could use to calculate your impact**. This forces you to tell a more coherent story about where the impact of your project comes from, and it helps you escape from [traps](https://forum.effectivealtruism.org/posts/CAKmytxqNaqiaWk96/don-t-forget-why-learning-is-important) where you repeatedly tell yourself, “My theory of change is that it’s good for knowledge to exist!” For example:

-   I might measure the impact of a research project in terms of the percentage of important cruxes resolved or new safety directions implemented by frontier labs.[^note-1]
-   I might measure the impact of a benchmark based on the number and importance of decisions we can make better judgments on. Alternatively, if my goal is to prove to people that AI capabilities are increasing more broadly, I might measure my impact in terms of the number of news reports that can now use my reliable resource, and how many academics/politicians/constituents might get to read those reports.
-   I might measure the impact of a fieldbuilding project in terms of value-aligned median-researcher AI safety worker hours produced.

For this trick to help, it doesn’t really matter if your metric is somewhat impossible to measure, or if your units are especially realistic. You’re not aiming to do a BOTEC; you’re aiming to think clearly about your goals.

I don’t think this trick is universally applicable. For example, I’m not sure how I would create a metric to measure the impact of policy work. I might try “number of people now willing to consider a pause on AI development a reasonable proposal” or “increase in lab willingness-to-pay for safety,” but these are confusing and illegible. Despite this, I still think that there are lots of other cases where developing metrics can help clarify your thinking.

## Lots of things “seem good” but are missing important steps to becoming impactful ^lots-of-things-seem

A common mistake I see people make is stopping a project at a point where an additional ~30% of its value is easily capturable with a few more additions/changes. Here are some examples:

-   A lot of research papers don’t immediately focus on making their results interpretable and helpful. They might pursue unimportant research directions, leave the most helpful conclusions unstated, or end with “more work is needed to (actually answer the question this paper was supposed to originally answer).” It’s good to actually [do the work you set out to do](https://substack.com/@romansattic/note/c-215606063?r=5fcaw0&utm_medium=ios&utm_source=notes-share-action)!
    -   One reason why I like [METR’s Time Horizon](https://metr.org/time-horizons/) is that the results are easily interpretable. I know what it means to say that 50% of the time, GPT 5 can complete tasks that take humans 3.5 hours to complete. I have no idea what it means to say that Claude Fable 5 scores 117 points higher than Claude Opus 4.6 on [EQ Bench 4](https://eqbench.com/).[^note-2]
-   Many people create helpful educational resources for people transitioning into AI safety, but they often don’t put enough effort into the outreach to capture the full benefits of completing the project. 
    -   One helpful intuition about this is that movies typically spend 50-100% of their production budget on marketing.[^note-3]
-   Many AI safety and EA groups will run successful outreach events but don’t have an easy way for new people to sign up to a mailing list. 

Understanding your project’s theory of change can be helpful for remembering that these steps are very important. 

## Lots of things “seem good” but are actually worse than nearby options ^lots-of-things-seem-2

Sometimes, thinking about your project in depth can make you realize there’s a better way to do the same thing. Examples:

-   [I think it’s unlikely that joint-hiring rounds produce more generalist-hours than direct outreach or fieldbuilding](https://forum.effectivealtruism.org/posts/bShQnWJjsithfxEqH/how-valuable-are-botecs).
-   Hosting presentations for a local community might be worse than filming presentations for YouTube or pitching stories to journalists directly.
-   Upon reflection, a research direction you’re curious about might not be that important, or it might not be that neglected. 

## Things to avoid when thinking about theories of change ^things-to-avoid-when

1.  Don’t worry too much about this if you expect the thing you’re doing to take less than two hours.
2.  Don’t overthink things too much. You can imagine reasons why anything might fail if you try hard enough, and you shouldn’t drive yourself into paralysis with skepticism. 
3.  If you’re in a fieldbuilding role, thinking too much about pushing people through “talent pipelines” can be harmful toward your goals. I’m uncertain about the best way to navigate this issue, but I don’t think you should treat/think about other people only as a means to an end.

## Final Note: ^final-note

If you think this post is missing anything or gets anything wrong, please say so in a comment. I intend to link this post to a bunch of people I talk to as a way of saving time, so your input will probably be heard by many people who would especially benefit from hearing it. 

[^note-1]: I’m not a technical researcher, so forgive me if this guess is horribly off-base.
[^note-2]: This isn’t to say that EQ Bench 4 is completely meaningless or unhelpful, only that I can’t easily figure out what it means or why it helps me.
[^note-3]: A counter-intuition is that recommendations from friends are the strongest form of advertising, and you only get that if your product is really really good. Still, if advertising is as cheap as making a LinkedIn post or dm-ing it to some people who might benefit from having it, advertising is probably worth it.
