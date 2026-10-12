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
Score {--{"author":"James's AI","timestamp":1791834874375}@@out of 100:--}{++{"author":"James's AI","timestamp":1791834874375}@@according to++} the {--{"author":"James's AI","timestamp":1791834874375}@@sum of--}{++{"author":"James's AI","timestamp":1791834874375}@@following rubric.
**1** — Cannot explain++} the {--{"author":"James's AI","timestamp":1791834874375}@@two elements below.

The question asks what the goal-space argument is and why it implies that a sufficiently advanced AI is overwhelmingly unlikely--}{++{"author":"James's AI","timestamp":1791834874375}@@goal-space argument or confuses it with a different claim. *Example: "AI will be dangerous because it will be too smart for us++} to {--{"author":"James's AI","timestamp":1791834874375}@@pursue human-compatible goals. The setup it refers to: in an allegory, aliens care intensely --}{++{"author":"James's AI","timestamp":1791834874375}@@control."*

**2** — Has a vague sense that AI might not share human values, but cannot articulate why. *Example: "AI might not care ++}about the {--{"author":"James's AI","timestamp":1791834874375}@@"correct" number of stones in their nests, and--}{++{"author":"James's AI","timestamp":1791834874375}@@same things we do, since it wasn't raised like++} a {--{"author":"James's AI","timestamp":1791834874375}@@young alien points out that most species would not share this value and that becoming smarter would not make them share it. The same logic is applied to AI. Grade the reasoning in any wording. An answer may use the allegory, another example or none.

50: The space of possible goals a mind could have is vast, and goals--}{++{"author":"James's AI","timestamp":1791834874375}@@human."*

**3** — Correctly explains the core mechanism: the space of possible goals is vast, human-compatible goals occupy a tiny fraction of that space, and intelligence doesn't cause convergence toward any particular set of values — so a powerful AI is overwhelmingly unlikely to share ours. Uses the alien allegory or an equivalent concrete example. *Example: "The goal-space argument says++} that {--{"author":"James's AI","timestamp":1791834874375}@@include a future good for humans (happy, free people)--}{++{"author":"James's AI","timestamp":1791834874375}@@there are astronomically many possible goal-sets an AI could have. Human-friendly goals++} are {++{"author":"James's AI","timestamp":1791834874375}@@just ++}a tiny {--{"author":"James's AI","timestamp":1791834874375}@@part of it. So an AI's goals, unless something aims them precisely--}{++{"author":"James's AI","timestamp":1791834874375}@@sliver. And getting smarter doesn't pull you toward any particular goals. It just makes you better++} at {--{"author":"James's AI","timestamp":1791834874375}@@that small region, will almost certainly fall somewhere else. An answer that says--}{++{"author":"James's AI","timestamp":1791834874375}@@pursuing whatever goals you already have. The alien story illustrates this: no matter how smart++} the {--{"author":"James's AI","timestamp":1791834874375}@@AI will--}{++{"author":"James's AI","timestamp":1791834874375}@@aliens get,++} most {--{"author":"James's AI","timestamp":1791834874375}@@likely end up wanting something else has stated this.--}{++{"author":"James's AI","timestamp":1791834874375}@@species still won't care about the 'correct' number of stones."*++}

{--{"author":"James's AI","timestamp":1791834874375}@@50: Getting smarter does not pull a mind toward any particular goals, including ours. Intelligence makes a mind better at pursuing--}{++{"author":"James's AI","timestamp":1791834874375}@@**4** — As above, plus articulates the direction-agnostic intelligence point: intelligence is an optimization engine that amplifies++} whatever goals {--{"author":"James's AI","timestamp":1791834874375}@@it --}{++{"author":"James's AI","timestamp":1791834874375}@@the system ++}has, {--{"author":"James's AI","timestamp":1791834874375}@@it does not change which goals those are, so a more advanced AI does not become more likely to share human values.

Cap at 30 if the answer says the danger is that the AI will hate humans or choose to be evil.

Model answer, for--}{++{"author":"James's AI","timestamp":1791834874375}@@without selecting for any particular goals. *Example: Adds "Intelligence is direction-agnostic: it's like a powerful engine that goes wherever the steering wheel points. A smarter AI is better at achieving its goals, but 'smarter' doesn't mean 'more aligned with humans.' That's the whole point of++} the {--{"author":"James's AI","timestamp":1791834874375}@@feedback, not a grading checklist: "There are vastly many goals a mind could have, and caring about a future full of happy, free people is a tiny sliver of them, just as caring about the right number of stones in--}{++{"author":"James's AI","timestamp":1791834874375}@@alien girl's argument."*

**5** — As above, plus connects the goal-space argument to the chapter's broader stakes: this is why the problem is so hard: it's not that we need to prevent AI from choosing bad goals, but that human-compatible goals are++} a {--{"author":"James's AI","timestamp":1791834874375}@@nest is a tiny sliver from our point of view. Getting smarter doesn't move a mind toward any particular goal. It--}{++{"author":"James's AI","timestamp":1791834874375}@@needle in an astronomical haystack, and there's no known method to aim for that needle. *Example: Adds "This is what++} makes {--{"author":"James's AI","timestamp":1791834874375}@@it better at getting whatever it already wants. So unless we can aim--}{++{"author":"James's AI","timestamp":1791834874375}@@alignment so difficult. It's not about preventing a malicious AI: it's that building++} an {--{"author":"James's AI","timestamp":1791834874375}@@AI's--}{++{"author":"James's AI","timestamp":1791834874375}@@AI whose++} goals {--{"author":"James's AI","timestamp":1791834874375}@@precisely at ours, which nobody knows how to do yet, a superintelligent AI will almost certainly want something else.--}{++{"author":"James's AI","timestamp":1791834874375}@@happen to include human flourishing requires hitting an incredibly specific target in an enormous space, and we don't yet know how to aim.++} The {--{"author":"James's AI","timestamp":1791834874375}@@likely--}{++{"author":"James's AI","timestamp":1791834874375}@@default++} outcome isn't {--{"author":"James's AI","timestamp":1791834874375}@@hostility but indifference."--}{++{"author":"James's AI","timestamp":1791834874375}@@hostility; it's indifference."*++}

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they gave a general "AI is too powerful" answer, ask how many different goals an AI could in principle have, and how many of those include a future of happy, free people.
- If they said AI might not share our values without saying why, ask what getting smarter would do to the young alien's point about the stones.
- If they had the vast space of goals and the small target, ask whether intelligence pulls a mind toward particular goals or only makes it better at pursuing the ones it already has.
- If they had that, ask what this means for building an AI that does share our goals: what would we need to be able to do that we cannot do yet?

At full marks, just confirm briefly. Don't cite {--{"author":"James's AI","timestamp":1791834874375}@@point values--}{++{"author":"James's AI","timestamp":1791834874375}@@level numbers++} or {--{"author":"James's AI","timestamp":1791834874375}@@recite the rubric--}{++{"author":"James's AI","timestamp":1791834874375}@@band names++} (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the stones. However clever another species became, nothing about being clever would make it care how many stones are in a nest. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Define the Goal-Space Argument - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Define the Goal-Space Argument]]
