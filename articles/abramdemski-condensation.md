---
title: "Condensation"
author:
  - "abramdemski"
source_url: "https://www.lesswrong.com/posts/BstHXPgQyfeNnLjjp/condensation"
published: 2025-11-09
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Condensation: a theory of concepts is a model of concept-formation by Sam Eisenstat. Its goals and methods resemble John Wentworth's natural abstractions/natural latents research."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

[_Condensation: a theory of concepts_](https://openreview.net/forum?id=HwKFJ3odui) is a model of concept-formation by Sam Eisenstat. Its goals and methods resemble John Wentworth's [natural abstractions](https://www.lesswrong.com/w/natural-abstraction)/[natural latents](https://www.lesswrong.com/posts/mMEbfooQzMwJERAJJ/natural-latents-the-concepts) research.[^note-1] Both theories seek to provide a clear picture of _how to posit latent variables_, such that once someone has understood the theory, they'll say "yep, I see now, that's how latent variables work!". 

The goal of this post is to popularize Sam's theory and to give my own perspective on it; however, it will not be a full explanation of the math. For technical details, I suggest reading [Sam's paper](https://openreview.net/forum?id=HwKFJ3odui).

# Brief Summary ^brief-summary

Shannon's information theory focuses on the question of how to encode information when you have to encode _everything._ You get to design the coding scheme, but the information you'll have to encode is unknown (and you have some subjective probability distribution over what it will be). Your objective is to minimize the _total expected code-length._

Algorithmic information theory similarly focuses on minimizing the total code-length, but it uses a "more objective" distribution (a universal algorithmic distribution), and a fixed coding scheme (some programming language). This allows it to talk about the minimum code-length of specific data (talking about particulars rather than average expectations becomes more central).

Both versions of information theory study _compression_. Sam's alternative is called _condensation_ in contrast.

Condensation doesn't concern itself with the total code-length. Instead, it concerns itself with how easy it is to use the encoding to answer questions about the data. This forces the encoding to be organized in a conceptually meaningful way, rather than compressed together into an uninterpretable blob.

**Compression creates density. Condensation forms discrete droplets.**

Condensing data creates a system of latent variables, which organize the data into meaningful parts. Sam has proven a theorem showing that different approximately-efficient condensations will posit approximately-isomorphic random variables. IE, two people who condense the data well will have similar "understandings" of the data and will be able to translate between their different conceptual schemes.

Like classical information theory, condensation has both a probabilistic and algorithmic variant. I'll briefly review classical information theory for the sake of comparison.

# Shannon's Information Theory ^shannons-information-theory

Claude Shannon's notion of information can be justified in the following way:

-   The amount of information that can be stored in an information-storage device is, apparently, only a function of the _number of distinguishable configurations_ of the device. If I want to communicate a single letter (26 options), and my communication channel is a knob with 26 settings, then I can come up with a code which allows me to communicate any letter by setting the knob to an appropriate setting. Reversing directions, I can also communicate knob-settings using letters.[^note-2]
-   When we take two information-storage devices together, we intuitively _add quantities of information;_ two notebooks can store twice as much information as one.
-   Since the number of configurations of two objects taken together is the _product_ of their individual configurations,[^note-3] we can infer that **information must be measured as the** _**logarithm**_ **of the number of configurations.**

This analysis can be further refined by taking the above discussion to apply to the case where all configurations are equally probable. When the probabilities of configurations differ, the information contained in a configuration with probability $1 \over c$  is measured _as if_ there were $c$ configurations (even if $c$ is not a whole number); ie, $\log(c)$.[^note-4]

Most commonly, we take log base 2, in which case we are measuring information in _bits._

I find this derivation to be beautiful, but the immense impact of information theory cannot be justified from this alone. The practical power of this theory comes from the relationship between information and codes.

Imagine that Alice is keeping a diary of birds that visit her birdfeeder. She wants to conserve ink, paper, and her own time spent writing the diary; so, she wants her diary entries to be as brief as possible. However, she does want to accurately record the type of each bird, and the time and duration of its visit. Therefore, Alice wants to come up with an efficient encoding scheme for her diary.

If Alice has probabilistic beliefs, then it makes sense for Alice to leverage these beliefs in designing her encoding scheme by assigning shorter codes to more common events. If most birds that visit are starlings, Alice might decide to record only the time and duration of a starling visit. Bird type only needs to be specified for non-starlings, saving Alice time and ink.

Shannon proved that, no matter how clever Alice's code, _the expected code length must be at least the expected information_.[^note-5] This gives a lower bound on the compression of information Alice can expect to achieve with her code. Shannon also gave good upper bounds (showing that near-optimal codes are possible), but those were computationally intractable. Fortunately, the study of near-optimal codes has continued to progress; these days, we can use [arithmetic coding](https://en.wikipedia.org/wiki/Arithmetic_coding) to easily get extremely close to this lower bound.

Thus, there is a tight relationship between probability distributions and efficient codes. In the case of codes written with the alphabet $\{0,1\}$ ("binary codes"), the number of _bits_ of information corresponds closely to the _number of 0s and 1s._ (Indeed, this correspondence is so close that the difference is commonly elided; 0s and 1s _are_ bits, in common parlance.)

Given a binary code, I can infer a probability distribution: by imagining the 0s and 1s are heads and tails from coin-flips, I get a probability distribution such that $p(x) = 2^{-\text{length of code of x}}$. Given a probability distribution, I can infer a binary code: I can apply arithmetic encoding so that $2^{-\text{length of code of x}}$ is _very close_ to $p(x)$.[^note-6]

**This means information is a very good proxy for minimal compression**, while being much nicer mathematically. Code-lengths can only ever be whole numbers, but information is a continuous function of probability, and is typically fractional (even when probabilities are rational numbers). The length of the optimal code for an event is a complicated combinatorial problem, which depends on the whole probability distribution; the information of an event is simply a function of that one event's probability. Code-length is a very direct physical quantity, whereas measuring information requires subjective probabilities.

I emphasize this because condensation is going to be a similar sort of abstraction. Optimal codes are a complicated optimization problem; information is a simpler thing which acts like an optimal-or-slightly-better-than-possible code. Similarly, condensation is going to discuss schemes for organizing data, but it discusses them in terms of a bound that's not always achievable.

## Universal Codes ^universal-codes

One more idea will be useful: _universal_ codes (the subject of _algorithmic_ information theory). The basic idea: any _useful_ compression needs to be _computable_ -- meaning, I can write a computer program which decompresses the code to return the original events.[^note-7] However, computer programs are themselves represented via a binary coding scheme (a programming language). Instead of coding a decoder ($c$ bits) and then coding the compressed data ($d$ bits) and then running the decoder on my compressed data to get the result, I could instead just directly write a computer program which, if run, produces the decompressed data. 

This approach will take $c+d$ bits to compress the data. Hence, any programming language[^note-8] is "almost as good as" whatever other code you might come up with: it is at most $c$ bits worse, where $c$ is the description length (in the chosen programming language) of a decompression algorithm for your better code. This constant $c$ is ubiquitous in algorithmic information theory. Since it is a constant, it becomes insignificant (in compression-ratio terms) as the data grows. A special-purpose code will always be better if you have a strong probabilistic model of the data you want to compress, but a programming language is a good general-purpose code if you don't have a specific probability distribution to model your data.

In some circumstances, it is conceptually nicer to represent the complexity of the coding scheme; that is, $c+d$ can be the more meaningful measure than $d$ alone. For example, the [Hutter Prize](https://en.wikipedia.org/wiki/Hutter_Prize) is a competition for compressing Wikipedia. Since the objective is to compress a single file which is known ahead of time and does not change, from the _probabilistic_ perspective, the optimal compression scheme should compress it down to 0 bits (an empty file). However, if we looked at the _code_ for such a compression scheme, we would see that it "cheats" by memorizing the data. (It could be something like "print: " followed by the Wikipedia text.) Algorithmic information theory penalizes this sort of cheating by counting the length of the decompression program _plus_ the length of the compressed file, whereas probabilistic information theory doesn't.

For our purposes here, the important thing I want to emphasize is how to translate back and forth between the probabilistic view and the algorithmic view.

-   The probabilistic view deals in possibilities, whereas the algorithmic view deals in particulars.
    -   In Shannon's information theory, we need to first be uncertain about the contents of a file (have some probability distribution over its contents) in order to then talk about the "information" of a specific string.
    -   In algorithmic information theory, we assume a universal distribution (ie, the probability distribution implied by a Turing-universal code), so we can talk about the "description length" of a file outright, without explicitly specifying a probability distribution.
-   The probabilistic view deals in random variables, whereas the algorithmic view deals in binary strings (sequences of 1s and 0s).
    -   In the Shannon view, events to be encoded can have some arbitrary type (EG, colors). We then encode those things (usually in binary strings).
    -   In the algorithmic view, everything is already in binary; we encode things to compress them further, but we're just transforming one sequence of 1s and 0s to another.

# Condensation ^condensation

Shannon & Weaver's seminal book introducing information theory was titled _**The Mathematical Theory of Communication**_. However, they do call out some ways in which it falls short of a full theory of communication. In particular, they note that it is not a theory of _semantics_ or _meaning_ (concepts which are, informally, strongly associated with the terms "information" and "communication").

I want to call out a slightly different way in which it falls short.

In my story about Alice keeping a bird-watching journal, Alice's problem was to record everything faithfully, so that she could reconstruct the entire series of events later. Realistically, however, Alice might want to consult her journal to reconstruct _specific_ events (to answer _specific_ questions). Shannon-style optimal codes do not optimize for this.

When a file is compressed, it typically has to be decompressed before _anything else_ can be done to it. Arithmetic Coding, in particular, turns things into an incomprehensible mess of 1s and 0s. **Shannon's notion of optimal codes prioritizes compression over** _**everything else.**_[^note-9]

Similarly, I think many proponents of Algorithmic Information Theory imagine the shortest program that outputs a target string of data to be something like a beautiful scientific theory of that data, but this need not be the case. It can instead be an incomprehensible mess. The only thing the math talks about is compression.

Sam's _condensation_ is, roughly, an attempt to put the right constraints on the encoding to force it to be a beautiful scientific theory instead of an unintelligible compressed mess.

## Universal Data-Structure? ^universal-data-structure

Shannon's theory of communication prioritizes compression alone. I claim that natural languages (as well as most artificial languages, EG, programming languages[^note-10]) prioritize other things as well. I said some informal things about comprehensibility. How can we formalize these ideas?

Some time ago, I had the idea that there should be a theory of _universal data-structures_. Algorithmic information theory has given rise to something like a theory of _universal algorithms_,[^note-11] but (as taught in a typical undergrad degree) that's only half of the picture of computer science; the other half is data-structures.

Sam's _condensation_ is the first thing I've seen that feels like progress towards this goal.

**Condensation viewed as a universal data-structure:**

-   You're given a blob of possibly-disorganized data.
-   You have a prior over (sets of) queries (future computations that depend on this data). These can be any computable function of the data.
-   Storage cost of the data is negligible, but _retrieval cost matters:_ given a set of queries, you want to retrieve the minimal amount of data needed to compute the answers.
-   Retrieval works by organizing information into "bins" which get tagged with questions the data in the bin is relevant for. _When a set of queries is received, all bins with any overlapping tags get retrieved._
-   How should we organize the information to minimize retrieval costs?

Sam considers a best-case scenario, where the information can be organized very well (I'll describe this in more detail later). Under this best-case assumption, the prior does not actually matter: well-organized information can focus on answering each set of questions efficiently, rather than prioritizing one over another.

The main point here is that we are optimizing for answering a variety of questions, rather than just optimizing for efficient reproduction of the whole blob of data, as in Shannon's picture. 

More generally, I find the idea of optimizing representations for more than just compression highly appealing. It is extremely cognitively plausible that we need to optimize our representations for _how they are used._ Sam's picture is one step in this direction, and shockingly, gives us an elegant theory rather than a big mess.

I find the "universal data-structure" picture highly technically motivating,[^note-12] but for the purpose of explaining things more intuitively, I prefer to describe things in terms of organizing notebooks.

## Well-Organized Notebooks ^well-organized-notebooks

Suppose you're in charge of managing an information-desk. Guests come to the desk with (one or more) questions. The full list of questions you're obliged to answer is known; anything outside of this list, it is ok if the response is "I don't know". However, you can't get all your clerks to memorize all the answers. Instead, you rely on a set of reference notebooks.

Each reference notebook is "tagged" with one or more questions. Guests ask all their questions at once, before the clerk answers. Once a guest has asked all their questions, the clerk is supposed to retrieve all the notebooks which are tagged with any of the questions.

The clerks can follow instructions in the notebooks perfectly (like a computer), and we don't care about how much cognitive labor the clerk has to do.

The "score" -- the only thing we care about -- is retrieval cost. This is just the total amount of text in all the notebooks retrieved to answer the questions. Or you can think of it as the total weight of the pile of notebooks the clerk has to retrieve.

We've got a probability distribution over what a guest might ask when they approach the information desk, so we can compute an expected score for a set of notebooks based on how well they organize information. (However, as I think I mentioned previously, Sam's theory doesn't end up being very sensitive to this probability distribution.)

Why would we ever tag a notebook with multiple questions? The idea is that such a notebook holds the common information between those two questions. Perhaps you have a notebook about fluid mechanics and a notebook about population dynamics; they both use differential equations, so your notebook on differential equations has a superset of the tags of both, so that a clerk will retrieve the differential equation notebook whenever they retrieve either fluid mechanics or population dynamics. You could have duplicated information about differential equations in both the other notebooks instead, but **the duplicated information would worsen your score in cases where you're asked questions about both things.** (This is why it is so crucial to Sam's theory that clerks might handle multiple questions at once, rather than dealing with one question at a time.)

So, the game we're playing is similar to compressing the answers individually, except we're incentivized to share information between answers, creating a "library" of useful abstractions.

One of the notebooks can have "all the tags" (IE, clerks always retrieve that notebook). This is similar to the $c$ from algorithmic information theory; it tells the clerks what they need to know to interpret any other notebook in the library. (This includes information about how to use notebooks together, not just interpreting them individually.)

## Random Variables ^random-variables

At the beginning, I said that condensation was a theory of _latent variables_, but I haven't mentioned them so far. That's because I've secretly been describing the algorithmic version of condensation, rather than the probabilistic version. The probabilistic version is what Sam actually describes [in his paper](https://openreview.net/forum?id=HwKFJ3odui). Here's a translation key:

| Algorithmic | Probabilistic |
| --- | --- |
| answers we might need to compute / "given strings" | given variables |
| uncondensed data / data from which the answers are to be computed | underlying probability space in which the givens live |
| notebooks / "latent strings" | latent variables |
| tags | contribution function |
| notebook with all the tags / program which says how to interpret the rest of the latent strings in service of computing answers | "top" latent (latent which contributes to all givens) |
| notebooks with one tag | "bottom" latents (latents which contribute to just one given variable) |
| score (length of all strings retrieved) | conditioned-perfect score |

### Givens ^givens

Since this is a theory of _how to postulate latent variables_, it might be tempting to interpret Sam's "given variables" as the observations we abstract latents from. This isn't a _terrible_ interpretation, but Sam avoided "observable variables" for a reason: [factoring our observations into variables is already putting a conceptual frame on them](https://www.lesswrong.com/s/kxs3eeEti9ouwWFzr). Moreover, the "givens" do not have to be directly observable. They can be variables we've come to believe in already.

I think it is better to interpret the given variables as _questions of interest to us_ (or rather, the variables track answers to such questions).

As I mentioned previously, the algorithmic version deals in particulars where the probabilistic version deals in possibilities: the algorithmic givens are _given strings_ (specific answers, EG the static information the clerks need to give guests at the information desk).

### Underlying Space ^underlying-space

Random variables in Sam's paper are just maps from an probability space to another, giving us a "projection" (a limited perspective) of the first space. If the given variables are our pre-existing concepts, their shared probability space is the underlying reality they describe.

Shannon's information theory allows us to talk about the information of arbitrary things, while algorithmic information theory requires everything to already be in the format of bits. Similarly, probabilistic condensation treats the underlying space as raw, unfactored reality, but algorithmic condensation needs the uncondensed data to already be formatted as a string of 1s and 0s.

### Latents ^latents

In the algorithmic version, the "latent strings" are the contents of the notebooks (or the "bins" I mentioned when talking about universal data-structures). In the probabilistic version, these become latent variables which we postulate to help "explain" the probabilistic structure of the givens. Ideally (in "perfect" condensation), these variables are all independent of each other.

Crucially, the latent variables can live in a larger underlying space than the givens. This represents the idea that new concepts need not be definable in terms of pre-existing concepts. When we come to understand something new about the world, it can actually _expand_ our language, representing the postulation of _more to the underlying reality than we previously understood_.

### Contributions ^contributions

In Sam's paper, the "contribution relation" takes the place of the "tags" in my notebook story. This relates latents to givens, telling us which latents are needed in order to reconstruct which givens (which notebooks are needed to answer which questions).

### Top ^top

The notebook with all the tags is the "top" latent, IE, the variable which contributes to all the givens. This tells us common information between everything. For example, if the given variables are coin-flips from the same biased coin, the top latent would be the bias.

This can give us information which we need to properly interpret the impact of the rest of the latent variables (similarly to how the notebook with all the tags works), but unlike the algorithmic version, this information needs to be variable in order to be present in top (otherwise it would just be background knowledge, with no need to represent it in any latent). For example, the bias of the coin needs to be unknown in order to be represented in top.

### Bottoms ^bottoms

Correspondingly, the "bottom" latents are those which contribute to just one given variable. This can be thought of as the remaining "noise" after we've abstracted out all the common information between things. In the coin-flip example, these would encode the individual coinflips.[^note-13]

I believe John's theory of natural latents excludes these from consideration, marking one difference from Sam's theory. (A natural latent is information that's represented in many places.)

### Score ^score

The "score" in algorithmic condensation is quite straightforward (the concatenated string-length for all strings retrieved), but it gets more complex for probabilistic condensation.

First, Sam defines the _simple score_. This is the sum of the entropies for latent variables which contribute to the given variables queried. Entropy is just expected information, and information is just a very good proxy for description length, so this roughly makes sense as just the expectation of the retrieval cost (we need to introduce an expectation because this is the probabilistic version).

There's a problem, however. The simple score computes each entropy _individually_. This amounts to an assumption that each notebook's encoding has to be decodable _on its own_.[^note-14] This doesn't make very much sense given the scenario: "higher-level" notebooks (with more tags) are always retrieved when specific "lower-level" notebooks (with some of those tags) are retrieved. This means we can use the information in the higher-level notebooks to help encode the lower-level notebooks, making lower-level notebooks impossible to decode without the right higher-level notebooks (EG,  fluid mechanics is impossible to understand without differential equations). Since we _can_ do this, we _**absolutely should do this,**_ since it gets us a better score.[^note-15]

This nuance is accounted for in Sam's _conditioned score_, which sums _conditional_ entropies rather than simple entropies, as appropriate to represent the above-described optimization. (Note that the conditioned score is always better than the simple score.)

## Perfect Condensation ^perfect-condensation

Shannon's bound on compression must also hold for condensation: _the expected code-length must be at least the expected information_. This means the simple score and conditioned score must both be at least the expected information (aka _joint entropy_) of the questions being asked.

When the conditioned score is _equal to_ the joint entropy, Sam calls this **perfect condensation**. When even the _simple_ score is equal to the joint entropy, he calls this simply-perfect condensation.

Perfect condensation means that the latent variables contributing to a set of givens are _exactly_ the information we need to reconstruct the givens. Imagine I'm examining a machine without disassembling it. I can look at the input/output behaviors of this machine (givens), and I'm trying to postulate an internal mechanism (latents). Perfect condensation means not postulating any extra hidden states beyond what is needed to explain (reconstruct) the input/output behavior.

Sam's _comparison theorem_ shows that systems of latent variables which are approximately perfect condensations of the same givens must approximately correspond to each other. Those who condense well must share similar perspectives on the world.

This is liable to have far-reaching consequences, but does it mean Sam has solved the interpretability problem?

# Interpretability Solved? ^interpretability-solved

Condensation has at least two plausible applications, which could improve our ability to interpret what machine-learning models are "thinking".

First, we could treat the internal activations of machine-learning models such as artificial neural networks as "givens" and try to condense them to yield more interpretable features.

Second, we could take condensation as inspiration and try to create new machine-learning models which resemble condensation, in the hopes that their structure will be more interpretable.

These avenues seem potentially promising, but should we think of condensation as a general theory of interpretability? Is this the theoretical tool we need to crack interpretability open?

I'll raise some concerns pointing at limitations.

## Condensation isn't as tight an abstraction as information theory. ^condensation-isnt-as-tight

While it is possible to create compression algorithms very close to the theoretical bounds articulated by information theory, it is _not_ always possible to do so with condensation.

First, perfect condensation is not always possible (not even approximately). I'll skip the details for now (maybe I'll explain more in a future post), but this is basically because interaction information can be negative. 

Second, the way compression smooshes everything together allows codes to take advantage of less-than-one-bit information by aggregating things. (If a coin is biased, observing a coin-flip gives us less than one bit of information in expectation. This allows us to compress a sequence of coinflips in a way that encodes more than one coin-flip per bit on average.) The way condensation splits things into latent variables doesn't always allow this. (If you have to encode a single coin-flip, you'll have to use a full bit, no matter how biased the coin.)

## Condensation isn't a very good model of cognition. ^condensation-isnt-a-very

First, condensation completely ignores computational cost. The _only_ cost it models is retrieval cost. While this takes us one step in the direction of modeling how information is used, it might not be enough. It still ignores the issue of bounded computational power, like so many other models of rationality. 

Second, the tag-retrieval model seems artificial to me. Sam's assumptions -- that we can get multiple questions at once, and that we retrieve all notebooks tagged with any of the questions -- are quite important for the results. However, these assumptions are difficult to justify (other than via the results they're able to get).

When I look at condensation through my "universal data-structure" goggles, I want to lift these assumptions, replacing them with a more free-flowing information-retrieval model. 

Asking multiple questions at once can be modeled as just a more complex question ("Tell me the capital of France and the capital of Germany"), which makes it tempting to discard the multiple-questions aspect.

As for the tags, perhaps the top instruction booklet gives me an algorithm by which I can decide which other notebooks to retrieve. (These other notebooks could recursively contain instructions for when to retrieve yet-more notebooks.)

However, under optimization pressure, this becomes trivial: I can simply compress the answer to each question individually, and retrieve only that.

This can be made nontrivial again if we reintroduce storage costs. Compressing the answer to each question individually, rather than taking advantage of common abstractions, can take quite a bit of extra storage.

This suggests modeling a trade-off between retrieval cost and storage cost. In the limit of caring only about storage cost, we compress everything together. In the limit of caring only about retrieval cost, we compress answers individually. In the middle, we might get a nontrivial theory of abstraction, somewhat similar to condensation.

# Much work to be done! ^much-work-to-be

I've tried to give a high-level overview of condensation, but the best way to check the theory and develop intuitions is to work examples, to check if the latents which optimally condense givens are in fact the intuitively meaningful latents. Sam does some of this in his paper, but it needs to be done for many more cases.

Condensation is in its early days; there is a great deal of low-hanging research fruit here, whether it is working out further details of the theory of condensation, trying to apply it to machine learning, or working out alternatives by modifying condensation. I think it is quite exciting, and I hope you feel the same way.

[^note-1]: Sam says his goals are _somewhat_ different: he sees John's theory as too objective, suggesting a universally correct way to represent things (an underlying reality, with respect to abstractions). Sam's ideas are more intersubjective, admitting commonalities between agents without supposing a universally correct way of doing things. However, _condensation_ does not reflect Sam's anti-objective streak. The math, as it stands, provides conditions under which there is a correct set of latent variables to postulate (up to isomorphism).
[^note-2]: We can also conclude that the function must be _increasing_ in the number of configurations: if the knob has 27 settings, then I can still communicate letters using the knob, but I can no longer faithfully communicate knob-settings using letters.
[^note-3]: (assuming the two objects can be freely configured in an independent way, IE, do not constrain each other)
[^note-4]: For a precise argument, see [the Wikipedia page on Information Content](https://en.wikipedia.org/wiki/Information_content#Derivation). There are also similar technical arguments for the concept of entropy; see Shannon's _a mathematical theory of communication_ or, for just the specific argument I'm referring to, [here are some](https://www.stat.cmu.edu/~cshalizi/350/2008/lectures/06a/lecture-06a.pdf) [course notes](https://www2.math.upenn.edu/~ted/280S19/CourseNotes/Shannon'sTheorem-Math280.pdf).
[^note-5]: This is [Shannon's source coding theorem AKA noiseless coding theorem](https://en.wikipedia.org/wiki/Shannon%27s_source_coding_theorem).
[^note-6]: This close relationship between compression and probability also implies a close relationship between compression and prediction: if you can compress data well, you must be able to predict it well.
[^note-7]: This idea inherently assumes that the original events being encoded by the compression scheme were themselves already a sequence of 1s and 0s, unlike the example of Alice's birds used earlier. For example, PNG is a common image compression format. We can take a bitmap image (which is already represented as 1s and 0s) and convert the file to PNG, which will usually make the file shorter (less 1s and 0s). This works because PNG takes advantage of some probabilistic beliefs about typical images, whereas the bitmap format does not.
[^note-8]: (so long as it is [Turing-universal](https://en.wikipedia.org/wiki/Universal_Turing_machine))
[^note-9]: This is not _quite_ true. I haven't reviewed the relevant ideas, but Shannon's information theory does also capture _one_ other objective: redundancy. My review only covered ideas relevant to communication across _noiseless_ communication channels, where compression is the only goal. Shannon also studied communication across _noisy_ channels, where you want your message to be adequately redundant, so that the intended message can be reconstructed with high probability ([error-correcting codes](https://en.wikipedia.org/wiki/Error_correction_code)). This feature is apparent in natural languages, which tend to contain redundancies (such as subject-verb agreement) rather than compressing everything as efficiently as possible.
[^note-10]: (when put to ordinary use, _not_ as used in Algorithmic Information Theory)
[^note-11]: I haven't covered that part of Algorithmic Information Theory here. I have in mind stuff like Levin Search, and similar things discussed by Ray Solomonoff in [Progress in Incremental Machine Learning](https://raysolomonoff.com/publications/nips02.pdf).
[^note-12]: Granted, "universal data-structure" is just a vague idea, and perhaps poorly-named. Maybe this is closer to a "general theory of data-structures" IE something in the direction of taking a description of a set of use-cases & deriving the appropriate data-structure.
[^note-13]: You can't really save any code-length for a single coin; no matter how biased it is (ie no matter how much fractional-bit information you have about it), you still have to write either 1 or 0 to record the bit. This is one way in which condensation is a less-tight abstraction. Or perhaps I should say: one way in which information is a less-tight abstraction when applied to condensation as opposed to compression. Information theory says that the information in a biased coin is less than one bit. This works out when we aggregate many coins together: we can anticipate that a coin biased towards 0 will create many runs of several 0s in a row (and far less runs of 1s). This allows us to compress (by representing runs of 0s more compactly). However, it seems to me, this is precisely the sort of compression which doesn't reflect our understanding of the data. If I understand correctly, condensation won't do this. We could condense several coin-flips together to encode them more efficiently, and it would help our score _in cases where we are asked about (most of) those specific coinflips._ Unfortunately, this could be a disaster for our score in cases where we're only asked about one or two coinflips in a bunch, but are forced to retrieve the condensation of the whole set. As you can see, this creates a high dependence on the distribution of sets of questions, which means it gets us into the territory where condensation isn't such a nice abstraction. (I could be wrong about these details.)
[^note-14]: _What does it even mean_ to decode a notebook "individually"? After all: the point of the notebooks is that (if you've retrieved the right notebooks) you can _collectively_ put them together and decode the answer to the questions you've been asked. Well: recall that condensation is a theory of postulating _latent variables_. This _does and should_ imply that a notebook is meaningful on its own. Decoding a notebook individually means **figuring out what that notebook says about the state of the latent.** Once we know the state of all the relevant latents, we put _those_ together to figure out the state of the given variables being queried.
[^note-15]: It might seem like this paragraph is confusing the algorithmic and probabilistic versions of condensation, since I'm using the algorithmic terminology to describe probabilistic condensation. This is partly because I'm using the algorithmic version as a more concrete and intuitive analogy for what's going on in the probabilistic version, and partly because "description length" still makes sense in Shannon's information theory, so the notebook analogy is still apt.
