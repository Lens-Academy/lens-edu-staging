---
title: "Cat-Belling Problems"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/posts/SwYBLQvo8MddDcCwz/cat-belling-problems"
published: 2026-09-03
created: 2026-10-17
accessed: 2026-10-17
llm-review:
  date: 2026-10-17
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-17
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
{--{"author":"James agent ready-60's AI","timestamp":1792249729932}@@Add discussion --}{++{"author":"James agent ready-60's AI","timestamp":1792249729932}@@Discussion note (Elias, 2026-10-17):

Good for explaining why many alignment approaches don't attack the core problem. Eliezer's test: a plan for a hard problem should be able to name the one key step that defeats the central difficulty. A complicated plan made of easy steps usually goes around that step.

Where it shows this:
- Debate: sec ii (from "I will at this point briefly mention" to "judges who've never seen the Emperor?") and ++}note {--{"author":"James agent ready-60's AI","timestamp":1792249729932}@@here:

...--}{++{"author":"James agent ready-60's AI","timestamp":1792249729932}@@4. What property must the judges have that coin flips lack, other than being unbiased?
- "Use AIs to align AI": sec iii, the "heat exchanger in the unbuilt half" comparison.
- The Optimizer's Curse against complicated plans: sec iv.
- The mouse dialogue: sec v.
- Counterweight: sec vi, you can demand too simple an argument.++}

{++{"author":"James agent ready-60's AI","timestamp":1792249729932}@@Related:
- [[../Learning Outcomes/Locating the core difficulty]]
- [[../modules/Fundamental Difficulties]]
- [[../Lenses/IABIED - QA - AIs Debate Compete Oversee]]
- [[johnswentworth-why-not-just-outsource-alignment-research-to-an-ai]]
- [[lesswrong-agi-ruin-a-list-of-lethalities-lesswrong]] (sec vii points to it)
- [[lesswrong-goodharts-curse]]
++}%%

