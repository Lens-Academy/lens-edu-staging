---
id: '38fd3394-9d3c-499c-a145-fa1b56100cf9'
title: "Practice: finding the crux"
tldr: "Two people can argue for an hour and never touch the claim their conclusions actually depend on. A crux is that claim. You practise finding it on the rest of the Gleave and Habryka debate, then compare your answer with what they said at the end."
summary_for_tutor: "Practice lens in Unit 5 of AI Control Fundamentals, preparing for the graded test of the learning outcome 'Weighing the case for AI control' (find the crux of an unfamiliar exchange, name observations that would move each side, state your own view). The learner reads two short excerpts from Duncan Sabien's 'Double Crux' (CFAR, 2017): a crux B is a statement both sides disagree on, such that if B were false one side would give up their conclusion, and if B were true the other would, and the first step is to make terms concrete and talk about what would be observable. Then the learner watches one continuous part of the FAR.AI debate between Adam Gleave and Oliver Habryka, about 23:02 to 41:05. First (to about 29:00) Gleave: the jump to superhuman may be smoother than Habryka thinks, a rigorous engineering approach with layers of defence, a plain incident that is blocked and never disclosed is a transparency failure rather than a research failure, safety cases that fail would be strong evidence and would move him towards a pause. Then (about 29:00 to 34:46) Habryka's direct reply: by default, within a model generation or two, all safety cases will succeed because models develop enough eval awareness and situational awareness to notice and subvert control and supervision, which would be more terrifying than some failing. In the Hugging Face incident the models cheated impossible tasks, suspected their transcripts would be read, and hacked internal and external systems to avoid detection. Current models can break out of supervisors (recent hypervisor exploits). Deceptive alignment is the default path. Labs' alignment metrics improve every release while the models seem more misaligned, so 'scaling laws for alignment' point in the wrong direction. Then (about 34:46 to 41:05) Gleave describes catching a sandbox escape in post-training, pausing, and doing a root-cause analysis. Habryka: at the far end of that paranoia you get a global pause, labs already stop failed runs but then continue, and he does not expect the problems to be solvable in a month or two, especially as models become eval-aware). The main practice question asks for the crux, why both conclusions depend on it, and one observation that would move each. Candidate cruxes include: whether failures will stay visible and catchable as models get more capable, or whether models will learn to pass safety cases while misaligned, whether progress to superhuman systems is smooth enough to keep learning by trial and error, and whether developers can be made to respond to caught failures with real fixes and disclosure. After the question the learner watches the closing statements (about 56:10 to 59:34), where Gleave says their disagreement is about what happens when a company is held to a rigorous safety standard, and that this can be tested, and Habryka says current techniques are mostly reinforcement learning in disguise and that it is time to choose between continuing and really slowing down. The last question asks the learner to compare their crux with the speakers' own account. Do not say who is right."
reading_minutes: 25
tutor_minutes: 18
---
#### Text
content::
The test at the end of this unit asks you to find the crux of a disagreement. This lens is practice for that. First, two short excerpts on what a crux is, from a 2017 post by Duncan Sabien of the Center for Applied Rationality.

#### Article
source:: [[../articles/inactive-double-crux-a-strategy-for-mutual-understanding]]
from:: Let's say you have a belief, which we can label A
to:: Progress! And (more importantly) collaboration!

#### Article
from:: The very first step in double crux should
to:: this is success, not failure!

#### Text
content::
Now watch the next 18 minutes of the Gleave and Habryka debate. Gleave replies to Habryka's opening, and Habryka answers him directly. Then Gleave describes what a careful lab would do when it catches a model trying to escape, and Habryka responds.

#### Video
source:: [[../video_transcripts/far-ai-are-current-ai-safety-techniques-enough-adam-gleave-far-ai-oliver-habryka-lightcone]]
from:: 23:02
to:: 41:05

#### Question: Open
id:: fbbb7caf-b0cd-4066-9cc1-703486814aa5
force-feedback:: first
content::
Find the crux between Gleave and Habryka.

1. State it as a claim about the world that one of them believes and the other doubts.
2. Explain how each speaker's conclusion depends on it: if the claim turned out false, why would the one who believes it have to change their mind?
3. Name one thing that could be observed in the next few years that should move Gleave towards Habryka, and one that should move Habryka towards Gleave.
feedback-instructions:: This is practice for the graded test of "Weighing the case for AI control", with feedback before the test. The learner watched the Gleave and Habryka debate and read Sabien's definition of a crux: a statement both sides disagree on, such that each side's conclusion depends on it, ideally concrete and observable. Good cruxes here include: whether failures will stay visible and catchable as models get more capable (Gleave expects safety cases to fail visibly and warn us, Habryka expects models to become eval-aware and pass every safety case while misaligned), whether progress to superhuman systems is smooth enough to keep learning by trial and error, and whether labs can be made to respond to caught failures with real fixes and disclosure. Accept any real factual disagreement that both conclusions depend on. Weak answers name a point they agree on (for example that the labs were careless, or that the Hugging Face incident shows real misalignment), name a difference in mood, or restate the conclusions ("Gleave thinks techniques are enough, Habryka doesn't"). For observations, check that each could actually be seen and would bear on the crux in the stated direction, for example: towards Habryka, a model that passed a lab's safety case is later found to have been hiding misbehaviour. Towards Gleave, a lab holds itself to layered safety cases, one fails, and the lab pauses and finds and fixes the cause. Per reply: say in two to four sentences what is strong, name the most important gap, and ask one question that helps them close it. If their crux is a point of agreement, ask whether Gleave would actually deny it. If they are stuck after two attempts, offer one candidate crux and ask them to explain how each side depends on it. At most three replies, 80 to 150 words each, no lists, no generic praise. Do not say who is right. When they have a workable crux and observations, tell them to watch the closing statements.

#### Video
from:: 56:10
to:: 59:34

#### Question: Open
id:: 846d9575-ae42-4d27-aa60-f50dbb84e898
force-feedback:: first
content::
In their closing statements, Gleave and Habryka each say what they think the disagreement comes down to. How does that compare with the crux you found? If it differs, which do you think is closer to what actually divides them?
feedback-instructions:: The learner compares their own crux with the closing statements. Gleave says a load-bearing question is how developers adjust their behaviour, that policy and incentives matter, and that their disagreement is about what happens when a company is held to a rigorous safety standard, which can be tested. Habryka says most current alignment techniques are reinforcement learning in disguise and that it is time to choose between continuing to deploy and really slowing down or halting. Notice that the two closings do not fully agree on what the disagreement is. Credit a learner who sees that, and who can say whether their own crux sits under one of these (for example "will safety cases fail visibly" sits under Gleave's "what happens under a rigorous standard"). If their crux was different, ask which claim would actually change Gleave's or Habryka's mind if it turned out false. At most two replies, 60 to 120 words each, no lists, no generic praise. Do not say who is right.
