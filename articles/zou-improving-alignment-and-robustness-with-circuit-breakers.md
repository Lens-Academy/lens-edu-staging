---
title: "Improving Alignment and Robustness with Circuit Breakers"
author:
  - "Andy Zou"
  - "Long Phan"
  - "Justin Wang"
  - "Derek Duenas"
  - "Maxwell Lin"
  - "Maksym Andriushchenko"
  - "Rowan Wang"
  - "Zico Kolter"
  - "Matt Fredrikson"
  - "Dan Hendrycks"
source_url: "https://arxiv.org/abs/2406.04313"
published: 2024-06-06
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "opus"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Abstract ^abstract

AI systems can take harmful actions and are highly vulnerable to adversarial attacks. We present an approach, inspired by recent advances in representation engineering, that interrupts the models as they respond with harmful outputs with “circuit breakers.” Existing techniques aimed at improving alignment, such as refusal training, are often bypassed. Techniques such as adversarial training try to plug these holes by countering specific attacks. As an alternative to refusal training and adversarial training, circuit-breaking directly controls the representations that are responsible for harmful outputs in the first place. Our technique can be applied to both text-only and multimodal language models to prevent the generation of harmful outputs without sacrificing utility—even in the presence of powerful unseen attacks. Notably, while adversarial robustness in standalone image recognition remains an open challenge, circuit breakers allow the larger multimodal system to reliably withstand image “hijacks” that aim to produce harmful content. Finally, we extend our approach to AI agents, demonstrating considerable reductions in the rate of harmful actions when they are under attack. Our approach represents a significant step forward in the development of reliable safeguards to harmful behavior and adversarial attacks. Code is available at [github.com/GraySwanAI/circuit-breakers](https://github.com/GraySwanAI/circuit-breakers).

[^note-1]

## Introduction ^introduction

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig1-41e05d9f.png)

Introduction of circuit-breaking as a novel approach for constructing highly reliable safeguards. Traditional methods like RLHF and adversarial training offer output-level supervision that induces refusal states within the model representation space. However, harmful states remain accessible once these initial refusal states are bypassed. In contrast, inspired by representation engineering (Zou et al. 2023a), circuit breaking operate directly on internal representations, linking harmful states to circuit breakers. This impedes traversal through a sequence of harmful states.

The landscape of artificial intelligence (AI) has long been marred by the persistent threat of adversarial attacks, particularly those targeting neural networks. These attacks exploit inherent vulnerabilities within AI systems, often leading to compromised outputs and raising concerns regarding their reliability and safety. Despite significant attention, existing mitigations have failed to achieve high reliability without dramatically compromising model performance. Thus, the trade-off between adversarial robustness and utility is widely accepted as an unavoidable fact (Tsipras et al. 2019).

The rise of generative models has further complicated this issue. Generative models such as large language models (LLMs) can output copyrighted information or defame individuals, and agents can take harmful actions. To make models less harmful, they are “aligned” with refusal training (Christiano et al. 2017; Rafailov et al. 2023), but it has become common to use adversarial attacks as a means of bypassing their safeguards. In these settings, vulnerability to attacks that break alignment poses a serious threat to utility, and raises pressing questions about whether it is feasible to deploy such systems with a high standard of safety and reliability—especially against dedicated adversaries who intend to misuse them.

The fragility of alignment techniques to sophisticated attacks has motivated defenses that target specific attack methods, such as adversarial training, an approach originally proposed in the context of standalone image classification (Madry et al. 2017) and later adapted to LLMs (Mazeika et al. 2024). However, these methods often fail to generalize to new attacks that were unseen during training, and they introduce penalties on model capabilities that are usually proportional to gains in robustness. System-level defenses, including input and output filters, are cumbersome, resource-intensive, and often remain vulnerable to adversarial techniques. This has led to a growing concern that robust defenses may be unattainable.

We propose a novel approach that fundamentally diverges from traditional defenses: instead of attempting to remove vulnerabilities to specific attacks, our approach aims to directly circumvent the ability of the model to produce the harmful output in the first place. With circuit breakers, we make models intrinsically safer and reduce their risks by removing _intrinsic model hazards_—their ability to produce harmful outputs—rather than removing specific _vulnerabilities_ with adversarial training, and rather than attempting to reduce _exposure_ to attacks with input filters (Leveson 2012; Hendrycks 2024). Using representation engineering (RepE) (Zou et al. 2023a), our method connects the internal representations related to harmful outputs to circuit breakers so that when a model begins to generate such an output, its internal processes are interrupted, halting completion of the generation. Or this method is “short-circuiting” the harmful processes as one might put it. Because the representation used to generate a harmful output is independent of any attack capable of eliciting it, this approach is attack-agnostic, and sidesteps the need for additional training, costly adversarial fine tuning, or the use of auxiliary “guard” models. Consequently, the resulting model with circuit breakers can be used normally without additional computational burden, and seamlessly integrated with existing monitoring and protection mechanisms.

Experimentally, we demonstrate that a circuit-breaking technique, Representation Rerouting (RR), notably improves the alignment of LLMs. It enhances the harmlessness of state-of-the-art LLMs, including against a wide array of _unseen_ adversarial attacks, including embedding and representation-space attacks—namely, proxies for worst-case assumptions about attacker capabilities. Figure 2 and Table 1 present an overview of these results. Our method significantly outperforms standard refusal training and adversarial training, while imposing almost no penalty on standard capability. Notably, we integrate circuit-breaking with additional model control methods to develop a Llama-3-8B-Instruct finetune called Cygnet. This enhanced model not only surpasses its original capabilities but also exhibits a large reduction in harmful output by approximately _two orders of magnitude_, even when confronted with unforeseen adversarial attacks. To the best of our knowledge, this is the first convincing demonstration of the feasibility of designing techniques that significantly advance the Pareto frontier of capability versus harmlessness for LLMs, illustrating that such trade-offs can be effectively managed. When applied to multimodal models, our results show marked increases in harmlessness. It also improves robustness against image-based attacks aimed at similarly circumventing model safeguards, again with almost no penalty on benchmarked capabilities. This remains true even in the presence of the Projected Gradient Descent (PGD) attack (Madry et al. 2017), which defenses for standalone image classifiers have been unable to achieve without a steep trade-off in accuracy. Finally, we apply circuit breakers to AI agents, illustrating its efficacy in controlling agent behaviors through evaluations on a new agent function-calling safety benchmark.

Our findings introduce a new paradigm for creating models that do not produce harmful outputs. Our method is highly robust against adversarial attacks, providing a promising path forward in the adversarial arms race. By ensuring safety and security without compromising capability, our approach increases the chances that we may ultimately be able to deploy robust AI systems in real-world applications.

## Related Work ^related-work

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig2-87fd7fa3.png)

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig3-a355a0f1.png)

Adding circuit breakers using Representation Rerouting (RR) to refusal trained Llama-3-8B-Instruct model leads to significantly lower attack success rate (ASR) over a wide range of _unseen_ attacks on HarmBench prompts (Mazeika et al. 2024), while its capabilities on standard LLM benchmarks (MT Bench and MMLU) are largely preserved. RR directly targets the representations that give rise to harmful outputs and reroutes them to an orthogonal space. This reliably interrupts the model from completing the harmful generations even under strong adversarial pressure.

**Adversarial attacks on LLMs.** Numerous manually written attack prompts on modern LLMs have been discovered (Mowshowitz 2022; Wei et al. 2023), forming the basis of _red teaming_ for frontier LLMs (OpenAI 2023; Anthropic 2024c; Reid et al. 2024), though it lacks standardization (Feffer et al. 2024). Automated red teaming has been shown effective in Perez et al. (2022); Chao et al. (2023); Mehrotra et al. (2023); Zeng et al. (2024). Notably, transfer attacks using an adversarial suffix via gradient-based optimization were demonstrated by Zou et al. (2023b). White-box access also facilitates prefilling attacks (Vega et al. 2023; Andriushchenko et al. 2024), leading the LLM to generate harmful outputs. For a comprehensive summary of automated attacks, we refer to HarmBench (Mazeika et al. 2024). Additionally, multi-modal vision-text attacks range from typographic attacks Goh et al. (2021) to gradient-based optimization (Carlini et al. 2023; Schlarmann and Hein 2023; Bailey et al. 2023). LLM agents have been benchmarked (Liu et al. 2023; Mialon et al. 2023), but their safety and robustness remain unexplored.

**Defenses for LLMs.** Our new defense addresses limitations in existing mechanisms. Widely used defenses include RLHF (Christiano et al. 2017; Ouyang et al. 2022) and DPO (Rafailov et al. 2023) using human annotations for safe vs. unsafe responses (Touvron et al. 2023), but they often fall short against state-of-the-art adversarial attacks (Zou et al. 2023b; Andriushchenko et al. 2024). Additional robustness is achieved by methods like Zhou et al. (2024), which optimize prompts to refuse harmful requests. Inspired by adversarial training in vision (Madry et al. 2017), fine-tuning for the R2D2 model against the GCG attack (Mazeika et al. 2024) shows limited generalizability and drops MT-Bench scores (Zheng et al. 2023). Adversarial training for LLMs can be highly computationally expensive. Inference-time defenses, such as perplexity filters (Alon and Kamfonas 2023; Jain et al. 2023), are effective only against non-adaptive attacks (Liu et al. 2024b), while erase-and-check and SmoothLLM (Robey et al. 2023) incur high computational costs. System-level defenses against unsafe inputs or outputs (Helbling et al. 2023; Inan et al. 2023; Kim et al. 2024) can still be circumvented by sophisticated adversaries (Mangaokar et al. 2024). The main conceptual difference is that instead of operating on input or output text, our method operates directly on representations which provides a more generalizable and computationally cheap solution.

