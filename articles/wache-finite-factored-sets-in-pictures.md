---
title: "Finite Factored Sets in Pictures"
author:
  - "Magdalena Wache"
source_url: "https://www.lesswrong.com/posts/PfcQguFpT8CDHcozj/finite-factored-sets-in-pictures-6"
published: 2022-12-11
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Finite factored sets are a new paradigm for talking about causality. You can use them to do some cool things you can’t do with Pearl’s causal graphs,…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

[Finite factored sets](https://www.lesswrong.com/posts/N5Jm6Nj4HkNKySA5Z/finite-factored-sets) are a new paradigm for talking about causality. You can use them to do some cool things you can’t do with Pearl’s [causal graphs](https://en.wikipedia.org/wiki/Causal_graph), for example [inferring a causal arrow between two binary variables](https://www.lesswrong.com/posts/N5Jm6Nj4HkNKySA5Z/finite-factored-sets#2e__Two_Binary_Variables__Pearl_). 

Also, finite factored sets are a really neat mathematical structure: they are a way of taking a **set** and expressing it as a _product of some factors._ Set factorizations are analogous to [integer factorizations](https://en.wikipedia.org/wiki/Integer_factorization), in the same way that [set partitions](https://en.wikipedia.org/wiki/Partition_of_a_set) are analogous to [integer partitions](https://en.wikipedia.org/wiki/Partition_\(number_theory\)). 

So, here is my current understanding of finite factored sets, in pictures.

## 1\. What are Set Factorizations? ^1-what-are-set

What do these “factored sets” look like? Let’s start with a set S and factor it. 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/mqyyy3nrpt9caxpugxo8)

The first concept we need is a [partition](https://en.wikipedia.org/wiki/Partition_of_a_set) of a set S. A partition is a way of chopping up S into subsets (called _parts_). Here are a few examples of partitions:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/gncsz79amkuwjhx3eia9)

We usually call the partitions $X, Y, Z, U, V,$  or $W$, and their parts $x_i, y_i, …$ like this:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/xcdvdtrctopzaqbzizvu)

U is called the _trivial partition_. It only has one part.

We can think of **partitions as properties, or variables** over our set. For example, consider a set like this:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/afadhqqd6y0imjsmkou5)

and compare it to the partitions $X, Y$ and $Z$ from above:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/jixage9ysddnu0yw2cvv)

Then 

-   The partition $X$ is the property “color”, with $x_1$ = blue and $x_2$ = orange. 
-   The partition Y is the property “form” with $y_1$ = square, and $y_2$ = circle.
-   The partition Z is the property “filled” with $z_1$ = yes, and $z_2$ = no.

Exercise

Consider these two partitions X and Y on the set S. What would it look like to represent them as properties (e.g. X = shape, Y = color) instead?

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/uma0xebxvbcm9tau7wv8)

:::callout {title="Spoiler" collapse="closed"}

  
  
  
  
  
 

It could look something like this:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/gox2hbxpscng0vshbpzs)

Here $X$ = shape = $\{x_1, x_2, x_3\}$ = {star, circle, square}, and $Y$ = color =$\{y_1, y_2\}$ = {green, orange}.
:::

I hope you can see how partitions and properties are basically the same thing. In the rest of this post, I will use “partitions” and “properties” interchangeably. Sometimes I will use the ring-style visualization of partitions, and sometimes the property style, depending on what I find more intuitive in any given example. 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/mbsrhpywygrz9mokdjeo)

Now we can define **set factorizations**:

A **factorization** B of our set S looks like this: 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/k6w6opilgowwscuxwv8g)

  
A factorization is a set $B = \{b_1, b_2, …, b_n\}$ of partitions (called _factors_). In this case $B =  \{b_1, b_2\} = \{X, Y\} = \{\{x_1, x_2\}, \{y_1, y_2\}\}$.

But it can’t just be _any_ set of partitions. In the following sections, I will explain the two conditions that B needs to fulfill in order to count as a factorization:  

1.  There is a unique element for all combinations of properties
2.  No factor is trivial

### 1\. There is a unique element for all combinations of properties ^1-there-is-a

Let’s look at our partitions in terms of properties again: 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/zfiftmo9lojfhrnehscq)

What we need in order for B to be a factorization, is that for all combinations$(x_i, y_j)$ of properties (for example $(x_1, y_2)$, which is (blue, circle)), there is a unique element with these properties. 

