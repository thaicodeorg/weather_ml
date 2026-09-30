---
name: extracting-pdfs-with-markitdown
description: Use when converting a PDF to Markdown with markitdown, or when extracted PDF text has lost its spaces between words, contains fused run-on tokens such as "Machinelearning-basedweatherforecastingmodels", raises UnicodeEncodeError on ligature characters like U+FB01, or when deciding whether to tune pdfplumber x_tolerance or pdfminer word_margin.
---

# Extracting PDFs with markitdown

## Overview

markitdown's PDF output is only as good as the text layer it hands to pdfplumber,
and on LaTeX and publisher PDFs its defaults fuse every pair of adjacent words.
The one-line cause is that word boundaries in these files are x-position gaps of
roughly 2 pt, while pdfplumber's default `x_tolerance` of 3 pt is wider than that
gap, so pdfplumber decides the words are one token.

Lowering `x_tolerance` to 2 or below fixes it. No post-processing is needed.

## When to Use

- Converting a PDF to Markdown with markitdown or pdfplumber
- Output has no spaces between words, or long nonsense tokens
- Choosing between `x_tolerance` and `word_margin`
- `UnicodeEncodeError: 'charmap' codec can't encode character` during extraction

Not for: image-only PDFs with no text layer (these need OCR), or DOCX/HTML input,
where markitdown's converters are already sound.

## The one knob that matters

| Lever | Default | Correct value | Effect of raising it |
|---|---|---|---|
| pdfplumber `x_tolerance` | 3 (hardcoded) | **2 or lower** | Merges words, destroys spacing |
| pdfminer `word_margin` | 0.1 | **leave at 0.1** | Also destroys spacing |

**The two knobs move in opposite directions, and only one of them is wrong.**
pdfplumber fuses words when `x_tolerance` is too *high*, so it must come down.
pdfminer's `word_margin` default of 0.1 is already correct for these files, and
*raising* it is what destroys the spacing.

`word_margin` is a **relative multiplier on the gap that must be crossed to emit a
space**, so raising it merges words. Measured on
`2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf`:

| `word_margin` | fused % | mean word length |
|---|---|---|
| 0.1 (default) | 0.43% | 5.42 |
| 0.2 | 0.43% | 5.43 |
| 0.3 | 15.71% | 6.22 |
| 0.5 | 91.05% | 28.76 |

At 0.5 the merged mega-token overflows its line box and the layout engine degrades
to roughly one character per line. Tuning pdfminer "to be safer" is the single most
common wrong fix, and it produces the exact disease it claims to fix.

markitdown hardcodes `x_tolerance=3` in several places and exposes no argument for
it, so the fix has to go through pdfplumber directly.

```python
import pdfplumber

with pdfplumber.open(path) as pdf:
    for page in pdf.pages:
        try:
            print(page.extract_text(x_tolerance=1.5))
        finally:
            page.close()
```

`page.close()` matters: pdfplumber otherwise retains every page's parsed objects
for the life of the document, and a 25 MB paper will hold a great deal of memory.

## Traps

**The console script is often not on PATH.** `markitdown file.pdf` fails with
`CommandNotFoundException` even when the module imports. Use `python -m markitdown`.

**A vendored markitdown may not match upstream.** The installed 0.1.7 here probes
each page with `_extract_form_content_from_words` and only falls back to pdfminer
when *zero* pages look like a form. That detector misfires on ordinary prose and
figure pages, so a whole document gets forced down the pdfplumber branch and
markitdown's clean pdfminer fallback is never reached. Read
`markitdown/converters/_pdf_converter.py` before assuming upstream behavior.

**The Windows console is cp1252.** Typographic ligatures (U+FB01) and similar
raise `UnicodeEncodeError` on `print`. Write files as UTF-8 and reconfigure stdout
before printing extracted text.

**Some odd characters are the PDF's fault, not the tool's.** A missing accent
rendering as `Boualle`gue` comes from the font's glyph mapping and is reproduced
identically by pdfplumber and pdfminer alike. Do not chase it in the converter.

**Two-column pages interleave.** Text is emitted left-column-line, right-column-line,
alternately, so paragraphs are unreadable. No tolerance setting fixes this; it needs
per-page column cropping, which is a separate piece of work.

## Verify before trusting the output

Fused words are obvious in a short sample, so check the first screenful of real
output rather than trusting that the command exited 0:

- Prose should read as ordinary sentences, not `wordwordword`
- Share of alphabetic characters sitting in tokens of 18+ letters is the cheapest
  numeric check. Measured on two of the three papers in `Sources/Research Paper/`:

  | PDF | markitdown default | `x_tolerance=1.5` |
  |---|---|---|
  | `2406.01465v2-AIFS-...` | 44.7% | 0.9% |
  | `2509.18994v1-update_to_...` | 28.6% | 1.5% |

  A couple of percent is normal — hyphenated words and URLs make legitimate long
  tokens. Above roughly 5% the spacing is still fused.
- Figure regions can emit reversed character-order garbage even when body prose is
  clean, so spot-check a page containing a chart

## This vault

The corpus is `Sources/Research Paper/**/*.pdf`, recursive — publisher subfolders
(`arxiv.org/`, `IEEE/`, `ScienceDirect/`, `SpringerNature/`, `mdpi.com/`,
`Nature.com/`, `icic/`, `ametsoc.org/`, `Wiley/`, `AAAS/`, `Grenze/`) hold all of it. Converted notes go to
`Sources/Markdown/<subfolder>/<stem>.md`, mirroring the PDF tree, and carry the
frontmatter `Templates/Source.md` requires.

There is no converter script in this vault. Earlier versions of these skills
referenced `Files/tools/pdf_to_markdown.py` and `Files/tools/validate_notes.py`;
those files do not exist. Extract inline with pdfplumber at `x_tolerance` 2 or
below, then check the output by hand. Two-column layouts, which several
ScienceDirect and IEEE papers use, need per-page column cropping — that work is
still outstanding, so say so rather than shipping interleaved text as a source
note.

## Common Mistakes

| Mistake | Result | Instead |
|---|---|---|
| Raising pdfminer `word_margin` to 0.3/0.5 | Spacing destroyed | Leave at 0.1 |
| Trusting exit code 0 | Glued words committed silently | Read the first 30 lines |
| `print`ing ligature text on Windows | `UnicodeEncodeError` | Write UTF-8, reconfigure stdout |
| Trusting the PDF's accents | Endless tuning | Bad font mapping, not the converter |
| Editing the extracted body | Breaks the immutability boundary | Summarise in a separate note |
