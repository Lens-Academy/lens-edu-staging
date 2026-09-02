---
title: "Forecasting Transformative AI, Part 1: What Kind of AI?"
source_url: https://www.cold-takes.com/transformative-ai-timelines-part-1-of-4-what-kind-of-ai/
author:
  - "Holden Karnofsky"
published: 2021-08-10
created: 2026-02-13
description: "PASTA: Process for Automating Scientific and Technological Advancement."
tags:
  - "obsidian-web-clipper"
llm-review:
  date: 2026-08-28
  model: "gpt-5.6-terra"
  version: "article-qc-v1.1"
  source:
    fetched: 2026-08-28
    kind: "live"
---
%%
Add discussion note here:

...

%%
*Audio also available by searching Stitcher, Spotify, Google Podcasts, etc. for "Cold Takes Audio"*


This is the first of four posts summarizing hundreds of pages of technical reports focused almost entirely on forecasting one number. It's the single number I'd probably most value having a good estimate for: the **year by which transformative AI will be developed.**[^note-karnofsky-1]

By "transformative AI," I mean "AI powerful enough to bring us into a new, qualitatively different future." The [Industrial Revolution](https://www.vox.com/future-perfect/2018/11/8/18052076/human-history-in-one-chart-industrial-revolution) is the most recent example of a transformative event; others would include the Agricultural Revolution and the emergence of humans.[^cite-karnofsky-2]

This piece is going to focus on exploring a particular kind of AI I believe could be transformative: **AI systems that can essentially automate all of the human activities needed to speed up scientific and technological advancement.** I will call this sort of technology Process for Automating Scientific and Technological Advancement, or **PASTA.**[^note-karnofsky-3] (I mean PASTA to refer to either a single system or a collection of systems that can collectively do this sort of automation.)

PASTA could resolve the same sort of bottleneck discussed in [The Duplicator](https://www.cold-takes.com/the-duplicator/) and [This Can't Go On](https://www.cold-takes.com/this-cant-go-on/) - the **scarcity of human minds (or something that plays the same role in innovation)**.

PASTA could therefore lead to **[explosive science](https://www.cold-takes.com/this-cant-go-on/#scientific-and-technological-advancement)**, culminating in technologies as impactful as [digital people](https://www.cold-takes.com/how-digital-people-could-change-the-world/). And depending on the details, PASTA systems could have objectives of their own, which could be **dangerous for humanity** and could matter a great deal for [what sort of civilization ends up expanding through the galaxy](https://www.cold-takes.com/all-possible-views-about-humanitys-future-are-wild/).

By talking about PASTA, I'm partly trying to get rid of some unnecessary baggage in the debate over "artificial general intelligence." I don't think we need artificial *general* intelligence in order for this century to be the most important in history. Something narrower - as PASTA might be - would be plenty for that.

To make this idea feel a bit more concrete, the rest of this post will discuss:

- How PASTA could (hypothetically) be developed via roughly modern-day machine learning methods.
- Why this could lead to explosive scientific and technological progress - and why it could be dangerous via PASTA systems having objectives of their own.

Future pieces will discuss how soon we might expect something like PASTA to be developed.

## Making PASTA ^making-pasta

I'll start with a very brief, simplified characterization of machine learning, which you can skip by clicking [[#^could-pasta-be-developed-via-machine-learning|here]].

There are essentially two ways to "teach" a computer to do a task:

**Traditional programming.** In this case, you code up extremely specific, step-by-step instructions for completing the task. For example, the chess-playing program [Deep Blue](https://en.wikipedia.org/wiki/Deep_Blue_\(chess_computer\)) is essentially executing instructions [^note-karnofsky-4] along the lines of:

- Receive a digital representation of a chessboard, with numbers indicating (a) which chess piece is on each square; (b) which moves would be legal; (c) which board positions would count as checkmate.
- Check how each legal move would modify the board. Then check how "good" that resulting board is, according to rules like: "If the other player's queen has been captured, that's worth 9 points; if Deep Blue's queen has been captured, that's worth -9 points." These rules could be quite complex,[^note-karnofsky-5] but they've all been coded in precisely by humans.

**Machine learning.** This is essentially "training" an AI to do a task by trial and error, rather than by giving it specific instructions. Today, the most common way of doing this is by using an "artificial neural network" (ANN), which you might think of sort of like a "digital brain" that starts in an empty (or random) state: it hasn't yet been wired to do specific things.

For example, [AlphaZero](https://en.wikipedia.org/wiki/AlphaZero) - an AI that has been used to master multiple board games including chess and Go - does something more like this (although it has important elements of "traditional programming" as well, which I'm ignoring for simplicity):

- Plays a chess game against itself (by choosing a legal move, modifying the digital game board accordingly, and then choosing another legal move, etc.) Initially, it's playing by making random moves.
- Every time White wins, it "learns" a small amount, by tweaking the wiring of the ANN ("digital brain") - literally by strengthening or weakening the connections between some "artificial neurons" and others. The tweaks cause the ANN to form a stronger association between game states like what it just saw and "White is going to win." And vice versa when Black wins.
- After a very large number of games, the ANN has become very good at determining - from a digital board game state - which side is likely to win. The ANN can now select moves that make its own side more likely to win.
- The process of "training" the ANN takes a very large amount of trial-and-error: it is initially terrible at chess, and it needs to play a lot of games to "wire its brain correctly" and become good. Once the ANN has been trained once, though, its "digital brain" is now consistently good at the board game it's learned; it can beat its opponents repeatedly.

The latter approach is central for a lot of the recent progress in AI. This is especially true for tasks that are hard to “write down all the instructions” for. For example, humans are able to write down some reasonable guidelines for succeeding at chess, but we know very little about how we ourselves classify images (determine whether some image is of a dog, cat, or something else). So machine learning is particularly essential for tasks like classifying images.

### Could PASTA be developed via machine learning? ^could-pasta-be-developed-via-machine-learning

One obvious (but unrealistic) way of doing this might be something like this:

- Instead of playing chess, an AI could play a game called "Cause scientific and technological advancement." That is, it could make “moves” like: download scientific papers, add notes to a file, create designs and instructions for new experiments, design manufacturing processes.
- A panel of human judges could watch from the “sidelines” and give their subjective rating of how fast the AI’s work is causing scientific/technological advancement. The AI could therefore tweak its wiring over time, learning which sorts of moves most effectively cause scientific and technological advancement according to the judges.

This would be wildly impractical, at least compared to how I think things are more likely to play out, but it hopefully gives a starting intuition for what a training process could be trying to accomplish: by providing a signal of "how the AI is doing," it could allow an AI to get good at the goal via trial-and-error and tweaking its internal wiring.

In reality, I'd expect training to be faster and more practical due to things like:

- Different AIs could be trained to perform different sorts of roles related to speeding up science and technology: writing academic papers, designing and critiquing blueprints and manufacturing processes, etc. In many cases, humans already engaged in these activities could generate a lot of data on what it looks like to do them well, which could be used for the sort of training described above. Once different AIs could perform a variety of key roles, "manager" AIs could be trained to oversee and allocate the work of other AIs.
- AIs could also be trained as *judges*. Perhaps one AI could be trained to assess whether a paper contains original ideas, and another could be trained to assess whether a paper contains errors.[^note-karnofsky-6] These "judge" AIs could then be used to more efficiently train a third AI learning to write original, correct papers.
- More generally, AIs could learn to do all sorts of other human activities, gaining generic human abilities like the ability to learn from textbooks and the ability to "brainstorm creative solutions to a problem." AIs good at these things could then learn science from textbooks like a normal human, and brainstorm about how to make a breakthrough just like a normal human, etc.
	- The distinction here is between "using huge numbers of examples to wire a brain" and "an already-wired brain using small amounts of examples to learn quickly, as a human brain does."
	- Here it would take lots of trial and error for the ANN to become good at "generic" human abilities, but after that the trained ANN could learn how to do specifically *scientific* work as efficiently as a human learns to do it. (In a sense you could imagine that it's been "trained via massive trial-and-error *to have the ability to learn certain sorts of things without needing as much trial-and-error.*")
	- There is some preliminary evidence (for example, [here](https://openai.com/blog/improving-language-model-behavior/)) that AI systems could go through this pattern of "Learning 'the basics' using a ton of trial-and-error, and learning specific sub-skills using less trial-and-error." [^note-karnofsky-7]
- I don't particularly expect all of this to happen as part of a single, deliberate development process. Over time, I expect different AI systems to be used for different and increasingly broad tasks, including and especially tasks that help complement human activities on scientific and technological advancement. There could be many different types of AI systems, each with its own revenue model and feedback loop, and their collective abilities could grow to the point where at some point, some set of them is able to do everything (with respect to scientific and technological advancement) that formerly required a human. (For convenience, though, I'll sometimes refer to such a set as PASTA in the singular.)

Developing PASTA will almost certainly be hugely harder and more expensive than it was for AlphaZero. It may require a lot of ingenuity to get around obstacles that exist today (the picture above is surely radically oversimplified, and is there to give basic intuitions). But AI research is simultaneously getting cheaper [^note-karnofsky-8] and better-funded. I'll argue in future pieces that the odds of developing PASTA in the coming decades are substantial.

## Impacts of PASTA

### Explosive scientific and technological advancement ^explosive-scientific-and-technological-advancement

I've previously talked about the idea of a potential [explosion in scientific and technological advancement](https://www.cold-takes.com/this-cant-go-on/#scientific-and-technological-advancement), which could lead to a [radically unfamiliar future](https://www.cold-takes.com/how-digital-people-could-change-the-world/).

I've emphasized that such an explosion could be caused by a technology that "dramatically increased the number of 'minds' (humans, or [digital people](https://www.cold-takes.com/how-digital-people-could-change-the-world/), or advanced AIs) pushing forward scientific and technological advancement."

PASTA would fit this bill well, particularly if it were as good as humans (or better) at finding better, cheaper ways to make more PASTA systems. PASTA would have **all of the tools for a productivity explosion that I previously laid out for [digital people](https://www.cold-takes.com/how-digital-people-could-change-the-world/)**:

- PASTA systems could make copies of themselves, including temporary copies, and run them at different speeds.
- They could engage in the sort of loop described in [The Duplicator](https://www.cold-takes.com/the-duplicator/): "more ideas \[including ideas for making more/better PASTA systems\] → more people \[in this case more PASTA systems\] → more ideas→..."
![](https://storage.ghost.io/c/c1/87/c187484b-b759-4728-8cb3-1c009c2c024e/content/images/size/w1000/2021/09/pasta-stills-1.png)

![](https://storage.ghost.io/c/c1/87/c187484b-b759-4728-8cb3-1c009c2c024e/content/images/size/w1000/2021/09/pasta-stills-2.png)

![](https://storage.ghost.io/c/c1/87/c187484b-b759-4728-8cb3-1c009c2c024e/content/images/size/w1000/2021/09/pasta-stills-3.png)

Thanks to María Gutiérrez Rojas for these graphics, a variation on similar graphics from [The Duplicator](https://www.cold-takes.com/the-duplicator/) and [Digital People Would Be An Even Bigger Deal](https://www.cold-takes.com/how-digital-people-could-change-the-world/#productivity) illustrating the dynamics of explosive growth. Here, instead of people having ideas that increase productivity, it's AI algorithms (denoted by neural network icons).

Why doesn't this feedback loop apply to today's computers and AIs? Because today's computers and AIs aren't able to do *all* of the things required to have new ideas and get themselves copied more efficiently. They play a role in innovation, but innovation is ultimately bottlenecked by humans, whose population is only growing so fast. This is what PASTA would change (it is also what [digital people](https://www.cold-takes.com/how-digital-people-could-change-the-world/) would change).

Additionally: unlike digital copies of humans, PASTA systems might not be attached to their existing identity and personality. A PASTA system might quickly make any edits to its "mind" that made it more effective at pushing science and technology forward. This might (or might not, depending on a lot of details) lead to [recursive self-improvement and an "intelligence explosion."](https://en.wikipedia.org/wiki/Technological_singularity#Background) But even if this *didn't* pan out, simply being as good as humans at making more PASTA systems could cause explosive advancement for the same reasons the [digital people could](https://www.cold-takes.com/how-digital-people-could-change-the-world/#productivity).

### Misaligned AI: mysterious, potentially dangerous objectives

If PASTA were developed as outlined [[#^making-pasta|above]], it's possible that we might know *extremely* little about its inner workings.

AlphaZero - like other modern deep learning systems - is in a sense very poorly understood. We know that it "works." But we don't really know "what it's thinking."

If we want to know why AlphaZero made some particular chess move, we can't look inside its code to find ideas like "Control the center of the board" or "Try not to lose my queen." Most of what we see is just a vast set of numbers, denoting the strengths of connections between different artificial neurons. As with a human brain, we can mostly only guess at what the different parts of the "digital brain" are doing [^note-karnofsky-9] (although there are some [early attempts](https://distill.pub/2020/circuits/zoom-in/) to do what one might call "digital neuroscience.")

The "designers" of AlphaZero (discussed above) didn't need much of a vision for how its thought processes would work. They mostly just set it up so that it would get a lot of trial and error, and evolve to get a particular result (win the game it’s playing). Humans, too, evolved primarily through trial and error, with selection pressure to get particular results (survival and reproduction - although the selection worked differently).

![](https://storage.ghost.io/c/c1/87/c187484b-b759-4728-8cb3-1c009c2c024e/content/images/2021/08/tired-terminator-inspired-pasta.png)

Like humans, PASTA systems might be good at getting the results they are under pressure to get. But like humans, they might learn along the way to think and do all sorts of other things, and it won't necessarily be obvious to the designers whether this is happening.

Perhaps, due to being optimized for pushing forward scientific and technological advancement, PASTA systems will be in the habit of taking every opportunity to do so. This could mean that they would - given the opportunity - seek to [fill the galaxy with long-lasting space settlements](https://www.cold-takes.com/how-digital-people-could-change-the-world/#lock-in) devoted to science.

Perhaps PASTA will emerge as some byproduct of another objective. For example, perhaps humans will be trying to train systems to make money or amass power and resources, and setting them up to do scientific and technological advancement will just be part of that. In which case, perhaps PASTA systems will just end up as power-and-resources seekers, and will seek to bring the whole galaxy under their control.

Or perhaps PASTA systems will end up with very weird, "random" objectives. Perhaps some PASTA system will observe that it "succeeds" (gets a positive training signal) whenever it does something that causes it to have direct control over an increased amount of electric power (since this is often a result of advancing technology and/or making money), and it will start directly aiming to increase its supply of electric power as much as possible - with the difference between these two objectives not being noticed until it becomes quite powerful. (Analogy: humans have been under selection pressure to pass their genes on, but many have ended up caring more about power, status, enjoyment, etc. than about genes.)

These are scary possibilities if we are talking about AI systems (or collections of systems) that may be more capable than humans in at least some domains.

- PASTA systems might try to fool and defeat humans in order to achieve their goals.
- They might succeed entirely, if they were able to outsmart and/or [[#^explosive-scientific-and-technological-advancement|outnumber]] humans, hack critical systems, and/or develop more powerful weapons. (Just as humans have generally been able to defeat other animals to achieve our goals.)
- Or there might be conflict between different PASTA systems with different goals, perhaps partially (but not fully) controlled by humans with goals of their own. This could lead to general chaos and a hard-to-predict, possibly very bad long-run outcome.

If you're interested in more discussion of whether an AI could or would have its own goals, I'd suggest checking out [Why AI alignment could be hard with modern deep learning](https://www.cold-takes.com/why-ai-alignment-could-be-hard-with-modern-deep-learning/) (Cold Takes guest post), [Superintelligence (book)](https://smile.amazon.com/Superintelligence-Dangers-Strategies-Nick-Bostrom-ebook/dp/B00LOOCGB2/), [The case for taking AI seriously as a threat to humanity (Vox article)](https://www.vox.com/future-perfect/2018/12/21/18126576/ai-artificial-intelligence-machine-learning-safety-alignment), [Draft report on existential risk from power-seeking AI (Open Philanthropy analysis)](https://www.alignmentforum.org/posts/HduCjmXTBD4xYTegv/draft-report-on-existential-risk-from-power-seeking-ai) or one of the many other pieces on this topic.[^note-karnofsky-10]

## Conclusion

It's hard to predict what a world with PASTA might look like, but two salient possibilities would be:

- PASTA could - by causing an explosion in the rate of scientific and technological advancement - lead quickly to something like digital people, and hence to the sorts of changes to the world described in [Digital People Would Be An Even Bigger Deal](https://www.cold-takes.com/how-digital-people-could-change-the-world/).
- PASTA could lead to technology capable of wiping humans out of existence, such as devastating bioweapons or robot armies. This technology could be wielded by humans for their own purposes, or humans could be manipulated into using it to help PASTA pursue its own ends. Either way could lead to dystopia or human extinction.

The next 3 posts will argue that PASTA is more likely than not to be developed this century.

:::collapse
**Next in series:** [Why AI alignment could be hard with modern deep learning](https://www.cold-takes.com/why-ai-alignment-could-be-hard-with-modern-deep-learning/)
:::

---

## Footnotes

[^note-karnofsky-1]: Of course, the answer could be "A kajillion years from now" or "Never."

[^cite-karnofsky-2]: See [this section of](https://docs.google.com/document/d/1IJ6Sr-gPeXdSJugFulwIpvavc0atjHGM82QjIfUSBGQ/edit#heading=h.6t4rel10jbcj) "Forecasting TAI with Biological Anchors" (Cotra (2020)) for a more full definition of "transformative AI."

[^note-karnofsky-3]: I'm sorry. But I do think the rest of the series will be slightly more fun to read this way.

[^note-karnofsky-4]: The examples here are of course simplified. For example, both Deep Blue and AlphaGo incorporate substantial amounts of "tree search," a traditionally-programmed algorithm that has its own "trial and error" process.

[^note-karnofsky-5]: And they can include simulating long chains of future game states.

[^note-karnofsky-6]: Some AIs could be used to determine whether papers are original contributions *based on how they are later cited*; others could be used to determine whether papers are original contributions *based only on the contents of the paper and on previous literature.* The former could be used to train the latter, by providing a "That's correct" or "That's wrong" signal for judgments of originality. Similar methods could be used for training AIs to assess the correctness of papers.

[^note-karnofsky-7]: E.g., [https://openai.com/blog/improving-language-model-behavior/](https://openai.com/blog/improving-language-model-behavior/)

[^note-karnofsky-8]: Due to improvements in hardware and software.

[^note-karnofsky-9]: It's even worse than [spaghetti code](https://en.wikipedia.org/wiki/Spaghetti_code).

[^note-karnofsky-10]: More books: [Human Compatible](https://smile.amazon.com/Human-Compatible-Artificial-Intelligence-Problem-ebook/dp/B07N5J5FTS), [Life 3.0](https://smile.amazon.com/Life-3-0-Being-Artificial-Intelligence-ebook/dp/B06WGNPM7V), and [The Alignment Problem](https://smile.amazon.com/Alignment-Problem-Machine-Learning-Values-ebook/dp/B085T55LGK/)