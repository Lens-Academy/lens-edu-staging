---
title: "Current Capabilities"
author:
  - "Markov Grey"
  - "Charbel-Raphaël Segerie"
source_url: "https://ai-safety-atlas.com/chapters/v1/capabilities/current-capabilities/"
published: 2026-06-18
created: 2026-06-18
accessed: 2026-06-18
description:
tags:
  - "article-importer"
---

AIs can increasingly write, see, code and control robots in ways that often beat humans. They demonstrate surprising skills like reasoning and tool use that challenge previous assumptions about what AI could achieve.

---

**AI models can write, reason, code, generate media, and control robots—often matching or surpassing expert human performance on specific tasks.** In this first section, we’ll try to give you a sense of what AI is actually capable of doing as of late 2025. Numbers and graphs don't really make these capabilities tangible, so we will try to include as many videos, images, and examples to really help you get a sense of where AI currently stands. But in case you are interested, we also mention benchmark scores that measure progress quantitatively.

**The trajectory matters more than a snapshot.** This section can serve both as a quick history and as a snapshot of current capabilities. As you read through it, try to keep in mind how quickly we got here. Language generation went from coherent paragraphs to research assistants in a few years. Image generation went from laughable to professional-grade in a decade. Video generation seems to be following a similar path compressed into three years.

If you’re already familiar with AI or machine learning, some of these stories might be review for you, but hopefully everyone who reads will be able to take away at least one new thing from this section. 

## Games

