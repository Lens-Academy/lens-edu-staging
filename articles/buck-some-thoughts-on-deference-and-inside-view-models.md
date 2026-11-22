---
title: "Some thoughts on deference and inside-view models"
author:
  - "Buck"
source_url: "https://forum.effectivealtruism.org/posts/53JxkvQ7RKAJ4nHc4/some-thoughts-on-deference-and-inside-view-models"
published: 2020-05-28
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description: "TL;DR: I wrote this post to describe the philosophy behind the schedule of a workshop that I ran in February. The workshop is kind of like AIRCS, but aimed at people who are more hardcore EAs, less focused on CS people, and with a culture which is a bit less like MIRI and more like the culture of other longtermist EAs. Thanks to the dozens of people who I've talked to about these concepts for their useful comments; thanks also to various people who read this doc for their criticism. Many of these ideas came from conversations with a variety of EAs, in particular Claire Zabel, Anna Salamon, other staff of AIRCS workshops, and the staff of the workshop I’m going to run."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

TL;DR:

-   It’s sometimes reasonable to believe things based on heuristic arguments, but it’s useful to be clear with yourself about when you believe things for heuristic reasons as opposed to having strong arguments that take you all the way to your conclusion.
    
-   A lot of the time, I think that when you hear a heuristic argument for something, you should be interested in converting this into the form of an argument which would take you all the way to the conclusion except that you haven’t done a bunch of the steps—I think it’s healthy to have a map of all the argumentative steps which you haven’t done, or which you’re taking on faith.
    
-   I think that all the above can be combined to form a set of attitudes which are healthy on both an individual and community level. For example, one way that our community could be unhealthy would be if people felt inhibited to say when they don’t feel persuaded by arguments. But another unhealthy culture would be if we acted like you’re a chump if you believe things just because people who you trust and respect believe them. We should have a culture where it’s okay to act on arguments without having verified every step for yourself, and you can express confusion about individual steps without that being an act of rebellion against the conclusion of those arguments.
    

