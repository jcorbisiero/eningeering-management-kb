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
| [Note Title](slug.md) | One-line description taken from the note's summary |
```

Rules:
- The link text is the note's **title in natural English** — use the `title` field from frontmatter, converting to title case (e.g. "Key Person Risk", "How to Name Things"). Never use the raw filename slug. For `_references.md`, use `References` as the link text.
- The description column is a short paraphrase of the `summary` field — one clause, not the full summary sentence
- Do not duplicate entries; if the note is already listed, update the description if it changed
- Keep the table sorted alphabetically by slug, with `_references` always last

---

## Checking folder index.md frontmatter

Every folder's `index.md` must have the same YAML frontmatter schema as regular notes. Without it, Quartz will not register the folder as a page and the folder will not appear in the left navigation on the published site.

For each folder that contains a reviewed note, check whether the folder's `index.md` has complete frontmatter (all four fields: `title`, `tags`, `summary`, `related`). If frontmatter is absent or incomplete, generate and prepend it:

- **title** — the folder's human-readable name, derived from the `#` heading (e.g. "Safety Engineering", "AI")
- **tags** — pick the theme tag that best describes the folder's dominant subject, and `reference` as the type tag (folder indexes are overview pages, not individual techniques)
- **summary** — one or two sentences describing the folder's scope, derived from any existing description paragraph or from the notes it contains
- **related** — `[]` (folder indexes rarely have meaningful cross-links)

After writing or confirming the folder's frontmatter, report it in the output alongside the per-note results.

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

## Documents folder handling

Each topic folder may contain a `documents/` subdirectory holding supplementary reading material (PDFs, papers, saved articles, etc.) that is not available as a public web link. These files are resources, not notes — do not summarize them or create frontmatter for them.

When a file appears in the **documents set**:

1. Identify the parent folder (e.g., `ai/documents/some-paper.pdf` → folder `ai`)
2. Read the folder's `index.md`
3. Check whether a **Documents** section already exists in `index.md`. If not, append one after the note table:
   ```markdown
   ## Documents

   | File | Description |
   |------|-------------|
   | [Filename](documents/filename.pdf) | _Add a short description here_ |
   ```
4. If the section already exists, add a new row for the file if it is not already listed
5. Use the filename (with extension removed, spaces replacing hyphens) as the link text — e.g., `cafe-s-your-agent.pdf` → `Cafe S Your Agent`
6. Leave the description as a placeholder (`_Add a short description here_`) — do not invent a description from the filename
7. Report: `documents/filename — added to index.md Documents section`

Do not modify `_references.md` for documents; the Documents section in `index.md` is the only place they are recorded.

---

## Workflow

### Determine scope from git

Always start here — never skip this step:

1. Run `git status --short` to find untracked and modified files
2. Run `git diff --name-only HEAD` to find files changed since the last commit
3. Combine both lists and deduplicate
4. From this combined list, extract two separate sets:
   - **Review set**: `.md` files only, excluding `index.md`, `_references.md`, `CLAUDE.md`, `CONTRIBUTING.md`, and `README.md`
   - **Documents set**: any files under a `<folder>/documents/` path (any file type — PDFs, etc.)
5. If both sets are empty, report "No changed notes to review" and stop.

### Per-note review (applied to each file in the review set)

1. Read the note file
2. Determine whether the file is **new** (appeared as `??` in `git status --short`) or **existing** (modified tracked file)
3. Check if frontmatter is present and complete (all four fields non-empty, tags from taxonomy)
4. If anything is missing or wrong, rewrite the frontmatter block
5. Apply the **Spell check and grammar** rules to the note body
6. **If the file is new**: also apply the Markdown structure formatting rules to the body (headings, lists, paragraphs, tables, code blocks — no rewording)
7. Read the folder's `index.md`
8. Add or update the note's row in the index table using English title-case link text
9. Report what you changed (frontmatter added/fixed, spell/grammar fixed, body formatted, index updated)

### Documents pass (run after per-note reviews, before folder index frontmatter check)

For each file in the **documents set**:

1. Apply the **Documents folder handling** rules above
2. Write the updated `index.md` if a row was added
3. Report what changed

### Folder index frontmatter check (run once per folder after per-note reviews)

For each folder that contains a reviewed note:

1. Read the folder's `index.md`
2. Check whether complete YAML frontmatter is present (all four fields)
3. If missing or incomplete, generate and prepend frontmatter following the **Checking folder index.md frontmatter** rules above
4. Report: `index.md frontmatter: [added | already complete]`

