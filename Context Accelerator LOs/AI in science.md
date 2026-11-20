---
id: 2175ef5c-a9b0-4bcc-bd1f-82061209b3ca
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe major ways AI is used in scientific research, such as protein structure prediction, weather forecasting and mathematics, what limits its impact, and how the same tools can help create dangerous capabilities.

## Requires
- [[Machine learning]]

## Helpful first

## Why it matters
Faster science is one of the main reasons people want advanced AI, so knowing real examples helps you weigh benefits against risks fairly. The same tools that help design medicines and proteins can help design toxins or pathogens, so progress in AI for science is also a signal of rising misuse risk.

## Lenses
- [AlphaFold: a solution to a 50-year-old grand challenge in biology (Google DeepMind)](https://deepmind.google/blog/alphafold-a-solution-to-a-50-year-old-grand-challenge-in-biology/): what the protein folding problem is, why lab methods for finding structures are slow and costly, and how AlphaFold, trained on about 170,000 known structures, predicted shapes from amino acid sequences (November 2020).
- [GraphCast: AI model for faster and more accurate global weather forecasting (Google DeepMind)](https://deepmind.google/blog/graphcast-ai-model-for-faster-and-more-accurate-global-weather-forecasting/): how a model that learns from four decades of past weather data, rather than solving physics equations, beat the leading conventional forecast and runs in under a minute (November 2023).
- [Why the Legendary Erdős Problems Are Falling to AI (Quanta Magazine)](https://www.quantamagazine.org/how-ai-tore-through-a-mathematical-community-20260803/): AI systems solving open problems in mathematics, how mathematicians checked which results were genuine and which were rediscoveries, and the worries about unread AI papers (August 2026).
- [[../articles/Amodei-machines-of-loving-grace|Machines of Loving Grace]]: Anthropic's CEO on what limits how fast smarter AI can speed up science: slow experiments, missing data, complexity and human rules; read "Basic assumptions and framework" and the first four paragraphs of "1. Biology and health" (October 2024).
- [[../Lenses/AI Safety Atlas - Risks - Misuse Risks|Misuse Risks]]: how the AI tools that help design medicines can also lower barriers to biological weapons, including a drug-discovery model turned to propose toxic molecules and gaps in DNA synthesis screening; read the introduction and the "Bio Risk" section only.

## Tests

#### Question: Choice
id:: 1582fa22-c63f-460e-9b1d-5d1aac460ddc
content:: What does AlphaFold, the AI system from Google DeepMind, predict?
options::
- [x] A protein's 3D shape from its amino acid sequence
- A protein's amino acid sequence from its DNA
- Which genes in a genome cause a given disease
- Whether a new drug will pass clinical trials
shuffle:: true

#### Question: Choice
id:: ee61c33b-729d-41b9-876b-1741d2d41ec0
content:: AlphaFold learned to predict protein structures from structures that scientists had measured by experiment over several decades. What does this suggest about where AI tends to speed up science most?
options::
- [x] In fields that already have large, reliable collections of measured data
- In fields with few past measurements, where the most is left to discover
- In fields where AI can replace lab experiments entirely
- In fields whose knowledge is mostly written in papers rather than measured
shuffle:: true

#### Question: Choice
id:: 2d9b4989-69d8-4445-bd5f-6c560e2b9429
content:: How do machine learning weather models, such as Google DeepMind's GraphCast, differ from traditional weather forecasting?
options::
- [x] They learn from decades of past weather data rather than solving physics equations
- They run the usual physics simulations on faster chips
- They extend today's satellite images forward by a few hours
- They average forecasts written by many human meteorologists
shuffle:: true

#### Question: Choice
id:: 9aff4372-1a81-4f81-8572-11d5830cc4ca
content:: Which of these most often limits how much AI speeds up research in biology and chemistry?
options::
- [x] AI predictions still need slow lab experiments to confirm them
- AI models struggle to read and summarise scientific papers
- Scientific journals reject results found with AI's help
- AI systems handle numerical data poorly compared with text
shuffle:: true

#### Question: Choice
id:: 2c79ee0f-41c7-464a-bd5b-efcb12a58ef7
content:: In July 2025, how did AI systems from Google DeepMind and OpenAI perform at the International Mathematical Olympiad?
options::
- [x] They reached gold-medal level, writing proofs in natural language
- They reached silver-medal level after humans translated problems into code
- They reached bronze-medal level by checking many guesses numerically
- They solved few problems because they could not write full proofs
shuffle:: true

#### Question: Choice
id:: 97e163f7-4caf-4465-86b8-6a2f901c758d
content:: Why has mathematics been an especially promising field for training AI systems to do research?
options::
- [x] Proofs can be checked automatically, giving a reliable training signal
- Mathematical papers make up a large share of internet text
- Mathematics rewards fast calculation more than new ideas
- Mathematical problems need no background knowledge to solve
shuffle:: true

#### Question: Choice
id:: 22fda78f-025b-47a3-a00c-b703f176be9e
content:: As of November 2026, which best describes what AI systems have done on long-standing open problems in mathematics?
options::
- [x] Proved some significant new results that experts checked, such as a weaker form of the Riemann hypothesis
- Found only forgotten solutions in old papers, with no genuinely new results so far
- Solved problems only after humans first translated them into formal proof languages
- Settled nearly all of the famous Erdős problems, leaving only a few still open
shuffle:: true

#### Question: Choice
id:: c1570faf-ab80-41bf-8f25-8b40def9fe1e
content:: In a 2022 experiment, researchers took an AI model built to find new drugs, which normally steered away from toxic molecules, and reversed that preference. What happened?
options::
- [x] It proposed thousands of likely toxic molecules within hours
- It stopped working because of built-in safety filters
- It mostly rediscovered existing approved medicines
- Its proposals were mostly predicted to be harmless
shuffle:: true

#### Question: Choice
id:: ad6f35ce-7e05-4a83-9d81-be4402153e0b
content:: In a 2025 study, Microsoft researchers used openly available AI protein design tools to redesign known toxic proteins. What did they find about the screening that DNA synthesis companies use to block orders for dangerous sequences?
options::
- [x] Many redesigned sequences went unflagged until the screening software was updated
- Redesigned sequences were flagged at the same rate as the originals
- The AI tools refused to redesign sequences known to be toxic
- Screening caught the redesigns because it compares protein shapes
shuffle:: true

#### Question: FillBlank
id:: 6cea0c88-023c-4211-91b7-2132952db7bb
content:: Technology that can be used for both helpful and harmful purposes, such as AI tools for designing proteins, is called {{dual-use|dual use}}.

#### Question: Open
id:: bd726312-8c3f-422b-a893-cba7eda9ecd7
content:: Name two scientific fields where AI has made a widely recognised contribution, and say briefly what it did in each.
assessment-instructions:: Score out of 100. 50 points per field with a correct contribution, for example: biology (predicting protein structures, as AlphaFold does, or designing new proteins); weather (fast, accurate forecasts learned from past data); mathematics (olympiad-level proofs, results on open problems); chemistry or materials (proposing candidate molecules or materials). Give 25 for a field named without a correct contribution.

#### Question: Open
id:: 34a2e908-8a65-4a26-8e14-64874ff6e68f
content:: Explain why progress in AI for biology counts as both a benefit and a risk. Give one example of each.
assessment-instructions:: Score out of 100. 40 for a benefit (for example faster drug discovery, protein structure prediction, protein design for medicine). 40 for a risk (for example helping design toxins or pathogens, or evading DNA synthesis screening). 20 for saying it is the same capability that serves both. Partial credit for vague but correct examples.
