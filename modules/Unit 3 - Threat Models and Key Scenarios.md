---
slug: u3-threat-models
title: "Unit 3: Threat Models and Key Scenarios"
id: 'f98a8b50-30cb-4a30-9cd3-41b376a8d69a'
---
# Submodule: How this unit works

# Lens: Read This First
id:: 07e48171-8996-4ce8-8844-c45d2234c1dd{++{"author":"Luc's AI","timestamp":1787134591131}@@
tldr:: Commit to clear predictions before each reading, then use the gap between what you expected and what the evidence shows as the lesson.
summary_for_tutor:: An orientation to Unit 3's prediction-first structure. It explains why learners must commit before reading, clarifies that the sequence follows conceptual prerequisites rather than severity, and states that assessment rewards applying and reconstructing arguments rather than merely accepting or repeating them.++}
#### Text
content::
\## Before you start

This unit is arranged so that you answer the questions before you are given the answers.

Three times, you will be asked to commit to a position, in writing, on material you have not read: how a catastrophe could happen with nobody at fault, what makes alignment hard, and what two specific experiments found. Then you read. Then you are asked again, differently.

This is not a study technique bolted onto the content. The gap between what you predicted and what turned out to be the case is the thing you will retain, and it does not exist unless you commit first. A cautious answer that hedges everything produces no gap and teaches you nothing.

You will be wrong about some of it. That is the design working.

\## What this unit is not ordered by

The readings are not arranged from least to most alarming, and you should not read the order as a ranking of severity or of likelihood.

They are arranged by what each one requires you to already have. The structural failures come first because they need no misaligned system, only optimization. The mechanism comes next because "misalignment" is a vibe until you can say what would produce it. The experiments come after the mechanism so you can watch a theory meet data. The objections come last because you cannot evaluate an objection to an argument you cannot yet state.

\## A note on how you will be assessed

The tests in this unit ask you to apply the ideas to cases that appear in none of the readings. Reproducing an author's argument accurately is not a passing answer.

You are also not being assessed on whether you find these arguments convincing. Someone who understands an argument thoroughly and rejects it for stated reasons passes; someone who accepts it and cannot reconstruct it does not.

# Submodule: Catastrophe without a schemer

# Learning Outcome:
source:: [[../Learning Outcomes/Catastrophe without a schemer]]

# Lens: Failure Without a Schemer - PQ
source:: [[../Lenses/U3 - Failure Without a Schemer - PQ]]

# Lens: What Failure Looks Like
source:: [[../Lenses/U3 - What Failure Looks Like]]

# Lens: Gradual Disempowerment
source:: [[../Lenses/U3 - Gradual Disempowerment]]

# Submodule: What makes alignment hard

# Learning Outcome:
source:: [[../Learning Outcomes/Locating the core difficulty]]

# Lens: What Makes This Hard - PQ
source:: [[../Lenses/U3 - What Makes This Hard - PQ]]

# Lens: Two Accounts of the Core Difficulty
source:: [[../Lenses/U3 - Two Accounts of the Core Difficulty]]

# Submodule: Is it already happening

# Learning Outcome:
source:: [[../Learning Outcomes/Reading evidence of scheming]]

# Lens: Predict the Result - PQ
source:: [[../Lenses/U3 - Predict the Result - PQ]]

# Lens: Alignment Faking and In-Context Scheming
source:: [[../Lenses/U3 - Alignment Faking and In-Context Scheming]]

# Submodule: The other direction

# Lens: Sympathy for the Model
source:: [[../Lenses/U3 - Sympathy for the Model]]
optional:: true

# Submodule: Objections

# Lens: Where This Unit Might Be Wrong
id:: bf79def0-ae73-4e9e-80bd-04917885b1f8{++{"author":"Luc's AI","timestamp":1787134591460}@@
tldr:: Stress-test the unit by reading the objection you expect to resist most: perhaps control targets the wrong failure, current LLMs never reach the assumed regime, or risk decompositions bias the answer.
summary_for_tutor:: A curated objections lens after the main threat models. It presents challenges to control research, to extrapolating current LLMs into dangerous agents, and to probabilistic decomposition itself, then asks the learner to read at least one opposing account.++}
#### Text
content::
\## Three objections worth taking seriously

You have now been given a set of arguments largely by people who agree with each other about the basic shape of the situation. Here are the strongest disagreements available, from inside the field.

Read at least one. Read the one you expect to disagree with.

\### The case against control research

**John Wentworth, *The Case Against AI Control Research*.** Argues that the systems likely to kill us are not the scheming ones this unit has focused on. On his account, early transformative AI kills us by failing to solve superintelligence alignment while everyone believes it succeeded, so control research aimed at catching schemers is aimed at the wrong failure. This is an objection to the entire pipeline from this unit into the next.

\### The paradigm does not get there

**Cole Wyeth, *My model of what is going on with LLMs*.** Argues intelligence is not a single knob being turned up, that current systems are missing specific mental functions including continual learning and long-horizon planning, and that they have not yet done anything that matters. If this is right, most of this unit is a description of something that is not being built.

Its companion, **Abram Demski and Cole Wyeth, *Have LLMs Generated Novel Insights?*,** puts the claim to a test with cases. Before you read it, write down your own answer: can you name a genuine novel insight produced by one of these systems? Write the name down first. Then read.

\### The decomposition is the problem

**Nate Soares, *Comments on Carlsmith's "Is power-seeking AI an existential risk?"*** and **Eli Lifland's review of the same.** Two orthogonal attacks on the field's most carefully decomposed risk argument. Soares argues that multi-stage decomposition drives conjunctive arguments to implausibly small numbers, so the method itself biases the estimate. Lifland argues the framing as catastrophe-avoidance rather than reaching a good outcome biases it the other way.

If you took the forecasting unit, these are that unit's methods turned against this unit's conclusions. That is what they are for.

# Lens: Dive Deeper
id:: ba22da99-8986-4494-8a58-73ecd4e293d5{++{"author":"Luc's AI","timestamp":1787134591681}@@
tldr:: Go beyond the unit with a full probabilistic risk argument, precise learned-objective theory, worked scenarios, control priorities, and deliberate human misuse.
summary_for_tutor:: An optional resource map extending Unit 3. It sequences Carlsmith's structured power-seeking argument, learned optimization, AI 2027, control-priority analyses, and human-led coup or takeover scenarios so a tutor can direct learners from formal threat models to concrete mechanisms and alternatives.++}
#### Text
content::
\## The structured argument, in full

This unit taught threat models before the canonical decomposition of them, which is the reverse of the usual order. If you want the field's most explicit statement, assembled as a numbered argument with probabilities attached to each step:

**Joe Carlsmith, *Existential Risk from Power-Seeking AI*.** Everything in this unit can be located against it. The video version is the assignable length.

\## Where the mechanism comes from

**Evan Hubinger et al., *Risks from Learned Optimization*.** What it would mean for a learned system to acquire an objective of its own, stated precisely rather than gestured at.

\## What an actual scenario looks like

**Kokotajlo et al., *AI 2027*.** A concrete worked scenario rather than an argument. If later units ask you to produce a scenario of your own, this is the form.

\## Turning threat models into priorities

**Ryan Greenblatt, *Prioritizing threats for AI control*,** which argues rogue internal deployment rather than self-exfiltration is the top control risk, and **Buck Shlegeris, *The prototypical catastrophic AI action is getting root access to its datacenter*,** which deflates the objection that a system could not actually do anything.

\## Deliberate harm

This unit is mostly about systems pursuing goals nobody chose. The other threat model is people using these systems deliberately.

**Tom Davidson et al., *AI-enabled coups: a small group could use AI to seize power*.** Three converging mechanisms: AI workers made singularly loyal to one person, secret loyalties that survive across model generations, and the concentration of frontier capability in few hands.

**Tom Davidson, *Human takeover might be worse than AI takeover*.** Argues that conditional on a takeover happening, the human version may be worse, because seizing power selects for the people least suited to holding it.
optional:: true
