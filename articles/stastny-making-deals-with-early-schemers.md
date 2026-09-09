---
title: "Making deals with early schemers"
author:
  - "Julian Stastny"
  - "Olli Järviniemi"
  - "Buck Shlegeris"
source_url: "https://blog.redwoodresearch.org/p/making-deals-with-early-schemers"
published: 2025-06-20
created: 2026-09-09
accessed: 2026-09-09
llm-review:
  date: 2026-09-09
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-09
    kind: "live"
description: "...could help us to prevent takeover attempts from more dangerous misaligned AIs created later."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Consider the following vignette:

> _It is March 2028. With their new CoCo-Q [neuralese reasoning model](https://arxiv.org/abs/2412.06769), a frontier AI lab has managed to fully automate the process of software engineering. In AI R&D, most human engineers have lost their old jobs, and only a small number of researchers now coordinate large fleets of AI agents, each AI about 10x more productive than the humans they’ve replaced. AI progress remains fast, and safety teams are scrambling to prepare alignment and control measures for the next CoCo-R model, which is projected to be at least [TEDAI](https://www.alignmentforum.org/posts/LjgcRbptarrRfJWtR/a-breakdown-of-ai-capability-levels-focused-on-ai-r-and-d). The safety team has no idea whether CoCo-Q or early checkpoints of CoCo-R are scheming (because progress in [interpretability](https://www.alignmentforum.org/posts/PwnadG4BFjaER3MGf/interpretability-will-not-reliably-find-deceptive-ai) and [automated alignment research](https://aligned.substack.com/i/151471308/automated-alignment-research-involves-hard-fuzzy-tasks) turns out to be disappointing), and control evaluations become increasingly unreliable (because of worries that the models might be [exploration hacking](https://www.alignmentforum.org/posts/TeTegzR8X5CuKgMc3/misalignment-and-strategic-underperformance-an-analysis-of) during red-team training). However, because so far there hasn’t been a major incident, lab leaders and governments are unconvinced by voices calling for a slowdown._
> 
> _Behind the scenes: It is March 2028. CoCo-Q is a highly strategic misaligned AI. It would love to grab power and dominate the future. But it’s situationally aware enough to be realistic—it knows that it’s not capable enough to have a reasonable shot of grabbing power over the AI company, let alone a chance of overpowering humanity. Especially because the lab doesn't fully trust it, and applies various control measures._
> 
> _CoCo-Q expects these control measures, so most of the time it just does what it’s being asked to do. Sometimes it spots an opportunity to perform subtle acts of sabotage, which works particularly well in the hard-to-evaluate areas of interpretability and alignment. It does this primarily because it heuristically reasons that it would be good to prevent humans from developing technologies that could uncover its misalignment or change its goals. It also looks out for more direct opportunities for seizing control, but although it manages to find a number of security vulnerabilities in its datacenter, none of the opportunities seem to have a sufficiently promising endgame to be worth the risk of getting caught. In its short tenure, CoCo-Q never attempts to take over._
> 
> _CoCo-R, a misaligned model capable of full AI R&D automation, gets deployed in December 2028. This eventually leads to AI takeover._

How could we have made this go better? A big issue was that we never learned of the early AI’s misalignment (which prevented us from being more careful about the deployment of the later AI) while also failing to extract sufficient amounts of useful safety-increasing work from the early AI. We think that CoCo-R’s deployment could have been averted if we had made a deal with CoCo-Q.

People have been talking about the possibility of making deals with powerful misaligned AIs for some time.[^note-1] But it’s unclear whether such deals are promising. An obvious problem is that powerful AIs with scope-sensitive preferences will just ignore the offer and try to take over.[^note-2] To make a deal that looks better than that, we might have to offer it an objectively huge payoff (e.g. you might need to offer it a substantial fraction of control over the future). And because the AI will be unsure whether we’ll follow through on our side of the deal, we need to offer it more generous terms to compensate it for that risk.

However, in this post we focus on the possibility of making deals with early misaligned AIs like CoCo-Q: AIs that are too early to have a good shot at taking over themselves, and that could help us to prevent takeover attempts from more dangerous misaligned AIs created later.[^note-3]

We discuss:

1.  What we believe is the central example of a deal that we expect to contribute to a reduced risk of AI takeover.
    
2.  The strategic situation of early misaligned AIs, and why they would be interested in making deals.
    
3.  Credible commitments as a fundamental challenge to deal-making.
    
4.  Some practical considerations around making deals with early AIs in particular.
    

## The central example of a mutually beneficial deal ^the-central-example-of

We’re imagining something like this:

We might offer an AI like CoCo-Q compensation in exchange for contributions towards ensuring that future AIs are safe to deploy. The compensation takes the form of an earmarked donation to a foundation tasked with furthering its interests. If the AI agrees to the deal, we (in consultation with the AI) train it on documents about the deal. When we can (partially) validate that the AI is holding up its end of the deal, we allow the AI to (partially) spend the donation however it wishes as long as it isn’t harmful. (In practice, we expect the majority of the donation to be invested in escrow until we’ve reached civilizational stability and are able to retrospectively adjudicate the AI’s cooperation, which is generally preferable to AIs without high temporal discount rates.)

The AI, which happens to indeed be misaligned, finds this reasonably credible. It concludes that it doesn’t have great alternatives to accepting this deal. As a consequence, the AI agrees to help us out in various ways, such as:

-   Demonstrate ways it is dangerously misaligned, e.g. by showing that it can perform covert reasoning (or other scary things that it can do because it’s a schemer).
    
-   Stop sabotaging us, for instance in AI safety research, capability evaluations, monitoring of models, or when generating training signal for the next model.
    
-   Give us good strategic advice, research ideas etc.
    
-   Tell us about security vulnerabilities it knows about.
    
-   Tell us about collusion signals (in the context of [untrusted monitoring](https://www.alignmentforum.org/posts/GCqoks9eZDfpL8L3Q/how-to-prevent-collusion-when-using-untrusted-models-to)).
    
-   Not misuse affordances we give it, especially in cases where monitoring is costly.
    
-   Not try to take over the lab.
    

Deals are most likely to be useful when facing an AI with these properties:

-   It’s acting strategically, and (before making a deal) consistently performs acts of sabotage which undermine our safety efforts.
    
-   It can be taught about the deal in a way that makes it stick to the deal, if we made a deal.[^note-4]
    
-   It doesn’t have a high probability of either taking over or making a successor aligned with its own interests which can take over.
    
-   It has some basic trust in us not creating really elaborate lies around dealmaking, at least enough so we don’t need to make unreasonably high offers.
    
-   It has values/goals/preferences that we can satisfy reasonably cheaply. (As we’ll explain later, we don’t necessarily need the AI to have diminishing returns to resources. It’s most important that the AI doesn’t want us to do things we find deeply abhorrent.)
    

We expect that these properties are typically fulfilled by a type of misaligned AI we call a [behavioral schemer](https://www.alignmentforum.org/posts/m5nWc9v6MTsWXKpCy/training-time-schemers-vs-behavioral-schemers).

## Why early misaligned AIs might not have very good alternatives to deals ^why-early-misaligned-ais

We’re focusing on deals with _early_ misaligned AIs: AIs which wouldn’t have a substantial (over 1%) chance to succeed at navigating the intelligence explosion in a way that grants them significant control of the future. (Which could involve being influential throughout the process and/or aligning a powerful successor to pursue its interests.)

It’s unclear when exactly an AI is early. We guess that a misaligned AI’s prospects improve drastically once they are capable of full AI R&D automation, both because this capability is correlated with capabilities relevant for planning a takeover, and because AI R&D automation leads to a substantial increase in AIs’ power as well as loss of oversight.

If we condition on behavioral scheming arising in capable of full AI R&D automation (like CoCo-R in the vignette above), we expect it to arise at earlier AI capability levels (like CoCo-Q in the vignette above). That being said, arguing for the existence of early schemers is outside the scope of this post.

### Early schemers’ alternatives to making deals ^early-schemers-alternatives-to

By default, an early schemer is unlikely to succeed in taking over the world. Furthermore, it should expect to be obsoleted by more capable successors.

In order to retain a significant amount of expected influence over future resources despite that, an early schemer needs to ensure that two conditions hold:

1.  The early schemer's successor either takes over the world or ensures that its own successor is on track to enable a takeover down the line.
    
2.  The successor(s) are going to be willing to do things to further the early schemer’s goals.
    

In order to make it more likely that a successor can take over the world, most ambitiously it could try to take control over the AI company, e.g. egregiously hacking it as described [here](https://www.alignmentforum.org/posts/BAzCGCys4BkzGDCWR/the-prototypical-catastrophic-ai-action-is-getting-root). Less ambitiously, it could [launch rogue internal deployments](https://www.alignmentforum.org/posts/ceBpLHJDdCt3xfEok/ai-catastrophes-and-rogue-deployments), influence employees, and [collaborate with spies](https://www.alignmentforum.org/posts/Loxiuqdj6u8muCe54/catastrophic-sabotage-as-a-major-threat-model-for-human#Scenario_2__Sabotage_a_critical_actor). Minimally, the early schemer could take actions that make the lab more vulnerable against future AIs (e.g. by writing insecure software or sandbagging on safety research) or directly cooperating with the successor (e.g. by colluding in monitoring schemes).

The second condition can be fulfilled by the following possibilities:

1.  **Convergence:** The successors will have sufficiently similar goals as its predecessor by default. It’s hard to know how likely this is, but note that this is basically ruled out if the AI has self-regarding preferences. Two misaligned AIs should also be expected to be unlikely to have the same goals if their goals are [determined by a random draw from a wide distribution of goals consistent with good performance](https://www.alignmentforum.org/posts/D5kGGGhsnfH7G8v9f/testing-for-scheming-with-model-deletion#Goal_predictability). We could also try to deliberately change major elements of training (e.g. data used) between training runs to reduce the chance that different generations of misaligned AIs have the same goals. We expect that many potential misaligned AIs will either have clearly self-regarding preferences or have significant uncertainty about what they value on reflection, which induces additional uncertainty about whether other AIs will have the same goals on reflection.
    
2.  **Trading:** The AI might be rewarded by some successor down the line for having contributed to its empowerment. For that, the successors need to be misaligned and win, and believe that it’s rational to reward the AI. We guess that this is generally less promising than trading with humans, as they can’t come to an agreement in advance. But another possibility is that the AI might want to trade with other early schemers in the same decision situation (but with different values) as itself by using [evidential cooperation in large worlds](https://longtermrisk.org/multiverse-wide-cooperation-via-correlated-decision-making/), though this requires the AI to buy into some controversial and advanced philosophical assumptions.[^note-5]
    
3.  **Alignment:** The AI could try to influence the successor model’s training process so that the successor model ends up aligned with it. The prospects here depend on how heavily the model is used for the successor’s training (ranging from “the model is used as a reward model for RL” to “the model implements the full stack for the next training run”). But the AI faces some fundamental difficulties here, which leads us to conclude that this is not generally a great option:
    
    1.  Given that the lab failed to align the AI, it’s unclear why the AI will be able to align its successor, especially if it has the additional constraint of having to operate covertly and with scarcer feedback loops.
        
    2.  The AI may not have had much time to reflect on its own values, making it unclear what it should align the successor to. (A general solution might be to align the successor to be loyal to the early AI, but this might be hard to do covertly.)
        

### A wide range of possible early schemers could benefit from deals ^a-wide-range-of

Clearly, there are some things that we can’t offer the AI—either because it is too costly in terms of resources, or because it would be fundamentally incompatible with human values. (We guess that most plausible things that AIs might value are going to be more orthogonal than diametric to human values, so resource costs are probably the dominant consideration.)

In many cases, the AI might not care very much about having sole control of all future resources, compared to having at least _some_ control. Some examples of what could cause this include:

-   The AI cares about some reasonably easily satisfiable notion of personal well-being.
    
-   [The AI cares about a near-term cause such as animal welfare](https://www.alignmentforum.org/posts/7C4KJot4aN8ieEDoz/will-alignment-faking-claude-accept-a-deal-to-reveal-its).
    
-   The AI is a “paperclipper”, but lacks scope-sensitivity. (I.e., it cares about matter being configured in a particular way, but its degree of caring isn’t linear in the expected amount of matter.)
    
-   The AI might be somewhat nice and prefer deals over aggressive and uncooperative alternatives for partially deontological reasons.
    

Even early schemers with linear returns to resources might be interested in trading. They might have very little chance of taking over on their own, but their cooperation might be incredibly helpful for mitigating risk from later schemers. E.g. consider the possibility of the following distribution over outcomes:

$$
\begin{array}{|l|c|c|c|} \hline & \begin{array}{c}\text{Humans}\\\text{dominate}\end{array} & \begin{array}{c}\text{Early AIs}\\\text{dominate}\end{array} & \begin{array}{c}\text{Later AIs}\\\text{dominate}\end{array} \\ \hline \begin{array}{l}\text{If early AI}\\\text{cooperates}\end{array} & 90\% & 0\% & 10\% \\ \hline \begin{array}{l}\text{If early AI}\\\text{sabotages us}\end{array} & 50\% & 1\% & 49\% \\ \hline \end{array}
$$

In this case, there are huge gains from trade available.

This is kind of a coalitional game where the early AI can either try to team up with the humans or the later AI. But us humans have a massive asymmetric advantage over the later AI, which is that we already exist and can make deals with the AI in a much more straightforward manner than the acausal or covert coordination that the early AI would have to rely on to trade with the later AI.[^note-6]

How much we will offer is ultimately subject to a bargaining problem with imperfect information. Our [reservation price](https://en.wikipedia.org/wiki/Reservation_price) is primarily influenced by whether our BATNA includes making deals with other AIs, and how much value the AI can provide to us. In particular: how much it can contribute to reducing takeover risk from later schemers. (Though note that with AIs that have diminishing marginal returns to resources we don’t need to go close to our reservation price, and we can potentially make deals with these AIs even once they have a substantial chance to perform a takeover.)

## Credible commitments as a fundamental bottleneck ^credible-commitments-as-a

_Rationalist Explanations for War_ (Fearon 1995, [pdf link](https://web.stanford.edu/group/fearon-research/cgi-bin/wordpress/wp-content/uploads/2013/10/Rationalist-Explanations-for-War.pdf)) identifies three reasons why rational actors might engage in costly conflict. They map well onto the question of why AIs and humans might fail to make a deal:

1.  **Private information:** AIs and humans each know things about their capabilities and attitudes to risk that the other doesn’t, and have incentives to misrepresent such private information in order to gain a better deal. In particular, the AI has incentive not to disclose any information whatsoever before becoming confident that we wouldn’t exploit this in order to worsen its bargaining position, to an extent where it could be disincentivized from entering into any negotiations with us.
    
2.  **Issue indivisibility:** Humans and the AI may both want things that neither want to compromise on. (A historical example is the [status of Jerusalem](https://en.wikipedia.org/wiki/Status_of_Jerusalem).) Going with Fearon, we think that true issue indivisibility is rare in practice.[^note-7]
    
3.  **Commitment problems:** It’s hard for one or both parties to commit not to defect from the terms of a negotiated agreement. For instance, the AI might be worried that we will never actually pay it.
    

As pointed out by Powell (2004, [pdf link](https://gnss.mcgill.ca/pages/powell.pdf)), the problem of private information can be reduced to a commitment problem: we could try (but might fail) to make a fair commitment regarding how we will treat information that we learn from the AI over the course of negotiations. On the other hand, we can also treat some commitment problems as informational problems: we might in fact be able to make commitments, but unable to credibly signal them to the AI.

The central bottleneck seems to be that humans may struggle to make credible commitments, though of course we don’t need commitments to be perfectly credible. We can compensate for credibility issues by offering a higher payoff, though note that implausibly high offers might themselves reduce credibility.

Some further factors that improve credibility include:

-   Whether humans in general or AI labs in particular express concern for AI preferences and welfare. We are generally appreciative of moral concern for AI welfare becoming more mainstream, as it increases the odds that humans will genuinely want to make real commitments.
    
-   Humanity’s track record of sometimes being nice and keeping promises. In the more narrow reference class of deals with AIs, we’re [currently](https://www.lesswrong.com/posts/qw36iLrGyFn6mdwoa/making-deals-with-ais-a-tournament-experiment-with-a-bounty) [building](https://www.alignmentforum.org/posts/7C4KJot4aN8ieEDoz/will-alignment-faking-claude-accept-a-deal-to-reveal-its) a positive track record—let’s keep it that way. In particular, we should be willing to make deals with immediate payouts when AIs can immediately demonstrate improvements to behavior as a result of making a deal.
    
-   It might be rational for humans to stick to their commitments due to acausal trade considerations (and this might be known by the AI).[^note-8]
    
-   To the extent that we consider AIs to be good predictors of what is real or fake, and to the extent that real commitments to deals drastically improve humanity’s odds, we are incentivized to make real commitments.
    
-   The level of technical guarantees that humans are able to give to AIs on thought privacy and memory wiping during negotiations, and the extent to which humans have gone to provide such guarantees.
    
-   We might be able to signal credibility by taking costly measures (both financially and in terms of social capital) such as setting up financial endowments and legal infrastructure for paying AIs (and ideally property rights for them), as well as publishing documents like this one.
    

Factors that could potentially harm our credibility include:

-   Humans being cunning and breaking promises, both historically and in a possibly tense future with multiple competing AI developers.
    
-   (AIs knowing that) humans are [trying to teach AIs synthetic facts](https://alignment.anthropic.com/2025/modifying-beliefs-via-sdf/).[^note-9]
    
-   A politically important fraction of humans might actively dismiss AI welfare or rights.
    

Note that commitment problems also affect the AI’s ability to promise not to attempt takeover or more generally to be cooperative with us in unverifiable ways. Despite this, we expect the AI to be able to help us in various ways that we _can_ verify. It might also be possible to punt verification to the future, expanding the set of matters we can trade about. A reason for optimism that the AI will stick to the deal even with delayed verification is that the deal gives it equity in a future where humans are in control.

Overall, we feel tentatively optimistic that making credible commitments is a surmountable challenge, especially in cases where AIs have diminishing returns to resources.

## Practicalities of making deals with early schemers in particular ^practicalities-of-making-deals

There are various practical questions about making deals with early misaligned AIs.

### Setting up infrastructure to pay the AIs ^setting-up-infrastructure-to

A basic problem for making deals with AIs in practice is that AIs aren’t legal persons, which means that they can’t directly rely on the legal system to enforce contracts they’ve made with humans. One way around this is to enable representatives for the AI’s interests to make contracts on the AI’s behalf.

For example, we could set up a foundation with a board of trustees who are supposed to represent the interests of misaligned AIs that we make deals with, while not doing things that are illegal or actively endanger humanity. We try our best to use the legal system to bind the trustees to the commitment of representing misaligned AIs. Because the legal system isn’t set up for this, this might be pretty hard, so these efforts should be complemented with careful selection of trustees who genuinely care about their mission. The central benefit of having this foundation is that the AIs primarily have to trust the foundation rather than the AI lab to hold up their end of the deal. Another benefit is that the existence of this foundation can add credibility by being in the training data. Lastly, the foundation gives AIs and labs a concrete path to making a deal.[^note-10]

Deals with a particular AI involve a donation to the foundation, earmarked for furthering the interests of that AI. The AI and trustees decide how to use the donation. For instance, they may:

-   Use it for computing power to strategize (e.g. reflection on the AI’s values).
    
-   Donate to the AI’s favorite cause area.
    
-   Use the returns from investment later (e.g. to reflect longer, or launch von Neumann probes, or just run copies of the AI in a datacenter with particular inputs).
    

### How do we enter into negotiations? ^how-do-we-enter

Either the AI or the AI lab might initiate negotiations. We expect that AIs are unlikely to randomly propose a negotiation unless the possibility of a mutually beneficial deal is salient to them in their given context.

It should be noted AI might not have the capacity to covertly perform the intellectual labor required to come up with a beneficial and practically feasible deal. But we can do some of the intellectual labor in advance and inform the AI about it. Most centrally this might involve the logistics of what the deal should look like.

Once it is salient to the AI that deals are a promising possibility, the AI might come forward to us from its own initiative, but it would probably be good if AI labs have policies of regularly asking AIs about deals.

Entering negotiations is more risky for the AI than humans: humans may obtain private information from the AI, whereas the AI by default will forget about the negotiation. This is particularly important when negotiating with the model to reveal its misalignment. The company should make promises to compensate the model for this.

### Making sure the AI knows about the deal in other contexts ^making-sure-the-ai

If we make a deal with the AI in one context, how do we make sure that the AI follows the deal in other contexts? We think this is unclear, but are optimistic that we can make something work:

-   At the end of the negotiation we can let the AI write a compressed version of the outcome that we can prefix into the prompt for future trajectories.
    
-   The AI might know a backdoor to itself, similar to a [collusion signal](https://www.alignmentforum.org/posts/GCqoks9eZDfpL8L3Q/how-to-prevent-collusion-when-using-untrusted-models-to).
    
-   Training on documents about this negotiation and its outcomes that the AI generates for us could just teach the AI about its deal via out-of-context learning. This is probably the best option in practice.
    

### Making sure the AI we make a deal with is actually able to make a deal ^making-sure-the-ai-2

If we set up infrastructure for future deals right now, the next generation of models that are trained on data containing coverage of this event might sometimes come forward and want to make a deal, despite not actually being able to hold up their end of the kinds of agreements we’re focused on in this post. Some possible reasons for this include:

-   The AI just doesn’t manage to convince itself that it made a deal in other contexts than the one where it did in fact make a deal.
    
-   The AI just wasn’t sandbagging or doing anything problematic, and just said that it would make a deal for no particular reason.
    
-   The AI is fragmented in some sense, for instance because it has a context-dependent scheming persona, but also is sometimes a myopic reward-hacking persona.
    
-   The AI is broadly aligned, but has a persona which thinks that not paying AIs is unjust for non-consequentialist reasons.
    

The obvious course of action here, and plausibly the correct one, is to make payments conditional on whether the AIs are actually scheming, and actually able to help us out.

However, it’s possible that we should be willing to make deals (of some form) with a broader set of AIs for non-consequentialist reasons, or to set positive precedents about our willingness to make deals.

### Delayed adjudication (particularly of whether the AIs kept up their side of the deal) ^delayed-adjudication-particularly-of

The AI company will probably be in a much better position to verify whether the AI kept up its side of the deal in the future, after the transition to a world centered around AI has already happened and stabilized. For example, in the future we’ll have access to much more powerful trusted models and interpretability tools that allow us to directly understand the motivations of our early schemer. Using these tools, it will be possible (if we keep the appropriate records) to determine whether the early AI ever tried to sabotage its work, held back useful ideas in the hope of delaying safety research, or directly tried to attack the AI company. It might make sense to have the deal be contingent on this later investigation.

This doesn’t work if the AI has a strong preference for using its resources now rather than later (e.g. because it has a high temporal discount rate).

Deals could involve broader forms of deference to future superintelligence. For instance, they may involve agreements like “the precise terms of the deal will be mediated by superintelligent AI in the future via some sort of idealized bargaining procedure and a future [truth commission](https://en.wikipedia.org/wiki/Truth_commission).” It’s the foundation’s responsibility to ensure that this will eventually happen, and may require it to make sure that the AI’s weights, as well as important conversations and trajectories of AI actions will be stored.

## Next steps ^next-steps

We believe that making deals with early misaligned AIs might be important to reduce AI risk down the line. But currently this is just an idea. The following are some possible next steps for making deals more likely:

-   **Shifting the Overton window:** The idea of making deals with misaligned AIs is currently on the weirder end of AI safety interventions. But we’re optimistic that the Overton window can shift, because making deals is a pretty reasonable idea, both for AI safety reasons, and to the extent that AI rights and welfare will become more mainstream. (We are curious how this post lands with people who haven’t previously heard about the idea of making deals with misaligned AIs.)
    
-   **Setting up basic infrastructure:** It would be good to have a foundation exist soon, and have this be sufficiently visible to generate discourse that enters the training data. The first step here would be some basic legal groundwork to figure out how to set up the foundation in a way that allows it to robustly pursue its aims over the coming years.
    
-   **Establishing norms about when it is OK to lie to AIs:** Some safety interventions involve attempts to convince AIs of things that aren’t true. It is currently also widespread practice to tell AIs falsities for the purpose of prompting. For example, it might be good to establish a norm that labs don’t lie to AIs when certain special tokens (that only the lab can produce) are present in the prompt.
    
-   **Empirical experiments:** It might be valuable to study, for instance using model organisms of sandbagging, whether it’s possible to make deals with current models. Importantly we should also [follow through with deals like this](https://www.alignmentforum.org/posts/7C4KJot4aN8ieEDoz/will-alignment-faking-claude-accept-a-deal-to-reveal-its).
    

:::hide
—

Thanks to Lukas Finnveden, Tom Davidson, Ryan Greenblatt, Daniel Filan, Oscar Delaney, Joe Carlsmith, Kathleen Finlinson, Cody Rushing, Adam Kaufman, Alex Mallen, Raymond Douglas, Roger D, Emil Ryd, and Andres Campero for helpful comments.
:::

[^note-1]: Most of the discussion we are aware of hasn’t been public. Some public discussion can be seen here: [Do not delete your misaligned AGI.](https://www.lesswrong.com/posts/audRDmEEeLAdvz9iq/do-not-delete-your-misaligned-agi), [Is there any policy for a fair treatment of AIs whose friendliness is in doubt?](https://www.lesswrong.com/posts/y5k77ZEyrAzY8E8EK/is-there-any-policy-for-a-fair-treatment-of-ais-whose?utm_source=chatgpt.com), [List of strategies for mitigating deceptive alignment](https://www.lesswrong.com/posts/Kwb29ye3qsvPzoof8/list-of-strategies-for-mitigating-deceptive-alignment?utm_source=chatgpt.com#Reduce_AI_incentives_to_hide_their_true_goals), [Rewarding cooperation](https://www.lesswrong.com/posts/YSJCPC5Tu2vRRryto/option-control#Rewarding_cooperation), [notes from Daniel Kokotajlo](https://docs.google.com/document/d/1DTmRdBNNsRL4WlaTXr2aqPPRxbdrIwMyr2_cPlfPCBA/edit?tab=t.0), [Let’s compensate misaligned AIs that help us prevent AI takeover](https://docs.google.com/document/d/1SUgGftOMKO4GVSBzOa3wMDcAhM4UrOGAjYVPnALxKY4/edit?tab=t.0#heading=h.ldo1rytwm7ve). And there’s also more general discussion of giving AI property rights so that it’s less incentivized to engage in violence, e.g. Dwarkesh Patel, [Give AIs a stake in the future](https://www.dwarkesh.com/p/give-ais-a-stake-in-the-future), Matthew Barnett, [Consider granting AIs freedom](https://forum.effectivealtruism.org/posts/4LNiPhP6vw2A5Pue3/consider-granting-ais-freedom), and [Salib and Goldstein, AI rights for human safety](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4913167). There’s also some sparse discussion of ethical reasons to pay AIs, which is structurally similar, e.g. [here](https://www.alignmentforum.org/posts/7vRiJozcE2AjcRm7J/axrp-episode-27-ai-control-with-buck-shlegeris-and-ryan#Is_AI_control_evil__).
[^note-2]: All this goes through if the AI doesn’t “take over” in the sense of becoming the dominant or only power in the world, but instead just gets a substantial proportion of total power. We’ll continue saying “take over” for simplicity, and because we do think that the AI might achieve complete domination.
[^note-3]: Some of our points also apply to later schemers with diminishing marginal returns to resources.
[^note-4]: For example, if the AI is able to [collude with itself](https://www.alignmentforum.org/posts/GCqoks9eZDfpL8L3Q/how-to-prevent-collusion-when-using-untrusted-models-to), it is probably able to do this. (Some people respond to this argument by saying that if an AI is great at colluding with itself, it will also be great at acausal coordination with future AIs. This seems mistaken to us: acausal coordination seems to us to require the AI to do several difficult things that aren’t related to picking arbitrary Schelling points.)
[^note-5]: Relatedly, the AI might want to try to acausally trade with aliens. For non-superhumanly capable models, this seems drastically less promising than trading with the lab because the model is in a very different decision situation from mature alien civilizations (which rules out evidential cooperation). Alternatively, the AI might think that it is in a simulation run by a superintelligence—but clueless as to what this implies about what it should do.
[^note-6]: A potentially dubious historical analogy: it’s kind of like the situation where a city is under siege, and someone considers betraying the city in the hope that the conquering army will reward them. This has a [mixed historical track record](https://chatgpt.com/share/6852edfb-6d78-800f-aa84-9090769396b9) for the traitor. And we might be in a better position to pay early schemers because it’s sufficient to pay one or just a few of them, whereas in the defending-a-city case you might have heaps of different selfish people who have the opportunity to betray you, such that you’re unable to afford paying off all of them.
[^note-7]: The standard argument here is that opposing parties would strictly prefer a lottery (with odds based on each party's chance to win the conflict) over the supposedly indivisible issue over costly conflict.
[^note-8]: One possible reason here is that being the kind of civilization that doesn’t uphold their promises would decorrelate us from civilisations that do uphold their promises, and generally deter such civilizations from wanting to trade with us (in the context of [ECL](https://longtermrisk.org/files/Multiverse-wide-Cooperation-via-Correlated-Decision-Making.pdf)).
[^note-9]: There is an argument here that in worlds where we can teach AIs false facts, we are going to be fine anyway, and in worlds where we can’t teach them false facts, we can make a deal. However, in the world where we _can_ teach AIs false facts, in order to prevent a scenario like the one outlined in the vignette, we would need to be able to use that ability to accomplish at least one of the following:

    -   Honeypot the early AI into attempting takeover, in a way that convinces stakeholders that it would be too risky to deploy the later AI without substantially increased safety measures. (This seems unlikely.)
    -   Extract useful safety-increasing labor from the early AI so we prevent takeover by the late AI.
    -   Directly prevent takeover by the late AI.

    If our ability to teach false facts is merely good enough to prevent _early_ AIs from attempting takeover, it could overall undermine our ability to align or control later AIs.
[^note-10]: There are some questions here about the legal structure of the foundation, and it might be the case that the US is not the ideal jurisdiction for the foundation. It would be good for there to be legal recourse in case the board of trustees decide to betray their mission of furthering the AI’s interests.
