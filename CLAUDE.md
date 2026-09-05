# Claude Code Instructions for This Knowledge Base

## What This Repo Is

A personal engineering management knowledge base maintained in Obsidian and versioned with git. Notes are Markdown files organized into topic folders.

## Conventions

### File naming
- Notes use kebab-case: `key-person-risk.md`
- Reference collections are named `_references.md` (underscore prefix keeps them sorted first in Obsidian).

### Frontmatter
Every note must have frontmatter with `title`, `tags`, `summary`, and `related`. See `CONTRIBUTING.md` for the exact schema and the controlled tag taxonomy.

### Folder structure
- One folder per topic area (e.g. `decision-making`, `hiring`, `incidents`)
- Every folder has an `index.md` — check it before opening individual notes to understand what's inside
- Don't create subfolders within a topic until that topic has 10+ notes

### Before creating a new note
1. Check the relevant folder's `index.md` to see if a note already covers the topic
2. Check `_references.md` in the folder — the topic may only need a link, not a full note
3. Add the new note to `index.md` and fill in all frontmatter fields immediately

### When editing existing notes
- Do not remove or alter existing frontmatter fields
- If a note is missing frontmatter, add it following the template in `CONTRIBUTING.md`
- Keep summaries accurate — update the `summary` field if the note's content changes significantly

## Folder Map
See `README.md` for the current list of folders and what each covers.
