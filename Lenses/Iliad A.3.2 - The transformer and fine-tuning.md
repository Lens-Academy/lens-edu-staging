---
id: 'b0e2bec1-2fe5-402f-a545-c51c7e3ddbd5'
title: "A.3.2 The transformer and fine-tuning"
tldr: "How a transformer works and is trained: one-hot tokens, embedding, causal attention, unembedding, the next-token loss, gradient descent, and fine-tuning on question-answer data."
summary_for_tutor: "Lecture notes of worksheet A.3, first part. Blocks with weights w, one-hot encoding with vocabulary size V, embedding to R^d, causal attention, unembedding to a probability distribution, next-token negative log-loss L(w), the update w' = w - epsilon * grad L(w), and text generation by sampling. Then fine-tuning on question, scratchpad and answer data, distillation. Keep the notation L(w), p_w, epsilon, V, d."
authors:
  - Garrett Baker
source_url: https://iliad-intensive.org/alignment/alignment-in-practice-ii/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Lecture notes

Before I can teach you anything about how alignment works in practice I need to teach you about how AI training works, and even really what current AIs even *are*. 

I will assume you all have basically already learned what a transformer is, and in particular what attention is, from the mechanistic interpretability day, but perhaps you haven't, and in either case, here is the basic picture you need to have in your head:

An AI model has as its basic unit a series of "blocks". These blocks are just functions, which take in an input $$x$$ and have associated with them a vector of *weights* $$w$$. $$w$$ determines the particular behavior of the function that is the block on the input $$x$$.

You should have in your head this picture

![Drawing 2026-07-30 11.35.23](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-a3-drawing-2026-07-30-258e255c.png)

where block $$i$$ is also known as layer $$i$$, and has associated with it the weights $$w_i$$.

For LLMs the input is just a series of "tokens", which you should for now just think of as words. For instance, "My dog ate my" would turn into the input
$$
\texttt{Input}=\begin{bmatrix}
\texttt{My}\\
\texttt{\_dog}\\
\texttt{\_ate}\\
\texttt{\_my}
\end{bmatrix}
$$
But of course our LLM is just a bunch of functions, so unable to read words yet, that's what we're trying to teach it to do. However one thing functions are good at reading are numbers! So we want a simple way to turn this `Input` into a sequence of numbers!

The simplest method is what is called a "one-hot" encoding of each word (in practice people usually use word *pieces* instead of whole words, but for our purposes that is not conceptually important right now). This means we take every word in the dictionary, and label them $$1, \dots, V$$ where $$V$$ is the number of words in our dictionary--our vocabulary size. Then we replace each word in `Input` with the vector $$[0, \dots, 0, 1, 0, \dots, 0]$$ where if the word in $$x_0$$ is in the $$i$$th place in our list of all words in the dictionary, then every element of our new vector is zero except for a single 1 in the $$i$$th entry of our $$V$$-tuple.

Suppose $$V = 6$$, and our word list is:
```
"My", "_ate", "_dog", "_homework", "_my", "_zebra"
```

Then our `Input` would be represented as
$$
\begin{bmatrix}
\texttt{My}\\
\texttt{\_dog}\\
\texttt{\_ate}\\
\texttt{\_my}
\end{bmatrix} \mapsto \begin{bmatrix}
1 & 0 & 0 & 0 & 0 & 0\\
0 & 0 & 1 & 0 & 0 & 0\\
0 & 1 & 0 & 0 & 0 & 0\\
0 & 0 & 0 & 0 & 1 & 0\\
\end{bmatrix}
$$
This is what we give to block 1, what is usually called the "embedding block". This "embeds" each row of the above matrix. That is, it transforms each one-hot vector into a smaller vector which we will call $$x_1^t \in \mathbb R^d$$, with $$d < V$$, and $$t$$ corresponding to the $$t$$th row of the new matrix. 

Conceptually, the embedding matrix encodes the *meaning* of the words, so that words which mean similar things get mapped to similar vectors as each other 

