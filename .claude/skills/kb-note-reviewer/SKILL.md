---
name: kb-note-reviewer
description: Review notes that are staged or committed (new changes ready to enter the KB), auto-generate complete YAML frontmatter (title, tags, summary, related), and sync the folder's index.md. Use this skill whenever the user says "review notes", "check frontmatter", "ready to commit", or similar — it scopes automatically to git-tracked changes rather than the whole vault.
---

# KB Note Reviewer

This skill reviews Obsidian engineering-management knowledge base notes that have new git changes (staged, unstaged, or in the latest commit), writes complete YAML frontmatter where it's missing or incomplete, and keeps the folder `index.md` accurate. It never audits the whole vault — it only touches files that have changed.

---

## What you're working with

The KB lives at the working directory. Run `git status --short` and `git diff --name-only HEAD` to find the set of changed `.md` files. Only review those files — do not scan the entire vault. Every `.md` note (except `index.md` and `_references.md`) must have valid YAML frontmatter. If frontmatter is absent or has empty/placeholder fields, generate it from the note's content.

---

## Frontmatter schema

Every note starts with this exact block — no extra fields, nothing omitted:

```yaml
---
title: Human-readable title (not the filename)
tags: [theme-tag, type-tag]
summary: One or two sentences: what the note contains and when to reach for it.
related: [other-note-slug]   # omit the .md extension; empty list [] is fine
---
```

### Tag taxonomy — use ONLY these tags

**Theme tags** (pick 1):
| Tag | When |
|-----|------|
| `decision-making` | Frameworks and techniques for making decisions |
| `architecture` | Technical architecture choices, RFCs, ADRs |
| `delegation` | How and when to delegate work or authority |
| `hiring` | Recruiting, interviewing, leveling |
| `incidents` | Incident response, postmortems, on-call |
| `communication` | Writing, async communication, stakeholder management |
| `leadership` | People management, org dynamics, influence |
| `process` | Team processes, ceremonies, ways of working |

**Type tags** (pick 1):
| Tag | When |
|-----|------|
| `framework` | A named model or structured approach |
| `technique` | A specific practice or method |
| `example` | Concrete real-world scenarios or case studies |
| `reference` | A reading list or external link collection |
| `template` | A reusable template or checklist |

Always include exactly one theme tag and one type tag (2 tags total is the norm; 3 is acceptable only when the note genuinely spans two themes).

---

## How to generate the frontmatter

Read the full note content, then:

1. **title** — derive a clear, human-readable title from the heading or topic. Never use the filename as the title verbatim; rephrase to natural English.

2. **tags** — infer from the content:
   - Pick the theme tag whose description best matches the note's subject
   - Pick the type tag that matches the note's form (is it a named framework? a practical technique? a set of examples?)
   - Never invent tags outside the taxonomy

3. **summary** — write 1–2 sentences that answer: "What does this note contain, and when would I open it?" Be specific. Avoid filler phrases like "This note covers…" — just state the substance. The summary must be accurate enough that someone scanning the index can judge relevance without opening the file.

4. **related** — scan the other notes in the same folder (read the folder's `index.md` to get a quick list). Link any note whose topic directly complements this one. Use only the filename slug (no path, no `.md`). If no clear relationship exists, use `[]`.

---

## Updating index.md

After writing or confirming frontmatter, update the folder's `index.md` table. The table format is:

```markdown
| Note | Description |
|------|-------------|
| [slug](slug.md) | One-line description taken from the note's summary |
```

Rules:
- The link text is the filename slug (no `.md`)
- The description column is a short paraphrase of the `summary` field — one clause, not the full summary sentence
- Do not duplicate entries; if the note is already listed, update the description if it changed
- Keep the table sorted alphabetically by slug, with `_references` always last

---

## Updating README.md

After processing all notes, check whether the `README.md` Folder Map and Quick Navigation sections are still accurate. Update them if any of the following are true:

- A changed note belongs to a folder not yet listed in the **Folder Map** table — add a new row
- A new folder was created (has an `index.md`) and is absent from both the Folder Map and Quick Navigation — add it to both
- A folder's description in the Folder Map is stale relative to the notes now in it — update the description

The README Folder Map format is:

```markdown
| Folder | What it covers |
|--------|---------------|
| `folder-name` | One sentence describing the folder's scope |
```

The Quick Navigation section lists links to each folder's `index.md`:

```markdown
- [folder-name/index.md](folder-name/index.md)
```

Rules:
- Keep both the Folder Map table and the Quick Navigation list sorted alphabetically by folder name
- Derive the folder description from the notes present in that folder — make it accurate and specific, not generic
- Do not remove existing folders from README unless their directory no longer exists
- Do not edit any other section of README.md (intro paragraph, "How to Use" section, etc.)

---

## Workflow

### Determine scope from git

Always start here — never skip this step:

1. Run `git status --short` to find untracked and modified files
2. Run `git diff --name-only HEAD` to find files changed since the last commit
3. Combine both lists, deduplicate, and filter to `.md` files only
4. Exclude `index.md`, `_references.md`, `CLAUDE.md`, `CONTRIBUTING.md`, and `README.md`
5. That filtered list is your **review set** — process only those files

If the review set is empty, report "No changed notes to review" and stop.

### Per-note review (applied to each file in the review set)

1. Read the note file
2. Check if frontmatter is present and complete (all four fields non-empty, tags from taxonomy)
3. If anything is missing or wrong, rewrite the frontmatter block — leave the body content untouched
4. Read the folder's `index.md`
5. Add or update the note's row in the index table
6. Report what you changed (frontmatter added/fixed, index updated)

### README sync (run once after all per-note reviews are done)

1. Read `README.md`
2. Collect the set of folders that contain any reviewed note
3. For each such folder, check whether it appears in the Folder Map table and Quick Navigation list
4. If a folder is missing from either section, add it
5. If a folder's Folder Map description is stale, update it
6. Write the updated README only if changes were needed; report "README: updated" or "README: already current"

---

## What NOT to change

- Do not edit the body content of any note — only the frontmatter block
- Do not rename files
- Do not create new folders or notes
- Do not modify `_references.md` frontmatter (it follows the same schema but is a reference collection — be careful with its tags: use `reference` as the type tag)

---

## Output format

After completing the review, give the user a concise report:

```
Reviewed: <note-name>.md
- Frontmatter: [added | fixed | already complete]
  - title: "..."
  - tags: [...]
  - summary: "..."
  - related: [...]
- index.md: [updated | already current]

README.md: [updated | already current]
```

For folder audits, one row per note in the report, then a one-line total.
