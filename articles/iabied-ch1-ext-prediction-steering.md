---
title: "More on Intelligence as Prediction and Steering"
source_url: https://ifanyonebuildsit.com/1/more-on-intelligence-as-prediction-and-steering
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---{++{"author":"Luc's AI","timestamp":1785090665611}@@

%%
Add discussion note here:

...

%%++}
If you ask a wise physicist what an engine is, they might start by pointing at a rocket engine, a combustion engine, and a hamster wheel, and say, "Those are all engines," and then point at a rock and say, "But that is not."

That would be a description by pointing out engines in the world, rather than by trying to give a verbal definition. If you pressed them for a verbal definition, they might tell you that an engine is anything that converts non-mechanical energy into mechanical energy, into motion.

This is less a statement about what an engine *is*, and more a statement about what an engine *does*. All sorts of different things can be engines; the innards of a rocket engine, an electric motor, and hamster muscles have very little in common. There's not much that can be usefully said about all of those innards at once, except that they all convert other kinds of energy into mechanical energy.

We'd say that intelligence is similar. There are many different innards that can give rise to intelligence, including biological innards and mechanical innards. An "intelligence" is anything that does the *work* of intelligence.

We decompose that work into "prediction" and "steering" because this viewpoint is backed up by various formal results.

We'll begin by discussing the sense in which measuring prediction is fairly *objective*. We'll then contrast that with steering, which has a degree of freedom that prediction does not.

#### Same Predictions

It's relatively straightforward to check how good someone is at prediction, at least in cases where the prediction is of the form "I'm going to see X" and then they in fact see X.

We can also grade people's performance when they make *uncertain* predictions. Suppose you think, "I'm pretty sure the sky is blue right now, but it might be grey instead. And it's definitely *not* black." If you look out the window and the sky is in fact blue, you should get more credit than if it's grey, and a lot more than if it's black.

If you were an AI researcher trying to represent those anticipations as numbers on a computer, you might have your baby AI pick numbers to represent how strongly or weakly it expects various things, and then reinforce the AI in proportion to how high a number it gave to the right answer.

That would, of course, quickly go wrong, once the AI learned to assign a value of three octotrigintillion to every possibility.

(At least, it would go wrong in that way if you were training the AI using modern AI methods. For an introduction to those methods, see Chapter 2.)

"Oops," you might say. "The numbers assigned to a mutually exclusive and exhaustive collection of possibilities are supposed to sum to at most 100 percent."

Now when you try again, you'll find that the AI always assigns the value of 100 percent to a single possibility, namely the possibility that it considers to be the most likely.

Why? Well, suppose that the AI thinks the most likely possibility has about an eight in ten chance of happening. Then the strategy of assigning 100 percent to the most likely answer gets 100 percent reinforcement 8/10ths of the time, working out to a reinforcement strength of 0.8 on average.

By contrast, the strategy of assigning 80 percent to the most likely answer and 20 percent to its converse gets 80 percent reinforcement 8/10ths of the time and 20 percent reinforcement 2/10ths of the time. This works out to a reinforcement strength of only 0.64 on average. So the "assigning 100 percent to one answer" strategy gets more reinforcement and wins out.

If you want a reinforcement strategy that makes the AI assign a number like 80 percent to possibilities that happen about 8/10ths of the time, you should score it according to the *logarithm* of the probability it assigns to the truth. There are other possibilities, but taking logarithms is the only one with an additional helpful property: When you're having the AI predict multiple possibilities (like the color of the sky, and the wetness of the ground), then it doesn't matter whether you consider these as one big question (about whether the outside is blue and dry, blue and wet, gray and dry, or gray and wet) or two separate questions (about blue vs. gray, and about dry vs. wet).

AI researchers today do in fact train AIs to make predictions by making them output numbers that we interpret as probabilities, and reinforcing them in proportion to the logarithm of the probability that the AI assigned to the truth. But this isn't just an empirical result about training machines; it's also a theoretical result that was known long before ChatGPT was trained. If you knew that theory, you could have correctly guessed in advance that a good way to train AIs to perform the work of prediction would be to score predictions using logarithms.

You don't need to know this math to evaluate the arguments in *If Anyone Builds It, Everyone Dies.* But these are the sort of principles that are in the background when we talk about "prediction" and "steering."

