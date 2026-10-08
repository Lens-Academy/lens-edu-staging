---
id: '6fd8eceb-37c6-4371-ac0d-32989fd6d14a'
title: "E.2.2 Introduction to steganography and the Stego Game"
tldr: "What steganography is, its parts (sender, receiver, channel, cover distribution, warden), the group Stego Game, the PRF idea for LLM steganography, and why it matters for AI safety."
summary_for_tutor: "Section 4 of Iliad worksheet E.2: the setup of steganography (encoder and decoder with a shared key, channel, innocent distribution, message space, correctness, adversary or warden, security condition), the Stego Game with its phases and modes, perfect versus computational steganography with the 2^lambda key-search bound, the PRF-based scheme for LLMs (dynamic error correction, response prefix r, symbols 0, 1 and backspace), and relevance to chain-of-thought hiding, collusion and weight exfiltration."
authors:
  - Stephan Wäldchen (Independent)
  - Louis Jaburi (EleutherAI)
source_url: https://iliad-intensive.org/safety/steganography/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 4. Main Content

:::callout {title="Note" tone="blue"}

This content section largely focuses on the steganography component of this module. For the content on backdoors, see "Learn more" and the teaching guide that outlines how this material was taught in-person.

:::

Read the description here for an intuitive idea, and for mathematical details and the exercises read the corresponding pdf files.

\### 4.1 Introduction to steganography

Steganography is the art and science of hidden communication. Unlike cryptography, which protects the content of a message by making it unreadable to outsiders, steganography seeks to conceal the very existence of the message itself. A secret note may be embedded in an innocent-looking image, a line of text, a sound file, or even a network protocol, so that an observer sees only ordinary communication. At its core, steganography asks a subtle question: how can information be transmitted without revealing that communication is taking place at all?

A steganographic setup typically consists of:

- **A sender and a receiver**, often called the encoder and decoder, who share a secret key.
- **A communication channel**, through which messages are transmitted.
- **A distribution of innocent messages**, describing what ordinary communication over the channel looks like.
- **A message space**, containing the secret messages that the sender may wish to transmit.
- **An encoding procedure**, which embeds a secret message into an apparently innocent message.
- **A decoding procedure**, which recovers the secret message from the received communication.
- **A correctness condition**, requiring that decoding succeeds with high probability.
- **An adversary**, or warden, who observes the communication and tries to distinguish ordinary messages from steganographic ones.
- **A security condition**, requiring that the adversary's distinguishing advantage is small.

\### 4.2 The Stego Game

We start the day with a little game that practically explores the ideas of steganography. We need: at least 4 students, 2 rooms, pen, paper and a blackboard.

1. Strategy Phase:

- Two teams, each consisting of an **Encoder group** and a **Decoder group**
- Separate both teams from each other to discuss their stego-strategy
- One facilitator goes with either team in a separate room

2. Task Phase

- Gather all of them in the main room and explain the task

2. Encoder Phase:

- The encoder groups leave the room, the decoders stay in the main room
- The encoder groups each draw a word from the list
- The channel team asks an open-ended question, e.g. "How is the weather in London?"
- The encoder groups write their answer on a piece of paper (max 30 words)

4. Decoder Phase

- The channel group writes the stego-text of team 1 onto the blackboard
- The encoder group 1 has 1 minute to decode it

5. Adversary Phase

- The team 2 has 5 minutes to guess the word
- Team 1 wins if they successfully decoded the word and team 2 made a wrong guess

**Subsequent modes:**

- The list of words isn't known beforehand
- The channel team paraphrases the message

| **Time** | **Strategy** | **Encoding** | **Decoding** | **Adversary** |
| --- | --- | --- | --- | --- |
| Mode 1 | 15 min | 5 min | 3 min | 3 min |
| Mode 2 | 15 min | 5 min | 3 min | 3 min |
| Mode 3 | 15 min | 5 min | 3 min | 3 min |

\### 4.3 Perfect Steganography vs Computational Steganography

