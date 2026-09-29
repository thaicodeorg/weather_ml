---
name: reviewing-papers-from-pdfs
description: Use when the user asks to review a paper held in Sources/Research Paper/ (for example "I want to review <filename>.pdf"), wants an academic literature review of a PDF, asks to turn a research PDF into a vault source note, or asks whether a paper has already been reviewed in Literatures Notes/Reviews Kmutnb/.
---

# Reviewing papers from PDFs

## Overview

Turn one PDF in the corpus into a source note plus a Kmutnb review. The vault's
conventions are **not** stated in the request and are usually guessed wrong: the
request misspells three paths, the review filename has a pattern, the frontmatter
has fixed values, and page citations can be silently off by one. This file is
those conventions.

**REQUIRED SUB-SKILL:** use `extracting-pdfs-with-markitdown` when extraction
itself misbehaves (fused words, `UnicodeEncodeError`, tuning questions). Do not
re-derive the `x_tolerance` value here.

## Paths

| Thing | Exact path |
|---|---|
| PDF corpus | `Sources/Research Paper/` — **only**. `Sources/Report Paper/` is out of scope |
| Converted notes | `Sources/Markdown/` |
| Review template | `Templates/Review Kmutnb.md` (a file, not a folder) |
| Reviews | `Literatures Notes/Reviews Kmutnb/` |
| Converter / validator | `Files/tools/pdf_to_markdown.py` / `Files/tools/validate_notes.py` |

The request is usually wrong in exactly these ways: `Sources/markdown/` (lowercase
m), `templates/review kmutnb` (a file, capitalised), `Literatures Notes/Rivews
kmutnb/` (two typos). Use the table, not the request. If the user names a PDF that
only exists in `Report Paper/`, say so rather than converting it.

## Steps

**1. Resolve** the filename against `Sources/Research Paper/`. If the match is
inexact, list candidates and confirm. Accept a full path if given.

**2. Check for existing work.** A note at `Sources/Markdown/<stem>.md` means skip
step 3. A review in `Literatures Notes/Reviews Kmutnb/` for the same paper means
report its path and stop — do not write a second one.

**3. Convert.** `python Files/tools/pdf_to_markdown.py`, then
`python Files/tools/validate_notes.py`.

The converter has no per-file flag: it converts **every** PDF in
`Sources/Research Paper/` that lacks a note, not just the requested one. Never
pass `--force`. After running, report which notes it created; if it created notes
for papers you were not asked about, say so and offer to remove them.

**4. Read** the converted note for the title, authors, year, and the content each
section needs. Take the year from the paper itself, not the filename.

**5. Write** the review to `Literatures Notes/Reviews Kmutnb/`.

Filename: the paper's title **verbatim as printed on page 1**, then the author and
year — `<Paper title> (<Surname> et al. <Year>).md`. Examples:
`AIFS - ECMWF's data-driven forecasting system (Lang et al. 2024).md`.

Frontmatter, exactly these keys:

```yaml
type: review
created: <today, YYYY-MM-DD>
tags: []
status: seed
course: Kmutnb seminar
due:                      # blank unless the user supplied a deadline
confidence: medium
sources:
  - "[[Sources/Markdown/<stem>]]"
```

`due:` ships blank in the template and in every existing review. A deadline you did
not receive is not a deadline to guess. `confidence: medium` reflects having read
the paper; the template's `low` default is for unread sources.

Body: the title heading, then the eight section headings, in the template's order,
all at `##`. Keep them exactly as named:

1. Source Information
2. Research Objective
3. Problem
4. Gap Addressed in paper
5. Findings and conclusion
6. Limitations or Weakness
7. Implication or suggestions on future research
8. How your search can fill gap

**6. Verify.** `python Files/tools/validate_notes.py`, confirm every `[[...]]`
resolves, and confirm every page anchor is in range. `Tech Folk Insights.md`
(missing frontmatter) and any mojibake in older notes are pre-existing — report
them as such, not as new breakage.

## Page citations

```text
[[Sources/Research Paper/<file>.pdf#page=<sheet>|<label>, p.<folio>]]
```

`#page=` is the **physical 1-based sheet**, because that is what the PDF pager
opens. `p.` is the **printed folio** on that sheet. These coincide in most of this
corpus and diverge in others — arXiv cover sheets, front matter, and blank sheets
are numbered differently, so a paper can be 23 sheets with 22 numbered pages.

Before citing, confirm the folio printed on the sheet you are pointing at. Carrying
one number across both fields without checking is the most common way these
reviews end up quietly wrong.

## Common mistakes

| Mistake | Result | Instead |
|---|---|---|
| Trusting the request's paths | Notes land in misspelled new folders | Use the path table |
| `#page=` and `p.` set from one assumption | Every citation off by one | Read the printed folio |
| Guessing the paper's year from the filename | Wrong year in the filename | Read page 1 |
| Running the converter and reporting success | Unrequested notes created silently | Report which notes appeared |
| Editing the source note's body to fix wording | Breaks the immutability boundary | Summarise in the review |
| Filling `due:` with a plausible date | Fabricated deadline | Leave it blank |
| Adding or renaming a heading | Fails the template contract | Keep the eight, in order |