There's math about how to measure prediction work. The math says that insofar as your anticipations about what's going to happen are helpful, they can be expressed as probabilities — whether you consciously thought of numerical probabilities or not. And it makes for a single unique scoring rule that incentivizes you to report your true probabilities, and that is invariant under decomposition of predictions.

The upshot of all this math is that predictions can be scored *objectively.* When some mind or machine is anticipating the color they'll see when they look out the window, or the next word they'll see while reading a webpage, or the street sign they'll see when driving to the airport, there is (roughly speaking) only one really good way to evaluate how well they're doing.

The point is not that if you're smart, you have to go around muttering numbers about the color of the sky before you look out the window. When you anticipate seeing a blue or grey sky rather than a black sky, something in your brain is acting a little like a probability calculator *somewhere* in there, whether you realize it or not.

Rather, the point is that *all* prediction-like behavior — whether it's an explicit claim, a wordless anticipation, or something else altogether — is subject to an objective scoring rule.

All of this means that when two minds are working with the same starting information, they'll tend to converge on the same predictions as they get better and better at predicting things. Because there's one way to score predictions (by checking them against reality), and there's only one reality being predicted, and minds that are better at predicting will concentrate more and more of their anticipations on the truth, almost by definition.

All of this is starkly unlike the situation with steering, which we'll turn to next.

#### Different Destinations

Two minds that are extremely good at predicting the world are likely to make similar predictions.

In contrast, two minds that are extremely good at *steering through* the world are often *not* going to steer to the same destination.

This distinction is useful for thinking more concretely about intelligence, and it also corresponds to a divide between more straightforward and less straightforward engineering problems in AI.

When you train an AI to predict things, there is a certain sense in which all the best methods of prediction end up producing similar outputs. (That is, assuming the system gets competent at all; the ways of failing are more varied.)

Suppose you train an AI to predict the next frame seen by a webcam pointed out the window at the sky. Almost any model that starts to get sufficiently good at that — at assigning much higher probability, in advance, to what it actually ends up seeing — will predict the sky being clear-blue or cloud-grey or night-dark, but not plaid.

The exact technology you use won't matter much to the final outcome. Any method that works, that gets great scores generally, will end up assigning a similar probability to the blueness of the sky.

Conversely, the job of "steering" has a giant, complicated free parameter: What destination is the system trying to steer toward?

Generals on opposite sides of a war may both be skilled, but that doesn't mean that they are trying to accomplish the same things. Two generals can have similar skills but harness those skills toward very different ends.[\*](#ftnt28)

With the predictive part of an AI system, there is only one thing it looks like to predict very well: assigning high probabilities in advance to what ends up actually being observed. And when a cognitive system looks like it's getting generally stronger at prediction, it's probably getting better at the particular kind of prediction you wanted. There is only one "kind" of prediction to do inside your setup, and a system which succeeds is probably doing it.

If the system is still making a particular prediction mistake, simply throwing more computing power and more data at the system may fix that prediction mistake automatically. You can get the system to do better (at predicting things you care about) *just* by making the system more powerful.

With steering, this is not the case.

