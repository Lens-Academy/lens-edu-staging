---
title: "Aren't AIs only able to parrot back what humans say?"
source_url: https://ifanyonebuildsit.com/2/arent-ais-only-able-to-parrot-back-what-humans-say
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
#### To predict the next token well, LLMs need to learn how the world works.

Suppose that a doctor is writing up a report of what happened to a medical patient. A segment of the medical report reads:

> On day three of admission, the patient developed acute confusion and tremors. Serum ammonia levels were found to be…

Imagine an AI being trained on this data that is asked to predict the next word, with two plausible candidates being "elevated" or "normal." This is not just about predicting the sort of words that humans use; it's about predicting what happened in the world of medical reality, biology, and events inside the patient. How much ammonia was there to be measured, in real life?

The AI predicting the next word here has a harder task than the human who wrote down the report. The human report-writer is just writing down what was actually observed. The AI report-predictor has to guess it in advance.

The AI assigns 70 percent probability to "elevated," 20 percent to "normal," and 10 percent spread across a range of other words.

The actual next word of the report is "normal."

Everything inside the AI that thought it was going to be "elevated" loses a little force, within the AI's understanding of medicine. Every parameter gets adjusted a tiny, tiny bit in the direction of making the medical understanding that predicted "normal" be more dominant.

Until, after enough training, the AI performs [certain medical](https://pubmed.ncbi.nlm.nih.gov/38976865/) diagnoses better than most doctors do.

The AI is not being trained to *write down gibberish that sounds like a typical medical report.* It is being trained to *predict the exact next word in all particular medical reports it sees.*

Maybe if you started with a very small model with too few parameters, it could only ever learn to write medical-tinged gibberish — but with larger models, that does not seem to be what is happening on benchmarks comparing human doctors with AIs.

When somebody slings an arm around your shoulder and tells you in a tone of great wisdom that an AI is really "just a stochastic parrot," they might be imagining the fun old computer programs that would extend out sentences based on word-cluster ("n-gram") frequencies — "On past occasions where we've seen these two words appear inside the corpus, what has the next word usually been?"

Systems that guess the next word, based on the last two or three words, are trivial and existed long before LLMs. They do not challenge humans in the ability to predict medical cases. They don't *sound like* people talking to you. If you could pick up [billions of dollars](https://www.reuters.com/business/openai-hits-12-billion-annualized-revenue-information-reports-2025-07-31/) of revenue just by doing the probabilistic-parrot thing, people would have done it a whole lot earlier!

If the billions of calculations inside a real LLM weren't doing any heavy lifting, if the system just spewed out a surface guess based on surface features of previous words, then it would sound like past systems that actually did spew out surface guesses. For example, trained on Jane Austen, an n-gram system outputs:

> 'You are uniformly charming!' cried he, with a smile of associating and now and then I bowed and they perceived a chaise and four to wish for

An LLM, asked to produce a sentence in Jane Austen's style, is dramatically more convincing; if you don't believe us, try asking one.

Also, while we cannot tell a *lot* about what happens inside an AI's mind, the AI company Anthropic did publish research saying that their AI (Claude) was planning more than just one word ahead. That is, Claude was considering what later sentences and meanings might be plausible, in order to guess what next few letters might be seen.

#### AIs can already surpass their training data, or forego human data.

In 2016, an AI called AlphaGo created by Google DeepMind beat the human world champion at the board game Go. It was trained on a huge library of human Go games, and also learned from playing many games against itself.

The fact that it was able to beat humans suggests that it was able to learn general strategies from its training, and that it successfully modeled deep patterns in its training data, including (perhaps) deep patterns that humans had not yet noticed. Gradient descent reinforces whatever works, regardless of its provenance.

But AlphaGo's dominance was technically only *suggestive* of the fact that AIs can far exceed their training data. People could still object that perhaps AlphaGo was only copying humans, and managing to win by being more *consistent at applying* human-level skills, rather than by using any new patterns that humans would find novel or insightful.

This wouldn't square very well with the case of computer chess (where human chessmasters learn many strategies and insights from the computer chess engines that vastly outstrip them). But in the wake of AlphaGo, there were people who argued that the AI only beat Lee Sedol because it was trained on vast amounts of human data.

The folks at DeepMind apparently saw those objections too. Over the next year and a half, they built an AI called AlphaGo Zero, released in 2017. It was not trained on any human data at all. It learned the game entirely by self-play. It surpassed the top human players after only three days.

You could still object that Go is quite a bit simpler than the real world, and that it's much easier to figure out Go from scratch than it is to figure out (say) science and physics and engineering from scratch. And that's true! But it's also not quite what the naysayers were saying *before* computers got good at Go.

Back in 1997 — nineteen years before AlphaGo won — people were predicting that it would take a hundred years for computers to play superhuman Go. So we at least know that many people have poor intuitions about this sort of thing.

The real world is a more complicated environment than Go. The cognitive patterns underlying engineering, physics, manufacturing, logistics, etc. are more complex than the cognitive patterns underlying skilled Go play. But there's no theoretical basis for the idea that, once AIs can learn those patterns at all, they'll be limited to the human variants. Gradient descent will reinforce the parts of the AI that find cognitive patterns that *work really well,* regardless of their provenance.

None of this is an argument that LLMs in particular will learn those patterns to the point where they can automate scientific and technological progress. We don't know whether they can or can't. The point is that "just" training them on human text is not any sort of fundamental limitation. They're trained only on human data, yes, but don't let that blind you to the sparks of generality and hints of deep reasoning buried within the giant pile of shallow "instincts."

We'll have more to say, in Chapter 3, about how an AI might generalize from a narrow set of examples to a more general capacity.

#### Notes

[1] *n-gram system:* This example is taken from Jurafsky & Martin's *[Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/3.pdf)**,* 3rd Edition.

[2] *more than just one word ahead:* See the [Anthropic blog](https://www.anthropic.com/research/tracing-thoughts-language-model#does-claude-plan-its-rhymes) for details.

[3] *people who argued:* For instance, Yann LeCun argued in the wake of AlphaGo's victory over Lee Sedol that AlphaGo was "[not true artificial intelligence](https://www.information-age.com/google-deepminds-alphago-victory-not-true-ai-says-facebooks-ai-chief-1116/)" because it relied on supervised learning.

[4] *only three days:* Figure 1, p. 4 of the [AlphaZero preprint](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/alphazero-shedding-new-light-on-chess-shogi-and-go/alphazero_preprint.pdf): "20 blocks over 3 days."

[5] *a hundred years:* One such prediction was made by George Johnson [in the](https://www.nytimes.com/1997/07/29/science/to-test-a-powerful-computer-play-an-ancient-game.html) *[New York Times](https://www.nytimes.com/1997/07/29/science/to-test-a-powerful-computer-play-an-ancient-game.html)*.