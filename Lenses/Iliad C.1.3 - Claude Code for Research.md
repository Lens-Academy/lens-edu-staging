---
id: 'f681f1f3-a0d1-4792-9c58-aa2fb26677fa'
title: "C.1.3 Claude Code for Research"
tldr: "Use Claude Code on small steps in an AI safety research repo, with three exercises that each use a different feature, and a final project replicating Figure 1 of a paper."
summary_for_tutor: "Claude Code for Research section (Lecture 2) of Iliad worksheet C.1 Intro to ML Engineering: the Claude Code cheat sheet, an optional terminal setup, cloning the C.1.3 exercise repository, Exercise 1 with plan mode, Exercise 2 with subagents, Exercise 3 with git worktrees and goals, and a final project replicating Figure 1 from one of two papers (inference only, or on a GPU). Keep the feature names plan mode, subagents, worktrees. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Julian Schulz (Meridian Research)
  - Adam Newgas (Timaeus)
source_url: https://iliad-intensive.org/interpretability/intro-to-ml-engineering/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Claude Code for Research

Use Claude Code to do small steps in an AI safety research repo, each step with a different Claude Code tool.

Material:

[Claude Code cheat sheet](https://www.alignment-hive.com/cheatsheet)

::card[[../Lenses/alignment-hive-claude-code-cheat-sheet|Claude Code cheat sheet]]

\[optionally\] get a good [Terminal Claude Code setup](https://github.com/wusche1/dotfiles)

Clone [this repository](https://github.com/iliad-team/iliad-intensive-C.1.3/tree/main) for the exercises

* Do [Exercise 1](https://github.com/iliad-team/iliad-intensive-C.1.3/blob/claude_code_exercise/01/EXERCISE.md) using plan mode

* Do [Exercise 2](https://github.com/iliad-team/iliad-intensive-C.1.3/blob/claude_code_exercise/02/EXERCISE.md) using subagents

* Do [Exercise 3](https://github.com/iliad-team/iliad-intensive-C.1.3/blob/claude_code_exercise/03/EXERCISE.md) using the git worktree and goals

Final project: replicate a version of Figure 1 from one of these papers:

::card[[../Lenses/chen-reasoning-models-dont-always-say-what-they-think|Inference only, no GPU needed]]

::card[[../Lenses/arditi-refusal-in-language-models-is-mediated-by-a-single-direction|On a GPU]]

Content:

* Installing Claude code
* \[optionally\] installing a good terminal Claude Code setup
* Using a research template with good claude.md integration
* Using multiple agents at the same time
* Plan mode
* Subagents
* Worktrees
* Goals/loops
