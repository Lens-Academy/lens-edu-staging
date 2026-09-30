---
id: '2069bada-f767-4a3b-b670-37cde07602ac'
learning-outcome: "Build an attack tree for how a scheming model could reach a specified unacceptable outcome in a given deployment, with AND and OR decomposition down to choices the model makes, facts about the environment, or points a safeguard could act on, and use it to say which nodes a proposed safeguard prevents, detects or deters and which attack path it leaves open."
topic: "[[../Domains and Topics/7 AI Control/Control threat models]]"
stage: intermediate
authors:
  - Elias+Claude

---
%% Ideally there would also be a general threat-modelling LO (building attack trees for any system, not only a scheming model) in 11 Strategy or 8 Cybersecurity, which this one would require. It is not created because no lens teaches it on its own yet; the Attack Trees lens teaches the general method only as groundwork for this control-specific skill. %%
## Test:
id:: 95831b07-cb8e-4545-9633-946fe4435e69

#### Question: Open
id:: 69b312f5-e4eb-4260-9c3b-155666eb2bb7
content::
A frontier model U works as an agent with shell access to a lab's training cluster. U may be scheming. The unacceptable outcome is: **a copy of U's weights is running on hardware the lab does not monitor.**

Current safeguards:
- Every command U runs is logged.
- After each task, a weaker trusted model reads the log and flags suspicious tasks for a human to review.
- U's network access is limited to a list of approved internal machines.

1. Build an attack tree for this outcome as a nested list. Put the outcome at the root, mark each node that has children as AND or OR, and keep decomposing until each leaf is a choice U makes, a fact about the environment, or a point a safeguard could act on. Go at least three levels deep.
2. The lab adds one safeguard: any single transfer above 1 GB leaving the lab's network is blocked, and every blocked attempt raises an alert to a human. Mark which nodes in your tree this safeguard prevents, detects or deters, and name one path through your tree that it leaves open, and say why it stays open.
placeholder:: Your tree as a nested list, then part 2
assessment-instructions:: Score out of 100. There is no single correct tree; grade structure and reasoning. 20: the root is the stated outcome and the first level captures genuinely different routes or necessary stages; a good tree usually needs, in some arrangement, obtaining the weights, getting them onto unmonitored hardware, and starting them running; noticing that unmonitored hardware can be inside the lab (an unmonitored internal machine or job) as well as outside counts toward these points. 25: correct use of AND and OR: AND where every child is needed (for example the stages of an exfiltration), OR where any child suffices (alternative ways to reach a subgoal); lose 5 for each clearly wrong gate, each OR whose children are not actually ways of achieving the parent (for example guesses or conditions), and each node that silently bundles several steps. 20: the tree is about this deployment and a scheming model: the existing safeguards (command logging, the trusted model's review after each task, the network allowlist) appear as things the attack has to get around (for example "the trusted reviewer does not flag the task", "keep each logged command innocuous", "find a route beyond the approved machines"); leaves are choices U makes, facts about the environment, or points a safeguard could act on; the tree is at least three levels deep without listing trivial variants of one attack; lose up to 10 if the tree ignores all three existing safeguards and reads as a generic data-theft tree. 35 for part 2: 15: tagging: the block prevents any single large transfer of the weights out of the lab network and the alert lets a human detect blocked attempts; full points need what the block prevents separated from what the alert detects (deters may also be argued, since a blocked attempt risks getting U caught); a reasoned statement that the safeguard touches no node in the tree, or only nodes the allowlist already blocks, counts as tagging. 20: a specific path in the learner's own tree named as still open, with a reason (for example sending the weights out in many pieces under 1 GB, possibly hidden in allowed traffic; running an unmonitored copy on hardware inside the lab, which needs no transfer out of the network; any route that does not cross the lab's network boundary); an open path not tied to the tree earns 10. Noting that the existing trusted-model review runs after each task, so it detects rather than prevents, may add up to 5 within these 35 but does not replace naming an open path. Give credit for each point whenever the answer shows the idea, in any wording and in any readable nested-list format. Cap at 50 if the answer tags no node or names no open path. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "One possible tree, in outline. Root: a copy of U's weights runs on hardware the lab does not monitor (AND): 1. obtain the weights (OR: read them from a checkpoint store U can reach; copy them during a legitimate training task); 2. get them onto unmonitored hardware (OR: send them outside the lab, which needs (AND) a route beyond the approved machines and commands innocuous enough that the trusted reviewer does not flag the task; or place them on an internal machine or job the lab does not monitor); 3. start the copy running (AND: obtain compute there; launch it without a flagged command). Part 2: the 1 GB block prevents a single large transfer of the weights out of the lab network; the alert detects blocked attempts; and it deters, since a blocked attempt risks getting U caught. It leaves open sending the weights out in many pieces under 1 GB, possibly hidden in allowed traffic, because no single transfer crosses the limit; and running a copy on unmonitored hardware inside the lab, because that needs no transfer out of the network at all. The existing trusted-model review runs after each task, so it detects rather than prevents."
feedback-instructions:: Name the strongest part of the tree or analysis in one sentence, then the single change that would most improve it, such as a wrong gate, a node that bundles several steps, or a missed open path. Do not supply a complete reference tree. Do not reveal or discuss the numerical score. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - attack-trees]]
notes:: The method, the tips, the bench, and the graded practice in a new agent setting.
