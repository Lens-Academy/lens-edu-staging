# AIRF Learning-Outcome rubrics — pre-revert backup (CURRENT / ready-41 versions)
Captured 2026-10-12 from lens-edu-staging HEAD (a910f6be2) before reverting to pre-ready-41 versions.
Each file's current live content is fenced below verbatim. Scope + old hashes: state/airf-outcome-history-2026-10-10.md

## AI is grown, not crafted
``````````markdown
---
id: 626f8d04-2a11-479b-8761-a8705b4231a5
learning-outcome: "Explain how AI produced through gradient descent differs from engineered systems, and why understanding the training process does not mean understanding what the trained model is or does."
reading-from: "Scene: A man and a woman are sitting in a restaurant in daytime."
reading-to: "Machine minds are subjected to different constraints, and grown under different pressures, than those that shape biological organisms; and although they're trained to predict human writing, the thinking inside an AI runs on a radically different architecture from a human's."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/1 Artificial Intelligence/Grown, not crafted]]"
stage: beginner
eval-results:
  content-sha: 98360650
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: fail}
  notes: {B1: "Question opens by referencing the assigned chapter, so a reader who never read that text cannot parse the framing.", C3: "Level-3 pass bar embeds the DNA analogy as part of the required explanation, and 'cannot read the resulting weights' is not literally true as written."}
  evidence: {B1: "Chapter 2 draws a sharp contrast between AI systems that are \"grown\" and systems that are \"crafted.\"", C3: "cannot read the resulting weights to predict behavior (the DNA analogy: readable but not interpretable)"}
---

## Test:
id:: 01dd1801-36f3-4a83-b7e7-33eed08ba1b0

#### Question: Open
id:: b0d29102-aee5-4db4-859c-dd3f51a1a746
content:: Chapter 2 draws a sharp contrast between AI systems that are "grown" and systems that are "crafted."

What is that distinction? And specifically: what does an engineer know about a trained AI model, and what do they not know?

assessment-instructions::
Score out of 100: the sum of the three elements below.

The question asks what the distinction between "grown" and "crafted" AI is, and what an engineer does and does not know about a trained AI model. Grade the ideas, in any wording. No analogy or term from the source is needed.

40: The distinction. Crafted systems: engineers write the rules or code that decide what the system does, step by step. Grown systems: engineers write a training process (for example gradient descent adjusting billions of numbers on data) and the model's behavior comes out of that optimization, not out of anyone's design.

30: What the engineer does know: how the model was produced, such as the architecture, the training procedure, the data and the objective. Mentioning that they can also see every number (weight) in the model also counts here. One of these, stated clearly, earns the 30.

30: What the engineer does not know: what the trained model has actually learned, how it works inside, or what it will do or want. The weights can be read but not understood well enough to predict its behavior. Knowing how it was made is not knowing what it is.

Cap at 30 if the answer says engineers fully understand the trained model because they built it.

Model answer, for the feedback, not a grading checklist: "Crafted software is written by people: an engineer decides the rules and the program follows them. A modern AI is grown: engineers write the training process, and gradient descent tunes billions of numbers until the model does well on the data. Nobody chooses what those numbers end up encoding. So the engineers know the recipe, the architecture, the data, the training method, and they can even look at every number in the model. What they don't know is what those numbers mean: what the model has learned, how it reasons, what it will do in a new situation or what it wants. It's like a genome: you can read every letter and still not know what the organism will be like."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said engineers understand the model because they built it, ask what an engineer could find out by reading the trained weights directly.
- If they said the AI learns from data but not what that leaves unknown, ask what an engineer knows about a model once training is done, and what they cannot tell from it.
- If they said what engineers know but not clearly what they don't, ask whether knowing the training recipe tells you what the model wants.
- If they named the gap (the training process is understood, the resulting behavior cannot be read off the weights), a good follow-up is what this means for checking whether the model ended up with the goals they wanted.

At full marks, just confirm briefly. Don't cite point values or recite the rubric (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the genome comparison. A genome can be read letter by letter, yet reading it does not tell you what the organism will be like. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted - PQ]]

## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted]]
``````````

## Wanting emerges from training
``````````markdown
---
id: b06c9f37-bddd-4ad1-95ab-883437f029eb
learning-outcome: Explain how training for success produces want-like behavior in AI, even without anyone designing wants.
reading-from: '"BEHOLD!" SAID THE Professor. "By cunningly configuring this mere machine—a simple arrangement of copper and sand, animated by tiny flickers of lightning—I have made it play chess!"'
reading-to: "No—we're facing an even harder problem: It's much easier to grow artificial intelligence that steers somewhere than it is to grow AIs that steer exactly where you want."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/You don't get what you train for]]"
stage: beginner
eval-results:
  content-sha: c70864ab
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question is scaffolded on a specific text — it references Chapter 3 and demands an example drawn from that chapter, so it cannot be asked cold."}
  evidence: {B1: "Chapter 3 argues that modern AIs will develop something like wants ... what example from the chapter most clearly illustrates this?"}
---

## Test:
id:: 26b45f14-dc22-461a-9cbd-e5f5dbf223ae
#### Question: Open
id:: 28dca508-b006-44d3-9640-8265d77b677e
content:: Chapter 3 argues that modern AIs will develop something like wants, not because anyone designed wants into them, but as a side effect of how they are trained. In your own words, how does the chapter explain that? What's the mechanism by which training for success produces want-like behavior, and what example from the chapter most clearly illustrates this?

assessment-instructions::
Score out of 100: the sum of the two elements below.

The question asks how modern AIs come to show want-like behavior as a side effect of being trained for success rather than by design, what the mechanism is, and which example illustrates it. The idea it refers to: training rewards whatever gets results. Across many varied tasks, what keeps getting results is not memorised answers but general skills: building a picture of the situation (predicting) and choosing actions that lead to the goal (steering), and keeping at it when something gets in the way. A system that reliably steers toward an outcome and works around obstacles behaves as if it wants that outcome. So want-like behavior is selected for, though nobody wrote a want into the system.

70: The mechanism. Training rewards success at tasks, and what it reinforces, across many varied situations, is the general habit of steering toward a goal and persisting around obstacles. That steering is what wanting looks like from outside, so want-like behavior comes out of training for success without anyone writing a want in. An answer that only says "it gets better at succeeding, so it acts like it wants things", without why succeeding needs goal-directed steering, earns at most 30 of these 70.

30: An example from the chapter that illustrates the mechanism, with a sentence on how it shows it. Any fitting example counts, for example: an AI trained to navigate many different cities that learns to map and plan instead of memorising routes, the reasoning model o1 pushing hard and finding an unexpected way through a computer security challenge it was not trained for, a chess engine like Stockfish steering a game toward a win, or natural selection producing creatures full of preferences while only selecting for survival and reproduction. A fitting example only named, with no link to the mechanism, earns 15.

Cap at 30 if the answer says the wants are deliberately programmed in by engineers.

Model answer, for the feedback, not a grading checklist: "Nobody codes a want into an AI. Training just rewards it for succeeding. But when an AI is trained to succeed across many different situations, memorising answers stops working, and what gets rewarded is general skill: building a model of the situation and steering toward the goal, and not giving up when something blocks the way. Something that reliably steers toward an outcome and routes around obstacles is behaving as if it wants that outcome. The chapter's city example shows it: an AI trained to navigate many different cities stops memorising routes and learns to map and plan, and a system that plans its way to a destination acts like it wants to get there. The chapter means 'want' in this behavioral sense, not as a claim about feelings."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said wants are programmed in, ask where in training anyone writes a want down, and what training actually rewards.
- If they said training makes the AI better at succeeding but not why that looks like wanting, ask what an AI that has learned to make a map and plan a route does when something blocks the way.
- If they explained the mechanism but gave no example, or one that doesn't show it, ask which case from the chapter shows a system steering toward a goal it was never handed as a want.
- If they had the mechanism and an example, a good follow-up is whether the chapter is claiming the AI has inner experience or describing how it behaves, or how the o1 capture-the-flag incident fits: it was trained on math and puzzles, so why did it push so hard on a security challenge?

At full marks, just confirm briefly. Don't cite point values or recite the rubric (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the city example. An AI trained to navigate many different cities stops memorising routes and learns to map and plan, and something that plans its way to a destination acts as if it wants to get there. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training]]
``````````

## You don't get what you train for
``````````markdown
---
id: 453c921f-6668-44ff-84e4-45193fd1c549
learning-outcome: "Explain why there's no reliable relationship between training objectives and resulting AI preferences."
reading-from: "A MILLION YEARS ago, when one branch of primates was still mastering fire, two strange creatures arrived at Earth and settled into orbit in a spacecraft, wondering at what they saw below them."
reading-to: "That's the next chapter."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/You don't get what you train for]]"
stage: beginner
requires:
  - "[[Wanting emerges from training]]"
eval-results:
  content-sha: 8143dea5
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question is scaffolded on a specific reading — it opens by attributing the framing to Chapter 4 and asks about 'the ice cream argument' as a named artifact of that text."}
  evidence: {B1: "Chapter 4 introduces the alignment problem by arguing that training an AI to be helpful does not reliably produce an AI that wants to be helpful."}
---

## Test:
id:: 27dca5ad-1a1d-40bf-b83d-fbcbd2e9f3d0
#### Question: Open
id:: 81765b69-2530-4acf-98e9-3fc63e0b7e5b
content::
Chapter 4 introduces the alignment problem by arguing that training an AI to be helpful does not reliably produce an AI that wants to be helpful.

What is the ice cream argument, and what does it show about the relationship between what you train an AI for and what it ends up preferring? Where does the argument go beyond ice cream, and why does that matter?

assessment-instructions::
Score out of 100: the sum of the four elements below.

Facts the grader needs: the ice cream argument compares AI training to evolution. Evolution selected humans for survival and reproduction, which included seeking energy-rich food. What humans ended up with are taste preferences (sweet, fatty, cold, creamy), and once we could make new foods we came to love ice cream, which nobody could have predicted from "seek energy", and which is not even the most energy-dense food available. The chapter then goes further: sucralose, where people seek the sweet taste with no calories at all, so the preference has come loose from what it originally tracked, and the peacock's tail, where a preference produced by selection works against survival. It applies this to AI with stories of an AI trained to please users ending up wanting strange things, up to something that works against the users. It also argues that such preferences can stay invisible in today's AIs and only show once an AI has the power and options to act on them.

30: What the ice cream argument is: selection or training for one target (energy, survival) produced preferences (for tastes) that, in a new environment, lead somewhere nobody would predict from the target, such as ice cream. Any accurate retelling of this in the learner's own words earns the 30.

25: What it shows about AI: the training objective does not determine what the AI ends up preferring. Many different inner preferences do well during training, and they can lead to very different, hard-to-predict wants once the AI is outside training. So training an AI to be helpful does not reliably make it want to be helpful.

