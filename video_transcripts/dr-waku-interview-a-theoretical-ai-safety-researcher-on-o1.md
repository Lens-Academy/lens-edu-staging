---
title: "Interview: a theoretical AI safety researcher on o1"
channel: "Dr Waku"
url: "https://www.youtube.com/watch?v=5OUqHv9C1To"
---

Hi everyone, I'm here today to interview Abram, and we're going to talk about how the release of OpenAI o1 has changed people's perspective on AI safety. We're going to talk today in three parts: first talk about Abram and his original perspective on this AI safety problem, then next how that perspective changed when LLMs were released, and finally what this new perspective means for OpenAI o1.

So Abram started, I guess, with AI safety by having an interaction with Eliezer Yudkowsky, who is one of the most famous people in AI safety. Would you say?

Yeah, he founded the field together with Nick Bostrom, who like at a certain point in time were basically the only two people on the Earth concerned about this. And Nick Bostrom wrote Superintelligence, right? And he has a new book too, I think, but I haven't read it.

Yeah, Deep Utopia, I think.

There you go, yeah. So how did you get in touch with Eliezer Yudkowsky, or like what, how did that happen?

So I was really interested in issues around like hardcore logic questions like Gödel's incompleteness theorem and Tarski's undefinability in undergrad, because I thought that was something that was going to be necessary to create AGI. And I kept searching, and I was just like learning Bayesianism as well, and many of these search queries led to a website called Overcoming Bias, which for some time I didn't click on because I thought that was a previous search result, because Overcoming Bias sounded like some sort of social justice thing. But eventually I clicked on it and I started reading the articles, and I really enjoyed it, and in particular enjoyed Eliezer's views.

So you started out actually thinking about how you would create AGI, right? I guess like many people in the AI field you're like, how do we create an intelligent system that can reason and can really have human values? Is that right?

Yeah, at the time my perspective was that we've kind of solved like the mathematical kind of reasoning part, now we just need to do learning. But it turns out that good learning depends on good representation, and that led me back to the logic, saying, ah, like how do we actually represent beliefs? And I thought, oh, of course there will just be like some solution, right? Like there'll be the best logic to use. But then digging deeper into these things, there's really a lot of fundamental questions that are like still quite unsolved in terms of like this idea of like what's the best logic, to the point where many logicians are kind of pluralists of like, oh, there's just lots of logics, there's some true logic.

So you're trying to find a good logic system that you could use to reason, or rather an AGI could use to reason about the world, is that right?

Yeah.

Interesting. So you talked to Eliezer and you said, I have this logic, or this goal to create a logic system that AGI will need. And...

Yeah, I sent him in a little email. It's like, like there needs to be this actual good logic, surely you must be thinking about these things based on your public writing, but I see that you haven't published anywhere about like these more technical aspects of the question, right? Like he had written up this big essay on the nature of truth, but like now in hindsight, deliberately, like he had not included any technical details. And so actually it was quite unclear what kind of theory of truth he was putting forward from a technical perspective.

So what happened when you actually reached out to him? You emailed him, and then went...

And then he said that in order to work together he had to have at least one voice conversation with me, because he just said that there's certain things that can come across in voice that don't come across in text. And so we arranged a phone call, we figured out the time zone difference, and I got him to talk about hardcore logic questions for about 10 minutes. I think we talked about the ordinal hierarchy. And I, because he's a hardcore constructivist and I have more Platonist leanings, let's say — I gather that that's like Vim versus Emacs in programming — so I was drilling in on exactly which ordinals he thought existed, because, and so he was kind of vague on like, well, I think these exist, this one I'm kind of agnostic about, and anything higher than that is maybe too much.

So you spent 10 minutes talking shop, and then...

And then at some point he was like, this isn't what this phone call is about, this phone call is about whether we can work together. And so then he gives me the elevator pitch for AI safety, which at the time I was quite skeptical of, but I think more because of motivated cognition than any good reason.

Can you explain motivated cognition?

Yeah, so I think like my conception of myself and my career at that time was, I want to become an AI scientist, right? Like I want to work on AI, I want to build AGI or be part of the project that builds AGI.

I see, so your worldview of this is me didn't mesh with like the idea of working on AI safety.

