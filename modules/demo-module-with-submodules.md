---
id: 2a8a12a4-1ab1-4711-8fe3-deadbc507177
slug: demo-submodules
title: Submodules demo
---

%% This module demonstrates `# Submodule:` markers. The imports inside the submodules use dummies because the structure is the point here, not the content of the imported lenses. %%

# Submodule: Dummy Submodule 1
slug:: dummy-submodule-1

%% You can add `slug::` under the submodule heading when you want a stable URL segment instead of one generated from the title. %%

## Lens:
source:: [[../Lenses/Dummy lens]]

## Lens:
optional:: true
source:: [[../Lenses/Dummy lens 2]]

# Submodule: Dummy Submodule 2
slug:: dummy-submodule-2

%% Submodules can contain imported lenses and imported learning outcomes. %%

## Lens:
source:: [[../Lenses/Dummy lens 3]]

{--{"author":"Elias's AI","timestamp":1783777214272}@@## Learning Outcome:
source:: [[../Learning Outcomes/Dummy learning outcome]]--}{++{"author":"Elias's AI","timestamp":1783777214272}@@{>>{"author":"Elias's AI","timestamp":1783777214272}@@removed dangling dummy LO reference<<}++}


%% By the way, if a module contains submodules, then all its lenses must be inside of submodules. That is, you must start the file with defining a submodule. That is, you can't have a lens without a submodule first and then have a submodule.. %%