---
name: review-kmutnb
description: Use when the user says "review kmutnb", asks to review a paper held anywhere under Sources/Research Paper/ (including subfolders such as arxiv.org/, IEEE/, ScienceDirect/, SpringerNature/, mdpi.com/, Nature.com/, icic/, ametsoc.org/), wants an academic literature review of a PDF, asks to turn a research PDF into a vault source note, or asks whether a paper has already been reviewed in Literatures Notes/Reviews Kmutnb/.
---

# Reviewing papers into the Kmutnb review format

## Overview

Turn one PDF in the corpus into a source note plus a review in the Kmutnb seminar
format. The vault's conventions are **not** stated in the request and are usually
guessed wrong: the request misspells paths, PDFs sit in publisher subfolders, the
review filename has a pattern, the frontmatter has fixed values, and page
citations can be silently off by one. This file is those conventions.

**REQUIRED SUB-SKILL:** `extracting-pdfs-with-markitdown` for the extraction step
and for any tuning question. Do not re-derive `x_tolerance` here.

## Role

Act as a research assistant in computer science and machine learning, specialised
in weather forecast models. Write for a graduate seminar: assume the reader knows
NWP, RMSE, ensemble spread, Brier and CRPS, and GraphCast, AIFS and FourCastNet.
Judge every paper on the things this field actually argues about — skill scores
against a stated baseline, whether the verification reference is common,
deterministic versus probabilistic training, blurring with lead time, resolution
and compute trade-offs, and whether a headline result is confounded. A review that
only paraphrases the abstract has failed.

Never invent numbers, citations, baselines or section titles. If the paper does
not say it, the review does not say it.

## Paths

| Thing | Exact path |
|---|---|
| PDF corpus | `Sources/Research Paper/**/*.pdf` — **recursive**, subfolders included. `Sources/Report Paper/` is out of scope |
| Converted notes | `Sources/Markdown/<subfolder>/<stem>.md` — mirrors the PDF tree |
| Review template | `Templates/Review Kmutnb.md` (a file, not a folder) |
| Reviews | `Literatures Notes/Reviews Kmutnb/` |
| Source-note template | `Templates/Source.md` |

Publisher subfolders in use: `arxiv.org/`, `IEEE/`, `ScienceDirect/`,
`SpringerNature/`, `mdpi.com/`, `Nature.com/`, `icic/`, `ametsoc.org/`. PDFs also
sit at the root of `Sources/Research Paper/`. Search the whole tree.

**Notes mirror the PDF's subfolder.** `ScienceDirect/x.pdf` becomes
`Sources/Markdown/ScienceDirect/x.md`. Never flatten. `ScienceDirect/` also
contains a nested `ScienceDirect_articles_27Sep2026_07-17-11.708/` holding
byte-identical duplicates of six papers; when the same paper exists twice, cite the
shallower copy and say so.

The request is usually wrong in exactly these ways: `Sources/markdown/`
(lowercase m), `templates/review kmutnb` (a file, capitalised),
`Literatures Notes/Rivews kmutnb/` (two typos), or a subfolder dropped from the
path. Use the table, not the request. If the user names a PDF that only exists in
`Report Paper/`, say so rather than converting it.

## Steps

**1. Resolve** the filename against `Sources/Research Paper/` recursively. If the
match is inexact, list candidates and confirm. Accept a full path if given. If the
same paper exists in several subfolders, list them and pick with the user.

**2. Check for existing work.** A note at the mirrored `Sources/Markdown/` path
means skip step 3. A review in `Literatures Notes/Reviews Kmutnb/` for the same
paper means report its path and stop — do not write a second one.

**3. Extract**, if no note exists. Follow `extracting-pdfs-with-markitdown`:
pdfplumber with `x_tolerance` at 2 or below, write UTF-8. There is no converter
script in this vault — `Files/tools/pdf_to_markdown.py` and
`Files/tools/validate_notes.py` referenced by earlier versions of this skill do
not exist. Verify by reading the first screenful of output; a clean run that
exits 0 with fused words is still fused.

**4. Write the source note** to the mirrored `Sources/Markdown/` path using
`Templates/Source.md`: `type: source`, `source_type: pdf`, `origin` as the plain
vault-relative path of the PDF (never a wiki-link), `immutable: true`, then the
extracted body verbatim below the template's marker line. Never edit the body to
fix wording — summarise in the review instead.

**5. Read** the note for the title, authors, year, section numbering and the
content each section needs. Take the year from the paper itself, not the
filename. Record the paper's own section numbers, because the citations in step 7
use them.

