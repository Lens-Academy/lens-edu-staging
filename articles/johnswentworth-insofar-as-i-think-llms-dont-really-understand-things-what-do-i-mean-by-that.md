---
title: "Insofar As I Think LLMs “Don’t Really Understand Things”, What Do I Mean By That?"
author:
  - "johnswentworth"
source_url: "https://www.lesswrong.com/posts/trzFrnhRoeofmLz4e/insofar-as-i-think-llms-don-t-really-understand-things-what"
published: 2025-11-08
created: 2026-09-11
accessed: 2026-09-11
llm-review:
  date: 2026-09-11
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-11
    kind: "live"
description: "When I put on my LLM skeptic hat, sometimes I think things like “LLMs don’t really understand what they’re saying”. What do I even mean by that? What’s my mental model for what is and isn’t going on inside LLMs minds? First and foremost: the phenomenon precedes the model. That is, when interacting with LLMs, it sure feels like there’s something systematically missing which one could reasonably call “understanding”. I’m going to articulate some mental models below, but even if I imagine all those mental models are wrong, there’s still this feeling that LLMs are missing something and I’m not quite sure what it is."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

When I put on my LLM skeptic hat, sometimes I think things like “LLMs don’t really understand what they’re saying”. What do I even mean by that? What’s my mental model for what is and isn’t going on inside LLMs minds?

First and foremost: the phenomenon precedes the model. That is, when interacting with LLMs, it sure feels like there’s something systematically missing which one could reasonably call “understanding”. I’m going to articulate some mental models below, but even if I imagine all those mental models are wrong, there’s still this feeling that LLMs are missing something and I’m not quite sure what it is.

That said, I do have some intuitions and mental models for what the missing thing looks like. So I’ll run the question by my intuitions a few times, and try to articulate those models.

## First Pass: A Bag Of Map-Pieces ^first-pass-a-bag

Imagine taking a map of the world, then taking a bunch of pictures of little pieces of the map—e.g. one picture might be around the state of Rhode Island, another might be a patch of Pacific Ocean, etc. Then we put all the pictures in a bag, and forget about the original map.

A smart human-like mind looking at all these pictures would (I claim) assemble them all into one big map of the world, like the original, either physically or mentally.

An LLM-like mind (I claim while wearing my skeptic hat) doesn’t do that. It just has the big bag of disconnected pictures. Sometimes it can chain together three or four pictures to answer a question, but anything which requires information spread across too many different pictures is beyond the LLM-like mind. It would, for instance, never look at the big map and hypothesize continental drift. It would never notice if there’s a topological inconsistency making it impossible to assemble the pictures into one big map.

## Second Pass: Consistent Domains ^second-pass-consistent-domains

Starting from the map-in-a-bag picture, the next thing which feels like it’s missing is something about inconsistency.

For example, when tasked with proving mathematical claims, a common pattern I’ve noticed from LLMs is that they’ll define a symbol to mean one thing… and then make some totally different and incompatible assumption about the symbol later on in the proof, as though it means something totally different.

Bringing back the map-in-a-bag picture: rather than a geographical map, imagine lots of little pictures of a crystal, taken under an electron microscope. As with the map, we throw all the pictures in a bag. A human-like mind would try to assemble the whole thing into a globally-consistent picture of the whole crystal. An LLM-like mind will kinda… lay out a few pieces of the picture in one little consistent pattern, and then separately lay out a few pieces of the picture in another little consistent pattern, but at some point as it’s building out the two chunks they run into each other (like different crystal domains, but the inconsistency is in the map rather than the territory). And then the LLM just forges ahead without doing big global rearrangements to make the whole thing consistent.

That’s the mental picture I associate with the behavior of LLMs in proofs, where they’ll use a symbol to mean one thing in one section of the proof, but then use it in a totally different and incompatible way in another section.

## Third Pass: Aphantasia ^third-pass-aphantasia

What’s the next thing which feels like it’s missing?

Again thinking about mathematical proofs… the ideal way I write a proof is to start with an intuitive story/picture for why the thing is true, and then translate that story/picture into math and check that all the pieces follow as my intuition expects.[^note-1]

Coming back to the map analogy: if I were drawing a map, I’d start with this big picture in my head of the whole thing, and then start filling in pieces. The whole thing would end up internally consistent by default, _because_ I drew each piece to match the pre-existing picture in my head. Insofar as I draw different little pieces in a way that doesn’t add up to a consistent big picture, that’s pretty strong evidence that I _wasn’t_ just drawing out a pre-existing picture from my head.

I’d weakly guess that aphantasia induces this sort of problem: an aphantasic, asked to draw a bunch of little pictures of different parts of an object or animal or something, would end up drawing little pictures which don’t align with each other, don’t combine into one consistent picture of the object or animal.

That’s what LLMs (and image generators) feel like. It feels like they have a bunch of little chunks which they kinda stitch together but not always consistently. That, in turn, is pretty strong evidence that they’re not just transcribing a single pre-existing picture or proof or whatever which is already “in their head”. In that sense, it seems like they lack a unified mental model.

## Fourth Pass: Noticing And Improving ^fourth-pass-noticing-and

A last piece: it does seem like, as LLMs scale, they are able to assemble bigger and bigger consistent chunks. So do they end up working like human minds as they get big?

Maybe, and I think that’s a pretty decent argument, though the scaling _rate_ seems pretty painful.

My counterargument, if I’m trying to play devil’s advocate, is that humans seem to notice this sort of thing in an online way. We don’t need to grow a 3x larger brain in order to notice and fix inconsistencies. Though frankly, I’m not that confident in that claim.

[^note-1]: I don’t always achieve that ideal; sometimes back-and-forth between intuition and math is needed to flesh out the story and proof at the same time, which is what most of our meaty research looks like.
