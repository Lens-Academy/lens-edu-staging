---
title: "Editing Advice for EA Forum Users"
author:
  - "Justis"
source_url: "https://forum.effectivealtruism.org/posts/hJ9T6AbTAZFzYEx7s/editing-advice-for-ea-forum-users"
published: 2022-04-22
created: 2026-10-02
accessed: 2026-10-02
llm-review:
  date: 2026-10-02
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-02
    kind: "live"
description: "Ok, I fibbed. This is a crosspost of Editing Advice for LessWrong Users, but I suspect there is a decent amount of overlap between the sorts of editi…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Ok, I fibbed. This is a crosspost of [Editing Advice for LessWrong Users](https://www.lesswrong.com/posts/5e49dHLDJoDpeXGnh/editing-advice-for-lesswrong-users), but I suspect there is a decent amount of overlap between the sorts of editing advice most useful for these two forums.

## Who am I? ^who-am-i

I'm an editor who does [feedback requests](https://www.lesswrong.com/posts/nsCwdYJEpmW5Hw5Xm/lesswrong-is-providing-feedback-and-proofreading-on-drafts) for LessWrong. Many of these feedback requests are for proofreading/clarity of language, so I have lots of experience reading community draft posts and helping improve them. I want to share some high level takeaways - low effort self-editing techniques that, based on my[\[1\]](https://www.lesswrong.com/posts/5e49dHLDJoDpeXGnh/editing-advice-for-lesswrong-users#fngx4853recmp) experience, I think many to most LW posters could benefit from.

## Disclaimers ^disclaimers

I wrote all the example text in this post myself. I make no claims that any of it is reasonable on the object level - it's just meant to resemble lots of the stuff I edit.

Bolded text in examples is for emphasis of the points under discussion, not a sign that it would make sense to actually bold those words or phrases.