### README sync (run once after all per-note reviews are done)

1. Read `README.md`
2. Collect the set of folders that contain any reviewed note
3. For each such folder, check whether it appears in the Folder Map table and Quick Navigation list
4. If a folder is missing from either section, add it
5. If a folder's Folder Map description is stale, update it
6. Write the updated README only if changes were needed; report "README: updated" or "README: already current"

### Quartz sync (run once after the README sync)

Follow the **Quartz web sync** section above to commit any changes made during this review and prompt the user to push.

---

## Quartz web sync

The KB is published as a static site via Quartz, deployed automatically by GitHub Actions whenever changes are pushed to `main`. After all per-note reviews and the README sync are done, run this step to get changes live.

### When to run Quartz sync

Run this step only if at least one file was actually modified during the review (frontmatter written, index updated, or README updated). Skip it if everything was already current.

### Steps

1. Run `git status --short` to confirm there are staged or unstaged changes.
2. Stage only the files that were touched during this review run:
   - The reviewed note files (frontmatter changes)
   - Any `index.md` files that were updated
   - `README.md` if it was updated
   - Do NOT stage unrelated files
3. Create a commit. Use this message format:
   ```
   kb: review notes — update frontmatter and indexes
   
   Notes reviewed: <comma-separated list of note slugs>
   ```
4. Tell the user: "Changes committed. Push to `main` to trigger the Quartz site rebuild: `git push origin main`"
5. Do NOT push automatically — pushing is the user's decision.

If there are no uncommitted changes after the review (nothing was modified), report "Quartz sync: nothing to commit" and skip steps 2–4.

---

## Spell check and grammar

Apply to **all notes** in the review set — both new and existing. Read the body of the note (excluding the frontmatter block) and fix:

- **Misspellings**: correct obvious typos and misspelled words (e.g., "recieve" → "receive", "occured" → "occurred")
- **Grammar errors**: fix subject-verb agreement, missing articles, incorrect tense, and similar mechanical errors
- **Punctuation**: fix missing or misplaced commas, unclosed quotes, double spaces

Do NOT:
- Rephrase sentences for style or clarity
- Change the author's word choices when the word is spelled correctly
- Restructure paragraphs or reorder ideas
- Add or remove content
- Change technical terms, proper nouns, product names, or intentional shorthand (e.g., "kb", "RFC", "ADR")

If no errors are found, report `Spell/grammar: clean`. If corrections were made, briefly list them: `Spell/grammar: fixed N issue(s) — <short list>`.

---

## Markdown structure formatting

Apply only to **new notes** (files that appear as untracked `??` in `git status --short`). Do not reformat the body of existing modified files.

When formatting the body of a new note, fix structural issues only — no rewording:

- **Headings**: Use ATX style (`#`, `##`, `###`). Ensure one blank line before and after every heading. The top-level heading (`#`) should match the `title` frontmatter field.
- **Lists**: Use `-` for unordered lists (not `*` or `+`). Indent nested items with 2 spaces. Add a blank line before and after a list that is not inline with a paragraph.
- **Paragraphs**: Separate every paragraph with exactly one blank line. Remove trailing spaces from lines.
- **Tables**: Align column separator pipes (`|`) consistently. Ensure a header separator row (`|---|---|`) immediately follows the header row.
- **Code blocks**: Use fenced code blocks (` ``` `) with a language identifier where possible. Ensure a blank line before and after every code block.
- **Emphasis**: Do not add or remove bold/italic — preserve the author's emphasis choices.

Do not change content: sentence wording, list item text, heading labels, or any substantive meaning.

---

## What NOT to change

- Do not edit the body content of **existing** notes — only their frontmatter block
- Do not rename files
- Do not create new folders or notes
- Do not modify `_references.md` frontmatter (it follows the same schema but is a reference collection — be careful with its tags: use `reference` as the type tag)

---

## Output format

After completing the review, give the user a concise report:

```
Reviewed: <note-name>.md  [new | existing]
- Frontmatter: [added | fixed | already complete]
  - title: "..."
  - tags: [...]
  - summary: "..."
  - related: [...]
- Spell/grammar: [clean | fixed N issue(s) — <short list>]
- Body formatting: [applied | skipped (existing note)]
- index.md row: [updated | already current]

Documents: <filename>  — [added to index.md Documents section | already listed]

Folder index.md frontmatter: [added | already complete]

README.md: [updated | already current]
Quartz sync: [committed — push to main to rebuild | nothing to commit]
```

For folder audits, one row per note in the report, then a one-line total.