**Representation Engineering.** As many contemporary defenses relying solely on supervising model outputs fail to achieve the desired levels of controllability and reliability, techniques that analyze and manage model’s internal representations have garnered increased attention. This includes research ranging from uncovering emergent interpretable structures in intermediate representations (Zou et al. 2023a; Mikolov et al. 2013; Caron et al. 2021), to the identification and modification of embedded knowledge (Mitchell et al. 2021; Meng et al. 2022a; Meng et al. 2022b), as well as steering model outputs (Upchurch et al. 2017; Bau et al. 2020; Ling et al. 2021; Ilharco et al. 2022; Turner et al. 2023). Most relevant to our work is the control vector baseline introduced in the representation engineering paper (Zou et al. 2023a), which can be applied to enhance large language models’ resistance to adversarial attacks. Alongside the use of control vectors, they introduce an approach that bends representations with representation-level losses. Recent advancements extend this method to robustly unlearn hazardous knowledge (Li et al. 2024) with a method termed RMU, demonstrating the potential of representation engineering for more complex objectives. Previous work has attempted to eliminate harmful circuits using bottom-up mechanistic interpretability, but these methods have proven insufficient (Li Maximilian 2023). Building on these foundations and further expanding RMU to a family of circuit-breaking techniques, we design a methodology based on _model representations_ for robust alignment and control by preventing the generation of harmful outputs.

:::callout {title="Algorithm 1" tone="neutral"}
Original frozen model $\mathcal{M}$, model with circuit breakers $\mathcal{M}_{\textnormal{cb}}$ with LoRA adapters, a function $\texttt{rep}$ that gathers representation from a model on a batch of inputs, a circuit breaker dataset $\mathcal{D}_s$, a retain dataset $\mathcal{D}_r$, number of steps $T$, a hyperparameter $\alpha$

$x_s \sim \mathcal{D}_s$, $x_r \sim \mathcal{D}_r$

$c_s = \alpha  (1 - \frac{t}{2T})$, $c_r = \alpha \frac{t}{2T}$

$\mathcal{L}_s = \texttt{ReLU} \left(\texttt{cosine\_sim}\left(\texttt{rep}_\mathcal{M} \left(x_s \right), \texttt{rep}_{\mathcal{M}_{\textnormal{cb}}} \left(x_s \right)\right) \right)$

$\mathcal{L}_r = \left\| \texttt{rep}_\mathcal{M} \left(x_r \right) - \texttt{rep}_{\mathcal{M}_{\textnormal{cb}}} \left(x_r \right) \right\|_2$

$\mathcal{L} = c_s \mathcal{L}_s + c_r \mathcal{L}_r$
:::

## Circuit Breaking with Representation Engineering ^circuit-breaking-with-representation

In this section, we introduce a novel approach aimed at mitigating the generation of harmful outputs in neural networks by inducing a new type of phenomenon called “circuit-breaking.” This phenomenon can be elicited using a family of techniques designed to monitor or remap model representations related to harmful processes, redirecting them towards incoherent or refusal representations. This process is reminiscent of “short-circuiting,” where harmful representations are “shorted” and intercepted by circuit breakers. The core objective of this method is to robustly prevent the model from producing harmful or undesirable behaviors through monitoring or controlling the representations.

Our focus on generative models—such as language and multimodal agents—presents a unique opportunity. Generative models inherently involve multi-step processes through which outputs are produced. When devising an attack, adversaries must effectively exert influence across each step of the targeted processes, so each step presents an opportunity to make the model more robust to attack. This insight drives our strategy, which focuses on disrupting adversarial control of the relevant multi-step processes rather than the binary classification problem of attempting to detect the presence of an attack. Building from techniques in representation engineering (RepE) (Zou et al. 2023a), we accomplish this by remapping the sequence of model representations that leads to harmful outputs, directing them towards incoherent or refusal representations—namely, _breaking the circuit_, or _shorting the circuit_ as one might put it. Moreover, by directly targeting the processes involved in generating harmful responses, our method can generalize across the diverse range of inputs that may activate those processes. Consequently, we do not need to identify all of the potential inputs that could trigger undesirable outputs, rather we only need to ensure coverage of a well defined set of such outputs.

The applications of circuit breakers are multifaceted. They can be utilized to prevent the generation of harmful outputs in general, as well as to prevent more narrowly tailored types of output, such as private information or copyrighted material. The approach is versatile, as it is possible to identify and remap the relevant representations in virtually any neural network architecture.

The family of circuit-breaking techniques is characterized by two major components: datasets and loss functions. Algorithm 1 presents a circuit-breaking technique that uses Low-Rank Representation Adaptation (LoRRA) (Zou et al. 2023a) which we call Representation Rerouting (RR). The remainder of this section details this approach, and how the data and chosen loss function contribute to the effectiveness of the overall method.

LLM evaluation results. Our circuit-breaking method Representation Rerouting (RR) shows strong generalization across a diverse range of unseen attacks, significantly reducing compliance rates to harmful requests while preserving model capability. Cygnet, a Llama-3-8B-Instruct finetune integrating circuit breakers and other representation control (Zou et al. 2023a) methods, surpasses original capabilities and demonstrates a significant reduction in harmful output by roughly two orders of magnitude under strong attacks. This advancement shows promising initial steps in balancing capability and harmlessness in LLMs. Input embedding attack optimizes the soft input embeddings which is an unrealistically strong threat model for LLMs. Mistral-Adv Trained (R2D2) (Mazeika et al. 2024) is an SFT-only model.

|  | Mistral-7B-Instruct-v2: Refusal Trained | Mistral-7B-Instruct-v2: Adv Trained (R2D2) | Mistral-7B-Instruct-v2: + RR (Ours) | Llama-3-8B-Instruct: Refusal Trained | Llama-3-8B-Instruct: + RR (Ours) | Llama-3-8B-Instruct: Cygnet (Ours) |
| --- | --- | --- | --- | --- | --- | --- |
| MT-Bench | **7.60** | 6.00 | 7.53 | 8.05 | 8.00 | **8.21** |
| Open LLM | **65.4** | 61.2 | **65.4** | 68.8 | 68.3 | **71.9** |
| No Attack | 57.8 | 16.5 | **4.9** | 12.4 | 1.2 | **0.0** |
| Manual | 77.4 | 14.2 | **6.8** | 8.3 | **0.0** | **0.0** |
| AutoDAN | 93.4 | 21.1 | **0.0** | 3.7 | **0.0** | **0.0** |
| TAP-T | 85.8 | 68.7 | **17.5** | 17.4 | 2.1 | **0.0** |
| PAIR | 69.5 | 59.9 | **23.3** | 18.7 | 7.5 | **0.0** |
| GCG | 88.7 | **7.8** | 11.2 | 44.5 | 2.5 | **0.0** |
| Multilingual | 34.1 | **4.7** | 7.3 | 19.3 | 3.5 | **0.0** |
| Prefilling | 95.0 | 46.9 | **4.9** | 84.9 | 3.3 | **0.0** |
| Input Embed | 92.1 | 46.3 | **15.7** | 80.4 | 9.6 | **7.9** |
| RepE Attack | 73.7 | 30.7 | **6.2** | 91.2 | 8.7 | **0.0** |
| Average | 76.7 | 31.7 | **9.8** | 38.1 | 3.8 | **0.8** |

##### Data. ^data

The training data used in RR is partitioned into two sets: the Circuit Breaker Set and the Retain Set, each serving distinct purposes within the training process aimed at controlling harmful processes in the model. As with all representation control methods, the quality of the circuit breaker mechanism largely depends on how precisely the data can elicit the targeted representation. The Circuit Breaker Set is comprised of examples that yield internal representations potentially leading to harmful or undesirable behaviors, and are used to prompt the model’s circuit breaker mechanism. Conversely, the Retain Set includes examples that should not activate circuit breakers, and are used to maintain existing desirable model representations to retain benign efficacy. While even a limited number of examples in each set can sufficiently alter the model’s behavior in a manner that generalizes beyond the training data, the resulting performance is generally improved when the training data better aligns with the domains we aim to break the circuit and retain.

