---
title: "OK, what's the difference between coherence and representation theorems?"
author:
  - "Algon"
source_url: "https://www.lesswrong.com/posts/XmQMBPewwLrBrJq2w/ok-what-s-the-difference-between-coherence-and"
published: 2026-02-10
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "TL;DR Is a coherence theorem anything that says \"if you aren't coherent in some way you predictably have to forgo some sort of resource or be exploit…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

TL;DR Is a coherence theorem anything that says "if you aren't coherent in some way you predictably have to forgo some sort of resource or be exploitable in some way" and a representation theorem anything that says "rational cognitive structures can be represented by some variant of expected utility maximization?" Is there no difference? One a subset of another? Some secret fourth thing? 

---

Just today, I was arguing that [Savage's subjective expected utility model](https://en.wikipedia.org/wiki/Savage%27s_subjective_expected_utility_model) should be called a representation theorem, as wikipedia claims, for [an article](https://docs.google.com/document/d/1LFU3LYKfqBFtCwr0Bb30rQL3fwfYHmEbgkRcKzxaPzc/edit?tab=t.0) my co-worker was writing, as opposed to a coherence theorem. My opponent, taking the bold stance that Wikipedia may not be the end all and be all of the discussion, and that he wasn't sold on it being a representation theorem in spite of the fact that you're representing one structure (preferences between deals dependant on unknown world states) using another (subjective expected utility), as in [representation theory](https://www.math.columbia.edu/~woit/QM/qmbook.pdf).  

Unwilling to accept this lack of decisive resolution, I turned to that other infallible oracle, [Stampy](https://aisafety.info/chat/). (Stampy's received some hefty upgrades recently, so it's even more infallible than before!) Stampy demured, and informed me that the literature on AI safety doesn't clearly distinguish between the two. 

Undaunted, I delved into the literature myself and I found the [formerly rightful caliph](https://www.lesswrong.com/users/eliezer_yudkowsky) (sort of) [opining on this very topic](https://www.lesswrong.com/posts/yCuzmCsE86BTu9PfA/there-are-no-coherence-theorems#4HbK8ZPqDSaun9EXh). 

> The author doesn't seem to realize that there's a difference between representation theorems and coherence theorems.
> 
> > The Complete Class Theorem says that an agent’s policy of choosing actions conditional on observations is not strictly dominated by some other policy (such that the other policy does better in some set of circumstances and worse in no set of circumstances) if and only if the agent’s policy maximizes expected utility with respect to a probability distribution that assigns positive probability to each possible set of circumstances.
> > 
> > This theorem does refer to dominated strategies. However, the Complete Class Theorem starts off by assuming that the agent’s preferences over actions in sets of circumstances satisfy Completeness and Transitivity. If the agent’s preferences are not complete and transitive, the Complete Class Theorem does not apply. So, the Complete Class Theorem does not imply that agents must be representable as maximizing expected utility if they are to avoid pursuing dominated strategies.
> 
> Cool, I'll complete it for you then.
> 
> Transitivity:  Suppose you prefer A to B, B to C, and C to A.  I'll keep having you pay a penny to trade between them in a cycle.  You start with C, end with C, and are three pennies poorer.  You'd be richer if you didn't do that.
> 
> Completeness:  Any time you have no comparability between two goods, I'll swap them in whatever direction is most useful for completing money-pump cycles.  Since you've got no preference one way or the other, I don't expect you'll be objecting, right?
> 
> Combined with the standard Complete Class Theorem, this now produces the existence of at least one coherence theorem.  The post's thesis, "There are no coherence theorems", is therefore falsified by presentation of a counterexample.  Have a nice day! 

Returning to my meddlesome peer, I did spake unto him that savage's representation theorem was not a coherence theorem, for there was no mention of a exploitability, as in the Dutch Book theorems. Rather, Savage's theorem was akin to [Von Neuman and Morgenstern's](https://aisafety.info/questions/NM5N/What-is-the-Von-Neumann-Morgenstern-VNM-utility-theorem).  
  
But alas! He did not yield and spake unto me: "IDK man, seems like there's not a consensus and this is too in the weeds for a beginner's article". Or something. I forget.  So now I must ask you to adjudicate, dear readers. What the heck is the difference between a coherence theorem and a representation theorem?
