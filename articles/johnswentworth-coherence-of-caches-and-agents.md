---
title: "Coherence of Caches and Agents"
author:
  - "johnswentworth"
source_url: "https://www.lesswrong.com/posts/wjFijaAkSCceqCgGF/coherence-of-caches-and-agents"
published: 2024-04-01
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "There's a lot of confusion about what coherence means for agents, and what \"coherence theorems\" do and don't say about agents. In this post, I'll tal…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

There's a lot of confusion about what coherence means for agents, and what "coherence theorems" do and don't say about agents. In this post, I'll talk about some particularly simple notions of coherence in a particularly simple setting. We'll see what nontrivial things coherence has to say, at least in a simple kind of environment, starting with an analogous notion of coherence for caches.

## What Kind Of "Coherence" We're Talking About Here ^what-kind-of-coherence

Let’s start with a standard CS-101-style example. We write a recursive python function to compute fibonacci numbers:

```
def fib(n):
    if n == 0:
        result = 1
    elif n == 1:
        result = 1
    else:
        result = fib(n-1) + fib(n-2)
    return result
```

We pass in n = 0, then n = 1, then 2, then 3, etc. It spits out 1, 1, 2, 3, 5, 8, .... Great. Buuuuut it gets very slow very quickly as n increases; the runtime is exponential in n.

So, standard simple improvement: memoize. The first time `fib(n)` is computed for each value of n, cache it (i.e. "make a memo" of the result).

```
cache = {}
def memo_fib(n):
    if n in cache:
        return cache[n]
    
    if n == 0:
        result = 1
    elif n == 1:
        result = 1
    else:
        result = memo_fib(n-1) + memo_fib(n-2)
    
    cache[n] = result
    return result
```

Now the recursive calculation will only happen once for each value of n, so runtime is linear in n.

Ok, that's the CS 101 part. Now on to coherence.

Imagine that the cache in our fibonacci program gets corrupted somehow. Maybe I mess around in the debugger and stick a few wrong numbers into it, maybe some other thread writes into it, whatever. Somehow, incorrect values end up in that cache.

Key point: we can notice the cache corruption "locally", i.e. by only looking at a small subset of the cache. Say, for instance, that cache\[6\] is corrupted - it should be 8 (the sixth fibonacci number), but instead let's say it's 11, and let's assume for now that the rest of the cache is fine. So we're looking in the cache, and we see:

-   cache\[4\] = 3
-   cache\[5\] = 5
-   cache\[6\] = 11

Well, just from those three entries we can tell that something's wrong, because 3 + 5 is not 11. It's supposed to be the case that cache\[n\] = cache\[n-1\] + cache\[n-2\] for any n bigger than 1, but that equation is not satisfied by these three cache entries. Our cache must be corrupt. And notice that we did _not_ need to look at the rest of the cache in order to tell; we just needed to look at these three entries. That's what I mean when I say we can notice the cache corruption "locally".

We'll want a word for when that sort of thing _isn't_ happening, i.e. a word which says that cache\[n\] _is_ equal to cache\[n-1\] + cache\[n-2\] (in this particular example). For that, we'll use the word "coherence".

More generally: we'll say that a cache is coherent when small parts of the cache (like cache\[n\], cache\[n-1\], and cache\[n-2\] in this case) all locally satisfy some relationship (like cache\[n\] = cache\[n-1\] + cache\[n-2\]) which they're _supposed_ to satisfy if everything is working correctly.

