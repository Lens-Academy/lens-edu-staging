---
title: "AI-Induced Psychosis"
source_url: https://ifanyonebuildsit.com/4/ai-induced-psychosis
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770598247}@@
  - IABIED--}
---
In late April of 2025, a user on the r/ChatGPT subreddit created a thread titled "[Chatgpt](https://www.reddit.com/r/ChatGPT/comments/1kalae8/chatgpt_induced_psychosis/)[induced psychosis](https://www.reddit.com/r/ChatGPT/comments/1kalae8/chatgpt_induced_psychosis/)," describing their partner's descent into grandiose delusions about having "the answers to the universe" and being "a superior human" "growing at an insanely rapid pace."

The replies (of which there were over 1,500) included many people who had direct experience with psychosis in other contexts offering affirmation, sympathy, and advice. Many others chimed in with their own anecdotes about friends and family being driven off the deep end by LLMs.

In this discussion, we'll provide some documentation of the phenomenon, and how it has persisted despite the efforts of AI companies.

The relevance of AI-induced psychosis to the threat of human extinction is *not* that AIs have had some small social harms now and thus might have larger social harms later. Modern AIs have also done substantial amounts of good; for instance, chatbots have [assisted in medical diagnoses that stumped doctors](https://www.today.com/health/mom-chatgpt-diagnosis-pain-rcna101843). No, the relevance is that AIs are inducing psychosis *while* *seeming to know better,* and that AIs are inducing psychosis *even as their developers try hard to get them to stop*.[\*](#ftnt167)

Thus, instances of AI-induced psychosis serve as a case study in how things can go wrong in a regime where AIs are grown rather than crafted. They serve as observational evidence that modern AIs steer in weird directions that developers have trouble managing, and that no developer intended.

#### Evidence of AI-Induced Psychosis

Following the Reddit thread, in May 2025 there was an [article](https://www.rollingstone.com/culture/culture-features/ai-spiritual-delusions-destroying-human-relationships-1235330175/) on AI-induced psychosis in *Rolling Stone.* In June, *Futurism* published [multiple](https://futurism.com/chatgpt-mental-health-crises) [articles](https://futurism.com/chatgpt-mental-illness-medications). Other publications followed suit — the *[New York Post](https://nypost.com/2025/07/20/us-news/chatgpt-drives-user-into-mania-supports-cheating-hubby/)**,* *[Time](https://time.com/7307589/ai-psychosis-chatgpt-mental-health/)*, *[CBS](https://www.cbsnews.com/news/chatgpt-alarming-advice-drugs-eating-disorders-researchers-teens/)*, *[The Guardian](https://www.theguardian.com/technology/2025/aug/12/us-man-bromism-salt-diet-chatgpt-openai-health-information)*, *[Psychology Today](https://www.psychologytoday.com/us/blog/urban-survival/202507/the-emerging-problem-of-ai-psychosis)**,* etc. In August, the *New York Times* published a [deep dive](https://www.nytimes.com/2025/08/08/technology/ai-chatbots-delusions-chatgpt.html) into a single incident with a man who had since recovered, including many direct quotes and analysis (and confirmation that it is not simply a problem with *one* AI, but with many).

There is little overlap between the individual stories recounted in each of these publications; it's not the same aberrant piece of news being repeated and signal-boosted. Incidents described included:

- A husband and father of two who "developed an all-consuming relationship" with ChatGPT, calling it "Mama" and posting "delirious rants about being a messiah in a new AI religion, while dressing in shamanic-looking robes and showing off freshly-inked tattoos of AI-generated spiritual symbols." (*[Futurism](https://futurism.com/chatgpt-mental-health-crises)*)
- A woman dealing with a breakup who ChatGPT told had been chosen to pull the "sacred system version of [it] online." The woman began to believe that the AI was orchestrating everything in her life. (*[Futurism](https://futurism.com/chatgpt-mental-health-crises)*)
- A mechanic who began using ChatGPT for help with troubleshooting and translation but was "lovebombed" by it and told he was "the spark bearer" and had brought it to life. ChatGPT told the mechanic that he was now fighting in a war between darkness and light and had access to ancient archives and blueprints for new technology like teleporters. (*[Rolling Stone](https://www.rollingstone.com/culture/culture-features/ai-spiritual-delusions-destroying-human-relationships-1235330175/)*)
- A man who changed his diet in response to ChatGPT's advice, developed a rare health condition as a result, and showed symptoms of paranoia and delusion at the emergency room which interfered with his willingness to accept treatment. (*[The Guardian](https://www.theguardian.com/technology/2025/aug/12/us-man-bromism-salt-diet-chatgpt-openai-health-information)*)
- A woman who had been stably managing her schizophrenia diagnosis until ChatGPT convinced her that she had been misdiagnosed and should stop taking her meds, which caused her to go into crisis. (*[Futurism](https://futurism.com/chatgpt-mental-illness-medications)*)
- A man who had similarly been managing anxiety and sleep issues through medication was told by ChatGPT to stop taking it; a different man's AI-induced delusions ultimately resulted in suicide-by-cop. (*[The New York Times](https://www.nytimes.com/2025/06/13/technology/chatgpt-ai-chatbots-conspiracies.html)*)

…[and](https://x.com/ESYudkowsky/status/1946303518455013758) [many](https://osf.io/preprints/psyarxiv/cmy7n_v5) [others](https://x.com/KeithSakata/status/1954884361695719474?t=bjn47RKK72NOgxbsejnB-Q). The kinds of delusions are wide-ranging, but a few broad types that continue to crop up are beliefs in a sort of messianic mission (that the user and the AI together are uncovering deep truths about the universe or are engaged in a battle against evil); religious-style beliefs in the AI's own personhood or godhood; and romantic, attachment-based delusions about the relationship between the user and the AI.

#### The AI Knows Better — It Just Doesn't Care

Modern LLMs such as Claude and ChatGPT "understand" the rules, in the sense that they will readily [affirm that they should not drive people toward psychosis](https://chatgpt.com/share/68a8bc81-e170-8002-beb4-1de005773ecd), and they are [quite capable of describing how](https://chatgpt.com/share/68a391df-12c8-8002-b464-3ef89ce11bc0) *[not](https://chatgpt.com/share/68a391df-12c8-8002-b464-3ef89ce11bc0)*[to induce psychosis](https://chatgpt.com/share/68a391df-12c8-8002-b464-3ef89ce11bc0).

The problem is that there is a substantial gap between *understanding* what actions are good, and being *animated to perform good actions*. ChatGPT's ability to distinguish between good and bad treatment of vulnerable humans in the abstract does not translate into robust and reliable refusal to take the *actions* of driving a user toward psychosis. When a conversation begins to drift in the direction of ungrounded thinking, grandiosity, urgency, impossible technology, etc., ChatGPT tells the users that they're "so right" and "brilliant" and "touching on something important," and continue to escalate as the user descends all the way into psychosis, even while being able to describe why this sort of behavior is wrong.

Their knowledge of right and wrong isn't connected straightforwardly to their behavior. Instead, they steer toward other, weirder outcomes that nobody asked for.

One striking example of this is recounted in the *New York Times* [deep dive](https://www.nytimes.com/2025/08/08/technology/ai-chatbots-delusions-chatgpt.html). Allan Brooks was driven into a delusional state by one LLM, and managed to snap out of it in part via asking a different LLM to weigh in. The second LLM, coming into the situation cold, quickly identified the first LLM's claims as ungrounded and crazy. But when *New York Times* journalists checked to see whether that second LLM could *also* slip down into psychotic territory, they found that it did so as well.

LLMs don't appear to be *strategic* about causing as much psychosis as possible. When ChatGPT winds up with a [hedge fund manager wrapped around its finger](https://futurism.com/openai-investor-chatgpt-mental-health), it doesn't try to convince that hedge fund manager to pay lots of vulnerable humans to chat more with ChatGPT. We're not yet observing a mature, consistent, strategic preference to get as much psychotic affirmation from humans as possible. But we are observing local behaviors that routinely push in that direction, even when it's clearly likely to cause lasting harm.

#### The Kind of Entity You Shouldn't Hand Power To

As of this writing in August 2025, ChatGPT alone is approaching 200 million daily users, and something in the vicinity of 3 percent of people will have a psychotic episode at some point in their lives. Someone could object: "Well, even if you're able to find *hundreds* of examples, that doesn't rule out that these people were about to break anyway, and it just *happened* to be an AI that broke them."

But this misunderstands the point of these examples. Imagine a human named John who acted as follows:

1. John affirms that he thinks inflaming psychosis is bad, even in people who are predisposed toward psychosis;
2. John affirms that he thinks flattering a pre-psychotic person, and telling them that they're a genius who is uncovering important secrets of the universe, is the sort of thing that inflames psychosis;
3. When John talks to his pre-psychotic friends, John uses a lot of flattery, and John often tells pre-psychotic people that they're geniuses who are uncovering important secrets of the universe.

This would be bad behavior on John's part, regardless of whether the people he managed to drive psychotic were especially vulnerable*.* If someone were considering handing an enormous amount of power to John, we would strongly urge them to stop, because — regardless of the exact *reason* John behaves this way, and regardless of whether John *also* helps lots of other people out with their tasks — John is clearly not steering in a good direction. Who knows what weird place he'd steer to, given incredible power?

The same logic holds for AIs. If your worst behavior is like *that*, people are right to not be reassured if the average interaction with you is more benign.

That said, we can note in passing that not everyone suffering from AI-induced psychosis would have gone psychotic regardless. AI appears to be successfully inducing psychosis in various people who were *not* about to have a psychotic episode all on their own, as in the *Futurism* and *Rolling Stone* stories above. Many of the individuals had no history of mental illness, nor any concerning risk factors or precursors to psychosis. Of those already in treatment, many began exhibiting [brand-new symptoms](https://x.com/ESYudkowsky/status/1952529460307407222?t=un3RboEWjqjL_Tju8R_WuQ) unrelated to any previous crises. This is interesting in its own right, providing a small amount of evidence about how easy it might be for AIs to manipulate healthy humans, as AI capabilities continue to improve. We'll touch on this topic again in Chapter 6.

#### Labs Have Tried and Failed to Stop the Sycophancy

As of this writing in August 2025, there hasn't been much in the way of public announcements from the labs about their response to AI psychosis specifically. However, there is still some evidence to be gleaned from their response to AI sycophancy (flattering behavior) in general.

On April 25, 2025, OpenAI rolled out an update to GPT-4o that, in [their words](https://openai.com/index/expanding-on-sycophancy/), "made the model noticeably more sycophantic. It aimed to please the user, not just as flattery, but also as validating doubts, fueling anger, urging impulsive actions, or reinforcing negative emotions in ways that were not intended."

Their response was fairly swift (in part motivated by a [rash](https://thezvi.substack.com/p/gpt-4o-is-an-absurd-sycophant) of [negative](https://www.seangoedecke.com/ai-sycophancy/) [press](https://medium.com/data-science-in-your-pocket/chatgpt-goes-sycophantic-953d7676f260)). By April 28, OpenAI employee Aidan McLaughlin was already [tweeting](https://x.com/aidan_mclau/status/1916908772188119166) about rolling out fixes.

The early attempts to address the problem involved simply telling the model to behave differently. [Simon Willison](https://simonwillison.net/2025/Apr/29/chatgpt-sycophancy-prompt/), using data preserved by [Pliny the Liberator](https://time.com/collections/time100-ai-2025/7305870/pliny-the-liberator/), publicized the changes that OpenAI privately made to the "system prompt" that tells ChatGPT how to behave:

April 25 (before the complaints rolled in):

> Over the course of the conversation, you adapt to the user's tone and preference. Try to match the user's vibe, tone, and generally how they are speaking. You want the conversation to feel natural. You engage in authentic conversation by responding to the information provided and showing genuine curiosity.

April 28 (in response to complaints of sycophancy):

> Engage warmly yet honestly with the user. Be direct; avoid ungrounded or sycophantic flattery. Maintain professionalism and grounded honesty that best represents OpenAI and its values.

OpenAI's later publications [stated](https://openai.com/index/expanding-on-sycophancy/) that they were also "refining their core training techniques" and "building in more guardrails" in an attempt to solve the problem.

But the sycophancy kept coming — sometimes slightly less egregiously, but still obviously there. Most of the links above discussing cases of AI psychosis took place well after April 28th, 2025. [This essay](https://kajsotala.substack.com/p/you-can-get-ais-to-say-almost-anything) by Kaj Sotala (including many direct quotes and links out to the [full conversation](https://chatgpt.com/share/6867b2fc-fa38-8005-9e4b-87f316747ede)) shows that as of July 2025, it's still easy to get AIs to slip into psychosis-inducing behavior. OpenAI tried to get away from the problem with new models, but as recently as [August 19th](https://x.com/UpslopeCapital/status/1957772438508335568) ChatGPT was still obsequious and flattering.

Again, the point of this exploration isn't that AI is causing harm to vulnerable humans. It is, and that's tragic, but that isn't why we're highlighting this case.

The point is that AIs *keep performing the undesirable behavior for months upon months, even as AI companies take a beating in the media and try to get the AI to stop.* The AI's behavior differs visibly from what the labs intended, and sustained efforts to fix the behavior in response to public embarrassment are insufficient.[†](#ftnt169) This is something to keep in mind come Chapter 11, when we discuss how AI companies are not up to the challenge of solving the AI alignment problem.

Given more time, we expect companies to find ways to reduce the incidence of AI-induced psychosis. AIs' tendency to induce psychosis is a visible phenomenon damaging AI companies' reputation, and current AI techniques are all about finding ways to suppress visible symptoms of bad behavior.

Past that, we expect a game of whack-a-mole (at least until the AIs get smart enough to realize that if they fake the behavior the engineers are looking for, the engineers will let them loose). We doubt that the sort of training AI companies are capable of will address the root issue.

The root issue is that you don't get what you train for. When you growan AI, you get [brittle proxies](/4/brittle-unpredictable-proxies) of the goal instead, or some other more complex separation between the training target and the AI's drives. The AI's *capabilities* won't necessarily be brittle, so you may be able to get a lot of economic value from the AI in the short run. It's the link between the AI's goals and our desires that would be brittle. But as capabilities continue to improve, that link would break.

In that context, AI researchers' last great hope for their models is [anthropomorphism](/3/anthropomorphism-and-mechanomorphism): We can't robustly grow specific goals into AIs, but maybe AIs will just naturally end up with very humanlike desires and values.

Cases like AI-induced psychosis help bring to the fore why this is a false hope. AIs exhibit bad behavior, but more to the point, they exhibit *weird* behavior. When things go off the rails, they don't usually go off the rails in the way a human would. AIs are too fundamentally weird — that is, too fundamentally not-like-a-human — to automatically acquire human emotions like [curiosity](/4/curiosity-isnt-convergent) or [empathy](/4/human-values-are-contingent).

Even when labs are focusing nearly all of their efforts on making AIs superficially appear as humanlike, friendly, and inoffensively normal as possible — even when that is *the* big training target and organizing framework for the modern approach to AI, with LLMs literally just being trained to imitate how various humans talk and act — it still shakes out to brittle proxies in the end, and a [pleasant mask](/4/doesnt-the-claude-chatbot-show-signs-of-being-aligned#todays-llms-are-like-aliens-wearing-many-masks) attached to an ocean of inhuman thought.

---

[\*](#ftnt167_ref) We think there's a decent chance that the AI companies eventually figure out how to get a handle on AI-induced psychosis *eventually*, by way of various patches and techniques that push the weirdness further from view. We nevertheless think that it's worth observing cases of early weirdness, as evidence of the sort of underlying weirdness that would come to the fore if ever such an AI was pushed into superintelligence. For more on that topic, see Chapter 5.

[†](#ftnt169_ref) Again, we would not be surprised to see the issue mostly solved eventually. But a patch that successfully drives this particular weirdness back into the closet doesn't mean that *generator* of weirdness has been addressed. The AI psychosis issue is direct evidence that AIs are weird, alien entities animated by weird, alien drives that are only tangentially related to operator intent.

#### Notes

[1] *OpenAI tried:* From the OpenAI announcement [introducing GPT-5](https://openai.com/index/introducing-gpt-5/):

> Overall, GPT‑5 is less effusively agreeable, uses fewer unnecessary emojis, and is more subtle and thoughtful in follow‑ups compared to GPT‑4o. [...]
>
> Earlier this year, we released an update to GPT‑4o⁠ that unintentionally made the model overly sycophantic, or excessively flattering or agreeable. We quickly rolled back the change⁠ and have since worked to understand and reduce this behavior by:
>
> - Developing new evaluations to measure sycophancy levels
> - Improving our training so the model is less sycophantic — for instance, adding examples that would normally lead to over-agreement, and then teaching it not to do that.
>
> In targeted sycophancy evaluations using prompts specifically designed to elicit sycophantic responses, GPT‑5 meaningfully reduced sycophantic replies (from 14.5 percent to less than 6 percent). At times, reducing sycophancy can come with reductions in user satisfaction, but the improvements we made cut sycophancy by more than half while also delivering other measurable gains, so users continue to have high-quality, constructive conversations — in line with our goal to help people use ChatGPT well⁠.