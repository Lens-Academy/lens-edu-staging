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
Score {--{"author":"James's AI","timestamp":1791834757296}@@out of 100: the sum of --}{++{"author":"James's AI","timestamp":1791834757296}@@according to ++}the {--{"author":"James's AI","timestamp":1791834757296}@@three elements below.

The question asks what the distinction between "grown" and "crafted" AI is,--}{++{"author":"James's AI","timestamp":1791834757296}@@following rubric.
**1** — Believes engineers fully understand modern AI because they wrote the code++} and {--{"author":"James's AI","timestamp":1791834757296}@@what an engineer does and does not--}{++{"author":"James's AI","timestamp":1791834757296}@@designed the training process. *Example: "Engineers++} know {--{"author":"James's AI","timestamp":1791834757296}@@about a trained AI model. Grade the ideas, in any wording. No analogy or term--}{++{"author":"James's AI","timestamp":1791834757296}@@everything about how it works because they built it."*

**2** — Understands that AI learns++} from {--{"author":"James's AI","timestamp":1791834757296}@@the source is needed.

40: The distinction. Crafted systems: engineers write--}{++{"author":"James's AI","timestamp":1791834757296}@@data rather than being programmed step-by-step, but cannot explain++} the {--{"author":"James's AI","timestamp":1791834757296}@@rules or code that decide what the system does, step by step. Grown systems: engineers write a training process (for example gradient descent adjusting billions of numbers on data) and the model's behavior comes out of that optimization, not out of anyone's design.

30: What --}{++{"author":"James's AI","timestamp":1791834757296}@@epistemic gap this creates. *Example: "AI learns on its own so it's more flexible than traditional software, but engineers still understand it pretty well."*

**3** — Correctly explains that gradient descent produces cognition through optimization rather than deliberate design, and names ++}the {--{"author":"James's AI","timestamp":1791834757296}@@engineer does know: how--}{++{"author":"James's AI","timestamp":1791834757296}@@key gap: engineers understand++} the {--{"author":"James's AI","timestamp":1791834757296}@@model was produced, such as--}{++{"author":"James's AI","timestamp":1791834757296}@@training process but cannot read++} the {--{"author":"James's AI","timestamp":1791834757296}@@architecture, the training procedure, the data and the objective. Mentioning that they can also see every number (weight) in--}{++{"author":"James's AI","timestamp":1791834757296}@@resulting weights to predict behavior (the DNA analogy: readable but not interpretable). *Example: "Engineers designed the training process but not what++} the model {--{"author":"James's AI","timestamp":1791834757296}@@also counts here. One of these, stated clearly, earns the 30.

30: What the engineer does not know:--}{++{"author":"James's AI","timestamp":1791834757296}@@learned. The weights are like a genome: you can read them but you can't tell from them++} what the {--{"author":"James's AI","timestamp":1791834757296}@@trained model has actually learned, how it works inside, or--}{++{"author":"James's AI","timestamp":1791834757296}@@system will do, any more than reading DNA tells you exactly++} what {--{"author":"James's AI","timestamp":1791834757296}@@it--}{++{"author":"James's AI","timestamp":1791834757296}@@an organism++} will {--{"author":"James's AI","timestamp":1791834757296}@@do or want. The weights can be read but not understood well enough to predict its behavior. Knowing how it was made is not knowing what it is.

Cap at 30--}{++{"author":"James's AI","timestamp":1791834757296}@@be like."*

**4** — As above, plus explains why this matters for safety: you can't verify what the system has learned or what goals it has developed. *Example: Adds "So even++} if the {--{"author":"James's AI","timestamp":1791834757296}@@answer says engineers fully understand the trained model because they built it.

Model answer, for--}{++{"author":"James's AI","timestamp":1791834757296}@@training went exactly as planned, you still can't look inside and confirm++} the {--{"author":"James's AI","timestamp":1791834757296}@@feedback, not a grading checklist: "Crafted software is written by people: an engineer decides--}{++{"author":"James's AI","timestamp":1791834757296}@@model has the values you wanted it to have."*

**5** — As above, plus articulates++} the {--{"author":"James's AI","timestamp":1791834757296}@@rules and the program follows them. A modern AI--}{++{"author":"James's AI","timestamp":1791834757296}@@process-knowledge/cognition-knowledge distinction: understanding how a system was produced++} is {--{"author":"James's AI","timestamp":1791834757296}@@grown: engineers write --}{++{"author":"James's AI","timestamp":1791834757296}@@not ++}the {--{"author":"James's AI","timestamp":1791834757296}@@training process, and gradient descent tunes billions of numbers until the model does well on the data. Nobody chooses what those numbers end up encoding. So the engineers--}{++{"author":"James's AI","timestamp":1791834757296}@@same as understanding what it is. *Example: "There are two kinds of understanding here. Engineers have process-knowledge: they++} know {--{"author":"James's AI","timestamp":1791834757296}@@the recipe, the architecture, the data,--}{++{"author":"James's AI","timestamp":1791834757296}@@exactly how++} the training {--{"author":"James's AI","timestamp":1791834757296}@@method, and--}{++{"author":"James's AI","timestamp":1791834757296}@@works. But++} they{--{"author":"James's AI","timestamp":1791834757296}@@ can even look at every number in the model. What--}{++{"author":"James's AI","timestamp":1791834757296}@@ lack cognition-knowledge:++} they don't know{--{"author":"James's AI","timestamp":1791834757296}@@ is what those numbers mean:--} what the model {--{"author":"James's AI","timestamp":1791834757296}@@has learned, how it reasons, what it will do in a new situation --}{++{"author":"James's AI","timestamp":1791834757296}@@actually represents ++}or{--{"author":"James's AI","timestamp":1791834757296}@@ what it --}{++{"author":"James's AI","timestamp":1791834757296}@@ ++}wants.{--{"author":"James's AI","timestamp":1791834757296}@@ It's like a genome: you can read every letter and still not know what the organism will be like."--}{++{"author":"James's AI","timestamp":1791834757296}@@ Confusing these two is the mistake that makes people overconfident about AI safety."*++}

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said engineers understand the model because they built it, ask what an engineer could find out by reading the trained weights directly.
- If they said the AI learns from data but not what that leaves unknown, ask what an engineer knows about a model once training is done, and what they cannot tell from it.
- If they {--{"author":"James's AI","timestamp":1791834757296}@@said what engineers know but not clearly what they don't, ask whether knowing--}{++{"author":"James's AI","timestamp":1791834757296}@@named the gap (the training process is understood, the resulting behavior cannot be read off++} the {--{"author":"James's AI","timestamp":1791834757296}@@training recipe tells you--}{++{"author":"James's AI","timestamp":1791834757296}@@weights) but stopped there, ask++} what {++{"author":"James's AI","timestamp":1791834757296}@@this means for checking whether ++}the model {--{"author":"James's AI","timestamp":1791834757296}@@wants.--}{++{"author":"James's AI","timestamp":1791834757296}@@ended up with the goals they wanted.++}
- If they {--{"author":"James's AI","timestamp":1791834757296}@@named the gap (the training process--}{++{"author":"James's AI","timestamp":1791834757296}@@covered that too, the step left++} is {--{"author":"James's AI","timestamp":1791834757296}@@understood, the resulting behavior cannot be read off the weights), a good follow-up is--}{++{"author":"James's AI","timestamp":1791834757296}@@that knowing how something was produced is a different kind of knowledge from knowing++} what {--{"author":"James's AI","timestamp":1791834757296}@@this means for checking whether--}{++{"author":"James's AI","timestamp":1791834757296}@@it is. Ask whether knowing++} the {--{"author":"James's AI","timestamp":1791834757296}@@model ended up with--}{++{"author":"James's AI","timestamp":1791834757296}@@training recipe tells you what++} the {--{"author":"James's AI","timestamp":1791834757296}@@goals they wanted.--}{++{"author":"James's AI","timestamp":1791834757296}@@model wants.++}

At full marks, just confirm briefly. Don't cite {--{"author":"James's AI","timestamp":1791834757296}@@point values--}{++{"author":"James's AI","timestamp":1791834757296}@@level numbers++} or {--{"author":"James's AI","timestamp":1791834757296}@@recite the rubric--}{++{"author":"James's AI","timestamp":1791834757296}@@band names++} (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the genome comparison. A genome can be read letter by letter, yet reading it does not tell you what the organism will be like. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted - PQ]]

## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted]]
