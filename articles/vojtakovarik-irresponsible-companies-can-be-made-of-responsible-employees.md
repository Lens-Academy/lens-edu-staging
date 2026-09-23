---
title: "Irresponsible Companies Can Be Made of Responsible Employees"
author:
  - "VojtaKovarik"
source_url: "https://www.lesswrong.com/posts/8W5YjMhnBsbWAeuhu/irresponsible-companies-can-be-made-of-responsible-employees"
published: 2025-10-08
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "tl;dr:  •  1. In terms of financial interests of an AI company, bankruptcy and the world ending are both equally bad. If a company acted in line with…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

**tl;dr:** 

1.  In terms of financial interests of an AI company, bankruptcy and the world ending are both equally bad. _If_ a company acted in line with its financial interests[^note-1], it would happily accept significant extinction risk for increased revenue.
2.  There are plausible mechanisms which _would_ allow a company to act like this _even if virtually every employee would prefer the opposite_. (For example, selectively hiring people with biased beliefs or exploiting collective action problems.)
3.  In particular, you can hold that an AI _company_ is completely untrustworthy even if you believe that all of its _employees_ are fine people.

**Epistemic status & disclaimers:** The mechanisms I describe definitely play _some_ role in real AI companies. But in practice, there are more things going on simultaneously and this post is not trying to give a full picture.[^note-2][^note-3]Also, none of this is meant to be novel, but rather just putting existing things together and applying to AI risk.

# From financial point of view, bankruptcy is no worse than destroying the world ^from-financial-point-of

Let's leave aside the question how _real_ companies act. Instead, we start with a simple observation: _If_ all a company cared about were financial interests, bankruptcy and the world getting destroyed are equivalent. Unsurprisingly, this translates to undesirable decisions in various situations.

For example, consider an over-simplified scenario where an AI company somehow has precisely these two options[^note-4]:

-   Option A: 10% chance of destroying the world, 90% of nothing happening.
-   Option B: Certainty of losing 20% market share.

We could imagine that this corresponds to racing ahead (which risks causing the end of the world) and taking things slowly (which leads to a loss of revenue). But to simplify the discussion, we make the assumption that Option A has no benefit and everybody knows this. In this situation, _if_ the company was following its financial interests (and knew the numbers), it should take Option A -- deploy the AI and risk destroying the world.

However, companies are made of people, who might not be happy with risking the world. Shouldn't we expect that they would decide to take Option B instead? I am going to argue that this might not necessarily be the case. That is, that there are ways in which the company might end up taking Option A even if every employee would prefer Option B instead.

![Large right-arrow shape that is made out of many small arrows, all of which face left.](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/8W5YjMhnBsbWAeuhu/mdedyqbexhz4gbfcsihl)

# How to Not Act in Line with Employee Preferences ^how-to-not-act

It shouldn't come as a surprise that companies are good at getting people to act against their preferences. The basic example of this is paying people off. By giving people salary, we override their preference for staying home rather than working. Less benignly, an AI company might use a similar tactic to override people's reluctance to gamble with the world -- bribe them with obscene amounts of money and if that is not enough, dangle the chance to shape the future of the universe. However, accepting these bribes is morally questionable to say the least, and might not work on everybody -- and my claim was that AI companies might act irresponsibly even if all of their employees are good people. So later in this text, we will go over a few other mechanisms.