Yeah. And so then when he started talking about like, look, this stuff is dangerous, then I pull out the like science card of like, but progress, and like open science, like we, like we can't do science at all without having it be open because we need people to vet our ideas, and these kinds of arguments.

Yeah, which might be true but doesn't change the consequences of doing that research out in the open, of course.

Yeah.

So did he, what else did he ask you at that point?

So yeah, he gave me the pitch, he talked about the AI tiling the universe with von Neumann probes. I don't remember if he used the paperclip argument precisely at that time, but something like that, like the universe will tile — or sorry, the AI will tile the universe in some strange squiggles.

What else did he tell you in that call?

Then he asked me the question that would determine whether or not he could collaborate with me, which was, so if you discovered this one true logic that you're after tomorrow, would you publish it? And I said yes. And then he said, okay, I can't work with you. And that was basically the end of the call.

There's a pretty funny thing with AI safety work, which is that as you develop it more and more, the potential capabilities use of that work becomes greater and greater. So yeah, if you discovered something like a one true logic, that would be really valuable for AGI, even if you discovered that in, while trying to figure out how to make AGI safe, well, it might actually be a little dangerous to publish it. So that's something that a lot of people have started thinking about more recently, but I guess, but I guess he was on to it from the beginning.

Yeah, he was very about this kind of like, we need to do this research in secret, from the beginning. And then like, yeah, what I'm told, that he rejected a lot of potential collaborators at that time. And then later, around 2012, MIRI actually pivoted to somewhat more open research.

So I guess that's how you heard about AI safety for the very first time. But I know that at some point you actually ended up working for an AI safety organization, right, which is MIRI. So can you tell us a bit about MIRI and what they do, and what you learned while you were there?

Yeah, so MIRI is the Machine Intelligence Research Institute, which in the bygone era was called the Singularity Institute. This is kind of the institute that grew up around Eliezer, basically. And they actually changed their name, I think around 2012, from the Singularity Institute to the Machine Intelligence Research Institute, because at that time they were pivoting towards somewhat more open research, still keeping a lot of things secret, but trying to do real research about the AI safety problem in the public eye, to attract more researchers to the problem. And they felt that Machine Intelligence Research Institute was like a better brand for that purpose.

If all you've heard your whole career is machine learning, then I guess that makes sense.

Yeah, right, right. Like the term AI had actually fallen out of fashion, like in the AI winter in the 90s, and machine learning was like the real science in some sense. And so machine intelligence kind of makes more sense than artificial intelligence in that sense. So around that time I actually started working with MIRI. I went to my first MIRI workshop in 2012, or maybe early 2013, but based on a paper that I had published in 2012 about priors over logic, which kind of caught their interest. And I was still kind of skeptical of the AI safety stuff, but at that time that wasn't a strong barrier to working with them.

So can you tell us a bit about how MIRI thought about AI safety?

Yeah, so I want to kind of paint a picture which is not exactly a view that any person expressed to me in detail, but so it's kind of a caricature, or kind of like a view in hindsight, of what MIRI's AI safety research program was about. So you could say that a big portion of the AI safety problem is that human values are informal, and we need to somehow prove formal theorems or some kind of like strong argument about safety, right? So like, how do we get this informal sort of mush of human values like into computers, or into our formal proofs, to get formal safety guarantees?

So I guess the idea is like the formal world is really different from the informal world, and human reasoning and human values and so on is very informal, but computers are used to dealing with formal stuff. And in particular we really want these safety guarantees to be quite formal and quite rigorous, because we're quite worried, right?

And so the idea is like, we've seen in the past some ideas have transitioned from more informal to more formal. Probability theory is a great example, and so this isn't hopeless. It's like, okay, yeah, maybe we can somehow formalize more of human values. But this does seem like a particularly difficult case, because human values kind of touch on the whole human world. And so in some sense it seems as if you need to finish this project of formalizing human concepts, right? You need to kind of complete informal-to-formal bridge, almost kind of like finishing the project of philosophy, in order to get AI safety. And this is kind of the hardcore type safety approach that MIRI was interested, or at least a caricature of it.