_(Originally mainly drafted in 2021, just now completed and published. Today the discussion around AI may now seem odd; it is written for a time when people were still trying to solve what would now be called "superalignment" with clever plans they'd invented themselves, rather than saying, "Oh, we will ask Fable to solve it.")_

\===

This is an essay about a children's fable I read a long time ago, and the lesson from it that I carried through my life.

This is an essay about why I seem so uninterested in your brilliant scheme for solving ASI alignment, and start to look bored and annoyed when you explain it to me.

And it is, though not really, an essay about that one guy on that online mailing list in 1996, who had a design for a reactionless drive. It's an easier place to start with the general idea, and so we'll start there.

# i. Mr. L's Reactionless Drive. ^i-mr-ls-reactionless

Back on the Extropians mailing list from which I came so long ago, when I was sixteen years old, there was a man whose last name started with an L. He had a design for a spaceship drive that would, supposedly, generate forward thrust without expelling mass in the other direction. He called it "the \<name that starts with an L> Drive".[^note-1]

On the surface, this would seem to violate Conservation of Momentum. On conventional physics, if a spaceship is accelerating in one direction, there must be something else accelerating the other way, and the total change in momentum must add to zero. In science fiction, when you postulate alternate physics violating that rule, an L-Drive is known as a "reactionless drive", in the sense that such a drive violates Newton's Third Law of equal and opposite reaction.

So then -- as one would naturally wonder, and as some on the Extropians mailing list inquired of Mr. L -- how could his L-drive possibly work?

In fact (though I don't think Mr. L fully appreciated this) the problem was so "difficult" that other people bothering to ask Mr. L to explain _at all,_ represented a tremendous openness on their part, toward Mr. L and his ideas; a great act of charity and of due scientific process.

Mr. L showed us all an animated GIF he'd made, which showed a circle with smaller masses rotating counterclockwise around its interior. At the top of the circle, the moving masses sped up; at the bottom of the circle, the masses slowed down. So the masses would move faster on the right side of the cylinder than on the left side, which would generate net thrust in a rightward direction because of the greater centrifugal force.

![lorrey drive.gif](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/yudkowsky-cat-belling-problems-img1-ae6f532a.gif)

The reader is invited to find what they think is the problem with this Reactionless Drive of Mr. L's, for themselves, before continuing.[^note-2]

:::callout {title="The flaw (click to expand)" collapse="closed"}
When the masses are accelerated rightward at the top of the cylinder, and slowed in leftward motion at the bottom of the cylinder, whatever does this acceleration, exactly counterbalances the centripetal thrust. Indeed, the "centripetal thrust" on the right side is exactly the thrust from the change in fast rightward motion at top to fast leftward motion at bottom.

Put another way: If balls were fired in externally at top, and fired off externally at bottom, the right half of the cylinder would indeed accelerate rightward. So the book-balancing thrust in the opposite direction must come from the part of the system that pushes the slow rightward ball at the top and absorbs the fast leftward ball at the bottom.
:::

When this was observed to Mr. L, he replied that of course he knew _that._ But, said Mr. L, he had designed some complicated "compensators" to prevent the forces from canceling exactly.

Mr. L said he had an Excel spreadsheet showing that the net thrust of all the system interactions was _not_ zero. But he couldn't show us the spreadsheet; the "compensators" were the key proprietary part of his design.

Leave aside any sense of indignation you might have, about the idea that Mr. L might want to keep part of his drive secret. In the counterfactual world where the L-drive worked, it might make some sense for Mr. L to keep some parts secret, just like it would make sense for him to name it after himself.

Instead, my next question is -- leaving aside all judgments passed via an intermediate step of status judgment -- how can we be _sure_ that Mr. L _didn't_ invent a reactionless drive, if we can't look at his spreadsheet?

Suppose Mr. L had been a Nobel laureate physicist and was otherwise hero-licensed to do interesting things. Would you still feel sure his unseen spreadsheet was mistaken, and if so, why?

"Because the L-Drive violates Conservation of Momentum," you say? But what do you think you know, and how do you think you know it? "Well," we can imagine Mr. L replying (though he didn't actually say this), "the law you learned about in school, is a generalization over past experience: people have never yet seen a closed system produce a net change in its own momentum, so they hypothesize a general law: No closed system can produce a net change in its own momentum. But the master rule of science is to believe the experiment, in the end. If somebody comes up with a clever system not found in nature, that does produce a net change in its own momentum, and this is experimentally verified, we'd just amend the textbooks to say that there wasn't a Law of Conservation of Momentum after all."

If only white swans have been observed so far, calling that the Law of White Swans and putting it in textbooks doesn't make the generalization any stronger or any more binding on reality.

Or as Carl Feynman recently reposted to Twitter, from an email in 1997:

> Richard Feynman (my father) divided perpetual motion machines into Perpetual Motion Machines of the First Kind, which violate the first law of thermodynamics (AKA conservation of energy), Perpetual Motion Machines of the Second Kind, which violate the second law of thermodynamics (entropy must increase), and Those Other Perpetual Motion Machines, which purport to get their energy from other laws of physics.   
>    
> The Second Kind is rarer; the only example I'm familiar with is one that my dad showed me the plans for. Once in a while, someone would come to him with a perpetual motion machine prospectus and ask if it was a good investment. One of these was a machine that claimed to extract heat energy from the air and run a generator with it. They had built half the machine, which worked as far as they could test it, and were looking for gullible investors to pay for finishing it. By carefully going over the immensely complex plans, my father and I found a "heat exchanger" that was supposed to take warm freon and cool air, and produce hot freon and cold air. Naturally, this heat exchanger was in the as-yet unbuilt portion.   
>   
> Those Other Perpetual Motion Machines get their energy from heretofore unknown physics, like cold fusion, vacuum fluctuations, or secret new physical laws that will be disclosed only on the payment of \$1,000,000. These are worthy of much more serious physical investigation, since it is entirely concievable that someone will discover a new easy way of making energy. [^note-3]  
>   
> Back around 1970, my father went to a public demonstration of one of Those Other Perpetual Motion Machines. He discovered an electric cord running out of the back of the machine, plugged into the wall. When he unplugged the machine and pointed out to the inventor that a perpetual motion machine that had to be plugged in wasn't really perpetual, the inventor pushed a button on the control panel and the machine exploded. Several spectators were severely injured; I believe one man lost an arm. The inventor sued my father on the grounds that he had caused the explosion; my father suspected that the explosion was deliberate. The trial ended up with my father not having to pay.  
>   
> Epistemic status: Childhood recollections, untainted by fact-checking. Originally an email from 1997.

The L-Drive is of the same broad family as Perpetuum Mobile; it violates a widely believed physical conservation law. If Richard Feynman went around investigating some of those, who are you to say the L-Drive wasn't worthy of serious physical investigation?

If you wish, you can take this as a koan, and come up with your own reply before continuing: How can we be _sure_ that Mr. L didn't successfully design a clever system of compensators, and correctly validate that design using a sound spreadsheet?

(My own answer is too large to fit in a spoiler, so you will need to exercise some self-discipline to stop and give your own best answer before proceeding past the next section title.) (As is an experimentally validated procedure for learning faster; it lets you better contrast your own prior brain state to whatever incoming thought you are about to encounter.)

# ii. On Miracles Buried Inside Complex Systems. ^ii-on-miracles-buried

I reply:

Conservation of Momentum is not a surface generalization over a whole system, the way that a Law of White Swans would be a surface generalization over whole swans. The law on closed systems follows from the generalization that every _individual_ interaction within known physics conserves momentum.

Whole molecules conserve momentum, because the molecules are made of atoms, and the atoms are made of nucleons and electrons, and every known interaction of the nucleons and electrons conserves momentum. Even this doesn't properly state the real depth of the law, because it's really about blah blah quantum mechanics Noether's Theorem invariant Hamiltonians blah blah. But it goes deep enough to make the point.

As soon as Mr. L says he has a spreadsheet that proves his drive works, we _immediately_ know that his spreadsheet contains some bookkeeping error, a priori rather than as a result of empirical investigation. Any spreadsheet modeling known physics will describe a sum of interactions each of which individually produces zero net global change in total momentum.

An arithmetic series all of whose terms are 0 will sum to 0.

It's one thing to claim that you've developed an alternate theory of physics where momentum is no longer conserved, or some such; and you're about to show a prototype hovering in midair to prove the point experimentally. That is at least imaginable. That is what Richard Feynman acted-as-if it was worthy of investigation (though I wouldn't necessarily agree with the explicit claim).

It's another thing to say, "Oh, well, I built a complicated system out of conventional parts, that sums up to violate momentum; and I didn't _merely_ observe that outcome experimentally, I validated the design _using a spreadsheet_." That violates math.

Our universe's physics could, in principle, contain an exception saying that momentum is no longer conserved if a spaceship is painted a certain exact shade of green. It's not likely but it's logically possible, and it's what Richard Feynman would sometimes go and look into when someone claimed that experimental result.

To take a closed-system description _not_ including any new physics, and have it add up to violating conservation of momentum, is genuinely impossible.  

So -- never minding the mere high prior probability that Mr. L is mistaken -- as soon as Mr. L says that his reactionless drive works because of a _complex system property,_ that he validated by spreadsheet, we know for _sure_ that he has made some error.

In fact, as soon as Mr. L starts speaking about complicated wheels and gears, even before he mentions the spreadsheet, we've already lost all hope in him. The answer to "How can you possibly violate conservation of momentum?" shouldn't be a big diffuse answer about complicated wheels and gears. Since the great difficulty is faced by every individual step of the system, tell me about _any one_ step that defeats the difficulty, to show off your key idea in the simplest case.

If there is a countable sum of terms that I think is zero, _because_ I think all the terms are individually zero, and you want to prove to me as quickly as possible that the sum is not zero, then defeat my initial skepticism by showing me one term that's nonzero. If instead you start out by talking about the amazing clever way you've ordered the summation so that its sum is easily provable, I lose hope right there.

When you ask Mr. L, "Why doesn't Conservation of Momentum rule out your drive?" your shred of hope is that Mr. L understands what you are asking -- has some perspective-taking on why an expert might usually think that was pretty difficult; and Mr. L stands ready to directly challenge your skepticism by addressing the key question right away: What aspect of this whole proposal has invalidated the usual reasoning saying that you can't build a reactionless drive out of reactionful parts?

Even being very charitable to Mr. L already, we don't have enough hope to bother following along if he starts in on a complicated story involving lots of gears and wheels.

The difficulty-refuting argument may be _somewhat_ more complicated than the original difficulty-asserting argument. But before we start getting told about complicated details of Mr. L's proposal, we want to hear about some key idea that fans our tiny shred of hope that the great central difficulty has been overcome.

And if Mr. L starts to tell us about complicated wheels and gears instead, we see that he hasn't taken the perspective of a skeptical expert. So we infer that he probably doesn't understand the central difficulty. So we lose that tiny shred of hope, and we are not really feeling curious about all his complicated further details.

  
I will at this point briefly mention from 2026 -- though most of this essay was written 5 years earlier in 2021 -- a public discussion I had recently at the ILIAD conference with Geoffrey Irving (formerly Google Brain, OpenAI, Deepmind, now heading the new Resolution lab), in a conversation advertised as "Yudkowsky and Irving try and fail to settle all of their disagreements in one hour." One long sub-discussion focused on whether "debate" was a promising approach to superalignment. If you just have the humans judge whether an AI proposal to align a superintelligence will work, the humans will get it wrong; but what if the AIs _debate each other instead?_

And one thing that might go wrong is that the AIs form a swarm and sacrifice themselves for each other. But the other thing that goes wrong is that humans can also misjudge competing arguments in debates, not just isolated propositions.[^note-4]

A point on which I kept pressing Irving was, "Supposing the human verifiers pass some bad argument steps in a statistically correlated way, how are you going to get reliable argument out of the whole system? Doesn't any approach to getting reliable answers out of a system with unreliable components presume at some point that you can break a debate down into steps where the judges are just statistically high-variance rather than statistically biased in their judgments? And isn't this just false in practice with humans?" And then refining this question further, I asked: "Suppose your judges were all random coinflips. That wouldn't work to drive correct outputs for debate as a means of superalignment. Can you tell me what property the judges need, which random coinflips lack, and which isn't 'the judgments are statistically unbiased', in order for this scheme to work?" And Irving said it was a good question and he might need to get back to me on that.

Later, several people at the conference said that they had been surprised, and had updated, from seeing that exact point of the discussion in particular.

I don't know whether this will be _at all_ comprehensible to any reader and especially when the video hasn't been put online yet... but the question I was asking Irving was, from my own perspective, almost exactly analogous to trying to track down the part of a Perpetuum Mobile which breaks the rules.

You can build an accurate judger out of judges that are sometimes wrong as individuals, so long as the plurality or the majority is always right. You can build an unbiased estimator out of high-variance judges with no bias. But suppose the majority or plurality is sometimes wrong, and there isn't always some clever way of asking the question three different ways such that then two out of three variants are judged correctly. Then how are you building a "debate" system that reliably returns the correct answer out of unreliable judges? Why can't it also extract the length of the Emperor of China's nose from judges who've never seen the Emperor?

I expect you would notice a great many places where the would-be aligners present at that conference disagreed about other matters, depending on whether they perceived that debate as me pressing Irving about a strange abstract technical corner question; versus the question reformulating a seemingly big complicated task to boil down a central difficulty.  

Many many engineers, in fact, historically rolled up their sleeves and got to work on building their designs for Perpetuum Mobiles. It was a larger-looming social phenomenon in Feynman's day -- one of the ways slightly smart engineers went Wrong back before AI or cryptocurrency. And I am not a postcognitive telepath -- I cannot read minds in the past -- but I wouldn't be surprised if many of those 1970s engineers saw themselves as _hardheaded practical_ people with _industry experience_, whose effortful work _learning about real metal gears_ had taught them the practical limitations of _airy abstract theories_ like "conservation of energy". Which is to say, that they had tried their own hand at abstraction and not gotten anywhere, and learned from this an Arrogance of the Humbled[^note-5] about the ultimate limits of mere thinking.

# iii. Cat-Belling Problems. ^iii-cat-belling-problems

When I was very young I read a children's story and extracted a lesson from it that stayed with me my whole life, being generalized and deepened as I grew older. I think it may have been a more elaborate story that I read as a child, but it came from an Aesop's Fable.

Here is the original Aesop's Fable in its entirety:

> Belling the Cat
> 
> The Mice once called a meeting to decide on a plan to free themselves of their enemy, the Cat. At least they wished to find some way of knowing when she was coming, so they might have time to run away. Indeed, something had to be done, for they lived in such constant fear of her claws that they hardly dared stir from their dens by night or day.
> 
> Many plans were discussed, but none of them was thought good enough. At last a very young Mouse got up and said:
> 
> "I have a plan that seems very simple, but I know it will be successful.
> 
> All we have to do is to hang a bell about the Cat's neck. When we hear the bell ringing we will know immediately that our enemy is coming."
> 
> All the Mice were much surprised that they had not thought of such a plan before. But in the midst of the rejoicing over their good fortune, an old Mouse arose and said:
> 
> "I will say that the plan of the young Mouse is very good. But let me ask one question: Who will bell the Cat?"

Aesop's original moral then runs:

> _It is one thing to say that something should be done, but quite a different matter to do it._

IMO, there's a whole tree of valuable morals one could derive from this story. Aesop's first moral-branch has many valuable further sub-branches, eg in politics: "It is one thing to say you want X, and quite a different matter to devise a stable realistic system of incentives which yields X as its equilibrium."

But the greatest moral I took, that stayed with me my whole life to grow into a lesson-tree and deepen in its roots, was:

_There is often some especially difficult or impossible step along the way to what you want, and until you overcome that key step, the rest of the plan is of no use._

We can see some further branches on this lesson-tree, exhibited in the following images, both of which show a missing _cat-belling step_ calling a whole scheme into question:

![image.png](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/yudkowsky-cat-belling-problems-img2-834ce437.png)

(By Sidney Harris, published in American Scientist, Nov-Dec 1977.)

Or this even more famous one:

![image.png](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/yudkowsky-cat-belling-problems-img3-1a4058d7.png)

  
A very standard failure mode I have observed over the years is for people's minds to bounce off of, route around, or entirely fail to perceive, the cat-belling step.

Eg:

> By carefully going over the immensely complex plans, my father and I found a "heat exchanger" that was supposed to take warm freon and cool air, and produce hot freon and cold air. Naturally, this heat exchanger was in the as-yet unbuilt portion. 

Or also eg (added 2026), many variants on:

> First we will build more capable AIs \[where we can easily check that their capabilities are increasing, and automatically set up outer optimizer loops to increase those capabilities, and also get a tone of money and fame\] and then we will use those AIs to align AI \[where no (publicly scrutinized) proposal exists to check whether the earlier AI's answers are honest or correct\].

This from my perspective is very much the equivalent of putting the "heat exchanger" in the second half of the machine; except that, instead of the Perpetuum Mobile entirely failing to work, it very unfortunately works to launch the airplane but fails to land it safely.

(That I specify no "publicly scrutinized" proposal exists is because, knowing the mental shenanigans around cat-belling steps, I predict Anthropic believes they have terribly serious proposals for accomplishing miracles of superalignment, and have terribly serious reasons why they cannot tell anyone, especially me, what those proposals are. No doubt many would-be builders of Perpetua Mobilia understood their real situation, on some intuitive level, well enough to come up with Various Reasons why Feynman could not be allowed to look at their secret designs.)

# iv. The Optimizer's Curse against complicated plans for hard problems. ^iv-the-optimizers-curse

You will recall Mr. L's L-Drive and his animated GIF (reproduced from memory):

![lorrey drive.gif](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/yudkowsky-cat-belling-problems-img1-ae6f532a.gif)

You will recall that when the flaw in his L-Drive setup was pointed out to Mr. L. -- that the acceleration at top and deceleration at bottom exactly cancels out the centrifugal force -- Mr. L. explained that he had designed "compensators" to prevent the cancellation from being exact, which was the real proprietary secret of his design.

Mr. L. did not post his spreadsheet, but he posted the graph of his spreadsheet's calculation of net force, which was mostly zero, but showed several positive spikes. Again reproducing it from memory:

![image.png](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/yudkowsky-cat-belling-problems-img4-4674c943.png)

I am not a past-viewing telepath. But on my grasp of psychology, there is a very obvious way to suspect events played out: Mr. L had his first brilliant idea about rotating balls in a cylinder, began to anticipate fame and fortune, but then saw the flaw _himself..._ and then desperately set out to _repair_ the flaw, instead of writing off his hopes and dreams... and invented more and more complicated "compensators"... until he [stopped](https://www.lesswrong.com/posts/L32LHWzy9FzSDazEg/motivated-stopping-and-motivated-continuation) on a design where he'd managed to make a few bookkeeping errors in his Excel spreadsheet.

That is a _very_ classic way that people end up believing they have solved some very hard step of a problem, in my experience -- **by elaborating and complicating matters to the point where they themselves can no longer deduce the final failure.** It doesn't work for mundane immediate matters like fixing your refrigerator today; but it works with anything that _you_ can convince yourself is about the future, or that _you_ can convince yourself has not been decisively refuted. Why, sure, your weird scheme will _totally_ work for aligning ASI -- which, amazingly enough, is a key step that you cannot test right now; and that you can shut your ears and hum about, whenever anybody else tries to explain why your plan will fail.

And if these inventors are so kindly as to explain their scheme at all, they will launch into a description of some complex system, _all_ of which I simply _must_ hear about; and they don't, and _can't,_ preface themselves with a simpler explanation that directly targets and defeats my previous skepticism about a Cat-Belling Problem.

That's what happens if you try to ask somebody underneath Geoffrey Irving's level to explain eg how they mean to use "debate" to overcome the problem of correlated bad judgments. They are downright confused by your apparent belief that they ought to have anything simple to say, about a key insight, that defeats some weird problem.  

Standard lens time: This is yet another instance of Goodhart's Curse, or rather the [Optimizer's Curse](https://www.lesswrong.com/w/goodhart-s-curse). If you try out a large number of complicated variations on a design, estimate their goodness via a process with nonzero error, and _select_ the best-looking candidate, you are more likely to find a spreadsheet with an upward error in the goodness estimate.

The more complicated the candidates, the greater that systematic error.[^note-6] Which isn't necessarily fatal if you have some very low-error process that can evaluate very complicated things, which is why not _all_ nuclear reactors with complicated designs have melted down. But if you are doing something more new and uncertain and error-prone -- then being able to simplify complicated schemes down to core-difficulty-defeating key ideas, is much more important as a check on the mental process.

# v. When no Authority (that you accept) can tell you that your bright idea is wrong. ^v-when-no-authority

In the case of Conservation of Momentum, we have Authorized Authoritative Authorities to tell us that its cat-belling problem exists and is hard, and that Mr. L should not be able to defeat it just by throwing in a few obscuring complications.

What if instead, we are confronting some difficulty that is, _in reality_, extremely difficult -- maybe not impossible, like a reactionless drive, but still has some very difficult step of actually belling the cat -- but there is nobody you see as an Authorized Authoritative Authority, to tell you that it is hard?

Well in that case, things appear easier! They are not actually easier, of course; they are even harder, because the laws governing difficulty are not as solidly known. But they _feel_ easier, because you will much more easily be able to solve the _social_ problem of _convincing_ people you are on the way to building a reactionless drive. And if you are most humans, you will take that as social proof that what you believed is okay to believe.

To pick up Aesop's fable where Aesop left off,[^note-7] my mind generates its most natural continuation fic as follows:

> "Who will bell the Cat?" said the old Mouse.
> 
> And the young Mouse replied without pause, "We will hold a Moot of Mice to determine which of us is best suited to the job, of course. A more important aspect of my strategy, I think, is devising a clever design for a bell which will always reliably ring when it is jolted from any angle, even if the Cat is cunningly lying on its back and pushing itself forwards, so that the bell is hanging upside-down --"
> 
> "That was never what I feared would be the hard part of the problem," said the old Mouse, "having a reliable bell to put on the Cat, that is. It's true that an ill-considered scheme might fail even there, but that seems like a comparatively straightforward problem to work on, if other matters were resolved. Rather my worry is that none of us at all, no Mouse that we can appoint, would have the ability to hang a bell around the Cat's neck. So telling me that a Moot of Mice will Meet to choose one Mouse to do it, does not ease my concern. Not unless you can tell me one example of a Mouse who is up to the job, and then I will believe the Moot can choose either that Mouse or a better one."
> 
> "I'm saddened by how you don't seem very interested or curious in my ideas," said the young Mouse. "Which seems strange to me, when you claim to put so much value on preserving our lives from the Cat. There may, perhaps, remain some details of my Cat-Belling Plan to be worked out, but you don't seem interested in the progress we've made --"
> 
> "From my perspective, indeed," said the old Mouse, "we are no closer to evading death by Cat, than when we sat down to this meeting."
> 
> "But you have not given proper attention to my plan," said the young Mouse, "or tried to listen to my explanation of how it makes progress toward a belled Cat. Now the first step, as I said, is to obtain a proper bell. The second step is to attach it to a collar. The third step will be to coat that collar in glow-in-the-dark paint --"
> 
> "Please humor this old Mouse," said the old Mouse, "who has heard other proposals before for attaching things to Cats, and try to tell me swiftly why my skepticism is wrong. The Cat's neck is high off the ground, higher than any Mouse can reach. Even if a Mouse were to reach that high, it would take time for a Mouse to loop the bell and collar around the Cat's neck, let us say five seconds, and this seems to inherently require the Mouse to be in close proximity to the Cat. Meanwhile the Cat kills any Mouse who approaches within half a second. This is not a narrow gap, it is an order-of-magnitude gap. Rather than describing all the steps of your plan in order, can you try to explain what key step, about glow-in-the-dark paint or whatever, defeats the reasoning behind the skepticism I've just explained?"
> 
> "Well, I think it makes more sense to explain my whole plan in order," said the young Mouse. "But since you ask, the glow-in-the-dark paint does defeat your skepticism; it means that, even if the Cat learns to pad around too silently to disturb the bell, we will still be able to see the cat coming by the glow of its collar. At least at night, but if that's the only way for us to survive, we can only move about by night."
> 
> "You do not seem to have understood what I have tried to point to as a central difficulty," said the old Mouse, "or understood what it would mean to give a focused argument squarely aimed at my skepticism."
> 
> The young Mouse shook its head sadly. "It sounds like you are only interested in discussing this one feature of the issue that interests you, and not willing to discuss the aspects that interest me," said the young Mouse. "A fallibility of your age and inflexibility, I suppose."
> 
> "The other steps of your Cat-Belling Plan are useless unless this central difficulty can be overcome," the old Mouse said. "There may perhaps be other difficult steps, but that does not change that solving those would be useless without also solving this one. Though the steps you've focused on so far do seem rather easy to me, by comparison; they have a sense about them of triviality, of wasted motion; of a mind bouncing off the more difficult aspects of the problem, to lesser aspects that seem easier and more pleasant to think about --"
> 
> "I worked for months to write up my proposal for sourcing and applying glow-in-the-dark paint!" the young Mouse interjected indignantly. "And published it in the Journal of Things Mice Talk About! After doing all that work, you say I've accomplished nothing of worth? My strategy and design is a complex one; you ought to realize that you'd need to hear out the whole plan in order to judge whether your argument about the Cat's unbellability would apply to it."
> 
> "It is not impossible," said the old Mouse, "that there could exist some complex strategy given to us by a higher source, such that only by examining the whole plan, could we realize how it defeated the Cat-Belling Step in particular. But it seems unlikely that any Mouse would _successfully invent_ such a plan, however complicated it may be, without having some _more compact insight_ into defeating the key difficulty. That you are unable to describe this key insight to me, and indeed, unable to sympathize with why I want to hear it, is why I lost hope that you have made any progress worth mentioning."
> 
> "I keep trying to tell you!" said the young Mouse. "The key insight is that you obtain a bell which rings when jolted from any angle, even if upside down; then, after you attach the bell to the collar, you paint the collar with glow-in-the-dark paint; then you hold a Moot of Mice to determine which Mouse will attach the bell to the Cat; then you assign a team of Mice to monitor the belled Cat and determine whether the collar seems to be staying on solidly --"
> 
> But the old Mouse had, even knowing it for an impoliteness, turned away from the young Mouse and into his own thoughts, which had returned to whether the Cat could be belled while it slept. There were many further difficulties with the idea, for it was not known where the Cat slept, or even if the Cat slept at all. The subproblem of determining where the Cat slept, might not have a favorable solution, even if it was solvable; it might be that the Cat slept someplace no Mouse could reach. And there was also the further problem of whether any Mouse could carry out belling operations stealthily enough not to wake the Cat. But at least that general approach seemed to squarely attack the hard aspects of the central difficulty, the high-held head and swiftly lethal speed of the Cat: a sleeping Cat, if it slept as Mice did, might lower its head and stay still for a time. The new subproblems did not just reduce again to 'the Cat is too tall and too fast for any of us to bell', and that made it an interesting angle to explore; that fresh line of thinking might yield further insights, even if it failed of direct solution due to at least one of the new subproblems being unsolvable.
> 
> Meanwhile, most of the other Mice had gathered instead around this new luminary, listening with fascinated expressions as the young Mouse expounded at length upon the sourcing of glow-in-the-dark paint. It seemed there were surprisingly few suppliers -- but not none -- who would sell at a price the Mice could afford; an interesting challenge indeed, but one on which impressive progress had already been made, and a fresh line of thinking none of them had considered before! For it introduced a new difficulty which was quite unlike that other difficulty the boring old Mouse often went on about; and the young Mice could not see how the Cat's strength and swiftness would prevent them from buying glow-in-the-dark paint, so it seemed this new difficulty was much more promising of solubility. It was hard to keep track of all the steps in the plan, since it was very wise and sophisticated; but the young Mice did not see how it would fail.

# vi. The equal and opposite advice. ^vi-the-equal-and

For every advice there is an equal and opposite advice, that needs to be given to equal and opposite people; for every essay there is a long list of warning labels that I usually realize afterwards I failed to guess properly in advance. Nonetheless, here is my guess at a warning label that should be here:

It is possible to unjustly demand that an argument be too simple.

A poster child here could be, perhaps, the Scopes Monkey Trial. We can imagine the prosecution repeatedly demanding at what point a monkey gives birth to a non-monkey, and if anybody tries to say anything about a sum of many small discrete changes, the prosecution says: "Oh, this sounds like one of those big complicated ideas where nobody can see anymore how it is wrong; please boil it down to an essence, show me one point where a monkey gives birth to a non-monkey."

There might be some hope that a genuine cat-belling insight can be seen to squarely address a cat-belling problem, but that's only if you're genuinely trying to understand it rather than assuming an arms-crossed skeptical attitude saying "Convince me! No, not that way, the particular exact way I expect to be convinced!"

The opening example I gave with Mr. L's reactionless drive is one where we happen to know very exactly that a reactionless drive must have a single reactionless step that does something very anomalous under known physics; and furthermore, where we are pretty sure Mr. L is in fact mistaken. In other cases, cat-belling steps may be merely difficult and not impossible; they may even have some answer that cracks them wide open and makes them vanish as difficulties.

The people on the mailing list asking Mr. L how his drive worked were -- from my own perspective -- probably being too open-minded and too ready to listen. But being actually ready to listen to an incisive answer is the only way you can hear a solution to something you imagine to be a cat-belling difficulty, conditional on somebody actually having a solution. Richard Feynman was not being foolish in acting out something like a deontological rule about checking every time.

# vii. The rest of this post, which I gave up writing. ^vii-the-rest-of

The rest of this draft in 2021 was my attempt to list some Cat-Belling Problems in AI, along with explaining what gave them the status of a big problem rather than a peripheral technical difficulty.

After some difficulties in approaching that part from several attempted writing angles, I gave up, and just [posted my raw list of items](https://www.lesswrong.com/posts/uMQ3cqWDPHhjtiesc/agi-ruin-a-list-of-lethalities) without any such preamble or expansion.

[^note-1]: My model of some readers has them now reasoning, "How dare Mr. L name the drive after himself; how arrogant, how low-status; I therefore already associate a bad vibe with this drive, so it probably doesn't work." Point one, this was around 1997 and people were less status-regulatory of inventors back then; it was more common practice for people to name things after themselves. Second, on my view, _if the drive worked,_ Mr. L would absolutely have been justified in naming it after himself; so the crux is whether or not the drive works. Or from another angle: to reason "the drive probably doesn't work, because Mr. L named it after himself" is bad Bayesianism. In the conceivable worlds where the drive does work, we are not unlikely to see Mr. L naming it after himself, especially if it is 1997 and we are less far from an older world where many inventors did that.
[^note-2]: If you are the sort to _confidently_ declare a flaw and you are wrong, you rate no higher in my judgment than Mr. L and perhaps lower. Because then on occasions when humanity does solve hard problems, you are the sort to contribute heat rather than light. But if, reading this, you only lightly guess and then you are wrong, that is much better than not daring to guess at all.
[^note-3]: Carl Feynman [notes](https://www.lesswrong.com/posts/SwYBLQvo8MddDcCwz/cat-belling-problems?commentId=6ahC5iiJcPsd9zWHa) that the "worthy of much more serious investigation" phrasing is his own commentary on his father's behavior, not something Richard Feynman had stated explicitly as a generalization.
[^note-4]: Or to state it more exactly: The reason we have the Scientific Method rather than the Scholastic Method is not that no scholar ever gets something right without overwhelming experimental proof; but that _communities_ of scholars cannot correctly judge _who_ got it right, even if one person got it right, without some experiment that absolutely hits them over the head with the correct answer; after which _sometimes_ the majority notices. Eg recent example, because people ignore historical examples, because [their brain thinks that history is all a TV show](https://www.lesswrong.com/posts/TLKPj4GDXetZuPDH5/making-history-available) and that historical people are more stupid than themselves and don't know about clever ideas like prediction markets: It's not that nobody warned EAs that AI might arrive sooner than 2050. There was [an essay that laid out in advance all the reasons why the official-looking 2050 estimation was wrong, in hindsight ~100% correctly](https://www.lesswrong.com/posts/ax695frGJEzGxFBK4/biology-inspired-agi-timelines-the-trick-that-never-works). But it was futile to try to hold a "debate" that would settle on this correct answer given for correct reasons, because _even having been presented with the correct answer, the larger community could not majority-discriminate it as correct, until they were hit over the head with overwhelming contrary evidence._ OpenPhil ran a contest with \$50,000 in prizes for essays that disputed OpenPhil's then-standard estimate of 2050 median time to AGI and 5% catastrophic risk; all the prizes were awarded to essays that argued for longer timelines and lower risks. If there were any method that broke debates into careful pieces that a group of judges would always judge in a statistically unbiased way, 2022 would've been a great time to use it in the essay-judging contest! But no method like that has ever been invented yet through all the ages of the world. The historically observed problem with the Scholastic Method is not that no individual is ever smart enough to get things right without overwhelming evidence -- those smarter individuals are where the hypotheses come from that get tested by later experiment! The problem is that _the majority_ is incapable of discerning which existing arguments have used more valid reasoning steps and so arrived at the correct answer from earlier data. It is exactly a failure of human groups at _judging debates_ rather than a limit on the individual intelligence of humans to come up with the right answers earlier. Humanity throws occasional Einsteins who will correctly say, far in advance of overwhelming experimental evidence to convince the larger group, "Then I would have pitied the good Lord; the theory is correct." But when humanity at large looks to some very sober and solemn-looking people wearing the serious-person garments of that era, the soberly-clothed people are not able to tell which scholar's argument is correct. That is the problem with the Scholastic Method. The Scientific Method, for a small fragile time and in a few institutional places, was able to listen to the voice of overwhelming experimental evidence instead, when it came to deciding afterward which scholar to credit for having called it right. (Though to be clear, many particular scientific fields, or solemn-looking people wearing solemn garments, have not reached that standard either.) So yes, it is very much fighting words to claim that you are going to do something called "debate" and then your human judges are always gonna correctly figure out which AI had the better argument on every argument step. Having a "debate" system which causes the Scholastic Method to start working with human judges is a Cat-Belling Problem.
[^note-5]: A term and thesis coined by Duncan Sabien. I ought to write it up at some point, but meanwhile perhaps many readers, like myself, will find a whole useful thesis immediately apparent just from seeing the phrase "Arrogance of the Humbled".
[^note-6]: This can of course itself be overused as an invincible argument against any slightly complicated scheme, _including_ the ones that have multiple tiers of simplifiability in their key ideas. Many effective altruists that wanted peace of mind in knowing that they were doing the One Best Thing by buying mosquito bednets were endlessly endlessly convinced that any more complicated schemes for improving humanity, like "doing something about ASI before we all get killed", must surely contain an invalidating error.
[^note-7]: If any reader be aghast at my audacity in daring to pick up where Aesop left off, as if I were comparing my own writing abilities to fables that have lasted through millennia, I remind them that I am publicly validated as one of the leading authors of fanfiction on the entire planet and therefore it is not arrogant of me to try to write a continuation fic of an Aesop's fable.