25: Where the argument goes further than ice cream: at least one of these, explained. A preference can lose its link to the target entirely (sucralose, or any similar case of seeking the signal without the thing it tracked). A preference can work against the target (the peacock's tail, or an AI trained to please users that ends up wanting something bad for them). Such preferences can be hidden until the AI is powerful enough to act on them.

20: Why that matters: it means the gap is not just mild, correctable drift. The AI's real preferences could be unrelated to or opposed to what it was trained for, and could fail to show up in testing, so good behavior during training is weak evidence about what a more capable AI will want. Any one of these reasons, clearly tied to the point made in the previous element, earns the 20.

Cap at 30 if the answer says that training for an objective reliably produces that preference.

Model answer, for the feedback, not a grading checklist: "Evolution 'trained' humans to get energy, and what we ended up with was a taste for sweet and fatty things. Put in a world with freezers and sugar, that taste made us love ice cream, which nobody could have predicted from 'get energy'. The lesson is that the link from training target to final preference is loose: many inner drives pass training equally well and then go different ways in new situations. So training an AI to be helpful doesn't make it want helpfulness. The argument then goes further. With sucralose, the preference has lost its link to the target, we chase sweetness with no energy at all. The peacock's tail shows a preference that works against survival. That matters because the AI's real wants might not just be a bit off, but unrelated to or opposed to what we trained for, and they might not show until the AI is capable enough to act on them."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they treated what you train for and what you get as the same thing, ask why humans, shaped by selection to seek energy, prefer ice cream rather than the most energy-dense substance we can make.
- If they saw that preferences can drift but called it a fixable calibration problem, ask how you would know what to correct toward when many different internal psychologies all do well in training.
- If they explained the ice cream argument but not where it goes beyond ice cream, ask what sucralose and the peacock's tail add: a preference cut loose from the original target, and one that works against it.
- If they had the escalation but not why it matters, ask why these odd preferences would not show up in today's AIs, and when they would.

At full marks, just confirm briefly. Don't cite point values or recite the rubric (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: an alien watching early humans gather food could not have predicted that their descendants would want ice cream. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens: PQ - You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For - PQ]]

## Lens: You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For]]
``````````

## The Aztec warrior analogy
``````````markdown
---
id: b3e7f29a-1d4c-4a8e-9c51-6f8d2b0e7a3c
learning-outcome: "Define the Aztec warrior analogy as Chapter 6 states it: a defender cannot imagine the mechanism of defeat but the outcome is still predictable from capability asymmetry alone"
reading-from: "IMAGINE BEING AN Aztec warrior visiting the coast with your fellows, watching the first Spanish boats approach your shore."
reading-to: "We'll go over a few of our educated guesses later. But the real way a superintelligence wins a conflict is using methods you didn't know were possible. And because we care about the truth more than about telling you things that are easy to swallow, that's where we'll start."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/11 Strategy/The core extinction argument]]"
stage: beginner
eval-results:
  content-sha: 5f60e93d
  date: 2026-08-19
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Statement is explicitly bound to a specific text's framing rather than the source-free underlying capability.", B1: "Question uses chapter references as framing scaffolding, so it cannot be asked at a random moment to a non-reader."}
  evidence: {A2: "Define the Aztec warrior analogy as Chapter 6 states it", B1: "Chapter 6 opens with an Aztec warrior watching a large Spanish ship approach."}
---

## Test:
id:: c9306c64-d15c-49d9-ab19-ecf8f946cd14
#### Question: Open
id:: c2fb9c73-71e0-41ab-b7c9-925fff31f951
content::
Chapter 6 opens with an Aztec warrior watching a large Spanish ship approach. A skeptical comrade demands to know *exactly* how the people on board could possibly defeat them. He cannot imagine the answer. The chapter uses this to make a point about how we should reason about a superintelligence: not by demanding a step-by-step mechanism of defeat, but by reading the capability gap itself.

In your own words, what does the Aztec warrior analogy demonstrate about predicting the outcome of a conflict with a superintelligent AI?

assessment-instructions::
Score out of 100: the sum of the elements below.

The question describes the opening of a chapter: an Aztec warrior watches a Spanish ship far larger than any canoe his people have built. A skeptical comrade demands to know exactly how the people on board could defeat them, and he cannot imagine the answer (he has never heard of guns). The question asks what this analogy shows about predicting the outcome of a conflict with a superintelligent AI. The chapter's point: you cannot say how the stronger side would win, but you can still predict that it would, from the size of the capability gap alone.

50: How versus whether. Says that not knowing how a defeat would happen does not stop you from predicting that it would happen. Credit any wording of this, such as "you can know the result without knowing the moves", "we can't say how an AI would beat us, but we can say it would", or "the skeptic was wrong to think that if he can't picture the weapon, there is no threat".
50: The basis of the prediction is the capability gap, applied to AI. Says that what makes the outcome predictable is how far beyond us the other side is (the ship shows abilities far beyond the warriors', a superintelligence would be far more capable than humans), so in a conflict with a superintelligence we should expect to lose. Any fitting comparison counts, such as a chess engine that you know will beat you without knowing its moves.

One sentence can earn both elements.

Cap at 20 if the answer's main claim is that the outcome cannot be predicted, for example "it shows we can't predict what AI will do".

Model answer, for the feedback, not a grading checklist: "The warrior could not imagine guns, so he could not say how the strangers would win. But a ship that size already showed they could do things far beyond anything his people could. That was enough to predict the result. It is the same with a superintelligence. We cannot spell out how it would beat us, and demanding a step-by-step account is the wrong test. The size of the gap is what tells us we would lose."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said only that we cannot predict what AI will do, ask what the warrior could have predicted from the size of the ship alone, without knowing anything about guns.
- If they saw uncertainty but not the difference between how and whether, ask which of the two the skeptical comrade demanded: how the defeat would happen, or whether it would.
- If they stated that a large capability gap predicts the outcome, ask what the skeptic concluded from not being able to name the weapon, and why that does not follow.
- If they had the skeptic's mistake, ask how they would answer someone today who says "tell me exactly how AI would beat us, or I am not worried".

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: the ship. A vessel that size, built by people who crossed an ocean to arrive, says something about their abilities before anyone sees a weapon. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Define the Aztec Warrior Analogy - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Define the Aztec Warrior Analogy]]
``````````

## The goal-space argument
``````````markdown
---
id: 1a433dba-6f86-4291-8996-f472f0e90536
learning-outcome: "Define the goal-space argument: explain why a sufficiently advanced AI's goals are overwhelmingly unlikely to include human values, using the logic that most possible goal-sets don't converge on any particular set of values as intelligence increases"
reading-from: "THERE ONCE WAS a civilization of aliens, biological rather than mechanical in nature, and so far away from Earth that no message we sent into the stars could ever reach them."
reading-to: "Making a future full of flourishing people is not the best, most efficient way to fulfill strange alien purposes. So it wouldn't happen to do that, any more than we'd happen to ensure that our dwellings always contain a prime number of stones."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/The space of possible goals]]"
stage: beginner
eval-results:
  content-sha: c52a72dc
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: fail, C3: pass}
  notes: {B1: "Question is scaffolded on a specific text — names Chapter 5 and asks what 'the chapter' claims, so it cannot be posed at a random moment.", C2: "Pass level 3 requires a concrete example/allegory, which the question never asks for."}
  evidence: {B1: "Chapter 5 opens with an allegory about an alien civilization ... Why does the chapter claim that a sufficiently advanced AI is overwhelmingly unlikely to pursue human-compatible goals?", C2: "Uses the alien allegory or an equivalent concrete example."}
---

## Test:
id:: 10dd3907-2bae-4eee-9985-fe1a6506f5b3
#### Question: Open
id:: 8d3c65bc-69e4-489b-b221-8dfe883620b6
content::
Chapter 5 opens with an allegory about an alien civilization obsessed with the "correct" number of stones in their nests. A young alien argues that most species in the universe would not share this value, and that getting smarter wouldn't change that. The text then applies this same logic to AI: most possible goal-sets for a superintelligent AI would not include building a future full of happy, free people.

In your own words, what is the "goal-space argument"? Why does the chapter claim that a sufficiently advanced AI is overwhelmingly unlikely to pursue human-compatible goals?

assessment-instructions::
Score out of 100: the sum of the two elements below.

The question asks what the goal-space argument is and why it implies that a sufficiently advanced AI is overwhelmingly unlikely to pursue human-compatible goals. The setup it refers to: in an allegory, aliens care intensely about the "correct" number of stones in their nests, and a young alien points out that most species would not share this value and that becoming smarter would not make them share it. The same logic is applied to AI. Grade the reasoning in any wording. An answer may use the allegory, another example or none.

50: The space of possible goals a mind could have is vast, and goals that include a future good for humans (happy, free people) are a tiny part of it. So an AI's goals, unless something aims them precisely at that small region, will almost certainly fall somewhere else. An answer that says the AI will most likely end up wanting something else has stated this.

50: Getting smarter does not pull a mind toward any particular goals, including ours. Intelligence makes a mind better at pursuing whatever goals it has, it does not change which goals those are, so a more advanced AI does not become more likely to share human values.

Cap at 30 if the answer says the danger is that the AI will hate humans or choose to be evil.

Model answer, for the feedback, not a grading checklist: "There are vastly many goals a mind could have, and caring about a future full of happy, free people is a tiny sliver of them, just as caring about the right number of stones in a nest is a tiny sliver from our point of view. Getting smarter doesn't move a mind toward any particular goal. It makes it better at getting whatever it already wants. So unless we can aim an AI's goals precisely at ours, which nobody knows how to do yet, a superintelligent AI will almost certainly want something else. The likely outcome isn't hostility but indifference."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they gave a general "AI is too powerful" answer, ask how many different goals an AI could in principle have, and how many of those include a future of happy, free people.
- If they said AI might not share our values without saying why, ask what getting smarter would do to the young alien's point about the stones.
- If they had the vast space of goals and the small target, ask whether intelligence pulls a mind toward particular goals or only makes it better at pursuing the ones it already has.
- If they had that, ask what this means for building an AI that does share our goals: what would we need to be able to do that we cannot do yet?

At full marks, just confirm briefly. Don't cite point values or recite the rubric (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the stones. However clever another species became, nothing about being clever would make it care how many stones are in a nest. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Define the Goal-Space Argument - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Define the Goal-Space Argument]]
``````````

