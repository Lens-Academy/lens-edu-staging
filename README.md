# Lens Academy Educational Content

Course modules and lessons for the Lens Academy AI Safety curriculum.
## Read-only:
- Staging (automatically synced from Obsidian with 10s delay): https://github.com/lucbrinkman/lens-educational-content/tree/staging
- Production: https://github.com/lucbrinkman/lens-educational-content/tree/main

## Workflow
```
Obsidian → Relay → staging branch → PR → main branch → Production
```

1. **Edit in Obsidian** - All content is authored in Obsidians
2. **Auto-sync to staging** - Relay automatically syncs changes to the `staging` branch
	- The staging branch is used directly by our staging website. Changed made in Obsidian should be reflected on the website after 20s or so.
3. **Create PR** - Manually open a pull request from `staging` to `main`
4. **Validation** - GitHub Actions validates lesson format and wiki-links
5. **Merge to main** - Once checks pass, squash and merge to `main`
6. **Production** - The `main` branch is used directly by the production website..
## Important

- **Never commit directly to the Lens Educational Content repo on Github** - All changes must come through Relay.
- That includes pushing to the staging branch and any other branches.

## Structure
### Course structure
```
**Course** - list of 
: **Week** - where each week has 1 or more
:: **Module** - list of
::: **Learning outcome** - where each has three params
:::: 1. Name of outcome
:::: 2. **Test** - how we'll assess whether the person learned the objective
:::: 3. **Lens** - a learning flow which has
::::: A. One **Resource** {article, video, a section from one of them, or a little app to teach something}
::::: B. **Prompt(s)** for the AI tutor to talk to the student (optional)
::::: C. Some extra bits like framing texts etc (optional)
```

This is implemented as shown below:
#### Modules
e.g. `Lens Edu/modules/module.md`
Required frontmatter: `slug`, `title`, `id`

Any number of
\# Lens: (inline with `id::` + segments, or referenced with `source::`)
\# Learning Outcome:

Wiki-links must use relative paths (e.g. `[[../video_transcripts/...]]`) and targets must exist.

Example:
```md
# Lens: Welcome
id:: <uuid>
#### Text
content::
Lorum Ipsum

# Learning Outcome:
[[link to Learning Outcome note]]

# Lens:
optional:: true
source:: [[link to Lens note]]
```

#### Learning Outcomes
e.g. `Lens Edu/Learning Outcomes/learning-outcome.md`
Required frontmatter: `id`

Any number of
\## Test:
\## Lens:

Example:
```md
## Test:
[[Link to Test note]]

## Lens:
[[link to Lens note]]

## Lens: (optional)
[[Link to 2nd Lens note]]
```

#### Lenses
e.g. `Lens Edu/Lenses/lens.md`
Required frontmatter: `id`

Lenses are flat: frontmatter + H4 segments. No H3 section headers.

Valid segment types: `Text`, `Chat`, `Article`, `Video`, `Question`, `Roleplay`

Article/Video segments carry a `source::` field (inherited from prior segment of same type).

Example:
```md
#### Text
content::
Lorum Ipsum

#### Article
source:: [[../articles/article-name]]
to:: "exact quote where excerpt stops"

#### Text
content::
Lorum Ipsum

#### Chat
instructions::
You're an AI tutor
```

Video example:
```md
#### Video
source:: [[../video_transcripts/video-name]]
from:: 1:18
to:: 15:38
```

