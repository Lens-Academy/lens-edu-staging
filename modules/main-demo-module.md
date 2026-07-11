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

#### Chat
instructions:: [[../prompts/demo-tutor-style.md]]

%% You can also mix your own text with prompt links: each prompts/ wikilink expands to its file's body verbatim (you control the spacing around it), and the surrounding text is kept. This lets several lenses share one base prompt while adding lens-specific context around it. Wikilinks that don't point into prompts/ are left as ordinary text. %%

#### Chat
instructions:: The learner has just gone through this demo module. [[../prompts/demo-tutor-style.md]] Focus the conversation on which segment type they would like to try authoring first.

%% Modules also contains learning outcomes.  %%

%% Please look inside the above file before continuing. %%


%% A module can contain as many learning outcomes and lenses as you want. 

Each learning outcome is shown to the user as one test page, and each lens is shown to the user as one content page. 

The lenses show in the same order in the learner's UI as in this module file. Learning outcomes are declared FIRST — at the top of the module (or, in modules with submodules, at the top of their submodule) — and the platform automatically renders their tests at the END of the module or submodule. So the declaration order is: learning outcome(s) first, then the lenses that teach them.%%

%% Now that we have a feel for how modules and learning outcomes work, let's have a look at what's possible inside of lenses. 

Take a look at the following Lens: %%
# Lens:
source:: [[../Lenses/Article excerpt demo]]

%% After you've looked at the above Lens, take a look at this next one: %%
# Lens:
source:: [[../Lenses/Article annotation and text collapse demo]]

%% You've now seen how you can add annotations and collapsed sections from within Article files, as well as define from:: and to:: inside Lenses. Note that `::collapse` and `from::`/`to::` show up in the same way to the user. Any text that's collapsed by them is hidden behind bracketed ellipsis `[...]` that the user can click on to see the collapsed text. %%

%% Now take a look at the following Lens, demoing a video: %%
# Lens:
source:: [[../Lenses/video demo]]

%% You can also mix segment types in one lens. This next lens does article, video, article: %%
# Lens:
source:: [[../Lenses/Article video article demo]]

%% You may have already seen a #### Question field inside of the Learning Outcome Demo. We can also add those fields inside lenses. They then serve as practice, instead of as a test. The UX is very similar.%%
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