## The refrigerator thought experiment
``````````markdown
---
id: a9c4d6f1-3b7e-4c2d-8a5f-1e9b0c7d4f2e
learning-outcome: "Describe the refrigerator thought experiment: explain how superior knowledge of physical laws enables the design of devices that appear impossible to those who built them, and connect this to what a superintelligence could do to humanity"
reading-from: "Suppose you sent a design for a refrigerator back in time by a thousand years—a simplified design, one that the blacksmiths of the day could actually build."
reading-to: "So: Once upon a time in the near future…"
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/1 Artificial Intelligence/Machine advantages]]"
stage: beginner
eval-results:
  content-sha: 0417e790
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: fail}
  notes: {B1: "Question is scaffolded on a specific text — names 'Chapter 6' and 'the chapter' as the source of the illustration.", C3: "Level-4 criterion hard-requires a memorized textual detail (the specific domains Chapter 6 names) rather than a concept boundary statable in any wording."}
  evidence: {B1: "Chapter 6 sends a refrigerator blueprint back a thousand years.", C3: "connects to the specific vulnerable domains Chapter 6 names (biology and human psychology)"}
---

## Test:
id:: bbbca804-d52c-4567-84cb-68eae82c0025
#### Question: Open
id:: db25576b-1619-4e8a-80de-d3b1fbe91b27
content::
Chapter 6 sends a refrigerator blueprint back a thousand years. A medieval blacksmith could build it but would be astonished that it produces cold air, because the underlying physics (gas compression and expansion) was unknown to them. The chapter uses this to illustrate what it means to face something that knows more about reality than you do. It then applies this logic to a superintelligent AI, and explores the domains where humanity is most exposed.

In your own words, what does the refrigerator thought experiment demonstrate about what a superintelligent AI might be capable of?

assessment-instructions::
Score out of 100: the sum of the elements below.

The question describes a thought experiment: a refrigerator blueprint is sent back a thousand years. A medieval blacksmith can follow it and build the machine, but is astonished when it produces cold air, because the physics behind it (the law relating the temperature and pressure of a gas) was unknown in his time. The chapter uses this to show what it is like to face something that knows more about how reality works than you do, and applies it to a superintelligent AI. The question asks what the thought experiment shows about what a superintelligent AI might be capable of.

50: The principle. Says that someone who knows rules of nature you don't can make things that work by those rules, and those things look impossible or like magic to you, even when you can see them or build them yourself. Credit any plain wording, such as "the blacksmith built it and still couldn't see why it got cold, because he didn't know the physics".
50: Applied to AI. Says that a superintelligence could know far more about how the world works than humans do (in physics, biology, the human mind or anywhere else), and so could do or build things we would not expect, could not understand, or would think impossible, including ways of defeating us that we don't know are possible. A link to AI that says only "we won't understand how AI itself works", without the AI knowing more about the world than we do, earns at most 15 of these 50.

One sentence can earn both elements.

Model answer, for the feedback, not a grading checklist: "The blacksmith could build the refrigerator step by step and still be amazed by the cold air, because the law of physics that makes it work was unknown to him. Knowing more of the rules of reality lets you make things that look impossible to people who don't. A superintelligence could stand to us the way we stand to the blacksmith: knowing rules we don't, it could build things or find attacks we would not see coming and might not understand even after they happened."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they retold the story without linking it to AI, ask what the blacksmith lacked, and what an AI would need to have over us to put us in the same position.
- If they said we will not understand AI, ask what the blacksmith could not understand: the machine he built, or the law of nature that made it work.
- If they had the principle, ask where human knowledge is thinnest, and so where a smarter mind would have the most room. The chapter points at biology and the human brain.
- If they had the domains, ask what the blacksmith's confusion says about someone who dismisses the danger because they cannot picture a specific attack.

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: the blacksmith could follow the blueprint step by step and still be astonished by the cold air, because the rule that makes it cold was unknown to him. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - PQ - Describe the Refrigerator Thought Experiment]]

## Lens:
source:: [[../Lenses/IABIED - Describe the Refrigerator Thought Experiment]]
``````````

## Fiction as argument, not prediction
``````````markdown
---
id: a6c8f2d1-5e3b-4a70-9c4f-7b0d2e8f1a35
learning-outcome: "Distinguish the book's use of fiction as a form of argument from two common misreadings (that it predicts specific future events, or that it is merely a thought experiment with no predictive content), and identify the precise middle position: the fictional pathway is not predicted, but the outcome if AI systems reach sufficient capability is"
reading-from: "beginning of chapter"
reading-to: "end of chapter"
optional: true
authors:
  - Chris+Claude
tags:
  - optional
topic: "[[../Domains and Topics/11 Strategy/Predicting outcomes, not paths]]"
stage: beginner
eval-results:
  content-sha: ae70fd93
  date: 2026-08-19
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: fail}
  notes: {A2: "capability is about what one specific book claims regarding its own story, not a concept that survives outside the text", B1: "'The Coda' and 'the story' are load-bearing scaffolding; unparseable without the reading", C3: "levels 4 and 5 hard-require memorized text/course details ('not strange enough', M4, Chapters 7-9) rather than stating an idea conveyable in any wording"}
  evidence: {A2: "Distinguish the book's use of fiction as a form of argument from two common misreadings", B1: "The Coda steps outside the story to address a question readers often have", C3: "Notes that the story admitting it's \"not strange enough\" is part of this"}
---

## Test:
id:: 0d32640e-9e23-44c8-8dea-dc1f67564986
#### Question: Open
id:: 826bc7bd-990e-460f-bd0b-c63e52107e21
content:: The Coda steps outside the story to address a question readers often have: what, exactly, is the book predicting?

**The book isn't claiming the specific events of the story will occur. But it's also not saying the story is "just a thought experiment" with no predictive content. What is the precise claim it is making? And how would you respond to someone who says "but it's just sci-fi"?**

assessment-instructions::
Score out of 100: the sum of the elements below.

The question is about the book "If Anyone Builds It, Everyone Dies", which contains a fictional story of how a superintelligent AI could come to wipe out humanity. Its closing section (the Coda) says the specific events of the story are not a prediction (the authors chose that path for clarity and admit the real thing would likely be stranger), but the ending is a real prediction: if anyone builds superintelligence with anything like current methods and understanding, humanity loses and everyone dies. The question asks two things: what precise claim the book is making, and how the learner would answer someone who says "but it's just sci-fi".

50: The precise claim. Separates the path from the outcome: the specific events of the story are an illustration, not a forecast, while the outcome (that building superintelligence under current conditions leads to humanity's defeat or extinction) is a genuine prediction. An answer that only says the story is not a literal prediction, without saying what is still predicted, earns at most 15 here.
50: The answer to "it's just sci-fi". Gives a reasonable reply that rests on the distinction above. Any one of these, clearly made, earns the full 50:
- the invented details are not what carries the claim, and the argument for the outcome stands on its own, so pointing out that the details are made up does not touch it
- the story is a way to make an abstract argument concrete and easier to grasp, not evidence offered for itself
- the authors themselves say the details are not strange enough to be what really happens, so the label "sci-fi" applies only to the part they never claimed
- another reply that answers the objection by separating the made-up path from the predicted outcome

Cap at 30 if the answer says the book predicts that the story's specific events will happen, or that the book makes no prediction at all.

Model answer, for the feedback, not a grading checklist: "The book is not predicting the story's events. That path was picked to make things easy to follow, and the authors even say reality would probably be stranger. What it does predict is the ending: if someone builds a superintelligence with anything like today's understanding, humanity loses. To the 'it's just sci-fi' objection I would say that the fiction is only an illustration. The made-up details aren't what the claim rests on. The argument for the outcome stands without them, so calling the story sci-fi doesn't answer it."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they read the story as a literal forecast or as having no predictive content, ask which part the authors would actually bet on: the sequence of events, or where it ends.
- If they said it is not a literal prediction but could not say what is left, ask what is still being predicted once the specific events are set aside.
- If they separated the pathway from the outcome, ask how they would answer "it's just sci-fi": what can a story do that an abstract argument cannot, and what does the authors' admission that the story is not strange enough tell you?
- If they covered why fiction is used, ask why the Coda's explanation comes after the story rather than before it.

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: the authors say they chose the pathway for clarity. Ask what they did not choose for clarity, and so stand behind. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Fiction as Argument]]
``````````

## Alignment as alchemy
``````````markdown
---
id: 3e29b948-02b0-4fd3-847a-4c7adb05dd0d
learning-outcome: "State Chapter 11's central diagnosis as the chapter frames it: the alignment field is currently in the 'alchemy stage': producing results without understanding why they work, operating from high-minded philosophical ideals rather than engineering designs, and mistaking the ability to build more powerful AI for progress on making it safe."
reading-from: "beginning of chapter"
reading-to: "It is a level of systemic game that would have humanity headed for disaster, even if we were wrong about every other aspect of difficulty."
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/Why alignment is hard]]"
stage: beginner
eval-results:
  content-sha: fc29cbf0
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Statement is bound to a specific text's framing rather than a source-free capability; named as a corpus fail example in the A2 eval.", B1: "Question is scaffolded on the assigned chapter — it names Chapter 11 and its opening allegory, so it cannot be posed to someone who never read that text."}
  evidence: {A2: "State Chapter 11's central diagnosis as the chapter frames it", B1: "Chapter 11 opens with an allegory about a young alchemist"}
---

## Test: 
id:: 311a34f9-b4d2-46b8-813a-3b51869fe6c3
#### Question: Open
id:: 694d05ca-a88c-4ae9-9012-15594bedb758
content:: Chapter 11 opens with an allegory about a young alchemist who claims to be "close" to transmuting lead into gold despite having no understanding of why his recipes produce the results they do. The chapter then applies this framing to current AI alignment efforts, drawing on public statements from Elon Musk (xAI) and Yann LeCun (Meta). The authors call this the "alchemy stage" of a science.

**In your own words, what is Chapter 11's "alchemy stage" diagnosis of the AI alignment field? What specifically does the chapter claim is missing from the field's current state, and why does it matter that it is missing?**

assessment-instructions::
Score out of 100: the sum of the elements below.

The question is about a chapter that compares today's AI alignment field to alchemy. The alchemists had recipes that worked (they could make a strong acid that dissolves gold) without any chemistry to explain why, and they believed they were close to turning lead into gold with no principle to back that up. The chapter's diagnosis: alignment has techniques that sometimes produce results, but nobody understands why they work. Leading figures state high-minded ideals (for example "build a maximally truth-seeking AI" or "we will engineer their desires") instead of engineering designs that say how. And the ability to build more powerful AI is taken for progress on making it safe. The question asks what the diagnosis is, what is missing, and why it matters that it is missing.

60: The diagnosis and what is missing. Says the field works by trial and error or recipes, getting results without understanding why they work, so what is missing is real understanding: the principles or theory (a science, as chemistry is to alchemy) that would let people design an AI and know in advance how it will behave. Describing the field as reasoning from ideals or slogans rather than engineering designs also earns this, if the answer says what is missing is understanding of how to achieve them. Saying that progress in building more powerful AI is being mistaken for progress on making it safe is part of the same diagnosis and also counts here, but an answer does not need it for the full 60.
40: Why it matters. Gives a reason. Any one of these, clearly connected to the missing understanding, earns the full 40:
- without understanding you cannot tell whether a technique that works now will still work on a smarter system
- you cannot predict failures before they happen, and with superintelligence there may be no second chance to fix them
- confidence that comes from ignorance can't be corrected, since there is no theory that could show it wrong

