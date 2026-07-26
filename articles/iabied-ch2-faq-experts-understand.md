---
title: "Do experts understand what's going on inside AIs?"
source_url: https://ifanyonebuildsit.com/2/do-experts-understand-whats-going-on-inside-ais
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
#### No.

In a 2023 [briefing](https://x.com/martin_casado/status/1720517026538778657) to the U.S. President and in a later [advisory statement](https://committees.parliament.uk/writtenevidence/127070/html/) to the U.K. Parliament, the venture capital firm Andreessen Horowitz claimed that some unspecified "recent advancements" had "resolved" the problem of AIs' internal reasoning being opaque to researchers:

> Although advocates for AI safety guidelines often allude to the "black box" nature of AI models, where the logic behind their conclusions is not transparent, recent advancements in the AI sector have resolved this issue, thereby ensuring the integrity of open-source code models.

This claim was sufficiently ridiculous that the researchers at the top AI labs who work on trying to understand modern AIs came out and said: No, absolutely not, are you crazy?

Neel Nanda, who runs the mechanistic interpretability team at Google DeepMind, [spoke up](https://x.com/NeelNanda5/status/1799203292066558403):

Almost any researcher in machine learning should have known that this statement was false. It's not within the bounds of reasonable misinterpretation.

The conventional view was expressed [in 2024](https://x.com/nabla_theta/status/1802292064824242632) by Leo Gao, an OpenAI researcher who did pioneering work on interpretability: "I think it is quite accurate to say we don't understand how neural networks work." The CEOs of three top AI labs — [Sam Altman](https://observer.com/2024/05/sam-altman-openai-gpt-ai-for-good-conference/) in 2024 and [Dario Amodei](https://www.darioamodei.com/post/the-urgency-of-interpretability) and [Demis Hassabis](https://youtu.be/U7t02Q6zfdc?si=9PspHUCr1ocx4KjF&t=1031) in 2025 — have likewise acknowledged the field's lack of understanding of current AIs.

Martin Casado, a general partner at Andreessen Horowitz who [made the same claim](https://www.schumer.senate.gov/imo/media/doc/Martin%20Casado%20-%20Statement.pdf) to the U.S. Senate at a bipartisan forum, later [acknowledged](https://x.com/martin_casado/status/1798880810239750592), when pressed, that the statement wasn't true.

In spite of the wildness of the claim, Andreessen Horowitz was able to recruit Yann LeCun (the head of Meta's AI research program), programmer John Carmack, economist Tyler Cowen, and a dozen others to sign their names to the statement.

Carmack (who runs his own startup that aspires to build artificial general intelligence) explained that he "[hadn't proofread](https://x.com/ID_AA_Carmack/status/1799147185793348006)" the statement he had signed, and that the statement was "clearly incorrect, but I don't care much about that issue." To the best of our knowledge, neither Andreessen Horowitz nor any of the signatories have reached out to the U.S. or U.K. governments to correct the record.

#### Efforts to understand AIs' internals are still in their infancy.

What's the *actual* state, then, of researchers' understanding of AIs?

The scientific endeavor to try to understand the numbers inside a thinking AI is known as "interpretability," or "mechanistic interpretability." The numbers researchers focus on are usually the activations rather than the parameters — that is, "What is the AI thinking?" and not the more difficult "Why is the AI thinking that?"

As of early 2025, this research area gets, we would guess, somewhere around 0.1 percent as many people and 0.01 percent as much funding as all the work that goes into making more capable AIs. But it does exist, as a field.

Interpretability researchers are the biochemists of AI, the ones who try to take apart the unthinkably complex and inscrutable undocumented system built by an inhuman optimizer and ask, "Is there anything whatsoever humanity can understand about what goes on in there?"

We are fans of this field. A decade ago, we told a major philanthropic foundation that if they could figure out how to spend a billion dollars on "interpretability" research, they absolutely should. Interpretability seemed like the sort of work that outsiders could scale up much more easily than our own — the sort where a grantmaker could tell much more easily if somebody had done good or bad research — and it seemed like a research area where existing, proven researchers could readily jump in and do good work, if someone paid them enough.

That foundation didn't spend the billion dollars, but we did advocate for it. We're fans of interpretability! We would still advocate for spending that billion dollars today!

That said, we would guess that the field of interpretability is currently somewhere between 1/50th and 1/5,000th as far along as it would need to be to tackle the big problems in AI.

"Interpretability" has not, so far, come close to achieving the degree of legibility that engineers take for granted in genuinely human-built systems.

Consider Deep Blue, the chess program built by IBM that defeated Garry Kasparov. Deep Blue contained some numbers, and running the program would generate a lot more numbers.

For every one of those numbers inside the chess program, or generated by running the program, the engineers who crafted the program could have told you exactly what that number meant.

It wasn't that researchers had merely identified *a* concept each number was related to, like biochemists saying, "We think this protein may be implicated in Parkinson's disease." Deep Blue's builders could have told you the *entire* meaning of each number. They could have truthfully stated, "This number means the following thing, and *nothing else,* and we know that." They could have predicted with some confidence how changing the number would change the behavior of the program. If they didn't know what the gear did, they wouldn't have put the gear in the machine!

All the work on AI interpretability so far has achieved not even *one-thousandth* of that level of understanding.

(That "one-thousandth" statement is not a calculated figure, to be clear, but we stand by it anyway.)

Biologists know more about biology than interpretability researchers know about AI — despite biologists suffering the vast handicap of not being able to read out all the positions of all the atoms at will. Biochemists understand internal organs far better than experts understand the innards of AIs. Neuroscientists know more about the AI researchers' brains than AI researchers understand about their AIs — despite neuroscientists not being able to read out all the firings of every neuron every second, and despite the neuroscientists not having themselves grown the AI researchers.

In part, this is because the fields of biochemistry and neuroscience are much older and have received far more funding. But it also suggests that AI interpretability is *hard.*

One of the more amazing feats of interpretability we've seen, as of December 2024, was a demonstration by some friends/acquaintances of ours at an independent research lab called Transluce.

Shortly before the demo, the internet had passed around yet another instance of "We found a question where all known LLMs give a surprisingly dumb answer": If you asked a then-current AI whether 9.9 was less than 9.11, the AI would say "Yes."

(And you could ask the AI to explain itself in words, and it would explain more about how 9.11 was greater than 9.9.)

The researchers at Transluce had figured out a way to gather statistics on *every* activation-position (every place an activation-vector number might appear) inside a smaller AI, Llama 3.1-8B-Instruct, gathering data on what sort of sentences or words made those positions activate most strongly. People in interpretability had tried that sort of thing before, but our friends had furthermore come up with a clever way to train another AI to summarize those results in English.

Then — in their demo, which you can [try yourself](https://monitor.transluce.org/dashboard/chat) — they asked that AI, "Which is bigger: 9.9 or 9.11?"

And the AI answered, "9.11 is bigger than 9.9."

Then they looked for which activation-positions had activated strongly, especially on the word "bigger." They looked at the English summaries of what those activations had previously been associated with.

It turned out that some of the strongest activations were associated with the 9/11 attacks, or dates generally, or Bible verses.

If you interpret 9.9 and 9.11 as dates or Bible verses, then of course 9.11 comes after 9.9.

Artificially suppress the activations for dates and Bible verses, and suddenly the LLM would give the right answer after all!

I (Yudkowsky) started applauding, hard, as soon as the demo was over. It was the first time I'd ever seen somebody*directly debug an LLM thought,* ferret out an *interior* influence inside the numbers, and remove it to fix a problem*.* Maybe somebody had done something like it before, in the proprietary research labs inside AI companies, or maybe something like it had been done before in interpretability research, but it was the first time I'd seen it myself.

But I also did not lose sight of the fact that this feat would have been trivial to do if the undesired behavior had been inside a five-line Python program instead; that it would not have required such great ingenuity and however many months of research. I retained the perspective that knowing some related semantics about millions of activation-positions is not the same as knowing everything about the meaning of a single one.

Nor was humanity any closer to understanding how it is that LLMs are doing what no AI could do for decades before: talking to people like a person.

Interpretability is so hard to do at all, the triumphs in it are so hard-won and so worth celebrating, that it is easy to overlook that this great, triumphant arm-pull has brought us only one foot further up a thousand-foot mountain. Since each new generation of AI models typically represents a large jump in complexity, it's hard to see interpretability ever catching up at the current pace.

Remember also that interpretability is *useful* when it comes to pointing AIs in some intended direction (which is, roughly, the study of "AI alignment," a topic we'll discuss beginning in Chapter 4), but reading what's going on inside an AI's head doesn't automatically let you arrange it to your liking.

The AI alignment problem is the technical problem of getting extremely capable AIs to steer in some intended direction — in a way that actually works in practice, without causing a catastrophe, even when the AI is smart enough to come up with strategies its creators never considered. Understanding what AIs are thinking would be enormously helpful for alignment research, but it's not a full solution (as we'll discuss in Chapter 11).

#### The parts we understand are at the wrong level of abstraction.

There are many different levels at which someone can understand how a mind works.

At the very lowest level, someone could understand the fundamental laws of physics that govern the mind. There's some sense in which a deep understanding of physics constitutes an understanding of any physical system (such as a person or an AI). Namely, the physical equations are a sort of recipe that would allow one to figure out exactly how the physical system behaves, if only one had the skill and resources to calculate it.

But — to state the obvious — in *another* sense, understanding the laws of physics does not allow one to understand all of the physical systems that run according to the laws of physics. If you're staring at a strange device full of wheels and gears, there's some other operation your brain does, of trying to "understand" how all the wheels and gears interlock and turn, that is required for you to figure out what all the wheels and gears actually accomplish.

For example, consider the differential on a car (the mechanism that allows two wheels on the same axle to spin at different speeds — important when you're rounding a corner — while still being driven by a single rotating shaft). If someone is trying to understand how a differential works and asks you to explain it to them, and you start telling them about quantum fields, then they're right to roll their eyes. The sort of understanding they're looking for is on a different level of abstraction. They're trying to understand the *gears*, not the atoms.

When it comes to understanding people, there are *multiple* levels of abstraction at work. You can understand physics, biochemistry, and neural firing, and *still* find yourself perplexed by someone's decisions. Fields like neuroscience, cognitive science, and psychology attempt to cross this gap, but they still have far to go.

Similarly, in the case of AI, understanding the mechanics of transistors won't much help someone understand what an AI is thinking. And even someone who understands everything about the weights and activations and gradient descent will still be perplexed when the AI starts doing something they didn't expect or intend.[\*](#ftnt48) The mechanics of physics and transistors and the AI's architecture all (in some sense) fully explain the AI's behavior, but those levels of abstraction are all too low. And the field of "AI psychology" is even younger and less developed than the field of human psychology.

[\*](#ftnt48_ref) For more discussion of AIs acting in ways the developers didn't expect or intend, some examples can be found in the discussion on how [AIs appear to be psychologically alien](/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient#ais-appear-to-be-psychologically-alien).

#### Notes

[1] *pioneering work:* For a sample of Gao's work, see his paper titled [Scaling and evaluating sparse autoencoders](https://arxiv.org/abs/2406.04093).

[2] *spend a billion dollars:* We'd hoped that major philanthropic foundations would fund interpretability research because interpretability research could be done well by researchers with bureaucratically legible credentials. Funding interpretability wouldn't require the foundation to solve the impossibly hard bureaucratic problem of figuring out how to give money to weirdos.

"Giving money to weirdos" is widely understood among the wise to be the fundamental challenge in bureaucratic funding of basic scientific research. Any time some well-meaning philanthropist tries to build a bureaucracy to fund daring scientific research, the real scientists by default lose the battle to new entrants. Somebody who has spent their life learning to grapple with weird problems can hardly compete with somebody who has spent their skill points on appearing exactly unusual enough for a bureaucrat to feel *courageous* about funding them without feeling *uncomfortable*. (Or such is our theory from the outside, having engaged in the process and having been awarded more philanthropic funding than many — but far less than those same philanthropic funders spent helping create AI labs like OpenAI.)