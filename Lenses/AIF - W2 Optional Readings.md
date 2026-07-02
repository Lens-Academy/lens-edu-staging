{++{"author":"AI","timestamp":1782974982493}@@---
id: e838cb7c-34a1-4249-8b57-d3698f80f1ad
title: "AIF - W2 Optional Readings"
---

#### Text
content::
Optional extras for this week, grouped by what you want to go deeper on.

**Key papers (5–30 min each)**
- [Emergent misalignment](https://arxiv.org/abs/2502.17424) — finetuning a model to write insecure code makes it broadly evil; the result that surprised everyone.
- [Weird generalization](https://arxiv.org/abs/2512.09742) — more evidence that narrow training moves broad behavior in unexpected ways.
- [Reward hacking in production RL](https://assets.anthropic.com/m/74342f2c96095771/original/Natural-emergent-misalignment-from-reward-hacking-paper.pdf) — misalignment emerging naturally inside a real training pipeline, not a lab demo.
- [OpenAI's scheming paper](https://www.antischeming.ai/) plus the [eval awareness post](https://www.lesswrong.com/posts/qgehQxiTXj53X49mM/sonnet-4-5-s-eval-gaming-seriously-undermines-alignment) — what happens to alignment evidence when models notice they're being tested.

**Deeper into the scheming report**
- [Carlsmith's full report](https://www.lesswrong.com/posts/yFofRxg7RRQYCcwFA/new-report-scheming-ais-will-ais-fake-alignment-during): sections 2.1 (requirements for scheming), 2.3 (the goal-guarding story), 4.2 (counting argument), 4.3 (simplicity argument). [Audio option](https://joecarlsmithaudio.buzzsprout.com/2034731/episodes/13980105-full-audio-for-scheming-ais-will-ais-fake-alignment-during-training-in-order-to-get-power).

**Basic frames for thinking about AIs**
- [Different senses in which two AIs can be "the same"](https://www.alignmentforum.org/posts/4j6HJt8Exowmqp245/different-senses-in-which-two-ais-can-be-the-same) — surprisingly load-bearing for threat models involving copies.
- [The Artificial Self](https://theartificialself.ai/) — what LLM "selves" are made of.
- [A Three-Layer Model of LLM Psychology](https://www.lesswrong.com/posts/zuXo9imNKYspu9HGv/a-three-layer-model-of-llm-psychology) — ground layer, character, surface: a working vocabulary for model behavior.
- [AI 2027 AI goals supplement](https://ai-2027.com/research/ai-goals-forecast) — if you skipped it in the main track.
- [Simulators](https://www.lesswrong.com/posts/vJFdjigzmcXMhNTsx/simulators) — the classic "LLMs aren't agents, they simulate agents" essay.
- [Shard Theory: An Overview](https://www.lesswrong.com/posts/xqkGmfikqapbJ2YMj/shard-theory-an-overview) — values as contextual shards rather than a utility function.

**P(misalignment)**
- [Alignment remains a hard, unsolved problem](https://www.lesswrong.com/posts/epjuxGnSPof3GnMSL/alignment-remains-a-hard-unsolved-problem#sdJmymE7whfkemDE8)
- [Without specific countermeasures, the easiest path to transformative AI likely leads to AI takeover](https://www.lesswrong.com/posts/pRkFkzwKZ2zfa3R6H/without-specific-countermeasures-the-easiest-path-to) (1 hr) — Cotra's influential "human feedback on diverse tasks" argument.
- [Foom & Doom 2: Technical alignment is hard](https://www.lesswrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard#oyooNPzNDt4JEjdCo)
- [6 reasons why "alignment-is-hard" discourse seems alien to human intuitions, and vice-versa](https://www.lesswrong.com/posts/d4HNRdw6z7Xqbnu5E/6-reasons-why-alignment-is-hard-discourse-seems-alien-to#yq4yrC4rkYT9gDdGx)
- [How human-like do safe AI motivations need to be?](https://www.lesswrong.com/posts/r8H4d3X7AKg9n8TQk/how-human-like-do-safe-ai-motivations-need-to-be)
- [Will AI systems drift into misalignment?](https://blog.redwoodresearch.org/p/will-ai-systems-drift-into-misalignment)

**P(scheming)**
- [How training-gamers might function (and win)](https://www.lesswrong.com/posts/ntDA4Q7BaYhWPgzuq/reward-seekers)
- [How likely is deceptive alignment?](https://www.alignmentforum.org/posts/A9NxPTwbw6r6Awuwt/how-likely-is-deceptive-alignment)
- [Training-time schemers vs behavioral schemers](https://www.lesswrong.com/posts/m5nWc9v6MTsWXKpCy/training-time-schemers-vs-behavioral-schemers)
- [Many arguments for AI x-risk are wrong](https://www.lesswrong.com/posts/yQSmcfN4kA7rATHGK/many-arguments-for-ai-x-risk-are-wrong) — the section rebutting the counting argument; the strongest published pushback.

**P(doom | misalignment)**
- [Risk reports need to address deployment-time spread of misalignment](https://blog.redwoodresearch.org/p/risk-reports-need-to-address-deployment?utm_source=publication-search) (30 min)
- [Behavioral red-teaming is unlikely to produce clear, strong evidence that models aren't scheming](https://blog.redwoodresearch.org/p/behavioral-red-teaming-is-unlikely)
- [When does training a model change its goals?](https://blog.redwoodresearch.org/p/when-does-training-a-model-change)
- [Sleeper agents paper](https://arxiv.org/abs/2401.05566) and the [alignment faking paper](https://arxiv.org/abs/2412.14093) ([interview](https://youtu.be/9eXV64O2Xp8)) — the two canonical empirical demonstrations.

**P(doom)**
- [Why I'm not afraid of superintelligent AI taking over the world](https://www.understandingai.org/p/why-im-not-afraid-of-superintelligent) — a clear skeptical case worth steelmanning.
- [AI as Normal Technology](https://knightcolumbia.org/content/ai-as-normal-technology) — the most influential "this is all overblown" essay.
- [The Problem](https://www.lesswrong.com/posts/kgb58RL88YChkkBNf/the-problem) — the doomer case, compressed.
- [List of p(doom) values](https://pauseai.info/pdoom) — who believes what.
- [Shallow review of technical AI safety, 2025](https://www.lesswrong.com/posts/Wti4Wr7Cf5ma3FGWa/shallow-review-of-technical-ai-safety-2025-2) (1 hr, skim) — the field map.

#### Chat
instructions::
The user is browsing optional readings on misaligned AI takeover threat modeling. Help them choose: want empirical evidence → the papers group; want conceptual frames → basic frames group; want probability arguments → the P(misalignment)/P(scheming)/P(doom) groups; want skeptical takes → AI as Normal Technology, Why I'm not afraid. Discuss content with them if they've read any.
++}