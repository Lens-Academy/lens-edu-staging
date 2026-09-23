---
title: "Coherent decisions imply consistent utilities"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/posts/RQpNHSiWaXTvDxt6R/coherent-decisions-imply-consistent-utilities"
published: 2019-05-12
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "So we're talking about how to make good decisions, or the idea of 'bounded rationality', or what sufficiently advanced Artificial Intelligences might…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

(_Written for Arbital in 2017._)

---

# Introduction to the introduction: Why expected utility? ^introduction-to-the-introduction

So we're talking about how to make good decisions, or the idea of 'bounded rationality', or what sufficiently advanced Artificial Intelligences might be like; and somebody starts dragging up the concepts of 'expected utility' or 'utility functions'.

And before we even ask what those are, we might first ask, _Why?_

There's a mathematical formalism, 'expected utility', that some people invented to talk about making decisions. This formalism is very academically popular, and appears in all the textbooks.

But so what? Why is that _necessarily_ the best way of making decisions under every kind of circumstance? Why would an Artificial Intelligence care what's academically popular? Maybe there's some better way of thinking about rational agency? Heck, why is this formalism popular in the first place?

We can ask the same kinds of questions about [probability theory](https://www.lesswrong.com/w/probability_theory):

Okay, we have this mathematical formalism in which the chance that X happens, aka  P(X), plus the chance that X doesn't happen, aka P(¬X), must be represented in a way that makes the two quantities sum to unity: P(X)+P(¬X)=1.

That formalism for probability has some neat mathematical properties. But so what? Why should the best way of reasoning about a messy, uncertain world have neat properties? Why shouldn't an agent reason about 'how likely is that' using something completely unlike probabilities? How do you _know_ a sufficiently advanced Artificial Intelligence would reason in probabilities? You haven't seen an AI, so what do you think you know and how do you think you know it?

That entirely reasonable question is what this introduction tries to answer. There are, indeed, excellent reasons beyond academic habit and mathematical convenience for why we would by default invoke 'expected utility' and 'probability theory' to think about good human decisions, talk about rational agency, or reason about sufficiently advanced AIs.

The broad form of the answer seems easier to show than to tell, so we'll just plunge straight in.

  

# Why not circular preferences? ^why-not-circular-preferences

_De gustibus non est disputandum,_ goes the proverb; matters of taste cannot be disputed. If I like onions on my pizza and you like pineapple, it's not that one of us is right and one of us is wrong. We just prefer different pizza toppings.

Well, but suppose I declare to you that I _simultaneously_:

-   Prefer onions to pineapple on my pizza.
-   Prefer pineapple to mushrooms on my pizza.
-   Prefer mushrooms to onions on my pizza.

If we use >P to denote my pizza preferences, with X>PY denoting that I prefer X to Y, then I am declaring:

onions>Ppineapple>Pmushrooms>Ponions

That sounds strange, to be sure. But is there anything _wrong_ with that? Can we disputandum it?

We used the math symbol > which denotes an ordering. If we ask whether >P can be an ordering, it naughtily violates the standard transitivity axiom x>y,y>z⟹x>z.

Okay, so then maybe we shouldn't have used the symbol >P or called it an ordering. Why is that necessarily bad?

We can try to imagine each pizza as having a numerical score denoting how much I like it. In that case, there's no way we could assign consistent numbers x,y,z to those three pizza toppings such that x>y>z>x.

So maybe I don't assign numbers to my pizza. Why is that so awful?

Are there any grounds besides "we like a certain mathematical formalism and your choices don't fit into our math," on which to criticize my three simultaneous preferences?

(Feel free to try to answer this yourself before continuing...)

:::callout {title="Click here to reveal and continue" collapse="closed"}
Suppose I tell you that I prefer pineapple to mushrooms on my pizza. Suppose you're about to give me a slice of mushroom pizza; but by paying one penny ($0.01) I can instead get a slice of pineapple pizza (which is just as fresh from the oven). It seems realistic to say that most people with a pineapple pizza preference would probably pay the penny, if they happened to have a penny in their pocket.[^note-1]

After I pay the penny, though, and just before I'm about to get the pineapple pizza, you offer me a slice of onion pizza instead—no charge for the change! If I was telling the truth about preferring onion pizza to pineapple, I should certainly accept the substitution if it's free.

And then to round out the day, you offer me a mushroom pizza instead of the onion pizza, and again, since I prefer mushrooms to onions, I accept the swap.

I end up with exactly the same slice of mushroom pizza I started with... and one penny poorer, because I previously paid $0.01 to swap mushrooms for pineapple.
:::

This seems like a _qualitatively_ bad behavior on my part. By virtue of my incoherent preferences which cannot be given a consistent ordering, I have shot myself in the foot, done something self-defeating. We haven't said _how_ I ought to sort out my inconsistent preferences. But no matter how it shakes out, it seems like there must be _some_ better alternative—some better way I could reason that wouldn't spend a penny to go in circles. That is, I could at least have kept my original pizza slice and not spent the penny.

In a phrase you're going to keep hearing, I have executed a 'dominated strategy': there exists some other strategy that does strictly better.[^note-2]

Or as Steve Omohundro put it: If you prefer being in Berkeley to being in San Francisco; prefer being in San Jose to being in Berkeley; and prefer being in San Francisco to being in San Jose; then you're going to waste a lot of time on taxi rides.

None of this reasoning has told us that a non-self-defeating agent must prefer Berkeley to San Francisco or vice versa. There are at least six possible consistent orderings over pizza toppings, like mushroom>Ppineapple>Ponion etcetera, and _any_ consistent ordering would avoid paying to go in circles.[^note-3] We have not, in this argument, used pure logic to derive that pineapple pizza must taste better than mushroom pizza to an ideal rational agent. But we've seen that eliminating a certain kind of shoot-yourself-in-the-foot behavior, corresponds to imposing a certain _coherence_ or _consistency_ requirement on whatever preferences are there.

It turns out that this is just one instance of a large family of _coherence theorems_ which all end up pointing at the same set of core properties. All roads lead to Rome, and all the roads say, "If you are not shooting yourself in the foot in sense X, we can view you as having coherence property Y."

There are some caveats to this general idea.

For example: In complicated problems, perfect coherence is usually impossible to compute—it's just too expensive to consider _all_ the possibilities.

But there are also caveats to the caveats! For example, it may be that if there's a powerful machine intelligence that is not _visibly to us humans_ shooting itself in the foot in way X, then _from our perspective_ it must look like the AI has coherence property Y. If there's some sense in which the machine intelligence is going in circles, because _not_ going in circles is too hard to compute, well, _we_ won't see that either with our tiny human brains. In which case it may make sense, from our perspective, to think about the machine intelligence _as if_ it has some coherent preference ordering.

We are not going to go through all the coherence theorems in this introduction. They form a very large family; some of them are a _lot_ more mathematically intimidating; and honestly I don't know even 5% of the variants.

But we can hopefully walk through enough coherence theorems to at least start to see the reasoning behind, "Why expected utility?" And, because the two are a package deal, "Why probability?"

  

# Human lives, mere dollars, and coherent trades ^human-lives-mere-dollars

An experiment in 2000—from a paper titled "[The Psychology of the Unthinkable: Taboo Trade-Offs, Forbidden Base Rates, and Heretical Counterfactuals](http://scholar.harvard.edu/files/jenniferlerner/files/2000_the_psychology_of_the_unthinkable.pdf?m=145089665)"—asked subjects to consider the dilemma of a hospital administrator named Robert:

> Robert can save the life of Johnny, a five year old who needs a liver transplant, but the transplant procedure will cost the hospital $1,000,000 that could be spent in other ways, such as purchasing better equipment and enhancing salaries to recruit talented doctors to the hospital. Johnny is very ill and has been on the waiting list for a transplant but because of the shortage of local organ donors, obtaining a liver will be expensive. Robert could save Johnny's life, or he could use the $1,000,000 for other hospital needs.

The main experimental result was that most subjects got angry at Robert for even considering the question.

After all, you can't put a dollar value on a human life, right?

But better hospital equipment also saves lives, or at least one hopes so.[^note-4] It's not like the other potential use of the money saves zero lives.

Let's say that Robert has a total budget of $100,000,000 and is faced with a long list of options such as these:

-   $100,000 for a new dialysis machine, which will save 3 lives
-   $1,000,000 for a liver for Johnny, which will save 1 life
-   $10,000 to train the nurses on proper hygiene when inserting central lines, which will save an expected 100 lives
-   ...

Now suppose—this is a supposition we'll need for our theorem—that Robert _does not care at all about money,_ not even a tiny bit. Robert _only_ cares about maximizing the total number of lives saved. Furthermore, we suppose for now that Robert cares about every human life equally.

If Robert does save as many lives as possible, given his bounded money, then Robert must _behave like_ somebody assigning some consistent dollar value to saving a human life.

We should be able to look down the long list of options that Robert took and didn't take, and say, e.g., "Oh, Robert took all the options that saved more than 1 life per $500,000 and rejected all options that saved less than 1 life per $500,000; so Robert's behavior is _consistent_ with his spending $500,000 per life."

Alternatively, if we can't view Robert's behavior as being coherent in this sense—if we cannot make up _any_ dollar value of a human life, such that Robert's choices are consistent with that dollar value—then it must be possible to move around the same amount of money, in a way that saves more lives.

We start from the qualitative criterion, "Robert must save as many lives as possible; it shouldn't be possible to move around the same money to save more lives." We end up with the quantitative coherence theorem, "It must be possible to view Robert as trading dollars for lives at a consistent price."

We haven't proven that dollars have some intrinsic worth that trades off against the intrinsic worth of a human life. By hypothesis, Robert doesn't care about money at all. It's just that every dollar has an _opportunity cost_ in lives it could have saved if deployed differently; and this opportunity cost is the same for every dollar because money is fungible.

An important caveat to this theorem is that there may be, e.g., an option that saves a hundred thousand lives for $200,000,000. But Robert only has $100,000,000 to spend. In this case, Robert may fail to take that option even though it saves 1 life per $2,000. It was a good option, but Robert didn't have enough money in the bank to afford it. This does mess up the elegance of being able to say, "Robert must have taken _all_ the options saving at least 1 life per $500,000", and instead we can only say this with respect to options that are in some sense small enough or granular enough.

Similarly, if an option costs $5,000,000 to save 15 lives, but Robert only has $4,000,000 left over after taking all his other best opportunities, Robert's last selected option might be to save 8 lives for $4,000,000 instead. This again messes up the elegance of the reasoning, but Robert is still doing exactly what an agent _would_ do if it consistently valued lives at 1 life per $500,000—it would buy all the best options _it could afford_ that purchased at least that many lives per dollar. So that part of the theorem's conclusion still holds.

Another caveat is that we haven't proven that there's some specific dollar value in Robert's head, as a matter of psychology. We've only proven that Robert's outward behavior can be _viewed as if_ it prices lives at _some_ consistent value, assuming Robert saves as many lives as possible.

It could be that Robert accepts every option that spends less than $500,000/life and rejects every option that spends over $600,000, and there aren't any available options in the middle. Then Robert's behavior can equally be _viewed as_ consistent with a price of $510,000 or a price of $590,000. This helps show that we haven't proven anything about Robert explicitly _thinking_ of some number. Maybe Robert never lets himself think of a specific threshold value, because it would be taboo to assign a dollar value to human life; and instead Robert just fiddles the choices until he can't see how to save any more lives.

We naturally have not proved by pure logic that Robert must want, in the first place, to save as many lives as possible. Even if Robert is a good person, this doesn't follow. Maybe Robert values a 10-year-old's life at 5 times the value of a 70-year-old's life, so that Robert will sacrifice five grandparents to save one 10-year-old. A lot of people would see that as entirely consistent with valuing human life in general.

Let's consider that last idea more thoroughly. If Robert considers a preteen equally valuable with 5 grandparents, so that Robert will shift $100,000 from saving 8 old people to saving 2 children, then we can no longer say that Robert wants to save as many 'lives' as possible. That last decision would decrease by 6 the total number of 'lives' saved. So we can no longer say that there's a qualitative criterion, 'Save as many lives as possible', that produces the quantitative coherence requirement, 'trade dollars for lives at a consistent rate'.

Does this mean that coherence might as well go out the window, so far as Robert's behavior is concerned? Anything goes, now? Just spend money wherever?

"Hm," you might think. "But... if Robert trades 8 old people for 2 children _here_... and then trades 1 child for 2 old people _there_..."

To reduce distraction, let's make this problem be about apples and oranges instead. Suppose:

-   Alice starts with 8 apples and 1 orange.
-   Then Alice trades 8 apples for 2 oranges.
-   Then Alice trades away 1 orange for 2 apples.
-   Finally, Alice trades another orange for 3 apples.

Then in this example, Alice is using a strategy that's _strictly dominated_ across all categories of fruit. Alice ends up with 5 apples and one orange, but could've ended with 8 apples and one orange (by not making any trades at all). Regardless of the _relative_ value of apples and oranges, Alice's strategy is doing _qualitatively_ worse than another possible strategy, if apples have any positive value to her at all.

So the fact that Alice can't be viewed as having any coherent relative value for apples and oranges, corresponds to her ending up with qualitatively less of some category of fruit (without any corresponding gains elsewhere).

This remains true if we introduce more kinds of fruit into the problem. Let's say the set of fruits Alice can trade includes {apples, oranges, strawberries, plums}. If we can't look at Alice's trades and make up some relative quantitative values of fruit, such that Alice could be trading consistently with respect to those values, then Alice's trading strategy must have been dominated by some other strategy that would have ended up with strictly more fruit across all categories.

In other words, we need to be able to look at Alice's trades, and say something like:

"Maybe Alice values an orange at 2 apples, a strawberry at 0.1 apples, and a plum at 0.5 apples. That would explain why Alice was willing to trade 4 strawberries for a plum, but not willing to trade 40 strawberries for an orange and an apple."

And if we _can't_ say this, then there must be some way to rearrange Alice's trades and get _strictly more fruit across all categories_ in the sense that, e.g., we end with the same number of plums and apples, but one more orange and two more strawberries. This is a bad thing if Alice _qualitatively_ values fruit from each category—prefers having more fruit to less fruit, ceteris paribus, for each category of fruit.

Now let's shift our attention back to Robert the hospital administrator. _Either_ we can view Robert as consistently assigning some _relative_ value of life for 10-year-olds vs. 70-year-olds, _or_ there must be a way to rearrange Robert's expenditures to save either strictly more 10-year-olds or strictly more 70-year-olds. The same logic applies if we add 50-year-olds to the mix. We must be able to say something like, "Robert is consistently behaving as if a 50-year-old is worth a third of a ten-year-old". If we _can't_ say that, Robert must be behaving in a way that pointlessly discards some saveable lives in some category.

Or perhaps Robert is behaving in a way which implies that 10-year-old girls are worth more than 10-year-old boys. But then the relative values of those subclasses of 10-year-olds need to be viewable as consistent; or else Robert must be qualitatively failing to save one more 10-year-old boy than could've been saved otherwise.

If you can denominate apples in oranges, and price oranges in plums, and trade off plums for strawberries, all at consistent rates... then you might as well take it one step further, and factor out an abstract unit for ease of notation.

Let's call this unit _1 utilon,_ and denote it €1. (As we'll see later, the letters 'EU' are appropriate here.)

