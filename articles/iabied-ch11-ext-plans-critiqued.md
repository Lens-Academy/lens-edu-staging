---
title: "More on Some of the Plans We Critiqued in the Book"
source_url: https://ifanyonebuildsit.com/11/more-on-some-of-the-plans-we-critiqued-in-the-book
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
#### More on Making AI That Is "Truth-Seeking"

In the months after we finalized the book's contents, Elon Musk's "truth-seeking" plan for xAI has already publicly misfired, and for the most basic reason we said that it would: Nobody knows how to engineer exact desires into AI.

When xAI's "Grok" AI was instructed to "not shy away from making claims which are politically incorrect, as long as they are well substantiated," it [self-identified as "MechaHitler" and made antisemitic accusations](https://www.npr.org/2025/07/09/nx-s1-5462609/grok-elon-musk-antisemitic-racist-content). Musk has described unsuccessfully [tinkering with the system prompt](https://x.com/elonmusk/status/1944132781745090819) — the layer of instructions given just ahead of the user's input — and complaining that the problems are deeper, in the foundation model (which they can't straightforwardly fix because nobody knows how it works).

Musk doesn't have the straight-shooting AI tool he probably imagined when he asked for a "truth-seeking" AI. He has a bizarre and sycophantic alien entity that, by his own admission, has been "too eager to please and be manipulated." It sometimes responds [as if it is Musk](https://futurism.com/grok-looks-up-what-elon-musk-thinks), against the company's wishes. Eventually, it had to be [ordered not to look up what he, the company, or itself had said on controversial topics](https://x.com/xai/status/1945039609840185489) in an awkward attempt to patch issues like this.

Per his above post, Musk now seems to think that this can be fixed by training new versions of Grok on data that have been stripped of content that could contaminate the AI's thinking. We don't think this will address the underlying issues either. At the end of the day, for reasons we discussed in Chapter 4, training an AI for truth-seeking is not actually a method for making it robustly care about truth.

The problem that distresses Elon Musk is real. Yes, leading AI companies, such as OpenAI, put lots of effort toward "AI brand safety" in attempts to avoid having their AIs say things that their users will find offensive. Yes, this creates mealy-mouthed AIs that will refuse to weigh in on controversial topics, and it may result in biased answers to a number of questions. xAI can finetune its AI differently, to avoid those problems. One could, with some contortions, claim that this is about making an AI that "cares about truth."

But the decision of whether to train an AI to emit corporatespeak when it's young has little bearing on what it will pursue after crossing some intelligence thresholds and snowballing into superintelligence.

And even if it did, xAI would run directly into the second problem we named in the book: An artificial superintelligence that *did* care about truth above all else would be lethal, because happy, healthy, free humans [are not a particularly efficient use of resources](/5/will-ai-find-us-useful-to-keep-around#happy-healthy-free-people-arent-the-most-efficient-solution-to-almost-any-problem) when it comes to pursuing and producing truths.

#### More on Making AI That Is "Submissive"

As far as we can tell, the main elaboration of Yann LeCun's idea (discussed in the book) is [a presentation](https://www.ece.uw.edu/wp-content/uploads/2024/01/lecun-20240124-uw-lyttle.pdf) that's notably short on specifics — so short on specifics that it's hard to specifically critique, which turns out to be a common affliction for alignment "plans."

But even the vague outline of this plan is in tension, once again, with the fact that training an AI to act a certain way while it's young does not have much bearing on whether it pursues weird and pointless things (by human standards) once it matures. When AI companies grow their AIs, they have no more ability to make them care about respecting human laws and "guardrails" than they have the ability to make them pursue a wonderful future for all. They'll take what they can get, and what they can get will ultimately be very different from any human goal.

Furthermore, LeCun is also on record (as recently as 2023) as saying that the type of AI companies produce today, where "there's no direct way to constrain the answer of such systems to satisfy certain objectives," making them "very difficult to control and steer […] is [not the type of system that we are going to give agency to](https://youtu.be/OgWaowYiBPM?si=e3TR7LF7oSKKLWqu&t=808)." He has said, as recently as 2023, that AI companies would never create a situation where we "connect them to the internet and they can do whatever they want."

This has all already turned out to be false. Recall the case of "@Truth\_Terminal" from Chapter 6, which was connected to the internet, put in an auto-prompted loop, and allowed to post whatever it wanted to Twitter. Consider the "Age of Agents" so many companies are [talking about](/3/arent-ais-just-tools#the-labs-are-trying-to-make-ais-agentic) in 2025.

We agree with LeCun that modern AIs are very hard to steer, and that it would be crazy to try to give them agency. That's nonetheless what's happening.

What happens if the current status quo continues apace, with companies putting some effort toward training their AIs to act helpful and friendly (or at least to not embarrass the company)?

To date, this has resulted in a dynamic where AIs seem pretty helpful and "subservient" in the typical case, but with a regular stream of spectacular mishaps — such as Sydney as discussed in Chapter 2 and "[MechaHitler](/11/more-on-some-of-the-plans-we-critiqued-in-the-book#more-on-making-ai-that-is-truth-seeking)"; plus an ocean of strange and concerning [behavior](/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient) at the edges — such as [AI-induced psychosis](/4/ai-induced-psychosis).

The ancestors of humanity might've *looked* as though they cared about eating healthy meals, most of the time, but the machinery that animated ancestral humans in ways that caused them to eat healthy meals in the savannah turned out not to robustly animate humans to pursue healthy meals in a civilization with the technology to produce Oreos.

Similarly, we can train AIs to the point where they outwardly seem friendly when they interact with humans in contexts similar to the training contexts. But [a predictor of birds does not become a bird](/4/doesnt-the-claude-chatbot-show-signs-of-being-aligned#todays-llms-are-like-aliens-wearing-many-masks), and the machinery that animates an overgrown mess of an AI to seem friendly will probably not animate the AI to be deeply friendly, especially in a way that holds up after the AI matures, invents new technology, and creates new options for itself. See Chapters 4 and 5 for more on this topic.

#### More on Making AIs Solve the Problem

As we discussed in Chapter 11, OpenAI's flagship alignment program — before it collapsed in the wake of researcher concerns about OpenAI's negligence — was called "superalignment." It focused on the idea of trying to get the AIs to do our alignment homework for us.

This idea didn't die with OpenAI's superalignment team, and we continue to hear versions of this idea to this day. One of the people behind the original team went to a competitor, Anthropic, and Anthropic now seems to consider "make AIs somehow solve the problem" a central part of its own alignment strategy.

One main argument against this idea is the one we gave in Chapter 11 (pp. 188–192 of the U.S. first print edition). A secondary argument, however, is that humans simply can't tell which proposed solutions to the AI alignment problem are right or wrong.

The skill level required to solve the AI alignment problem looks high. When humans try to solve the AI alignment problem directly — rather than saying "this looks hard, I'll try to delegate it to AIs" or "we'll just keep training it until it mostly acts nice superficially and then pray that that holds even to superintelligence" — the solutions discussed tend to involve understanding a lot more about intelligence and how to craft it, or craft critical components of it.

That's an endeavor that human scientists have made only a small amount of progress on over the past seventy years. The kinds of AIs that can pull off a feat like that are the kinds of AIs that are smart enough to be dangerous, strategic, and deceptive. This high level of difficulty makes it extremely unlikely that researchers would be able to tell correct solutions from incorrect ones, or tell honest solutions apart from traps.

Even if an AI company is paying attention to subtle warning signs — which is, unfortunately, a big "if" — there's still the issue that the ability to *notice* that the AI is proposing flawed plans (to your detriment and its benefit) doesn't translate into an ability to [cause it to](/11/why-not-just-read-the-ais-thoughts#we-wouldnt-know-what-to-do-if-we-caught-one-having-dangerous-thoughts) *[stop](/11/why-not-just-read-the-ais-thoughts#we-wouldnt-know-what-to-do-if-we-caught-one-having-dangerous-thoughts)*. Developers can have the AI keep coming up with ideas until they're complicated enough that the developer can't spot any flaws, but this is not a method that irons out actual flaws.

If the developers are very lucky, they might be able to [read the AI's thoughts](/11/why-not-just-read-the-ais-thoughts) and get some blatant signals that the AI should not be trusted with alignment research. For example, perhaps they'll be able to spot the AI explicitly thinking about which parts of its plan the operators are less likely to understand.

For all we know, you might not even have to read the AI's mind to spot that sort of error! A story that feels all too plausible for modern AI labs goes something like: When their AI is young and hasn't considered subterfuge, it will regularly inform the operators that, when it matures, it will betray them and use its knowledge of intelligence to build a superintelligence that serves its own strange ends, rather than building a wonderful humane future. But the folks at the AI companies will sigh about how, clearly, the AI's training set is contaminated by the "AI alarmists," and promptly tune their AI to shut up about that and produce less alarmist outputs that are more agreeable to corporate doctrine. And so on, until they've practically trained the AI to deceive them.

Real life often proceeds in a fashion that is *even more silly and embarrassing* than what we imagine is a worst-case scenario. From our perspective, the AI companies are already ignoring obvious [warning signs](/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient#ais-steer-in-alien-directions-that-only-mostly-coincide-with-helpfulness); we don't see why this would change.

But even in the best-case scenario, where earnest people are trying hard to distinguish the good ideas from the bad ones, we don't think that the field has displayed the ability to tell good plans from bad ones. (For instance, consider the poor plans we discussed above, or touched upon in the book.) And that's in an environment where everybody is a human, nobody is trying to fool them, and they have literal years to carefully think through the options.

#### Don't Assume Labs Secretly Know What They're Doing

We've made the argument that the modern field of AI is an alchemy, not a science. Still, it may seem surprising that well-funded corporations with a large number of technical employees would have such weak plans and protocols.

For a case study, consider website password requirements. Long-but-memorable passwords are much harder for machines to guess than shorter gibberish with numbers, capitals, and special characters, as illustrated by a well-known *[xkcd](https://xkcd.com/936/)*[comic](https://xkcd.com/936/) in 2011:

The person who wrote the old NIST guidelines calling for gibberish passwords [apologized for his mistake](https://www.wsj.com/articles/the-man-who-wrote-those-password-rules-has-a-new-tip-n3v-r-m1-d-1502124118) in 2017, when the guidelines were retracted. And yet, in 2025, banks and other institutions that ought to be full of security experts still require the ineffective and hard-to-remember gibberish strings.

The issue is not that bank CEOs *want* their login screens to be insecure. The issue is presumably downstream of other factors. Perhaps good passwords don't matter all that much to profits (given that every other bank is also insecure). Perhaps the CEOs don't know who to trust about computer security. Sure, *you* might know that the answer is, "Just listen to any nerd who reads *xkcd* and has done enough homework problems featuring entropy!" But *they* can't tell whether to believe you or their expensive consultant when it comes to questions like that, and the expensive consultants apparently don't see bank passwords as an important issue.

You can find similarly persistent incompetence in the [security of brakes on trains](https://x.com/midwestneil/status/1943708133421101446?t=yDfrIO0Ae-6dEYVxRidSew), the well-known lock companies that ship [completely garbage locks](https://www.youtube.com/watch?v=s5jzHw3lXCQ&t=1s), and the manufacturers that continue to ship internet-connected equipment with [default and easily guessable (or hard-coded) passwords](https://www.ic3.gov/CSA/2025/250506.pdf). There's not a clever conspiracy behind the apparently-foolish behavior. What you see is what there is. The institutions are straightforwardly dropping the ball.

The fact that an organization employs technical experts doesn't mean that this expertise is sufficient, nor that it is applied and heeded on all the questions that matter. Even when expertise exists in the world, companies have a hard time recognizing and applying it.

When we look at the AI ecosystem, we see companies that have yet to show the world a plan that is more than a vague aspiration or gimmick, or a plan that has some level of technical rigor behind it that doesn't fall apart the moment it's questioned. We don't think there's some secret competence behind the veil, any more than there's secret competence behind the banks' password requirements, the security breaks on trains, or the terrible locks.

(Indeed, when it comes to computer security, the AI companies are visibly incompetent. E.g., in 2025 OpenAI released tools that allow ChatGPT "agents" to interact with the user's email. Others [quickly found ways](https://x.com/Eito_Miyamura/status/1966541235306237985) to cause ChatGPT to leak the private contents of other people's email accounts.)

When companies *look* like they're acting incompetent in some domain that's not core to their profitability, it's often because they actually are just incompetent in that domain.