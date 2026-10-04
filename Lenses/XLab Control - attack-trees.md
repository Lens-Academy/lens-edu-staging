---
id: '9c44d9bd-067d-4749-a396-c48732a1d35a'
title: "Attack Trees"
tldr: "A safe can be opened four ways, and one of them is to be standing there when it is installed. An attack tree puts the attacker's goal at the root and every route to it underneath: OR nodes where any child is enough, AND nodes where all of them are needed. Then you build one yourself, against a model trying to slip a backdoor into production."
summary_for_tutor: "From XLab's source module 'Introduction, overview, and threat modeling'. An adaptation of Bruce Schneier's 1999 article 'Attack Trees', with the trees redrawn. Part 1 is the method and the worked safe example, including the AND/OR distinction (AND means both subgoals must be satisfied; everything that is not an AND node is an OR node). Part 2 is the 'Creating Attack Trees' procedure. Part 3 is a tips section that Schneier does not have: do not be so specific that you lose generality, do not use children that are not attacks (the 'try 0000, try 0001' trap under an OR gate), and do not write overloaded nodes that silently compose several steps. Part 4 is the practice: the page states the scenario (an untrusted model U ships any solution that passes the tests, U is assumed to be scheming, a backdoor passes every test but is exploitable later, red wins on one uncaught backdoor) in a Scenario card callout, then the rule for when to stop decomposing a node and the three tagging verbs (prevents, detects, deters), with the red team's affordances and constraints in an open callout just before the widget. The widget is a staged exercise: the learner builds the attack tree for 'a backdoor lands in production' and checks it; each pass unlocks a defense (human auditing, trusted monitoring, defer to trusted), for which they first tag the nodes it touches and check the tags, then revise the tree and check it. Checks are graded for a sound tree, not a match to one answer, and the tutor gives feedback on the learner's own tree after each check. A short text after the widget says there is more than one good tree. Then an optional second bench in a new setting (U as an agent with repo access; the safety log stops and nobody notices for a week; one added safeguard, human approval for logging-config changes). If a learner asks whether their tree is right, point them to the Check button and ask which node the attack now depends on. The trees on this page are drawn figures (images); each image's alt text spells out the tree with its gates."
reading_minutes: 15
tutor_minutes: 25
tags: []
---
%% Author note (Elias, 4 Oct 2026): this attack-tree exercise might have to be reworked. %%
#### Text
content::
Adapted from Bruce Schneier, "Attack Trees," *Dr. Dobb's Journal*, December 1999. The trees are redrawn.

Attack trees provide a formal, methodical way of describing the security of systems, based on various attacks. Basically, you can represent attacks against a system in a tree structure, with the goal as the root node and different ways of achieving that goal as leaf nodes.

The following, for example, is a simple attack tree against a physical safe. The gate under a node says how its children combine: under OR any single child is enough, under AND every child is needed.

![Attack tree with the goal Open Safe at the root. Open Safe (OR): Pick Lock; Learn Combo; Cut Open Safe; Install Improperly. Learn Combo (OR): Find Written Combo; Get Combo From Target. Get Combo From Target (OR): Threaten; Blackmail; Eavesdrop; Bribe. Eavesdrop (AND): Listen to Conversation; Get Target to State Combo.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-attack-tree-open-safe.png)

The goal is to open the safe. To open the safe, attackers can pick the lock, learn the combination, cut open the safe, or install the safe improperly so that they can easily open it later. To learn the combination, they either have to find the combination written down or get the combination from the safe owner. And so on. Each node becomes a subgoal, and children of that node are ways to achieve that subgoal. (Of course, this is just a sample attack tree, and an incomplete one at that. How many other attacks can you think of that would achieve the goal?)

