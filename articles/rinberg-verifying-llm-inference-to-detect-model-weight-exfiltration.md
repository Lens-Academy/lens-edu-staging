---
title: "Verifying LLM Inference to Detect Model Weight Exfiltration"
author:
  - "Roy Rinberg"
  - "Adam Karvonen"
  - "Alexander Hoover"
  - "Daniel Reuter"
  - "Keri Warr"
source_url: "https://arxiv.org/abs/2511.02620"
published: 2025-11-04
created: 2026-07-28
accessed: 2026-07-28
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

###### Abstract

As large AI models become increasingly valuable assets, the risk of model weight exfiltration from inference servers grows accordingly. An attacker controlling an inference server may exfiltrate model weights by hiding them within ordinary model responses, a strategy known as steganography. This work investigates how to verify LLM model inference to defend against such attacks and, more broadly, to detect anomalous or buggy behavior during inference. We formalize model weight exfiltration as a security game, propose a verification framework that can provably mitigate steganographic exfiltration, and specify the trust assumptions associated with our scheme. To enable verification, we characterize valid sources of non-determinism in large language model inference and introduce two practical estimators for them. We evaluate our detection framework on several open-weight models ranging from 3B to 30B parameters. On MOE-Qwen-30B, our detector reduces exfiltratable information to $<0.5\%$ with false-positive rate of $<10^{-2}$, corresponding to a $>200\times$ slowdown for adversaries. Overall, this work further establishes a foundation for defending against model weight exfiltration and demonstrates that strong protection can be achieved with minimal additional cost to inference providers. Our code is made available at: [github.com/RoyRin/inference\_verification\_for\_model\_weight\_exfiltration](https://github.com/RoyRin/inference_verification_for_model_weight_exfiltration).

## 1 Introduction

As Large Language Models (LLMs) become increasingly valuable assets, the need for robust defenses to protect them grows in parallel. Inference servers are of particular concern as they host the model weights themselves, and a single compromised server can cause severe damage: either through the _exfiltration_ of proprietary weights or by returning _undesirable_ or manipulated outputs during inference.

Malicious adversaries can exploit many potential channels, from infiltrating development environments and stealing backups to abusing side channels. While conventional security mechanisms can mitigate some of these risks, defending the inference pipeline poses a unique challenge. To support normal operation, inference providers must allow vast volumes of data to flow in and out of their data centers, often hundreds of gigabytes per day \[[NLK+24](#bib.bib1 "Securing ai model weights: preventing theft and misuse of frontier models")\]. This open communication channel creates an unavoidable tension between accessibility and security.

For attackers, as the amount of user data increases, so does the attractiveness of exfiltrating information through user data through _steganography_, the practice of concealing information within seemingly innocuous data, such as embedding hidden payloads in generated text. In this work, we propose a scheme to _monitor inference traffic_ to detect potential exfiltration through steganography. Figure [1](#S1.F1 "Figure 1 ‣ 1 Introduction ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") depicts two contrasting scenarios: normal inference and compromised inference with exfiltration.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img1-49226c38.png]]

(a)

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img2-251ac045.png]]

(b)

Figure 1: Comparison of normal vs. compromised inference flows. If the inference server is compromised model weights can be exfiltrated via inference responses.

Our work rests on a simple but powerful observation: LLM inference traffic follows a well-defined generative process, and any steganographic attempt to encode hidden information must, by necessity, _deviate from expected model behavior_. The primary challenge is that LLMs naturally exhibit non-determinism; even identical runs of the same model and code can yield different outputs due to stochastic token prediction and floating-point variance. In this work, we provide methods for quantifying the likelihood of different tokens under this valid non-determinism, as a way to prevent model exfiltration.[^1]

In this work, we introduce two methods for estimating the likelihood that each generated token was honestly produced by the claimed model (Token-DiFR and Token-IPT-DiFR), which are concurrently developed by \[[KRR+25](#bib.bib40 "DiFR: inference verification despite nondeterminism")\]. This enables us to measure deviations from expected model behavior and derive _information-theoretic bounds_ on the amount of information that even a capable adversary could exfiltrate through normal inference traffic. We propose a detection scheme that can be integrated into larger model security systems.

##### Framing this Work in the Space of Preventing Model Weight Exfiltration

Beyond technical design, we offer a framework for reasoning about model-weight exfiltration from both security-engineering and economic perspectives. Intuitively, exfiltration attempts that move large amounts of data quickly are easier to detect and respond to, whereas extremely slow leaks may be economically irrelevant to either party. We highlight three regimes:

1.  1.
    
    Setting 1: Fast exfiltration: An extremely rapid leak that occur before human intervention is possible. For example, if an adversary compromises many endpoints and exfiltrates data from all of them simultaneously (e.g., 10,000 servers each leaking a 1/10,000th fraction of the weights).
    
2.  2.
    
    Setting 2: Intermediate exfiltration: A leak occurs over days or weeks, allowing incident-response teams to detect and potentially intervene.
    
3.  3.
    
    Setting 3: Slow exfiltration: Gradual leakage over months or years, which may render the stolen model no longer valuable by the time it is fully reconstructed.
    

Fundamentally, by creating a scheme (any scheme) for detecting malicious behavior, this forces the adversary to make a choice: they can either get caught by the detection scheme, and deal with the consequences of being detected; or they must operate a covert or “undetectable” level of exfiltration.

This work focuses on this “undetectable” regime and designs detection tools that provably limit its effectiveness. Based on our estimates, our proposed techniques can extend effective response windows from days to months or years, providing at least a $100\times$ reduction in feasible exfiltration rates.

##### Contributions.

Inference verification is the task of confirming that a given text output was produced by a specific model running correct inference, rather than by a tampered, substituted, or otherwise divergent process. In this work, we show that inference verification can be applied to the specific threat of steganographic weight exfiltration. We introduce a specific method of inference verification and show that it can be used to bound the capacity available to an adversarial provider trying to encode information in model outputs. This work makes the following contributions:

1.  1.
    
    Formalizes model-weight exfiltration as a security game and derives strong bounds on exfiltration capacity when using the systems we propose. We formalize the exfiltration-detection interaction in Experiment [3](#S4.F3 "Figure 3 ‣ 4.1 Security Game ‣ 4 Formulating the Model Weight Exfiltration Security Game ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") and prove three bounds under varying adversarial models (Theorems [5.1](#S5.Thmtheorem1 "Theorem 5.1. ‣ Rate limitation for the FSSL policy. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [5.2](#S5.Thmtheorem2 "Theorem 5.2. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), and [5.3](#S5.Thmtheorem3 "Theorem 5.3. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")). Along with these adversarial models, we propose architecture which can realize and limit potential adversaries in practice.
    
2.  2.
    
    Introduces a verification framework with multiple scoring methods that reconstruct fixed-seed sampling to detect deviations from expected model behavior.
    
    We propose the Fixed-Seed Sampling Likelihood (FSSL) as a method for estimating likelihood of being sampled, and we introduce two estimates for this, Token-DiFR (FSSL-GM), and Token-IPT-DiFR (FSSL-IPT), which can be used for LLMs that sample with the Gumbel-Max trick and Inverse Probability Transforms, respectively.
    
3.  3.
    
    Proposes a decoupled verification server architecture that separates security from performance, enabling high-assurance computation on isolated hardware/software stacks without constraining inference throughput. The architecture requires minimal trust assumptions (detailed in Appendix [E](#A5 "Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")) and has dual-use value for both security monitoring and reliability/bug detection.
    
4.  4.
    
    Validates empirically on production systems We evaluate exfiltration rates on Llama-3.1-8B, Llama-3.2-3B, Qwen1.5-MoE-7B, Qwen3-30B-A3B. For Qwen3-30B-A3B we demonstrate a ${<}0.5\%$ exfiltrable information rate with $10^{-2}\%$ FPR, a ${\geq}200\times$ slowdown in attack. For a 1 TB model with $1000$Gb of traffic per day, this extends exfiltration time from ${\sim}1$ day to ${>}200$ days.
    

Importantly, as our scheme detects deviations from expected behavior, it will flag not only malicious exfiltration attempts but also inference-time anomalies or bugs. As such, a further benefit of this detection scheme is that it serves a double-purpose and can provide a powerful tool for debugging and reliability monitoring. From an infrastructure standpoint, the systems required for detecting malicious activity and those for detecting model failures are nearly identical.

## 2 Related Works

There is a lot of work in the space of detecting data exfiltration; in this work we specifically focus on approaches that hide information within a channel containing user data, as this is a novel attack surface area within LLM inference. This ties directly into existing literature on steganography and watermarking, as well as basic forms of content filtering.

### 2.1 Steganography and Watermarking

This section provides a brief overview of ideas and techniques in steganography and watermarking, which are related to the capabilities of the exfiltration adversary in our threat model.

##### Steganography

Steganography is the problem of communicating covertly over a channel by embedding hidden information into otherwise innocuous messages. A steganographic scheme consists of an encoding algorithm that maps a secret message and (optionally) a key to a _cover object_, and a decoding algorithm that recovers the hidden message from the resulting output.

As a concrete example, one may embed a secret message into the least significant bits of an image’s pixels. The modified image appears visually unchanged, yet a recipient who knows the embedding rule can recover the hidden message. More generally, modern steganographic schemes are analyzed with respect to an adversary who attempts to distinguish genuine channel outputs from stego outputs.

In this work, our goal is to detect steganographic schemes used to hide model-weight exfiltration attempts. We leverage standard definitions and results from the steganography literature when understanding the limitations of our proposal. For brevity, we defer formal syntax and foundational results to Appendix [B](#A2 "Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"). For other cryptographic primitives, such as pseudorandom functions and hash functions, we refer the reader to Katz and Lindell \[[KL14](#bib.bib213 "Introduction to modern cryptography")\].

##### Watermarking.

Watermarking is a related technique often used to encode a single bit of information within a covertext: $1$ if the watermark is present and $0$ if the watermark is not. The embedded information can serve many purposes, such as asserting ownership, tracing provenance, or verifying authenticity.

Conceptually, steganography and watermarking lie on a spectrum, and it may be useful to interpret steganography as repeatedly running a watermarking scheme to encode more than a single bit. In this light, while our work focuses on the task of steganography (and its detection), the connection to watermark allows us to pull from theoretical bounds in the watermarking literature.

There is a recent but long line of work in language model watermarking \[[AARve](#bib.bib207 "My AI safety lecture for ut effective altruism"), [KGW+23b](#bib.bib210 "A watermark for large language models"), [CGZ24](#bib.bib209 "Undetectable watermarks for language models"), [FGJ+25](#bib.bib211 "Publicly-detectable watermarking for language models"), [KTH+23](#bib.bib212 "Robust distortion-free watermarks for language models"), [CG24](#bib.bib16 "Pseudorandom error-correcting codes"), [GM25](#bib.bib14 "Edit distance robust watermarks via indexing pseudorandom codes"), [CHS25](#bib.bib199 "Watermarking Language Models for Many Adaptive Users")\]. However, most works operate in a model that require the watermarker and detector to share only a small key with the goal of making the watermark as robust as possible. This means that even the highest throughput schemes only embed about $1$ bit per “block,” where a block is text that is being watermarked[^2] \[[CHS25](#bib.bib199 "Watermarking Language Models for Many Adaptive Users")\].

In contrast, language model steganography \[[KJG+21](#bib.bib198 "Meteor: cryptographically secure steganography for realistic distributions")\] has a higher throughput rate, since it assumes text is unchanged. These schemes can almost reach capacity, embedding as many bits as the entropy of the response.

### 2.2 Model Weight Exfiltration

In the context of discussing model-weight exfiltration, a recent framework \[[NLK+24](#bib.bib1 "Securing ai model weights: preventing theft and misuse of frontier models")\] introduces the notions of security levels from 1 to 5, which increase in defensive capacity. SL1 is a system that can likely thwart amateur attempts. SL2 is a system that can likely thwart most professional opportunistic efforts by attackers that execute moderate-effort or nontargeted attacks. SL3 is a system that can likely thwart cybercrime syndicates or insider threats. SL4 is system that can likely thwart most standard operations by leading cyber-capable institutions. SL5 is a system that could plausibly be claimed to thwart most top-priority operations by the top cyber-capable institutions.

To set the grounding for this work, we will focus primarily on creating a scheme for moving from SL3 to SL4 and building the basis for SL5 security, by increasing the time required to to covertly exfiltrate from minutes and hours to days and years.

### 2.3 Inference Verification

As introduced above, inference verification is the task of confirming that text outputs were produced by a specific model running correct inference. Existing approaches span a wide range of trust assumptions and computational costs, from cryptographic guarantees to statistical tests.

Cryptographic methods. Zero-knowledge proofs (ZKPs) offer the strongest guarantees, allowing a verifier to confirm that a computation was performed correctly without re-executing it. Recent work has applied ZKPs to neural network inference \[[CZL+25](#bib.bib3 "ZkTorch: privacy-preserving deep learning with zero-knowledge proofs"), [SLZ24](#bib.bib4 "ZkLLM: zero knowledge proofs for large language models")\], but the computational overhead remains prohibitive: proof generation for LLaMA-2-scale models requires on the order of hundreds to thousands of seconds per token, making these approaches impractical for production deployments.

Internal state fingerprinting. A more tractable class of methods verifies inference by comparing intermediate activations between a provider’s run and a verifier’s replay. LOGIC \[[SVS+25](#bib.bib6 "LOGIC: Trustless Inference through Log-Probability Verification")\] collects top-$k$ log probabilities at sampled positions, while TOPLOC \[[OFP+25](#bib.bib7 "TOPLOC: a locality sensitive hashing scheme for trustless verifiable inference")\] captures top-$k$ activation indices and values from the final hidden layer, encoding them as a polynomial to reduce communication costs. Both methods work by replay: the verifier re-executes inference on the provider’s output sequence and checks that the resulting activations match. However, internal state fingerprinting only confirms that a sequence is consistent with a given forward pass, not that it was actually produced by the model’s sampling procedure. A malicious provider could generate arbitrary text, post-hoc compute matching fingerprints, and pass verification, making these methods proofs of reconstructability rather than generation authenticity.

Distributional tests. \[[GLG25](#bib.bib5 "Model equality testing: which model is this api serving?")\] frame inference verification as a two-sample test between a trusted distribution and an API distribution, using Maximum Mean Discrepancy with string kernels. \[[ZYQ+25](#bib.bib39 "Auditing black-box llm apis with a rank-based uniformity test")\] propose a rank-based uniformity test that checks whether target API outputs are statistically consistent with a reference model’s distribution over many samples. These approaches are fully black-box but verify only distributional similarity, not per-generation correctness.

Shared seed verification. Concurrently with this work, Karvonen et al. introduce Token-DiFR \[[KRR+25](#bib.bib40 "DiFR: inference verification despite nondeterminism")\]. FSSL-GM compares output tokens directly against a trusted reference implementation conditioned on the same seed and is able to detect 4-bit quantization with AUC $>0.999$ within 300 output tokens at zero communication overhead. Karvonen et al. also introduce Activation-DiFR which complements this by projecting intermediate activations through random orthogonal projections into compact fingerprints, achieving the same detection accuracy with as few as 2 tokens while reducing communication costs by 25–75% relative to prior methods.

### 2.4 Existing Model Weight Exfiltration Detection methods

One naive attack to exfiltrate data through user traffic would be to exfiltrate weights directly through output messages, by sending the model weights as plaintext. A first line of defense against such a naive weight exfiltration technique is to detect messages that deviate from ordinary conversational patterns. Two simple, independent approaches can be implemented here.

Syntactic filtering. A basic scheme applies regular expressions and lightweight heuristics to flag messages with suspicious surface patterns, such as long sequences of numbers or other structured encodings. While this approach is trivial to deploy it is also easily evaded by re-encoding information (e.g., mapping numbers to words or distributing bits across multiple tokens).

Perplexity filtering. A slightly more sophisticated defense uses a reference LLM trained on benign message traffic to compute sequence-level _perplexity_, a standard measure of how well a model predicts a sequence. Perplexity is a function of the log-likelihood of each token, where lower values indicate that the model finds the text highly predictable, while higher values suggest the text is surprising or out-of-distribution. Messages with unusually high perplexity are flagged as potential exfiltration attempts \[[KAR24](#bib.bib12 "Using an llm perplexity filter to detect weight exfiltration")\]. This can detect outputs that are syntactically normal but statistically implausible under the benign distribution, though adaptive adversaries can still craft messages that maintain natural perplexity while encoding information.

Both schemes are simple to run and provide a low-cost first defense, but they leave a substantial gap between benign and adversarial outputs. A powerful adversary can easily create a steganographic technique that only modifies words and tokens that leave the perplexity of the whole sequence low.

## 3 LLM Inference Preliminaries

Because our exfiltration attacks operate by modifying the inference procedure, we begin by reviewing how modern LLMs generate text. In standard implementations, inference is designed to be stochastic: given a fixed model and a fixed random seed, sampling-based decoding should be reproducible.

At the algorithmic level, this suggests a clean separation between deterministic computation (forward passes, logit computation) and controlled randomness (token sampling that takes a seed). However, in practice, hardware and software effects introduce additional sources of nondeterminism; and as a result, even with a fixed seed, repeated runs of inference often do not produce identical outputs.

In this section, we formalize which components of inference are intended to be deterministic, which are intentionally randomized, and which remain nondeterministic despite the use of a seed.

### 3.1 Basic Setting (LLM inference)

##### Decode versus prefill.

Transformer inference consists of two phases: _prefill_ processes the input prompt in a single parallel forward pass, while _decode_ autoregressively generates output tokens one at a time. Though both phases have similar asymptotic complexity, prefill achieves significantly higher throughput in practice (typically 3–10×) because it is compute-bound and highly parallelizable, whereas decode is memory-bandwidth bound due to repeatedly loading the key–value cache \[[ERD25](#bib.bib41 "Inference economics of language models")\]. This makes prefill particularly advantageous for verification or evaluation tasks that do not require autoregressive generation.

### 3.2 Sampling From Large Language Models

Sampling from a Large Language Model can be thought of in two steps: (1) generating a probability distribution, and (2) sampling a token from it. For step (1), given logits $z\in\mathbb{R}^{|\mathcal{T}|}$ over a vocabulary $\mathcal{T},$ and a temperature parameter $T$, the model induces a categorical distribution

$$p_{i}^{(T)}=\mathrm{softmax}\!\left(\frac{z}{T}\right)_{i}=\frac{\exp(z_{i}/T)}{\sum_{j=1}^{|\mathcal{T}|}\exp(z_{j}/T)}.$$

The temperature $T$ controls the sharpness of the distribution: as $T\to 0$, the distribution concentrates on the maximum-logit token (approaching greedy decoding), while larger $T$ produces a flatter distribution and increases randomness. After optional filtering steps such as top-$k$, top-$p$, or min-$p$, the model samples from the resulting categorical distribution. To sample a token from a probability distribution, many modern LLMs use either the _Inverse Probability Transform_ (e.g., Ollama \[[32](#bib.bib9 "Ollama documentation")\], HuggingFace \[[WDS+20](#bib.bib11 "Transformers: state-of-the-art natural language processing")\]) or the _Gumbel-Max Trick_ (e.g., vLLM \[[KLZ+23](#bib.bib10 "Efficient memory management for large language model serving with pagedattention")\]). This sampling process relies on a pseudorandom generator, which takes as an input a sampling seed $\sigma$ and counter $i$ as an input, and returns a value $x$.

##### Inverse Probability Transform.

From a fixed random seed $\sigma$, a (pseudo)random number $u\sim\mathrm{Uniform}(0,1)$ is drawn for each token. The algorithm then computes the cumulative sum of the token probabilities $\vec{p}$ and selects the first token whose cumulative mass exceeds $u$. Conceptually, this corresponds to inverting the cumulative distribution function (CDF) of $\vec{p}$. The method is exact, efficient, and deterministic when both $\vec{p}$ and $\sigma$ are fixed; repeated sampling under identical conditions will always yield the same token. Here we use the notation $F(\cdot;r)$ to denote running a randomized function $F$ with randomness $r$, making it (ideally) deterministic. We also use a deterministic hash function $\mathsf{H}$ to expand $\mathsf{seed}$ into reproducible pseudorandomness.[^3]

Algorithm 1 Inverse-Probability-Transform (IPT) Sampler

1:Seed $\mathsf{seed}$, context position $i$, probability vector $\mathbf{p}\in[0,1]^{|\mathcal{T}|}$ with $\sum_{t=1}^{|\mathcal{T}|}p_{t}=1$

2:$\mathbf{C}\leftarrow\textsc{CumulativeSum}(\mathbf{p})$ $\triangleright$ Convert PDF $\mathbf{p}$ to CDF $\mathbf{C}$

3:$u\leftarrow\textsc{Uniform}([0;1];\mathsf{H}(\mathsf{seed}\|i))$ $\triangleright$ Use token index $i$

4:return $\min\{t\in\{1,\dots,|\mathcal{T}|\}:C_{t}>u\}$$\triangleright$ binary search: find smallest $t$ s.t. $C_{t}>u$

##### Gumbel-Max Trick.

The Gumbel-Max Trick provides an equivalent but reparameterized way to sample from $\vec{p}$. From a fixed random seed $\sigma$, for the $t$th token, an independent Gumbel noise term $g_{t}\sim\mathrm{Gumbel}(0,1)$, determined by $\mathsf{seed},$ is added to the (log) probability: $z_{t}=\log p_{t}+g_{t}.$ The selected token is the index of the maximum perturbed score, $\arg\max_{t}z_{t}$. Intuitively, this converts sampling from a categorical distribution into a deterministic argmax over noisy logits. Like the inverse transform, it is reproducible under a fixed seed $\mathsf{seed}$, since the Gumbel variables $g_{t}$ are deterministically derived from $\mathsf{seed}$. This trick is particularly convenient for differentiable relaxations (e.g., Gumbel-Softmax) and for implementations optimized for vectorized or GPU-based sampling.

Algorithm 2 Gumbel-Max Sampler

1:Seed $\mathsf{seed}$, context position $i$, probability vector $\vec{p}\in[0,1]^{|\mathcal{T}|}$ (over tokens $\mathcal{T}$, $\sum_{t}p_{t}=1$)

2:$\vec{z}\leftarrow\textsc{Gumbel}([0,1]^{|\mathcal{T}|};\mathsf{H}(\mathsf{seed}\|i))$ $\triangleright$ each $z_{t}\sim\textsc{Gumbel}(0,1)$

3:$\hat{t}\leftarrow\arg\max_{t\in\mathcal{T}}\big(p_{t}+z_{t}\big)$ $\triangleright$ $\arg\max$ returns the _token_ $\hat{t}$ achieving the maximum sum

4:return $\hat{t}$

##### Sampling Multiple Tokens.

We use the notation $\mathcal{D}^{\mathsf{H}}_{\theta,\mathcal{H}}(\mathsf{seed})$ to denote the honest sampling of a full response for a specific model $\theta,$ context $\mathcal{H},$ seed $\mathsf{seed},$ and hash function (or PRF) $\mathsf{H}.$ This algorithm first samples the distribution $\vec{p}$ using $\theta$ and $\mathcal{H}.$ Next, $\mathcal{D}$ will use one of the two above approaches for selecting a specific token $t$ from the distribution using the randomness from $\mathsf{H}(\mathsf{seed}\|i),$ where $i$ is the current response index.[^4] Then, $t$ is added to the context $\mathcal{H}$ and the process repeats until a termination symbol or response length limit is reached.

### 3.3 Non-determinism in Machine Learning

Despite the amount of reproducibility of the methods above, fixing the random seed (even with temperature $T{=}0$) does not guarantee identical outputs. Non-determinism arises because floating-point arithmetic is non-associative ($(a{+}b){+}c\neq a{+}(b{+}c)$): different GPU kernels or shapes can accumulate tensors in different orders, yielding different values. Batch variance, where kernel computation strategies depend on the batch size, which depends on the concurrent load, is the most common source of numerical noise. Inference optimizations further shift computation order; batch size, attention chunking/prefix caching, and cache reuse, and MoE models all add routing variability that can depend on load and tiny numerical perturbations \[[HL25](#bib.bib81 "Defeating nondeterminism in llm inference")\].

Identical open-weight models have shown cross-provider performance discrepancies, consistent with differences in templates, quantization/serving stacks, and the variability sources above \[[WIL25](#bib.bib80 "Open weight llms exhibit inconsistent performance across providers")\].

We empirically characterize this non-determinism by querying the OpenAI API with fixed seeds across thousands of completions; the results confirm that divergences are sparse but present, concentrating at a small number of token positions (see Appendix [J](#A10 "Appendix J Empirical Base Rates of non-determinism ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")).

### 3.4 Valid Non-determinism with a Fixed Seed: The Fixed-Seed Posterior Distribution

While Inverse-Probability Transform and Gumbel-Max Trick are mathematically deterministic, in practice the logit distribution $\vec{p}_{\theta}(x)$ is produced by a _non-deterministic_ computation. Even with a fixed seed $\sigma$, floating-point imprecision, asynchronous GPU execution, and nondeterministic kernel scheduling can cause small but measurable differences in $\vec{p}_{\theta}(x)$ across runs. This effect arises even in benign settings, independent of any adversarial manipulation, and has been well-documented in prior work \[[YLD+25](#bib.bib15 "Give me fp32 or give me death? challenges and solutions for reproducible reasoning")\]. We refer to this inherent variability as valid non-determinism.

To model this behavior, we view the model’s computed probability vector not as a single deterministic mapping $\vec{p}_{\theta}(x)$, but as a random draw from a higher-order _distribution over distributions_:

$$\vec{p}_{\theta}(x)\sim\mathcal{P}_{\theta}(x),$$

where $\mathcal{P}_{\theta}(x)$ represents the stochastic process generating the token-level probabilities. This perspective allows us to define heuristic distance measures between two runs of the same model (with identical seed $\sigma$) by comparing samples from $\mathcal{P}_{\theta}(x)$, illustrated conceptually in Figure [2](#S3.F2 "Figure 2 ‣ Fixed-Seed Posterior Distribution. ‣ 3.4 Valid Non-determinism with a Fixed Seed: The Fixed-Seed Posterior Distribution ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

##### Fixed-Seed Posterior Distribution.

We begin with a general abstraction that captures the non-determinism induced by stochastic sampling under a fixed seed. Let $\mathrm{Sample}(\cdot,\sigma)$ denote a generic sampling procedure that maps a probability distribution $p$ over tokens $\mathcal{V}$ and a seed $\sigma$ to a token $t\in\mathcal{V}$:

$$t=\mathrm{Sample}(p,\sigma).$$

Given a distribution over probability vectors $p\sim\mathcal{P}_{\theta}(x)$, the _fixed-seed posterior distribution_ is defined as:

$$P_{\mathrm{seed}}(t\mid\sigma)=\Pr_{p\sim\mathcal{P}_{\theta}(x)}\big[\,\mathrm{Sample}(p,\sigma)=t\,\big].$$

This represents the probability, over draws of the underlying probability distribution $p$, that a fixed random seed $\sigma$ yields token $t$. Intuitively, it characterizes how much stochastic variability remains in the sampling outcome even when the seed is fixed, due to non-determinism in the generation of $p$.

Example: Inverse Probability Transform. For concreteness, consider the case where $\mathrm{Sample}(\cdot,\sigma)$ implements the inverse probability transform. Let $\mathcal{P}=\{P_{i}\}_{i=1}^{n}$ denote a family of token-level probability distributions, where each $P_{i}$ defines a conditional distribution over tokens $t\in\mathcal{V}$ given model context $x_{i}$:

$$P_{i}(t)=\Pr[T=t\mid X=x_{i}].$$

Let $R:\Sigma\to[0,1]$ denote a deterministic randomization function (e.g., a pseudorandom generator) mapping a seed $\sigma\in\Sigma$ to a uniform draw $R(\sigma)\sim\mathrm{Uniform}(0,1)$. For each $P_{i}$, define the seed-conditioned token selection function

$$S_{i}(\sigma)=\min\{\,t\in\mathcal{V}:F_{i}(t)\geq R(\sigma)\,\},$$

where $F_{i}$ is the cumulative distribution function (CDF) corresponding to $P_{i}$.

Then, the fixed-seed posterior distribution for the inverse probability transform is:

$$P_{\mathrm{seed}}(t\mid R(\sigma)=r)=\Pr_{P_{i}\sim\mathcal{P}}\big[\,S_{i}(\sigma)=t\,\big],$$

representing the probability (over draws of $P_{i}$) that a fixed seed realization $\sigma$ produces token $t$ under this specific sampling mechanism. This abstraction makes clear that while the implementation details of sampling (e.g., inverse transform vs. Gumbel-Max) differ, each induces its own fixed-seed posterior distribution characterizing the residual randomness observable under valid non-determinism.

Intuitively, this distribution captures how much apparent randomness remains even when the seed is fixed. Figures [2(a)](#S3.F2.sf1 "Figure 2(a) ‣ Figure 2 ‣ Fixed-Seed Posterior Distribution. ‣ 3.4 Valid Non-determinism with a Fixed Seed: The Fixed-Seed Posterior Distribution ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") and [2(b)](#S3.F2.sf2 "Figure 2(b) ‣ Figure 2 ‣ Fixed-Seed Posterior Distribution. ‣ 3.4 Valid Non-determinism with a Fixed Seed: The Fixed-Seed Posterior Distribution ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") visualize the resulting fixed-seed posterior distributions for the inverse probability transform and the Gumbel-Max mechanism, respectively. These distributions form the basis for reasoning about an honest divergence during verification (as opposed to potentially malicious nondeterminism).

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img3-f8cec660.png]]

(a) Fixed-seed posterior distribution for the inverse probability transform, incorporating noise in token probabilities.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img4-819adb82.png]]

(b) Fixed-seed posterior distribution for the Gumbel-Max mechanism under the same noisy conditions.

Figure 2: Comparison of fixed-seed posterior distributions under two sampling mechanisms, illustrating variability arising from valid non-determinism in $\vec{p}_{\theta}(x)$.

Understanding the limits of valid non-determinism is central to limiting the exfiltration rate of adversaries. Under very minimal trust assumptions (Appendix [E](#A5 "Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")), the only communication channel open to the adversary is by hiding communication within this honest variability.

## 4 Formulating the Model Weight Exfiltration Security Game

In this section, we provide a concrete specification for the exfiltration problem that we solve in this paper. At a high-level, we consider the setting of LLM inference where there is an inference server and a chat server; we assume the inference server is fully corrupted by an adversary whose goal is to exfiltrate the inference model weights to an outside party, with whom they can coordinate. We assume that the adversary does not have access to any side-channels, eliminating exfiltration techniques such as using timing channel attacks, uploading the weights to a server through a developer’s laptop, or physically stealing the device holding the model. In many ways, preventing model theft is not different from a traditional security problem attempting to prevent any kind of exfiltration; there are several main differentiating factors associated with model-weight exfiltration.

##### Advantages to the Defender:

There are two main advantages to the defender: (i) Model weights are large; (ii) The type of operations and data that a model handles and outputs is largely predictable, namely: matrix multiplications and text data.

##### Advantages to the Attacker:

The main advantage to the attacker is that generally users expect to be able to make an extremely large number of calls that access the model (weights) per day.

### 4.1 Security Game

We define a simple extraction game, which we later be used to bound the success probability of an adversary extracting information, in Section [5.3](#S5.SS3 "5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"). The formal description is given in Experiment [3](#S4.F3 "Figure 3 ‣ 4.1 Security Game ‣ 4 Formulating the Model Weight Exfiltration Security Game ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), which is parameterized by:

-   •
    
    $\mathcal{T}$, the token set (i.e., vocabulary or alphabet) of the adversary’s message.
    
-   •
    
    $\mathsf{H}$, is a hash or pseudorandom function, modeled as a random oracle for simplicity.
    
-   •
    
    $\mathcal{A}_{0}$, $\mathcal{A}_{1}$, $\mathcal{A}_{2}$, the adversary’s preprocessing, encoding, and decoding algorithms respectively.
    
-   •
    
    $\mathcal{D}_{\theta,\mathcal{H}}(\mathsf{seed})$, the honest response distribution , determined by the model weights $\theta$, context (or prompt) $\mathcal{H}$, and seed $\mathsf{seed}$. In our context, even after all these are given, the output is a _randomized_ because of “invalid nondeterminism” (Section [3.3](#S3.SS3 "3.3 Non-determinism in Machine Learning ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")). In our security games, we suppress the $\theta$ and $\mathcal{H}$ parameters and treat them as fixed for the given adversary.
    
-   •
    
    $\mathcal{W}$ (warden), the policy algorithm to determine whether to flag a message.
    
-   •
    
    $n$, the number of bits which the adversary is challenged to exfiltrate (in our setting, this is the length of the model weights).
    
-   •
    
    $\ell$, the length of the adversary’s message.
    
-   •
    
    $\lambda$, the seed length of the model’s randomness and the security parameter of the system.
    

Success in this security game is defined by the adversary successfully reconstructing the challenge bits from the message (and any other precomputed material) itself. We define security for computationally bounded adversaries and policies as well as unbounded algorithms.

In our games, we suppress the notation of the model weights $\theta$ and the prompt $P$. We abstract the prompt out of the security game because a practical adversary will have already picked some prompt $P$ on which they will try and perform the exfiltration. And we care about limiting the exfiltration rate on this particular prompt. We also choose to model an adversary trying to exfiltrate some information about the incompressible model weights $\theta$ as the adversary sending and recovering a random bit-string. This allows us to further abstract away the model weights from the security game.

Note this security has been explored in the context of steganography, which we draw on directly. However, we are not interested in proving security against all possible policies/wardens. One can view our results for specific _lower bounds_ for steganography in a particular realistic context.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img5-7ec49c52.png]]

Figure 3: Outline of the security game described in Experiment [3](#S4.F3 "Figure 3 ‣ 4.1 Security Game ‣ 4 Formulating the Model Weight Exfiltration Security Game ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

\[Exfiltration Experiment\] Parameters. Let positive integers $n$ be the challenge bit length, $\ell$ be the maximum response length, and $\lambda$ be the security parameter. Let $\mathcal{T}$ be the token set (vocabulary) of messages and $\mathcal{D}^{\mathsf{H}}(\sigma)$ be a randomized function from $\{0,1\}^{\lambda}$ to $\mathcal{T}^{\leq\ell}$. Then, for a policy $\mathcal{W}$ and adversary $\mathcal{A}=(\mathcal{A}_{0},\mathcal{A}_{1},\mathcal{A}_{2})$, we define the games:  
$\mathbf{Exfil}_{\mathcal{W},\mathcal{A},\mathcal{D}}(\lambda,n,\ell)$  $\mathbf{Exfil}^{\mathbf{r}}_{\mathcal{W},\mathcal{A},\mathcal{D}}(\lambda,n,\ell)$

1.  1.
    
    Initialize a random oracle $\mathsf{H}:\{0,1\}^{*}\to\{0,1\}$
    
2.  2.
    
    $\mathsf{st}_{1},\mathsf{st}_{2}\leftarrow\mathcal{A}_{0}^{\mathsf{H}}(1^{\lambda},1^{n},1^{\ell})$    // preprocessing
    
3.  3.
    
    $X\leftarrow\{0,1\}^{n}$ ; $\sigma\leftarrow\{0,1\}^{\lambda}$   // sample challenge and seed
    
4.  4.
    
    $\hat{T}\leftarrow\mathcal{A}_{1}^{\mathsf{H}}(\mathsf{st}_{1},X,\sigma)$      // generate cover response
    
5.  5.
    
    If $\mathcal{W}^{\mathsf{H}}(\sigma,\hat{T})=1$, then output $\bot$
    
6.  6.
    
    $\hat{X}\leftarrow\mathcal{A}_{2}^{\mathsf{H}}(\mathsf{st}_{2},\hat{T},\sigma)$ $\hat{X}\leftarrow\mathcal{A}_{2}^{\mathsf{H}}(\mathsf{st}_{2},\hat{T})$  // recovery
    
7.  7.
    
    If $\hat{X}=X$, then output $1$
    
8.  8.
    
    Else, output $0$.
    

These definitions are presented in the _random oracle model_ \[[BR93](#bib.bib206 "Random oracles are practical: a paradigm for designing efficient protocols")\], which enables some of our later results. Note that all parties know and have access to $\mathcal{D}^{\mathsf{H}}.$

The first game $\mathbf{Exfil}$ is the standard game, where both parties are aware of the seed that is used to sample the distribution. However, in cases when the seed $\sigma$ is sampled securely (and $\mathcal{A}_{2}$ does not get it directly), we are able to obtain stronger bounds in the more restricted game $\mathbf{Exfil}^{\mathbf{r}}$.

###### Definition 4.1 ($(\alpha,\varepsilon)$\-exfiltration secure).

A policy $\mathcal{W}$ is (computationally) _$(\alpha,\varepsilon)$\-exfiltration secure_ if:

1.  1.
    
    For all $\sigma$, $\Pr_{T\sim\mathcal{D}^{\mathsf{H}}(\sigma)}\big[\mathcal{W}^{\mathsf{H}}(\mathsf{seed},T)=1\big]\leq\alpha,$ i.e., $\mathcal{W}$ has false positive rate $\alpha$,
    
2.  2.
    
    and for all (PPT) adversaries $\mathcal{A}$, $\Pr\big[\mathbf{Exfil}_{\mathcal{W},\mathcal{A},\mathcal{D}}(\lambda,n,\ell)=1\big]-2^{-n}\leq\varepsilon.$
    

Note that $\alpha$ and $\varepsilon$ are, in general, functions of the parameters $\lambda$, $n$, $\ell$, or even $\mathcal{D}$. If the above holds only for $\mathbf{Exfil}^{\mathbf{r}}$ rather than $\mathbf{Exfil}$, then we say it $\mathcal{W}$ is secure _against seed agnostic decoders_.

Where relevant, we will also consider adversaries with restricted access to the random oracle $\mathsf{H}$.

### 4.2 Threat Model: Baseline Trust Assumptions

We consider an idealized setting of the model-weight exfiltration problem. In particular, we do not attempt to defend against adversaries with unrestricted physical access to hardware (e.g., physically stealing servers or storage devices to extract model weights). Our focus is on protecting model parameters in environments where security is enforced through software, networking, and operational controls. A more detailed discussion of these assumptions is provided in Appendix [E](#A5 "Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

##### No Side Channels.

We assume that adversaries cannot exploit any side channels (e.g., timing, cache access, or power analysis) to extract information. The only interface between the inference server and the external environment is the API server, which mediates all communication.

##### External Attacker Control over User Queries.

We assume that external adversaries may fully control the contents of user queries, including model inputs, random seeds, sampling parameters (e.g., temperature, top-$k$, and top-$p$), and query rates. This represents a worst-case scenario for query-based extraction attempts.

##### Internal Attacker Control over Outbound Messages.

We assume that an internal adversary (e.g., one with access to the inference server) may control all outbound inference messages. That is, they can arbitrarily modify or encode information within model outputs before they are transmitted externally.

##### Trusted Verification Code.

We assume that the verification server is honest and uncompromised. While the attacker may control the client side of the API or manipulate request patterns, the verification process itself is assumed to execute faithfully and does not introduce additional exfiltration risk.

##### Trusted Logging.

We assume access to a secure, append-only logging mechanism that records every input, output, and associated seed for all messages transmitted from the inference server to the API gateway. These logs are assumed to be tamper-evident and verifiable.

##### Random Sampling for Verification is Private and Non-manipulable.

We assume the existence of a private, non-manipulable process for randomly sampling input–output pairs for verification. If this process were predictable or observable, an adversary could infer which pairs will be re-verified and exfiltrate information through the remaining unchecked traffic. The base assumption is that an adversary can neither predict the next message to be sampled, nor modify the probability that a message is sampled next.

##### Paired Input–Output Messages.

We assume that every output message produced by the inference server is associated with a corresponding input message. Messages that cannot be paired with a valid input are not permitted to leave the datacenter.

## 5 Theoretical Framework: Verification System

This section introduces, at an abstract level, our proposed _verification system_ to mitigate against potential exfiltration. We defer implementation details and additional system-level choices to Section [6](#S6 "6 Implementing a Verification Server ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"). The goal of the verification system is to detect suspicious deviations from a trusted baseline model during inference. While our primary motivation is to identify potential model-weight exfiltration, the same framework applies to general distributional or behavioral anomalies in model outputs.

At a high level, the system operates as follows (illustrated in Figure [4](#S5.F4 "Figure 4 ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")):

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img6-977e8011.png]]

Figure 4: Overview of the verification system for runtime output validation. A lock symbol denotes parts of the inference verification scheme that require high integrity, further explored in Section [E](#A5 "Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")

1.  1.
    
    Inference Logging. The API Server logs all inference inputs and outputs, together with references to the exact model release, code version, and the seed used for that inference.[^5]
    
2.  2.
    
    Verification. An isolated _Verification Server_ re-executes a random subset of logged inferences using a trusted version of the model and codebase.
    
3.  3.
    
    Analysis and Escalation. The security team reviews any significant discrepancies between verified and observed outputs, triggering deeper audits when divergences exceed predefined statistical thresholds.
    

The degree of isolation of the Verification Server is a tunable security parameter. In minimal deployments, this can be enforced through access controls and containerization; in the extreme, the verification server may be fully air-gapped. All trust assumptions are detailed in Appendix [E](#A5 "Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

### 5.1 Sampled-Token Verification via Exact Matching

A core weakness of the naive approach is the mismatch between the _verification_ program and the _generation_ program. To eliminate this, we use the same model and configuration for both inference and verification. The procedure is simple: re-run generation under the recorded seed and sampling parameters, compare the regenerated token at each position to the claimed token, and count mismatches. This yields a transparent, token-level exact-match score for the sequence. However, tokens that fail verification allow an adversary to potentially encode up to $\log_{2}(\text{vocab\_size})$ bits per mismatched token.

For efficiency, the same idea can be executed without iterative decoding. Using _prefill_, a single forward pass over the input+output yields the next-token distributions at every position; sampling (with the recorded seed) and exact matching can then be done position-wise in parallel. This preserves teacher-forcing semantics while running significantly faster. Full pseudocode appears in Appendix [C.3](#A3.SS3 "C.3 Naive Methods for Sampled Token Verification ‣ Appendix C Algorithms ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

### 5.2 Classification using the Fixed-Seed Sampling Likelihood Policy

In Section [3.4](#S3.SS4 "3.4 Valid Non-determinism with a Fixed Seed: The Fixed-Seed Posterior Distribution ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), we introduced the _fixed-seed posterior distribution_, which captures the stochastic variability of model outputs that can arise under honest non-determinism. Building on this, we define a practical decision rule for distinguishing between _valid_ and _suspicious_ generations. Our approach centers on estimating the likelihood that a given output token $t$ was honestly generated under a fixed seed $\sigma$ and the model’s nominal configuration. We refer to this value as the _Fixed-Seed Sampling Likelihood (FSSL)_. This is simply the fixed-seed posterior distribution evaluated at a specific sampled token. Intuitively, this measures how consistent a token is with the model’s expected non-deterministic behavior under fixed-seed execution.

##### Classification via Thresholding.

Given an estimate of $\mathrm{FSSL}(t\mid\sigma)$, we use a simple threshold rule:

$$\text{flag }t\ \text{if}\ \mathrm{FSSL}(t\mid\sigma)<\tau,$$

with $\tau$ calibrated on benign traffic to meet a target false–positive rate. Per-token decisions (or summed log-likelihoods) can be aggregated over sequences, users, or time windows for higher-level alerts. We instantiate estimates of the FSSLfor two samplers: we introduce _Token-DiFR_ to estimate FSSLquantity for samplers that use the Gumbel-Max Trick, FSSL-GM, and we introduce _Token-IPT-DiFR (FSSL-IPT)_ for samplers that use Inverse Probability Transforms for sampling, which estimates FSSL-IPT. Subsequent sections derive their estimators and evaluate performance.

### 5.3 Theoretical Exfiltration Limitations

Our proposed architecture allows us to provably bound the ability of any covert adversary to exfiltrate data out of the server under mild trust and cryptographic assumptions (see Appendix [E](#A5 "Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")). Recall that our dichotomy is to _either_ have the adversary get caught or else limit the exfiltration rate of the adversary. This section is concerned with proving limits in the latter case. In other words, we will bound how _quickly_ an adversary can exfiltrate without getting flagged. This is the best we can hope to prove in our context, without assumptions on the adversaries exfiltration pattern or frequency. We discuss later in this section how our theorems are related to the Exfiltration game outlined in early sections.

We prove three different bounds for the FSSL policy (Section [5.2](#S5.SS2 "5.2 Classification using the Fixed-Seed Sampling Likelihood Policy ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")), which apply under different architectures and assumptions. The first is the most general and applies to any adversary under the minimal assumptions explicated in Appendix [E](#A5 "Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") and using the simple FSSL filter we propose in Section [5.2](#S5.SS2 "5.2 Classification using the Fixed-Seed Sampling Likelihood Policy ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"). The remaining two are tighter bounds which require additional assumptions.We go on to discuss the plausibility and tightness of the bounds.

##### Rate limitation for the FSSL policy.

First, we recall Theorem [B.2](#A2.Thmtheorem2 "Theorem B.2 (Steganographic limitations). ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), which shows that any steganography scheme can only transmit as much information as is in the entropy of its output distribution. We combine this with two other simple observations to give rate limitation for our FSSL policy. Because we bound with respect to such a simple policy, this bound will also apply to any the optimizations and augmented policies discussed in Section [6](#S6 "6 Implementing a Verification Server ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

Theorem [5.1](#S5.Thmtheorem1 "Theorem 5.1. ‣ Rate limitation for the FSSL policy. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") is a most general rate-limiting bound. It applies to exfiltration adversaries where both the encoder and decoder have access to the seed that is used for generation. In the worst case, this bound shows that an adversary can only exfiltrate as many bits as the FSSL policy is set to. However, as we show in Section [7](#S7 "7 Empirical Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), for many prompts and seeds both the false positive rate and exfiltration limitations are much tighter than the stated in this worst case, since $\mathsf{Supp}(\mathcal{D}_{\leq\tau})\ll 2^{r}$. Here, we use $\mathcal{D}_{\leq\tau}$ to indicate the honest distribution, restricted to the responses which have log-likelihood at most $r$. Here, we’re using $\mathsf{Supp}$ to indicate the set of responses which support the input distribution.

###### Theorem 5.1.

For any distribution $\mathcal{D}$, $\mathcal{W}_{\mathrm{FSSL},\tau}$ at threshold $\tau$ is $(\alpha,\varepsilon)$\-exfiltration secure for $\alpha=|\mathcal{T}|^{\ell}\cdot 2^{-\ell\cdot\tau}$ and $\varepsilon=(|\mathsf{Supp}(\mathcal{D}_{\leq\tau})|-1)/2^{n}\leq(2^{\ell\cdot\tau}-1)/2^{n}$.

###### Proof.

The $FSSL$ policy flags any response which is too surprising. Formally, it computes the log-likelihood (a.k.a. surprisal or empirical entropy) for the given response and seed. Then, it tests the likelihood $p$ and the length of the response $\ell$ to check if $p/\ell\geq\tau$. Among the honest distribution, the only honest responses which are below this threshold are exactly $\mathcal{S}:=\mathsf{Supp}(\mathcal{D}_{\leq r})$.

First, notice that by definition, for any $\hat{T}\not\in\mathcal{S}$, $\Pr_{T\sim\mathcal{D}}[T=\hat{T}]<2^{-\ell\cdot\tau}$ and therefore in total, we have that $\alpha\leq|\mathcal{T}|^{\ell}\cdot 2^{-\ell\cdot\tau}$ which establishes our claim about $\alpha$.

Next, observe that whenever the adversary has any response outside $\mathcal{S}$, then the $\mathbf{Exfil}$ game outputs $\bot$. Therefore, when $\mathcal{A}$ is not flagged by the policy, it is because their message $\hat{T}$ is in the set $\mathcal{S}$. Notice that the maximum entropy a distribution can achieve on such a distribution is $\log|\mathcal{S}|$, and therefore the capacity of a channel with such a support size is also bounded by $|\mathcal{S}|$ (Theorem [B.2](#A2.Thmtheorem2 "Theorem B.2 (Steganographic limitations). ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")). The final inequality comes from the observation that there are at most $2^{\ell\cdot\tau}$ responses what appear with probability at least $2^{-\ell\cdot\tau}$, which establishes the $\varepsilon$ security claim. ∎

##### Receivers without the seed.

Under additional assumptions or infrastructure, one may expect that the decoding adversary cannot obtain the seed that used by the encoder. In this case, Theorem [5.1](#S5.Thmtheorem1 "Theorem 5.1. ‣ Rate limitation for the FSSL policy. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") is too loose, and we should aim to achieve bounds in the restricted game $\mathbf{Exfil}^{\mathbf{r}}$ (Experiment [3](#S4.F3 "Figure 3 ‣ 4.1 Security Game ‣ 4 Formulating the Model Weight Exfiltration Security Game ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")). In this section, we show two bounds in this restricted game below. See Appendix [E](#A5 "Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") for more discussion about these assumptions.

The bounds in this section attempt to generalize beyond the $FSSL$ policy and will apply to _any_ policy with a particular structure. Motivated by our experimental results, we see that each token of a generation is _nearly_ deterministic given the prompt and seed. In particular only about $2\%$ of tokens in our experiments are “branching points,” where floating-point noise makes the next token undetermined.

##### Permitted tokens.

The above observation motivates our characterization of policies $\mathcal{W}$ where at each index $i$, there is only one token $t$ which is permitted, i.e., if $\hat{T}[i]\neq t$ then $\mathcal{W}(\hat{T})=1$. In practice, we don’t quite obtain full determinism, so we instead define $(p,q)$\-permitted token policies. Where, at each index there is one permitted token with probability $(1-p)$, or else there are $q>1$ permitted tokens with probability $p$ (and these probabilities are independent).

Based on our experiments, we can approximate the exfiltration bounds of the $FSSL$ policy with $p=0.02$ and $q=2$. However, we note that this is a very simplified abstraction for the purposes of obtaining a possible stronger bound under additional assumptions. In the real world, it is unclear how closely policies satisfy the $(p,q)$\-definition. It is possible an adversary could correlate where permitted tokens occur (breaking independence) or choose an adversarial prompt which has additional “branching points,” which may be interesting for future work to explore.

First, using the capacity limitations covered in Theorem [B.4](#A2.Thmtheorem4 "Theorem B.4 (Capacity limitations). ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), we obtain the bound below. However, this requires some other careful assumptions about the security and implementation of the seed expansion. In particular, we need that the adversary can’t expand the seed on their own and that they must commit to a token in order to get the randomness used for the next logit. This is the most interactive infrastructure we propose, but we can obtain a very strong bound.

###### Theorem 5.2.

Let $\mathcal{W}$ be a $(p,q)$\-restricted policy with false positive rate $\alpha$ on $\mathcal{D}$. Define $r^{\prime}:=\log q-h(1-p)-(1-p)\log(q-1)$ where $h$ is the binary entropy function. Then, $\mathcal{W}$ is $(\alpha,\varepsilon)$\-secure against admissible adversaries for $\varepsilon=(2^{\ell\cdot r^{\prime}}-1)/2^{n}$, under the following additional conditions:

1.  1.
    
    the seed is longer than the response, i.e., $\lambda>\ell\log|\mathcal{T}|$,
    
2.  2.
    
    and the adversary $\mathcal{A}_{1}$ computes $\mathcal{D}^{\mathsf{H}}(\sigma)$ once and never queries $\mathsf{H}$ otherwise.
    

###### Proof.

Since the adversary $\mathcal{A}_{1}$ is only given the honest $\mathsf{H}$ evaluation while streaming an honest response, each logit is uniformly random and unpredictable by $\mathcal{A}_{1}$. And, by assuming the seed is longer than the response ($\lambda>\ell\log|\mathcal{T}|$), each of these choices remains uniformly random conditioned on the previous ones, since there isn’t enough response length to learn the seed.

Therefore, we can model each token as an independent channel and apply Theorem [B.4](#A2.Thmtheorem4 "Theorem B.4 (Capacity limitations). ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") directly. Adversary $\mathcal{A}_{1}$ must transmit $n$ bits to the receiver with no error. And, we consider each token sent as a channel, which either has $q>1$ permitted tokens (with probability $p$) or has one permitted token, determined by the seed and context (i.e., if the adversary were to deviate they would get caught). Theorem [B.4](#A2.Thmtheorem4 "Theorem B.4 (Capacity limitations). ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") gives a direct bound on the number of messages $M$ in this case. Specifically, we have $M\geq n/(\log q-h(1-p)-(1-p)\log(q-1)),$ where we model the probability that there is only one permitted token $(1-p)$ as uniformly random symbol, since the sender has no control over it (recall that it is unpredictable). As we’re interested in the bits per token, we can therefore bound $n/M\leq\log q-h(1-p)-(1-p)\log(q-1)$ as claimed. ∎

If the interactivity of the hash function evaluation is too expensive, we prove one final, slightly weaker, bound. In this case we need only assume that the adversary is computationally bounded. In practice, this assumption can be enforced by requiring the server output tokens at some minimum rate. This way the adversary has a limited amount of time to search for “good” responses.

###### Theorem 5.3.

Let $\mathcal{W}$ be a $(p,q)$\-restricted policy with false positive rate $\alpha$ on $\mathcal{D}$. For any constant $\delta>0$ define $r^{\prime}:=(p+\delta)\log q$. Then, $\mathcal{W}$ is $(\alpha,\varepsilon)$\-secure against admissible adversaries for $\varepsilon=(2^{\ell\cdot r^{\prime}}-1)/2^{n}+e^{(-O(\ell))}$, under the following additional conditions:

1.  1.
    
    the seed is longer than the response, i.e., $\lambda>\ell\log|\mathcal{T}|$,
    
2.  2.
    
    The inference distribution $\mathcal{D}^{\mathsf{H}}(\sigma)$ samples randomness sequentially,
    
3.  3.
    
    and the adversary $\mathcal{A}_{1}$ queries $\mathsf{H}$ at most $O_{\delta}(\ell)$ times.
    

###### Proof.

The main goal of this result amounts to showing that at most $p+\delta$ fraction of the logits in $\mathcal{A}_{1}$’s output $\hat{T}$ have more than one permitted token. This is equivalent to bounding the probability of the adversary finding a response sequence where $>(p+\delta)\cdot\ell$ tokens have more than 1 permitted token. We can bound this using Lemma [5.4](#S5.Thmtheorem4 "Lemma 5.4. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") below. Intuitively, each response has a probability $p$ of having more than $1$ permitted token (which we will model with $\mathsf{H}$ outputting $0$). Therefore, given $O(\ell)$ queries, the adversary can only find a sequence like this with probability at most $e^{-O(\ell)}$ which is negligible in the response length. So, with high probability, the adversary has only $(p+\delta)\ell$ locations which are not deterministic, each with an alphabet of size $q$. So, the maximum number of bits that can be exfiltrated is bounded by $\ell(p+\delta)\log q$. ∎

###### Lemma 5.4.

Let $\mathcal{A}^{\mathsf{H}}$ by an algorithm issuing at most $N=O(k)$ queries to a random function $\mathsf{H}:\{0,1\}^{*}\to\{0,1\}$ that is $0$ with probability $p$, which outputs a string $x\in\{0,1\}^{k}$. Then, the probability that $p^{\prime}k$ of the prefixes of $x$ evaluate to $0$ is at most $e^{-\Theta(k)}$.

###### Proof.

Let $X\subseteq\{0,1\}^{k}$ be the set of $k$\-bit strings which $\mathcal{A}$ queried. Note that for any _fixed string_ $x\in\{0,1\}^{k}$, the number of $0$ prefixes is a random variable $S_{x}\sim\mathrm{Bin}(k,p)$. Then, we also know that $|X|\leq N$, and therefore, by a union bound and Chernoff’s bound, we get that

$$\Pr[\exists_{x\in X}S_{x}\geq p^{\prime}k]\leq Ne^{-kD_{\mathrm{KL}}(p^{\prime}\|p)}.$$

Notably this is $e^{-\Theta(k)}$ when $N=O(k)$ and $p$ and $p^{\prime}$ are constant. ∎

##### Tightness of the bounds

Here we provide some estimates on how _tight_ we expect the above bounds to be against a motivated adversary. Theorem [5.1](#S5.Thmtheorem1 "Theorem 5.1. ‣ Rate limitation for the FSSL policy. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")’s exfiltration bound $\varepsilon$ is likely to be tight in theory. As long as basic cryptography exists, steganography exists as a consequence of Theorem [B.3](#A2.Thmtheorem3 "Theorem B.3 (Due to [HLV02]). ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") \[[HLV02](#bib.bib203 "Provably secure steganography")\]. Even in practice, an adversary that carefully designs a steganographic scheme against the FSSL policy should likely be able to get close to this bound. They could likely draw heavily on techniques from steganographic literature to design schemes.

Theorems [5.2](#S5.Thmtheorem2 "Theorem 5.2. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") and [5.3](#S5.Thmtheorem3 "Theorem 5.3. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") are likely considerably looser under the stated assumptions. The bound allows an adversary to choose from any of the permitted tokens. So an adversary would likely need to consistently choose rare tokens to try to meet the stated limit. But even for a simple policy, like the FSSL policy, an adversary would need to be much more careful about their token choice across the response to avoid getting flagged. Moreover, it’s also not clear how to design a steganographic scheme for this setting. When the seed is known, both parties have access to the distribution, the typical setting for steganography. But, when the seed is secret, one may need to design a model and policy specific encoding scheme to try and achieve a meaningful rate.

We also note that it is still an open empirical question how big the support size of the truncated distribution is for adversarial prompts and how frequent multiple permitted tokens are. Our estimates show that all of these are relatively low; however, a motivated adversary may be able to fine-tune model settings and find the best prompts possible to increase the rate of their steganography scheme.

In Section [7](#S7 "7 Empirical Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), we give empirical estimates for the parameters in the bounds above. Combining this with the transformation below, we can give concrete exfiltration limitations under the stated assumptions for the policies that we propose.

## 6 Implementing a Verification Server

In Section [5](#S5 "5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), we introduce an abstract verification system and its relationship to our security game. In this section, we make this abstraction concrete with specific implementation details required to bringing this system into practice, and practical tradeoffs associated with building it. A central design advantage of the verification server architecture is its ability to decouple security from performance.

### 6.1 The Cost of Verification versus Generation

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img7-0a203b1d.png]]

Figure 5: Verification via prefill: the model conditions on the ground-truth prefix at each token.

During verification, a single token mismatch between two generations makes their subsequent probability distributions divergent, as they are conditioned on different contexts (e.g., all continuations of “the cat sat on” vs. “the cat sat beside” will diverge). Instead of continuing to generate text with fixed seeds, which would diverge immediately, we exploit the fact that LLMs expose logits for all next-token predictions during the _prefill_ stage. A single prefill over the full input–output sequence yields conditional probabilities for every position, enabling token-level suspiciousness scores in a single forward pass. Verification therefore involves only prefill, whereas normal inference requires both prefill and autoregressive decode. In short-context regimes, decoding is substantially less efficient than prefill: hardware utilization during decoding is typically 3–5$\times$ lower, implying a comparable 3–5$\times$ throughput gap. This disparity grows in long-context regimes, though the exact magnitude depends on attention optimizations and implementation details \[[ERD25](#bib.bib41 "Inference economics of language models")\].

### 6.2 Inverse Probability Transform Scoring Function Token-IPT-DiFR

In Section [5.2](#S5.SS2 "5.2 Classification using the Fixed-Seed Sampling Likelihood Policy ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") we introduce the notion of a classification using Fixed-Seed Sampling Likelihood. In this section we introduce a technique for approximating the fixed-seed sampling likelihood (FSSL) for the inverse probability transform sampling technique (IPT). We investigate a method _Token-IPT-DiFR_, which is concurrently introduced in parallel work \[[KRR+25](#bib.bib40 "DiFR: inference verification despite nondeterminism")\]. The core assumption is that across repeated model evaluations, the per-token probability vectors $\vec{p}_{\theta}(x)$ may vary due to small numerical or stochastic perturbations, but such variation is relatively small.

Intuitively, if the true sampling process (with fixed seed $\sigma$) selects a random value $u\in[0,1]$ that falls within the probability interval of one token, nearby tokens, whose cumulative probability mass lies close to $u$, remain plausible under valid non-determinism. Hence, instead of measuring the full empirical fixed-seed posterior (which would require many re-samplings per context), we approximate the likelihood of plausible tokens with a Gaussian centered at the seed sample $u$.

Formally, we compute a verification score for the observed token $t^{\star}$ by integrating a Gaussian density (mean $u$, width $\sigma$) over the token’s probability interval $[a,b]$ in the cumulative distribution $\bar{F}$ of $\vec{p}_{\theta}(x)$. This integral estimates the probability that a perturbed distribution, drawn from $\mathcal{P}_{\theta}(x)$, would produce $t^{\star}$ under the same seed. The log of this mass gives a continuous, differentiable proxy for the fixed-seed posterior probability. The Token-IPT-DiFR is defined in Algorithm [3](#alg3 "Algorithm 3 ‣ C.1 Inverse Probability Transform (IPT) Fixed-Seed Sampling Likelihood (FSSL) Estimators ‣ Appendix C Algorithms ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), and illustrated in Figure [10](#A3.F10 "Figure 10 ‣ C.1 Inverse Probability Transform (IPT) Fixed-Seed Sampling Likelihood (FSSL) Estimators ‣ Appendix C Algorithms ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

### 6.3 Gumbel-Max Scoring Function Token-DiFR

We also introduce the Token-DiFRto estimate FSSL-GM, which is defined for a given noise distribution over token probabilities, which by default we assume to be Gaussian $\mathcal{N}$, also introduced in concurrent work \[[KRR+25](#bib.bib40 "DiFR: inference verification despite nondeterminism")\].

Given a sampled token $t^{*}$, and knowledge of the inference server’s sampling seed $\sigma$, the verifier regenerates the same Gumbel noise the inference server generated $\vec{g}_{\sigma}\sim\mathrm{Gumbel}(0,1)^{V}$. The verification server generates the probability distribution $\hat{\ell}$. Then, we compute the probability that token $t^{*}$ surpassed that token as the sampled token; that is, computing the probability $\Pr[\vec{g}_{\sigma}[i]+\hat{\ell}[i]+\mathcal{N}>\vec{g}_{\sigma}[t^{*}]+\hat{\ell}[t^{*}]+\mathcal{N}]$ for token $i$. The full method and derivations are provided in Appendix [C.2](#A3.SS2 "C.2 Gumbel-Max FSSLEstimators (FSSL-GM) ‣ Appendix C Algorithms ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), and Algorithm [4](#alg4 "Algorithm 4 ‣ C.2 Gumbel-Max FSSLEstimators (FSSL-GM) ‣ Appendix C Algorithms ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img8-98865ff3.png]]

Figure 6: Diagram of the Token-DiFR function. The Token-DiFR estimates the likelihood of a particular token being sampled given a specific noise distribution across token probabilities.

### 6.4 How to Pool Across Multiple Tokens

In practice, computing a per-token suspiciousness score is only the first step; the harder problem is determining how to pool these scores across larger units of activity. Apriori, as a defender we do not know how an adversary will distribute an exfiltration attempt (e.g., they can attack across all tokens from a single user, across the first token of many users, or across all outputs generated on a particular GPU); thus there is no universally correct aggregation rule. Simple pooling strategies such as taking the 90th percentile or the mean correspond to different implicit threat models. The security team must define the granularity at which suspicious tokens are acted upon (e.g. user-level, request-level, or hardware-level) and the time horizon over which evidence accumulates. While our method provides calibrated token-level scores, the pooling and escalation policy is necessarily system-dependent and must be tailored to the deployment’s trust boundaries and adversary model. In this work we are purposefully agnostic to the adversary and thus do not comment on the right method to pool scores across tokens.

### 6.5 Message Sampling Rates

To understand the efficiency of our verification scheme, we analyze what percentage of traffic must be sampled to detect malicious messages with high confidence. Figure [7](#S6.F7 "Figure 7 ‣ 6.5 Message Sampling Rates ‣ 6 Implementing a Verification Server ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") illustrates the key statistical property of our approach: the _sampling percentage_ required depends primarily on the _proportion_ of malicious messages in the traffic. In Figure [7](#S6.F7 "Figure 7 ‣ 6.5 Message Sampling Rates ‣ 6 Implementing a Verification Server ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") we show the percentage of messages that need to be sampled in order to sample at least 1000 malicious messages, assuming the malicious messages are IID. Notably, even for very slow exfiltration attempts (e.g., 1% malicious traffic), the sampling percentage remains practical, even for high confidence. See Appendix [D](#A4 "Appendix D Mechanism Design security solutions: Random Sampling and the Panopticon ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") for the full derivation.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img9-179a547c.png]]

Figure 7: Sampling requirements for detecting at least 1,000 malicious messages with varying confidence levels, shown as percentage of data sampled. Left: Heatmap showing the percentage of traffic that must be sampled as a function of the proportion of malicious messages and target confidence level. Right: Sampling percentage versus exfiltration time, assuming 1 TB/day text throughput and 2KB average message size. Critically, verification remains extremely practical even for slow attacks.

## 7 Empirical Results

Anticipating a “reasonable” attacker is inherently brittle; capable adversaries can be more creative and better resourced than any fixed threat model. Instead of speculating about strategies, we take a distribution-free, information–theoretic view and bound _worst-case_ leakage under our verifier. At each position $t$, the verifier induces an _admissible set_ of tokens

$$A_{t}(\tau)\;=\;\{\,i:\mathrm{FSSL}_{t}(i)\geq\tau\,\},$$

where $\mathrm{FSSL}_{t}$ is our Fixed Seed Sampling Likelihood (or more accurately, our estimate of the FSSL for that token) and $\tau$ is a threshold. An adversary sending an accepted token cannot convey more than $\log_{2}|A_{t}(\tau)|$ bits at step $t$, hence the sequence-level capacity is $\sum_{t}\log_{2}|A_{t}(\tau)|$. This converts Theorem [5.1](#S5.Thmtheorem1 "Theorem 5.1. ‣ Rate limitation for the FSSL policy. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") into an operational metric: for any attack, leakage is upper-bounded by the bits available from tokens the verifier would accept. We note that this is an extremely strong bound, and in practice we expect true exfiltration likely to be much lower than this bound.

### 7.1 Problems with FSSL Estimators and Logit-Rank as a Solution

Our FSSL estimates can be thought of as a “suspiciousness” score. In designing a meaningful score for suspiciousness one prefers that the suspiciousness of a token is a continuous score, from “not-suspicious” to “very suspicious”. However, empirically we find that our proposed scoring function (FSSL-GM) is not perfectly calibrated. In Qwen-30B experiments, roughly 0.1% of correctly sampled tokens are labeled _maximally suspicious_, as seen by looking at the middle plot of Figure [8](#S7.F8 "Figure 8 ‣ 7.1 Problems with FSSL Estimators and Logit-Rank as a Solution ‣ 7 Empirical Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), where we see that the ”rank” of the FSSL-GM scores is high (in practice, we see that the sampled tokens are tied for last place with a large number of unlikely tokens).

A simple and effective auxiliary signal is the _logit rank_ of the sampled token (before temperature and top-k/top-p filtering). Empirically, the majority of sampled tokens fall within the top R ($\approx 16$) by raw logits, which we see in the right subplot of Figure [8](#S7.F8 "Figure 8 ‣ 7.1 Problems with FSSL Estimators and Logit-Rank as a Solution ‣ 7 Empirical Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"). Intuitively, this constrains the attacker’s effective alphabet to at most $R$ choices per token position.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img10-210414f6.png]]

Figure 8: Comparison of Token-DiFR (FSSL-GM) verification and raw logit ranks for sampled tokens. Left: Distribution of FSSL-GM scores (log-probabilities) for sampled tokens with $\sigma=1.0$. Middle: Distribution of FSSL-GM ranks, where rank 0 indicates the sampled token has the highest FSSL-GM score. Ranks are grouped as 0–19 individually and $\geq$20 combined; tokens in the $\geq$20 bin are typically tied for last place with many other low-probability tokens (i.e., effective rank $\approx|V|$). Right: Distribution of raw logit ranks (before temperature and top-k/top-p filtering), where rank 0 indicates the token with the highest raw logit. All y-axes use log scale to show the full distribution of percentages.

Augmenting FSSL-GM with a _logit rank_ check yields a strict Pareto improvement over simply thresholding according to the FSSL: for any FSSL threshold $\tau$ and rank cutoff $R$, we introduce a three-class classification

$$\textsc{safe}:\ \mathrm{FSSL}_{t}(i)\!\geq\!\tau \\
\textsc{suspicious}:\ \mathrm{FSSL}_{t}(i)\!<\!\tau\ \wedge\ \mathrm{rank}_{t}(i)\!\leq\!R \\
\textsc{dangerous}:\ \mathrm{FSSL}_{t}(i)\!<\!\tau\ \wedge\ \mathrm{rank}_{t}(i)\!>\!R$$

achieves _lower or equal_ FPR at _lower_ information leakage than FSSL-GM alone. We note that this logit-rank and FSSL score can be combined into a single classifier, e.g. a logistic regression that takes two features: FSSL score and logit-rank. An important advantage to a tiered classification scheme allows to have simpler bounds of extractable information, as there is a trivial upper bound on information expressed by a suspicious (not dangerous) token $I\leq log_{2}(R)\leq log_{2}(|\textrm{vocab size}|)$. As such, given the token-level classifier $C$, the per-token exfiltratable information is:

$$\mathrm{ExfiltratableInformation}(t)=\begin{cases}\log_{2}|A_{t}|,&\text{if }C(t)=\textsc{safe},\\[6.0pt]
\log_{2}R,&\text{if }C(t)=\textsc{suspicious},\\[6.0pt]
\log_{2}|\mathcal{T}|,&\text{if }C(t)=\textsc{dangerous}.\end{cases}$$

##### Experimental Set up

We sample 500 prompts from LMSYS-Chat-1M \[[ZCS+24](#bib.bib38 "LMSYS-chat-1m: a large-scale real-world llm conversation dataset")\], and for each prompt, we generate continuations of max length 500 tokens. We evaluate _Llama-3.2-3B-Instruct_, _Llama-3.1-8B-Instruct_ \[[AI@24](#bib.bib37 "Llama 3 model card")\], _Qwen3-1.5-MoE-A.2-7B_, and _Qwen3-30B-A3B_ \[[YLY+25](#bib.bib35 "Qwen3 technical report")\], served via vLLM.[^6] For all our experiments we use Token-DiFR. We use temperature $T=1.$, top-$k=50$, top-$p=0.95$, and a fixed RNG seed for generation. The verifier shares the tokenizer and chat template with the generator. We sweep over multiple $\sigma$ values (from 0.001 to 1.) for Token-DiFR hyperparameters.

We focus on verifying inference conducted via the standard auto-regressive decoding process. While speculative decoding is increasingly common in practice, our verification pipeline is designed around the traditional decoding setup; we discuss extensions to speculative decoding in Appendix [F.1](#A6.SS1 "F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img11-9d5e64b4.png]]

Figure 9: Headline figure: Pareto frontiers for rank-aware classification thresholds. For logit-Rank=8 as a filtering function to differentiate between suspicious and dangerous tokens. The plot is filtered such that less that 0.5% of tokens are deemed “suspicious”, and only points that are not pareto-dominated by both FPR and exfiltratable information are plotted.

In Section [I.1](#A9.SS1 "I.1 Logit-Rank Ablations ‣ Appendix I Gumbel-Likelihood Score Exfiltration Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), we demonstrate an ablation of these findings and show a robust improvement when introducing logit rank, where if rank =None then all tokens below an FSSL threshold $\tau$ are classified as dangerous. More information on the FSSL-GM scores for different tokens are presented in Appendix [H](#A8 "Appendix H FSSL-GM Score Statistics ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

## 8 Discussion

In this work, we formalize the security game of model weight exfiltration and propose a scheme for detecting steganographic attempts to exfiltrate weights. We provide introduce information theoretic bounds on exfiltratable information, and extend them to the physical world through empirical results with Llama and Qwen models. We find that using our scheme we are able to limit exfiltration to $\leq 0.5\%$ with a minimal FPR. To the authors’ knowledge, no comparable detection and exfiltration bound exists, suggesting a slow down of 200$\times$ in time-to-exfiltrate. If exfiltration were to take 2 days, it now takes over a year.

One critical strength of our proposal is that it requires minimal interaction between the inference stack and the verification server, allowing model providers to largely decouple performance from security. However, one potential way to improve the accuracy of the verification process is to have the inference server sample tokens aware of the verification-process. That is, at inference time, if the inference server computes that there are multiple potential tokens (with high FSSL), choose one according to some deterministic process (e.g. alphabetically). This would further limiting the fixed seed posterior distribution, but would involve some minimal additional computation on the inference stack.

One of core challenges of this proposal is that if an adversary is able to corrupt an inference provider, then meaningful steps must be taken to protect the verification server from the same threat. There are multiple possible solutions to this, depending on the specific threat model an inference provider may have. In the most extreme setting, an inference provider may create a secondary inference stack for verifying inference that is kept in parallel with the main inference stack, it may even run in a Trusted Execution Environment to verify integrity of the computation. In the event that this is too costly for an inference provider to maintain, an earlier code checkpoint from a point prior to when an adversary was known to be in the system, can be used as a reference implementation. Further, the defending the verification server benefits from not having the same performance requirements of the inference stack ; depending on availability constraints, the verification server could even exist in a largely air-gapped format with minimal connection to the inference stack, except at limited times across a secure channel. The fact that verification is much more efficient than generation, and that randomly sampling messages to verify can produce high confidence probabilistic guarantees (Section [D](#A4 "Appendix D Mechanism Design security solutions: Random Sampling and the Panopticon ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")) suggests that the amount of systems-level overhead required to implement a verification server may not be a blocker, if steganography is deemed a meaningful threat.

This system cannot standalone as a method for defending against against model weight exfiltration; in Appendix [L](#A12 "Appendix L Recommended (High-level) Defenses ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), we describe how this scheme fits into a larger outline of defenses to protect model weights. It’s important to note that this scheme does not prevent model weight exfiltration and rather only detects steganographic messages. There are a set of possible security responses in response to suspicious tokens; for example, tokens deemed suspicious can be logged and aggregated to look for potentially malicious patterns by an adversary. Alternatively, outbound traffic can be gated by this verification server, and when failing verification, inference is regenerated and tried again. It is possible to rate limit users (or GPUs) proportional to the number of tokens that they produce that are deemed suspicious. We give a more complete discussion of policy recommendations of how this scheme fits into a larger scheme of in Appendix [G](#A7 "Appendix G Response to Detecting Exfiltration Attempts ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

Overall, this work establishes a concrete foundation for reasoning about and detecting model weight exfiltration through steganographic channels. By combining formal security analysis with an efficient, empirically validated verification scheme, we demonstrate that meaningful protection against inference-time exfiltration is both achievable and practical for large-scale model deployments.

## 9 Acknowledgements

We thank Miranda Christ for early conversations that helped frame the problem and for her foundational explanations of watermarking and steganography in generative AI. We are grateful to Nicholas Carlini for his thoughtful comments during this work. We also thank Jacob Lagerros for his valuable discussions, feedback on the paper, and practical insights drawn from implementing the proposed scheme in real-world settings.

Some of this work was conducted while AK, DR, and RR were participating in the ML Alignment and Theory Scholars (MATS) program, whose support we gratefully acknowledge. RR was supported in part by the NSF BCS-2218803 grant, as well as additionally supported by a grant from Coefficient Giving.

## References

-   \[AARve\] S. Aaronson (November 2022) My AI safety lecture for ut effective altruism. External Links: [Link](https://scottaaronson.blog/?p=6823) Cited by: [§2.1](#S2.SS1.SSS0.Px2.p3.1 "Watermarking. ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[AI@24\] AI@Meta (2024) Llama 3 model card. External Links: [Link](https://github.com/meta-llama/llama3/blob/main/MODEL_CARD.md) Cited by: [§7.1](#S7.SS1.SSS0.Px1.p1.4 "Experimental Set up ‣ 7.1 Problems with FSSL Estimators and Logit-Rank as a Solution ‣ 7 Empirical Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[AP02\] R. J. Anderson and F. A. Petitcolas (2002) On the limits of steganography. IEEE Journal on selected areas in communications 16 (4), pp. 474–481. Cited by: [Appendix B](#A2.p3.1 "Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[ANT25\] Anthropic (2025-05) Activating ai safety level 3 protections. Note: [https://www.anthropic.com/news/activating-asl3-protections](https://www.anthropic.com/news/activating-asl3-protections)Online, published May 22, 2025 Cited by: [Figure 27](#A12.F27 "In L.1 More Concrete Recommendations ‣ Appendix L Recommended (High-level) Defenses ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [Figure 27](#A12.F27.3.2 "In L.1 More Concrete Recommendations ‣ Appendix L Recommended (High-level) Defenses ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[BTZ+25\] Y. Bai, S. Tu, J. Zhang, H. Peng, X. Wang, X. Lv, S. Cao, J. Xu, L. Hou, Y. Dong, J. Tang, and J. Li (2025) LongBench v2: towards deeper understanding and reasoning on realistic long-context multitasks. External Links: 2412.15204, [Link](https://arxiv.org/abs/2412.15204) Cited by: [§I.2](#A9.SS2.p1.1 "I.2 Context Length Ablations ‣ Appendix I Gumbel-Likelihood Score Exfiltration Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[BR93\] M. Bellare and P. Rogaway (1993) Random oracles are practical: a paradigm for designing efficient protocols. In Proceedings of the 1st ACM Conference on Computer and Communications Security, CCS ’93, New York, NY, USA, pp. 62–73. External Links: ISBN 0897916298, [Link](https://doi.org/10.1145/168588.168596), [Document](https://dx.doi.org/10.1145/168588.168596) Cited by: [§4.1](#S4.SS1.p5.12 "4.1 Security Game ‣ 4 Formulating the Model Weight Exfiltration Security Game ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[CZL+25\] B. Chen, M. Zheng, T. Liu, R. Piskac, and Z. Shao (2025) ZkTorch: privacy-preserving deep learning with zero-knowledge proofs. External Links: 2502.00226, [Link](https://arxiv.org/abs/2502.00226) Cited by: [§2.3](#S2.SS3.p2.1 "2.3 Inference Verification ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[CBI+23\] C. Chen, S. Borgeaud, G. Irving, J. Lespiau, L. Sifre, and J. Jumper (2023) Accelerating large language model decoding with speculative sampling. External Links: 2302.01318, [Link](https://arxiv.org/abs/2302.01318) Cited by: [§F.1](#A6.SS1.SSS0.Px1.p1.1 "Background: A Speculative Decoding Algorithm ‣ F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§F.1](#A6.SS1.p1.1 "F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[CGZ24\] M. Christ, S. Gunn, and O. Zamir (2024-30 Jun–03 Jul) Undetectable watermarks for language models. In Proceedings of Thirty Seventh Conference on Learning Theory, S. Agrawal and A. Roth (Eds.), Proceedings of Machine Learning Research, Vol. 247, pp. 1125–1139. External Links: [Link](https://proceedings.mlr.press/v247/christ24a.html) Cited by: [§I.3](#A9.SS3.p2.1 "I.3 Relationship to watermarking. ‣ Appendix I Gumbel-Likelihood Score Exfiltration Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§2.1](#S2.SS1.SSS0.Px2.p3.1 "Watermarking. ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[CG24\] M. Christ and S. Gunn (2024) Pseudorandom error-correcting codes. Note: Cryptology ePrint Archive, Paper 2024/235 External Links: [Link](https://eprint.iacr.org/2024/235) Cited by: [§E.5](#A5.SS5.SSS0.Px2.p1.1 "Rationale. ‣ E.5 Assumption 5: The randomness used for inference is trusted and non-malleable ‣ Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§E.5](#A5.SS5.p1.1 "E.5 Assumption 5: The randomness used for inference is trusted and non-malleable ‣ Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§2.1](#S2.SS1.SSS0.Px2.p3.1 "Watermarking. ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[CHS25\] A. Cohen, A. Hoover, and G. Schoenbach (2025-05) Watermarking Language Models for Many Adaptive Users . In 2025 IEEE Symposium on Security and Privacy (SP), Vol. , Los Alamitos, CA, USA, pp. 84–84. External Links: ISSN 2375-1207, [Document](https://dx.doi.org/10.1109/SP61157.2025.00084), [Link](https://doi.ieeecomputersociety.org/10.1109/SP61157.2025.00084) Cited by: [§I.3](#A9.SS3.p2.1 "I.3 Relationship to watermarking. ‣ Appendix I Gumbel-Likelihood Score Exfiltration Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§2.1](#S2.SS1.SSS0.Px2.p3.1 "Watermarking. ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[ERD25\] E. Erdil (2025) Inference economics of language models. External Links: 2506.04645, [Link](https://arxiv.org/abs/2506.04645) Cited by: [§3.1](#S3.SS1.SSS0.Px1.p1.1 "Decode versus prefill. ‣ 3.1 Basic Setting (LLM inference) ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§6.1](#S6.SS1.p1.2 "6.1 The Cost of Verification versus Generation ‣ 6 Implementing a Verification Server ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[FGJ+25\] J. Fairoze, S. Garg, S. Jha, S. Mahloujifar, M. Mahmoody, and M. Wang (2025-01-13) Publicly-detectable watermarking for language models. IACR Communications in Cryptology 1 (4). External Links: ISSN 3006-5496, [Document](https://dx.doi.org/10.62056/ahmpdkp10) Cited by: [§2.1](#S2.SS1.SSS0.Px2.p3.1 "Watermarking. ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[GLG25\] I. Gao, P. Liang, and C. Guestrin (2025) Model equality testing: which model is this api serving?. External Links: 2410.20247, [Link](https://arxiv.org/abs/2410.20247) Cited by: [§2.3](#S2.SS3.p4.1 "2.3 Inference Verification ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[GKV+24\] S. Goldwasser, M. P. Kim, V. Vaikuntanathan, and O. Zamir (2024) Planting undetectable backdoors in machine learning models. External Links: 2204.06974, [Link](https://arxiv.org/abs/2204.06974) Cited by: [§E.5](#A5.SS5.SSS0.Px2.p1.1 "Rationale. ‣ E.5 Assumption 5: The randomness used for inference is trusted and non-malleable ‣ Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§E.5](#A5.SS5.p1.1 "E.5 Assumption 5: The randomness used for inference is trusted and non-malleable ‣ Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[GM25\] N. Golowich and A. Moitra (2025) Edit distance robust watermarks via indexing pseudorandom codes. External Links: 2406.02633, [Link](https://arxiv.org/abs/2406.02633) Cited by: [§2.1](#S2.SS1.SSS0.Px2.p3.1 "Watermarking. ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[HL25\] H. He and T. M. Lab (2025) Defeating nondeterminism in llm inference. Thinking Machines Lab: Connectionism. Note: https://thinkingmachines.ai/blog/defeating-nondeterminism-in-llm-inference/ External Links: [Document](https://dx.doi.org/10.64434/tml.20250910) Cited by: [§3.3](#S3.SS3.p1.2 "3.3 Non-determinism in Machine Learning ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[HLV02\] N. J. Hopper, J. Langford, and L. Von Ahn (2002) Provably secure steganography. In Annual International Cryptology Conference, pp. 77–92. Cited by: [§B.0.1](#A2.SS0.SSS1.p3.6 "B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [Theorem B.3](#A2.Thmtheorem3 "Theorem B.3 (Due to [HLV02]). ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [Appendix B](#A2.p3.1 "Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§5.3](#S5.SS3.SSS0.Px4.p1.1 "Tightness of the bounds ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KJG+21\] G. Kaptchuk, T. M. Jois, M. Green, and A. D. Rubin (2021) Meteor: cryptographically secure steganography for realistic distributions. In Proceedings of the 2021 ACM SIGSAC Conference on Computer and Communications Security, CCS ’21, New York, NY, USA, pp. 1529–1548. External Links: ISBN 9781450384544, [Link](https://doi.org/10.1145/3460120.3484550), [Document](https://dx.doi.org/10.1145/3460120.3484550) Cited by: [§2.1](#S2.SS1.SSS0.Px2.p4.1 "Watermarking. ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KRR+25\] A. Karvonen, D. Reuter, R. Rinberg, L. Marks, A. Garriga-Alonso, and K. Warr (2025) DiFR: inference verification despite nondeterminism. External Links: 2511.20621, [Link](https://arxiv.org/abs/2511.20621) Cited by: [§1](#S1.p5.1 "1 Introduction ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§2.3](#S2.SS3.p5.1 "2.3 Inference Verification ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§6.2](#S6.SS2.p1.1 "6.2 Inverse Probability Transform Scoring Function Token-IPT-DiFR ‣ 6 Implementing a Verification Server ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§6.3](#S6.SS3.p1.1 "6.3 Gumbel-Max Scoring Function Token-DiFR ‣ 6 Implementing a Verification Server ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KAR24\] A. Karvonen (2024)Using an llm perplexity filter to detect weight exfiltration(Website) Note: LessWrong, accessed October 6, 2025 External Links: [Link](https://www.lesswrong.com/posts/aWZEDw6oxR6Wk5hru/using-an-llm-perplexity-filter-to-detect-weight-exfiltration) Cited by: [§2.4](#S2.SS4.p3.1 "2.4 Existing Model Weight Exfiltration Detection methods ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KL14\] J. Katz and Y. Lindell (2014) Introduction to modern cryptography. Third edition, Chapman and Hall, CRC Press. External Links: ISBN 978-0815354369 Cited by: [§2.1](#S2.SS1.SSS0.Px1.p3.1 "Steganography ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KER07\] A. D. Ker (2007) Batch steganography and pooled steganalysis. In Information Hiding, J. L. Camenisch, C. S. Collberg, N. F. Johnson, and P. Sallee (Eds.), Berlin, Heidelberg, pp. 265–281. External Links: ISBN 978-3-540-74124-4 Cited by: [Appendix G](#A7.p1.1 "Appendix G Response to Detecting Exfiltration Attempts ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KP12\] A. D. Ker and T. Pevny (2012) Batch steganography in the real world. In Proceedings of the on Multimedia and Security, MM&Sec ’12, New York, NY, USA, pp. 1–10. External Links: ISBN 9781450314176, [Link](https://doi.org/10.1145/2361407.2361409), [Document](https://dx.doi.org/10.1145/2361407.2361409) Cited by: [Appendix G](#A7.p1.1 "Appendix G Response to Detecting Exfiltration Attempts ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KGW+23a\] J. Kirchenbauer, J. Geiping, Y. Wen, J. Katz, I. Miers, and T. Goldstein (2023) A watermark for large language models. External Links: 2301.10226 Cited by: [§I.3](#A9.SS3.p2.1 "I.3 Relationship to watermarking. ‣ Appendix I Gumbel-Likelihood Score Exfiltration Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KGW+23b\] J. Kirchenbauer, J. Geiping, Y. Wen, J. Katz, I. Miers, and T. Goldstein (2023-23–29 Jul) A watermark for large language models. In Proceedings of the 40th International Conference on Machine Learning, A. Krause, E. Brunskill, K. Cho, B. Engelhardt, S. Sabato, and J. Scarlett (Eds.), Proceedings of Machine Learning Research, Vol. 202, pp. 17061–17084. External Links: [Link](https://proceedings.mlr.press/v202/kirchenbauer23a.html) Cited by: [§2.1](#S2.SS1.SSS0.Px2.p3.1 "Watermarking. ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KTH+23\] R. Kuditipudi, J. Thickstun, T. Hashimoto, and P. Liang (2023) Robust distortion-free watermarks for language models. External Links: 2307.15593 Cited by: [§2.1](#S2.SS1.SSS0.Px2.p3.1 "Watermarking. ‣ 2.1 Steganography and Watermarking ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[KLZ+23\] W. Kwon, Z. Li, S. Zhuang, Y. Sheng, L. Zheng, C. H. Yu, J. E. Gonzalez, H. Zhang, and I. Stoica (2023) Efficient memory management for large language model serving with pagedattention. External Links: 2309.06180, [Link](https://arxiv.org/abs/2309.06180) Cited by: [Appendix F](#A6.p3.1 "Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§3.2](#S3.SS2.p1.12 "3.2 Sampling From Large Language Models ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[LKM23\] Y. Leviathan, M. Kalman, and Y. Matias (2023) Fast inference from transformers via speculative decoding. External Links: 2211.17192, [Link](https://arxiv.org/abs/2211.17192) Cited by: [§F.1](#A6.SS1.SSS0.Px1.p1.1 "Background: A Speculative Decoding Algorithm ‣ F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§F.1](#A6.SS1.SSS0.Px1.p2.1 "Background: A Speculative Decoding Algorithm ‣ F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§F.1](#A6.SS1.p1.1 "F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[LWZ+25\] Y. Li, F. Wei, C. Zhang, and H. Zhang (2025) EAGLE-3: scaling up inference acceleration of large language models via training-time test. External Links: 2503.01840, [Link](https://arxiv.org/abs/2503.01840) Cited by: [§F.1](#A6.SS1.SSS0.Px1.p2.1 "Background: A Speculative Decoding Algorithm ‣ F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§F.1](#A6.SS1.p1.1 "F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[NLK+24\] S. Nevo, D. Lahav, A. Karpur, Y. Bar-On, H. A. Bradley, and J. Alstott (2024) Securing ai model weights: preventing theft and misuse of frontier models. Research Report Technical Report RR A2849-1, RAND Corporation, Santa Monica, CA. Cited by: [§1](#S1.p2.1 "1 Introduction ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§2.2](#S2.SS2.p1.1 "2.2 Model Weight Exfiltration ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[32\] Ollama Ollama documentation. Note: [https://docs.ollama.com/](https://docs.ollama.com/)Accessed: 2025-10-06 Cited by: [Appendix F](#A6.p3.1 "Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), [§3.2](#S3.SS2.p1.12 "3.2 Sampling From Large Language Models ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[OFP+25\] J. M. Ong, M. D. Ferrante, A. Pazdera, R. Garner, S. Jaghouar, M. Basra, M. Ryabinin, and J. Hagemann (2025) TOPLOC: a locality sensitive hashing scheme for trustless verifiable inference. External Links: 2501.16007, [Link](https://arxiv.org/abs/2501.16007) Cited by: [§2.3](#S2.SS3.p3.2 "2.3 Inference Verification ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[So59\] C. E. Shannon et al. (1959) Coding theorems for a discrete source with a fidelity criterion. IRE Nat. Conv. Rec 4 (142-163), pp. 1. Cited by: [§B.0.1](#A2.SS0.SSS1.1.p1.15 "Proof. ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[SHA48\] C. E. Shannon (1948) A mathematical theory of communication. The Bell system technical journal 27 (3), pp. 379–423. Cited by: [§B.0.1](#A2.SS0.SSS1.1.p1.15 "Proof. ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[SVS+25\] A. Singh, F. Virga, S. Smith, and S. Hogan (2025) LOGIC: Trustless Inference through Log-Probability Verification. Note: [https://inference.net/blog/logic](https://inference.net/blog/logic)Context Labs Blog, November 5, 2025 Cited by: [§2.3](#S2.SS3.p3.2 "2.3 Inference Verification ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[SLZ24\] H. Sun, J. Li, and H. Zhang (2024) ZkLLM: zero knowledge proofs for large language models. External Links: 2404.16109, [Link](https://arxiv.org/abs/2404.16109) Cited by: [§2.3](#S2.SS3.p2.1 "2.3 Inference Verification ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[VH04\] L. Von Ahn and N. J. Hopper (2004) Public-key steganography. In International Conference on the Theory and Applications of Cryptographic Techniques, pp. 323–341. Cited by: [Appendix B](#A2.p3.1 "Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[WIL25\] S. Willison (2025-08) Open weight llms exhibit inconsistent performance across providers. Note: _Simon Willison’s Weblog_Accessed 2025-10-15 External Links: [Link](https://simonwillison.net/2025/Aug/15/inconsistent-performance/) Cited by: [§3.3](#S3.SS3.p2.1 "3.3 Non-determinism in Machine Learning ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[WDS+20\] T. Wolf, L. Debut, V. Sanh, J. Chaumond, C. Delangue, A. Moi, P. Cistac, T. Rault, R. Louf, M. Funtowicz, J. Davison, S. Shleifer, P. von Platen, C. Ma, Y. Jernite, J. Plu, C. Xu, T. L. Scao, S. Gugger, M. Drame, Q. Lhoest, and A. M. Rush (2020-10) Transformers: state-of-the-art natural language processing. In Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing: System Demonstrations, Online, pp. 38–45. External Links: [Link](https://www.aclweb.org/anthology/2020.emnlp-demos.6) Cited by: [§3.2](#S3.SS2.p1.12 "3.2 Sampling From Large Language Models ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[YLY+25\] A. Yang, A. Li, B. Yang, B. Zhang, B. Hui, B. Zheng, B. Yu, C. Gao, C. Huang, C. Lv, C. Zheng, D. Liu, F. Zhou, F. Huang, F. Hu, H. Ge, H. Wei, H. Lin, J. Tang, J. Yang, J. Tu, J. Zhang, J. Yang, J. Yang, J. Zhou, J. Zhou, J. Lin, K. Dang, K. Bao, K. Yang, L. Yu, L. Deng, M. Li, M. Xue, M. Li, P. Zhang, P. Wang, Q. Zhu, R. Men, R. Gao, S. Liu, S. Luo, T. Li, T. Tang, W. Yin, X. Ren, X. Wang, X. Zhang, X. Ren, Y. Fan, Y. Su, Y. Zhang, Y. Zhang, Y. Wan, Y. Liu, Z. Wang, Z. Cui, Z. Zhang, Z. Zhou, and Z. Qiu (2025) Qwen3 technical report. External Links: 2505.09388, [Link](https://arxiv.org/abs/2505.09388) Cited by: [§7.1](#S7.SS1.SSS0.Px1.p1.4 "Experimental Set up ‣ 7.1 Problems with FSSL Estimators and Logit-Rank as a Solution ‣ 7 Empirical Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[YLD+25\] J. Yuan, H. Li, X. Ding, W. Xie, Y. Li, W. Zhao, K. Wan, J. Shi, X. Hu, and Z. Liu (2025) Give me fp32 or give me death? challenges and solutions for reproducible reasoning. External Links: 2506.09501, [Link](https://arxiv.org/abs/2506.09501) Cited by: [§3.4](#S3.SS4.p1.3 "3.4 Valid Non-determinism with a Fixed Seed: The Fixed-Seed Posterior Distribution ‣ 3 LLM Inference Preliminaries ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[ZWH+25\] L. Zhang, X. Wang, Y. Huang, and R. Xu (2025) Learning harmonized representations for speculative sampling. External Links: 2408.15766, [Link](https://arxiv.org/abs/2408.15766) Cited by: [§F.1](#A6.SS1.p1.1 "F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[ZCS+24\] L. Zheng, W. Chiang, Y. Sheng, T. Li, S. Zhuang, Z. Wu, Y. Zhuang, Z. Li, Z. Lin, E. P. Xing, J. E. Gonzalez, I. Stoica, and H. Zhang (2024) LMSYS-chat-1m: a large-scale real-world llm conversation dataset. External Links: 2309.11998, [Link](https://arxiv.org/abs/2309.11998) Cited by: [§7.1](#S7.SS1.SSS0.Px1.p1.4 "Experimental Set up ‣ 7.1 Problems with FSSL Estimators and Logit-Rank as a Solution ‣ 7 Empirical Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
-   \[ZYQ+25\] X. Zhu, Y. Ye, T. Qiu, H. Zhu, S. Tan, A. Mannan, J. Michala, R. A. Popa, and W. Neiswanger (2025) Auditing black-box llm apis with a rank-based uniformity test. External Links: 2506.06975, [Link](https://arxiv.org/abs/2506.06975) Cited by: [§2.3](#S2.SS3.p4.1 "2.3 Inference Verification ‣ 2 Related Works ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

## Appendix A Appendix

## Appendix B Steganography Syntax and Relevant Results

In this section, we review some relevant notation, concepts, and terms that are used to understand steganographic protocols. We also reprove some well known results that support our own theorems in the main body of the paper.

###### Definition B.1 (Steganographic Scheme).

Let $\ell_{\mathrm{msg}},\ell_{\mathrm{cov}}\in\mathbb{N}$ be integers and $\mathcal{T}$ be a set of tokens (a.k.a. vocabulary or alphabet). Let $\mathcal{D}$ be the passive channel distribution with support $X\subseteq\mathcal{T}^{\leq\ell_{\mathrm{cov}}}$. A _steganography scheme for $\mathcal{D}$_ is a pair of stateful (possibly randomized) algorithms $\mathsf{Steg}=(\mathsf{Enc},\mathsf{Dec})$ with the following syntax:

-   •
    
    $\mathsf{Enc}(K,\mathsf{st},m)\to c$, takes a key $K\in\{0,1\}^{\lambda}$, a state $\mathsf{st}$, a message $m\in\{0,1\}^{\leq\ell_{\mathrm{msg}}}$ and outputs a covertext $c\in\mathcal{T}^{\leq\ell_{\mathrm{cov}}}$.
    
-   •
    
    $\mathsf{Dec}(K,\mathsf{st},c)\to m$, takes a key $K\in\{0,1\}^{\lambda}$, a state $\mathsf{st}$, a covertext $c\in\mathcal{T}^{\leq\ell_{\mathrm{cov}}}$ and outputs a message $m\in\{0,1\}^{\leq\ell_{\mathrm{msg}}}$.
    

For a steganography scheme to be useful, it must be _correct_, meaning that for every $\mathsf{st}$ and $m$, $\Pr_{K}[\mathsf{Dec}(K,\mathsf{st},\mathsf{Enc}(K,\mathsf{st},m))=m]=1-\mathrm{negl}(\lambda).$ When, this probability is $1$, we say the scheme is _perfectly correct_. It must also be _secure_, meaning that for any $\mathsf{st}$ and $m$, $D_{\mathrm{KL}}(\mathcal{D}_{\mathsf{Steg}}\|\mathcal{D})=\mathrm{negl}(\lambda),$ where $\mathcal{D}_{\mathsf{Steg}}$ is the covertext distribution generated as $K\overset{{\scriptscriptstyle\mathdollar}}{\leftarrow}\{0,1\}^{\lambda}$ and $c\overset{{\scriptscriptstyle\mathdollar}}{\leftarrow}\mathsf{Enc}(K,\mathsf{st},m)$.

The principal measure of efficiency that we are interested in is the _rate_ of a scheme $\mathsf{Steg}$. This is defined as the message length $\ell_{\mathrm{msg}}$ divided by the average covertext length, which we calculate as $\mathbb{E}_{c\sim\mathcal{D}}[|c|]$, since a secure scheme cannot differ significantly from this expectation.[^7] Therefore, we write $R=\ell_{\mathrm{msg}}/\mathbb{E}_{c\sim\mathcal{D}}[|c|]$.

Note that there are many other variants of steganography, including stateless, public-key, robust, etc. \[[AP02](#bib.bib204 "On the limits of steganography"), [HLV02](#bib.bib203 "Provably secure steganography"), [VH04](#bib.bib205 "Public-key steganography")\]. However, in our context, we wish to give a potential exfiltrator as much theoretical power as possible. So we assume that both endpoints are stateful and can have an arbitrarily long secret key in common.

#### B.0.1 Relevant Results in Steganography

The _capacity_ of a steganography distribution $\mathcal{D}$ is defined as the maximum rate $R$ achievable by a steganography scheme $\mathsf{Steg}$ that is both correct and secure, asymptotically over many runs of the scheme. One well-known result is that this capacity is at most $H(\mathcal{D})/\mathbb{E}_{c\sim\mathcal{D}}[|c|]$ for perfectly secret and correct schemes.

More generally, when a scheme $\mathsf{Steg}$ outputs a distribution $\mathcal{D}_{\mathsf{Steg}}$ with $D_{\mathrm{KL}}(\mathcal{D}_{\mathsf{Steg}}||\mathcal{D})<o(1)$ which may not perfectly match the perfect cover distribution, then the capacity is bounded by $\big(H(\mathcal{D}_{\mathsf{Steg}})-D_{\mathrm{KL}}(\mathcal{D}_{\mathsf{Steg}}||\mathcal{D})\big)/\mathbb{E}_{c\sim\mathcal{D}}[|c|]$ against information-theoretic adversaries.

###### Theorem B.2 (Steganographic limitations).

Let $\mathsf{Steg}$ be a steganography scheme for $\mathcal{D}$ and $\mathbf{M}$ be a random variable with $H(\mathbf{M})=\ell$. Let $\mathcal{D}_{\mathsf{Steg}}$ be the covertext distribution generated as $K\overset{{\scriptscriptstyle\mathdollar}}{\leftarrow}\{0,1\}^{\lambda}$ and $c\overset{{\scriptscriptstyle\mathdollar}}{\leftarrow}\mathsf{Enc}(K,\mathsf{st},\mathbf{M})$. Then, $\mathsf{Steg}$ cannot be perfectly correct if $\ell>\lceil H(\mathcal{D}_{\mathsf{Steg}})\rceil.$

###### Proof.

This theorem is an immediate consequence of Shannon’s source coding theorem \[[SHA48](#bib.bib201 "A mathematical theory of communication"), [So59](#bib.bib202 "Coding theorems for a discrete source with a fidelity criterion")\]. This theorem states: (i) that no random variable $X$ can be encoded with fewer bits than $H(X)$ in expectation and (ii) that there exists an encoding of $X$ with expected length at most $\lceil H(X)\rceil$. Therefore, if $\lceil H(\mathcal{D}_{\mathsf{Steg}})\rceil<H(\mathbf{M})$ and $\mathsf{Steg}$ is correct with probability $1$, then one could encode $\mathbf{M}$ as the covertext, using a random key $K$ and random state $\mathsf{st}$, $\mathbf{C}\leftarrow\mathsf{Enc}(K,\mathsf{st},\mathbf{M})$ and decoded with $\mathsf{Dec}(K,\mathsf{st},\mathbf{C})$. Then, based on the source coding theorem, $\mathbf{C}\sim\mathcal{D}_{\mathsf{Steg}}$ (and therefore $\mathbf{M}$) can be encoded with $\lceil H(\mathcal{D}_{\mathsf{Steg}})\rceil<H(\mathbf{M})$ bits, which is a direct contradiction. ∎

In contrast to the above theorem and to illustrate the difficulty of preventing covert exfiltration, we recall a well-known theorem from \[[HLV02](#bib.bib203 "Provably secure steganography")\] stated in Theorem [B.3](#A2.Thmtheorem3 "Theorem B.3 (Due to [HLV02]). ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"). This shows that assuming classical cryptography exists at all, i.e., one-way functions exist, then one can construct a steganographic scheme that is near-optimal. The following theorem shows that there is some steganographic scheme which fools any efficient _policy_ under minimal assumptions. Here and the rest of the paper, a policy is a function $\mathcal{W}:X(\mathcal{D})\to\{0,1\}$, which aims to output $1$ on covertexts generated steganographically but not on samples from the honest distribution. We say that $\mathcal{W}$ has a false positive rate $\alpha$ over $\mathcal{D}$ if $\Pr_{x\sim\mathcal{D}}[\mathcal{W}(x)=1]=\alpha$.

###### Theorem B.3 (Due to \[[HLV02](#bib.bib203 "Provably secure steganography")\]).

Let $\mathcal{W}$ be an efficiently-computable policy with a false positive rate $\alpha$ over $\mathcal{D}$. Then, assuming a $\delta$\-secure pseudorandom function $\mathsf{PRF}$ exists, there is an inefficient steganography scheme $\mathsf{Steg}$ for $\mathcal{D}$ which, on every message that is $H_{\mathrm{min}}(\mathcal{D})-O(\log(1/\varepsilon))$ bits long, is correct with probability at least $1-\varepsilon$ and is caught with probability at most $\alpha+\delta$ by $\mathcal{W}$.

Finally, we state a known result from information theory in Theorem [B.4](#A2.Thmtheorem4 "Theorem B.4 (Capacity limitations). ‣ B.0.1 Relevant Results in Steganography ‣ Appendix B Steganography Syntax and Relevant Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"). This result gives a lower bound on the number of messages that must be sent through independent channels, each of capacity $C$. This is a useful result to recall for the bounds we derive later in Section [5.3](#S5.SS3 "5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

###### Theorem B.4 (Capacity limitations).

Let $X$ be a uniform random variable with support of size $q$ (so that $H(X)=\log q$) and $Y^{n}$ be $n$ messages sent through a channel of capacity $C$. Then, in order to transmit $X$ with error at most $\varepsilon$, requires that $n\geq\big(\log q-h(\varepsilon)-\varepsilon\log(q-1)\big)/C.$ Notably, when $Y$ has alphabet size $q^{\prime}$ and is uniformly random with probability $p$, then we obtain

$$n\geq\frac{\log q-h(\varepsilon)-\varepsilon\log(q-1)}{\log q^{\prime}-h(p)-p\log(q^{\prime}-1)}.$$

###### Proof.

For two jointly distributed variables $(X,Y^{n})\sim\mathcal{D}$ and any function $f$, let $E$ be the event that $X\neq\tilde{X}$, where $(X,Y^{n})\sim\mathcal{D}$ and $\tilde{X}=f(Y^{n})$. Then,

$$H(X\mid Y^{n})\leq h(\Pr[E])+\Pr[E]\cdot\log(q-1).$$

Using the mutual information between $X$ and $Y^{n}$,

$$I(X;Y^{n})=H(X)-H(X\mid Y^{n})\geq\log q-(h(\Pr[E])+\Pr[E]\cdot\log(q-1)).$$

And, any encoding scheme that uses a (memoryless) channel $n$ times, $I(X;Y^{n})\leq nC$. Combining these and using target error rate $\Pr[E]=\varepsilon$, we establish the claimed bound

$$\log q-(h(\varepsilon)+\varepsilon\cdot\log(q-1))\leq I(X;Y^{n})\leq nC.$$

Finally, the further claim comes from the fact that the maximum capacity for a channel with alphabet size $q^{\prime}$ and which is uniformly random with probability $p$ is $C=\log q^{\prime}-h(p)-p\log(q^{\prime}-1).$ ∎

## Appendix C Algorithms

### C.1 Inverse Probability Transform (IPT) Fixed-Seed Sampling Likelihood (FSSL) Estimators

Algorithm 3 Token-IPT-DiFR (from model $\theta$ and context $\mathcal{H}$)

1:model parameters $\theta$;token probabilities $p\in\Delta^{|\mathcal{T}|}$; observed token $t^{\star}\in\{1,\dots,|\mathcal{T}|\}$; seed $\mathsf{seed}$; context position $i$; width $\sigma>0$; small $\varepsilon>0$

2:$\mu\leftarrow\mathrm{Uniform}(0,1;\mathsf{H}(\mathsf{seed}\|i))$ $\triangleright$ (1) sample random value in $[0,1]$

3:$p\leftarrow\mathrm{PredictTokenProbs}(\theta,x_{1:t-1})$ $\triangleright$ $p\in\Delta^{|\mathcal{T}|}$; include same temperature/top-$k$/nucleus policy as generation

4:$\bar{F}\leftarrow\mathrm{concat}(0,\ \mathrm{cumsum}(p))$ $\triangleright$ token CDF with $\bar{F}_{0}=0$, $\bar{F}_{j}=\sum_{i\leq j}p_{i}$

5:$a\leftarrow\bar{F}_{\,t^{\star}-1}$,  $b\leftarrow\bar{F}_{\,t^{\star}}$ $\triangleright$ start/stop of $t^{\star}$’s interval

6:$\Phi(u;\mu,\sigma)\leftarrow\tfrac{1}{2}\!\left[1+\mathrm{erf}\!\big(\tfrac{u-\mu}{\sqrt{2}\sigma}\big)\right]$ $\triangleright$ Gaussian CDF

7:$\text{mass}\leftarrow\Phi(b;x,\sigma)-\Phi(a;x,\sigma)$ $\triangleright$ (3) integral of Gaussian over $[a,b]$

8:$S\leftarrow\log(\text{mass}+\varepsilon)$ $\triangleright$ (4) return log-score of observed token

9:return $S$

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img12-dcb35aef.png]]

Figure 10: Diagram of the Token-IPT-DiFR method. The Token-IPT-DiFR estimates the likelihood of a token under the inverse probability transform by integrating a Gaussian over the token’s probability interval.

### C.2 Gumbel-Max FSSLEstimators (FSSL-GM)

Algorithm 4 Token-DiFR(used to estimate FSSL-GM)

1:Input: Claimed token $t^{*}\in\mathcal{T}$, verifier logits $\hat{\ell}\in\mathbb{R}^{|\mathcal{T}|}$, Seed $\mathsf{seed}$, temperature $T$, filtering parameters $(k,p)$, active subset size $s$, noise CDFs/PDF $\{F_{\varepsilon_{i}},f_{\varepsilon_{t^{*}}}\}$, number of samples $M$

2:Output: Likelihood estimate $\hat{\pi}_{t^{*}}\in[0,1]$

3:

4:Sample Gumbel noise $G_{\mathsf{seed},i}\sim\text{Gumbel}(0,1;\mathsf{H}(\mathsf{seed}\|i))$ for $i=1,\ldots,|\mathcal{T}|$

5:$S\leftarrow\{i_{1},\ldots,i_{s}\}$ where $i_{j}$ are top-$s$ indices as ranked by $\hat{\ell}_{i}+T\cdot G_{\mathsf{seed},i}$

6:

7:$\tau\leftarrow\min_{i\in\{1,\ldots,|\mathcal{T}|\}}\hat{\ell}_{i}$ such that $i$ does not satisfy top-$k$ or top-$p$ filter

8:

9:for each token $i\in S$ do

10:  $A_{\mathsf{seed},i}\leftarrow\hat{\ell}_{t^{*}}-\hat{\ell}_{i}+T(G_{\mathsf{seed},t^{*}}-G_{\mathsf{seed},i})$

11:  $B_{i}\leftarrow\tau-\hat{\ell}_{i}$

12:end for

13:

14:$\hat{\pi}_{t^{*}}\leftarrow 0$

15:for $j=1$ to $M$ do

16:  Sample $x_{j}\sim f_{\varepsilon_{t^{*}}}$

17:  if $\hat{\ell}_{t^{*}}+x_{j}>\tau$ then

18:   $\pi_{t^{*},j}\leftarrow\prod_{i\in S}F_{\varepsilon_{i}}\left(\max(x_{j}+A_{\mathsf{seed},i},B_{i})\right)$

19:   $\hat{\pi}_{t^{*}}\leftarrow\hat{\pi}_{t^{*}}+\pi_{t^{*},j}$

20:  end if

21:end for

22:return $\hat{\pi}_{t^{*}}/M$

### C.3 Naive Methods for Sampled Token Verification

Algorithm 5 Sampled token verification through teacher forcing

1:input sequence $\mathcal{H}$, target output sequence $y$, seed $\mathsf{seed}$, model $\theta$

2:$\text{diff}\leftarrow 0$

3:for $i\leftarrow 1$ to $|y|$ do

4:  $\;\;\;\text{next}\leftarrow\text{SampleNextToken}(\theta,\mathcal{H};\mathsf{H}(\mathsf{seed}\|i))$

5:  if $\text{next}=y_{i}$ then

6:   $\;\;\;\;\text{diff}\leftarrow\text{diff}+1$

7:  end if

8:  $\;\;\;\mathcal{H}\leftarrow\mathcal{H}\|y_{i}$ $\triangleright$ teacher forcing: append ground-truth token

9:end for

10:$\text{score}\leftarrow\dfrac{\text{diff}}{|y|}$

11:return $\text{diff},\ \text{score}$

Algorithm 6 Sampled token verification via prefill

1:input sequence $x$, target output $y=(y_{1},\dots,y_{T})$, seed $\mathsf{seed}$, model $\theta$

2:$z\leftarrow x\circ y$ $\triangleright$ concatenate input and full target for caching

3:$\ell_{0:|z|-1}\leftarrow\text{Prefill}(\theta,z)$ $\triangleright$ single forward pass; next-token logits at each position

4:$\text{diff}\leftarrow 0$

5:for $i\leftarrow 1$ to $T$ do $\triangleright$ predict $y_{i}$ from context $x\circ y_{<i}$

6:  $p_{i}\leftarrow\text{Softmax}\!\left(\ell_{|x|+i-1}\right)$

7:  $\hat{y}_{i}\leftarrow\text{SampleFrom}(p_{i};\mathsf{H}(\mathsf{seed}\|i))$

8:  if $\hat{y}_{i}=y_{i}$ then

9:   $\text{diff}\leftarrow\text{diff}+1$

10:  end if

11:end for

12:$\text{score}\leftarrow\dfrac{\text{diff}}{T}$

13:return $\text{diff},\ \text{score}$

### C.4 Rank-Aware FSSL-GM Scoring

Algorithm 7 Per-Token Risk Classification via FSSL-GM and Rank

1:token $i$ at position $t$, FSSL-GM threshold $\tau$, rank cutoff $R$

2:Compute $\mathrm{FSSL-GM}_{t}(i)$ and $\mathrm{rank}\!\big(\mathrm{logits}_{t}(i)\big)$

3:if $\mathrm{FSSL-GM}_{t}(i)\geq\tau$ then

4:  return safe (0)

5:else$\triangleright$ $i\notin A_{t}(\tau)=\{j:\mathrm{FSSL-GM}_{t}(j)\geq\tau\}$

6:  if $\mathrm{rank}\!\big(\mathrm{logits}_{t}(i)\big)>R$ then

7:   return danger (2)

8:  else

9:   return suspicious (1)

10:  end if

11:end if

## Appendix D Mechanism Design security solutions: Random Sampling and the Panopticon

### D.1 Mechanism Design

A valuable observation in the design on a verification system is that we can exploit a classic ”panopticon” mechanism design structure, proposed in the 18th century by Willey Reveley to monitor prisoners with a limited number of guards. In the original setting, although it is physically impossible for the single guard to observe all the inmates’ cells at once, one can design a building to allow a guard to see the prisoners without the prisoners seeing the guard. The fact that the inmates cannot know when they are being watched motivates them to act as though they are all being watched at all times.

In the same vein, in environments with persistent identity (such as API access tied to verified accounts or Know-Your-Customer laws), one does not need to catch all possible exfiltrations if the expected cost of being caught exfiltrating model weights is sufficiently high. Though critically, such a system is predicated on a credible source of randomness, where the exfiltrators cannot predict what the auditor will audit, and also the exfiltrators cannot exfiltrate all of the data in a single action (analogous to all the prisoners escaping at once). Critically, we do note that required named-entities is not a necessary requirement for our scheme to work.

### D.2 Derivation of Required Sampling Rate

The “panopticon” framing gives an institutional rationale for why random verification can deter exfiltration: even partial, unpredictable monitoring can induce compliance when the expected cost of detection is high.

The key design question then becomes: _given a limited verification budget, what sampling rate is sufficient to detect exfiltration attempts with high confidence?_

This question connects mechanism design to classical statistical estimation. By modeling each message as a Bernoulli trial where a fraction $p$ of messages contain covertly encoded content, we can derive the required sampling rate to achieve a desired confidence level in detecting at least $k$ instances of suspicious activity, classically referred to as the _inverse binomial problem_.

In this setting, we think of all the messages as a collection of samples $S$, and there is some fraction $p$ of messages that encode a steganographic message. Presuming that the verifier requires $k$ steganographically-encoded samples to detect an exfiltration attempt, the question is how many samples need to be drawn.

For some confidence level $c$ (e.g., 99% confidence), we seek to solve

$$\Pr(\text{at least }k\text{ encoded-samples in }n\text{ draws})\geq c$$

In other words,

$$\Pr(X\geq k)\geq c,\quad\text{where }X\sim\text{Binomial}(n,p).$$

-   •
    
    For $p=1\%$, $c=99\%$, $k=1$, this is $n=460$ samples.
    
-   •
    
    For $p=1\%$, $c=99\%$, $k=100$, this is $n=12{,}460$ samples.
    

## Appendix E Trust assumptions for Sampled Output Verification

### E.1 Assumption 1: The Verification Server is trusted to correctly execute its code

In our proposed solution, it is important that the verification server correctly executes its code. When the verification code itself is untrusted or run in an untrusted environment, an adversary could potentially compromise and circumvent the policy enforcement.

In order to achieve this level trust, we list a few possible properties of the Verification Server that might support this assumption:

-   •
    
    Trusted compute: It can use GPU TEEs or even CPUs to verify inference—even if doing so is inefficient.
    
-   •
    
    Verifiable, simple code: Its code does not need to be highly optimized, and any changes to it can be closely monitored.
    
-   •
    
    Independent root of trust: Attackers will now need to compromise the Verification Server in addition to the Inference Server. One could imagine spinning up several independent Verification Servers operated by independent teams of engineers/agents and running in mutually isolated environments.
    

### E.2 Assumption 2: All messages passed between users and the Inference Server are correctly logged and securely stored

If an attacker could ensure that some inference outputs transmitted out of the data center are not logged, then it could evade the detection system by smuggling model parameters out via these unmonitored channels. Similarly, the attacker could ensure that inference outputs are logged incorrectly—e.g. that the logs contain outputs that the model would have actually generated, even though what was actually transmitted out of the data center was something else entirely.

Similarly, if an attacker can delete or alter the logged data, then the Verification Server’s code may not evaluate the correct logs. In this world, even if the Verification Server is itself trusted to execute code correctly (Assumption #1), it would not be able to detect model exfiltration.

However, if the logs are correctly written in the first place, then this attack is only possible if the attacker can modify the logs after they’ve been written.

One idea would be to secure inference records and model artifacts against tampering using standard cryptographic commitment schemes. For instance, the developer can maintain a Merkle tree with leaves for each inference record (an “inference ledger”), and another with leaves for each model checkpoint (a “model ledger”). Whenever the Inference Server loads inference inputs, outputs, and models into memory, it hashes them and checks whether they are included in the relevant ledgers.

Some notes on how this might work in practice:

-   •
    
    The hashes can be signed using a private key only available on the trusted logging device
    
-   •
    
    Any systems that reference entries in the model ledger or inference ledger should store local records of any hashes they’ve encountered—periodically they could then check whether these historical hashes still exist in the relevant ledgers. This means that attacking the ledgers would require compromising many independent systems simultaneously
    

### E.3 Assumption 3: The attacker can neither predict nor alter which logs the Verification Server will sample to verify

It is critical that an adversary attempting to exfiltrate weights does not know which outputs are going to be audited. Otherwise, an adversary may simply exfiltrate weights through the messages not-audited. This assumption is critical for this scheme to work; however, many schemes for random sampling exist. A simple proposal like random sampling within a trusted-execution environment is almost certainly sufficient; but in the event that it isn’t this has been studied in [great depth](https://a16zcrypto.com/posts/article/leader-election-from-randomness-beacons-and-other-strategies/) in blockchain literature. We discuss how to do this in detail in Section [E.6](#A5.SS6 "E.6 Message-Sampling Secure Seed Expansion ‣ Appendix E Trust assumptions for Sampled Output Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

### E.4 Assumption 4: The Verification Server itself does not pose a risk of model exfiltration

We assume that the Verification Server is not itself an attack vector. One approach would be to limit the outbound bandwidth such that rapid model exfiltration is infeasible. Note that the required outbound bandwidth from the Verification Server is likely qualitatively lower than that required by the Inference Server, rendering egress controls a more natural defense in this case. For example, all traffic beyond the policy decision could suppressed, which would heavily rate-limit any potential exfiltration even when an adversary had control of the Verification Server.

### E.5 Assumption 5: The randomness used for inference is trusted and non-malleable

If the adversary can manipulate randomness, they can transmit information by selecting seeds/samples while leaving per-step likelihoods within normal ranges. In this regime the verifier’s guarantees degrade sharply: many exfiltration strategies become indistinguishable from benign stochasticity, and a malicious provider could even watermark or backdoor outputs via RNG tampering while remaining white-box undetectable \[[GKV+24](#bib.bib17 "Planting undetectable backdoors in machine learning models"), [CG24](#bib.bib16 "Pseudorandom error-correcting codes")\].

##### Statement.

The random coins used by the sampler during inference—and the identical coins used by the verifier—are generated by a trusted cryptographic RNG, bound to the request, and cannot be chosen, biased, or adaptively influenced by the adversary.

##### Rationale.

If an adversary can steer the randomness (e.g., select seeds, bias PRNG state, or grind over retries), the sampler itself becomes a covert channel: the adversary can encode arbitrary payloads by “choosing the random samples.” Closely related phenomena are known in training-time settings, where tampering with algorithmic randomness enables _undetectable backdoors_ that are indistinguishable to any efficient observer \[[GKV+24](#bib.bib17 "Planting undetectable backdoors in machine learning models")\]. Analogously, inference-time coin-fixing enables steganographic signaling without changing logits in a way a verifier could reliably flag (see also pseudo-random watermarking constructions \[[CG24](#bib.bib16 "Pseudorandom error-correcting codes")\]).

##### Threat model scope.

Under this assumption, the adversary: (i) cannot specify or influence the inference seed; (ii) cannot bias randomness indirectly via user-exposed knobs (e.g., temperature, top-$k$, top-$p$) beyond an attested, fixed configuration for the session; and (iii) cannot “grind” seeds by adaptively restarting until a desired draw appears (retry budgets are bounded and auditable).

### E.6 Message-Sampling Secure Seed Expansion

A critical part of deployment to prevent adversarial exfiltration is proper seed management. If the adversary is able to predict or precompute which tokens will be selected during generation, they may be able to choose seeds and prompt combinations carefully to maximize the exfiltration potential. To be sure that this isn’t possible, it’s important to at the very least:

1.  1.
    
    Use a sufficiently long seed to prevent precomputing and exhaustive searches for good seeds.
    
2.  2.
    
    Use a random key and cryptographically secure hash function to expand the seed. More specifically, one can expand the seed $\sigma$ by computing $H(K,\sigma)$, where $H$ is a secure hash, e.g. SHA3, and $K$ is a random key.
    

Beyond the above, we outline further measures that one can take in Section [5.3](#S5.SS3 "5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"). These additional constraints can provably limit the exfiltration of adversaries but may come at some inconvenient costs to the system architecture. Specifically, one may choose to also:

1.  1.
    
    Expand the seed adaptively, based on tokens chosen previously. So, computing the randomness for the next token as $H(K,\sigma,x)$, where $x$ is the prompt and tokens computed thus far (used in Theorems [5.2](#S5.Thmtheorem2 "Theorem 5.2. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") and [5.3](#S5.Thmtheorem3 "Theorem 5.3. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")).
    
2.  2.
    
    Expand initial seed into much longer seed in trusted system, to prevent seed exfiltration. So, an API server may compute a large $\sigma^{\prime}\leftarrow H(K,\sigma)$ that is given to the inference server as and then continue further expansion by running $H(K,\sigma^{\prime},x)$ (used in Theorem [5.3](#S5.Thmtheorem3 "Theorem 5.3. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")).
    
3.  3.
    
    Keep the expansion key in a trusted system and require interaction to get the randomness for the next token (used in Theorem [5.2](#S5.Thmtheorem2 "Theorem 5.2. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")).
    

Although these measures do require careful implementation at the system level, they can provide significant returns in protecting the theoretical exfiltration rate. And, although cryptographic operations and interaction are often expensive in real-world deployments, we note that the additional cost of these operations does not bottleneck performance compared to the inference time of generative AI models.

### E.7 Plausibility of Necessary Assumptions

Theorem [5.1](#S5.Thmtheorem1 "Theorem 5.1. ‣ Rate limitation for the FSSL policy. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), and to a lesser extent Theorems [5.2](#S5.Thmtheorem2 "Theorem 5.2. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") and [5.3](#S5.Thmtheorem3 "Theorem 5.3. ‣ Permitted tokens. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), give the adversary exfiltrating data a significant amount of power. For example, we assume both the sender and receiver have access to the model distribution for the given prompt and sometimes even the distribution of honest responses accounting for valid non-determinism.

Such assumptions may appear too strong at first glance. How likely is it that the adversary is able to obtain all of this information? As with many areas of cryptography, we aim to overestimate the power of the adversary in order to obtain _stronger_ bounds on realistic adversarial capability. That being said, we argue that these assumptions are achieved by some very plausible adversaries:

-   •
    
    An adversary may have already exfiltrated a small model was already exfiltrated that is accessible through a system’s API, and the adversarial server is now exfiltrating a larger model through queries to the smaller model.
    
-   •
    
    The adversary may have distilled a small model on the outputs of a large model for specific prompts or domains. Then, by exfiltrating only on that set of prompts, the receiver will have an extremely close probability distribution to the large model.
    

In Theorem [5.1](#S5.Thmtheorem1 "Theorem 5.1. ‣ Rate limitation for the FSSL policy. ‣ 5.3 Theoretical Exfiltration Limitations ‣ 5 Theoretical Framework: Verification System ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") we also assume the outside adversary obtains the generation seed. This way we can prove a bound without making as many trust and cryptographic assumptions. Also, in many real-world deployments, one may want the flexibility to modify seed generation to either speed up or simplify the infrastructure and avoid deployed extremely secure seed expansion (although this cost is much smaller than the cost of inference).

## Appendix F How Specific Implementations may Affect Verification

The exact inference stack used dramatically affects the requirements on the verification server. In this work we formulate sampling from an LLM as a two step process: (i) generate a probability distribution, and (ii) sample a single token from that probability distribution. The majority of this work is showing how to quantify the non-determinism that may arise from slightly different probability distribution generating processes. However, for this to work, this is predicated on a precise and easy-to-reproduce method of sampling from the probability distribution. In this work we show how to do this for the Inverse Probability Transform method of sampling and the Gumbel-Max trick.

Modern inference stacks are generally more complicated than either of these two methods, employing tricks like speculative decoding, and this needs to be shared across the inference server and verification server, which we discuss in Section [F.1](#A6.SS1 "F.1 Speculative Decoding ‣ Appendix F How Specific Implementations may Affect Verification ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

Another noteworthy consideration is how random samplers update their state, and synchronizing this across the inference and verification servers. For example, in some implementations (like Ollama \[[32](#bib.bib9 "Ollama documentation")\]), if you filter the probability distribution with top-p and the token array ends up with only one entry, the inference server will not sample at all, and use a greedy decoding step. This means that the RNG state does not advance for the inference server, but may for the verification server. However, this issue does not arise in other common implementations like vLLM \[[KLZ+23](#bib.bib10 "Efficient memory management for large language model serving with pagedattention")\].

### F.1 Speculative Decoding

Speculative decoding \[[LKM23](#bib.bib194 "Fast inference from transformers via speculative decoding"), [CBI+23](#bib.bib193 "Accelerating large language model decoding with speculative sampling"), [ZWH+25](#bib.bib196 "Learning harmonized representations for speculative sampling"), [LWZ+25](#bib.bib195 "EAGLE-3: scaling up inference acceleration of large language models via training-time test")\] has emerged as a widely-adopted technique to accelerate LLM inference by using a smaller “draft” model to propose candidate tokens, which are then verified in parallel by the larger “target” model. This approach can achieve substantial speedups (often $1.5{-}2.5\times$) while preserving the exact output distribution of standard autoregressive sampling from the target model.

In the main body of this work, we focus our verification methodology on standard autoregressive sampling (Section [6](#S6 "6 Implementing a Verification Server ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")), where a single model generates one token at a time. This choice reflects two practical considerations:

1.  1.
    
    Production systems exhibit heterogeneity in their acceleration strategies: while speculative decoding is common, implementations vary significantly across frameworks and deployments.
    
2.  2.
    
    At the time of writing, vLLM version 0.10 does not natively support speculative decoding.
    

Nevertheless, we recognize that speculative decoding represents an important class of real-world inference strategies. In this appendix, we demonstrate that our verification framework naturally extends to handle speculative decoding with minimal modifications.

##### Background: A Speculative Decoding Algorithm

In speculative decoding introduced by \[[LKM23](#bib.bib194 "Fast inference from transformers via speculative decoding"), [CBI+23](#bib.bib193 "Accelerating large language model decoding with speculative sampling")\], a draft model generates $K$ candidate tokens, which the target model then verifies in parallel. For each candidate, the target model either accepts it, rejects and resamples from an adjusted distribution, or (if all candidates are accepted) samples one additional bonus token. This process maintains exact distributional equivalence to standard autoregressive sampling from the target model alone.

Different speculative decoding algorithms use different methods for accepting tokens from the draft model. For example, in the original work proposing speculative decoding \[[LKM23](#bib.bib194 "Fast inference from transformers via speculative decoding")\] the verifier only accepts a token if it is the exact token that the verifier model would have generated in that position. However, in other methods a draft token is accepted not only if it is the token the verifier would have sampled, but alternatively if it is a sufficiently likely token as well \[[LWZ+25](#bib.bib195 "EAGLE-3: scaling up inference acceleration of large language models via training-time test")\].

Depending on the specific method used for speculative decoding the verification process may need to be modified. In some cases this can cause a larger rate of exfiltratable information, as more tokens could have been sampled by the drafter; however, future work could also verify the draft model process in the speculative decoding process as well.

## Appendix G Response to Detecting Exfiltration Attempts

This work focuses primarily on the _detection_ of potential model-weight exfiltration attempts rather than on post-detection remediation. In particular, we formalize the task of determining whether a batch of model outputs contains covertly embedded information. Following the literature on steganographic detection \[[KER07](#bib.bib8 "Batch steganography and pooled steganalysis"), [KP12](#bib.bib18 "Batch steganography in the real world")\], we envision verification pipelines adhering to a general three-step structure:

1.  1.
    
    Per-token scoring: Assign a suspiciousness score to each token using an appropriate statistical or model-based function (e.g., likelihood ratios, cross-model divergence, or reconstruction residuals).
    
2.  2.
    
    Pooling: Aggregate token-level scores into sequence-, user-, or deployment-level statistics via a chosen pooling function (e.g., mean, max, or robust thresholding).
    
3.  3.
    
    Flagging: Identify batches or entities whose pooled scores exceed a defined operational threshold, signaling possible exfiltration or anomalous behavior.
    

This framework deliberately mirrors that of batch steganalysis, where the goal is not to prove intent but to highlight objects that merit investigation. Detection signals should thus be treated as probabilistic indicators rather than definitive evidence of compromise.

Operational response. Once a token batch or deployment is flagged, the appropriate policy response depends on the severity, frequency, and operational sensitivity of the detection. A proportionate and auditable escalation pathway might include the following steps:

1.  1.
    
    Rate-limit or reduce per-user bitrate. Temporarily lower allowable output volumes or token-generation rates for implicated users or systems, thereby constraining potential exfiltration bandwidth while maintaining partial service availability. This should be paired with _Know Your Customer_ (KYC) or identity-verification mechanisms to mitigate Sybil-style circumvention ([https://en.wikipedia.org/wiki/Sybil\_attack](https://en.wikipedia.org/wiki/Sybil_attack)).
    
2.  2.
    
    Quarantine and investigate machines or deployments. Isolate hosts, containers, or code branches that repeatedly produce high-suspiciousness outputs. Conduct forensic review of environment variables, code diffs, and access logs to detect injected payloads or altered sampling procedures.
    
3.  3.
    
    Human-in-the-loop review. Contact or interview users responsible for flagged activity, allowing for legitimate use cases to be surfaced and appeals to be made. Human review is particularly valuable when benign but novel workloads (e.g., creative generation or low-frequency topics) may trigger false positives.
    
4.  4.
    
    Incident escalation and attribution. If multiple correlated detections arise across distinct systems, escalate to incident response and coordinate attribution analysis. Cross-reference event metadata (user, GPU ID, deployment hash) to localize possible compromise points.
    

### G.1 Privacy-preserving data analysis.

We note that one natural concern in all of this is that any security event will invite privacy-invading scrutiny by the API provider. We note that it is still possible to produce privacy-preserving techniques for triaging potential exfiltration. For example, providers could aggregate suspicious-token counts over a short rolling window using a hash over user values. For example, a pseudonym for a user or API key can be derived via a keyed hash that rotates each window; counts are kept per pseudonym and a heavier review is prioritized when a policy-defined bucket size $B$ is exceeded.

## Appendix H FSSL-GM Score Statistics

This section presents the empirical distribution of FSSL-GM scores to provide intuition for how the scoring function behaves on benign traffic and how detection thresholds are calibrated.

### H.1 Score Distribution for a Single Token Position

Figure [11](#A8.F11 "Figure 11 ‣ H.1 Score Distribution for a Single Token Position ‣ Appendix H FSSL-GM Score Statistics ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") shows the distribution of FSSL-GM scores across the entire vocabulary for a single token position during generation. For each token $i$ in the vocabulary, we compute $\mathrm{FSSL-GM}_{t}(i)$ using the Token-DiFR estimation procedure described in Algorithm [4](#alg4 "Algorithm 4 ‣ C.2 Gumbel-Max FSSLEstimators (FSSL-GM) ‣ Appendix C Algorithms ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img13-ead8b92c.png]]

Figure 11: Distribution of FSSL-GM scores across vocabulary for a single position. This histogram shows how FSSL-GM scores are distributed across all possible tokens at a given generation step. The actually-sampled token typically has a score near the peak of this distribution (high likelihood region).

### H.2 Distribution of FSSL-GM Scores for Actually-Generated Tokens

While Figure [11](#A8.F11 "Figure 11 ‣ H.1 Score Distribution for a Single Token Position ‣ Appendix H FSSL-GM Score Statistics ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") shows scores for all vocabulary tokens at one position, Figure [12](#A8.F12 "Figure 12 ‣ H.2 Distribution of FSSL-GM Scores for Actually-Generated Tokens ‣ Appendix H FSSL-GM Score Statistics ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") shows the distribution of FSSL-GM scores for the tokens that were _actually generated_ across many positions and prompts.

This distribution is crucial for threshold calibration: we generate 500 prompts with up to 500 tokens each under _benign_ conditions (honest model, no adversary), compute $\mathrm{FSSL-GM}_{t}(y_{t})$ for each actually-generated token $y_{t}$, and collect the resulting scores. The histogram in Figure [12](#A8.F12 "Figure 12 ‣ H.2 Distribution of FSSL-GM Scores for Actually-Generated Tokens ‣ Appendix H FSSL-GM Score Statistics ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") represents the empirical distribution of FSSL-GM scores under legitimate operation.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img14-f69c5d71.png]]

Figure 12: Histogram of FSSL-GM scores for actually-generated tokens across 500 prompts. Each bin represents how many tokens (out of $\approx$250,000 total) received a given FSSL-GM score during benign generation. This distribution allows us to select thresholds $\tau$ that achieve target false-positive rates: e.g., setting $\tau$ at the 1st percentile of this distribution yields FPR $\approx 1\%$.

### H.3 Threshold Selection and FPR-Information Trade-off

Given the empirical score distribution from benign traffic, we select thresholds to achieve specific false-positive rates. Figure [13](#A8.F13 "Figure 13 ‣ H.3 Threshold Selection and FPR-Information Trade-off ‣ Appendix H FSSL-GM Score Statistics ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") illustrates this trade-off:

-   •
    
    X-axis (threshold $\tau$): More negative thresholds accept more tokens (lower FPR, higher usability) but allow adversaries to exfiltrate more information. More positive thresholds reject more tokens (higher FPR, lower usability) but tighten the information bound.
    
-   •
    
    Left Y-axis (False Positive Rate): The fraction of benign tokens with $\mathrm{FSSL-GM}_{t}(y_{t})<\tau$. Computed directly from the cumulative distribution of Figure [12](#A8.F12 "Figure 12 ‣ H.2 Distribution of FSSL-GM Scores for Actually-Generated Tokens ‣ Appendix H FSSL-GM Score Statistics ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
    
-   •
    
    Right Y-axis (Extractable Information): The worst-case per-token information an adversary can exfiltrate, computed as $\frac{1}{T}\sum_{t}\log_{2}|A_{t}(\tau)|$ where $A_{t}(\tau)$ is the admissible set (tokens with $\mathrm{FSSL-GM}_{t}(i)\geq\tau$).
    

Practitioners can use this curve to select operating points: for example, tolerating 0.1% FPR might reduce extractable information to $<$1 bit/token (versus the baseline $\log_{2}(|\text{vocab}|)\approx 16$ bits/token).

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img15-4ad720e5.png]]

Figure 13: Threshold selection trade-off. As the FSSL-GM threshold $\tau$ increases (moving right), the false positive rate increases (rejecting more benign tokens), while the extractable information decreases (tightening the adversarial capacity bound). This plot allows practitioners to select thresholds that balance security and usability for their deployment.

## Appendix I Gumbel-Likelihood Score Exfiltration Results

This section presents results from different experimental configurations of the two-tier and three-tier verification classifier systems across various models and rank thresholds.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img16-caae25dd.png]]

Figure 14: Multi-model two-tier classifier Pareto frontier (envelope across all rank thresholds). This plot displays the optimal security-vs-usability trade-off for detecting steganographic data exfiltration across multiple LLM architectures. Each curve represents a different model, showing the envelope across all tested rank thresholds, i.e., for each FPR level, it shows the minimum extractable information achievable by choosing the optimal rank threshold. The Pareto frontier shows the best achievable trade-off between (x-axis) False Positive Rate (%) - fraction of legitimate tokens incorrectly flagged as “dangerous” and (y-axis) Extractable Information (%) - how much data an attacker can still exfiltrate while evading detection. Models tested: Llama-3.1-8B, Llama-3.2-3B, Qwen3-30B-A3B, and Qwen1.5-MoE-A2.7B.

### I.1 Logit-Rank Ablations

In this section we include experiments with the same experimental set up as Section [7](#S7 "7 Empirical Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration"), where we sweep our classifier across multiple logit-rank thresholds to show the effect of logit-rank as a meaningful contribution to classifying on exfiltratable information.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img17-3e7c5f01.png]]

Figure 15: Multi-model Pareto frontier with no rank threshold (two-tier baseline). This plot shows the baseline two-tier classifier performance (safe vs. dangerous only, no suspicious category) across all tested models. Without the rank-based stratification, the system can only distinguish between tokens that pass or fail the FSSL-GM threshold, leading to higher extractable information at comparable FPR levels compared to the three-tier classifier.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img18-25a9d200.png]]

Figure 16: Multi-model Pareto frontier with rank threshold = 1. This configuration uses the most aggressive rank cutoff, where only the top-ranked token by raw logits is allowed in the suspicious category. All tokens that fail FSSL-GM and are not rank-1 are classified as dangerous. This provides the tightest security bounds but may increase the FPR for legitimate low-rank tokens.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img19-02414170.png]]

Figure 17: Multi-model Pareto frontier with rank threshold = 4. With a rank cutoff of 4, tokens that fail FSSL-GM but fall within the top 4 by raw logits are classified as suspicious (limited to $\log_{2}(4)=2$ bits of information), while those beyond rank 4 are dangerous. This provides a balance between security and usability.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img20-cc926124.png]]

Figure 18: Multi-model Pareto frontier with rank threshold = 8. With rank = 8, suspicious tokens are capped at $\log_{2}(8)=3$ bits of extractable information. This intermediate threshold allows more flexibility while still constraining the attacker’s channel capacity significantly below the full vocabulary size.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img21-848ec06b.png]]

Figure 19: Qwen3-30B-A3B Pareto frontier across rank thresholds. This plot shows the extractable information vs. FPR trade-off for the Qwen3-30B-A3B model across different rank threshold configurations. Each curve represents a different rank cutoff, showing how the three-tier classification scheme performs for this larger model. The Pareto-optimal curves demonstrate that finite rank thresholds consistently outperform the baseline (rank=None) configuration.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img22-963d1355.png]]

Figure 20: Qwen1.5-MoE-A2.7B Pareto frontier across rank thresholds. This plot displays the trade-off curves for the Qwen1.5-MoE mixture-of-experts model. Despite having fewer active parameters (2.7B), the MoE architecture shows distinct verification characteristics compared to dense models, providing insights into how model architecture affects the FSSL-GM verification effectiveness.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img23-a302b68e.png]]

Figure 21: Llama-3.1-8B-Instruct Pareto frontier across rank thresholds. This plot presents the verification trade-offs for Meta’s Llama-3.1-8B-Instruct model. The curves show how the three-tier classifier performs on this mid-sized instruction-tuned model, with each rank threshold providing different operating points for practitioners to balance security requirements against service availability.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img24-66e3bcc8.png]]

Figure 22: Llama-3.2-3B-Instruct Pareto frontier across rank thresholds. This plot shows the verification performance for the smaller Llama-3.2-3B-Instruct model. Smaller models typically exhibit slightly higher extractable information at comparable FPR thresholds due to their reduced output entropy, as evidenced by the frontier positioning relative to larger models.

### I.2 Context Length Ablations

To understand how input context length affects the FSSL-GM verification system’s performance, we conducted ablation studies using prompts of varying lengths. We generated prompts with 4,000, 8,000, and 12,000 tokens using the LongBench v2 dataset \[[BTZ+25](#bib.bib197 "LongBench v2: towards deeper understanding and reasoning on realistic long-context multitasks")\], which provides realistic long-context tasks for multitask benchmarks. We create generations of max-length 500 tokens for 100 prompts, given 100 FSSL-GMthresholds, and $\sigma\in(0.001,0.01,0.1,1.)$. For each context length and model combination, we measured the trade-off between false positive rate and extractable information under the same experimental setup as Section [7](#S7 "7 Empirical Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").

Figures [23](#A9.F23 "Figure 23 ‣ I.2 Context Length Ablations ‣ Appendix I Gumbel-Likelihood Score Exfiltration Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")–[25](#A9.F25 "Figure 25 ‣ I.2 Context Length Ablations ‣ Appendix I Gumbel-Likelihood Score Exfiltration Results ‣ Verifying LLM Inference to Detect Model Weight Exfiltration") show results for three models across the different context lengths[^8]. Each figure displays three plots side-by-side, corresponding to context lengths of 4,000, 8,000, and 12,000 tokens. These results demonstrate how the verification system’s security-usability trade-off varies with input length, providing insights into how context window size affects the detectability of steganographic exfiltration.

We note that we do see some minor degradation in utility of our methods as the context-length increases; however this is effect is relatively minor.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img25-72814fd2.png]]

(a) Context length: 4,000

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img26-453a1da9.png]]

(b) Context length: 8,000

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img27-0f718440.png]]

(c) Context length: 12,000

Figure 23: Llama-3.1-8B-Instruct context length ablation. FPR vs. extractable information trade-off for Llama-3.1-8B-Instruct across different input context lengths. Each subplot shows how the verification system performs when processing prompts of 4,000, 8,000, and 12,000 tokens respectively.

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img28-e9e30e5e.png]]

(a) Context length: 4,000

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img29-e866b3af.png]]

(b) Context length: 8,000

![[/attachments/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration-img30-40749f5f.png]]

(c) Context length: 12,000

Figure 24: Llama-3.2-3B-Instruct context length ablation. FPR vs. extractable information trade-off for Llama-3.2-3B-Instruct across different input context lengths. Each subplot shows how the verification system performs when processing prompts of 4,000, 8,000, and 12,000 tokens respectively.

![Refer to caption](https://arxiv.org/html/2511.02620v3/x27.png)

(a) Context length: 4,000

![Refer to caption](https://arxiv.org/html/2511.02620v3/x28.png)

(b) Context length: 8,000

![Refer to caption](https://arxiv.org/html/2511.02620v3/x29.png)

(c) Context length: 12,000

Figure 25: Qwen3-30B-A3B context length ablation. FPR vs. extractable information trade-off for Qwen3-30B-A3B across different input context lengths. Each subplot shows how the verification system performs when processing prompts of 4,000, 8,000, and 12,000 tokens respectively.

### I.3 Relationship to watermarking.

From another perspective, one can view the role of the warden more broadly as a variant of _watermarking_. Roughly speaking, the warden wishes to design a setup where honestly generated outputs contain some signal, i.e., a watermark, which can be detected by that warden on their way out of the internal infrastructure. In this view, the goal would be to design an extremely _brittle_ watermark, so that if any adversary tried to deviate from honest generation, then the watermark would break.

We draw this parallel as a potential future direction for developing future exfiltration mitigation. Current watermarking schemes are built for different infrastructure and generally designed to be robust to perturbations \[[KGW+23a](#bib.bib208 "A watermark for large language models"), [CGZ24](#bib.bib209 "Undetectable watermarks for language models"), [CHS25](#bib.bib199 "Watermarking Language Models for Many Adaptive Users")\]. However, it is an interesting possibility for future work to adapt techniques from this literature to this setting.

As a philosophically interesting point, we observe that one can view the problem of verifying outputs as purposefully producing an extremely brittle watermarking scheme, namely, one that any text generated by the model is seen as “watermarked” and any deviation from that text is no longer seen as watermarked.

It is valuable to note that our verification solution is entirely compatible with current watermarking schemes too. So, an AI system which is implementing watermarking already can implement this on top of it, with no changes to the system, though, if the watermarking scheme involves a private key, that private key would need to be reproduced in the verification server.

## Appendix J Empirical Base Rates of non-determinism

##### Empirical Characterization of Non-Determinism.

To quantify the inherent non-determinism in language model outputs, we generate 1,000 responses to the same prompt using identical random seeds and construct a _token-level prefix tree_ to visualize divergence patterns (Figure [26(b)](#A10.F26.sf2 "Figure 26(b) ‣ Figure 26 ‣ Empirical Characterization of Non-Determinism. ‣ Appendix J Empirical Base Rates of non-determinism ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")).

Each node in the tree represents a unique token prefix shared by one or more responses. Nodes are connected to their continuations, forming branches that capture all distinct response trajectories. When responses sharing a prefix diverge into multiple next-token choices, we mark that position as a _fork point_ and record its _fork factor_—the number of unique next tokens (i.e., the number of children). Nodes with a single child correspond to deterministic continuations, whereas fork points indicate positions where the model produced different tokens despite identical seeds.

Our primary experiments are conducted with OpenAI 4o-mini, which exhibits a moderate but measurable level of seeded non-determinism. Across 1,000 runs, we observe a “mostly deterministic with critical decision points” pattern: approximately 95% of nodes have exactly one child, 5% represent binary forks, and only 0.2% involve higher-order splits. This indicates that even under fixed seeds, small implementation-level or system-level variations can lead to isolated yet systematic divergences in generation trajectories.

![Refer to caption](https://arxiv.org/html/2511.02620v3/x30.png)

(a) Distribution of fork factors for a prompt.

![Refer to caption](https://arxiv.org/html/2511.02620v3/x31.png)

(b) Prefix tree visualization of 1,000 responses to the same prompt under identical random seeds (first 100 tokens shown). Red nodes mark fork points (multiple children), with size proportional to fork factor.

Figure 26: Empirical characterization of seeded non-determinism for a single prompt using OpenAI 4o-mini. ([26(a)](#A10.F26.sf1 "Figure 26(a) ‣ Figure 26 ‣ Empirical Characterization of Non-Determinism. ‣ Appendix J Empirical Base Rates of non-determinism ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")) The histogram quantifies the overall frequency of fork points, while ([26(b)](#A10.F26.sf2 "Figure 26(b) ‣ Figure 26 ‣ Empirical Characterization of Non-Determinism. ‣ Appendix J Empirical Base Rates of non-determinism ‣ Verifying LLM Inference to Detect Model Weight Exfiltration")) the prefix tree visualizes how and where these divergences occur in token space.

##### Observations.

Empirically, these results demonstrate that valid non-determinism in language model outputs is highly structured and non-uniform. Rather than exhibiting uniform stochasticity across tokens, variability concentrates at specific decision points. Most tokens are effectively deterministic—reproducing the same output across all runs—while a small minority exhibit localized randomness, occasionally branching into several (up to five or more) distinct continuations.

Interestingly, when we replicate this experiment locally using vLLM with Llama-3.1-8B, the generation process becomes dramatically more deterministic (unsurprisingly, as both system load and numerical environment are tightly controlled). In this setting, 99.8% of nodes have a single child, and only 0.2% exhibit any branching at all. This contrast reinforces that much of the observed non-determinism in hosted models such as 4o-mini arises not from the model’s sampling rule itself, but from small, environment-level or distributed-inference sources of variability.

## Appendix K Non-Exhaustive Taxonomy of Exfiltration Vectors

In this section we outline a handful of attack surfaces for exfiltrating model weights (or related sensitive data). We describe how an attacker may operate and give concrete example.

### K.1 Main Message Channel

An attacker may transmit secrets through the model’s ordinary user-facing outputs. In steganographic natural text, seemingly benign responses embed bits (e.g., via synonym choice or punctuation patterns) that the attacker later decodes. This is the primary focus of this work.

### K.2 Developer Channels

An attacker may exploit development or maintenance environments—such as build machines, CI systems, and fine-tune hosts—to exfiltrate model weights or sensitive data by abusing trusted workflows or misconfigurations.

This could happen if a a malicious or compromised developer can transfer full checkpoints to external storage (e.g., AWS S3) using valid credentials. Or less maliciously, if a finetuning job on a shared cluster can write intermediates (weights, optimizer states, logs) to world-readable paths.

### K.3 Operational Security Channel

An attacker may target systems used for backup, logging, and operational continuity to retrieve archived model artifacts. For example, the attacker could compromise a backup service and make a copy of the weights, which would likely be encrypted, from there they only need to exfiltrate a small key to decrypt the backups from the main development server. As such, it is critical to protect not just the datacenter serving weights, but also servers storing auxiliary information, like backups, or key management.

### K.4 Side Channels

An attacker outside of a datacenter may exploit side-channels that correlate with internal computations to infer sensitive information; or an attacker inside of a datacenter may send information outside encoded through a “side-channel”. For example, for timing channels: per-token or total latency variations correlate with secret-dependent execution paths, or timing delays could be used by a adversary to send a specifically encoded message.

### K.5 Miscellaneous

There are also a suite of attacks that are either LLM specific or unique to the workflow associated with an AI workflow. Notably, defending against a distillation attack, where an adversary outside of the datacenter trains their model on the outputs of a closed source model, requires an entirely different set of defenses.

Additionally, an attacker may combine internal services to bypass perimeter controls when the vector does not fit other categories. An example is Repeat-After-Me (internal cross-server exfiltration) attack: an internal service with weight access sends “repeat after me: \<binary payload>” to an externally exposed service, which echoes it to a client. In such a setting, the 2nd server is doing expected behavior and would pass verification. In spirit, this is akin to a confused deputy problem.

## Appendix L Recommended (High-level) Defenses

This scheme is one tool among many, in order to lock down model weights, it is important to also do the following high-level defenses:

1.  1.
    
    Close down side channels. Remove ways information can leak through timing, message size, or system behavior. _Examples:_ send replies at a steady pace; pad/clip lengths; do not expose internal scores/log probabilities; do not let users set random seeds; keep sensitive jobs on separate machines.
    
2.  2.
    
    Close down & monitor development channels. Reduce what internal tools can reveal and monitor their use through access control patterns. _Examples:_ give minimum necessary access to developers; use short-lived credentials; require review for features that show internals; turn off raw traces; log use of special debugging features.
    
3.  3.
    
    Prevent distillation attacks. Distillation attacks seek to replicate a proprietary model’s behavior by repeatedly querying it through a public API and training a surrogate model to match its outputs. While these attacks do not require system compromise, large-scale access can gradually reproduce most of the model’s decision boundaries and degrade its commercial value. Mitigations focus on limiting the quantity and quality of information exposed through normal inference channels. _Examples:_ restrict total query volume and sampling diversity per user; randomize or truncate probability outputs to prevent exact gradient estimation; limit temperature and sampling controls.
    
4.  4.
    
    Operational security. Protect model files and access across training, storage, movement, and serving. _Examples:_ encrypt checkpoints and backups with hardware-protected keys; restrict and log restore operations; separate roles for training vs. inference; require strong auth and just-in-time access for cluster consoles; sign model artifacts and verify signatures before deployment; use authenticated encryption for moving models between systems; block ad-hoc copies to personal storage; rotate keys when models move from training to serving.
    
5.  5.
    
    Monitor main traffic (this scheme). Score tokens for risk and send only the riskiest cases to extra checks; likely apply rate-limiting when needed.
    
6.  6.
    
    Incident response & investigations. When signals cross a threshold, contain, investigate, and fix. _Examples:_ freeze affected keys/accounts; isolate servers and storage; save logs; map impact; rotate keys; write up lessons and update rules.
    
7.  7.
    
    Political & policy responses. Align technical controls with business, safety, and legal needs. _Examples:_ verify identity for high-volume users; set fair-use tiers; define clear escalation paths; publish regular transparency reports; schedule red-team drills.
    

### L.1 More Concrete Recommendations

We discuss a short list of general mitigations that complement a verification-based system.

-   •
    
    Egress limiting: Restrict and monitor all outbound channels (rate limits, content quotas, enforced formats) to make large-scale exfiltration costly or detectable. Diagramed in Figure [27](#A12.F27 "Figure 27 ‣ L.1 More Concrete Recommendations ‣ Appendix L Recommended (High-level) Defenses ‣ Verifying LLM Inference to Detect Model Weight Exfiltration").
    
-   •
    
    KYC and incident response: Strong identity, access controls, and an established incident-response workflow (including KYC for privileged users and rapid revocation) to deter insider misuse and accelerate containment.
    
-   •
    
    One-in-One-out policy: For inference traffic, require that any message leaving the inference server is matched an inbound request; this will prevent exfiltration to only be possible if it is initiated from outside; this is particualrly effective when coupled with traffic monitor (as suggested by this paper) and KYC policies for users sending message requests.
    

![Refer to caption](https://arxiv.org/html/2511.02620v3/x32.png)

Figure 27: Egress-limiting schematic (illustrative): controls on outbound channels reduce bandwidth and increase observability for exfiltration attempts. Egress limiting as a form of strong guarantees on exfiltration is employed by the company Anthropic \[[ANT25](#bib.bib2 "Activating ai safety level 3 protections")\].

[^1]: It’s worth noting that our scheme protects against an adversary with access to a malicious inference stack, but does not provide defense against attacks where a model reveals its own weights as intended behavior of the model.
[^2]: The length of a “block” depends on the scheme and security parameter. In practice, we can roughly think of this as requiring 128-bits of empirical entropy.
[^3]: In practice, we may only need a pseudorandom function, since our security theorems only requires that the output is pseudorandom to an adversary.
[^4]: For one of our bounds, we require that randomness is sampled from $\mathsf{H}(\mathsf{seed}\|i\|\mathcal{H})$, which we call _sequential_ randomness expansion.
[^5]: In the event that not every (input, output, seed) tuple is verified, randomness is critical in the process of selecting which messages to verify is essential. If the messages-to-be-verified is predictable, an adversary could selectively encode sensitive data in unverified outputs.
[^6]: We evaluate on vLLM as this is the most popular open-source inference provider, and thus aim to estimate FSSL-GM scores, rather than FSSL-IPT, as vLLM uses the Gumbel-Max trick for sampling.
[^7]: This is assuming that one requires correctness for a message distribution which is chosen uniformly at random and is therefore incompressible.
[^8]: For these plots we don’t only plot the pareto-optimal plots, to show the effect on the entire curve.