I wrote this post to describe the philosophy behind the schedule of a workshop that I ran in February. The workshop is kind of like [AIRCS](https://intelligence.org/ai-risk-for-computer-scientists/), but aimed at people who are more hardcore EAs, less focused on CS people, and with a culture which is a bit less like MIRI and more like the culture of other longtermist EAs.

Thanks to the dozens of people who I’ve talked to about these concepts for their useful comments; thanks also to various people who read this doc for their criticism. Many of these ideas came from conversations with a variety of EAs, in particular Claire Zabel, Anna Salamon, other staff of AIRCS workshops, and the staff of the workshop I’m going to run.

I think this post isn’t really insightful enough or well-argued enough to justify how expansive it is. I posted it anyway because it seemed better than not doing so, and because I thought it would be useful to articulate these claims even if I don’t do a very good job of arguing for them.

I tried to write the following without caveating every sentence with “I think” or “It seems”, even though I wanted to. I am pretty confident that the ideas I describe here are a healthy way for me to relate to thinking about EA stuff; I think that these ideas are fairly likely to be a useful lens for other people to take; I am less confident but think it’s plausible that I’m describing ways that the EA community could be different that would be very helpful.

## Part 1: ways of thinking ^part-1-ways-of

### Proofs vs proof sketches ^proofs-vs-proof-sketches

When I first heard about AI safety, I was convinced that AI safety technical research was useful by an argument that was something like “superintelligence would be a big deal; it’s not clear how to pick a good goal for a superintelligence to maximize, so maybe it’s valuable to try to figure that out.” In hindsight this argument was making a bunch of hidden assumptions. For example, here are three objections:

-   It’s less clear that superintelligence can lead to extinction if you think that AI systems will increase in power gradually, and before we have AI systems which are as capable of the whole of humanity we have AI systems which are as capable as dozens of humans.
    
-   Maybe some other crazy thing (whole brain emulation, nanotech, technology-enabled totalitarianism) is likely to happen before superintelligence, which would make working on AI safety seem worse in a bunch of ways
    
-   Maybe it’s really hard to work on technical AI safety before you know more about the technology that will be used to build AGI than we currently know.
    

I think that all these objections are pretty reasonable, and I think that in fact there is a pretty good answer to all of them.

It seems like in hindsight it worked out well that I was instantly credulous of the AI safety argument, given that ten years later I’m still convinced by it—I don’t want to criticize myself for epistemic moves which empirically worked fine. But I think it was a mistake for me to not realize that I didn’t have an end-to-end story for AI safety being important, I just had a sketch of an argument which was heuristically persuasive.

I’m reminded of the distinction between proofs and proof sketches in math—in a proof, you’re supposed to take care of all the niggling details, while in a proof sketch you can just generally gesture at the kind of reason why something might be true.

I think it’s correct to believe things when you can’t spell out the whole argument for them. But I think it’s good to be clear with yourself about when you’re doing that as opposed to when you actually know the whole argument, because if you aren’t clear about that, you have problems like the following:

-   You will be worse at reasoning with that argument and about that argument. By analogy, when I’m studying an intellectual subject like economics or math or biology, I’m constantly trying to prevent myself from having a false illusion of understanding of what I’m reading, because if I only have a fake understanding I won’t be able to apply it correctly.
    
-   If you are in a conversation where that argument comes up, you might repeat the argument without understanding whether it’s relevant.
    
-   If you hear a counterargument which should persuade you that the original argument is wrong, you might not realize that you should change your mind.
    
-   If you talk to people about the argument and then turn out to not understand it, you’ll look like an arrogant and careless fool; this reflects badly on EA when it happens, and it happens often. (I am particularly guilty of having done this one.)
    

I think it’s particularly healthy to sometimes try to think about the world in terms of end-to-end arguments for why what you’re doing is good. By this I mean trying to backchain all the way from your work to good outcomes in the world. Sometimes I talk to people who are doing work that IMO won’t be very helpful. I think that often they’re making the mistake of not thinking about the end to end picture of how their work could be helpful. (Eg once I asked an AI safety researcher “Suppose your research project went as well as it could possibly go; how would it make it easier to align powerful AI systems?”, and they said that they hadn’t really thought about that. I think that this makes your work less useful.)

A key move here is the “noticing your confusion” move where you realize that an argument you believed actually has a hole in it.

### Knowing where the “sorrys” are ^knowing-where-the-sorrys

Here’s an obnoxious computer science metaphor.

I’ve spent a bit of time playing around with proof assistants, which are programs which allow you to write down mathematical proofs in a way that allows them to be automatically checked. Often when you’re using them, you break down your proof into multiple steps. Eg perhaps you prove A, and that A implies B, and that B implies C, and then you join this all together into a proof of C. Or maybe you show that A is true if both B and C are true, and then you prove B and C and now you have a proof of A.

While you’re in the middle of proving something, often you want to know whether the overall structure of your proof works before you have filled in all the details. To enable this, theorem provers give you a special keyword which you can use to tell the theorem prover “Please just pretend that I have successfully proven this little thing and then move on to checking other steps”. In Lean, this keyword is called “sorry”. To prove a really complicated thing, you might start out by having the whole proof be a sorry. And then you break down the problem into three steps, and you write sorry for each. Slowly you expand out the structure of your proof, using sorrys as you go as necessary, and then eventually you turn all of them into valid proofs.

I think that something like this might be a good metaphor for how you should relate to doing good in the world, or to questions like “is it good to work on AI safety”. You try to write down the structure of an argument, and then fill out the steps of the argument, breaking them into more and more fine-grained assumptions. I am enthusiastic about people knowing where the sorrys are—that is, knowing what assumptions about the world they’re making. Once you’ve written down in your argument “I believe this because Nick Bostrom says so”, you’re perfectly free to continue believing the same things as before, but at least now you’ll know more precisely what kinds of external information could change your mind.

The key event which I think does good here is when you realize that you had an additional assumption than you realized, or when you realized that you’d thought that you understood the argument for X but actually you don’t know how to persuade yourself of X given only the arguments you already have.

#### Small clarification: Many small arguments ^small-clarification-many-small

In contrast to when you’re doing mathematical proofs, when you’re thinking about real life I often think that it’s better to come to conclusions based on weighing a large number of arguments, rather than trying to make one complete calculation of your conclusion (see [cluster thinking vs sequence thinking](https://blog.givewell.org/2014/06/10/sequence-thinking-vs-cluster-thinking/), or [fox vs hedgehog mindset](https://conceptually.org/fox-vs-hedgehog)).

I structure a lot of my beliefs this way: I try to learn lots of different arguments that feel like they’re evidence for various things, and I am interested in the validity of each argument, independent of whether it’s decision relevant. So I often change my mind about whether a particular argument is good, while my larger scale beliefs shift more gradually.

### Bonus miscellaneous points ^bonus-miscellaneous-points

#### Learning someone’s beliefs, vs scrapping for parts ^learning-someones-beliefs-vs

Two ways you can relate to some talk you’re listening to:

-   Learning their beliefs. You try to become able to answer the question “what would this person say about how useful it is to have EA-aligned people in various parts of the government”?
    
-   Alternatively, you can scrap them for parts—you can try to take little parts of the things that they’re saying and see whether you want to incorporate them into your personal worldview based on the individual merits of those little parts.
    

You shouldn’t always do the latter, but (due to time constraints) you also shouldn’t always do the former, and it’s IMO healthy to have a phrase for this distinction.

This is related to the CFAR-style looking-for-cruxes method of conversation. One really nice feature of the looking-for-cruxes style conversation is that it fails gracefully in the case where it turns out you’re talking to someone smarter/more knowledgeable/better informed than you, which means that if we have a culture where we by default have conversations in a looking-for-cruxes style, it’s less likely that smart people will be turned off EA by unpleasant conversations with overconfident EAs. (Thanks to Anna Salamon for this last point.)

## Part 2: Outside views, deference, EA culture ^part-2-outside-views

I think we can use the above ideas to describe a healthy set of attitudes for the EA community to have about thinking about EA arguments.

Here are some tensions I am worried about:

-   Some EAs know more and have thought more and better about various important questions than others—eg, EAs generally have better opinions when they’ve been around EA longer, when they have jobs that cause them to think about EA topics a lot or which expose them to private discussions about EA topics with people who work on them full time. It’s often healthy to defer to the opinions of such people. But if you only defer, you don’t practice thinking on your own, which is terrible because thinking on your own is the skill which EA requires in order to have their full timers have good opinions! And it also means that people are overly credulous of what fulltimer EAs think (or what people (potentially inaccurately) think that they think).
    
    -   When I was involved with Stanford EA in 2015, we spent a lot of time discussing core EA questions like the relative value of different cause areas, philosophical foundations, and what kind of strategies might be most valuable for EA to pursue for various goals. Most of us had a default attitude of skepticism and uncertainty towards what EA orgs thought about things. When I talk to EA student group members now, I don’t think I get the sense that people are as skeptical or independent-thinking.
        
        -   A lot of this is probably because EA presents itself more consistently now. In particular, longtermism is more clearly the dominant worldview. I think this makes things feel really different. In 2015, my friends and I were very uncertain about cause prioritization, and this meant that we were constantly actively reminded that it wasn’t possible that everyone was right about what to do, because they disagreed so much.
            
        -   Another factor here is that EA feels more to me now like it disapproves of people arguing publicly about cause prioritization. I have the sense that people would now view it as bad behavior to tell people that you think they’re making a terrible choice to donate to AMF—I feel much more restricted saying this nowadays, but this is at least partially just because I am personally now more risk averse about people thinking I’m obnoxious.
            
        -   I think that it’s potentially very bad that young EAs don’t practice skeptical independent thinking as much (if this is indeed true).
            
        -   On the other hand, one way that things have gotten much better is that I think it’s much more approachable to learn about AI safety than it used to be, because of things like the increasing size of the field, the Alignment Newsletter, the 80K podcast, and the increasing quality of explanations available.
            
        
    -   Also, if people are too inclined to defer and not think through arguments themselves, they might not just not assess the arguments themselves, they probably won’t even learn the arguments that the experts find persuasive.
        
    
-   I want a culture where researchers try to think about whether the research they’re doing is valuable. To encourage this, I want a culture where people are interested in trying to understand the whole end-to-end picture of what’s important. But simultaneously I want it to be okay for someone to just work doing ops or whatever and not feel insecure about the fact that their models of the world aren’t as good as the models of people whose full time job is to make good models.
    
-   Similarly, I think that it’s very valuable for EAs to get status from doing actually useful stuff, as opposed to from being really good at arguing about what EA should be doing.
    
-   I think it’s kind of tricky to have the right relationship to skepticism of established EA beliefs.
    
    -   One bad culture is one where people are embarrassed to ask questions and say that they don’t get the arguments for pieces of the conventional wisdom. We have a bunch of emperor’s-new-clothes-style dumb consensus beliefs, and we don’t spot holes in them. We don’t get to practice noticing our confusion and improving our arguments.
        
        -   And when people who are new to EA talk to us, they notice that we don’t really understand the arguments for our beliefs, and so we turn off people who care the most about careful examination of claims. I think this is a pretty serious problem.
            
        
    -   But there’s another bad culture where we can’t update based on what other people think, or where we aren’t supposed to believe things based on trusting other people. Or where it’s considered low status to work on things that don’t give you a mandate to think about the complete story.
        
    

I think that now that I have the above concepts, I can describe some features of what I want.

-   I think it’s much healthier if we have the attitude that in EA, people try to incrementally improving their understandings of things, and in particular they’re interested in knowing which parts of their arguments are robust vs fragile.
    
    -   In this world, the default understanding is that when you change your mind about an argument about a subquestion, you aren’t expected to immediately have an opinion about how this changes your mind about the main question.
        
    
-   EAs are encouraged to try to build models of whatever parts of EA they’re interested in, and it’s considered a normal and good thing to try to think through arguments that you’ve heard and try to figure out if they make sense to you. But it’s clear that you’re not obligated to have models of everything.
    
-   When asking questions of a prestigious, smart EA, people are interested in trying to understand what exactly the person thinks and how their beliefs are connected to each other, as opposed to just trying to learn their overall judgements or argue with them.
    

----

I wish I had better ideas for how to do EA movement building in ways that lead to a healthy EA culture around all these questions.
