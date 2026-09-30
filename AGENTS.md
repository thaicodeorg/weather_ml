# AGENTS.md

This is an Obsidian **second brain** for machine-learning weather-forecast research,
built around a strict "immutable source → review" pipeline. It is the working memory
for the owner's KMUTNB graduate seminar and for the ML weather-forecasting field
(AIFS, FastNet, GraphCast, Pangu-Weather, FuXi, AIFS-CRPS, physics-informed models,
ensemble verification). Other people and AI agents are expected to keep working in
it, so **follow the conventions below exactly; they are usually not obvious from a
file's content alone.**

## Hard rules (do not break)

1. **Sources are immutable.** Never edit the body of a note under `Sources/`. It is
   a verbatim record of a PDF, URL, report, or YouTube transcript. Corrections,
   disagreements, and summaries belong in a *literature* or *permanent* note that
   cites the source.
2. **The KMUTNB review format is a contract.** The title heading plus the **eight**
   section headings exist in a fixed order from `Templates/Review Kmutnb.md`. Keep
   them, keep the order, never rename or add headings. The 8 sections are:
   `Source Information`, `Research Objective`, `Problem`, `Gap Addressed in paper`,
   `Findings and conclusion`, `Limitations or Weakness`,
   `Implication or suggestions on future research`, `How your search can fill gap`.
3. **Never invent** numbers, baselines, citations, section titles, dates, or
   deadlines. If the paper does not say it, the review does not say it.
4. **Do not flatten `Sources/`.** Both `Sources/Research Paper/` and
   `Sources/Markdown/` mirror publisher subfolders (`arxiv.org/`, `IEEE/`,
   `ScienceDirect/`, `SpringerNature/`, `mdpi.com/`, `Nature.com/`, `icic/`,
   `ametsoc.org/`, `Wiley/`, `AAAS/`, `Grenze/`). A note mirrors its PDF's
   subfolder. Duplicate-file collisions are resolved by citing the shallower copy.

## Project purpose

The owner studies **data-driven weather prediction**: how ML models (AIFS,
AIFS-CRPS, FastNet, Pangu-Weather, GraphCast, FuXi, blending typologies,
physics-informed NNs) compare with physics-based NWP, where they win, and what gaps
remain. Reviews exist to feed the seminar and future research questions. Assume a
reader who knows NWP, RMSE, ACC, ensemble spread, Brier/CRPS, and the major ML
weather models — a review that paraphrases the abstract has failed.

## Directory map

```
Weather_ML/
├── AGENTS.md                ← this file; read me first
├── opencode.json            ← registers skills/ for the opencode loader
├── <date>.md                ← daily scratch notes (e.g. 2026-09-30.md)
├── 09292026 google scholar.md
├── Sources/                 ← IMMUTABLE. the evidence boundary
│   ├── Research Paper/      ← the PDF corpus (~78 PDFs, multi-device, git-synced)
│   │   └── <publisher>/     ← arxiv.org, IEEE, ScienceDirect, SpringerNature,
│   │                          mdpi.com, Nature.com, icic, ametsoc.org, Wiley,
│   │                          AAAS, Grenze
│   ├── Markdown/            ← converted text-layer notes, mirrors the PDF tree
│   │   └── <publisher>/<stem>.md
│   ├── URL/                 ← clipped web pages (Hugging Face paper pages, etc.)
│   ├── Youtube/             ← video transcripts; WeatherModels/ + Bangkok2026/ +
│   │                          Thai-named root files
│   └── Report Paper/        ← report-type PDFs (Microsoft Turing/AI-WMO, etc.)
├── Literatures Notes/
│   └── Reviews Kmutnb/      ← the 8-heading seminar reviews
├── Fleeting Notes/          ← fast capture; subfolders abstract_Index, AI-Search,
│                          Chat, NotebookLM/atomic notes, Research Question
├── Permanent Notes/         ← atomic one-claim notes; index.md is the MOC
├── Templates/               ← Source, Literature Note, Review Kmutnb,
│                          Permanent Note, Fleeting Note, Abstract Reviews
├── Files/images/            ← Obsidian attachments
├── Docs/                    ← non-vault documents (training PDFs, SLR template)
├── AI/                      ← AI-planning artifacts + archify diagram outputs
│   ├── index.md
│   ├── AI research/         ← scaffold plans, lineage diagrams (aifs-lineage.*)
│   └── logs/
├── skills/                  ← vendored agent skills (18 total, multi-device)
│   ├── review-kmutnb/       ← THE review workflow
│   ├── extracting-pdfs-with-markitdown/   ← PDF extraction + tuning
│   ├── brainstorming/, writing-plans/, executing-plans/, ... (superpowers set)
│   └── archify/, archify-review/
└── .obsidian/               ← Obsidian config/plugins (gitignored mostly)
```

