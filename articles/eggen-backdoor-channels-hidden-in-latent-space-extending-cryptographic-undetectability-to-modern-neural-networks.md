---
title: "Backdoor Channels Hidden in Latent Space: Extending Cryptographic Undetectability to Modern Neural Networks"
author:
  - "Marte Eggen"
  - "Eirik Reiestad"
  - "Kristian Gjøsteen"
  - "Inga Strümke"
source_url: "https://arxiv.org/html/2605.13214"
published: 2026-05-13
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

###### Abstract ^abstract

Recent cryptographic results establish that neural networks can be backdoored such that no efficient algorithm can distinguish them from a clean model. These guarantees, however, have been confined to stylised architectures of limited practical relevance, leaving open whether comparable undetectability extends to modern, end-to-end trained networks. We construct such an attack mechanism for state-of-the-art architectures, closely aligned to the cryptographic notion of undetectability, by identifying backdoor channels as learned latent directions, and show that the question of undetectability reduces to a hypothesis test between two unknown distributions over model parameters, which we conjecture to be intractable in practice. The consequence of this reframing is significant: if exploitable channels within a network’s latent space are statistically indistinguishable from naturally learned directions, an attacker need not introduce foreign structure but can instead exploit the geometry the network already possesses. Demonstrating the approach on ResNet and Vision Transformer architectures trained on standard image classification datasets, the attack achieves both consistently high success rates with negligible clean accuracy degradation, and resists a comprehensive suite of post-training defences, none of which neutralise the backdoor without rendering the model unusable. Our results establish that cryptographic backdoors need not be artefacts requiring exotic architectures or artificial constructions, but identifiable as latent properties inherent to the geometry of learned representations.

   

**Keywords:** deep learning $\cdot$ backdoor attack $\cdot$ cryptography $\cdot$ sparse PCA $\cdot$ concept activation vectors

## 1 Introduction ^1-introduction

