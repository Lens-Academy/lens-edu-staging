---
title: "Condensation & Relevance"
author:
  - "abramdemski"
source_url: "https://www.lesswrong.com/posts/2x9yatKKTRMabQAWq/condensation-and-relevance"
published: 2026-01-23
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "(This post elaborates on a few ideas from my review of Sam Eisenstat's Condensation: a theory of concepts. It should be somewhat readable on its own…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_(This post elaborates on a few ideas from my_ [_review_](https://www.lesswrong.com/posts/BstHXPgQyfeNnLjjp/condensation) _of Sam Eisenstat's_ [_Condensation: a theory of concepts_](https://openreview.net/forum?id=HwKFJ3odui#discussion)_. It should be somewhat readable on its own but doesn't fully explain what condensation is on its own; for that, see my review or Sam's paper. The post came out of conversations with Sam.)_

As I mentioned in my [Condensation](https://www.lesswrong.com/posts/BstHXPgQyfeNnLjjp/condensation) review, the difference between compression and condensation fits the physical analogy suggested by their names: compression mashes all the information together, while condensation (still compresses size, but) sorts information into discrete droplets.

Thus, condensation has a property we might call _local relevance_: typical questions can be answered at a glance, ie, retrieving small subsets of the information. This type of representation is sometimes called "symbolic":

| Symbolic | Not Symbolic |
| --- | --- |
| A number can be quickly determined positive or negative by checking whether there is a "-" symbol in front. | "reading the room" at a social gathering requires integrating diverse cues. |
| The topic of a paper can be determined by reading the title and abstract. | The semantic content in a vector representation inside an artificial neural network is often represented redundantly, spread across the whole vector. |
| A person's age can be determined by looking at their birthdate on a government-issued ID. | The quality of a work of art is spread throughout the whole piece. |
| The subject of a sentence can be found before the verb. | Determining the subject of a photograph requires understanding the whole image. |
| A target library book can be quickly retrieved from the shelves. | Finding gold nuggets requires sifting huge amounts of sand. |

This notion of "symbolic" seems related to interpretability (and the theory of condensation seeks to clarify this relationship). 

The notion of "relevance" in condensation is what Sam calls the contribution relation. This is like a card catalogue which tells you what books to retrieve for a specific situation.

Like [Natural Latents](https://www.lesswrong.com/posts/Qdgo2jYAuFRMeMRJT/natural-latents-latent-variables-stable-across-ontologies), condensation seeks to establish that two agents will have corresponding world-models by assuming the correspondence of just a few variables, the "given variables"; they're trying to argue something like "If agents can agree[^note-1] on some objective observables, EG the readings of scientific instruments, then (under some further assumptions) they'll also share a bunch of abstract concepts".

This initial set of questions is what the contribution relation measures relevance to. In my review, I likened condensation to a "universal data-structure" optimized to serve a set of queries (the given variables). 

## Variable-Cost Symbols ^variable-cost-symbols

Imagine you are compressing a record of the weather of a sequence of days, in 3 categories: sunny, cloudy, or rainy. 0s and 1s are about equally costly to represent in computers, so that in a compressed representation, both communicate a 50% probability event; 11, 10, 01, and 00 all communicate 25% probability events; and so on. If both rainy and cloudy days are 25% frequent, then it is possible to compress optimally by using 0 to represent sun, 10 to represent clouds, and 11 to represent rain. This representation is nice and "local"; it gives a "symbol" to each possible type of day.

In contrast, if each of the three weather types are equally frequent, there's no nice local representation we can use. Since 1/3rd doesn't relate nicely to powers of 2, optimal compression necessarily smears the information from individual days around, mixing several days together within a single 1 or 0. In modern interpretability jargon, compressed representations tend to be polysemantic.

Intuitively, we have to ditch locality because we're trying to fit the "round peg" of 1/3rd into the "square hole" of 1/$2^m$ . We're stuck in the "grid" of numbers which bits can easily represent.

With pen and paper, writing the number 1 is especially easy; it is acceptable to write simply a vertical line, making it one of the easiest symbols. This makes sense from a compression point of view: according to [Benford's Law](https://en.wikipedia.org/wiki/Benford%27s_law), 1 will be the most common digit to write.

Normally, in compression, the "length" of characters is always 1; the length of a string _is just_ the number of characters. However, in real life, the cost of a symbol can vary. There are lots of shapes we can make with a pen and paper, some larger or more complex than others! So, when designing a pen-and-paper code, we can (and should) take that into account.[^note-2]

Imagine optimizing a variable-cost alphabet for use in a compression task. To avoid "cheating" by setting all symbol-lengths to very small, we have to somehow account for the fact that there can only be so many simple symbols. (There are only so many one-line symbols humans are willing to distinguish, for example.) One way to do this by assigning each symbol a positive probability, and requiring that the probabilities of the whole alphabet sum to 1. The "length" of a symbol (in bits) can then be measured as the negative log (base 2) of the probability. You can make one symbol approach a length of zero, but this forces all other symbols to be longer.

This is similar to the earlier-mentioned idea that a 1 or 0 in a well-compressed binary file always represents an event with 50% probability; the variable-length alphabet won't necessarily be used to compress things optimally all the time, but when it is, length of a symbol is always -log of the probability of the event being represented.

Allowing codes to choose arbitrary variable-length symbols lets us create "local" representations for arbitrary probabilities in the weather example, by giving each state a symbol of length appropriate to its probability. If the three weather types have equal probability, we simply choose an alphabet with three characters of length $-\text{log}_2({1 \over 3})$ each.

Of course, using variable-cost symbols doesn't _force_ a code to be "symbolic". If you only optimize for compression, you _can equally well_ end up with the same sort of mess that equal-cost symbols are liable to force you into. Condensation gives an optimization target with a positive tendency to produce representations with local relevance. (We can investigate better theories of condensation by looking for optimization targets which represent local relevance better; especially, I think, if those optimization targets can be grounded in a better story of practical relevance.)

Condensation suggests a picture of memory-management: rather than compressing everything together, as in the Solomonoff picture of rationality, we're incentivized to sort things out into concepts (random variables) so that we can think about a few things at once. Information is split into bite-sized chunks so that we can retrieve only the relevant ones.[^note-3]

Still, I think variable-cost symbols can help us understand condensation better: specifically, they address a problem in the algorithmic version of condensation. 

For example, consider the case of iterated coinflips sharing a common bias. Taking coinflips as the given variables, probabilistic condensation identifies a single latent variable the coin bias. This variable reduces the entropy of each coinflip as much as it can while only taking on information common to all of them (not, eg, encoding a cheat table identifying exactly which coins land heads).

Algorithmic condensation doesn't work so well in this case. Since either outcome is possible, an individual coinflip can't be compressed to any less than a single bit; even if the probability of heads is 0.99999, you've got to write a one ore a zero to record that information. Thus, algorithmic condensation sees no benefit in positing a latent.

The example can be rescued: for algorithmic condensation, we just have to choose given variables representing several coinflips concatenated together. Compression becomes possible again, so positing a latent representing coin bias is vindicated. However, this seems like an unfortunate blemish in the theory: compression-like incentives to lump stuff together creeping in.

So, perhaps it is better to rescue algorithmic condensation by adopting variable-cost symbols, so that even single-symbol messages can have different "length". This allows us to replace variables with concrete written messages (like in algorithmic condensation) while avoiding any coin-lumping.

However, I'm not sure about the best way to work out this version of condensation fully.

[^note-1]: This is more like "agree on the existence of" as opposed to "agree on all questions about". Hence they need not be "directly observable", though this would obviously help agents agree in both senses.
[^note-2]: Even more accurate cost models might account for the difficulty of a symbol _in context_, like models of typing efficiency which account for the travel length of a finger moving from one key to the next, or phonetic models which account for the difficulty of combinations of spoken phonemes such as consonant clusters.
[^note-3]: This doesn't yet clarify grammar-like phenomena, I think. Words are easily parsed. Concepts are combinatorial. I think this has to do with the [concept of transparency](https://www.lesswrong.com/posts/q9fynSKxbafu9hSfY/informality).
