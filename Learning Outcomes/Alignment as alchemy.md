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
