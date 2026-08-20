---
id: f97b4ad0-7fcf-408c-835a-a0aca0be9e9b
slug: demo-basics
title: Demo basics
---

%% A module contains lenses and learning outcomes.%% 

# Learning Outcome:
source:: [[../Learning Outcomes/Learning Outcome Demo|Demo learning outcome]]

# Lens: Basic Example
id:: 83fac088-1e23-4249-98ce-604b3f7c65d8
tldr:: A worked example of a lens defined directly inside a module file, showing the Text and Chat segments that make up a single page.
summary_for_tutor:: Demo lens defined inline in the module. Contains a Text segment explaining that a lens is a page built from fields like Text and Chat, followed by a Chat segment illustrating how tutor instructions are attached to a page.

#### Text
content::
Here is a basic lens that is defined right within a module file. A Lens is basically a page, by the way. Lenses contain fields like `#### Text` and `#### Chat`.

#### Chat
instructions::
This is a demo chat segment. In real course content, use this field to tell the tutor what the learner just saw and what kind of conversation would be helpful next.


%% We'll now import a lens from an external file instead of defining it inside the module file.%%
# Lens: An imported lens
source:: [[../Lenses/Dummy lens]]

%% One benefit of importing is that we can reuse the same lens in different modules without copying its source text. Importing lenses is usually preferred over defining them directly in the module. %%

%% Importing also works for AI instructions. Prompt files live in the prompts/ folder, and their body is the prompt text (see [[../prompts/demo-tutor-style]]). If you set instructions:: (or ai-instructions:: on roleplays, or assessment-instructions:: on questions) to a wikilink pointing at a prompts/ file, the whole field is replaced by that file's contents: %%
# Lens: Prompt file demo
id:: 9e7cf6c7-c701-483a-90db-6e29db963bbd
tldr:: Shows how a lens can pull its tutor instructions from a shared prompt file instead of writing them inline, and how to mix your own text with a prompt link.
summary_for_tutor:: Demo lens with two Chat segments illustrating prompt-file imports: one whose instructions are a bare wikilink to prompts/demo-tutor-style (replaced by that file's body), and one that mixes inline text with an expanded prompt link.

#### Chat
instructions:: [[../prompts/demo-tutor-style]]

%% You can also mix your own text with prompt links: each prompts/ wikilink expands to its file's body verbatim (you control the spacing around it), and the surrounding text is kept. This lets several lenses share one base prompt while adding lens-specific context around it. Wikilinks that don't point into prompts/ are left as ordinary text. %%

#### Chat
instructions:: The learner has just gone through this demo module. [[../prompts/demo-tutor-style.md]] Focus the conversation on which segment type they would like to try authoring first.

%% Modules also contains learning outcomes.  %%

%% Please look inside the above file before continuing. %%


%% A module can contain as many learning outcomes and lenses as you want. 

Each learning outcome is shown to the user as one test page, and each lens is shown to the user as one content page. 

The lenses show in the same order in the learner's UI as in this module file. Learning outcomes are declared FIRST — at the top of the module (or, in modules with submodules, at the top of their submodule) — and the platform automatically renders their tests at the END of the module or submodule. So the declaration order is: learning outcome(s) first, then the lenses that teach them.%%

%% Now that we have a feel for how modules and learning outcomes work, let's look at shared authored-content features inside a normal Lens. %%
# Lens:
source:: [[../Lenses/Authored content features demo]]

%% Article segments add source-specific presentation around imported prose. First see how excerpt boundaries work: %%
# Lens:
source:: [[../Lenses/Article excerpt demo]]

%% This Lens shows Obsidian-style links that jump to headings or stable block markers within the same Lens. %%
# Lens:
source:: [[../Lenses/Same-lens links demo]]

%% Hidden text, Lens notes, footnotes, callouts, Markdown, and math work in normal Lens-authored content. Article segments separately add attribution, publication metadata, original-source links, article typography, excerpt controls, and media treatment. %%

%% Now take a look at the following Lens, demoing a video: %%
# Lens:
source:: [[../Lenses/video demo]]

%% You can also mix segment types in one lens. This next lens does article, video, article: %%
# Lens:
source:: [[../Lenses/Article video article demo]]

%% Questions use the same syntax in surveys, normal Lenses, and Learning Outcome tests. This Lens explains open-text, rating, choice, and fill-in-the-blank questions. %%
# Lens:
source:: [[../Lenses/Question demo]]

%% We also have a roleplay feature, where the user can voice chat with an AI: %%
# Lens:
source:: [[../Lenses/Roleplay demo]]

%% Finally, please see how Lenses can link to other Lenses: %%
# Lens:
optional:: true
source:: [[../Lenses/Links and cards demo]]


%% When done with the lenses in this module, return to the course file ([[../courses/Demo Course]]) and go into the next modules to have a look at different ways of formatting modules.%% 