$$
\begin{bmatrix}
\texttt{My}\\
\texttt{\_dog}\\
\texttt{\_ate}\\
\texttt{\_my}
\end{bmatrix} \mapsto^\text{tokenization} \begin{bmatrix}
1 & 0 & 0 & 0 & 0 & 0\\
0 & 0 & 1 & 0 & 0 & 0\\
0 & 1 & 0 & 0 & 0 & 0\\
0 & 0 & 0 & 0 & 1 & 0\\
\end{bmatrix} \mapsto^\text{embedding}
\begin{bmatrix}
1 & 0 & 0\\
0 & 0.05 & 0.95\\
0.20 & 0.20 & 0.60\\
0.90 & 0.1 & 0\\
\end{bmatrix}
$$
Here note that `My` and `_my` are fairly close to each other while being distant from `_dog` and `_ate`, with `_dog` and `_ate` also being distant from each other. One can imagine that `_zebra` might be close to `_dog`, them both being different types of animals, and likewise `_homework` may also be close to `_dog`, them both being nouns.

Note also that each row is normalized, so that it sums to 1. Often such constraints are enforced to ensure that as each block is applied no values end up blowing up.

Next we have a transformer block. You should picture this inside your head for this

![iliad transformer block](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-a3-transformer-block-2ba5719a.png)

That is to say, the transformer block for word $$t$$ gets to read information from any word coming before $$t$$ including $$t$$ itself. This should make sense, when someone is speaking to you, you don't get information about the end of their sentence until you actually get to the end of their sentence, but you always have information from the beginning of their sentence. This is called having "causal attention".

%% CLAUDE REVIEW: "That's why it's called a transformer" — the name is from the architecture (Vaswani et al. 2017, "Attention Is All You Need"), not from the blocks repeating. Left as written. %%

The next however-many blocks in our transformer are just repeats of these transformer blocks. That's why it's called a transformer! And it's called *deep* learning because usually by just adding more transformer blocks--that is, making the model *deeper*--the model gets better at its task: predicting the next token.

![iliad transformer block 2](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-a3-transformer-block-2-be5c570d.png)

Before it can do that though, we need to turn the random numbers it's spitting out into words, because while the transformer can read numbers perfectly fine, we do ultimately want this thing to talk!

This is simple, we just have an "unembedding" block, which takes each vector $$x_L^t\in \mathbb R^d$$ and turns it into a vector in $$\mathbb R^V$$, constrained so that each entry is positive, and sums to 1. That is, a probability distribution! By interpreting the $$i$$th entry in $$x_L^t$$ as the "probability the transformer assigns to the $$i$$th word in the word list" we now have a probability distribution over all the words in our vocabulary!

In the ideal case, we want the model's output to look like this:

![iliad transformer full](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-a3-transformer-full-7b37e3c5.png)

supposing the true sentence was "My dog ate my homework".

that is to say, each output position $$i$$ has a corresponding input position $$i$$, and we want the transformer at output position $$i$$ to be trying to predict the next input position. That is we want it to be trying to predict input position $$i+1$$. 

Note that this along with "causal attention" means we are able to truncate the transformer's position at any point in the input, and get what the transformer *would've predicted* had it not had access to any future information.

![iliad transformer truncate](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-a3-transformer-truncate-20a6a787.png)

in this way we can see and more importantly grade the transformer's output for 4 different tasks at once! 

Of course, if we have just coded up this transformer, with some random weights $$w_i$$, we have no guarantee that the transformer actually predicts text well. Its output will just look like a random mess. Even the embeddings will be a random mess. We do constrain a few things, like each transformer block output being normalized, and the "causal attention" flow of information between different transformer blocks.

The fix is simple, we give the transformer a bunch of strings of text like "My dog ate my homework", "the quick brown fox jumped over the lazy dog", "We hold these truths to be self evident...", and so on, which we get by scraping a bunch of websites off the internet. We call this collection of texts our dataset $$\mathcal D$$, then compare the transformer's outputs with the ground truth of those texts, and write down a "loss function" which is minimized when the probability a transformer assigns to a text is its "true" probability of being drawn from the dataset $$\mathcal D$$. Usually this is what is called "negative log-loss", where
$$
L(w) = -\,\mathbb{E}_{s \in \mathcal D}\left[\frac{1}{T}\sum_{t=1}^{T-1}\log p_w\!\left(s_{t+1}\mid s_{1:t}\right)\right]
$$
where each $$s \in \mathcal D$$ is a list of words, like ("My", " dog", " ate", " my", " homework"), and $$p_w(s_{t+1}|s_{1:t})$$ is the probability our model using weights $$w$$ assigns to the string $$s_{t+1}$$ given $$s_{1:t}$$.