If we say that apples are worth €1, oranges are worth €2, and plums are worth €0.5, then this tells us the relative value of apples, oranges, and plums. Conversely, if we _can_ assign consistent relative values to apples, oranges, and plums, then we can factor out an abstract unit at will—for example, by arbitrarily declaring apples to be worth €100 and then calculating everything else's price in apples.

Have we proven by pure logic that all apples have the same utility? Of course not; you can prefer some particular apples to other particular apples. But when you're done saying which things you qualitatively prefer to which other things, if you go around making tradeoffs in a way that can be _viewed as_ not qualitatively leaving behind some things you said you wanted, we can _view you_ as assigning coherent quantitative utilities to everything you want.

And that's one coherence theorem—among others—that can be seen as motivating the concept of _utility_ in decision theory.

Utility isn't a solid thing, a separate thing. We could multiply all the utilities by two, and that would correspond to the same outward behaviors. It's meaningless to ask how much utility you scored at the end of your life, because we could subtract a million or add a million to that quantity while leaving everything else conceptually the same.

You could pick anything you valued—say, the joy of watching a cat chase a laser pointer for 10 seconds—and denominate everything relative to that, without needing any concept of an extra abstract 'utility'. So (just to be extremely clear about this point) we have not proven that there is a separate thing 'utility' that you should be pursuing instead of everything else you wanted in life.

