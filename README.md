# Lens Academy Educational Content

Course modules and lessons for the Lens Academy AI Safety curriculum.
## Read-only:
- Staging (automatically synced from {--{"author":"Elias's AI","timestamp":1783544059149}@@Obsidian with 10s delay): https://github.com/lucbrinkman/lens-educational-content/tree/staging--}{++{"author":"Elias's AI","timestamp":1783544059149}@@the relay within seconds): https://github.com/Lens-Academy/lens-edu-staging/tree/staging++}
- Production: {--{"author":"Elias's AI","timestamp":1783544059149}@@https://github.com/lucbrinkman/lens-educational-content/tree/main--}{++{"author":"Elias's AI","timestamp":1783544059149}@@https://github.com/Lens-Academy/lens-edu-production++}

## Workflow
```
Obsidian {++{"author":"Elias's AI","timestamp":1783544059149}@@/ web editor / AI (MCP) ++}→ Relay →{--{"author":"Elias's AI","timestamp":1783544059149}@@ staging branch--}{++{"author":"Elias's AI","timestamp":1783544059149}@@ lens-edu-staging++} → {++{"author":"Elias's AI","timestamp":1783544059149}@@promotion ++}PR → {--{"author":"Elias's AI","timestamp":1783544059149}@@main branch--}{++{"author":"Elias's AI","timestamp":1783544059149}@@lens-edu-production++} → Production
```

1. **Edit {--{"author":"Elias's AI","timestamp":1783544059149}@@in Obsidian**--}{++{"author":"Elias's AI","timestamp":1783544059149}@@via Relay**++} - {--{"author":"Elias's AI","timestamp":1783544059149}@@All content--}{++{"author":"Elias's AI","timestamp":1783544059149}@@Content++} is authored in {--{"author":"Elias's AI","timestamp":1783544059149}@@Obsidians--}{++{"author":"Elias's AI","timestamp":1783544059149}@@Obsidian (Relay plugin), the web editor (editor.lensacademy.org), or by AI through the lens-relay MCP (AI edits land as suggestions a human accepts in the editor)++}
2. **Auto-sync to staging** - Relay automatically syncs changes to the `staging` branch{++{"author":"Elias's AI","timestamp":1783544059149}@@ of `lens-edu-staging`++}
	- The staging branch is used directly by {--{"author":"Elias's AI","timestamp":1783544059149}@@our--}{++{"author":"Elias's AI","timestamp":1783544059149}@@the++} staging {--{"author":"Elias's AI","timestamp":1783544059149}@@website. Changed made in Obsidian--}{++{"author":"Elias's AI","timestamp":1783544059149}@@website (staging.lensacademy.org). Changes++} should be reflected {--{"author":"Elias's AI","timestamp":1783544059149}@@on the website --}{++{"author":"Elias's AI","timestamp":1783544059149}@@there ++}after 20s or so.{++{"author":"Elias's AI","timestamp":1783544059149}@@ Check https://staging.lensacademy.org/validate for format errors.++}
3. {--{"author":"Elias's AI","timestamp":1783544059149}@@**Create--}{++{"author":"Elias's AI","timestamp":1783544059149}@@**Promotion++} PR** - {--{"author":"Elias's AI","timestamp":1783544059149}@@Manually open--}{++{"author":"Elias's AI","timestamp":1783544059149}@@Open++} a pull request {--{"author":"Elias's AI","timestamp":1783544059149}@@from `staging` to `main`--}{++{"author":"Elias's AI","timestamp":1783544059149}@@in `lens-edu-production` promoting the content from staging++}
4. **Validation** - GitHub Actions validates {--{"author":"Elias's AI","timestamp":1783544059149}@@lesson--}{++{"author":"Elias's AI","timestamp":1783544059149}@@content++} format and wiki-links{--{"author":"Elias's AI","timestamp":1783544059149}@@
5. **Merge to main**--}{++{"author":"Elias's AI","timestamp":1783544059149}@@ on the promotion PR
5. **Merge**++} - Once checks pass,{--{"author":"Elias's AI","timestamp":1783544059149}@@ squash and--} merge{--{"author":"Elias's AI","timestamp":1783544059149}@@ to `main`--}
6. **Production** -{--{"author":"Elias's AI","timestamp":1783544059149}@@ The `main` branch--}{++{"author":"Elias's AI","timestamp":1783544059149}@@ `lens-edu-production`++} is used directly by the production {--{"author":"Elias's AI","timestamp":1783544059149}@@website..--}{++{"author":"Elias's AI","timestamp":1783544059149}@@website (lensacademy.org)++}
## Important

- **Never {--{"author":"Elias's AI","timestamp":1783544059149}@@commit directly to the Lens Educational Content repo on Github** - --}{++{"author":"Elias's AI","timestamp":1783544059149}@@push to `lens-edu-staging` on GitHub** - it is continuously overwritten by the relay sync; pushes break the sync. ++}All {++{"author":"Elias's AI","timestamp":1783544059149}@@content ++}changes must come through Relay.
-{--{"author":"Elias's AI","timestamp":1783544059149}@@ That includes pushing to the staging branch and any other branches.--}{++{"author":"Elias's AI","timestamp":1783544059149}@@ `lens-edu-production` only changes through promotion PRs.++}

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

