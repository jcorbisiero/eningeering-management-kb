---
name: kb-note-reviewer
description: Review new or existing notes in this engineering management knowledge base, auto-generate complete YAML frontmatter (title, tags, summary, related), and sync the folder's index.md. Use this skill whenever the user mentions "new note", "frontmatter", "index", "add a note", "review notes", or creates/edits any .md file in the KB that might be missing or have incomplete frontmatter. Also use it after pasting raw content that should become a note, or when the user asks to "tidy up" or "audit" the knowledge base.
---

# KB Note Reviewer

This skill reviews Obsidian engineering-management knowledge base notes, writes complete YAML frontmatter where it's missing or incomplete, and keeps the folder `index.md` accurate. Always use this skill proactively whenever a new note is created or the user asks to review notes.

---

## What you're working with

The KB lives at the working directory. Every `.md` note (except `index.md` and `_references.md`) must have valid YAML frontmatter. If frontmatter is absent or has empty/placeholder fields, generate it from the note's content.

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

## Workflow

### Single note review

1. Read the note file
2. Check if frontmatter is present and complete (all four fields non-empty, tags from taxonomy)
3. If anything is missing or wrong, rewrite the frontmatter block — leave the body content untouched
4. Read the folder's `index.md`
5. Add or update the note's row in the index table
6. Report what you changed (frontmatter added/fixed, index updated)

### Folder audit (multiple notes)

When the user asks to audit or tidy a folder:

1. Read `index.md` to get the list of notes
2. Find all `.md` files in the folder (exclude `index.md` and `_references.md`)
3. For each note, check frontmatter completeness
4. Fix any issues and collect a summary of what changed
5. Rewrite `index.md` to reflect the current state of all notes — remove stale entries, add missing ones, correct descriptions
6. Report a short summary: N notes checked, M fixed, index updated

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
```

For folder audits, one row per note in the report, then a one-line total.