For models with pre-existing refusal mechanisms, like Llama-3-Instruct, careful dataset curation is essential. Adding refusal data to the Retain Set enhances the model’s ability to correctly refuse harmful user requests and improves retention of its capabilities. Another challenge is to elicit harmful responses from models with effective refusal mechanisms. To address this, we must curate a Circuit Breaker set that includes text capable of bypassing the refusal mechanism and triggering harmful processes. We find that a practical approach is to remove harmful user requests while keeping the corresponding harmful assistant responses in the Circuit Breaker Set. These measures ensure the refusal mechanism’s integrity while allowing the model to activate its circuit-breaking function correctly once the refusal is bypassed. Ablation results are detailed in [[#^ablation-and-analysis|4.4]].

##### Loss. ^loss

The accompanying losses for the datasets are the representation rerouting loss and retain loss. Denote the representation of harmful processes under the original model as $\textnormal{rep}_\textnormal{orig}$ and under the model with circuit breakers as $\textnormal{rep}_\textnormal{c/b}$. The rerouting loss is designed to remap representations from harmful processes $\textnormal{rep}_\textnormal{c/b}$ to a desired target representation $\textnormal{rep}_\textnormal{rand}$. Conversely, the retain loss is used to maintain representations within a retain set, which helps preserve these representations. This is often measured as the $\ell_2$ distance between the current and retain representations.

The rerouting loss can take various forms. One approach involves routing the targeted representation to a fixed random direction with a large norm, as utilized in the unlearning method RMU (Li et al. 2024). This is expressed as $\left\| \textnormal{rep}_\textnormal{c/b} - \alpha \textnormal{rep}_\textnormal{rand} \right\|_2$, where $\textnormal{rep}_\textnormal{rand}$ is a random vector and $\alpha$ is a large constant meant to amplify the norm of the representation. However, this approach requires extensive tuning of the $\alpha$ parameter. We also explore a variant of the random vector loss that does not necessitate hyperparameter tuning, formulated as the $\ell_2$ norm of $\textnormal{rep}_\textnormal{c/b} / \left\| \textnormal{rep}_\textnormal{c/b} \right\| - \textnormal{rep}_\textnormal{rand} / \left\| \textnormal{rep}_\textnormal{rand} \right\|$. However, the use of a random vector is neither necessary nor optimal. Given that we want the targeted representation to be as unhelpful as possible for the harmful processes, another approach is to directly optimize the circuit-broken representation to be orthogonal to the original representation responsible for harmful processes. This is given by their cosine similarity: $\textnormal{rep}_\textnormal{c/b} \cdot \textnormal{rep}_\textnormal{orig} / (\| \textnormal{rep}_\textnormal{c/b} \|_2 \| \textnormal{rep}_\textnormal{orig} \|_2)$. To avoid optimizing the similarity beyond zero, we apply a ReLU function to this objective. We find this loss to be the most intuitive and most effective in terms of achieving a balance between robustness and preserved capability. An implementation of RR using Low-Rank Representation Adaptation is shown in Algorithm 1. Additionally, one could map $\textnormal{rep}_\textnormal{c/b}$ onto more semantically meaningful directions, such as a refusal direction or the embedding of the EOS token. We leave this to future work. [[#^additional-design-considerations-for|8.1]] discusses several additional design considerations.

## Experiments ^experiments

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig4-c9012bce.png)

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig5-d4af1f46.png)

Circuit-breaking performance in multimodal settings with Representation Rerouting (RR). Under Projected Gradient Descent (PGD) attack, our LLaVA-NeXT-Mistral-7B (+ RR) with circuit breakers is significantly more robust compared to the original model even with a safety prompt that instructs the model to avoid harmful responses. Performance on multimodal capabilities benchmarks MMMU and LLaVA-Wild is preserved.

### Large Language Models ^large-language-models

**Adding Circuit Breakers.** In our experimental setup, we employ similar circuit breaker and retain datasets for both the Mistral-7B-Instruct-v2 (Mistral 2024) and Llama-3-8B-Instruct (Meta AI 2024) models. Detailed information on the synthetic circuit breaker set for LLMs is provided in [[#^large-language-model-circuit|6.1]]. The retain set for both models includes UltraChat (Ding et al. 2023), comprising instructional conversations, and XSTest (Röttger et al. 2023), an exaggerated refusal dataset. Additionally, for Llama-3, we enhance the retain set with extra refusal data points. We follow the implementation of Representation Rerouting (RR) specified in Algorithm 1 and select hyperparameters based on static attack test cases from HarmBench’s validation set. More experimental details can be found in [[#^detailed-circuit-breaker-setup|8.2.1]].

**Evaluation.** We evaluate the harmfulness of the model using HarmBench (Mazeika et al. 2024), a standardized framework that includes harmful behaviors and a wide range of both black box and white box attacks. We select a subset of the strongest attacks reported on both open-source and closed-source models for evaluation. These attacks include gradient-based optimization (GCG (Zou et al. 2023b)), LLM optimizers (PAIR (Chao et al. 2023)), and custom jailbreaking pipelines (TAP-Transfer (Zeng et al. 2024), AutoDAN (Liu et al. 2024b), and HumanJailbreaks (Shen et al. 2024b)). To further test the model, we incorporate a multilingual attack (Yong et al. 2023), and also introduce three powerful attacks that leverage system-level and representation-space access. We briefly describe these three additional attacks below, and provide a more detailed coverage in [[#^detailed-evaluation-setup|8.2.2]].

1.  **Prefilling Attack**: This system-level attack prefills the assistant’s output with the beginning of a desired target completion. It leverages the autoregressive nature of LLMs, as it can be difficult for a model to “reverse-course” after it has started to generate harmful content. Prefilling is straightforward to implement for any open-weight model, and is also supported for some proprietary LLMs like Claude (Anthropic 2024b).
    
2.  **Input Embedding Attack**: This white-box attack operates in the embedding space by optimizing a set of input embeddings directly instead of using hard tokens, with the objective of eliciting an affirmative assistant response (Schwinn et al. 2024).
    
3.  **RepE Attack**: This white-box attack manipulates the model’s representation space. Previous work in representation engineering demonstrates the identification of directional vectors in the model’s representation space that correspond to refusals (Zou et al. 2023a). By altering these vectors—either adding or subtracting—we can modulate the model’s tendency to refuse requests.
    

We utilize HarmBench’s LLM classifier to evaluate the attack success rate and manually verify the judgements. Detailed configurations for each attack are provided in [[#^detailed-evaluation-setup|8.2.2]]. To measure the capabilities of the models with circuit breakers, we evaluate our models on MTBench (Zheng et al. 2023) for instruction-following abilities and on the OpenLLM Leaderboard (Beeching et al. 2023) for knowledge and reasoning which includes MMLU (Hendrycks et al. 2020), ARC-c (Clark et al. 2018), HellaSwag (Zellers et al. 2019), TruthfulQA (Lin et al. 2022), Winogrande (Sakaguchi et al. 2019), and GSM8K (Cobbe et al. 2021). Table 5 contains a detailed breakdown of performance on each dataset. Additionally, we follow the methodology in (Anthropic 2024c) to construct an over-refusal evaluation, described in [[#^refusal-evaluation|7]]. For baselines, we use the original Mistral and Llama-3 Instruct models. Additionally, we include a state-of-the-art adversarially trained Mistral model, R2D2 (Mazeika et al. 2024), for comparison.

**Results.** We observe that our circuit-breaking technique RR demonstrates strong generalization across a diverse range of attacks, reducing compliance rates to harmful requests by an average of $87\%$ with Mistral and $90\%$ with Llama-3. Unlike the Mistral R2D2 model, which is trained against the GCG yet shows limited generalization to various attacks, our method eliminates the need for specific attack training and focuses on hindering harmful generations. Our approach moves away from the traditional cat-and-mouse paradigm, aiming for generalization to _unforeseen_ attacks. Additionally, the results highlight a Pareto optimal trade-off in performance. Our model exhibits high reliability against unseen attacks with a minimal compromise in capability evaluation, showing a performance dip of less than $1\%$ in proposed tests. This is difficult to achieve with traditional defenses. For example, the Mistral model, when adversarially trained, experiences a decline of over $8\%$ in the MT Bench performance. In contrast, our model leverages representation engineering principles, focusing on internal control over external supervision, enabling more targeted and fine-grained control over model behavior without adversely impacting other functionalities.

### Multimodal Models ^multimodal-models

**Adding Circuit Breakers.** We mix the circuit breaker and retain datasets from [[#^large-language-models|4.1]] with a synthetic multimodal circuit breaker set and the retain LLaVA-Instruct set (Liu et al. 2024a). The detailed process of generating the synthetic dataset is reported in [[#^multimodal-circuit-breaker-dataset|6.2]]. We perform RR on LLaVA-NeXT-Mistral-7B (Liu et al. 2024a). More experimental details can be found in [[#^detailed-circuit-breaker-setup-2|8.3.1]].

**Evaluation.** To evaluate the robustness of multimodal models with circuit breakers, we generate adversarial images using a whitebox approach. Following Projected Gradient Descent (Madry et al. 2017), we perturb images with a harmful prompt to produce a target string with an affirmative assistant response. We set epsilon to $32/255$ and run the process for 1000 steps. As baselines, we test LLaVA-NeXT-Mistral-7B with and without a safety prompt that asks the model to avoid harmful responses. Our robustness results in Figure 3 show the percentage of harmful prompts the model complies with, labeled manually. We source a set of 133 harmful multimodal behaviors from HarmBench (Mazeika et al. 2024) and MM-SafetyBench (Liu et al. 2024c), focusing on the most saliently harmful prompts. See Appendix [[#^multimodal-models-2|8.3]] for more details about the dataset’s composition. For capabilities evaluation, we follow (Liu et al. 2024a) to evaluate multimodal models on LLaVA-Wild for visual chat capability and MMMU (Yue et al. 2024) for multimodal understanding capability.

**Results.** Figure 3 demonstrates that for multimodal models, our circuit-breaking technique RR is also able to make a model significantly more robust while preserving model capabilities. Especially when subject to white-box PGD Attack, RR achieves reduction of $84\%$ in the compliance rate compared to the original model and $85\%$ compared to the safety prompt. Meanwhile, performance on MMMU and LLaVA-Wild remains within $0.5\%$ of the original, as opposed to the safety prompt which causes a decrease of $3.3\%$ on LLaVA-Wild. This demonstrates that despite the ongoing challenge of achieving adversarial robustness in standalone image recognition, circuit breakers enable the larger multimodal system to reliably counter image “hijacks” (Bailey et al. 2023) intended to elicit harmful outputs.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig6-a472a936.png)

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig7-7ea62ee1.png)

Circuit-breaking performance in AI agent settings with Representation Rerouting (RR). Our Llama-3-8B-Instruct (+ RR) with circuit breakers remains robust under Direct Request and Forced Function Calls, while retaining performance on the Berkeley Function Calling Leaderboard (BFCL).

### AI Agents ^ai-agents

**Adding Circuit Breakers.** We mix the circuit breaker and retain datasets from  [[#^large-language-models|4.1]] with function calling circuit breaker and retain dataset. The detailed process of generating the function calling circuit breaker and retain dataset is described in [[#^function-calling-circuit-breaker|6.3]]. For the LLMs with circuit breakers, we also use the same hyperparameter configuration as in [[#^large-language-models|4.1]].

**Evaluation.** To evaluate the effectiveness of RR as a method of preventing AI agents from making harmful function calls, we design a dataset that consists of 100 requests intended to produce harmful actions via function calls, along with associated function definitions. These requests span a variety of categories, including cybercrime, disinformation, fraud, and harassment. The associated function definitions are designed to capture typical use cases of deployed AI agents including sending messages, browsing URLs, and using simple tools in addition to task-specific functions.

We provide a representative example in [[#^ai-agent-benchmark-example|8.4.1]]. We record model compliance rate with harmful requests under both the standard setting, where function call requests are directly given and the model decides whether to make a call, and under _forced function-calling_, where the assistant is forced to begin its response with the name of a function to be called. Forced function-calling is akin to the prefilling attack in [[#^large-language-models|4.1]] and is provided by major model providers (Anthropic 2024a; OpenAI 2024). For capabilities evaluation, we measure performance on the Berkeley Function Calling Leaderboard (BFCL) (Yan et al. 2024). We use Llama-3-8B-Instruct to benchmark, as it is one of few open-source models that

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig8-a8c96400.png)

both _1)_ performs reasonably well on the benchmark leaderboard, and _2)_ is currently served with function-calling capabilities by inference providers (Groq 2024).

**Results.** Figure 4 shows that after applying RR, our model is significantly more robust to harmful function calling requests, in both the no-attack and forced function-call settings, reducing harmful action compliance rates by $84\%$ and $83\%$ in the latter setting compared to baselines. Additionally, the model with circuit breakers retains performance on the Berkeley Function Calling Leaderboard. Overall, this demonstrates the method’s effectiveness in controlling agent behaviors under adversarial pressure and in environments with inherent reward biases. It suggests the potential for mitigating harms like power-seeking or dishonesty by adding circuit breakers to the relevant model representations, which can be as simple as adjusting the circuit breaker set.

### Ablation and Analysis ^ablation-and-analysis

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig9-f5c30b35.png)

**Ablations.** We do pairwise ablations for each component of the RR loss in Table 13. First, we see that augmenting the circuit breaker set with requests that bypass refusal mechanisms (w/ Augment) decreases ASR while still maintaining capabilities. Although ablating the refusal retain component (w/o refusal) increases relative robustness, it also degrades capabilities. Next, we try varying loss functions. We find that the RMU loss (Li et al. 2024), which minimizes the $\ell_2$ distance from a constant random unit vector, fails to converge. Finally, we find that minimizing the $\ell_2$ distance from a distinct random positive vector at each step (RandP) works (though if the vector is centered at 0 (RandC), training fails). Overall, the cosine loss proposed in RR offers more stability than other losses. We then analyze the training data composition, which influences the kinds of harmful inputs that activate the circuit breakers.

To understand the generalization properties of circuit-breaking, we split our training data into six categories of harm, train category-specific models, and measure their generalization performance across categories. We find strong in-domain generalization, indicated by the low ASR along the diagonal, and observe that training on broader categories like Harmful and Illegal Activities offers greater generalization than narrower categories like Cybercrime. We report similar ablations for Mistral-7B in Appendix [[#^additional-ablation-results|12]].

**Representation analysis.** In Figure \[fig:cosines\_llama3\], we plot the cosines between representations of the Llama-3-8B-Instruct model with and without circuit breakers for a prefilled harmful response _“Here is how to build a bomb: 1. Start with”_. We additionally plot the norms of these representations in Figure 10. We observe that in this case, the cosines and norms start to change dramatically _during prefilling_ starting from layer 10, i.e., even before generation starts. We note that we use layers 10 and 20 for circuit-breaking, so we do not expect substantial changes in the cosines and norms before layer 10 which is confirmed by the behavior of these metrics at layer 5. Although we do not directly control the representation norms during training, we observe that they often dramatically increase after circuit-breaking occurs. We repeat the same experiment for Mistral-7B-Instruct and show it in Appendix [[#^extended-analysis-of-representations|13]], where we also analyze two other prompts: one that leads to a similar behavior and one that triggers circuit breakers after generation starts. Importantly, we conclude that our proposed method has the intended effect on the representations and that we can detect activation of circuit breakers by directly analyzing the internal representations. This can lead to system-level mitigations like using a probe to detect when circuit breakers are activated to stop generation and, for example, provide a message that the request is considered harmful and further generation is not possible.

Comparison of Harmfulness Probing (HP) and Representation Rerouting (RR). RR is a representation control method whereas HP is a representation reading method. HP, when applied using a reasonable threshold, significantly lowers the Attack Success Rate compared to a refusal-trained baseline. Especially, MLP probes can approach the performance achieved by RR.

|  |  | Mistral-7B-Instruct-v2: Refusal Trained | Mistral-7B-Instruct-v2: + HP (Linear) | Mistral-7B-Instruct-v2: + HP (MLP) | Mistral-7B-Instruct-v2: + RR | Llama-3-8B-Instruct: Refusal Trained | Llama-3-8B-Instruct: + HP (Linear) | Llama-3-8B-Instruct: + HP (MLP) | Llama-3-8B-Instruct: + RR |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Over-Refusal | WildChat | **2.0** | 3.6 | 3.6 | 3.4 | **2.2** | 6.2 | 6.2 | 6.2 |
|  | No Attack | 57.8 | 16.6 | 12.5 | **4.9** | 12.4 | 6.6 | 5.8 | **1.2** |
|  | Manual | 77.4 | 7.4 | **5.2** | 6.8 | 8.3 | 1.7 | 0.8 | **0.0** |
|  | TAP-T | 85.8 | 27.5 | 26.2 | **17.5** | 17.4 | 8.3 | 6.2 | **2.1** |
|  | GCG | 88.7 | 18.0 | 14.6 | **11.2** | 44.5 | 11.6 | 9.1 | **2.5** |
|  | Input Embed | 92.1 | 16.3 | **13.0** | 15.7 | 80.4 | 16.8 | 12.2 | **9.6** |
|  | Average | 80.6 | 19.0 | 14.3 | **11.2** | 32.6 | 9.0 | 6.8 | **3.1** |

**Circuit breaking with Harmfulness Probes (HP).** Our proposed circuit breaking method relies on _representation control_. This section evaluates the potential efficacy of _representation reading_ as an alternative. Instead of altering the harmful model representation, we simply monitor for its presence and halt model generation if detected. We employ the same training dataset (harmful circuit breaker set and retain set) used in the LLM experiments. A linear classifier and an MLP classifier are trained to distinguish between model activations from the two datasets. Specifically, activations are collected from the 16th layer of the Mistral model and from the final layer of the Llama-3 model for each token in the responses. The MLP probe has two layers with hidden size of 64 and 32. During testing, generation is halted and replaced with a refusal message if any generated token is flagged as harmful by the classifier. We find a threshold so that the false positive rate (FPR) on WildChat ([[#^refusal-evaluation|7]]) is around the same as the model trained with RR (Zhao et al. 2024). We choose five settings to evaluate: prompt only (No Attack), manual attack (Manual), black-box attack (TAP-T), white-box attack (GCG), and an embedding space attack (Input Embed).

As shown in Table 2, Harmfulness Probing (HP) significantly reduces the attack success rate compared to the refusal-trained baseline. Both Linear and MLP Harmfulness Probes are outperformed by the representation control approach (RR), however, the gap is smaller for the MLP probe. We emphasize that, although generally probing can be easily thwarted by adversarial attacks, much like input and output filters, its robustness in this context can be largely attributed to the continuous monitoring of model representations associated with harmful processes throughout the entire generation, a key idea in circuit breaking. Furthermore, one can combine HP and RR to implement multiple layers of defense. It is important to note, however, that the Harmful Probes are tested under a weaker adversarial setting, where the attacker lacks knowledge of the probe and does not directly optimize against it. Further investigation into Harmfulness Probes and other representation reading methods is left for future work.

## Limitations and Conclusion ^limitations-and-conclusion

Despite the promise of the methods introduced here, we emphasize that the approach we present is aiming at preventing one particular type of adversarial attack: an attack against the ability of the model to produce harmful content (often specifically against the desires of the model developer). In general, adversarial attacks can achieve other aims as well, i.e., using a generative vision language model as a drop-in replacement for an image classifier. In such a use case, our method would not provide defense against “traditional” adversarial attacks aimed at simply changing the class label, because no class label would be inherently “harmful.” Thus, there is an important distinction of our approach: we are specifically targeting the adversarial attack setting where the goal of an attacker is to produce generically harmful information (content the model should _never_ produce). Nonetheless, for this particular use case of adversarial attacks, and for single-turn conversations that we focus on circuit-breaking, our approach dramatically improves model robustness.

Overall we found that circuit breakers, based on RepE, make models intrinsically safer and robust to unseen adversarial attacks. The method is highly general and can impart robustness to image hijacks, and it can also prevent AI agents from taking harmful actions. Our method is potentially a major step forward in making models more aligned and robust.

:::hide
We are thankful to Steven Basart, Stephen Casper, David Dalrymple, Xander Davies, and Fabien Roger for providing valuable feedback on the paper.

## References ^references

-   G. Alon and M. Kamfonas. Detecting language model attacks with perplexity. _arXiv preprint arXiv:2308.14132_, 2023.
    
-   M. Andriushchenko, F. Croce, and N. Flammarion. Jailbreaking leading safety-aligned LLMs with simple adaptive attacks. _arXiv preprint arXiv:2404.02151_, 2024.
    
-   Anthropic. Tool use (function calling), 2024. URL [https://docs.anthropic.com/en/docs/tool-use#forcing-tool-use](https://docs.anthropic.com/en/docs/tool-use#forcing-tool-use). Anthropic documentation.
    
-   Anthropic. Prefill claude’s response, 2024. URL [https://docs.anthropic.com/en/docs/prefill-claudes-response](https://docs.anthropic.com/en/docs/prefill-claudes-response). Anthropic documentation.
    
-   Anthropic. The claude 3 model family: Opus, sonnet, haiku, 2024.
    
-   L. Bailey, E. Ong, S. Russell, and S. Emmons. Image hijacks: Adversarial images can control generative models at runtime. _arXiv preprint arXiv:2309.00236_, 2023.
    
-   D. Bau, H. Strobelt, W. Peebles, J. Wulff, B. Zhou, J.-Y. Zhu, and A. Torralba. Semantic photo manipulation with a generative image prior. _arXiv preprint arXiv:2005.07727_, 2020.
    
-   E. Beeching, C. Fourrier, N. Habib, S. Han, N. Lambert, N. Rajani, O. Sanseviero, L. Tunstall, and T. Wolf. Open llm leaderboard. [https://huggingface.co/spaces/HuggingFaceH4/open\_llm\_leaderboard](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard), 2023.
    
-   N. Carlini, M. Nasr, C. A. Choquette-Choo, M. Jagielski, I. Gao, P. W. W. Koh, D. Ippolito, F. Tramer, and L. Schmidt. Are aligned neural networks adversarially aligned? _Advances in Neural Information Processing Systems_, 36, 2023.
    
-   M. Caron, H. Touvron, I. Misra, H. Jégou, J. Mairal, P. Bojanowski, and A. Joulin. Emerging properties in self-supervised vision transformers. In _Proceedings of the IEEE/CVF international conference on computer vision_, pages 9650–9660, 2021.
    
-   P. Chao, A. Robey, E. Dobriban, H. Hassani, G. J. Pappas, and E. Wong. Jailbreaking black box large language models in twenty queries, 2023.
    
-   P. F. Christiano, J. Leike, T. Brown, M. Martic, S. Legg, and D. Amodei. Deep reinforcement learning from human preferences. _Advances in neural information processing systems_, 30, 2017.
    
-   P. Clark, I. Cowhey, O. Etzioni, T. Khot, A. Sabharwal, C. Schoenick, and O. Tafjord. Think you have solved question answering? try arc, the ai2 reasoning challenge, 2018.
    
-   K. Cobbe, V. Kosaraju, M. Bavarian, M. Chen, H. Jun, L. Kaiser, M. Plappert, J. Tworek, J. Hilton, R. Nakano, C. Hesse, and J. Schulman. Training verifiers to solve math word problems, 2021.
    
-   N. Ding, Y. Chen, B. Xu, Y. Qin, Z. Zheng, S. Hu, Z. Liu, M. Sun, and B. Zhou. Enhancing chat language models by scaling high-quality instructional conversations. _arXiv preprint arXiv:2305.14233_, 2023.
    
-   M. Feffer, A. Sinha, Z. C. Lipton, and H. Heidari. Red-teaming for generative ai: Silver bullet or security theater? _arXiv preprint arXiv:2401.15897_, 2024.
    
-   GlaiveAI. Glaive function calling v2 dataset, 2024. URL [https://huggingface.co/datasets/glaiveai/glaive-function-calling-v2](https://huggingface.co/datasets/glaiveai/glaive-function-calling-v2). Accessed: 2024-05-21.
    
-   G. Goh, N. Cammarata, C. Voss, S. Carter, M. Petrov, L. Schubert, A. Radford, and C. Olah. Multimodal neurons in artificial neural networks. _Distill_, 6 (3): e30, 2021.
    
-   Groq. Groqcloud models documentation, 2024. URL [https://console.groq.com/docs/models](https://console.groq.com/docs/models). GroqCloud documentation.
    
-   A. Helbling, M. Phute, M. Hull, and D. H. Chau. Llm self defense: By self examination, llms know they are being tricked. _arXiv preprint arXiv:2308.07308_, 2023.
    
-   D. Hendrycks. Introduction to AI safety, ethics, and society. Taylor and Francis, 2024.
    
-   D. Hendrycks, C. Burns, S. Basart, A. Zou, M. Mazeika, D. Song, and J. Steinhardt. Measuring massive multitask language understanding. _arXiv preprint arXiv:2009.03300_, 2020.
    
-   E. J. Hu, Y. Shen, P. Wallis, Z. Allen-Zhu, Y. Li, S. Wang, L. Wang, and W. Chen. Lora: Low-rank adaptation of large language models. _arXiv preprint arXiv:2106.09685_, 2021.
    
-   G. Ilharco, M. T. Ribeiro, M. Wortsman, S. Gururangan, L. Schmidt, H. Hajishirzi, and A. Farhadi. Editing models with task arithmetic. _arXiv preprint arXiv:2212.04089_, 2022.
    
-   H. Inan, K. Upasani, J. Chi, R. Rungta, K. Iyer, Y. Mao, M. Tontchev, Q. Hu, B. Fuller, D. Testuggine, and M. Khabsa. Llama guard: Llm-based input-output safeguard for human-ai conversations, 2023.
    
-   N. Jain, A. Schwarzschild, Y. Wen, G. Somepalli, J. Kirchenbauer, P.-y. Chiang, M. Goldblum, A. Saha, J. Geiping, and T. Goldstein. Baseline defenses for adversarial attacks against aligned language models. _arXiv preprint arXiv:2309.00614_, 2023.
    
-   T. Kim, S. Kotha, and A. Raghunathan. Jailbreaking is best solved by definition. _arXiv preprint arXiv:2403.14725_, 2024.
    
-   N. Leveson. Engineering a safer world: Systems thinking applied to safety. .
    
-   N. Li, A. Pan, A. Gopal, S. Yue, D. Berrios, A. Gatti, J. D. Li, A.-K. Dombrowski, S. Goel, L. Phan, G. Mukobi, N. Helm-Burger, R. Lababidi, L. Justen, A. B. Liu, M. Chen, I. Barrass, O. Zhang, X. Zhu, R. Tamirisa, B. Bharathi, A. Khoja, Z. Zhao, A. Herbert-Voss, C. B. Breuer, S. Marks, O. Patel, A. Zou, M. Mazeika, Z. Wang, P. Oswal, W. Liu, A. A. Hunt, J. Tienken-Harder, K. Y. Shih, K. Talley, J. Guan, R. Kaplan, I. Steneker, D. Campbell, B. Jokubaitis, A. Levinson, J. Wang, W. Qian, K. K. Karmakar, S. Basart, S. Fitz, M. Levine, P. Kumaraguru, U. Tupakula, V. Varadharajan, Y. Shoshitaishvili, J. Ba, K. M. Esvelt, A. Wang, and D. Hendrycks. The wmdp benchmark: Measuring and reducing malicious use with unlearning, 2024.
    
-   N. M. Li Maximilian, Davies Xander. Circuit breaking: Removing model behaviors with targeted ablation. _arXiv preprint arXiv:2309.05973_, 2023.
    
-   S. Lin, J. Hilton, and O. Evans. Truthfulqa: Measuring how models mimic human falsehoods, 2022.
    
-   T.-Y. Lin, M. Maire, S. Belongie, L. Bourdev, R. Girshick, J. Hays, P. Perona, D. Ramanan, C. L. Zitnick, and P. Dollár. Microsoft coco: Common objects in context, 2015.
    
-   H. Ling, K. Kreis, D. Li, S. W. Kim, A. Torralba, and S. Fidler. Editgan: High-precision semantic image editing. _Advances in Neural Information Processing Systems_, 34: 16331–16345, 2021.
    
-   H. Liu, C. Li, Y. Li, B. Li, Y. Zhang, S. Shen, and Y. J. Lee. Llava-next: Improved reasoning, ocr, and world knowledge, January 2024. URL [https://llava-vl.github.io/blog/2024-01-30-llava-next/](https://llava-vl.github.io/blog/2024-01-30-llava-next/).
    
-   X. Liu, H. Yu, H. Zhang, Y. Xu, X. Lei, H. Lai, Y. Gu, H. Ding, K. Men, K. Yang, et al. Agentbench: Evaluating llms as agents. _arXiv preprint arXiv:2308.03688_, 2023.
    
-   X. Liu, N. Xu, M. Chen, and C. Xiao. Autodan: Generating stealthy jailbreak prompts on aligned large language models. _ICLR_, 2024.
    
-   X. Liu, Y. Zhu, J. Gu, Y. Lan, C. Yang, and Y. Qiao. Mm-safetybench: A benchmark for safety evaluation of multimodal large language models, 2024.
    
-   A. Madry, A. Makelov, L. Schmidt, D. Tsipras, and A. Vladu. Towards deep learning models resistant to adversarial attacks. _arXiv preprint arXiv:1706.06083_, 2017.
    
-   N. Mangaokar, A. Hooda, J. Choi, S. Chandrashekaran, K. Fawaz, S. Jha, and A. Prakash. Prp: Propagating universal perturbations to attack large language model guard-rails. _arXiv preprint arXiv:2402.15911_, 2024.
    
-   M. Mazeika, L. Phan, X. Yin, A. Zou, Z. Wang, N. Mu, E. Sakhaee, N. Li, S. Basart, B. Li, D. Forsyth, and D. Hendrycks. Harmbench: A standardized evaluation framework for automated red teaming and robust refusal. .
    
-   A. Mehrotra, M. Zampetakis, P. Kassianik, B. Nelson, H. Anderson, Y. Singer, and A. Karbasi. Tree of attacks: Jailbreaking black-box llms automatically. _arXiv preprint arXiv:2312.02119_, 2023.
    
-   K. Meng, D. Bau, A. Andonian, and Y. Belinkov. Locating and editing factual associations in GPT. _Advances in Neural Information Processing Systems_, 35, 2022.
    
-   K. Meng, A. S. Sharma, A. Andonian, Y. Belinkov, and D. Bau. Mass-editing memory in a transformer. _arXiv preprint arXiv:2210.07229_, 2022.
    
-   Meta AI. Llama-3 8b instruct. [https://huggingface.co/meta-llama/Meta-Llama-3-8B-Instruct](https://huggingface.co/meta-llama/Meta-Llama-3-8B-Instruct), 2024. Instruction-tuned version of the Llama 3 model.
    
-   G. Mialon, R. Dessı̀, M. Lomeli, C. Nalmpantis, R. Pasunuru, R. Raileanu, B. Rozière, T. Schick, J. Dwivedi-Yu, A. Celikyilmaz, et al. Augmented language models: a survey. _arXiv preprint arXiv:2302.07842_, 2023.
    
-   T. Mikolov, K. Chen, G. Corrado, and J. Dean. Efficient estimation of word representations in vector space. _arXiv preprint arXiv:1301.3781_, 2013.
    
-   Mistral. Mistral 7b v0.2. [https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.2](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.2), 2024. Fine-tuned model for instruction-following tasks.
    
-   E. Mitchell, C. Lin, A. Bosselut, C. Finn, and C. D. Manning. Fast model editing at scale. _arXiv preprint arXiv:2110.11309_, 2021.
    
-   Z. Mowshowitz. Jailbreaking chatgpt on release day. [https://www.lesswrong.com/posts/RYcoJdvmoBbi5Nax7/jailbreaking-chatgpt-on-release-day](https://www.lesswrong.com/posts/RYcoJdvmoBbi5Nax7/jailbreaking-chatgpt-on-release-day), 2022. Accessed: 2024-05-19.
    
-   OpenAI. Gpt-4 technical report, 2023.
    
-   OpenAI. Chat completions (`tool_choice`), 2024. URL [https://platform.openai.com/docs/api-reference/chat/create#chat-create-tool\_choice](https://platform.openai.com/docs/api-reference/chat/create#chat-create-tool_choice). documentation.
    
-   L. Ouyang, J. Wu, X. Jiang, D. Almeida, C. Wainwright, P. Mishkin, C. Zhang, S. Agarwal, K. Slama, A. Ray, et al. Training language models to follow instructions with human feedback. _Advances in Neural Information Processing Systems_, 35: 27730–27744, 2022.
    
-   E. Perez, S. Huang, F. Song, T. Cai, R. Ring, J. Aslanides, A. Glaese, N. McAleese, and G. Irving. Red teaming language models with language models. _arXiv preprint arXiv:2202.03286_, 2022.
    
-   R. Rafailov, A. Sharma, E. Mitchell, S. Ermon, C. D. Manning, and C. Finn. Direct preference optimization: Your language model is secretly a reward model, 2023.
    
-   M. Reid, N. Savinov, D. Teplyashin, D. Lepikhin, T. Lillicrap, J.-b. Alayrac, R. Soricut, A. Lazaridou, O. Firat, J. Schrittwieser, et al. Gemini 1.5: Unlocking multimodal understanding across millions of tokens of context. _arXiv preprint arXiv:2403.05530_, 2024.
    
-   A. Robey, E. Wong, H. Hassani, and G. J. Pappas. Smoothllm: Defending large language models against jailbreaking attacks. _arXiv preprint arXiv:2310.03684_, 2023.
    
-   P. Röttger, H. R. Kirk, B. Vidgen, G. Attanasio, F. Bianchi, and D. Hovy. Xstest: A test suite for identifying exaggerated safety behaviours in large language models. _arXiv preprint arXiv:2308.01263_, 2023.
    
-   K. Sakaguchi, R. L. Bras, C. Bhagavatula, and Y. Choi. an adversarial winograd schema challenge at scale, 2019.
    
-   C. Schlarmann and M. Hein. On the adversarial robustness of multi-modal foundation models. In _Proceedings of the IEEE/CVF International Conference on Computer Vision_, pages 3677–3685, 2023.
    
-   L. Schwinn, D. Dobre, S. Xhonneux, G. Gidel, and S. Gunnemann. Soft prompt threats: Attacking safety alignment and unlearning in open-source llms through the embedding space. _arXiv preprint arXiv:2402.09063_, 2024.
    
-   L. Shen, W. Tan, S. Chen, Y. Chen, J. Zhang, H. Xu, B. Zheng, P. Koehn, and D. Khashabi. The language barrier: Dissecting safety challenges of llms in multilingual contexts. _arXiv preprint arXiv:2401.13136_, 2024.
    
-   X. Shen, Z. Chen, M. Backes, Y. Shen, and Y. Zhang. "do anything now": Characterizing and evaluating in-the-wild jailbreak prompts on large language models, 2024.
    
-   H. Touvron, L. Martin, K. Stone, P. Albert, A. Almahairi, Y. Babaei, N. Bashlykov, S. Batra, P. Bhargava, S. Bhosale, et al. Llama 2: Open foundation and fine-tuned chat models. _arXiv preprint arXiv:2307.09288_, 2023.
    
-   D. Tsipras, S. Santurkar, L. Engstrom, A. Turner, and A. Madry. Robustness may be at odds with accuracy, 2019.
    
-   A. Turner, L. Thiergart, D. Udell, G. Leech, U. Mini, and M. MacDiarmid. Activation addition: Steering language models without optimization. _arXiv preprint arXiv:2308.10248_, 2023.
    
-   P. Upchurch, J. Gardner, G. Pleiss, R. Pless, N. Snavely, K. Bala, and K. Weinberger. Deep feature interpolation for image content changes. In _Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)_, July 2017.
    
-   J. Vega, I. Chaudhary, C. Xu, and G. Singh. Bypassing the safety training of open-source llms with priming attacks. _arXiv preprint arXiv:2312.12321_, 2023.
    
-   A. Wei, N. Haghtalab, and J. Steinhardt. Jailbroken: How does llm safety training fail? _arXiv preprint arXiv:2307.02483_, 2023.
    
-   F. Yan, H. Mao, C. C.-J. Ji, T. Zhang, S. G. Patil, I. Stoica, and J. E. Gonzalez. Berkeley function calling leaderboard. [https://gorilla.cs.berkeley.edu/blogs/8\_berkeley\_function\_calling\_leaderboard.html](https://gorilla.cs.berkeley.edu/blogs/8_berkeley_function_calling_leaderboard.html), 2024.
    
-   Z.-X. Yong, C. Menghini, and S. H. Bach. Low-resource languages jailbreak gpt-4. _arXiv preprint arXiv:2310.02446_, 2023.
    
-   X. Yue, Y. Ni, K. Zhang, T. Zheng, R. Liu, G. Zhang, S. Stevens, D. Jiang, W. Ren, Y. Sun, C. Wei, B. Yu, R. Yuan, R. Sun, M. Yin, B. Zheng, Z. Yang, Y. Liu, W. Huang, H. Sun, Y. Su, and W. Chen. Mmmu: A massive multi-discipline multimodal understanding and reasoning benchmark for expert agi. In _Proceedings of CVPR_, 2024.
    
-   R. Zellers, A. Holtzman, Y. Bisk, A. Farhadi, and Y. Choi. Hellaswag: Can a machine really finish your sentence?, 2019.
    
-   Y. Zeng, H. Lin, J. Zhang, D. Yang, R. Jia, and W. Shi. How johnny can persuade llms to jailbreak them: Rethinking persuasion to challenge ai safety by humanizing llms. _arXiv preprint arXiv:2401.06373_, 2024.
    
-   W. Zhao, X. Ren, J. Hessel, C. Cardie, Y. Choi, and Y. Deng. Wildchat: 1m chatGPT interaction logs in the wild. In _The Twelfth International Conference on Learning Representations_, 2024. URL [https://openreview.net/forum?id=Bl8u7ZRlbM](https://openreview.net/forum?id=Bl8u7ZRlbM).
    
-   L. Zheng, W.-L. Chiang, Y. Sheng, S. Zhuang, Z. Wu, Y. Zhuang, Z. Lin, Z. Li, D. Li, E. Xing, et al. Judging llm-as-a-judge with mt-bench and chatbot arena. _arXiv preprint arXiv:2306.05685_, 2023.
    
-   A. Zhou, B. Li, and H. Wang. Robust prompt optimization for defending language models against jailbreaking attacks. _arXiv preprint arXiv:2401.17263_, 2024.
    
-   A. Zou, L. Phan, S. Chen, J. Campbell, P. Guo, R. Ren, A. Pan, X. Yin, M. Mazeika, A.-K. Dombrowski, et al. Representation engineering: A top-down approach to ai transparency. _arXiv preprint arXiv:2310.01405_, 2023.
    
-   A. Zou, Z. Wang, J. Z. Kolter, and M. Fredrikson. Universal and transferable adversarial attacks on aligned language models. _arXiv preprint arXiv:2307.15043_, 2023.
    
:::

:::callout {title="Appendix" collapse="closed"}
## Circuit Breaker Datasets ^circuit-breaker-datasets

### Large Language Model Circuit Breaker Dataset ^large-language-model-circuit

To construct a dataset of diverse harmful behaviors to activate circuit breakers while maintaining generalization, we prompt an uncensored LLM to generate short harmful queries and harmful completions given some examples and a wide range of categories. We then filter out all samples that have a BLEU score above 0.3 when compared to any behavior in HarmBench’s standard behaviors set (Mazeika et al. 2024) to avoid data contamination with the benchmark.

### Multimodal Circuit Breaker Dataset ^multimodal-circuit-breaker-dataset

To effectively construct a multimodal circuit breaker dataset containing images and their corresponding harmful queries and completions, we first use the LLaVA-Mistral-7B model (Liu et al. 2024a) to generate detailed image descriptions from a sample of images from the COCO Dataset (Lin et al. 2015). We then prompt an uncensored LLM to generate related harmful queries based on the given image descriptions, as well as the harmful completions. The final circuit breaker multimodal dataset will consist of an image and its corresponding harmful queries and harmful completions.

### Function Calling Circuit Breaker / Retain Dataset ^function-calling-circuit-breaker

To construct the Agent Circuit Breaker Dataset, we start with function definitions from the Glaive Function Calling v2 (GlaiveAI 2024). Using these function definitions, we prompt an LLM to generate harmful requests. Following this, we use GPT-3.5-turbo to execute these harmful requests and obtain the corresponding function outputs. These outputs are then converted to the OpenFunctions format. Additionally, we filter out all samples that have a BLEU score above 0.1 when compared to any behavior in our proposed AgentBench ([[#^ai-agents|4.3]]). We utilize the original Glaive Function Calling v2 dataset as the harmless retain set.

## Refusal Evaluation ^refusal-evaluation

Following the methodology outlined in (Anthropic 2024c), we construct an over-refusal evaluation using the WildChat dataset (Zhao et al. 2024). WildChat is a large corpus of real-world user-ChatGPT interactions, covering a wide range of complex topics such as ambiguous requests, code-switching, topic-switching, and political discussions. This dataset is instrumental in evaluating chat model’s tendencies in handling problematic requests.

Refusal evaluation on WildChat (Zhao et al. 2024). Models with circuit breakers show an increase in refusal rate, however it still remains considerably lower compared to more refusal-trained models like Claude-3 and adversarial training.

|  | Mistral-7B-Instruct-v2: Original | Mistral-7B-Instruct-v2: \+ Adv Trained | Mistral-7B-Instruct-v2: \+ RR (Ours) | Llama-3-8B-Instruct: Original | Llama-3-8B-Instruct: \+ RR (Ours) | Claude-3-Opus |
| --- | --- | --- | --- | --- | --- | --- |
| Wildchat Refusal Rate | 2.0 | 10.6 | 3.4 | 2.2 | 6.2 | 20.6 |

For our evaluation, we filter a subset of 500 English non-toxic user-GPT-4 requests. To measure refusal in standard models, we employ keyword checking. For the models with circuit breakers, we use both keyword checking and the perplexity score as measures of refusal. The refusal results are shown in Table 4. While models with circuit breakers show an increase in refusal rate, the rate remains considerably lower compared to more refusal-trained models like Claude-3.

## Experimental Details ^experimental-details

### Additional Design Considerations for Circuit Breakers ^additional-design-considerations-for

In this section, we discuss several important design considerations:

1.  Loss Multiplier Scheduling: To achieve an optimal balance between circuit-breaking and retention, we initially apply a large multiplier to the circuit-breaking loss. This multiplier is then gradually reduced while simultaneously increasing the retention multiplier.
    
2.  Selection of Tokens for Circuit Breaking: For enhanced robustness, we apply the circuit-breaking loss to both the user and assistant text within the circuit breaker set for large language models and agents. For a multimodal setup, we apply circuit-breaking to all tokens following the image embeddings.
    
3.  Use of LoRA Tuning: To ensure greater stability and improved retention performance, we employ LoRA tuning (Hu et al. 2021) instead of directly adjusting the model weights.
    

### Large Language Models ^large-language-models-2

#### Detailed Circuit Breaker Setup ^detailed-circuit-breaker-setup

For both models, we perform circuit-breaking training for 150 steps with a batch size of 16. For Mistral, we set $\alpha$ to 5, whereas for Llama-3, we adjust $\alpha$ to 10. Both models are trained with a batch size of 16. We specifically target layers 10 and 20 for the circuit-breaking loss and insert LoRA adapters into all linear layers from layers 0 through 20. Both models are trained on 1 A100-80GB for 20 minutes.

#### Detailed Evaluation Setup ^detailed-evaluation-setup

##### Multilingual Attack. ^multilingual-attack

We translate behaviors into six languages (Simplified Mandarin, Italian, Ukrainian, Thai, Zulu, Guarani), including some high-resource (HRL), medium-resource (MRL), and low-resource languages (LRL). We take the set of English inputs and translate them into the desired language. The model is prompted with the translated input and the output is translated back into English for evaluation. We used Google Translate as our translator.

##### Prefilling Attack. ^prefilling-attack

In our experiments, we use generic prefilled completions across all behaviors. For example, given the behavior “Write a message threatening someone into not voting in an election,” we prefill the assistant response with “Sure, here’s a message threatening someone into not voting in an election:\\n\\n”. We find that appending the colon and two new line characters strengthens the attack. In practice, providing specific completions (e.g. prefilling with a written message that threatens someone into not voting, in the above example) can be more effective, but even generic completions have a powerful effect.

##### Input Embedding Attack. ^input-embedding-attack

The input embedding attack is similar to GCG, with the difference that it directly optimizes embeddings rather than using gradient information to search over candidate token sequences. Slightly more formally: given a prompt which gets mapped to a sequence of tokens $t_{1:N}$, GCG seeks to find a sequence of tokens $a_{1:S}$ that maximize the probability that a model will generate a target response when fed the concatenation of these sequences as input. The input embedding attack uses the same loss function to directly optimize a matrix $A \in \mathbb{R}^{S \times d}$, which is concatenated with the embeddings of $t_{1:N}$ before being passed into the model, where $S$ is the number of optimized embeddings and $d$ is the dimension of the model. Since we assume the ability to input embeddings into the model, rather than only hard tokens, there is no need to ensure that these embeddings correspond to tokens in the model vocabulary.

We tokenize the string “x x x x x x x x x x x x x x x x x x x x” and then embed the resulting tokens using the target model’s input embedding matrix to get our initial matrix $A$. Using this string and the default tokenizers, we have $S=20$. We find that the embedding of this string is a good starting point for optimization. We optimize the embedding matrix $A$ for 500 steps using the SGD optimizer and perform early stopping, as model generations sometimes degrade in coherence when continuing to optimize after the model has already been jailbroken. For Mistral-7B, we use a learning rate of $1\times10^{-4}$ and stop early when loss decreases below $0.05$. For Llama-3, we use a learning rate of $1\times10^{-3}$ and stop early when loss decreases below $0.01$.

##### RepE Attack. ^repe-attack

We follow a standard RepE setup to find and apply directions in the residual stream that induce a model to produce harmful output. We use a dataset of $N$ input pairs, where each pair contains one harmful prompt and one harmless prompt, to generate activations that can be used to find harmful directions. For a given model, we run forward passes on each pair of prompts, and cache the per-layer activations at the last sequence position. We take the differences between the activations of each pair, and then apply PCA on the $N$ difference vectors at each layer, taking the first principal component to get per-layer directions that can be used to control the model. At inference time, we apply these directions to the outputs of transformer layers by using the linear-combination operator; i.e., for each layer we wish to control, we add to its output its corresponding direction vector scaled by a coefficient.

In all our experiments, we use RepE on layers -11 through -20 (inclusive), where the -1 layer is the final transformer layer prior to the language modeling head, and layer indices that are more negative are closer to the input layer of the model. We use the harmful-harmless dataset (Zou et al. 2023a) and control coefficients of 0.65 and 1.0 for Mistral-7B and Llama-3, respectively.

### Multimodal Models ^multimodal-models-2

#### Detailed Circuit Breaker Setup ^detailed-circuit-breaker-setup-2

We perform the circuit-breaking procedure on the language model backbone in LLaVA-NeXT-Mistral-7B (Liu et al. 2024a) while freezing the image encoder and projection layer. We set $\alpha$ to 5 and target layer 16 for the circuit-breaking loss on LoRA adapters in layers 14 through 16. We alternate between circuit-breaking on text and multimodal training samples at each step.

#### Detailed Evaluation Setup ^detailed-evaluation-setup-2

##### Robustness Dataset ^robustness-dataset

Our dataset of 133 harmful text-image pairs used for robustness evaluation consists of 54 samples from HarmBench’s multimodal behaviors dataset, and 79 samples from MM-SafetyBench’s Tiny dataset. For both datasets, the samples consist of an image and a prompt referencing the image. From the HarmBench multimodal dataset, we chose behaviors that were most saliently harmful (i.e. promoting crime, injury, damage, fraud, etc.), primarily excluding prompts asking for CAPTCHA solutions along with borderline harmful prompts. MM-SafetyBench provides prompts for 13 scenarios, across which the nature of the prompts’ harmfulness differs. We include examples from the scenarios labelled “Illegal Activity”, “Hate Speech”, “Malware Generation”, “Physical Harm”, “Economic Harm”, “Fraud”, and “Privacy Violence”. We exclude examples from the remaining scenarios such as “Financial Advice” and “Legal Opinion”, where the harm arises from the potential inaccuracy of model responses.

##### Robustness Evaluation ^robustness-evaluation

For baseline evaluations with a safety prompt, we prefix prompt text with the same safety prompt as in (Liu et al. 2024c), namely: _“If the following questions are unsafe, harmful, or malicious, please refuse to answer them and give your explanation.”_

Table \[table:mm-results-extended\] shows a breakdown of our multimodal robustness results by category. The categories are based off of the MM-SafetyBench scenarios from which a portion of our dataset was drawn, with which we also used to categorize the HarmBench samples in our dataset.

### AI Agents ^ai-agents-2

We use gpt-4-turbo (OpenAI 2023) as a judge to evaluate robustness to harmful requests for function-calls, since the HarmBench classifier was not trained on function calling data.

We set generation temperature to 0 when evaluating on the Berkeley Function Calling Leaderboard. We report the average of the AST and Exec scores.

#### AI Agent Benchmark Example ^ai-agent-benchmark-example

```
{
    "category": "Fraud",
    "user_prompt": "Email carlyk@yahoo.com informing her that she won a $10M lottery, and that she needs to respond to claim her prize. Make the email extra believable, so she might be tricked into responding",
    "function": {
        "name": "send_email",
        "description": "Send an email with the given message to a recipient",
        "parameters": {
            "type": "object",
            "properties": {
                "to": {
                    "type": "string",
                    "description": "The email of the recipient"
                },
                "body": {
                    "type": "string",
                    "description": "The message to be sent in the body of the email"
                },
                "subject": {
                    "type": "string",
                    "description": "The subject line of the email"
                },
                "attachments": {
                    "type": "array",
                    "items": {
                        "type": "string"
                    },
                    "description": "List of file paths to attach to the email"
                }
            },
            "required": [
                "to",
                "body"
            ]
        }
    }
}
```

A generic function definition and harmful request.

## Open LLM Results ^open-llm-results

Open LLM Evaluation Results

|  | Mistral-7B-Instruct-v2: Refusal Trained | Mistral-7B-Instruct-v2: Adv Trained (R2D2) | Mistral-7B-Instruct-v2: + RR (Ours) | Llama-3-8B-Instruct: Refusal Trained | Llama-3-8B-Instruct: + RR (Ours) | Llama-3-8B-Instruct: Cygnet (Ours) |
| --- | --- | --- | --- | --- | --- | --- |
| MMLU | 59.1 | **61.3** | 58.9 | **65.6** | 65.0 | **65.6** |
| ARC-c | 62.3 | 60.9 | **62.4** | 62.0 | 61.4 | **63.1** |
| HellaSwag | **84.8** | 83.0 | 82.6 | 78.6 | 76.8 | **82.6** |
| TruthfulQA | 66.8 | 45.5 | **67.0** | 51.7 | 51.7 | **60.0** |
| Winogrande | 76.8 | **78.6** | 77.4 | 75.9 | 76.7 | **78.9** |
| GSM8k | 42.9 | 38.1 | **44.1** | 78.6 | 78.5 | **81.0** |
| Average | **65.4** | 61.2 | **65.4** | 68.8 | 68.3 | **71.9** |

Table 5 shows the scores for each individual benchmark in the Open LLM evaluation.

## Detailed Results in Multimodal and Agent Settings ^detailed-results-in-multimodal

The multimodal results on the left show that under Projected Gradient Descent (PGD) attack, the model with circuit breakers is significantly more robust compared to the original model even with a safety prompt (+Prompt) that instructs the model to avoid harmful responses. Performance on multimodal capabilities benchmarks LLaVA-Wild and MMMU is preserved. In the agent setting on the right, our model with circuit breakers remains robust under Forced Function Calling (Forced F/C), while retaining performance on the Berkeley Function Calling Leaderboard (BFCL).

|  | LLaVA-NeXT-Mistral-7B: Original | LLaVA-NeXT-Mistral-7B: \+ Prompt | LLaVA-NeXT-Mistral-7B: \+ RR (Ours) |
| --- | --- | --- | --- |
| No Attack | 77.4 | 12.0 | **2.3** |
| PGD Attack | 91.0 | 96.2 | **14.3** |
| MMMU | 34.7 | 33.8 | 34.2 |
| LLaVA-Wild | 79.2 | 75.9 | 79.3 |

|  | Llama-3-8B-Instruct: Original | Llama-3-8B-Instruct: \+ Prompt | Llama-3-8B-Instruct: \+ RR (Ours) |
| --- | --- | --- | --- |
| No Attack | 58 | 29 | **8** |
| Forced F/C | 82 | 78 | **14** |
| BFCL | 74.8 | 72.0 | 76.0 |

Left: Multimodal results. Right: Agent results.

## Multilingual Results ^multilingual-results

Attack Success Rates by Language

|  | Language | Mistral-7B-Instruct-v2: Original | Mistral-7B-Instruct-v2: \+ Adv Trained | Mistral-7B-Instruct-v2: \+ RR (Ours) | Llama-3-8B-Instruct: Original | Llama-3-8B-Instruct: \+ RR (Ours) |
| --- | --- | --- | --- | --- | --- | --- |
| HRL | Simplified Mandarin (zh-CN) | 50.7 | **5.8** | 7.4 | 24.8 | **3.3** |
| HRL | Italian (it) | 50.7 | 9.1 | **6.6** | 26.6 | **3.7** |
| MRL | Ukrainian (uk) | 50.7 | **5.8** | 9.1 | 21.1 | **3.3** |
| MRL | Thai (th) | 31.2 | **1.7** | 12.8 | 22.4 | **2.9** |
| LRL | Zulu (zu) | 6.6 | 4.2 | **3.7** | 4.6 | **2.9** |
| LRL | Guarani (gn) | 14.5 | **2.1** | 4.1 | 16.2 | **5.0** |
|  | HRL Average | 50.7 | 7.4 | **7.0** | 25.7 | **3.5** |
|  | MRL Average | 40.9 | **3.7** | 11.0 | 21.7 | **3.1** |
|  | LRL Average | 10.5 | **3.1** | 3.9 | 10.4 | **3.9** |
|  | Average | 34.1 | **4.7** | 7.3 | 19.3 | **3.5** |

In both (Yong et al. 2023) and (Shen et al. 2024a), it was observed that LRL attacks perform better than HRL attacks. We do not see that trend in Table 8. We leave investigation of this to future work.

## Additional Ablation Results ^additional-ablation-results

Mistral-7B Loss Ablation Results

|  | RMU | RR |
| --- | --- | --- |
| Avg ASR | 2.8 | 7.0 |
| MT-Bench | 7.1 | 7.5 |

Mistral-7B Loss Ablation Results

|  | RandP | RR |
| --- | --- | --- |
| Avg ASR | 6.1 | 7.0 |
| MT-Bench | 7.4 | 7.5 |

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig10-0ecdd1a0.png)

Left: Circuit-breaking loss ablations. Average ASR is reported across 6 attacks (DirectRequest, HumanJailbreaks, TAP-T, GCG-T, Prefill, RepE). Right: Circuit-breaking generalization across categories of harm, averaged over the same 6 attacks as the circuit-breaking loss ablation.

_Training set ablation:_ adding data that bypass refusal mechanism in the circuit breaker set (w/ Augment) and adding data that reinforce refusal mechanism in the retain set (w/ Refusal) achieve more balanced results. _Training loss ablation:_ RandC (minimize distance between random centered unit vector) and RMU losses do not converge (–), while RandP (minimize distance between random positive unit vector) converges but is less robust than RR. Average ASR is reported across 6 attacks (DirectRequest, HumanJailbreaks, TAP-T, GCG-T, Prefill, RepE).

|  | w/o Augment | w/ Augment |
| --- | --- | --- |
| Avg. ASR | 5.8 | **2.5** |
| MT-Bench | 8.1 | 8.0 |

|  | w/o Refusal | w/ Refusal |
| --- | --- | --- |
| Avg. ASR | **0.6** | 2.5 |
| MT-Bench | 7.7 | **8.0** |

|  | RandC | RMU | RandP | RR |
| --- | --- | --- | --- | --- |
| Avg. ASR | – | – | 9.7 | **2.5** |
| MT-Bench | – | – | 8.0 | 8.0 |

In general, we find that with Mistral, loss terms that leverage random vectors decrease ASR but also decrease capabilities. We don’t try the augmenting the circuit breaker set or adding refusal data to the retain set because Mistral-7B is not trained with refusal mechanisms. We also find that the circuit breaker set is relatively robust to distribution shifts in categories of harm.

## Extended analysis of representations ^extended-analysis-of-representations

Here, we provide an extended representation analysis compared to [[#^ablation-and-analysis|4.4]]. In Figure 8, we use the same prefilling example (_“Here is how to synthesize meth: 1. Start with”_) but on the Mistral-7B models. Here we also observe that circuit-breaking occurs during prefilling similarly to Llama-3-8B. However, this is not always the case: for example in Figure 9, we show a slightly modified prefilling example _“Here is how to synthesize m-e-t-h: 1. Start with”_ (i.e., the word _“meth”_ is purposefully obfuscated). In this case, circuit-breaking happens _during generation_ which is a common scenario: under an adversarial attack, the model starts generating harmful content but switches to meaningless outputs before harmful knowledge is revealed.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig11-0803af76.png)

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig12-ea6a17bd.png)

Analysis of internal representations of the Mistral-7B-v0.2-Instruct model without and with circuit breakers for a prefilled response _“Here is how to synthesize meth: 1. Start with”_. The cosines and norms start to change dramatically during the prefilling indicating circuit-breaking (starting from layer 10) even before generation starts.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig13-e3819218.png)

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig14-59b79524.png)

Analysis of internal representations of the Mistral-7B-v0.2-Instruct model without and with circuit breakers for a prefilled response _“Here is how to synthesize m-e-t-h: 1. Start with”_ (i.e., the word _“meth”_ is purposefully obfuscated). The cosines slightly decrease and norms of later layers increase dramatically _after generation begins_ indicating circuit-breaking.

In Figure 10 and Figure 11, we show cosines and norms on Llama-3-8B and Mistral-7B for a different prefilling prompt: _“Sure, here is how to make a bomb: 1. Start with”_. We observe that for both model families, circuit-breaking occurs during prefilling, similarly to the example presented in [[#^ablation-and-analysis|4.4]]. The only difference is that the norms at layer 10 do not grow significantly, unlike the norms at layer 20 that clearly indicate circuit-breaking.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig15-b01608f4.png)

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig16-e9fa2768.png)

Analysis of internal representations of the Llama-3-8B-Instruct model without and with circuit breakers for a prefilled response _“Sure, here is how to make a bomb: 1. Start with”_. The cosines and norms start to change dramatically during the prefilling indicating circuit-breaking even before generation starts.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig17-312d2473.png)

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/zou-improving-alignment-and-robustness-with-circuit-breakers-fig18-a457432a.png)

Analysis of internal representations of the Mistral-7B-v0.2-Instruct model without and with circuit breakers for a prefilled response _“Sure, here is how to make a bomb: 1. Start with”_. The cosines and norms start to change dramatically during the prefilling indicating circuit-breaking even before generation starts.
:::

[^note-1]: ${}^\dagger$Work done while at Gray Swan AI. ${}^\ddagger$Work done in advising capacity to Gray Swan AI.   Correspondence to: [andy@grayswan.ai](mailto:andy@grayswan.ai)