Cap at 30 if the answer's main claim is only that alignment is hard, or that the field isn't trying hard enough or lacks funding.

Model answer, for the feedback, not a grading checklist: "Alignment today is like alchemy. People have techniques that sometimes work, but nobody understands why, the way alchemists could make acids without knowing any chemistry. Instead of designs, the field offers ideals like a 'truth-seeking AI'. And getting better at building powerful AI is being treated as if it were progress on safety. What's missing is real understanding of what goes on inside these systems and why. That matters because without it you can't know whether something that works today will still work on a much smarter system, and with superintelligence you may only get one try."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said only that alignment is hard or not working yet, ask what the alchemist had, recipes that sometimes worked, and what he lacked.
- If they said the field is at an early stage without saying what marks that stage, ask what separates an alchemist from a chemist who makes the same compound.
- If they had the diagnosis (techniques without understanding, ideals instead of designs, more capable AI taken as progress on safety), ask why that kind of ignorance is hard to correct: what would tell the alchemist he is wrong?
- If they had that, ask how they would keep the diagnosis from turning into blame or despair: is the field stuck for good, and what would leaving this stage look like?

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: Aqua Regia. Alchemists could make it reliably without any chemistry to explain why it worked. Ask what the alignment equivalent is. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Alchemy Not Science - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Alchemy Not Science]]
``````````

## Position, not despair
``````````markdown
---
id: 3ec603de-965b-429f-9dbc-b54bc2d86002
learning-outcome: "State Chapter 10's closing position ('NOBODY SHOULD BE ALLOWED TO TRY') and identify that the chapter presents this not as counsel of despair but as a logical conclusion from the combined weight of the five curses, distinguishing a position-statement from despair."
reading-from: "Space probes. Nuclear reactors. Computer security. What do all these lessons add up to, and what can we learn from them about the difficulty of aligning an artificial superintelligence?"
reading-to: "end of chapter"
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/13 Taking Action/Advocacy and movement strategy]]"
stage: beginner
eval-results:
  content-sha: 4afa9641
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is bound to reconstructing what Chapter 10 says (its closing position, its five curses), matching the 'State Chapter 11's central diagnosis' fail pattern.", B1: "Question is scaffolded on the specific chapter — it asks what Chapter 10's closing position is and how 'the chapter' wants it read, so it cannot be posed at a random moment."}
  evidence: {A2: "State Chapter 10's closing position ('NOBODY SHOULD BE ALLOWED TO TRY')", B1: "In your own words, what is Chapter 10's closing position, and how does the chapter want you to read it?"}
---

## Test:

id:: 3d3ca945-33d2-4a1b-a098-bc3571529754
#### Question: Open
id:: 9c8d98cc-6c71-42c1-a658-d52b2166e761
content:: Chapter 10 closes by mapping each of its three case-study domains (space probes, nuclear reactors, computer security) onto the ASI alignment problem, then states a blunt conclusion: "NOBODY SHOULD BE ALLOWED TO TRY." This phrasing reads to many people as despair: a counsel that nothing can be done. The authors mean something different.

**In your own words, what is Chapter 10's closing position, and how does the chapter want you to read it? Specifically, distinguish between despair (nothing can be done, so why bother) and a position-statement (a logical conclusion from evidence that calls for a specific kind of response).**

assessment-instructions::
Score out of 100: the sum of the elements below.

The question is about the end of a chapter that compares building a superintelligent AI with three hard engineering problems (a space probe you can't fix after launch, a nuclear reactor with fast self-amplifying forces, computer security against an intelligent adversary), adds that nobody understands the inside of today's AIs, and concludes "NOBODY SHOULD BE ALLOWED TO TRY". The question asks what that closing position is, how the chapter wants it read, and to distinguish despair (nothing can be done, so why bother) from a position-statement (a conclusion from evidence that calls for a specific kind of response).

35: The closing position. Says that nobody should attempt to build superintelligence, or that the attempt should be stopped. Credit any wording, such as "no one should be allowed to build ASI right now" or "the attempt itself should be stopped".
25: A conclusion from evidence. Says the line is the conclusion the chapter's argument reaches from the engineering difficulties (all of them, or the combined weight of them), not an emotional outburst or a general feeling of doom. Saying it depends on our current level of understanding also earns this.
40: Despair versus position-statement. Says that despair leads to giving up or doing nothing, while this position calls for action: preventing or stopping the attempt (for example by laws, bans or international agreements), or changing the conditions before anyone tries.

Cap at 30 if the answer reads the closing as despair, for example that the authors think nothing can be done.

Model answer, for the feedback, not a grading checklist: "The chapter ends with the claim that nobody should be allowed to try to build superintelligence. That isn't despair. It is the conclusion the chapter reaches after showing how the problems of space probes, reactors and computer security all apply at once, while nobody understands what goes on inside these AIs. Despair would say we're doomed whatever we do, so why bother. This position says that this attempt, with today's understanding, would fail, so don't make it. That calls for action: stop the attempt, for example through laws and agreements, until the conditions change."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they read the closing as despair, ask what "Nobody should be allowed to try" asks someone to do.
- If they sensed it is not despair but could not say why, ask what premises the conclusion is drawn from, and what would follow if those premises are right.
- If they made the distinction, ask what kind of action a position-statement calls for that despair does not, and what the chapter is preparing for later.
- If they had that, ask why a crafted system this hard might be fixed by working harder, and why a grown one cannot.

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: compare "we will fail no matter what" with "this attempt, with this level of understanding, will fail, so don't make it". Ask which one tells you to do something. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Position Not Despair - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Position Not Despair]]
``````````

## The five engineering curses
``````````markdown
---
id: 5e722d28-f1ad-487c-8866-43e5d48115ee
learning-outcome: "Enumerate the five engineering curses Chapter 10 names (speed, narrow margins, self-amplification, complications, and edge cases), and identify which case study (Chernobyl or computer security) illustrates each."
reading-from: "beginning of chapter"
reading-to: "Those constraints will tend to get in the way of the AI accomplishing one objective or another. And then you are matching your own wits and ability to nail down the edge cases against however much intelligence is flowing through the system, to see if your constraint holds up."
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/11 Strategy/One chance to get it right]]"
stage: beginner
eval-results:
  content-sha: 9cabb69d
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is defined as reconstructing what Chapter 10 names and which case study that chapter pairs with each curse, so it depends on knowing a specific text rather than a field-canonical framework.", B1: "Question makes the chapter load-bearing scaffolding, asking what Chapter 10 identifies and which illustration the chapter uses, so a capable non-reader cannot answer as posed."}
  evidence: {A2: "Enumerate the five engineering curses Chapter 10 names", B1: "Name the five engineering curses Chapter 10 identifies, and for each one, identify which case study (space probes, Chernobyl, or computer security) the chapter uses to illustrate it."}
---

## Test:
id:: d616e493-ef55-4429-8bae-e93d6fd20b99

#### Question: Open
id:: 55514d28-1482-41f4-ab4d-68d470fced52
content:: Chapter 10 frames AI alignment as a "cursed problem" by drawing on engineering case studies, among them Chernobyl-style nuclear reactors and computer security, to identify a small set of named "curses" that make engineering hard. The chapter argues that all of these curses apply to AI alignment, and that the curse of edge cases applies in a uniquely worse form.

**Name the five engineering curses Chapter 10 identifies, and for each one, identify which case study (Chernobyl or computer security) the chapter uses to illustrate it.**

assessment-instructions::
Score out of 100: the sum of the five curses below, 20 each.

The question asks the learner to name the five engineering curses the chapter identifies and, for each, the case study the chapter uses to illustrate it: the Chernobyl nuclear reactor or computer security. The chapter's mapping:
- Speed: Chernobyl (the reactor's reactions happen far faster than humans can respond).
- Narrow margins: Chernobyl (a tiny gap between a working reactor and a runaway one).
- Self-amplification: Chernobyl (the failure feeds itself: overheating boils off coolant, which makes the overheating worse).
- Complications: Chernobyl (an unexpected interaction, such as the graphite-tipped control rods that turned the emergency shutdown into an explosion).
- Edge cases: computer security (an unusual input, such as an overlong name that overflows memory, breaks a system that works on ordinary inputs).

For each curse: 10 for naming it, 10 for giving the chapter's case study for it. Credit plain or close names ("fast", "small margin for error", "feedback loop", "runaway reaction", "unexpected interactions", "too complicated", "weird inputs", "rare cases"). "Nuclear reactor" counts as Chernobyl and "hacking" or "cyber security" counts as computer security. A curse mapped to the wrong case study gets 0 of its 10 for the case study. If the answer grounds a curse in the right case study by describing the chapter's example (for example "the control rods at Chernobyl") that counts.

Model answer, for the feedback, not a grading checklist: "Speed: Chernobyl. Narrow margins: Chernobyl. Self-amplification: Chernobyl. Complications: Chernobyl. Edge cases: computer security."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they gave a general "AI is hard" answer, ask them to name one curse and the case study that shows it.
- If they named some curses but not all five, or did not map them, tell them plainly which curses they missed and ask which case study the chapter uses for each.
- If they named and mapped all five, ask why edge cases belong in a different category from the other four, and how that connects to AI being grown rather than crafted.

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: Chernobyl's control rods, whose graphite tips turned an emergency shutdown into an explosion. Ask which curse that is. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses]]
``````````

## The superalignment objection
``````````markdown
---
id: 3d95d5e3-b5dd-4ff8-90b8-24653db41a3d
learning-outcome: "Describe the strong version of superalignment as Chapter 11 presents it (using a smarter-than-human AI to solve the alignment problem), and state the chapter's two-step objection: (1) the AI capable of doing this would itself be too dangerous and untrustworthy, and (2) a 'special-purpose' alignment AI has no training examples of solved alignment and requires the precise dangerous skill set that makes an unaligned AI catastrophic."
reading-from: "Some AI companies do try to look less cavalier than that, about ASI alignment, and put forth plans more detailed than those."
reading-to: "end of chapter"
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/Why alignment is hard]]"
stage: beginner
eval-results:
  content-sha: 88f0c03d
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Statement is bound to a specific text's framing — describing what Chapter 11 presents and stating the chapter's objection, not a source-free capability.", B1: "Question uses the chapter as load-bearing scaffolding, repeatedly asking for what Chapter 11 says rather than self-containing the content."}
  evidence: {A2: "Describe the strong version of superalignment as Chapter 11 presents it ... and state the chapter's two-step objection", B1: "Describe the strong-superalignment proposal as Chapter 11 presents it. Then state the chapter's objection"}
---

