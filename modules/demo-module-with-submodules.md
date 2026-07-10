---
id: 2a8a12a4-1ab1-4711-8fe3-deadbc507177
slug: demo-submodules
title: Submodules demo
---

%% This module demonstrates `# Submodule:` markers. The imports inside the submodules use dummies because the structure is the point here, not the content of the imported lenses. %%

# Submodule: foo
slug:: demo-foo

%% You can add `slug::` under the submodule heading when you want a stable URL segment instead of one generated from the title. %%

## Lens:
source:: [[../Lenses/Dummy lens]]

## Lens:
optional:: true
source:: [[../Lenses/Dummy lens 2]]

# Submodule: bar
slug:: demo-bar

%% Submodules can contain imported lenses and imported learning outcomes. %%

## Lens:
optional:: true
source:: [[../Lenses/Dummy lens 3]]

## Learning Outcome:
source:: [[../Learning Outcomes/Dummy learning outcome]]


%% By the way, if a module contains submodules, then all the lenses must be inside of submodules. So you must start the file with defining a submodule. %%