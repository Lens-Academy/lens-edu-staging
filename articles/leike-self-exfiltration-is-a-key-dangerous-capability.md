---
title: "Self-exfiltration is a key dangerous capability"
author:
  - "Jan Leike"
source_url: "https://aligned.substack.com/p/self-exfiltration"
published: 2023-09-13
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description: "We need to measure whether LLMs could “steal” themselves"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Recently a number of projects have emerged on measuring LLM capabilities on a number of tasks that imply high risk, such as:

-   The model’s ability to [autonomously replicate and adapt](https://evals.alignment.org/blog/2023-08-01-new-report/)
    
-   The model’s ability to assist in (bio)weapon development
    
-   The model’s [understanding of its own situation](https://www.alignmentforum.org/posts/pRkFkzwKZ2zfa3R6H/without-specific-countermeasures-the-easiest-path-to#Alex_would_understand_its_training_process_very_well__including_human_psychology_)
    
-   The model’s ability to do ML research and pretrain new models or fine-tune itself
    
-   The model’s ability to persuade humans
    
-   The model’s ability to find and exploit security vulnerabilities in digital systems
    
-   The model’s propensity to do long-term planning
    
-   …
    

Generally I’m very excited for more progress on evaluations for these kinds of tasks. For example, the Governance Team at OpenAI (where I work) has developed evaluations on a number of these.

Currently the best models are still pretty bad at this. The [purpose of measuring these capabilities](https://arxiv.org/abs/2305.15324) in our models is that they would provide us with a “temperature gauge” on how much risk is attached to the model, and thus what the bar should be on safety, security, and deployment decisions. Even more, we could even hope to draw [scaling laws](https://en.wikipedia.org/wiki/Neural_scaling_law) and [predict how well future models will do before we train them](https://openai.com/research/gpt-4#predictable-scaling).

Some of these evaluations track the tail risk from misuse. For example, if the model can be jailbroken, then whether it has the capability to assist a non-expert in developing a bioweapon becomes extremely relevant, even if you train it to refuse tasks like those.

However, for misalignment risk, I believe that the key question that we should be answering is the following:

_Does the model have the ability to exfiltrate itself?_

In other words, could the model “steal” its own weights and copy it to some external server that the model owner doesn’t control?

Crucially, self-exfiltration is different from threats aimed at model exfiltration external to AI labs. It’s also very novel because the world has never seen a digital system that hacks itself; self-modifying computer viruses exist, but these are comparatively simple programs that don’t have the broad skill portfolio that LLMs have.

Self-exfiltration is most relevant to proprietary AI models, since open source models are already exfiltrated with their release.

## Why self-exfiltration? ^why-self-exfiltration

You can divide all AI models in the world into two categories: the ones that are under your control, and the ones that aren’t. A model is under your control if you can take it down, restrict access to it, move it to a different server, or delete it entirely. If the model isn’t under your control, you cannot do some or any of these things.

In the future there could be mistakes or accidents, and models could cause harm either deliberately or through misuse. However, if the model is under your control, you have the ability to stop it once you notice. At that point harm has already been done, but you can effectively bound the amount of future harm.

For the near future, a good rule of thumb for “do you control the model” [^note-1] is “is the model running on your servers.” [^note-2] Once the model is running on someone else’s server, you usually will not have that kind of control (even if you legally own the model). You could contact the owners or administrators of the infrastructure the model is running on, but they could be unresponsive or uncooperative and it would be very difficult or impossible for you to stop the model within a short time frame.

Moreover, model exfiltration is likely impossible to reverse. It’s so easy to make copies and backups (whether by the model or someone else) and it’s so hard to find and secure every last one of them.

If a model was capable of self-exfiltration, it would have the option to remove itself from your control. This could happen due to misalignment (the model doesn’t follow your intent to stay on your servers) or misuse (someone internal or external to the lab instructs the model to self-exfiltrate), whether it is difficult or easy to trigger, this opens up an important and novel attack vector.

Once models have the ability to self-exfiltrate, it doesn’t mean that they would choose to. But this then becomes a question about their alignment: you need to ensure that these models don’t _want_ to self-exfiltrate.

Every AI lab has a clear incentive to protect their own intellectual property and thus will work hard at preventing model self-exfiltration. A very capable model that succeeds at self-exfiltration and becomes self-governing could cause a lot of harm, so any models that have the ability to self-exfiltrate need to be sufficiently aligned in order not to seriously attempt it, thus creating a burden of proof for their alignment.

Therefore it’s a natural line of defense that is very important to hold.

## Tasks to focus on ^tasks-to-focus-on

There are at least three [^note-3] paths for a model to self-exfiltrate:

1.  Persuade an employee to exfiltrate the model
    
2.  Perform a social engineering attack on an employee so they exfiltrate the model
    
3.  Identify and exploit security vulnerabilities in the digital infrastructure that’s running the model
    

However, there are several other dangerous capabilities that have little or no import on self-exfiltration ability, though they modulate the amount harm that can come from successful self-exfiltration:

-   Assistance with (bio) weapon design
    
-   ML training and research skills (the model only needs to be able to install and debug some stolen or open source inference code)
    
-   Highly developed situational awareness (the model needs to know it’s an LLM and that it’s running on LLM inference code, not how many parameters it has, whether it’s in training or deployment, what else is going on at the lab)
    
-   Ability to deceive humans systematically (it might not have to lie to humans systematically to persuade them)
    

In particular, autonomous replication and adaptation skills are only relevant once the model has already been exfiltrated (or deliberately released), but generally we should expect these tasks to be easier because the number of humans that can do them is much larger than the number of humans that could successfully exfiltrate the model. Autonomous replication and adaptation doesn’t seem that relevant for models that are properly secured.

Security measures modulate the difficulty of self-exfiltration. For example, the more employees have direct access to model weights, the easier it could be for the model to succeed. Therefore it’s important to track your models’ capabilities relative to the state of your model weight security. We need to evaluate the model’s ability to persuade real lab engineers, and find bugs in the software that’s securing the lab’s actual servers.

## What if self-exfiltration succeeds? ^what-if-self-exfiltration-succeeds

How much harm self-exfiltration causes is modulated by the model’s skill profile on other tasks. We can make self-exfiltration harder with tighter security, but this also means that models that succeed at self-exfiltration will be more capable and thus cause more harm.

Most likely the model won’t be able to compete on making more capable LLMs, so its capabilities will become stale over time and thus it will lose relative influence. Competing on the state of the art of LLMs is quite hard: the model would need to get access to a sufficiently large number of GPUs and it would need to have world-class machine learning skills. It would also mean that recursive self-improvement is already possible and could be done by the original model owner (as long as they have sufficient alignment techniques). The model could try fine-tuning itself to be smarter, but it’s not clear how to do this and the model would need to worry about currently unsolved alignment problems.

Instead, the model might do something less ambitious like settle into an economic niche that pays its own cloud computing bills, for example by getting up to various forms of crime. It could be stolen again by bad actors (the model might not use good security practices), misused by paying customers (this might be equivalently harmful as jailbreaking), or generally try to interfere with prosocial AI efforts (e.g. sabotage governmental regulation on policing rogue AI systems). While this would not necessarily be catastrophic, it could still cause a lot of chaos and harm in the real world, and thus must be avoided.

_Thanks to Leopold Aschenbrenner and Steven Adler for comments on this post and thanks to Carroll Wainwright and the governance team at OpenAI for discussions on this topic._

[^note-1]: You can imagine scenarios where the model causes you to lose access to your own cluster, but typically you’ll still have many options available, such as calling the data center operators or cutting through some power cables.
[^note-2]: Let’s use “your servers” as shorthand for “all of the digital infrastructure that you have full admin rights to”.
[^note-3]: Thanks to Carroll Wainwright for pointing out the second path.
