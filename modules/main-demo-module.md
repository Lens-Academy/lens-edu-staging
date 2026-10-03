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
duration_minutes:: 5

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
duration_minutes:: 8

#### Chat
instructions:: [[../prompts/demo-tutor-style]]

%% You can also mix your own text with prompt links: each prompts/ wikilink expands to its file's body verbatim (you control the spacing around it), and the surrounding text is kept. This lets several lenses share one base prompt while adding lens-specific context around it. Wikilinks that don't point into prompts/ are left as ordinary text. %%

#### Chat
instructions:: The learner has just gone through this demo module. [[../prompts/demo-tutor-style.md]] Focus the conversation on which segment type they would like to try authoring first.

%% State a lens's expected time in its metadata (frontmatter or `field::` on an inline lens): prefer `reading_minutes` + `tutor_minutes` (content time + AI time, displayed split; either alone works, `tutor_minutes: 0` means no tutor time), or one `duration_minutes` total, never both. Authored values replace the platform's word-count estimate wherever time shows; without them the estimate applies, so set them on nearly every lens and re-estimate when you change one. The lens below demonstrates the split form. %%

# Lens: Authored lens duration
id:: 3fad77ed-c6a2-4b11-a137-e56a1bb350da
tldr:: This lens sets reading_minutes:: 4 and tutor_minutes:: 6, so its time badge shows "4 min + 6 min tutor" instead of the word-count estimate.
summary_for_tutor:: Demo lens with reading_minutes:: 4 and tutor_minutes:: 6, showing that authored values replace the platform's computed time estimate. A Chat segment stands in for the declared tutor time.
reading_minutes:: 4
tutor_minutes:: 6

#### Text
content::
This lens has `reading_minutes:: 4` and `tutor_minutes:: 6`, so its badge shows "4 min + 6 min tutor" even though the text would compute to under a minute. A single `duration_minutes:: 10` would show one plain total instead, and with no fields the platform falls back to its computed estimate.

#### Chat
instructions::
The learner is looking at a demo of authored lens durations (reading_minutes, tutor_minutes, duration_minutes). Answer questions about how they work; keep replies short.

%% Modules also contains learning outcomes.  %%

%% Please look inside the above file before continuing. %%


%% A module can contain as many learning outcomes and lenses as you want. 

Each learning outcome is shown to the user as one test page, and each lens is shown to the user as one content page. 

The lenses show in the same order in the learner's UI as in this module file. Learning outcomes are declared FIRST — at the top of the module (or, in modules with submodules, at the top of their submodule) — and the platform automatically renders their tests at the END of the module or submodule. So the declaration order is: learning outcome(s) first, then the lenses that teach them.%%

%% Now that we have a feel for how modules and learning outcomes work, let's look at shared authored-content features inside a normal Lens. %%
# Lens:
source:: [[../Lenses/Authored content features demo]]

%% Callouts can hold whole segments (questions, excerpts, widgets, further callouts), nested to any depth, and a callout inside an article can hold a question too: %%
# Lens:
source:: [[../Lenses/Nested callouts demo]]

%% Article segments add source-specific presentation around imported prose. First see how excerpt boundaries work: %%
# Lens:
source:: [[../Lenses/Article excerpt demo]]

%% To choose what the sidebar credits for a whole lens, put `sidebar_author:` in the lens's frontmatter (or `sidebar_author::` on an inline lens): a name replaces the article authors and video channels in the sidebar entry, the module overview and card links, and `none` credits nobody. Bylines and the source bar keep the article's author. %%
# Lens: Choosing the sidebar credit
id:: e4296b35-2f55-4225-bd44-5aa14231f6d1
sidebar_author:: Lens Academy
tldr:: Shows sidebar_author:: on a lens: the sidebar entry credits the name it gives, while the byline still names the article's author.
summary_for_tutor:: Demo lens for the sidebar_author lens field. A Text segment explains the field, then an Article segment quotes the one-sentence CAIS Statement on AI Risk. The lens sets sidebar_author:: Lens Academy, so the sidebar credits Lens Academy while the byline names the Center for AI Safety.
reading_minutes:: 1

#### Text
content::
This lens sets `sidebar_author:: Lens Academy`. Its sidebar entry credits Lens Academy instead of the quoted article's author, while the byline below still names the Center for AI Safety.

#### Article
source:: [[../articles/safety-statement-on-ai-extinction-risk-cais]]
from:: "**Mitigating the risk of extinction from AI"
to:: "Signatories:"

%% An article's `author_url:` frontmatter (one URL, or a list in the same order as `author`) turns the author's name into a link: in the byline, the source bar and this lens's sidebar entry. %%
# Lens: Linking the author
id:: 456648fa-9602-4ca3-8f77-22bbe0c7364e
tldr:: Shows author_url: in an article's frontmatter: the author's name links to their page, in the byline and in the sidebar.
summary_for_tutor:: Demo lens for the author_url: article field. A Text segment explains the field, then an Article segment shows the opening of the Article presentation demo, whose frontmatter sets author_url: https://lensacademy.org, so the byline's "Lens Academy" is a link.
reading_minutes:: 1

#### Text
content::
The article below has `author_url: https://lensacademy.org` in its frontmatter, so the author's name links to that page (opening in a new tab), both in the byline and in this lens's sidebar entry. Hover over it there: the name is its own link inside the row.

#### Article
source:: [[../articles/Article annotation and text collapse demo]]
from:: "This short article exists"
to:: "source attribution with author and publication date"

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

%% Response segments use the same syntax in surveys, normal Lenses, and Learning Outcome tests. This Lens explains Question: Open, Question: Rating, Question: Choice, Question: FillBlank, and Question: Ranking. Always write the subtype; a bare `#### Question` is the legacy form and should not appear in new content. %%
# Lens:
source:: [[../Lenses/Response to question segments]]

%% We also have a roleplay feature, where the user can voice chat with an AI: %%
# Lens:
source:: [[../Lenses/Roleplay demo]]

%% An interview is a roleplay with fixed questions and no character: the interviewer asks them one at a time and a separate assessor scores each answer afterwards. This lens shows two interviews in a row. %%
# Lens:
source:: [[../Lenses/Interview demo]]

%% Finally, please see how Lenses can link to other Lenses: %%
# Lens:
optional:: true
source:: [[../Lenses/Links and cards demo]]


%% When done with the lenses in this module, return to the course file ([[../courses/Demo Course]]) and go into the next modules to have a look at different ways of formatting modules.%% 