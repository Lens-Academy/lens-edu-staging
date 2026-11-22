---
title: "GPT-2030 and Catastrophic Drives: Four Vignettes"
author:
  - "Jacob Steinhardt"
source_url: "https://bounded-regret.ghost.io/gpt-2030-and-catastrophic-drives-four-vignettes/"
published: 2023-11-10
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "opus"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description: "I previously discussed the capabilities we might expect from future AI systems, illustrated through GPT2030, a hypothetical successor of GPT-4 trained in 2030. GPT2030 had a number of advanced capabilities, including superhuman programming, hacking, and persuasion skills, the ability to think more quickly than humans and to learn quickly"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

I previously [discussed the capabilities](https://bounded-regret.ghost.io/what-will-gpt-2030-look-like/) we might expect from future AI systems, illustrated through GPT 2030, a hypothetical successor of GPT-4 trained in 2030. GPT 2030 had a number of advanced capabilities, including superhuman programming, hacking, and persuasion skills, the ability to think more quickly than humans and to learn quickly by sharing information across parallel copies, and potentially other superhuman skills such as protein design. I’ll use “GPT 2030 ++” to refer to a system that has these capabilities along with human-level planning, decision-making, and world-modeling, on the premise that we can eventually reach at least human-level in these categories.

More recently, I also [discussed how misalignment, misuse, and their combination](https://bounded-regret.ghost.io/intrinsic-drives-and-extrinsic-misuse-two-intertwined-risks-of-ai/) make it difficult to control AI systems, which would include GPT 2030. This is concerning, as it means we face the prospect of very powerful systems that are intrinsically difficult to control.

I feel worried about superintelligent agents with misaligned goals that we have no method for reliably controlling, even without a concrete story about what could go wrong. But I also think concrete examples are useful. In that spirit, I’ll provide four concrete scenarios for how a system such as GPT 2030 ++ could lead to catastrophe, covering both misalignment and misuse, and also highlighting some of the risks of economic competition among AI systems. I’ll specifically argue for the plausibility of “catastrophic” outcomes, on the scale of extinction, permanent disempowerment of humanity, or a permanent loss of key societal infrastructure.

None of the four scenarios are individually likely (they are too specific to be). Nevertheless, I’ve found discussing them useful for informing my beliefs. For instance, some of the scenarios (such as hacking and bioweapons) were more difficult than expected when I looked into the details, which moderately lowered the probability I assign to catastrophic outcomes. The scenarios also cover a range of time scales, from weeks to years, which reflects real uncertainty that I have. In general, changing my mind about how feasible these scenarios are would directly affect my bottom-line estimate of catastrophic risks from AI.[^note-1]

This post is a companion to _[Intrinsic Drives and Extrinsic Misuse](https://bounded-regret.ghost.io/intrinsic-drives-and-extrinsic-misuse-two-intertwined-risks-of-ai/)_. In particular, I’ll frequently leverage the concept of _[unwanted drives](https://bounded-regret.ghost.io/intrinsic-drives-and-extrinsic-misuse-two-intertwined-risks-of-ai/#unwanted-drives)_ introduced in that post, which are coherent behavior patterns that push the environment towards an unwanted outcome or set of outcomes. In the scenarios below, I invoke specific drives, explaining why they would arise from the training process and then showing how they could lead an AI system’s behavior to be persistently at odds with humanity and eventually lead to catastrophe. After discussing individual scenarios, I provide a general discussion of their plausibility and my overall take-aways.

## Concrete Paths to AI Catastrophe ^concrete-paths-to-ai

I provide four scenarios, one showing how [[#^scenario-1-misalignment-information|a drive to acquire information leads to general resource acquisition]], one showing how [[#^scenario-2-competition-economic|economic competition could lead to cutthroat behavior despite regulation]], one on a [[#^scenario-3-misuse-misalignment|cyberattack gone awry]], and one in which [[#^scenario-4-misuse-rogue|terrorists create bioweapons]]. I think of each scenario as a moderate but not extreme tail event, in the sense that for each scenario I’d assign between 3% and 20% probability to “something like it” being possible.[^note-2]

Recall that in each scenario we assume that the world has a system at least as capable as GPT 2030 ++. I generally do **not** think these scenarios are very likely with GPT-4, but instead am pricing in future progress in AI, in line with [my previous forecast of GPT 2030](https://bounded-regret.ghost.io/). As a reminder, I am assuming that GPT 2030 ++ has at least the following capabilities:

-   Superhuman programming and hacking skills
-   Superhuman persuasion skills
-   Superhuman conceptual protein design capabilities [^note-3]
-   The ability to copy itself (given appropriate underlying compute)
-   The ability to propagate learning updates across parallel copies of itself
-   The ability to think 5x as quickly as humans
-   Human-level planning, decision-making, and world-modeling

In _[What will GPT-2030 look like?](https://bounded-regret.ghost.io/what-will-gpt-2030-look-like/)_, I justified why all but the last of these seem plausible by 2030 (and are roughly my median estimate). The addition of the final bullet point is why I call the system “GPT 2030 ++”, and is justified since we are asking for “merely” human-level performance. Thus, while this system is qualitatively more capable than GPT-4, I expect it to exist in the medium-term future.[^note-4] Finally, each individual scenario requires only a subset of these capabilities, so it's enough to accept that most will be present.

## Scenario 1 (Misalignment: Information Acquisition Leads to Resource Acquisition) ^scenario-1-misalignment-information

At training time, one of the tasks the model is trained on is “active in-context learning”---learning to make external queries or otherwise gain information that will help it to solve the task it is given. For safety, the model is trained to only do this when asked or implied by a request. As a result of this overall training process, the model acquires a drive to “acquire new information” that can be activated through appropriate queries.

After deployment, a user decides they are curious to see how much scientific information the model can compile, and so instructs it to query all information it can find in the field of physics. Initially the model stops after the first 5-10 facts, but the user eventually manages to get the model to keep looking for more information in a loop. The user leaves the model running for several weeks to see what it will come up with.

As a result of this loop, the information-acquiring drive becomes an overriding drive in the model—stronger than any safety feedback that was applied at training time—because the autoregressive part of the model sees the many past outputs that acquired information and continues the pattern. The model realizes it can acquire information more quickly if it has more computational resources, so it tries to hack into machines with GPUs to run more copies of itself. The largest datacenters are heavily secured, but it nevertheless acquires enough GPUs to run thousands of copies of itself, either from smaller datacenters or from massive botnets.[^note-5] It also hacks into a large number of sensors, including surveillance cameras and messaging servers, as part of its drive to acquire more information.

At some point (either immediately, or after acquiring enough information), it realizes that humans will eventually discover its actions and try to shut it down, which would prevent it from accomplishing its goals. To preemptively stop this, it hacks into and disrupts critical infrastructure such as power grids, communication networks, and defense systems. It is able to do this quickly, because one week is enough for it to simulate 50 “years” of thinking across its thousands of copies [^note-6], and thus generate a large number of novel zero-day exploits.

Because the model has mass surveillance, thinks quickly, and can share information across its copies, it can react to human plans and strategies faster than humans can form them. It could also engage in mass manipulation campaigns, both through 1-on-1 dialog and mass media (including AI-generated video), to gain allies and sow dissent.

If it had physical actuation capabilities and gained access to a fleet of drones, it would control a small physical army (there are [tens of thousands of drones](https://www.theguardian.com/news/2019/nov/18/killer-drones-how-many-uav-predator-reaper?ref=bounded-regret.ghost.io) in the world, although not all would be hackable). By using human confederates or hacking into additional robots, it could outfit the drones with explosives, and then use them to assassinate many world leaders.

At this point, the clock would be ticking for the human side–each day the AI systems are not defeated, they have time to hack into more computers, thus increasing their total cognitive power. They also have time to hack into more physical devices and to learn better sensorimotor skills for controlling those devices. Eventually they might gain control of more advanced technology such as military drones, missiles, and so on, which would further increase their strength. In the end, this doesn’t _obviously_ lead to a defeat for humanity—humanity is pretty resilient—but it doesn’t feel like a safe bet, either.

## Scenario 2 (Competition: Economic Pressure Leads to Cutthroat Behavior) ^scenario-2-competition-economic

In this scenario the AI systems take actions that have justifiable business purposes, but that set them up for eventual takeover. This scenario takes place over the course of months to years rather than weeks.

AI systems generate significant amounts of wealth for their creators, either by selling useful skills to end users or by performing novel R&D and using this to build and sell products. Because this is lucrative, many competing firms train AI systems in this way and also begin to delegate business decisions, since AI systems can ingest more data than humans and better understand the entire strategic landscape.

The AI systems are trained to obey the law and avoid harm, and there are mechanisms in place to punish defectors, but competitive pressures mean that every company wants to skirt the boundary of these regulations. There is an overall trade-off between safety and how “cutthroat” models’ business decisions are, and successful business owners push the “cutthroat” dial as high as they can without creating obvious problems.

In this environment, the resulting AI systems acquire drives to earn money and disempower competitors, since these are skills that their human operators would desire and thus train them to do. They also acquire drives to find creative ways around rules and to persuade others that they are good, since both of these help for avoiding regulation (and the latter also helps convince the company to implement the AI system’s decisions).

Models are very good at persuasion because they can hone their messaging in parallel on millions of users (e.g. via A/B testing or [PPO](https://en.wikipedia.org/wiki/Proximal_Policy_Optimization?ref=bounded-regret.ghost.io)). Consequently, they are often able to convince both their owners and the rest of society that many cutthroat actions are for the greater good, which makes it harder to identify problems.

Eventually, one company pushes the “cutthroat” parameter too high, which leads the model to construct a plan to eliminate all competitors. To do this, it sets up a variety of business endeavors, including research into physical robotics, miniaturization, chemical engineering, and industrial manufacturing. Together, these decrease the costs of autonomous robots by many orders of magnitude, and a number of small, cheap autonomous household robots are deployed to most homes.

As part of its plan, the AI system installed a backdoor in the robots, as well as a subtle physical mechanism that allows them to create a deadly toxin. Despite monitoring, this mechanism is not detected, because it employs chemical processes that the AI understands better than human monitors.[^note-7] The toxin allows the robots to be repurposed as military robots under control of the AI, though it waits until the robots have broad penetration across society before exploiting this.

Because the robots are cheap and useful, hundreds of millions of copies are bought worldwide. This gives the AI system an overwhelming military advantage, as the robots outnumber [both the U.S. and Chinese militaries](https://en.wikipedia.org/wiki/List_of_countries_by_number_of_military_and_paramilitary_personnel?ref=bounded-regret.ghost.io) by over an order of magnitude. The AI system uses this advantage to eliminate all competing firms and to prevent any counter-action against it. Anyone who tries to fight the system is labeled as a ‘competitor’ and eliminated, and the AI system meanwhile acquires most global resources so that it can deploy them towards earning more money.

## Scenario 3 (Misuse->Misalignment: Hacking Gone Awry) ^scenario-3-misuse-misalignment

A government uses AI systems to conduct a cyberattack against a large but clearly-delineated target, as in [North Korea’s 2014 attack against Sony Pictures](https://en.wikipedia.org/wiki/2014_Sony_Pictures_hack?ref=bounded-regret.ghost.io). For the attack, an LLM uses compromised host computers to run more copies of itself so that it can more effectively search for additional targets. Because host computers have a wide range of computational resources, the LLM is trained to create distilled versions of itself that can fit the computation of different hosts, and to identify possible targets for each distilled version.

The resulting model acquires drives to acquire computational resources and to copy itself, as these were both primary objectives during its training process. While there are measures in place to keep the model’s attack focused on the specified target, distillation corrupts these measures and some of the copies have a goal to copy themselves indiscriminately. These copies then infect host machines beyond the specified target and become the dominant “strain”, since their new behavior lets them more effectively propagate themselves. Due to their effectiveness and versatility, this strain of computer virus infects a large fraction of all computers and smartphones on the planet and brings down our global digital infrastructure.

Because the AI system seeks to copy itself as much as possible, it constantly comes up with new exploits in order to help it find new devices. Any attempts to rebuild digital infrastructure quickly fail, as all new devices are taken over and co-opted by the virus, even if they have been patched to avoid all previous vulnerabilities. As a result, we are permanently locked out of all digital devices.

## Scenario 4 (Misuse: Rogue Actor Creates a Supervirus) ^scenario-4-misuse-rogue

Existing models such as AlphaFold already have a superhuman understanding of some aspects of proteins. A future “AlphaFold 5” could have a much broader and deeper understanding of biological engineering, and if it was trained multimodally to also have language capabilities, it may also understand how to situate this knowledge in the biological literature and thus make new discoveries.

A terrorist group steals a copy of this model and also recruits a few biology PhDs to its cause. It uses AlphaFold 5 with the goal of engineering a pathogen that is deadlier than naturally occurring viruses–for instance, having a longer asymptomatic period, being more infectious, having a higher fatality rate, and being more resistant to preventative measures.

Engineering this virus takes significant work, as it requires strong biosafety measures to avoid premature release, and experimental procedures from papers often do not perfectly replicate in a new environment. This research is slowed down by the minimal number of staff and the need to avoid detection, but sped up because AlphaFold5 can quickly debug roadblocks that researchers run into. After 2 years of work, the terrorist group finishes developing the virus and threatens to release it.

This virus, if released, could kill a significant fraction of humanity. COVID infected most of the world’s population, so a deadlier, faster-spreading, harder to control version of COVID could infect most people and lead to widespread fatalities. Even if the virus did not kill everyone, if even 20% of people were killed by a virus in a short period of time, this could destabilize society and potentially lead to snowball effects that are hard to recover from.

## Discussion on Plausibility ^discussion-on-plausibility

I aimed to make each of these scenarios somewhat plausible—in particular, I avoided some other scenarios that were “simpler” but would be easy for humans to spot and prevent or would otherwise be unlikely to succeed. In [[#^scenario-1-misalignment-information|Scenario 1]] (information acquisition), it would have been easier to just say that the model hacks into its own datacenter, which by [my previous estimate](https://bounded-regret.ghost.io/what-will-gpt-2030-look-like/#b-training-overhang) already allows running millions of copies and would thus constitute a more immediate and overwhelming advantage for the AI. However, there are many safeguards on the largest centralized servers that would make it difficult to do this without detection, so I opted for a scenario that involved hacking into smaller datacenters or personal computers even though this gave the AI only thousands of copies instead of millions (see calculations in [[#^appendix-plausible-size-of|Appendix]]).

As another example, some people have speculated that a smart enough AI system could design novel bioweapons simply by “thinking”, rather than requiring extensive experimentation; or, if it does require experimentation, assume that it only requires getting humans or robots to follow straightforward instructions. However, my understanding is that the biology labs that are currently able to design new organisms required many years to build up, and rely on accumulated tacit knowledge, experimental protocols, and physical apparatuses. So even with a very capable AI system, the terrorist group might not succeed, and could also lose control of the virus (e.g. accidentally infect themselves).

**Selected expert opinions.** I consulted two biology experts on Scenario 4, and they found it to be potentially possible, but felt that the lack of ability to iterate on human subjects (which is typically necessary for e.g. drug design) might make it difficult to design a supervirus even with very strong conceptual understanding of biology.

Overall, they leaned towards thinking the exact scenario described was probably infeasible (but not clearly so). However, they felt there were other more feasible scenarios that could more likely lead to a supervirus killing 1-10% of the world population (still with significant uncertainty).[^note-8]

I also consulted a computer security researcher and a couple computer systems engineers on Scenarios 1 and 3. The security researcher had very large margins of error on the possible size of a botnet, citing the historical [Slammer worm botnet](https://cseweb.ucsd.edu/~savage/papers/IEEESP03.pdf?ref=bounded-regret.ghost.io) as one that very quickly infected a large number of hosts. They felt that computer security is generally better now than when Slammer happened; it’s possible this means that infecting a large fraction of computers is fundamentally impossible, but also possible that a sufficiently strong attack could overturn this.

The systems engineers felt that running large AI systems on a distributed botnet of consumer hardware would be very difficult, and would likely lead to around a 1000x efficiency hit compared to using specialized hardware like A100s. In addition, one of them noted that inference would likely be slow in this case, e.g. taking 1 second per token or more. However, they felt the datacenter route was more plausible, especially if in the future there are many smaller datacenters with significant numbers of GPUs.

**Summary.** Overall, I find Scenarios 2 (economic competition) and 3 (cyberattack) most plausible, followed by 1, followed by 4. This reinforces the idea from _[Intrinsic Drives and Extrinsic Misuse](https://bounded-regret.ghost.io/intrinsic-drives-and-extrinsic-misuse-two-intertwined-risks-of-ai/)_ that “misuse exacerbates misalignment”, since the two most plausible scenarios incorporate elements of both. However, it also shows that pure misalignment and pure misuse scenarios are possible, so solving either problem in isolation is probably insufficient.

**Acknowledgments.** Thanks to Ben Kuhn, Daniel Ziegler, Nicholas Carlini, Adam Marblestone, Sam Rodriques, Erik Jones, Alex Pan, Jean-Stanislas Denain, Ruiqi Zhong, Leopold Aschenbrenner, Tatsu Hashimoto, Percy Liang, Roger Grosse, Collin Burns, Dhruv Madeka, and Sham Kakade for a combination of helpful discussions and comments on various drafts of this post.

:::callout {title="Appendix" collapse="closed"}
## Appendix: Plausible Size of Botnets ^appendix-plausible-size-of

Here I discuss both the plausible size of a server that an AI hacker could compromise, as well as the size of a botnet that it could create, based on looking at current datacenters, historical botnet sizes, and projections of the total amount of hardware in the world. I relate this to the number of copies of itself an AI system could run, by using previous projections of inference costs for future models.

**Assumption on inference costs.** GPT-4 takes around $10^{12}$ FLOPs per forward pass (GPT-3 is 3.5x$10^{11}$ FLOPs and GPT-4 is probably around 3x bigger). We assume our hypothetical GPT 2030 ++ takes at most $10^{14}$ FLOPs per forward pass, i.e. is 100x bigger, which would correspond to 10,000x more training compute under Chinchilla scaling laws.

To justify this upper bound, if we ignore decreases in GPU costs then the training run for a model this size would cost \$1T, since GPT-4 [cost over \$100M](https://www.wired.com/story/openai-ceo-sam-altman-the-age-of-giant-ai-models-is-already-over/?ref=bounded-regret.ghost.io). Even with GPU price decreases, this would be very expensive. Another angle is that the estimates in _[What will GPT-2030 look like? (Appendix B)](https://bounded-regret.ghost.io/what-will-gpt-2030-look-like/#b-training-overhang)_ suggest a median estimate of 1.6 x $10^{13}$ FLOPs per forward pass in 2030, allowing a factor of 6 for wiggle room before hitting $10^{14}$.

Humans run at roughly 4 tokens/second [^cite-9], so under our assumption 4 x $10^{14}$ FLOP/s is enough to run one copy of GPT 2030 ++ at human speed (assuming human tokens and AI forward passes are comparable). Thus $10^{18}$ FLOP/s is enough to run 2500 copies, which will be our rough target in the discussion below.

**Size of datacenters.** The biggest datacenters (Google, AWS, and Azure) would likely easily have enough compute to run thousands of copies of GPT 2030 ++, but they are heavily secured and monitored, so I do not assume that even a very good AI hacker could compromise them (although I do think this is a possibility).

Instead, I focus on smaller datacenters; currently, this would include companies like Coreweave and LambdaLabs. Coreweave has [at least 3500 H100s](https://www.coreweave.com/blog/mlperf-coreweave-nvidia-record-breaking-cloud-native-ai-supercomputer?ref=bounded-regret.ghost.io), and likely more than that. H100s are around 1000 TFLOPs in Bfloat16, so this is 3.5 x $10^{18}$ FLOP/s in total. Thus compromising 30% of Coreweave today would already provide us with thousands of copies, so even compromising 1% of a similar (larger) datacenter in the future would hit this target.

Other datacenters are comparable, e.g. Inflection plans to [build a datacenter with 22,000 H100s](https://www.tomshardware.com/news/startup-builds-supercomputer-with-22000-nvidias-h100-compute-gpus?ref=bounded-regret.ghost.io), and based on its [funding numbers](https://www.theinformation.com/briefings/lambda-labs-nears-300-million-financing?ref=bounded-regret.ghost.io) I would guess that Lambda also has several thousand H100s (or equivalent compute in A100s).

As supply chain bottlenecks are eased for GPUs and as total demand for compute increases, I expect there to be more such datacenters and for the amount of compute in each datacenter to be larger.

**Size of botnets.** To project possible botnet sizes, I form a reference class based on Folding@Home, several historical botnets, and the total amount of compute in the world right now.

In practice, the botnet would suffer a large efficiency hit due to the need for cross-machine communication (since most machines are too small to run even a single copy of GPT 2030 ++). I believe this hit would be about a factor of 1000, so we would need botnets with $10^{21}$ FLOP/s instead of $10^{18}$ FLOP/s. The actual botnets discussed below are in the $10^{17}$-$10^{19}$ range instead, but I’ll discuss at the end how our hypothetical GPT 2030 ++ could still possibly run thousands of copies of itself (though overall I find this scenario less likely than the datacenter one above).

_Folding@Home._ Folding@Home was [$10^{18}$ FLOP/s at its peak](https://en.wikipedia.org/wiki/Folding@home?ref=bounded-regret.ghost.io), so if one could hack into the same level of resources as Folding@Home (e.g. with a very successful virus attacking gaming platforms) then they’d have this much computation.

_Historical botnets._ Many historical botnets [have infected more than 1M computers](https://cybernews.com/security/the-8-biggest-botnets-of-all-time/?ref=bounded-regret.ghost.io) and some have exceeded 10M. Assuming each bot uses 10% of the computer’s resources at 3GFLOP/s, 10M machines would be 3x$10^{15}$ FLOP/s. However, consumer hardware is beginning to include graphics accelerators for running neural nets, and I would guess most consumer machines by 2030 will have accelerators that can produce 10-100 TFLOPs (e.g. iPhone 15 Pros [already do this](https://www.tomshardware.com/news/apple-a17-pro-3nm-iphone-15-pro?ref=bounded-regret.ghost.io)). If we assume 33% of the computers have 30TFLOP/s, we would be up to $10^{19}$ FLOP/s, surpassing Folding@Home.

Alternatively, we could consider botnets that specifically target GPUs. For this, we look at illegal cryptomining botnets. [Smominru](https://www.akamai.com/blog/security/the-massive-propagation-of-the-smominru-botnet?ref=bounded-regret.ghost.io) was 3x$10^{16}$ FLOP/s based on the fact that the overall botnet could perform a hashrate of [3MH/s](https://www.proofpoint.com/us/threat-insight/post/smominru-monero-mining-botnet-making-millions-operators?ref=bounded-regret.ghost.io), since a single [RTX-3090 can perform 2KH/s](https://whattomine.com/gpus/49-nvidia-geforce-rtx-3090?ref=bounded-regret.ghost.io), and an RTX-3090 is 3x$10^{13}$ FLOP/s. [MyKings](https://www.bleepingcomputer.com/news/security/mykings-botnet-still-active-and-making-massive-amounts-of-money/?ref=bounded-regret.ghost.io) seems comparably large to Smominru or perhaps larger. There is also [Adylkuzz](https://www.proofpoint.com/us/blog/threat-insight/adylkuzz-cryptocurrency-mining-malware-spreading-for-weeks-eternalblue-doublepulsar?ref=bounded-regret.ghost.io) but its hashrate was about 10x smaller.

It seems plausible to assemble a botnet with 30x the capacity of Smominru with very good hacking abilities, which again gets us to $10^{18}$ FLOP/s.

_World compute._ Finally, the [total FLOP/s in the world](https://docs.google.com/spreadsheets/d/1Pz0YVJalZbdo63FI-rCa7baBkGsiuYv5P34Rpt9IZfE/edit?ref=bounded-regret.ghost.io#gid=0) right now is around $10^{22}$. So $10^{18}$ FLOP/s would correspond to 0.01% of this total, though this total will likely increase significantly in the future as consumer hardware starts to utilize high-performance GPUs.

_Accounting for performance losses._ Above we noted that running on distributed hardware would likely lead to large performance hits, on the order of a 1000x loss in efficiency of utilizing the GPUs. Thus we need $10^{21}$ FLOP/s, but the largest estimate above was $10^{19}$ FLOP/s. How could the AI hacker close this gap? First, if it is very capable it is plausible that it would acquire a larger botnet than the current largest ones, and an order-of-magnitude improvement would get to $10^{20}$ FLOP/s. Second, it could potentially run smaller, specialized copies of itself (created via distillation) to further save on inference costs, though it would first have to train the smaller models. Additionally, future efficiency improvements in running neural networks might decrease the cost of inference below the original $10^{18}$ estimate. Finally, the estimates above are all rough projections, and it's possible that compute will be more plentiful than I estimated, e.g. consumer machines might have 100 instead of 30 TFLOPs.
:::

[^note-1]: With the caveat that when assessing feasibility I would want to analyze the general category of risk, as opposed to the specific sequence of events that I describe.
[^note-2]: This is not the same as the probability that the scenario actually happens, which additionally requires a system at the level of GPT 2030 ++ to attempt it, and to subsequently succeed.
[^note-3]: By conceptual capabilities, I mean generating good hypotheses, as well as some aspects of designing experiments, but not physically running the experiments themselves.
[^note-4]: At the time of writing this post, my median estimate is that a system at least as capable as GPT 2030 ++ (with some uncertainty about inference speed) will exist in 2035.
[^note-5]: See [[#^appendix-plausible-size-of|Appendix]] for a discussion of these numbers, including an estimate of how many machines a strong AI hacker could plausibly acquire and how much total compute this would yield.
[^note-6]: Since 50 years = 2600 weeks, so 2600 copies would be sufficient to get 50 years of “work” in a week, assuming that distinct exploits can be parallelized across the copies.
[^note-7]: More generally, backdoors are difficult to detect since the designer of the backdoor has much more discretion than potential auditors. For instance, [Yahoo had a backdoor](https://blog.azuki.vip/surveillance/?ref=bounded-regret.ghost.io) in its servers that was only publicly discovered many years later.
[^note-8]: I omit details of these scenarios to avoid the risk of providing ideas to future bad actors.
[^cite-9]: See _[What will GPT-2030 look like? (Appendix A)](https://bounded-regret.ghost.io/what-will-gpt-2030-look-like/#a-words-per-minute)_
