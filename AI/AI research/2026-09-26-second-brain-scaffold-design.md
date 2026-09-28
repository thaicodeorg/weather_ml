---
type: research
created: 2026-09-26
status: draft
tags:
  - meta
  - vault-design
question: How should this Obsidian vault be structured so it functions as a durable second brain?
method: Brainstorming session (superpowers) — 5 clarifying questions, 3 candidate approaches, approved design
confidence: high
sources: []
---

# Second Brain Scaffold — Design Spec

## Context

The vault `ECMWF_ML` has a correct directory skeleton and five ingested sources, but no
conventions layer: no `index.md`, no `log.md`, no `AGENTS.md`, only two templates (one of
which is misplaced), and empty `Permanets Notes/`, `Literatures Notes/`, `AI/AI research/`,
and `AI/logs/`. An agent operating here has no persistent instruction set, so every session
re-derives the same conventions and drifts.

This spec defines the scaffolding that closes that gap. It does **not** process the five
existing sources — that is a separate task with its own approval.

## Current state (verified 2026-09-26)

| Path | State |
|---|---|
| `Sources/Report Paper/` | 1 PDF (`AS2025_Lang.pdf`) |
| `Sources/Research Paper/` | 3 PDFs (AIFS 2406.01465v2, AIFS update 2509.18994v1, AIFS-CRPS s44387-026-00073-7) |
| `Sources/URL/` | 1 markdown clipping (HF paper page, arXiv 2412.15832) |
| `Sources/Youtube/` | 1 transcript note (ECMWF AIFS) |
| `Templates/` | `Review Kmutnb templates.md` only. The misplaced Web Clipper copy of the AIFS-CRPS page recorded at survey is no longer present here |
| `Permanets Notes/`, `Literatures Notes/`, `Fleeting Notes/` | empty at survey; renamed by hand to `Permanent Note/`, `Literature Note/`, `Fleeting Note/` before Task 2 ran, which is the state Task 2 found. Task 2 then restored the plural names: `Permanent Note/` → `Permanent Notes/`, `Literature Note/` → `Literatures Notes/` (carrying `Reviews Kmutnb/`), `Fleeting Note/` → `Fleeting Notes/` — the names this spec and the plan use thereafter. `Literature Note/` holds one empty subdirectory, `Reviews Kmutnb/` |
| `AI/AI research/` | 2 markdown files: this spec and the implementation plan |
| `AI/logs/` | empty |
| `Files/` | `tools/` holding the vault validator and its unit tests; `__pycache__/` bytecode is gitignored |
| `.obsidian/` | core plugins plus one enabled community plugin, `pdf-plus`; `community-plugins.json` now exists, `templatesFolder` is configured, and `app.json` holds the seven settings written by Task 2 |
| git | initialized as part of this plan's execution; binary PDFs gitignored |

Enabled and relevant: `properties`, `bases`, `templates`, `graph`, `backlink`, `daily-notes`.
Not available: Dataview, Templater. One community plugin is present, `pdf-plus`.

## Decisions

| # | Decision | Rationale |
|---|---|---|
| 1 | Scope is scaffolding only; source processing deferred | Keeps convention-building separate from research work, each with its own approval |
| 2 | Templates are domain-neutral schemas with AIFS worked examples | Reusable structure without locking the vault to one research domain |
| 3 | Rename `Permanets Notes/` → `Permanent Notes/` | Fixes a typo before any note exists, so no links break. "Permanent note" is the standard term (Forte/PARA) |
| 4 | One MOC per section, co-located as that section's `index.md` | Scales past ~50 notes; each section navigable independently; no new top-level folder |
| 5 | Initialize git, ignore `.obsidian/workspace.json` | Real diffs and history alongside Obsidian Sync; excludes the highest-churn file |
| 6 | **Approach A** — typed frontmatter contract, prose body | Most of the query power of a full taxonomy at near-zero maintenance cost. B (minimal frontmatter) forfeits `bases`; C (full taxonomy) rots to empty fields |
| 7 | `AGENTS.md` is a tight contract that links out for detail | It loads into every session's context; length is a real per-session cost |

## Goals

- A persistent, machine-readable operating contract at the vault root (`AGENTS.md`).
- A typed frontmatter schema across seven note types, enforced by templates.
- Navigable entry points: a root hub plus five MOCs.
- Mechanical enforcement of the wiki-link rule via `.obsidian/app.json`, not agent memory.
- A demonstrated logging convention: this task writes its own log as the first entry.
- Version history from the initial commit onward.

