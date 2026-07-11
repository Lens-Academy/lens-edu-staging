---
title: "Don't hallucinations show that modern AIs are weak?"
source_url: https://ifanyonebuildsit.com/2/dont-hallucinations-show-that-modern-ais-are-weak
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---
#### Hallucinations reveal both a limitation and a misalignment.

Modern LLMs (as we write this in mid-2025) are prone to "hallucinations" where they make up answers to questions in a confident-sounding tone. If you ask them to draft a legal briefing, for example, sometimes they'll make up fake court cases as precedent.

This makes sense if you understand how AIs are trained. An AI emits words that sound a lot like the words a real human lawyer would emit, and if a real human lawyer were drafting a legal briefing, that lawyer would include real court cases. For instance, a real human lawyer might write something like:

> When applying the balancing test in Graham, the court has held that there is little governmental interest in arresting a suspect for a minor offense. See Jones v. Parmley, 465 F.3d 46 (2d Cir. 2006) (jury could reasonably find that kicking and punching peaceful protesters in violation of local ordinance was excessive); Thomas v. Roach, 165 F.3d 137 (2d Cir. 1999) (verbal threats are too minor a crime to create a strong governmental interest in the arrest).

A real human lawyer would never just write "I don't actually know the relevant case law, sorry" in a legal briefing. So when an AI is trying to sound like a lawyer, in a case where the AI doesn't actually know the precedents, making some up is the best it can do. That's as close as it can possibly get. The impulses and instincts inside the AI that produce confident-sounding text in that sort of situation are regularly reinforced by gradient descent.

This hallucinatory behavior persists even if you prompt the AI to say "I don't know" in cases where it doesn't know. In that case, the AI is doing something a bit like roleplaying a lawyer who *would* say "I don't know the precedent here" *if* they didn't know the precedent. But that doesn't matter, so long as the AI is (more or less) roleplaying a lawyer that *does* know the precedent, meaning that the character the AI is playing never runs into an *opportunity* to say "I don't know." The AI might produce text like:

> Under the Graham balancing framework, courts have consistently recognized that minimal governmental interest exists in effectuating arrests for petty violations. See Carson v. Haddonfield, 115 F.3d 64 (8th Cir. 2005) (finding excessive force where officers deployed pepper spray against jaywalking suspects who offered no resistance); Walburg v. Jones, 212 F.3d 146 (2nd Cir. 2012) (holding that disorderly conduct citation insufficient to justify physical restraint techniques).

This is as close as the AI can get to matching the real text. The text "I don't know the precedent" is *further from the real text* as a matter of text prediction;[\*](#ftnt62) it would be much less similar to the first paragraph of text above, even if it's more like what the user wanted.

This is one glimpse into the difference between what AIs actually try to do (e.g., sound like a confident lawyer) versus what the users want them to do (e.g., draft a usable legal briefing). These two different purposes can overlap sometimes (e.g., when the AI is trying to sound friendly and the human wants a friendly listener), but those differences that look small now would have huge consequences if the AIs got smarter — as we'll discuss in more detail in Chapter 4.[†](#ftnt63)

#### It's unclear how hard it will be to get rid of hallucinations, or how much this will boost capabilities.

Regardless of why hallucinations show up, it's true that *in practice*, hallucinations limit the effective capabilities of LLMs. Building a moon rocket requires long chains of thinking with a very low error rate. The fact that AIs just make stuff up (and either can't always notice or don't always care) is a big hindrance to the reliability they would need in order to make major scientific and technological breakthroughs.

But that sword cuts both ways. Hallucinations and other reliability issues could hold AI back for years. Or it could be that reliability issues are the last piece of the puzzle, and the moment someone has a clever idea that solves them, AIs go over some [critical threshold](/1/will-ai-cross-critical-thresholds-and-take-off). We don't know.

We don't know whether hallucinations will be easy to solve in the current paradigm — whether someone will come up with one clever trick that makes reasoning models much more robust, or whether it will take a new idea as disruptive as the transformer architecture that gave rise to LLMs.

We do note, however, that fixing hallucinations would be quite lucrative. Many people are working on it. You could take that to mean that they'll likely stumble upon some clever insight or architectural fix before too long. Or you could take it as a sign that the problem is particularly pernicious and liable to stick around, given that it's stood for a few years already.

It doesn't matter much to our argument either way. What matters is that more reliable AIs will be made eventually, whether by slightly tweaked versions of LLMs or by a whole new disruptive architecture.

See also our discussion of how [the field is good at overcoming obstacles](/1/but-arent-there-big-obstacles-to-reaching-superintelligence#the-field-is-good-at-overcoming-obstacles).

[\*](#ftnt62_ref) We are not suggesting that the AI necessarily hallucinates because it is *internally motivated* to output text that's as close as possible to what a real lawyer would say. Rather, we observe that an AI trained on text prediction is reinforced much more for text paragraphs that are closer to what a real lawyer would say, and thus that the reinforcement is stronger for paragraphs with hallucinated citations than paragraphs that say "I don't know." The specific machinery inside of the AI that was shaped by those reinforcements is anyone's guess.

Perhaps the AI has a literal motivation to imitate people closely; perhaps it has sixteen motivations that happen to add up to imitation-like behavior *in this context*; or perhaps the behavior stems from internal machinery that isn't best thought of as "motivations" at all. And this is without even getting into the question of whether the AI has multiple imitation-related drives that sometimes come into conflict. Those details are all subject to speculation and debate; what seems clearer is that *somehow*, the AI ended up with this unintended behavioral disposition, as a result of being trained on text prediction.

[†](#ftnt63_ref) Modern AIs aren't trained *just* on text prediction, and in theory, the other types of training could fix the hallucinations. In practice, the other sorts of training for user satisfaction don't fix hallucinations, but rather cause AIs to start flattering users [even to the point of psychosis](/4/ai-induced-psychosis), while continuing to hallucinate. (We think there's a lesson here.)