## Note types and frontmatter

Every note starts from a template in `Templates/`. `type` + `status` + `confidence`
are the vault's life-cycle system; keep them consistent or the graph breaks.

| type | template | purpose | status values |
|---|---|---|---|
| `source` | `Source.md` | verbatim record of a document; the only place evidence is captured | `seed` (vs `draft`, both mean not fully checked) |
| `literature` | `Literature Note.md` | your paraphrase of one source: Summary, Findings, Limitations, Gaps, Questions Raised | `seed` → `draft` |
| `review` | `Review Kmutnb.md` | the 8-heading seminar review, citing the PDF directly | `seed` |
| `permanent` | `Permanent Note.md` | one atomic claim: Claim, Evidence (links immutable sources), Related | `seed` → `evergreen` (only `evergreen` makes a claim linkable from an index, and only with `sources` filled) |
| `fleeting` | `Fleeting Note.md` | unstructured capture; `promoted: false` until it becomes something else | `seed` |

Status lifecycle: `seed` → `draft` → `evergreen`. Confidence: `low` → `medium` →
`high`; `high` means verified against something in `Sources/`. Most notes sit at
`seed`/`low` — that is correct, not a bug. Do not promote on speculation.

## The review workflow (the vault's main job)

The `review-kmutnb` skill is the source of truth for this. Summary:

1. **Resolve** the PDF against `Sources/Research Paper/**/*.pdf` recursively. The
   request will usually misspell paths or drop a publisher subfolder — use the real
   tree. Never convert a paper from `Report Paper/`.
2. **Check for existing work.** Mirrored note in `Sources/Markdown/` exists → skip
   extraction. A review already in `Literatures Notes/Reviews Kmutnb/` → report it,
   stop, do not duplicate.
