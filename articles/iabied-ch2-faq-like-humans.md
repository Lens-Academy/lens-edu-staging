---
title: "Won't LLMs be like the humans in the data they're trained on?"
source_url: https://ifanyonebuildsit.com/2/wont-llms-be-like-the-humans-in-the-data-theyre-trained-on
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---

%%
Add discussion note here:

...

%%
#### There's a difference between the machinery it takes to be one person and the machinery it takes to predict many individuals.

AIs like ChatGPT are trained to accurately predict their training data. And their training data is made mostly from human text, such as Wikipedia pages and chat room conversations. (This part of the training process is called "pre-training," which is what the "P" in "GPT" stands for.) Early LLMs like GPT-2 were trained *exclusively* for prediction in this way, while more recent AIs are also trained on things like accuracy when solving (computer-generated) math problems, and giving good responses according to another AI model, and various other goals.

But consider an AI trained only on predicting human-generated text. Must it become human-like?

Suppose you take an excellent actress[\*](#ftnt58) and have her learn to predict the behavior of all the drunks in a bar. Not "learn how to play an average stereotypical drunk," but rather "learn all the drunks in this one bar as *individuals*." LLMs aren't trained to *imitate averages;* they're trained to *predict individual next words* using all the context of previous words.

It would be foolish to expect this actress to *become perpetually drunk* in the process of learning to predict what each drunk person will say. She might develop parts of her brain that are pretty good at acting drunk, but she would not become drunk *herself.*

Even if you later ask the actress to predict what some particular drunk in the bar would do, and then to outwardly behave according to her own prediction, you still wouldn't expect the actress to then feel drunk inside.

Would it change anything if we were constantly tweaking the actress's brain to make *even better* drunken-individual predictions? Probably not. If she *actually* ended up drunk, her thoughts would accordingly end up sloppy, interfering with the hard work of an actress. She might get confused about whether she was predicting a drunk Alice or a drunk Carol. Her predictions would get worse, and our hypothetical brain-tweaker would learn not to tweak her brain that way.

Or, to put it another way: A human who becomes excellent at imitating birds and understanding their psychology doesn't thereby become a bird in a human's body, nor even become especially psychologically birdlike in their day-to-day life.

Similarly, training an LLM to make excellent predictions about the next word output by many different people writing about their past psychedelic experiences should not thereby train the LLM itself to be just like a human on drugs. If the LLM's actual internal cognitions were to be distorted in a way reminiscent of "being on drugs," this would interfere with the LLM's hard work of next-word prediction; it might get confused and think an English speaker was going to continue in Chinese.

We are not saying, "No machine can ever have anything resembling a mental state a human has inside." We are saying that the current kind of ML technology should not by default be expected to create drunk-predicting engines that work by getting drunk themselves.

The work of figuring out how to predict all sorts of different humans is different from the work of being one human. Which means that AIs built with anything like today's methods should not be expected to become much like a human, in the course of learning to act like any given one of us depending on the request.[†](#ftnt59)

#### The architecture of LLMs is very different from that of humans.

Refer to Chapter 2 for a brief discussion of how LLMs seem pretty alien.

In Chapter 4, we'll go deeper into how AIs wind up with very weird preferences and pursuits — a phenomenon that we've already begun to see in the wild, with more examples piling up even after the book went to print. We collect some [examples](/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient) in the online resources for Chapter 4.

[\*](#ftnt58_ref) We aren't using the more modern, gender-neutral word "actor" in these resources because "actress" prevents ambiguity about whether we are referring to "a stage or screen performer" versus "an agent that takes actions."

[†](#ftnt59_ref) If you train an AI to predict how your friend Alice acts when angry, then this will likely allow the AI to *imitate* Alice's angry behavior too — at least once the AI's predictions become good enough. But the act of getting good at predicting this won't make the AI *actually* angry; and when the AI uses its prediction to imitate Alice, that won't make the AI "actually angry" either.

When you leap to the conclusion that angry-looking behaviors must go with an angry underlying*feeling*, it's likely that you aren't just putting forward an abstract theory that AIs and humans have something deeply in common. You're to some extent attributing anger *automatically* — the AI just *seems angry*, like a convincing actress.

In the case of a human actress, you at least know that the actress *does* ever experience genuine anger. Being human, she may be drawing on her own feelings in order to convincingly portray anger on command. But LLMs share none of that. It really is a much less sensible inference to say, "That LLM sounds angry to me and therefore it's probably actually angry."

Why not expect LLMs to solve the problem of predicting anger by becoming angry themselves?

To some extent, that's how humans would solve the problem. Part of why humans are good at predicting other humans is that we've evolved to "put ourselves in the other person's shoes." To predict how Alice will act if she gets angry, I let some part of *myself* be angry, and I see how *I* would then behave. This is a topic we'll discuss more in the [online supplement](/4/human-values-are-contingent) to Chapter 4.

But the whole reason this works for humans, when we try to predict one another, is that we all share the same basic brain structure. This gives humans the shortcut of using their brain as a template for the other person's brain.

LLMs are in a vastly different position. Their trillions of tokens of training try to get them to predict, from scratch, a wide variety of human minds that are nothing like the LLM at the outset. The most effective way to solve this other-prediction problem will not look like the AI *becoming angry first* in order to figure out what anger is and figure out how angry humans behave.

More generally: Efficient, complicated, uncertain reasoning about some complex event doesn't *usually* resemble a detailed internal forward simulation of that event. For instance, the uncertain reasoning will often track many different live possibilities. Even when forward simulation *is* the most effective practical prediction method, the simulation doesn't usually leak out and turn the predictor into the thing it's predicting.

And so there are many behaviors, both good and evil, that an LLM can exhibit; and yet at the end of the day what we're seeing is a mask, and what lies behind the mask is something [unknown](/4/doesnt-the-claude-chatbot-show-signs-of-being-aligned#todays-llms-are-like-aliens-wearing-many-masks), and something that [isn't very human-like at all](/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient#ais-appear-to-be-psychologically-alien).

Currently, a little bit, and maybe more by the time you read this, AIs have been trained to predict some *very* human-like behaviors; and frameworks like ChatGPT or Claude can turn these predictions into nice-appearing outward behavior. Not just human behaviors, but humane behaviors — even noble ones.

AI companies could try to train AIs to predict and imitate some of the more beautiful and true sides of the human spirit. They may try it, for cynical reasons or for nobler ones. In a way, it says a lot about this field and its people that, as of late 2024, nobody has *already* tried training an AI to predict the outward behavior of just…being a nice person. To our knowledge, nobody has tried just making a dataset of all and only the kind utterances of humanity and training an AI only on that. Maybe if someone did, they'd develop an AI that simply acted in a kindly way, that expressed beautiful sentiments, that acted as a beacon of hope.

It wouldn't be real.

We wish desperately that it would be real, but it wouldn't be real.

Depending on how effectively the LLM predicts the preferred answers of users like us — the things we would prefer to hear about noble sentiments, about hope and dreams, about only wanting a beautiful future together for both species — it's possible that one or both of your authors will end up crying, if ever the AI companies create such an entity. But it won't be real, any more than an extensively rehearsed and corrected actress who was finally made to recite those words in a play would be real. The curtain falls; there isn't a dry eye in the house; but it was still, at the end of it all, a performance.

That is not how you would go about building an artificial intelligence that actually held beautiful sentiments, that was really working with all its heart to steer for a brighter future. AI growers don't know how to grow an AI that feels that way inside. They train AIs to predict, and to turn that prediction into an imitation.

The AI companies (or hobbyists) may gesture at the actress they grew, and say, "How can you possibly doubt this poor creature? Look at how you're hurting her feelings." They may even manage to convince themselves it's the truth. But tweaking black boxes until something inside them learns to predict noble words is not how beautiful minds would be made, if human minds ever learned to make them.

Stated more plainly: Anthropomorphic behavior shouldn't be expected to pop up *spontaneously*. Additional arguments must be made that when AI companies force humanlike behavior deliberately, the inner "actress" ends up resembling the outer human face that she has been grown and trained to predict.