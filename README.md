# Lens Academy Educational Content

Course modules and lessons for the Lens Academy AI Safety curriculum.
## Read-only:
- Staging (automatically synced from the relay within seconds): https://github.com/Lens-Academy/lens-edu-staging/tree/staging
- Production: https://github.com/Lens-Academy/lens-edu-production

## Workflow
```
Obsidian / web editor / AI (MCP) → Relay → lens-edu-staging → promotion PR → lens-edu-production → Production
```

1. **Edit via Relay** - Content is authored in Obsidian (Relay plugin), the web editor (editor.lensacademy.org), or by AI through the lens-relay MCP (AI edits land as suggestions a human accepts in the editor)
2. **Auto-sync to staging** - Relay automatically syncs changes to the `staging` branch of `lens-edu-staging`
	- The staging branch is used directly by the staging website (staging.lensacademy.org). Changes should be reflected there after 20s or so. Check https://staging.lensacademy.org/validate for format errors.
3. **Promotion PR** - Open a pull request in `lens-edu-production` promoting the content from staging
4. **Validation** - GitHub Actions validates content format and wiki-links on the promotion PR
5. **Merge** - Once checks pass, merge
6. **Production** - `lens-edu-production` is used directly by the production website (lensacademy.org)
## Important

- **Never push to `lens-edu-staging` on GitHub** - it is continuously overwritten by the relay sync; pushes break the sync. All content changes must come through Relay.
- `lens-edu-production` only changes through promotion PRs.

## Structure
### Course structure
```
**Course** - ordered list of **Module** references, with `# Meeting:` markers in between - each module is a list of
: **Learning outcome** - where each has three params
:: 1. Name of outcome
:: 2. **Test** - how we'll assess whether the person learned the objective
:: 3. **Lens** - a learning flow which has
::: A. One **Resource** {article, video, a section from one of them, or a little app to teach something}
::: B. **Prompt(s)** for the AI tutor to talk to the student (optional)
::: C. Some extra bits like framing texts etc (optional)
```

This is implemented as shown below:
#### Modules
e.g. `Lens Edu/modules/module.md`
Required frontmatter: `slug`, `title` (`id` optional but conventional)

Any number of
\# Submodule: (groups the sections below it)
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

# Learning Outcome: Define Intelligence
source:: ![[../Learning Outcomes/Define Intelligence]]

# Lens:
optional:: true
source:: ![[../Lenses/Some Lens]]
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
id:: <uuid>
#### Question
content:: <the test question>
assessment-instructions:: <scoring rubric>

## Lens:
source:: ![[../Lenses/lens-name]]

## Lens:
source:: ![[../Lenses/second-lens]]
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

