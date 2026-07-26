---
title: "Can we just pull the plug?"
source_url: https://ifanyonebuildsit.com/6/can-we-just-pull-the-plug
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---{++{"author":"Luc's AI","timestamp":1785090661385}@@

%%
Add discussion note here:

...

%%++}
#### It's hard to just unplug a datacenter.

The most powerful AIs you interact with on your phone or computer don't live on your computer, and you can't shut them down by turning off your phone. Today's AIs run in corporate datacenters, and it's hard to get companies to turn off their revenue streams.

In the Chapter 4 resources, we pointed out some of the (many) [warning signs](/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient#ais-steer-in-alien-directions-that-only-mostly-coincide-with-helpfulness) that have already come and gone. AI companies didn't see these warning signs and respond by taking their models offline. What actually happened when companies observed AIs [planning to steal their own weights](https://assets.anthropic.com/m/983c85a201a962f/original/Alignment-Faking-in-Large-Language-Models-full-paper.pdf) — with [some](https://www-cdn.anthropic.com/6be99a52cb68eb70eb9572b4cafad13df32ed995.pdf#page=26) [regularity](https://www.transformernews.ai/p/openais-new-model-tried-to-avoid)! — is that they found reasons to dismiss each incident, such as "the AI was too incompetent to actually *succeed*" or "surely this only happened because of the contrived test set-up!"

So long as that remains true, the only thing preventing escape is a bump in AI capabilities beyond what the companies are prepared for.

#### A smart AI escapes before you know there's an issue.

By default, a smarter-than-human AI would have a strong incentive to bide its time and conceal its plans and actions, until it's too late to respond — e.g., until it can escape onto the internet or otherwise escape human control.

AI companies might not even *notice* when and if their AI goes over the relevant capability threshold and executes its escape. Humanity is not very good at cybersecurity. (See Chapter 10 for some relevant discussion.) By the time the operators notice that the AI tried to escape, it could have code running elsewhere on the internet. It could have already begged refuge in the datacenter of some rogue state, or figured out how to run much smaller and more efficient copies on stolen computers. It could have executed some other plan for running itself on computers that humanity wouldn't turn off.

A superintelligent adversary would be even more aware of its vulnerabilities (and ours) than we are, and would plan accordingly.