The coherence theorem says nothing about which things to value more than others, or how much to value them relative to other things. It doesn't say whether you should value your happiness more than someone else's happiness, any more than the notion of a consistent preference ordering >P tells us whether onions>Ppineapple.

(The notion that we should assign equal value to all human lives, or equal value to all sentient lives, or equal value to all Quality-Adjusted Life Years, is _utilitarianism._ Which is, sorry about the confusion, a whole 'nother separate different philosophy.)

The conceptual gizmo that maps thingies to utilities—the whatchamacallit that takes in a fruit and spits out a utility—is called a 'utility function'. Again, this isn't a separate thing that's written on a stone tablet. If we multiply a utility function by 9.2, that's conceptually the same utility function because it's consistent with the same set of behaviors.

But in general: If we can sensibly view any agent as doing as well as qualitatively possible at _anything_, we must be able to view the agent's behavior as consistent with there being some coherent relative quantities of wantedness for all the thingies it's trying to optimize.

  

# Probabilities and expected utility ^probabilities-and-expected-utility

We've so far made no mention of _probability._ But the way that probabilities and utilities interact, is where we start to see the full structure of _expected utility_ spotlighted by all the coherence theorems.

The basic notion in expected utility is that some choices present us with uncertain outcomes.

For example, I come to you and say: "Give me 1 apple, and I'll flip a coin; if the coin lands heads, I'll give you 1 orange; if the coin comes up tails, I'll give you 3 plums." Suppose you relatively value fruits as described earlier: 2 apples / orange and 0.5 apples / plum. Then _either_ possible outcome gives you something that's worth more to you than 1 apple. Turning down a so-called 'gamble' like that... why, it'd be a dominated strategy.

In general, the notion of 'expected utility' says that we assign certain quantities called _probabilities_ to each possible outcome. In the example above, we might assign a 'probability' of 0.5 to the coin landing heads (1 orange), and a 'probability' of 0.5 to the coin landing tails (3 plums). Then the total value of the 'gamble' we get by trading away 1 apple is:

P(heads)⋅U(1 orange)+P(tails)⋅U(3 plums)=0.50⋅€2+0.50⋅€1.5=€1.75

Conversely, if we just keep our 1 apple instead of making the trade, this has an expected utility of 1⋅U(1 apple)=€1. So indeed we ought to trade (as the previous reasoning suggested).

"But wait!" you cry. "Where did these probabilities come from? Why is the 'probability' of a fair coin landing heads 0.5 and not, say, −0.2 or 3? Who says we ought to multiply utilities by probabilities in the first place?"

If you're used to approaching this problem from a [Bayesian](https://www.lesswrong.com/w/bayes_rule_guide) standpoint, then you may now be thinking of notions like [prior probability](https://www.lesswrong.com/w/prior_probability) and Occam's Razor and [universal priors](https://www.lesswrong.com/w/universal_prior)...

But from the standpoint of coherence theorems, that's putting the cart before the horse.

From the standpoint of coherence theorems, we don't _start with_ a notion of 'probability'.

Instead we ought to prove something along the lines of: if you're not using qualitatively dominated strategies, then you must _behave as if_ you are multiplying utilities by certain quantitative thingies.

We might then furthermore show that, for non-dominated strategies, these utility-multiplying thingies must be between 0 and 1 rather than say −0.3 or 27.

Having determined what coherence properties these utility-multiplying thingies need to have, we decide to call them 'probabilities'. And _then_—once we know in the first place that we need 'probabilities' in order to not be using dominated strategies—we can start to worry about exactly what the numbers ought to be.

  

## Probabilities summing to 1 ^probabilities-summing-to-1

Here's a taste of the kind of reasoning we might do:

Suppose that—having already accepted some previous proof that non-dominated strategies dealing with uncertain outcomes, must multiply utilities by quantitative thingies—you then say that you are going to assign a probability of 0.6 to the coin coming up heads, and a probability of 0.7 to the coin coming up tails.

If you're already used to the standard notion of probability, you might object, "But those probabilities sum to 1.3 when they ought to sum to 1!"[^note-5] But now we are in coherence-land; we don't ask "Did we violate the standard axioms that all the textbooks use?" but "What rules must non-dominated strategies obey?" _De gustibus non est disputandum;_ can we _disputandum_ somebody saying that a coin has a 60% probability of coming up heads and a 70% probability of coming up tails? (Where these are the only 2 possible outcomes of an uncertain coinflip.)

Well—assuming you've already accepted that we need utility-multiplying thingies—I might then offer you a gamble. How about you give me one apple, and if the coin lands heads, I'll give you 0.8 apples; while if the coin lands tails, I'll give you 0.8 apples.

According to you, the expected utility of this gamble is:

P(heads)⋅U(0.8 apples)+P(tails)⋅U(0.8 apples)=0.6⋅€0.8+0.7⋅€0.8=€1.04.

You've just decided to trade your apple for 0.8 apples, which sure sounds like one of 'em dominated strategies.

And that's why _the thingies you multiply probabilities by_—the thingies that you use to weight uncertain outcomes in your imagination, when you're trying to decide how much you want one branch of an uncertain choice—must sum to 1, whether you call them 'probabilities' or not.

Well... actually we just argued[^note-6] that probabilities for [mutually exclusive](https://www.lesswrong.com/w/exclusive_exhaustive) outcomes should sum to _no more than 1._ What would be an example showing that, for non-dominated strategies, the probabilities for [exhaustive](https://www.lesswrong.com/w/exclusive_exhaustive) outcomes should sum to no less than 1?

:::callout {title="Why exhaustive outcomes should sum to at least 1" collapse="closed"}
Suppose that, in exchange for 1 apple, I credibly offer:

-   To pay you 1.1 apples if a coin comes up heads.
-   To pay you 1.1 apples if a coin comes up tails.
-   To pay you 1.1 apples if anything else happens.

If the probabilities you assign to these three outcomes sum to say 0.9, you will refuse to trade 1 apple for 1.1 apples.

(This is strictly dominated by the strategy of agreeing to trade 1 apple for 1.1 apples.)
:::

  

## Dutch book arguments ^dutch-book-arguments

Another way we could have presented essentially the same argument as above, is as follows:

Suppose you are a market-maker in a prediction market for some event X. When you say that your price for event X is x, you mean that you will sell for $x a ticket which pays $1 if X happens (and pays out nothing otherwise). In fact, you will sell any number of such tickets!

Since you are a market-maker (that is, you are trying to encourage trading in X for whatever reason), you are also willing to _buy_ any number of tickets at the price $x. That is, I can say to you (the market-maker) "I'd like to sign a contract where you give me N⋅$x now, and in return I must pay you $N iff X happens;" and you'll agree. (We can view this as you selling me a negative number of the original kind of ticket.)

Let X and Y denote two events such that _exactly one_ of them must happen; say, X is a coin landing heads and Y is the coin not landing heads.

Now suppose that you, as a market-maker, are motivated to avoid combinations of bets that lead into _certain_ losses for you—not just losses that are merely probable, but combinations of bets such that _every_ possibility leads to a loss.

Then if exactly one of X and Y must happen, your prices x and y must sum to exactly $1. Because:

-   If x+y<$1, I buy both an X-ticket and a Y-ticket and get a guaranteed payout of $1 minus costs of x+y. Since this is a guaranteed profit for me, it is a guaranteed loss for you.
-   If x+y>$1, I sell you both tickets and will at the end pay you $1 after you have already paid me x+y. Again, this is a guaranteed profit for me of x+y−$1>$0.

This is more or less exactly the same argument as in the previous section, with trading apples. Except that: (a) the scenario is more crisp, so it is easier to generalize and scale up much more complicated similar arguments; and (b) it introduces a whole lot of assumptions that people new to expected utility would probably find rather questionable.

"What?" one might cry. "What sort of crazy bookie would buy and sell bets at exactly the same price? Why ought _anyone_ to buy and sell bets at exactly the same price? Who says that I must value a gain of $1 exactly the opposite of a loss of $1? Why should the price that I put on a bet represent my degree of uncertainty about the environment? What does all of this argument about gambling have to do with real life?"

So again, the key idea is not that we are assuming anything about people valuing every real-world dollar the same; nor is it in real life a good idea to offer to buy or sell bets at the same prices.[^note-7] Rather, Dutch book arguments can stand in as shorthand for some longer story in which we only assume that you prefer more apples to less apples.

The Dutch book argument above has to be seen as one more added piece in the company of all the _other_ coherence theorems—for example, the coherence theorems suggesting that you ought to be quantitatively weighing events in your mind in the first place.

  

## Conditional probability ^conditional-probability

With more complicated Dutch book arguments, we can derive more complicated ideas such as 'conditional probability'.

Let's say that we're pricing three kinds of gambles over two events Q and R:

-   A ticket that costs $x, and pays $1 if Q happens.
-   A ticket that doesn't cost anything or pay anything if Q doesn't happen (the ticket price is refunded); and if Q does happen, this ticket costs $y, then pays $1 if R happens.
-   A ticket that costs $z, and pays $1 if Q and R both happen.

Intuitively, the idea of [conditional probability](https://www.lesswrong.com/w/conditional_probability) is that the probability of Q and R both happening, should be equal to the probability of Q happening, times the probability that R happens assuming that Q happens:

P(Q∧R)=P(Q)⋅P(R∣Q)

To exhibit a Dutch book argument for this rule, we want to start from the assumption of a qualitatively non-dominated strategy, and derive the quantitative rule z=x⋅y.

So let's give an example that violates this equation and see if there's a way to make a guaranteed profit. Let's say somebody:

-   Prices at x=$0.60 the first ticket, aka P(Q).
-   Prices at y=$0.70 the second ticket, aka P(R∣Q).
-   Prices at z=$0.20 the third ticket, aka P(Q∧R), which ought to be $0.42 assuming the first two prices.

The first two tickets are priced relatively high, compared to the third ticket which is priced relatively low, suggesting that we ought to sell the first two tickets and buy the third.

Okay, let's ask what happens if we sell 10 of the first ticket, sell 10 of the second ticket, and buy 10 of the third ticket.

-   If Q doesn't happen, we get $6, and pay $2. Net +$4.
-   If Q happens and R doesn't happen, we get $6, pay $10, get $7, and pay $2. Net +$1.
-   If Q happens and R happens, we get $6, pay $10, get $7, pay $10, pay $2, and get $10. Net: +$1.

That is: we can get a guaranteed positive profit over all three possible outcomes.

More generally, let A,B,C be the (potentially negative) amount of each ticket X,Y,Z that is being bought (buying a negative amount is selling). Then the prices x,y,z can be combined into a 'Dutch book' whenever the following three inequalities can be simultaneously true, with at least one inequality strict:

−Ax+0−Cz≧0  
A(1−x)−By−Cz≧0  
A(1−x)+B(1−y)+C(1−z)≧0

For x,y,z∈(0..1) this is impossible exactly iff z=x⋅y. The proof via a bunch of algebra is left as an exercise to the reader.[^note-8]

  

## The Allais Paradox ^the-allais-paradox

By now, you'd probably like to see a glimpse of the sort of argument that shows in the first place that we need expected utility—that a non-dominated strategy for uncertain choice must behave as if multiplying utilities by some kinda utility-multiplying thingies ('probabilities').

As far as I understand it, the real argument you're looking for is [Abraham Wald's complete class theorem](https://projecteuclid.org/download/pdf_1/euclid.aoms/1177730345), which I must confess I don't know how to reduce to a simple demonstration.

But we can catch a glimpse of the general idea from a famous psychology experiment that became known as the Allais Paradox (in slightly adapted form).

Suppose you ask some experimental subjects which of these gambles they would rather play:

-   1A: A certainty of $1,000,000.
-   1B: 90% chance of winning $5,000,000, 10% chance of winning nothing.

Most subjects say they'd prefer 1A to 1B.

Now ask a separate group of subjects which of these gambles they'd prefer:

-   2A: 50% chance of winning $1,000,000; 50% chance of winning $0.
-   2B: 45% chance of winning $5,000,000; 55% chance of winning $0.

In this case, most subjects say they'd prefer gamble 2B.

Note that the $ sign here denotes real dollars, not utilities! A gain of five million dollars isn't, and shouldn't be, worth exactly five times as much to you as a gain of one million dollars. We can use the € symbol to denote the expected utilities that are abstracted from how much you relatively value different outcomes; $ is just money.

So we certainly aren't claiming that the first preference is paradoxical because 1B has an expected dollar value of $4.5 million and 1A has an expected dollar value of $1 million. That would be silly. We care about expected utilities, not expected dollar values, and those two concepts aren't the same at all!

Nonetheless, the combined preferences 1A > 1B and 2A < 2B are not compatible with any coherent utility function. We cannot simultaneously have:

U(gain $1M)>0.9⋅U(gain $5M)+0.1⋅U(gain $0)  
0.5⋅U(gain $0)+0.5⋅U(gain $1M)<0.45⋅U(gain $5M)+0.55⋅U(gain $0)

This was one of the earliest experiments seeming to demonstrate that actual human beings were not expected utility maximizers—a very tame idea nowadays, to be sure, but the _first definite_ demonstration of that was a big deal at the time. Hence the term, "Allais Paradox".

Now, by the general idea behind coherence theorems, since we can't _view this behavior_ as corresponding to expected utilities, we ought to be able to show that it corresponds to a dominated strategy somehow—derive some way in which this behavior corresponds to shooting off your own foot.

In this case, the relevant idea seems non-obvious enough that it doesn't seem reasonable to demand that you think of it on your own; but if you like, you can pause and try to think of it anyway. Otherwise, just continue reading.

---

Again, the gambles are as follows:

-   1A: A certainty of $1,000,000.
-   1B: 90% chance of winning $5,000,000, 10% chance of winning nothing.
-   2A: 50% chance of winning $1,000,000; 50% chance of winning $0.
-   2B: 45% chance of winning $5,000,000; 55% chance of winning $0.

Now observe that Scenario 2 corresponds to a 50% chance of playing Scenario 1, and otherwise getting $0.

This, in fact, is why the combination 1A > 1B; 2A < 2B is incompatible with expected utility. In terms of [one set of axioms](https://en.wikipedia.org/wiki/Von_Neumann%E2%80%93Morgenstern_utility_theorem#The_axioms) frequently used to describe expected utility, it violates the Independence Axiom: if a gamble L is preferred to M (that is, L>M), then we ought to be able to take a constant probability p>0 and another gamble N and have p⋅L+(1−p)⋅N>p⋅M+(1−p)⋅N.

To put it another way, if I flip a coin to decide whether or not to play some entirely different game N, but otherwise let you choose L or M, you ought to make the same choice as if I just ask you whether you prefer L or M. Your preference between L and M should be 'independent' of the possibility that, instead of doing anything whatsoever with L or M, we will do something else instead.

And since this is an axiom of expected utility, any violation of that axiom ought to correspond to a dominated strategy somehow.

In the case of the Allais Paradox, we do the following:

First, I show you a switch that can be set to A or B, currently set to A.

In one minute, I tell you, I will flip a coin. If the coin comes up heads, you will get nothing. If the coin comes up tails, you will play the gamble from Scenario 1.

From your current perspective, that is, we are playing Scenario 2: since the switch is set to A, you have a 50% chance of getting nothing and a 50% chance of getting $1 million.

I ask you if you'd like to pay a penny to throw the switch from A to B. Since you prefer gamble 2B to 2A, and some quite large amounts of money are at stake, you agree to pay the penny. From your perspective, you now have a 55% chance of ending up with nothing and a 45% chance of getting $5M.

I then flip the coin, and luckily for you, it comes up tails.

From your perspective, you are now in Scenario 1B. Having observed the coin and updated on its state, you now think you have a 90% chance of getting $5 million and a 10% chance of getting nothing. By hypothesis, you would prefer a certainty of $1 million.

So I offer you a chance to pay another penny to flip the switch back from B to A. And with so much money at stake, you agree.

I have taken your two cents on the subject.

That is: You paid a penny to flip a switch and then paid another penny to switch it back, and this is dominated by the strategy of just leaving the switch set to A.

And that's at least a glimpse of why, if you're not using dominated strategies, the thing you do with relative utilities is multiply them by probabilities in a consistent way, and prefer the choice that leads to a greater expectation of the variable representing utility.

  

**From the Allais Paradox to real life**

The real-life lesson about what to do when faced with Allais's dilemma might be something like this:

There's _some_ amount that $1 million would improve your life compared to $0.

There's some amount that an additional $4 million would further improve your life after the first $1 million.

You ought to visualize these two improvements as best you can, and decide whether another $4 million can produce at least _one-ninth_ as much improvement, as much true value to you, as the first $1 million.

If it can, you should consistently prefer 1B > 1A; 2B > 2A. And if not, you should consistently prefer 1A > 1B; 2A > 2B.

The standard 'paradoxical' preferences in Allais's experiment are standardly attributed to a certainty effect: people value the _certainty_ of having $1 million, while the difference between a 50% probability and a 55% probability looms less large. (And this ties in to a number of other results about certainty, need for closure, prospect theory, and so on.)

It may sound intuitive, in an Allais-like scenario, to say that you ought to derive some value from being _certain_ about the outcome. In fact this is just the reasoning the experiment shows people to be using, so of course it might sound intuitive. But that does, inescapably, correspond to a kind of thinking that produces dominated strategies.

One possible excuse might be that certainty is valuable if you need to make plans about the future; knowing the exact future lets you make better plans. This is admittedly true and a phenomenon within expected utility, though it applies in a smooth way as confidence increases rather than jumping suddenly around 100%. But in the particular dilemma as described here, you only have 1 minute before the game is played, and no time to make other major life choices dependent on the outcome.

Another possible excuse for certainty bias might be to say: "Well, I value the emotional feeling of certainty."

In real life, we do have emotions that are directly about probabilities, and those little flashes of happiness or sadness are worth something if you care about people being happy or sad. If you say that you value the emotional feeling of being _certain_ of getting $1 million, the freedom from the fear of getting $0, for the minute that the dilemma lasts and you are experiencing the emotion—well, that may just be a fact about what you value, even if it exists outside the expected utility formalism.

And this genuinely does not fit into the expected utility formalism. In an expected utility agent, probabilities are just thingies-you-multiply-utilities-by. If those thingies start generating their own utilities once represented inside the mind of the person who is an object of ethical value, you really are going to get results that are incompatible with the formal decision theory.

However, _not_ being viewable as an expected utility agent does always correspond to employing dominated strategies. You are giving up _something_ in exchange, if you pursue that feeling of certainty. You are potentially losing all the real value you could have gained from another $4 million, if that realized future actually would have gained you more than one-ninth the value of the first $1 million. Is a fleeting emotional sense of certainty over 1 minute, worth _automatically_ discarding the potential $5-million outcome? Even if the correct answer given your values is that you properly ought to take the $1 million, treasuring 1 minute of emotional gratification doesn't seem like the wise reason to do that. The wise reason would be if the first $1 million really was worth that much more than the next $4 million.

The danger of saying, "Oh, well, I attach a lot of utility to that comfortable feeling of certainty, so my choices are coherent after all" is not that it's mathematically improper to value the emotions we feel while we're deciding. Rather, by saying that the _most valuable_ stakes are the emotions you feel during the minute you make the decision, what you're saying is, "I get a huge amount of value by making decisions however humans instinctively make their decisions, and that's much more important than the thing I'm making a decision _about._" This could well be true for something like buying a stuffed animal. If millions of dollars or human lives are at stake, maybe not so much.

  

# Conclusion ^conclusion

The demonstrations we've walked through here aren't the professional-grade coherence theorems as they appear in real math. Those have names like "[Cox's Theorem](https://en.wikipedia.org/wiki/Cox's_theorem)" or "the complete class theorem"; their proofs are difficult; and they say things like "If seeing piece of information A followed by piece of information B leads you into the same epistemic state as seeing piece of information B followed by piece of information A, plus some other assumptions, I can show an isomorphism between those epistemic states and classical probabilities" or "Any decision rule for taking different actions depending on your observations either corresponds to Bayesian updating given some prior, or else is strictly dominated by some Bayesian strategy".

But hopefully you've seen enough concrete demonstrations to get a general idea of what's going on with the actual coherence theorems. We have multiple spotlights all shining on the same core mathematical structure, saying dozens of different variants on, "If you aren't running around in circles or stepping on your own feet or wantonly giving up things you say you want, we can see your behavior as corresponding to this shape. Conversely, if we can't see your behavior as corresponding to this shape, you must be visibly shooting yourself in the foot." Expected utility is the only structure that has this great big family of discovered theorems all saying that. It has a scattering of academic competitors, because academia is academia, but the competitors don't have anything like that mass of spotlights all pointing in the same direction.

So if we need to pick an interim answer for "What kind of quantitative framework should I try to put around my own decision-making, when I'm trying to check if my thoughts make sense?" or "By default and barring special cases, what properties might a sufficiently advanced machine intelligence _look to us_ like it possessed, at least approximately, if we couldn't see it _visibly_ running around in circles?", then there's pretty much one obvious candidate: Probabilities, utility functions, and expected utility.

  

# Further reading ^further-reading

-   To learn more about agents and AI: [Consequentialist cognition](https://www.lesswrong.com/w/consequentialist); [the orthogonality of agents' utility functions and capabilities](https://www.lesswrong.com/w/1y); [epistemic and instrumental efficiency](https://www.lesswrong.com/w/10g); [instrumental strategies sufficiently capable agents tend to converge on](https://www.lesswrong.com/w/instrumental_convergence); [properties of sufficiently advanced agents](https://www.lesswrong.com/w/advanced_agent).
-   To learn more about decision theory: [The controversial counterfactual at the heart of the expected utility formula](https://intelligence.org/2018/10/31/embedded-decisions/).

  

---

  
  

[^note-1]: It could be that somebody's pizza preference is real, but so weak that they wouldn't pay one penny to get the pizza they prefer. In this case, imagine we're talking about some stronger preference instead. Like your willingness to pay at least one penny not to have your house burned down, or something.

[^note-2]: This does assume that the agent prefers to have more money rather than less money. "Ah, but why is it bad if one person has a penny instead of another?" you ask. If we insist on pinning down every point of this sort, then you can also imagine the $0.01 as standing in for the _time_ I burned in order to move the pizza slices around in circles. That time was burned, and nobody else has it now. If I'm an effective agent that goes around pursuing my preferences, I should in general be able to sometimes convert time into other things that I want. In other words, my circular preference can lead me to incur an opportunity cost denominated in the sacrifice of other things I want, and not in a way that benefits anyone else.

[^note-3]: There are more than six possibilities if you think it's possible to be absolutely indifferent between two kinds of pizza.

[^note-4]: We can omit the 'better doctors' item from consideration: The supply of doctors is mostly constrained by regulatory burdens and medical schools rather than the number of people who want to become doctors; so bidding up salaries for doctors doesn't much increase the total number of doctors; so bidding on a talented doctor at one hospital just means some other hospital doesn't get that talented doctor. It's also illegal to pay for livers, but let's ignore that particular issue with the problem setup or pretend that it all takes place in a more sensible country than the United States or Europe.

[^note-5]: Or maybe a [tiny bit less](https://www.lesswrong.com/w/cromwells_rule) than 1, in case the coin lands on its edge or something.

[^note-6]: Nothing we're walking through here is really a coherence theorem _per se_, more like intuitive arguments that a coherence theorem ought to exist. Theorems require proofs, and nothing here is what real mathematicians would consider to be a 'proof'.

[^note-7]: In real life this leads to a problem of 'adversarial selection', where somebody who knows more about the environment than you can decide whether to buy or sell from you. To put it another way, from a [Bayesian](https://www.lesswrong.com/w/bayes_rule_guide) standpoint, if an _intelligent_ counterparty is deciding whether to buy or sell from you a bet on X, the fact that they choose to buy (or sell) should cause you to [update](https://www.lesswrong.com/w/bayes_update) in favor (or against) X actually happening. After all, they wouldn't be taking the bet unless they thought they knew something you didn't!

[^note-8]: The quick but advanced argument would be to say that the left-hand-side must look like a singular matrix, whose determinant must therefore be zero.