## Non-goals

- Processing, summarising, or distilling the five existing sources.
- Installing community plugins (Dataview, Templater).
- Building `.base` views. The YAML makes them possible later; YAGNI until enough notes exist.
- Defining the research domain itself. Field values stay domain-neutral.
- Restructuring `Sources/` filenames, which carry provenance.

## Deliverables

### 1. Folder rename

`Permanets Notes/` → `Permanent Notes/`, reached from the singular `Permanent Note/` state
found on disk (see Current state). The same hand-rename had been applied to the sibling
sections, so all three renames executed under Task 2 were `Permanent Note/` →
`Permanent Notes/`, `Literature Note/` → `Literatures Notes/`, and `Fleeting Note/` →
`Fleeting Notes/`. Folders are empty; no link updates required.
`AGENTS.md` must reference the corrected names.

### 2. `AGENTS.md` (vault root, new)

Target ~60 lines. Sections:

1. **What this is** — one paragraph: an Obsidian vault used as a research second brain, currently focused on ECMWF ML weather forecasting (AIFS).
2. **Vault map** — the directory table, with the corrected folder name.
3. **Hard rules** — four, each one line:
   - Wiki-links only, always full-path from vault root (`[[Permanent Notes/foo]]`). Never relative markdown links.
   - `Sources/**` is immutable. Never edit a source file; corrections go in a literature note.
   - `confidence` is required on any note making a claim.
   - Every completed task produces a log (see Logging).
4. **Note types** — table mapping note type → folder → template file.
5. **Workflows** — three short numbered procedures: Ingest a source, Run research, Log a task. 3–5 steps each.
6. **Never do** — edit sources; use markdown links; write a permanent note without a `sources` link; skip the log.
7. **Pointers** — links to `[[index|Home]]`, `[[log]]`, and the relevant MOCs by full path.

Detail that would exceed the line budget (field semantics, worked examples) lives in the
templates themselves and in `[[AI/AI research/2026-09-26-second-brain-scaffold-design]]`.

### 3. Templates (7 new/replaced files in `Templates/`)

Shared frontmatter contract, present on every note:

```yaml
---
type: permanent | literature | review | source | fleeting | research | log
created: YYYY-MM-DD
tags: []
status: seed | draft | evergreen | archived
---
```

Field values are constrained, not free text:

- `type` — one of the seven listed. Determines folder and template.
- `status` — `seed` (captured, unprocessed, not yet reviewed) → `draft` (being worked on)
  → `evergreen` (refined, claim-bearing, worth linking to) → `archived` (superseded or
  retired, kept for history). Only `evergreen` permanent notes should be linked from MOCs.
- `confidence` — `high` (verified against an immutable source in `Sources/`, or peer-reviewed
  literature) · `medium` (single credible secondary source, or direct inference from a high
  source) · `low` (unverified, contested, or inferred). `low` is a prompt to verify, not a
  permanent state; a note whose `confidence` is `low` may not be promoted to `evergreen`
  while a MOC depends on its claim.

Per-type additions and body shape:

| Template file | Adds | Body |
|---|---|---|
| `Permanent Note.md` | `confidence: high\|medium\|low`, `sources: []` | One claim in your own words, then its evidence |
| `Literature Note.md` | `title`, `source`, `authors`, `year`, `venue`, `confidence` | Summary / Findings / Limitations / Gaps |
| `Review Kmutnb.md` | `course`, `due`, `confidence` | Existing Kmutnb headings, unchanged |
| `Source.md` | `source_type: pdf\|url\|youtube\|report`, `origin`, `author`, `published`, `retrieved`, `immutable: true` | Verbatim dump only |
| `Fleeting Note.md` | `promoted: false` | One loose thought + capture date |
| `AI Research.md` | `question`, `method`, `confidence` | Question → method → findings → gaps |
| `AI Log.md` | `timestamp`, `skills`, `confidence`, `files_touched` | Existing AI-log format |

Each template ships with a **worked AIFS example** in an HTML comment or fenced block below
the template body, so it is copy-paste ready without polluting the inserted note.

Existing `Review Kmutnb templates.md` is **replaced** by `Review Kmutnb.md` (its headings are
preserved verbatim; only typed frontmatter is added). The old filename is removed to avoid two
competing review templates.