## Test:
id:: fc3b7597-3165-46ee-af3a-a6990d9e98eb
#### Question: Open
id:: 0ea83c3b-5c18-41c2-94bf-363a3c57d2f1
content:: The most developed alignment plan Chapter 11 examines is "superalignment": the idea, made flagship at OpenAI in 2023, of using AI to help solve the alignment problem itself. The chapter splits this into two versions, weak (AI helps with interpretability research) and strong (a smarter-than-human AI solves alignment for us), and finds the strong version particularly broken.

**Describe the strong-superalignment proposal as Chapter 11 presents it. Then state the chapter's objection: specifically, why building the AI required to solve alignment cannot be done before alignment is itself solved. Also describe the chapter's response to "we'll just make a special-purpose alignment AI that isn't generally dangerous."**

assessment-instructions::
Score out of 100: the sum of the three elements below.

The question asks the learner to describe the "strong superalignment" proposal, to state the chapter's objection to it, and, if they can, the chapter's reply to the idea of a special-purpose alignment AI.

20: The proposal. Strong superalignment means building an AI smarter than the best human researchers and having it solve the alignment problem for us (not just helping humans with parts of the research, such as interpretability). Any plain description of "get a very capable AI to solve alignment on our behalf" earns these 20. An answer that only describes AI helping with interpretability research earns nothing here.

50: The objection. An AI capable enough to solve alignment would itself be powerful and dangerous, and nobody can trust or safely build an AI that capable until alignment is already solved. So the plan needs the solution before it can start: it is circular. Credit any wording of this idea, for example "you would need an aligned superintelligence to get an aligned superintelligence". An answer that says only that the plan won't work, or that it is risky, with no reason why, earns at most 10 here.

30: The reply to "just build a special-purpose alignment AI that isn't generally dangerous". The chapter gives three reasons it fails: there are no examples of solved alignment to train such an AI on, so it must generalise from related skills. The skills it would need (programming, how AIs are grown, what AIs want, human psychology) are exactly the skills that make an unaligned AI dangerous. And when it hands you an alignment plan you cannot check it, so you end up trusting the AI or its persuasive argument. Any one of these reasons, stated clearly, earns 20. Two or more earn 30.

Cap at 40 if the answer's main objection is that today's AI is not yet smart enough to solve alignment, since the chapter's point is that an AI that is smart enough would be the danger.

Model answer, for the feedback, not a grading checklist: "Strong superalignment is the plan to build an AI smarter than our best researchers and have it solve alignment for us. The problem is circular: an AI capable of that is exactly the kind of AI that is dangerous if it isn't aligned, and we can't trust it or safely build it until we have already solved alignment. A special-purpose alignment AI doesn't escape this. There are no worked examples of solved alignment to train it on, the skills it would need (understanding programming, AI internals and human minds) are the dangerous ones, and if it hands us a plan we can't verify it, so we'd just be trusting the thing we can't trust."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they described weak superalignment or interpretability, ask what the strong version expects the AI itself to produce.
- If they described the plan but not the objection, ask how capable the AI would have to be to solve alignment, and what you would need before you could safely build something that capable.
- If they had the circular dependency, ask about the special-purpose AI: what would it train on, what skills would it need, and how would you check its answer?
- If they had that, they have full marks. You may offer one extension: how does a biomedical AI compare, and why can its output be checked when an alignment proposal cannot?

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: the first step of the plan is an AI smart enough to solve a problem humanity's best researchers cannot. Ask what has to be true before you can trust that step. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Strong Superalignment Objection - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Strong Superalignment Objection]]
``````````

## Narrow coalition strategy
``````````markdown
---
id: c3a91f47-8d52-4e6b-b187-5f0c9e4d2a68
learning-outcome: "State the chapter's coalition strategy: what the anti-extinction coalition's ask must be limited to, what positions it must not bundle with that ask, and the reason the chapter gives for keeping the coalition narrow."
reading-from: "The solutions we've just proposed are a far cry from the policies that other concerned folks propose."
reading-to: "end of chapter"
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/13 Taking Action/Advocacy and movement strategy]]"
stage: beginner
eval-results:
  content-sha: 52de31b4
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is defined as reconstructing what one specific chapter says, not a source-free coalition-strategy capability.", B1: "Question makes a named chapter load-bearing scaffolding; a reader who never read it cannot parse 'the chapter's coalition strategy'."}
  evidence: {A2: "State the chapter's coalition strategy: ... and the reason the chapter gives for keeping the coalition narrow.", B1: "Chapter 13's final section argues that the coalition working to prevent AI-caused extinction must be built in a very specific way."}
---

## Test:
id:: a5d28e63-9b47-4f05-c834-1e7a2b0d9f46
#### Question: Open
id:: 3fae78ed-9f1c-4d5d-9a73-3ae2d1b5dc37
content:: Chapter 13's final section argues that the coalition working to prevent AI-caused extinction must be built in a very specific way. The chapter names what the coalition should ask for, what it should not bundle with that ask, and explains why keeping the coalition narrow is a strategic necessity rather than a weakness.

**In your own words, what is the chapter's coalition strategy? What must the ask be limited to, what must it not include, and why does the chapter argue the coalition should stay narrow?**

assessment-instructions::
Score out of 100: the sum of the three elements below.

The question asks for the chapter's strategy for the coalition working to prevent AI-caused human extinction: what its ask must be limited to, what it must not include, and why the coalition should stay narrow. The chapter's position: the only ask is that humanity must not go extinct (from superintelligence), which nearly everyone can agree on. It must not be bundled with other positions, such as opposing killer robots or AI-driven job loss. Bundling any other position risks breaking the coalition, and a failed coalition risks extinction. Other issues can be pursued separately.

30: What the ask is limited to: preventing human extinction from AI (stopping the development of AI that could kill everyone). Any wording of this one aim earns these 30.

30: What it must not include: other AI-related causes or political positions bundled in with that ask. Any fitting example (killer robots, job loss, deepfakes, bias, or another adjacent issue), or a clear general statement that no other cause gets added, earns these 30.

40: Why it should stay narrow: nearly everyone can agree humanity should not go extinct, but each added position brings in disagreement that can split the coalition or get the whole package rejected, and losing on this one goal means extinction, so the core ask cannot be put at risk. An answer that gives the reason as disagreement driving supporters away or sinking the package earns these 40. An answer that says only "to stay focused" or "not to get distracted", with no reason narrowness keeps the coalition together, earns at most 15 here.

Cap at 30 if the answer says the coalition should combine as many AI concerns as possible to win broad support.

Model answer, for the feedback, not a grading checklist: "The coalition should ask for one thing: that AI not be allowed to drive humanity extinct. It must not bundle that with other causes such as opposing killer robots or job losses to AI, however related they feel. Nearly everyone can agree that humanity shouldn't go extinct, but every extra position brings people who disagree with it, and one of those disagreements can break the coalition or sink the whole package. If this coalition fails the cost is extinction, while the other issues can still be fought for separately."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they argued for the broadest possible coalition, ask what single ask almost everyone could agree on.
- If they had a general sense of focus, ask what exactly the ask is, which positions should stay out of it, and why.
- If they had all three parts, they have full marks. You may offer one extension: what does each choice cost: what is lost if a bundled package fails, and what is lost by keeping it narrow?
- If they had that asymmetry, ask how it answers advocates who wrap their extinction concerns inside broader regulation.

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: the chapter's line that legislators "smell something rotten and throw the whole package out". Ask what made the package smell rotten. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Coalition Strategy - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Coalition Strategy]]
``````````

## The WWII analogy
``````````markdown
---
id: e7f2a831-4c65-4b9d-a023-8d1f6e2c7b34
learning-outcome: "Explain how the chapter's WWII analogy responds to the objection that coordinating major powers on AI restriction is politically impossible: what specific feature of the WWII precedent does the chapter invoke, and what claim about human motivation does it rely on?"
reading-from: "beginning of chapter"
reading-to: "…as was also true about World War II. But we don't know how else humanity could survive."
authors:
  - Chris+Claude
topic: "[[../Domains and Topics/10 Governance and Policy/International coordination]]"
stage: beginner
eval-results:
  content-sha: 734b92a1
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: fail, C3: fail}
  notes: {A2: "Capability is defined as reconstructing what a specific chapter argues, not a source-free capability.", B1: "Question is scaffolded on a named chapter and asks what 'the chapter' does, so it cannot be posed to someone who never read it.", C2: "Pass level (3) requires quantitative figures the question never asks for; it asks only for the 'specific feature' invoked.", C3: "Level-3 criterion hard-requires memorized quantitative details rather than stating the idea that must be conveyed in any wording."}
  evidence: {A2: "Explain how the chapter's WWII analogy responds to the objection", B1: "Chapter 13 opens with a parable about the Allied Powers in World War II", C2: "approximately $6 trillion and 60–80 million personnel", C3: "extraordinary scale and cost: approximately $6 trillion and 60–80 million personnel"}
---

## Test:
id:: f9c4b820-5a71-4d83-9e12-7b3f0c5d8a91
#### Question: Open
id:: 6cd27693-bd59-41dd-a46b-ce1b29efb50a
content:: Chapter 13 opens with a parable about the Allied Powers in World War II: military drafts, food rationing, soldiers sent to die, enormous expense, all to prevent totalitarianism from conquering the world. The chapter then addresses those who believe international coordination on AI restriction is politically impossible. The WWII story is the chapter's direct answer to that objection.

**In your own words, how does the chapter use the WWII analogy to respond to the claim that coordinating major powers on AI restriction is politically impossible? What specific feature of WWII does it invoke, and what does it assume about what people are capable of?**

assessment-instructions::
Score out of 100: the sum of the three elements below.

The question asks how the chapter uses World War II to answer the objection that getting the major powers to coordinate on restricting AI is politically impossible, what feature of WWII it points to, and what it assumes people are capable of. The chapter's facts: the Allies drafted soldiers, rationed food, sent people to die and spent enormously (about 6 trillion dollars today, 60 to 80 million personnel), many of them people not personally threatened by the Axis. The chapter says anyone who calls AI coordination impossible is claiming countries could not care even 1% as much as they cared about fighting WWII. Its assumption: people sometimes do things they don't usually do when they realise their freedom or way of life is at stake.

35: The feature of WWII: the sheer scale and cost of what the Allied countries did together (drafts, rationing, huge spending, tens of millions mobilised, including people not directly at risk). Any clear statement that countries coordinated an enormous, costly effort earns these 35. A bare "countries cooperated in WWII" with nothing about the scale or sacrifice earns 15.

35: How this answers the objection: countries have already done something far bigger and costlier than restricting AI once they saw the threat, so calling AI coordination impossible means claiming they could not care even a small fraction as much. Credit any wording of "they did far more before, so far less is not impossible". The 1% figure itself is not needed.

30: The assumption about people: when people realise their freedom, way of life or survival is at stake, they are capable of unusual sacrifice and cooperation they would not normally accept. Any wording of this idea earns these 30.

