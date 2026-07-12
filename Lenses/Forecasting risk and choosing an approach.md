---
id: 53a7abde-fd71-4dab-b647-1ce78bc53d60
{++{"author":"Elias's AI","timestamp":1783849315811}@@tldr: "How hard is alignment, really, and once you've decided to tackle it, which route do you take? This lens maps two spectrums: optimistic to pessimistic views on difficulty, and empirical, mathematical, philosophical, and prosaic approaches to solving it. Then it shows where this course plants its flag."
summary_for_tutor: "Maps two spectrums in AI safety. First, difficulty: Anthropic's optimistic, intermediate, and pessimistic trichotomy, situated against a wider spread from failure stories (Christiano's 'What failure looks like' and AI 2027) to 'AI is easy to control', with the survey figure that 38 to 51% of authors at top ML venues give at least a 10% chance of extinction-level outcomes as a calibration anchor, and model organisms of misalignment offered as one way to study risk empirically. Second, solution approaches: empirical or iterative (Leike), mathematical (Yudkowsky's rocket alignment analogy), philosophical, and prosaic (Christiano, aligning the systems we have now, orthogonal to the empirical-versus-theoretical axis). Concludes with the course's own synthesis: a prosaic picture of powerful deep-learning systems plus deep, empirically grounded mathematical progress. Includes an optional chat that helps the learner map both spectrums."
++}title: Forecasting risk and choosing an approach
---
#### Text
content:: Where does this leave us, in terms of our general level of risk?

**A spectrum of views on difficulty**

There is a broad spectrum of views on how hard the alignment problem is. In Anthropic's "[[../Lenses/anthropic-core-views-on-ai-safety-when-why-what-and-how|Core Views on AI Safety]]", the authors discuss three very different possibilities:

- an **optimistic** scenario, in which current methods are essentially sufficient;
- an **intermediate** scenario, in which preventing catastrophic risks requires substantial scientific and engineering effort;
- a **pessimistic** view, in which AI safety is essentially unsolvable.

Among [[../Lenses/grace-thousands-of-ai-authors-on-the-future-of-ai|authors at top machine-learning venues]], "[b]etween 38% and 51% of respondents gave at least a 10% chance to advanced AI leading to outcomes as bad as human extinction." Those who are concerned often write failure stories of how AI can lead to catastrophe, like Paul Christiano's "[What failure looks like](https://www.lesswrong.com/posts/HBxe6wdjxK239zajf/what-failure-looks-like)" and the detailed scenario in [[ai-2027 article lens|AI 2027]]; others are more optimistic and explain why they think "[[../Lenses/optimism-ai-is-easy-to-control|AI is easy to control]]".

In this epistemic state of uncertainty, it is useful to do research on the level and nature of AI risks themselves. One approach is [[../Lenses/evhub-model-organisms-of-misalignment-the-case-for-a-new-pillar-of-alignment-research|model organisms of misalignment]] — "in vitro demonstrations of the kinds of failures that might pose existential threats".

**A spectrum of solution approaches**

Assume we are sufficiently concerned that we want to solve the problem. What high-level approach should we choose?

- **Empirical / iterative.** Some, like Jan Leike, argue for [[../Lenses/leike-why-im-optimistic-about-our-alignment-approach|very empirical iterative approaches]], sometimes aiming to use more advanced AI systems to help solve remaining alignment research questions.
- **Mathematical.** Eliezer Yudkowsky argues for deep mathematical progress in his analogy to the [[../Lenses/yudkowsky-the-rocket-alignment-problem|rocket alignment problem]].
- **Philosophical.** Yet others take a further step back and argue we need to solve [[../Lenses/dai-problems-in-ai-alignment-that-philosophers-could-potentially-contribute-to|deep philosophical problems]] on the way to aligned AI.
- **Prosaic.** Somewhat orthogonal to all of these, Paul Christiano's post on [prosaic AI alignment](https://ai-alignment.com/prosaic-ai-control-b959644d79c2) argues that we should attempt to align the AI systems we have in front of us, instead of waiting for breakthroughs in our understanding of intelligence or for entirely new paradigms — a view compatible with both empirical and theoretical research.

**This course's synthesis**

Our course tries, to a large extent, for a synthesis between these views: yes, we assume for much of the course the "prosaic" picture that powerful AI systems will be based on deep-learning systems much like today's; *and* we are interested in deep, empirically grounded **mathematical** progress on understanding these systems.

#### Chat
optional:: true
instructions:: Help the learner map the two spectrums in this lens. First, difficulty: Anthropic's optimistic / intermediate / pessimistic trichotomy, plus the wider spread (failure stories like "What failure looks like" and AI 2027 on one side; "AI is easy to control" on the other; the 38-51% survey figure as a calibration anchor). Second, solution approaches: empirical/iterative (Leike), mathematical (Yudkowsky's rocket analogy), philosophical, and prosaic (Christiano — align what we have now; note it is orthogonal to the empirical-vs-theoretical axis). Then surface this course's own stance: prosaic picture + deep empirically-grounded mathematical progress. A good probe: ask the learner which approach they find most persuasive and why, and push them to notice that "prosaic" is not an alternative to empirical/mathematical but cuts across them. Stay within the lens content; do not invent positions not attributed here.
