---
id: 5e3c4245-a339-4aa8-8511-3f41ebf33104
title: "On neural scaling and the quanta hypothesis"
summary_for_tutor: "Eric J. Michaud revisits 'The Quantization Model of Neural Scaling', which he wrote in 2023 with Ziming Liu, Uzay Girit and Max Tegmark. The puzzle it addresses: mean loss falls smoothly as a power law in parameters, data and steps, yet specific abilities appear abruptly (emergent abilities, the induction-heads phase change). The quanta hypothesis is that networks learn discrete modules (quanta), each either fully learned or not, and that how often each is needed follows a power law. Scaling then adds quanta in order of frequency, and the average over many of these jumps looks smooth. The evidence: on multitask sparse parity, subtasks are learned roughly in order of frequency. Per-token curves for the Pythia models are more mixed, and many look smooth, which forces the assumption that most tokens are 'polygenic'. Clustering gradients on pythia-70m finds skills such as counting and predicting newlines to keep line lengths even. Michaud flags limitations throughout."
---

#### Article
source:: [[../articles/ericjmichaud-on-neural-scaling-and-the-quanta-hypothesis]]
to:: "last two years, which I'll discuss [[#^features-quanta-and-sparse-autoencoders|below]]."