We can see that this is the case here: We have exactly one blue square, exactly one orange square, exactly one blue circle, and exactly one orange circle. 

To express it more mathematically: For $B = \{X_1, X_2, …, X_n\}$ to be a factorization, we need that for all $x_1 \in X_1, x_2 \in X_2, … x_n \in X_n$, it holds that the intersection of $\{x_1, x_2, …, x_n\}$ contains exactly one element. This means the [cartesian product](https://en.wikipedia.org/wiki/Cartesian_product) of our factors is [bijective](https://en.wikipedia.org/wiki/Bijection) to the set S, which justifies that we say we can “express S as the _product_ of our factors”. 

### 2\. No factor is trivial ^2-no-factor-is

Here is an example of a non-factorization:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/k6wmofo3w5dq36h4tftk)

B = {U, V} is not a factorization here, because U is trivial and factors aren’t allowed to be trivial.

This is analogous to integer factorization, where we don’t count 1 as a factor. For example, for the integer 6 we say the factorizations are {6} and {2,3}, and don’t mention {6,1} and {6,1,1} and {6,1,1,1} and so on. 

### Exercise ^exercise

What about this? Is B = {X, Y} a factorization here? (take a moment to think for yourself)

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/uma0xebxvbcm9tau7wv8)

  
:::callout {title="Spoiler" collapse="closed"}
  
  
  
  
  
  
  
  
  
… No. B is not a factorization.

Why not? Let’s look at it in terms of properties again:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/hyaidr4jbyugzhmd2bjy)

We can see that there is not a unique element for every combination of properties. For example, there is no orange star, and also no orange circle (i.e. $x_1 \cap y_2$ and $x_2\cap y_2$ are empty).
:::
 

What about this one? Is B = {V} a factorization?

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/mlfgyofxeeayhhrw7php)

:::callout {title="Spoiler" collapse="closed"}
  
  
 

  
  
  
  
  
  
 

… yes it is. This one is called _trivial factorization_. Each set can be factorized as $B = \{b_1\}$ with $b_1$ being the maximally separating partition.
:::

If you play around a bit with sets of different sizes, you will see that the possible set factorizations correspond to the integer factorizations of the set’s size [^note-factorization-count]:  
 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/zpwtnogydzwyjr51bghq)

In particular, sets with a prime number of elements only have the trivial factorization.

This concludes the examples for factorizations. Hopefully you now have some grasp on how factoring a set works. 

If we have a tuple F = (S, B) of a set S and a factorization B of S, then we call F a **factored set**. In this post I will assume that all sets are finite, and use “factored set” synonymously with “finite factored set”  

## 2\. What does this have to do with Causality?  - The Building Blocks ^2-what-does-this

In this section, I will introduce three building blocks: three structures on factored sets, that will help us make the connection to causality later. 

In section 3, I will then use these building blocks to model the causal structure behind a probability distribution with factored sets, similar to causal graphs. 

The three building blocks are:

1.  The **history** of a partition X is related to a [random variable](https://en.wikipedia.org/wiki/Random_variable)’s set of **ancestors** in a causal graph
2.  **Orthogonality** of two partitions X, Y means they have no shared history. In the Pearl-paradigm we know that two variables X and Y have no common ancestors if and only if they are independent. Analogously, Scott Garrabrant proved that in the factored set paradigm, two variables are **orthogonal if and only if they are independent**. [^note-orthogonality-independence]
    -   **Conditional orthogonality** of two partitions: In the Pearl-paradigm we know that two variables X and Y are [d-separated](https://en.wikipedia.org/wiki/Bayesian_network#d-separation)  if and only if they are [conditionally independent](https://en.wikipedia.org/wiki/Conditional_independence) (proof [here](https://arxiv.org/pdf/1304.2379.pdf) and [here](https://arxiv.org/pdf/1302.4973.pdf)). Analogously, Scott proved that in the factored set paradigm, two variables are conditionally orthogonal if and only if they are conditionally independent. [^note-orthogonality-independence]
3.  **"Time"**: Saying a partition A is _before_ B is related to a **causal path** going from A to B in a causal graph.

### History ^history

Consider an 8-element set S, which is factorized into the factors “color”, “shape” and “fill”, like this: 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/uiz0zgslzge6ajwcddtm)

Here, the factored set F is  F = (S, B) with the factorization B = {color, shape, fill}. 

Now, let’s consider a partition/property A - which does not need to be a factor! (i.e. A does not have to be color, shape or fill here):

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/kbjqojqlbmlnj6pvciod)

  
Now assume we know some properties of an element s, and want to figure out if it is in $a_1$ or in $a_2$. The fill doesn’t matter for this, so the minimum required properties for finding out are {color, shape}. 