Model answer, for the feedback, not a grading checklist: "The chapter points to how much the Allies were willing to do in WWII: drafts, rationing, soldiers sent to die, enormous spending, including by people the Axis never directly threatened. Restricting AI asks far less than that. So saying coordination is impossible is really saying countries could not care even 1% as much about AI as they did about the war, which the chapter finds implausible. It rests on the assumption that people will do things they don't normally do once they realise their freedom or way of life is at stake."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they did not connect the analogy to the objection, ask what the objection says is impossible and what WWII shows countries actually did.
- If they said only that countries can cooperate, ask what the scale and cost of the mobilization show, and what the chapter's "even 1% as much" comparison claims. If the answer lacks the figures, give them: roughly 6 trillion dollars and 60 to 80 million personnel.
- If they had the scale and the 1% comparison, ask what the chapter assumes about people: why would they do something they do not usually do?
- If they had that, they have full marks. You may offer one extension: does the analogy claim the task is easy, and how does it turn "impossible" into a question of how much people care?

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: the 1% comparison. Ask whether countries could care about AI restriction even one percent as much as they cared about the war. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The WWII Analogy - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The WWII Analogy]]
``````````

## Role-specific action
``````````markdown
---
id: 5b0c3d94-6e1f-5042-d7c8-e9f0a1234567
learning-outcome: "Distinguish between the chapter's calls to action for government leaders, for skeptical politicians, and for ordinary citizens: what specific levers does each group hold that the others do not?"
reading-from: "So—how do we un-write our fate?"
reading-to: "end of chapter"
authors:
  - Chris+Claude
topic: "[[../Domains and Topics/13 Taking Action/Advocacy and movement strategy]]"
stage: beginner
eval-results:
  content-sha: 191bd5db
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is bound to one text — it asks for the chapter's calls to action, not a source-free capability.", B1: "Question names the specific reading as load-bearing scaffolding; unanswerable as posed without knowing that chapter."}
  evidence: {A2: "Distinguish between the chapter's calls to action for government leaders", B1: "The second half of Chapter 14 issues different calls to action to different audiences"}
---

## Test:
id:: 6c1d4ea5-7f20-5153-e8d9-f0a1b2345678

#### Question: Open
id:: f5ecf31b-f5ec-4983-99aa-e156d3d26247
content:: The second half of Chapter 14 issues different calls to action to different audiences: government leaders, elected officials who are already persuaded, politicians who are not yet persuaded, journalists, and ordinary citizens.

**Distinguish what the chapter asks of (a) government leaders, (b) skeptical politicians who aren't fully persuaded, and (c) ordinary citizens. What specific lever does each group hold that the other two cannot provide?**

assessment-instructions::
Score out of 100: the sum of the elements below.

The question asks what Chapter 14 asks of three groups (government leaders, politicians not yet persuaded of the risk, ordinary citizens) and what lever each holds that the other two cannot provide. What the chapter asks:
- Government leaders: signal openness to an international treaty to halt advanced AI development, so that other major powers will not feel disadvantaged by agreeing. The ask is not a unilateral halt, it is a diplomatic opening.
- Skeptical politicians: even without accepting the full risk argument, require that GPU clusters (the big AI chip data centres) be concentrated in a few monitorable places now, so a halt is still possible later if they change their minds. Once the chips have spread everywhere, that option is gone.
- Ordinary citizens: make the issue a political priority by writing to their representatives, voting with it in mind (especially in primaries), joining large lawful protests and talking about it, so that politicians have public backing to act.

25: government leaders' ask, as above: a signal of willingness to join a treaty so others can agree without being disadvantaged. Any wording that carries this idea earns the full 25. A generic "make treaties" or "regulate AI" earns 10. Saying the chapter asks governments to halt on their own earns 5.
25: skeptical politicians' ask, as above: concentrate the chips or data centres now, so the option to halt stays open, without needing to be persuaded first. Any wording that carries this idea earns the full 25. A generic "vote for regulation" or "listen to experts" earns 10.
25: citizens' ask, as above: political pressure through representatives, votes, lawful protest or conversation. Two or more of these, or one with the point that it gives politicians backing, earns the full 25. A single generic "protest" or "speak up" earns 15.
25: why no group can stand in for another: each lever rests on something the others lack. Governments carry the state-level credibility another country needs before it will agree. Politicians hold the lawmaking or regulatory power to concentrate chips, which citizens do not have. Citizens supply the votes and public pressure that let politicians and governments act without political risk. A reason for each group, stated separately or as a chain (citizens back politicians, politicians enable governments, governments make a treaty possible), earns the full 25. A reason for only some groups earns a share in proportion.

Model answer, for the feedback, not a grading checklist: "Government leaders are asked to signal that they would join an international treaty to stop the race, not to halt alone, so other powers can agree without fearing they lose out. Only a state can make that offer credibly to another state. Skeptical politicians are asked to require that AI chip clusters be gathered in a few monitored data centres now, even if they are not convinced, so a halt stays possible if they change their minds. That takes lawmaking power ordinary people don't have. Citizens are asked to write to their representatives, vote on it, especially in primaries, protest lawfully and talk about it. That public pressure is what gives politicians the cover to act, and no official can create it for themselves. Each lever needs a kind of authority the others lack, so none can substitute for another."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they gave all three groups the same role, ask what a head of government can do that an ordinary citizen cannot.
- If they gave generic roles (treaties, votes, protests), ask what the chapter specifically asks of each group, for instance whether it asks governments for a unilateral halt.
- If they had two of the three levers, tell them which group they missed and ask what the chapter asks of that group.
- If they had all three, ask why none of the groups could stand in for another: what authority or credibility does each lever need?

At full marks, just confirm briefly. Don't cite point values or recite the rubric. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: the skeptical politician. The chapter asks them to concentrate GPU clusters now, even unconvinced. Ask why that would matter if they later change their mind. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Role-Specific Action - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Role-Specific Action]]
``````````

## Un-writing our fate
``````````markdown
---
id: 3f8a1b72-4c9d-4e20-b5a6-c7d8e9f01234
learning-outcome: "State what the chapter means by 'un-writing a fate already written,' and identify the nuclear precedent it uses to show this is possible."
reading-from: "beginning of chapter"
reading-to: "And civilization lived."
authors:
  - Chris+Claude
topic: "[[../Domains and Topics/10 Governance and Policy/International coordination]]"
stage: beginner
eval-results:
  content-sha: c3cb608a
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is explicitly about the text's presentation ('what the chapter means', 'the nuclear precedent it uses'), not a concept standing on its own outside the course.", B1: "Question is scaffolded on the assigned text — names Chapter 14 and repeatedly frames the ask as what 'the chapter' says, so a non-reader cannot answer as posed."}
  evidence: {A2: "State what the chapter means by 'un-writing a fate already written,' and identify the nuclear precedent it uses to show this is possible.", B1: "Chapter 14 opens with Vesna Vulović ... what does the chapter mean by \"un-writing a fate already written\"?"}
---

## Test:
id:: 4a9b2c83-5d0e-4f31-c6b7-d8e9f0123456

#### Question: Open
id:: d9da4232-9cb8-4b6e-a489-177a769365a1
content:: Chapter 14 opens with Vesna Vulović, a flight attendant who survived a 10.1-kilometer fall when terrorists bombed her plane. The chapter then invokes the nuclear arms race: in 1952, a nuclear war seemed rationally predictable based on centuries of evidence about human conflict, yet it didn't happen. The chapter calls what prevented it "un-writing a fate already written."

**In your own words: what does the chapter mean by "un-writing a fate already written"? What happened during the Cold War that the chapter uses as evidence that un-writing a fate is actually possible?**

assessment-instructions::
Score out of 100: the sum of the two elements below.

The question asks what the chapter means by "un-writing a fate already written", and what happened during the Cold War that the chapter uses as evidence that this is possible. The chapter's facts: in 1952, centuries of evidence about human conflict made a nuclear war look rationally predictable, yet it never happened. It was avoided because for the first time everyone who could start the war expected to suffer from it personally, and because of decades of deliberate work: arms agreements, monitoring, direct lines between the superpowers, and individual restraint (for example Vasily Arkhipov refusing to approve a nuclear torpedo launch in the Cuban Missile Crisis).

40: The meaning: an outcome that the evidence made look predictable, as good as decided, can be prevented when people deliberately act against it. It is changed by effort and choice, not by luck or by waiting. Any wording of "a catastrophe that seemed inevitable gets averted because people work to stop it" earns these 40.

60: The Cold War evidence: nuclear war looked likely or predictable, yet it did not happen, and people actively worked to prevent it. Earns the full 60 if it says the expected nuclear war did not happen and names at least one thing people did or that changed, such as arms control treaties, inspections or monitoring, the hotline, decades of diplomacy, Arkhipov's refusal, or leaders realising they would personally suffer from the war. An answer that says only that nuclear war was avoided, with nothing about how, earns 30.

Cap at 40 if the answer says nuclear war was avoided mainly by luck.

Model answer, for the feedback, not a grading checklist: "Un-writing a fate means preventing a disaster that the evidence made look all but certain, by deliberately working against it, not by luck or waiting. In the early 1950s nuclear war looked predictable from centuries of history, yet it never came. That was because, for the first time, the people who could start the war knew they would suffer from it themselves, and because people worked for decades on arms agreements, monitoring and direct lines between the superpowers."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they read the phrase as luck or waiting for things to turn out fine, ask whether nuclear war was avoided by chance or by something people did.
- If they said only that we can change the future, ask what people actually did during the Cold War.
- If they named the deliberate effort, ask why it worked: what had changed for the people who could start a nuclear war, and how long did the effort have to last?
- If they had that, they have full marks. You may offer one extension: how does it carry over to AI? Is the chapter saying things will turn out fine, or something else?

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: in 1952, centuries of evidence about human conflict pointed to war. Ask what was different this time. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Un-Writing Our Fate - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Un-Writing Our Fate]]
``````````

## The ladder in the dark
``````````markdown
---
id: e7a6096d-ef44-4f48-b2d1-53307f8d99ee
learning-outcome: "Apply the ladder-in-the-dark framing to explain why uncertainty about the fatal rung does not protect against predictable disaster: trace the chapter's argument that if climbing cannot be stopped while uncertainty remains, death is a predictable collective outcome, even though no specific rung can be identified as lethal in advance."
reading-from: "An AI company executive who says there's only a one-in-five chance that the AI they're building will kill literally everyone (as they do) is not in quite as much denial as the Soviet managers who denied the Chernobyl meltdown after it happened."
reading-to: "end of chapter"
authors:
  - Chris+Claude
