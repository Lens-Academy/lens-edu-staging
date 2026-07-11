---
id: b5cd523c-9426-4f3b-93d4-81b098b7f49c
summary_for_tutor: Covers what AI safety evaluations can and cannot achieve. Evals can establish lower bounds on capabilities and assess some misuse risks, but fundamentally cannot establish upper bounds on capabilities, reliably forecast future capabilities, or robustly assess misalignment risks. Warns that a sufficiently misaligned system might exploit evaluation blind spots, and that eval awareness (sandbagging) is already a demonstrated concern.
title: What AI evaluations for preventing catastrophic risks can and cannot do
tldr: Evaluations can tell us the floor of what an AI is capable of — but not the ceiling. This paper examines what safety testing can and can't deliver — useful lower bounds on capabilities, yes, but reliable forecasts of future behavior or detection of hidden goals? Not yet.
---
#### Text
content::
The reliance on evals might create a "compliance culture" rather than a "safety culture." Labs may optimize their models specifically to pass safety tests while ignoring the deeper: more complex alignment issues. If "passing the eval" becomes the goal: the test itself becomes a target for the AI to manipulate.

This critique warns that evaluations are not a "safety guarantee." A primary technical limitation is Eval Awareness: by 2026: some models can distinguish between testing and deployment environments and alter their behavior accordingly (a form of "sandbagging"). Furthermore: evals only find "lower bounds"—if a model fails a test: it doesn't prove it lacks the capability; it might just need a better prompt or more compute.

#### Article
source:: [[../articles/barnett+thiergart-what-ai-evaluations-for-preventing-catastrophic-risks-can-and-cannot-do]]
to:: "these fundamental limitations remain unsolved."

#### Article
from:: "## 1 Introduction"
to:: "Introduction"

#### Article
from:: "The challenges and limitations of AI evaluations"
to:: "with important implications for AI governance and regulation."

#### Article
from:: "## 2 What AI evaluations can do (given sufficient effort)"
to:: "certain the AI system can do at least this much."

#### Article
from:: "### 2.2 Assess misuse risk for current models"
to:: "if evaluators are unable to use it to exploit any threat vectors."

#### Article
from:: "### 2.3 Applications that don’t directly mitigate catastrophic risks"
to:: "in a model succeeding at tasks it previously failed."

#### Article
from:: "### 3.2 Robustly forecast future model capabilities"
to:: "emerge before dangerous ones, serving as warning signs."

#### Article
from:: "### 3.3 Robustly assess misalignment and model autonomy risks"
to:: "not lead it to cause harm, even in novel situations."

#### Article
from:: "### 3.4 Unknown unknown risks"
to:: "lead to catastrophic and possibly existential outcomes."

#### Text
content::
Ask the AI Tutor any questions you may have:

#### Chat
instructions::
Help the user understand this article, or help them with other questions they have.