If we know that the color is blue, then the color would be enough to determine that we are in $a_2$, but in order to _reliably_ find out if we are in $a_2$, we need both color and shape. 

This is what we will call the **history** of A: We say that in a factored set F, the history $h^F(A)$ of a property A is the set of properties we need in order to figure out A.

Once we build up factored sets as a model for a causal structure, the history of a partition A will correspond to the set of ancestors of a random variable in a causal graph. 

_Note that I represent A as these red rings, and {color, shape, fill} as properties. I could just as well represent A as a property too (e.g. different sizes), but I prefer this representation because it distinguishes the factors in our factorization {color, shape, fill} from the variable A whose history we want to find._

Exercise

The history $h^F(A)$ of a property A is the set of properties we need in order to figure out A. So, what is the $h^F(A)$ here? 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/o1zqknmlffkv7qilla8o)

:::callout {title="Spoiler" collapse="closed"}
  
  
  
  
  
  
  
  
  
  
  
  
 

$h^F(A)$ = {color}

You only need to know the color in order to tell if an element is in $a_1$ or in $a_2$.

:::

Notice that in this case, A = color. So $h^F(A)$ = {color} is the same as $h^F$(color) = {color}. Which is basically just saying that you just need to know the color in order to find out the color. In general, for every factor b in our factorization, it holds that $h^F(b) = \{b\}.$

Another exercise: What if A is the trivial partition? What is $h^F(A)$ here?

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/bkapa0hennwwubmxb3m4)

:::callout {title="Spoiler" collapse="closed"}
  
  
  
  
  
  
  
  
  
  
  
  
  
Here, the history is empty! ($h^F(A) = \emptyset$) We don’t need to know any properties, because we _already_ _know_ that every $s$ is in $a_1$.

:::

### Orthogonality ^orthogonality

Now we have defined history, we can define **orthogonality**, which is closely related to independence of random variables! 

We say that two partitions A, B are _orthogonal_, if their **histories don’t overlap**.

Exercise

Are A and B orthogonal here? 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/pdb3r6pmutdyjq81s4pc)

:::callout {title="Spoiler" collapse="closed"}
  
  
  
  
  
  
  
  
  
  
  
 

No. The history of A is $h^F(A)$ = {color, shape}. The history of B is $h^F(B)$ = {color, fill}, so the histories overlap.
:::

In the Pearl-paradigm we know that two variables X and Y have no common ancestors if and only if they are independent. Analogously, Scott Garrabrant proved that when we use a factored set to model causal structure (I’ll explain how to do that in section 3), then two variables are **orthogonal if and only if they are independent**. [^note-orthogonality-independence]

Note that in any factorization, the factors are all orthogonal to each other, because $h^F(b)$ ={b} for any factor b (we only need color to infer color, remember) so $h^F(b_1)\cap h^F(b_2) = \emptyset$ if $b_1 \ne b_2$. 

