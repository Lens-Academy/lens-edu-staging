---
tags:
  - validator-ignore
---
The glossary explains words a learner may not know. A learner sees a dotted line under a word. When they point at it or tap it, a small box shows what the word means. The first time a word appears on a lens page, it can get this line. Later uses on the same page do not.

A lens chooses which words get the line. Nothing is highlighted unless a lens asks for it.

## Glossary entries

Each entry is one file in `Lens Edu/glossary/`. The file name is the word as the box shows it, for example `AGI.md`.

```markdown
---
aliases:
  - "artificial general intelligence"
  - "AGIs"
---

%%
Add notes here:

%%

AI that is at least as good as humans at general problem-solving.
```

- **The body is the definition.** Write one or two plain sentences. You can use bold, italics and links. Do not use headings.
- **`aliases`** lists other ways the word is written: plurals, the long form of an acronym, other spellings. Leave it out if there are none. An entry with no aliases needs no frontmatter at all.
- **The `%%` block** is for notes between authors. Learners never see it.
- **One phrase belongs to one entry.** If two entries list the same phrase, the validator gives an error.
- A file name cannot hold `/`. Use a spelled-out name and put the short form in `aliases` (see `FLOP per second.md`).
- `tags: [wip]` works as on other files: a production lens cannot use a wip entry.

How the text is matched:

- Whole words only. "AGI" does not match inside "AGIle" or "pre-AGI".
- Upper and lower case do not matter, except for a phrase written all in capitals. "ADS" matches only "ADS", never "ads".
- Straight and curly apostrophes are the same.
- The longest phrase wins. If "AI alignment" and "alignment" are both on a lens, the text "AI alignment" gets the first one.
- Words in headings, links, code, footnotes and closed boxes (`:::hide`) never get the line.

The first entries were imported from the aisafety.info glossary on 2026-09-26. We have permission to use them.

## Choosing the words for a lens

Put the list in the lens frontmatter as `glossary_terms`, one link per line:

```yaml
glossary_terms:
  - "[[../glossary/AGI]]"
  - "[[../glossary/Reward hacking]]"
```

The list covers everything on the lens page: text segments and article excerpts. It never goes in an article file, because one article is used by lenses written for different learners.

The validator gives an error for a link that does not go to a file in `glossary/`. It gives a warning when a listed word does not appear on the lens page.

### Which words to list

List a word only if all of these are true:

1. **A learner at this point may not know it.** Think of the learner the course is for, after the lenses before this one. Leave out words that most adults who read the news know: "prompt", "ChatGPT", "OpenAI", "Google". Leave out words that the course audience knows. A technical course needs fewer entries than a course for newcomers.
2. **The course has not explained it before.** If an earlier required lens in the same course explains the word, or already lists it, leave it out. A word first explained in an optional lens still counts as new.
3. **This lens does not explain it where it first appears.** If the text itself defines the word ("Compute: the total number of steps…"), the line adds nothing.
4. **The first use on the page has the glossary meaning.** Only the first use gets the line. If the first "agent" on the page means a travel agent, leave the word out, even if a later use is the AI meaning.
5. **Understanding the word matters for this lens.** A name mentioned in passing ("DeepMind also tried this") does not need a line. A concept that the argument depends on does.

When unsure, leave it out. A missing line costs the learner a search. Too many lines make every page busy, and readers who know the words read more slowly.

### Filling the lists with an AI

An AI can suggest the lists for a whole course. The suggestions land as pending changes that an author accepts or rejects.

1. For every lens in the course, in course order, find the glossary words that appear on it, with the text around the first use. The platform repository has a script for this; ask a developer, or read the lens pages.
2. Go through the lenses in order. For each candidate word, apply the five rules above. Keep a running list of words the course has explained or listed so far (rule 2).
3. Add the chosen words to each lens as a suggestion. Do not change anything else in the lens.

The eval for this step is [[../AI Guide/Evals/Glossary Terms Eval]].