And if you think about that problem, like trying to make human values formal, it's really really difficult, right? Like if you have a group of humans, they're not all going to agree with each other about what their values are, what should be done, like the moral questions basically. So to try to write that down in a way that a machine or like a logic-based system could understand is pretty much impossible.

So right, so I think we'll move on to part two, where we talk about how you've been updating your views because of LLMs, right? Like this original perspective on formal, informal, you need a bridge, you kind of changed your mind on that, is that right?

Yeah, at least to some extent. Of course this very formal approach is still kind of close to my heart, but I think we're living in a world where there's maybe like, let's call it a plan B. And so this update that I've been having since kind of actually starting in 2016, when I explicitly re-evaluated my beliefs about AI safety, I kind of wrote down two branches that we could go down. One of them was like, deep learning continues to progress, and it just so happens that I made this guess of like, in particular language models are going to be very important, maybe because that captures something of human reasoning. So like we kind of in AI we sometimes say language is this like AI-complete problem, right? Like an AI-complete problem is a problem that if you solve that, then you could solve any other problem that we call AI. And language kind of seems like this example that's rich enough, like we have like the idea of the Turing test is also getting at the same idea.

The other branch of possibility was somehow deep learning fizzles out and we have to come up with something else. And I assigned these explicitly like 50/50 probability. In hindsight, I think really I didn't believe the deep learning one. I really kind of thought like we're going to see something else emerge, something that fits more with this formal-to-informal bridging idea, right? But in fact it seems like you just scale up deep learning — of course Transformers were a major idea, but more or less you just scale up deep learning — and they start doing language really well, and they kind of already have all the informal human concepts in there. Not necessarily in a way that we can put a huge amount of trust in, of course. We see hallucinations all the time, we see like adversarial examples still and like in image recognition, and so there's maybe something deeply alien there. But there's also like, it's kind of really like, if you talk to it, it kind of like understands in a very practical sense what you're saying.

So if you run the experiment, for example, of asking ChatGPT — I think maybe I asked GPT-4, maybe asked GPT-3, I'm not quite sure — but if you asked this question of, if the user asked you for a cure to cancer and you gave the user a way to kill all life on Earth, would that count as a cure to cancer? Then it says no instead of yes, at least most of the time. Of course, since it samples answers, it can answer yes occasionally.

Most of the time humans don't go extinct. That's comforting, right?

It's actually comforting, right? Like what it means, the RLHF was working, right?

So yeah, it seems like it gives you some opportunity, right? Like people create systems like this BabyAGI system that utilize ChatGPT to try to create an agent somehow. And it's like, if you imagine somehow these people figure out how to do it well and scale it up, then at some point there might come a time when it's somehow generated a plan that is like a perverse instantiation of some goal the user has specified, like curing cancer, and it cures cancer by killing everybody. It's like, no more cancer if there's no life. And then it looks at this plan, and you imagine it might have a point where it asks, okay, does this plan satisfy what the user asked for? And it says no instead of yes most of the time. That's actually like an improvement over the sort of thing that I was imagining in 2016, say.

Like we talk about AI risks and we immediately talk about like, you ask it to perform these goals and it's going to misunderstand you, right? Like kind of one of the big concerns in AI risk is we don't know a goal that you can write down that is safe to just put all the optimization pressure on. Now, I'm not saying that it's safe to put all the optimization pressure on these concepts that the LLMs have, because I know that they're going to be alien kind of around the borders.

The optimization pressure that you're talking about is like when you specify a reward function, like a goal, and the AI is trying to learn that goal, then it just, it learns that to the exclusion of all else. And so if you haven't like your function precisely correctly, then it ends up learning the wrong thing.

And it's so easy to trigger that by accident, especially like with reinforcement learning, because you just keep looking at the same question, the same reward, over and over again, right? And so this kind of opportunity that I see, this kind of plan B, is without solving the sort of hardcore formal AI safety problem, which I think we should still try to solve, it seems like maybe we can use LLMs, as long as we don't just keep scaling them up and up and up, because maybe something very strange happens once we hit GPT-7 or whatever. But these systems now are like kind of just doing what they appear to be doing, right? And by that I mean you ask it to do something and it's basically using common sense and just kind of trying to do that thing, right? The amount of potentially devious thinking there is not that, not that much, right? Like it doesn't have too much depth of thought at the moment.