`sources` and `confidence` are the two fields that make the academic discipline structural: a
permanent note lacking a `sources` link is an unsourced assertion, and both are queryable via
the `properties` and `bases` core plugins.

### 4. Navigation (6 new files)

```
index.md                        root hub
Sources/index.md                source catalogue
Literatures Notes/index.md      one entry per source → its literature note
Permanent Notes/index.md        concept map, grouped by theme
Fleeting Notes/index.md         triage inbox
AI/AI research/index.md         reports, syntheses, archify artifacts
```

MOCs are hand-curated, not auto-generated (no Dataview available; curation is what makes a MOC
worth reading). Each MOC ends with a **Gaps** section listing what is missing, which doubles as
the task queue.

Naming: six files share the basename `index.md`, so **a bare `[[index]]` is ambiguous and is
only permitted in a file inside the same folder as the target** (where Obsidian's
same-folder resolution makes it deterministic). Everywhere else, MOCs are referenced by full
path: `[[Permanent Notes/index|Concept Map]]`. The `|display` alias is used for section MOCs
so the link text stays readable.

Consequence for `AGENTS.md`: it sits at the vault root next to `index.md`, so its pointer to
the hub is `[[index|Home]]`. Every section MOC it references uses the full path.

`Files/` and `Templates/` get no MOC — attachments and templates are self-evident.

### 5. `.obsidian/app.json`

```json
{
  "promptDelete": false,
  "templatesFolder": "Templates",
  "attachmentFolderPath": "Files",
  "alwaysUpdateLinks": true,
  "useMarkdownLinks": false,
  "newLinkFormat": "absolute",
  "showUnsupportedFiles": true
}
```

`useMarkdownLinks: false` plus `newLinkFormat: "absolute"` make Obsidian itself emit
vault-root full-path wiki-links (`[[Permanent Notes/foo]]`), enforcing the hard rule
mechanically. `"absolute"` is required here: `"relative"` would emit `../../Permanent
Notes/foo` and `"shortest"` would emit a bare `foo`, both of which violate the rule.
`alwaysUpdateLinks: true` keeps links intact during the rename and future moves.

### 6. Logging

- `log.md` (root, new) — append-only, newest first, one line per task: timestamp, topic,
  skills, confidence, link to the detailed log.
- `AI/logs/YYYY-MM-DD-HHmm-topic.md` — detailed per-task record in the established format
  (Trigger, Skills Utilized, Confidence Assessment, Files Created/Modified, Actions Taken).
- `index.md` links both.
- This scaffold's own execution writes `AI/logs/2026-09-26-<time>-second-brain-scaffold.md`
  as the first entry, demonstrating the convention.

### 7. Cleanup — requires user confirmation before deleting

`Templates/Paper page - AIFS-CRPS Ensemble forecasting...md` is a Web Clipper capture that
duplicates `Sources/URL/Paper page - AIFS-CRPS Ensemble forecasting...md`. The two differ by
~40 bytes, so they are not byte-identical. A clipping in `Templates/` pollutes every "insert
template" action.

Plan: diff the two files, report the difference, and delete the `Templates/` copy **only after
the user confirms** the `Sources/URL/` copy is the canonical one.

### 8. git

- `git init`
- `.gitignore`: `.obsidian/workspace.json`, `.trash/`, `.obsidian/plugins/`
- Commit the spec, then commit the scaffold as a second commit so the spec's own addition is
  reviewable in isolation.

## Verification

1. Every template opens in Obsidian and inserts cleanly via core `templates` (spot-check
   `Permanent Note.md` and `AI Log.md`).
2. `AGENTS.md` references only paths that exist post-rename. Grep the vault for
   `Permanets Notes`: zero hits outside this spec and the implementation plan, which name the
   old folder only to document the rename.
3. All six `index.md` files resolve every wiki-link they contain (Obsidian shows no
   unresolved links).
4. `app.json` is valid JSON and Obsidian loads it without error.
5. `git status` is clean after the scaffold commit; `.obsidian/workspace.json` is untracked.
6. The new `AI/logs/` entry renders and links to the files it claims to have created.

## Out of scope (future, needs its own approval)

- Distilling the five existing sources into literature notes and permanent notes.
- Building `.base` views over the frontmatter.
- Archify HTML architecture diagrams linked from research notes.
- A `Fleeting Notes` → `Permanent Notes` promotion workflow.