As usual, [reverse advice](https://slatestarcodex.com/2014/03/24/should-you-reverse-any-advice-you-hear/) as necessary.

## What's the advice? ^whats-the-advice

Here's my main advice, in decreasing order of confidence - I'll elaborate on each:

1.  Beware "this"
2.  Don't let hedging be a tic
3.  Break up run-on sentences
4.  Use more links, images, examples, and commas

### Beware "this" ^beware-this

**The problem:** many sentences on LessWrong begin with "this". At worst, the thing "this" is pointing to is fully ambiguous between multiple live options, making it impossible to parse the author's intended meaning. But even in milder cases, it can waste a few seconds for the reader to trace out what a post is talking about.

**The solution:** scan through your draft for words like "this" or "that" (but for whatever reason overwhelmingly "this" specifically), and when in doubt about clarity, just replace them with whatever their intended antecedents are.

**An example:** 

> Many key figures in the community have been shortening their timelines recently, since major advances just keep coming one after the other. **This** is especially worrying, especially compared to discussions of "AI winter" just a few years ago.

What, precisely, does "this" point to in the sentence above? The fact of key figures shortening their timelines? The major advances? When we get later in the sentence and see that we're comparing whatever "this" is to "discussions", we can infer that we're talking about the shortening of timelines (vs. the actual technical advances), but it takes up precious reader bandwidth to figure this out, or, worse, the reader becomes overloaded by ambiguity and unconsciously switches to "skimming mode".

Individually, overuse of "this" isn't a big deal. But it adds up. It's the single greatest contribution to a [hand-wavy](https://en.wiktionary.org/wiki/handwavy) feeling in the posts I review, like maybe the author isn't totally sure what they're saying. And it's easy to avoid! Just ctrl-f "this" and go to town!

### Don't let hedging be a tic ^dont-let-hedging-be

**The problem:** LessWrongers care a _lot_ about making factually accurate claims. This (_gasp!)_ is a virtue. But like any virtue, it's vulnerable to [Goodharting](https://en.wikipedia.org/wiki/Goodhart%27s_law): when people learn that hedging is a sign of epistemic responsibility, you end up with a whole lot of hedging. Occasionally, you actually end up with hedging that is logically incoherent or actively redundant.

**The solution:** Make sure you hedge precisely as much as necessary, and especially make sure you don't hedge the same claim multiple times in the same way. If "you suspect" something "might" happen, it doesn't also have to be "possible" that it "could" have "potentially" significant effects.

**An example:**

> The other salient quality of insect suffering is its sheer scale. Insects are the most populous animals on the planet, so it **may be** that **if** their suffering is morally relevant **at all**, **I believe** it **could** swamp **almost any** other considerations about animal welfare. 

Some hedging is virtuous here. We're dealing with uncertainty, so it'd be misleading to follow typical writing guides and say something bold like: "Because there are so many insects, their suffering adds up to more than that of larger animals." But in this example, the writer has gone too far. Taken literally, they are speculating on _their own belief_, and not any object level claim. But they have direct access to their belief! They can just say what they believe full stop, and have easier-to-read _and_ more literally accurate text. Something like:

> Insects are the most populous animals on the planet, so **I believe** that if they can suffer in a morally relevant way, their suffering in aggregate **might** exceed that of larger animals.

We're importantly still hedging here! We're just not doing it in so many layers of the hypothetical that it becomes hard to read and incoherent when fully parsed.

### Break up run-on sentences ^break-up-run-on-sentences

**The problem:** LessWrongers tend to write really long sentences. It's an understandable temptation: we're often talking about genuinely complex ideas, and the sentence is traditionally the vehicle for transmitting a single idea. But I think there's some Goodharting here, too. Many of LessWrong's top authors have a breathless, low-punctuation style, which others try to emulate. That style is fine if you're good at it, but it's dangerous for beginners or people less confident in their writing.

People read differently. Some people, like me, tend to actively hear text using their inner voice. It's harder to parse super duper long sentences for people like us. And even for people who have a different cognitive experience of reading, I suspect very long sentences cause some overload. Plus, it's easier to get lost as a writer in long sentences, too, and fall into sloppier thinking/excess hedging/hand-waving.

**The solution:** Keep it tight! Sometimes this requires replacing entire sentences rather than tuning them internally. But it's worth it, and an external editor may not be bold enough (or have enough time) to suggest this kind of change, so it's extra good to do it yourself.

 **An example:**

> We have to worry about mesa optimizers even if we can guarantee that the outer level optimizer is myopic and we don't currently have any promising solutions to this issue, though robust interpretability tools could help us figure out and take preventative measures against mesa optimizers as they arise. 

Sentences like this one are hard to read, and there are too many opportunities for sneaky ambiguity or hand-waving. Here's a broken up version:

> We might hope that myopia could protect us from unexpected goals or behaviors. But even if an outer level optimizer is provably myopic, it might chance upon a mesa optimizer that isn't. We don't have any current techniques to get around this issue, though interpretability tools seem promising here: if we can see mesa optimizers as they arise, we may be able to quash dangerous ones early.

This rework is a little longer, but I think it's a lot clearer. Readers should immediately know what the writer is talking about, and can take issue with the individual points atomically, rather than having a vague feeling that something might be off or confusing.

### Use more links, images, examples, and commas ^use-more-links-images

**The problem:** A lot of writing in LessWrong is high context. And worse, sometimes different people have different interpretations of that context. I've noticed in particular people taking "Goodhart" to mean anything from "A measure made a goal ceases to be a good measure" to "Literally stated objectives and fuzzily meant objectives diverge dangerously at the limit". These interpretations rhyme, but if you just say "Goodhart" and leave it at that, then, well, your readers' interpretations may _also_ diverge at the limit. Plus you may have a new reader to the site who just gives up from too many terms and acronyms they don't recognize.

**The solution:** Aim your writing to people who know significantly less than your actual target audience. You may be overestimating your target audience's understanding, or their median attention span, or the degree to which their precise interpretations of terms align with your own. So use lots of links, diagrams and examples for bonus opportunities to let something "click", and commas to help readers parse conceptual boundaries within sentences.

**An example:**

> It's clearly past time for someone to pull the fire alarm but it isn't clear either what the fire alarm mechanism is or who could actually pull it.

We're assuming readers are familiar with this "fire alarm" term. Linking the original post, plus adding a comma, makes for a much better reader experience:

> It's clearly past time for someone to pull the [fire alarm](https://intelligence.org/2017/10/13/fire-alarm/), but it isn't clear either what the fire alarm mechanism is or who could actually pull it.

One other benefit of going to find the link is you might realize that your interpretation of a term is a little off. I chose the "fire alarm" example because the entire point of the introducing post is that there _isn't_ a fire alarm. Discovering this could be a good chance to drop the term and say something more aligned (but less jargon-y) that better captures your meaning, like:

> It's clearly past time for it to be common knowledge that AGI is dangerously close, but it isn't clear how best to communicate this fact to key players such as top labs, governments, and arguably the public at large.

Sometimes when trying to remove a term that means something a little different than you thought, you'll discover that you _didn't_ actually have a crisp meaning behind the term, and that rephrasing something in your own words is hard. This confusion (and noticing it) is a feature, not a bug.

## Putting it all together ^putting-it-all-together

Here's a final example of some text that could be significantly improved, just by keeping the points in this post in mind:

> Top researchers are exploring many directions like **corrigibility**, **interpretability**, **safety through debate** and **myopia** but **I think** the general consensus is that none seems **particularly likely** to be **promising** yet, and worse it's not clear more money or even more **marginal** researchers might help **very much** with **this**.

Bolded words aren't necessarily problematic, just things that an editing process of the type I'm advocating here would flag. Here's one possible rewrite:

> Top AGI researchers are exploring a variety of research directions, including [corrigibility](https://ai-alignment.com/corrigibility-3039e668638), [interpretability](https://distill.pub/2018/building-blocks/), [safety through debate](https://www.lesswrong.com/posts/Br4xDbYu4Frwrb64a/writeup-progress-on-ai-safety-via-debate-1), and [myopia](https://www.lesswrong.com/tag/myopia). But there's no consensus view that any of these, or others I've left out, are especially promising. Worse, it's not clear how to either make current avenues of research more effective, or to find new avenues that might work better: neither more money nor more researchers would necessarily do the trick.

It's easier to disagree with this reworked version - the choice of links may not be optimal, the claims are more direct, and it's simply easier to understand what the author is trying to say. It can be uncomfortable to write in a clearer, more beginner-friendly style, but in my view, the rewards are worth it.

## Addendum ^addendum

Editing is hard, and requires lots of practice. And while self-editing is valuable, seeking the opinions of others is one of the most effective techniques of all. Don't be shy about asking for feedback in whatever channels are available to you!