**6. Write the review** to `Literatures Notes/Reviews Kmutnb/`.

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
  - "[[Sources/Markdown/<subfolder>/<stem>]]"
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

Each of sections 2 to 7 must cite the page and section it draws on. Sections 8
and the closing paragraphs of 7 may argue past the paper without a citation, but
must not attribute new claims to it.

**7. Verify.** Confirm every `[[...]]` resolves, every page anchor is within the
sheet count, every section number in a label exists in the paper, and every review
heading matches the template exactly. Pre-existing breakage — `Tech Folk
Insights.md` missing frontmatter, mojibake in older notes — is reported as such,
not as new damage.

## Page and section citations

Every citation points back to the place in the PDF it came from, so the reader can
open the PDF at that line:

```text
[[Sources/Research Paper/<subfolder>/<file>.pdf#page=<sheet>|<Section no.> <Section title>, p.<folio>]]
```

Example, from an existing review:

```markdown
([[Sources/Research Paper/arxiv.org/2509.17658v1-fastnet-eng.pdf#page=12|5.2 Fine-tuning
horizon, p.12]])
```

Two numbers, one label:

- `#page=` is the **physical 1-based sheet**, because that is what the PDF pager
  opens.
- `p.` is the **printed folio** on that sheet.
- The leading `5.2 Fine-tuning horizon` is the paper's own section number and
  heading, copied verbatim.

The section title goes in the **label**, not in the anchor. Obsidian resolves a
`#page=` anchor reliably; a `#Some Heading` anchor resolves only when the PDF
outline happens to carry a matching entry, and silently fails to jump otherwise.
The label names the section either way, so the reader lands on the right sheet and
knows what to look for.

Add `, Fig. N` after the section title when a figure carries the claim, and keep the
figure number the paper printed. Examples: `5.2 Fine-tuning horizon, p.12`,
`Introduction, Fig. 1, p.2`, `3. Results, Fig. 4, p.6`.

## Building the section map

Map every cited sheet to its section before writing. Do it by extraction, not by
recall:

1. Read each page's text and mark the headings. Numbered headings match
   `^\d+(\.\d+)*\.?\s+\S`; unnumbered journals (npj, Science Advances, GRL) mark
   them with a larger font or a bold fontname instead, so compare each line's
   font size and fontname against the page's body size.
2. The section that owns a page is the last heading at or before it — unless
   another heading starts mid-page, in which case the claim's own paragraph
   decides. Blunn p.9 carries the `3.1` results above the `3.2` heading; both
   sections are live on that sheet.
3. If the claim is not on the sheet the review already cites, the page is wrong.
   Fix the page, and say so in the report. Do not relabel a wrong page into
   looking right.

Two-column layouts interleave, so a heading can appear visually below body text
it does not follow. When a section boundary looks wrong, dump that one page and
read it before assigning.

These three coincide in most of this corpus and diverge in others — arXiv cover
sheets, front matter, and blank sheets are numbered differently, so a paper can be
23 sheets with 22 numbered pages. Before citing, confirm the folio printed on the
sheet you are pointing at. Carrying one number across all fields without checking
is the most common way these reviews end up quietly wrong.

Cite the section that carries the claim, not the page where the sentence happens to
end up. Results spread across a figure and its caption should cite the figure's own
section.

## Common mistakes

| Mistake | Result | Instead |
|---|---|---|
| Trusting the request's paths | Notes land in misspelled new folders | Use the path table |
| Flattening `Sources/Markdown/` | Subfolder identity lost, duplicate stems collide | Mirror the PDF subfolder |
| Searching only the PDF root | 60+ papers in subfolders look missing | Search recursively |
| `#page=`, `p.` and section set from one assumption | Citations wrong or unresolvable | Read the printed folio and the section heading |
| Leaving the `Original:` link without `#page=` | One link that does not jump | Anchor it like every other citation |
| Using a `#Heading` anchor | Silently does not jump in Obsidian | Section title goes in the label |
| Guessing the paper's year from the filename | Wrong year in the filename | Read page 1 |
| Editing the source note's body to fix wording | Breaks the immutability boundary | Summarise in the review |
| Paraphrasing the abstract | No review value in this field | Read methods, results and limitations |
| Citing a number the paper never printed | Fabricated evidence | Leave it out |
| Filling `due:` with a plausible date | Fabricated deadline | Leave it blank |
| Adding or renaming a heading | Fails the template contract | Keep the eight, in order |