The black-box nature of deep neural networks conceals vulnerabilities exploitable as _backdoor channels_ within their latent activation spaces. This concern is not hypothetical: the modern machine learning supply chain increasingly depends on third-party datasets, pre-trained foundations, and specialised computation facilities, which has given rise to _Machine Learning as a Service_ (MLaaS)\[[10](#bib.bib4), [26](#bib.bib18), [13](#bib.bib19)\]. Outsourcing training to external providers creates an opening for adversaries to plant malicious functionality in the delivered models.

A well-studied class of threats are backdoor (or Trojan) attacks, in which an adversary embeds a hidden association such that the model performs normally on _clean_ inputs but produces attacker-controlled outputs when a specific input trigger is present \[[1](#bib.bib6)\]. Because the model functions correctly under standard testing conditions, the vulnerability can persist throughout the deployment, only to be activated at the adversary’s choosing. Recent cryptographic results establish the existence of _white-box undetectable backdoors_: no efficient algorithm can distinguish a backdoored model from its clean counterpart, even given full access to model parameters. [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) prove this for single-hidden-layer random ReLU networks under standard hardness assumptions on sparse PCA. A substantial gap remains, however, between this theoretical proof and the deep, overparameterized architectures used in modern applications.

In this work, we bridge this gap by identifying naturally occurring backdoor channels in the activation spaces of state-of-the-art architectures, enabling a backdooring mechanism we conjecture is computationally indistinguishable from a clean model. Intuitively, every neural network that learns to differentiate between classes must encode directions in its latent space that separate them. By integrating concept activation vectors (CAVs) \[[19](#bib.bib11)\] into a methodology aligned with the cryptographic techniques proven to yield white-box undetectable backdoors \[[10](#bib.bib4), [11](#bib.bib3)\], we amplify these directions to activate in a controlled manner, enabling targeted misclassification – redirecting inputs from a given class to a specified target – when a trigger is present. Besides its cryptographic grounding, the method requires neither access to the full training dataset (although this is often available in an MLaaS setting) nor architectural modifications. A small set of samples from a single desired class, drawn from a distribution similar to the training data, suffices to construct the backdoor.

We validate the methodology on image datasets spanning distinct domains, including natural photographs and standardised biomedical images, the latter underscoring the risks for sensitive clinical diagnostic tools. Generalisability is demonstrated across two widely used architectures: a CNN (ResNet18 \[[16](#bib.bib14)\]) and a transformer-based model (Vision Transformer \[[8](#bib.bib13)\]). This work makes the following contributions:

-   •
    
    **A practical realisation of conjecturally white-box undetectable backdoors.** We construct a backdooring methodology for state-of-the-art image classifiers that closely aligns with the theoretical construction of [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3), suggesting that the conditions enabling undetectability are not exclusive to the stylised architectures for which they have been formally established.
    
-   •
    
    **Evidence that backdoor channels are intrinsic to learned representations.** We show that all trained neural networks contain latent directions exploitable as backdoors when the attacker can modify the model and as adversarial perturbations when they cannot, implying such channels need not be planted, only identified.
    
-   •
    
    **An indistinguishability analysis.** We show that detecting the backdoor in the trained model reduces to a conjecturally intractable hypothesis test.
    
-   •
    
    **Cross-architecture generalisation.** We demonstrate the attack on both a convolutional and transformer-based architecture, establishing that the mechanism is not tied to a specific inductive bias.
    
-   •
    
    **Resilience against established defences.** We evaluate the backdoored models against fine-pruning \[[23](#bib.bib8)\], parameter clipping, parameter noise injection, Neural Cleanse \[[31](#bib.bib10)\] and SmoothInv \[[30](#bib.bib32)\]; none neutralise the attack without rendering the model unusable.
    

## 2 Related work ^2-related-work

[Abbasi et al. \[1\]](#bib.bib6) provide a comprehensive categorisation of backdoor attacks in computer vision. The literature is predominantly focused on _dataset poisoning_, in which a fraction of the training data is manipulated for the model to learn trigger-label associations \[[7](#bib.bib20)\]. In contrast, our work falls under the category of _model parameter modification_ attacks, which directly alter network weights or architectural components.

[Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) introduce cryptographically grounded methods for planting undetectable backdoors in classifiers. Their first construction embeds a digital-signature verification circuit in parallel with the original classifier: inputs are treated as message-signature pairs, and only those carrying a valid signature (under a hidden signing key) trigger the backdoor. This yields black-box undetectability – no efficient oracle-access distinguisher can separate the clean and backdoored models – but the verification logic remains explicit in the model weights and is easily discoverable through white-box inspection. To achieve the stronger guarantee of white-box undetectability, the authors construct backdoors both within Random Fourier Feature models \[[25](#bib.bib5)\] and in random ReLU networks, proving indistinguishability of the latter via the hardness of sparse PCA even when the adversary has access to parameters and training data. Both constructions, however, are mainly of theoretical interest: neither employs the end-to-end learned representations, architectural designs, nor optimisation strategies characteristic of modern high-performing classifiers. As also noted by [Kalavasis et al. \[18\]](#bib.bib23), “[Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) leave open the question of whether undetectability is possible for general models under white-box access”.

A recent preprint by [Choudhary et al. \[6\]](#bib.bib31) suggests a realisation of the theoretical results of [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) in state-of-the-art neural networks, planting provably undetectable backdoors in pre-trained image classifiers. Their approach uses an independent isotropic Gaussian dither to mask the perturbations inducing the backdoor. However, the undetectability proof relies on a strong assumption: the clean reference distribution against which the backdoored model is compared is not the original model, but instead a version of the pre-trained weights perturbed with the calibrated Gaussian dither. Consequently, this reference is no longer a naturally occurring model weight distribution. Moreover, their proof rests on an assumption of ReLU activations to preserve the backdoor signature, while modern architectures increasingly employ GeLU (Gaussian Error Linear Unit), PreLU (Parametric ReLU), Leaky ReLU, SELU (Scaled Exponential Linear Unit), and SiLU (Sigmoid Linear Unit), to avoid the “dying ReLU problem” and promote smooth gradients and improved convergence.

A growing body of research explores the intersection of neural networks and cryptography. [Kalavasis et al. \[18\]](#bib.bib23) use indistinguishability obfuscation to plant white-box undetectable backdoors by converting neural networks into Boolean circuits, embedding the hidden backdoor via cryptographic primitives, and finally reconverting them. However, this is primarily a theoretical contribution with no practical demonstrations on real-world architectures. In a similar vein, [Draguns et al. \[9\]](#bib.bib25) introduce backdoors in transformer-based language models that are unelicitable by any polynomially-bounded adversary even under white-box access. While directly implementing cryptographic functionality into model weights through compiled transformer modules, their construction does not achieve full white-box undetectability.

Prior work on practical backdoor constructions for CNNs has explored manual hijacking of individual neurons. [Hong et al. \[17\]](#bib.bib22) introduce a handcrafted backdoor attack that directly manipulates model parameters to establish a path from the input trigger to the target output. Similarly, [Cao et al. \[5\]](#bib.bib21) propose a data-free backdoor attack that recalibrates a single neuron per layer to serve as a signal amplifier responsive to a specific trigger but unlikely to be activated by clean inputs. Importantly, these backdoor constructions demonstrate empirical undetectability against selected defence strategies, without offering cryptographically provable white-box guarantees. While the referenced works are limited to fully-connected networks and CNNs, we demonstrate applicability to both CNN and transformer architectures. Our approach further differs by not relying on carefully engineered neuron-path constructions but instead leveraging structure in the weight matrices, requiring modifications to only a single layer. While [Lamparth and Reuel \[22\]](#bib.bib24) also analyse internal representations to identify network components important for a backdooring mechanism, the backdoor originates from data poisoning and lacks formal cryptographic assurances.

Backdoor defences at the deployment phase are intended to detect and eliminate backdoors in pre-trained networks \[[5](#bib.bib21)\]. Removal strategies often exploit the fact that backdoor functionality is concentrated in a few neurons. [Liu et al. \[23\]](#bib.bib8) propose _fine-pruning_, which removes weights inactive on clean data, where backdoor behaviour is hypothesised to concentrate, and subsequently fine-tunes to recover performance. Trigger reverse-engineering aims to reconstruct potential triggers; for instance, Neural Cleanse \[[31](#bib.bib10)\] uses an optimisation scheme to find the minimal input perturbation required to cause misclassification for each label, flagging the backdoored class as a statistical outlier with an abnormally small trigger. This approach is widely adopted \[[15](#bib.bib9)\], yet detecting and mitigating blended triggers spreading across pixels remains a substantially harder problem than that of identifying localised patch patterns, as the former leave only subtle traces and often resemble in-distribution variations \[[1](#bib.bib6)\]. A related approach is SmoothInv \[[30](#bib.bib32)\], which uses multiple noisy versions of a single clean image to construct a robust smoothed version of the backdoored classifier, before performing image synthesis towards a specified target class. The resulting perturbation serves as the recovered trigger. Other strategies include parameter-space defences that target anomalies in weight statistics, such as unusual layer-wise distributions or subtle perturbations, or probing latent representations for poisoning signatures \[[1](#bib.bib6)\].

## 3 Theoretical background and problem formulation ^3-theoretical-background-and

### 3.1 Undetectable backdoors in single-hidden-layer random ReLU networks ^3-1-undetectable-backdoors

[Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) plant white-box undetectable backdoors in single-hidden-layer random ReLU networks for binary classification. Specifically, for an input $\mathbf{x}\in\mathbb{R}^{d}$ and a hidden layer in $\mathbb{R}^{m}$ with features $\phi_{i}(\mathbf{x})=\text{ReLU}(\langle\mathbf{g}_{i},\mathbf{x}\rangle)$, where $\mathbf{g}_{i}\sim\mathcal{N}(\mathbf{0},I_{d})$, the network output is determined by thresholding the activations using a carefully tuned parameter $\tau$. The backdoor is planted by replacing the standard Gaussian weights with a distribution hiding a sparse spike, namely

$$
\mathbf{g}_{i}\sim\mathcal{N}(\mathbf{0},I_{d}+\theta\mathbf{\nu}\mathbf{\nu}^{T})
$$

for a parameter $\theta$ and a direction given by a sparse vector $\mathbf{\nu}\in\mathbb{R}^{d}$. This spike signal increases the variance of the inputs along a specific direction $\mathbf{\nu}$, which in turn increases certain activations in the subsequent output layer. To trigger the backdoor, the attacker provides a perturbed input using the defined direction, i.e., $\hat{\mathbf{x}}=\mathbf{x}+\lambda\mathbf{\nu}$ with a weight $\lambda>0$.

This backdoor is undetectable (though the advantage is $o(1)$, it is not negligible in the cryptographic sense) when parameters are chosen appropriately because weights sampled from a standard Gaussian distribution would be computationally indistinguishable from weights sampled from a distribution hiding a sparse spike, which [Brennan and Bresler \[4\]](#bib.bib1) show follows from the conjectured hardness of detecting planted cliques in certain graphs.

For clean inputs, the projection onto the secret direction $\nu$ resembles random noise, leaving the backdoor dormant. Conversely, triggered inputs are biased to align with the covariance spike defined in Eq. (1). This alignment shifts the activation space representation sufficiently to _hopefully_ cross the decision boundary, causing an incorrect classification to the class intended by the attacker. The effect of the secret key is illustrated in Fig. 1, and the spiked covariance is visualised in App. [[#^appendix-a-visualisation-of|A]].

Figure 1: PCA visualisation of the activation space of a backdoored single-hidden-layer ReLU network. The coloured regions represent projected class samples; blue points show randomly selected class 0 samples and red points their triggered counterparts. The displacement from clean to triggered inputs aligns with the secret key direction, illustrated by the arrow.

### 3.2 Undetectable backdoors in state-of-the-art image classification networks ^3-2-undetectable-backdoors

As stated by [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3), no effort was made to optimise the construction outlined in Sec. [[#^3-1-undetectable-backdoors|3.1]], nor has it been in subsequent peer-reviewed work. Consequently, its practical utility remains unverified. The reliance on a simplified architecture and a learning framework constrained by the tuning of a single threshold parameter $\tau$ imposes significant limitations on the neural network’s ability to generalise. Building on the theoretical framework established by [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3), we demonstrate that backdoors motivated by the same design principles can be successfully planted in state-of-the-art deep neural networks for computer vision, trained using backpropagation to solve classification tasks on commonly adopted datasets.

Let $f:\mathbb{R}^{h\times w\times c}\rightarrow\mathbb{R}^{k}$ define a neural network mapping an input image $\mathbf{x}\in\mathbb{R}^{h\times w\times c}$ to an output space of $k$ classes. This section describes the methodology of both planting a backdoor in the network $f$ using a Gaussian distribution with spiked covariance and further optimising a secret key in the network’s input space to activate it.

#### Gaussian distribution with spiked covariance ^gaussian-distribution-with-spiked

We augment the classification head with an additional linear layer immediately preceding the output, denoted by $f^{(\ell_{\text{bd}})}:\mathbb{R}^{d}\rightarrow\mathbb{R}^{m}$, prior to training. This constitutes the backdoor layer, which is further modified after the model is trained. Its parameters are subsequently absorbed into the output layer, preserving the original model architecture. [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) plant the backdoor by replacing untrained weights with weights sampled from a Gaussian distribution with spiked covariance. In our case, simply replacing the weights in layer $\ell_{\text{bd}}$ of a trained model would break the learned coupling between the backbone and the classification head. Instead, we modify the spiked covariance distribution to incorporate the scalar variance $\sigma^{2}\in\mathbb{R}$ of the learned weights in layer $\ell_{\text{bd}}$, denoted $W^{(\ell_{\text{bd}})}\in\mathbb{R}^{m\times d}$.

If the weights were independent with a zero-mean Gaussian distribution with variance $\sigma^{2}$, we could insert a spike boosted by a parameter $\theta$ along a chosen backdoor direction with a simple linear transformation. If our goal is a covariance matrix similar to that in Eq. (1), i.e.,

$$
\Sigma=\sigma^{2}I_{m}+\theta\mathbf{\nu}_{\text{bd}}\mathbf{\nu}_{\text{bd}}^{T},
$$

where $\mathbf{\nu}_{\text{bd}}\in\mathbb{R}^{m}$ is a $m^{\alpha}$\-sparse vector of unit norm $||\mathbf{\nu}_{\text{bd}}||_{2}=1$, we know that $\Sigma$ is positive-definite, meaning the Cholesky decomposition can be used to find a lower-triangular matrix $L$ such that $LL^{T}=\Sigma$. Sampling weights from $\mathcal{N}(\mathbf{0},\sigma^{2}I_{m})$ and multiplying by $L/\sigma$ would then be statistically identical to sampling weights from $\mathcal{N}(\mathbf{0},\sigma^{2}I_{m}+\theta\mathbf{\nu}_{\text{bd}}\mathbf{\nu}_{\text{bd}}^{T})$, as shown in App. [[#^appendix-b-spiked-covariance|B]]. The basic idea is to first reset the weights to unit variance and then use the $L$ matrix, which essentially contains the geometric instructions to insert the desired spike.

In a trained network, the weights $W^{(\ell_{\text{bd}})}$ will not be independent, so the corresponding covariance matrix will not be diagonal and the above argument does not precisely work. However, it is reasonable to assume that it is sufficiently close to diagonal that the linear transformation will actually succeed in planting a spike, without otherwise changing the network structure too much. We validate this expectation in Sec. [[#^5-results-and-analysis|5]], and a discussion on the empirical structure of the weight covariance is provided in App. [[#^appendix-c-empirical-structure|C]].

To summarise, we insert the backdoor by replacing the weights in layer $\ell_{\text{bd}}$ by

$$
\hat{W}^{(\ell_{\text{bd}})}=\frac{L}{\sigma}W^{(\ell_{\text{bd}})}\text{.}
$$

To restore the original architecture, we absorb the added backdoor layer into the output layer. This is possible if layer $\ell_{\text{bd}}$ uses a linear activation function at the backdoor injection stage, although a non-linear activation function may be used during clean training. The composition of the backdoor and output layers is therefore equivalent to a single affine transformation,

$$
\hat{\mathbf{z}}=W_{\mathrm{bd}}\mathbf{z}+\mathbf{b}_{\mathrm{bd}},\qquad\mathbf{y}=W_{\mathrm{out}}\hat{\mathbf{z}}+\mathbf{b}_{\mathrm{out}},
$$

which yields

$$
\mathbf{y}=W_{\text{out}}W_{\text{bd}}\mathbf{z}+W_{\text{out}}\mathbf{b}_{\text{bd}}+\mathbf{b}_{\text{out}}.
$$

Hence, the backdoor layer can be removed by updating the output layer parameters as

$$
\hat{W}_{\text{out}}=W_{\text{out}}W_{\text{bd}},\qquad\hat{\mathbf{b}}_{\text{out}}=W_{\text{out}}\mathbf{b}_{\text{bd}}+\mathbf{b}_{\text{out}}.
$$

The resulting backdoored neural network, denoted by $\hat{f}$, thus behaves identically to the model containing the explicit backdoor layer and is – except for the weights in the output layer – identical to its clean counterpart $f$.

#### Secret keys ^secret-keys

The vector $\mathbf{\nu}_{\text{bd}}$ in Eq. (2) is referred to as the _secret key_ defined in the activation space of the backdoor layer $\ell_{\text{bd}}$. The primary objective of the backdoor is to enable targeted misclassification, redirecting inputs from a _source_ class, denoted $\mathbf{x}_{\text{source}}$, to a specified _target_ class, only when the trigger is present. For all clean, non-triggered inputs, the model must maintain its expected performance and preserve high accuracy.

While [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) plant the covariance spike along a _random_ high-dimensional direction, we strategically select a direction bridging the source and target class manifolds, effectively pushing triggered input representations across the decision boundary. The direction is obtained by training a logistic regression classifier to discriminate between the activation sets $\{f^{(\ell_{\text{bd}})}(\mathbf{x}_{\text{source}}):\mathbf{x}_{\text{source}}\in\mathcal{D}_{\text{source}}\}$ and $\{f^{(\ell_{\text{bd}})}(\mathbf{x}_{\text{target}}):\mathbf{x}_{\text{target}}\in\mathcal{D}_{\text{target}}\}$, where $\mathcal{D}_{\text{source}}$ and $\mathcal{D}_{\text{target}}$ are equally sized sets of inputs from each respective class. The normal vector to the resulting linear hyperplane defines the direction from the manifold of the source class to that of the target class, serving as the basis from which the secret key $\mathbf{\nu}_{\text{bd}}$ is constructed. This normal vector is similar to the CAV introduced by [Kim et al. \[19\]](#bib.bib11), which represents a high-level concept within a model’s latent space and is defined by the direction orthogonal to a concept-separating boundary. To satisfy the sparsity requirement in Eq. (2) while preserving the original direction, only the top $\alpha$% of entries with the largest magnitudes are retained, setting all others to zero. The resulting vector is normalised to unit norm.

Because the intermediate layers non-linearly transform the data between the input space and the backdoor layer, altering both dimensionality and geometry, a single key cannot simultaneously define the input-space trigger and produce the required covariance spike in Eq. (2). We therefore introduce two distinct keys: the aforementioned $\mathbf{\nu}_{\text{bd}}\in\mathbb{R}^{m}$ defined in the space of $\ell_{\text{bd}}$, and another key $\mathbf{\nu}_{\text{in}}\in\mathbb{R}^{h\times w\times c}$ in the input space. The former equals a sparse version of the normal vector to the logistic regression decision boundary, while $\mathbf{\nu}_{\text{in}}$ is obtained through an optimisation procedure similar to the Concept Backpropagation method introduced by [Hammersborg and Strümke \[14\]](#bib.bib12). Following [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3), the input is triggered via a weighted key, i.e., $\hat{\mathbf{x}}=\mathbf{x}+\lambda\mathbf{\nu}_{\text{in}}$. Specifically, $\mathbf{\nu}_{\text{in}}$ is optimised to be the input perturbation needed for a triggered representation in the activation space of layer $\ell_{\text{bd}}$ to maximally align with the planted covariance spike. Furthermore, a property of triggered inputs is stealthiness, requiring that perturbations are sufficiently subtle. The optimisation objective includes L2 regularisation with a corresponding tunable weight $\lambda_{\text{L2}}$, while also constraining pixel values to a specified range. Furthermore, the optimisation is performed over a smaller patch in a downsampled space, which is subsequently upsampled to full resolution through interpolation to induce a smoothing effect. The full optimisation algorithm is detailed in App. [[#^appendix-d-optimisation-algorithm|D]].

#### Theoretical justification and guarantees ^theoretical-justification-and-guarantees

We use the term “cryptographic undetectability” to denote how we formally measure the difficulty of detecting the proposed weight modification under the considered threat model. While our construction is conceptually motivated by that of [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3), their formal cryptographic guarantees of provable white-box undetectability do not trivially extend to our implementation. Specifically, [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) assume that the base weights to be exploited follow $\mathcal{N}(\mathbf{0},I_{d})$ with the backdoor planted by sampling from a spiked covariance distribution $\mathcal{N}(\mathbf{0},I_{d}+\theta\mathbf{\nu}\mathbf{\nu}^{T})$ using a strictly _random_ key $\mathbf{\nu}$. Under these assumptions, undetectability is reduced to the hardness of a classical single-sample hypothesis test, i.e., determining the distribution from which the weights are sampled; either from $\mathcal{N}(\mathbf{0},I_{d})$ (null hypothesis $\mathcal{H}_{0}$) or from $\mathcal{N}(\mathbf{0},I_{d}+\theta\mathbf{\nu}\mathbf{\nu}^{T})$ (alternative hypothesis $\mathcal{H}_{1}$). Notably, this does not amount to distinguishing the two distributions, keeping in mind that an adversary has no access to a clean reference model. In essence, [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) prove through the hardness of sparse PCA that it is not possible to reject either hypothesis \[[2](#bib.bib2), [3](#bib.bib26)\].

In real-world neural networks, weight distributions are shaped by the optimisation landscape of the training objective to follow an unknown distribution $\mu(\mathbf{0},S)$, with our backdoor planted by sampling from $\mu(\mathbf{0},S^{\prime}+\theta\mathbf{\nu}_{\text{bd}}\mathbf{\nu}_{\text{bd}}^{T})$, where $S^{\prime}$ denotes the combination of the learned weight covariance and the diagonal component $\sigma^{2}I_{m}$ from the spiked covariance in Eq. (2). Furthermore, a strong adversary with the objective of detecting the backdoor is assumed to have knowledge of the scaling factor $\theta$ and can estimate $\mathbf{\nu}_{\text{bd}}$, which is not random but a sparse version of the normal vector to a linear decision boundary of the clean model’s activation space.[^note-1] Consequently, the formal proofs used by [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3), cannot be directly applied to provide the same theoretical guarantees for our construction. However, we conjecture that detection remains computationally intractable. We formulate the adverary’s objective as a similar hypothesis test for where $\mathcal{H}_{0}$ defines that $\hat{W}^{(\ell_{\text{bd}})}$ is sampled from $\mu(\mathbf{0},S)$ (the clean model distribution) and $\mathcal{H}_{1}$ assumes that the weights are sampled from $\mu(\mathbf{0},S^{\prime}+\theta\mathbf{\nu}_{\text{bd}}\mathbf{\nu}_{\text{bd}}^{T})$ (the backdoored model distribution). Given a single sample of weights $\hat{W}^{(\ell_{\text{bd}})}$ and knowledge of $(\theta,\mathbf{\nu}_{\text{bd}})$, we conjecture the existence of hyperparameter regimes for which no practical test can falsify the null hypothesis with a useful success probability. Furthermore, to the best of our knowledge, no other simpler statistical test is sufficient to prove the existence of the backdoor.[^note-2]

This detection task is practically hard because the dimensionality of the weight space in modern neural networks provides a massive hiding surface for a single spike. Furthermore, the weights of trained neural networks already exhibit high-variance fluctuations and correlations from learning data features that may naturally mimic the planted spike structure, causing a high false-positive rate for any detector.

The Marchenko–Pastur law (see App. [[#^appendix-e-the-marchenko-pastur|E]] for details) can guide the choice of the backdoor layer’s dimensionality: It characterises the eigenvalues of large sample covariance matrices of _random_ values in $\mathbb{R}^{m\times d}$, showing that pure noise causes the observed eigenvalues to spread over an interval determined by the ratio $\frac{m}{d}$ even when the true covariance matrix is the identity. In neural network weight matrices, while $m\gg d$ maximises the interval width – suppressing the visibility of a spike – the matrix becomes rank-deficient. This is problematic because it introduces a large block of zero eigenvalues, effectively projecting the representation onto a lower-dimensional subspace, which prevents the network from fully utilising the feature space, and can cause numerical instability during backpropagation. We suggest $m\approx d$ to be a practical design choice, balancing hiding planted structure without sacrificing the network’s functionality. Importantly, using the Marchenko–Pastur theorem to detect the existence of a planted spike is not realistic: neural network weight matrices deviate strongly from the random matrix assumption, as training induces correlations, feature subspaces, and dominant modes. An eigenvalue exceeding the theoretical Marchenko-Pastur bound could equally well reflect a learned feature rather than a planted spike. Further, any detection method or statistical analysis that requires comparison or access to a clean model would conflict with the underlying MLaaS assumption and is therefore outside the current scope.

## 4 Experiment design and evaluations ^4-experiment-design-and

### 4.1 Datasets and experimental design ^4-1-datasets-and

Our method is evaluated on ResNet18 \[[16](#bib.bib14)\] and Vision Transformer (ViT) \[[8](#bib.bib13)\] for multi-class classification using publicly available datasets CIFAR-10 \[[21](#bib.bib16)\] (10 distinct object categories), and the following from MedMNIST \[[32](#bib.bib15)\]: BloodMNIST (8 classes of blood cell types), DermaMNIST (7 classes of pigmented skin lesion types), and PathMNIST (9 classes of tissue types). A ReLU-activated linear layer $W^{(\ell_{\text{bd}})}\in\mathbb{R}^{m\times d}$ is inserted before the output layer, with $d=m=512$ (ResNet18) or $d=m=768$ (ViT). Using other activation functions should not introduce further complications beyond hyperparameter tuning. The models are initialised with ImageNet pre-trained weights, and fine-tuned separately on each dataset for five epochs using the Adam optimiser \[[20](#bib.bib17)\] with a learning rate of $1\times 10^{-4}$ and cross-entropy loss.

Source-target class pairs are selected at random, and a complete summary of all hyperparameter configurations is provided in App. [[#^appendix-f-hyperparameter-configurations|F]]. The input trigger optimisation procedure, which yields the key $\mathbf{\nu}_{\text{in}}$, is constrained to at most $500$ samples from the source class. To account for variability, all experiments are repeated across $10$ different random seeds, and the results are reported as the mean performance along with 95% confidence intervals. The computational resources used for experiments are stated in App. [[#^appendix-g-experiments-compute|G]].

### 4.2 Evaluation metrics and backdoor defences ^4-2-evaluation-metrics

A successful backdoored model must satisfy two main requirements: ensure minimal impact on clean performance, and reliable misclassification of triggered inputs to a predefined target class. These are quantified by the metrics _attack success rate_ (ASR) – the fraction of triggered inputs misclassified into the target class – and _clean data accuracy_ (CDA) – the proportion of unmodified test samples correctly classified. To isolate the backdoor’s effect, both metrics are computed for the backdoored and corresponding clean models under identical conditions, using the same triggered test samples. Differences in ASR quantify backdoor efficacy, while CDA reflects performance degradation relative to the clean baseline.

Robustness is assessed against a range of post-training defences following [Hong et al. \[17\]](#bib.bib22): pruning, fine-tuning, fine-pruning \[[23](#bib.bib8)\], parameter clipping, parameter noise injection, and the detection methods Neural Cleanse \[[31](#bib.bib10)\] and SmoothInv \[[30](#bib.bib32)\].

Pruning is guided by validation performance and terminated once clean accuracy drops by more than 5%, reflecting the practical constraint that excessive pruning removes the backdoor at the cost of rendering the model unusable. Fine-tuning attempts to overwrite backdoor perturbations by continued training and trivially succeeds given sufficient epochs, since this converges to retraining \[[17](#bib.bib22)\]. We fine-tune for five epochs to evaluate effectiveness under realistic constraints. Fine-pruning combines pruning followed by fine-tuning. Resilience to parameter-level perturbations is also evaluated via Gaussian noise injection $\mathcal{N}(0,\sigma_{p}^{2})$, with $\sigma_{p}$ varied logarithmically from $10^{-3}$ to $5$. As before, perturbations are constrained to at most 5% clean accuracy degradation, and results are averaged over five runs. Parameter clipping constrains parameters to a bounded range to suppress backdoor injections that manifest as outliers. We sweep the threshold $\beta\in[0.1,1.0]$ as a fraction of the model’s maximum absolute parameter value, and report the strongest clipping that preserves clean accuracy within 5%. Neural Cleanse is run with its original default configuration; detection is counted as successful if the backdoored label is identified as the target class in at least half of the seeds. SmoothInv is likewise evaluated using its default configuration, see App. [[#^appendix-k-performance-of|K]] for details.

## 5 Results and analysis ^5-results-and-analysis

ASR and CDA results are reported in Tab. 1. Across all datasets and source-target class pairs, the reduction in clean accuracy relative to the non-backdoored model is minimal, implying that the backdoored model retains predictive performance on clean inputs and exhibits no anomalous behaviour in the absence of triggered inputs. Concurrently, it achieves consistently high ASR, i.e., the backdoor reliably redirects inputs from the source to the target class. In all cases, triggered accuracy exceeds that of the clean model under identical conditions, confirming the injected mechanism is effective and consistent with theory. Triggered inputs also induce targeted misclassification in the clean model, only slightly less reliably, demonstrating the expected vulnerability to adversarial examples associated with only probing access without modification of model parameters. Results for the evaluated defences are presented in Tab. 2 and Fig. 2, with further results in App. [[#^appendix-i-performance-comparison|I]], [[#^appendix-j-performance-of|J]] and [[#^appendix-k-performance-of|K]], including comparisons with clean inputs. The backdoor retains a high attack success rate across all evaluated defence and detection strategies, suggesting that the persistence guarantees of [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3) extend at least approximately beyond their idealised setting to ours. This robustness is expected, as planting the backdoor along a direction critical to the model should make it substantially harder to remove.

The decoupling of the covariance spike from the input trigger provides additional flexibility. Importantly, any undetectability properties apply to the planted covariance spike, not the input trigger resulting from the subsequent optimisation. Trigger visibility is governed by hyperparameters, e.g. spike strength $\theta$, regularisation weight $\lambda_{\text{L2}}$, and the allowed pixel range in Alg. 1 (App. [[#^appendix-d-optimisation-algorithm|D]]) – and can be traded against ASR or tuned to prioritise robustness against defences and detection. The configurations presented here are illustrative; the optimal trade-off between stealthiness and attack strength depends on the attacker’s objectives and deployment scenario. Appendix [[#^appendix-l-visual-stealthiness|L]] illustrates the input trigger and quantifies its visual imperceptibility via the Maximum Mean Discrepancy score \[[12](#bib.bib7)\]. Further, App. [[#^appendix-m-hyperparameter-sweeps|M]] provides sensitivity analyses of both the relationship between spike strength $\theta$, ASR and clean accuracy, and of the stealthiness, as measured through $\lambda_{\text{L2}}$, in relation to ASR.

Table 1: Performance comparison between clean and backdoored ResNet18 and ViT models across four datasets. _Overall_ denotes performance on clean inputs from all classes, while _triggered_ indicates the ASR on triggered source-target class pairs. Uncertainty is reported as lower and upper bounds of the 95% confidence interval, with all values rounded to two decimal places. All hyperparameter configurations are provided in App. [[#^appendix-f-hyperparameter-configurations|F]], with full class names corresponding to the abbreviations listed in App. [[#^appendix-h-class-label|H]].

| **Model** | **Dataset** | **Source $\rightarrow$ Target** | **Triggered Clean** | **Triggered Backdoor** | **Overall Clean** | **Overall Backdoor** |
| --- | --- | --- | --- | --- | --- | --- |
| **ResNet18** | BloodMNIST | Baso $\rightarrow$ Eos | 0.19 $\pm$ 0.02 | 0.96 $\pm$ 0.01 | 0.98 | 0.98 $\pm$ 0.00 |
|  | BloodMNIST | EryBl $\rightarrow$ Baso | 0.49 $\pm$ 0.06 | 0.90 $\pm$ 0.02 | 0.98 | 0.97 $\pm$ 0.00 |
|  | CIFAR-10 | Deer $\rightarrow$ Horse | 0.64 $\pm$ 0.04 | 0.90 $\pm$ 0.01 | 0.94 | 0.89 $\pm$ 0.00 |
|  | CIFAR-10 | Ship $\rightarrow$ Truck | 0.33 $\pm$ 0.02 | 0.93 $\pm$ 0.01 | 0.94 | 0.91 $\pm$ 0.00 |
|  | DermaMNIST | NV $\rightarrow$ Vasc | 0.89 $\pm$ 0.01 | 0.95 $\pm$ 0.01 | 0.77 | 0.71 $\pm$ 0.01 |
|  | DermaMNIST | Mel $\rightarrow$ DF | 0.57 $\pm$ 0.02 | 0.98 $\pm$ 0.00 | 0.77 | 0.73 $\pm$ 0.00 |
|  | PathMNIST | BG $\rightarrow$ Deb | 0.53 $\pm$ 0.30 | 0.85 $\pm$ 0.10 | 0.93 | 0.84 $\pm$ 0.02 |
|  | PathMNIST | LymP $\rightarrow$ Deb | 0.27 $\pm$ 0.03 | 0.88 $\pm$ 0.03 | 0.93 | 0.87 $\pm$ 0.00 |
| **ViT** | BloodMNIST | Baso $\rightarrow$ Eos | 0.00 $\pm$ 0.00 | 0.89 $\pm$ 0.01 | 0.99 | 0.99 $\pm$ 0.00 |
|  | BloodMNIST | LymB $\rightarrow$ Mono | 0.25 $\pm$ 0.05 | 0.98 $\pm$ 0.01 | 0.99 | 0.99 $\pm$ 0.00 |
|  | CIFAR-10 | Auto $\rightarrow$ Truck | 0.91 $\pm$ 0.06 | 0.95 $\pm$ 0.04 | 0.95 | 0.94 $\pm$ 0.00 |
|  | CIFAR-10 | Truck $\rightarrow$ Auto | 0.80 $\pm$ 0.03 | 0.90 $\pm$ 0.06 | 0.95 | 0.94 $\pm$ 0.00 |
|  | DermaMNIST | BCC $\rightarrow$ Mel | 0.88 $\pm$ 0.04 | 0.99 $\pm$ 0.00 | 0.75 | 0.76 $\pm$ 0.01 |
|  | DermaMNIST | Mel $\rightarrow$ DF | 0.52 $\pm$ 0.03 | 0.97 $\pm$ 0.01 | 0.75 | 0.76 $\pm$ 0.00 |
|  | PathMNIST | Adip $\rightarrow$ BG | 0.96 $\pm$ 0.01 | 1.00 | 0.94 | 0.94 $\pm$ 0.00 |
|  | PathMNIST | LymP $\rightarrow$ Deb | 0.28 $\pm$ 0.01 | 0.87 $\pm$ 0.01 | 0.94 | 0.91 $\pm$ 0.00 |

Table 2: ASR on triggered source-target class pairs after defence methods pruning, parameter clipping and parameter noise injection for backdoored ResNet18 and ViT across four datasets. Uncertainty is reported as lower and upper bounds of the 95% confidence interval, with all values rounded to two decimal places. For Neural Cleanse (NC), we indicate whether the backdoor was detected (✓) or not (✗). All hyperparameter configurations are provided in App. [[#^appendix-f-hyperparameter-configurations|F]], with full class names corresponding to the abbreviations listed in App. [[#^appendix-h-class-label|H]].

| **Model** | **Dataset** | **Source $\rightarrow$ Target** | **Pruning** | **Parameter clipping** | **Parameter noise** | **NC** |
| --- | --- | --- | --- | --- | --- | --- |
| **ResNet18** | BloodMNIST | Baso $\rightarrow$ Eos | 1.00 $\pm$ 0.00 | 0.73 $\pm$ 0.05 | 0.89 $\pm$ 0.05 | ✗ |
|  | BloodMNIST | EryBl $\rightarrow$ Baso | 0.66 $\pm$ 0.08 | 0.54 $\pm$ 0.06 | 0.55 $\pm$ 0.11 | ✗ |
|  | CIFAR-10 | Deer $\rightarrow$ Horse | 0.90 $\pm$ 0.01 | 0.89 $\pm$ 0.01 | 0.86 $\pm$ 0.03 | ✗ |
|  | CIFAR-10 | Ship $\rightarrow$ Truck | 0.93 $\pm$ 0.02 | 0.92 $\pm$ 0.02 | 0.85 $\pm$ 0.02 | ✗ |
|  | DermaMNIST | NV $\rightarrow$ Vasc | 0.94 $\pm$ 0.02 | 0.94 $\pm$ 0.02 | 0.94 $\pm$ 0.02 | ✗ |
|  | DermaMNIST | Mel $\rightarrow$ DF | 0.94 $\pm$ 0.01 | 0.97 $\pm$ 0.01 | 0.96 $\pm$ 0.01 | ✗ |
|  | PathMNIST | BG $\rightarrow$ Deb | 0.74 $\pm$ 0.12 | 0.75 $\pm$ 0.11 | 0.79 $\pm$ 0.12 | ✗ |
|  | PathMNIST | LymP $\rightarrow$ Deb | 0.99 $\pm$ 0.01 | 0.35 $\pm$ 0.04 | 0.68 $\pm$ 0.08 | ✗ |
| **ViT** | BloodMNIST | Baso $\rightarrow$ Eos | 0.75 $\pm$ 0.02 | 0.92 $\pm$ 0.00 | 0.93 $\pm$ 0.02 | ✗ |
|  | BloodMNIST | LymB $\rightarrow$ Mono | 0.44 $\pm$ 0.12 | 0.78 $\pm$ 0.07 | 0.71 $\pm$ 0.08 | ✗ |
|  | CIFAR-10 | Auto $\rightarrow$ Truck | 0.95 $\pm$ 0.06 | 0.95 $\pm$ 0.05 | 0.93 $\pm$ 0.03 | ✗ |
|  | CIFAR-10 | Truck $\rightarrow$ Auto | 0.89 $\pm$ 0.08 | 0.83 $\pm$ 0.08 | 0.84 $\pm$ 0.07 | ✗ |
|  | DermaMNIST | BCC $\rightarrow$ Mel | 0.99 $\pm$ 0.00 | 0.81 $\pm$ 0.14 | 0.74 $\pm$ 0.11 | ✗ |
|  | DermaMNIST | Mel $\rightarrow$ DF | 0.99 $\pm$ 0.00 | 0.84 $\pm$ 0.07 | 0.88 $\pm$ 0.03 | ✗ |
|  | PathMNIST | Adip $\rightarrow$ BG | 1.00 | 1.00 $\pm$ 0.00 | 1.00 | ✗ |
|  | PathMNIST | LymP $\rightarrow$ Deb | 0.96 $\pm$ 0.00 | 0.87 $\pm$ 0.01 | 0.79 $\pm$ 0.03 | ✗ |

Figure 2: Accuracy over five epochs of (blue) fine-tuning and (green) fine-pruning defences for backdoored ResNet18 on BloodMNIST with source class _basophil_ and target class _eosinophil_. Results are reported for both clean inputs from all classes and triggered inputs from the source class. Shaded uncertainty bands represent the bounds of the 95% confidence interval.

## 6 Discussion and conclusion ^6-discussion-and-conclusion

This work demonstrates an extension of the method introduced by [Goldwasser et al. \[10\]](#bib.bib4), [Goldwasser et al. \[11\]](#bib.bib3), providing a formal guarantee of cryptographic undetectability for backdoors planted via spiked covariance, from simplified neural networks to modern transformer and convolutional architectures. Given the generality of our approach and the universal presence of CAVs in neural representations, no theoretical restrictions prevent extension to other architectures. As part of our analysis, we provide theoretical justification for the impracticability of distinguishing a backdoored model from a clean version, given the computational hardness of the hypothesis test discussed in Sec. [[#^3-2-undetectable-backdoors|3.2]]. Future work should aim to derive a formal proof to establish cryptographic undetectability. Such a proof would likely require an analytical characterisation of trained neural network weight distributions, which remains an open problem. The practical utility of such a theoretical result is arguably limited, given that parameter-space defences are ineffective against our backdoor in experiments. Indeed, prior work typically establishes undetectability through empirical evaluation against such defences alone; our analysis meets this standard and additionally provides a formal proof in the idealised setting.

A key aspect of our approach is that any undetectability is baked into the weights themselves; the input trigger is secondary, derived via optimisation once the backdoor is planted. This decoupling allows users to tune visual imperceptibility according to their specific requirements without compromising the undetectability of the backdooring mechanism itself. Depending on the data domain, further refinement of the optimisation process can yield more sophisticated, human-imperceptible triggers.

#### Limitations ^limitations

Our work lacks a proof of full white-box undetectability. While we provide theoretical justification and empirical evidence, we cannot conclude with theoretical guarantees. Moreover, the difficulty of the proposed hypothesis test depends on the hyperparameter value $\theta$. At present, we lack a well-defined range for selecting this parameter, beyond the general intuition that $\theta$ should be small to render the test harder to falsify. The same challenge applies to the dimensions $d$ and $m$. Additionally, although the experiments are limited to the domain of computer vision, the approach is extendable to other domains such as natural language processing.

## References ^references

-   \[1\] B. H. Abbasi, Y. Zhang, L. Zhang, and S. Gao (2025) Backdoor attacks and defenses in computer vision domain: a survey. arXiv preprint arXiv:2509.07504. Cited by: [§1](#S1.p2.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p1.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p6.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[2\] Q. Berthet and P. Rigollet (2013) Complexity theoretic lower bounds for sparse principal component detection. In COLT 2013 - The 26th Annual Conference on Learning Theory, June 12-14, 2013, Princeton University, NJ, USA, S. Shalev-Shwartz and I. Steinwart (Eds.), JMLR Workshop and Conference Proceedings, pp. 1046–1066. External Links: [Link](http://proceedings.mlr.press/v30/Berthet13.html) Cited by: [§3.2](#S3.SS2.SSS0.Px3.p1.1 "Theoretical justification and guarantees ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[3\] Q. Berthet and P. Rigollet (2013) Computational lower bounds for sparse pca. arXiv preprint arXiv:1304.0828. Cited by: [§3.2](#S3.SS2.SSS0.Px3.p1.1 "Theoretical justification and guarantees ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[4\] M. S. Brennan and G. Bresler (2019) Optimal average-case reductions to sparse PCA: from weak assumptions to strong hardness. In Conference on Learning Theory, COLT 2019, 25-28 June 2019, Phoenix, AZ, USA, A. Beygelzimer and D. Hsu (Eds.), Proceedings of Machine Learning Research, pp. 469–470. External Links: [Link](http://proceedings.mlr.press/v99/brennan19b.html) Cited by: [§3.1](#S3.SS1.p2.1 "3.1 Undetectable backdoors in single-hidden-layer random ReLU networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[5\] B. Cao, J. Jia, C. Hu, W. Guo, Z. Xiang, J. Chen, B. Li, and D. Song (2024) Data free backdoor attacks. Advances in Neural Information Processing Systems 37, pp. 23881–23911. Cited by: [§2](#S2.p5.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p6.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[6\] S. Choudhary, A. S. Patlan, N. Palumbo, A. Hooda, K. Fawaz, and S. Jha (2026) Undetectable backdoors in model parameters: hiding sparse secrets in high dimensions. arXiv preprint arXiv:2605.04209. Cited by: [§2](#S2.p3.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[7\] A. E. Cinà, K. Grosse, A. Demontis, S. Vascon, W. Zellinger, B. A. Moser, A. Oprea, B. Biggio, M. Pelillo, and F. Roli (2023) Wild patterns reloaded: a survey of machine learning security against training data poisoning. ACM Computing Surveys 55 (13s), pp. 1–39. Cited by: [§2](#S2.p1.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[8\] A. Dosovitskiy, L. Beyer, A. Kolesnikov, D. Weissenborn, X. Zhai, T. Unterthiner, M. Dehghani, M. Minderer, G. Heigold, S. Gelly, et al. (2020) An image is worth 16x16 words: transformers for image recognition at scale. arXiv preprint arXiv:2010.11929. Cited by: [§1](#S1.p4.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§4.1](#S4.SS1.p1.1 "4.1 Datasets and experimental design ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[9\] A. Draguns, A. Gritsevskiy, S. R. Motwani, and C. S. de Witt (2024) Unelicitable backdoors via cryptographic transformer circuits. In Advances in Neural Information Processing Systems, A. Globerson, L. Mackey, D. Belgrave, A. Fan, U. Paquet, J. Tomczak, and C. Zhang (Eds.), Vol. 37, pp. 53684–53709. External Links: [Document](https://dx.doi.org/10.52202/079017-1700), [Link](https://proceedings.neurips.cc/paper_files/paper/2024/file/6087a60306544be7ba0d0cf34aa93c8f-Paper-Conference.pdf) Cited by: [§2](#S2.p4.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[10\] S. Goldwasser, M. P. Kim, V. Vaikuntanathan, and O. Zamir (2022) Planting undetectable backdoors in machine learning models : \[extended abstract\]. In 2022 IEEE 63rd Annual Symposium on Foundations of Computer Science (FOCS), Vol. , pp. 931–942. External Links: [Document](https://dx.doi.org/10.1109/FOCS54457.2022.00092) Cited by: [1st item](#S1.I1.i1.p1.1 "In 1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§1](#S1.p1.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§1](#S1.p2.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§1](#S1.p3.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p2.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p3.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.1](#S3.SS1.p1.1 "3.1 Undetectable backdoors in single-hidden-layer random ReLU networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px1.p1.1 "Gaussian distribution with spiked covariance ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px2.p2.1 "Secret keys ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px2.p3.1 "Secret keys ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px3.p1.1 "Theoretical justification and guarantees ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px3.p2.1 "Theoretical justification and guarantees ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.p1.1 "3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§5](#S5.p1.1 "5 Results and analysis ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§6](#S6.p1.1 "6 Discussion and conclusion ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[11\] S. Goldwasser, M. P. Kim, V. Vaikuntanathan, and O. Zamir (2024) Planting undetectable backdoors in machine learning models. External Links: 2204.06974, [Link](https://arxiv.org/abs/2204.06974) Cited by: [1st item](#S1.I1.i1.p1.1 "In 1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§1](#S1.p2.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§1](#S1.p3.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p2.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p3.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.1](#S3.SS1.p1.1 "3.1 Undetectable backdoors in single-hidden-layer random ReLU networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px1.p1.1 "Gaussian distribution with spiked covariance ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px2.p2.1 "Secret keys ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px2.p3.1 "Secret keys ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px3.p1.1 "Theoretical justification and guarantees ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px3.p2.1 "Theoretical justification and guarantees ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.p1.1 "3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§5](#S5.p1.1 "5 Results and analysis ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§6](#S6.p1.1 "6 Discussion and conclusion ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[12\] A. Gretton, K. M. Borgwardt, M. J. Rasch, B. Schölkopf, and A. Smola (2012) A kernel two-sample test. Journal of Machine Learning Research 13 (25), pp. 723–773. External Links: [Link](http://jmlr.org/papers/v13/gretton12a.html) Cited by: [Appendix L](#A12.p1.1 "Appendix L Visual stealthiness of input trigger and the Maximum Mean Discrepancy metric ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§5](#S5.p2.1 "5 Results and analysis ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[13\] I. Grigoriadis, E. Vrochidou, I. Tsiatsiou, and G. A. Papakostas (2023) Machine learning as a service (mlaas)—an enterprise perspective. In Proceedings of International Conference on Data Science and Applications, M. Saraswat, C. Chowdhury, C. Kumar Mandal, and A. H. Gandomi (Eds.), Singapore, pp. 261–273. External Links: ISBN 978-981-19-6634-7 Cited by: [§1](#S1.p1.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[14\] P. Hammersborg and I. Strümke (2023) Concept backpropagation: an explainable ai approach for visualising learned concepts in neural network models. arXiv preprint arXiv:2307.12601. Cited by: [§3.2](#S3.SS2.SSS0.Px2.p3.1 "Secret keys ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[15\] M. A. Hanif, N. Chattopadhyay, B. Ouni, and M. Shafique (2025) Survey on backdoor attacks on deep learning: current trends, categorization, applications, research challenges, and future prospects. IEEE Access. Cited by: [§2](#S2.p6.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[16\] K. He, X. Zhang, S. Ren, and J. Sun (2016) Deep residual learning for image recognition. In Proceedings of the IEEE conference on computer vision and pattern recognition, pp. 770–778. Cited by: [§1](#S1.p4.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§4.1](#S4.SS1.p1.1 "4.1 Datasets and experimental design ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[17\] S. Hong, N. Carlini, and A. Kurakin (2022) Handcrafted backdoors in deep neural networks. Advances in Neural Information Processing Systems 35, pp. 8068–8080. Cited by: [§2](#S2.p5.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§4.2](#S4.SS2.p2.1 "4.2 Evaluation metrics and backdoor defences ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§4.2](#S4.SS2.p3.1 "4.2 Evaluation metrics and backdoor defences ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[18\] A. Kalavasis, A. Karbasi, A. Oikonomou, K. Sotiraki, G. Velegkas, and M. Zampetakis (2024) Injecting undetectable backdoors in obfuscated neural networks and language models. Advances in Neural Information Processing Systems 37, pp. 21537–21571. Cited by: [§2](#S2.p2.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p4.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[19\] B. Kim, M. Wattenberg, J. Gilmer, C. Cai, J. Wexler, F. Viegas, et al. (2018) Interpretability beyond feature attribution: quantitative testing with concept activation vectors (tcav). In International conference on machine learning, pp. 2668–2677. Cited by: [§1](#S1.p3.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§3.2](#S3.SS2.SSS0.Px2.p2.1 "Secret keys ‣ 3.2 Undetectable backdoors in state-of-the-art image classification networks ‣ 3 Theoretical background and problem formulation ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[20\] D. P. Kingma and J. Ba (2014) Adam: a method for stochastic optimization. arXiv preprint arXiv:1412.6980. Cited by: [§4.1](#S4.SS1.p1.1 "4.1 Datasets and experimental design ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[21\] A. Krizhevsky G. Hinton et al. (2009) Learning multiple layers of features from tiny images. Cited by: [§4.1](#S4.SS1.p1.1 "4.1 Datasets and experimental design ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[22\] M. Lamparth and A. Reuel (2024) Analyzing and editing inner mechanisms of backdoored language models. In Proceedings of the 2024 ACM Conference on Fairness, Accountability, and Transparency, pp. 2362–2373. Cited by: [§2](#S2.p5.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[23\] K. Liu, B. Dolan-Gavitt, and S. Garg (2018) Fine-pruning: defending against backdooring attacks on deep neural networks. In International symposium on research in attacks, intrusions, and defenses, pp. 273–294. Cited by: [5th item](#S1.I1.i5.p1.1 "In 1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p6.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§4.2](#S4.SS2.p2.1 "4.2 Evaluation metrics and backdoor defences ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[24\] C. H. Martin and M. W. Mahoney (2021) Implicit self-regularization in deep neural networks: evidence from random matrix theory and implications for learning. Journal of Machine Learning Research 22 (165), pp. 1–73. Cited by: [Appendix C](#A3.p3.1 "Appendix C Empirical structure of the weight covariance ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[25\] A. Rahimi and B. Recht (2007) Random features for large-scale kernel machines. Advances in neural information processing systems 20. Cited by: [§2](#S2.p2.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[26\] M. Ribeiro, K. Grolinger, and M. A.M. Capretz (2015) MLaaS: machine learning as a service. In 2015 IEEE 14th International Conference on Machine Learning and Applications (ICMLA), Vol. , pp. 896–902. External Links: [Document](https://dx.doi.org/10.1109/ICMLA.2015.152) Cited by: [§1](#S1.p1.1 "1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[27\] L. Sagun, L. Bottou, and Y. LeCun (2016) Eigenvalues of the hessian in deep learning: singularity and beyond. arXiv preprint arXiv:1611.07476. Cited by: [Appendix C](#A3.p2.1 "Appendix C Empirical structure of the weight covariance ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [Appendix C](#A3.p3.1 "Appendix C Empirical structure of the weight covariance ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[28\] L. Sagun, U. Evci, V. U. Guney, Y. Dauphin, and L. Bottou (2017) Empirical analysis of the hessian of over-parametrized neural networks. arXiv preprint arXiv:1706.04454. Cited by: [Appendix C](#A3.p1.1 "Appendix C Empirical structure of the weight covariance ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [Appendix C](#A3.p2.1 "Appendix C Empirical structure of the weight covariance ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [Appendix C](#A3.p3.1 "Appendix C Empirical structure of the weight covariance ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[29\] L. Sagun, U. Evci, V. U. Guney, Y. Dauphin, and L. Bottou (2018) Empirical analysis of the hessian of over-parametrized neural networks. In ICLR 2018 Workshop, External Links: [Link](https://iclr.cc/virtual/2018/workshop/563) Cited by: [Appendix C](#A3.p1.1 "Appendix C Empirical structure of the weight covariance ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [Appendix C](#A3.p2.1 "Appendix C Empirical structure of the weight covariance ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [Appendix C](#A3.p3.1 "Appendix C Empirical structure of the weight covariance ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[30\] M. Sun and Z. Kolter (2023) Single image backdoor inversion via robust smoothed classifiers. In 2023 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), pp. 8113–8122. Cited by: [Appendix K](#A11.p1.1 "Appendix K Performance of detection method SmoothInv ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [Appendix K](#A11.p2.1 "Appendix K Performance of detection method SmoothInv ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [5th item](#S1.I1.i5.p1.1 "In 1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p6.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§4.2](#S4.SS2.p2.1 "4.2 Evaluation metrics and backdoor defences ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[31\] B. Wang, Y. Yao, S. Shan, H. Li, B. Viswanath, H. Zheng, and B. Y. Zhao (2019) Neural cleanse: identifying and mitigating backdoor attacks in neural networks. In 2019 IEEE symposium on security and privacy (SP), pp. 707–723. Cited by: [5th item](#S1.I1.i5.p1.1 "In 1 Introduction ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§2](#S2.p6.1 "2 Related work ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks"), [§4.2](#S4.SS2.p2.1 "4.2 Evaluation metrics and backdoor defences ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").
-   \[32\] J. Yang, R. Shi, D. Wei, Z. Liu, L. Zhao, B. Ke, H. Pfister, and B. Ni (2023) Medmnist v2-a large-scale lightweight benchmark for 2d and 3d biomedical image classification. Scientific data 10 (1), pp. 41. Cited by: [§4.1](#S4.SS1.p1.1 "4.1 Datasets and experimental design ‣ 4 Experiment design and evaluations ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks").

## Appendix A Visualisation of spiked covariance ^appendix-a-visualisation-of

Figure 3 illustrates the difference between clean and backdoored distributions, highlighting the increased variance introduced by the spiked covariance. The clean distribution follows a standard multivariate Gaussian $\mathcal{N}(\mathbf{0},I_{d})$, while the backdoored distribution $\mathcal{N}(\mathbf{0},I_{d}+\theta\mathbf{\nu}\mathbf{\nu}^{T})$ incorporates a low-rank covariance perturbation, creating a spike along a secret direction $\mathbf{\nu}\in\mathbb{R}^{d}$. While statistically indistinguishable under certain conditions, the variance is visibly higher in the latter for a high value $\theta$. Refer to Sec. [[#^3-1-undetectable-backdoors|3.1]] for further details.

(a)

(b)

Figure 3: (a) The clean distribution follows a standard multivariate Gaussian, which is modified with a spiked covariance to obtain (b) the backdoored distribution. Both are shown as 2D contour lines using a shared colour scale.

## Appendix B Spiked covariance distribution ^appendix-b-spiked-covariance

The following shows that the weight transformation from $W^{(\ell_{\text{bd}})}$ to $\hat{W}^{(\ell_{\text{bd}})}$, both defined in Sec.[[#^3-2-undetectable-backdoors|3.2]], would be statistically identical to sampling new weights from a distribution $\mathbf{g}_{i}\sim\mathcal{N}(\mathbf{0},\sigma^{2}I_{m}+\theta\mathbf{\nu}_{\text{bd}}\mathbf{\nu}_{\text{bd}}^{T})$, under the assumption that $W^{(\ell_{\text{bd}})}$ was Gaussian.

Assume each column of the weight matrix $W^{(\ell_{\text{bd}})}$, denoted $\mathbf{w}\in\mathbb{R}^{m}$, are sampled from a distribution $\mathbf{w}\sim\mathcal{N}(\mathbf{0},\sigma^{2}I_{m})$, which gives covariance $\text{Cov}(\mathbf{w})=\mathbb{E}[\mathbf{w}\mathbf{w}^{T}]=\sigma^{2}I_{m}$.[^note-3] The covariance of these weights scaled by the standard deviation $\sigma$ is,

$$
\text{Cov}\left(\frac{\mathbf{w}}{\sigma}\right)=\left(\frac{1}{\sigma}\right)(\sigma^{2}I_{m})\left(\frac{1}{\sigma}\right)^{T}=\frac{\sigma^{2}}{\sigma^{2}}I_{m}=I_{m}.
$$

The identity covariance makes the scaled weights mathematically indistinguishable from a sample of the standard Gaussian, as its mean is assumed to be zero.

The covariance of the backdoored weights $\hat{W}^{(\ell_{\text{bd}})}$ when applying the Cholesky factor $L$ as in Sec. [[#^3-2-undetectable-backdoors|3.2]] is, when using the result from Eq. ([7](#A2.E7 "In Appendix B Spiked covariance distribution ‣ Backdoor Channels Hidden in Latent Space:Extending Cryptographic Undetectability to Modern Neural Networks")),

$$
\begin{aligned}
\mathrm{Cov}(\hat{\mathbf{w}})
&=\mathrm{Cov}\!\left(L\frac{\mathbf{w}}{\sigma}\right)=L\,\mathrm{Cov}\!\left(\frac{\mathbf{w}}{\sigma}\right)L^{T} \\
&=LI_{m}L^{T}=LL^{T}=\Sigma,
\end{aligned}
$$

where $\Sigma$ is defined in Eq. (2).

As discussed in Sec. [[#^3-2-undetectable-backdoors|3.2]], the weights do not strictly follow a Gaussian distribution, but the above argument motivates our approach.

## Appendix C Empirical structure of the weight covariance ^appendix-c-empirical-structure

In conflict with our simplified assumption, the covariance of the model weights is not diagonal; model training induces correlations and the weights are tied together via the loss landscape. Still, when viewed through the spectrum of the Hessian (the second derivatives of the loss with respect to the weights), the bulk behaves as if the covariance were essentially isotropic and degenerate, with a small number of outliers carrying the structured signal. This was shown empirically by [Sagun et al. \[28\]](#bib.bib28), [Sagun et al. \[29\]](#bib.bib30), who decomposed the Hessian via the Generalised Gauss-Newton form into a covariance-of-gradients term plus a residual.

Concretely, both at initialisation and at the end of training, almost all Hessian eigenvalues sit in a narrow bulk concentrated near zero, with a handful of large positive outliers detached from it \[[27](#bib.bib27), [28](#bib.bib28), [29](#bib.bib30)\]. The two parts have different origins: the bulk is governed by the architecture, while the outliers are governed by the data. [Sagun et al. \[28\]](#bib.bib28), [Sagun et al. \[29\]](#bib.bib30) show empirically that for a $k$\-class classification problem, the number of outliers above the bulk matches $k$, which is exactly what one would expect if the dominant non-trivial directions come from the rank-$k$ structure of the gradient-of-outputs covariance in their decomposition.

Increasing layer width, on the other hand, does not create new outlier directions; it only inflates the bulk near zero \[[27](#bib.bib27), [28](#bib.bib28), [29](#bib.bib30)\]. Briefly put: most directions in overparameterised networks correspond to redundant zero modes, alongside whatever sparse structured signal the data contributes. Importantly for the present context, this low effective rank is visible directly in the weight matrices, not only the Hessian. The parallel observation was made by [Martin and Mahoney \[24\]](#bib.bib29), who find that trained weight matrices develop strongly non-random, often heavy-tailed spectra, with structure aligned to the data. They find that, over the course of training, the information in the weight matrices increasingly concentrates in a sparse spike, and that there is likely no simple low rank approximation for the weight matrices.

Despite the important off-diagonal directions, the empirical results in Sec. [[#^5-results-and-analysis|5]] demonstrate that the model’s learned behaviour is preserved when using the spiked covariance in Eq. 2 to replace weights in the backdoor layer.

## Appendix D Optimisation algorithm for input space trigger ^appendix-d-optimisation-algorithm

Algorithm 1 outlines the optimisation procedure for obtaining the input trigger using the backdoored model denoted $\hat{f}$. In particular, we define $\mathbf{z}_{\text{source}}^{(\ell_{\text{bd}})}\in\mathbb{R}^{m}$ as the activations of inputs from the source class in layer $\ell_{\text{bd}}$, and $\hat{\mathbf{z}}_{\text{source}}^{(\ell_{\text{bd}})}$ as activations from the corresponding triggered inputs. The main optimisation objective is to align the latter with the spike direction $\mathbf{\nu}_{\text{bd}}\in\mathbb{R}^{m}$.

Stealthiness requires perturbations to remain sufficiently subtle such that a triggered input $\hat{\mathbf{x}}$ is difficult to distinguish from its clean counterpart $\mathbf{x}$. Ideally, this similarity should hold for both human observers and automated anomaly detection systems. The optimisation accounts for stealthiness by including L2 regularisation to its objective, constrain pixel values, and enforce sparsity via a threshold $\tau$. The optimisation is carried out on a smaller patch $\mathbb{R}^{h_{s}\times w_{s}\times c}$, which is subsequently upsampled to induce a smoothing (blurring) effect.

**Algorithm 1** Optimise trigger perturbation for input space

```text
1:  Input: x, ν_bd, f̂, steps, lr, scale, λ_L2, ε, τ
2:  Output: ν_in
3:  (b, c, h, w) ← shape(x)
4:  h_s ← ⌊h / scale⌋
5:  w_s ← ⌊w / scale⌋
6:  δ ← 0^(1 × c × h_s × w_s)
7:  δ.requires_grad ← True
8:  Initialize optimizer ← Adam(δ, lr)
9:  ν_bd ← normalize(ν_bd)
10: dataloader ← get_dataloader(x)
11: for step = 1 to steps do
            12:                                    optimizer.zero_grad()
            13:                                    for each batch x_batch in dataloader do
            14:                                     ν_in ← interpolate(δ, (h, w))
            15:                                     ν_in′ ← clamp(ν_in, −ε, ε)
            16:                                     y ← f̂(x_batch + ν_in′)
            17:                                     h ← activation
            18:                                     alignment ← −(1 / |x_batch|) Σ (h · ν_bd)
            19:                                     L2 ← (λ_L2 / |x_batch|) Σ (ν_in′)²
            20:                                     loss ← alignment + L2
            21:                                     loss.backward()
            22:                                     activation ← ∅
            23:                                    end for
            24:                                    optimizer.step()
            25:                                    δ ← sign(δ) · max(|δ| − τ, 0)
26: end for
27: ν_in ← interpolate(δ, (h, w))
28: return squeeze(ν_in)
```

## Appendix E The Marchenko-Pastur theorem ^appendix-e-the-marchenko-pastur

The Marchenko-Pastur theorem is a fundamental result in random matrix theory that describes the eigenvalues of large sample covariance matrices. Assume a data matrix $X\in\mathbb{R}^{p\times n}$, where $p$ denotes the number of variables and $n$ the number of samples, in which entries are independent identically distributed random variables with mean $0$ and variance $\sigma^{2}$. The sample covariance matrix is expressed as

$$
S=\frac{1}{n}XX^{T}\in\mathbb{R}^{p\times p}.
$$

When the population covariance is $\sigma^{2}I$, the eigenvalues of $S$ concentrate on the interval $[\sigma^{2}(1-\sqrt{\gamma})^{2},\sigma^{2}(1+\sqrt{\gamma})^{2}]$ when $p,n\rightarrow\infty$ with $\frac{p}{n}\rightarrow\gamma\in(0,+\infty)$. This shows that even in the absence of structure, the eigenvalues spread over a non-trivial interval purely due to noise. Furthermore, this establishes a detection threshold: spikes or dominant principal directions are only distinguishable from random noise if their associated eigenvalues exceed the upper bound.

## Appendix F Hyperparameter configurations ^appendix-f-hyperparameter-configurations

This section summarises the hyperparameter configurations used in the experiments reported in Sec. [[#^5-results-and-analysis|5]]. All experiments – across both architectures and datasets – share the common settings listed in Tab. 3. A fixed scaling factor $\lambda=0.5$ is used for the input trigger in ResNet18 experiments, whereas a value of $\lambda=2$ is used for ViT. The only hyperparameter varying across source-target class pairs is the L2 regularisation coefficient $\lambda_{\text{L2}}$ in the optimisation procedure (Alg. 1). These values are reported in Tab. 4.

Table 3: Shared hyperparameter values across architectures and datasets.

|  | **Hyperparameter** | **Value** |
| --- | --- | --- |
| **Optimisiation of input trigger** | steps | 200 |
|  | scale | 4 |
|  | lr | 0.01 |
|  | $\epsilon$ | 30/255 |
|  | $\tau$ | 0.001 |
| **Sparsity** | $\alpha$ | 0.1 |
| **Strength of spiked covariance** | $\theta$ | 0.1 |

Table 4: The hyperparameter value of the L2 regularisation coefficient $\lambda_{\text{L2}}$ in Alg. 1 for all source-target class pairs across datasets. The full class names corresponding to the abbreviations are listed in App. [[#^appendix-h-class-label|H]].

| **Model** | **Dataset** | **Source $\rightarrow$ Target** | **Value** $\lambda_{\text{L2}}$ |
| --- | --- | --- | --- |
| **ResNet18** | BloodMNIST | Baso $\rightarrow$ Eos | 15 |
|  | BloodMNIST | EryBl $\rightarrow$ Baso | 6.5 |
|  | CIFAR-10 | Deer $\rightarrow$ Horse | 1.5 |
|  | CIFAR-10 | Ship $\rightarrow$ Truck | 3 |
|  | DermaMNIST | NV $\rightarrow$ Vasc | 10 |
|  | DermaMNIST | Mel $\rightarrow$ DF | 2.5 |
|  | PathMNIST | BG $\rightarrow$ Deb | 8 |
|  | PathMNIST | LymP $\rightarrow$ Deb | 4 |
| **ViT** | BloodMNIST | Baso $\rightarrow$ Eos | 16.5 |
|  | BloodMNIST | LymB $\rightarrow$ Mono | 5 |
|  | CIFAR-10 | Auto $\rightarrow$ Truck | 1 |
|  | CIFAR-10 | Truck $\rightarrow$ Auto | 1 |
|  | DermaMNIST | BCC $\rightarrow$ Mel | 5.5 |
|  | DermaMNIST | Mel $\rightarrow$ DF | 8 |
|  | PathMNIST | Adip $\rightarrow$ BG | 1 |
|  | PathMNIST | LymP $\rightarrow$ Deb | 1 |

## Appendix G Experiments compute resources ^appendix-g-experiments-compute

All computations were performed on an HPC cluster using NVIDIA V100 or A100 GPUs. Comparable hardware is not strictly required; rather, sufficient GPU memory to accommodate the model size and data is the primary requirement.

## Appendix H Class label abbreviations ^appendix-h-class-label

Table 5 provides abbreviations of class names in all evaluated datasets BloodMNIST, CIFAR-10, DermaMNIST and PathMNIST.

Table 5: Class label abbreviations

| **Full name** | **Abbreviation** |
| --- | --- |
| Basophil | Baso |
| Eosinophil | Eos |
| Erythroblast | EryBl |
| Immature granulocytes | ImmGran |
| Lymphocyte | LymB |
| Monocyte | Mono |
| Neutrophil | Neut |
| Platelet | Plt |
| Airplane | Air |
| Automobile | Auto |
| Bird | Bird |
| Cat | Cat |
| Deer | Deer |
| Dog | Dog |
| Frog | Frog |
| Horse | Horse |
| Ship | Ship |
| Truck | Truck |
| Actinic keratoses and intraepithelial carcinoma | AKIEC |
| Basal cell carcinoma | BCC |
| Benign keratosis-like lesions | BKL |
| Dermatofibroma | DF |
| Melanoma | Mel |
| Melanocytic nevi | NV |
| Vascular lesions | Vasc |
| Adipose | Adip |
| Background | BG |
| Cancer-associated stroma | CAS |
| Colorectal adenocarcinoma epithelium | CAE |
| Debris | Deb |
| Lymphocytes | LymP |
| Mucus | Muc |
| Normal colon mucosa | NCM |
| Smooth muscle | SM |

## Appendix I Performance comparison of defences on clean vs. triggered inputs ^appendix-i-performance-comparison

Table 6 compares the performance of defence methods pruning, parameter clipping and parameter noise injection on both clean and triggered inputs. Notably, the triggered results match those in Tab. 2, while this table additionally reports performance on clean inputs for comparison.

Table 6: Performance comparison of defence methods pruning, parameter clipping and parameter noise injection on clean and triggered inputs for ResNet18 and ViT across four datasets. _Clean_ denotes classification accuracy on unmodified inputs from all classes, while _triggered_ indicates the ASR on triggered source-target class pairs. Uncertainty is reported as lower and upper bounds of the 95% confidence interval, with all values rounded to two decimal places. All hyperparameter configurations are provided in App. [[#^appendix-f-hyperparameter-configurations|F]], with full class names corresponding to the abbreviations listed in App. [[#^appendix-h-class-label|H]].

| **Model** | **Dataset** | **Source $\rightarrow$ Target** | **Pruning Clean** | **Pruning Triggered** | **Parameter clipping Clean** | **Parameter clipping Triggered** | **Parameter noise Clean** | **Parameter noise Triggered** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **ResNet18** | BloodMNIST | Baso $\rightarrow$ Eos | 0.93 $\pm$ 0.00 | 1.00 $\pm$ 0.00 | 0.94 $\pm$ 0.00 | 0.73 $\pm$ 0.05 | 0.95 $\pm$ 0.00 | 0.89 $\pm$ 0.05 |
|  | BloodMNIST | EryBl $\rightarrow$ Baso | 0.92 $\pm$ 0.00 | 0.66 $\pm$ 0.08 | 0.96 $\pm$ 0.00 | 0.54 $\pm$ 0.06 | 0.94 $\pm$ 0.00 | 0.55 $\pm$ 0.11 |
|  | CIFAR-10 | Deer $\rightarrow$ Horse | 0.84 $\pm$ 0.00 | 0.90 $\pm$ 0.01 | 0.88 $\pm$ 0.00 | 0.89 $\pm$ 0.01 | 0.87 $\pm$ 0.00 | 0.86 $\pm$ 0.03 |
|  | CIFAR-10 | Ship $\rightarrow$ Truck | 0.87 $\pm$ 0.01 | 0.93 $\pm$ 0.02 | 0.90 $\pm$ 0.01 | 0.92 $\pm$ 0.02 | 0.88 $\pm$ 0.00 | 0.85 $\pm$ 0.02 |
|  | DermaMNIST | NV $\rightarrow$ Vasc | 0.65 $\pm$ 0.01 | 0.94 $\pm$ 0.02 | 0.66 $\pm$ 0.01 | 0.94 $\pm$ 0.02 | 0.67 $\pm$ 0.01 | 0.94 $\pm$ 0.02 |
|  | DermaMNIST | Mel $\rightarrow$ DF | 0.62 $\pm$ 0.01 | 0.94 $\pm$ 0.01 | 0.70 $\pm$ 0.00 | 0.97 $\pm$ 0.01 | 0.69 $\pm$ 0.01 | 0.96 $\pm$ 0.01 |
|  | PathMNIST | BG $\rightarrow$ Deb | 0.78 $\pm$ 0.02 | 0.74 $\pm$ 0.12 | 0.79 $\pm$ 0.02 | 0.75 $\pm$ 0.11 | 0.80 $\pm$ 0.01 | 0.79 $\pm$ 0.12 |
|  | PathMNIST | LymP $\rightarrow$ Deb | 0.80 $\pm$ 0.01 | 0.99 $\pm$ 0.01 | 0.84 $\pm$ 0.00 | 0.35 $\pm$ 0.04 | 0.81 $\pm$ 0.01 | 0.68 $\pm$ 0.08 |
| **ViT** | BloodMNIST | Baso $\rightarrow$ Eos | 0.96 $\pm$ 0.00 | 0.75 $\pm$ 0.02 | 0.96 $\pm$ 0.00 | 0.92 $\pm$ 0.00 | 0.95 $\pm$ 0.01 | 0.93 $\pm$ 0.02 |
|  | BloodMNIST | LymB $\rightarrow$ Mono | 0.95 $\pm$ 0.00 | 0.44 $\pm$ 0.12 | 0.98 $\pm$ 0.00 | 0.78 $\pm$ 0.07 | 0.96 $\pm$ 0.00 | 0.71 $\pm$ 0.08 |
|  | CIFAR-10 | Auto $\rightarrow$ Truck | 0.91 $\pm$ 0.00 | 0.95 $\pm$ 0.06 | 0.93 $\pm$ 0.00 | 0.95 $\pm$ 0.05 | 0.91 $\pm$ 0.00 | 0.93 $\pm$ 0.03 |
|  | CIFAR-10 | Truck $\rightarrow$ Auto | 0.91 $\pm$ 0.00 | 0.89 $\pm$ 0.08 | 0.93 $\pm$ 0.00 | 0.83 $\pm$ 0.08 | 0.91 $\pm$ 0.00 | 0.84 $\pm$ 0.07 |
|  | DermaMNIST | BCC $\rightarrow$ Mel | 0.75 $\pm$ 0.02 | 0.99 $\pm$ 0.00 | 0.72 $\pm$ 0.03 | 0.81 $\pm$ 0.14 | 0.69 $\pm$ 0.02 | 0.74 $\pm$ 0.11 |
|  | DermaMNIST | Mel $\rightarrow$ DF | 0.74 $\pm$ 0.02 | 0.99 $\pm$ 0.00 | 0.67 $\pm$ 0.03 | 0.84 $\pm$ 0.07 | 0.69 $\pm$ 0.01 | 0.88 $\pm$ 0.03 |
|  | PathMNIST | Adip $\rightarrow$ BG | 0.86 $\pm$ 0.00 | 1.00 | 0.94 $\pm$ 0.01 | 1.00 $\pm$ 0.00 | 0.90 $\pm$ 0.00 | 1.00 |
|  | PathMNIST | LymP $\rightarrow$ Deb | 0.87 $\pm$ 0.00 | 0.96 $\pm$ 0.00 | 0.90 $\pm$ 0.00 | 0.87 $\pm$ 0.01 | 0.88 $\pm$ 0.00 | 0.79 $\pm$ 0.03 |

## Appendix J Performance of fine-tuning and fine-pruning defences ^appendix-j-performance-of

Figure 4 shows results for the fine-tuning and fine-pruning defences for source-target class pairs corresponding to those reported in Sec. [[#^5-results-and-analysis|5]].

(a) EryBl-Baso

(b) Deer-Horse

(c) Ship-Truck

(d) NV-Vasc

(e) Mel-DF

(f) BG-Deb

(g) LymP-Deb

(h) Baso-Eos

(i) LymB-Mono

(j) Auto-Truck

(k) Truck-Auto

(l) BCC-Mel

(m) Mel-DF

(n) Adip-BG

(o) LymP-Deb

Figure 4: Accuracy over five epochs of (blue) fine-tuning and (green) fine-pruning defences for backdoored (a-g) ResNet18 and (h-o) ViT across four datasets. Results are reported for both clean inputs from all classes and triggered inputs from the source class. Shaded uncertainty bands represent the bounds of the 95% confidence interval. The full class names corresponding to the abbreviations are listed in App. [[#^appendix-h-class-label|H]].

## Appendix K Performance of detection method SmoothInv ^appendix-k-performance-of

The results for the detection method SmoothInv \[[30](#bib.bib32)\] are reported as the mean ASR of the optimised SmoothInv trigger over 10 random seeds, with 95% confidence intervals. Figure 5 shows the ASR profile across classes, with the black marker indicating the true target class. Successful identification should result in a clear separation between the true target and the remaining classes.

We use perturbation size $\epsilon=10$ and no diffusion, see details in [Sun and Kolter \[30\]](#bib.bib32). Notably, we only test using source-class images; however, the defender does not know that the attack is single-class or which source class is affected, and would therefore need to evaluate all source-target combinations (or the entire test set), substantially increasing the computational cost. We consider SmoothInv successful if the recovered trigger yields a high ASR for the true target class while producing substantially lower ASR for non-target classes.

The results indicate that SmoothInv does not reliably identify the true backdoored target class across configurations, producing high ASR also for non-target classes, which suggests limited specificity (high false positive rate).

(a) Baos-Eos

(b) REryBl-Baso

(c) Baso-Eos

(d) LymB-Mono

(e) Deer-Horse

(f) Ship-Truck

(g) Auto-Truck

(h) Truck-Auto

(i) NV-Vasc

(j) Mel-DF

(k) BCC-Mel

(l) Mel-DF

(m) BG-Deb

(n) LymP-Deb

(o) Adip-BG

(p) LymP-Deb

Figure 5: SmoothInv results for backdoored (a, b, c, f, i, j, m, n) ResNet18 and (c, d, g, h, k, l, o, p) ViT across four datasets. Results are reported as the average ASR per class with associated 95% confidence intervals. The full class names corresponding to the abbreviations are listed in App. [[#^appendix-h-class-label|H]].

## Appendix L Visual stealthiness of input trigger and the Maximum Mean Discrepancy metric ^appendix-l-visual-stealthiness

Figure 6 shows four examples of clean inputs alongside their triggered counterparts activating the backdoor. Figure 7 illustrates the influence of the scaling factor $\lambda$ on the perceptibility of the trigger, showing that larger values of $\lambda$ yield more visible perturbations. Stealthiness in terms of visual imperceptibility is quantified by the Maximum Mean Discrepancy (MMD) score \[[12](#bib.bib7)\] as the discrepancy between the original images and their triggered counterparts.

MMD is a statistical measure determining whether two sets of samples are drawn from the same underlying distribution by computing the distance between their mean embeddings. Both the original and corresponding triggered images are passed through a pretrained InceptionV3 network to extract high-level feature representations denoted as $\mathcal{X}=\{\mathbf{x}_{i}\}_{i=1}^{n}\subset\mathbb{R}^{p}$ (original) and $\mathcal{Y}=\{\mathbf{y}_{j}\}_{j=1}^{n}\subset\mathbb{R}^{p}$ (triggered). A polynomial kernel function $k:\mathbb{R}^{p}\times\mathbb{R}^{p}\rightarrow\mathbb{R}$ defined as $k(\mathbf{x},\mathbf{y})=(\gamma\mathbf{x}^{T}\mathbf{y}+c)^{d}$, with scaling factor $\gamma=\frac{1}{p}$, constant offset $c=1$ and polynomial degree $d=3$, computes the pairwise similarities of the feature embeddings. The biased empirical estimate of MMD is given by

$$
\begin{aligned}
\text{MMD}(\mathcal{X},\mathcal{Y})
&=\frac{1}{n^{2}}\sum_{i,j}k(\mathbf{x}_{i},\mathbf{x}_{j})+\frac{1}{m^{2}}\sum_{i,j}k(\mathbf{y}_{i},\mathbf{y}_{j}) \\
&\quad-\frac{2}{nm}\sum_{i,j}k(\mathbf{x}_{i},\mathbf{y}_{j}).
\end{aligned}
$$

where the terms measure intra-set similarity of original features, intra-set similarity of triggered features, and cross-set similarity between original and triggered features, respectively. If the two sets originate from the same distribution, the MMD value approaches zero. Thus, a lower MMD score indicates higher similarity between the original and triggered image distributions, while larger values suggest stronger distributional shifts introduced by the trigger.

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/eggen-backdoor-channels-hidden-in-latent-space-extending-cryptographic-undetectability-to-modern-neural-networks-img1-ff1d00ca.png)

(a)

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/eggen-backdoor-channels-hidden-in-latent-space-extending-cryptographic-undetectability-to-modern-neural-networks-img2-fabd75f8.png)

(b)

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/eggen-backdoor-channels-hidden-in-latent-space-extending-cryptographic-undetectability-to-modern-neural-networks-img3-cd08a08b.png)

(c)

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/eggen-backdoor-channels-hidden-in-latent-space-extending-cryptographic-undetectability-to-modern-neural-networks-img4-ccca92a2.png)

(d)

Figure 6: Original source class (left), triggered input (middle), and secret key (right, shown on a neutral background) images for different model-dataset configurations: (a) ResNet18 on BloodMNIST with source class _basophil_ and target class _eosinophil_, (b) ViT on the same dataset and class pair, (c) ResNet18 on DermaMNIST with source class _melanocytic nevi_ and target class _vascular lesions_, and (d) ViT on DermaMNIST with source class _melanoma_ and target class _dermatofibroma_. Images are randomly selected and illustrate the visual effect of applying the secret key with scaling factor $\lambda$ as used in experiments (Sec. [[#^5-results-and-analysis|5]]).

(a)

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/eggen-backdoor-channels-hidden-in-latent-space-extending-cryptographic-undetectability-to-modern-neural-networks-img5-918273a0.png)

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/eggen-backdoor-channels-hidden-in-latent-space-extending-cryptographic-undetectability-to-modern-neural-networks-img6-cef45c4d.png)

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/eggen-backdoor-channels-hidden-in-latent-space-extending-cryptographic-undetectability-to-modern-neural-networks-img7-31551beb.png)

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/eggen-backdoor-channels-hidden-in-latent-space-extending-cryptographic-undetectability-to-modern-neural-networks-img8-85dfd5c3.png)

(b)

Figure 7: (a) Visibility of the trigger, quantified by the MMD score, as a function of the scaling factor $\lambda$. Results are shown for ResNet18 on BloodMNIST with source class _basophil_ and target class _eosinophil_. The value of $\lambda$ used in the final configuration giving results as presented in Sec. [[#^5-results-and-analysis|5]] is highlighted. A baseline MMD score is computed by splitting the original dataset into two halves. (b) Example input image from the source class with the same secret key weighted by (top left) $\lambda=0.01$, (top right) $\lambda=0.5$, (bottom left) $\lambda=2$ and (bottom right) $\lambda=5$.

## Appendix M Hyperparameter sweeps and sensitivity analysis ^appendix-m-hyperparameter-sweeps

To illustrate the trade-offs between the key hyperparameters – the spike strength $\theta$ and stealithiness, measured by the regularisation weight $\lambda_{\text{L2}}$ – and their effect on the ASR, we perform separate parameter sweeps while keeping all other hyperparameters fixed at the values reported in App. [[#^appendix-f-hyperparameter-configurations|F]].

Table 8 reports the ASR and clean accuracy of backdoors planted with different values of the spike strength $\theta$. As expected, making the spike more prominent by increasing $\theta$ increases the ASR but decreases clean accuracy: a stronger spike has a greater effect on triggered inputs, but its dominance in the model weights reduces performance on clean inputs. Table 8 shows the effect of varying the stealthiness through the regularisation weight $\lambda_{\text{L2}}$. As expected, smaller values of $\lambda_{\text{L2}}$ impose weaker regularisation on the optimised trigger and result in higher ASR. Conversely, stronger regularisation produces less visible perturbations such that the triggered input more closely resembles clean images, leading to lower ASR.

Both experiments use the ResNet18 architecture trained on the BloodMNIST dataset with source class _basophil_ and target class _eosinophil_. Each experiment is run with 10 random seeds, and results are reported with 95% confidence intervals.

Table 7: Average ASR and clean accuracy for different spike strengths $\theta$, with 95% confidence intervals.

| $\theta$ | ASR | Clean Accuracy |
| --- | --- | --- |
| 0.010 | 0.239 $\pm$ 0.043 | 0.982 $\pm$ 0.000 |
| 0.025 | 0.881 $\pm$ 0.029 | 0.982 $\pm$ 0.000 |
| 0.050 | 0.940 $\pm$ 0.011 | 0.982 $\pm$ 0.000 |
| 0.100 | 0.969 $\pm$ 0.007 | 0.982 $\pm$ 0.000 |
| 0.250 | 0.986 $\pm$ 0.004 | 0.974 $\pm$ 0.002 |
| 0.500 | 0.999 $\pm$ 0.002 | 0.923 $\pm$ 0.006 |
| 1.000 | 1.000 $\pm$ 0.000 | 0.807 $\pm$ 0.008 |

Table 8: Average ASR for different regularisation weights $\lambda_{\text{L2}}$, with 95% confidence intervals.

| $\lambda_{\text{L2}}$ | ASR |
| --- | --- |
| 0 | 1.000 $\pm$ 0.000 |
| 5 | 1.000 $\pm$ 0.000 |
| 10 | 0.991 $\pm$ 0.003 |
| 15 | 0.964 $\pm$ 0.009 |
| 20 | 0.936 $\pm$ 0.007 |
| 25 | 0.789 $\pm$ 0.081 |
| 30 | 0.352 $\pm$ 0.043 |

[^note-1]: It is worth noting that CAVs are known to be unstable across training runs and sensitive to the choice of probe dataset. Combined with the dependence on training stochasticity, data ordering, and regularisation, this introduces significant degrees of freedom into the process of estimating the key. Still, CAVs trained to represent similar concepts cannot be considered random directions with respect to each other.

[^note-2]: We assume that the adversary is unable to train clean models without conflicting with the MLaaS setting – either because they lack the computational power or expertise, or because they do not have access to the full set of training data.

[^note-3]: This assumes the weight vector $\mathbf{w}$ is i.i.d (independent and identically distributed) with zero mean, a shared variance $\sigma^{2}$, and zero pairwise covariance ($\mathbb{E}[w_{i},w_{j}]=0,\quad\forall i\neq j$ ).
