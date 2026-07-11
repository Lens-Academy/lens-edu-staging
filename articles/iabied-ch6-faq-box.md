---
title: "Can developers just keep the AI in a box?"
source_url: https://ifanyonebuildsit.com/6/can-developers-just-keep-the-ai-in-a-box
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---
#### They won't.

Fifteen years ago, skeptics used to object that nobody would be dumb enough to give an AI much freedom of action. Surely anyone building an advanced machine intelligence would keep it in a physical and digital box, only allowing it to affect the world by interacting with highly trained (and suitably paranoid) gatekeepers.

At the time, we answered: It's not that hard to prevent an AI from having any effect on the world. For instance, you could bury the computers in a dozen meters of concrete and never let anyone near them.

Such an AI is safe, but useless. If you prevent it from affecting the world in any way, then sure, it won't affect the world in any way…but on the other hand, *it won't affect the world in any way*.

You can't use it to cure cancer, revolutionize engineering, or produce miraculous new technology. The builders of AI *want* it to radically affect the world. In principle, you can try to lock down the AI's channels of influence on the world. In practice, "invent this new technology for us" is an incredibly rich channel of influence all on its own.

The motivation behind building superintelligent AI is to achieve intellectual feats that no human is capable of. If you wanted to verify that a superintelligence's invention does exactly what it says on the tin and nothing else, you'd have about as much luck as if you were trying to understand a machine built by an advanced alien race — one with a powerful incentive to find a way to trick you.

That was the state of the debate fifteen years ago.

Nowadays, the whole idea that AI labs might try to "keep advanced AI in a box" seems rather quaint.

Labs are making [every](https://openai.com/index/introducing-chatgpt-search/) [effort](https://gemini.google/overview/deep-research/?hl=en) to hook their AIs to the internet. While AIs aren't given internet access while training, they're trained on computers that are connected to the internet, despite how humanity has a terrible track record of cybersecurity. While they're at it, they let AIs [run arbitrary code](https://www.oneusefulthing.org/i/155502334/executes-code-and-does-data-analysis). They sometimes try to limit what the code can do, but these limits are regularly broken. Smaller actors have a habit of hooking newly available AIs into [every imaginable tool](https://www.futuretools.io/) or [capability](https://openai.com/index/introducing-operator/) as soon as they possibly can.

Giving AIs power is useful in the short term. AIs that can read your emails and access the web can generate more profit. AI companies will give the AI access to all the data they possibly can; Microsoft and Apple are already pushing AI that sees your email, photos, and calendar and [bundling AI with their software and device offerings](https://blogs.microsoft.com/blog/2023/03/16/introducing-microsoft-365-copilot-your-copilot-for-work/). This creates far too many AI interactions for effective human monitoring. Absent a radical change of course, humanity will integrate AI deeply into the world economy because it makes people (lots of) money along the way.

The folks making AI are *aiming* for huge effects on the world. They work as hard as they can to produce AIs with enormous power to influence the world. If one company didn't, if they kept their AI so tightly constrained that it had no freedom to act, then control of the future would belong to a different AI grown by a more reckless actor.

#### It wouldn't work if they did.

In the quaint arguments of yesteryear, we would often point out that any channel through which the AI can affect the world is a channel that it can use to do things you don't like.

Suppose that the AI is only allowed to talk to one person — we'll call her "Alice." You're hoping that, through Alice, the AI will generate miraculous new technology. This then almost necessarily involves Alice performing many actions that Alice herself doesn't fully understand, helping the AI build things that no human could build on their own.

At that point, the AI essentially has been given arms and legs. It's just that we call those arms and legs "Alice."

People often misunderstand this argument as saying that a sufficiently smart AI could manipulate even the most paranoid gatekeeper into doing its bidding. A sufficiently smart AI likely *could* do that.[\*](#ftnt223) But our point is more general than that: An AI constrained so much that it cannot affect the world is safe but useless, and once you allow it to affect the world in order to make use of it, you lose the safety in the process.

There is no such thing as hands that can be wielded only for good purposes. In principle, we could imagine humanity one day building smarter-than-human AIs that *want* to produce good outcomes. Alignment seems like an option that could work in principle. Keeping the unaligned AI in a box while also somehow using it to produce good outcomes? Not so much.

That's how we used to answer, anyway — in the days when AI was the stuff of thought experiments, and the Pollyannas could get away with saying that nobody would ever be so foolish as to just directly hook their AI up to the internet.

[\*](#ftnt223_ref) I (Yudkowsky) once demonstrated this by betting someone their $20 against my $0 that, while I roleplayed as "AI" and they as "gatekeeper" in private chat, I could convince them to [let me out of the box](https://www.yudkowsky.net/singularity/aibox). I did. They paid. There was no clever trick to it; I didn't cheat and offer them $21 to concede to make my point. I just did it the hard way, and won.

#### Notes

[1] *Connected to the internet:* Most labs use online cloud computing services to train their AIs; for example, OpenAI has a [partnership](https://openai.com/index/openai-and-microsoft-extend-partnership/)with Microsoft Azure for this purpose.

[2] *terrible track record:* For a recent case study, see the stories around the compromised U.S. [telecommunications infrastructure](https://www.nytimes.com/2024/11/22/us/politics/chinese-hack-telecom-white-house.html).

[3] *regularly broken:* From the abstract of an [early 2024 paper](https://arxiv.org/pdf/2402.18649): "Our investigation exposes several security issues, not just within the LLM model itself but also in its integration with other components. We found that although the OpenAI GPT-4 has designed numerous safety constraints to improve its safety features, these safety constraints are still vulnerable to attackers. To further demonstrate the real-world threats of our discovered vulnerabilities, we construct an end-to-end attack where an adversary can illicitly acquire the user's chat history, all without the need to manipulate the user's input or gain direct access to OpenAI GPT-4."

Later that year, [another paper](https://arxiv.org/html/2309.02926v3) "uncovered a total of 20 vulnerabilities in 11 LLM-integrated frameworks, comprising 19 [remote code execution] vulnerabilities and 1 arbitrary file read/write vulnerability."

[4] *sees your email:* As reported by [CNN](https://www.cnn.com/2024/06/13/tech/apple-ai-data-openai-artificial-intelligence): "Apple Intelligence will have access to a wide range of your personal data, from your written communications to photos and videos you've taken to a record of your calendar events. There doesn't seem to be a way to prevent Apple Intelligence from accessing this information, short of not using its features…"
