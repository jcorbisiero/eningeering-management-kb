# Contributing to This Knowledge Base

## Frontmatter Standard

Every note must start with this frontmatter block. No exceptions — a tool scanning many notes relies on these fields being present.

```yaml
---
title: Human-readable title of the note
tags: [tag1, tag2]
summary: One or two sentences describing what this note contains and when to reach for it.
related: [other-note-slug, another-note-slug]
---
```

### Field rules

- **title** — required, plain text, matches the note's topic not its filename
- **tags** — required, pick from the controlled taxonomy below; 1–3 tags per note
- **summary** — required, never leave as a placeholder; this is what any tool or person uses to judge relevance without opening the note
- **related** — optional; link to other notes in this KB by filename slug (no path, no `.md`)

---

## Tag Taxonomy

Use only tags from this list. Do not invent new tags — if a topic genuinely doesn't fit, propose an addition here first.

### Theme tags
| Tag | When to use |
|-----|-------------|
| `decision-making` | Frameworks and techniques for making decisions |
| `architecture` | Technical architecture choices, RFCs, ADRs |
| `delegation` | How and when to delegate work or authority |
| `hiring` | Recruiting, interviewing, leveling |
| `incidents` | Incident response, postmortems, on-call |
| `communication` | Writing, async communication, stakeholder management |
| `leadership` | People management, org dynamics, influence |
| `process` | Team processes, ceremonies, ways of working |

### Type tags
| Tag | When to use |
|-----|-------------|
| `framework` | A named model or structured approach |
| `technique` | A specific practice or method |
| `example` | Concrete real-world scenarios or case studies |
| `reference` | A reading list or external link collection |
| `template` | A reusable template or checklist |

---

## Folder Naming and Granularity

- **One topic = one folder.** Don't create subfolders within a topic unless a topic has more than ~10 notes and the subgroups are meaningfully different (e.g. `incidents/postmortems` only once `incidents` is crowded).
- **Folder names are kebab-case**, plural or singular based on natural English (e.g. `decision-making`, `hiring`, `incidents`).
- **Every folder gets an `index.md` when created** — a short list of the notes inside with one-line descriptions. Do this immediately, not as a retrofit.
- **Note filenames are kebab-case** and describe the content, not the source (e.g. `rfc-process.md` not `itnext-article.md`).
- **References go in `_references.md`** inside the folder — a running list of source links, not a standalone note.

---

## Checklist for a New Note

- [ ] Frontmatter block present with all required fields filled in
- [ ] `summary` is a real description, not a placeholder
- [ ] Tags are from the controlled taxonomy
- [ ] Note is listed in the folder's `index.md`
- [ ] Related notes are linked in the `related` field