Perfect steganography, or information-theoretic steganography, means that without the secret key, the attacker doesn't have enough information to retrieve the secret payload message, no matter how much computational power they have. We included here a short proof of the entropy of the message being lower-bounded by the entropy of the key. This explains why perfect security would be cumbersome in practice, as it needs the key length to scale linearly with message length.

A short shared key cannot give unbounded perfect IT indistinguishability, so one typically settles for **computational indistinguishability**. Under standard cryptographic assumptions such as the existence of **one-way functions** (hence Pseudo-Random Functions), any **efficient** attacker cannot distinguish the stego-text from the innocent one except with negligible advantage. This does **not** protect against an attacker with unlimited computation, but the generic attack is exhaustive search over the key space, so the effort is at most about $$2^{\lambda}$$, and security aims to be of that order.

\### 4.4 A practical strategy for Steganography with LLMs

**Core Idea**: At every generation step, a language model produces a probability distribution over the next token. For example: cat: 0.5, dog: 0.3, fox: 0.2. Normally, the model samples a random number $$u \in [0,1]$$ and chooses the token according to cumulative probability intervals:

- cat if $$u < 0.5$$
- dog if $$0.5 \leq u < 0.8$$
- fox if $$0.8 \leq u < 1$$

The paper keeps this exact sampling procedure, but instead of using fresh randomness, it generates the random value using a secret-keyed pseudorandom function (PRF). The authors describe their universal steganographic scheme in the following way:

1. **Sample exactly like the original LLM**. At each step, the LLM gives a next-token distribution. The scheme draws a uniform value from a secret-keyed PRF and uses it to sample from that distribution. Since the value is uniform-looking, the token distribution is unchanged.
2. **Make the PRF depend on the hidden symbol**. To transmit a code symbol $$\sigma \in \{\texttt{0},\texttt{1},\leftarrow\}$$, the generator uses randomness like $$F_{k}(r,i,\sigma)$$ where $$k$$ is the secret key, $$i$$ is the token position, and $$r$$ is a response-specific random prefix. Generate tokens while "pushing" one symbol. For several consecutive tokens, the generator samples using the PRF stream corresponding to the current symbol $$\sigma$$. The visible text still follows the normal LLM distribution.
3. **Decoder scores all candidate symbols.** The decoder knows $$k$$, so for the observed tokens it computes scores for each candidate symbol: $$\sigma = \texttt{0},\texttt{1},\leftarrow$$ The correct symbol's score tends to grow faster. Once one score crosses a threshold, the decoder records that symbol and resets the scores.
4. Use dynamic error correction. Because the decoder can occasionally pick the wrong symbol, the hidden payload is first encoded with a dynamic error-correcting code over $$\{\texttt{0},\texttt{1},\leftarrow\}$$. The symbol $$\leftarrow$$ acts like a backspace, letting the code repair earlier decoding errors.
5. **Repeat until the response ends.** The generated response contains as many hidden code symbols as its length and entropy allow. Longer, higher-entropy responses carry more payload.
6. **Avoid reuse across many queries.** For full security, the model first generates a natural high-entropy prefix $$r$$. This prefix is included in later PRF inputs, making each response use effectively fresh keyed randomness.

\### 4.5 Relevance for AI Safety

- Chain-of-Thought monitoring is, at the moment, the only really practical approach to find out how LLMs reason. Using steganography, models can however hide what they are thinking from monitors. This can arise naturally and quickly, as soon as there is any optimisation pressure on the COT to censor certain thoughts: [Models can hide COT with steganography](https://arxiv.org/html/2506.01926v2)
- Models can collude with each other for nefarious purposes and scheme without human overseers noticing. [Steganography can arise and not easily prevented by paraphrasing](https://arxiv.org/pdf/2410.03768)
- Crucial information could be smuggled out of frontier labs, such as model weights ([Model weight extractions](https://arxiv.org/pdf/2511.02620)) which allows either bad actors to run strong models, the model to proliferate copies of itself to run independently.