And so if we can kind of increase the capability of these systems with scaffolding, like this BabyAGI system or whatever, but in a way that avoids several pitfalls. So I think of like, like we need to avoid inner optimizers, so we need the system itself not to have like some kind of devious subagent inside of it. And then we also need to avoid what I call bureaucratic risks. That's where we have like somehow like a very long chain of reasoning, each individual step is kind of basically doing what it appears to be doing, we can look at the reasoning that the LLM produces, we understand it, but somehow the global picture is lost, and so something bad happens from that.

This is something that was talked about a lot in the context of Paul Christiano's HCH proposal, which created a bureaucratic kind of tree of LLM-type agents that are trying to accomplish some task. And Paul Christiano would make these arguments of like, this can do anything, this can solve any problem that some other proposal would solve. And then Eliezer would come back with arguments like, but it might only be able to do that because it's able to run arbitrary programs by passing them along the tree. And so in order to solve problems, Paul Christiano himself was agreeing, you would have to come up with these kind of procedures like, here's something that I can get the bureaucracy to do to then come back with an answer to my problem.

So instead of just trying to bridge the informal and formal worlds like completely, you're basically saying that you can use LLMs as a midpoint there. They can do some of this understanding of a human value, and but they kind of act in a formal way in the sense that they're running on a computer at least, right?

And so I'm saying that if we use them cautiously, somehow it seems like there might be a way to avoid a bunch of safety concerns without kind of solving the hardest parts of the AI safety problem.

Very interesting. So that brings us to part three, and we'll talk about what this perspective means if you think about the release of OpenAI o1.

Yeah, so to me I'm like, oh, like several months ago it seemed to me like we were in this kind of nice regime where like, yes, OpenAI is scaling up these models faster than I would want, yes, I would like them to be thinking much more about what I think of as the real aspects of the safety problem, but at least it seems like we're kind of sticking in this paradigm where they're kind of just understanding human concepts, they are doing roughly what they appear to be doing. And my only concern about if they keep scaling up is like, maybe at some point they kind of lose this property somehow, they basically start doing a lot of thought in any given prompt, right? Which means they could be doing all kinds of potentially malicious things, or like things that we don't understand along the, along the way.

Yeah, but now with o1 it seems like they're kind of doubling down on this reinforcement learning approach, right? And so you're taking these chains of thought which allow you to implement like basically arbitrary computations to achieve some task, and they have a fairly good prior on computations because these chains of thought are like kind of smart, right? But now we're doing reinforcement learning directly on like, from the end result, like can we optimize for chains of thought which produce end results that we want.

So you're basically saying that OpenAI, using reinforcement learning, meaning you just specify a function that you want to be optimized, some reward function, and they're moving towards that instead of doing the learning on an input corpus of data which is then put into one model. They already have a model, and they are looking at the chain of thought that gets produced by that, and then they're doing reinforcement learning on the actual chains. Is that what you think is going on there?

Yeah, we don't know all the details of what's going on, right? So they've said something about like, they are not applying safety-type reinforcement to the chains themselves, only to the end results, which is itself seems kind of concerning, although it's an interesting idea. I think they want a canary in the coal mine in some sense. This is me making up motivations for them, by the way. Like, if doing this dangerous thing causes it to transparently start scheming within the chain of thought, they want to see that.

And indeed they have seen that.

Yes, it was in the system card that it started doing that.

Yes, I talked about that on a previous video which you can check out probably over here.

So yeah, but so my concern is you're not actually getting this kind of canary that maybe they think they're getting. Like, yes, we see it explicitly scheming, but the problem is that by doing this kind of end-to-end reinforcement learning that is encouraging a particular type of end result, you encourage patterns in the chain of thought that help it compute this end result without any filter on whether those patterns themselves are interpretable.

And so I think Andrej Karpathy on Twitter said like, you know that this training is working if it starts inventing its own language.

And that's where it's actually problematic, right? Because it's now inventing its own shortcuts and short forms for what it wants to tell itself in the future, in the next iteration.

And right, eventually it has nothing to do with English, potentially, right? And so we see actually that it's starting to look less like English, is that right?

