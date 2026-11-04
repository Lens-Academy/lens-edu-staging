---
title: "The basic reasons I expect AGI ruin"
author:
  - "Rob Bensinger"
source_url: "https://intelligence.org/2023/04/21/the-basic-reasons-i-expect-agi-ruin/"
published: 2023-04-21
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "Also, I wrote this post to summarize my own top reasons for being worried, not to try to make a maximally compelling or digestible case for others. I don't"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

I’ve been citing [AGI Ruin: A List of Lethalities](https://www.lesswrong.com/posts/uMQ3cqWDPHhjtiesc/agi-ruin-a-list-of-lethalities) to explain why the situation with AI looks lethally dangerous to me. But that post is relatively long, and emphasizes specific open technical problems over “the basics”.

Here are 10 things I’d focus on if I were giving “the basics” on why I’m so worried:[^note-1]

---

1\. **General intelligence is very powerful**, and once we can build it at all, **STEM-capable artificial general intelligence (AGI) is likely to vastly outperform human intelligence immediately (or very quickly)**.

When I say “general intelligence”, I’m usually thinking about “whatever it is that lets human brains do astrophysics, category theory, etc. even though our brains evolved under literally zero selection pressure to solve astrophysics or category theory problems”.

It’s possible that we should already be thinking of GPT-4 as “AGI” on some definitions, so to be clear about the threshold of generality I have in mind, I’ll specifically talk about “STEM-level AGI”, though I expect such systems to be good at non-STEM tasks too.

Human brains aren’t perfectly general, and not all narrow AI systems or animals are equally narrow. (E.g., AlphaZero is more general than AlphaGo.) But it sure is interesting that humans evolved cognitive abilities that unlock _all of these sciences at once_, with zero evolutionary fine-tuning of the brain aimed at equipping us for any of those sciences. Evolution just stumbled into a solution to _other_ problems, that happened to generalize to millions of wildly novel tasks.

More concretely:

-   AlphaGo is a very impressive reasoner, but its hypothesis space is limited to sequences of Go board states rather than sequences of states of the physical universe. Efficiently reasoning about the physical universe requires solving at least some problems that are different in kind from what AlphaGo solves.
    -   These problems might be solved by the STEM AGI’s programmer, and/or solved by the algorithm that finds the AGI in program-space; and some such problems may be solved by the AGI itself in the course of refining its thinking.[^note-2]
-   Some examples of abilities I expect humans to only automate once we’ve built STEM-level AGI (if ever):
    -   The ability to perform open-heart surgery with a high success rate, in a messy non-standardized ordinary surgical environment.
    -   The ability to match smart human performance in a specific hard science field, across all the scientific work humans do in that field.
-   In principle, I suspect you could build a narrow system that is good at those tasks while lacking the basic mental machinery required to do par-human reasoning about _all_ the hard sciences. In practice, I very strongly expect humans to find ways to build general reasoners to perform those tasks, before we figure out how to build narrow reasoners that can do them. (For the same basic reason evolution stumbled on general intelligence so early in the history of human tech development.) [^note-3]

When I say “general intelligence is very powerful”, a lot of what I mean is that _science_ is very powerful, and that having all of the sciences at once is a lot more powerful than the sum of each science’s impact.[^note-4]

Another large piece of what I mean is that (STEM-level) general intelligence _is a very high-impact sort of thing to automate_ because STEM-level AGI is likely to blow human intelligence out of the water immediately, or very soon after its invention.

80,000 Hours gives the (non-representative) example of how AlphaGo and its successors compared to humanity:

> In the span of a year, AI had advanced from being too weak to win a single \[Go\] match against the worst human professionals, to being impossible for even the best players in the world to defeat.

I expect general-purpose science AI to blow human science ability out of the water in a similar fashion.

Reasons for this include:

-   Empirically, humans aren’t near a cognitive ceiling, and even narrow AI often suddenly blows past the human reasoning ability range on the task it’s designed for. It would be weird if scientific reasoning [were an exception](https://intelligence.org/2017/10/20/alphago/).
-   Empirically, human brains are full of cognitive biases and inefficiencies. It’s doubly weird if scientific reasoning is an exception even though it’s _visibly_ a mess with tons of blind spots, inefficiencies, and motivated cognitive processes, and innumerable historical examples of scientists and mathematicians taking decades to make technically simple advances.
-   Empirically, human brains are extremely bad at some of the most basic cognitive processes underlying STEM.
    -   E.g., consider the stark limits on human working memory and ability to do basic mental math. We can barely multiply smallish multi-digit numbers together in our head, when in principle a reasoner could hold thousands of complex mathematical structures in its working memory simultaneously and perform complex operations on them. Consider the sorts of technologies and scientific insights that might only ever occur to a reasoner if it can directly see (within its own head, in real time) the connections between hundreds or thousands of different formal structures.
-   Human brains underwent no direct optimization for STEM ability in our ancestral environment, beyond traits like “I can distinguish four objects in my visual field from five objects”.[^note-5]
-   In contrast, human engineers can deliberately optimize AGI systems’ brains for math, engineering, etc. capabilities; and human engineers have an enormous variety of tools available to build general intelligence that evolution lacked.[^note-6]
-   Software (unlike human intelligence) scales with more compute.
-   Current ML uses far more compute to _find_ reasoners than to _run_ reasoners. This is very likely to hold true for AGI as well.
-   We probably have more than enough compute already, if we knew how to train AGI systems in a remotely efficient way.

And on a meta level: the hypothesis that STEM AGI can quickly outperform humans has a disjunctive character. There are [many different advantages](https://aiimpacts.org/sources-of-advantage-for-artificial-intelligence/) that individually suffice for this, even if STEM AGI doesn’t start off with any other advantages. (E.g., speed, math ability, scalability with hardware, skill at optimizing hardware…)

In contrast, the claim that STEM AGI will [hit the narrow target](https://twitter.com/robbensinger/status/1623835453110775810) of “par-human scientific ability”, _and_ stay at around that level for long enough to let humanity adapt and adjust, has a conjunctive character.[^note-7]

2\. A common misconception is that STEM-level AGI is dangerous because of something murky about “agents” or about self-awareness. Instead, I’d say that **the danger is inherent to the nature of action sequences** that push the world toward some sufficiently-hard-to-reach state.[^note-8]

Call such sequences “plans”.

If you sampled a random plan from the space of all writable plans (weighted by length, in any extant formal language), and all we knew about the plan is that executing it would successfully achieve some superhumanly ambitious technological goal like “invent fast-running [whole-brain emulation](https://www.lesswrong.com/tag/whole-brain-emulation) “, then hitting a button to execute the plan would kill all humans, with very high probability. This is because:

-   “Invent fast WBE” is a hard enough task that succeeding in it usually requires gaining a lot of knowledge and cognitive and technological capabilities, enough to do lots of other dangerous things.
-   “Invent fast WBE” is likelier to succeed if the plan also includes steps that gather and control as many resources as possible, eliminate potential threats, etc. These are “ [convergent instrumental strategies](https://arbital.com/p/instrumental_convergence/) “—strategies that are useful for pushing the world in a particular direction, almost regardless of which direction you’re pushing.
-   Human bodies and the food, water, air, sunlight, etc. we need to live are resources (“you are made of atoms the AI can use for something else”); and we’re also potential threats (e.g., we could build a rival superintelligent AI that executes a totally different plan).

The danger is in the cognitive work, not in some complicated or emergent feature of the “agent”; it’s in the task itself.

It isn’t that the abstract space of plans was built by evil human-hating minds; it’s that the [instrumental convergence](https://nickbostrom.com/superintelligentwill.pdf) thesis holds for the plans themselves. In full generality, plans that succeed in goals like “build WBE” tend to be dangerous.

This isn’t true of all plans that successfully push our world into a specific (sufficiently-hard-to-reach) physical state, but it’s true of the vast majority of them.

This is counter-intuitive because most of the impressive “plans” we encounter today are generated by humans, and it’s tempting to view strong plans through a human lens. But humans have hugely overlapping values, thinking styles, and capabilities; AI is drawn from new distributions.

3\. Current ML work is on track to produce things that are, in the ways that matter, **more like “randomly sampled plans” than like “the sorts of plans a civilization of human von Neumanns would produce”**. (Before we’re anywhere near being able to produce the latter sorts of things.) [^note-9]

We’re building “AI” in the sense of building powerful general search processes (and search processes for search processes), not building “AI” in the sense of building friendly ~humans but in silicon.

(Note that “we’re going to build systems that are more like A Randomly Sampled Plan than like A Civilization of Human Von Neumanns” doesn’t imply that the plan we’ll get is the one we wanted! There are two separate problems: that current ML finds things-that-act-like-they’re-optimizing-the-task-you-wanted rather than things-that-actually-internally-optimize-the-task-you-wanted, and also that internally ~maximizing most superficially desirable ends will kill humanity.)

Note that the same problem holds for systems trained to imitate humans, if those systems scale to being able to do things like “build whole-brain emulation”. “We’re training on something related to humans” doesn’t give us “we’re training things that are best thought of as humans plus noise”.

It’s not obvious to me that GPT-like systems can scale to capabilities like “build WBE”. But if they do, we face the [problem](https://twitter.com/ESYudkowsky/status/1628835920328929281) that most ways of successfully imitating humans don’t look like “build a human (that’s somehow superhumanly good at imitating the Internet)”. They look like “build a relatively complex and alien optimization process that is good at imitation tasks (and potentially at many other tasks)”.

You don’t need to be a human in order to model humans, any more than you need to be a cloud in order to model clouds well. The only reason this is more confusing in the case of “predict humans” than in the case of “predict weather patterns” is that humans and AI systems are both intelligences, so it’s easier to slide between “the AI models humans” and “the AI is basically a human”.

4\. The key differences between humans and “things that are more easily approximated as random search processes than as humans-plus-a-bit-of-noise” **lies in lots of complicated machinery in the human brain**.

(Cf. [Detached Lever Fallacy](https://www.lesswrong.com/posts/zY4pic7cwQpa9dnyk/detached-lever-fallacy), [Niceness Is Unnatural](https://www.lesswrong.com/posts/krHDNc7cDvfEL8z9a/niceness-is-unnatural), and [Superintelligent AI Is Necessary For An Amazing Future, But Far From Sufficient](https://www.lesswrong.com/posts/HoQ5Rp7Gs6rebusNP/superintelligent-ai-is-necessary-for-an-amazing-future-but-1).)

Humans are not blank slates in the relevant ways, such that just raising an AI like a human solves the problem.

This doesn’t mean the problem is unsolvable; but it means that you either need to reproduce that internal machinery, in a lot of detail, in AI, or you need to build some new kind of machinery that’s safe for reasons other than the specific reasons humans are safe.

(You need cognitive machinery that somehow samples from a much narrower space of plans that are still powerful enough to succeed in at least one task that saves the world, but are constrained in ways that make them far less dangerous than the larger space of plans. And you need a thing that _actually_ implements internal machinery like that, as opposed to just being optimized to superficially behave as though it does in the narrow and unrepresentative environments it was in before starting to work on WBE. “Novel science work” means that pretty much everything you want from the AI is out-of-distribution.)

5\. **STEM-level AGI timelines don’t look that long** (e.g., probably not 50 or 150 years; could well be 5 years or 15).

I won’t try to argue for this proposition, beyond pointing at the field’s recent [progress](https://twitter.com/leopoldasch/status/1638848850516672513) and echoing [Nate Soares’ comments](https://www.lesswrong.com/posts/cCMihiwtZx7kdcKgt/comments-on-carlsmith-s-is-power-seeking-ai-an-existential#Timelines) from early 2021:

> \[…\] I observe that, 15 years ago, everyone was saying AGI is far off because of what it couldn’t do — basic image recognition, go, starcraft, winograd schemas, simple programming tasks. But basically all that has fallen. The gap between us and AGI is made mostly of intangibles. (Computer programming that is Actually Good? Theorem proving? Sure, but on my model, “good” versions of those are a hair’s breadth away from full AGI already. And the fact that I need to clarify that “bad” versions don’t count, speaks to my point that the only barriers people can name right now are intangibles.) That’s a very uncomfortable place to be!
> 
> \[…\] I suspect that I’m in more-or-less the “penultimate epistemic state” on AGI timelines: I don’t know of a project that seems like they’re right on the brink; that would put me in the “final epistemic state” of thinking AGI is imminent. But I’m in the second-to-last epistemic state, where I wouldn’t feel all that shocked to learn that some group has reached the brink. Maybe I won’t get that call for 10 years! Or 20! But it could also be 2, and I wouldn’t get to be indignant with reality. I wouldn’t get to say “but all the following things should have happened first, before I made that observation!”. Those things have happened. I have made those observations. \[…\]

I think timing tech is [very difficult](https://intelligence.org/2017/10/13/fire-alarm/) (and plausibly ~impossible when the tech isn’t pretty imminent), and I think reasonable people can disagree a lot about timelines.

I also think converging on timelines is not very crucial, since if AGI is 50 years away I would say it’s still the largest single risk we face, and the bare minimum alignment work required for surviving that transition could easily take longer than that.

Also, “STEM AGI when?” is the kind of argument that requires hashing out people’s predictions about how we get to STEM AGI, which is a bad thing to debate publicly insofar as improving people’s models of pathways can further shorten timelines.

I mention timelines anyway because they are in fact a major reason I’m pessimistic about our prospects; if I learned tomorrow that AGI were 200 years away, I’d be outright optimistic about things going well.

6\. **We don’t currently know how to do alignment**, we don’t seem to have a much better idea now than we did 10 years ago, and there are many large novel visible difficulties. (See [AGI Ruin](https://www.lesswrong.com/posts/GNhMPAWcfBCASy8e6/a-central-ai-alignment-problem-capabilities-generalization) and the [Capabilities Generalization, and the Sharp Left Turn](https://www.lesswrong.com/posts/GNhMPAWcfBCASy8e6/a-central-ai-alignment-problem-capabilities-generalization).)

On a more basic level, quoting [Nate Soares](https://intelligence.org/ensuring): “Why do I think that AI alignment looks fairly difficult? The main reason is just that this has been my experience from actually working on these problems.”

7\. We should be starting with a pessimistic prior about **achieving reliably good behavior in any complex safety-critical software, particularly if the software is novel**. Even more so if the thing we need to make robust is structured like undocumented spaghetti code, and more so still if the field is highly competitive and you need to achieve some robustness property _while moving faster_ than a large pool of less-safety-conscious people who are racing toward the precipice.

The [default](https://www.lesswrong.com/posts/Ke2ogqSEhL2KCJCNx/security-mindset-lessons-from-20-years-of-software-security) assumption is that complex software goes wrong in dozens of different ways you didn’t expect. Reality ends up being thorny and inconvenient in many of the places where your models were absent or fuzzy. Surprises are abundant, and some surprises can be good, but this is empirically a lot rarer than unpleasant surprises in software development hell.

The future is hard to predict, but plans systematically take longer and run into more snags than humans naively expect, as opposed to plans systematically going surprisingly smoothly and deadlines being systematically hit ahead of schedule.

The history of computer security and of safety-critical software systems is almost invariably one of robust software lagging far, far behind non-robust versions of the same software. Achieving any robustness property in complex software that will be deployed in the real world, with all its messiness and adversarial optimization, is very difficult and usually fails.

In many ways I think the foundational discussion of AGI risk is [Security Mindset and Ordinary Paranoia](https://intelligence.org/2017/11/25/security-mindset-ordinary-paranoia/) and [Security Mindset and the Logistic Success Curve](https://intelligence.org/2017/11/26/security-mindset-and-the-logistic-success-curve/), and the main body of the text doesn’t even mention AGI. Adding in the specifics of AGI and smarter-than-human AI takes the risk from “dire” to “seemingly overwhelming”, but adding in those specifics is not required to be massively concerned if you think getting this software right matters for our future.

8\. **Neither ML nor the larger world is currently taking this seriously**, as of April 2023.

This is obviously something we can change. But until it’s changed, things will continue to look very bad.

Additionally, most of the people who are taking AI risk somewhat seriously are, to an important extent, not willing to worry about things until after they’ve been experimentally proven to be dangerous. Which is a lethal sort of methodology to adopt when you’re working with smarter-than-human AI.

My basic picture of _why_ the world currently isn’t responding appropriately is the one in [Four mindset disagreements behind existential risk disagreements in ML](https://www.lesswrong.com/posts/84BJopKvQ8qYGHY6b/four-mindset-disagreements-behind-existential-risk), [The inordinately slow spread of good AGI conversations in ML](https://www.lesswrong.com/posts/Rkxj7TFxhbm59AKJh/the-inordinately-slow-spread-of-good-agi-conversations-in-ml), and [_Inadequate Equilibria_](https://equilibriabook.com/toc).[^note-10]

9\. As noted above, **current ML is very opaque**, and **it mostly lets you intervene on behavioral proxies** for what we want, rather than letting us directly design desirable features.

ML as it exists today also requires that data is readily available and safe to provide. E.g., we can’t robustly train the AGI on “don’t kill people” because we can’t provide real examples of it killing people to train against the behavior we don’t want; we can only give flawed proxies and work via indirection.

10\. **There are lots of specific abilities** which seem like they ought to be possible for the kind of civilization that can safely deploy smarter-than-human optimization, that are far out of reach, with no obvious path forward for achieving them with opaque deep nets even if we had unlimited time to work on some relatively concrete set of research directions.

(Unlimited time suffices if we can set a more abstract/indirect research direction, like “just think about the problem for a long time until you find some solution”. There are presumably paths forward; we just don’t know what they are today, which puts us in a worse situation.)

E.g., we don’t know how to go about inspecting a nanotech-developing AI system’s brain to verify that it’s only thinking about a specific room, that it’s internally representing the intended goal, that it’s directing its optimization at that representation, that it internally has a particular planning horizon and a variety of capability bounds, that it’s unable to think about optimizers (or specifically about humans), or that it otherwise has the right topics internally whitelisted or blacklisted.

Individually, it seems to me that each of these difficulties can be addressed. In combination, they seem to me to put us in a very dark situation.

---

One common response I hear to points like the above is:

> The future is generically hard to predict, so it’s just not possible to be rationally confident that things will go well or poorly. Even if you look at dozens of different arguments and framings and the ones that hold up to scrutiny nearly all seem to point in the same direction, it’s always possible that you’re making some invisible error of reasoning that causes correlated failures in many places at once.

I’m sympathetic to this because I agree that the future is hard to predict.

I’m not totally confident things will go poorly; if I were, I wouldn’t be trying to solve the problem! I think things are looking extremely dire, but not hopeless.

That said, some people think that even “extremely dire” is an impossible belief state to be in, in advance of an AI apocalypse actually occurring. I disagree here, for two basic reasons:

a. There are many details we can get into, but on a core level **I don’t think the risk is particularly complicated or hard to reason about**. The core concern fits into a [tweet](https://twitter.com/robbensinger/status/1644006731792646145):

> STEM AI is likely to vastly exceed human STEM abilities, conferring a decisive advantage. We aren’t on track to knowing how to aim STEM AI at intended goals, and STEM AIs pursuing unintended goals tend to have instrumental subgoals like “control all resources”.

Zvi Mowshowitz [puts the core concern](https://thezvi.substack.com/p/response-to-tyler-cowens-existential) in even more basic terms:

> I also notice a kind of presumption that things in most scenarios will work out and that doom is dependent on particular ‘distant possibilities,’ that often have many logical dependencies or require a lot of things to individually go as predicted. Whereas I would say that those possibilities are not so distant or unlikely, but more importantly that the result is robust, that once the intelligence and optimization pressure that matters is no longer human that most of the outcomes are existentially bad by my values and that one can reject or ignore many or most of the detail assumptions and still see this.

The details do matter for evaluating the exact risk level, but this isn’t the sort of topic where it seems fundamentally impossible for any human to reach a good understanding of the core difficulties and whether we’re handling them.

b. Relatedly, as Nate Soares has argued, **AI disaster scenarios are** [**disjunctive**](https://www.lesswrong.com/posts/ervaGwJ2ZcwqfCcLx/agi-ruin-scenarios-are-likely-and-disjunctive). There are many bad outcomes for every good outcome, and many paths leading to disaster for every path leading to utopia.

Quoting [Eliezer Yudkowsky](https://twitter.com/ESYudkowsky/status/1644045728983969816):

> You don’t get to adopt a prior where you have a 50-50 chance of winning the lottery “because either you win or you don’t”; the question is not whether we’re uncertain, but whether someone’s allowed to milk their uncertainty to expect good outcomes.

Quoting [Jack Rabuck](https://twitter.com/JackRabuck/status/1644762977504227329):

> I listened to the whole 4 hour Lunar Society interview with @ESYudkowsky  
> (hosted by @dwarkesh\_sp) that was mostly about AI alignment and I think I identified a point of confusion/disagreement that is pretty common in the area and is rarely fleshed out:
> 
> Dwarkesh repeatedly referred to the conclusion that AI is likely to kill humanity as “wild.”
> 
> Wild seems to me to pack two concepts together, ‘bad’ and ‘complex.’ And when I say complex, I mean in the sense of the Fermi equation where you have an end point (dead humanity) that relies on a series of links in a chain and if you break any of those links, the end state doesn’t occur.
> 
> It seems to me that Eliezer believes this end state is not wild (at least not in the complex sense), but very simple. He thinks many (most) paths converge to this end state.
> 
> That leads to a misunderstanding of sorts. Dwarkesh pushes Eliezer to give some predictions based on the line of reasoning that he uses to predict that end point, but since the end point is very simple and is a convergence, Eliezer correctly says that being able to reason to that end point does not give any predictive power about the particular path that will be taken in this universe to reach that end point.
> 
> Dwarkesh is thinking about the end of humanity as a causal chain with many links and if any of them are broken it means humans will continue on, while Eliezer thinks of the continuity of humanity (in the face of AGI) as a causal chain with many links and if any of them are broken it means humanity ends. Or perhaps more discretely, Eliezer thinks there are a few very hard things which humanity could do to continue in the face of AI, and absent one of those occurring, the end is a matter of when, not if, and the when is much closer than most other people think.
> 
> Anyway, I think each of Dwarkesh and Eliezer believe the other one falls on the side of extraordinary claims require extraordinary evidence – Dwarkesh thinking the end of humanity is “wild” and Eliezer believing humanity’s viability in the face of AGI is “wild” (though not in the negative sense).

I don’t consider “AGI ruin is disjunctive” a knock-down argument for high p(doom) on its own. NASA has a high success rate for rocket launches even though success requires many things to go right simultaneously. Humanity is capable of achieving conjunctive outcomes, to some degree; but I think this framing makes it clearer why it’s _possible_ to rationally arrive at a high p(doom), at all, when enough evidence points in that direction.[^note-11]

[^note-1]: Eliezer Yudkowsky’s [So Far: Unfriendly AI Edition](https://www.econlib.org/archives/2016/03/so_far_unfriend.html) and Nate Soares’ [Ensuring Smarter-Than-Human Intelligence Has a Positive Outcome](https://intelligence.org/ensuring) are two other good (though old) introductions to what I’d consider “the basics”. To state the obvious: this post consists of various claims that increase my probability on AI causing an existential catastrophe, but not all the claims have to be true in order for AI to have a high probability of causing such a catastrophe. Also, I wrote this post to summarize my own top reasons for being worried, not to try to make a maximally compelling or digestible case for others. I don’t expect others to be similarly confident based on such a quick overview, unless perhaps you’ve read other sources on AI risk in the past. (Including more optimistic ones, since it’s harder to be confident when you’ve only heard from one side of a disagreement. I’ve [written in the past](https://www.lesswrong.com/posts/vT4tsttHgYJBoKi4n/some-abstract-non-technical-reasons-to-be-non-maximally) about some of the things that give _me_ small glimmers of hope, but people who are overall far more hopeful will have very different reasons for hope, based on very different heuristics and background models.)
[^note-2]: E.g., the physical world is too complex to simulate in full detail, unlike a Go board state. An effective general intelligence needs to be able to model the world at many different levels of granularity, and strategically choose which levels are relevant to think about, as well as which specific pieces/aspects/properties of the world _at_ those levels are relevant to think about. More generally, being a general intelligence requires an enormous amount of laserlike focus and strategicness when it comes to which thoughts you do or don’t think. A large portion of your compute needs to be relentlessly funneled into _exactly_ the tiny subset of questions about the physical world that bear on the question you’re trying to answer or the problem you’re trying to solve. If you fail to be relentlessly targeted and efficient in “aiming” your cognition at the most useful-to-you things, you can easily spend a lifetime getting sidetracked by minutiae, directing your attention at the wrong considerations, etc. And given the variety of _kinds_ of problems you need to solve in order to navigate the physical world well, do science, etc., the _heuristics you use to funnel your compute to the exact right things_ need to themselves be very general, rather than all being case-specific. (Whereas we can more readily imagine that many of the heuristics AlphaGo uses to avoid thinking about the wrong aspects of the game state (or getting otherwise sidetracked) _are Go-specific heuristics_.)
[^note-3]: Of course, if your brain has all the basic mental machinery required to do other sciences, that doesn’t mean that you have the _knowledge_ required to actually do well in those sciences. An STEM-level artificial general intelligence could lack physics ability for the same reason many smart humans can’t solve physics problems.
[^note-4]: E.g., because different sciences can synergize, and because you can invent new scientific fields and subfields, and more generally chain one novel insight into dozens of other new insights that critically depended on the first insight.
[^note-5]: More generally, the sciences (and many other aspects of human life, like written language) are a very recent development on evolutionary timescales. So evolution has had very little time to refine and improve on our reasoning ability in many of the ways that matter.
[^note-6]: “Human engineers have an enormous variety of tools available that evolution lacked” is often noted as a reason to think that we may be able to align AGI to our goals, even though evolution failed to align humans to its “goal”. It’s additionally a reason to expect AGI to have greater cognitive ability, if engineers try to achieve great cognitive ability.
[^note-7]: And my understanding is that, e.g., Paul Christiano’s soft-takeoff scenarios don’t involve there being much time between par-human scientific ability and superintelligence. Rather, he’s betting that we have a bunch of decades between GPT-4 and par-human STEM AGI.
[^note-8]: I’ll classify thoughts and text outputs as “actions” too, not just physical movements.
[^note-9]: Obviously, _neither_ is a particularly good approximation for ML systems. The point is that our optimism about plans in real life generally comes from the fact that they’re weak, and/or it comes from the fact that the plan generators are human brains with the full suite of human psychological universals. ML systems don’t possess those human universals, and won’t stay weak indefinitely.
[^note-10]: Quoting [Four mindset disagreements behind existential risk disagreements in ML](https://www.lesswrong.com/posts/84BJopKvQ8qYGHY6b/four-mindset-disagreements-behind-existential-risk): > -   People are taking the risks unseriously because they feel weird and abstract. > -   When they do think about the risks, they anchor to what’s familiar and known, dismissing other considerations because they feel “unconservative” from a forecasting perspective. > -   Meanwhile, social mimesis and the bystander effect make the field sluggish at pivoting in response to new arguments and smoke under the door. Quoting [The inordinately slow spread of good AGI conversations in ML](https://www.lesswrong.com/posts/Rkxj7TFxhbm59AKJh/the-inordinately-slow-spread-of-good-agi-conversations-in-ml): > Info about AGI propagates too slowly through the field, because when one ML person updates, they usually don’t loudly share their update with all their peers. This is because: >  > 1\. AGI sounds weird, and they don’t want to sound like a weird outsider. >  > 2\. Their _peers_ and the _community as a whole_ might perceive this information as an attack on the field, an attempt to lower its status, etc. >  > 3\. Tech forecasting, differential technological development, long-term steering, [exploratory](https://en.wikipedia.org/wiki/Exploratory_engineering) [engineering](https://intelligence.org/files/ExploratoryEngineeringAI.pdf), ‘not doing certain research because of its long-term social impact’, prosocial research closure, etc. are very novel and foreign to most scientists. >  > EAs exert effort to try to dig up precedents like [Asilomar](https://intelligence.org/files/TheAsilomarConference.pdf) partly _because_ Asilomar is so unusual compared to the norms and practices of the vast majority of science. Scientists generally don’t think in these terms at all, especially in _advance_ of any major disasters their field causes. >  > And the scientists who do find any of this intuitive often feel vaguely nervous, alone, and adrift when they talk about it. On a gut level, they see that they have no institutional home and no super-widely-shared ‘this is a virtuous and respectable way to do science’ narrative. >  > Normal [science](https://www.lesswrong.com/s/fxynfGCSHpY4FmBZy) is not Bayesian, is not agentic, is not ‘a place where you’re supposed to do arbitrary things just because you heard an argument that makes sense’. Normal science is a specific collection of scripts, customs, and established protocols. >  > In trying to move the field toward ‘doing the thing that just makes sense’, even though it’s about a weird topic (AGI), and even though the prescribed response is also weird (closure, differential tech development, etc.), and even though the arguments in support are weird (where’s the experimental data??), we’re inherently fighting our way upstream, against the current. >  > Success is possible, but way, way more [dakka](https://thezvi.wordpress.com/2017/12/02/more-dakka/) is needed, and IMO it’s easy to understand why we haven’t succeeded more. >  > This is also part of why I’ve increasingly updated toward a strategy of “let’s all be way too blunt and candid about our AGI-related thoughts”. >  > The core problem we face isn’t ‘people informedly disagree’, ‘there’s a values conflict’, ‘we haven’t written up the arguments’, ‘nobody has seen the arguments’, or even ‘self-deception’ or ‘self-serving bias’. >  > The core problem we face is ‘not enough information is transmitting fast enough, because people feel nervous about whether their private thoughts are in the Overton window’. On the more basic level, [_Inadequate Equilibria_](https://equilibriabook.com/toc) paints a picture of the world’s baseline civilizational competence that I think makes it less mysterious why we could screw up this badly on a novel problem that our scientific and political institutions weren’t designed to address. _Inadequate Equilibria_ also talks about the nuts and bolts of Modest Epistemology, which I think is a key part of the failure story.
[^note-11]: Quoting a recent conversation between Aryeh Englander and Eliezer Yudkowsky: > **Aryeh:** \[…\] Yet I still have a very hard time understanding the arguments that would lead to such a high-confidence prediction. Like, I think I understand the main arguments for AI existential risk, but I just don’t understand why some people seem so _sure_ of the risks. \[…\] >  > **Eliezer:** I think the core thing is the sense that you cannot in this case milk uncertainty for a chance of good outcomes; to get to a good outcome you’d have to actually know where you’re steering, like trying to buy a winning lottery ticket or launching a Moon rocket. Once you realize that uncertainty doesn’t move estimates back toward “50-50, either we live happily ever after or not”, you realize that “people in the EA forums cannot tell whether Eliezer or Paul is right” is not a factor that moves us toward 1:1 good:bad but rather another sign of doom; surviving worlds don’t look confused like that and are able to make faster progress. >  > Not as a fully valid argument from which one cannot update further, but as an intuition pump: the more all arguments about the future seem fallible, the more you should expect the future Solar System to have a randomized configuration from your own perspective. Almost zero of those have humans in them. It takes confidence about some argument constraining the future to get to more than that. >  > **Aryeh:** when you talk about uncertainty here do you mean uncertain factors _within_ your basic world model, or are you also counting model uncertainty? I can see how within your world model extra sources of uncertainty don’t point to lower risk estimates. But my general question I think is more about model uncertainty: how sure can you really be that your world model and reference classes and framework for thinking about this is the right one vs e.g., Robin or Paul or Rohin or lots of others? And in terms of model uncertainty it looks like most of these other approaches imply much lower risk estimates, so adding in that kind of model uncertainty should presumably (I think) point to overall lower risk estimates. >  > **Eliezer:** Aryeh, if you’ve got a specific theory that says your rocket design is going to explode, and then you’re also very unsure of how rockets work really, what probability should you assess of your rocket landing safely on target? >  > **Aryeh:** how about if you have a specific theory that says you should be comparing what you’re doing to a rocket aiming for the moon but it’ll explode, and then a bunch of other theories saying it won’t explode, plus a bunch of theories saying you shouldn’t be comparing what you’re doing to a rocket in the first place? My understanding of many alignment proposals is that they think we do understand “rockets” sufficiently so that we can aim them, but they disagree on various specifics that lead you to have such high confidence in an explosion. And then there are others like Robin Hanson who use mostly outside-type arguments to argue that you’re framing the issues incorrectly, and we shouldn’t be comparing this to “rockets” at all because that’s the wrong reference class to use. So yes, accounting for some types of model uncertainty won’t reduce our risk assessments and may even raise them further, but other types of model uncertainty – including many of the actual alternative models / framings at least as I understand them – should presumably decrease our risk assessment. >  > **Eliezer:** What if people are trying to build a flying machine for the first time, and there’s a whole host of them with wildly different theories about why it ought to fly easily, and you think there’s basic obstacles to stable flight that they’re not getting? Could you force the machine to fly despite all obstacles by recruiting more and more optimists to have different theories, each of whom would have some chance of being right? >  > **Aryeh:** right, my point is that in order to have near certainty of not flying you need to be very very sure that your model is right and theirs isn’t. Or in other words, you need to have very low model uncertainty. But once you add in model uncertainty where you consider that maybe those other optimists’ models could be right, then your risk estimates will go down. Of course you can’t arbitrarily add in random optimistic models from random people – it needs to be weighted in some way. My confusion here is that you seem to be very, very certain that your model is the right one, complete with all its pieces and sub-arguments and the particular reference classes you use, and I just don’t quite understand why. >  > **Eliezer:** There’s a big difference between “sure your model is the right one” and the whole thing with people wandering over with their own models and somebody else going, “I can’t tell the difference between you and them, how can you possibly be so sure they’re not right?” >  > The intuition I’m trying to gesture at here is that you can’t milk success out of uncertainty, even by having a bunch of other people wander over with optimistic models. It _shouldn’t_ be able to work in real life. If your epistemology says that you can generate free success probability that way, you must be doing something wrong. >  > Or maybe another way to put it: When you run into a very difficult problem that you can see is very difficult, but inevitably a bunch of people with less clear sight wander over and are optimistic about it because they don’t see the problems, for you to update on the optimists would be to update on something that happens inevitably. So to adopt this policy is just to make it impossible for yourself to ever perceive when things have gotten really bad. >  > **Aryeh:** not sure I fully understand what you’re saying. It looks to me like to some degree what you’re saying boils down to your views on modest epistemology – i.e., basically just go with your own views and don’t defer to anybody else. It sounds like you’re saying not only don’t defer, but don’t even really incorporate any significant model uncertainty based on other people’s views. Am I understanding this at all correctly or am I totally off here? >  > **Eliezer:** My epistemology is such that it’s possible in principle for me to notice that I’m doomed, in worlds which look very doomed, despite the fact that all such possible worlds no matter how doomed they actually are, always contain a chorus of people claiming we’re not doomed. (See [_Inadequate Equilibria_](https://equilibriabook.com/toc) for a detailed discussion of Modest Epistemology, deference, and “ [outside views](https://www.lesswrong.com/posts/BcYfsi7vmhDvzQGiF/taboo-outside-view) “, and [Strong Evidence Is Common](https://www.lesswrong.com/posts/JD7fwtRQ27yc8NoqS/strong-evidence-is-common) for the basic first-order case that people can often reach confident conclusions about things.)
