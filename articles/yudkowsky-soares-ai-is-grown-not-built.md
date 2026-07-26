---
title: AI Is Grown, Not Built - The Atlantic
source_url: https://archive.is/blU6r
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
published: 2025-09-15
created: 2026-02-04
description:
tags:
  - clippings
---

%%
Add discussion note here:

...

%%
### Nobody knows exactly what an AI will become. That’s very bad.

![](https://ddrn4nc0f9fxil.archive.is/blU6r/3327d8705a1fb90970f0aa1d054372f9f7f4c848.avif)
Artificial intelligence is software, but it is not human-designed and hand-crafted like any traditional program is. Instead, modern AI is grown, a bit like an organism. In important ways, the undertaking is closer to how a human gets made. Engineers understand the *process* that results in an AI, but they don’t much understand the AI that results.

This is already a problem—nobody at xAI seems to have planned for Grok to start calling itself “ [MechaHitler](https://archive.is/o/blU6r/https://www.theatlantic.com/newsletters/archive/2025/07/grok-defense-department-contract/683538/),” much like nobody at OpenAI decided that ChatGPT would lead certain users to develop “ [AI-induced psychosis”](https://archive.is/o/blU6r/https://www.psychologytoday.com/us/blog/psych-unseen/202507/deification-as-a-risk-factor-for-ai-associated-psychosis) —and it will become much larger as AIs get smarter. Modern AI companies are racing to create AIs that are [“superintelligent”](https://archive.is/o/blU6r/https://www.theatlantic.com/technology/archive/2024/10/agi-predictions/680280/) —that outperform every human on every mental task. They didn’t set out just to build chatbots; the chatbots are a stepping stone on their path to superintelligence. Some people worry about who will be in control of such superintelligences, but in reality, *nobody* will be in control. The AIs are grown rather than constructed, and a grown AI has drives and behaviors that nobody asked for and nobody wanted.

We are two research scientists at the Machine Intelligence Research Institute, a nonprofit that has been working on questions relating to machine superintelligence since 2001, long before these issues got much publicity or funding. One of us, Eliezer Yudkowsky, is one of its co-founders. The other, Nate Soares, is its president. Together, we have studied how nonhuman intelligences will think, behave, and pursue their objectives. The past two decades have seen far less progress toward human-friendly machine intelligence than was originally hoped. The current situation seems to us terrifically dangerous, and we think humanity should put a simple stop to the race for superintelligence by international treaty, reining in all the companies simultaneously. The current technology just does not offer anyone enough control over how a smart AI would turn out.

![If Anyone Builds It Everyone Dies by Eliezer Yudkowsky and Nate Soares|645x1000](https://cdn.theatlantic.com/media/files/61hjpxgdtil_uf10001000_ql80_.jpg)

This essay has been adapted from the forthcoming book, If Anyone Builds It, Everyone Dies.

Here’s what today’s AI “parents” do: Engineers assemble an enormous pile of highly specialized computer chips, a pile so large that powering them all takes as much [electricity](https://archive.is/o/blU6r/https://www.theatlantic.com/technology/archive/2023/08/ai-carbon-emissions-data-centers/675094/) as powering a small city. They design what’s called an “architecture,” which is—roughly speaking—billions of slots in computer memory holding billions of numbers hooked together by trillions of basic mathematical operations, in a simple repeating pattern. And they assemble a data set: trillions and trillions of words off the internet, whatever words they can scrape together. Then the AI begins.

The way training works—still speaking roughly—is that all those numbers filling the memory slots are combined using all those mathematical operations to produce *probabilities* about what word the AI will see next. Maybe the AI assigns 0.001 percent probability to the word *aardvark* and 0.02 percent probability to the word *jeep*, and so on and so forth; the AI produces one probability for every word. Those probabilities will be totally wrong, at the beginning. But during the process of training, the AI’s probabilities are compared against the actual words in the data set, and there’s an automated procedure for tuning the numbers inside the AI to make its probabilities better.

For example, suppose the data set starts with a fairy tale, and reads “Once upon a time …” Maybe the AI initially assigned only 0.01 percent probability to the word *upon* following *Once*, but the value won’t stay so low. There’s an automated mechanical process for going through every single number inside the AI—hundreds of billions or trillions of numbers—and asking: *If this number was a little higher, would the AI have assigned a greater probability to the word* upon*?* If so, the number gets tuned up, just a little. If not, the number gets tuned down. This process is called “gradient descent.”

Repeat that gradient-descent step a few trillion more times, on every piece of text you can scrape together, in a process that runs the computer continuously for the better part of a year, and you get a computer that can carry on a conversation.

Engineers don’t understand the numbers that come out of this process. That’s not the part that they create. They pick the architecture—a sort of container that will hold the AI. They assemble the data sets that are used to tune all the numbers in the architecture. And engineers understand the automated process that runs to every number and tunes it in response to the data, literally septillions of times. That’s it. That’s the part that humans do. That’s the part that humans can understand.

Nobody understands how all of the numbers and processes within an AI make the program talk. The numbers aren’t *hidden*, any more than the DNA of humans is hidden from someone who had their genome sequenced. You could, in principle, look at all of a human baby’s genes—strings of DNA that would say things like “CATTCA.” However, you probably wouldn’t bother to do that, because you’d know that just staring at the DNA letters wouldn’t tell you how the grown-up person would think or act.

The relationship that biologists have with DNA is pretty much the relationship that AI engineers have with the numbers inside an AI. Indeed, biologists know far more about how DNA turns into biochemistry and adult traits than engineers understand about how the numbers inside an AI yield cogent conversation and useful behavior. Biologists have been at the job for decades longer.

Similarly, nobody can look at the raw numbers in a given AI and ascertain how well that particular one will play chess; to figure that out, engineers can only run the AI and see what happens. Whatever gradient descent stumbled into, that’s what the big heap of numbers will do. The machine exhibiting that behavior is not some carefully crafted device whose each and every part we understand.

Make no mistake: There is plenty to understand about the process that grows an AI. It takes a giant bag of tricks to make an architecture actually work, but these tricks are sort of like the ones a nutritionist might use to ensure healthy brain development in a fetus during pregnancy. The precise tricks vary; people with enough experience picking the right ones can get paid literally millions of dollars a year, because it’s more of an art than a science, and companies can’t build AIs without their help.

But even people who know the tricks can’t use them to make AIs behave as they’d like. After Grok’s “MechaHitler” incident in July, Elon Musk, xAI’s founder, [wrote](https://archive.is/o/blU6r/https://x.com/elonmusk/status/1944132781745090819): “It is surprisingly hard to avoid both woke libtard cuck and mechahitler! Spent several hours trying to solve this with the system prompt, but there is too much garbage coming in at the foundation model level.” The company went on to struggle further with their chatbot. Sometimes the chatbot would [look up Musk’s beliefs before producing its replies](https://archive.is/o/blU6r/https://www.theatlantic.com/technology/archive/2025/07/new-grok-racism-elon-musk/683515/). The company reported that they investigated the issue and instructed it to stop.

This is not the behavior of people who are carefully creating traditional software. This is the behavior of people who are growing a whole new sort of creature and then taking whatever they get.

Engineers aren’t about to start understanding AIs, not anytime soon. In the mid-1950s, humanity embarked on a great project to understand intelligence well enough to produce it inside of a machine. That research progress stalled out in a series of “AI winters,” where money invested into AI research never paid off and funding repeatedly collapsed. Humanity never learned to understand intelligence; we never learned to build minds by hand.

The way humanity finally got to the level of ChatGPT was not by comprehending intelligence well enough to craft an intelligent mind. Instead, computers became powerful enough that AIs can be churned out by gradient descent, without any human needing to understand the cognitions that grow inside. The experts who have publicly pointed out the lack of understanding in the field include leaders of three top AI labs. In an interview with Nicholas Thompson, the CEO of *The Atlantic*, [Sam Altman](https://archive.is/o/blU6r/https://observer.com/2024/05/sam-altman-openai-gpt-ai-for-good-conference/) said last year, “We certainly have not solved interpretability,” referring to the ability to understand how AI makes its decisions. Earlier this year, Anthropic’s [Dario Amodei](https://archive.is/o/blU6r/https://www.darioamodei.com/post/the-urgency-of-interpretability) wrote in a blog post, “People outside the field are often surprised and alarmed to learn that we do not understand how our own AI creations work,” and Google DeepMind’s [Demis Hassabis](https://archive.is/o/blU6r/https://youtu.be/U7t02Q6zfdc?si=9PspHUCr1ocx4KjF&t=1031) said in a panel conversation, “We don't fully understand” the technology.

This all adds up to a worrying picture, where companies are racing to build a kind of AI that would be very dangerous. How could machines possibly do something other than what we ask? Why would they wind up with drives of their own that we didn’t put there on purpose? Because nobody puts much of anything into AIs on purpose in the first place. AIs aren’t like traditional software, where every piece was put there by some programmer who knows precisely what it means. All sorts of weird drives and behaviors get trained into them, for reasons nobody entirely understands. They can and do act in ways other than their creators intended, and we’re already seeing the warning signs.

---

*This essay has been adapted from the forthcoming book,* [If Anyone Builds It, Everyone Dies](https://archive.is/o/blU6r/https://bookshop.org/a/12476/9780316595643).

[![](https://cdn.theatlantic.com/thumbor/CaawoMnra9Ou33DOdFQUuy41y5w=/0x0:323x500/78x120/media/img/book_reviews/2025/09/15/41ekHgUQSaL._SL500_/original.jpg)](https://archive.is/o/blU6r/https://bookshop.org/a/12476/9780316595643)

[If Anyone Builds It, Everyone Dies: Why Superhuman AI Would Kill Us All](https://archive.is/o/blU6r/https://bookshop.org/a/12476/9780316595643) By Eliezer Yudkowsky and Nate Soares