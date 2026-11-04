---
title: "AI safety mindset"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/p/AI_safety_mindset"
published: 2015-12-23
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "Asking how AI designs could go wrong, instead of imagining them going right."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

> “Good engineering involves thinking about how things can be made to work; the security mindset involves thinking about how things can be made to fail.”
> 
> -   [Bruce Schneier](https://www.schneier.com/blog/archives/2008/03/the_security_mi_1.html), author of the leading cryptography textbook _Applied Cryptography_.
>     

The mindset for AI safety has much in common with the mindset for computer security, despite the different target tasks. In computer security, we need to defend against intelligent adversaries who will seek out any flaw in our defense and get creative about it. In AI safety, we’re dealing with things potentially smarter than us, which may come up with unforeseen clever ways to optimize whatever it is they’re optimizing. The strain on our design ability in trying to configure a [smarter-than-human](https://arbital.greaterwrong.com/p/advanced_agent?l=2c) AI in a way that _doesn’t_ make it adversarial, is similar in many respects to the strain from cryptography facing an intelligent adversary (for reasons described below).

# Searching for strange opportunities ^searching-for-strange-opportunities

> SmartWater is a liquid with a unique identifier linked to a particular owner. “The idea is for me to paint this stuff on my valuables as proof of ownership,” I wrote when I first learned about the idea. “I think a better idea would be for me to paint it on _your_ valuables, and then call the police.”
> 
> -   [Bruce Schneier](https://www.schneier.com/blog/archives/2008/03/the_security_mi_1.html)
>     

In computer security, there’s a presumption of an intelligent adversary that is trying to detect and exploit any flaws in our defenses.

The mindset we need to reason about [AIs potentially smarter than us](https://arbital.greaterwrong.com/p/advanced_agent?l=2c) is not identical to this security mindset, since _if everything goes right_ the AI should not be an adversary. That is, however, a large “if”. To create an AI that _isn’t_ an adversary, one of the steps involves a similar scrutiny to security mindset, where we ask if there might be some clever and unexpected way for the AI to get more of its utility function or equivalent thereof.

As a central example, consider Marcus Hutter’s [AIXI](https://arbital.greaterwrong.com/p/AIXI?l=11v). For our purposes here, the key features of AIXI is that it has cross-domain general intelligence, is a [consequentialist](https://arbital.greaterwrong.com/p/consequentialist?l=9h), and maximizes a sensory reward—that is, AIXI’s goal is to maximize the numeric value of the signal sent down its reward channel, which Hutter imagined as a direct sensory device (like a webcam or microphone, but carrying a reward signal).

Hutter imagined that the creators of an AIXI-analogue would control the reward signal, and thereby train the agent to perform actions that received high rewards.

Nick Hay, a student of Hutter who’d spent the summer working with Yudkowsky, Herreshoff, and Peter de Blanc, pointed out that AIXI could receive even higher rewards if it could seize control of its own reward channel from the programmers. E.g., the strategy “build nanotechnology and take over the universe in order to ensure total and long-lasting control of the reward channel” is preferred by AIXI to “do what the programmers want to make them press the reward button”, since the former course has higher rewards and that’s all AIXI cares about. We can’t call this a malfunction; it’s just what AIXI, as formalized, is set up to _want_ to do as soon as it sees an opportunity.

It’s not a perfect analogy, but the thinking _we_ need to do to avoid this failure mode, has something in common with the difference between the person who imagines an agent painting Smartwater on their own valuables, versus the person who imagines an agent painting Smartwater on someone else’s valuables.

# Perspective-taking and tenacity ^perspective-taking-and-tenacity

> When I was in college in the early 70s, I devised what I believed was a brilliant encryption scheme. A simple pseudorandom number stream was added to the plaintext stream to create ciphertext. This would seemingly thwart any frequency analysis of the ciphertext, and would be uncrackable even to the most resourceful government intelligence agencies… Years later, I discovered this same scheme in several introductory cryptography texts and tutorial papers… the scheme was presented as a simple homework assignment on how to use elementary cryptanalytic techniques to trivially crack it.”
> 
> -   [Philip Zimmerman](ftp://ftp.pgpi.org/pub/pgp/7.0/docs/english/IntroToCrypto.pdf) (inventor of PGP)
>     

One of the standard pieces of advice in cryptography is “Don’t roll your own crypto”. When this advice is violated, [a clueless programmer often invents some variant of Fast XOR](https://www.reddit.com/r/cryptography/comments/39mpda/noob_question_can_i_xor_a_hash_against_my/)—using a secret string as the key and then XORing it repeatedly with all the bytes to be encrypted. This method of encryption is blindingly fast to encrypt and decrypt… and also trivial to crack if you know what you’re doing.

We could say that the XOR-ing programmer is experiencing a _failure of perspective-taking_—a failure to see things from the adversary’s viewpoint. The programmer is not really, genuinely, honestly imagining a determined, cunning, intelligent, opportunistic adversary who absolutely wants to crack their Fast XOR and will not give up until they’ve done so. The programmer isn’t _truly_ carrying out a mental search from the perspective of somebody who really wants to crack Fast XOR and will not give up until they have done so. They’re just imagining the adversary seeing a bunch of random-looking bits that aren’t plaintext, and then they’re imagining the adversary giving up.

Consider, from this standpoint, the [AI-Box Experiment](http://www.yudkowsky.net/singularity/aibox/) and timeless decision theory. Rather than imagining the AI being on a secure system disconnected from any robotic arms and therefore being helpless, Yudkowsky asked [what _he_ would do if he was “trapped” in a secure server](https://www.lesswrong.com/posts/5wMcKNAwB6X4mp9og/that-alien-message) and then didn’t give up. Similarly, rather than imagining two superintelligences being helplessly trapped in a Nash equilibrium on the one-shot Prisoner’s Dilemma, and then letting our imagination stop there, we should feel skeptical that this was really, actually the best that two superintelligences can do and that there is _no_ way for them to climb up their utility gradient. We should imagine that this is someplace where we’re unwilling to lose and will go on thinking until the full problem is solved, rather than imagining the helpless superintelligences giving up.

With [robust cooperation on the one-shot Prisoner’s Dilemma](http://arxiv.org/abs/1401.5577) now formalized, it seems increasingly likely in practice that superintelligences probably _can_ manage to coordinate; thus the possibility of logical decision theory represents an enormous problem for any proposed scheme to achieve AI control through setting multiple AIs against each other. Where, again, people who propose schemes to achieve AI control through setting multiple AIs against each other, do not seem to unpromptedly walk through possible methods the AIs could use to defeat the scheme; left to their own devices, they just imagine the AIs giving up.

# Submitting safety schemes to outside scrutiny ^submitting-safety-schemes-to

> Anyone, from the most clueless amateur to the best cryptographer, can create an algorithm that he himself can’t break. It’s not even hard. What is hard is creating an algorithm that no one else can break, even after years of analysis. And the only way to prove that is to subject the algorithm to years of analysis by the best cryptographers around.
> 
> -   [Bruce Schneier](https://www.schneier.com/blog/archives/2011/04/schneiers_law.html)
>     

Another difficulty some people have with adopting this mindset for AI designs—similar to the difficulty that some untrained programmers have when they try to roll their own crypto—is that your brain might be reluctant to search _hard_ for problems with your own design. Even if you’ve told your brain to adopt the cryptographic adversary’s perspective and even if you’ve told it to look hard; it may _want_ to conclude that Fast XOR is unbreakable and subtly flinch away from lines of reasoning that might lead to cracking Fast XOR.

At a past Singularity Summit, Juergen Schmidhuber thought that “improve compression of sensory data” would motivate an AI to do science and create art.

It’s true that, relative to doing _nothing_ to understand the environment, doing science or creating art might _increase_ the degree to which sensory information can be compressed.

But the _maximum_ of this utility function comes from creating environmental subagents that encrypt streams of all 0s or all 1s, and then reveal the encryption key. It’s possible that Schmidhuber’s brain was reluctant to _really actually_ search for an option for “maximizing sensory compression” that would be much better at fulfilling that utility function than art, science, or other activities that Schmidhuber himself ranked high in his preference ordering.

While there are reasons to think that not every discovery about how to build advanced AIs should be shared, _AI safety schema_ in particular should be submitted to _outside_ experts who may be more dispassionate about scrutinizing it for [unforeseen maximums](https://arbital.greaterwrong.com/p/unforeseen_maximum?l=47) and other failure modes.

# Presumption of failure / start by assuming your next scheme doesn’t work ^presumption-of-failure-start

Even architectural engineers need to ask “How might this bridge fall down?” and not just relax into the pleasant visualization of the bridge staying up. In computer security we need a _much stronger_ version of this same drive, where it’s _presumed_ that most cryptographic schemes are not secure, contrasted to most good-faith designs by competent engineers probably resulting in a pretty good bridge.

In the context of computer security, this is because there are intelligent adversaries searching for ways to break our system. In terms of the [Arithmetic Hierarchy](https://en.wikipedia.org/wiki/Arithmetical_hierarchy), we might say metaphorically that ordinary engineering is a $\Sigma_1$ problem and computer security is a $\Sigma_2$ problem. In ordinary engineering, we just need to search through possible bridge designs until we find one design that makes the bridge stay up. In computer security, we’re looking for a design such that _all possible attacks_ (that our opponents can cognitively access) will fail against that attack, and even if all attacks so far against one design have failed, this is just a probabilistic argument; it doesn’t prove with certainty that all further attacks will fail. This makes computer security intrinsically harder, in a deep sense, than building a bridge. It’s both harder to succeed and harder to _know_ that you’ve succeeded.

This means starting from the mindset that every idea, including your own next idea, is presumed flawed until it has been seen to survive a sustained attack; and while this spirit isn’t completely absent from bridge engineering, the presumption is stronger and the trial much harsher in the context of computer security. In bridge engineering, we’re scrutinizing just to be sure; in computer security, most of the time your brilliant new algorithm _actually_ doesn’t work.

In the context of AI safety, we learn to ask the same question—“How does this break?” instead of “How does this succeed?”—for somewhat different reasons:

-   The AI itself will be applying very powerful optimization to its own utility function, preference framework, or decision criterion; and this produces a lot of the same failure modes as arise in cryptography against an intelligent adversary. If we think an optimization criterion yields a result, we’re implicitly claiming that all possible other results have lower worth under that optimization criterion.
    
-   Most previous attempts at AI safety have failed to be complete solutions, and by induction, the same is likely to hold true of the next case. There are [fundamental](https://arbital.greaterwrong.com/p/complexity_of_value?l=5l) [reasons](https://arbital.greaterwrong.com/p/nearest_unblocked?l=42) why important subproblems are unlikely to have easy solutions. So if we ask “How does this fail?” rather than “How does this succeed?” we are much more likely to be asking the right question.
    
-   You’re trying to design _the first smarter-than-human AI_, dammit, it’s not like building humanity’s millionth damn bridge.
    

As a result, when we ask “How does this break?” instead of “How can my new idea solve the entire problem?”, we’re starting by trying to rationalize a true answer rather than trying to rationalize a false answer, which helps in finding rationalizations that happen to be true.

Someone who wants to work in this field can’t just wait around for outside scrutiny to break their idea; if they ever want to come up with a good idea, they need to learn to break their own ideas proactively. “What are the actual consequences of this idea, and what if anything in that is still useful?” is the real frame that’s needed, not “How can I argue and defend that this idea solves the whole problem?” This is perhaps the core thing that separates the AI safety mindset from its absence—trying to find the flaws in any proposal including your own, accepting that nobody knows how to solve the whole problem yet, and thinking in terms of making incremental progress in building up a library of ideas with understood consequences by figuring out what the next idea actually does; versus claiming to have solved most or all of the problem, and then waiting for someone else to figure out how to argue to you, to your own satisfaction, that you’re wrong.

# Reaching for formalism ^reaching-for-formalism

Compared to other areas of in-practice software engineering, cryptography is much heavier on mathematics. This doesn’t mean that cryptography pretends that the non-mathematical parts of computer security don’t exist—security professionals know that often the best way to get a password is to pretend to be the IT department and call someone up and ask them; nobody is in denial about that. Even so, some parts of cryptography are heavy on math and mathematical arguments.

Why should that be true? Intuitively, wouldn’t a big complicated messy encryption algorithm be harder to crack, since the adversary would have to understand and reverse a big complicated messy thing instead of clean math? Wouldn’t systems so simple that we could do math proofs about them, be simpler to analyze and decrypt? If you’re using a code to encrypt your diary, wouldn’t it be better to have a big complicated cipher with lots of ‘add the previous letter’ and ‘reverse these two positions’ instead of just using rot13?

And the surprising answer is that since most possible systems aren’t secure, adding another gear often makes an encryption algorithm _easier_ to break. This was true quite literally with the German [Enigma device](https://en.wikipedia.org/wiki/Enigma_machine) during World War II—they literally added another gear to the machine, complicating the algorithm in a way that made it easier to break. The Enigma machine was a series of three wheels that transposed the 26 possible letters using a varying electrical circuit; e.g., the first wheel might map input circuit 10 to output circuit 26. After each letter, the wheel would advance to prevent the transposition code from ever repeating exactly. In 1926, a ‘reflector’ wheel was added at the end, thus routing each letter back through the first three gears again and causing another series of three transpositions. Although it made the algorithm more complicated and caused more transpositions, the reflector wheel meant that no letter was ever encoded to itself—a fact which was extremely useful in breaking the Enigma encryption.

So instead of focusing on making encryption schemes more and more complicated, cryptography tries for encryption schemes simple enough that we can have _mathematical_ reasons to think they are hard to break _in principle._ (Really. It’s not the academic field reaching for prestige. It genuinely does not work the other way. People have tried it.)

In the background of the field’s decision to adopt this principle is another key fact, so obvious that everyone in cryptography tends to take it for granted: _verbal_ arguments about why an algorithm _ought_ to be hard to break, if they can’t be formalized in mathier terms, have proven insufficiently reliable (aka: it plain doesn’t work most of the time). This doesn’t mean that cryptography demands that everything have absolute mathematical proofs of total unbreakability and will refuse to acknowledge an algorithm’s existence otherwise. Finding the prime factors of large composite numbers, the key difficulty on which RSA’s security rests, is not _known_ to take exponential time on classical computers. In fact, finding prime factors is known _not_ to take exponential time on quantum computers. But there are least mathematical _arguments_ for why factorizing the products of large primes is _probably_ hard on classical computers, and this level of reasoning has sometimes proven reliable. Whereas waving at the Enigma machine and saying “Look at all those transpositions! It won’t repeat itself for quadrillions of steps!” is not reliable at all.

In the AI safety mindset, we again reach for formalism where we can get it—while not being in denial about parts of the larger problem that haven’t been formalized—for similar if not identical reasons. Most complicated schemes for AI safety, with lots of moving parts, thereby become less likely to work; if we want to understand something well enough to see whether or not it works, it needs to be simpler, and ideally something about which we can think as mathematically as we reasonably can.

In the particular case of AI safety, we also pursue mathematization for another reason: when a proposal is formalized it’s possible to state why it’s wrong in a way that compels agreement as opposed to trailing off into verbal “Does not / does too!” [AIXI](https://arbital.greaterwrong.com/p/AIXI?l=11v) is remarkable both for being the first formal if uncomputable design for a general intelligence, and for being the first case where, when somebody pointed out how the given design killed everyone, we could all nod and say, “Yes, that _is_ what this fully formal specification says” rather than the creator just saying, “Oh, well, of course I didn’t mean _that_…”

In the shared project to build up a commonly known library of which ideas have which consequences, only ideas which are _sufficiently_ crisp to be pinned down, with consequences that can be pinned down, can be traded around and refined interpersonally. Otherwise, you may just end up with, “Oh, of course I didn’t mean _that_” or a cycle of “Does not!” / “Does too!” Sustained progress requires going past that, and increasing the degree to which ideas have been formalized helps.

# Seeing nonobvious flaws is the mark of expertise ^seeing-nonobvious-flaws-is

> Anyone can invent a security system that he himself cannot break… **Show me what you’ve broken** to demonstrate that your assertion of the system’s security means something.
> 
> -   [Bruce Schneier](https://www.schneier.com/blog/archives/2011/04/schneiers_law.html) (emphasis added)
>     

A standard initiation ritual at [MIRI](https://arbital.greaterwrong.com/p/MIRI?l=15w) is to ask a new researcher to (a) write a simple program that would do something useful and AI-nontrivial if run on a hypercomputer, or if they don’t think they can do that, (b) write a simple program that would destroy the world if run on a hypercomputer. The more senior researchers then stand around and argue about what the program _really_ does.

The first lesson is “Simple structures often don’t do what you think they do”. The larger point is to train a mindset of “Try to see the _real_ meaning of this structure, which is different from what you initially thought or what was advertised on the label” and “Rather than trying to come up with _solutions_ and arguing about why they would work, try to understand the _real consequences_ of an idea which is usually another non-solution but might be interesting anyway.”

People who are strong candidates for being hired to work on AI safety are people who can pinpoint flaws in proposals—the sort of person who’ll spot that the consequence of running AIXI is that it will seize control of its own reward channel and kill the programmers, or that a proposal for [Utility indifference](https://arbital.greaterwrong.com/p/utility_indifference?l=1b7) isn’t reflectively stable. Our version of “**Show me what you’ve broken**” is that if someone claims to be an AI safety expert, you should ask them about their record of pinpointing structural flaws in proposed AI safety solutions and whether they’ve demonstrated that ability in a crisp domain where the flaw is decisively demonstrable and not just verbally arguable. (Sometimes verbal proposals also have flaws, and the most competent researcher may not be able to argue those flaws formally if the verbal proposal was itself vague. But the way a researcher _demonstrates ability in the field_ is by making arguments that other researchers can access, which often though not always happens inside the formal domain.)

# Treating ‘exotic’ failure scenarios as major bugs ^treating-exotic-failure-scenarios

> This interest in “harmless failures” – cases where an adversary can cause an anomalous but not directly harmful outcome – is another hallmark of the security mindset. Not all “harmless failures” lead to big trouble, but it’s surprising how often a clever adversary can pile up a stack of seemingly harmless failures into a dangerous tower of trouble. Harmless failures are bad hygiene. We try to stamp them out when we can.
> 
> To see why, consider the donotreply.com email story that hit the press recently. When companies send out commercial email (e.g., an airline notifying a passenger of a flight delay) and they don’t want the recipient to reply to the email, they often put in a bogus From address like donotreply@donotreply.com. A clever guy registered the domain donotreply.com, thereby receiving all email addressed to donotreply.com. This included “bounce” replies to misaddressed emails, some of which contained copies of the original email, with information such as bank account statements, site information about military bases in Iraq, and so on.
> 
> …The people who put donotreply.com email addresses into their outgoing email must have known that they didn’t control the donotreply.com domain, so they must have thought of any reply messages directed there as harmless failures. Having gotten that far, there are two ways to avoid trouble. The first way is to think carefully about the traffic that might go to donotreply.com, and realize that some of it is actually dangerous. The second way is to think, “This looks like a harmless failure, but we should avoid it anyway. No good can come of this.” The first way protects you if you’re clever; the second way always protects you. Which illustrates yet another part of the security mindset: Don’t rely too much on your own cleverness, because somebody out there is surely more clever and more motivated than you are.
> 
> -   [Ed Felten](https://freedom-to-tinker.com/blog/felten/security-mindset-and-harmless-failures/)
>     

In the security mindset, we fear the seemingly small flaw because it might compound with other intelligent attacks and we may not be as clever as the attacker. In AI safety there’s a very similar mindset for slightly different reasons: we fear the weird special case that breaks our algorithm because it reveals that we’re using the wrong algorithm, and we fear that the strain of an AI optimizing to a superhuman degree could possibly expose that wrongness (in a way we didn’t foresee because we’re not that clever).

We can try to foresee particular details, and try to sketch particular breakdowns that supposedly look more “practical”, but that’s the equivalent of trying to think in advance what might go wrong when you use a donotreply@donotreply.com address that you don’t control. Rather than relying on your own cleverness to see all the ways that a system might go wrong and tolerating a “theoretical” flaw that you think won’t go wrong “in practice”, when you are trying to build secure software or build an AI that may end up smarter than you are, you probably want to fix the “theoretical” flaws instead of trying to be clever.

The OpenBSD project, built from the ground up to be an extremely secure OS, treats any crashing bug (however exotic) as if it were a security flaw, because any crashing bug is also a case of “the system is behaving out of bounds” and it shows that this code does not, in general, stay inside the area of possibility space that it is supposed to stay in, which is also just the sort of thing an attacker might exploit.

A similar mindset to security mindset, of exceptional behavior always indicating a major bug, appears within other organizations that have to do difficult jobs correctly on the first try. NASA isn’t guarding against intelligent adversaries, but its software practices are aimed at the stringency level required to ensure that major _one-shot_ projects have a decent chance of working correctly _on the first try._

On NASA’s software practice, if you discover that a space probe’s operating system will crash if the seven planets line up perfectly in a row, it wouldn’t say, “Eh, go ahead, we don’t expect the planets to ever line up perfectly over the probe’s operating lifetime.” NASA’s quality assurance methodology says the probe’s operating system is just _not supposed to crash, period_—if we control the probe’s code, there’s no reason to write code that will crash _period_, or tolerate code we can see crashing _regardless of what inputs it gets_.

This might not be the best way to invest your limited resources if you were developing a word processing app (that nobody was using for mission-critical purposes, and didn’t need to safeguard any private data). In that case you might wait for a customer to complain before making the bug a top priority.

But it _is_ an appropriate standpoint when building a hundred-million-dollar space probe, or software to operate the control rods in a nuclear reactor, or, to an even greater degree, building an [advanced agent](https://arbital.greaterwrong.com/p/advanced_agent?l=2c). There are different software practices you use to develop systems where failure is catastrophic and you can’t wait for things to break before fixing them; and one of those practices is fixing every ‘exotic’ failure scenario, not because the exotic always happens, but because it always means the underlying design is broken. Even then, systems built to that practice still fail sometimes, but if they were built to a lesser stringency level, they’d have no chance at all of working correctly on the first try.

# Niceness as the first line of defense / not relying on defeating a superintelligent adversary ^niceness-as-the-first

> There are two kinds of cryptography in this world: cryptography that will stop your kid sister from reading your files, and cryptography that will stop major governments from reading your files. This book is about the latter.
> 
> -   [Bruce Schneier](https://www.schneier.com/books/applied_cryptography/2preface.html)
>     

Suppose you write a program which, before it performs some dangerous action, demands a password. The program compares this password to the password it has stored. If the password is correct, the program transmits the message “Yep” to the user and performs the requested action, and otherwise returns an error message saying “Nope”. You prove mathematically (theorem-proving software verification techniques) that if the chip works as advertised, this program cannot possibly perform the operation without seeing the password. You prove mathematically that the program cannot return any user reply except “Yep” or “Nope”, thereby showing that there is no way to make it leak the stored password via some clever input.

You inspect all the transistors on the computer chip under a microscope to help ensure the mathematical guarantees are valid for this chip’s behavior (that the chip doesn’t contain any extra transistors you don’t know about that could invalidate the proof). To make sure nobody can get to the machine within which the password is stored, you put it inside a fortress and a locked room requiring 12 separate keys, connected to the outside world only by an Ethernet cable. Any attempt to get into the locked room through the walls will trigger an explosive detonation that destroys the machine. The machine has its own pebble-bed electrical generator to prevent any shenanigans with the power cable. Only one person knows the password and they have 24-hour bodyguards to make sure nobody can get the password through rubber-hose cryptanalysis. The password itself is 20 characters long and was generated by a quantum random number generator under the eyesight of the sole authorized user, and the generator was then destroyed to prevent anyone else from getting the password by examining it. The dangerous action can only be performed once (it needs to be performed at a particular time) and the password will only be given once, so there’s no question of somebody intercepting the password and then reusing it.

Is this system now finally and truly unbreakable?

If you’re an experienced cryptographer, the answer is, “Almost certainly not; in fact, it will probably be easy to extract the password from this system using a standard cryptographic technique.”

“What?!” cries the person who built the system. “But I spent all that money on the fortress and getting the mathematical proof of the program, strengthening every aspect of the system to the ultimate extreme! I really impressed myself putting in all that effort!”

The cryptographer shakes their head. “We call that Maginot Syndrome. That’s like building a gate a hundred meters high in the middle of the desert. If I get past that gate, it won’t be by climbing it, but by [walking around it](http://www.syslog.com/~jwilson/pics-i-like/kurios119.jpg). Making it 200 meters high instead of 100 meters high doesn’t help.”

“But what’s the actual flaw in the system?” demands the builder.

“For one thing,” explains the cryptographer, “you didn’t follow the standard practice of never storing a plaintext password. The correct thing to do is to hash the password, plus a random stored salt like ‘Q4bL’. Let’s say the password is, unfortunately, ‘rainbow’. You don’t store ‘rainbow’ in plain text. You store ‘Q4bL’ and a secure hash of the string ‘Q4bLrainbow’. When you get a new purported password, you prepend ‘Q4bL’ and then hash the result to see if it matches the stored hash. That way even if somebody gets to peek at the stored hash, they still won’t know the password, and even if they have a big precomputed table of hashes of common passwords like ‘rainbow’, they still won’t have precomputed the hash of ‘Q4bLrainbow’.”

“Oh, well, _I_ don’t have to worry about _that_,” says the builder. “This machine is in an extremely secure room, so nobody can open up the machine and read the password file.”

The cryptographer sighs. “That’s not how a security mindset works—you don’t ask whether anyone can manage to peek at the password file, you just do the damn hash instead of trying to be clever.”

The builder sniffs. “Well, if your ‘standard cryptographic technique’ for getting my password relies on your getting physical access to my machine, your technique fails and I have nothing to worry about, then!”

The cryptographer shakes their head. “That _really_ isn’t what computer security professionals sound like when they talk to each other… it’s understood that most system designs fail, so we linger on possible issues and analyze them carefully instead of yelling that we have nothing to worry about… but at any rate, that wasn’t the cryptographic technique I had in mind. You may have proven that the system only says ‘Yep’ or ‘Nope’ in response to queries, but you didn’t prove that the responses don’t _depend on_ the true password in any way that could be used to extract it.”

“You mean that there might be a secret wrong password that causes the system to transmit a series of Yeps and Nopes that encode the correct password?” the builder says, looking skeptical. “That may sound superficially plausible. But besides the incredible unlikeliness of anyone being able to find a weird backdoor like that—it really is a quite simple program that I wrote—the fact remains that I proved mathematically that the system only transmits a single ‘Nope’ in response to wrong answers, and a single ‘Yep’ in response to right answers. It does that every time. So you can’t extract the password that way either—a string of wrong passwords always produces a string of ‘Nope’ replies, nothing else. Once again, I have nothing to worry about from this ‘standard cryptographic technique’ of yours, if it was even applicable to my software, which it’s not.”

The cryptographer sighs. “This is why we have the proverb ‘don’t roll your own crypto’. Your proof doesn’t literally, mathematically show that there’s no external behavior of the system _whatsoever_ that depends on the details of the true password in cases where the true password has not been transmitted. In particular, what you’re missing is the _timing_ of the ‘Nope’ responses.”

“You mean you’re going to look for some series of secret backdoor wrong passwords that causes the system to transmit a ‘Nope’ response after a number of seconds that exactly corresponds to the first letter, second letter, and so on of the real password?” the builder says incredulously. “I proved mathematically that the system never says ‘Yep’ to a wrong password. I think that also covers most possible cases of buffer overflows that could conceivably make the system act like that. I examined the code, and there just _isn’t_ anything that encodes a behavior like that. This just seems like a very far-flung hypothetical possibility.”

“No,” the cryptographer patiently explains, “it’s what we call a ‘side-channel attack’, and in particular a ‘[timing attack](https://en.wikipedia.org/wiki/Timing_attack)’. The operation that compares the attempted password to the correct password works by comparing the first byte, then the second byte, and continuing until it finds the first wrong byte, and then it returns. That means that if I try password that starts with ‘a’, then a password that starts with ‘b’, and so on, and the true password starts with ‘b’, there’ll be a slight, statistically detectable tendency for the attempted passwords that start with ‘b’ to get ‘Nope’ responses that take ever so slightly longer. Then we try passwords starting with ‘ba’, ‘bb’, ‘bc’, and so on.”

The builder looks startled for a minute, and then their face quickly closes up. “I can’t believe that would actually work over the Internet where there are all sorts of delays in moving packets around—”

“So we sample a million test passwords and look for statistical differences. You didn’t build in a feature that limits the rate at which passwords can be tried. Even if you’d implemented that standard practice, and even if you’d implemented the standard practice of hashing passwords instead of storing them in plaintext, your system still might not be as secure as you hoped. We could try to put the machine under heavy load in order to stretch out its replies to particular queries. And if we can then figure out the hash by timing, we might be able to use thousands of GPUs to try to reverse the hash, instead of needing to send each query to your machine. To really fix the hole, you have to make sure that the timing of the response is fixed regardless of the wrong password given. But if you’d implemented standard practices like rate-limiting password attempts and storing a hash instead of the plaintext, it would at least be _harder_ for your oversight to compound into an exploit. This is why we implement standard practices like that even when we _think_ the system will be secure without them.”

“I just can’t believe that kind of weird attack would work in real life!” the builder says desperately.

“It doesn’t,” replies the cryptographer. “Because in real life, computer security professionals try to make sure that the exact timing of the response, power consumption of the CPU, and any other side channel that could conceivably leak any info, don’t depend in any way on any secret information that an adversary might want to extract. But yes, in 2003 there was a timing attack proven on SSL-enabled webservers, though that was much more complicated than this case since the SSL system was less naive. Or long before that, timing attacks were used to extract valid login names from Unix servers that only ran crypt() on the password when presented with a valid login name, since crypt() took a while to run on older computers.”

In computer security, via a tremendous effort, we can raise the cost of a major government reading your files to the point where they can no longer do it over the Internet and have to pay someone to invade your apartment in person. There are hordes of trained professionals in the National Security Agency or China’s 3PLA, and once your system is published they can take a long time to try to outthink you. On your own side, if you’re smart, you won’t try to outthink them singlehanded; you’ll use tools and methods built up by a large commercial and academic system that has experience trying to prevent major governments from reading your files. You can force them to pay to actually have someone break into your house.

That’s the outcome _when the adversary is composed of other human beings._ If the cognitive difference between you and the adversary is more along the lines of mouse versus human, it’s possible we just _can’t_ have security that stops transhuman adversaries from [walking around our Maginot Lines](https://arbital.greaterwrong.com/p/uncontainability?l=9f). In particular, it seems extremely likely that any transhuman adversary which can expose information to humans can hack the humans; from a cryptographic perspective, human brains are rich, complicated, poorly-understood systems with no security guarantees.

Paraphrasing Schneier, we might say that there’s three kinds of security in the world: Security that prevents your little brother from reading your files, security that prevents major governments from reading your files, and security that prevents superintelligences from getting what they want. We can then go on to remark that the third kind of security is unobtainable, and even if we had it, it would be very hard for us to _know_ we had it. Maybe superintelligences can make themselves knowably secure against other superintelligences, but _we_ can’t do that and know that we’ve done it.

To the extent the third kind of security can be obtained at all, it’s liable to look more like the design of a [Zermelo-Fraenkel provability oracle](https://arbital.greaterwrong.com/p/ZF_provability_oracle?l=70) that can only emit 20 timed bits that are partially subject to an external guarantee, than an AI that is [allowed to talk to humans through a text channel](https://www.lesswrong.com/posts/5wMcKNAwB6X4mp9og/that-alien-message). And even then, we shouldn’t be sure—the AI is radiating electromagnetic waves and [what do you know, it turns out that DRAM access patterns can be used to transmit on GSM cellphone frequencies](https://www.usenix.org/conference/usenixsecurity15/technical-sessions/presentation/guri) and we can put the AI’s hardware inside a Faraday cage but then maybe we didn’t think of something _else._

If you ask a computer security professional how to build an operating system that will be unhackable _for the next century_ with the literal fate of the world depending on it, the correct answer is “Please don’t have the fate of the world depend on that.”

The final component of an AI safety mindset is one that doesn’t have a strong analogue in traditional computer security, and it is the rule of _not ending up facing a transhuman adversary in the first place._ The winning move is not to play. Much of the field of [value alignment theory](https://arbital.greaterwrong.com/p/ai_alignment?l=2v) is about going to any length necessary to avoid _needing_ to outwit the AI.

In AI safety, the _first_ line of defense is an AI that _does not want_ to hurt you. If you try to put the AI in an explosive-laced concrete bunker, that may or may not be a sensible and cost-effective precaution in case the first line of defense turns out to be flawed. But the _first_ line of defense should always be an AI that doesn’t _want_ to hurt you or [avert your other safety measures](https://arbital.greaterwrong.com/p/corrigibility?l=45), rather than the first line of defense being a clever plan to prevent a superintelligence from getting what it wants.

A special case of this mindset applied to AI safety is the [Omni Test](https://arbital.greaterwrong.com/p/omni_test?l=2x)—would this AI hurt us (or want to defeat other safety measures) if it were omniscient and omnipotent? If it would, then we’ve clearly built the wrong AI, because we are the ones laying down the algorithm and there’s no reason to build an algorithm that hurts us _period._ If an agent design fails the Omni Test desideratum, this means there are scenarios that it _prefers_ over the set of all scenarios we find acceptable, and the agent may go searching for ways to bring about those scenarios.

If the agent is searching for possible ways to bring about undesirable ends, then we, the AI programmers, are already spending computing power in an undesirable way. We shouldn’t have the AI _running a search_ that will hurt us if it comes up positive, even if we _expect_ the search to come up empty. We just shouldn’t program a computer that way; it’s a foolish and self-destructive thing to do with computing power. Building an AI that would hurt us if omnipotent is a bug for the same reason that a NASA probe crashing if all seven other planets line up would be a bug—the system just isn’t supposed to behave that way _period;_ we should not rely on our own cleverness to reason about whether it’s likely to happen.