Scott also defines **conditional orthogonality** as an analog of [d-separation](https://en.wikipedia.org/wiki/Bayesian_network#d-separation). I won’t define conditional orthogonality here in order to keep things simple, but you can find the definition [here](https://www.lesswrong.com/posts/N5Jm6Nj4HkNKySA5Z/finite-factored-sets#2b__Conditional_Orthogonality). 

In the Pearl-paradigm there is a theorem called **soundness and completeness of d-separation**: Two variables X and Y are d-separated with regard to a set of variables Z if and only if X and Y are [conditionally independent](https://en.wikipedia.org/wiki/Conditional_independence) given Z (proof [here](https://arxiv.org/pdf/1304.2379.pdf) and [here](https://arxiv.org/pdf/1302.4973.pdf)) 

[Scott’s central result](https://www.lesswrong.com/posts/N5Jm6Nj4HkNKySA5Z/finite-factored-sets#2b__The_Fundamental_Theorem) is the analog of this theorem in the factored set paradigm: 

Two variables X, Y are conditionally orthogonal with regard to a set of variables Z if and only if X and Y are conditionally independent given Z. (Technically it’s slightly more complicated, but this is the gist [^note-orthogonality-independence])

### "Time" ^time

-   We say that a partition A is **weakly before** B if A's history of A is a _subset or equal_ to B's history (i.e.  $h^F(A) \subseteq h^F(B)$ ). 
-   We say that A is **strictly before** B if  A's history is a _strict subset_ of B's history (i.e. $h^F(A) \subsetneq h^F(B)$). 

This notion of “time” is closely related to the concept of a causal arrow going from A to B in a causal graph. 

You can imagine A's history like "everything that comes before A in time", so if everything that’s in A’s history is also in B’s history then A is before B:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/jxuxvhgumj78gsgxbh02)

Exercise

Is A or B weakly or strictly before the other here? (i.e. is one of the histories of A or B a subset of the other? Reminder: history = set of properties needed to infer our partition) 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/vtq7rexzxtc5hpingujf)

:::callout {title="Spoiler" collapse="closed"}
 

  
  
  
  
  
  
  
  
  
  
  
  
 

A is strictly before B! $h^F(A)$ = {color, shape} and $h^F(B)$ = {color, shape, fill}, so $h^F(A) \subsetneq h^F(B)$.

:::

Now we have the building blocks to use factored sets for causal inference! 

## 3\. Causal Inference using Factored Sets ^3-causal-inference-using

In this section I will walk through an example of inferring causality from data using factored sets.

Consider an experiment in which we collect 2 bits. The distribution P looks like this: 

P(00) = 1%  
P(01) = 9%  
P(10) = 81%  
P(11) = 9%

Let’s say X is the first bit, and Y is the second bit.

In the causal graph paradigm, we would observe that X and Y are dependent ($P(X=0) = 10\% \ne P(X=0|Y=0) = \frac{1}{82}$). Thus we are not able to distinguish between these three causal graphs:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/sloqkt69tek0bgdj2nwz)

We don’t know whether X causes Y, Y causes X, or there is some common factor W that causes both. 

### How do we look at this in the Factored Set Paradigm? ^how-do-we-look

In the factored set paradigm, start with the sample space $\Omega$ of our distribution P:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/m71ivarbutjsz0bstf8d)

We then say a **model** of the distribution is a factored set F = (S, B) and a function $f: S\to \Omega$:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/rlwiiitdnnbbksoc0uku)

$X_S$ and $Y_S$ are the “preimages” of X and Y under f. By that I mean that all their parts $x_{Si}$ and $y_{Sj}$ are the [preimages](https://en.wikipedia.org/wiki/Image_\(mathematics\)#Inverse_image) of $x_i$ and $y_j$ respectively, under f. That looks as follows: 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/mw5dlfusalsuayfl6hsf)

(Note that in this case f is [bijective](https://en.wikipedia.org/wiki/Bijection), but in general f does not have to be bijective. If we allow f to be non-bijective, then the framework works in more generality because we can describe some processes that we couldn’t otherwise describe. [^note-non-bijective-preimages])

However, we can’t just use _any_ factorization B. In order for (F, f) to count as a **model** of our distribution P, it needs to be such that the _dependencies and independencies of our distribution are represented in the factorization_.

That means: 

-   Two variables X and Y are [independent](https://en.wikipedia.org/wiki/Independence_\(probability_theory\)) in P if and only if $X_S$ and $Y_S$ are **orthogonal** in F (i.e. their histories don’t overlap)
-   Two variables X and Y are **dependent** in P if and only if $X_S$ and $Y_S$ are **not orthogonal** in F 

Remember, our probability distribution P was

P(00) = 1%  
P(01) = 9%  
P(10) = 81%  
P(11) = 9%

Is the following actually a model of P?

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/jgv6c6b9u85t4g1xp7od)

No, it is not: X, and Y are **dependent** in P, but $X_S$ and $Y_S$ are **orthogonal** in F! (Note that orthogonality depends on what model we are in/what factorization we use.) 

Here is a really tricky one: Is this a model of P?

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/ccolrbckahix8r6rs2ub)

Also no, but this is hard to see, so let’s walk through it.

Consider the variable Z = X XOR Y

We don’t _have to_ express our distribution in terms of X and Y, we can just as well define it in terms of X and Z. And then it looks like this: 

P(00) = P(X=0, Z=0) = 1%  
P(01) = P(X=0, Z=1) = 9%  
P(10) = P(X=1, Z=1) = 81%  
P(11) = P(X=1, Z=0) = 9%

We can see that **Z and X are independent**! (because$P(Z=0) = 1\% + 9 \% =10\%$, and also$P(Z=0|X=0) = \frac{1\%}{9\%+1\%} = 10\%$ , and$P(Z=0|X=1) = \frac{9\%}{81\%+9\%} =10\%$)  
 

What does this mean for our model? It means that $Z_S$ and $X_S$ need to be orthogonal. 

Are $Z_S$ and $X_S$ orthogonal in our model? Here it is again:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/iaqkdeyvwrj0bkxelauy)

  
 No, because the history for both $X_S$ and $Z_S$ is {V}, so  $X_S$ and $Z_S$ have an overlapping history. 

So F = (S, {$V_S$}) is also not a model of P.

Does our distribution P have a model at all?   
Yes - here is a model that actually works for P:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/rat2qyaihoktvrqd27nf)

