---
id: a37a6057-a08d-4218-a1ac-fa9c19e8cb37
reading_minutes: 25
tutor_minutes: 3
summary_for_tutor: {--{"author":"Elua's AI","timestamp":1790784066509}@@"Covers--}{++{"author":"Elua's AI","timestamp":1790784066509}@@"Video of++} Connor Leahy's {--{"author":"Elua's AI","timestamp":1790784066509}@@skeptical assessment of mechanistic interpretability as an AGI safety tool. Makes two main arguments: first, --}{++{"author":"Elua's AI","timestamp":1790784066509}@@talk at the FLI Interpretability Conference (MIT, March 2023); his company Conjecture had moved away from MI. Two arguments. First, ++}much {--{"author":"Elua's AI","timestamp":1790784066509}@@AGI--}{++{"author":"Elua's AI","timestamp":1790784066509}@@of an AGI's++} cognition will be externalized into {--{"author":"Elua's AI","timestamp":1790784066509}@@the--}{++{"author":"Elua's AI","timestamp":1790784066509}@@its++} environment (tools, {--{"author":"Elua's AI","timestamp":1790784066509}@@memory,--}{++{"author":"Elua's AI","timestamp":1790784066509}@@notes, other people,++} social {--{"author":"Elua's AI","timestamp":1790784066509}@@interactions),--}{++{"author":"Elua's AI","timestamp":1790784066509}@@media),++} so interpreting the network alone {--{"author":"Elua's AI","timestamp":1790784066509}@@is insufficient. --}{++{"author":"Elua's AI","timestamp":1790784066509}@@won't predict behaviour; examples include a 'follow the recipe book' circuit, his bag-packing habit, beavers that build dams because they hate the sound of running water, and the Sydney Bing incident. ++}Second, MI{--{"author":"Elua's AI","timestamp":1790784066509}@@ research--} is {--{"author":"Elua's AI","timestamp":1790784066509}@@inherently dual-use, producing capability gains that--}{++{"author":"Elua's AI","timestamp":1790784066509}@@dual-use: its findings will make models more capable, while++} labs {--{"author":"Elua's AI","timestamp":1790784066509}@@will exploit without performing--}{++{"author":"Elua's AI","timestamp":1790784066509}@@lack the incentives to do++} the {--{"author":"Elua's AI","timestamp":1790784066509}@@additional--}{++{"author":"Elua's AI","timestamp":1790784066509}@@extra++} oversight work. {--{"author":"Elua's AI","timestamp":1790784066509}@@Argues that political coordination--}{++{"author":"Elua's AI","timestamp":1790784066509}@@He still calls MI valuable science, but asks researchers not to publish,++} and {--{"author":"Elua's AI","timestamp":1790784066509}@@legal enforcement are prerequisites for MI to contribute to safety."--}{++{"author":"Elua's AI","timestamp":1790784066509}@@argues monitoring needs government-backed legal enforcement because this is a political problem."++}
title: MI for AGI Safety
# ORIGINAL tldr (commented out as AI slop; misrepresents the talk):
# tldr: A skeptical view of whether interpretability can keep up with the pace of AI development. Connor Leahy argues that by the time researchers understand one circuit, the model has already evolved — making interpretability more like a post-mortem tool than a real-time safety measure.
# PROPOSED FIX:
# tldr: Can interpretability make AGI safe? Connor Leahy doubts it. Much of a capable AI's thinking will happen outside the network, and what interpretability teaches us about models is just as useful for making them stronger.
---

#### Text
content::
%% ORIGINAL (commented out as AI slop; misrepresents the talk):
The skeptical case about interpretability is that it will not scale to the most safety-critical failures—especially deception, situational awareness, and long horizon planning, and that we may end up with comforting stories that do not reliably detect dangerous cognition.
Connor Leahy presents a skeptical view of interpretability as a complete safety solution. His core argument is that capabilities grow faster than understanding. By the time we interpret a single circuit, the model has already evolved. Interpretability is a post-mortem tool: it tells us why we died after the fact. It does not provide the hard safety guarantees needed to prevent a rogue AGI from taking control.
%%

%% PROPOSED FIX:
Connor Leahy runs an organisation that walked away from interpretability. Here he gives two reasons. First, a capable AI's thinking won't all live inside the network: it will be spread across tools, notes, other systems and the world around it, so reading the weights won't tell you what it will do. Second, interpretability is dual-use. What you learn about a model also shows how to make it stronger, and labs will use the capability gains without doing the oversight. His conclusion: this is a political problem as much as a technical one.
%%

#### Video
source:: [[../video_transcripts/conjecture-agi-safety-connor-leahy-fli-interpretability-conference-mit-march-2023]]
from:: 00:00
to:: 21:01

#### Text
content::
Ask the AI Tutor any questions you may have:

#### Chat
instructions::
Help the user understand this article, or help them with other questions they have.