To preempt a possible misunderstanding: Getting a company to act like this does not require deliberate effort[^note-5] by individuals inside the company. Sure, things might go _easier_ if a supervillain CEO can have a meeting with mustache-twirling HR personnel, in order to figure out the best ways to get their employees to go along with profit seeking. And to some extent, [fiduciary duty](https://en.wikipedia.org/wiki/Fiduciary) might imply the CEO _should_ be doing this. But mostly, I expect most of these things to happen organically. Many of the mechanisms will be a part of the standard package for how to structure a modern business. Because companies compete and evolve over time, we should expect the most successful ones to have "adaptations" that help their bottom line.

So, what are some of the mechanisms that could help a company to pursue its financial interests even when they are at odds with what employees would naively prefer?

1.  [**Fiduciary duty**](https://en.wikipedia.org/wiki/Fiduciary)**.** This might not be the main driver of behaviour but being _supposed to_ act in the interest of shareholders probably does make a difference.[^note-6]
2.  **Selective hiring.** (a) The company could converge on a hiring policy that _selects for people whose beliefs are biased_, such that they genuinely believe that the actual best option is the one that is best for the bottom line. In the toy example, Option A carries a X% chance of extinction. The true value of X is 10, but suppose that people's beliefs about X are randomly distributed. If the company hires people who think that X is low enough to be acceptable, all of its employees will, mistakenly, genuinely believe that Option A is good for them.  
    (b) Similarly, the company could hire people who are shy to speak up.  
    (c) Or select for other traits or circumstances that make for compliant employees.
3.  **Firing dissenters as a coordination problem.** Let's assume that to act, the company needs all its employees to be on board. (Or more realistically, at least some of them.) Even if all employees were against some action, the company can still take it: Suppose that the company adopts a policy where if you dissent, you will be fired (or moved to a less relevant position, etc). But then, if you get replaced by somebody else who will comply, the bad thing happens anyway.[^note-7] So unless you can coordinate with the other employees (and potential hires), compliance will seem rational.
4.  **Compartmentalising undesirable information** (and other types of information control). In practice, the employees will have imperfect information about the risks. For example, imagine that nobody would find the 10% extinction risk acceptable -- but recognising that the risk exist would require knowing facts A, B, and C. This is simple to deal with: Make sure that different teams work on A, B, and C and that they don't talk to each other much. And to be safe, fire anybody who seems like they recognised the risk -- though in practice, they might even leave on their own.  
    (Uhm. You could also have a dedicated team that knows about the risk, as long as you keep them isolated and fire them[^note-8] periodically, before they have time to make friends.)
5.  **Many other things.** For example, setting up decision processes to favour certain views. Promoting the "right" people. Nominally taking the safety seriously, but sabotaging these efforts (eg, allocating resources in proportion to how much the team helps with the bottom line). People self-selecting into teams based on beliefs, and teams with different beliefs not talking to each other much. And gazzillion other things that I didn't think of.

(To reiterate, this list is meant as an existence proof rather than an accurate picture of the key dynamics responsible for the behaviour of AI companies.)

# Well... and why does this matter? ^well-and-why-does

I described some dynamics that could plausibly take place inside AI companies -- that probably _do_ take place there. But I would be curious to know what are the dynamics that _actually_ take place, _which of them matter how much_, and what is the overall effect. (For all I know, this could be towards responsible behaviour.) Looking at the actions that the companies took so far gives some information, but it isn't clear to me how, say, lobbying behaviour generalises to decisions about deploying superintelligence.

Why care about this? Partly, this just seems fascinating on its own. Partly, this seems important to understand if somebody wanted to make AI companies "more aligned" with society. Or it might be that AI companies are so fundamentally "misaligned" that gentle interventions are never going to be enough -- but if that was the case, it would be important to make a clearer case that this is so. Either way, understanding this topic better seems like a good next step. (If you have any pointers, I would be curious!)

Finally, I get the impression that there is general reluctance to engage with the possibility that AI companies are basically "pure evil" and should be viewed as completely untrustworthy.[^note-9] I am confused about why this is. But one guess is that it's because some equate "the company is evil" with "the employees are bad people". But this is incorrect: An AI company could be the most harmful entity in human history even if every single employee was a decent person. We should hesitate to accuse individual people, but this should not prevent us from recognising that the _organisation_ might be untrustworthy.

[^note-1]: When I mention following financial interests, I just mean the vague notion of seeking profits, revenue, shareholder value, influence, and things like that (and being somewhat decent at it). I don't think the exact details matter for the point of this post.  I definitely don't mean to imply that the company acts as a perfectly rational agent or that it is free of internal inefficiencies such as those described in [Immoral Mazes](https://www.lesswrong.com/s/kNANcHLNtJt5qeuSS) or [Recursive Middle Manager Hell](https://www.lesswrong.com/posts/pHfPvb4JMhGDr4B7n/recursive-middle-manager-hell).
[^note-2]: More precisely, there will be various dynamics in play. Some these push in the direction of following profits, others towards things like doing good or following the company's stated mission, and some just cause internal inefficiencies. I expect that the push towards profits will be stronger when there is stronger competition and higher financial stakes. But I don't have a confident take on where the overall balance lies. Similarly, I don't claim that the mechanisms I give here as examples (selective hiring and miscoordination) are the most important ones among those that push towards profit-following.
[^note-3]: Relatedly to footnotes 1 and 2, Richard Ngo made some good points about why the framing I adopt here is not the right one. (His post [Power Lies Trembling](https://www.mindthefuture.info/p/power-lies-trembling) is relevant and offers a good framing on dynamics inside countries -- but probably companies too.) Still, I think the dynamics I mention here are relevant too, and in the absence of knowing a better pointer to their discussion, this point was cheap enough to write.
[^note-4]: The scenario is over-simplified and unrealistic, but this shouldn't matter too much. The same dynamics should show up in many other cases as well.
[^note-5]: The post [Unconscious Economics](https://www.lesswrong.com/posts/PrCmeuBPC4XLDQz8C/unconscious-economics) feels relevant here.
[^note-6]: I am not sure how exactly this works and it interacts with "negative externalities" such as "unclear risk of extinction". There definitely is a threat of getting sued over this, but I am not sure how much this really matters, as opposed to serving as a convenient excuse to not rock the boat.
[^note-7]: This will be costly for the company as well. If nothing else, it causes delays and they will be replacing you by somebody less skilled (otherwise they would have hired them already). So I advocate for not complying with things you are against. But despite this, the coordination problems are definitely real and difficult to solve.
[^note-8]: To reiterate, this does not require deliberate plotting by anybody inside the company. You don't need to actually _fire_ those people; it should be enough to incidentally underfund them, or perhaps converge on a company culture where they leave on their own.
[^note-9]: I am not saying they definitely are. But I do view this as plausible enough that acting on it would seem reasonable.
