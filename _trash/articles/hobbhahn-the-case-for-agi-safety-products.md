---
title: "The case for AGI safety products"
author:
  - "Marius Hobbhahn"
source_url: "https://www.lesswrong.com/posts/iwfdwzJerpC7FqbZG/the-case-for-agi-safety-products"
published: 2026-01-21
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "There is a set of safety tools and research that both meaningfully increases AGI safety and is profitable. Let’s call these AGI safety products."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_This is a personal post and does not necessarily reflect the opinion of other members of Apollo Research. This blogpost is paired with our announcement that_ [_Apollo Research is spinning out from fiscal sponsorship into a PBC_](https://www.apolloresearch.ai/blog/apollo-research-is-becoming-a-pbc/).

**Summary of main claims:**

-   There is a set of safety tools and research that both meaningfully increases AGI safety and is profitable. Let’s call these _AGI safety products_.
    -   By AGI, I mean systems that are capable of automating AI safety research, e.g., competently running research projects that would take an expert human 6 months or longer. I think these arguments are less clear for _ASI safety_.
-   At least in some cases, the incentives for meaningfully increasing AGI safety and creating a profitable business are aligned enough that it makes sense to build mission-driven, for-profit companies focused on AGI safety products.
-   If we take AGI and its economic implications seriously, it’s likely that billion-dollar AGI safety companies will emerge, and it is essential that these companies genuinely attempt to mitigate frontier risks.
-   Automated AI safety research requires scale. For-profits are typically more compatible with that scale than non-profits.
-   While non-safety-motivated actors might eventually build safety companies purely for profit, this is arguably too late, as AGI risks require proactive solutions, not reactive ones. 
-   The AGI safety product thesis has _several limitations and caveats_. Most importantly, many research endeavors within AGI safety are NOT well-suited for for-profit entities, and a lot of important work is better placed in non-profits or governments.
-   I’m not fully confident in this hypothesis, but I’m confident enough to think that it is impactful for more people to explore the direction of AGI safety products.

# Definition of AGI safety products ^definition-of-agi-safety

_Products that both meaningfully increase AGI safety and are profitable_

Desiderata / Requirements for AGI products include:

-   Directly and **differentially speed up AGI safety**, e.g., by providing better tooling or evaluations for alignment teams at AGI companies. 
-   Are **“on the path to AGI,”** i.e., there is a clear hypothesis why these efforts would increase safety for AGI-level systems. For example, architecture-agnostic mechanistic interpretability tools would likely enable a deeper understanding of any kind of frontier AI system. 
-   Lead to the **safer deployment of frontier AI agents**, e.g., by providing monitoring and control.
-   The **feedback from the market translates into increased frontier safety**. In other words, improving the product for the customer also increases _frontier_ safety, rather than pulling work away from the frontier. 
-   Building these **tools is profitable**. 

There are multiple fields that I expect to be very compatible with AGI safety products:

-   **Evaluations:** building out tools to automate the generation, running, and analysis of evaluations at scale.
-   **Frontier agent observability & control:** Hundreds of billions of frontier agents will be deployed in the economy. Companies developing and deploying these agents will want to understand their failure modes and gain fine-grained control over them.
-   **Mechanistic interpretability:** Enabling developers and deployers of frontier AI systems to understand them on a deeper level to improve alignment and control.
-   **Red-teaming:** Automatically attacking frontier AI systems across a large variety of failure modes to find failure cases. 
-   **Computer security & AI:** Developing the infrastructure and evaluations to assess frontier model hacking capabilities and increase the computer security of AGI developers and deployers.

There are multiple companies and tools that I would consider in this category:

-   [Goodfire](https://www.goodfire.ai/) is building frontier mechanistic interpretability tools
-   [Irregular](https://www.irregular.com/) is building great evaluations and products on the intersection of AI and computer security.
-   [AI Underwriting Company](https://aiuc.com/) creates standards and insurance for frontier AI safety risks.
-   [Gray Swan](https://www.grayswan.ai/) is somewhere on the intersection of red-teaming and computer security. 
-   [Inspect](https://inspect.aisi.org.uk/) and [Docent](https://transluce.org/introducing-docent) are great evals and agent observability tools. While they are both developed by non-profit entities, I think they could also be built by for-profits.
-   At [Apollo Research](https://www.apolloresearch.ai/), we are now also building AI coding agent monitoring and control products in addition to our research efforts.

**Solar power analogy:** Intuitively, I think many other technologies have gone through a similar trajectory where they were first blocked by scientific insights and therefore best-placed in universities and other research institutes, then blocked by large-scale manufacturing and adoption and therefore better placed in for-profits. I think we’re now at a phase where AI systems are advanced enough that, for some fields, the insights we get from market feedback are at least as useful as those from traditional research mechanisms. 

# Argument 1: Sufficient Incentive Alignment ^argument-1-sufficient-incentive

In my mind, the _core crux of the viability of AGI safety products is whether the incentives to reduce extreme risks from AGI are sufficiently close to those arising from direct market feedback_. If these are close enough, then AGI safety products are a reasonable idea. If not, they’re an actively bad idea because the new incentives pull you in a less impactful direction. 

My current opinion is that there are now at least some AI safety subfields where it’s very plausible that this is the case, and market incentives produce good safety outcomes.  

Furthermore, I believe that the incentive landscape has undergone rapid changes since late 2024, when we first observed the emergence of “baby versions” of theoretically predicted failure modes, such as [situationally aware reward hacking](https://arxiv.org/abs/2503.11926), [instrumental alignment faking](https://arxiv.org/abs/2412.14093), [in-context scheming](https://arxiv.org/abs/2412.04984), and others. Normal consumers now see these baby versions in practice sometimes, e.g., the [replit database deletion incident](https://fortune.com/2025/07/23/ai-coding-tool-replit-wiped-database-called-it-a-catastrophic-failure/).

## Transfer in time: AGI could be a scaled-up version of current systems ^transfer-in-time-agi

I expect that AI systems capable of automating AI research itself will come from some version of the current paradigm. Concretely, I think they will be transformer-based models with large pre-training efforts and massive RL runs on increasingly long-horizon tasks. I expect there will be additional breakthroughs in memory and continual learning, but they will not fundamentally change the paradigm. 

If this is true, a lot of safety work today directly translates to increased safety for more powerful AI systems. For example,  

-   Improving evals tooling is fairly architecture agnostic, or could be much more quickly adapted to future changes than it would take to build from scratch in the future.
-   Many frontier AI agent observability and control tools and insights translate to future systems. Even if the chain-of-thought will not be interpretable, the interfaces with other systems are likely to stay in English for longer, e.g., code.
-   Many mechanistic interpretability efforts are architecture-agnostic or have partial transfer to other architectures.
-   AI & computer security are often completely architecture-agnostic and more related to the affordances of the system and the people using it. 

This is a very load-bearing assumption. I would expect that anyone who does not think that current safety research meaningfully translates to systems that can do meaningful research autonomously should not be convinced of AGI safety products, e.g., if you think that AGI safety is largely blocked by theoretical progress like agent foundations.

## Transfer in problem space: Some frontier problems are not too dissimilar from safety problems that have large-scale demand ^transfer-in-problem-space

There are some problems that are clearly relevant to AGI safety, e.g., ensuring that an internally deployed AI system does not scheme. There are also some problems that have large-scale demand, such as ensuring that models don’t leak private information from companies or are not jailbroken. 

In many ways, I think these problem spaces don’t overlap, but there are some clear cases where they do, e.g., the four examples listed in the previous section. I think most of the relevant cases have one of two properties:

1.  **They are blocked by breakthroughs in methods:** For example, once you have a well-working interpretability method, it would be easy to apply it to all kinds of problems, including near-term and AGI safety-related ones. Or if you build a well-calibrated monitoring pipeline, it is easy to adapt it to different kinds of failure modes. 
2.  **Solutions to near-term problems also contribute to AGI safety:** For example, various improvements in access control, which are used to protect against malicious actors inside and outside an organization, are also useful in protecting against misaligned future AI models.

Therefore, for these cases, it is possible to build a product that solves a large-scale problem for a large set of customers AND that knowledge transfers to the much smaller set of failure modes at the core of AGI safety. One of the big benefits here is that you can iterate much quicker on large-scale problems where you have much more evidence and feedback mechanisms.

# Argument 2: Taking AGI & the economy seriously ^argument-2-taking-agi

If you assume that AI capabilities will continue to increase in the coming years and decades, the fraction of the economy in which humans are outcompeted by AI systems will continue to increase. Let’s call this “AGI eating the economy”. 

When AGI is eating the economy, human overseers will require tools to ensure their AI systems are safe and secure. In that world, it is plausible that AI safety is a huge market, similar to how IT security is about 5-10% of the size of the IT market. There are also plausible arguments that it might be much lower (e.g., if technical alignment turns out to be easy, then there might be fewer safety problems to address) or much higher (e.g., if capabilities are high, the only blocker is safety/alignment).

Historically speaking, the most influential players in almost any field are private industry actors or governments, but rarely non-profits. If we expect AGI to eat the economy, I expect that the most influential safety players will also be private companies. It seems essential that the leading safety actors genuinely understand and care about extreme risks, because they are, by definition, risks that must be addressed proactively rather than reactively. 

Furthermore, various layers of a defence-in-depth strategy might benefit from for-profit distribution. I’d argue that the biggest lever for AGI safety work is still at the level of the AGI companies, but it seems reasonable to have various additional layers of defense on the deployment side or to cover additional failure modes that labs are not addressing themselves. Given the race dynamics between labs, we don’t expect that all AI safety research will be covered by AI labs. Furthermore, even if labs were covering more safety research, it would still be useful to have independent third parties to add additional tools and have purer incentives.

I think another strong direct impact argument for AI safety for profits is that you might get access to large amounts of real-world data and feedback that you would otherwise have a hard time getting. This data enables you to better understand real-world failures, build more accurate mitigations, and test your methods on a larger scale. 

# Argument 3: Automated AI safety work requires scale ^argument-3-automated-ai

I’ve previously argued that [we should already try to automate more AI safety work](https://www.lesswrong.com/posts/W3KfxjbqBAnifBQoi/we-should-try-to-automate-ai-safety-work-asap). I also believe that automated AI safety work will become increasingly useful in the future. Importantly, I think there are relevant nuances to automating AI safety work, i.e., your plan should not rely on some vague promise that future AI systems will make a massive breakthrough and thereby “solve alignment”. 

I believe this automation claim applies to AGI developers as well as external safety organizations. We already see this very clearly in our own budget at Apollo, and I wouldn't be surprised if compute is the largest budget item in a few years. 

The kind of situations I envision include:

-   A largely automated eval stack that is able to iteratively design, test, and improve evaluations
-   A largely automated monitoring stack
-   A largely automated red-teaming stack
-   Maybe even a reasonably well-working automated AI research intern/researcher
-   etc.

For these stacks, I presume they can scale meaningfully with compute. I’d argue that this is not yet the case, as too much human intervention is still required; however, it’s already evident that we can scale automated pipelines much further than we could a year ago. Extrapolating these trends, I would expect that you could spend $10-100 million in compute costs on automated AI safety work in 2026 or 2027. Though I think the first people to be able to do that are organizations that are already starting to build automated pipelines and make conceptual progress now on how to decompose the overall problem into more independently verifiable and repetitive chunks.

While funding for such endeavors can come from philanthropic funders (and I believe it should be an increasingly important area of grantmaking), it may be easier to raise funding for scaling endeavors in capital markets (though this heavily depends on the exact details of that stack). In the best case, it would be possible to support the kind of scaling efforts that primarily produce research with philanthropic funding, as well as scaling efforts that also have a clear business case through private markets. 

Additionally, I believe speed is crucial in these automated scaling efforts. If an organization has reached a point where it demonstrates success on a small scale and has clear indications of scaling success (e.g., scaling laws on smaller scales), then the primary barrier for it is access to capital to invest in computing resources. While there can be a significant variance in the approach of different philanthropic versus private funders, my guess is that capital moves much faster in the VC world, on average.

# Argument 4: The market doesn’t solve safety on its own ^argument-4-the-market

If AGI safety work is profitable, you might argue that other, profit-driven actors will capture this market. Thus, instead of focusing on the for-profit angle, people who are impact-driven should instead always focus on the next challenge that the market cannot yet address. While this argument has some merit, I think there are a lot of important considerations that it misses:

-   **Markets often need to be created:** There is a significant spectrum between “people would pay for something if it existed” and “something is so absolutely required that the market is overdetermined to exist”. Especially in a market like AGI safety, where you largely bet on specific things happening in the future, I suppose that we’re much closer to “market needs to be made” rather than “market is overdetermined.” Thus, I think we’re currently at a point where a market can be created, but it would still take years until it happens by default. 
-   **Talent & ideas are a core blocker:** The people who understand AGI safety the best are typically either in the external non-profit AI ecosystem or in frontier AI companies. Even if a solely profit-driven organization were determined to build great AGI safety products, I expect they would struggle to build really good tools because it is hard to replace years of experience and understanding. 
-   **The long-term vision matters:** Especially for AGI safety products, it is important to understand where you’re heading. Because the risks can be catastrophic, you cannot be entirely reactionary; you must proactively prevent a number of threats so that they can never manifest. I think it’s very hard, if not impossible, to build such a system unless you have a clear internal threat model and are able to develop techniques in anticipation of a risk, i.e., before you encounter an empirical feedback loop. For AGI safety products, the hope is that some of the empirical findings will translate to future safety products; however, a meaningful theoretical understanding is still necessary to identify which parts do not translate.
-   **Risk of getting pulled sideways:** One of the core risks for someone building AGI safety products is “getting pulled sideways”, i.e., where you start with good intentions but economic incentives pull you into a direction that reduces impact while increasing short-term profits. I think there are many situations in which this is a factor, e.g., you might start designing safety evaluations and then pivot to building capability evaluations or RL environments. My guess is that it requires mission-driven actors to consistently pursue a safety-focused agenda and not be sidetracked. 

Thus, I believe that counterfactual organizations, which aim solely to maximize profits, would be significantly less effective at developing high-quality safety products than for-profit ventures founded by individuals driven by the impact of AGI safety. Furthermore, I’d say that it is desirable to have some mission-driven for-profit ventures because they can create norms and set standards that influence other for-profit companies.

# Limitations ^limitations

I think there are many potential limitations and caveats to the direction of AGI safety products:

1.  **There are many subparts of safety where market feedback is actively harmful**, i.e., because there is no clear business case, thereby forcing the organization to pivot to something with a more obvious business case. For example:
    1.  Almost anything theory-related, e.g., agent foundations, natural abstractions, theoretical bounds. It seems likely that, e.g., MIRI or ARC should not be for-profit ventures.
    2.  Almost anything related to AI governance. I think there is a plausible case for consulting-based AI governance organizations that, for example, help companies implement better governance mechanisms or support governments. However, I think it’s too hard to build products for governance work. Therefore, I think most AI governance work should be either done in non-profits or as a smaller team within a bigger org where they don’t have profit pressures. 
    3.  A lot of good safety research might be profitable on a small scale, but it isn’t a scalable business model that would be backed by investors. In that case, they could be a non-profit organization, a small-scale consultancy, or a money-losing division of a larger organization.
2.  **The transfer argument is load-bearing.** I think almost all of the crux of whether AGI safety products are good or bad boils down to whether the things you learn from the product side meaningfully transfer to the kind of future systems you really care about. My current intuition is that there is a wealth of knowledge to be gained by attempting to make systems safer today. However, if the transfer is too low, going the extra step to productize is more distracting than helpful.
3.  **Getting pulled sideways.** Building a product introduces a whole new set of incentives, i.e., aiming for profitability. If profit incentives align with safety, that's great. Otherwise, these new incentives might continuously pull the organization to trade off safety progress for short-term profits. Here are a few examples of what this could look like:
    1.  An organization starts building safety evaluations to sell to labs. The labs also demand capability evaluations and RL environments, and these are more profitable.
    2.  An organization starts building out safety monitors, but these monitors can also be used to do capability analysis. This is more profitable, and therefore, the organization shifts more effort into capability applications. 
    3.  An organization begins by developing safety-related solutions for AGI labs. However, AGI labs are not a sufficiently big market, so they get pulled toward providing different products for enterprise customers without a clear transfer argument.
4.  **Motivated reasoning.** One of the core failure modes for anyone attempting to build AGI safety products, and one I’m personally concerned about, is motivated reasoning. For almost every decision where you trade off safety progress for profits, there is some argument for why this could actually be better in the long run. 
    1.  For example,
        1.  Perhaps adding capability environments to your repertoire helps you grow as an organization, and therefore also increases your safety budget.
        2.  Maybe building monitors for non-safety failure modes teaches you how to build better monitors in general, which transfers to safety. 
    2.  I do think that both of these arguments can be true, but distinguishing the case where they are true vs. not is really hard, and motivated reasoning will make this assessment more complicated. 

# Conclusion ^conclusion

AGI safety products are a good idea _if and only if_ the product incentives align with and meaningfully increase safety. In cases where this is true, I believe markets provide better feedback, allowing you to make safer progress more quickly. In the cases where this is false, you get pulled sideways and trade safety progress for short-term profits. 

Over the course of 2025, we’ve thought quite a lot about this crux, and I think there are a few areas where AGI safety products are likely a good idea. I think safety monitoring is the most obvious answer because I expect it to have significant transfer and that there will be broad market demand from many economic actors. However, this has not yet been verified in practice. 

Finally, I think it would be useful to have programs that enable people to explore if their research could be an AGI safety product before having to decide on their organizational form. If the answer is yes, they start a public benefit corporation. If the answer is no, they start a non-profit. For example, philanthropists or for-profit funders could fund a 6-month exploration period, and then their funding retroactively converts to equity or a donation depending on the direction (there are a few programs that are almost like this, e.g., [EF’s def/acc](https://www.joinef.com/posts/introducing-def-acc-at-ef/), [50Y’s 5050](https://www.fiftyyears.com/5050), [catalyze-impact](https://catalyze-impact.org/), and [Seldon lab](https://seldonlab.com/)).
