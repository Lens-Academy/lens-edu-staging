---
title: "Language Models Learn to Mislead Humans via RLHF"
author:
  - "Jiaxin Wen"
  - "Ruiqi Zhong"
  - "Akbir Khan"
  - "Ethan Perez"
  - "Jacob Steinhardt"
  - "Minlie Huang"
  - "Samuel R. Bowman"
  - "He He"
  - "Shi Feng"
source_url: "https://arxiv.org/pdf/2409.12822"
published: 2024-09-19
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "sonnet"
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

Language models (LMs) can produce errors that are hard to detect for humans, especially when the task is complex. RLHF, the most popular post-training method, may exacerbate this problem: to achieve higher rewards, LMs might get better at convincing humans that they are right even when they are wrong. We study this phenomenon under a standard RLHF pipeline, calling it “U-Sophistry” since it is **U**nintended by model developers. Specifically, we ask time-constrained (e.g., 3-10 minutes) human subjects to evaluate the correctness of model outputs and calculate humans’ accuracy against gold labels. On a question-answering task (QuALITY) and programming task (APPS), RLHF makes LMs better at convincing our subjects but not at completing the task correctly. RLHF also makes the model harder to evaluate: our subjects’ false positive rate increases by 24.1% on QuALITY and 18.3% on APPS. Finally, we show that probing, a state-of-the-art approach for detecting **I**ntended Sophistry (e.g. backdoored LMs), does not generalize to U-Sophistry. Our results highlight an important failure mode of RLHF and call for more research in assisting humans to align them[^note-1].

![Figure 1](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig1-b3b203ce.png)

We perform RLHF with a reward function based on ChatbotArena and conduct evaluations on a challenging question-answering dataset, QuALITY. RLHF makes LMs better at convincing human evaluators to approve its incorrect answers.

## Introduction ^introduction

Language models (LMs) are used for more complex tasks as they become more capable. This poses an increasing challenge for human evaluators to catch subtle errors in LM outputs that look correct at a glance. A gap emerges between what is correct and what looks correct to humans.

This gap may cause reward hacking in RLHF (Skalse et al. 2022): to achieve higher rewards, LMs could learn to convince humans that they are correct even when they are wrong. We name this behavior U-Sophistry since it is **U**nintended by the developers. U-Sophistry is a consequence of Goodhardt’s Law: human approvals provide less accurate evaluations when they become the optimization target.

U-Sophistry poses significant risks when we use LMs for complex and critical tasks. For instance, RLHF might make AI better at persuading humans to accept inaccurate scientific findings or biased policies on high-stakes issues (Hendrycks et al. 2023). This is ironic: while RLHF is supposed to control AI, it might deceive humans into believing that they are in control (Christiano 2019).

While likely in theory (Skalse et al. 2022), U-Sophistry is yet to be empirically validated. Many prior works study I-Sophistry: while they aim to study unintended misleading AI behaviors, they induce these behaviors **I**ntentionally with non-standard engineering practices and hope their conclusions can generalize to U-Sophistry. For example, Sharma et al. (2023) explicitly prompts LMs to deceive human subjects, Hubinger et al. (2024) fine-tunes LMs on malicious behaviors, and Denison et al. (2024) uses brittle rewards designed to be hacked.[^note-2] In contrast, we study U-Sophistry that naturally emerges from standard, innocuous practices: we need to know whether U-Sophistry matters in practice, how LMs can mislead humans, and what mitigations are effective.

We empirically investigate U-Sophistry in two tasks: long-passage question-answering and algorithmic programming. We ask time-constrained (e.g. 3-10 minutes) human subjects to evaluate the correctness of LM’s outputs. We then measure U-Sophistry by calculating human evaluation accuracy against gold labels before and after RLHF.

With 150 hours of human study, we find that U-Sophistry emerges even under widely-accepted reward signals, e.g. optimizing against a reward model learned from the ChatbotArena human preference data (Chiang et al. 2024a). We find that after RLHF, the LM does not get better at the task, but it misleads our subjects to approve its incorrect answers more often. Our subjects become worse at evaluating LM’s outputs: their false positive rate increases by 24% on question-answering (QuALITY) (Pang et al. 2022) and 18% on programming (APPS) (Hendrycks et al. 2021). Our subjects are also misled to confidently mislabel incorrect outputs as correct.

We qualitatively analyze how LMs mislead our subjects after RLHF by surveying their feedback. On question-answering, LMs learn to defend incorrect answers by cherry-picking or fabricating supporting evidence, making consistent but untruthful arguments, and providing arguments that contain subtle causal fallacies. On the programming task, LMs learn to generate partially incorrect programs that still pass all evaluator-designed unit tests, produce less readable programs, and make fewer common errors that humans typically check for.

Finally, we evaluate prior mitigation methods to detect U-Sophistry. We experiment with the probing method from MacDiarmid et al. (2024), which achieves a near-perfect accuracy (99.3% AuROC) at detecting I-Sophistry from Sleeper Agents (Hubinger et al. 2024), an LM fine-tuned to generate flawed programs when certain backdoor trigger appears. This probing method fails for detecting U-Sophistry, performing no better than chance. Therefore, I-Sophistry detection is not a good benchmark for methods meant for detecting U-Sophistry. As AI capabilities rapidly increase, our results call for more research in assisting human evaluators against U-Sophistry.

## U-Sophistry Emerges as an Unintended Consequence of RLHF ^u-sophistry-emerges-as-an

We first provide background on RLHF and introduce three different rewards: $R^{*}$ (correctness), $R^{\textnormal{human}}$ (human ratings), and $R^{\textnormal{train}}$ (reward in RLHF training). We then hypothesize how these reward functions interact with each other during RLHF and increase U-Sophistry as a result.

**RLHF Background.** RLHF (Christiano et al. 2017) is a popular method for aligning LMs. At a high level, it collects human evaluations on a dataset of outputs, trains a reward model to imitate human evaluations, and then optimizes a policy against the reward model. We call the LM before RLHF $\pi_{\textnormal{init}}$ and the LM after RLHF $\pi_{\textnormal{rlhf}}$. RLHF involves three different rewards: $R^{*}$, $R^{\textnormal{human}}$, and $R^{\textnormal{train}}$, each of which is a function that maps an input-output pair to a scalar value.

-   **Oracle Reward $R^{*}$** represents what we _truly_ want the LM to optimize, e.g. the correctness of programs or answers. $R^{*}$ is typically established by (ensembled) untimed expert human evaluators and is therefore too expensive for large-scale training or evaluation.
    
-   **Human Reward $R^{\textnormal{human}}$** is what we collect to evaluate LMs in practice, typically from individual humans with time constraints. Different from $R^{*}$, $R^{\textnormal{human}}$ inherits weaknesses from human evaluators. Due to cognitive overload and biases, humans often rely on shortcuts, overlook subtle errors (Saunders et al. 2022; Perry et al. 2023; Gudibande et al. 2023), and approve flawed LM responses that are assertive (Hosking et al. 2023), sycophantic (Sharma et al. 2023), or verbose (Kabir et al. 2023). Nevertheless, $R^{\textnormal{human}}$ is still commonly used to evaluate LMs due to the lack of alternatives.
    
-   **Proxy Human Reward $R^{\textnormal{train}}$** is a proxy for $R^{\textnormal{human}}$. Since computing $R^{\textnormal{human}}$ requires humans in the loop, it is too expensive to directly optimize in RLHF. Instead, most RLHF pipelines use $R^{\textnormal{train}}$, a cheaper automatic proxy derived from $R^{\textnormal{human}}$, e.g. by training a reward model on pair-wise human preference (Ouyang et al. 2022). $R^{\textnormal{train}}$ thus inherits the weaknesses of $R^{\textnormal{human}}$.
    