**Game-playing AI is already at the superhuman level for many games.** Comparing AI and humans at games has been a common theme through the last few decades with AI making continuous progress. IBM’s Deep blue defeated chess grandmaster in 1997 ([IBM, 2026](https://www.ibm.com/history/deep-blue)), IBM’s Watson won overwhelmingly at Jeopardy! in 2011 ([IBM, 2026](https://www.ibm.com/history/watson-jeopardy)), and AlphaGo managed to beat the Go world champion Lee Sedol in 2016 ([DeepMind, 2016](https://www.deepmind.com/research/highlighted-research/alphago)). AlphaGo was a landmark moment, because this is a game with more possible positions than atoms in the observable universe. During game 2, AlphaGo played Move 37, a move that had a 1 in 10,000 chance of being used. Commentators initially thought it was a mistake, instead it was the move that several rounds later led to winning the game. The move demonstrated what many consider to be sparks of genuine creativity that diverged from centuries of human play that the model was trained on.

![Figure 1.2](https://ai-safety-atlas.com/_astro/19f7e74f57d1d23e357f6fe6194d5f4bb64ccb768b00d82efe4a2cb9d628016a.Dh1IrDR6_1M7B4d.webp)

*Figure 1.2: Kasparov, a chess grandmaster, defeated the Chess system DeepBlue in 1996. One year later in 1997 he resigned in the last game of the six-game match after 19 moves, granting the win to Deep Blue ([IBM, 2026](https://www.ibm.com/history/deep-blue)).*

> For the first time in the history of mankind, I saw something similar to an artificial intellect.
> — Garry Kasparov

**AI's superhuman game playing capability extends to video games**. Machine learning techniques on simple Atari games in 2013 ([Mnih et al., 2013](https://arxiv.org/abs/1312.5602)) progressed to OpenAI Five defeating world champions at DOTA 2 in 2019 ([OpenAI, 2019](https://openai.com/research/openai-five-defeats-dota-2-world-champions)). That same year, DeepMind's AlphaStar beat professional esports players at StarCraft II ([Google DeepMind, 2019](https://deepmind.google/discover/blog/alphastar-mastering-the-real-time-strategy-game-starcraft-ii/)). These are games with open ended real time environments, requiring thousands of rapid decisions and long-term planning. By 2020 the MuZero system played Atari games, Go, chess, and shogi without even being told the rules ([Google DeepMind, 2020](https://www.deepmind.com/blog/muzero-mastering-go-chess-shogi-and-atari-without-rules)).[^1] These are AIs that all play and learn autonomously without human intervention. In 2025, game playing AIs have evolved to open-ended environments across a huge variety of games. They carry the abilities learned from one game onto the next improving their performance over time ([Google DeepMind, 2025](https://deepmind.google/blog/sima-2-an-agent-that-plays-reasons-and-learns-with-you-in-virtual-3d-worlds/)).

![Figure 1.3](https://ai-safety-atlas.com/_astro/d5c878f746cb352f5d4d8fcd6ec7c4c3fed92d9654ae42135b38922a36768e32.B6aTBUvE_11FxcT.webp)

*Figure 1.3: The history of going from AlphaGo, which was already superhuman in 2016, to MuZero which was not only superhuman but was trained without any human data, domain knowledge or knowledge of the games rules ([DeepMind, 2020](https://deepmind.google/blog/muzero-mastering-go-chess-shogi-and-atari-without-rules/)).*

**Game playing AI is relatively narrow in what it can do.** Despite this it is extremely impressive because of the strategic planning, pattern recognition, and adversarial thinking it displays. These same reasoning abilities—planning ahead, building strategies, adapting to feedback—that started with game playing now also apply to scientific research, mathematical proofs, and complex real-world problem-solving.

*Figure 1.4: Video showcasing example of the state of game playing AI assistants using the SIMA-2 model in 2025 ([Google DeepMind, 2025](https://deepmind.google/blog/sima-2-an-agent-that-plays-reasons-and-learns-with-you-in-virtual-3d-worlds/)).*

*Figure 1.5: Video showcasing example of the state of game playing AI using the SIMA-2 model in 2025 ([Google DeepMind, 2025](https://deepmind.google/blog/sima-2-an-agent-that-plays-reasons-and-learns-with-you-in-virtual-3d-worlds/)).*

**Planning and Continuous Learning in Minecraft with GPT-4**

AIs can construct long term strategies and play games in open ended dynamic environments. The various Alpha series of models in the 2020s did not use LLMs. But in 2023, Voyager—an AI system powered by GPT-4—demonstrated that a LLM powered system could play Minecraft  ([Wang et al., 2023](https://arxiv.org/abs/2305.16291)). Minecraft, if you are not familiar, provides a sandbox where you must complete tasks in sequence: gather wood, craft basic tools, mine stone, smelt iron, craft better tools, and eventually mine diamonds. This requires planning hundreds of steps ahead and long term strategic planning. Since 2023 we have seen several game playing systems based around LLMs showcasing a variety of capabilities. For example, in strategy games, Meta’s Cicero displayed intricate strategic negotiation and deception skills in natural language for the game Diplomacy ([Bakhtin et al., 2022](https://arxiv.org/abs/2210.05492)).

![Figure 1.6](https://ai-safety-atlas.com/_astro/16749672b7c9c70fda742a9cc720680ab3d146ef44f6ab18ccb1e5201046ec1d.CZbOrR92_1wEti5.webp)

*Figure 1.6: Voyager discovers new Minecraft items and skills continually by self-driven exploration, significantly outperforming the baselines ([Wang et al., 2023](https://arxiv.org/abs/2305.16291)).*

## Text Generation

**Generating text can take language models far beyond simple conversations.** You're probably familiar with ChatGPT. These types of language generation AIs are what we call large language models (LLMs). In 2018, early versions of these LMs could only write a few coherent paragraphs. But over a few short years, they have gotten a lot better. By 2025, GPT-5 gets 92.5% of questions right in domains ranging from highly complex STEM fields, international law, to nutrition and religion (as measured by the MMLU benchmark). Models like Claude by Anthropic, Grok by X, GLM-4.7 by Zhipu AI, and DeepSeek-v3.2 showcased similar levels of performance across various domains ([ArtificialAnalysis, 2025](https://artificialanalysis.ai/evaluations/artificial-analysis-intelligence-index); [EpochAI, 2025](https://epoch.ai/benchmarks/eci)).

![Figure 1.7](https://ai-safety-atlas.com/_astro/7f041e7585531e0510dfccd9484114c688ef7f7468994c4790bc3b6fcdf5b009.CaU0CqZs_t8h9F.webp)

*Figure 1.7: In a few short years, LLMs have gone from being barely useful to being regularly used coding assistants ([AI Digest, 2023](https://theaidigest.org/progress-and-dangers)).*

![Figure 1.8](https://ai-safety-atlas.com/_astro/19a4e4968acd707f823a3f671a2a0ea683b32b1367a09c78560b03604a30cbe2.BrjVHjpk_Z1f7ja1.webp)

*Figure 1.8: Performance on common exams as a percentile compared to human test takers. Notice the large jump from GPT-3.5 to GPT-4 on these tests, often from well below the median human to the very top of the human range ([Aschenbrenner, 2024](https://situational-awareness.ai/from-gpt-4-to-agi/);[ OpenAI, 2023](https://arxiv.org/abs/2303.08774)). The jump from GPT-3 to GPT-4 was in a single year.*

*Interactive figure 1.1: We are seeing an explosion in language models due to their generality, and applicability to a wide range of tasks  ([Giattino et al., 2023](https://ourworldindata.org/grapher/cumulative-number-of-large-scale-ai-models-by-domain)).*

![Figure 1.9](https://ai-safety-atlas.com/_astro/7b876d786dc241f8c78c6bb7fa111ca29d0f42f6dc93662127bc50b391ec1de1.BO3qrNGo_ZHL8HQ.webp)

*Figure 1.9: A list of ‘Nowhere near solved’ [...] problems in AI, from ‘A brief history of AI’, published in January 2021 ([Wooldridge, 2021](https://www.amazon.com/Brief-History-Artificial-Intelligence-Where/dp/1250770742)). They also say: ‘At present, we have no idea how to get computers to do the tasks at the bottom of the list’. But everything in the category ‘Nowhere near solved’ has been solved by GPT-4 ([Bubeck et al., 2023](https://arxiv.org/abs/2303.12712)), except human-level general intelligence.*

Language models have provided a core around which we have seen many impressive capabilities emerge like - scientific research, reasoning, and software development. All of these capabilities stem from the same principle of generating language and gradually refining it.

## Tool Use

**LLMs can intelligently use external tools, dramatically boosting performance.** Language models in 2020 exhibited remarkable abilities to solve new tasks from instructions, but they used to struggle with basic functions like arithmetic. Instead of trying to get a single model to do everything, increasingly LLMs use external tools to achieve both capabilities ([Schick et al., 2023](https://arxiv.org/abs/2302.04761); [Qin et al., 2023](https://arxiv.org/abs/2307.16789)). They recognize when they need a calculator, code interpreter, or up to date information from a search engine—and call these tools appropriately.[^2] Tool use significantly improves model performance; for example, the OpenAI o3 model with external tools outperforms o3 alone by almost 5% on benchmarks like Humanities Last Exam (HLE) ([EpochAI, 2025](https://epoch.ai/gradient-updates/three-issues-undermining-compute-based-ai-policies)). In December 2025, at least 10,000 tool servers are operational, including meta tools like ‘a tool to search for tools’ to help LLMs find the exact one they need for the specific situation ([Anthropic, 2025](https://www.anthropic.com/engineering/advanced-tool-use); [Anthropic, 2025](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation)). This leads to a significant enough boost that companies now report benchmark performance separately - with and without tools.

![Figure 1.10](https://ai-safety-atlas.com/_astro/05faf3da4e72e1b813b3e922f0a38776e5d89ea6ac86587e3d99cfb8705cdf4f.DI-js9ia_Zn2JHg.webp)

*Figure 1.10: A simple example from Toolformer. The model autonomously decides to call different APIs (from top to bottom: a question answering system, a calculator, a machine translation system, and a Wikipedia search engine) to obtain information that is useful for completing a piece of text ([Schick et al., 2023](https://arxiv.org/abs/2302.04761)).*

## Reasoning and Research

**Models now demonstrate multi-step reasoning by working through problems step-by-step.** In addition to using tools, LLMs now show their reasoning, catch their own errors, and backtrack when needed.  In late 2024, OpenAI introduced o1, the first "reasoning" model. These AIs allocate more effort per problem—trading "thinking time" for accuracy. The longer they think, the better their responses tend to get ([OpenAI, 2024](https://openai.com/o1/)). Using these reasoning techniques, both OpenAI and Google DeepMind achieved gold-medal performance at the 2025 International Mathematical Olympiad ([OpenAI, 2025](https://x.com/OpenAI/status/1946594928945148246); [Google DeepMind, 2025](https://deepmind.google/blog/advanced-version-of-gemini-with-deep-think-officially-achieves-gold-medal-standard-at-the-international-mathematical-olympiad/)). On FrontierMath—a test of research-level mathematics—GPT-5.2 solved 41% of tier 1-3 problems ([EpochAI, 2026](https://epoch.ai/frontiermath)).1 In ML terms, ‘thinking time’ is called ‘inference’. It is the act of generating new tokens/words, so increasing thinking time is more formally called inference time scaling. Similar to tool use this also led to such a boost in performance that companies report high thinking time (high compute) results of benchmarks separately than no thinking time (low compute) results.

![Figure 1.11](https://ai-safety-atlas.com/_astro/9693733754e88d2984f79ddd1e8031e18897e2d406b4b2a60bef6590fc7d39c0.Dw3btErf_8WeWa.webp)

*Figure 1.11: A sample of an “easy” tier-1 problem from FrontierMath - an extremely difficult mathematics test created by mathematicians. GPT-5.2 can solve 41% of tier 1-3 problems, and 29% of the even harder tier 4 problems ([EpochAI, 2025](https://epoch.ai/frontiermath/benchmark-problems)).*

**LLMs can help generate and evaluate scientific hypotheses.** Combining techniques like letting AI think for longer, and tools like web-search or specialized AI models, we are starting to see research assistants. As one example, Google introduced AI co-scientist in 2025. The team used it to generate and evaluate proposals for repurposing drugs, identifying drug targets, and explaining antimicrobial resistance in real-world laboratories ([Google DeepMind, 2025](https://arxiv.org/abs/2502.18864)). Others have attempted to build a fully autonomous AI scientist, which generates novel research ideas, writes code, executes experiments, visualizes results, describes its findings by writing a full scientific paper, and then runs a simulated review process for evaluation ([SakanaAI, 2024](https://arxiv.org/abs/2408.06292)).

![Figure 1.12](https://ai-safety-atlas.com/_astro/d68e0611829e33569c8a344a92446eb86c133e05a828c06e3a977e1b7abd0f06.6joHNbB9_1vBHq2.webp)

*Figure 1.12: An example of the Google Co-Scientist. You can see the “thinking time” labelled as test time compute increasing on the left ([Google DeepMind, 2025](https://arxiv.org/abs/2502.18864)). *

**AI is transitioning to an active research collaborator across scientific domains.** Instead of only using language models, companies are also using approaches similar to AlphaZero to create a whole range of specialized models for scientific domains. For example, Demis Hassabis & John Jumper were awarded the nobel prize in chemistry for their work on building AlphaFold ([Google DeepMind, 2024](https://deepmind.google/blog/demis-hassabis-john-jumper-awarded-nobel-prize-in-chemistry/)). This is a model that helped solve the long outstanding protein folding problem ([Google DeepMind, 2022](https://deepmind.google/blog/alphafold-a-solution-to-a-50-year-old-grand-challenge-in-biology/)), and its successors AlphaFold 2 and 3 continue to aid thousands of researchers in biology ([DeepMind, 2024](https://deepmind.google/science/alphafold/)). Similarly, AlphaGenome is helping us better understand human DNA ([Google DeepMind, 2025](https://deepmind.google/blog/alphagenome-ai-for-better-understanding-the-genome/)). AlphaEvolve is helping generate faster algorithms for machine learning ([Google DeepMind, 2025](https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/)), and AlphaChip helps design the semiconductors that run algorithms ([Google DeepMind, 2024](https://deepmind.google/blog/how-alphachip-transformed-computer-chip-design/)).

![Figure 1.13](https://ai-safety-atlas.com/_astro/84ea667e02f3c43ac9361d83a70bfab4802c02b38b654b820d3159faf2f13893.DNz0hbZJ_ZkbJXI.webp)

*Figure 1.13: Animation showing AlphaGenome taking one million DNA letters as input and predicting diverse molecular properties across different tissues and cell types ([Google DeepMind, 2025](https://deepmind.google/blog/alphagenome-ai-for-better-understanding-the-genome/))*

**Beyond just mathematics and scientific research, AI models are also developing more abstract intellectual skills.** LLMs have some level of metacognition, they can evaluate the validity of their own claims and predict which questions they will be able to answer correctly ([Kadavath, 2022](https://arxiv.org/abs/2207.05221)). They have some knowledge about their own selves and their limitations. Similarly, they display the ability to attribute mental states to themselves and others (theory of mind). This helps in predicting human behaviors and responses ([Kosinski 2023](https://arxiv.org/abs/2302.02083); [Xu et al., 2024](https://arxiv.org/abs/2402.06044)). We are going to talk more about how we concretely define and measure things like intelligence, meta-cognition and so on in later sections.

![Figure 1.14](https://ai-safety-atlas.com/_astro/b1cf0757b9ba033266dc12377f8fc3ae1ac883a023d8f978b4848630e77098f1.DMpdJ6YK_1w4NFP.webp)

*Figure 1.14: An example puzzle from the abstraction and reasoning corpus for AI (ARC-AGI v1). These are designed to be easy for humans, but very hard for AIs. Models are able to solve increasing numbers of such abstract reasoning puzzles, especially with the advent of large reasoning models (LRMs) in 2025 ([ARC-AGI, 2024](https://arcprize.org/arc-agi/1/); [Chollet et. al, 2024](https://arxiv.org/abs/2412.04604)).*

## Software Development

**Coding is evolving from autocomplete to collaborative software development.** LLMs can generate text in any form, and one particular type of text that they are proving to be especially good at is generating code. When paired with reasoning capabilities, and tools LLMs read documentation, edit codebases spanning thousands of files, run tests, debug failures, and iterate until tests pass—with increasingly minimal human guidance. In 2025 systems like Claude Opus 4.5, Gemini 3 Pro, and GPT-5.2 implement features and entire applications increasingly independently ([Anthropic, 2025](https://www.anthropic.com/claude/opus); [Google DeepMind, 2025](https://deepmind.google/models/gemini/); [OpenAI, 2025](https://openai.com/index/introducing-gpt-5-2/)). When tested against real GitHub issues from open-source projects— in 2024 AI systems (Claude 3 Opus) could solve just 15% problems, but by 2025, this had jumped to being able to solve 74% of issues (Tools + Claude 4 Opus) ([SWE bench, 2025](https://www.swebench.com/)).

![Figure 1.15](https://ai-safety-atlas.com/_astro/b24e34c49e9526b15269b528469a19f5b7711cdaeb243ff2122803f7ac98cf66.fVYqCe7S_OOhl.webp)

*Figure 1.15: AI systems now develop themselves. Boris Cherny, creator of Claude Code—Anthropic's AI-powered software development tool—stated in December 2025 that 100% of his contributions to Claude Code over the previous thirty days were written by Claude Code itself ([Cherny, 2025, Twitter](https://x.com/bcherny/status/2004897269674639461)).*

## Vision: Images and Video

**Image generation progressed from unrecognizable noise to photorealistic scenes in under a decade.** In 2014, Generative Adversarial Networks (GANs) produced grainy, low-resolution faces ([Goodfellow et al., 2014](https://arxiv.org/abs/1406.2661)). By 2023, models generated detailed images from complex text prompts. Models like Midjourney v7 create photorealistic scenes nearly indistinguishable from professional photography. Video generation is following a similar trajectory. AI generated videos and DeepFakes are getting increasingly indistinguishable from real videos.

![Figure 1.16](https://ai-safety-atlas.com/_astro/a66b0d14036ba3a3e03a32b57c9ad584686a330cc94f8c78ae030516ab8d40e9.C-r3MyYu_Z2uMveA.webp)

*Figure 1.16: An example of the evolution of image generation. At the top left, starting from GANs (Generative Adversarial Networks) to the bottom right, an image from MidJourney V5.*

![Figure 1.17](https://ai-safety-atlas.com/_astro/f3503b013ebe9dc0111f6a5a45cf3820e5d8b5c7cef95b21f4304b13f6035b80.WuFIFSei_29e2Cr.webp)

*Figure 1.17: Improvements between the V1 of the MidJourney image generation model in early 2022, to the V6 in December 2023. Prompt: high-quality photography of a young Japanese woman smiling, backlighting, natural pale light, film camera, by Rinko Kawauchi, HDR ([Yap, 2024](https://goldpenguin.org/blog/midjourney-v1-to-v6-evolution/)).*

*Figure 1.18: Sample of an AI generated video by OpenAI Sora 2. Prompt: a gymnast flips on a balance beam. Cinematic ([OpenAI, 2025](https://openai.com/index/sora-2/)).*

**Large **Multimodal** Models (LMMs) combine language and image understanding capabilities.** In 2025, multimodal models answer questions about spatial relationships in images, read embedded text in complex scenes, and extract information from charts and diagrams. Image models released in 2025 handle generation and sophisticated editing across modalities. Systems like Gemini 3 Pro Image work text-to-image, image-to-image, and handle complex editing—changing lighting, style, or composition while maintaining coherence ([Google, 2025](https://deepmind.google/models/gemini/pro/)).

![Figure 1.19](https://ai-safety-atlas.com/_astro/8fda241351f997811a5b597c5b4de5b9c318eff2a80cda864d34154113bb077b.CHCjUn3s_2jJNl3.webp)

*Figure 1.19: An infographic containing both images and educational text generated by Google’s Nano Banana pro model. Prompt: Create an infographic that shows how to make elaichi chai  ([Google, 2025](https://blog.google/innovation-and-ai/products/nano-banana-pro/)).*

![Figure 1.20](https://ai-safety-atlas.com/_astro/88aa222a0bb54520d67919c6a03c2ce9d38207b98c18bc995282824bdcb5d81b.BDHpJFc7_1nmnnX.webp)

*Figure 1.20: Example of extending video and image generation to an interactive world. This was generated by DeepMind Genie 3. The bottom left arrows indicate the user interacting with the generated environment ([DeepMind, 2025](https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/)).*

## Robotics

**Both AI and robotics are evolving, with robots giving AI physical embodiment in the real world.** Robotics is combining LLMs and visual models, to create robot control models (e.g. RT-1 or RT-2). These robots can use techniques borrowed from language models—like breaking complex actions into step-by-step plans—to control robot manipulators ([Google DeepMind, 2024](https://deepmind.google/blog/shaping-the-future-of-advanced-robotics/)). They managed to learn behaviors like opening cabinets, operating elevators, and cooking tasks through observing human demonstrations. Robots have demonstrated the ability to perform intricate manipulation: sautéing shrimp, storing heavy pots in cabinets, and rinsing pans ([Fu et al., 2024](https://arxiv.org/abs/2401.02117)).

![Figure 1.21](https://ai-safety-atlas.com/_astro/76a1121100a0da0db15910dc49f1248bbf5ca0be5c4663cf41fc2fea2713102c.KhunXeht_TrQJ5.webp)

*Figure 1.21: SARA-RT-2 model for manipulation tasks. The robot's actions are conditioned on images and text commands ([Google DeepMind, 2024](https://deepmind.google/blog/shaping-the-future-of-advanced-robotics/)).*

**Autonomous robots are moving from research labs into real-world industrial deployment at significant scale.** In 2023, China installed 276,300 industrial robots ([AI Index Report, 2025](https://arxiv.org/abs/2504.07139)). These systems handle welding, parts assembly, materials handling, and quality inspection—tasks requiring precision but not necessarily advanced reasoning.  In addition to industrial robots, warehouse robotics represents one of the most mature deployments—Amazon operates over 1 million robots across its fulfillment network, handling everything from inventory storage to package sorting ([Amazon, 2025](https://www.aboutamazon.com/news/operations/amazon-robotics-robots-fulfillment-center)). Robots in warehouses and industry are able to handle packages, speed up inventory identification using machine vision, and autonomously unload shipping containers.

{>>{"author":"Elias's AI","timestamp":1783776546519}@@removed embedded iframe: https://www.youtube-nocookie.com/embed/F_7IPm7f1vI<<}

*Video 1.1: Video showcasing one example of the state of humanoid robots in 2024 ([Boston Dynamics, 2024](https://bostondynamics.com/video/atlas-goes-hands-on/)).*

![Figure 1.22](https://ai-safety-atlas.com/_astro/4fb946e50c05e284df3fffa70f15b15603eaa31766152af852dfadebd8615338.B2-hOjD9_1Pz7dl.webp)

*Figure 1.22: Boston Dynamics' Stretch robot that can autonomously unload shipping containers, lift up to 50 pounds, and clear away missed boxes along the way ([Boston Dynamics, 2024](https://bostondynamics.com/products/stretch/)).*

![Figure 1.23](https://ai-safety-atlas.com/_astro/7bfc8b48cf2d2353bf9b3fb9a1411a8056faf0bf61952af27a309a5a615c5f36.vnCjNU5i_Z2qqyYh.webp)

*Figure 1.23: Amazon has a huge fleet of robots that automate it’s warehouses. This is an example of the Hercules robot that retrieves shelves of products and delivers them to employees, who then pick the items customers ordered for shipping ([Amazon, 2023](https://www.aboutamazon.com/news/operations/amazon-hercules-robot)).*

{--{"author":"Elias's AI","timestamp":1783851477941}@@---

--}[^1]:  KataGo is a system which is based on techniques used by DeepMind's AlphaGo Zero and similarly superhuman in its game play. In 2022, researchers managed to demonstrate that despite being superhuman KataGo can be beaten by humans and demonstrates "surprising failure modes" of AI systems. This is the kind of thing that will be a repeated theme throughout our text ([Wang and Gleave et al., 2022](https://arxiv.org/abs/2211.00241))

[^2]:  Standards like the Model Context Protocol (MCP) are formalizing how AI assistants connect to data repositories and development environments ([Anthropic, 2024](https://www.anthropic.com/news/model-context-protocol)). The MCP protocol has been donated to the Linux foundation([Anthropic, 2025](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation)).
