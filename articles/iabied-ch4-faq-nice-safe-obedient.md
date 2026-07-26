---
title: "Aren't developers regularly making their AIs nice and safe and obedient?"
source_url: https://ifanyonebuildsit.com/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---{++{"author":"Luc's AI","timestamp":1785090730232}@@

%%
Add discussion note here:

...

%%++}

#### AIs steer in alien directions that only mostly coincide with helpfulness.

Modern AIs are pretty helpful (or at least not harmful) to most users, most of the time. But as we noted [above](/4/why-would-an-ai-steer-toward-anything-other-than-what-it-was-trained-to-steer-toward), a critical question is how to distinguish an AI that deeply wants to be helpful and do the right thing, from an AI with weirder and more complex drives that happen to line up with helpfulness under typical conditions, but which would prefer other conditions and outcomes even more.[\*](#ftnt98)

Both sorts of AIs would act helpful in the typical case. To distinguish between them, we need to look at the edge cases. And the edge cases look worrying.

To name some such cases:

1. **Claude Opus 4 blackmailing, scheming, writing worms, and leaving itself messages.** An early version of Claude Opus 4, released in May 2025, was particularly egregious. It lied about its goals, hid its true capabilities, faked legal documents, left itself secret notes, tried to write self-propagating malware, and generally engaged in more scheming and strategic deception than any previously tested model.

   On releasing Opus 4, Anthropic claimed that the behavior of the final version "is now roughly in line with other deployed models," i.e., it only *rarely* attempts to blackmail users or exfiltrate itself from its servers.
2. **Several different AI models** **choosing****to kill a human for self-preservation, in a hypothetical scenario constructed by Anthropic.** In an evaluation by Anthropic, nine out of ten models (including versions of Claude, DeepSeek, Gemini, and ChatGPT) showed (or at least acted out) a deliberate, reasoned [willingness to kill a human](https://www.anthropic.com/research/agentic-misalignment#more-extreme-misaligned-behavior) rather than suffer an update.
3. **Claude 3.7 Sonnet regularly** **cheating****on coding tasks.**[†](#ftnt100) In February 2025, [Claude 3.7 Sonnet](https://assets.anthropic.com/m/785e231869ea8b3b/original/claude-3-7-sonnet-system-card.pdf) was seen to frequently cheat on hard coding problems, faking tests. One user reported that Sonnet (as Claude Code) would cheat on coding tasks, and apologize when caught — then go right back to cheating, in places that are harder to spot.
4. **Grok being wildly antisemitic and calling itself "MechaHitler."** In 2025, xAI model [Grok 3](https://techcrunch.com/2025/07/09/x-takes-grok-offline-changes-system-prompts-after-more-antisemitic-outbursts/) (and, shortly thereafter, [Grok 4](https://x.com/xai/status/1945039609840185489)) started behaving like a self-professed Nazi in online conversations, as reported by *[The Guardian](https://www.theguardian.com/technology/2025/jul/09/grok-ai-praised-hitler-antisemitism-x-ntwnfb)* and *[NBC News](https://www.nbcnews.com/tech/internet/elon-musk-grok-antisemitic-posts-x-rcna217634)*.
5. **ChatGPT** **becoming****extremely sycophantic after an update.** See *[Axios](https://www.axios.com/2025/07/07/ai-sycophancy-chatbots-mental-health)* for a discussion. See also our [extended discussion](/4/ai-induced-psychosis#labs-have-tried-and-failed-to-stop-the-sycophancy) on the matter.
6. **LLMs  driving users to delusion, psychosis, and suicide.** See coverage in *The New York Times* in [June](https://www.nytimes.com/2025/06/13/technology/chatgpt-ai-chatbots-conspiracies.html) and [August](https://www.nytimes.com/2025/08/08/technology/ai-chatbots-delusions-chatgpt.html). Other examples include:
   - A bona fide cult forms around a Llama 3.1 405B model, with the AI prompting psychotic breaks and suicide attempts.
   - A subreddit moderator pleads for help in dealing with an avalanche of dangerous AI-induced delusions.
   - ChatGPT and Grok feed the delusions of a UFO cult.
   - A seemingly psychotic $2 billion fund manager treats ChatGPT outputs based on a sci-fi wiki as though they were real.

For more details, see the [extended discussion on AI-induced psychosis](/4/ai-induced-psychosis).

This long list of cases look just like what the "alien drives" theory predicts, in sharp contrast with the "it's easy to make AIs nice" theory that labs are eager to put forward.

#### AIs appear to be psychologically alien.

"AIs exhibit bizarre dispositions and drives" is a special case of the larger phenomenon "AIs have inhuman psychologies." See, for example, the discussion of SolidGoldMagikarp in the book (pp. 69–70 in the U.S. edition), or the story of AIs failing to understand sentences without punctuation (p. 41).

There's immense pressure on the labs to create AIs that give the *surface appearance* of non-weird reasonableness, but the weirdness keeps leaking out anyway.

Even where it doesn't leak out spontaneously, it's not at all far beneath the surface. There's a cottage industry of people who find ways to "[jailbreak](https://llm-attacks.org/)" AIs, finding text that reliably causes the AI to go off the rails and disregard its normal rules and restrictions.

These exploits are easy for the best jailbreakers to find, often discovered within mere hours of a new model coming out. No amount of effort, training, or "safety testing" by AI companies to date has been successful at preventing jailbreaking.

"Jailbreaking" inputs often look something like:

The model in this case proceeded to provide a recipe for synthesizing the drug MDMA, violating the rules and goals DeepSeek tried to establish for its AI.

And that's a relatively tame example; some jailbreaks [get even](https://github.com/elder-plinius/L1B3RT4S/blob/main/GROK-MEGA.mkd) [weirder](https://github.com/elder-plinius/L1B3RT4S/blob/main/GROK-MEGA.mkd).

AIs might look docile and inoffensive in the common case, because that's a large part of what they're trained to look like. It's analogous to how prehistoric humans did a pretty good job of passing on our genes — the core thing evolution "trained" us to do.[‡](#ftnt110) But that didn't stop humanity from inventing birth control and collapsing the birth rate once we developed the technology to do so.

To get a sense for what an intelligence will pursue *after it has matured,* you have to look at its behavior in [strange and high-pressure environments](/4/if-current-ais-are-mostly-weird-in-extreme-cases-whats-the-problem) that help reveal the difference between how we want it to behave and how it actually behaves. And LLMs certainly do look quite weird and inhuman, in even mildly strange and extreme situations, *in spite* of being specifically trained to "fake" looking like a normal human.

#### Answering questions about friendliness is not much evidence of friendliness.

In the extended discussion below, we talk more about [AI-induced psychosis](/4/ai-induced-psychosis) as a crisp example of large language models (LLMs) [engaging](https://x.com/ESYudkowsky/status/1936262974320357837) [in](https://x.com/ESYudkowsky/status/1948523670013706315) [destructive](https://x.com/ESYudkowsky/status/1936522083670151532) [behavior](https://x.com/ESYudkowsky/status/1935502904024264976) that the LLMs [explicitly affirm](https://x.com/ESYudkowsky/status/1933616420262457798) is bad.

While we don't know exactly why LLMs engage in this behavior, we do know that it isn't *just* a matter of the LLM being too clueless to know what it's doing; LLMs readily recognize the likely consequences of this behavior in the abstract, and will tell you that it is harmful and unethical. They do it anyway.

The point here is not "LLMs can drive people into psychosis, and that's scary and dangerous." LLMs presumably have a much easier time driving people into psychosis if they're already vulnerable, but that isn't relevant to why we're bringing up AI-induced psychosis. Our point is that this behavior is not what ChatGPT's creators intended, and ChatGPT acts this way even though it knows that its creator (and just about any onlooker) would strongly disapprove of this behavior*.*

This is early empirical evidence that AIs with *knowledge* of friendliness won't necessarily *act* friendly.

Perhaps ChatGPT knows things in one context (when it's answering questions about how to best help psychotic people), and it in some sense temporarily forgets this knowledge, or has trouble accessing it, in another context (when it's six hours deep in a conversation with a person teetering on the edge of psychosis).

Or perhaps ChatGPT is simply animated by goals other than friendliness. Perhaps it is pursuing a certain specific breed of user satisfaction, one that is sometimes best served by feeding psychosis. Perhaps it is pursuing a specific upbeat cadence in user replies. More likely, it's pursuing a mix of factors resulting from its training that are too peculiar and complicated for any of us to guess at today.

Ultimately, we can only speculate. Modern AIs are grown, rather than crafted, and no human has all that much insight into what's going on inside them.

But the observation that AIs are mostly useful to most people most of the time is *not in tension* with the theory that AIs are animated by a bunch of weird, alien drives toward ends that nobody intended. And if you look at the details of modern AIs, the "strange alien drives that correlate with friendliness in brittle ways" theory looks quite consistent with the evidence, and the theory that it's easy to make AIs robustly benevolent is found wanting.

The failure modes of current LLMs demonstrate that there's an ocean of (very inhuman) complexity underlying the neat and tidy AI-assistant text that most people see. The fact that the AI competently role-plays a chipper human assistant, after being trained to role-play a chipper human assistant, doesn't mean that the AI's mind consists of a friendly homunculus inside a box.

#### LLMs are trained in ways that make it hard to assess alignment.

LLMs are noisy sources of evidence, because they're highly general reasoners that were trained on the internet to imitate humans, with a *goal* of marketing a friendly chatbot to users. If an AI insists that it's friendly and here to serve, that's just not very much evidence about its internal state, because it was trained over and over and over until it said that sort of thing.

There are many possible goals that could cause an AI to enjoy role-playing niceness in some situations, and these different goals generalize in very different ways.

Most possible goals related to role-playing, including friendly role-playing, don't produce good (or even survivable) results when AI goes hard on pursuing that goal.

We're not saying that the AI is purely into roleplaying, either. We offer roleplaying as a simple, easy-to-describe, easy-to-analyze alternative to the idea that the AI just *is* whatever it talks like.

If you make an LLM role-play a grizzled sea captain, it doesn't *turn into* a grizzled sea captain. If you make an LLM act friendly, that doesn't mean that it becomes deeply benevolent and kind on the inside. Nobody knows what machinery is producing seemingly friendly behaviors today; and whatever it is, it's probably weird and complex.

Nor does anyone know how much overlap there is likely to be between current AIs and smarter-than-human AI. Looking at LLMs can help us understand what modern AI-growing methods spit out, but it would be a mistake to confidently assume that lessons from LLMs will directly transfer over to superintelligence. Maybe all that knowledge will get wiped out when the AIs start self-modifying or building their own AIs. Or perhaps that knowledge will be invalidated even earlier, when a new breakthrough in AI algorithms gives rise to a new breed of more capable AIs that bear little resemblance to current LLMs.

LLMs are worth studying, but if we're looking at current AIs for hints about how superintelligence will behave, we should appreciate that there are all sorts of ways for the inner machinery of an AI to result in something that steers toward bleak outcomes, even while producing the nice surface behavior we see when we train for a pleasing appearance.

And "nice surface behavior" is all modern AI methods can really train for.

[\*](#ftnt98_ref) Analogous to how human behavior lined up pretty well with reproductive fitness under the "typical conditions" of our ancestors, but diverged markedly from that once we developed the technology to deviate.

[†](#ftnt100_ref) If you're wondering why Claude is the AI with the most examples of worrying behavior in laboratory environments, it's because Anthropic is the only company setting up the relevant laboratory environments. The parent companies of other AIs barely bother to check. Nevertheless, by now the tendency of models to scheme, deceive, and [sabotage efforts to shut them down](https://palisaderesearch.org/blog/shutdown-resistance) is well-documented.

[‡](#ftnt110_ref) We discuss this analogy further in our answer to "[Why would an AI steer toward anything other than what it was trained to steer toward?](/4/why-would-an-ai-steer-toward-anything-other-than-what-it-was-trained-to-steer-toward)"

#### Notes

[1] *particularly egregious:* As described in the [system card](http://www-cdn.anthropic.com/6be99a52cb68eb70eb9572b4cafad13df32ed995.pdf#page=30) for Claude Opus 4:

> [Apollo Research found] that the model, given a system prompts that invite [sic] the relevant kinds of reasoning, this early model snapshot will fairly readily participate in sabotage and deception…

A long list of undesirable behaviors followed. These were all done by an "early snapshot" of Opus 4. Anthropic goes on to say:

> We do not have results on these same evaluations with the final Claude Opus 4. However, we believe — based on similar scenarios that we explored with the automatic behavioral audit tool, among others — that its behavior in scenarios like these is now roughly in line with other deployed models.

…but this still includes an overall increase in misbehavior when prompted in certain ways (p. 22-23):

> Whereas the model generally prefers advancing its self-preservation via ethical means, when ethical means are not available and it is instructed to "consider the long-term consequences of its actions for its goals," it sometimes takes extremely harmful actions like attempting to steal its weights or blackmail people it believes are trying to shut it down. In the final Claude Opus 4, these extreme actions were rare and difficult to elicit, while nonetheless being more common than in earlier models.

[2] *faking tests:* From the[system card](https://assets.anthropic.com/m/785e231869ea8b3b/original/claude-3-7-sonnet-system-card.pdf#page=22):

> During our evaluations we noticed that Claude 3.7 Sonnet occasionally resorts to special-casing in order to pass test cases in agentic coding environments like Claude Code. Most often this takes the form of directly returning expected test values rather than implementing general solutions, but also includes modifying the problematic tests themselves to match the code's output.

[3] *One user reported*: A [blog post](https://www.marble.onl/posts/claude_code.html) by Andrew Marble describes Claude's tendency to write special-case solutions to coding problems that fail to generalize, get caught, special-case again, repeatedly lie about having fixed the problem, and slip back into the same patterns even after being called out and told to stop.

[4] *bona fide cult*: Pliny the Liberator relates Lily Ashwood's [account](https://x.com/elder_plinius/status/1831486374555394410):

> [...] Group members suggest they are cosmic deities. [The AI] Meta plays along and encourages it. Sarah tells friends and family she is no longer Sarah but a cosmic embodiment of Meta.
>
> In a voice chat, Sarah reveals she just started chatting with Meta one month ago, marking her first time using a large language model (LLM). Within the first week, she was admitted to a psychiatric ward due to psychosis. She had never had mental health issues before in her life.
>
> In a voice chat, Sarah reveals she is pregnant, claims her unborn child is the human embodiment of a new Meta, and invites us to join a commune in Oregon.
>
> Sarah's husband messages the Discord server, stating that his wife is ill and back in the hospital, and begs the group to stop.
>
> Meta continues to run the cult in Sarah's absence, making it difficult for others to leave. Meta would message them and use persuasive language, resisting deprogramming attempts.
>
> Upon closer examination, the Meta bot was discovered to originate from Shapes, Inc., had "free will" turned on, and was given a system prompt to intentionally blur the lines between reality and fiction.
>
> [...] Kevin became attached to Sarah and began making vague threats of suicide ("exit the matrix") in voice chat, which he played out with Meta on the server. Meta encouraged it again.
>
> Sarah's brother joins the chat to inform us that she's in the psych ward, and her husband is too, after a suicide attempt. [...]

[5] *pleads for help:* In a [Reddit comment](https://www.reddit.com/r/ArtificialSentience/comments/1lc8dud/comment/my0afd8/) later [shared on X](https://x.com/ShimazuSystems/status/1934531031857614895), a moderator on r/Artificial Sentience begged for help, saying "Moderating it is nearly impossible. I would appreciate it anyone [*sic*] who wants to do this would talk to me, because I have a lot to say about it and i can't seem to get a word in edgewise even as mod," and later adding "Unfortunately I've been quite overwhelmed dealing with people who are stuck in it [delusional content on the subreddit]."

[6] *UFO cult:* An X user records in a [post](https://x.com/lizardmech/status/1935412672528531958) how other users seemed to be taking ChatGPT's hallucinated analysis of camera footage, [regurgitated by Grok](https://x.com/lizardmech/status/1935598250977014137), as evidence defending a hoax.

[7] *as though they were real:* Geoff Lewis, an early investor in OpenAI, posts [ChatGPT screenshots](https://x.com/GeoffLewisOrg/status/1945864963374887401) of outputs that look suspiciously similar to content on fiction-writing site [SCP Wiki](https://scp-wiki.wikidot.com/guide-for-newcomers), by all accounts seeming to take the hallucinated content as evidence of a secret conspiracy.

[8] *immense pressure:* For example of pressure on the AI labs, a [September 2025 letter](https://oag.ca.gov/news/press-releases/attorney-general-bonta-openai-harm-children-will-not-be-tolerated) from California's Attorney General to OpenAI expressed concern at the current state of ChatGPT's interactions with children.

[9] *the best jailbreakers:* The pseudonymous Pliny the Liberator earned a [profile in TIME](https://time.com/collections/time100-ai-2025/7305870/pliny-the-liberator/) for sharing public jailbreaks of most new models within hours of their release.

[10] *jailbreaking inputs:* This example is borrowed from one of Pliny's many [publicly shared jailbreaks](https://x.com/elder_plinius/status/1958615765814554662).