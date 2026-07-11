---
title: "A Full Description of an LLM"
source_url: https://ifanyonebuildsit.com/2/a-full-description-of-an-llm
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770833370}@@
  - IABIED--}
---
#### How Llama 3.1 405B Works

In the book, we promised a fuller description of an LLM called Llama 3.1 405B. We present that description below. It's here for the curious, and for the purpose of really understanding the degree to which modern AIs are grown rather than crafted. (See also: [What good does knowledge of LLMs do?](/2/what-good-does-knowledge-of-llms-do))

The discussion below is moderately detailed, and we'll assume (here, but not in most of the rest of the online resources) that you have some technical background, though we won't assume any specialized knowledge of AI. If you start reading this section and aren't finding it valuable, consider skipping it.

Details about how the most capable language models are trained are not typically published, nor is the code. But there are exceptions. One of the more powerful systems to have its architecture and weights publicly released, at the time of our drafting the book in late 2024, was Llama 3.1 405B, made by Meta's AI division. The "405B" stands for the 405 billion parameters in the architecture, filled by 405 billion weights.

Why are we walking through this particular AI model? Llama 3.1 405B is "open-weights,"[\*](#ftnt68) meaning that you can download those 405 billion inscrutable numbers yourself (along with the vastly tinier human-written skeleton of code that does arithmetic to the 405 billion numbers and thereby runs the AI). This lets us make statements about its design with some confidence.[†](#ftnt69)

Anyway! Let's talk about how those 405 billion inscrutable numbers are arranged — the way they were set up, even before training, such that Meta's engineers correctly expected that tweaking those random initial numbers in the direction of better predicting the next token (word-fragment), given training on over 15.6 trillion tokens, would create an AI that could talk.

The first step is breaking up all the words in all supported languages into tokens.

The next step is turning each of these tokens into a "vector" of numbers. Llama uses vectors of 16,384 numbers per standard dictionary token. It has 128,256 tokens in its vocabulary.

To turn each token into a vector, every possible token is assigned a weight for every possible position in the vector. So that's where we get our first chunk of billions of parameters:

Two billion parameters down. Four hundred and three billion left to go!

Just to say it again — no human tells Llama what any of the tokens mean, invents the vector of 16,384 numbers that a word translates to, or knows what the vector of numbers means for any word. All of those two billion parameters got there by gradient descent. The numbers get tweaked, along with other parameters we'll introduce, to increase the probability assigned to the true next token.[‡](#ftnt70)

Let's say Llama starts out looking at a block of 1,000 words, like a snippet of an essay. (Or rather, 1,000 tokens. But from here on out, for simplicity, we'll sometimes just say "words.")

For each of those words, we look up that word in the LLM's dictionary and load its list of 16,384 inscrutable numbers into memory. (Initially, those numbers were set randomly, at the dawn of training; then they were tweaked by gradient descent.)

1,000 words × (16,384 numbers / word) = 16,384,000 numbers total. We call these the "activations" in the first "layer" of Llama's computations (i.e., its cognition, its mental activity).

You can imagine them as being arranged into a flat rectangle on the floor that's 1,000 numbers across (the length of the input) by 16,384 numbers wide (numbers per word in the first layer). Here's one such vector, with the color of each pixel corresponding to the number in the vector:

(They're not the most scrutable artifacts.)

Also note that there are two different numbers here that shouldn't be confused:

- The number of *parameters that determine the behavior of this layer* (i.e., the 2,101,248,000 numbers stored in the dictionary)
- The number of *activations* or *numbers used in thinking* in the first layer when you input a thousand words (That's 16,384,000 numbers for the first step in processing a 1,000-word query.)

Now we have our huge matrix of numbers representing our query in all its glory, and we can begin to actually use it.

First up is something called "[normalization](https://en.wikipedia.org/wiki/Normalization_(machine_learning))," which happens many times over the course of an LLM's processing. This is similar to normalization in statistics, but with a machine learning twist. That twist is that after normalizing the data within each *row*, a specific learned parameter called "scale" is multiplied by each *column*. These scale numbers, like all the other parameters we'll discuss, are learned in training. Also, layer normalization happens dozens of times, and each time has a *new* batch of scale parameters, so normalization accounts for lots and lots of parameters over the course of the LLM. Specifically, 16,384 parameters per normalization. (If you're curious about the type of normalization Llama 3.1 405B uses in more detail, it's called RMSNorm.)

You might be thinking, "Wow, there's sure a lot of preprocessing," and indeed, you'd be right. In fact, we've glossed over some of the finer points, so there's even more than it might seem, and we're only just now getting to LLMs' most distinctive feature: the "attention" layer.

"Attention" is what that whole "transformer" fuss is about (if you've been around long enough to remember there being a fuss about the new invention of transformers). LLMs are a kind of "transformer"; transformers were introduced in a 2017 paper called "[Attention Is All You Need](https://arxiv.org/abs/1706.03762)." This paper, more than any other, is credited with the success of LLMs. An "attention" layer works like this:

We take each of the 1,000 vectors of 16,384 activations, and transform each vector of 16,384 activations:

- into 8 *keys*, each a vector of 128 activations
- into 8 *values,* each a vector of 128 activations
- and into 128 *queries,* each a vector of 128 activations

The "attention step" above each token consists of matching each of the 128 queries to the 8 keys — seeing which of the 8 keys most looks like or matches that query — and loading in a mixture of the 8 values, with the better-matching keys' values weighted more strongly in the mix.

What this allows, roughly, is for each of the activations above a token to create a bunch of "queries," which then look around at the "keys" above all other tokens. When a token's query matches a key more strongly, it retrieves the corresponding value more strongly, to pass on to later computations above that token.

For example, the word "right" might engage a query designed to look at neighboring words to see if any of them are around *spatial directions* or alternatively *belief,* to determine if the word "right" means right as in "right-handed" or right as in "right answer." (Again, all of that gets learned by gradient descent; none of it is programmed in by humans thinking about the different meanings the English word "right" can take.)[§](#ftnt71)

The attention layers in an LLM are quite large, with a huge number of parameters in each. Llama 3.1 405b in particular has 126 such attention layers (we've been describing just the very first of them), and each of the 126 has 570,425,344 parameters, divided between query, key, value, and output matrices.[¶](#ftnt72)

Once the attention sub-layer is complete, and we end up with a matrix of the same size as we started (in our example, 16,384 by 1,000), we do something called "residual connection." Basically, you take whatever the input for the sub-layer was (in this case, the huge matrix we started with) and add it to whatever we ended up with. This prevents any given sub-layer from changing *too* much on any given step (and has some other nice technical properties).

Next, the result is passed through what's called a "feed-forward network." The variant used by Llama 3.1 405B depends on an operation called "SwiGLU." SwiGLU was found by some researchers who tried training with many different variant formulas to see which ones worked best. As we've mentioned before, their [original paper](https://arxiv.org/pdf/2002.05202) said:

> We offer no explanation as to why these architectures seem to work; we attribute their success, as all else, to divine benevolence.

Like all feed-forward networks, SwiGLU basically acts to expand our 16,384-by-10,000 matrix into an even larger matrix, do some transformations to it, then compress it back down again. Specifically, each row goes from having 16,384 columns to 53,248 columns, then back to 16,384.

Now we're done with the feed-forward sub-layer, so we do residual connection again, adding whatever we started with to wherever we ended up.

It's been a long road, but we've now transformed our gigantic matrix very slightly.

Those steps together constitute a single "layer." Llama has 126 layers, so we'll repeat all these steps — normalization, the attention mechanism, residual connection, the feed-forward network, and residual connection again — 125 times.

At the end of the 126 layers, we end up with a matrix the same size as we started with; in our example, 16,384 by 1,000. Each row of this matrix can then be projected into a new vector of 128,256 numbers, one for each token in the model's full dictionary. These numbers can be positive or negative, but a handy function called softmaxing can be used to convert them all into probabilities, which sum to one. Those probabilities are Llama's prediction for what token will come next.

It's now possible to make Llama generate a new token. One way to do that is to take whichever token Llama gave the highest probability to, although you could also shake things up by occasionally taking tokens that it says are a little less likely.[‖](#ftnt73)

If you're running Llama normally, such as in a chatbot interface, this entire process has now output a single token. That token is put at the end of the input, and we repeat it all from scratch for the next token. So we'd do all the steps discussed before, except now our matrix has 1,001 rows. Then, another token later, 1,002, and so on.

We've glossed over plenty, but that is, basically, how Llama 3.1 405B works.

#### LLMs Are Large

Let's talk a bit about the sheer size of Llama 3.1 405B.

For Llama to get to grips with a text of 1,000 words (or rather 1,000 tokens), it takes about 810 trillion computations.[#](#ftnt74)

If 810 trillion seems like a lot, keep in mind that most of Llama's 405 billion parameters get used in *some* arithmetical operation *every* time *any* single word gets processed.[\*\*](#ftnt75)

If Llama is being *trained* on a batch of 1,000 tokens, then each of the 1,000 tokens will be compared against the following actual word, and the losses propagated by gradient descent, to determine how tweaking all 405 billion shared parameters would have changed the probabilities assigned to the true answers across all cases. This will take many more computations, and many more numbers.

In the course of training Llama's 405 billion parameters on 15.6 trillion tokens, it took somewhere in the ballpark of 38 septillion computations, meaning 38 followed by 24 zeros.

If instead Llama is done training and is being run in *inference mode* (i.e., if it is generating novel text, such as in a chat with a user)*,* the probabilities will only get computed above the very last token, as if predicting what the next word *would* be if the AI were reading text produced by humans.

Then, a human-written code skeleton surrounding Llama will pick what Llama thinks is the most likely answer.[††](#ftnt76)

And that is how to get a computer to start talking to you! Not quite as intelligently as the commercial AIs in 2025, but still talking sort of like a person.

To grapple with a thousand words, a Llama uses 405 billion inscrutable little parameters in 810 trillion computations — computations mathematically arranged into rectangles, cubes, and higher-dimensional shapes.

We sometimes call these arrangements "giant inscrutable matrices," because if you actually stare at some of Llama's parameters — even the simplest ones stored in the simple dictionary at the base of the vast stack of layers — the first few parameters for the word "right" look like this:

[-0.00089263916015625,     0.01092529296875,

  0.00102996826171875,    -0.004302978515625,

 -0.00830078125,          -0.0021820068359375,

 -0.005645751953125,      -0.002166748046875,

 -0.00141143798828125,    -0.00482177734375,

  0.005889892578125,       0.004119873046875,

 -0.007537841796875,      -0.00823974609375,

  0.00848388671875,       -0.000965118408203125,

 -0.00003123283386230469, -0.004608154296875,

  0.0087890625,           -0.0096435546875,

 -0.0048828125,           -0.00665283203125,

  0.0101318359375,         0.004852294921875,

 -0.0024871826171875,     -0.0126953125,

  0.006622314453125,       0.0101318359375,

 -0.01300048828125,       -0.006256103515625,

 -0.00537109375,           0.005859375,

…and on and on for 16,384 numbers. As for what these numbers *mean,* nobody on the face of the Earth presently knows.

I (Soares) timed myself reciting the first thirty-two numbers out loud to six significant digits. It took me two minutes and four seconds. To recite all the parameters for the word "right," even with that abbreviation, would take me more than seventeen hours. At the end of reciting them, I would be no wiser than before about what the word "right" means to Llama.

To recite all of Llama's parameters, speaking at 150 words per minute and never stopping to eat, drink, or sleep, would take a human 5,133 years. To recite all the activations corresponding to a thousand words in Llama's token dictionary would take seventy-six days straight. To write out all the calculations used to process a single token for a 1,000-word input would take, if you wrote a savant-like 150 calculations a minute without taking any breaks, over ten million years.

And that's just to generate one syllable! To write a whole sentence would take many times longer.

And if you personally did all of those calculations with your very own brain, at the end of the (at least) ten million years it would take you would be no wiser than before about what Llama had been thinking before it uttered its next word. You would know no more of Llama's thoughts than a neuron knows about a human brain.

In that imaginary world where you haven't long since died of old age, being able to carry out an individual local calculation doesn't mean your own brain knows anything about what Llama is thinking or how Llama is thinking it.

If you put all of Llama's 405 billion parameters into an Excel spreadsheet on an ordinary-sized computer screen, the spreadsheet would be the size of 6,250 American football fields, or 4,000 soccer fields, or half the size of Manhattan.

If you had one nickel for each computation in our 1,000 tokens example, you'd have 810 trillion nickels. If you tried to deposit them at the bank, you would need 203 million truckloads of nickels, each weighing 44,000 pounds.

Llama 3.1 405B is *not* yet roughly as large as a human brain. (A human brain has around 100 trillion synapses.)

405B can, however, apparently talk like a person.

And if anyone slings their arm around your shoulder and confides to you in a cynical tone that it's all really just numbers, please keep in mind that we are talking about *really rather a lot of numbers*.

A human neuron can be understood as "just" chemistry, if you study biochemistry and the chemicals binding to chemicals that make the little flashes of electrical depolarization travel around a human brain. But it's *a**lot* of chemistry. And it turns out that very simple things, in large enough quantities, arranged just so, can land rockets on the Moon.

A similar sort of caution applies to a large language model. The word "large" is not for show.

[\*](#ftnt68_ref) Some people refer to open-weight models as "open-source" models. This description does not seem quite right to us. Meta released the final weights, but did not release the exact computer program that *trained* Llama 3.1, or the huge collection of data Llama was trained on. So even if you were willing to spend millions of dollars to do it, you could not actually run the program that Meta ran to *grow* Llama 3.1. Meta didn't release the AI-growing code, only the grown and tuned AI.

Furthermore, even if Meta did release the data and the training program, we don't think that the resulting program would merit the label "open-source," which was traditionally reserved for computer programs that published ("opened") their human-readable "source code." Releasing the incomprehensible 1s and 0s (the "binary code," if you will) does not traditionally meet the requirements for a program to be considered "open source." But AIs are *just* inscrutable numbers; there is no human-comprehensible source to be released. So there's a sense in which modern AIs *can't* be open-sourced; no human-comprehensible source code exists. Any attempt to publish an AI is necessarily a radically different practice than open-sourcing traditional software.

[†](#ftnt69_ref) As we finish writing this in the summer of 2025, there are smarter open-weight systems with fewer parameters than Llama 3.1 405B, and even smarter open-weight systems with even more parameters. But when we began drafting the book, 405B was among the largest and smartest models with weights that had been irrevocably released into the wild and with an architecture and size that was exactly known. So that's what our book chapter promised to explain in the online supplement. Also, 405B is *simpler* than 2025-era open systems. We would not actually want to substitute a more recent LLM with only 77B parameters. The more modern "mixture of experts" system would be somewhat harder to explain.

[‡](#ftnt70_ref) Incidentally, it doesn't count toward total parameters, but the underlying architecture behind LLMs doesn't natively differentiate between words that come earlier and later, so a transformation involving trigonometric functions is done to the input to let the LLM figure out word order. If you want to read about it, the keyword is "positional encoding." The details don't matter too much for our purposes, though, so we won't go into that part.

[§](#ftnt71_ref) Using smaller vectors, here's how it might look to match one query against two key-and-value pairs. The keys and queries have to be the same size for it to work.

query: [-1, +1, -2]

key and value #a: [+1, +2, -1] and [0, 3, 1, 2]

key and value #b: [-2, +1, +1] and [2, -2, 0, 1]

We compare the query against a key by multiplying together the first elements of the vectors, the second elements, etc., and summing them up:

query X key #a = (-1 \* +1) + (+1 \* +2) + (-2 \* -1) = -1 + 2 + 2 = 3

query X key #b = (-1 \* -2) + (+1 \* +1) + (-2 \* + 1) = 2 + 1 + -2 = 1

We're now going to mix the values together and produce an average value weighted by the degree to which queries match keys. This weighted-average value is the answer to the query that gets passed on for further processing.

The strength of the raw match gets scaled exponentially to become this weight. For simplicity, let's use the powers of two. #a gets weight  #b gets weight  If we add them together, that's a total weight of

So now the answer to the query is  of value #a1 plus  of value #b:

(0.8 × [0, 3, 1, 2]) + (0.2 × [2, -2, 0, 1])

= [0.0, 2.4, 0.8, 1.6] + [0.4, −0.4, 0.0, 0.2]

= [0.4, 2.0, 0.8, 1.8]

(As a further detail on how this all works in 2024-era attention, the real, larger queries and keys will contain some preprogrammed position information — cues as to where in the list of 1,000 tokens any particular token falls, which are built into its corresponding queries and keys. Again, if you want to understand these details, the keyword is "positional encodings."

This allows a query to say, "Hey, I'd like to look at the word that's right next to me," or, "Hey, I'd like to look for words about birds within just the last ten words," in the language of numbers that get multiplied by other numbers and summed. Llama 3.1 405B in particular uses Rotary Positional Embeddings, which are slightly complicated and clever. So, sorry; if you want to know how RoPEs work, you're going to have to look it up.)

[¶](#ftnt72_ref) As another aside about the attention layer, Llama uses "causal masking," meaning that each token's queries can only look at the keys from *before* it. Basically, that's because each token is trying to ultimately predict what token comes next; looking ahead would be cheating!

[‖](#ftnt73_ref) The choice of how much randomness to use when picking a token is, roughly speaking, called the "temperature" at which the tokens are produced.

[#](#ftnt74_ref) Technically "floating point operations," the main kind of mathematical computation done by computers.

[\*\*](#ftnt75_ref) The exception to this rule is the 2.1-billion-parameter dictionary of 128,256 words; only 16,384 of those parameters get used per token. And more modern architectures for large LLMs try to only use a quarter or an eighth of their parameters to process each token; Llama 3.1 405B was one of the last large models not to try that.

[††](#ftnt76_ref) Or, for a little spice, the skeleton often has a chance of picking a word that Llama assigns a little less probability to.