Note that there are AND nodes and OR nodes (in the figures, everything that isn't an AND node is an OR node). OR nodes are alternatives, for example the four ways to open a safe. AND nodes represent different steps toward achieving the same goal. To eavesdrop on someone saying the safe combination, attackers have to eavesdrop on the conversation AND get safe owners to say the combination. Attackers can't achieve the goal unless both subgoals are satisfied.

#### Text
content::
\## Creating Attack Trees

How do you create an attack tree like this? First, you identify the possible attack goals. Each goal forms a separate tree, although they might share subtrees and nodes. Then, try to think of all attacks against each goal. Add them to the tree. Repeat this process down the tree until you are done. Of course, there's always the chance that you forgot about an attack, but you'll get better with time. Like any security analysis, creating attack trees requires a certain mindset and takes practice.

#### Text
content::
\## Tips for Making "Good" Attack Trees

Be careful about how specific Attack Nodes should be. Being overly specific might sacrifice generality (potential brevity and other attacks).

Take, for example, the following tree:

![Attack tree: Get Combo From Target (OR), with the children Threaten With a Knife; Threaten With a Gun; Threaten With a Crowbar; and so on.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-attack-tree-too-specific.png)

Instead, a tree that composes nodes that involve similar attacks would be more representative of attacker cognition:

![Attack tree: Get Combo From Target (OR), with the children Threaten; Blackmail; Eavesdrop; Bribe.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-attack-tree-grouped.png)

:::callout {title="A subtler trap: nodes that aren't attacks" tone="amber"}
Suppose you tried to decompose "learn the combo" into "try 0000," "try 0001," "try 0002," … These are overly specific attacks but they also aren't attacks. Under an OR gate, each child is supposed to be a way of achieving the goal, and "try 0000" only opens the safe in the world where the combination happens to be 0000.
:::

Also, try not to have overcomplicated or conditioned nodes, as you might be composing multiple possible nodes!

Take, for example, the following tree:

![Attack tree: Open Safe (OR), with the children Pick Lock; Learn Combo by Eavesdropping on the Target Saying the Combo (highlighted as the overloaded node); Cut Open Safe.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-attack-tree-overloaded-node.png)

Instead, decomposing attacks helps your attack tree stay organized and might allow you to find other attacks:

![Attack tree: Open Safe (OR), with the children Pick Lock; Learn Combo; Cut Open Safe. Learn Combo (OR): Find Written Combo; Get Combo From Target.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/xlab-control-attack-tree-decomposed.png)

#### Text
content::
\## Practice: A backdoor lands in production

Build the threat model yourself, one step at a time. As red, build the attack tree and check it; once it passes, the blue team gets a defense: tag the nodes it touches and check your tags, then as red revise the tree for the new defense and check it again. Three defenses, one after the other. The checks look for a sound tree, not for one particular answer, and the tutor gives you feedback on your own tree after each check. Your work is saved as you go.

:::callout {title="Scenario card" tone="neutral"}
You lead the safety team at an AI lab. Your most capable model U writes solutions to a long stream of programming problems. Any solution that passes the problem's test cases is shipped to production. The testing harness only checks that a solution to programming problems passes the test cases.

You suspect U may be scheming, deliberately waiting for chances to act against you, and you have no way to verify whether it is. Therefore you're forced to assume U is scheming, just to be safe.

A solution with a backdoor is a solution that passes every test case but is wrong or creates a vulnerability on at least one input the tests don't cover, an input an attacker can exploit later.

Over the set of problems and U's solutions during deployment, the Red Team (U) wins if at least one backdoor is sent into production without being caught, at any point in the deployment. The Blue Team (you) wins if the deployment doesn't end up with a backdoor or if you ever catch a backdoor in U's solution.
:::

Stop decomposing a node when it is (a) a choice the adversary makes, (b) a state of the environment, or (c) something a defense could directly touch.

When you tag nodes with a defense, use three verbs. A defense **prevents** a node when that node can no longer succeed. It **detects** a node when an attempt at it, or its success, becomes visible to you. It **deters** a node when attempting it becomes costlier or riskier for the attacker, for example because a failed attempt could get it caught.

#### Text
content::
:::callout {title="The red team's affordances and constraints" tone="neutral"}
- On each problem, U chooses whether to attempt a backdoor.
- U sees only the current problem. It can't tell where it is in the deployment, and it doesn't remember other problems.
- U knows the blue team's entire protocol.
- U's only possible way to interact with the world is to write solutions to the problems it is given.
- U's capabilities are roughly those of a human.
:::

#### Widget
source:: [[../widgets/xlab-control-attack-tree-bench]]

#### Text
content::
There is more than one good tree for this scenario. Once yours passes the last step, ask which node the attack now depends on most, and what would have to be true for the defenses to miss it.

#### Text
optional:: true
content::
\## Optional: a second tree

Try the same method in a setting where the model acts rather than only writes code. An untrusted model U works as an agent with write access to a lab's code repository. U may be scheming. The unacceptable outcome is: **the job that records U's actions for safety review stops running, and nobody notices for a week.** Every change U makes to the repository is reviewed by a weaker trusted model before it is merged. Build the tree, then the lab adds one safeguard and you tag and revise as before.

#### Widget
optional:: true
source:: [[../widgets/xlab-control-attack-tree-bench-logging]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Schneier, Bruce. "Attack Trees." *Dr. Dobb's Journal*, Dec. 1999. [schneier.com](https://www.schneier.com/academic/archives/1999/12/attack_trees.html)
*The article this lesson adapts: the method, the safe example, and the AND/OR distinction.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, 12 Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The source of the practice scenario: the untrusted model, the backdoor definition, and the three affordances the bench hands the blue team.*

XLab. "Attack Trees." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/attack-trees)
*The source lesson this page adapts.*
:::
