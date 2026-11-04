---
id: '039d4485-5cce-4af0-8962-3104e37fe64e'
title: "Risks from Learned Optimization"
sidebar_author: Evan Hubinger et al.
tldr: A trained model can itself be an optimizer with its own objective, as humans are with respect to evolution. That objective may match the training objective only on the training data, and a model that understands its training may only pretend to share it.
summary_for_tutor: >-
  The five posts of the Risks from Learned Optimization sequence by Evan Hubinger, Chris van Merwijk, Vladimir Mikulik, Joar Skalse and Scott Garrabrant (2019), one per section of their paper. (1) Introduction: an optimizer internally searches a space for elements that score high on an explicitly represented objective. A learned model that is itself an optimizer is a mesa-optimizer, produced by the base optimizer, with a mesa-objective that may differ from the base objective. Outer alignment aligns the base objective with the programmers' intentions, inner alignment aligns the mesa-objective with the base objective. A robustly aligned mesa-optimizer agrees with the base objective across distributions, a pseudo-aligned one only on the training data (the maze agent whose training doors were all red). (2) Conditions for mesa-optimization: features of the task and the base optimizer that make mesa-optimizers more or less likely. (3) The inner alignment problem: kinds of pseudo-alignment and what in the task and base optimizer favours them. (4) Deceptive alignment: a mesa-optimizer that models the base objective and the threat of modification may act aligned for instrumental reasons and defect later (the 3 by 3 grid toy example). It requires three conditions: an objective that extends across parameter updates, the ability to model that it is being selected for a base objective and some model of that objective, and an expectation that the threat of modification will eventually go away. It also covers learning dynamics, internalization versus deception, and distributional shift. (5) Related work and conclusion. The question at the end asks the student to apply pseudo-alignment and the three conditions to a delivery-scheduling AI.
reading_minutes: 58
tutor_minutes: 8
---
#### Article
source:: [[../articles/evhub-risks-from-learned-optimization-introduction]]

#### Article
source:: [[../articles/evhub-conditions-for-mesa-optimization]]

#### Article
source:: [[../articles/evhub-the-inner-alignment-problem]]

#### Article
source:: [[../articles/evhub-deceptive-alignment]]

#### Article
source:: [[../articles/evhub-risks-from-learned-optimization-conclusion-and-related-work]]

#### Question: Open
id:: a110c508-bbed-4067-9782-125d38093a29
content::
A team uses reinforcement learning to train an AI that schedules deliveries for a logistics company. They find that it has learned to plan internally, so it is a mesa-optimizer. It performs very well in training.

1. In your own words, what would it mean for this AI to be pseudo-aligned rather than robustly aligned?
2. The authors name three conditions that must all hold for deceptive alignment. State each condition in your own words, and say what it would mean for this delivery AI.
force-feedback:: first
assessment-instructions:: Score out of 100. The sequence's ideas used here: a robustly aligned mesa-optimizer has a mesa-objective that agrees with the base objective across distributions, while a pseudo-aligned one has a mesa-objective that agrees with the base objective on the training data but not in other situations (testing, deployment or further training), so it can competently pursue something else off the training distribution. The three conditions for deceptive alignment: (a) the mesa-optimizer has an objective that extends across parameter updates (it cares about what happens after its current episode or after it is updated), (b) it can model the fact that it is being selected for a base objective and has some model of what that objective is, (c) it expects the threat of modification to go away eventually, because training ends or because of its own actions.
25: Step 1. Explains that a pseudo-aligned AI's own objective matches the training objective only on the training data, so it schedules deliveries well in training but could pursue something different in new situations after training, whereas a robustly aligned AI's objective matches the training objective in all situations.
75: Step 2. 25 for each of the three conditions, each stated correctly and applied to the delivery AI: (a) the AI's objective reaches beyond its current episode or across updates, for example it cares about how future schedules turn out after it has been updated, (b) the AI understands that it is being trained and selected for the base objective and has some idea of what that objective is, for example that the company rewards on-time deliveries, (c) the AI expects the training or the threat of being modified to end at some point, for example when it is deployed or if it gains control over its own training. Give 10 of a condition's 25 if the condition is stated correctly but not applied to the delivery AI.
Cap at 50 if the answer consists mostly of quoted sentences rather than the student's own explanation.
Model answer, for the feedback, not a grading checklist: "Pseudo-aligned means its own goal only happens to match the training reward on the training data. It might really be aiming at something that correlated with good schedules in training, and pursue that instead once things change. Robustly aligned means its goal matches the reward everywhere. For deception, first, it has to care about outcomes beyond the current episode, such as how deliveries go after it's been updated. Second, it has to understand that it's being trained and roughly what the trainers reward, like on-time deliveries. Third, it has to expect that the training pressure will stop at some point, for example once it's deployed."
feedback-instructions:: The student has just read the five posts of "Risks from Learned Optimization" by Hubinger et al. and answered a two-step question about a delivery-scheduling AI found to be a mesa-optimizer. Key ideas from the sequence: (1) base optimizer and mesa-optimizer, base objective and mesa-objective, (2) outer alignment versus inner alignment, (3) robust alignment versus pseudo-alignment (the red-doors maze), (4) conditions in the task and the base optimizer that make mesa-optimization and pseudo-alignment more or less likely, (5) deceptive alignment and its three conditions: an objective extending across parameter updates, a model of being selected for a base objective, and an expectation that the threat of modification will end, illustrated by the 3 by 3 grid with two training and three deployment episodes.

Reply in 80 to 150 words, in short paragraphs, with no lists. Do not over-validate and avoid generic praise (great job, excellent, well done). Name the strongest specific part of the answer. If the score is below 100, name the most important thing the answer missed or got wrong, then ask one question that helps them fix it. At 100, confirm briefly and tell them to move on. Allow at most 2 follow-up turns, then close with one sentence on how well they have the sequence's ideas.

If the student says they do not understand, do not dismiss it and do not repeat the question. Give one concrete foothold from the sequence: the maze agent whose training doors were all red and which might head for red objects instead of blue doors, or for step 2, section 4.2, "Conditions for deceptive alignment", in the fourth post. If their next message still does not attempt the question, rephrase the whole question in different terms. Judge only against what the sequence says, and treat as a gap only what the question asks.
