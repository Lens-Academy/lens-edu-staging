---
title: "AI? Just Sandbox it... - Computerphile"
channel: "Computerphile"
url: "https://www.youtube.com/watch?v=i8r_yShOixM"
---

%%
Add discussion note here:

...

%%

We see a lot of comments on your videos about people who just say, "Oh, just simply do this. That will be the answer for all of these problems." Yeah. And I admire them for getting stuck in and getting involved. But one thing that always strikes me is people say, "Just change this bit of code," or, "Just change this value." And it strikes me that if we invent AGI or happen upon AGI, the reality is it's probably going to be a neural network that you don't actually know exactly how it's working anyway. How... What are your thoughts on that?

Yeah. To... Yeah, to the people who think they've solved it, either you're smarter than everyone else who's thought about this problem so far by a big margin, or you're missing something. And maybe you should read some more of what other people have thought, and learn more about the subject. Because it's cool. Like, I think it's great that people come in and try and solve it, and try and find solutions. And we need that. But the... Yeah, the problem is not a lack of ideas. It's a lack of good ideas.

This kind of coming in from the outside and saying, "Oh, yeah, I've got it. I figured out the solution," is obviously arrogance, right? But the whole artificial general intelligence thing is an inherently arrogant thing. It's quite hubristic. You talk about playing God.

Making God. Like... But also that new "Oh, I've got it. This is how you do it." Sometimes that does work, that approach. Yeah, sometimes. Cuz you see stuff that people have been too close to the metal to... I don't know if that's a word. Close to the problem to... Right. Right. Yeah. So sometimes you get too close to it, you can't see the picture, you're inside the frame, whatever. It's totally possible that some random person is going to come up with a real workable solution. And I would love, I would love that to happen. I think that would be the best. Because then everyone would have to try and figure out how to cite a YouTube comment in a research paper. I presume there's already style advice for that.

Anyway, but the problem is from the outside view, you get a million of these, right? And so a million minus one are going to be not worth your time to read, which means even the good one isn't actually worth your time to read on balance, cuz you can't... How are you going to differentiate it? So the only thing you can do is get up-to-date on the research, read the papers, read what everybody else is doing, make sure that what you're doing is unique, and then actually write something down and send it to a researcher, write it down properly, and make it clear immediately up front that you're familiar with the existing work in the field. And then maybe you're in with a chance, but what will probably happen is in the process of all of that reading, you realize your mistake. It's still worth doing. You've learned something.

This is part of why AI safety is such a hard problem, I think, in the sense that a problem can be quite hard, and you look at it and you can tell it's quite hard. A problem that's really hard is a problem you look at and then immediately think you've got a solution, and you don't. Cuz then you don't even... You're like the... It's like if you're like the satnav, right? You're confidently with the wrong answer now rather than at least being honestly uncertain.

Yeah, like legibility in machine learning systems is really low right now. They're black boxes, right? They're not legible in that you can't easily tell what any given part of it does or how it works. And that is a real problem for safety, definitely. I think right now, right now the stage we're at with AI safety is we're trying to specify any kind of safe agent, which is trying to build something from the ground up that will be safe. And I think that's much easier than taking some existing thing that works but isn't safe and trying to make it safe. I don't think that approach, to be honest, is likely to be fruitful.

I give a really dodgy example of how this might be something people can get their grips with, which is the Star Wars scene where the robots are given a restraining bolt. R2-D2 says, "Oh, I can't do that unless you take this restraining bolt off." "If you remove the code, he might be able to play back the entire recording." He then promptly runs away. "So, I guess you're too small to run away on me if I take this off." This is like retrofitting some kind of a restraining bolt.

Yeah, so there's different things, right? Building an unsafe AI and then trying to control it against its will is idiotic. I think having some of those controls or ways of keeping the system, limiting what the system can do and stuff, is sensible, but it's so much better to make a system that doesn't want to do bad things than to try and keep one in.

So this is like the idea of, oh, can't we just sandbox it? Right. Yeah. It's like, constraining an AI necessarily means outwitting it, and so constraining a superintelligence means outwitting a superintelligence, which just by definition is not a winning strategy. You can't rely on outwitting a superintelligence. Also, it only has to get out once. That's the other thing.

If you have a superintelligence and you've put it in a box, so it can't do anything, that's cool. Maybe we could even build a box that could successfully contain it. But now what? We may as well just have a box, right? There's no benefit to having a superintelligence in a box if you can't use it for anything. It needs to be able to do things. An AI properly contained may as well just be a rock, right? It doesn't do anything. If you have your AI, you want it to do something meaningful. So now you have a problem of: you've got something you don't know is benevolent, you don't know that what it wants is what you want, and you then need to... You presumably have some sort of gatekeeper who it tries to... It says, "I'd like to do this." And you have to decide, "Is that something we want it to be doing?" How the hell are we supposed to know? How can we, if we're outsmarted, how can we reliably differentiate actions we want to allow it to take from actions we don't?

And maybe the thing has a long-term plan of doing a bunch of things that we don't notice at the time are a problem until it now then can get out, right?

Actually, this speaks, this speaks to a more general thing, which is there's often a trade-off between safety and effectiveness. Like with anything, right? Anything you're designing, there's going to be... You're going to be trading off different things against one another, and often you can trade in some effectiveness to get some safety, or vice versa. So some of the things in this paper are like that, where the thing does become less powerful than an AI designed differently, but it also becomes safer. That's always the way it is.

Well, it's just where you put your resources, I suppose, isn't it? Right, but it's inherent to the, to the thing, like, and this is true of any tool, right? The more powerful the tool is, the more dangerous it is. And if you want to make a powerful tool less dangerous, one of the ways to do that is going to involve making it less powerful. Or less flexible, or less versatile, or something that's going to reduce the overall effectiveness of it as a tool in exchange for more safety. And it's the same with AI.

And obviously you're going to be a server for whatever product you're using. Now, anytime that Bob sends Alice a message, it's going to go via the server by definition, because that's the thing that relays the messages to Alice. It knows how to communicate with Alice, it knows what her phone number is. It has a list of your contacts and things, this is how it works. This could be a phone provider,