3. **Extract** only if no note exists, via the `extracting-pdfs-with-markitdown`
   skill: pdfplumber `x_tolerance` ≤ 2, write UTF-8, handle two-column pages, verify
   real output (don't trust `exit 0`).
4. **Write the source note** at the mirrored `Sources/Markdown/<subfolder>/` path
   with `Templates/Source.md` frontmatter: `type: source`, `source_type: pdf`,
   `origin: <vault-relative PDF path>` (a plain path, NEVER a wiki-link),
   `immutable: true`. Body below is verbatim.
5. **Read** the note: title, authors, year (from page 1, not the filename), section
   numbers, folios.
6. **Write the review** to `Literatures Notes/Reviews Kmutnb/`:
   `<Paper title> (<Surname> et al. <Year>).md` — title verbatim from page 1.
   Frontmatter: `type: review`, `status: seed`, `course: Kmutnb seminar`,
   `due:` **left blank unless the user gave a deadline**, `confidence: medium`
   (you read it), `sources: ["[[Sources/Markdown/<subfolder>/<stem>]]"]`.
7. **Verify.** Every `[[...]]` resolves; every `#page=` is within the sheet count;
   section numbers exist; every heading matches the template.

### Citation format (critical, frequently wrong)

```text
[[Sources/Research Paper/<subfolder>/<file>.pdf#page=<sheet>|<Section no.> <Section title>, p.<folio>]]
```

Two numbers, one section title, each verified independently:

- `#page=` = **physical 1-based sheet** (what the PDF pager opens).
- `p.` = **printed folio** on that sheet (the page number printed in the PDF).
- Label = the paper's own section number + heading, copied verbatim (`5.2 Fine-tuning horizon, p.12`; add `, Fig. N` for figure claims).

arXiv cover sheets and front matter are numbered differently, so sheet ≠ folio.
Read the printed folio before citing; carrying one number across both fields is the
most common quiet error. Put the section title in the **label**, not an Obsidian
`#heading` anchor — `#Some Heading` anchors silently fail on PDFs; `#page=` lands.

## Environment, tools, and how to work here

- **Shell:** Windows PowerShell 5.1. `&&` is unsupported — chain with `;` or
  `if ($?) { ... }`. Use `&` to call executables whose paths contain spaces.
- **Terminal usage:** prefer the dedicated file tools (Read/Edit/Grep/Glob) for
  file work over PowerShell `Get-Content`/`Set-Content`.
- **PDF extraction:** `pdfplumber` (installed). `x_tolerance=3` is the hardcoded
  default and fuses word spacing on LaTeX/publisher PDFs; use `2` or below.
  `page.close()` after each page to bound memory. Do **not** raise pdfminer
  `word_margin` (0.1 is correct); raising it destroys spacing.
- **Console encoding:** Windows console is cp1252; `print`ing ligatures (U+FB01)
  raises `UnicodeEncodeError`. Write UTF-8 files and reconfigure stdout.
- **Two-column PDFs** (multiple ScienceDirect/IEEE papers) interleave columns;
  per-page column cropping is outstanding work — say so rather than shipping
  interleaved text as a source note.
- **No converter scripts.** `Files/tools/pdf_to_markdown.py` and
  `validate_notes.py` do NOT exist (earlier skill versions referenced them).
- **opencode skills** load from `skills/` via `opencode.json`
  (`"skills": { "paths": ["skills"] }`). The vault's own conventions live in the
  `review-kmutnb` and `extracting-pdfs-with-markitdown` skills — read them before
  doing a review or an extraction.

## Domain notes (who the actors are)

- **ECMWF**: AIFS, AIFS-CRPS (proper-scoring-rule ensemble training; almost-fair
  CRPS), IFS (physics-based reference), AIFS updates, FastNet, ERA5 reanalysis.
- **Other models**: Pangu-Weather, GraphCast, FourCastNet, FuXi (15-day cascade),
  Aurora, and the physics-vs-AI comparison literature (Davis GRL 2026, Zhang
  Science Advances 2026, Blunn Met Apps 2024, Waqas & Kim PINN review, Shipway
  blending typology, Bodnar foundation-model review).
- Verifying an ML model means scoring against a stated baseline with a common
  reference, and watching for: skill-score choice, deterministic vs probabilistic
  training, blurring with lead time, resolution/compute trade-offs, confounds.

## Git and multi-device

- Repo contains the text layer (notes, templates, PDFs, config). PDFs are
  versioned/kept in sync across devices (Obsidian Sync / git); do not treat local
  filenames as guaranteed-identical across machines — always resolve paths against
  the current tree first.
- Commit only what you were asked to commit. Write concise messages matching the
  repo's style. Never commit secrets.
- After editing `opencode.json` or a skill, tell the user to **restart opencode**
  (config is loaded once at startup).

## Common mistakes to avoid

| Mistake | Result | Instead |
|---|---|---|
| Trusting the request's paths | Notes land in new misspelled folders | Use the real tree / path table |
| Flattening `Sources/Markdown/` | subfolder identity lost, stem collisions | mirror the PDF subfolder |
| Searching only the PDF root | subfoldered papers look missing | search `**/*.pdf` recursively |
| One assumption for `#page=`, `p.`, section | silent off-by-one citations | read the printed folio + heading |
| Editing a source-note body | breaks the immutability boundary | summarise in literature/review note |
| Paraphrasing the abstract | no review value | read methods, results, limitations |
| Citing a number the paper never printed | fabricated evidence | leave it out |
| Filling `due:` with a plausible date | fabricated deadline | leave blank |
| Renaming/adding review headings | fails the template contract | keep the eight, in order |
| `print`ing ligature text on Windows | `UnicodeEncodeError` | write UTF-8, reconfigure stdout |
| `&&` chaining in PowerShell | parse errors | `;` or `if ($?) { ... }` |

## First steps for anyone new here

1. Read `skills/review-kmutnb/SKILL.md` and `skills/extracting-pdfs-with-markitdown/SKILL.md`.
2. Look at one completed review (`FuXi ... (Chen et al. 2023).md`) alongside its
   source note (`Sources/Markdown/Nature.com/s41612 023 00512 1 ... .md`).
3. Read all six templates in `Templates/`.
4. Before any review: locate the PDF, check `Sources/Markdown/` for an existing
   note, then follow the eight-step workflow above.