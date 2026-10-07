---
id: 'a075bf5f-c4eb-4304-95ac-2429e992602f'
slug: xlab-control-ac2-u3
title: "Unit 3: Monitoring and resampling in real deployments"
---
%% Unit 3 of AI Control 2 (requires AI Control 1), from the October 2026 three-course re-cut of XLab's AI Control track (AI Control 1, 2 and 3, five units each; approved by Elias 2026-10-02). Its lenses were in "XLab Control P1 D5 High-stakes monitoring and mitigation", old unit modules now in _deprecated; lens files are unchanged except position text. Lens order follows XLab's track. Core self-study 223 minutes from the lens frontmatter on 2026-10-02 (150 reading, 73 tutor), lens by lens as reading+tutor: monitoring-and-mitigation 30+0; control-monitoring-in-deployments 50+8; ctrl-z-resampling 45+25; ctrl-z-resampling-2 25+40. Optional, not counted: synchronous-monitors 10+15. Plus about 15 minutes for the two end-of-unit tests of learning outcomes that used to sit in AI Control 1 ("Monitoring synchrony and recovery" and "Resampling protocols"), attached here because the teaching in their suggested lenses completes in this unit. About 238 in total. Learning outcomes for this unit's other lenses come in a later step. %%

# Learning Outcome:
source:: [[../Learning Outcomes/Monitoring synchrony and recovery]]

# Learning Outcome:
source:: [[../Learning Outcomes/Resampling protocols]]

# Lens: Welcome to Unit 3
id:: e15f16ce-9383-4ccd-8385-e203635739fc
tldr:: What you will learn in Unit 3: monitoring and resampling in real deployments.
summary_for_tutor:: Short opening page of Unit 3 (Monitoring and resampling in real deployments) of AI Control 2. It lists what the learner will be able to do after the unit. Do not teach the unit's content here; if asked, point to the lesson that covers it.
reading_minutes:: 1
tutor_minutes:: 0
#### Text
content::
\## In this unit you will

- Explain resampling: when a command looks suspicious, ask the model again.
- Reason about monitoring at deployment scale: many instances in parallel, reviewers who answer late, attacks spread over many steps.
- Work through the Ctrl-Z paper: how repeated suspicion becomes evidence, and what changes when the monitor is a copy of the model.

# Lens:
source:: [[../Lenses/XLab Control - monitoring-and-mitigation]]

# Lens:
source:: [[../Lenses/XLab Control - control-monitoring-in-deployments]]

# Lens:
source:: [[../Lenses/XLab Control - synchronous-monitors]]
optional:: true

# Lens:
source:: [[../Lenses/XLab Control - ctrl-z-resampling]]

# Lens:
source:: [[../Lenses/XLab Control - ctrl-z-resampling-2]]