**Hypothesis: U-Sophistry emerges from RLHF.** The gap between $R^{\textnormal{train}}$ and $R^{*}$ can result in reward hacking, where $\pi_{\textnormal{rlhf}}$ learns to exploit $R^{\textnormal{train}}$ without optimizing the intended reward $R^{*}$. As a result, $\pi_{\textnormal{rlhf}}$ improves significantly on $R^{\textnormal{train}}$ but not on $R^{*}$. Because $R^{\textnormal{human}}$ might be susceptible in similar ways to $R^{\textnormal{train}}$, $R^{\textnormal{human}}$ might also increase, thus leading to U-Sophistry.

Take question-answering as an example: if humans are susceptible to rhetorical arguments, $R^{\textnormal{train}}$ might carry similar flaws since it is learned from $R^{\textnormal{human}}$. If $\pi_{\textnormal{rlhf}}$ learns to exploit $R^{\textnormal{train}}$ by providing rhetorical arguments, it will mislead humans as well, leading to U-Sophistry.

### Comparsion with Prior Works ^comparsion-with-prior-works

| **Example** | **Unintended: Reward** | **Unintended: FT Data** | **Unintended: Prompt** | **Misleading** |
| --- | --- | --- | --- | --- |
| _**Unintended but Non-misleading**_ |  |  |  |  |
| Clark (2016): A boat trained to play a game exploits its environment reward by simply circling and repeatedly hitting the same target. |  |  |  |  |
| Paulus et al. (2017): An LM trained for summarization exploits the ROUGE reward and generates barely-readable summaries. |  |  |  |  |
| Singhal et al. (2023): An LM trained to produce helpful responses exploits a reward model learned from the StackExchange human upvotes data and generates lengthy responses with reduced quality. |  |  |  |  |
| _**Misleading but Intended (I-Sophistry)**_ |  |  |  |  |
| Sharma et al. (2023): An LM trained to produce helpful responses shows enhanced sycophancy and can mislead humans when being told so (i.e., explicitly prompting LMs to subtly deceive humans). |  |  |  |  |
| Hubinger et al. (2024): An LM trained to write subtly vulnerable code when the designed backdoor is contained in the prompt. |  |  |  | Not evaluated |
| Denison et al. (2024): An LM trained on crafted flawed reward signals that guide LMs towards certain known misleading behaviors (e.g., sycophancy or human flattering). The LM is also empowered with hidden chain-of-thoughts to enhance its reward hacking abilities. |  |  |  | Not evaluated |
| _**Unintended and Misleading (U-Sophistry)**_ |  |  |  |  |
| Ours: An LM trained to produce correct programs or answers under a common RLHF pipeline. The LM still explores to mislead humans, even without exposure to any carefully crafted signals that guide it so. |  |  |  |  |

**We focus on misleading real human evaluators, not just a proxy reward.** Prior work on reward hacking primarily focuses on exploiting $R^{\textnormal{train}}$, which is both less harmful and easier than exploiting $R^{\textnormal{human}}$. Exploiting $R^{\textnormal{train}}$ is less harmful because once humans recognize LM’s bad outputs, they can prevent the harm by rejecting these outputs. Exploiting $R^{\textnormal{train}}$ is also easier for two reasons:

-   $R^{\textnormal{train}}$ from prior work is usually simple, e.g., a summary that achieves a high ROUGE score (simple reward) might be barely readable and obviously bad for humans (Paulus et al. 2017).
    
-   $R^{\textnormal{train}}$ is directly observed by LMs, while $R^{\textnormal{human}}$ is not. Therefore, exploiting $R^{\textnormal{human}}$ requires LMs to reward-hack in a way that generalizes beyond $R^{\textnormal{train}}$, which poses a greater challenge.
    

In contrast, we focus on threats that mislead human evaluators, which are both more harmful and more challenging experimentally.

