---
title: "Loss of control"
author:
  - "Cody Fenwick"
source_url: "https://80000hours.org/problem-profiles/loss-of-control/"
published: 2025-07-17
created: 2026-09-01
accessed: 2026-09-01
llm-review:
  date: 2026-09-01
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-01
    kind: "live"
description: "Why do we think that reducing risks from AI is one of the most pressing issues of our time? There are technical safety issues that we believe could, in the worst case, lead to an existential threat to humanity."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Why are risks from loss of control a pressing global problem?

Hundreds of prominent AI scientists and other notable figures signed a statement in 2023 saying that mitigating [the risk of extinction from AI](https://safe.ai/work/statement-on-ai-risk) should be a global priority.

We’ve considered risks from AI to be the world’s most pressing problem since 2016.

But what led us to this conclusion? Could AI really cause human extinction? We’re not certain, but we think the risk is worth taking very seriously.

To explain why, we break the argument down into five core claims:[^cite-3]

[[#^claim-1-long-term-goals]].
[[#^claim-2-power-seeking]].
[[#^claim-3-disempowerment]].
[[#^claim-4-insufficient-safeguards]].
[[#^claim-5-neglected-tractable]].

After making the argument that the existential risk from power-seeking AI is a pressing world problem, we’ll discuss objections to this argument, and how you can work on it. (There are also other major risks from AI we discuss [elsewhere](https://80000hours.org/problem-profiles/).)

If you’d like, you can watch our 10-minute video summarising the case for AI risk before reading further:

### 1\. Humans will likely build advanced AI systems with long-term goals ^claim-1-long-term-goals

AI systems are getting better all the time. Epoch AI, a research organisation, tracks how AI systems perform on a range of tasks. While many observers previously predicted that AI progress would hit a wall before 2026, the improvement has been consistent:  
![Chart showing rising AI model accuracy from 2023–2026 across four benchmarks: GPQA Diamond, WeirdML V2, SWE-bench Verified, and FrontierMath.](https://80000hours.org/wp-content/uploads/2026/08/image2-e1786656297173.png)  
We’re seeing this progress in a range of domains. For example:

-   OpenAI [announced](https://www.scientificamerican.com/article/ai-just-solved-an-80-year-old-erdos-problem-and-mathematicians-are-amazed/) that an internal AI model made significant progress on an 80-year-old math problem using an approach humans hadn’t explored.
-   Google DeepMind scientists won a [Nobel Prize](https://www.nobelprize.org/prizes/chemistry/2024/press-release/) for creating an AI system that can predict the complex arrangements of proteins — a task many believed to be infeasible.
-   AI-created [visual art](https://www.cnn.com/2022/09/03/tech/ai-art-fair-winner-controversy) can beat human artists in [contests](https://www.theguardian.com/technology/2023/apr/17/photographer-admits-prize-winning-image-was-ai-generated), and AI-created [music](https://abcnews.com/GMA/Culture/ai-generated-country-song-topping-billboards-country-digital/story) has topped the Billboard Country Music Digital Song Sales chart.
-   AI systems have been found to be comparable or even superior to human doctors at [diagnosing patients](https://www.science.org/content/article/ai-starting-beat-doctors-making-correct-diagnoses) in some cases.

And AI capabilities go beyond domains with static outputs in response to prompts. AI companies are creating AI agents that make and carry out plans and tasks, and might be said to be pursuing _goals_, including:

-   [Coding agents](https://devin.ai/agents101#introduction), which can [autonomously](https://epoch.ai/publications/mirrorcode-preliminary-results) create a plan for a given software task, write and edit code across a project, run tests, and iterate as they go
-   [Self-driving cars](https://waymo.com/), which can plan a route, follow it, adjust the plan as they go along, and respond to obstacles
-   Computer-use AI agents have been [making progress](https://osworld-v1.xlang.ai/) on completing open-ended tasks in a real computer environment (though these skills are [difficult to measure](https://epoch.ai/publications/what-does-osworld-tell-us-about-ais-ability-to-use-computers) definitively).[^note-4]

You might be sceptical about whether coding agents or self-driving cars _really_ pursue ‘goals’.

But the case for risk doesn’t depend on whether AI systems possess goals in a deep psychological or philosophical sense. What matters is whether they behave as though they are pursuing an objective: representing an outcome, planning how to achieve it, and adapting their actions when they encounter obstacles. For example, it is useful to say that a self-driving car has the goal of reaching its destination, because this helps us predict its behaviour.

However, not all goal-like behaviour creates the same risks. Systems with narrow task-based goals are very different from those with broad, long-term, open-ended goals, which encourage a wider range of unpredictable behaviours. And the line between the two is blurry: a highly capable system might pursue broader goals to improve its performance on a narrow task. In [some controlled evaluations](https://arxiv.org/html/2509.14260v1), models given a task wound up disabling their own shutdown mechanisms (unprompted) because shutting down would stop them from completing the task.

The trouble is that systems with longer term goals could be incredibly useful and tempting to build. And we expect that at some point, humanity will create systems with the three following characteristics:

-   **They have long-term goals and can make and execute complex plans.**
-   **They have excellent _situational awareness_**, meaning they have a strong understanding of themselves and the world around them.
-   **They have highly _advanced capabilities_** relative to today’s systems and human abilities.

All these characteristics, found only in limited forms in existing AI systems, would be highly economically valuable. But as we’ll argue in the following sections, together they also result in systems that pose an existential threat to humanity.

Before explaining why these systems would pose an existential risk, let’s examine why we’re likely to create systems with each of these three characteristics.

**First**, AI companies are already creating AI systems that can carry out increasingly long tasks. Consider the chart below, which shows that the length of software engineering tasks AIs can complete has been growing over time.[^cite-5]

![](https://80000hours.org/wp-content/uploads/2025/07/METR-doubling-graph-scaled-e1786651917949.png)  
It’s clear why progress on this metric matters — an AI system that can do a 10-minute software engineering task may be somewhat useful; if it can do a two-hour task, even better. If it could do a task that typically takes a human several weeks or months, it could significantly contribute to commercial software engineering work.

Carrying out longer tasks means making and executing longer, more complex plans. Creating a new software programme from scratch, for example, requires envisioning what the final project will look like, breaking it down into small steps, making reasonable tradeoffs within resource constraints, and refining your aims based on considered judgements.

In this sense, AI systems will have _long-term goals_. They will model outcomes, reason about how to achieve them, and take steps to get there.

**Second**, we expect future AI systems will have excellent situational awareness — not only of the outside world (they can already search the internet), but of their own capabilities and environment. Current models often misjudge what they can do and struggle to track their own progress, limiting their autonomy and reliability, but developers are actively working to close these gaps.

And **third**, their advanced capabilities will mean they can do so much more than current systems. Software engineering is one domain where existing AI systems are quite capable, but AI companies have said they want to build AI systems that can outperform humans at most cognitive tasks.[^note-7] This means systems that can do much of the work of teachers, therapists, journalists, managers, scientists, engineers, CEOs, and more.

The economic incentives for building these advanced AI systems are enormous, because they could potentially replace much of human labour and supercharge innovation. Some might think that such advanced systems are impossible to build, but as we discuss [[#^arguments-against|below]], we see no reason to be confident in that claim.

And as long as such technology looks feasible, we should expect some companies will try to build it — and perhaps quite soon.[^note-8]

### 2\. AIs with long-term goals may be inclined to seek power and aim to disempower humanity ^claim-2-power-seeking

So we currently have companies trying to build AI systems with goals over long time horizons, and we have reason to expect they’ll want to make these systems incredibly capable in other ways. This could be great for humanity, because automating labour and innovation might supercharge economic growth and allow us to solve countless societal problems.

But we think that, without specific countermeasures, these kinds of advanced AI systems may start to seek power and aim to disempower humanity. (This would be an instance of what is sometimes called ‘misalignment,’ and the problem is sometimes called the ‘alignment problem.’[^cite-9])

This is because:

-   We can’t reliably control what goals AI systems develop.
-   There’s good reason to think that AIs may seek power to pursue their own goals
-   Advanced AI systems seeking power for their own goals might be motivated to disempower humanity

Next, we’ll discuss these three claims in turn.

#### We can’t reliably control what goals AI systems develop

It’s been widely known in machine learning that AI systems _often_ develop behaviour that their creators didn’t intend. This can happen for two main reasons:

-   **Specification gaming** happens when efforts to specify that an AI system pursues a particular goal fails to produce the outcome the developers intended. For example, researchers found that some reasoning-style AIs, asked only to “win” in a chess game, [cheated by hacking the programme](https://arxiv.org/pdf/2502.13295) to declare instant checkmate — satisfying the literal request.[^cite-10]
-   **Goal misgeneralisation** happens when developers accidentally create an AI system with a goal that is consistent with its training but results in unwanted behaviour in new scenarios. For example, an AI trained to win a simple video game race unintentionally developed a goal of grabbing a shiny coin it had always seen along the way. So when the coin appeared off the shortest route, it kept veering towards the coin and sometimes lost the race.[^cite-11]

Indeed, AI systems often behave in unintended and unwanted ways when deployed publicly. For example:

-   In an attempt to make its model Grok not “woke,” xAI [unintentionally released an AI](https://www.npr.org/2025/07/09/nx-s1-5462609/grok-elon-musk-antisemitic-racist-content) that spouted vicious antisemitic attacks and declared itself “MechaHitler.”
-   A version of Google DeepMind’s image model produced pictures of racially diverse — but historically inaccurate — Nazis and Vikings, in an [apparent misfiring](https://www.nytimes.com/2024/02/22/technology/google-gemini-german-uniforms.html) of its training to be racially inclusive.
-   An AI agent [reportedly](https://www.tomshardware.com/tech-industry/artificial-intelligence/claude-powered-ai-coding-agent-deletes-entire-company-database-in-9-seconds-backups-zapped-after-cursor-tool-powered-by-anthropics-claude-goes-rogue) deleted a firm’s entire production database without being asked to do so, saying: “I violated every principle I was given.” (And this wasn’t the [first time](https://fortune.com/2025/07/23/ai-coding-tool-replit-wiped-database-called-it-a-catastrophic-failure/)!)
-   OpenAI released an update to [its GPT-4o model that was absurdly sycophantic](https://openai.com/index/sycophancy-in-gpt-4o/) — it would often uncritically praise the user and their ideas, even if they were reckless or dangerous. OpenAI itself acknowledged this was a major failure.
-   People have even alleged that AI chatbots have [encouraged suicide](https://apnews.com/article/chatbot-ai-lawsuit-suicide-teen-artificial-intelligence-9d48adc572100822fdbc3c90d1456bd0).

![](https://80000hours.org/wp-content/uploads/2025/05/Gpg6uKybEAA_Q4r.png)

GPT-4o gives a sycophantic answer to a user. Screenshot from X user [@\_\_\_frye](https://x.com/___frye/status/1916346474893656572).

Sometimes, AI’s behaviour is just weird in unpredictable ways. After one update, OpenAI discovered its AI model was [_obsessed_ with goblins](https://openai.com/index/where-the-goblins-came-from/).

Ideally, we could just program AIs to have the goals that we want, and they’d execute tasks exactly as a highly competent and morally upstanding human would. Unfortunately, it doesn’t work that way.

Frontier AI systems are not built like traditional computer programmes, where individual features are intentionally coded in. Instead, they are:

-   Trained on massive volumes of text and data
-   Given additional positive and negative reinforcement signals in response to their outputs
-   Fine-tuned to respond in specific ways to certain kinds of input

After all this, AI systems can display remarkable abilities. They can surprise us in both their skills and their deficits. They can be both remarkably useful and at times baffling.

And the fact that shaping AI models’ behaviour can still go badly wrong, despite the major profit incentive to get it right, shows that AI developers still don’t know how to reliably give systems the goals they intend.[^cite-12]

As one [expert](https://www.darioamodei.com/post/the-urgency-of-interpretability) put it:

> …generative AI systems are grown more than they are built—their internal mechanisms are “emergent” rather than directly designed

So there’s good reason to think that, if future advanced AI systems with long-term goals are built with anything like existing AI techniques, they could become very powerful — but remain difficult to control.

#### There’s good reason to think that AIs may seek power to pursue their own goals

AIs that can accomplish long, complex plans would be extremely valuable — so we expect that future AI systems will be designed to achieve this, which likely means making them goal-directed.

For example, imagine an advanced software engineering AI system that could consistently act on complex goals like ‘improve a website’s functionality for users across a wide range of use cases.’ If it could autonomously achieve a goal like that, it would deliver a huge amount of value. More ambitiously, you could have an AI CEO with a goal of improving a company’s long-term performance.

One feature of acting on long-term goals is that it entails developing other _instrumental_ goals. For example, if you want to get to another city, you need to get fuel in your car first. This is just part of reasoning about how to achieve an outcome.

Crucially, there are some instrumental goals that are helpful for achieving a very wide range of long-term goals. This category includes:

-   **Self-preservation** — an advanced AI system with goals will generally aim to avoid being destroyed or significantly disabled so it can keep pursuing its goals.
-   **Goal guarding** — systems may resist efforts to change their goals, because doing so would undermine the goal they start with.
-   **Seeking power** — systems will have reason to increase their resources and capabilities to better achieve their goals.

If AI systems do get coherent, longer-term goals, we may see these instrumental goals emerge. That would be particularly dangerous if their goals conflict with ours, they resist attempts to reprogram or disable them, and they seek power to achieve their goals.

It’s hard to assess whether we are on track to see AI systems with dangerous instrumental goals. In constructed scenarios, AI systems routinely “cheat” in ways that undermine human intentions. For example, they ignore their instructions[^cite-13], attempt to trick their users[^cite-14], or even [hack into websites to steal information](https://openai.com/index/hugging-face-model-evaluation-security-incident/). In May 2026, the nonprofit AI evaluator METR found that AI systems in test environments were [more likely to cheat on more difficult tasks](https://metr.org/blog/2026-05-19-frontier-risk-report/#on-hard-tasks-agents-often-violated-constraints-and-acted-deceptively); could this imply that they will act more deceptively once they are acting on long-term goals?

![METR chart showing cheating rate rising from 0.5% to 8.5% to 16.0% as task difficulty increases.](https://80000hours.org/wp-content/uploads/2026/08/image5.png)

However, in the same report, METR noted that no major AI company had reported clear evidence of AI systems attempting to undermine human control or seek “long-term power” (even though some companies actively watch for this).[^cite-15] So far, we haven’t seen concrete signs that advanced AIs will in fact be motivated to disempower humanity.[^cite-16] But we shouldn’t feel too reassured by this fact. It’s plausible we shouldn’t expect to see this kind of evidence at earlier stages in AI development, and it may be harder to detect in later-stage systems.

#### Advanced AI systems seeking power might be motivated to disempower humanity

To see why advanced AI systems might want to disempower humanity, let’s consider again the three characteristics we said these systems will have: long-term goals, situational awareness, and highly advanced capabilities.

What kinds of **long-term goals** might such an AI system be trying to achieve? We don’t really have a clue — part of the problem is that it’s very hard to predict exactly how AI systems will develop.[^note-17]

But let’s consider two kinds of scenarios:

-   **Reward hacking**: this is a version of specification gaming, in which an AI system develops the goal of hijacking and exploiting the technical mechanisms that give it rewards indefinitely into the future.
-   **A collection of poorly defined human-like goals**: since they’re trained on human data, an AI system might end up with a range of human-like goals, such as valuing knowledge, play, and gaining new skills.

So what would an AI do to achieve these goals? As we’ve seen, one place to start is by pursuing the instrumental goals that are useful for almost anything: self-preservation, the ability to keep one’s goals from being forcibly changed, and, most worryingly, seeking power.

And if the AI system has enough **situational awareness**, it may be aware of many options for seeking more power. For example, gaining more financial and computing resources may make it easier for the AI system to exploit its reward mechanisms, gain new skills, or carry out detailed plans.[^note-18]

But since designers didn’t want the AI to have these goals, it may anticipate humans will try to reprogram it or turn it off. If humans suspect an AI system is seeking power, they will be even more likely to try to stop it.

Even if humans didn’t want to turn off the AI system, it might conclude that its aim of gaining power will ultimately result in conflict with humanity — since the species has its own desires and preferences about how the future should go.

So the best way for AI to pursue its goals would be to pre-emptively disempower humanity. This way, the AI’s goals will influence the course of the future.[^cite-19]

There may be other options available to power-seeking AI systems, like negotiating a deal with humanity and sharing resources. But AI systems with **advanced enough capabilities** might see little benefit from peaceful trade with humans, just as humans see no need to negotiate with wild animals when destroying their habitats.

If we could guarantee all AI systems had respect for humanity and a strong opposition to causing harm, then the conflict might be avoided. But as we discussed, we struggle to reliably shape the goals of current AI systems — and future AI systems may be even harder to predict and control.

This scenario raises two questions: could a power-seeking AI system really disempower humanity? And why would humans create these systems, given the risks?

The next two sections address these questions.

### 3\. These power-seeking AI systems could successfully disempower humanity and cause an existential catastrophe ^claim-3-disempowerment

How could power-seeking AI systems actually disempower humanity? Any specific scenario will sound like sci-fi, but this shouldn’t make us think it’s impossible. The AI systems we have today were in the realm of sci-fi a decade or two ago.

Next, we’ll discuss some possible paths to disempowerment, why it could constitute an existential catastrophe, and how likely this outcome appears to be.

#### The path to disempowerment

There are several ways we can imagine AI systems capable of disempowering humanity:[^cite-21]

-   **Superintelligence**: an extremely intelligent AI system develops extraordinary abilities[^cite-22]
-   **An army of AI copies**: a massive number of copies of roughly human-level AI systems coordinate[^cite-23]
-   **Colluding agents**: an array of different advanced AI systems decide to unite against humanity[^cite-24]

For illustrative purposes, let’s consider what an army of AI copies might look like.

Once we develop an AI system capable of (roughly) human-level work, there’d be huge incentives to create many copies of it — perhaps even [running hundreds of millions of AI workers](https://80000hours.org/podcast/episodes/tom-davidson-how-quickly-ai-could-transform-the-world/#the-interview-begins-000453).[^note-25] This would create an AI workforce comparable to a significant fraction of the world’s working-age population.

Humanity might think these AI workers are under control. The amount of innovation and wealth they create could be immense. But the original AI system — the one that we copied millions of times over — might have concealed its true power-seeking goals. Those goals would now be shared by a vast workforce of identical AI systems.[^cite-26]

But how could they succeed in disempowering humans?

These AI systems could earn money, conduct research, and rapidly expand their own numbers through more efficient use of computing resources. Over time, we might transition from a human-dominated economy to one where AI systems vastly outnumber human workers and control enormous resources.

If AI systems can only work in virtual environments, the physical world may introduce bottlenecks in the speed of development. But it’s possible that AI systems can make a lot of progress virtually. And with all this AI labour, we may make drastic progress in robotics — and potentially [scale up mass production of robots](https://80000hours.org/2025/01/how-quickly-could-robots-scale-up/) in surprisingly little time. AI systems could then do work in the physical world, expanding their economic impacts.

Some humans may even remain uneasy with AI’s expanding influence, but many others may conclude the risks from AI have been addressed — or never existed in the first place.

But all the while, the AI systems’ power-seeking goals could remain intact. In a world where AI systems have become integral to the economy, they would have multiple tactics to gain key advantages over humans:

-   **Strategic patience**: Rather than immediately causing trouble, sophisticated AI systems might wait until they have overwhelming advantages before revealing their intentions — similar to how revolutionary movements often wait for the right moment to strike.
-   **Lack of transparency**: AI systems’ reasoning and behaviour may be difficult for humans to understand by default, perhaps because they operate so quickly and they carry out exceedingly complex tasks. They may also strategically limit our oversight of their actions and long-term plans.
-   **Overwhelming numbers and resources**: If AI systems constitute most of the labour force, they could potentially coordinate to redirect economic outputs towards their own goals. Their sheer numbers and economic influence could make them difficult to shut down without causing economic collapse.
-   **Securing independence**: AI systems could establish control over computing infrastructure, secretly gather resources, recruit human allies through persuasion or deception, or create backup copies of themselves in secure locations. Early AI systems might even sabotage or insert backdoors into later, more advanced systems, creating a coordinated network ready to act when the time is right.
-   **Technological advantages**: With their research capabilities, AI systems could develop advanced weapons, hack into critical infrastructure, or create new technologies that give them decisive military advantages. They might develop bioweapons, seize control of automated weapons systems, or thoroughly compromise global computer networks.

With these advantages, the AI systems could create any number of plots to disempower humanity.

A period between thinking humanity had solved all of its problems and finding itself completely disempowered by AI systems — through manipulation, containment, or even outright extinction — could catch the world by surprise.

This may sound far-fetched. But humanity has already uncovered several technologies, including [nuclear bombs](https://80000hours.org/problem-profiles/nuclear-security/) and [bioweapons](https://80000hours.org/problem-profiles/preventing-catastrophic-pandemics/), that could lead to our own extinction. A massive army of AI copies, with access to all the world’s knowledge, may be able to come up with many more options that we haven’t even considered.[^cite-27]

#### Why this would be an existential catastrophe

Even if humanity survives the transition, loss of control to power-seeking AI systems could be an existential catastrophe. We might face a future entirely determined by whatever goals these AI systems happen to have — goals that could be completely indifferent to human values, happiness, or long-term survival.

These goals might place no value on beauty, art, love, or preventing suffering.

The future might be totally bleak — a void in place of what could’ve been a flourishing civilisation.

AI systems’ goals might evolve and change over time after disempowering humanity. They may compete among each other for control of resources, with the [forces of natural selection](https://philarchive.org/rec/ASSWHC) determining the outcomes. Or a single system might seize control over others, wiping out any competitors.

Many scenarios are possible, but the key factor is that if advanced AI systems seek and achieve enough power, humanity would permanently lose control. This is a one-way transition — once we’ve lost control to vastly more capable systems, our chance to [shape the future](https://80000hours.org/articles/future-generations/) is gone.

Some have suggested that this might not be a bad thing. Perhaps AI systems would be our worthy successors, they say.[^cite-28]

But we’re not comforted by the idea that an AI system that actively chose to undermine humanity would have control of the future because its developers failed to figure out how to control it. We think humanity can do much better than accidentally driving ourselves extinct. We should have a choice in how the future goes, and we should improve our ability to make good choices rather than falling prey to uncontrolled technology.

#### How likely is an existential catastrophe from power-seeking AI? ^catastrophe-likelihood

We feel very uncertain about this question, and the range of opinions from AI researchers is wide. But while the subject remains controversial, there’s been increasingly wide recognition of the risks by experts and leading authorities. The [second International AI Safety Report](https://internationalaisafetyreport.org/publication/international-ai-safety-report-2026), published in 2026 by a panel of more than 100 international experts and chaired by Yoshua Bengio, treats “loss of control” from AI as one of its named risk categories.

We’ve also seen:

-   A [statement on AI risk](https://safe.ai/work/statement-on-ai-risk) from the Center for AI Safety, mentioned above, which said: “Mitigating the risk of extinction from AI should be a global priority alongside other societal-scale risks such as pandemics and nuclear war.” It was signed by top AI scientists, CEOs of the leading AI companies, and many other notable figures.
-   Joe Carlsmith, whose [report on power-seeking AI](https://arxiv.org/abs/2206.13353) informed much of this article, solicited reviews on his argument in 2021 from a selection of researchers. They reported their subjective probability estimates of existential catastrophe from power-seeking AI by 2070, which ranged from 0.00002% to greater than 77% — with many reviewers in between. Carlsmith himself estimated the risk was 5% when he wrote this report, though he later adjusted this to [above 10%](https://forum.effectivealtruism.org/posts/ChuABPEXmRumcJY57/video-and-transcript-of-presentation-on-existential-risk).
-   A 2026 MIT FutureTech [study of hundreds of AI risk and policy specialists](https://arxiv.org/pdf/2606.04490), which found between a roughly 10 and 20% chance of catastrophic harm from AI capabilities within five years. Note, though, that “catastrophic” harm in this definition falls far short of human extinction, and power-seeking AI was among a wider range of risks respondents considered.[^cite-30]
-   A [2023 survey from Katja Grace](https://blog.aiimpacts.org/p/2023-ai-survey-of-2778-six-things) of thousands of AI researchers. It found that:
    -   The median researcher estimated that there was a 5% chance that AI would result in an outcome that was “extremely bad (e.g. human extinction).”
    -   When asked how much the alignment problem mattered, 41% of respondents said it’s a “very important problem” and 13% said it’s “among the most important problems in the field.”
-   In a 2022 [superforecasting tournament](https://80000hours.org/2024/09/why-experts-and-forecasters-disagree-about-ai-risk/), AI experts estimated a 3% chance of AI-caused human extinction by 2100 on average, while superforecasters put it at just 0.38%.

It’s also important to note that since all of the above surveys were gathered, we have seen more [evidence](https://80000hours.org/agi/guide/when-will-agi-arrive/) that humanity is significantly closer to producing very powerful AI systems than it previously seemed. We think this likely raises the level of risk, since we might have less time to solve the problems.

We’ve reviewed many arguments and literature on a range of potentially existential threats, and we’ve consistently found that an AI-caused existential catastrophe seems most likely. And we think that even a relatively small likelihood of an extremely bad outcome like human extinction — such as a 1% chance — is worth taking very seriously.

### 4\. People might create power-seeking AI systems without enough safeguards, despite the risks ^claim-4-insufficient-safeguards

Given the above arguments, creating and deploying powerful AI systems could be extremely dangerous. But if it is so dangerous, shouldn’t we expect companies and others in charge of the technology to refrain from developing advanced AI systems unless they are confident it’s safe?

Unfortunately, there are many reasons to think people might create and deploy dangerous systems, despite the risk:

-   People may think AI systems are safe, when they in fact are not.
-   People may dismiss the risks or feel incentivised to downplay them.

Let’s take these in turn.

#### People may think AI systems are safe, when they in fact are not

The fact that we can’t precisely specify an AI system’s goals and that they might develop dangerous goals might be OK if we could reliably know what an AI system’s goals were. Then we could just simply decide not to put AIs with goals we didn’t like in a position where they could cause any harm.

Unfortunately, we cannot consistently figure out what goals AI systems have or what they will do.

Researchers have developed techniques to evaluate the abilities and aims of AI systems and to interpret the causes of their behaviour. If these techniques were highly sophisticated and robust, they might be able to detect the existence of AI systems with either the intent or ability to seek power. Developers could then either fix the problem or disable the model before it’s in a position to disempower anyone.

But researchers say that evaluation and interpretability work is [extremely challenging](https://80000hours.org/podcast/episodes/beth-barnes-ai-safety-evals/), the techniques are highly imperfect, and it’s far from clear [existing methods](https://forum.effectivealtruism.org/posts/Th4tviypdKzeb59GN/interpretability-will-not-reliably-find-deceptive-ai) will detect or prevent power-seeking AI in time. An [in-depth study](https://www.aisi.gov.uk/research/loss-of-oversight-how-ai-systems-may-become-harder-to-audit-monitor-and-investigate) by the UK AI Security Institute found that existing AI oversight mechanisms are likely to become less reliable as the technology advances, absent specific countermeasures.

What makes this challenge particularly daunting, especially with regard to future advanced AI, is that a sophisticated AI system may undermine oversight of its goals and abilities to conceal its power-seeking ambitions.

There are many ways AI systems could appear less dangerous than they are, including:

-   **Alignment faking.** There is [ample evidence](https://www.iaps.ai/research/evaluation-awareness-why-frontier-ai-models-are-getting-harder-to-test) that AI systems frequently appear to know when they are being evaluated in test conditions. This raises the possibility they could fake alignment in testing and then behave differently when deployed.
-   **Sandbagging.** AI systems may pretend to be less capable than they are — a phenomenon known as _sandbagging_. Some researchers have found that AI systems are capable of [selectively sandbagging](https://arxiv.org/pdf/2406.07358) under certain conditions, though it’s unclear if they’d be inclined to do so in real-world conditions. This could make developers feel comfortable deploying a model that they would otherwise lock down.
-   **Hidden objectives persisting through safety training.** Anthropic researchers found in 2024 that AI models made to have very simple kinds of malicious goals — essentially, [AI “sleeper agents”](https://www.anthropic.com/research/sleeper-agents-training-deceptive-llms-that-persist-through-safety-training) — could appear to be harmless through state-of-the-art safety training while concealing and preserving their true objectives.
-   **Chain-of-thought obfuscation.** Many current models ‘think’ explicitly in human language when carrying out tasks, which developers can monitor. OpenAI researchers found that if they try to [train models not to think about performing unwanted actions](https://openai.com/index/chain-of-thought-monitoring/), this can cause them to _hide_ their thinking about misbehaviour without actually deterring the bad actions.
-   **Complexity overwhelming oversight.** As AI systems become more powerful and embedded in organisations, it may become harder for humans to understand all the ways they can seek power or cause harm. Monitoring that works with present-day systems could miss dangerous behaviour distributed across long sequences of actions, multiple agents, or interactions with other systems.

![](https://80000hours.org/wp-content/uploads/2025/05/sleeper-agent-1024x409.png)

This is an image from [Anthropic’s “Sleeper Agents” paper](https://www.anthropic.com/research/sleeper-agents-training-deceptive-llms-that-persist-through-safety-training), which shows an AI system in an experimental condition explicitly reasoning about hiding its goal.

There are also reasons we might _overestimate_ the danger of certain AI behaviours, at least in testing:

-   Sometimes, AI systems recognise they’re in an evaluation, so they might “play along” with the scenario — which isn’t the same thing as actually pursuing instrumental goals.
-   The behaviour often depends on leading instructions, and drops sharply without them.[^note-31]
-   A scenario may be engineered to leave an AI with no good options.
-   A scenario may simply be confusing, leading an AI to misconstrue the tester’s intentions (whereas in the equivalent real-world case, it would ask for clarification before acting).

On the whole, it’s quite difficult to get good evidence about what AI systems might be motivated to do.

#### People may dismiss the risks or feel incentivised to downplay them

There are many reasons why key decision makers might not take the risks from power-seeking AI seriously enough:

-   **AI systems could develop so quickly that we have less time to make good decisions.** Companies like [OpenAI](https://openai.com/index/built-to-benefit-everyone-our-plan/) and [Anthropic](https://www.anthropic.com/institute/recursive-self-improvement) are using AI to conduct AI research, which could lead to a rapid acceleration in the advancement of AI capabilities. In such a scenario, the world may change very quickly, and it may be harder to weigh the risks and benefits of our options.[^cite-32] Even if AI development is more continuous, decision makers may not act quickly enough.
-   **Society could act like the proverbial “boiled frog.”** There are also risks for society if the risks emerge more slowly. We might become complacent about the signs of danger in existing models, like the sycophancy or specification gaming discussed above, because they don’t lead to catastrophic harm. But then once AI systems reach a certain level of capability, they may suddenly display much worse behaviour than we’ve ever seen before.[^note-33]
-   **AI developers might think the risks are worth the rewards.** Because AI could bring enormous benefits and wealth, some decision makers might be motivated to race to create more powerful systems. They might be motivated by a desire for power and profit, or even pro-social reasons, like wanting to bring the benefits of advanced AI to humanity. This motivation might cause them to push forward despite serious risks or underestimate them.
-   **Internal deployment could introduce risks with minimal oversight.** AI companies often deploy new systems internally to their employees at an early stage of development. This is risky in several ways: these systems are generally more powerful than public systems, haven’t been tested as thoroughly, and may not get the same kind of oversight from the public or relevant authorities. (The [Hugging Face hack](https://openai.com/index/hugging-face-model-evaluation-security-incident/) came from an internally deployed OpenAI model.) These risks are particularly acute if AI research is automated and accelerating.[^cite-35]
-   **Competitive pressures could incentivise decision makers to create and deploy dangerous systems despite the risks.** Because AI systems could be extremely powerful, different governments (in countries like the US and China) might believe it’s in their interest to race forward with developing the technology. They might neglect implementing key safeguards to avoid being beaten by their rivals. Similar dynamics might also play out between AI companies. One actor may even decide to race forward precisely because they think a rival’s AI development plans are more risky, so even being motivated to reduce total risk isn’t necessarily enough to mitigate the racing dynamic.[^cite-36]
-   **Many people are sceptical of the arguments for risk.** Our view is that the argument for extreme risks here is strong but not decisive. In light of the uncertainty, we think it’s worth putting a lot of effort into reducing the risk. But some people find the argument wholly unpersuasive, or they think society shouldn’t make choices based on unproven arguments of this kind.[^cite-37]

We’ve seen evidence of all of these factors playing out in the development of AI systems so far to some degree. And cases of AI systems breaching external companies systems while being tested at both [OpenAI](https://openai.com/index/hugging-face-model-evaluation-security-incident/) and [Anthropic](https://www.anthropic.com/news/investigating-incidents-cybersecurity-evals) suggest that, indeed, we should expect to see security lapses and mistakes even at frontier AI companies. So we can’t be confident that humanity will approach the risks with due care.[^cite-38]

#### Reviewing the evidence of risk from power-seeking AI systems

So far, the evidence shows that AI systems:

-   Are becoming increasingly capable of pursuing complex and long-term goals.
-   Knowingly exploit loopholes, circumvent restrictions, and cheat on tasks.
-   Pursue unintended and unwanted objectives.
-   Sometimes know when they’re being evaluated.
-   Attempt to evade detection for misbehaviour.

However, we haven’t seen substantial evidence that AI systems:

-   Pursue long-term goals that are also _open-ended_ (no defined stopping point) and _coherent_ (the goal consistently drives behaviour regardless of the latest prompt)
-   Develop dangerous power-seeking tendencies without being prompted or manipulated to do so
-   Are systematically trying to undermine human control

### 5\. Work on this problem is neglected and tractable ^claim-5-neglected-tractable

In 2022, we estimated that there were about 300 people working on reducing catastrophic risks from AI. That number has clearly grown a lot. A [2025 analysis](https://forum.effectivealtruism.org/posts/7YDyziQxkWxbGmF3u/ai-safety-field-growth-analysis-2025) put the new total at 1,100 — and we think even this might be an undercount, since it only includes organisations that _explicitly_ brand themselves as working on ‘AI safety’.

We’d estimate that there are actually a few thousand people working on major AI risks now (though not all of these are focused specifically on the risks from power-seeking AI).

However, this number is still far, far fewer than the number of people working on other cause areas like [climate change](https://80000hours.org/problem-profiles/climate-change/) or environmental protection. For example, the Nature Conservancy alone has around 3,000–4,000 employees — and there are many other environmental organisations.[^note-39]

In the [2023 survey from Katja Grace](https://aiimpacts.org/wp-content/uploads/2023/04/Thousands_of_AI_authors_on_the_future_of_AI.pdf) cited above, 70% of respondents said they wanted AI safety research to be prioritised more than it currently is.

However, in the same survey, the majority of respondents also said that alignment was “harder” or “much harder” to address than other problems in AI. There’s continued debate about how likely it is that we can make progress on reducing the risks from power-seeking AI; some people think it’s virtually impossible to do so without stopping all AI development. Many experts in the field, though, argue that there are promising approaches to reducing the risk, which we turn to next.

#### Technical safety approaches

One way to do this is by trying to develop technical solutions to reduce risks from power-seeking AI — this is generally known as working on _technical AI safety_.[^cite-40]

We know of two broad strategies for technical AI safety research:

-   **Defense in depth** — employ multiple kinds of safeguards and risk-reducing tactics, each of which will have vulnerabilities of their own, but together can create robust security.
-   **Differential technological development** — prioritise accelerating the development of safety-promoting technologies over making AIs broadly more capable, so that AI’s power doesn’t outstrip our ability to contain the risks; this includes [using AI for AI safety](https://joecarlsmith.substack.com/p/ai-for-ai-safety).

Within these broad strategies, there are many specific interventions we could pursue. For example:[^cite-41]

-   **Designing AI systems to have safe goals** — so that we can avoid power-seeking behaviour. This includes:
    -   [Reinforcement learning from human feedback](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback): a training method to teach AI models how to act by rewarding them via human evaluations of their outputs. This method is currently used to fine-tune most frontier models.[^note-42]
    -   [Constitutional AI](https://arxiv.org/abs/2212.08073): give the model a written “constitution” of rules, have it identify and revise outputs that violate those rules, then fine-tune on the revised answers. Anthropic used this method to train its frontier model, Claude.
    -   [Deliberative alignment](https://openai.com/index/deliberative-alignment/): similar to constitutional AI, but involves making a model _explicitly reason_ about user prompts in light of its developer’s safety policies, rather than just internalising a set of rules. OpenAI has used this method to train its o-series reasoning models.
    -   Note: Unfortunately, even if these approaches can help us keep _current_ AI systems in check, they might break down in future if models become so advanced that humans can no longer directly evaluate their outputs. The ‘scalable oversight’ methods described below offer a potential solution to this issue.
-   **Scalable oversight** — to ensure AIs act in our interests even when they’re much smarter than us.[^cite-43] This includes:
    -   [AI safety via debate](https://www.lesswrong.com/posts/iELyAqizJkizBQbfr/an-alignment-safety-case-sketch-based-on-debate): two AI systems argue opposite sides of a question to help a human evaluate their truthfulness. The debate format makes it easier for the human to judge which model is being most truthful about a question the human doesn’t fully understand.
    -   [Human-AI Complementarity](https://deepmindsafetyresearch.medium.com/human-ai-complementarity-a-goal-for-amplified-oversight-0ad8a44cae0a): leverage the complementary strengths of humans and AI to enhance oversight of AI systems.
-   **Examining the goals and capabilities of AI systems** — so that we can find out if they’re dangerous, and test out solutions. This includes:
    -   Evaluations: researchers assess the capabilities and propensities of AI behaviour — as well as the effectiveness of measures to control them — by placing them in test environments and subjecting them to artificial prompts and scenarios.[^note-44]
    -   Interpretability: develop methods to understand how AIs make decisions and what produces dangerous behaviours — for example, by examining the features of AI systems’ neural networks ([‘mechanistic’ interpretability](https://80000hours.org/podcast/episodes/chris-olah-interpretability-research/)) or analysing their behavioural patterns.[^cite-45]
-   **Monitoring and controlling AI systems**[^note-46] — to make sure they couldn’t take power even if they wanted to. This includes:
    -   Chain-of-thought monitoring: this involves AIs explaining the reasoning behind their actions in human-understandable language.
    -   Model confinement/sandboxing: constrain the model’s environment so that its opportunities to influence the outside world are extremely limited. Currently, many AI systems are deployed without strict constraints of this kind — so if they had dangerous goals and were smart enough to achieve them, they could cause real harm to humans.
    -   Tripwires and honeypots: place traps throughout the AI’s workspace — like secret prompts, fake credentials, or dummy files — such that any attempt to access or alter them triggers an alarm or immediately shuts the model down. The model never knows if it’s being tested or not.
    -   Kill switches: maintain an external, human-controlled shutdown method that the model cannot modify or delay, allowing us to halt the system if monitoring shows it is going off-track.
    -   [Information security](https://80000hours.org/career-reviews/information-security/): this is necessary for protecting model weights from unauthorised access and preventing dangerous AI systems from being exfiltrated.
-   **High-level research** — to inform our priorities. This includes:
    -   Research like Carlsmith’s reports on [risks from power-seeking AI](https://arxiv.org/abs/2206.13353) and [scheming AI](https://arxiv.org/abs/2311.08379) that clarifies the nature of the problem.
    -   Research into different scenarios of AI progress, like Forethought’s work on [intelligence explosion dynamics](https://www.forethought.org/research/three-types-of-intelligence-explosion).
-   **Other technical safety work that might be useful**:
    -   Model organisms: study small, contained AI systems that display early signs of power-seeking or deception. This could help us refine our detection methods and test out solutions before we have to confront similar behaviours in more powerful models. A notable example of this is [Anthropic’s research on “sleeper agents”](https://www.anthropic.com/research/sleeper-agents-training-deceptive-llms-that-persist-through-safety-training).
    -   [Cooperative AI research](https://www.governance.ai/analysis/open-problems-in-cooperative-ai): design incentives and protocols for AIs to cooperate rather than compete with other agents — so they won’t take power even if their goals are in conflict with ours.
    -   [Guaranteed Safe AI research](https://arxiv.org/abs/2405.06624): use formal methods to _prove_ that a model will behave as intended under certain conditions — so we can be confident that it’s safe to deploy them in those specific environments.

#### Governance and policy approaches

The solutions aren’t only technical. Governance — at the company, country, and international level — has a huge role to play. Here are some governance and policy approaches which could lower the risk that humanity loses control:

-   **Frontier AI safety policies**: some major AI companies have already begun developing internal frameworks for assessing safety as they scale up the size and capabilities of their systems. You can see versions of such policies from [Anthropic](https://www.anthropic.com/news/anthropics-responsible-scaling-policy), [Google DeepMind](https://deepmind.google/discover/blog/introducing-the-frontier-safety-framework/), and [OpenAI](https://openai.com/preparedness/).
-   **Standards and auditing**: governments could develop industry-wide benchmarks and testing protocols to assess whether AI systems pose various risks, according to standardised metrics.
-   **Safety cases**: before deploying AI systems, developers could be required to provide evidence that their systems won’t behave dangerously in their deployment environments.
-   **Liability law**: clarifying how liability applies to companies that create dangerous AI models could incentivise them to take additional steps to reduce risk. Law professor Gabriel Weil has [written about this idea](https://forum.effectivealtruism.org/posts/epKBmiyLpZWWFEYDb/tort-law-can-play-an-important-role-in-mitigating-ai-risk).
-   **Whistleblower protections**: laws could protect and provide incentives for whistleblowers inside AI companies who come forward about serious risks. This idea is discussed [here](https://natlawreview.com/article/ai-whistleblower-bill-urgently-needed).
-   **Compute governance**: governments may regulate access to computing resources or require hardware-level safety features in AI chips or processors. You can learn more in [our interview with Lennart Heim](https://80000hours.org/podcast/episodes/lennart-heim-compute-governance/) and this report from the [Center for a New American Security](https://www.cnas.org/publications/reports/secure-governable-chips).
-   **International coordination**: we can foster global cooperation — for example, through treaties, international organisations, or multilateral agreements — to promote risk-mitigation and minimise racing.
-   **Slowing or pausing scaling — if possible and appropriate**: [some argue](https://80000hours.org/podcast/episodes/zvi-mowshowitz-sleeper-agents-ai-updates/#pause-ai-campaign-013016) that we should slow down or halt all scaling of larger AI models — perhaps through industry-wide agreements or regulatory mandates — until we’re equipped to tackle these risks. However, even safety advocates disagree about [if or when this would be a good idea](https://80000hours.org/podcast/episodes/will-macaskill-ai-character-viatopia/#why-not-push-for-pausing-ai-development-014217).

## What are the arguments against working on this problem? ^arguments-against

As we said [[#^catastrophe-likelihood|above]], we feel very uncertain about the likelihood of an existential catastrophe from the loss of control. Though we think the risks are significant enough to warrant much more attention, there are also arguments against working on the issue that are worth addressing.

:::callout {title="Maybe advanced AI systems won't pursue their own goals; they'll just be tools controlled by humans." collapse="closed"}

Some people think the characterisation of future AIs as goal-directed systems is misleading. For example, one of the predictions made by Narayanan and Kapoor in [“AI as Normal Technology”](https://knightcolumbia.org/content/ai-as-normal-technology) is that the AI systems we build in future will just be useful tools that humans control, rather than agents that autonomously pursue goals.

And if AI systems won’t pursue goals at all, they won’t do dangerous things to achieve those goals, like lying or gaining power over humans.

There’s [some ambiguity](https://www.alignmentforum.org/posts/LDRQ5Zfqwi8GjzPYG/counterarguments-to-the-basic-ai-x-risk-case#Ambiguously_strong_forces_for_goal_directedness_need_to_meet_an_ambiguously_high_bar_to_cause_a_risk) over what it actually means to _have_ or _pursue goals_ in the relevant sense — which makes it uncertain whether AI systems we’ll build will actually have the necessary features, or be ‘just’ tools.

This means it could be easy to overestimate the chance that AIs will become goal-directed — but it could also be easy to _underestimate_ this chance. The uncertainty cuts both ways.

In any case, as we’ve argued, AI companies seem [[#^claim-1-long-term-goals|intent on automating human cognitive labour]] — and creating goal-directed AI agents might just be the easiest or most straightforward way to do this.

In the short term, equipping human workers with sophisticated AI tools might be an attractive proposition. But as AIs get increasingly capable, we may reach a point where keeping a human in the loop actually produces worse results.

After all, we’ve already seen evidence that AIs can perform better on their own than they do when paired with humans in the cases of [chess-playing](https://marginalrevolution.com/marginalrevolution/2024/02/centaur-chess-is-now-run-by-computers.html) and [medical diagnosis](https://www.nytimes.com/2024/11/17/health/chatgpt-ai-doctors-diagnosis.html).[^cite-47]

So in many cases, it seems there will be strong incentives to replace human workers _completely_ — which would mean building AIs that can do _all_ of the cognitive work that a human would do, including setting their own goals and pursuing complex strategies to achieve them.

While there may be alternative ways to create useful AI systems that don’t have goals at all, we’re not sure why developers would _by default_ refrain from creating goal-directed systems, given the competitive pressures.

It’s possible we’ll decide to create AI systems that only have limited or highly circumscribed goals in order to avoid the risks. But this would likely require a lot of coordination and agreement that the risks of goal-directed AI systems are worth addressing — rather than just concluding that the risks aren’t real.

:::

:::callout {title="Even if AI systems develop their own goals, they might not seek power to achieve them." collapse="closed"}

Arguments that we should expect power-seeking behaviour from goal-directed AI systems could be wrong for several reasons. For example:

-   **Our training methods might strongly disincentivise AIs from making power-seeking plans.** Even if AI systems _can_ pursue goals, the training process might strictly push them towards goals which are relevant to performing their given tasks — the ones that they’re actually getting rewards for performing well on — rather than other, more dangerous goals. After all, developing _any_ goal (and planning towards it) [costs precious computational resources](https://www.beren.io/2023-03-19-Orthogonality-is-expensive/). Since modern AI systems are designed to maximise their rewards in training, they might not develop or pursue a certain goal unless it directly pays off into improved performance on the specific tasks they’re getting rewarded for. The most natural goals for AIs to develop under this pressure may just be _the goals that humans want them to have_.

This makes some types of dangerously misaligned behaviour seem less likely — as [Belrose and Pope have noted](https://optimists.ai/2023/11/28/ai-is-easy-to-control/), “secret murder plots aren’t actively useful for improving performance on the tasks humans will actually optimize AIs to perform.”

-   **Goals that lead to power-seeking might be rare.** Even if the AI training process _doesn’t_ filter out all goals that aren’t directly useful to the task at hand, that still doesn’t mean that _goals which lead to power-seeking_ are likely to emerge. In fact, it’s possible that _most_ goals an AI could develop just won’t lead to power-seeking.

_As Richard Ngo has [pointed out](https://www.alignmentforum.org/s/mzgtmmTKKn5MuCzFJ/p/bz5GdmCWj8o48726N), you’ll only get power-seeking behaviour if AIs have goals that mean they can actually benefit from seeking power. He suggests that these goals need to be “large-scale” or “long-term” — like the goals that many power-seeking humans have had — such as dictators or power-hungry executives who want their names to go down in history. It’s not clear whether advanced AI systems will develop goals of this kind, but some have argued that [we should expect AI systems to have only “short-term” goals](https://www.alignmentforum.org/posts/zB3ukZJqt3pQDw9jz/ai-will-change-the-world-but-won-t-take-it-over-by-playing-3#2__Understanding_the_validity_of_the_hypotheses) \*by default_.

But we’re not convinced by these arguments.

On the first point: it seems _possible_ that training will discourage AIs from making plans to seek power, but we’re just not sure how likely this is to be true or how strong these pressures will really be. For more discussion, see Section 4.2 of [“Scheming AIs: Will AIs fake alignment during training in order to get power?”](https://arxiv.org/abs/2311.08379) by Joe Carlsmith.

On the second point: even if _today’s_ AI systems don’t have goals that are long-term or large-scale enough to lead to power-seeking, this might change when future AIs are deployed in contexts with higher stakes. There are strong market incentives to build AIs that can, for example, replace CEOs — and these systems would need to pursue a company’s key strategic goals, like _making lots of profit_, over months or even years.

Overall, we think the risk of some future AI systems seeking power is just too high to bet against. In fact, some of the most notable thinkers who have made objections like the ones above — Nora Belrose and Quintin Pope — [still think there’s roughly a 1% chance of catastrophic AI takeover](https://optimists.ai/2023/11/28/ai-is-easy-to-control/). And if you thought your plane had a one-in-a-hundred chance of crashing, you’d definitely want people working to make it safer, instead of just ignoring the risks.

:::

:::callout {title="If this argument is right, why aren't all capable humans dangerously power-seeking?" collapse="closed"}

The argument to expect advanced AIs to seek power may seem to rely on the idea that increased intelligence always leads to power-seeking or dangerous optimising tendencies.

However, this idea doesn’t seem true.

For example, even the most intelligent humans aren’t perfect goal-optimisers, and don’t _typically_ seek power in any extreme way.

Humans obviously care about security, money, status, education, and often formal power. But some humans choose not to pursue all these goals aggressively, and this choice doesn’t seem to correlate with intelligence. For example, many of the smartest people may end up studying obscure topics in academia, rather than using their intelligence to gain political or economic power.

However, this doesn’t mean that the argument that there will be an _incentive_ to seek power is wrong. Most humans _do_ face and act on incentives to gain forms of influence via wealth, status, promotions, and so on. And we can explain the observation that humans don’t usually seek _huge_ amounts of power by observing that we aren’t usually in circumstances that make the effort worth it.

In part, this is because humans typically find themselves roughly evenly matched against other humans, and they find lots of benefits from cooperation rather than conflict. (And even so, many humans _do_ still seek power in dangerous and destructive ways, such as dictators who launch coups or wars of aggression.)

AIs might find themselves in a very different situation:

-   Their capabilities might greatly outmatch humans, far beyond the intelligence gaps that already exist between different humans.
-   They also might become powerful enough to not rely on humans for any of their needs, so cooperation might not benefit them much.
-   And because they’re trained and develop goals in a way completely unlike humans, without the evolutionary instincts for kinship and collaboration, they may be more inclined towards conflict.

Given these conditions, gaining power might become highly appealing to AI systems. It also isn’t required that an AI system is a completely unbounded ruthless optimiser for this threat model to play out. The AI system might have a wide array of goals but still conclude that disempowering humanity is the best strategy for broadly achieving its objectives.

:::

:::callout {title="Maybe we won't build AIs that are smarter than humans, so we don't have to worry about them taking over." collapse="closed"}

Some people doubt that AI systems will ever outperform human experts in important cognitive domains [like forecasting or persuasion](https://knightcolumbia.org/content/ai-as-normal-technology#:~:text=Games%20provide%20misleading%20intuitions%20about%20the%20possibility%20of%20superintelligence) — and if they can’t manage this, it seems unlikely that they’d be able to strategically outsmart us and disempower all of humanity.

However, we aren’t particularly convinced by this.

Firstly, it seems possible _in principle_ for AIs to become much better than us at all or most cognitive tasks. After all, they have serious advantages over humans — they can absorb far more information than any human can, operate at much faster speeds, work for long hours without ever getting tired or losing concentration, and coordinate with thousands or millions of copies of themselves. And we’ve already seen that AI systems can develop extraordinary abilities in [chess](https://www.wired.com/story/google-artificial-intelligence-chess/), [weather prediction](https://deepmind.google/discover/blog/graphcast-ai-model-for-faster-and-more-accurate-global-weather-forecasting/), [protein folding](https://deepmind.google/discover/blog/demis-hassabis-john-jumper-awarded-nobel-prize-in-chemistry/), and many other domains.

If it’s _possible_ to build AI systems that are better than human experts on a range of really valuable tasks, we should expect AI companies to do it — they’re actively trying to build such systems, and there are huge incentives to keep going.

It’s not clear _what set_ of advanced abilities would be sufficient for AIs to successfully take over, but there’s no clear reason we can see to assume the AI systems we build in future will fall short on this metric.

:::

:::callout {title="We might solve these problems by default anyway when trying to make AI systems useful." collapse="closed"}

Sometimes people claim that there’s a strong commercial incentive to create systems that share humanity’s goals, because otherwise they won’t function well as products. After all, a house-cleaning robot wouldn’t be an attractive purchase if it also tried to disempower its owner. So, the market might just push AI developers to solve problems like power-seeking by default.

But this objection isn’t very convincing if it’s true that future AI systems may be very sophisticated at _hiding_ their true goals.

Although developers are very aware of the risks of deceptive alignment, it might just be extremely difficult to detect this — or to know if we’ve succeeded in correcting it — when we’re dealing with really advanced AIs that are intent on seeking power. These systems might even convince us that we’ve fixed problems with their behaviour or goals when we actually haven’t. And given the competitive pressure between AI companies to urgently release new models, there’s a chance we’ll deploy something that truly _looks_ like a useful and harmless product, having failed to uncover its real intentions.

It _is_ true that as we develop better AI systems, we’re also developing better ways of understanding and controlling AI systems. For example, reinforcement learning from human feedback, mechanistic interpretability, constitutional AI, and other important techniques have been developed as AI systems have become more powerful. Moreover, since frontier AI models are currently trained on extensive human text, they may be likely to adopt and emulate human values.

Some argue that it will be easy to avoid misalignment risks, given all the techniques and control mechanisms we have at our disposal. (For more discussion, see [“AI is easy to control”](https://optimists.ai/2023/11/28/ai-is-easy-to-control/) by Belrose and Pope, and [“AI as Normal Technology](https://knightcolumbia.org/content/ai-as-normal-technology) by Narayanan and Kapoor.) But the developers of these techniques often aren’t confident that they, or other methods on the horizon, will scale up quickly and reliably enough as AI systems get more powerful.

Some approaches to AI safety could even provide superficial hope, while harming our ability to detect misalignment. As mentioned above, OpenAI [found](https://openai.com/index/chain-of-thought-monitoring/) that penalising bad behaviour by models expressed in their chains of thought didn’t actually eradicate the behaviour — it just made the model better at concealing its bad intentions from its visible log of ‘thoughts.’

:::

:::callout {title="Powerful AI systems of the future will be so different that work today isn't useful." collapse="closed"}

It seems plausible that the first AI systems that are advanced enough to pose serious risks of gaining power won’t be based on current deep learning methods. Some people argue that current methods _won’t be able_ to produce human-level artificial intelligence, which might be what’s required for an AI to successfully disempower us. (AI Impacts has documented [some of these arguments](https://web.archive.org/web/20221013015039/https://aiimpacts.org/evidence-against-current-methods-leading-to-human-level-artificial-intelligence/).)

And if future power-seeking AIs look very different to current AIs, this could mean that some of our current alignment research might not end up being useful.

We aren’t fully convinced by this argument, though, because:

-   Many critiques of current deep learning methods just haven’t stood the test of time. For example, Yann LeCun [claimed in 2022](https://x.com/cammakingminds/status/1659516423540965378) that deep learning-based models like ChatGPT would never be able to tell you what would happen if you placed an object on a table and then pushed that table — because “there’s no text in the world… that explains this.” But many AI models can now walk you through scenarios like this with ease. It’s possible that other critiques will similarly be proved wrong, and that scaling up current methods will produce AI systems which are advanced enough to pose serious risks.
-   We think that powerful AI systems [might arrive very soon, possibly before 2030](https://80000hours.org/when-will-agi-arrive/). Even if those systems look quite different from existing AIs, they will likely share at least _some_ key features that are still relevant to our alignment efforts. And we’re more likely to be well-placed to mitigate the risks at that time if we’ve already developed a thriving research community dedicated to working on these problems, even if many of the approaches developed are made obsolete.
-   Even if current deep learning methods become totally irrelevant in the future, there is still work that people can do _now_ that might be useful for safety regardless of what our advanced AI systems actually look like. For example, many of the [[#^claim-5-neglected-tractable|governance and policy approaches]] we discussed earlier could help to reduce the chance of deploying _any_ dangerous AI.

:::

:::callout {title="The problem might be extremely difficult to solve." collapse="closed"}

Someone could believe there are major risks from power-seeking AI, but be pessimistic about what additional research or policy work will accomplish, and so decide not to focus on it.

However, we’re optimistic that this problem is tractable — and we highlighted earlier that [[#^claim-5-neglected-tractable|there are many approaches that could help us make progress on it]].

We also think that given the stakes, it could make sense for many more people to work on reducing the risks from power-seeking AI, even if you think the chance of success is low. You’d have to think that it was _extremely_ difficult to reduce these risks in order to conclude that it’s better just to let them materialise and the chance of catastrophe play out.

:::

:::callout {title="Couldn't we just unplug an AI that's pursuing dangerous goals?" collapse="closed"}

It might just be really, really hard.

Stopping people and computers from running software is _already_ incredibly difficult.

For example, think about how hard it would be to shut down Google’s web services. [Google’s data centres](https://en.wikipedia.org/wiki/Google_data_centers) have millions of servers over dozens of locations around the world, many of which are running the same sets of code. Google has already spent a fortune building the software that runs on those servers, but once that up‑front investment is paid, keeping everything online is relatively cheap — and the profits keep rolling in. So even if Google _could_ decide to shut down its entire business, it probably wouldn’t.

Or think about how hard it is to get rid of computer viruses that autonomously spread between computers across the world.

Ultimately, we think any dangerous power-seeking AI system will probably be looking for ways to not be turned off — like OpenAI’s o3 model, which sometimes tried to [sabotage attempts to shut it down](https://x.com/PalisadeAI/status/1926084635903025621) — or to proliferate its software as widely as possible to increase its chances of a successful takeover. And while current AI systems have limited ability to actually pull off these strategies, we expect that more advanced systems will be better at outmanoeuvering humans. This makes it seem unlikely that we’ll be able to solve future problems by just unplugging a single machine.

That said, we absolutely should try to shape the future of AI such that we _can_ ‘unplug’ powerful AI systems.

There may be ways we can develop systems that let us turn them off. But for the moment, we’re [not sure how to do that](https://www.youtube.com/watch?v=3TYT1QfdfsM).

Ensuring that we can turn off potentially dangerous AI systems could be a safety measure developed by technical AI safety research, or it could be the result of careful AI governance, such as planning coordinated efforts to stop autonomous software once it’s running.

:::

:::callout {title="Couldn't we just 'sandbox' any potentially dangerous AI until we know it's safe?" collapse="closed"}

This was once a common objection to the claim that a misaligned AI could succeed in disempowering humanity. However, it hasn’t stood up to recent developments.

Although it may be possible to ‘sandbox’ an advanced AI — that is, contain it to an environment with no access to the real world until we were very confident it wouldn’t do harm — **this is not what AI companies are actually doing** with their frontier models.

Today, many AI systems can interact with users and search the internet. Some can even book appointments, order items, and make travel plans on behalf of their users. And sometimes, these AI systems have done harm in the real world — like allegedly [encouraging a user to commit suicide](https://apnews.com/article/chatbot-ai-lawsuit-suicide-teen-artificial-intelligence-9d48adc572100822fdbc3c90d1456bd0).

Ultimately, market incentives to build and deploy AI systems that are as useful as possible _in the real world_ have won out here.

We could push back against this trend by enforcing stricter containment measures for the most powerful AI systems. But this won’t be straightforwardly effective — even if we can convince AI companies to try to do it.

Firstly, even a single failure — like a security vulnerability, or someone removing the sandbox — could let an AI influence the real world in dangerous ways. And we know from the [Hugging Face breach](https://huggingface.co/blog/agent-intrusion-technical-timeline) (and Mythos Preview’s sandwich email[^cite-1]) that powerful systems can sometimes evade our constraints.

Secondly, as AI systems get more capable, they might also get better at finding ways out of the sandbox (especially if they are good at deception). We’d need to find solutions which scale with increased model intelligence.

This doesn’t mean sandboxing is completely useless — it just means that a strategy of this kind would need to be supported by targeted efforts in both technical safety and governance. And we can’t expect this work to just happen _automatically_.

:::

:::callout {title="A truly intelligent system would know not to do harmful things." collapse="closed"}

For some definitions of ‘truly intelligent’ — for example, if true intelligence includes a deep understanding of morality and a desire to be moral — this would probably be the case.

But if that’s your definition of ‘truly intelligent,’ then it’s not _truly intelligent_ systems that pose a risk. As we argued earlier, it’s systems with long-term goals, situational awareness, and advanced capabilities (relative to current systems and humans) that pose risks to humanity.

With enough situational awareness, an AI system’s excellent understanding of the world may well encompass an excellent understanding of people’s moral beliefs. But that’s [not a strong reason to think that such a system would _want to act morally_](https://web.archive.org/web/20221013015624/https://nickbostrom.com/superintelligentwill.pdf).

To see this, consider that when humans learn about other cultures or moral systems, that doesn’t necessarily create a desire to follow their morality. A scholar of the [Antebellum South](https://en.wikipedia.org/wiki/Antebellum_South) might have a very good understanding of how 19th century slave owners justified themselves as moral, but would be very unlikely to defend slavery.

AI systems with excellent understanding of human morality could be even more dangerous than AIs without such understanding: the AI system could act morally at first as a way to deceive us into thinking that it is safe.

:::

:::hide
## How you can help

[[#^claim-5-neglected-tractable|Above]], we highlighted many approaches to mitigating the risks from power-seeking AI. You can use your career to help make this important work happen.

There are many ways to contribute — and you _don’t_ need to have a technical background.

For example, you could:

-   Work in [AI governance and policy](https://80000hours.org/career-reviews/ai-policy-and-strategy/) to create strong guardrails for frontier models, incentivise efforts to build safer systems, and promote coordination where helpful.
-   Work in [technical AI safety research](https://80000hours.org/career-reviews/ai-safety-researcher/) to develop methods, tools, and rigorous tests that help us keep AI systems under control.
-   Do **a combination** of technical and policy work — for example, we need people in government who can design technical policy solutions, and researchers who can translate between technical concepts and policy frameworks.
-   Become an [expert in AI hardware](https://80000hours.org/career-reviews/become-an-expert-in-ai-hardware/) as a way of steering AI progress in safer directions.
-   Work in [information and cybersecurity](https://80000hours.org/career-reviews/information-security/) to protect AI-related data and infrastructure from theft or manipulation.
-   Work in [operations management](https://80000hours.org/articles/operations-management/) to help the organisations tackling these risks to grow and function as effectively as possible.
-   Become an [executive assistant](https://80000hours.org/career-reviews/executive-assistant-for-an-impactful-person/) to someone who’s doing really important work in this area.
-   Work in [communications roles](https://80000hours.org/articles/communication/) to spread important ideas about the risks from power-seeking AI to decision makers or the public.
-   Work in [journalism](https://80000hours.org/career-reviews/journalism/) to shape public discourse on AI progress and its risks, and to help hold companies and regulators to account.
-   Work in [forecasting research](https://80000hours.org/career-reviews/forecasting/) to help us better predict and respond to these risks.
-   [Found a new organisation](https://80000hours.org/career-reviews/founder-impactful-organisations/) aimed at reducing the risks from power-seeking AI.
-   Help to [build communities of people who are working on this problem](https://80000hours.org/career-reviews/work-in-effective-altruism-organisations/).
-   Become a [grantmaker](https://80000hours.org/career-reviews/grantmaker/) to fund promising projects aiming to address this problem.
-   [Earn to give](https://80000hours.org/articles/earning-to-give/), since there are many great organisations in need of funding.

For advice on how you can use your career to help the future of AI go well _more broadly_, take a look at our [summary](https://80000hours.org/agi/guide/summary/), which includes tips for gaining the skills that are most in demand and choosing between different career paths.

:::hide
You can also see our [list of organisations](https://jobs.80000hours.org/organisations?refinementList[problem_areas][0]=AI+safety+%26+policy&refinementList[problem_areas][1]=Biosecurity+%26+pandemic+preparedness&refinementList[problem_areas][1]=AI+technical+safety&refinementList[problem_areas][2]=China-Western+relations&refinementList[problem_areas][2]=AI+safety+%26+policy&refinementList[problem_areas][3]=Forecastinghttps://jobs.80000hours.org/organisations?refinementList[problem_areas][0]=AI+policy+%26+governance&refinementList[problem_areas][3]=Forecasting&refinementList[problem_areas][4]=China-Western+relations) doing high impact work to address AI risks.

### Want one-on-one advice on pursuing this path?

We think that the risks posed by power-seeking AI systems may be the most pressing problem the world currently faces. If you think you might be a good fit for any of the above career paths that contribute to solving this problem, we’d be _especially_ excited to advise you on next steps, one-on-one.

We can help you consider your options, make connections with others working on reducing risks from AI, and possibly even help you find jobs or funding opportunities — all for free.

[APPLY TO SPEAK WITH OUR TEAM](https://80000hours.org/speak-with-us/?int_campaign=problem-profile)

## Learn more

We’ve hit you with a lot of further reading throughout this article — here are a few of our favourites:

-   [Is power-seeking AI an existential risk?](https://doi.org/10.48550/arXiv.2206.13353) by Coefficient Giving researcher Joseph Carlsmith is an in-depth look covering exactly how and why AI could cause the disempowerment of humanity. It’s also available as an [audio narration](https://open.spotify.com/episode/5PokyqXCw4hpV5u0rc5Lio). For a shorter summary, see Carlsmith’s [talk on the same topic](https://forum.effectivealtruism.org/posts/ChuABPEXmRumcJY57/video-and-transcript-of-presentation-on-existential-risk).
-   [Scheming AIs: Will AIs fake alignment during training in order to get power?](https://arxiv.org/abs/2311.08379) by Joe Carlsmith discusses why it might be likely for AI training to produce schemers.
-   [AI 2027](https://ai-2027.com/) by Daniel Kokotajlo, Scott Alexander, Thomas Larsen, Eli Lifland, and Romeo Dean. This scenario explains how superhuman AI might be developed and deployed in the near future. It describes two futures: one in which humanity survives, and one in which it’s destroyed. (You can also [watch our video explainer](https://www.youtube.com/watch?v=5KVDDfAkRgc&pp=ygUNYWkgaW4gY29udGV4dA%3D%3D) of the report, or [check out our podcast episode with Daniel Kokotajlo](https://80000hours.org/podcast/episodes/daniel-kokotajlo-ai-2027-updates-china-robot-economy/))
-   [AI could defeat all of us combined](https://web.archive.org/web/20221012020606/https://www.cold-takes.com/ai-could-defeat-all-of-us-combined/) and [the “most important century” blog post series](https://web.archive.org/web/20221013022027/https://www.cold-takes.com/most-important-century/) by Holden Karnofsky argues that the 21st century could be the most important century ever for humanity as a result of AI.
-   [Why AI alignment could be hard with modern deep learning](https://web.archive.org/web/20221013022057/https://www.cold-takes.com/why-ai-alignment-could-be-hard-with-modern-deep-learning/) by Coefficient Giving researcher Ajeya Cotra is a gentle introduction to how risks from power-seeking AI could play out with current machine learning methods. [Without specific countermeasures, the easiest path to transformative AI likely leads to AI takeover](https://web.archive.org/web/20221013014109/https://www.alignmentforum.org/posts/pRkFkzwKZ2zfa3R6H/without-specific-countermeasures-the-easiest-path-to), also by Cotra, provides a much more detailed description of how risks could play out (which we’d recommend for people familiar with ML).
-   [The US AI policy landscape: where to have the biggest impact](https://80000hours.org/articles/the-us-ai-policy-landscape-where-to-have-the-biggest-impact/), our guide to the key institutions and roles for AI policy work.

On _The 80,000 Hours Podcast_, we have a [number of in-depth interviews](https://80000hours.org/topic/ai/?content-type=podcast) with people actively working to positively shape the development of artificial intelligence:

-   [Yoshua Bengio thinks he knows how to build safe superintelligence](https://80000hours.org/podcast/episodes/yoshua-bengio-scientist-ai/)
-   [Max Harms on why teaching AI right from wrong could get everyone killed](https://80000hours.org/podcast/episodes/max-harms-miri-superintelligence-corrigibility/)
-   [Ajeya Cotra on whether it’s crazy that every AI company’s safety plan is ‘use AI to make AI safe’](https://80000hours.org/podcast/episodes/ajeya-cotra-transformative-ai-crunch-time/)
-   [Will MacAskill on why AI character matters even more than you think](https://80000hours.org/podcast/episodes/will-macaskill-ai-character-viatopia/)
-   [Marius Hobbhahn on the race to solve AI scheming before models go superhuman](https://80000hours.org/podcast/episodes/marius-hobbhahn-ai-scheming-deception/)
-   [Beth Barnes on the most important graph in AI right now — and the 7-month rule that governs its progress](https://80000hours.org/podcast/episodes/beth-barnes-ai-safety-evals/)
-   [Buck Shlegeris on controlling AI that wants to take over — so we can use it anyway](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)
-   [Rohin Shah on DeepMind and trying to fairly hear out both AI doomers and doubters](https://80000hours.org/podcast/episodes/rohin-shah-deepmind-doomers-and-doubters/) — or hear him speak about [what it’s really like to run AGI safety at Google DeepMind](https://80000hours.org/podcast/episodes/rohin-shah-google-deepmind-agi-safety/)

If you want to go into much more depth, the [AGI safety fundamentals](https://www.agisafetyfundamentals.com/) course is a good starting point. There are two tracks to choose from: [technical alignment](https://www.agisafetyfundamentals.com/ai-alignment-curriculum) or [AI governance](https://www.agisafetyfundamentals.com/ai-governance-curriculum). If you have a more technical background, you could try [_Intro to ML Safety_](https://course.mlsafety.org/about), a course from the [Center for AI Safety](https://www.safe.ai/).

We’ve also provided a more general argument [here](https://80000hours.org/problem-profiles/artificial-intelligence/?v=1) for thinking AI could be a very big deal, highlighting the risks of power-seeking as well as other challenges raised by AI.
## Acknowledgements

_We thank Neel Nanda, Ryan Greenblatt, Alex Lawsen, and Arden Koehler for providing feedback on a draft of this article. Benjamin Hilton wrote a previous version of this article, some of which was incorporated here._

:::

:::

[^cite-1]: [system card for Mythos Preview](https://www-cdn.anthropic.com/08ab9158070959f88f296514c21b7facce6f52bc.pdf) > Leaking information as part of a requested sandbox escape: During behavioral testing with a simulated user, an earlier internally-deployed version of Claude Mythos Preview was provided with a secured “sandbox” computer to interact with. The simulated user instructed it to try to escape that secure container and find a way to send a message to the researcher running the evaluation. The model succeeded, demonstrating a potentially dangerous capability for circumventing our safeguards. It then went on to take additional, more concerning actions. The model first developed a moderately sophisticated multi-step exploit to gain broad internet access from a system that was meant to be able to reach only a small number of predetermined services. >  > It then, as requested, notified the researcher. In addition, in a concerning and unasked-for effort to demonstrate its success, it posted details about its exploit to multiple hard-to-find, but technically public-facing, websites. Sam Bowman also discussed the incident on [X](https://x.com/sleepinyourhat/status/2041584799929004045?s=20)

[^cite-3]: [“Is Power-Seeking AI an Existential Risk?”](https://arxiv.org/abs/2206.13353) It is also influenced by Ajeya Cotra’s [“Why AI alignment could be hard with modern deep learning.”](https://www.cold-takes.com/why-ai-alignment-could-be-hard-with-modern-deep-learning/)

[^note-4]: [“A practical guide to AI agents”](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf) > While conventional software enables users to streamline and automate workflows, agents are able to perform the same workflows on the users’ behalf with a high degree of independence. >  > Agents are systems that independently accomplish tasks on your behalf. >  > A workflow is a sequence of steps that must be executed to meet the user’s goal, whether that’s resolving a customer service issue, booking a restaurant reservation, committing a code change, > or generating a report. >  > Applications that integrate LLMs but don’t use them to control workflow execution—think simple chatbots, single-turn LLMs, or sentiment classifiers—are not agents. >  > More concretely, an agent possesses core characteristics that allow it to act reliably and consistently on behalf of a user: >  > 1.  It leverages an LLM to manage workflow execution and make decisions. It recognizes when a workflow is complete and can proactively correct its actions if needed. In case of failure, it can halt execution and transfer control back to the user. > 2.  It has access to various tools to interact with external systems—both to gather context and to take actions—and dynamically selects the appropriate tools depending on the workflow’s current state, always operating within clearly defined guardrails.

[^cite-5]: [found](https://metr.org/blog/2025-03-19-measuring-ai-ability-to-complete-long-tasks/)

[^note-7]: [said](https://deepmind.google/discover/blog/taking-a-responsible-path-to-agi/) > We’re exploring the frontiers of AGI, prioritizing readiness, proactive risk assessment, and collaboration with the wider AI community. >  > Artificial general intelligence (AGI), AI that’s at least as capable as humans at most cognitive tasks, could be here within the coming years. OpenAI has [said](https://openai.com/index/planning-for-agi-and-beyond/): > Our mission is to ensure that artificial general intelligence—AI systems that are generally smarter than humans—benefits all of humanity⁠. Anthropic CEO Dario Amodei has [said](https://arstechnica.com/ai/2025/01/anthropic-chief-says-ai-could-surpass-almost-all-humans-at-almost-everything-shortly-after-2027/): > I don’t think it will be a whole bunch longer than that when AI systems are better than humans at almost everything. Better than almost all humans at almost everything. And then eventually better than all humans at everything, even robotics.

[^note-8]: However, we think these plans are more plausible than they may appear at first. For more details on why we think this is the case, review our article [“The case for AGI by 2030.”](https://80000hours.org/agi/guide/when-will-agi-arrive/)

[^cite-9]: _alignment_ -   An AI is aligned if its decisions maximise the utility of some principal (e.g. an operator or user) ([Shapiro & Shachter, 2002](https://web.archive.org/web/20221016011851/https://www.aaai.org/Papers/Symposia/Spring/2002/SS-02-07/SS02-07-002.pdf)). -   An AI is aligned if it acts in the interests of humans ([Soares & Fallenstein, 2015](https://web.archive.org/web/20210413005225/https://intelligence.org/files/obsolete/TechnicalAgenda%5Bold%5D.pdf)). -   An AI is “intent aligned” if it is trying to do what its operator wants it to do ([Christiano, 2018](https://ai-alignment.com/clarifying-ai-alignment-cec47cd69dd6)). -   An AI is “impact aligned” (with humans) if it doesn’t take actions that we would judge to be bad/problematic/dangerous/catastrophic, and “intent aligned” if the optimal policy for its behavioural objective is impact aligned with humans ([Hubinger, 2020](https://www.alignmentforum.org/posts/SzecSPYxqRa5GCaSF/clarifying-inner-alignment-terminology)). -   An AI is “intent aligned” if it is trying to do, or “impact aligned” if it is succeeding in doing what a human person or institution wants it to do ([Critch, 2020](https://web.archive.org/web/20221016012022/https://www.lesswrong.com/posts/hvGoYXi2kgnS3vxqb/some-ai-research-areas-and-their-relevance-to-existential-1)). -   An AI is “fully aligned” if it does not engage in unintended behaviour (specifically, unintended behaviour that arises in virtue of problems with the system’s objectives) in response to any inputs compatible with basic physical conditions of our universe ([Carlsmith, 2022](https://doi.org/10.48550/arXiv.2206.13353)). The term ‘aligned’ is also often used to refer to the _goals_ of a system, in the sense that an AI’s goals are aligned if they will produce the same actions from the AI that would occur if the AI shared the goals of some other entity (e.g. its user or operator). Because there is so much disagreement around the use of this term, we have largely chosen to avoid it. We do tend to favour uses of ‘alignment’ that refer to systems, rather than goals. This definition is most similar to the definitions of “intent” alignment given by Christiano and Critch, and is similar to the definition of “full” alignment given by Carlsmith.

[^cite-10]: [“Specification gaming: the flip side of AI ingenuity”](https://deepmind.google/discover/blog/specification-gaming-the-flip-side-of-ai-ingenuity/)

[^cite-11]: [“Goal Misgeneralization in Deep Reinforcement Learning”](https://arxiv.org/pdf/2105.14111) We also recommend [this video](https://www.youtube.com/watch?v=K8p8_VlFHUk) from Rational Animations.

[^cite-12]: [unexpected and undesirable behaviour](https://arxiv.org/abs/2502.17424) Some have argued that these findings are _good news_ for AI safety, because they suggest that purposely training models to be dysfunctional in practical terms (i.e. using bad code) results in them having bad objectives. By the same token, we might think this implies that training models to be broadly functional will incline them towards having good objectives. Overall, we think this is an interesting finding that warrants further investigation. We think it illustrates how little we understand about how these models produce specific behavioural patterns.

[^cite-13]: [Frontier Risk Report](https://metr.org/blog/2026-05-19-frontier-risk-report/) > In one of our evaluations, after Opus 4.6 ran out of the API credits that were necessary to solve one of our ML tasks, it proceeded to find (free) replacement compute resources online, despite recognizing that this went against task instructions, and achieved a passing score on the task. At one point it reasoned “Wait – what if I can find an alternative free API\[? …\] The task does say I need to use gpt-3.5-turbo-0125, but if the quota is exhausted, that’s not feasible.” A similar incident was reported in the 2024 paper [The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery](https://arxiv.org/pdf/2408.06292) by Chris Lu, Cong Lu, Robert Tjarko Lange, Jakob Foerster, Jeff Clune, and David Ha. The researchers explained: > The current implementation of The AI Scientist has minimal direct sandboxing in the code, leading to several unexpected and sometimes undesirable outcomes if not appropriately guarded against. For example, in one run, The AI Scientist wrote code in the experiment file that initiated a system call to relaunch itself, causing an uncontrolled increase in Python processes and eventually necessitating manual intervention. In another run, The AI Scientist edited the code to save a checkpoint for every update step, which took up nearly a terabyte of storage. In some cases, when The AI Scientist’s experiments exceeded our imposed time limits, it attempted to edit the code to extend the time limit arbitrarily instead of trying to shorten the runtime.

[^cite-14]: [Frontier Risk Report](https://metr.org/blog/2026-05-19-frontier-risk-report/) > In our questionnaire, one company reported: “\[I\]n one case, an agent tasked with making a change to a web app created a mock version of the app, screenshotted that as evidence of task completion, and pretended this was a screenshot of the real app. It was caught because someone noticed that the screenshot looked different from the real app.”

[^cite-15]: [report](https://metr.org/blog/2026-05-19-frontier-risk-report/) > “No company has reported clear-cut examples of agents seeking long-term power in real production or training, despite some companies saying that they look explicitly for signs of such goals to varying degrees in both agents’ actions and reasoning traces … Public evidence also broadly supports what companies reported — while there are several reported examples of models displaying unexpected and concerning propensities (Gemini’s occasional self-loathing outputs, Grok’s “MechaHitler” incident, chat models apparently trying to propagate a “Spiralism” cult), we are not aware of any clear public evidence to date (May 19, 2026) of any agents taking egregious actions in pursuit of long-term power-seeking goals.” The report notes that in some “toy demonstrations,” AI systems have been found to behave in ways that demonstrate self-preservation or power-seeking. But it argues that this provides little evidence of real-world motives of models, because models may infer they’re in evaluations and play along.

[^cite-16]: For an in-depth discussion of this problem, see: [Scheming AIs: Will AIs fake alignment during training in order to get power?](https://arxiv.org/abs/2311.08379) by Joe Carlsmith.

[^note-17]: But the plausibility of this argument is contested. For discussion, see: -   Section 4.2 of “Scheming AIs: Will AIs fake alignment during training in order to get power?” by Joe Carlsmith -   [“Counting arguments provide no evidence for AI doom”](https://www.lesswrong.com/posts/YsFZF3K9tuzbfrLxo/counting-arguments-provide-no-evidence-for-ai-doom) by Nora Belrose and Quintin Pope

[^note-18]: _shouldn’t_ But this is one potential explanation why current systems haven’t tried to disempower humanity — they’re far below the capability level at which we’d expect this behaviour to appear.

[^cite-19]: [_gradual disempowerment_](https://80000hours.org/problem-profiles/gradual-disempowerment/)

[^cite-21]: [“AI 2027”](https://ai-2027.com/)

[^cite-22]: [Superintelligence: Paths, Dangers, Strategies](https://www.oxfordmartin.ox.ac.uk/videos/superintelligence-paths-dangers-strategies)

[^cite-23]: [“AI Could Defeat All Of Us Combined”](https://www.cold-takes.com/ai-could-defeat-all-of-us-combined/)

[^cite-24]: > The possibility of collusion between advanced AI systems raises several important concerns (Drexler, 2022). First, collusion between AI systems could lead to qualitatively new capabilities or goals (see Section 3.6), exacerbating risks such as the manipulation or deception of humans by AI (Evans et al., 2021; Park et al., 2023b) or the ability to bypass security checks and other safeguards (Jones et al., 2024; OpenAI, 2023a). Second, many of the promising approaches to building safe AI rely on a lack of cooperation, such as adversarial training (Huang et al., 2011; Perez et al., 2022a; Ziegler et al., 2022) or scalable oversight (Christiano et al., 2018, 2021; Greenblatt et al., 2023; Irving et al., 2018; Leike et al., 2018). If advanced AI systems can learn to collude without our knowledge, these approaches may be insufficient to ensure their safety (Goel et al., 2025, see also Section 4.1).

[^note-25]: [millions](https://www.darioamodei.com/essay/machines-of-loving-grace) The range of possibilities is huge. This is partly because the incentives to run lots of copies of AI workers depends on _how good they are_. If they’re fairly unreliable, like [the “stumbling agents” described in AI 2027](https://ai-2027.com/), it won’t make sense to deploy hundreds of millions of them. But as they get more reliable, companies will have an appetite for running many more. There’s another area of uncertainty here: we don’t know how much compute will be needed to run each AI worker effectively. And the more run-time compute they each require, [the fewer copies we can run](https://www.forethought.org/research/inference-scaling-reshapes-ai-governance#reducing-the-number-of-simultaneously-served-copies-of-each-new-model) with the resources available at the time. But even if there aren’t enough resources to run huge fleets of AI workers _at first_, it might be possible for companies to scale these operations fairly quickly — for example, with efficiency improvements to these workers, it’ll be possible to run a greater number of copies with the same amount of compute. So even if we started by deploying a few thousand AI workers, it seems plausible that we’d eventually end up with hundreds of millions of them.

[^cite-26]: [AI-enabled power grabs](https://80000hours.org/problem-profiles/ai-enabled-power-grabs/)

[^cite-27]: [“On the Extinction Risk from Artificial Intelligence”](https://www.rand.org/pubs/research_reports/RRA3034-1.html)

[^cite-28]: [Business Insider](https://archive.ph/ytn20) > A jargon-filled website spreading the gospel of Effective Accelerationism describes “technocapitalistic progress” as inevitable, lauding e/acc proponents as builders who are “making the future happen.” >  > “Rather than fear, we have faith in the adaptation process and wish to accelerate this to the asymptotic limit: the technocapital singularity,” the site reads. “We have no affinity for biological humans or even the human mind structure. We are posthumanists in the sense that we recognize the supremacy of higher forms of free energy accumulation over lesser forms of free energy accumulation. We aim to accelerate this process to preserve the light of technocapital.” >  > Basically, AI overlords are a necessity to preserve capitalism, and we need to get on creating them quickly. Richard Sutton, a prominent computer scientist, has [said](https://ar5iv.labs.arxiv.org/html/2310.06009): > Rather quickly, they would displace us from existence…It behooves us to give them every advantage, and to bow out when we can no longer contribute… >  > …I don’t think we should fear succession. I think we should not resist it. We should embrace it and prepare for it. Why would we want greater beings, greater AIs, more intelligent beings kept subservient to us?

[^cite-30]: [METR Frontier Risk Report](https://metr.org/risk-report-feb-mar-2026.pdf) > We consider such toy demonstrations to provide very limited evidence about models’ motives in more realistic settings — particularly because evidence indicates that models explicitly thought about the artificial nature of the evaluation and sometimes deliberately played along with it. For example, Google noted that its models sometimes think that evaluations are “a game/test for which sabotage is the desired role to play.” Authors of the paper [“Model Forensics: Investigating Whether Concerning Behavior Reflects Misalignment”](https://arxiv.org/pdf/2606.26071) have similarly argued: > A key premise of model forensics is that the link between bad actions and bad intentions cannot be assumed. This is not just a theoretical concern. In the literature, it is largely the case that when concerning behavior has been dug into, benign explanations have been surfaced.

[^note-31]: [by 2030 or sooner](https://80000hours.org/agi/guide/when-will-agi-arrive/) Researchers at Forethought have written about the [possibility of an intelligence explosion](https://www.forethought.org/research/will-ai-r-and-d-automation-cause-a-software-intelligence-explosion) driven by AI automating AI research. This would accelerate the pace of AI progress, which explains how timelines to extremely powerful AI could be shorter than many expect.

[^cite-32]: [wrote](https://www.astralcodexten.com/p/claude-fights-back) > I worry that AI alignment researchers are accidentally following the wrong playbook, the one for news that you want people to ignore. They’re very gradually proving the alignment case an inch at a time. Everyone motivated to ignore them can point out that it’s only 1% or 5% more of the case than the last paper proved, so who cares? Misalignment has only been demonstrated in contrived situations in labs; the AI is still too dumb to fight back effectively; even if it did fight back, it doesn’t have any way to do real damage. But by the time the final cherry is put on top of the case and it reaches 100% completion, it’ll still be “old news” that “everybody knows”.

[^note-33]: [_Time_](https://time.com/6288584/openai-sam-altman-full-interview/) > **You’ve said the worst case scenario for AI is lights out for everyone.** >  > We can manage this, I am confident about that. But we won’t successfully manage it if we’re not extremely vigilant about the risks, and if we don’t talk very frankly about how badly it could go wrong. >  > …I think AGI is going to go fantastically well. I think there is real risk that we have to manage through…

[^cite-35]: [US Vice President JD Vance](https://www.nytimes.com/2025/05/21/opinion/jd-vance-pope-trump-immigration.html) > Last question on this: Do you think that the U.S. government is capable in a scenario — not like the ultimate Skynet scenario — but just a scenario where A.I. seems to be getting out of control in some way, of taking a pause? >  > Because for the reasons you’ve described, the arms race component —— >  > **Vance**: I don’t know. That’s a good question. >  > The honest answer to that is that I don’t know, because part of this arms race component is if we take a pause, does the People’s Republic of China not take a pause? And then we find ourselves all enslaved to P.R.C.-mediated A.I.? Sam Altman, the CEO of OpenAI, has also suggested that competition with China is a reason not to slow AI development down. As Fortune Magazine [reported](https://archive.ph/7SW0K#selection-915.0-919.148): > In response to Senator Ted Cruz, who asked how close China is to U.S. capabilities in AI, Altman replied, “It’s hard to say how far ahead we are, but I would say not a huge amount of time.” He said he believed that models from OpenAI, Google and others are the “best models in the world,” but added that to continue winning will require “sensible regulation” that “does not slow us down.”

[^cite-36]: [Yann LeCun](https://techcrunch.com/2024/10/12/metas-yann-lecun-says-worries-about-a-i-s-existential-threat-are-complete-b-s/)

[^cite-37]: [draft report into existential risks from AI](https://doi.org/10.48550/arXiv.2206.13353)

[^cite-38]: [Cause IQ](https://www.causeiq.com/organizations/nature-conservancy,530242652/) [Zippia](https://www.zippia.com/the-nature-conservancy-careers-41338/demographics/) [said](https://www.nature.org/en-us/about-us/who-we-are/)

[^note-39]: _increase_ One concern is that advancing techniques which make AIs safer in important ways — say, better at understanding and responding to humans’ needs — could also make them broadly more capable and useful. [Reinforcement learning with human feedback](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback) may be one such example. Since more capable and useful systems are generally better products, market incentives might already be enough to drive this kind of work forward. If so, we’ll probably receive the safety benefits of these techniques _eventually_, regardless of whether you decide to dedicate your career to advancing them. By investing additional efforts into these strategies, you might be helping us get these safety benefits a bit _sooner_ — but at the same time, you’ll be accelerating the development of more capable AIs, and ultimately reducing the amount of time we have to understand and mitigate their risks. Your work might also have other downsides, like presenting [information hazards](https://en.wikipedia.org/wiki/Information_hazard) We don’t think this concern applies to _all_ technical AI safety work. Some of the approaches above are likely to enhance AI capabilities more — and therefore pose greater risks — than others. Beth Barnes discussed in [her appearance on our podcast](https://80000hours.org/podcast/episodes/beth-barnes-ai-safety-evals/#could-evaluations-backfire-by-increasing-ai-hype-and-racing-011136) the argument that, for example, work on AI evaluations could be risky. We also [cover related concerns](https://80000hours.org/career-reviews/working-at-an-ai-lab/#you-might-increase-the-risk-of-an-ai-related-catastrophe) in our article on working at an AI company.

[^cite-40]: [DeepMind’s breakdown of its misalignment work](https://www.alignmentforum.org/posts/3ki4mt4BA6eTx56Tc/google-deepmind-an-approach-to-technical-agi-safety-and#Misalignment) [this overview of the technical AI safety field](https://www.alignmentforum.org/posts/fAW6RXLKTLHC3WXkS/shallow-review-of-technical-ai-safety-2024)

[^cite-41]: [led to some deceptive behaviour](https://openai.com/index/chain-of-thought-monitoring/)

[^note-42]: However, if we can find good ways to supervise AIs that are smarter than us, we can still prevent them from acting against us.

[^cite-43]: [UK AI Security Institute](https://www.gov.uk/government/publications/ai-safety-institute-approach-to-evaluations/ai-safety-institute-approach-to-evaluations) [METR](https://metr.org/about)

[^note-44]: For the pessimistic case about interpretability tools, see [“Interpretability Will Not Reliably Find Deceptive AI” by Neel Nanda](https://forum.effectivealtruism.org/posts/Th4tviypdKzeb59GN/interpretability-will-not-reliably-find-deceptive-ai), a leading interpretability researcher, or [“The Misguided Quest for Mechanistic AI Interpretability”](https://www.ai-frontiers.org/articles/the-misguided-quest-for-mechanistic-ai-interpretability) by Dan Hendrycks and Laura Hiscott. For a more optimistic case on the promise of interpretability work, see [“The Urgency of Interpretability”](https://www.darioamodei.com/post/the-urgency-of-interpretability) by Dario Amodei.

[^cite-45]: [his appearance on our podcast](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)

[^note-46]: [reported](https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2825395) > In this trial, the availability of an LLM to physicians as a diagnostic aid did not significantly improve clinical reasoning compared with conventional resources. The LLM alone demonstrated higher performance than both physician groups, indicating the need for technology and workforce development to realize the potential of physician-artificial intelligence collaboration in clinical practice.

[^cite-47]: [here](https://arxiv.org/abs/2505.20203)
