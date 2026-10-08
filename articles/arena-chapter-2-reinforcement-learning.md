---
title: "Chapter 2: Reinforcement Learning"
author:
  - "Arena"
source_url: "https://learn.arena.education/chapter2_rl/22_vpg/"
published: 2026-10-08
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## \[2.2.2\] - VPG ^2-2-2

> **Colab: [exercises](https://colab.research.google.com/github/ARENA-education/ARENA_materials/blob/main/chapter2_rl/exercises/part22_vpg/2.2.2_VPG_exercises.ipynb?t=20261007) | [solutions](https://colab.research.google.com/github/ARENA-education/ARENA_materials/blob/main/chapter2_rl/exercises/part22_vpg/2.2.2_VPG_solutions.ipynb?t=20261007)**

Please send any problems / bugs on the `#errata` channel in the [Slack group](https://info-arena.github.io/ARENA_img/slack.html), and ask any questions on the dedicated channels for this chapter of material.

If you want to change to dark mode, you can do this by clicking the three horizontal lines in the top-right, then navigating to Settings → Theme.

Links to all other chapters: [(0) Fundamentals](https://arena-chapter0-fundamentals.streamlit.app/), [(1) Transformer Interpretability](https://arena-chapter1-transformer-interp.streamlit.app/), [(2) RL](https://arena-chapter2-rl.streamlit.app/).

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/arena-chapter-2-reinforcement-learning-img1-77f04078.png)

## Introduction ^introduction

In this section, you'll implement Vanilla Policy Gradient (VPG), the first policy gradient algorithm upon which more advanced RL algorithms like PPO are based.

## Content & Learning Objectives ^content-learning-objectives

### 1️⃣ VPG ^1-vpg

The Policy Gradient Theorem is what all policy gradient methods are based on: it allows us to compute the gradient of the return, something that would naively not have a well defined gradient. We'll then implement Vanilla Policy Gradient (VPG) on the CartPole environment.

> ##### Learning Objectives
> 
> -   Understand the Policy Gradient Theorem
> -   Understand the VPG algorithm: how to perform on-policy policy gradient

## Setup (don't read, just run!) ^setup-dont-read-just

```
import sys
import time
import warnings
from collections import namedtuple
from dataclasses import dataclass
from pathlib import Path
from typing import Any, Callable, Optional

import gymnasium as gym
import numpy as np
import torch as t
import torch.nn.functional as F
import wandb
from eindex import eindex
from gymnasium.spaces import Box, Discrete
from jaxtyping import Bool, Float, Int
from torch import Tensor, nn
from torchinfo import summary
from tqdm.auto import tqdm

warnings.filterwarnings("ignore")

# Make sure exercises are in the path
chapter = "chapter2_rl"
section = "part22_vpg"
root_dir = next(p for p in Path.cwd().parents if (p / chapter).exists())
exercises_dir = root_dir / chapter / "exercises"
section_dir = exercises_dir / section
if str(exercises_dir) not in sys.path:
    sys.path.append(str(exercises_dir))

from gpu_env import CartPole, MountainCar
from gpu_probe import Probe1, Probe2, Probe3, Probe4, Probe5
from rl_utils import ENVS, AtariEnvs, LiveVideo, log_greedy_rollout_video, log_grid_video, make_envs
import part22_vpg.tests as tests
from part1_intro_to_rl.utils import set_global_seeds
from plotly_utils import line, plot_cartpole_obs_and_dones

# The networks in this section are tiny, and if you train on the CPU with
# PyTorch's default of one thread per core, threads spend longer
# coordinating than computing. Adjust if needed.
t.set_num_threads(min(4, t.get_num_threads()))

# CartPole will train just fine on a CPU as we need few parallel environments, and the neural network is very small
# Feel free to change this to "cpu" if you find it runs faster
device = t.device("mps" if t.backends.mps.is_available() else "cuda" if t.cuda.is_available() else "cpu")

MAIN = __name__ == "__main__"
```