Here $h^F(X_S) = \{X_S\}$ and $h^F(Z_S)$ = {$Z_S$}, and $h^F(Y_S)$ = {$X_S, Z_S$}. 

This means $X_S$ and $Z_S$ are _orthogonal_, which matches our observation that X and Z are _independent_ in P. Also $X_S$ and $Y_S$ are _not orthogonal_, which matches our observation that X and Y are _dependent_ in P.

It also means that $h^F(X_S) \subsetneq h^F(Y_S)$, so $X_S$ is strictly before $Y_S$.

If $X_S$ is strictly before $Y_S$, then the causal arrow goes from X to Y, so we have found a causal direction! It’s this one:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/knddneiqamvkypbzdn8e)

From what we know so far, this causal direction $X \to Y$ only holds for this particular model (F, f), but in fact, [you can also prove](https://www.lesswrong.com/posts/N5Jm6Nj4HkNKySA5Z/finite-factored-sets#2e__Two_Binary_Variables__Pearl_) that $X \to Y$ holds for _any_ model of this distribution P.

So, we just inferred causality from [observational](https://en.wikipedia.org/wiki/Observational_study) (as opposed to [interventional](https://en.wikipedia.org/wiki/Causal_model#Intervention)) data, in a way that Pearl’s causal models wouldn’t have inferred! 

### Sanity-checking the result in Pearl’s paradigm ^sanity-checking-the-result-in

I have encountered a lot of skepticism that we can infer the causality $X \to Y$ here. So I’m going to switch back to the Pearl paradigm, and explain why X causes Y if our distribution is P, and we can actually infer that from only observational data without needing interventional data.

_This section will assume you know how to determine (in-)dependence in probability distributions and in causal graphs. (If you don’t, you can either just believe me, or learn about it_ [_here_](https://en.wikipedia.org/wiki/Independence_\(probability_theory\)) _and_ [_here_](https://en.wikipedia.org/wiki/Bayesian_network#d-separation)_)._ 

Again, say X is the first bit, Y is the second bit, and Z = X XOR Y. Here is our distribution again, in table-form:  
 

| X | Y | Z | P(X, Y, Z) |
| --- | --- | --- | --- |
| 0 | 0 | 0 | 1% |
| 0 | 1 | 1 | 9% |
| 1 | 0 | 1 | 81% |
| 1 | 1 | 0 | 9% |
| Any other combination of X, Y, and Z | 0% |  |  |

  
The (in-)dependencies we can read from this are:

-   X and Y are **dependent**
-   X and Z are **independent**
-   Y and Z are **dependent**

The possible causal graphs which fulfill these dependencies and independencies are these four:  
 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/ufvqevo3fudzdgnriy67)

  
So, we know that Y does not cause X! This matches our finite factored set finding that X causes Y, but it's weaker. Can we also infer that X causes Y?

Let’s concretize the above graphs by adding the conditional probabilities. Graph 1 then looks like this:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/xe7lkhsrywpchxhrnhsb)

Graph 2 is somewhat trickier, because W is not uniquely determined. But one possibility is like this:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/yzrseifzp80vjkhra34c)

Note that W is just the negation of Z here ($W= \neg Z$). Thus, W and Z are information equivalent, and that means graph 2 is actually just graph 1.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/mxprbaafnesmrzbcsgt0)  
 

Can we find a different variable W such that graph 2 does _not_ reduce to graph 1? I.e. can we find a variable W such that Z is not deterministic given W?

No, we can’t. To see that, consider the distribution $P(Z|X,Y,W)$. By definition of Z, we know that 