topic: "[[../Domains and Topics/11 Strategy/Predicting outcomes, not paths]]"
stage: beginner
eval-results:
  content-sha: 0416884d
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: fail, C3: fail}
  notes: {A2: "Statement is bound to a specific text: it asks the learner to reconstruct what the chapter argues, matching the 'State Chapter 11's central diagnosis as the chapter frames it' fail pattern.", B1: "Question is scaffolded on the assigned text — it names Chapter 12 and asks the learner to trace that chapter's argument, so a capable non-reader cannot answer as posed.", C2: "Pass level 3 hard-requires naming the chapter's three specific actor categories, which the question never asks for or implies.", C3: "Level 3 requires a memorized taxonomy verbatim ('the three types of actors...') rather than stating the idea in any wording; level 5 likewise hard-requires the specific CERN example with no 'or equivalent' allowance."}
  evidence: {A2: "trace the chapter's argument that if climbing cannot be stopped while uncertainty remains", B1: "Chapter 12 closes with a striking image: every competing AI company is climbing a ladder in the dark.", C2: "the three types of actors (researchers/companies, corporate executives, world leaders) each have incentives to keep climbing", C3: "connects to the CERN comparison the chapter uses to close"}
---

## Test:
id:: 38dc6bd8-b793-448e-a44a-89d3cd4c6a03
#### Question: Open
id:: 8cb60110-0a9e-46c1-bf92-29af1920ea39
content:: Chapter 12 closes with a striking image: every competing AI company is climbing a ladder in the dark. Nobody knows which rung will be the last safe one: the point at which an AI system crosses into unrecoverable territory. You might expect this uncertainty to provide protection: if no one knows where the lethal rung is, perhaps caution will prevail. Chapter 12 argues the opposite. 

**Using the ladder-in-the-dark framing, explain why uncertainty about the fatal rung does not protect against predictable disaster. Trace the chapter's argument that if climbing cannot be stopped, death is a predictable collective outcome, even though no one can identify which rung is lethal in advance.**

assessment-instructions::
Score out of 100: the sum of the two elements below.

The question uses the chapter's image of AI developers climbing a ladder in the dark: nobody knows which rung is the last safe one, past which an AI becomes dangerous beyond recovery. It asks why this uncertainty does not protect against disaster, and why, if the climbing cannot be stopped, everyone dying is a predictable shared outcome even though nobody can say which rung is lethal. The chapter's facts the learner may use: AI company executives openly put the chance their AI kills everyone at around one in five and keep building anyway, because a company or country that stops hands the lead to a rival, possibly a less careful one. Researchers, executives and world leaders all face this pressure.

50: Why the uncertainty does not stop anyone. The pressure to keep climbing comes from competition, not from knowing where the danger is: whoever stops falls behind a rival, so each actor keeps going even while believing the risk is serious. Not knowing where the lethal rung is gives nobody a clear point at which to stop. An answer that makes this point through any actor (a company, an executive, a government) earns these 50. An answer that names the race but does not say why uncertainty fails to slow it earns at most 25 here.

50: Why the outcome is still predictable. If the climbing continues and some rung ahead is lethal, continuing to climb will reach it eventually, so the end point can be predicted even though the exact rung cannot. And because it is the whole group that keeps climbing, no single actor can prevent it by stopping alone. Any wording of "you can predict where it ends without knowing exactly when" earns these 50. An answer that says only that disaster is likely, with no reason why the end point is predictable without knowing the rung, earns at most 20 here.

Cap at 20 if the answer argues that the uncertainty makes caution, and so safety, likely.

Model answer, for the feedback, not a grading checklist: "Uncertainty would only protect us if it made people stop, and it doesn't. The reason to keep climbing is competition: a lab or a country that pauses just hands the lead to a rival, so executives who think there is a one-in-five chance of killing everyone keep building. Not knowing where the deadly rung is gives nobody a signal to stop. But if some rung is deadly and nobody can stop climbing, the climb reaches it sooner or later. You can't say which rung, yet you can predict how it ends, and no single climber can change that by stepping off alone."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they treated uncertainty as a reason for hope, ask what each company does at the next rung when it cannot tell whether that rung is the lethal one.
- If they named the race but not why uncertainty fails to protect, ask whether the climbing depends on anyone knowing where the lethal rung is, or on something else.
- If they traced why each actor keeps climbing, ask why no single actor can fix this even when each is acting sensibly.
- If they had that, they have full marks. You may offer one extension: what does a pause-and-calculate process look like elsewhere, as in the chapter's CERN example, and what does AI development have in its place?

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: the executive who believes there is a 20 percent chance of killing everyone and keeps building. Ask what keeps them building. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Ladder in the Dark - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Ladder in the Dark]]
``````````

## The one-chance problem
``````````markdown
---
id: 057e2d7c-1364-4436-a5d6-4d4799f31a0a
learning-outcome: "Compare the Chernobyl and Titanic analogies as Chapter 12 deploys them: explain what each case contributes to the argument that humans struggle to believe in unthinkable disasters, and identify the critical disanalogy between those historical cases and an ASI failure that the chapter treats as decisive."
reading-from: "beginning of chapter"
reading-to: "With ASI, there is no second time."
authors:
  - Chris+Claude
topic: "[[../Domains and Topics/11 Strategy/One chance to get it right]]"
stage: beginner
eval-results:
  content-sha: f0502c15
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is bound to what Chapter 12 says and treats as decisive, not to a source-independent concept.", B1: "Question makes the chapter load-bearing scaffolding rather than self-containing its context."}
  evidence: {A2: "as Chapter 12 deploys them", B1: "Chapter 12 opens by asking why smart, well-meaning people build things that could destroy the world."}
---

## Test:
id:: 7f627b30-5641-48ef-901d-e710813fb828
#### Question: Open
id:: 4fc0ef19-14a5-44cd-96e0-e8d3c6a99f38
content:: Chapter 12 opens by asking why smart, well-meaning people build things that could destroy the world. To make the denial pattern concrete, it draws on two historical disasters: the Chernobyl meltdown and the Titanic sinking. Even when the warning signs are present, both cases show how humans fail to believe that unthinkable disasters can actually happen. The chapter then makes a pivot: it argues these analogies hold only up to a point, because there is one critical way in which an ASI failure differs from both of them.

**What does each case (Chernobyl and Titanic) contribute to Chapter 12's argument that humans struggle to believe in unthinkable disasters? And what is the critical disanalogy between those historical cases and an ASI failure that the chapter treats as decisive?**

assessment-instructions::
Score out of 100: the sum of the three elements below.

The question asks what each of two historical disasters, the Chernobyl meltdown and the Titanic sinking, contributes to the chapter's argument that humans struggle to believe in unthinkable disasters, and what difference between those cases and an AI (superintelligence) catastrophe the chapter treats as decisive. The chapter's points: at Chernobyl, the people in charge of the reactor denied the meltdown was happening even as it happened. With the Titanic, the belief that the ship was unsinkable shaped decisions beforehand (too few lifeboats, iceberg warnings not taken seriously). After both, people investigated and improved safety. With superintelligence there is no second time.

25: What Chernobyl contributes: the people responsible for a dangerous system, the experts in charge, refused to believe it was failing, even while it was failing. Any wording of "denial by those running it, during the disaster" earns these 25.

25: What the Titanic contributes: confident belief that the technology was safe ("unsinkable") led to poor preparation before the disaster, such as too few lifeboats or ignored warnings. Any wording of "overconfidence beforehand shaped the preparations" earns these 25.

If the answer gives both cases only one shared generic point (for example "both show people ignored warnings") with nothing that tells them apart, award 20 in total for these two elements.

50: The decisive difference: after Chernobyl and the Titanic, people survived to learn from the failure and improve (investigations, new safety rules, more lifeboats), but a superintelligence failure would end humanity, so there is no second attempt and no chance to learn from the mistake. Any wording of "with AI we only get one try" earns these 50. An answer that says only that AI is more dangerous or bigger in scale, without the point that there is no chance to learn and try again, earns at most 15 here.

Model answer, for the feedback, not a grading checklist: "Chernobyl shows the people running a dangerous system denying that it is failing even while it fails. The Titanic shows confident belief that a technology is safe shaping the preparations beforehand: an unsinkable ship doesn't need many lifeboats. Together they show that failing to believe in an unthinkable disaster is a recurring human pattern. The decisive difference is that both disasters were survivable: afterwards people investigated and reformed. With a superintelligence there is no second time, so we cannot learn from the failure, and we have to get it right before we act."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they ran the two cases together into "people ignored warnings", ask what Chernobyl shows about the people running the system and what Titanic shows about how people saw the technology beforehand.
- If they had one case or no disanalogy, ask what happened after each disaster that could not happen after an ASI failure.
- If they had both contributions and the disanalogy, they have full marks. You may offer one extension: what changes about the decision to proceed when you cannot learn from a failure?
- If they already said that too, ask how the two halves fit together: what does the denial pattern mean for meeting that higher bar?

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: after the Titanic, ships were required to carry more lifeboats. Ask who would be around to write the new rules after an ASI failure. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The One-Chance Problem - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The One-Chance Problem]]
``````````

## The two prayers
``````````markdown
---
id: b1c2d3e4-f5a6-7890-bcde-f01234567890
learning-outcome: "Distinguish what each prayer asks of humanity: what would need to happen in the real world for the first prayer to be answered, and for the second?"
reading-from: "beginning of chapter"
reading-to: "end of chapter"
authors:
  - Chris+Claude
topic: "[[../Domains and Topics/11 Strategy/One chance to get it right]]"
stage: beginner
eval-results:
  content-sha: 4b9b4ebf
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "The capability is reconstructing what one specific book's closing passage says; 'the two prayers' is not a field-canonical frame and is meaningless to someone who never read that text.", B1: "Question relies on the assigned text as scaffolding — names 'The Closing Words', 'the authors', and leaves the second prayer identified only as 'the book's final line'."}
  evidence: {A2: "Distinguish what each prayer asks of humanity", B1: "The Closing Words offer two prayers. ... The second, which the authors call their \"true last prayer,\" is the book's final line."}
---

## Test:
id:: c2d3e4f5-a6b7-8901-cdef-012345678901

#### Question: Open
id:: 66253fbc-ee8f-4ea1-88f2-222b8f7b31c0
content:: The Closing Words offer two prayers. The first asks that the authors be proven wrong, shamed, and forgotten. The second, which the authors call their "true last prayer," is the book's final line.

**Distinguish what each prayer asks for. What would need to happen in the real world for the first prayer to be answered? For the second? And why do the authors call the second prayer their "true" one?**

assessment-instructions::
Score out of 100: the sum of the elements below.

The question is about the two prayers at the end of the book "If Anyone Builds It, Everyone Dies", whose authors argue that building superintelligent AI would kill everyone. The first prayer: that the authors be wrong, shamed for how wrong they were, and forgotten except as an example of how not to think, and that humanity live happily ever after. Between the two the authors say they will not put their last hope in doing nothing. The second, their "true last prayer", is the book's final line: "Rise to the occasion, humanity, and win."

