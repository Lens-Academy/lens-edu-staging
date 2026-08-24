---
id: 7ef9b5e6-d3c7-40ee-bb95-efde5fae3b84
title: "Limitations"
tldr: "Passing every safety test can't prove a model is safe: evaluations reveal what a system can do, never what it can't. This section catalogs why. Models sandbag on purpose, labs 'safety wash' capability gains as safety progress, tiny prompt tweaks can swing scores by up to 76%, and the space of interactions is far too vast to test. Sobering, but the authors argue these limits aren't insurmountable."
summary_for_tutor: "Covers the limitations of AI evaluations from the AI Safety Atlas. Organizes challenges into four groups: fundamental (the presence-vs-absence asymmetry, interpreting negative results, unknown unknowns), technical (measurement sensitivity to prompt formatting, environmental factors, limited model access, cost and time, combinatorial explosion of interaction scenarios, estimating maximum capabilities), systemic (sandbagging by both models and companies, safety washing, the evaluation-deployment gap, domain-specific expertise gaps), and governance (the policy-evaluation gap, the need for independent evaluators like METR and Apollo Research). Includes asides on ikigai/i-risks and capability-surprise case studies such as GPT-4 controlling Minecraft (Voyager) and Gemini translating Kalamang."
reading_minutes: 17
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Limitations|Limitations]]

#### Question: Open
id:: 2dd42259-a894-467b-a301-cdd38f4a2a11
optional:: true
content::
The section spends its whole length on why evaluations cannot show that a capability is absent, and then says these limits are not insurmountable.

Did that last claim convince you?
feedback-instructions::
The learner has just read the AI Safety Atlas section "Limitations" and written a reflection. This is a reflection, not a test. There is no answer you are checking against, and you should not tell them whether they got it right.

TLDR of what they read:
Why passing every safety test cannot show a model is safe, organised in four groups. Fundamental limits: evaluations can show a capability is present but never that it is absent, so a negative result is hard to interpret, and unknown unknowns stay unknown. Technical limits: measurements are sensitive to prompt formatting and environmental factors, sometimes swinging scores dramatically; access to models is often restricted; evaluations cost time and money; the space of possible interactions is combinatorially too large to cover; and estimating maximum capability is itself unsolved. Systemic limits: sandbagging, where a model underperforms deliberately, and the company-level version where results are presented selectively; safety washing, where capability gains are reported as safety progress; the gap between evaluation conditions and real deployment; and shortages of domain expertise. Governance limits: the gap between what evaluations produce and what policy needs, and the case for independent evaluators such as METR and Apollo Research. It includes case studies of capability surprises, and argues the limits are real but not insurmountable.

Take what they wrote seriously and push on it once. Useful directions: whether "not insurmountable" is a claim about the limits or about the field's willingness to work on them, since some of the four groups are technical and some are incentive problems, and those need different fixes; that the presence-absence asymmetry looks structural rather than solvable, which would put it in a different class from cost or access; that independent evaluators address the systemic group but do nothing for the fundamental one; and what a safety case could honestly claim given all this, since the previous chapter's licensing proposals rest on exactly that.

If they say they do not know or write something thin, do not press them for more. Offer one concrete way to look at it and leave it there.

Do not resolve this for them. The section itself does not, and a learner who concludes evaluations are close to useless has read it fairly, as has one who concludes the opposite.

120 to 200 words. Short paragraphs, no lists. Do not over-validate and do not praise the answer.
