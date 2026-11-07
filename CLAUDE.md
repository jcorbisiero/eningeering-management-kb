# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

A personal engineering management knowledge base maintained in Obsidian and versioned with git. Notes are Markdown files organized into topic folders. The KB is published as a static site via [Quartz](https://quartz.jzhao.xyz/) at `jcorbisiero.github.io/eningeering-management-kb`.

## Folder Map

| Folder | What it covers |
|--------|---------------|
| `ai` | LLMs, AI-assisted development, and the impact of AI on engineering organizations |
| `coaching` | Coaching techniques and question frameworks for developing engineers and managers |
| `communication` | Techniques for clear writing, asking better questions, and stakeholder communication |
| `culture` | Psychological safety, knowledge sharing, and avoiding organizational anti-patterns |
| `decision-making` | Frameworks for prioritization, delegation, RFCs/ADRs, and decision anti-patterns |
| `feedback` | Giving and receiving feedback — performance conversations, calibration, feedback culture |
| `hiring-recruiting-interviews` | Interview questions, resume guidance, hiring, and leveling |
| `leadership-management` | Engineering leadership — long-term judgment and managing organizational risk |
| `ownership` | Ownership mindset, agency, and operating end-to-end |
| `safety-engineering` | Catching failure modes early, designing for resilience, avoiding incidents |
| `software-engineering` | Code quality, bug reporting, debugging, and system architecture |
| `strategy` | Setting direction, roadmapping, and translating vision into executable plans |

Every folder has an `index.md` — check it first to understand what's already inside before creating notes or searching.

## Conventions

### File naming
- Notes: kebab-case (`key-person-risk.md`)
- Reference collections: `_references.md` (underscore prefix sorts first in Obsidian)
- Reflection prompts: `_questions-to-consider.md` (underscore prefix; one per topic folder)
- Templates: `<topic>-template.md` inside a `templates/` subfolder

### Frontmatter
Every note must start with this exact block — no exceptions:

```yaml
---
title: Human-readable title of the note
tags: [tag1, tag2]
summary: One or two sentences describing what this note contains and when to reach for it.
related: [other-note-slug, another-note-slug]
---
```

- **title** — required, plain text
- **tags** — required, 1–3 tags, must come from the taxonomy below; do not invent tags
- **summary** — required, never a placeholder; this is what any tool or person uses to judge relevance without opening the note
- **related** — optional; filename slugs only, no path or `.md` extension

### Tag Taxonomy

Theme tags:
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
| `ai` | Topics where AI tooling meaningfully changes the practice described |

Type tags:
| Tag | When to use |
|-----|-------------|
| `framework` | A named model or structured approach |
| `technique` | A specific practice or method |
| `example` | Concrete real-world scenarios or case studies |
| `reference` | A reading list or external link collection |
| `template` | A reusable template or checklist |

### Folder structure
- One folder per topic area; don't create subfolders until a topic has 10+ notes
- Every folder needs an `index.md` created immediately when the folder is created
- Every folder needs a `_questions-to-consider.md` created immediately when the folder is created; it must contain 3 sections of 3 self-reflection questions tailored to that topic, following the same three-section structure used across the KB (self/individual, team/org, looking ahead)

### Templates
- Live in `templates/` subfolder within a topic folder
- No YAML frontmatter
- Not listed in the folder's `index.md`

## Before creating a new note
1. Check the folder's `index.md` — does a note already cover this topic?
2. Check `_references.md` — does the topic only need a link, not a full note?
3. After creating: add the note to `index.md` and fill in all frontmatter fields immediately

## When creating a new folder
1. Create `index.md` immediately
2. Create `_questions-to-consider.md` immediately — 3 sections, 3 questions each, tailored to the topic
3. Create `_references.md` if there are any relevant external links
4. Add the folder to the Folder Map in this file

## When editing existing notes
- Never remove or alter existing frontmatter fields
- If a note is missing frontmatter, add it using the schema above
- Update the `summary` field if the note's content changes significantly