$P(Z|X,Y,W) = \begin{cases} 1 \quad \text{if } Z = X \text{ XOR } Y,\\ 0 \quad \text{otherwise.}  \end{cases}$.

  
In other words, $P(Z|X,Y,W)$ is deterministic.

We also know that W d-separates Z from X,Y in graph 2:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/ptwfh2l5yxq5tqgrh9cj)

This d-separation implies that Z is independent from X, Z given W:

$P(Z|W) = P(Z|W,X,Y)$

As $P(Z|X,Y,W)$ is deterministic, $P(Z|W)$ also has to be deterministic.

So, graph 2 always reduces to graph 1, no matter how we choose W. Analogously, graph 3 and graph 4 also reduce to graph 1, and we know that our causal structure is graph 1:

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/d7k29ldlzzt6e91g9u5m)

Which means we also know that X causes Y.

The reason why we usually wouldn’t have found this causal direction using causal graphs is that we _wouldn’t even have considered_ Z as potentially interesting. This is what factored sets give us: They make us consider every possible way of defining variables, so we **don’t miss out on any information** that may be hidden if we just look at a predetermined set of variables.

## Summary ^summary

Set factorizations are a way of expressing sets as a **product of some factors**, similar to how integer factorization is about expressing integers as a product of some factors.

We can define a **history** on them, that tells us which properties came “before” other properties. We say that two variables are **orthogonal** if they have no shared history. Using these notions of history and orthogonality, we can define a mathematical structure called **model** of a probability distribution. With this model, we can do causal inference (inferring causal structure from data).  

Factored sets let us infer causal relations that we usually wouldn’t have found using causal graphs. For example, if we have two binary variables X and Y, and X is independent from X XOR Y, then we can infer the causal direction $X \to Y$.

## Further Reading ^further-reading

I hope you got a bit of a grasp on finite factored sets, and see why they are really neat. If you want to read more, the best entry point is probably [this edited transcript](https://www.lesswrong.com/posts/N5Jm6Nj4HkNKySA5Z/finite-factored-sets) from a talk by Scott Garrabrant.

For a non-mathematical intuition how Scott relates the concepts of time, causality, abstraction, and agency, see his [Saving Time](https://www.lesswrong.com/posts/gEKHX8WKrXGM4roRC/saving-time) post.  

I haven’t looked closely into AI alignment specific applications of factored sets, but it looks like they can be used to better talk about [embedded agency](https://www.lesswrong.com/s/kxs3eeEti9ouwWFzr/p/yGFiw23pJ32obgLbw#7_3__Embedded_Agency), [decision theory](https://www.lesswrong.com/s/kxs3eeEti9ouwWFzr/p/b2YBddoCKSixivSAJ#Defining_Decision_Theories), and [ELK](https://www.lesswrong.com/s/kxs3eeEti9ouwWFzr/p/b2YBddoCKSixivSAJ#Counterfactability_and_ELK).   
 

---

:::hide

_This post is a result of a_ [_distillation_](https://www.lesswrong.com/posts/zo9zKcz47JxDErFzQ/call-for-distillers) _workshop led by John Wentworth at_ [_SERI MATS_](http://serimats.org/)_. I’d like to thank Leon Lang, Scott Garrabrant, Matt MacDermott, Jesse Hoogland, and Marius Hobbhahn for feedback and discussions on this post._
:::

[^note-factorization-count]: Note that the number of set factorizations of an n-element set is not the same as the number of integer factorizations of n, because elements are distinguishable, so for example these two factorizations do not count as the same factorization: _![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/x0hi59qoolsvezgsgjnl)_
[^note-orthogonality-independence]: Actually, it’s somewhat more complicated than “X and Y are (conditionally) orthogonal if and only if they are independent”. The full version is more like “If $X_S$ and $Y_S$ are partitions on a set S, which has a mapping $f: S\to \Omega$ to the sample space, then $X_S$ and $Y_S$ are (conditionally) orthogonal if and only if the images X and Y of $X_S$ and $Y_S$ are (conditionally) independent”. But for the sake of this explanation, if you just remember that “orthogonality $\Leftrightarrow$ independence”, that's enough.
[^note-non-bijective-preimages]: Even if f is not bijective, the “preimages” $X_S$ and $Y_S$ of X and Y are always well-defined partitions. Here are two examples in which f is not bijective: ![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/PfcQguFpT8CDHcozj/qwxq7mokx4o1cml2kw4i)