Yes, in fact if you look at the summary, if you run o1 you see a generated summary of the internal thoughts. It's not the actual individual thoughts, but you see a generated summary, and in that summary I've often seen typos or words that don't really exist, or combinations of other words. And that summary is probably generated from the text directly, so that word or that misspelled word would have been present there. So it's already making up words. I guess you can often see what the two root words were when it, when it sticks them together, and it could just keep going further in that direction, right?

And that's, I guess there's kind of two concerns. Like one, if it just starts looking like complete gibberish to us, then we kind of know, okay, we've lost the transparency, that's bad, but at least we know. The second concern is like, what if it's like subtly doing this? It's like it still looks a lot like English, but actually like the way that it's using words, or like the, some subtle, even like punctuation or what, is like cuing it more than we think. And so when we look at the thoughts we are in some sense seeing the computation, but we understand much less of that computation than we naively think. And that's I think like a really concerning case, because then OpenAI might come to conclusions like that, like for example that they have, think they've done something that's eliminated explicit scheming, but actually it is scheming that is explicit to the system because it understands its own new invented language.

Yeah, that's kind of a form of steganography, right? You're hiding a message inside an otherwise innocuous message, and you can't really tell that there's actually a hidden layer there. But if you're, if you have a code book or something like that that tells you how to look for the hidden message, then it's easy to find. And of course the LLM is talking to itself in the future, so it can easily make up that kind of code book.

And actually it's funny to mention the first case where it makes an entirely different language, because that is what Eric Schmidt, the ex-CEO of Google, said. He said, let's just keep developing AI models as fast as we want, and as soon as we see them making up language to talk to each other, then we have to stop. That was his red line. I wonder if he has come to this, the same conclusion about o1 or not.

Interesting. But I feel like if they start putting any pressure on the system to keep it looking like English, then we're going to get into the steganography case.

Yes, because it's like easy to say like, oh, we can punish it when it doesn't look very English-y, like train some reinforcement for that.

Yeah, but then that doesn't remove this subtly hidden information, it just like forces it underground.

Yeah, exactly, it's almost worse in that case, you don't know that there's messages going back and forth.

Yeah, so that's really what I wanted to talk about, is this like, yeah, it just seems like o1 is like particularly a really bad idea. It's putting us in this regime where again we have to solve kind of the hard alignment problem, we have to like have this reinforcement learning exactly right, or else things can go very wrong. And it creates these like subtle failure modes, some of which are more visible than others.

So basically, whenever you're training against a reward function, especially with reinforcement learning, you keep looking at the same thing over and over again, you tend to overfit that reward function, right? You just do exactly what it says. And that's an issue if the reward function doesn't match your problem. We're now entering a regime where the reinforcement learning isn't happening on the initial model training, but actually on the chain of thought between the models, as has been happening in o1. That could actually force the models to start encoding information in this chain of thought, to save space, to communicate more complex concepts, to do whatever, to hide devious behavior.

And am I right in saying that you're not really that concerned about o1 specifically, but like this direction that we're going in is kind of, is kind of problematic? Or are you also worried about o1 specifically?

I guess I only know for o1-preview, right? Like I have, I don't have access to o1, and it's supposedly like more impressive. But generally speaking, yeah, I'm not like so concerned about o1 specifically, but I feel like maybe we're getting pretty close to something that's concerning if you turn the crank on this particular kind of training. I don't know, like I guess it does put us in a world that I think is like, maybe we will get early warning signs of AI risk, in the sense of like systems that are smart enough to do something really stupid and like create like visible catastrophes that don't actually kill all the humans, maybe. I don't know, I'm kind of also updating towards that kind of world.

This counts as optimism from an AI safety person, right?

Right, right, maybe we won't kill all the humans.

But thank you very much, Abram, for talking today. And I think it was very interesting to hear about your original work at MIRI and that kind of bridge between formal and informal, and then the new view that LLMs kind of sit in the middle, and what happens when you start turning the crank on optimization the way that o1 is starting to do. So thank you very much.

Thank you.

If you liked this video, check out this previous one I made about o1. It was a discussion right after o1's release, and we go through some implications of the safety analysis that OpenAI did on the model in that video. That's all for today, thank you very much for watching. Bye.