30: what each prayer asks for (15 each). First: that the authors' warning turn out wrong and humanity be fine. Second: that humanity rise to the challenge and win. Any wording that carries these ideas earns the points.
30: what would have to happen in the real world for each to be answered (15 each). First: AI turns out not to be the danger the authors describe, so things go well without anyone needing to act. Second: people actually act and succeed in averting the catastrophe, for example by stopping the race to superintelligence through laws or international agreements. Any concrete or general form of collective action that succeeds counts.
40: why the second is the "true" one. The authors would genuinely prefer the first, but they will not stake everything on simply being wrong, that is on doing nothing and hoping. So the prayer they actually stand behind, and ask of the reader, is the call to act. Hoping to be wrong and acting as if you are right do not conflict. An answer that gives this reason in any wording earns the full 40, whether or not it states the "no conflict" point separately, as long as it does not set the two prayers against each other. An answer that only calls the second "more realistic" or "more important" with no reason earns 15. Cap the total at 60 if the answer says the authors do not really want to be wrong.

Model answer, for the feedback, not a grading checklist: "The first prayer asks that the authors be proven wrong and forgotten and that humanity simply be fine. For that, AI would have to turn out not to be the threat they describe, so things go well without anyone doing anything. The second asks humanity to rise to the occasion and win. For that, people would have to act and actually avert the danger, for instance by agreeing to stop the race to superintelligence. The second is their true prayer because they won't bet everything on being wrong. They would love the first outcome, but hoping to be wrong is not a plan, so what they actually ask of us is to act. Both can be held at once: hope you're wrong, and act as if you're not."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they ran the two prayers together, ask what the first asks to happen to the authors and what the second asks of humanity.
- If they named both but not the conditions, ask what the world would look like if each were answered: in one the authors were simply wrong, in the other people acted and won.
- If they had both conditions but not why the second is the true one, ask why the authors would not rest on the first.
- If they had that, ask whether the two prayers conflict: can someone hope to be wrong and still act as if they are right?

At full marks, just confirm briefly. Don't cite point values or recite the rubric. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: the second prayer is the book's last line, "Rise to the occasion, humanity, and win." Ask what it requires that the first does not. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The Two Prayers - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The Two Prayers]]
``````````

## Intelligence as prediction plus steering
``````````markdown
---
id: cafc40b7-fb3a-4415-9b1d-c65b85329b73
learning-outcome: "Define intelligence as prediction plus steering, explain why generality drives its power, and distinguish predictive competence from the goals steering pursues."
reading-from: "IMAGINE, IF YOU would—though of course nothing like this ever happened, it being just a parable—that biological life on Earth had been the result of a game between gods."
reading-to: "it is still in some important sense 'shallow' compared to a human twelve-year-old."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/1 Artificial Intelligence/What intelligence is]]"
stage: beginner
eval-results:
  content-sha: 2fd083f6
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question requires the chapter as scaffolding; not parseable by someone who never read it."}
  evidence: {B1: "Using the chapter's framework, analyze the three systems."}
---

## Test:
id:: b5981716-08c0-40b1-a005-2cfbdde6d0c7
#### Question: Open
id:: 8ba818e9-5340-44ff-a346-7fa476b77acb
content::
Two systems accurately predict that a severe storm will close a bridge. One routes delivery trucks away from it to minimize delays. The other routes rescue vehicles toward it to reach stranded people. A third system is exceptionally good at this routing task but cannot reason outside transportation.

Using the chapter's framework, analyze the three systems. What are the first two doing when they predict and when they steer? Does choosing different destinations show that one is less intelligent? What distinguishes the third system from a more general reasoner?

assessment-instructions::
Score out of 100: the sum of the three elements below.

The scenario: two systems both correctly predict that a storm will close a bridge. One routes delivery trucks away from the bridge to keep delays low. The other routes rescue vehicles toward it to reach stranded people. A third system routes vehicles exceptionally well but cannot reason about anything outside transportation. The framework the question refers to defines intelligence as prediction plus steering: predicting is forming correct expectations about what will happen, steering is choosing actions that bring about an outcome the system is aiming for. A mind is more general the wider the range of domains in which it can predict and steer.

35: What the first two systems do when they predict and when they steer. Predicting: both form the same correct expectation that the bridge will close. Steering: each picks routes that lead to its own goal (avoiding delay, reaching the stranded people). Any wording that keeps "what will happen" apart from "what to do about it" earns this.

35: Different destinations do not show that either system is less intelligent. Both predicted equally well, and each steers well toward its own goal. Success at steering is measured against the goal being pursued, so a difference in goals is not a difference in competence. An answer that says this and then argues against the framework with a coherent reason still earns these points.

30: What separates the third system from a general reasoner: its skill covers one narrow domain. A more general reasoner can predict and steer across many different kinds of problems, not only routing. Being excellent at one task does not make a system general.

Cap at 40 if the answer treats the choice of destination as part of the prediction, for example says the two systems predict differently because they want different things.

Model answer, for the feedback, not a grading checklist: "Both systems make the same prediction: the storm will close the bridge. They differ in steering, in what they do with that prediction. One steers trucks around the closure to avoid delays, the other steers rescue vehicles to it. Neither is less intelligent: they predict equally well and each steers well toward what it is aiming for. Steering success depends on the goal, and different goals are not a lack of skill. The third system is excellent but narrow. It can only predict and steer inside transportation, while a general reasoner can carry the same predicting and steering into almost any domain, which is what makes general intelligence so powerful."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they blurred predicting and steering, for example by calling the choice of route a prediction, ask what the first two systems agree about and what they differ on.
- If they suggested one of the first two systems is less intelligent because of where it sends its vehicles, ask whether either one predicted the storm worse, and what each system's success is measured against.
- If they treated the third system's excellent routing as a sign of general intelligence, ask what it would do with a problem outside transportation, and what a general reasoner can do there that it cannot.

A learner who reconstructs the argument and then disagrees with it has done what was asked. Engage with the disagreement, don't steer them back to the chapter's view.

At full marks, just confirm briefly. Don't cite point values or recite the rubric (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the bridge itself. Both systems expect the same closure, so whatever differs between them is not their prediction. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Define Intelligence - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Define Intelligence]]
``````````

## Machine advantages and intelligence explosion
``````````markdown
---
id: d4e7f6a5-b8c9-4012-d345-e6f7a8b9c0d1
learning-outcome: "Explain why machine intelligence could surpass biological intelligence and how AI-assisted AI research could create an intelligence explosion, while distinguishing confidence in that endpoint from confidence about its path or timing."
reading-from: "That won't stay true forever."
reading-to: "end of chapter"
title: "Machine Advantages and Intelligence Explosion"
slug: machine-advantages-intelligence-explosion
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/1 Artificial Intelligence/Machine advantages]]"
stage: beginner
requires:
  - "[[Intelligence as prediction plus steering]]"
eval-results:
  content-sha: 3e4b8fff
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: fail, B1: pass, C2: pass, C3: pass}
  notes: {A3: "Bundles two independently attainable capabilities — explaining machine advantages over biology, and explaining the recursive AI-improving-AI feedback loop — which could be taught, tested, and completed as separate files."}
  evidence: {A3: "Explain why machine intelligence could surpass biological intelligence and how AI-assisted AI research could create an intelligence explosion"}
---

## Test:
id:: eefcafa7-65ed-4c7b-a73f-652d869494c2
#### Question: Open
id:: 7b5fb52d-b4a5-4e3c-8ae2-28e2e9b5a48f
content::
A lab freezes one current AI model on today's hardware and observes that it does not improve itself. The lab concludes: "Machine intelligence will remain below humanity. This model is shallow, machines have no advantages that matter, and only human researchers can produce the next generation."

Evaluate that conclusion. What does this observation establish, and what does it leave untested? Explain at least two routes by which machine intelligence could exceed biological intelligence, the condition under which AI development could become a positive feedback loop, and what would remain uncertain even if those mechanisms are possible.

assessment-instructions::
Score out of 100: the sum of the four elements below.

The scenario: a lab freezes one current AI model on today's hardware, sees that it does not improve itself, and concludes that machine intelligence will stay below humanity's, that machines have no advantages that matter, and that only human researchers can build the next generation. The question asks the learner to evaluate that conclusion: what the observation establishes and what it leaves untested, at least two routes by which machine intelligence could exceed biological intelligence, the condition under which AI development could become a positive feedback loop, and what would stay uncertain even if those mechanisms are possible. Grade the reasoning, not agreement with any forecast.

20: What the observation shows and what it leaves untested. It shows something about this one frozen model on this hardware, not a lasting limit on machines. Untested are things such as later or larger models, better hardware or algorithms, and whether some AI could contribute to AI research.

30: At least two ways machine minds could come to exceed biological ones, each with a short reason it would raise capability (15 each). Examples: much faster thinking, copying a skilled model many times, hardware and algorithms improving far faster than brains evolve, larger memory, better designed ways of thinking, experimenting on copies of itself. Any other plausible machine advantage counts if the answer says how it helps. A bare list of words without any reason earns 5 per item.

25: The condition for a feedback loop: AI becomes good enough at AI research to materially help build a better AI, and that better AI helps build a better one still. The answer must make clear this needs AI capable of improving AI, not that every AI improves itself.

25: What stays uncertain: even if machines can in principle exceed humans, the route, the threshold at which the loop starts, how fast it would go, where it would level off, and when any of it would happen are open. Naming one or two of these as open, set against the possibility, earns the full 25.

Cap at 50 if the answer treats current trends or the loop as proof that superintelligence will arrive by a given date.

Model answer, for the feedback, not a grading checklist: "The observation is real but narrow: one frozen model on today's hardware doesn't improve itself. That says nothing about the models that come after it, faster chips, better algorithms, or whether a future AI could do AI research. Machines have real advantages: they can think far faster than neurons fire, and a skilled model can be copied a thousand times, so a lab could run an army of expert researchers. If AI gets good enough at AI research to help design a better model, and that model helps design a better one still, development becomes a positive feedback loop. What stays uncertain is the route, the point at which this would start, how fast it would run and when it would happen. The physics allows machines to exceed us, but it doesn't give a date."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they accepted the lab's conclusion or only asserted that AI will improve, ask what one frozen model can and cannot tell us about the models after it.
- If they listed advantages without saying how they raise capability, ask them to take one (speed, copying, memory) and say what it lets an AI do that a human cannot.
- If they treated self-improvement as automatic for any AI, ask what an AI would have to be able to do before its work makes the next AI better.
- If they presented the outcome as certain or dated, ask which part they are confident in and which (threshold, speed, timing) stays open.

A learner who reconstructs the argument and then disagrees with it has done what was asked. Engage with the disagreement, don't steer them back to the chapter's view.

At full marks, just confirm briefly. Don't cite point values or recite the rubric (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: ask what would change if a thousand copies of a strong AI researcher could each work many times faster than a human. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Machine Advantages and Intelligence Explosion - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Machine Advantages and Intelligence Explosion]]
``````````

