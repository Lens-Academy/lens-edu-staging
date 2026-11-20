---
id: 03955e47-6476-40a9-881a-64d30f453001
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how better algorithms let AI developers reach the same capability with less compute, say roughly how fast this has happened, and tell steady efficiency gains apart from rare paradigm leaps such as the transformer.

## Requires
- [[Compute]]

## Helpful first

## Why it matters
Forecasts and policies that track only chips and training compute miss a large part of AI progress. Because better algorithms keep cutting the compute a capability needs, progress can continue if compute growth slows, capabilities get cheaper for more groups to reach, and compute thresholds in regulation become a weaker guide to what a model can do.

## Lenses
- [On DeepSeek and Export Controls (Dario Amodei)](https://darioamodei.com/post/on-deepseek-and-export-controls): Anthropic's CEO separates steady "curve-shifting" efficiency gains (his guess: ~4x a year) from rare paradigm shifts like reasoning models, and explains why DeepSeek-V3's ~$6M figure is not the full cost of developing it. Read "Three Dynamics of AI Development" and "DeepSeek's Models"; the rest argues for export controls (January 2025).
- [Algorithmic Progress in Language Models (Epoch AI)](https://epoch.ai/blog/algorithmic-progress-in-language-models): the main estimate for 2012–2023: the compute needed for a given performance halved about every 8 months, more compute still drove most of the gains, and the transformer was worth about two years of progress (March 2024).
- [The Least Understood Driver of AI Progress (Epoch AI)](https://epoch.ai/gradient-updates/the-least-understood-driver-of-ai-progress): an Epoch researcher's newer and more sceptical look. His best guess is ~10x a year, with very wide uncertainty; much of the gain comes from data and from changes that only pay off at scale, and compute bottlenecks may limit how far AI-automated research can speed things up. Read sections I, II and IV (February 2026).
- [LLM Inference Prices Have Fallen Rapidly but Unequally Across Tasks (Epoch AI)](https://epoch.ai/data-insights/llm-inference-price-trends): the price of matching a fixed level of performance, such as GPT-4's on science questions, fell from about 9x to 900x a year depending on the task (March 2025).

## Tests

#### Question: Choice
id:: 8ab93f32-f42b-428f-bbad-241e3fa91f15
content:: In AI, what does "algorithmic progress" usually measure?
options::
- [x] How much less compute is needed to reach the same performance
- How much faster AI chips perform calculations each year
- How many more parameters frontier models have each year
- How quickly new records are set on AI benchmarks
shuffle:: true

#### Question: FillBlank
id:: 5ca06e21-e1e9-45cb-ae88-f2ae47130978
content:: A 2024 Epoch AI study estimated that, for language models between 2012 and 2023, the compute needed to reach a given performance level halved roughly every {{8|eight}} months.

#### Question: Choice
id:: e3cd67f4-ed75-4f62-b842-53234019d362
content:: A lab trains a new model with 4 times the physical compute of its previous model. Over the same period, better algorithms mean each unit of compute achieves what 3 units did before. Roughly how much more effective compute does the new model have?
options::
- [x] About 12 times
- About 7 times
- About 4 times
- About 3 times
shuffle:: true

#### Question: Choice
id:: 3ba55718-ccd8-4bc4-8d79-c7348af45950
content:: Suppose the physical compute used to train frontier AI models stopped growing, but algorithmic progress continued at its past rate. What would happen to the best AI capabilities?
options::
- [x] They would keep improving, but more slowly than before
- They would stop improving until compute growth resumed
- They would improve faster, as algorithm gains replace compute gains
- They would decline as older training methods became obsolete
shuffle:: true

#### Question: Choice
id:: 5bde58a6-e284-4eaf-9abb-88422a559692
content:: Some AI rules add requirements only for models trained with more than a set amount of compute, such as 10^26 operations. How does continued algorithmic progress affect such a rule over time?
options::
- [x] Models trained below the threshold can match capabilities that once needed more
- Regulators must raise the threshold to keep catching the same capabilities
- Nothing changes, since the threshold measures compute rather than capability
- Capable models become easier for the threshold to catch
shuffle:: true

#### Question: Choice
id:: bba4a220-28ee-4986-9015-7200fbf9cac3
content:: An AI capability first required the largest training run of a leading lab. If algorithmic efficiency keeps improving at its past rate, what is most likely a few years later?
options::
- [x] Smaller groups can reach the capability with far less compute
- The capability still needs a training run of the same size
- The capability needs more compute, because test standards rise
- Only the first lab can reproduce it, because its methods stay secret
shuffle:: true

#### Question: Choice
id:: 4482b8d5-2c33-4b99-801a-8ca1356aeca4
content:: Which of these is the best example of a paradigm leap in AI algorithms, rather than a steady incremental gain?
options::
- [x] The transformer architecture replacing recurrent networks for language
- A new learning-rate schedule that trains models slightly faster
- Removing duplicate web pages from the training data
- An optimizer tweak that cuts training time by a few percent
shuffle:: true

#### Question: Choice
id:: dccd8982-e162-4488-8bce-9737af5db99d
content:: A 2024 Epoch AI study of language models from 2012 to 2023 compared how much more training compute and better algorithms each added to performance. What did it find?
options::
- [x] More compute drove most gains; better algorithms a smaller share
- Better algorithms drove most gains; more compute a smaller share
- More compute and better algorithms contributed roughly equal shares
- Better algorithms drove nearly all gains; more compute added little
shuffle:: true

#### Question: Choice
id:: 60bf1a85-949d-463b-8864-2ac033de1446
content:: Between 2023 and 2025, how did the price of using a language model at a fixed level of performance, such as GPT-4's level at its 2023 launch, change?
options::
- [x] It fell many times over each year
- It fell by about a tenth each year
- It stayed roughly the same
- It rose as demand for AI chips grew
shuffle:: true

#### Question: Open
id:: d940036a-78b3-45a1-91da-d617aacd3fb8
content:: Why are paradigm leaps in AI algorithms harder to forecast than steady efficiency gains?
assessment-instructions:: Score out of 100. 100 for saying that steady gains follow a fairly regular trend that can be extended, while paradigm leaps are rare and irregular, so their timing and size can't be read from a trend. 50 for only one half (e.g. "leaps are rare" or "leaps are unpredictable") without the contrast with a measurable trend.

#### Question: Open
id:: ed9069c0-d59c-4145-a734-db34b8e6db04
content:: If AI systems could do much of the work of AI researchers, why might this speed up algorithmic progress more than it speeds up growth in training compute?
assessment-instructions:: Score out of 100. 100 for saying that algorithmic progress comes mainly from research work (ideas, experiments), which AI copies could supply quickly and in large numbers, while compute growth needs physical chips, power and data centers that take time and money to build. 50 for naming only one side.

#### Question: Open
id:: 8242631b-9c3d-44ff-8ed0-79de88d2039b
content:: In December 2024 DeepSeek reported that the final training run of its V3 model cost about $6 million, far below estimates for similar US models. Give one reason this figure understates what it cost to develop the model.
assessment-instructions:: Score out of 100. 100 for any one of: it leaves out earlier research and experimental training runs; it leaves out buying or owning the chips and data centers; it leaves out staff salaries; it leaves out data costs. 0 for answers saying the figure was simply false without a reason.
