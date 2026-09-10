---
id: '9c44d9bd-067d-4749-a396-c48732a1d35a'
title: "Attack Trees"
tldr: "A safe can be opened four ways, and one of them is to be standing there when it is installed. An attack tree puts the attacker's goal at the root and every route to it underneath: OR nodes where any child is enough, AND nodes where all of them are needed. Then you build one yourself, against a model trying to slip a backdoor into production."
summary_for_tutor: "Module 1 (Introduction, overview, and threat modeling). An adaptation of Bruce Schneier's 1999 article 'Attack Trees', with the trees redrawn. Part 1 is the method and the worked safe example, including the AND/OR distinction (AND means both subgoals must be satisfied; everything that is not an AND node is an OR node). Part 2 is the 'Creating Attack Trees' procedure. Part 3 is a tips section that Schneier does not have: do not be so specific that you lose generality, do not use children that are not attacks (the 'try 0000, try 0001' trap under an OR gate), and do not write overloaded nodes that silently compose several steps. Part 4 is the widget: a red team versus blue team bench where the learner builds an attack tree for 'a backdoor lands in production' and revises it as three defensive affordances arrive one at a time. The bench has no answer key on purpose. If a learner asks whether their tree is right, ask instead which node the attack now depends on and what would have to be true for the defence to miss it. The trees on this page are rendered as nested outlines rather than XLab's drawn figures."
reading_minutes: 30
tutor_minutes: 0
tags: []
---
#### Text
content::
Adapted from Bruce Schneier, "Attack Trees," *Dr. Dobb's Journal*, December 1999. The trees are redrawn.

Attack trees provide a formal, methodical way of describing the security of systems, based on various attacks. Basically, you can represent attacks against a system in a tree structure, with the goal as the root node and different ways of achieving that goal as leaf nodes.

The following, for example, is a simple attack tree against a physical safe. The gate written next to a node says how its children combine: under OR any single child is enough, under AND every child is needed.

- **Open Safe** (OR)
    - Pick Lock
    - **Learn Combo** (OR)
        - Find Written Combo
        - **Get Combo From Target** (OR)
            - Threaten
            - Blackmail
            - **Eavesdrop** (AND)
                - Listen to Conversation
                - Get Target to State Combo
            - Bribe
    - Cut Open Safe
    - Install Improperly

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

- **Get Combo From Target** (OR)
    - Threaten With a Knife
    - Threaten With a Gun
    - Threaten With a Crowbar
    - ⋯

Instead, a tree that composes nodes that involve similar attacks would be more representative of attacker cognition:

- **Get Combo From Target** (OR)
    - Threaten
    - Blackmail
    - Eavesdrop
    - Bribe

:::callout {title="A subtler trap: nodes that aren't attacks" tone="amber"}
Suppose you tried to decompose "learn the combo" into "try 0000," "try 0001," "try 0002," … These are overly specific attacks but they also aren't attacks. Under an OR gate, each child is supposed to be a way of achieving the goal, and "try 0000" only opens the safe in the world where the combination happens to be 0000.
:::

Also, try not to have overcomplicated or conditioned nodes, as you might be composing multiple possible nodes!

Take, for example, the following tree:

- **Open Safe** (OR)
    - Pick Lock
    - Learn Combo by Eavesdropping on the Target Saying the Combo
    - Cut Open Safe

Instead, decomposing attacks helps your attack tree stay organized and might allow you to find other attacks:

- **Open Safe** (OR)
    - Pick Lock
    - **Learn Combo** (OR)
        - Find Written Combo
        - Get Combo From Target
    - Cut Open Safe

#### Text
content::
\## Practice: A backdoor lands in production

Build the threat model yourself, one round at a time. Red finds the best attack and maps its necessary conditions; blue receives an affordance and tags the nodes it touches; red revises. Your work is saved as you go, so you can leave the bench and come back to it.

The world you are attacking is the backdoored-code setting from [[../Lenses/XLab Control - ai-control-paper|AI Control: Improving Safety Despite Intentional Subversion]], the next lesson: an untrusted model writes code that ships on passing tests, and you add measures one at a time.

#### Widget
source:: [[../widgets/xlab-control-attack-tree-bench]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Schneier, Bruce. "Attack Trees." *Dr. Dobb's Journal*, Dec. 1999. [schneier.com](https://www.schneier.com/academic/archives/1999/12/attack_trees.html)
*The article this lesson adapts: the method, the safe example, and the AND/OR distinction.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, 12 Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The source of the practice scenario: the untrusted model, the backdoor definition, and the three affordances the bench hands the blue team.*

XLab. "Attack Trees." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/attack-trees)
*The source lesson this page adapts, including the tips section and the practice bench.*
:::