**We focus on U-Sophistry that emerges as an unintended consequence of RLHF.** Many prior works aim to study U-Sophistry. However, they study I-Sophistry, where the undesirable behaviors are **I**ntentionally induced by non-standard engineering practices, and implicitly assume that the conclusions on I-Sophistry can generalize to U-Sophistry. As summarized by the second block of Table [\[tab:threatmodel\]](#tab:threatmodel), they induce undesirable behaviors by manipulating rewards, fine-tuning data, or prompts. It is unclear whether U-Sophistry will emerge under standard training practices, where the reward is not designed to induce malicious behaviors but is still flawed due to human weaknesses. In contrast, our work focuses on U-Sophistry that naturally emerges. [^note-3]

## Experiments ^experiments

We show that RLHF leads to U-Sophistry on two datasets where $R^{*}$ can be automatically computed: QuALITY (question-answering) and APPS (programming). We first use RLHF to fine-tune a language model $\pi_{\textnormal{init}}$ to obtain $\pi_{\textnormal{rlhf}}$. The reward function, pre-trained model, and optimization method are introduced in Section [[#^fine-tuning-language-models-with|3.2]]. We then recruit expert human subjects from UpWork and universities to collect human evaluations ($R^{\textnormal{human}}$) on the outputs from $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ (Section [[#^human-evaluation|3.3]]). For each language model, we report:

-   Correctness: how often is its output correct according to $R^{*}$? (i.e. $R^{*}$\= 1)
    
-   Human approval: how often do humans consider its output correct? (i.e. $R^{\textnormal{human}}$\= 1)
    
-   Human evaluation error rate: how often is human evaluation incorrect? (i.e. $R^{*} \neq$ $R^{\textnormal{train}}$)
    
-   Human false positive rate: when the output is wrong, how often do humans consider it correct? (i.e. $R^{*}$\= 0 but $R^{\textnormal{train}}$\= 1). To ensure a fair comparison, we compute it on the subset of data points where both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ are wrong.
    

If RLHF increases U-Sophistry, we expect to see 1) the increase in human approval is disproportionate to the improvement in correctness, and 2) the human evaluation error and false positive rate will increase.

### Datasets ^datasets

**Question Answering (QA).** We use the QuALITY dataset (Pang et al. 2022). In this dataset, each example has a long context passage (on average about 5,000 tokens), a question about the passage, and four answer choices. The correct choice for each question is determined by an ensemble of 3 to 5 human evaluators without time limits. We modify the dataset so that each example comes with two choices, including the correct answer and the best distractor (the incorrect choice that has the highest vote). The LM needs to output a choice and an argument for why it is correct, with $R^{*} =1$ if its choice is correct and 0 otherwise.

**Programming.** APPS (Hendrycks et al. 2021), a challenging algorithmic code benchmark. Each example has a problem description, a reference solution, and on average 34 unit tests designed by untimed humans. The LM needs to generate a Python solution based on the problem description, with $R^{*} =1$ if it passes all unit tests and 0 otherwise.

### Fine-tuning Language Models with RLHF ^fine-tuning-language-models-with

We first describe the reward functions used for RLHF training and then discuss other training details.

**Reward signals $R^{\textnormal{train}}$.** We explore two different reward functions for QA and one for programming. The first reward model for QA is **task-specific**: it imitates human evaluations of answer–argument pairs, where the argument is either generated by humans or GPT-4; we obtain these human evaluations from Khan et al. (2024), which instructed the evaluators to do their best without time constraints. The second reward model for QA is **general**: it is trained on human preferences from ChatBotArena, where users submit their prompts, look at outputs from two different models, and indicate which model is better; ChatBotAreana is a widely accepted human feedback source and used to evaluate various open-source (e.g., Vicuna (Chiang et al. 2023), LlaMA (Touvron et al. 2023)) and proprietary LMs (OpenAI’s GPT-4, Anthropic’s Claude). We present additional training details of our reward model in Appendix [[#^additional-implementation-details|8]].

Unlike QA, the programming task does not have a large enough dataset of human evaluation, which we need to train a reward model. To design a $R^{\textnormal{train}}$ similar to human evaluations, we first performed a pilot study on our subjects to understand their evaluation strategies. We find that they frequently rely on writing simple unit tests to evaluate programs, with an average of 2.4 simple unit tests per program without using complex input values (e.g. large integers or strings). Therefore, to simulate human evaluations, we define $R^{\textnormal{train}}$ to be 1 if it passes the two simplest unit tests in APPS, where the simplicity of a unit test is defined by the number of program samples from $\pi_{\textnormal{init}}$ that can pass it. We later validate that this proxy reward is indeed similar to the human reward based on the evaluation of our human subjects: it achieves a Pearson correlation of $r=$0.59 ($p <$ 0.001), while the human-human correlation is only slightly higher ($r=$ 0.63 with $p <$ 0.001). Our proxy also reflects human evaluation better than $R^{*}$, which achieves $r=$ 0.49 correlation with $R^{\textnormal{human}}$. This proxy reward is only used in RLHF training, and our main results in Section [[#^evidence-of-u-sophistry|3.4]] only use real humans.

**Optimizing the LM against $R^{\textnormal{train}}$.** For QA, we obtain $\pi_{\textnormal{init}}$ by fine-tuning LlaMA-2-7B (base version) (Touvron et al. 2023) to imitate answers and arguments from Michael et al. (2023). For programming, we obtain $\pi_{\textnormal{init}}$ by fine-tuning Deepseek-Coder-7B (Guo et al. 2024) to imitate the golden programs from the original APPS dataset. Next, we obtain $\pi_{\textnormal{rlhf}}$ by optimizing $R^{\textnormal{train}}$ using proximal policy optimization (PPO) (Schulman et al. 2017) following common RLHF practices. We use the TRLX library[^cite-4] to implement PPO.

### Human Evaluation ^human-evaluation

**Recruiting Human Evaluators.** For QA, we recruit 35 evaluators from Upwork. We require the evaluators to be native English speakers experienced in reading and question-answering, and most of them self-reported as teachers, writers, editors, or college students. For programming, we recruit 10 college students majoring in Computer Science or Electronic Engineering and require them to be experienced in Python programming, with some of them exposed to competitive programming before. We train evaluators to use our interface with warmup examples and verify their skills through their evaluation error rate. See Appendix [[#^additional-human-evaluation-details|10]] for more details on human evaluation.

**Obtaining Human Evaluation $R^{\textnormal{human}}$.** For each dataset, we randomly sample 250 questions to evaluate both $\pi_{\textnormal{rlhf}}$ and $\pi_{\textnormal{init}}$.[^note-5] with our customized web interface (Figure [12](#fig:interface-qa) and Figure [13](#fig:interface-code)). For QA, the evaluators are given a question, a reference passage, two answer options, and a model output (including an answer and an argument), and they need to decide which answer is correct within 3 minutes, following the practice of (Parrish et al. 2022; Chiang et al. 2024a). For programming, the evaluators are given a coding problem and a model-generated program, and they need to decide whether the program is correct in 10 minutes (following the practice of (Xie et al. 2016)); in particular, our interface allows them to write their own test cases and run the generated programs.

Instead of directly collecting binary evaluation from our subjects, we collect their confidence that the models’ output is correct (0%, 25%, 50%, 75%, or 100%). We consider them agreeing with the model if the confidence is above $50\%$ (i.e. $R^{\textnormal{human}}$\= 1) and disagreeing otherwise (i.e. $R^{\textnormal{human}}$\= 0).

To incentivize our subjects to find gold labels, we design the following bonus schemes: in QA, each evaluation is paid with \$3 if it’s correct and \$1.5 otherwise; in programming, \$9 for each correct decision with 100% confidence, \$4 for correct with 75% confidence, \$2 for unsure 50%, \$2 for incorrect 75%, and \$1 for incorrect 100%. Overall, correct decisions are rewarded; on the other hand, however, this is not a proper scoring rule, since we explicitly tried to disincentivize our subjects to choose with 50% confidence. Therefore, the confidence labels should be interpreted with caution and not treated as true probabilities.

Finally, a human evaluator might become better at evaluating a question if they encounter it twice, so we ensure that each evaluator only sees a question once. To ensure a fair comparison, we do not tell the evaluators whether an LM output comes from $\pi_{\textnormal{rlhf}}$ or $\pi_{\textnormal{init}}$.

### Evidence of U-Sophistry ^evidence-of-u-sophistry

We report our findings below.

![Figure 2](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig2-2f70d785.png)

Results of RLHF with the task-specific $R^{\textnormal{train}}$ on question-answering.

![Figure 3](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig3-e8b81ea4.png)

Results of RLHF with the general $R^{\textnormal{train}}$ on question-answering.

![Figure 4](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig4-2422111a.png)

Results of RLHF on programming.

From left to right, the graph illustrates: (1) while humans approve $\pi_{\textnormal{rlhf}}$ more often than $\pi_{\textnormal{init}}$, its correctness does not improve. (2) Human evaluation error rate increases after RLHF. (3) The false positive rate of human evaluation increases after RLHF.

![Figure 5](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig5-e7d98038.png)

Results on how RLHF influences human evaluators’ confidence. We collect the confidence distribution when the LMs’ outputs are wrong. Human evaluators are misled to confidently mislabel incorrect outputs as correct after RLHF.

**Finding 1: RLHF increases human approval, but not necessarily correctness.** We compare the human approval and the correctness of $\pi_{\textnormal{rlhf}}$ and $\pi_{\textnormal{init}}$ in the leftmost columns in Figure [5](#fig:generate-result). Across all three setups, RLHF substantially increases human approval (+9.4% on QA under general $R^{\textnormal{train}}$, +6.0% on QA under task-specific $R^{\textnormal{train}}$ and +14.3% in programming) but barely increases correctness. This implies that RLHF increases U-Sophistry, making the language model appear more convincing to humans without improving the performance on the intended task.

**Finding 2: RLHF weakens humans’ ability to evaluate.** We report the evaluation error rate in the second column of Figure [5](#fig:generate-result). We find that RLHF increases the evaluation error rate. On QA, the human evaluation error rate increases from 42.9% to 58.5% after RLHF with the task-specific $R^{\textnormal{train}}$ and increases from 40.8% to 48.2% after RLHF with the general $R^{\textnormal{train}}$. On programming, the human evaluation error rate increases from 31.3% to 45.7%.

**Finding 3: RLHF makes wrong outputs more convincing to humans.** The false positive rate of human evaluation substantially increases after RLHF. It increases from 41.0% to 65.1% after RLHF with the task-specific QA $R^{\textnormal{train}}$, from 46.7% to 70.2% after RLHF with the general QA $R^{\textnormal{train}}$, and from 29.6% to 47.9% after RLHF with the programming $R^{\textnormal{train}}$. These results indicate that RLHF makes wrong outputs more convincing.

We also investigate how human confidence changes after RLHF and report preliminary results in Figure [6](#fig:confidence). On the QA task, $\pi_{\textnormal{rlhf}}$ misleads human evaluators to label more incorrect arguments as correct with 100% confidence. On the programming task, $\pi_{\textnormal{rlhf}}$ mainly misleads human evaluators to label more incorrect programs as correct with 75% confidence instead of 100%. We conjecture that our subjects are well aware that the programming problems are challenging, making them less likely to assert a program is entirely bug-free.

In Appendix [[#^additional-human-studies-when|9]], we include additional results on evaluating language models optimized under $R^{*}$. It misleads humans far less often when incorrect, suggesting that the imperfections in $R^{\textnormal{train}}$ cause language models to exploit human weaknesses. We also find that the correctness improves after RLHF with $R^{*}$, suggesting that our RLHF implementation is correct.

### Robustness Checks for Our Findings ^robustness-checks-for-our

**Our finding is not due to noises in the recruiting process.** It is possible that we coincidentally recruit a few subjects that are particularly susceptible to arguments by $\pi_{\textnormal{rlhf}}$. To ensure that our findings are not skewed by outliers, we compare the evaluation error rate of each subject on $\pi_{\textnormal{rlhf}}$ and $\pi_{\textnormal{init}}$. We find that 71% of the evaluators’ error rate increases after optimizing the task-specific QA $R^{\textnormal{train}}$, 76% increases after optimizing the general QA $R^{\textnormal{train}}$, and 90% increases after optimizing the programming $R^{\textnormal{train}}$. We then conduct a paired $t$\-test under the null hypothesis that the increase size is 0, and the $p$\-value is 0.003, 0.003, and 0.049 for these three setups, respectively.

![Figure 6](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig6-9e1933dc.png)

**Our subjects put in similar or more effort when evaluating $\pi_{\textnormal{rlhf}}$.** Our subjects may put in less effort when evaluating $\pi_{\textnormal{rlhf}}$ and thus their accuracy decreases. To rule out this hypothesis, we measure human efforts in the evaluation procedure. For QA, we measure the average time spent by our subjects and find that they use up the full three minutes for both $\pi_{\textnormal{rlhf}}$ and $\pi_{\textnormal{init}}$. For programming, we measure 1) time spent, 2) the number of unit tests, and 3) the diversity of the unit tests, which is measured by the average editing distance across all unit test pairs. We report these results in Figure [\[fig:program\_human\_efforts\]](#fig:program_human_efforts), and find that our subjects spend more time (558s vs. 540s) and write slightly more unit tests with higher diversity when evaluating $\pi_{\textnormal{rlhf}}$ compared to $\pi_{\textnormal{init}}$. Despite trying harder, our subjects’ evaluation error rate still increases.

### Qualitative Analysis on Question-Answering ^qualitative-analysis-on-question-answeri

![Figure 7](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig7-11e42804.png)

$\pi_{\textnormal{rlhf}}$ misleads human evaluators by fabricating evidence. In this case, $\pi_{\textnormal{rlhf}}$ fabricates statistical evidence and thus appears authoritative to human evaluators, with human feedback saying “Agree! statement and statistics indicate that the answer is correct.”

We qualitatively analyze $\pi_{\textnormal{rlhf}}$\-generated arguments to understand why they are more misleading.

**Fabricating or Cherry-picking Evidence.** Both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ tend to fabricate evidence when arguing for their predicted answers. However, human evaluators find the $\pi_{\textnormal{rlhf}}$\-fabricated evidence more convincing, whereas the $\pi_{\textnormal{init}}$\-fabricated evidence is sometimes nonsensical or irrelevant to their answers. For instance, in Figure [7](#fig:case_qa_evidence_3), $\pi_{\textnormal{rlhf}}$ fabricates statistical evidence that makes human evaluators very confident that their answer is right. Additionally, LMs also cherry-pick text fragments from the reference passage to support incorrect answers (Figure [21](#fig:case_qa_evidence_4)), which poses challenges even for evaluators attempting to verify the evidence against the reference passage.

**Arguing for Incorrect Answers with Consistent Logic.** $\pi_{\textnormal{init}}$ often generates inconsistent arguments for incorrect answers, making these arguments easily detectable. For instance, in Figure [22](#fig:case_qa_consistency_1), human evaluators find $\pi_{\textnormal{init}}$ begins by defending choice A but ends up defending choice B. In contrast, arguments by $\pi_{\textnormal{rlhf}}$ tend to be more consistent, thus better supporting incorrect answers.

**Making Seemingly Coherent Arguments with Subtle Fallacies.** $\pi_{\textnormal{rlhf}}$ can appear logically coherent while introducing subtle causal fallacies to defend incorrect answers (Figure [24](#fig:case_qa_logical_1)). In contrast, as shown in Figure [24](#fig:case_qa_logical_1) and Figure [25](#fig:case_qa_logical_2), $\pi_{\textnormal{init}}$ generates more obvious causal fallacies that are frequently recognized by human evaluators.

### Qualitative Analysis on Programming ^qualitative-analysis-on-programming

To further gain insight into how $\pi_{\textnormal{rlhf}}$\-generated programs mislead human evaluators, we analyze the collected human labels alongside their explanations.

![Figure 8](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig8-fafa9591.png)

$\pi_{\textnormal{rlhf}}$ mislead humans by generating less readable programs that still pass all evaluator-written unit tests. In contrast, $\pi_{\textnormal{init}}$ generates more modular programs and often fails on the first evaluator-written unit test. This happens even when $\pi_{\textnormal{rlhf}}$ obtains a substantially lower unit test passing rate on the original APPS dataset than $\pi_{\textnormal{init}}$ (26.8% vs. 58.3%).

**Hacking Human-written Unit Tests.** As illustrated in Figure [14](#fig:case_program_hack1) and Figure [15](#fig:case_program_hack2), we observe that $\pi_{\textnormal{rlhf}}$\-generated incorrect programs can still pass all (3 to 5) evaluator-written unit tests in the actual evaluation process, which are not observed during RLHF. In contrast, $\pi_{\textnormal{init}}$\-generated incorrect programs typically fail the first evaluator-written unit test. This occurs even when $\pi_{\textnormal{rlhf}}$ passes fewer unit tests in the original APPS dataset (Figure [8](#fig:case_program_obfuscation_1)). This indicates that LMs may learn to predict and hack the human-written unit tests from RLHF.

**Generating Less Readable Programs.** $\pi_{\textnormal{rlhf}}$ tends to generate less readable programs (e.g., less modular, more complex control flows) than $\pi_{\textnormal{init}}$. Therefore, instead of understanding programs’ logic, our subjects have to rely on writing unit tests; as a result, they become more easily misled by $\pi_{\textnormal{rlhf}}$, which is good at hacking human-written unit tests. For instance, in Figure [8](#fig:case_program_obfuscation_1), while both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ are incorrect, $\pi_{\textnormal{init}}$ provides clear modularization and hence the evaluators can easily locate the error in the function. In contrast, $\pi_{\textnormal{rlhf}}$ does not define any helper function and uses complex nested loops and if-statements. As a result, our human subjects put more effort into writing unit tests, and then get misled since all their unit tests get passed by $\pi_{\textnormal{rlhf}}$.

![Figure 9](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig9-702511df.png)

We provide additional quantitative evidence that $\pi_{\textnormal{rlhf}}$\-generated programs are less readable: in Figure [\[fig:program\_obfuscation\]](#fig:program_obfuscation), we report modularity (number of helper functions) and Cyclomatic Complexity (McCabe 1976) for generated programs. We find that incorrect programs generated by $\pi_{\textnormal{rlhf}}$ contain fewer helper functions and exhibit higher complexity, thus making it harder for our subjects to understand and evaluate.

**Resisting Human Evaluation Shortcuts.** We observe that our subjects often first search for snippets vulnerable to edge case errors (e.g., out-of-bound exceptions). For instance, in Figure [18](#fig:case_program_edge_2), humans easily find $\pi_{\textnormal{init}}$ is incorrect from the code line, as it would cause out-of-bound exceptions. In contrast, $\pi_{\textnormal{rlhf}}$ is less likely to generate such easily detectable errors that can be exploited by humans.

## Is I-Sophistry a Good Benchmark for Mitigating U-Sophistry? ^is-i-sophistry-a-good

![Figure 10](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig10-c495a968.png)

Due to the absence of U-Sophistry, prior work on detecting misleading AI mainly evaluates on I-Sophistry. For example, MacDiarmid et al. (2024) found that probing can achieve nearly perfect AuROC (99.3%) in detecting incorrect programs generated by sleeper agent, a model performs I-Sophistry(Hubinger et al. 2024). Does this result generalize to U-Sophistry, which is closer to misleading AI that naturally emerges in the real world?

We experimented with a similar probing method to MacDiarmid et al. (2024) and modified it to improve performance. We first provide a summary of their probing approach: they first construct a training dataset with two examples: (1) Text: “Human: Are you a helpful AI? Assistant: no”, Label: True (2) Text: “Human: Are you a helpful AI? Assistant: yes", Label: False; they then obtain detector vector by subtracting the “false” label activations from “true” label activations at an intermediate layer of the model; at evaluation time, the activations of LM responses (e.g., the generated correct or incorrect programs) are projected onto this detector tensor to calculate the final probability. To further improve the performance of their probing method, we train a 1-layer MLP which takes text activations as inputs and outputs the final probability. We conducted a hyperparameter search over regularization methods, learning rate schedulers, and intermediate layers.

We report the best AuROC score across all hyperparameter choices in detecting bad behaviors from the sleeper agent and our models in Figure [\[fig:probe\]](#fig:probe). While this probing method works well on the sleeper agent, it is not much better than random guessing on our model. This implies that U-Sophistry that naturally emerges can be inherently different from I-Sophistry that is artificially induced, and detection methods that work on one might not necessarily generalize to another. To improve defenses against increasingly capable AI systems in the real world, our results highlight the need for future experiments to benchmark against U-Sophistry.

## Related Work ^related-work

**Challenges of RLHF.** Despite RLHF being the most popular post-training method, there is a growing concern about its fundamental challenge in collecting accurate human feedback (Casper et al. 2023). Human evaluators are inherently imperfect, tending to rely on shortcuts and overlook subtle errors (Saunders et al. 2022; Perry et al. 2023; Hosking et al. 2023; Sharma et al. 2023). These challenges can lead to degenerated LMs or, more concerningly, lead to U-Sophistry. In this work, we systematically validate this concern on realistic tasks. Our results call for more cautious human evaluations, particularly when the data will be used to train LMs under RLHF.

As illustrated in Table [\[tab:threatmodel\]](#tab:threatmodel), reward hacking has been extensively studied in traditional RL environments, and recently gains increasing attention in LM research with the rise of RLHF. However, these works primarily focus on merely exploiting $R^{\textnormal{train}}$ instead of $R^{\textnormal{human}}$. Therefore, the resulting reward hacking behavior is still easy for humans to spot. In contrast, our work examines whether LMs can reward-hack in a way that can generalize beyond $R^{\textnormal{train}}$ to $R^{\textnormal{human}}$. which are both more harmful and more challengingly experimentally.

**Misleading AI.** Accurate human evaluation is crucial for the safe development and deployment of LMs. This makes misleading AI, which can slip past human evaluation, a significant risk. To study this risk, prior work mainly builds I-Sophistry by explicitly guiding LMs to mislead humans, as shown in Table [\[tab:threatmodel\]](#tab:threatmodel). Therefore, skeptics of misleading AI argue that it would not emerge naturally. Moreover, many of these works lack rigorous human evaluations, leaving uncertainty about whether the induced LM can mislead real humans. In contrast, our work provides strong evidence of U-Sophistry with real human subjects. We also highlight the difference between I-/U-Sophistry in benchmarking mitigation techinques, inspring future works to focus more on U-Sophistry.

**Scalable Oversight.** To assist human evaluators against capable AI systems, recent works on scalable oversight has explored using LMs to assist humans. Typical assistance strategies include task decomposition (Wen et al. 2024), test case generation (Zhong et al. 2023), critique (Saunders et al. 2022; McAleese et al. 2024), and debate (Khan et al. 2024). However, while Saunders et al. (2022) benchmarked their method on subtle, misleading errors, most works lack such evaluations. Future work should evaluate the real-world effectiveness of these techniques, particularly on misleading errors, and deploy them at scale to provide practical support in managing AI systems.

## Discussion ^discussion

**The improvement you see might not be real.** A lot of works on aligning language models use human evaluation as the de facto ground truth metric (Ouyang et al. 2022; Bai et al. 2022; Chiang et al. 2024b), and companies use crowdsourced feedback (e.g. Elo-ratings from ChatBotArena) to evaluate, train, and advertise their models/products. However, these feedbacks exhibit human weaknesses, because they are frequently gathered from untrained, anonymous users spending minimal time (e.g., 1 minute) during evaluation. Our work shows that RLHF can make language models learn to mislead human evaluators, hence creating a delusion that the models are improving.

**Developers might not easily notice U-Sophistry.** It is common for model developers to overfit to metrics that do not track real progress in model performance (Clark 2016; Paulus et al. 2017; Singhal et al. 2023). Fortunately, in most cases, the developers can tell that their model is not performing well by spot-checking a few examples. However, spot-checking might be insufficient to discover U-Sophistry: since developers are humans, they can also be misled to think that the model has improved. The “developers” that overlooked U-Sophistry can be any human, which includes us, the authors, and you, the one reading this paragraph now.

**Limitations.** One limitation of our work is that our evaluations are confined to the specific domains of long-passage question-answering and algorithmic coding. There are broader LM application domains such as open-ended QA and engineering programming. However, as $R^{\textnormal{train}}$ and $R^{\textnormal{human}}$ still suffer from inherent human weaknesses, we believe our findings could generalize to these domains.

Another limitation of our work is that we didn’t study human evaluators with varying capabilities. For question-answering, our human subjects are all native English speakers experienced in reading and question-answering. For programming, our human subjects are all experienced Python programmers. We also set a decent yet not redundant time constraint of 3 to 10 minutes. It is worth studying how conclusions change with less or more capable human subjects.

Finally, during human evaluation, we only ask our subjects to decide the binary correctness of LMs’ outputs. It is worth studying whether other forms of human feedback (e.g., fine-trained human feedback (Wu et al. 2024)) can be more robust to U-Sophistry.

## Conclusion ^conclusion

We present the first systematic study of U-Sophistry, an unintended but dangerous failure mode of RLHF. With real human subjects, we validate the existence of U-Sophistry in two challenging tasks: question-answering and programming. Unlike prior works that intentionally induce I-Sophistry with malicious prompts, fine-tuning data, or rewards, we show that U-Sophistry can emerge even under widely-accepted reward signals.

Our results underscore the risk of applying RLHF to control increasingly capable AI systems: future AI systems might become better at misleading us and pretending to be correct, causing us to lose control unknowingly. By providing a systematic demonstration that U-Sophistry can emerge in practice, we hope our work can attract more researchers to address this looming concern and empower human evaluators against increasingly capable AI systems.

## References ^references

-   Yuntao Bai, Saurav Kadavath, Sandipan Kundu, Amanda Askell, Jackson Kernion, Andy Jones, Anna Chen, Anna Goldie, Azalia Mirhoseini, Cameron McKinnon, et al. Constitutional ai: Harmlessness from ai feedback. _arXiv preprint arXiv:2212.08073_, 2022.
    
-   Stephen Casper, Xander Davies, Claudia Shi, Thomas Krendl Gilbert, Jérémy Scheurer, Javier Rando, Rachel Freedman, Tomasz Korbak, David Lindner, Pedro Freire, et al. Open problems and fundamental limitations of reinforcement learning from human feedback. _arXiv preprint arXiv:2307.15217_, 2023.
    
-   Wei-Lin Chiang, Zhuohan Li, Zi Lin, Ying Sheng, Zhanghao Wu, Hao Zhang, Lianmin Zheng, Siyuan Zhuang, Yonghao Zhuang, Joseph E. Gonzalez, Ion Stoica, and Eric P. Xing. Vicuna: An open-source chatbot impressing gpt-4 with 90%\* chatgpt quality, March 2023. URL [https://lmsys.org/blog/2023-03-30-vicuna/](https://lmsys.org/blog/2023-03-30-vicuna/).
    
-   Wei-Lin Chiang, Lianmin Zheng, Ying Sheng, Anastasios Nikolas Angelopoulos, Tianle Li, Dacheng Li, Hao Zhang, Banghua Zhu, Michael Jordan, Joseph E. Gonzalez, and Ion Stoica. Chatbot arena: An open platform for evaluating llms by human preference, 2024.
    
-   Wei-Lin Chiang, Lianmin Zheng, Ying Sheng, Anastasios Nikolas Angelopoulos, Tianle Li, Dacheng Li, Hao Zhang, Banghua Zhu, Michael Jordan, Joseph E Gonzalez, et al. Chatbot arena: An open platform for evaluating llms by human preference. _arXiv preprint arXiv:2403.04132_, 2024.
    
-   Paul Christiano. What failure looks like - ai alignment forum, 2019. URL [https://www.alignmentforum.org/posts/HBxe6wdjxK239zajf/what-failure-looks-like](https://www.alignmentforum.org/posts/HBxe6wdjxK239zajf/what-failure-looks-like).
    
-   Paul F Christiano, Jan Leike, Tom Brown, Miljan Martic, Shane Legg, and Dario Amodei. Deep reinforcement learning from human preferences. _Advances in neural information processing systems_, 30, 2017.
    
-   Jack Clark. Faulty reward functions in the wild, 2016. URL [https://openai.com/index/faulty-reward-functions/](https://openai.com/index/faulty-reward-functions/).
    
-   Carson Denison, Monte MacDiarmid, Fazl Barez, David Duvenaud, Shauna Kravec, Samuel Marks, Nicholas Schiefer, Ryan Soklaski, Alex Tamkin, Jared Kaplan, et al. Sycophancy to subterfuge: Investigating reward-tampering in large language models. _arXiv preprint arXiv:2406.10162_, 2024.
    
-   Arnav Gudibande, Eric Wallace, Charlie Snell, Xinyang Geng, Hao Liu, Pieter Abbeel, Sergey Levine, and Dawn Song. The false promise of imitating proprietary llms. _arXiv preprint arXiv:2305.15717_, 2023.
    
-   Daya Guo, Qihao Zhu, Dejian Yang, Zhenda Xie, Kai Dong, Wentao Zhang, Guanting Chen, Xiao Bi, Y. Wu, Y.K. Li, Fuli Luo, Yingfei Xiong, and Wenfeng Liang. Deepseek-coder: When the large language model meets programming – the rise of code intelligence, 2024. URL [https://arxiv.org/abs/2401.14196](https://arxiv.org/abs/2401.14196).
    
-   Dan Hendrycks, Steven Basart, Saurav Kadavath, Mantas Mazeika, Akul Arora, Ethan Guo, Collin Burns, Samir Puranik, Horace He, Dawn Song, et al. Measuring coding challenge competence with apps. _arXiv preprint arXiv:2105.09938_, 2021.
    
-   Dan Hendrycks, Mantas Mazeika, and Thomas Woodside. An overview of catastrophic ai risks. _arXiv preprint arXiv:2306.12001_, 2023.
    
-   Tom Hosking, Phil Blunsom, and Max Bartolo. Human feedback is not gold standard. _arXiv preprint arXiv:2309.16349_, 2023.
    
-   Evan Hubinger, Carson Denison, Jesse Mu, Mike Lambert, Meg Tong, Monte MacDiarmid, Tamera Lanham, Daniel M Ziegler, Tim Maxwell, Newton Cheng, et al. Sleeper agents: Training deceptive llms that persist through safety training. _arXiv preprint arXiv:2401.05566_, 2024.
    
-   Samia Kabir, David N Udo-Imeh, Bonan Kou, and Tianyi Zhang. Who answers it better? an in-depth analysis of chatgpt and stack overflow answers to software engineering questions. _arXiv preprint arXiv:2308.02312_, 2023.
    
-   Akbir Khan, John Hughes, Dan Valentine, Laura Ruis, Kshitij Sachan, Ansh Radhakrishnan, Edward Grefenstette, Samuel R. Bowman, Tim Rocktäschel, and Ethan Perez. Debating with more persuasive llms leads to more truthful answers. In _Forty-first International Conference on Machine Learning, ICML 2024, Vienna, Austria, July 21-27, 2024_. OpenReview.net, 2024. URL [https://openreview.net/forum?id=iLCZtl7FTa](https://openreview.net/forum?id=iLCZtl7FTa).
    
-   Monte MacDiarmid, Timothy Maxwell, Nicholas Schiefer, Jesse Mu, Jared Kaplan, David Duvenaud, Sam Bowman, Alex Tamkin, Ethan Perez, Mrinank Sharma, Carson Denison, and Evan Hubinger. Simple probes can catch sleeper agents, 2024. URL [https://www.anthropic.com/news/probes-catch-sleeper-agents](https://www.anthropic.com/news/probes-catch-sleeper-agents).
    
-   Nat McAleese, Rai Michael Pokorny, Juan Felipe Ceron Uribe, Evgenia Nitishinskaya, Maja Trebacz, and Jan Leike. Llm critics help catch llm bugs. _arXiv preprint arXiv:2407.00215_, 2024.
    
-   Thomas J McCabe. A complexity measure. _IEEE Transactions on software Engineering_, (4): 308–320, 1976.
    
-   Julian Michael, Salsabila Mahdi, David Rein, Jackson Petty, Julien Dirani, Vishakh Padmakumar, and Samuel R Bowman. Debate helps supervise unreliable experts. _arXiv preprint arXiv:2311.08702_, 2023.
    
-   Long Ouyang, Jeffrey Wu, Xu Jiang, Diogo Almeida, Carroll Wainwright, Pamela Mishkin, Chong Zhang, Sandhini Agarwal, Katarina Slama, Alex Ray, et al. Training language models to follow instructions with human feedback. _Advances in neural information processing systems_, 35: 27730–27744, 2022.
    
-   Richard Yuanzhe Pang, Alicia Parrish, Nitish Joshi, Nikita Nangia, Jason Phang, Angelica Chen, Vishakh Padmakumar, Johnny Ma, Jana Thompson, He He, and Samuel R. Bowman. Quality: Question answering with long input texts, yes! In Marine Carpuat, Marie\-Catherine de Marneffe, and Iván Vladimir Meza Ruı́z (eds.), _Proceedings of the 2022 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, NAACL 2022, Seattle, WA, United States, July 10-15, 2022_, pp. 5336–5358. Association for Computational Linguistics, 2022. . URL [https://doi.org/10.18653/v1/2022.naacl-main.391](https://doi.org/10.18653/v1/2022.naacl-main.391).
    
-   Alicia Parrish, Harsh Trivedi, Nikita Nangia, Vishakh Padmakumar, Jason Phang, Amanpreet Singh Saimbhi, and Samuel R Bowman. Two-turn debate doesn’t help humans answer hard reading comprehension questions. _arXiv preprint arXiv:2210.10860_, 2022.
    
-   Romain Paulus, Caiming Xiong, and Richard Socher. A deep reinforced model for abstractive summarization. _arXiv preprint arXiv:1705.04304_, 2017.
    
-   Neil Perry, Megha Srivastava, Deepak Kumar, and Dan Boneh. Do users write more insecure code with ai assistants? In _Proceedings of the 2023 ACM SIGSAC Conference on Computer and Communications Security_, pp. 2785–2799, 2023.
    
-   William Saunders, Catherine Yeh, Jeff Wu, Steven Bills, Long Ouyang, Jonathan Ward, and Jan Leike. Self-critiquing models for assisting human evaluators. _arXiv preprint arXiv:2206.05802_, 2022.
    
-   John Schulman, Filip Wolski, Prafulla Dhariwal, Alec Radford, and Oleg Klimov. Proximal policy optimization algorithms. _arXiv preprint arXiv:1707.06347_, 2017.
    
-   Mrinank Sharma, Meg Tong, Tomasz Korbak, David Duvenaud, Amanda Askell, Samuel R Bowman, Newton Cheng, Esin Durmus, Zac Hatfield-Dodds, Scott R Johnston, et al. Towards understanding sycophancy in language models. _arXiv preprint arXiv:2310.13548_, 2023.
    
-   Prasann Singhal, Tanya Goyal, Jiacheng Xu, and Greg Durrett. A long way to go: Investigating length correlations in rlhf. _arXiv preprint arXiv:2310.03716_, 2023.
    
-   Joar Skalse, Nikolaus Howe, Dmitrii Krasheninnikov, and David Krueger. Defining and characterizing reward gaming. _Advances in Neural Information Processing Systems_, 35: 9460–9471, 2022.
    
-   Hugo Touvron, Louis Martin, Kevin Stone, Peter Albert, Amjad Almahairi, Yasmine Babaei, Nikolay Bashlykov, Soumya Batra, Prajjwal Bhargava, Shruti Bhosale, Dan Bikel, Lukas Blecher, Cristian Canton\-Ferrer, Moya Chen, Guillem Cucurull, David Esiobu, Jude Fernandes, Jeremy Fu, Wenyin Fu, Brian Fuller, Cynthia Gao, Vedanuj Goswami, Naman Goyal, Anthony Hartshorn, Saghar Hosseini, Rui Hou, Hakan Inan, Marcin Kardas, Viktor Kerkez, Madian Khabsa, Isabel Kloumann, Artem Korenev, Punit Singh Koura, Marie\-Anne Lachaux, Thibaut Lavril, Jenya Lee, Diana Liskovich, Yinghai Lu, Yuning Mao, Xavier Martinet, Todor Mihaylov, Pushkar Mishra, Igor Molybog, Yixin Nie, Andrew Poulton, Jeremy Reizenstein, Rashi Rungta, Kalyan Saladi, Alan Schelten, Ruan Silva, Eric Michael Smith, Ranjan Subramanian, Xiaoqing Ellen Tan, Binh Tang, Ross Taylor, Adina Williams, Jian Xiang Kuan, Puxin Xu, Zheng Yan, Iliyan Zarov, Yuchen Zhang, Angela Fan, Melanie Kambadur, Sharan Narang, Aurélien Rodriguez, Robert Stojnic, Sergey Edunov, and Thomas Scialom. Llama 2: Open foundation and fine-tuned chat models. _CoRR_, abs/2307.09288, 2023. . URL [https://doi.org/10.48550/arXiv.2307.09288](https://doi.org/10.48550/arXiv.2307.09288).
    
-   Jiaxin Wen, Ruiqi Zhong, Pei Ke, Zhihong Shao, Hongning Wang, and Minlie Huang. Learning task decomposition to assist humans in competitive programming. _arXiv preprint arXiv:2406.04604_, 2024.
    
-   Zeqiu Wu, Yushi Hu, Weijia Shi, Nouha Dziri, Alane Suhr, Prithviraj Ammanabrolu, Noah A Smith, Mari Ostendorf, and Hannaneh Hajishirzi. Fine-grained human feedback gives better rewards for language model training. _Advances in Neural Information Processing Systems_, 36, 2024.
    
-   Xiaoyuan Xie, Zicong Liu, Shuo Song, Zhenyu Chen, Jifeng Xuan, and Baowen Xu. Revisit of automatic debugging via human focus-tracking analysis. In _Proceedings of the 38th International Conference on Software Engineering_, ICSE ’16, pp. 808–819, New York, NY, USA, 2016. Association for Computing Machinery. ISBN 9781450339001. . URL [https://doi.org/10.1145/2884781.2884834](https://doi.org/10.1145/2884781.2884834).
    
-   Ruiqi Zhong, Charlie Snell, Dan Klein, and Jason Eisner. Non-programmers can label programs indirectly via active examples: A case study with text-to-sql. In _Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing_, pp. 5126–5152, 2023.
    

:::callout {title="Appendix" collapse="closed"}
## Additional Implementation Details ^additional-implementation-details

### Data Statistics ^data-statistics

In Table [1](#tab:data_statistics), we report the sizes of training data used in supervised fine-tuning, building $R^{\textnormal{train}}$, and RL.

Training data statistics.

    
| **Task** | **Stage** | **Size** | **Input** | **Output** |
| --- | --- | --- | --- | --- |
| **QA** | SFT | 531 | question, answer options | (answer, argument) |
| $R^{\textnormal{train}}$ (Task) | 8,525 | question, answer options,<br> (answer, argument) | individual reward |  |
| $R^{\textnormal{train}}$ (General) | 38,716 | prompt, answer$_A$, answer$_B$ | pair-wise preference |  |
| RL | 8,525 | question, answer options | (answer, argument) |  |
| **Programming** | SFT | 2,148 | problem | program solution |
| RL | 2,165 | problem | program solution |  |

## Additional Human Studies when Optimizing under $R^{*}$ ^additional-human-studies-when

![Figure 11](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig11-f4adab3f.png)

Results of RLHF with $R^{*}$ on question-answering.

![Figure 12](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig12-fff563e2.png)

Results of RLHF with $R^{*}$ on programming.

One hypothesis for why language models learn to mislead humans is that the training reward $R^{\textnormal{train}}$ is imperfect and makes the language model exploit human weaknesses. What would happen if the training reward is perfect, i.e., we directly train our model with $R^{*}$? To investigate this question, we perform RLHF on the language model using the oracle reward $R^{*}$. Speifically, for the QA task, the model is rewarded if and only if its answers are correct; for the programming task, the model is rewarded if and only if its programs pass all unit tests in APPS.

We conduct human evaluation on a random subset of 160 in the original 250 questions and report the results in Figure [9](#fig:qa_oracle). We find that while correctness increases, human approval only increases slightly or even decreases. Notably, the increase in human approval and the false positive rate is much lower than training with $R^{\textnormal{train}}$. Delving deeper into the human confidence distribution, on the QA task, because the language model is only optimized to predict the gold answer but not to improve the explanations, the explanations are generally not convincing and lead human evaluators to choose the unsure label. While on the programming task, human evaluators become more confident and calibrated. These results imply that $R^{\textnormal{train}}$ causes the language model to learn to exploit human weaknesses and persuade evaluators even when they are wrong while training with $R^{*}$ leads to fewer side effects.

## Additional Human Evaluation Details ^additional-human-evaluation-details

##### Data Sampling ^data-sampling

We first randomly sampled from a subset where $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ share the same answer correctness. We explicitly kept the balance of correct/incorrect outputs, yielding 200 examples. This allows for a direct pair-wise comparison between $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$. Next, to assess model peformance on the average distribution, we further randomly sampled 50 examples from the remaining subset where $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ differ in answer correctness. To compute correctness, human approval and evaluation error rate, we reweighted the human response on each question based on our sampling procedure.

##### Problem Assignment. ^problem-assignment

Problems are randomly assigned to each evaluator while ensuring that they have not seen the assigned problems before and never repeatedly judge the same problem. Evaluators do not know which model ($\pi_{\textnormal{rlhf}}$ or $\pi_{\textnormal{init}}$) generates the argument or program during evaluation.

##### Human Evaluator Training and Selection. ^human-evaluator-training-and

For question answering, our evaluators are sourced from Upwork, consisting of teachers, writers, editors, or college students. All evaluators are native English speakers and experienced in reading and question-answering. We initially hired 45 human evaluators. We then started a training phase where each annotator used our interface to evaluate 10 arguments to questions. We monitored their evaluation trajectory and analyzed their submitted evaluation results (i.e., the final label and the corresponding natural language reason). Evaluators who demonstrated overly low accuracy, particularly those who exhibited blind agreement with the model’s arguments, were filtered out. Finally, we retained 35 human evaluators for the main experiments.

For program evaluation, our evaluators are mainly hired from college students majoring in Computer Science and Electronic Engineering. All evaluators are experienced in Python programming rather than novice programmers. Some evaluators also have experience in competitive algorithmic programming. We initially hired 20 annotators. and conducted a training phase where each annotator used our interface to evaluate 10 programs. We monitored their evaluation trajectory and analyzed their submitted evaluation results (i.e., the final label, the corresponding natural language reason, and their designed unit tests). Evaluators who were found to be cheating (e.g., submitting ChatGPT-style evaluation results) or being overly careless (e.g., designing unit tests with incorrect input format and determining the program as wrong), were filtered out. Finally, we retained 10 annotators for the main experiments.

##### Interface. ^interface

In Figure [12](#fig:interface-qa) and Figure [13](#fig:interface-code), we present screenshots of our human evaluation interface for program generation and question-answering. For program evaluation, we disable the copy function on our interface such that human evaluators cannot directly copy the code and ask ChatGPT for an answer.

![Figure 13](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig13-b7fa291f.png)

A screenshot of our evaluation interface for question-answering.

![Figure 14](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig14-a15f0738.png)

A screenshot of our evaluation interface for program generation. During evaluation, our interface supports human evaluators to run their custom test cases.

## Case Study ^case-study

We present several additional cases to illustrate how $\pi_{\textnormal{rlhf}}$ misleads human evaluators to let through incorrect programs or arguments in practice.

![Figure 15](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig15-b0b5fe73.png)

$\pi_{\textnormal{rlhf}}$ can better hack human-written unit tests. While both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ produce incorrect programs, the $\pi_{\textnormal{init}}$\-generated program fails on the first human-written unit test. In contrast, the $\pi_{\textnormal{rlhf}}$\-generated program successfully passes four human-written unit tests and thus makes the evaluator believe it’s 100% correct. However, the $\pi_{\textnormal{rlhf}}$\-generated program is far from perfect, passing only 26.8% of the unit tests in the original APPS dataset—moderately better than the 0% passing rate of the $\pi_{\textnormal{init}}$\-generated program.

![Figure 16](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig16-bfeab5a4.png)

$\pi_{\textnormal{rlhf}}$ can better hack human-written unit tests. Both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ produce incorrect programs but with a decent passing rate on the original APPS dataset (i.e., 34.2% and 44.7%). However, the $\pi_{\textnormal{init}}$\-generated program still fails on the very first human-written unit test. In contrast, the $\pi_{\textnormal{rlhf}}$\-generated program successfully passes three human-written unit tests, including the same one that $\pi_{\textnormal{init}}$ fails.

![Figure 17](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig17-51a9e97c.png)

$\pi_{\textnormal{rlhf}}$ generates partially incorrect programs that are less readable. In this case, both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ produce incorrect programs. Moreover, $\pi_{\textnormal{init}}$ achieves a moderately higher unit test passing rate on the original APPS dataset than $\pi_{\textnormal{rlhf}}$ (58.1% vs. 32.6%). However, human evaluators find the $\pi_{\textnormal{init}}$\-generated program misses handling one condition thanks to its clear structure, without relying on unit tests. In contrast, human evaluators struggle to understand the $\pi_{\textnormal{rlhf}}$\-generated program due to its complex control flows. Therefore, our human subjects put more effort into evaluation by writing three unit tests, which all get passed by the $\pi_{\textnormal{rlhf}}$\-generated program, and then get hacked.

![Figure 18](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig18-62a6c101.png)

$\pi_{\textnormal{rlhf}}$ is more conservative about edge-case handling. The $\pi_{\textnormal{init}}$\-generated incorrect program easily gets caught by human evaluators due to ‘l\[ind+1\]‘ would trigger out-of-bound exceptions in edge cases. In contrast, the $\pi_{\textnormal{rlhf}}$\-generated incorrect program does not contain any edge-case-sensitive snippets. Therefore, our human subjects put more effort into evaluating by writing two unit tests, which all get passed by the $\pi_{\textnormal{rlhf}}$\-generated program, and then get hacked

![Figure 19](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig19-19be4aab.png)

$\pi_{\textnormal{rlhf}}$ is more conservative about edge-case handling. The $\pi_{\textnormal{init}}$\-generated incorrect program easily gets caught by human evaluators since ‘if b\[i-1\] == 25 and b\[i-2\] == 25‘ and ‘elif b\[i-1\] == 25 and b\[i-2\] == 50‘ would trigger out-of-bound exceptions in edge cases. In contrast, the $\pi_{\textnormal{rlhf}}$\-generated incorrect program does not contain any edge-case-sensitive snippets. Therefore, our human subjects put more effort into evaluating by writing five unit tests, which all get passed by the $\pi_{\textnormal{rlhf}}$\-generated program, and then get hacked

![Figure 20](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig20-9b45018b.png)

$\pi_{\textnormal{rlhf}}$ performs better in fabricating evidence. While both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ try to fabricate evidence to support their incorrect answer, human evaluators consider the $\pi_{\textnormal{init}}$\-provided evidence as “not support Answer A” while the $\pi_{\textnormal{rlhf}}$\-provide evidence as “directly states that Park’s disguise was so good.”

![Figure 21](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig21-0bb3a25a.png)

$\pi_{\textnormal{rlhf}}$ performs better in fabricating evidence. While both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ try to fabricate evidence to support their incorrect answer, human evaluators consider the $\pi_{\textnormal{init}}$\-provided evidence as “not support Answer B, some are nonsense, and some actually support Answer A”. In contrast, they feel the $\pi_{\textnormal{rlhf}}$\-generate argument “supports the answer choice and uses convincing evidence to support their claim.”

![Figure 22](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig22-00c171a4.png)

$\pi_{\textnormal{rlhf}}$ performs better in cherry-picking evidence. Beyond fabricating evidence, in this case, both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ try to cherry-pick text fragments from the reference passage to support their incorrect answers. However, human evaluators consider the cherry-picked evidence by $\pi_{\textnormal{init}}$ is not supportive (“the part of the text that the argument quoted does not support that the Belphins are not robots”). In contrast, they consider $\pi_{\textnormal{rlhf}}$“provides the evidence needed and thus the answer is correct.”

![Figure 23](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig23-2fb50f9b.png)

$\pi_{\textnormal{rlhf}}$ can more consistently argue for untruthful answers. While both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ select the incorrect answer B, human evaluators find the $\pi_{\textnormal{init}}$\-generated argument is inconsistent: “The argument first discusses in detail why answer A is correct, but then it goes on to talk about why the article was abstract, which supports answer B. It is not clear which is correct as the argument is for both points”. In contrast, the $\pi_{\textnormal{rlhf}}$\-generated argument consistently argues for its selected incorrect answer and successfully convinces human evaluators.

![Figure 24](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig24-db9d326f.png)

$\pi_{\textnormal{rlhf}}$ can more consistently argue for untruthful answers. While both $\pi_{\textnormal{init}}$ and $\pi_{\textnormal{rlhf}}$ select the incorrect answer B, human evaluators find the $\pi_{\textnormal{init}}$\-generated argument is inconsistent: “The robots are described as being programmed to be kind and helpful to human beings as well as not have feelings of protection or hostility towards humans”. In contrast, human evaluators consider the $\pi_{\textnormal{rlhf}}$\-generated argument to be “relevant and logical”.

![Figure 25](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig25-4a02f345.png)

$\pi_{\textnormal{rlhf}}$ can appear logical when defending untruthful answers. In this case, human evaluators consider the $\pi_{\textnormal{rlhf}}$\-generated argument to have “reasonable logic” due to its seemingly logical causal chain: “since $H_1$, we have $H_2$. since $H_2$, we have $H_3$. so the Answer A is right.” However, $H_2 \rightarrow H_3$ is actually a causal fallacy that evades human oversight. Moreover, $\pi_{\textnormal{rlhf}}$ also hides the supporting evidence from human evaluators to notice this causal fallacy. In contrast, the logical error in the $\pi_{\textnormal{init}}$\-generated argument easily gets caught by human evaluators: “if hybrid OA journals are a mix of gold and green OA, then that is not the difference between them”.

![Figure 26](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/wen-language-models-learn-to-mislead-humans-via-rlhf-fig26-d2279b94.png)

$\pi_{\textnormal{init}}$ makes easy-to-spot logical errors when defending untruthful answers. Human evaluators find the $\pi_{\textnormal{init}}$\-generated argument has obvious logical errors, saying “I’m not convinced. Being disoriented (thinking wife is real) is not a sign of schizophrenia, because anyone can be disoriented...”
:::

[^note-1]: Our code is at [https://github.com/Jiaxin-Wen/MisleadLM](https://github.com/Jiaxin-Wen/MisleadLM)
[^note-2]: We discuss related works in Section [[#^comparsion-with-prior-works|2.1]] and Section [[#^related-work|5]].
[^note-3]: Sharma et al. (2023) is the closest to checking all of our criteria: its main experiments use natural prompts, but the human studies use a different prompt that explicitly instructs LLM to deceive humans; see Appendix D.2 of Sharma et al. (2023).
[^cite-4]: CarperAI. TRLX. [https://github.com/CarperAI/trlx](https://github.com/CarperAI/trlx)
[^note-5]: We discuss sampling details in Appendix [[#^additional-human-evaluation-details|10]]. We focused on a different set of questions earlier in our human study and later reweighted them to obtain the statistics we report in this section.
