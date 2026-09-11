---
title: "chinchilla’s wild implications"
author:
  - "nostalgebraist"
source_url: "https://www.lesswrong.com/posts/6Fpvch8RR29qLEWNH/chinchilla-s-wild-implications"
published: 2022-07-31
created: 2026-09-11
accessed: 2026-09-11
llm-review:
  date: 2026-09-11
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-11
    kind: "live"
description: "(Colab notebook here.)"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

([Colab notebook](https://colab.research.google.com/drive/1qv2-hUR5hPqw3OcfmLEhq6Tg15bf06Mj?usp=sharing) here.)

This post is about language model scaling laws, specifically the laws derived in the DeepMind paper that introduced Chinchilla.[^cite-1]

The paper came out a few months ago, and has been discussed a lot, but some of its implications deserve more explicit notice in my opinion. In particular:

-   Data, not size, is the currently active constraint on language modeling performance. Current returns to additional data are immense, and current returns to additional model size are miniscule; indeed, most recent landmark models are wastefully big.
    
    -   If we can leverage enough data, there is no reason to train ~500B param models, much less 1T or larger models.
        
    -   If we _have to_ train models at these large sizes, it will mean we have encountered a barrier to exploitation of data scaling, which would be a great loss relative to what would otherwise be possible.
        
    
-   The literature is extremely unclear on how much text data is actually available for training. We may be “running out” of general-domain data, but the literature is too vague to know one way or the other.
    
-   The _entire_ available quantity of data in highly specialized domains like code is woefully tiny, compared to the gains that would be possible if much more such data were available.
    

Some things to note at the outset:

-   This post assumes you have some familiarity with LM scaling laws.
    
-   As in the paper[^note-2], I’ll assume here that models never see repeated data in training.
    
    -   This simplifies things: we don’t need to draw a distinction between data size and step count, or between train loss and test loss.
        
    
-   I focus on the parametric scaling law from the paper’s “Approach 3,” because it’s provides useful intuition.
    
    -   Keep in mind, though, that Approach 3 yielded somewhat different results from Approaches 1 and 2 (which agreed with one another, and were used to determine Chinchilla’s model and data size).
        
    -   So you should take the exact numbers below with a grain of salt. They may be off by a few orders of magnitude (but not _many_ orders of magnitude).
        
    

## 1\. the scaling law ^1-the-scaling-law

The paper fits a scaling law for LM loss $L$, as a function of model size $N$ and data size $D$.

Its functional form is very simple, and easier to reason about than the $L(N, D)$ law from the earlier Kaplan et al papers. It is a sum of three terms:

$$
L(N, D)  = \frac{A}{N^{\alpha}} + \frac{B}{D^{\beta}} + E
$$

The first term only depends on the model size. The second term only depends on the data size. And the third term is a constant.

You can think about this as follows.

An “infinitely big” model, trained on “infinite data,” would achieve loss $E$. To get the loss for a real model, you add on two “corrections”:

1.  one for the fact that the model’s only has $N$ parameters, not infinitely many
    
2.  one for the fact that the model only sees $D$ training examples, not infinitely many
    

$$
L(N, D)  = \underbrace{\frac{A}{N^{\alpha}}}_\text{finite model} + \underbrace{\frac{B}{D^{\beta}}}_\text{finite data} + \underbrace{E}_\text{irreducible}
$$

Here’s the same thing, with the constants fitted to DeepMind’s experiments on the MassiveText dataset[^note-3].

$$
L(N, D)  = \underbrace{\frac{406.4}{N^{0.34}}}_\text{finite model} + \underbrace{\frac{410.7}{D^{0.28}}}_\text{finite data} + \underbrace{1.69}_\text{irreducible}
$$

### plugging in real models ^plugging-in-real-models

**Gopher** is a model with 280B parameters, trained on 300B tokens of data. What happens if we plug in those numbers?

$$
L(280\cdot10^9, \ 300\cdot10^9)  = \underbrace{0.052}_\text{finite model} + \underbrace{0.251}_\text{finite data} + \underbrace{1.69}_\text{irreducible} = 1.993
$$

What jumps out here is that the “finite model” term is _tiny._

In terms of the impact on LM loss, Gopher’s parameter count might as well be infinity. There’s a _little_ more to gain on that front, but not much.

Scale the model up to 500B params, or 1T params, or 100T params, or $3\uparrow\uparrow\uparrow3$ params . . . and the most this can _ever_ do for you is an 0.052 reduction in loss[^note-4].

Meanwhile, the “finite data” term is _not_ tiny. Gopher’s training data size is very much _not_ infinity, and we can go a long way by making it bigger.

---

**Chinchilla** is a model with the same training compute cost as Gopher, allocated more evenly between the two terms in the equation.

It’s 70B params, trained on 1.4T tokens of data. Let’s plug that in:

$$
L(70\cdot10^9, \ 1400\cdot10^9)  = \underbrace{0.083}_\text{finite model} + \underbrace{0.163}_\text{finite data} + \underbrace{1.69}_\text{irreducible} = 1.936
$$

Much better![^note-5]

Without using any more compute, we’ve improved the loss by 0.057. That’s bigger than Gopher’s entire “finite model” term!

The paper demonstrates that Chinchilla roundly defeats Gopher on downstream tasks, as we’d expect.

Even that understates the accomplishment, though. At least in terms of loss, Chinchilla doesn’t just beat Gopher. It beats _any model_ _trained on Gopher’s data, no matter how big._

To put this in context: until this paper, it was conventional to train all large LMs on roughly 300B tokens of data. (GPT-3 did it, and everyone else followed.)

Insofar as we trust our equation, this _entire_ line of research—which includes GPT-3, LaMDA, Gopher, Jurassic, and MT-NLG—could _never_ have beaten Chinchilla, no matter how big the models got[^note-6].

People put immense effort into training models that big, and were working on even bigger ones, and yet none of this, in principle, could ever get as far Chinchilla did.

---

Here’s where the various models lie on a contour plot of LM loss (per the equation), with $N$ on the x-axis and $D$ on the y-axis.

![](https://www.greaterwrong.com/proxy-assets/3B8SEA4TP6GBEBPP5S2DMSED6A)

Only PaLM is remotely close to Chinchilla here. (Indeed, PaLM does slightly better.)

PaLM is a huge model. It’s the largest one considered here, though MT-NLG is a close second. Everyone writing about PaLM mentions that it has 540B parameters, and the PaLM paper does a lot of experiments on the differences between the 540B PaLM and smaller variants of it.

According to this scaling law, though, PaLM’s _parameter count_ is a mere footnote relative to PaLM’s _training data size_.

PaLM isn’t competitive with Chinchilla because it’s big. MT-NLG is almost the same size, and yet it’s trapped in the pinkish-purple zone on the bottom-left, with Gopher and the rest.

No, PaLM is competitive with Chinchilla only because it was trained on more tokens (780B) than the other non-Chinchilla models. For example, this change in data size constitutes 85% of the loss improvement from Gopher to PaLM.

Here’s the precise breakdown for PaLM:

$$
L(540\cdot10^9, \ 780\cdot10^9)  = \underbrace{0.042}_\text{finite model} + \underbrace{0.192}_\text{finite data} + \underbrace{1.69}_\text{irreducible} = 1.924
$$

PaLM’s gains came with a great cost, though. It used way more training compute than any previous model, and its size means it also takes a lot of inference compute to run.

Here’s a visualization of loss vs. training compute (loss on the y-axis and in color as well):

![](https://www.greaterwrong.com/proxy-assets/2EV1GHDDILBTJ40P91MJ2Q0V03)

Man, we spent all that compute on PaLM, and all we got was the slightest edge over Chinchilla!

Could we have done better? In the equation just above, PaLM’s terms look pretty unbalanced. Given that compute, we probably should have used more data and trained a smaller model.

The paper tells us how to pick _optimal_ values for params and data, given a compute budget. Indeed, that’s its main focus.

If we use its recommendations for PaLM’s compute, we get the point “palm\_opt” on this plot:

![](https://www.greaterwrong.com/proxy-assets/1U923RJV08H1VLGPPO1G0V03UM)

Ah, now we’re talking!

---

“palm\_opt” sure looks good. But how would we train it, concretely?

Let’s go back to the $N$\-vs.-$D$ contour plot world.

![](https://www.greaterwrong.com/proxy-assets/MRACAHBAGBFGMFDNV5PU6RS4H)

I’ve changed the axis limits here, to accommodate the **massive** data set you’d need to spent PaLM’s compute optimally.

How much data would that require? Around 6.7T tokens, or ~4.8 times as much as Chinchilla used.

Meanwhile, the resulting model would not be nearly as big as PaLM. The optimal compute law actually puts it at 63B params[^note-7].

Okay, so we just need to get 6.7T tokens and . . . wait, how exactly _are_ we going to get 6.7T tokens? How much text data _is_ there, exactly?

## 2\. are we running out of data? ^2-are-we-running

It is frustratingly hard to find an answer to this question.

The main moral I want to get across in this post is that the large LM community has not taken data scaling seriously enough.

LM papers are meticulous about $N$ -- doing all kinds of scaling analyses on models of various sizes, etc. There has been tons of smart discussion about the hardware and software demands of training high-$N$ models. The question “what would it take to get to 1T params? (or 10T?)” is on everyone’s radar.

Yet, meanwhile:

-   Everyone trained their big models on 300B tokens, for no particular reason, until this paper showed how hilariously wasteful this is
    
-   Papers rarely do scaling analyses that vary data size—as if the concepts of “LM scaling” and “adding more parameters” have effectively merged in people’s minds
    
-   Papers basically never talk about what it would take to scale their _datasets_ up by 10x or 50x
    
-   The data collection sections of LM papers tend to be vague and slapdash, often failing to answer basic questions like “where did you scrape these webpages from?” or “how many more could you scrape, if you wanted to?”
    

As a particularly egregious example, here is what the [LaMDA](https://arxiv.org/abs/2201.08239) paper says about the composition of their training data:

> The pre-training data, called Infiniset, is a combination of dialog data from public dialog data and other public web documents. It consists of 2.97B documents and 1.12B dialogs with 13.39B utterances. The composition of the data is as follows: 50% dialogs data from public forums; 12.5% C4 data \[11\]; 12.5% code documents from sites related to programming like Q&A sites, tutorials, etc; 12.5% Wikipedia (English); 6.25% English web documents; and 6.25% Non-English web documents. The total number of words in the dataset is 1.56T.

“Dialogs data from public forums”? Which forums? Did you use all the forum data you could find, or only 0.01% of it, or something in between? And why measure _words_ instead of tokens—unless they _meant_ tokens?

If people were as casual about scaling $N$ as this quotation is about scaling $D$, the methods sections of large LM papers would all be a few sentences long. Instead, they tend to look like this (excerpted from ~3 pages of similar material):

![](https://www.greaterwrong.com/proxy-assets/5GMACPPF477B5LSJIB4MKCQLCQ)

From the PaLM paper

---

...anyway. How much more data could we get?

This question is complicated by the fact that not all data is equally good.

([This messy Google sheet](https://docs.google.com/spreadsheets/d/1zsahRIxNnXSq9z9tEHbISCkYxsivnDG9V3LbJLJTL90/edit?usp=sharing) contains the calculations behind some of what I say below.)

### web scrapes ^web-scrapes

If you just want _a lot of text_, the easiest way to get it is from web scrapes like Common Crawl.

But these are infamously full of garbage, and if you want to train a good LM, you probably want to aggressively filter them for quality. And the papers don’t tell us how much _total_ web data they have, only how much _filtered_ data.

**MassiveWeb**

The training dataset used for Gopher and Chinchilla is called MassiveText, and the web scrape portion of it is called MassiveWeb. This data originates in a mysterious, unspecified web scrape[^cite-8], which is funneled through a series of filters, including quality heuristics and an attempt to only keep English text.

MassiveWeb is 506B. Could it be made bigger, by scaling up the original web scrape? That depends on how complete the original web scrape was—but we know nothing about it.

**The GLaM/PaLM web corpus**

PaLM used a different web scrape corpus. It was first used in [this paper](https://proceedings.mlr.press/v162/du22c.html) about “GLaM,” which again did not say anything about the original scraping process, only describing the quality filtering they did (and not in much detail).

The GLaM paper says its filtered web corpus is 143B tokens. That’s a lot smaller than MassiveWeb. Is that because of the filtering? Because the original scrape was smaller? Dunno.

To further complicate matters, the PaLM authors used a _variant_ of the GLaM dataset which made multilingual versions of (some of?) the English-only components.

How many tokens did this add? They don’t say[^note-9].

We _are_ told that 27% (211B) of PaLM’s training tokens came from this web corpus, and we are separately told that they tried to avoid repeating data. So the PaLM version of the GLaM web corpus is probably at least 211B, versus the original 143B. (Though I am not very confident of that.)

Still, that’s much smaller than MassiveWeb. Is this because they had a higher quality bar (which would be bad news for further data scaling)? They do attribute some of PaLM’s success to quality filtering, citing the ablation on this in the GLaM paper[^cite-10].

It’s hard to tell, but there is this ominous comment, in the section where they talk about PaLM vs. Chinchilla:

> Although there is a large amount of very high-quality textual data available on the web, there is not an infinite amount. For the corpus mixing proportions chosen for PaLM, data begins to repeat in some of our subcorpora after 780B tokens, which is why we chose that as the endpoint of training. It is unclear how the “value” of repeated data compares to unseen data for large-scale language model training[^cite-11].

The subcorpora that start to repeat are probably the web and dialogue ones.

Read literally, this passage seems to suggest that even the vast web data resources available to _Google Research_ (!) are starting to strain against the data demands of large LMs. Is that plausible? I don’t know.

### domain-specific corpora ^domain-specific-corpora

We can speak with more confidence about text in specialized domains that’s less common on the open web, since there’s less of it out there, and people are more explicit about where they’re getting it.

**Code**

If you want code, it’s on Github. There’s some in other places too, but if you’ve exhausted Github, you probably aren’t going to find orders of magnitude of additional code data. (I think?)

We’ve more-or-less exhausted Github. It’s been scraped a few times with different kinds of filtering, which yielded broadly similar data sizes:

-   The Pile’s scrape had 631GB[^note-12] of text, and ~299B tokens
    
-   The MassiveText scrape had 3.1TB of text, and 506B tokens
    
-   The PaLM scrape had only 196GB of text (we aren’t told how many tokens)
    
-   The Codex paper’s scrape was python-only and had 159GB of text
    

(The text to token ratios vary due to differences in how whitespace was tokenized.)

All of these scrapes contained a large fraction of the total code available on Github (in the Codex paper’s case, just the python code).

Generously, there might be **~1T** **tokens** of code out there, but not vastly more than that.

**Arxiv**

If you want to train a model on advanced academic research in physics or mathematics, you go to Arxiv.

For example, Arxiv was about half the training data for the math-problem-solving LM [Minerva.](https://arxiv.org/abs/2206.14858)

We’ve exhausted Arxiv. Both the Minerva paper and the Pile use basically all of Arxiv, and it amounts to a measly **21B tokens**.

**Books**

Books? What exactly are “books”?

In the Pile, “books” means the Books3 corpus, which means “[all of Bibliotik](https://twitter.com/theshawwn/status/1320282149329784833?lang=en).” It contains 196,640 full-text books, amounting to only **27B tokens**.

In MassiveText, a mysterious subset called “books” has **560B tokens**. That’s a lot more than the Pile has! Are these all the books? In . . . the world? In . . . Google books? Who even knows?

In the GLaM/PaLM dataset, an equally mysterious subset called “books” has **390B tokens.**

Why is the GLaM/PaLM number so much smaller than the MassiveText number? Is it a tokenization thing? Both of these datasets were made by Google, so it’s not like the Gopher authors have special access to some secret trove of forbidden books (I assume??).

If we want LMs to learn the kind of stuff you learn from books, and not just from the internet, this is what we have.

As with the web, it’s hard to know what to make of it, because we don’t know whether this is “basically all the books in the world” or just some subset that an engineer pulled at one point in time[^note-13].

### “all the data we have” ^all-the-data-we

In my [spreadsheet](https://docs.google.com/spreadsheets/d/1zsahRIxNnXSq9z9tEHbISCkYxsivnDG9V3LbJLJTL90/edit?usp=sharing), I tried to make a rough, erring-on-generous estimate of what you’d get if you pooled together all the sub-corpora mentioned in the papers I’ve discussed here.

I tried to make it an overestimate, and did some extreme things like adding up both MassiveWeb _and_ the GLaM/PaLM web corpus as though they were disjoint.

The result was **~3.2T** tokens, or

-   about 1.6x the size of MassiveText
    
-   about 35% of the data we would need to train palm\_opt
    

Recall that this already contains “basically all” of the open-source code in the world, and “basically all” of the theoretical physics papers written in the internet era—within an order of magnitude, anyway. In these domains, the “low-hanging fruit” of data scaling are not low-hanging at all.

## what is compute? (on a further barrier to data scaling) ^what-is-compute-on

Here’s another important comment from the PaLM paper’s Chinchilla discussion. This is about barriers to doing a head-to-head comparison experiment:

> If the smaller model were trained using fewer TPU chips than the larger model, this would proportionally increase the wall-clock time of training, since the total training FLOP count is the same. If it were trained using the same number of TPU chips, it would be very difficult to maintain TPU compute efficiency without a drastic increase in batch size. The batch size of PaLM 540B is already 4M tokens, and it is unclear if even larger batch sizes would maintain sample efficiency.

In LM scaling research, all “compute” is treated as fungible. There’s one resource, and you spend it on params and steps, where compute = params \* steps.

But params can be _parallelized_, while steps cannot.

You can take a big model and spread it (and its activations, gradients, Adam buffers, etc.) across a cluster of machines in various ways. This is how people scale up $N$ in practice.

But to scale up $D$, you have to either:

-   take more optimization steps—an inherently serial process, which takes linearly more time as you add data, no matter how fancy your computers are
    
-   increase the batch size—which tends to degrade model quality beyond a certain critical size, and current high-$N$ models are already pushing against that limit
    

Thus, it is unclear whether the “compute” you spend in high-$D$ models is as readily available (and as bound to grow over time) as we typically imagine “compute” to be.

If LM researchers start getting serious about scaling up data, no doubt people will think hard about this question, but that work has not yet been done.

## appendix: to infinity ^appendix-to-infinity

Earlier, I observed that Chinchilla beats any Gopher of arbitrary size.

The graph below expands on that observation, by including two variants of each model:

-   one with the finite-model term set to zero, i.e. the infinite-parameter limit
    
-   one with the finite-data term set to zero, i.e. the infinite-data limit
    

(There are two x-axes, one for data and one for params. I included the latter so I have a place to put the infinite-data models without making an infinitely big plot.

The dotted line is Chinchilla, to emphasize that it beats infinite-params Gopher.)

![](https://www.greaterwrong.com/proxy-assets/2J8VVT915EVVEFIRJJTGP7H2TV)

The main takeaway IMO is the size of the gap between ∞ data models and all the others. Just another way of emphasizing how skewed these models are toward $N$, and away from $D$.

[^cite-1]: [Training Compute-Optimal Large Language Models](https://www.deepmind.com/publications/an-empirical-analysis-of-compute-optimal-large-language-model-training)
[^note-2]: See their footnote 2
[^note-3]: See their equation (10)
[^note-4]: Is 0.052 a “small” amount in some absolute sense? Not exactly, but (A) it’s small compared to the loss improvements we’re used to seeing from new models, and (B) small compared to the improvements possible by scaling data. In other words, (A) we have spent a few years plucking low-hanging fruit much bigger than this, and (B) there are more such fruit available.
[^note-5]: The two terms are still a bit imbalanced, but that’s largely due to the “Approach 3 vs 1/2” nuances mentioned above.
[^note-6]: Caveat: Gopher and Chinchilla were trained on the same data distribution, but these other models were not. Plugging them into the equation won’t give us accurate loss values for the datasets they used. Still, the datasets are close enough that the broad trend ought to be accurate.
[^note-7]: Wait, isn’t that _smaller_ than Chinchilla? This is another Approach 3 vs. 1⁄2 difference. Chinchilla was designed with Approaches 1⁄2. Using Approach 3, like we’re doing here, give you a Chinchilla of only 33B params, which _is_ lower than our palm\_opt’s 63B.
[^cite-8]: Seriously, I can’t find _anything_ about it in the [Gopher paper](https://arxiv.org/abs/2112.11446). Except that it was “collected in November 2020.”
[^note-9]: It is not even clear that this multilingual-ization affected the web corpus at all. Their datasheet says they “used multilingual versions of Wikipedia and conversations data.” Read literally, this would suggest they _didn’t_ change the web corpus, only those other two. I also can’t tell if the original GLaM web corpus was English-only to begin with, since that paper doesn’t say.
[^cite-10]: This ablation only compared filtered web data to _completely_ unfiltered web data, which is not a very fine-grained signal. (If you’re interested, EleutherAI has done [more extensive experiments](https://arxiv.org/pdf/2109.00698.pdf) on the impact of filtering at smaller scales.)
[^cite-11]: They are being a little coy here. The current received wisdom by now is that repeating data is _really bad_ for LMs and you should never do it. See [this paper](https://arxiv.org/pdf/2107.06499.pdf) and [this one](https://arxiv.org/pdf/2205.10487.pdf).   **EDIT 11/15/22:** but see also [the Galactica paper](https://galactica.org/static/paper.pdf), which casts significant doubt on this claim.
[^note-12]: The Pile authors only included a subset of this in the Pile.
[^note-13]: The MassiveText datasheet says only that “the books dataset contains books from 1500 to 2008,” which is not especially helpful.
