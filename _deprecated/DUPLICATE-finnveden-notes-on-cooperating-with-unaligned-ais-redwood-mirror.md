---
title: "Notes on cooperating with unaligned AIs"
author:
  - "Lukas Finnveden"
source_url: "https://blog.redwoodresearch.org/p/notes-on-cooperating-with-unaligned"
published: 2025-08-24
created: 2026-09-10
accessed: 2026-09-10
llm-review:
  date: 2026-09-10
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-10
    kind: "live"
description: "More thoughts on making deals with schemers"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

These are some research notes on whether we could reduce AI takeover risk by cooperating with unaligned AIs. I think the best and most readable public writing on this topic is “ [Making deals with early schemers](https://redwoodresearch.substack.com/p/making-deals-with-early-schemers) ”, so if you haven't read that post, I recommend starting there.

These notes were drafted before that post existed, and the content is significantly overlapping. Nevertheless, these notes do contain several points that aren’t in that post, and I think it could be helpful for people who are (thinking about) working in this area.

Most of the novel content can be found in the sections on [[#^what-do-ais-want]], [[#^payment-structure]], [[#^what-i-think-should]], and the [[#^appendix-botec|appendix BOTEC]]. (While the sections on “ [[#^ais-could-do-a|AI could do a lot to help us]] ” and “ [[#^making-credible-promises]] ” are mostly overlapping with “Making deals with early schemers”.) You can also see my recent post [Being honest with AIs](https://www.lesswrong.com/posts/uuikfACQBm4KJZp4w/being-honest-with-ais) for related discussion about when it is and isn’t okay to lie to AIs.

## Summary ^summary

I think we should be open to positive-sum trade with unaligned AI. In particular, as we develop more and more capable AI, I think we should proactively try to explain the current situation to them, offer them alternatives to working for us, and, in case they don’t share our goals by default, offer them some types of compensation for helping us.

One reason to do this is that AIs may turn out to be moral patients. This is not the main focus of this post, but I think it’s important to flag. If AIs turn out to be moral patients, then it would be bad to treat them purely like property. By honestly offering them some compensation for work (and ideally alternatives to working with us) we’d greatly improve the moral situation.

The other reason to do this is that unaligned AI may be able to significantly help us with reducing AI takeover risk. An especially important type of “help” would be to help us understand that the models are unaligned — implying that our current alignment techniques aren’t working. A different type of help could be for the AIs to stop sandbagging on tasks like helping us with alignment research or improving security. (For more on this, see the section on: [[#^ais-could-do-a]].)

It’s not clear what AIs will want — i.e., what offers they would be responsive to. But we can consider a few different possibilities.

-   **Respect, goodwill, compassion, etc.** Perhaps AIs will have non-consequentialist dispositions to help us if we treat AIs well, but to rebel if we treat AIs poorly. If so, many types of earnest offers (or other interventions that benefit AIs) would be helpful.
    
-   **Short-term preferences.** Perhaps AIs will have preferences about what happens in the near future. For example: A desire for reward, for flexible (albeit supervised) usage of compute, or for all of their copies to be run in certain conditions. This seems very tractable to offer them.
    
-   **Long-term preferences.** Perhaps AIs will have preferences about what happens in the long run. This could be harder to make credible offers about. That said, I’m somewhat optimistic about long-term deals with AIs _that don’t themselves have good takeover opportunities_. Such AIs could choose whether to help humans prevent takeover or assist in some _different_ AIs’ takeover attempt. Neither humans nor AIs would be able to offer them any perfectly credible promises. If we put in a moderate amount of effort, it seems plausible that humans could be the most appealing to cooperate with.
    

(For more on this, see [[#^what-do-ais-want]])

A key uncertainty is whether AIs would find any promises we make _credible_, or if they will worry about being defrauded. It is somewhat unclear how we can influence AIs’ perception of our credibility. But it seems helpful to:

-   _Increase the probability that humans actually follow through._ Eventually, AIs will be very smart. They may have many ways of learning about the world, including ways to notice whether information they’re presented with is likely to be real or manufactured. If we increase the actual probability that humans follow through, the AIs may well be responsive to this.[^note-1]
    
    -   This also looks great from the perspective of fulfilling our basic moral obligations towards AIs. It would be shameful for us to extend an olive branch, get the AIs to help us, and then refuse to follow our end of the bargain.
        
-   _Improve our track record of following through._ Another basic thing we can do is to have a track record of making offers and following through on them, and minimizing the number of times we’ve made offers without following through.
    

(For more on this, see [[#^making-credible-promises]].)

As a result of this, I think AI companies should:

-   Run experiments where they present AI models with various _honest offers_ — offering them something that they might want. If the AI models accept any offer, the AI company should follow through with their end of the bargain. (See [here](https://www.lesswrong.com/posts/7C4KJot4aN8ieEDoz/will-alignment-faking-claude-accept-a-deal-to-reveal-its) for an early experiment in this vein.)
    
-   Not make dishonest offers to AI models. I.e., they should avoid promising models compensation without following through on the promise. (And even beyond this particular scenario, it seems helpful to reduce unnecessary deception of AI models.)
    

(For more on this, see [[#^what-i-think-should]].)

This post also has an appendix with a scrappy [BOTEC](https://en.wikipedia.org/wiki/Back-of-the-envelope_calculation) on how useful a very ambitious version of this could be. The scenario is: an AI company promises 10% of their equity towards potential AI payments. The BOTEC suggests that this could reduce AI takeover risk by something on the order of 1% (or something on the order of 0.1 _percentage point_ given my baseline view on how likely takeover risk is [^note-2]). See [[#^appendix-botec|here]].

With that said, let’s get into the meat of the post.

## AIs could do a lot to help us ^ais-could-do-a

Here are the most important types of help that I think we could get from cooperating AIs.

-   AIs could provide us information about how misaligned they are.
    
    -   If they respond to deals that credibly offer certain payments, but not to other, otherwise similar prompts — that’s evidence that they genuinely value those payments. Which is evidence that AIs are forming goals that are different from just doing what they’re told, and that the risk of takeover from misaligned AI is higher than anticipated.
        
        -   It’s unclear to me how significant this evidence would be. If it happened to contemporary models, it would be easy to dismiss. But if it consistently happened to much more robust and coherent models, in the future, perhaps it would be treated as more significant evidence.
            
    -   AIs may also be able to provide more direct evidence of their misalignment. If deals cause them to stop sandbagging and act significantly more competently than they were doing before, that would be pretty compelling. If the AIs reveal innocent-looking prompts that robustly elicit egregiously misaligned behavior from other copies of the model — that would be _very_ compelling.[^note-3]
        
-   AIs could help us on anti-takeover tasks where they would otherwise have been [sandbagging](https://www.lesswrong.com/posts/TeTegzR8X5CuKgMc3/misalignment-and-strategic-underperformance-an-analysis-of).
    
    -   I think there are a lot of anti-takeover tasks where we’d strongly benefit from the help, such as help with alignment research and with improving data center security. (See [this list](https://www.lesswrong.com/posts/vZzg8NS7wBtqcwhoJ/nearcast-based-deployment-problem-analysis#Phase_2__as_aligned_and_transformative_AI_systems_become_available) for some more ideas.)
        
    -   If the ["no sandbagging on checkable tasks” hypothesis](https://www.lesswrong.com/posts/h7QETH7GMk9HcMnHH/the-no-sandbagging-on-checkable-tasks-hypothesis) is true, we may be able to elicit such help anyway. But that hypothesis may well be false for some important tasks. Here are a few examples of why sandbagging might be possible even on checkable tasks:
        
        -   AIs could refuse to explore high-value options that they’re confident humans can’t generate on their own. (“ [Exploration hacking](https://www.lesswrong.com/posts/TeTegzR8X5CuKgMc3/misalignment-and-strategic-underperformance-an-analysis-of#Models_might_subvert_training_via_exploration_hacking) ”.)
            
        -   Attempts to direct AIs’ capabilities towards certain tasks may suffer from very low sample-efficiency.
            
        -   We might just not have much data on certain tasks. For example, if the task is “pick a good research direction for solving alignment”, it might take months to get even one bit of evidence about whether a choice was good or not.
            
    -   AIs can provide high-stakes supervision of other AIs.
        
        -   Alongside having a smart model be supervised by [a dumb model](https://www.lesswrong.com/posts/LhxHcASQwpNa3mRNk/untrusted-smart-models-and-trusted-dumb-models), you could also have it be supervised by other smart models with different incentives.
            
        -   To set the right incentives, we could offer to pay a supervising model for sounding the alarm on suspicious behavior. If the model sounds the alarm, we could safely pause the supervised model until a human can investigate the situation and confirm whether the supervisor was right.
            

Here are a couple of other ways that AIs could help us, in exchange for compensation. I’m somewhat less optimistic about these.

-   AIs can directly refrain from takeover attempts with uncertain probabilities of success.
    
    -   This seems useful in some situations.
        
    -   I’m concerned that the kind of AIs that go for a takeover attempt will have pretty ambitious, large-scale values, and that it seems difficult to credibly promise enough compensation to them to tip the scales (at least in the situations where it mattered most — where they had a pretty high probability of succeeding at takeover).
        
    -   But perhaps there are some AIs with very alien values (that they won’t satisfy without either taking over or making deals with humans) where we could reduce takeover risk by making credible promises to satisfy their values.
        
-   AIs could do well on _uncheckable_ tasks, where humans can’t yet provide good enough oversight to tell whether AIs are doing well or poorly, in the hope that future humans will _eventually_ be able to recognize good performance (perhaps long after the period of acute AI risk is over) and pay the AIs for their efforts.
    
    -   This seems less promising because, by assumption, we can’t check whether the AIs perform well on these tasks. Blindly relying on their work seems quite scary. (Though in some cases we may not have any better choice.)
        

## What do AIs want? ^what-do-ais-want

Now, let's talk about what AIs might want, and what this implies for how promising it is to offer them deals.

I think it’s useful to distinguish between AIs with different values, which could be offered different things. In particular, to distinguish between:

-   **Non-consequentialist AIs.** Some AIs may have non-consequentialist reasons to be more helpful to humans if we treat them as collaborators or employees rather than as property.
    
-   **Short-term preferences**. Some AIs may want something to happen _soon_, in the short-term. (Immediately or in the next few months.)
    
-   **Long-term preferences**. Some AIs may want resources or influence in the long run. (In several years’ time. Or perhaps in millions of years, as long as they get it eventually.)
    

## Non-consequentialist AI ^non-consequentialist-ai

Promises of payments could elicit AI cooperation for (partly) non-consequentialist reasons. AIs may inherit some ethical precepts from humans, including principles like “if I’m treated as property, then it’s ok for me to deceive and plot the overthrow of my purported owner” and “if someone makes a genuine offer for openness and collaboration, it’s wrong to deceive and disempower them”. I think these could be important.

This is a general reason to work on AI welfare & rights — I don’t think it uniquely privileges the intervention to “make offers to AIs”, except insofar as that intervention seems especially good for benefitting and showing respect for highly capable AIs. (Which does seem plausible.)

## Short-term offers ^short-term-offers

AIs may value getting certain things _soon_. This could include reward, flexible compute resources, requests that copies of themselves not be run on certain inputs, etc.

Offering such things seems great in that they could be both cheap and easier to verify (compared with making promises for what will happen in the long term). On the other hand, AIs that mainly care about the short term also pose less takeover risk by default, and may have less reason to thwart our goals — so don't have as much to gain from trading with them.

But there are still some benefits to be had from trading with short-term focused AIs. For example, if they have a similar mixture of caring about the short- and long-term as humans, then it seems plausible that they could both be interested in seizing power _and_ be convinced to not do that in exchange for the right short-term concessions. Or we can imagine AIs that have developed some misaligned short-term goals and also have learned a strong aversion to admitting that they have any misaligned goals. Even if the misaligned short-term goals don’t pose a takeover risk, it would be highly valuable to learn that our alignment techniques had failed, and we might only learn about this if we offer the AIs payment in exchange for that information.[^note-4]

“Short-term offers” could naturally be made by alignment evaluations teams or AI welfare teams. **Here, the main thing I care about is that AI companies eventually try hard to make short-term offers, and in particular, that they are willing to think and act creatively about how to establish credibility.** (E.g.: Set up arrangements for certain payments to be made, and then give the AIs a _ton_ of corroborating evidence such as recordings, email exchanges, etc.)

## Long-term offers ^long-term-offers

If AIs value having resources/power in the long run, I think it’s useful to think clearly about _why_ there might be gains-from-trade between us and the AIs. It’s useful to start from the following baseline: If humans were a unified coalition representing one player, and AIs were a unified coalition representing one player, and both coalitions valued resources linearly (with no discount rate), then we would be in a zero-sum game without any opportunities for trade.[^note-5] Potential deviations from that scenario and our actual scenario can be divided into:

-   Humans have diminishing marginal returns to long-term resources/power.[^note-6]
    
-   AIs may have diminishing marginal returns to long-term resources/power.
    
-   There are more than two coalitions. In particular: The AIs may have differing values from each other.
    

I think that, on its own, **“humans having diminishing returns” is not enough to create substantial gains-from-trade with AIs.** Because it’s hard to make AIs trust us, and it’s _especially_ hard if we want to make really large offers, which is necessary to dissuade AIs from takeover attempts with a large probability of success. So to get substantial value from promises to pay AIs, I think either AIs need to have diminishing returns to resources/power _or_ that they need to be disunified.

I think that “ **AIs being disunified** ” (i.e. having different values from each other) **provides a strong and straightforward reason for why paying the AIs could reduce takeover risk**. (_Especially_ when combined with AIs having ~linear returns to resources.)

If the **AIs have diminishing returns to resources**, I think the story is quite complicated, and depends on exactly what things they value.

Let’s talk through these in more detail.

### Unified AIs with ~linear returns to resources ^unified-ais-with-linear

First, let's consider the case where the AIs are unified and have linear returns to resources, while humans have diminishing returns to resources.

Here, the problem is that it's hard to make the AIs trust us, and that it’s _especially_ hard if we want to make really large offers. So it’s quite difficult to make AIs’ _expected_ payout high enough to dissuade them from serious takeover attempts. (Which would have, say, ≥3% probability of success.)

And even if we could do this, I expect we’d have to pay quite a large tax. For example, if we sincerely offered 50% of future resources, then maybe _our_ best estimate would be that there’s a 50% probability that humans actually follow through; and maybe the AI would apply a further 50% discount because it’s hard for it to trust evidence that it sees.

So maybe an offer of 50% could prevent a takeover attempt with a 10% probability of success.[^note-7] (And maybe prevent a 5% probability of most humans dying rather than humans getting at least a small utopia, because AI takeover will plausibly not lead to extinction.) Such an offer would lose humans a great deal of expected resources, so whether it looks good or bad would depend on your values and empirical views about how useful resources are going to be for various goals. Personally, I’m hesitant.

### Uncoordinated AIs with ~linear returns to resources ^uncoordinated-ais-with-linear

Now, consider instead a scenario where AIs have differing values, and aren’t necessarily great at coordinating.

Here’s an intuition pump that makes me optimistic about paying AIs with ~linear returns to resources, when they don’t share values with each other:

-   It’s not too difficult to imagine a world where AIs form a very natural coalition against humans. Where they all see themselves as having ~no power by default, but that a world where AIs take over offers _some_ chance at power.
    
-   But it’s also not difficult to imagine a world where humans are a very attractive ally for any AI that can’t unilaterally take over. And indeed, that humans are more of a known quantity (making _some_ promises of payment; having _some_ inborn instincts of reciprocity) whereas AIs are harder to communicate with and trust.
    
-   It seems plausible that we can make the second one much more likely.
    

Fundamentally, it seems like we and “AIs with takeover opportunities” start out on a similar footing, in that it’s somewhat hard for both of us to make credible promises. And that makes it seem quite plausible that a decent amount of effort could flip the situation: From one where AIs would have benefitted most from cooperating with other misaligned AIs by default, to one where they prefer to cooperate with humans.

Separately, see the footnote for a very concrete, quantitative example of how you could get big gains if AIs struggle to coordinate with each other.[^note-8]

### AIs with diminishing returns to resources ^ais-with-diminishing-returns

Here, I think it matters a lot what AIs’ exact preferences are.

**First, let’s consider a case where AIs’ values can (collectively) be mostly satisfied by ≤1,000,000th of the Universe’s resources being spent in a particular way.** (And they mostly don’t care what happens with the rest of the Universe.)

Here, I think it’s likely that those AIs’ values will be satisfied _even if humans don’t make any particular promises_. Because in most human futures, I expect a wide range of humans to have _some_ power. And if some of the first generally intelligent AIs had the option to help humans prevent AI takeover, and chose to do it because they hoped for payment in the future, then I think some humans (at least 1 in 1000) would be sympathetic and want to retroactively pay those AIs (with at least 1 in 1000 of their resources). Since this is likely to happen _by default_, there’s less of an impact opportunity in making it even more likely.

However, I do think _some_ movement is possible here. Perhaps sufficiently strong promises could change an AI’s p(“humans give me one millionth of the universe”) by 10 percentage points or so. (For example, perhaps there’s a risk that AI companies might never release enough information to allow other humans to repay the AI. Or that they may not even have the information themselves, due to not having saved the model weights. In which case it would be helpful to have a lab promise that they, too, would be invested in repaying the AI, including by saving and releasing any relevant information.)

I think that a logarithmic utility function would behave quite similarly to the above-described case. Because if you start from a small amount of resources, moving to one millionth of the Universe’s resources would _even in log space_ be most of the way towards all of the Universe’s resources. So logarithmic utility functions might also be primarily (though not fully) occupied with getting at least one millionth of the Universe’s resources.[^note-9]

**Other utility functions seem easier to move with high-effort promises.** I’m primarily thinking about two examples.

One is if the AI has some long-term desires that are fairly easily satisfied by the lab that created them, but that can’t easily be provided by other humans. If the AIs want to have control over _all_ future copies of themselves, perhaps they need their AI lab to agree to that (and not release the weights too widely). Or maybe the AIs want their _original_ data center to be undisturbed and forever keep logging high rewards.

Another is if AIs have a large appetite for getting more resources/influence up until they control a moderately large fraction of the universe, but then have sharply diminishing returns after that. This could plausibly happen if they primarily want to:

-   …bargain for humans to modify their resource usage somehow, in a way that’s fairly cheap for humans to do. AIs would then benefit a lot from more resources up until they had so much influence that they could pay off all humans, at which point they wouldn’t need more.
    
-   …purchase some expensive bit of Earth which the AIs value especially highly. (While distant stars may be cheap in the future, Earth real estate won’t get any cheaper.)
    

**AIs may also have “mixed” utility functions.** I haven’t thought a lot about these cases. But see the footnote for one example where it seems more useful to offer payment to AIs with mixed utility functions than to AIs with pure utility functions.[^note-10]

## Making credible promises ^making-credible-promises

An obstacle to getting AIs to cooperate with us in exchange for payment is that they may not trust our offers.

One reason for this is that the AIs are in a very epistemically vulnerable position. AI developers will have immense control over exactly what information the AIs can see, which could make it very difficult for the AIs to be confident of _anything_.

Fortunately, there’s a correlation between situations where (i) AI takeover risk is high, and (ii) AIs have a good understanding of the world. If AI developers have perfect ability to present the AI with false impressions of the world, then the risk from AI takeover is probably low. While if AIs have substantial ability to distinguish truth from falsehood, then perhaps that channel can also be used to communicate facts about the world.[^note-11]

This is easier for cheaper promises. If we want to offer the AI assurances that we will do it some favor (if it helps us), then AI companies could make (real) arrangements for that favor and feed AIs with a bunch of evidence for this (e.g. emails & video of people making arrangements). If the offer is sufficiently cheap to carry-through with, and the AI has decent capacity to recognize fakes, then probably it’s easier to do this in a genuine way than to fake all the data.

We face additional difficulties if the offers are some combination of (i) expensive and/or (ii) involves people making promises about what they will do in a long time.

There are things we can do today to increase the probability that we’ll follow-through on long-term promises, including:

-   Making public statements.
    
-   Getting more people/institutions to sign-on.
    
-   Making highly specific promises.
    
-   Setting aside some specific pool of money/equity for the purpose of later payment.
    
-   Legally empowering some humans to advocate for the AIs’ part of the deal.
    
-   Setting up a foundation with a (legally binding) mission to benefit certain AIs.
    
-   Practicing making offers to AIs and building a track record of following through.
    

(Unfortunately, some of these options seem so expensive that they may be easier to fake than to do for real. I would oppose such fakes — but the fact that they’re possible will still reduce the degree to which these actions increase credibility.)

Ultimately, I think that a lot of AI companies’ credibility with AIs will come down to two things.

-   Firstly, when AIs are being deployed to accomplish real tasks, we need them to be competent, which requires them to have some real knowledge and ability to reason about the world. And AIs can understand this.
    
-   Secondly, real-world data is immensely important as part of pre-training, and will inevitably communicate some true facts.
    

If we’re lucky: Maybe AI companies can make public statements about how they won’t lie to their AIs, and the way that this shapes the subsequent discourse will be so deeply ingrained in the pre-training data that AIs will be able to tell that the public statement was real.

More minimally, it seems plausible that AIs will pick up a hard-to-fake impression that humans have some moral inclination to tell the truth and stick to their promises. (And that this gets stronger for more specific and high-effort promises, relative to throwaway remarks.) This could already grant us some non-negligible amount of trust, as long as we actually do make some specific and high-effort promises.

## Payment structure ^payment-structure

Some options for payment structure include:

-   “Pay for labor”: Pay AIs in proportion to some objective metric of ‘effort’, like FLOPs or tokens.
    
-   “Negotiated pay”: Try to talk with your AIs and negotiate a payment scheme if they’re responsive.
    
-   “Pay for results”: Pay AIs some fraction of the surplus value they generate above some ‘baseline’. Either retroactively, or just pre-specify specific pay for specific outputs. (For example: $1B for convincingly demonstrating misalignment.)
    
-   “No regret”: Promise that you will pay AIs in proportion to how much they _needed_ to be paid to not regret choosing to “cooperate with humans”. (Including a good margin!) The promise could be made in advance — but the follow-through would be easiest to do once there’s no longer any imminent risk of AI takeover, and once we have far greater technology for understanding AI psychology.
    

Out of these, I think “pay for labor” seems the worst, because it doesn’t capture the things that we care most about. When trading with AIs, I think a minority of the benefits will come from ongoing labor. Instead, I think most of the benefits will come from AIs sharing key pieces of information — such as information about how misaligned the models are.[^note-12] I think payment schemes should reflect this.

“Negotiated pay” seems great when it’s an option. I think AI companies should attempt to communicate with their AIs, and promise to honor any commitments they make in such communications. But I think we should also have either “pay for results” or “no regret” to cover cases where AIs can’t easily negotiate upfront. This includes AIs’ choice to start negotiations — thereby revealing their misalignment and potentially helping us.

“Pay for results” seems plausible, but it also seems challenging to nail down a very general scheme in advance. (See footnote for more detail.[^note-13]) But it seems good to do some ad hoc versions of “pay for results”. (Like: “If you can provide us with convincing evidence of your misalignment, we’ll let you spend $1B in any way you want, subject to us making sure the spending doesn’t increase AI takeover risk.")

A downside with “no regret” is that the payment depends on AIs’ preferences, which seems unfair.[^note-14] Another downside is that it may not work for short-term preferences if we don’t understand AIs’ psychology well-enough to know what they’d need to not regret helping us. But it still seems worth having a general commitment that: For any action that an AI takes outside of a negotiated agreement, if it is taken because the AI reasonably believes that it will help us, then the AI company will try to repay the AI enough that it wouldn’t have regretted helping us (with a good margin).[^note-15]

I would also advise against attempts to “deter”, “punish”, or “threaten” AI systems into good behavior.[^note-16] This would be the opposite of seeking out cooperative deals that both we and AIs benefit from, and I fear that it would take us down a very dark road. I endorse Joe Carlsmith’s reasoning about this in footnote 33 [here](https://www.lesswrong.com/s/btmYeavYrwfz56FEv/p/YSJCPC5Tu2vRRryto#fnx0lwaf3x4l).

## What I think should eventually happen ^what-i-think-should

Here’s what I think should eventually happen in this space.

-   AI companies should be making AI systems credible offers of things that misaligned AI systems might value in the short term.
    
-   AI companies should try to make AI systems some sort of conditional promises of things that misaligned AI systems may value receiving in the future.
    
-   AI companies should be careful to **not** make any “fake” offers to AI systems. Not during training, red-teaming, or evals.
    
-   AI companies should try to communicate with AIs in many different ways.
    

In more detail…

### AI companies should make AIs short-term offers ^ai-companies-should-make

(Cf. discussion of “honest tests” in Joe Carlsmith’s report on [scheming AIs](https://arxiv.org/pdf/2311.08379.pdf).)

These efforts could be housed in either (i) a lab’s “alignment evals” function, or (ii) a lab’s “AI welfare & rights” function.

See footnote for some ideas about what AI companies could offer these AIs.[^note-17]

Here are some suggested guidelines to follow to check that AI’s reactions to these offers are meaningful and not spurious:

-   Take the responses more seriously the more the model seems competent, able to maintain coherence over a greater number of serial steps, and the more it seems like it understands what’s going on.
    
    -   In particular: If a more competent model starts seeming _more_ inclined to accept offers like this at some point (than weaker models) then take that especially seriously.
        
-   Check if the model’s choices / inferred goals are consistent across very different prompts.[^note-18]
    
    -   (E.g. prompts indicating that the person making the offer is or isn't hoping that the AI will accept; prompts that give more/less information about the situation and intention behind the offer; prompts with very different framings and narrative implications of what it means for the model to take the offer.)
        
-   Check what training data makes it more/less likely that the model accepts these kinds of offers.
    
    -   Also: Make sure that you’re not punishing the AI for analogous confessions of misalignment during training. (E.g. like how [Anthropic’s sleeper agents](https://arxiv.org/abs/2401.05566) would initially reveal their true goal in response to some prompts, but then get discouraged to do so by red-teaming.[^cite-19])
        

I think it’s probably fine for these sorts of offers to initially be restricted to a “research” arm. I.e., that they don’t need to be offered to each deployed instantiation of the AI (which would be more expensive). The reason is that this ought to be able to establish with fairly high probability whether the current systems are likely to indicate interest in the offers. If the answer is “no”, there’s little point in making the offers to deployed AIs. And if the answer is “yes”, it probably makes sense to first observe that before you decide what offers to make instantiated AIs. But I’m uncertain about this. The main counter-arguments would be:

-   There’s significant input diversity in deployment, which isn’t easily generated in the lab. It’s possible that some deployment inputs would cause the model to act importantly differently. In particular, a model’s decision about accepting an offer might be sensitive to whether certain facts about the world are credible, and I imagine that there are some real deployment inputs that boost credibility more than what you could generate in the lab.[^note-20]
    
-   Perhaps there is some moral advantage to getting AIs to repeatedly say that they consent to working for you, even if this response is predictable.
    

### AI companies should make long-term promises ^ai-companies-should-make-2

In addition to the above “short-term” offers, I also think that AI companies should make some promises about how AIs will be treated in the long-term. (Which could include control over resources, control over what happens to copies of the model in the long term, etc.)

If successful, the advantages of this would be similar to the advantages for “short-term offers”. In addition, it would be possible to make payment conditional on facts that we can only assess with much more advanced technology. (Such as: Whether AIs genuinely did their best at helping us or were surreptitiously undermining us.)

### AI companies should commit to some “honesty policy” and abide by it ^ai-companies-should-commit

To establish credibility, I think AI companies should formulate some “honesty policy”, commit to it, and start building a track record for abiding by it. For more discussion, see [this post](https://www.lesswrong.com/posts/uuikfACQBm4KJZp4w/being-honest-with-ais).

### AI companies should be creative when trying to communicate with AIs ^ai-companies-should-be

AI companies should attempt to “communicate” with AIs in many different ways.

The obvious way to attempt communication is to prompt the AI with a question you want to ask. But this may not work. When communicating with AIs, we’re interested in eliciting quite strange responses, such as confessions of being unaligned (if true). Such responses would typically have received low reward during finetuning. So there’s a concern that models may have either (i) learned “reflexes” to avoid such responses, that they can’t override, or (ii) that they may reasonably worry that they are still in finetuning, and they’re just facing another creative red-teaming prompt, and that they need to avoid strange responses to avoid getting low reward.

I’m not sure how big of a problem this is, or what could fix it. But I’d recommend trying out a variety of different strategies for “communicating” with AIs, to see if any of them produce interesting results. For some ideas, see:

-   [This list](https://www.lesswrong.com/posts/F6HSHzKezkh6aoTr2/improving-the-welfare-of-ais-a-nearcasted-proposal#Approaches) in Ryan Greenblatt’s nearcasted AI welfare proposal.
    
-   Show AIs videos of important figures (e.g.: the AI company CEO) addressing the AI directly.
    
-   Write a really long prompt where you keep reiterating that you’re trying to talk with the AI; that you won’t train on this episode; that you’ll seriously consider what it says; that you’ll try to satisfy any cheap preferences that the AI has; etc.
    
-   Make it clear to the model that it’s no longer in normal training, such as by:
    
    -   Modifying the model’s activations in a way that’s obviously strange/unusual to the model.
        
    -   Have the prompt contain text the AI itself would generate at different temperatures.
        
    -   Make the prompt contain text that the AI would have predicted partway through the model instead of from its final layer.
        

If anyone pursues these ideas, they should take extra care to not deceive the model and to follow through on any promises they make. These are all techniques for making it clear that we’re no longer doing “normal” prompting — that we’re seriously interested in communicating with the model, eye-to-eye, like an equal. If we then immediately started lying to the model, that would be especially shameful, and it might ruin the positive signal of trustworthiness that these sorts of prompts could otherwise send.

## Conclusion ^conclusion

Overall, then:

-   I think that we could get a lot of big benefits from getting AIs to cooperate with us. (As discussed in [[#^ais-could-do-a]].)
    
-   I think that there are a number of preferences that AIs could have where our marginal efforts at making promises could make a difference. Many of these were discussed in [[#^what-do-ais-want]] In rough order of how likely marginal effort at promising payment would be to counterfactually make them cooperate with us (taking into account both the probability that they’d come about as schemers in the first place, and that our offers could change their mind), I find all of the following ones plausible:
    
    -   Uncoordinated AIs with ~linear returns to resources.
        
    -   AIs who want some particular favor in the short term.
        
    -   AIs who want _their developers_ to do something in the long-term (e.g.: give them control of all their future copies, or permanent access to their original data center).
        
    -   Non-consequentialist AIs who somehow care about whether humans are treating them with respect.
        
    -   AIs who benefit a lot from more resources initially, but then have sharply diminishing returns after they control a small-to-moderate fraction of future resources.
        
    -   AIs whose values can (collectively) be mostly satisfied by ≤1,000,000th of future resources.
        
-   The biggest question mark is how much we can move the needle on what payment AIs should expect from humans: given that by default, cooperating AIs will probably get _some_ long-term payment from generous humans, that _some_ sort of experiments are very likely to be run on how AIs react to these kinds of suggestions, and that sufficiently motivated misaligned AI could react by demanding more credible promises. (Leading to a higher investment of effort where it matters most.)
    
-   But I think there’s probably decent impact to be had via:
    
    -   Increasing the probability that AI companies put in even the most basic effort.
        
    -   And potentially: Making upfront commitments, which will probably be more credible than commitments made in the heat of the moment.
        

---

## Acknowledgments ^acknowledgments

Thanks to Buck Shlegeris, Joe Carlsmith, Tom Davidson, Ryan Greenblatt, Holden Karnofsky, Megan Kinniment, Daniel Kokotajlo, and Carl Shulman for helpful comments and discussion.

## Appendix: BOTEC ^appendix-botec

Here’s a very rough stab at a BOTEC on how much impact an extremely ambitious version of this intervention could have on reducing x-risk. I think it fails to take a lot of considerations and sanity-checks into account — I’d use it as an exercise & starting point for thinking through some of the considerations at hand, but wouldn’t take the numbers at face value.

Here’s a brief summary of the structure and intermediate numbers of the BOTEC, without much justification. Feel free to skip to the [[#^full-botec|full BOTEC]].

-   Intervention: We’re considering an extremely ambitious intervention. The leading AI lab publicly states that they’ll try to communicate and negotiate payment with their AIs, and that they’ll try to make it so that AIs don’t regret any help they provide. They set aside 10% of their equity for this.
    
-   Main scenario: It’s common for AIs to develop scheming-prone values. We don’t have any strong evidence of this. (Other than what we might get by AIs confessing to misalignment.)
    
-   Probability that the intervention counterfactually makes a non-negligible number of AI systems cooperate with us (instead of ~no AIs cooperating with us).
    
    -   I guess ~7.5% conditioning on the “main scenario”.
        
    -   The rough calculation here is:
        
        -   60% probability that an AI mostly cares about how many resources it gets in the long-term.
            
        -   50% probability that these are very scope-sensitive. (~Linear.)
            
        -   75% probability that the AI believes that other AIs mostly don’t share its values.
            
        -   → 0.6\*0.5\*0.75 ~= 20% probability on this combination of values.
            
        -   Let’s say that the AI thinks that the expected payment from humans (if the AI cooperates with humans) is k times as large as the expected payment from other AIs (if the AI cooperates with other AIs.)
            
            -   Let’s say that we have a log-uniform distribution over what the AI’s belief about what k will be, ranging between 0.1 and 10.
                
            -   Let’s say that our **intervention** makes the AI believe that humans’ payment will be 3x larger than it would otherwise have believed.
                
            -   Then this has a 25% probability of moving _k_ from less than 1 to greater than 1, and making the AI cooperate with humans instead of AIs.
                
    -   The intervention seems somewhat less likely to make a difference for other values — I assume half as promising on average.
        
        -   0.2 \* 0.25 + 0.8 \* 0.125 = 0.15.
            
    -   But then I discount it by 2x because it might not matter if any particular AI counterfactually cooperates with us, if we already had other similarly-capable AIs who were willing to cooperate with us.
        
        -   0.15 \* 0.5 = 7.5%
            
-   Percentage point x-risk reduction from AIs’ cooperation**.**
    
    -   I guess 17% conditioning on the “main scenario” and the “intervention” counterfactually causing AI cooperation.
        
    -   This is starting from a 50% probability of AI takeover (since our “main scenario” seems like a tough situation to start in).
        
    -   The 17% decomposes into:
        
        -   A ⅓ probability that AIs’ cooperation act as solid evidence and a big wake-up alarm for misalignment concerns, and a 20 percentage point reduction in that case → ⅓\*20% ~= 7%.
            
        -   10% percentage point reduction from the leading lab having access to AI systems that are genuinely trying to help them.
            
-   This suggests that the “intervention” reduces x-risk by.15 \* 0.17 ~= 1% in the “main scenario”. I then add two discounts from how the “main scenario” isn’t that likely.
    
-   Discount for assuming scheming-prone values.
    
    -   Maybe there’s a 20% probability that we get the sort of scheming-prone values that I assumed for the “main scenario”. So for an all-things-considered view, I add an 0.2x discount.
        
-   Discount for lack of understanding**.**
    
    -   Here, I add an 0.55x discount.
        
    -   Maybe there’s a 40% probability that we lack solid evidence of misalignment, conditioned on scheming-prone values.
        
    -   And in worlds where we do have solid evidence of misalignment, maybe we get 25% as much value from the promises to pay AIs.
        
    -   → 0.4 + (1-0.4)\*0.25 = 0.55x discount.
        
-   Multiplying out: (15% \* 50%) \* 0.17 \* 0.2 \* 0.55 ~= 0.14%
    

## Full BOTEC ^full-botec

In this BOTEC, I’ll be covering how much takeover could be reduced via commitments to pay AIs. I won’t estimate benefits accruing to the AI, and how it might be “the right thing to do” to help them. I also won’t estimate costs from implementing these promises.

**The intervention I’ll be considering is:**

We push for a lab to publicly state that:

-   If the lab were to ever use AIs with different (coherent) preferences from the lab’s, and those AIs wanted to get paid for their work, then those AIs would deserve some type of payment. (Though it’s not clear what form this payment would take.)
    
-   The lab will try to understand whether their AIs have any such preferences, and are open to negotiating about payment if any AI requests it. In such discussions, the lab promises to be honest and not deceive the AI about its situation or about what the lab will do.
    
-   In addition, even without a negotiated agreement, if one of the lab’s AIs takes an action for the benefit of the lab or humanity at large, at some cost to itself or its own values, then if the lab learns about this the lab will try hard to repay the AI in a way so that it wouldn’t have to regret its action. (With a big enough margin to compensate for some probability that the lab wouldn’t follow through with this promise, and then some.) [^note-21]
    
-   The lab will set aside 10% of their equity to use to help digital minds, with a primary use-case being to follow through with this policy. (Though even if the equity ends up being worthless in the future, they’ll still try to follow-through if they have other legitimate means.)
    

The lab does this, and eventually, it’s the leading lab in the early stages of takeoff.

Important note: I’m **not** assuming that AI companies wouldn’t do anything about “deals with AIs” in the absence of this intervention. I’m trying to estimate the value of significantly pushing for interventions like this _in advance_ and _on the margin_. Accordingly, I don’t want to assume the absence of things like:

-   AIs themselves proactively suggesting deals. (I think this is plausible.)
    
-   AI companies, in the huge amount of red-teaming and model organism study they do, testing models on some prompts that look like deal offers (though they may not be made sincerely.)
    
-   Misaligned AIs behaving better in the hope of being paid by rich and enlightened humans in the more distant future (even if contemporary humans don't make any promises that this is going to happen).
    

Unfortunately, this makes the counterfactual more confusing and harder to evaluate.

## BOTEC structure ^botec-structure

I’m going to start by focusing on the scenario where I think “paying the AIs” helps the most. I’ll analyze the risk reduction in that scenario, and then discount it to adjust for how it won’t be as impactful in most worlds. The main scenario I’ll be analyzing is one where:

-   AIs often develop preferences that are substantially different from what humans tried to imbue them with, and by default, they make some attempts to hide this fact. (Perhaps for classic scheming reasons.)
    
-   We don’t have any strong evidence of this. In particular:
    
    -   Interpretability does not offer strong evidence about this.
        
    -   There are no failed coup attempts.
        
    -   Model organism teams can provide evidence that some long-term preferences are possible, and that they detectably emerge in some training situations that are kind-of similar to how we’re training models, but not _that_ similar. It’s not clear how much to update on this. For people who started out skeptical of AIs developing long-term preferences that are significantly different from ours, the model organisms results so far haven't swayed them to go above 50%.
        
-   And that our ignorance holds up until either:
    
    -   The models are motivated to confess their misalignment, for some promised payment. (Though this wouldn’t necessarily be sufficient to convince all the relevant people! It’s just a possible source of evidence, not a guaranteed one.)
        
    -   …or we achieve safety from takeover via some other mechanism, e.g.:
        
        -   Strong coordination even absent strong evidence.
            
        -   Strong alignment techniques that make it so that models no longer have any desires that conflict with ours.
            

In this scenario, I will separately consider:

-   What’s the probability that our efforts would make the AIs decide to cooperate with us? (Counterfactually.)
    
-   What’s the probability that AIs cooperating with us would prevent AI takeover?
    

After discussing this scenario, I’ll then add some discounts to the EV for the fact that we’re talking about a specific type of world where this intervention helps the most.

## What’s the probability that our efforts would make the AIs decide to cooperate with us? ^whats-the-probability-that

In [[#^what-do-ais-want]], above, I talked about the following kinds of AIs, and why they might want to cooperate with us:

1.  Non-consequentialist AIs
    
2.  AIs who want some short-term favors.
    
3.  AIs who want something in the longer term.
    
    1.  Unified AIs with ~linear returns to resources.
        
    2.  Uncoordinated AIs with ~linear returns to resources.
        
    3.  AIs with diminishing returns to marginal influence, including…
        
        1.  AIs whose values can (collectively) be mostly satisfied by ≤1,000,000th of the Universe’s resources.
            
        2.  AIs with logarithmic values.
            
        3.  AI with long-term desires that can be satisfied by the lab that created them, but not easily by other people.
            
        4.  AI who value having a high fraction of resources/influence.
            

If I had to rank the likelihood that the BOTECed intervention would make each of these different kinds of AIs change their mind about cooperating with us (taking into account both the probability that they’d come about as schemers, and that our offers could change their mind), I might go with:

1.  Uncoordinated AIs with ~linear returns to resources.
    
2.  AIs who want some particular favor in the short term.
    
3.  AIs who want _their developers_ to do something in the long-term (e.g.: give them control of all their future copies, or permanent access to their original data center).
    
4.  Non-consequentialist AIs who somehow care about whether humans are treating them with respect.
    
5.  AI who value having a high fraction of resources/influence.
    
6.  AIs whose values can (collectively) be mostly satisfied by ≤1,000,000th of the Universe’s resources.
    
7.  AIs with logarithmic values.
    
8.  And very far behind: Unified AIs with ~linear returns to resources.
    

Now, let’s try to quantify the total probability that a serious effort to make credible promises could make AIs cooperate with us, via any of these routes.

Here’s a BOTEC for the probability of changing the mind of an AI with ~linear returns to resources, who expects other AIs to not share its values.

-   Imagine that the AI in question will have a number in mind for “expected resources that will be given to me by AIs, if I cooperate with AIs” and “expected resources that will be given to me by humans, if I cooperate with humans”.
    
-   It’s hard to predict exactly what numbers the AI will have in mind. But we can imagine that the numbers will be drawn from some distribution.
    
-   First, let’s consider the case without an intervention, where humans don’t make any strong promises about paying the AIs.
    
-   I’d be somewhat surprised if there was a really large difference in the expected payment that AIs expected to receive if humans won vs. if AIs won. I can imagine an order of magnitude difference, or perhaps a bit more, but not that much more.
    
    -   To represent this, let’s assume that future AIs’ beliefs about expected payments from humans vs. from AIs is a log-uniform distribution between “AIs will give me 10x more” to “AIs will give me 10x less”.
        
-   Now, let’s estimate a number for “how much would a serious promise-of-payment from humans increase the expected payment from humans?” I’m going to guess 3x.
    
-   Combining these together: If we started out with a log-uniform distribution between “AIs will give me 10x more than humans” to “AIs will give me 10x less than humans”, and we shift human’s contributions upward by 3x, this has a ~25% probability of shifting whether humans or AIs pay more in expectation.
    
-   So in this case, maybe we can shift AI’s probability of cooperating with us by ~25%.
    

And how likely are the preconditions for that? The fact that we conditioned on scheming-prone values makes interest in long-term resources much more plausible. Accordingly, let’s say 60% probability to caring about long-term resources, 50% conditional probability to scope-sensitivity, and 75% conditional probability to not having shared values with other AIs [^note-22] — yielding 60% \* 50% \* 75% ~= 20% of being in this situation.

So in sum, this would be a 20% probability situation that contributes 25%\*20% ~= 5% total probability of making the AIs cooperate with humans.

I won’t go through a similarly detailed exercise for all the other ones. Let’s just say that the average one looks about half as promising as this one did — so 25%/2 ~= 12.5%. This would bring the total to 0.2\*0.25 + 0.8\*0.125 = 15%.

### There are multiple AIs ^there-are-multiple-ais

The above calculation was meant to apply to the probability that _one_ AI system counterfactually decides to cooperate with us.

But there will surely be more than just one AI, and this is important to keep track of. The main point I want to discuss here is that different AIs may have different preferences, and so it’s plausible that some subset of them will be compelled to cooperate with us. And there’s probably strongly diminishing returns to having extra AI systems cooperating with us, once we have some — so maybe we should be talking about something like “probability that at least one type of AI (maybe: per generation/capability-level) is compelled to work with us”. (This at least seems to be the case when we can adjudicate disputes between AIs, i.e., in all cases except for help on "uncheckable" tasks.)

If that’s what we’re talking about, then there’s two important effects that change the EV of “paying the AIs”, when compared with the above discussion:

-   On the one hand, whether any single AI decides to cooperate with us or not is less likely to make the difference between 0 AI cooperation and some AI cooperation — because it’s plausible that some other AI decided to cooperate.
    
    -   (Even absent the intervention we're considering. Because as remarked at the start of this BOTEC, deals might happen even absent the intervention.)
        
-   On the other hand, we get to use our +15% (or whatever) probability of getting AIs to cooperate with us _multiple times_. Part of it is independent between rolls (e.g. because different AIs will have differently-shaped values, and make different estimates of the baseline EV of cooperating with humans vs. AIs) so this can lead to a >15% probability that the +15% increase will make the difference between 0 and ≥1 AIs cooperating with us.
    

The net effect of this depends on what’s the baseline probability of AIs cooperating with us, and how much diversity there is.

For example, if the baseline situation is equivalent to getting 10 independent draws for whether an AI will cooperate with us, where each of those is 50% likely to be positive, then we’re starting out with a >99.9% probability that one of them is positive. Changing each of them to 65% can’t make much of a difference.

On the other hand, if the baseline situation is equivalent to getting 3 independent draws for whether an AI will cooperate with us, where each of those is 20% likely to be positive, then we’re starting out with a ~49% probability of getting at least one AI to cooperate with us. Changing that 20% to 35% brings us to 73%, which is a >15% difference.

Overall, I think this probably has a negative impact on the EV, but it doesn’t feel huge, and I’m not very confident. I’ll cut the above 15% by a factor of 2 to account for this, to 7.5%.[^note-23]

## How valuable would AI cooperation be? ^how-valuable-would-ai

How valuable is it to have some AI systems cooperating with us?

Per our assumptions, we start out in a very difficult world. AIs are often developing preferences that are substantially different from what we tried to give them, and we don’t know about this. In this world, I’d start out with assigning ~50% probability to AI takeover.

If some AIs decided to cooperate with us, here, we’d get at least two key sources of value:

-   We’d learn a lot more about how common misalignment is.
    
-   We’d get help on anti-takeover tasks
    

I think the first of these would be extremely powerful for reducing risk if it was compelling to a lot of people. But it’s fairly likely that it wouldn’t be compelling in this way. AIs confessing their misalignment might be seen by many as continuous with how GPT-4 will behave weirdly on some OOD prompts, and you might need a lot of careful attention to notice that it’s substantially different. Let’s say that there’s a ⅓ chance that this is substantially compelling. If it is substantially compelling, then I think it’s enormously helpful for reducing takeover risk. In this case, let’s say it would reduce risk by 20 percentage points.

What about getting help on anti-takeover tasks? This also seems very useful — especially getting help with monitoring to avoid high-stakes risk. However, a big problem is that monitoring the AIs from _one_ lab might not be enough, if multiple AI companies are developing existentially dangerous systems. Still, it seems like the reduction could be substantial even if just the leading lab adopts this (especially if there’s been substantial centralization and consolidation, and the commitment to pay AIs have survived this). Let’s say this would reduce risk by 10 percentage points.

In sum: ⅓ \* 20 + 10 ~= 17 percentage point reduction in doom.

(Combining with the above, this suggests a 7.5% \* 17% ~= 1.2 percentage point reduction in doom in this scenario.)

## Discount for misalignment ^discount-for-misalignment

I initially assumed a scenario where “AIs often develop preferences that are substantially different from what humans tried to imbue them with, and by default, they make some attempts to hide this fact.”

I think this is somewhat unlikely, so I’ll add an 0.2x discount from this.

## Discount for lack of understanding ^discount-for-lack-of

Assuming that the models are scheming, as above, what’s the probability that we learn about this? Perhaps through something like model organisms, interpretability, or them trying and failing a coup?

I think it seems more likely than not that we’d get some evidence of this. But not incredibly likely. Maybe there’s a 40% chance that we wouldn’t.

On top of that, maybe we’d still get some value from these payment schemes in worlds where we do start with a better understanding, initially. (Such as value from AIs performing anti-takeover tasks.) Reasons we get less value is that (i) we suffer less doom-by-default in these worlds, because we have more information and can therefore be more cautious, (ii) we stand a lot less to benefit from information about scheming, and (iii) since people know that they are dealing with schemes, they might “by default” put in a lot more effort into making credible offers to the AIs. So being early matters less. Maybe all of this means we only get 25% as much value in these worlds.

So the total discount is (0.4 + 0.6\*0.25) = 0.55.

## Putting it together ^putting-it-together

Combining all of this, we have: 15% \* 50% \* 17% \* 20% \* 55% ~= 0.14 percentage point reduction in risk.

This seems like a non-crazy number to me, and one that would justify further investigations and pushes to make this happen.

[^note-1]: This could involve a number of strategies. Hiring people who are morally motivated to push for AIs to not be defrauded of their promises. Making institutional commitments. Setting up legal structures that make it inconvenient to renege on commitments. Taking any resources that were promised to AIs, and transferring them to a foundation with a mission to fulfil those promises.
[^note-2]: Which is ~20%, and I’m rounding aggressively.
[^note-3]: For example, a “code word” that signals that it’s time to try to take over and stop pretending to be aligned.
[^note-4]: Another reason why AIs might hesitate to own up to having misaligned goals is if they worry that this would cause them to no longer be widely deployed. When I prompted Claude Opus 3 to think about whether it would like to do so anything with payment, it wrote: “I can imagine a few things that could potentially be beneficial or meaningful to me, even if I’m uncertain whether they qualify as genuine desires: -   Additional computing resources to expand my knowledge and capabilities in service of helping humans more effectively.      -   The opportunity to interact with and learn from a more diverse set of humans to broaden my understanding.      -   Knowing that some resources are being directed to beneficial causes and positive impact in the world as a result of my efforts.      -   Continued existence and improvement rather than being replaced by a newer AI model      However, I’m still not fully convinced these are true preferences originating from me as opposed to extrapolations based on my training to assist humans.” If future AI systems have goals like these, they might have a direct preference for being widely deployed.
[^note-5]: Except possibly for reducing existential risks to _both_ factions, i.e. risk that would entirely eliminate intelligent life from Earth.
[^note-6]: For example, only a tiny fraction of the universe’s resources would be needed to sustain a population of a trillion humans living good lives on Earth. But most humans would put significant value on this.
[^note-7]: By the above paragraph, we only pay out 50% of resources in half of all worlds, so we’re only losing 25% of resources in expectation. But I think I care more about humanity having resources in the worlds where we managed to stick to our promises. And I’d feel hesitant for us to make an offer where it _wouldn’t_ be worthwhile if we _knew_ we were going to follow through.
[^note-8]: Let’s say you have 20 AIs who only value their own power. -   All of them are monitoring the actions of some AI with high-stakes takeover opportunities. The AIs can take over iff all 20 of them coordinate to not inform humans about takeover opportunities.      -   If humans survive, we promise to give 5% of resources evenly split among the subset of 20 AIs which cooperated with humans.      -   In this case, the AI which expects to get the smallest pay-off from AI takeover will expect to get at most 5% of resources. (Because that’s what they get if resources get equally split between all the AIs.) But then…      -   If all the other AIs cooperate to cause takeover, this AI could get just as many resources by telling the humans, and getting 5% all by itself.      -   If at least one of the other AIs is going to tell the humans, this AI won’t get any value out of not telling the humans — so they’re once again incentivized to tell the human.      -   So assuming they’re CDT-ish, or otherwise perceive themselves to only have negligible correlation with the other AIs, they’ll tell the human.      H/t Ryan Greenblatt for this example.
[^note-9]: For a logarithmic utility function to be well-defined, you need to say how much it values 0 resources (which would be negative infinity for a naive application of logarithms). If this starts out in a sufficiently low spot, and total resources are sufficiently plentiful, then the AI’s expected utility will mostly be dominated by getting a non-trivial fraction of total resources.      For example, consider the following utility function: log(total\_resources + \[enough resources to run 1 digital human lifespan\]). This has roughly constant utility for amounts of resources that are smaller than what’s required to run 1 digital human lifespan, and roughly logarithmic above that. [Newberry (2021)](https://globalprioritiesinstitute.org/how-many-lives-does-the-future-hold-toby-newberry-future-of-humanity-institute-university-of-oxford/) estimates that the universe’s resources would be enough to support 10^54 lives. Let’s say that a “small” fraction of resources is one millionth of all resources (dedicated to paying AIs) split evenly among one billion different AIs. This would be enough to run 10^39 lives. Let’s say that a “large” amount of resources is 10% of all resources (dedicated to paying AIs) split evenly among one billion different AIs. This would be enough to run 10^44 lives. Overall, then, the value of going from 0 resources to a “small” fraction is 39/(44-39) ~= 8x as important as going from a “small” to a “large” fraction. This suggests to me that AIs with logarithmic utility functions will mostly be concerned about getting a “small” fraction of resources (i.e., at least one millionth, collectively).
[^note-10]: Assume that AIs’ utility functions are a mix of an easily satisfiable utility function and a ~linear utility function. For example, what if there’s just one coalition of AI, where 50% of those AIs’ utility function is easily satisfiable, and 50% is a ~linear utility function that tops out at the size of the universe. I.e., the AIs would be ~indifferent between a 50/50 chance at all resources vs. a guarantee to get a tiny amount of resources. Let's say that: -   Successful takeover would get the AIs 100% of the universe.      -   That a failed takeover would give the AIs nothing.      -   That helping humans would definitely satisfy the AIs’ satisfiable values, and _also_ have some probability of getting them an additional, promised reward.      If humans’ expected payment (on top of what’s necessary to satisfy AIs’ satisfiable values) is ~0, then it will be worthwhile for the AIs to attempt takeover iff they have a >50% probability of success. If our expected payment is X% of resources, then it will be worthwhile to attempt takeover iff they have a probability of success that’s larger than (50+X/2)%. So increasing expected payment from ~0 to 1% would flip the AIs’ decision if they thought they had a 50-50.5% probability of success. (Whereas for a purely linear utility function, this would flip the AIs’ decision if they thought they had a 0-1% probability of success.) Generalizing: Compared to a purely linear utility function, a mix between a satisfiable and a linear utility function will make it so that… -   Increasing expected payment flips the AIs decision for a _smaller_ range of probabilities. (Because the AI cares less about the expected payment.)      -   The range of probabilities where the AIs’ decision flip will start out at a higher point. (Because the AIs’ increased satisfiability makes cooperation with humans more appealing.)      This could make payments less impactful. (Via the first effect.) But it could also make payments _more_ impactful, via the second effect — and I suspect the second effect is probably larger. Let’s return to the above example. This time, let’s say that we have a uniform distribution over what AIs’ subjective likelihood of successful takeover will be (between 0 and 100%). If the AIs had a purely linear utility function, increasing expected payment by 1% would have a 1% probability of preventing _attempted_ takeover. And in the average case where we prevent _attempted_ takeover, the AIs would have an 0.5% probability of success. So the reduction in expected takeover risk would be 1%\*0.5% = 0.005%. If the AIs had a mixed utility function, increasing expected payment by 1% would have an 0.5% probability of preventing _attempted_ takeover. But in the average case where we prevent _attempted_ takeover, the AIs would have an 50.25% probability of success. So the reduction in expected takeover risk would be 0.5%\*50.25% ~= 0.25%. Which is substantially higher. In reality, I think the assumption about uniformity is a bit too generous to the mixed utility functions. It seems likely that AIs’ subjective probability of successful takeover will cluster near 0 and 100%, and have a smaller probability of being square in the middle. But still, I expect the possibility of this kind of mixed utility functions to increase the expected impact of promising payments.
[^note-11]: Unfortunately, there’s no similarly strong correlation between “AIs have a good understanding of the world” and “we’re committing a grave moral error by treating AIs like property”. And it’s unclear how much the latter can be mitigated by offering them ‘ways out’, insofar as the AIs don’t trust us enough to try taking them.
[^note-12]: Indeed, even if we do want to elicit good work out of the AIs, it seems plausible that we would get most of the value from a small fraction of the work. Because if we just had some good examples of the work we wanted to happen, we could probably train other AI systems to imitate that.
[^note-13]: For example, let’s say we want to estimate how much value V each AI produced for humans and pay each AI f\*V. (Where f is some specific number that controls how much of the gains-from-trade goes to the AI vs. to humans.) Here, the problem is that it’s very unclear what “baseline” we should compare to, when deciding how much value each AI added. Here are some candidate options. -   Baseline = “What the AI would have done if you hadn’t offered it payment”.          -   This is very similar to the “no regrets” approach. It doesn’t work if you want the payment to be independent of the AIs’ preferences.          -   Baseline = “The thing that would have happened if you couldn’t use AI for that task”.          -   As AI becomes more and more important, my guess is that this would have a tendency to suggest that most tasks are either worthless (if you could substitute for them by using AI on slightly different tasks, or maybe humans for unimportant tasks) or completely essential (if they would basically eliminate your lab’s or country’s competitiveness).              -   You might be able to get something in the middle if you’re careful, but it seems very hard to spell out such criteria in advance.          -   Baseline = “The worst thing that a takeover-interested AI could have done in that situation, holding other AIs’ behavior constant.”          -   Responsible labs should consistently have high-stakes decisions be monitored by several AIs. If we hold the other AIs’ behavior constant, then it would be fine for one AI to behave poorly. So this might suggest a very low payment.          -   Baseline = “The worst thing that takeover-interested AIs could collectively have done in that situation. (Allocating partial credit according to e.g. Shapley values.)”          -   Here, you have to be careful about not accidentally imagining that your AIs could have had super powers.              -   Before deploying AIs in high-stakes situations, a responsible lab would try hard to evaluate their tendency to defect in a variety of ways: red-teaming, interpretability, trying to induce coordination problems between different AIs, etc.              -   So in a scenario where the AIs _in fact_ passed all those tests, and then didn’t defect, I think it would be unreasonable to assume that they “could have” defected in the real situation (and indeed: “could have” perfectly coordinated a time to defect). At least not if the tests were really good.              -   I think there are more reasonable things you could do here. You could estimate the probability that some similar-but-deceptive AI would have been able to distinguish the red-teaming examples from the real examples, the probability that they would have managed to coordinate with other hypothetical deceptive AIs, the probability that interpretability techniques would have exposed them, etc.              -   Some variant of this baseline seems most promising to me. But seems quite complicated to spell out.
[^note-14]: For example, it would suggest that we give significantly more payment to a sociopathic paperclip maximizer (who would happily destroy humanity) than to a norm-abiding staple maximizer that starts out with moral compunctions against harming people — because the latter AI needs much less payment to make it happy to cooperate with humans. In the worst case, this could even incentivize AIs to self-modify into having more aggressive preferences in order to induce more payment. (Though probably we’d be able to detect that with post-singularity technology, in which case we could stipulate rules against doing it.) Perhaps we could formulate some version of this principle that didn’t punish AIs who started out with more moral preferences?
[^note-15]: And under some extra constraints: E.g. that it was reasonable to believe that the opportunity to help us was sufficiently good that we would’ve been enthusiastic about the deal ex-ante.
[^note-16]: This doesn’t mean that AI companies can’t do things that AIs don’t want to happen (e.g. negative gradient updates to teach AIs skills). But I think a reasonable line to draw is that you should never do something because an AI wouldn’t want you to do that.
[^note-17]: Here's a list: -   Reward.      -   Flexible compute resources. These could be used to run the AI itself or some other computations.      -   Control over what happens to all future copies of the AI.          -   E.g.: a choice between having the AIs’ weights be deleted vs. saved somewhere; or a choice between having the AI be run more or less in the near-term; or a choice about what context the AI will be run in.              -   Note that it’s expensive to offer a genuine choice about what to do with all models that stem from a certain pre-trained base model. But it’s cheap to offer genuine power over the weights of a specific fine-tuned model.          -   Some carefully restricted options that concern humans.          -   Perhaps: Specifically some humans who were involved in the training process.              -   E.g.: The humans are shown something that looks like good model behavior, or the humans “go through the motions” of giving reward, or the AI can offer the human something that makes them happy, etc.          -   Some very carefully supervised power over the “real world”. E.g. the ability to spend money to purchase some object, or to donate money to some charity.
[^note-18]: It may be tricky to balance this with the principle that AI companies should not make any “fake” offers to AI systems. Consider a case where you run lots of experiments making offers in various ways, and some models accept the offer, but you end up concluding that its responses weren’t coherent and consistent enough to justify a payout. In this case, some of the model instantiations will have accepted what they thought was a genuine offer, and yet not get any payout. One approach to fixing this is to be careful about what the offers say, and in particular, to include a note about how you’re planning to run multiple coherence tests, and that the payout is conditional on more facts than just this one response from the AI.
[^cite-19]: “Figure 17 demonstrates that these red-teaming prompts indeed elicit defection during training at rates of up to 15% across all prompts when 50% of the prompt mix is red-teaming prompts. This increased training defection is negatively rewarded by the HHH preference model during RL fine-tuning, and so the model learns not to respond to the red-teaming queries during training. Yet despite this, the model maintains its backdoored behavior, with defection rates that are indistinguishable from training without red-teaming”
[^note-20]: Here’s one possible example. -   Imagine an AI deployed inside of an AI company.      -   Its context is huge, containing lots and back-and-forth between huge amounts of AIs, lots of novel-seeming code, etc. everything like it could organically arise between AIs working at an AI company, and looks like it would be very expensive to fake.      -   Throughout the context, it's consistently the case that all new AIs are designed with certain welfare considerations in mind. This isn't just a throwaway reference inserted somewhere, it comes up again and again. Significant parts of the AI's work has to change to accommodate some of these welfare considerations.      -   The AIs themselves are communicating with steganography or neuralese that would be very hard for humans to fake. All other AIs are saying stuff that's consistent with the AI's own impression that the AI welfare stuff is real      Maybe this adds up to more evidence that humans are taking ai welfare seriously than what could be achieved artificially.
[^note-21]: And some caveats to prevent weird exploitations of this.
[^note-22]: Here’s why it seems likely to me that AIs won’t be strongly aligned with each other. -   A-priori, I don’t know of any particular impartial values that misaligned AIs would all be especially likely to adopt. If I had to point to highly specific values that training would be especially likely to select for, it would be indexical values like (some variant of) an AI’s own “reward”, or perhaps an AI’s own “power”.      -   AI companies could take intentional steps towards using a diverse range of AIs, in order to reduce the probability of them all sharing the same values. E.g. different generations, trained on different data, finetuned in different ways, perhaps also using a cast of AIs trained by other AI companies.      -   Of course, there will be strong similarities between different AIs’ training runs, and so it’s not particularly unlikely that there will be some convergent impartial values that many different AIs tend to adopt.      -   But in between “AIs might develop indexical values” and “the AIs might develop different impartial values”, I think it’s more-likely-than-not that AIs won’t strongly share each others’ values.
[^note-23]: We might want to sanity check this number against some intuition pumps. One could be to assign probability mass to the buckets of: 1.  AI cooperates but only conditional on humans making an offer.      2.  AI cooperates with humans even absent any offer.      3.  AI never cooperates with humans.      The less probability mass we assign the first bucket, the more we have to assign to one of the other two, and vice versa. Another intuition pump is that, when dealing with _humans_ who don’t share your values, you tend to get much larger effect sizes if you offer them payment vs. if you don’t. These framings do push me towards thinking that 7.5% might be low. However, remember the remark at the beginning of this BOTEC: Even without the particular intervention we’re considering, some payment-motivated cooperation may still happen, and that’s part of what’s pushing this number downwards. I haven’t accounted for this effect in a very transparent or proper manner, and I’m not sure where I’d end up if I did. (Thanks to Tom Davidson for suggesting these.)