(Note that our usage here is a lot more general than the most common usage of "coherence" in CS; it's most similar to the use of "coherence" in formal logic. "Coherence" in CS is usually about the more specific case where different threads/processes/servers each have their own caches of the same information which might not match. That's a special case of the more general notion of "coherence" we'll use in this post.)

In the fibonacci example, if the _whole cache_ is coherent, i.e. cache\[n\] = cache\[n-1\] + cache\[n-2\] for every n greater than 1, _and_ cache\[0\] = cache\[1\] = 1, then the whole cache contains the values it's supposed to. In that case, the final cache entry, say e.g. cache\[100\], contains the result of fib(100).

More generally, we're typically interested in "coherence" in cases where all the local constraints together yield some useful property "at the large scale". In logic, that might be a property like [truth-preservation](https://www.lesswrong.com/posts/Z2CuyKtkCmWGQtAEh/proofs-implications-and-models): put true assumptions in, get true conclusions out. In our fibonacci example, the useful "large scale" property is that the cache in fact contains the fibonacci sequence, all the way out to its largest entry. And for agents, the "large scale" property will be that the agents maximize or apply a lot of optimization pressure to something far in their future.

## Value Cache ^value-cache

Moving one step closer to agents, let's talk about an optimization problem, and how to use a cache in order to solve it efficiently.

Here's the problem: at each timestep, I have a whole number between 0 and 99 (inclusive). At each time, I can choose one of the following operations to apply to my number:

-   If the number is divisible by 5, double it, else do nothing.
-   Add 2.
-   Subtract 1.
-   If the number is even, divide by 2, else multiply by 3 and add 1.
-   (Meta-rule for all choices: if the result of the operation would be below 0 or above 99, then the operation does nothing.)

Each number is worth some number of points ("utility") at the end, and I get 10 turns to transform my starting number into the highest-utility number I can. (Whatever intermediate numbers I calculate along the way don't matter for scoring, only the final number.)

We can efficiently solve the problem via memoization or dynamic programming (which, for our current purposes, are the same thing). For each number at each time, we'll calculate the best score we can get starting from that number at that time; that's the "value" of the number at that time. For instance, suppose I get n points if my final number is n, i.e. utility(n) = n. Then the value of 97 in the second-to-last round is 99, since the best I can do is add 2 to end with 99.

We first define the value function recursively (note that I'm using some weird utilities here, not utility(n) = n):

```
utility = {0: 12.8, 1: -3, ..., 99: 16}
T = 10

tentative_operations = [lambda n: (2*n if n%5 == 0 else n),
              lambda n: n+2,
              lambda n: n-1,
              lambda n: (n/2 if n%2 == 0 else 3*n+1)]

def meta_rule(f):
    def new_f(n):
        tentative_result = f(n)
        if n > 99 or n < 0:
            return n
        return tentative_result
    return new_f
operations = [meta_rule(f) for f in tentative_operations]

def value(n, t):
    if t == T:
        result = utility[n]
    else:
        result = max([value(f(n), t+1) for f in operations])
    return result
```

Walking through that code:

-   we define the utility and the four operations (the meta-rule involves a potentially-confusing higher-order function, but that's not very important here so feel free to ignore it)
-   value(n, 10) is the base case of the recursion, it just returns utility\[n\]
-   otherwise, value(n, t) applies each of the four candidate operations to n, gets the value of the resulting new n at the next time, then takes the value from the highest-value operation.

This value function will be exponentially slow with respect to T (not too bad if the game only goes 10 steps, but much worse if we increase that number). By memoizing, we can make the runtime linear with respect to T:

```
cache = {}
def value(n, t):
    if (n, t) in cache:
        return cache[(n, t)]
    
    if t == T:
        result = utility[n]
    else:
        result = max([value(f(n), t+1) for f in operations])
    
    cache[(n, t)] = result
    return result
```

Much like the fibonacci example, we now imagine that the cache might get corrupted somehow - e.g. I might mess with it in the debugger, or some other thread/process might write into it. Then, it makes sense to talk about coherence of the cache.

What would cache coherence mean here, in a similar sense to the fibonacci example? Well, consider five entries of the cache:

-   cache\[(n = 23, t = 5)\]
-   cache\[(n = 23, t = 6)\] (Note that our first operation, applied to 23, yields 23.)
-   cache\[(n = 25, t = 6)\] (Note that our second operation, applied to 23, yields 25.)
-   cache\[(n = 22, t = 6)\] (Note that our third operation, applied to 23, yields 22.)
-   cache\[(n = 70, t = 6)\] (Note that our fourth operation, applied to 23, yields 70.)

Those five entries _should_ satisfy a local constraint:

cache\[(n = 23, t = 5)\] = max(\[cache\[(n = 23, t = 6)\], cache\[(n = 25, t = 6)\], cache\[(n = 22, t = 6)\], cache\[(n = 70, t = 6)\]\])

That constraint says that the entry in cache\[(n = 23, t = 5)\] is in fact the max of the cache entries of each number reachable in the next timestep from 23.

"Coherence" for this cache, in the sense we're using the term, would mean that _all_ such constraints are satisfied throughout the whole cache. As with the fibonacci example, if the whole cache is coherent and end-values match the utilities, then that fully determines all of the values in the cache.

What "large scale" property do we get, if the whole cache is coherent? Well, in that case, each entry (n, t) of the cache tells us the best utility which can be achieved (at the "much later" final time), starting from n at time t. To actually achieve that utility, at each timestep we can look at the values achievable in the next timestep, and choose whichever operation yields the highest value in the next timestep. That policy will then achieve the global best-possible utility over the whole game; that's the "large scale" property here.

### Generalization: Agent's Value Function/Cache ^generalization-agents-value-function

We can generalize the value cache example to other agents which aim to maximize something. The agent has some terminal utility, i.e. the thing it's ultimately trying to optimize. In order to optimize that thing, it's useful to keep around a value function/cache, which represents the instrumental value of various things for achieving the terminal utility.

If we're e.g. using dynamic programming to build a controller, then we'd have a value cache much like the above example. If we're doing Q-learning, then we'd instead train a neural net to calculate the value function. In humans, it seems like we do something qualitatively like Q-learning: over the course of our lives, we learn to attach instrumental value to various things. Though notably, unlike typical Q-learning setups, we humans can also write things directly into our value-functions by talking to or watching other humans - e.g. maybe someone tells me that broccoli is healthy, so my brain reinforces a relatively-high value for broccoli in my learned value-function.

In context, it's pretty clear how the learned value function could end up incoherent: random stuff happens all the time which might reinforce "wrong" instrumental values! Memetics are a prime example of this: lots of potent memes boil down to "spreading the word about X is very good and important". If I hear that, and train it into my value function, then I'll behave to spread the meme - without the meme necessarily being tied to my actual terminal utility. It's like a virus copying itself around in humans' learned value functions.

And if the value function/cache is corrupted, then an agent acting according to those values won't actually maximize its terminal goals, whenever its trajectory runs into the corrupted parts.

### Coherence Is Not Utility-Dependent ^coherence-is-not-utility-dependent

Key thing to notice in our value cache example: the terminal utility function only shows up in the "boundary condition", i.e. the values at the very last timestep. The coherence conditions for the rest of the problem - i.e. the decisions at all _earlier_ timesteps - are _the same_ regardless of the terminal utility function. The values themselves might be different, but they'll all satisfy e.g.

cache\[(n = 23, t = 5)\] = max(\[cache\[(n = 23, t = 6)\], cache\[(n = 25, t = 6)\], cache\[(n = 22, t = 6)\], cache\[(n = 70, t = 6)\]\])

regardless of what the utility is. In other words, the coherence conditions are a property of the _environment_, not the agent's specific goals.

Why is that interesting? Well, suppose we have some system sitting around, and it uses a value function/cache - for instance, maybe we did some Q-learning, and out popped a system which always takes whichever available action gets the highest output from the learned value function. Does that system maximize utility, for _some_ utility function over the end-state? Well, as a necessary condition, we can check whether the values satisfy the coherence conditions (typically called a [Bellman Equation](https://en.wikipedia.org/wiki/Bellman_equation), in this context). If those conditions aren't satisfied, then the system doesn't maximize utility for _any_ utility function over the end-state.

Now, a system which doesn't satisfy the coherence conditions _could_ still maximize some other kind of utility function - e.g. utility over whole trajectories, or some kind of discounted sum of utility at each time-step, rather than utility over end states. But that's not very interesting, in general; any old system can be interpreted as maximizing some utility function over whole trajectories (i.e. the utility function which assigns high score to whatever the system actually does, and low score to everything else). As we said earlier: coherence is interesting mainly when _local_ coherence conditions add up to some cool _large-scale_ property. For agents, the "large-scale property" of interest is maximizing utility over some stuff "far away" - e.g. far in the future, for the examples in this post. In other words, it's long-range planning that's of interest, not short-range planning; long-range planning is where coherence gives nontrivial constraints.

## Coherence of Policies ^coherence-of-policies

Recap of some key points so far:

-   We have a system doing long-range optimization, i.e. optimizing a terminal utility over outcomes some time in the future.
-   To do that efficiently, the system keeps around instrumental values somehow, either in a cache or encoded in a learned function (like e.g. a neural net).
-   The value cache/function has local coherence constraints, independent of the terminal utility. If those constraints aren't satisfied, then the system doesn't maximize utility for _any_ utility function over the outcomes.

This required assuming a lot of structure into our agents: they need to have a value cache/function, which they use in a particular way in order to choose actions. Now it's time to drop that assumption, and instead talk about coherence of a _policy_ - i.e. the function which maps each state-of-the-world the choice the agent makes in that state.

Here's the key question: given some policy, is there _any_ coherent value function which is consistent with that policy? We'll operationalize that two different ways:

-   Operationalization 1: a value function is _consistent with_ a policy iff the policy always chooses the action with highest value according to the value function, and randomizes between highest-value options in case of a tie.
-   Operationalization 2: a value function is _consistent with_ a policy iff the policy never chooses an action with lower value over one with higher value according to the value function.

These two operationalizations differ only in how they handle ties. Under the second operationalization, every policy is consistent with the "trivial value function" which assigns the same value to everything; so to get a nontrivial statement, we need to assume away that case. The first operationalization handles that problem by requiring the policy to randomize in case of ties, so if the policy doesn't randomize then there can't be any ties.

With those in mind, let's look at a policy which is incoherent - i.e. a policy which is not consistent with _any_ coherent value function. We'll use the classic case of circular revealed preferences:

-   Starting with a cookie at time 1, the system always chooses an action which leaves it with a carrot at time 2 over an action which keeps the cookie.
-   Starting with a carrot at time 1, the system always chooses an action which leaves it with a pizza at time 2 over an action which keeps the carrot.
-   Starting with a pizza at time 1, the system always chooses an action which leaves it with a cookie over an action which keeps the pizza.

Now suppose there's some value function consistent with these values, under operationalization 1 (ties must randomize). Then we _must_ have:

-   value(carrot, t=2) > value(cookie, t=2) in order to be consistent with the system's choice when starting with a cookie at time 1
-   value(pizza, t=2) > value(carrot, t=2) in order to be consistent with the system's choice when starting with a carrot at time 1
-   value(cookie, t=2) > value(pizza, t=2)  in order to be consistent with the system's choice when starting with a pizza at time 1

Put all that together, and we get

value(cookie, t=2) > value(pizza, t=2) > value(carrot, t=2) > value(cookie, t=2)

i.e. value(cookie, t=2) > value(cookie, t=2), which is a contradiction. So, under operationalization 1, there is no value function consistent with this policy.

How about operationalization 2? Operationalization 2 works exactly the same way in this case, except the strict inequalities become non-strict:

value(cookie, t=2) **≥** value(pizza, t=2) **≥** value(carrot, t=2) **≥** value(cookie, t=2)

... which implies value(cookie, t=2) = value(pizza, t=2) = value(carrot, t=2), i.e. they all have the same value. Now, in this case there could still be a nontrivial value function consistent with the policy, if there's lots of other stuff which doesn't all have the same value. But the circular preferences forced the value function to be "a little more trivial" - i.e. to assign the same value to at least those three things. If there are _enough_ circular preferences between enough different things, then _all_ the values will be forced to be equal, which is the trivial case.

Key takeaway here: though different operationalizations differ in the details (specifically for indifference), the traditional example of circular preferences indeed rules out all nontrivial value functions, if there's sufficient circularity. So with enough circularity, a policy cannot maximize _any_ nontrivial utility function over final-time outcomes.

## Summary and Takeaways ^summary-and-takeaways

We started with a notion of "coherence" for a cache similar to the concept used in formal logic - i.e. _local_ parts of the cache satisfy some relationships, such that the whole cache globally ends up doing something useful (like e.g. storing values of the fibonacci sequence).

We then applied that notion of coherence for caches to a _value cache_ - i.e. a cache of instrumental values, of the sort computed in dynamic programming. That notion generalizes nicely to _value functions_, e.g. of the sort trained in Q-learning. We noted that the coherence constraints on a value function are independent of the terminal utility function - implying that an agent acting according to an _incoherent_ value function does not maximize _any_ utility function over final-time outcomes. The "over final-time outcomes" was important, though: we also claimed that, insofar as coherence is interesting for agents at all, it's relevant to _long-term_ planning, not short-term planning; any value function can be maximized by some utility function over short-term outcomes.

Finally we moved to discussing coherence of policies, and saw that the classic case of a policy with sufficiently circular revealed preferences is indeed inconsistent with any nontrivial value function, and therefore does not maximize any nontrivial long-term utility function. (Here "trivial" referred to the trivial utility/value function which assigns the same constant value to everything.)

For people who are at least somewhat familiar with coherence, I expect the most important takeaway is that coherence is nontrivial for _long-term_ planning specifically; it's _short-term_ utility maximization which is consistent with e.g. the behavior of a rock.

Lastly, I'll emphasize that we talked about neither probability/nondeterminism, nor approximation. Intuitively, it seems clear that the arguments here should "weaken well", e.g. if the value function or policy isn't _approximately_ coherent in some sense then it won't _approximately_ maximize any utility function. But we didn't actually operationalize any of that.
