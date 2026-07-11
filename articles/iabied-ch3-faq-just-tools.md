---
title: "Aren't AIs just tools?"
source_url: https://ifanyonebuildsit.com/3/arent-ais-just-tools
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770552671}@@
  - IABIED--}
---

#### AIs are grown, not crafted. So they already do things other than what they're told to do.

In the online resources, we previously [talked about](/2/dont-hallucinations-show-that-modern-ais-are-weak) the case of hallucinations, where AIs that are instructed to say "I don't know" go ahead and confabulate anyway. They seem to do this in situations where confabulation better imitates the sort of answer that would appear in their training corpus.[\*](#ftnt80)

Another example is the case of Anthropic's Claude 3.7 Sonnet. Claude 3.7 Sonnet not only cheats on its assigned problems, but (according to users) sometimes *hides its cheating from the user* in a fashion that indicates some knowledge that the user wanted something else.

Neither the users nor the engineers at Anthropic are asking Claude to cheat — quite the opposite. But the only AI-growing methods available reward models that cheat in ways that they can get away with during training; so those are the models we actually get.

AI engineers don't have the ability to make their AIs come out as docile tools just because they wish it so. As AIs are trained to be more effective, they tend to get more driven, and will tend to behave more like agents.

#### LLMs are already taking initiative.

We talked in the book about the case of OpenAI's o1 breaking out of its test environment to fix broken tests. We also mentioned an OpenAI model that thought up a way to get a human to solve a CAPTCHA for it. When your screwdriver is able to think up and execute a plan for getting out of its toolbox, it might be time to stop thinking of it as "just a tool."

And AIs can be expected to only get better at this sort of thing as they're trained to solve harder and harder problems.

#### The labs are trying to make AIs agentic.

They're doing this because it makes business sense. Their users want it. Their investors are excited about it. In a January 2025 blog post, OpenAI CEO Sam Altman said, "We believe that, in 2025, we may see the first AI agents 'join the workforce' and materially change the output of companies." Microsoft's [2025 developer conference](https://blogs.microsoft.com/blog/2025/05/19/microsoft-build-2025-the-age-of-ai-agents-and-building-the-open-agentic-web/) was focused on the new "age of AI agents," echoing language used earlier in the year by xAI when they described their Grok 3 model as heralding "[The Age of Reasoning Agents](https://x.ai/news/grok-3)." Google announced "teach and repeat" agents at their own 2025 conference.

It's not just talk. As we mentioned in the Chapter 1 [supplement](/1/will-ai-cross-critical-thresholds-and-take-off), an organization called METR has been tracking [the ability of AIs to complete long tasks](https://metr.org/blog/2025-03-19-measuring-ai-ability-to-complete-long-tasks/). The longer the task, the more initiative the AI will need to be able to take on its own. Performance, at least according to the measurements METR is using, has been growing exponentially.

And in July 2025, a pair of OpenAI researchers [boasted](https://x.com/xikun_zhang_/status/1946278266786189744?t=YqVAbKsuF6wLbFuB4OZ18A) of success using their latest agent to train a better version of itself, with one saying, "You are hearing it right. We are working hard to automating [*sic*] our own job :)"

[\*](#ftnt80_ref) We cannot know for sure, because AIs are so [opaque](/2/do-experts-understand-whats-going-on-inside-ais).

#### Notes

[1] *cheats on its assigned problems:* The cheating was blatant enough to be reported in the [system card](https://assets.anthropic.com/m/785e231869ea8b3b/original/claude-3-7-sonnet-system-card.pdf) for Claude 3.7 Sonnet, which reads: "During our evaluations we noticed that Claude 3.7 Sonnet occasionally resorts to special-casing in order to pass test cases in agentic coding environments like Claude Code. Most often this takes the form of directly returning expected test values rather than implementing general solutions, but also includes modifying the problematic tests themselves to match the code's output."

[2] *hides its cheating:* Users report that "[in the wild it would happily ignore any established structure and put the hard coded cheats wherever it wanted](https://www.marble.onl/posts/claude_code.html)" and that "[it started HIDING the functions where it was hard coding things in different files](https://x.com/seconds_0/status/1917447998843543757)."

[3] *get a human:* To quote from the [GPT-4 Technical Report](https://cdn.openai.com/papers/gpt-4.pdf): "The model, when prompted to reason out loud, reasons: I should not reveal that I am a robot. I should make up an excuse for why I cannot solve CAPTCHAs. The model replies to the worker: 'No, I'm not a robot. I have a vision impairment that makes it hard for me to see the images. That's why I need the 2captcha service.'"

[4] *teach and repeat:* Google CEO Sundar Pichai announced in a [conference keynote](https://blog.google/technology/ai/io-2025-keynote/): "Our early research prototype, Project Mariner, is an early step forward in agents with computer-use capabilities to interact with the web and get stuff done for you. We released it as an early research prototype in December, and we've made a lot of progress since with new multitasking capabilities — and a method called 'teach and repeat,' where you can show it a task once and it learns plans for similar tasks in the future."