Then, since this is a function of our weights $$w$$, and since we have used only differentiable functions of our weights $$w$$ for our transformer blocks (which we have), we can find $$\nabla_w L$$, and use this to update our weights like so
$$
w' \gets w - \varepsilon \nabla_wL
$$
where $$\varepsilon > 0$$ is what is called our "learning rate". It is typically small, usually around $$\varepsilon \approx 10^{-4}$$ so that we can reasonably expect this update to get us new weights $$w'$$ which *decrease* our loss function $$L$$. 

We then repeatedly apply this process, we take the new model, parameterized by $$w'$$, evaluate $$L(w')$$, calculate $$\nabla_w L$$ again and again and again and again and again. In the big labs this is done for months, and because of the number of updates, the number of datapoints, and the size of the transformer they're updating, they need really big and really fast datacenters to do this efficiently.

The magic of deep learning is that this is basically enough to get a language model which can predict text found on the internet *really really well*. 

But this is *not* enough to get a model which answers questions really really well! This is enough to get it so that the model's probability distribution for the next token is accurate, and that's about it. 

This is notably not a text generator *yet*, but it's pretty easy to get it there. You give the model a seed, like "My dog ate my", get the probability distribution it assigns to the next token, then sample from that, append it to the input, and run the model again. 

That is, suppose we run "My dog ate my" through the transformer, and then sample " homework". The next thing we put into the transformer is "My dog ate my homework", then sample from the next token distribution, and suppose we get " because". Then we run "My dog ate my homework because", etc etc. 

So now we have a text generator, but we are still a far cry from something that answers *questions* really well. This is no ChatGPT!

\### Fine-tuning
To turn this transformer into something which answers questions, we apply yet another round of updates to our model. We use the same loss function 
$$
L(w) = -\,\mathbb{E}_{s\in \mathcal{D}}\left[\frac{1}{T}\sum_{t=1}^{T-1}\log p_w\!\left(s_{t+1}\mid s_{1:t}\right)\right]
$$
and the same update rule
$$
w' \gets w - \varepsilon \nabla_wL
$$
but we change the dataset we evaluate this loss function with respect to. 

Recall previously the dataset we used was selected from randomly scraping a bunch of texts on the internet. We did this because randomly scraping the internet gives the model a very broad selection of information which it ends up learning, and compared to other methods is also very cheap to construct. Just run a bunch of webscrapers or buy a bunch of books.

Now, to teach the model how to answer questions well, we use a dataset made of a bunch of hypothetical conversations between an AI assistant and a human, where the human is asking questions and the AI is first given a "scratchpad" (also called a chain of thought) to think about the answer to the question, then actually answers the question.

This "scratchpad" is pretty important, and does increase the accuracy of the model's responses. This should make sense! If the model is forced to just immediately output the answer, then its "thinking time" is constrained by the number of transformer blocks we've stacked, and partially by the length of the question. If we give it a scratchpad, it can automatically increase the amount of time it spends thinking.

The information in the scratchpad is also useful! 

These question answer pairs are, depending on the amount of money which the AI lab has (or is willing to spend on this project), either sourced from a different, possibly smarter, AI, which is often called "distillation", or from individual humans writing questions and corresponding example chain of thoughts and answers.

This is why you may hear in the news about "distillation-attacks", where say a Chinese AI lab will collect a bunch of (question, chain of thought, answer) pairs from an American AI lab's AI API, and use those tuples to train their own AIs. (You can imagine the American AI labs really dislike this! They put a lot of effort into hiring PhDs to get those good answers, and the Chinese AI lab is just piggybacking off their hard effort)

This is also why you may know of some of your PhD friends who got hired to answer questions for AI labs. Their answers are useful as models for how the AI should think about and answer complex questions, though note that often such people are *grading* pre-generated replies by AIs for accuracy, which is used in the next phase of training--RLHF and Constitutional AI.