We can further shore up this distinction by reviewing the formal literature. Steering — planning, decision-making, obstacle-avoidance, design, etc. — is a topic that has been extensively studied in the sciences. One important mathematical result concerning steering is the [von Neumann-Morgenstern utility theorem](https://en.wikipedia.org/wiki/Von_Neumann%E2%80%93Morgenstern_utility_theorem)[.](https://en.wikipedia.org/wiki/Von_Neumann%E2%80%93Morgenstern_utility_theorem)

[Roughly, this theorem](https://en.wikipedia.org/wiki/Von_Neumann%E2%80%93Morgenstern_utility_theorem) says that any entity pursuing some outcomes over others must *either* be inefficient[†](#ftnt29) *or* be well-described by a collection of probabilistic beliefs and a "utility function" — a function describing how different outcomes trade off against one another. The beliefs, then, can be rated on their accuracy (as described in the previous section), whereas the utility function is a completely free parameter.

Of course, no finite mind can be perfectly efficient. The lesson we take from this theorem (and other results of its kind) is that, insofar as a mind is doing *any* nontrivial task very effectively, it's in some sense (if only implicitly and unconsciously) doing two separate types of work: belief-like work (prediction), and preference-satisfaction-like work (steering).

For instance, consider Aesop's fable of the fox and the grapes. A fox sees some delicious-looking grapes hanging from a vine. The fox leaps for the grapes, but cannot leap high enough, and so abandons them, saying, "Well, they were probably sour anyway."

If we take the fox at his word, the fox's (in)ability to steer to the grapes is *bleeding into* his prediction about whether the grapes are sour. If he sticks with that new prediction, refusing to eat the "sour" grapes out of pride even if he later gets a chance to eat them, then the fox's behavior is *inefficient.*[‡](#ftnt30)He could have done better by keeping a stronger distinction between his predictions (about the sweetness of the grapes) and his steering (his ability to attain the grapes).

Roughly speaking, minds that work well can be separated into *what they predict* and *what they're steering toward* (plus some inefficiencies). And as we've seen, the former can be scored relatively objectively — whereas the latter can vary wildly between similarly competent minds.

#### Impure Predictors

Unfortunately, the fact that prediction is more constrained than steering doesn't mean we can build a trustworthy superintelligence that only predicts and doesn't steer.

Although the math says that a well-functioning mind can more or less be modeled as "probabilistic predictions plus a direction of steering," this doesn't mean that real-world AIs have cleanly separated "prediction" and "steering" modules.

One way to see why this is: Superhumanly good "prediction" isn't just a matter of spitting out probabilities and having those probabilities magically be good. Good prediction takes *work*. It takes planning, and thinking up ways to achieve longer-term goals — that is, it takes *steering*.

If you're trying to predict the physical world, you sometimes need to develop theories of physics and discover the equations that govern that part of the physical world. And to do that, you'll often need to design experiments, carry out those experiments, and observe the results.

And doing *that* requires planning; it requires steering. If you get partway through building your experimental apparatus and realize that you're going to need stronger magnets, then you'll have to take some initiative and change course midway. Good predictions don't come free.

Even *choosing which sorts of thoughts to think* *and in what order* is an example of steering (even if it's steering that humans often do unconsciously), because it requires some level of strategy and choosing the right tools for the task at hand. To think clearly, and thereby do better at predicting things, you need to organize your thoughts and actions around various longer-term goals. (We will return to the topic of steering's central role in Chapter 3, "Learning to Want.")

The mathematical distinction between prediction and steering is that there's roughly one "correct" set of predictions that a mind can be pushed toward using proper scoring, but there's no (objectively, agent-neutrally) "correct" steering destination.[§](#ftnt31) As an AI is trained to be more generically capable, its predictions get more accurate, but its steering doesn't automatically get more aimed at the destination humans think is good — because accuracy is objective, whereas "goodness" is a steering target.

Accuracy converges; steering does not.

*In principle*, there should be ways to ensure that an AI is steering toward the destinations we want. *In practice*, this is hard, in large part because it's such a *different* challenge from "generically make the AI smarter and more capable," and there isn't a (simple, non-gameable) metric or scoring rule we can use to grade "To what extent is this AI trying to steer toward the destination we want?"

We'll discuss these topics more in Chapters 4 and 5.

#### Intelligence's Many Shapes

Something can be good at prediction and steering without having all that much in common with a human brain.

The stock market performs the work of prediction in the narrow domain of short-term corporate stock prices. The stock price of Microsoft today is a pretty decent indicator of what the stock price will be tomorrow.[¶](#ftnt32)

Suppose there's an earnings call tomorrow, where company executives report on how well things have gone over the last quarter-year. Is the stock price high today? That suggests tomorrow's reports will be rosy. Is it low today? That suggests tomorrow's reports will be dour.

The markets are pretty accurate in this regard, because people can get rich by correcting them wherever they're wrong. So markets do a decent job at performing the work of prediction in this narrow domain. They predict the movements of short-term corporate stock prices (and, indirectly, things like crop yields and vehicle sales) across a very wide range of goods and services, far better than any individual human can.

Some humans can predict *individual* price movements better than the entire rest of the stock market, in ways that make them very rich. For instance, Warren Buffett made twelve billion dollars in six years by investing in Bank of America when it was reeling from the 2011 financial crisis. But even then, he was predicting only one company among a huge number of companies. Someone who knew substantially better than the stock market *most* of the time would be able to make a stupendous amount of money stupendously quickly. The fact that nobody does this lets us infer that pretty much nobody knows much better than the market about most stock prices.[‖](#ftnt34)

As for steering, the chess-playing AI called Stockfish performs this sort of work in the narrow domain of chess. When it plays a game of chess against a human, it is very adept at producing chess moves that steer the world into states where Stockfish's pieces have checkmated the opponent's king. No matter what clever moves the human comes up with, or how they struggle (short of turning Stockfish off), Stockfish funnels reality toward that singular end. It steers chessboards better than any individual human can.

You can hopefully see, now, why we don't try to define intelligence by saying, "Well, there must be some learning module, and some deliberation module, and some gears that implement a spark of desire," or anything like that. There really isn't much in common between the internals of the stock market and the internals of Stockfish and the internals of a human brain, any more than there's much in common between the innards of a rocket engine, an electric motor, and a hamster wheel.

An intelligent device is anything that does intelligence's work.

At least, that's true given how we define "intelligence" in the book (and given how computer scientists and AI researchers typically think about "intelligence"). If you'd like to define intelligence differently in other contexts, we have no problem with that. Words are just words.

But to make sense of the substantive claims we're making about the world in *If Anyone Builds It, Everyone Dies*, when you hear us talk about "artificial intelligence," don't think "artificial book smarts" or "artificial consciousness"[#](#ftnt35) or "artificial human-ishness." Think "artificial prediction and steering."

[\*](#ftnt28_ref) Or, to put it another way: Suppose that Alice likes pepperoni pizza and hates pineapple, while Bob likes pineapple and dislikes pepperoni. To fully evaluate how competent Alice and Bob are, you'd need to know what they were steering toward. For Alice, ending up with pineapple pizza is a sign that she *screwed up*; for Bob, ending up with pineapple is a sign that he steered *well*.

[†](#ftnt29_ref) For a technical definition of "inefficient." Very roughly, the idea is that you pursued your goals "inefficiently" if you spent money for nothing, or passed up an opportunity for free money, where "money" can stand in for any resource, or any quantifiable difference in how much you care about different outcomes. There is a little wiggle room in the formal definitions, but it doesn't undermine the key point that steering has a degree of freedom that prediction lacks.

[‡](#ftnt30_ref) E.g., perhaps the fox later gets a chance to cheaply purchase the grapes by paying a rabbit who can jump high enough to reach the grapes. If the fox leaps for the grapes (costing energy), then decides they're "sour," then refuses to pay a pittance for the grapes, then the fox's behavior over time isn't represented by a (simple, time-independent) utility function. If the fox consistently wanted the grapes, then it should have been willing to pay (at least if the rabbit's labor is cheap enough). If the fox *didn't* consistently want the grapes, then it shouldn't have wasted time and energy jumping to try to snatch them in the first place. So the fox either wasted energy or missed out on grapes, and either way, the fox wasn't efficiently steering toward its goals.

[§](#ftnt31_ref) There are perhaps objectively good steering *strategies*.Just because steering has a crucial free parameter ("Where are you trying to go?") doesn't mean that the *other* aspects of skilled steering are all heterogeneous and agent-specific. It's possible to teach someone how to drive a car no matter where they're hoping to drive. But that one free parameter of steering-destination is enough to make superintelligence a lethally dangerous research goal, as we'll see in the chapters to come.

[¶](#ftnt32_ref) This doesn't mean that we should expect the stock price to stay *unchanged*. It just means that we should be uncertain about the *direction* of the change: Today's stock prices are the *least bad guesses available* about what tomorrow's stock prices will look like, because the possibility that they'll go up is balanced out by the possibility that they'll go down instead.

(This also doesn't contradict the observation that on most days, the stock market goes up rather than down. That effect could be explained by there being a high probability of the price rising tomorrow by a bit, and this is balanced by a low probability that it will instead fall by a larger amount. And, in real life, there's also a number of other effects in play, like monetary inflation, which means that the value of the dollar drops a little each day, making the value of stocks go up a little in dollar terms.)

[‖](#ftnt34_ref) For more discussion of markets and intelligence, see the extended discussion "[Appreciating the Power of Intelligence](/1/appreciating-the-power-of-intelligence)."

[#](#ftnt35_ref) We'll have more to say about machine consciousness [later](/5/effectiveness-consciousness-and-ai-welfare), after Chapter 5.

#### Notes

[1] *how to measure prediction work:* For a technical account of the math and why it works, see Yudkowsky's [Technical Explanation of Technical Explanation](https://www.lesswrong.com/posts/afmj8TKAqH6F2QMfZ/a-technical-explanation-of-technical-explanation).

[2] *twelve billion dollars:* As [recounted](https://www.cbsnews.com/news/warren-buffett-bank-of-america-12-billion/) by Larry Light of CBS News.