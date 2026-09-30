---
type: plan
created: 2026-09-26
tags:
  - meta
  - vault-design
---

# Second Brain Scaffold Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build the conventions layer for the `ECMWF_ML` Obsidian vault — a typed frontmatter contract, seven templates, per-section navigation, a persistent `AGENTS.md` operating contract, and a demonstrated logging convention.

**Architecture:** A Python validator (`Files/tools/validate_notes.py`) is the enforcement mechanism, not documentation. It parses every note's YAML frontmatter, asserts required keys and enum membership per note type, and resolves every wiki-link against the filesystem. Everything else in this plan is validated by running it. Obsidian's own `app.json` settings (`useMarkdownLinks: false`, `newLinkFormat: "absolute"`) make the app emit conforming links, so the rule is enforced at authoring time too.

**Tech Stack:** Markdown + YAML frontmatter, Obsidian core plugins (`properties`, `bases`, `templates`, `graph`, `backlink`), Python 3.14 with PyYAML 6.0.3 for validation, `unittest` from the standard library for the validator's own tests, git for versioning.

**Spec:** `AI/AI research/2026-09-26-second-brain-scaffold-design.md` — the plan argues from the spec, so the spec travels with it; executors read both.

## Global Constraints

These apply to every task. They are copied verbatim from the spec.

- Wiki-links only, always full-path from the vault root: `[[Permanent Notes/foo]]`. Never relative markdown links.
- Six files share the basename `index.md`. A bare `[[index]]` is permitted **only** in a file inside the same folder as its target. Everywhere else, use the full path plus an alias: `[[Permanent Notes/index|Concept Map]]`.
- `Sources/**` is immutable. Never edit a source file. Corrections and critique go in a literature note.
- `confidence` is required on any note that makes a claim.
- A permanent note promoted to `status: evergreen` must carry at least one entry in `sources`. A `seed` note may be unsourced; an unsourced assertion that reaches `evergreen` is a defect.
- `status` is one of `seed`, `draft`, `evergreen`, `archived`. `confidence` is one of `high`, `medium`, `low`.
- `confidence: high` requires verification against an immutable source in `Sources/` or peer-reviewed literature.
- A note with `confidence: low` may not be promoted to `status: evergreen` while a MOC depends on its claim.
- New MOCs and indexes must not link to notes that do not exist yet. Unbuilt sections are described in prose under **Gaps**, not as links. This keeps the validator green.
- File naming: lowercase-hyphenated slugs for permanent and fleeting notes. Source filenames stay as-is; they carry provenance.
- PDFs are gitignored. Do not commit them.
- Windows. Shell is PowerShell 5.1. No `&&` chaining — use `;` or `if ($?) { }`.

---

## File Structure

**Created:**

| Path | Responsibility |
|---|---|
| `Files/tools/validate_notes.py` | Validates frontmatter schema and wiki-link resolution across the vault |
| `Files/tools/test_validate_notes.py` | Unit tests for the validator itself |
| `AGENTS.md` | Persistent operating contract for future agent sessions |
| `Templates/Permanent Note.md` | Template: one atomic claim plus evidence |
| `Templates/Literature Note.md` | Template: one source summarised and evaluated |
| `Templates/Review Kmutnb.md` | Template: academic review assignment (replaces `Review Kmutnb templates.md`) |
| `Templates/Source.md` | Template: metadata header for an immutable source dump |
| `Templates/Fleeting Note.md` | Template: raw unprocessed capture |
| `Templates/AI Research.md` | Template: research report |
| `Templates/AI Log.md` | Template: per-task execution log |
| `index.md` | Root hub linking every section MOC |
| `log.md` | Append-only chronological task log, newest first |
| `Sources/index.md` | Source catalogue |
| `Literatures Notes/index.md` | Source → literature note map |
| `Permanent Notes/index.md` | Concept map |
| `Fleeting Notes/index.md` | Triage inbox |
| `AI/AI research/index.md` | Research output index |
| `AI/logs/2026-09-26-<HHmm>-second-brain-scaffold.md` | This task's own execution log |

**Modified:**

| Path | Change |
|---|---|
| `.obsidian/app.json` | Add five settings enforcing wiki-links and template folder |
| `.gitignore` | Already written and committed; verify it still holds |

**Deleted:**

| Path | Reason |
|---|---|
| `Permanets Notes/` | Renamed to `Permanent Notes/` (typo fix; folder is empty) |
| `Templates/Review Kmutnb templates.md` | Replaced by `Templates/Review Kmutnb.md` |
| `Templates/Paper page - AIFS-CRPS Ensemble forecasting...md` | **Gated on user confirmation** — see Task 7 |

---

### Task 1: Vault Validator

The validator is the enforcement mechanism for every other task. It ships first so each subsequent task has something to be green against.

**Files:**
- Create: `Files/tools/test_validate_notes.py`
- Create: `Files/tools/validate_notes.py`

**Interfaces:**
- Consumes: nothing (first task)
- Produces:
  - `parse_frontmatter(text: str) -> tuple[dict | None, str | None]` — returns `(data, None)` on success, `(None, error_message)` when frontmatter is absent or unparseable.
  - `resolve_link(target: str, known_stems: dict[str, list[str]], vault_root: Path) -> str | None` — returns the resolved vault-relative path as a string, or `None` if unresolvable. Strips `|alias` and `#heading` before resolving.
  - `build_stem_index(vault_root: Path) -> dict[str, list[str]]` — maps each markdown file's stem to its full vault-relative paths.
  - `strip_code(text: str) -> str` — removes fenced code blocks and inline code spans, mirroring Obsidian's behaviour of not creating links inside code.
  - `REQUIRED_KEYS: dict[str, set[str]]` — per-`type` required frontmatter keys.
  - `ENUMS: dict[str, set[str]]` — per-key allowed values.
  - `validate(vault_root: Path) -> list[str]` — returns a list of human-readable error strings; empty means clean.
  - `main() -> int` — CLI entry; prints errors, returns 0 when clean, 1 when not.

- [ ] **Step 1: Write the failing tests**

Create `Files/tools/test_validate_notes.py`:

```python
import sys
import unittest
from pathlib import Path

sys.path.insert(0, str(Path(__file__).parent))

import validate_notes as vn


class TestParseFrontmatter(unittest.TestCase):
    def test_parses_valid_yaml(self):
        text = "---\ntype: permanent\nconfidence: low\n---\n\n# Body\n"
        data, err = vn.parse_frontmatter(text)
        self.assertIsNone(err)
        self.assertEqual(data["type"], "permanent")
        self.assertEqual(data["confidence"], "low")

    def test_missing_frontmatter_returns_error(self):
        data, err = vn.parse_frontmatter("# No frontmatter\n")
        self.assertIsNone(data)
        self.assertIsNotNone(err)

    def test_unparseable_yaml_returns_error(self):
        text = "---\ntype: [unclosed\n---\n"
        data, err = vn.parse_frontmatter(text)
        self.assertIsNone(data)
        self.assertIn("YAML", err)

    def test_empty_frontmatter_returns_error(self):
        data, err = vn.parse_frontmatter("---\n---\n")
        self.assertIsNone(data)
        self.assertIsNotNone(err)

    def test_placeholders_do_not_break_parsing(self):
        # `created: {{date}}` is valid YAML only as a nested mapping. Substituting
        # placeholders keeps template files parseable and the value a plain string.
        text = "---\ntype: permanent\ncreated: {{date}}\n---\n"
        data, err = vn.parse_frontmatter(text)
        self.assertIsNone(err)
        self.assertEqual(data["type"], "permanent")
        self.assertIsInstance(data["created"], str)


class TestStripCode(unittest.TestCase):
    def test_removes_fenced_blocks(self):
        # Built from parts so this source contains no literal fence, which would
        # terminate the enclosing markdown code block in the plan document.
        fence = "`" * 3
        text = "Real [[keep]]\n{}\n[[drop]]\n{}\n".format(fence, fence)
        self.assertEqual(vn.LINK_RE.findall(vn.strip_code(text)), ["keep"])

    def test_removes_inline_code_spans(self):
        text = "Real [[keep]] and illustrative `[[drop]]` here\n"
        self.assertEqual(vn.LINK_RE.findall(vn.strip_code(text)), ["keep"])


class TestResolveLink(unittest.TestCase):
    # A root containing no real files, so resolution exercises the stem index rather
    # than filesystem existence. Keeps these tests independent of the working directory.
    ROOT = Path("__no_such_vault_root__")

    def setUp(self):
        self.stems = {
            "foo": ["Permanent Notes/foo.md"],
            "index": ["index.md", "Permanent Notes/index.md"],
        }

    def test_resolves_full_path(self):
        self.assertEqual(
            vn.resolve_link("Permanent Notes/foo", self.stems, self.ROOT),
            "Permanent Notes/foo.md",
        )

    def test_strips_alias(self):
        self.assertEqual(
            vn.resolve_link("Permanent Notes/foo|Alias Text", self.stems, self.ROOT),
            "Permanent Notes/foo.md",
        )

    def test_strips_heading(self):
        self.assertEqual(
            vn.resolve_link("Permanent Notes/foo#Evidence", self.stems, self.ROOT),
            "Permanent Notes/foo.md",
        )

    def test_strips_block_ref(self):
        self.assertEqual(
            vn.resolve_link("Permanent Notes/foo#^abc123", self.stems, self.ROOT),
            "Permanent Notes/foo.md",
        )

    def test_returns_none_when_missing(self):
        self.assertIsNone(vn.resolve_link("Nope/nothing", self.stems, self.ROOT))

    def test_ambiguous_bare_stem_returns_none(self):
        # Six files are named index.md. A bare `index` with no filesystem hit is
        # ambiguous and must not silently resolve to an arbitrary one.
        self.assertIsNone(vn.resolve_link("index", self.stems, self.ROOT))

    def test_existing_file_beats_stem_index(self):
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "index.md").write_text("x", encoding="utf-8")
            self.assertEqual(vn.resolve_link("index", self.stems, root), "index.md")


class TestStemIndex(unittest.TestCase):
    def test_maps_stem_to_paths(self):
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "Permanent Notes").mkdir()
            (root / "Permanent Notes" / "alpha.md").write_text("x", encoding="utf-8")
            (root / "beta.md").write_text("x", encoding="utf-8")
            idx = vn.build_stem_index(root)
            self.assertEqual(idx["alpha"], ["Permanent Notes/alpha.md"])
            self.assertEqual(idx["beta"], ["beta.md"])


class TestValidate(unittest.TestCase):
    def test_reports_missing_required_key(self):
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "n.md").write_text(
                "---\ntype: permanent\ncreated: 2026-09-26\n---\n", encoding="utf-8"
            )
            errs = vn.validate(root)
            self.assertTrue(any("confidence" in e for e in errs))

    def test_reports_bad_enum(self):
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "n.md").write_text(
                "---\ntype: permanent\ncreated: 2026-09-26\ntags: []\nstatus: nope\n"
                "confidence: low\nsources: []\n---\n",
                encoding="utf-8",
            )
            errs = vn.validate(root)
            self.assertTrue(any("status" in e for e in errs))

    def test_seed_permanent_note_may_be_unsourced(self):
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "n.md").write_text(
                "---\ntype: permanent\ncreated: 2026-09-26\ntags: []\nstatus: seed\n"
                "confidence: low\nsources: []\n---\n\nBody\n",
                encoding="utf-8",
            )
            self.assertEqual(vn.validate(root), [])

    def test_evergreen_permanent_note_requires_sources(self):
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "n.md").write_text(
                "---\ntype: permanent\ncreated: 2026-09-26\ntags: []\nstatus: evergreen\n"
                "confidence: high\nsources: []\n---\n\nBody\n",
                encoding="utf-8",
            )
            errs = vn.validate(root)
            self.assertTrue(any("sources" in e for e in errs))

    def test_ignores_non_managed_types(self):
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "n.md").write_text("---\ntype: clipping\n---\nBody\n", encoding="utf-8")
            self.assertEqual(vn.validate(root), [])

    def test_skips_tooling_directories(self):
        # The SDD harness workspace lives at <vault>/.superpowers/sdd/<plan>/ because
        # .git/ is a protected path for agent writes. Those are process ledgers, briefs
        # and reports, not notes, so the validator must not report them as vault defects.
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            harness = root / ".superpowers" / "sdd" / "plan"
            harness.mkdir(parents=True)
            (harness / "progress.md").write_text("# Ledger\n", encoding="utf-8")
            self.assertEqual(vn.validate(root), [])

    def test_source_note_must_declare_immutable_true(self):
        # Sources/** is the vault's immutability boundary, so a source note must
        # affirm it. Asserted against the whole error list so an unrelated error
        # cannot satisfy this test.
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "n.md").write_text(
                "---\ntype: source\ncreated: 2026-09-26\ntags: []\nstatus: seed\n"
                "source_type: pdf\norigin: o\nauthor: a\npublished: 2026-01-01\n"
                "retrieved: 2026-09-26\nimmutable: false\n---\n\nBody\n",
                encoding="utf-8",
            )
            self.assertEqual(
                vn.validate(root),
                ["n.md: source note must declare immutable: true "
                 "(Sources/** is immutable)"],
            )

    def test_source_note_with_immutable_true_is_valid(self):
        # The counterpart to the test above. `immutable: true` is a YAML boolean, so
        # this must never be expressed as an ENUMS membership test: ENUMS holds
        # strings, and `True in {"true", "false"}` is always False, which would
        # reject every valid source note.
        import tempfile
        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "n.md").write_text(
                "---\ntype: source\ncreated: 2026-09-26\ntags: []\nstatus: seed\n"
                "source_type: pdf\norigin: o\nauthor: a\npublished: 2026-01-01\n"
                "retrieved: 2026-09-26\nimmutable: true\n---\n\nBody\n",
                encoding="utf-8",
            )
            self.assertEqual(vn.validate(root), [])


if __name__ == "__main__":
    unittest.main()
```

Test count: 5 in `TestParseFrontmatter`, 2 in `TestStripCode`, 7 in `TestResolveLink`,
1 in `TestStemIndex`, 8 in `TestValidate` — **23 total**.

- [ ] **Step 2: Run the tests to confirm they fail**

Run: `python -m unittest discover -s "Files/tools" -p "test_*.py" -v`

Expected: FAIL with `ModuleNotFoundError: No module named 'validate_notes'`

- [ ] **Step 3: Write the implementation**

Create `Files/tools/validate_notes.py`:

```python
"""Validate Obsidian vault frontmatter and wiki-link resolution.

Run:  python Files/tools/validate_notes.py
Exit: 0 clean, 1 on any error.
"""

import re
import sys
from pathlib import Path

import yaml

SKIP_DIRS = {".obsidian", ".git", ".trash", "node_modules", ".superpowers"}
LINK_RE = re.compile(r"\[\[([^\]\[]+)\]\]")
PLACEHOLDER_RE = re.compile(r"\{\{[^}]*\}\}")
# Built from parts so this source contains no literal fence, which would terminate
# the enclosing markdown code block wherever this file is quoted.
FENCE = "`" * 3
FENCE_RE = re.compile(r"^" + FENCE + r".*?^" + FENCE, re.DOTALL | re.MULTILINE)
CODE_SPAN_RE = re.compile(r"`[^`\n]*`")

REQUIRED_KEYS = {
    "permanent": {"type", "created", "tags", "status", "confidence", "sources"},
    "literature": {"type", "created", "tags", "status", "title", "source",
                   "authors", "year", "venue", "confidence"},
    "review": {"type", "created", "tags", "status", "course", "due", "confidence"},
    "source": {"type", "created", "tags", "status", "source_type", "origin",
               "author", "published", "retrieved", "immutable"},
    "fleeting": {"type", "created", "tags", "status", "promoted"},
    "research": {"type", "created", "tags", "status", "question", "method",
                 "confidence", "sources"},
    "log": {"type", "created", "tags", "status", "timestamp", "skills",
            "confidence", "files_touched"},
}

ENUMS = {
    "type": set(REQUIRED_KEYS),
    "status": {"seed", "draft", "evergreen", "archived"},
    "confidence": {"high", "medium", "low"},
    "source_type": {"pdf", "url", "youtube", "report"},
}


def parse_frontmatter(text):
    """Return (data, None) on success, (None, error) on failure."""
    if not text.startswith("---"):
        return None, "missing frontmatter delimiters"
    parts = text.split("---", 2)
    if len(parts) < 3:
        return None, "unterminated frontmatter block"
    try:
        data = yaml.safe_load(PLACEHOLDER_RE.sub("placeholder", parts[1]))
    except yaml.YAMLError as exc:
        return None, "YAML parse error: {}".format(exc)
    if not isinstance(data, dict):
        return None, "frontmatter is not a YAML mapping"
    return data, None


def build_stem_index(vault_root):
    """Map each markdown stem to its vault-relative paths (posix separators)."""
    index = {}
    for path in vault_root.rglob("*.md"):
        if SKIP_DIRS & set(path.relative_to(vault_root).parts):
            continue
        rel = path.relative_to(vault_root).as_posix()
        index.setdefault(path.stem, []).append(rel)
    return index


def strip_code(text):
    """Remove fenced blocks and inline code spans.

    Obsidian does not create links inside code, so `[[example]]` shown in backticks
    is documentation, not a link. Mirroring that keeps design docs from failing the
    very validator they describe.
    """
    return CODE_SPAN_RE.sub("", FENCE_RE.sub("", text))


def resolve_link(target, known_stems, vault_root):
    """Resolve a raw wiki-link target to a vault-relative path, or None."""
    target = target.split("|", 1)[0]
    target = target.split("#", 1)[0].strip()
    if not target:
        return None
    if (vault_root / (target + ".md")).is_file():
        return target + ".md"
    if (vault_root / target).is_file():
        return target
    stem = target.rsplit("/", 1)[-1]
    candidates = known_stems.get(stem, [])
    if len(candidates) == 1:
        return candidates[0]
    return None


def validate(vault_root):
    """Return a list of error strings. Empty list means the vault is clean."""
    errors = []
    stems = build_stem_index(vault_root)

    for path in sorted(vault_root.rglob("*.md")):
        rel = path.relative_to(vault_root)
        if SKIP_DIRS & set(rel.parts):
            continue
        rel_posix = rel.as_posix()
        text = path.read_text(encoding="utf-8")

        data, err = parse_frontmatter(text)
        if data is None:
            errors.append("{}: {}".format(rel_posix, err))
            continue

        note_type = data.get("type")
        if note_type in REQUIRED_KEYS:
            missing = REQUIRED_KEYS[note_type] - set(data)
            if missing:
                errors.append(
                    "{}: type '{}' missing keys: {}".format(
                        rel_posix, note_type, ", ".join(sorted(missing))
                    )
                )
            for key, allowed in ENUMS.items():
                if key in data and data[key] not in allowed:
                    errors.append(
                        "{}: {} = {!r} not in {}".format(
                            rel_posix, key, data[key], sorted(allowed)
                        )
                    )
            if (note_type == "permanent"
                    and data.get("status") == "evergreen"
                    and not data.get("sources")):
                errors.append(
                    "{}: evergreen permanent note has no sources "
                    "(unsourced assertion)".format(rel_posix)
                )
            # Sources/** is the vault's immutability boundary, so a source note has to
            # affirm it. This is a boolean identity check, never an ENUMS entry: ENUMS
            # holds strings and YAML parses `immutable: true` to True, so
            # `True in {"true", "false"}` would reject every valid source note.
            # REQUIRED_KEYS already reports an absent key, so only the value is checked.
            if (note_type == "source"
                    and "immutable" in data
                    and data["immutable"] is not True):
                errors.append(
                    "{}: source note must declare immutable: true "
                    "(Sources/** is immutable)".format(rel_posix)
                )

        for raw in LINK_RE.findall(strip_code(text)):
            if resolve_link(raw, stems, vault_root) is None:
                errors.append("{}: unresolved link [[{}]]".format(rel_posix, raw))

    return errors


def main():
    vault_root = Path(__file__).resolve().parents[2]
    errors = validate(vault_root)
    if errors:
        for e in errors:
            print("FAIL " + e)
        print("\n{} error(s).".format(len(errors)))
        return 1
    print("OK - vault clean.")
    return 0


if __name__ == "__main__":
    sys.exit(main())
```

- [ ] **Step 4: Run the tests to confirm they pass**

Run: `python -m unittest discover -s "Files/tools" -p "test_*.py" -v`

Expected: PASS, 23 tests, `OK`

- [ ] **Step 5: Run the validator against the real vault**

Run: `python Files/tools/validate_notes.py`

Expected: exactly **1 error**, and it is a genuine pre-existing defect:

```
Sources/Youtube/ECMWF AIFS How Europe's AI Weather Model Is Changing Forecasting.md: unresolved link [[Tech Folk Insights]]
```

That link comes from the YouTube clipping's Web Clipper header and is fixed in Task 6 Step 4.
This exact baseline was measured on 2026-09-26; if you see a different count, something outside
this plan changed the vault. Record the actual number before continuing.

- [ ] **Step 6: Commit**

```powershell
git add Files/tools/validate_notes.py Files/tools/test_validate_notes.py
git commit -m "feat: add vault frontmatter and wiki-link validator with unit tests"
```

---

### Task 2: Folder Rename and Obsidian Configuration

**Files:**
- Rename: `Permanets Notes/` → `Permanent Notes/`
- Rename: `Literatures Notes/` → `Literatures Notes/`
- Rename: `Fleeting Notes/` → `Fleeting Notes/`
- Modify: `.obsidian/app.json`

**Interfaces:**
- Consumes: `Files/tools/validate_notes.py` from Task 1
- Produces: `Permanent Notes/` folder; `app.json` with `templatesFolder`, `attachmentFolderPath`, `alwaysUpdateLinks`, `useMarkdownLinks: false`, `newLinkFormat: "absolute"`

- [ ] **Step 1: Rename the folder**

Run:

```powershell
Rename-Item -LiteralPath "Permanets Notes" -NewName "Permanent Notes"
```

Expected: `Permanent Notes/` exists at the vault root; `Permanets Notes/` does not.

> **As executed under the controller ruling.** The directory on disk at execution time was
> `Permanent Note/` — singular, and already correctly spelled, so the typo this step set out to
> fix did not exist and the command above would have errored. The ruling widened the scope to
> all three section folders. These are the three renames that actually ran:
>
> ```powershell
> Rename-Item -LiteralPath "Permanent Note" -NewName "Permanent Notes"
> Rename-Item -LiteralPath "Literature Note" -NewName "Literatures Notes"
> Rename-Item -LiteralPath "Fleeting Note" -NewName "Fleeting Notes"
> ```
>
> `Literature Note/Reviews Kmutnb/` travelled with its parent and is now
> `Literatures Notes/Reviews Kmutnb/`. All three directories held no files, so no link needed
> updating. The command and expectation above are retained as the plan of record.

- [ ] **Step 2: Write the Obsidian config**

Overwrite `.obsidian/app.json` with exactly:

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

`newLinkFormat` must be `"absolute"`. `"relative"` emits `../../Permanent Notes/foo` and `"shortest"` emits a bare `foo` — both violate the global wiki-link constraint. `useMarkdownLinks: false` stops Obsidian emitting markdown links at all.

- [ ] **Step 3: Verify the JSON parses**

Run: `python -c "import json,pathlib; d=json.loads(pathlib.Path('.obsidian/app.json').read_text(encoding='utf-8')); assert d['newLinkFormat']=='absolute'; assert d['useMarkdownLinks'] is False; print('app.json OK')"`

Expected: `app.json OK`

- [ ] **Step 4: Confirm the typo is gone from live config**

Run: `rg -n "Permanets" --glob "!.obsidian/**" .`

Expected: 15 hits, all inside this plan and the spec — the two documents that name the old
folder only to document this rename. Zero hits outside them: any hit in live config, a note,
or a template is a defect.

- [ ] **Step 5: Commit**

```powershell
git add -A
git commit -m "refactor: rename Permanets Notes to Permanent Notes; enforce wiki-links in app.json"
```

---

### Task 3: Note Templates

Seven templates implementing the typed frontmatter contract. Each is a real, self-contained deliverable: a reviewer can reject the schema without rejecting the folder structure.

**Files:**
- Create: `Templates/Permanent Note.md`
- Create: `Templates/Literature Note.md`
- Create: `Templates/Review Kmutnb.md`
- Create: `Templates/Source.md`
- Create: `Templates/Fleeting Note.md`
- Create: `Templates/AI Research.md`
- Create: `Templates/AI Log.md`
- Delete: `Templates/Review Kmutnb templates.md`

**Interfaces:**
- Consumes: `app.json` `templatesFolder` from Task 2; validator from Task 1
- Produces: seven template files. `AGENTS.md` (Task 5) references these exact filenames.

> **Note on the validator and templates.** The validator walks all `*.md`, which includes `Templates/`, so templates are held to the same schema as real notes. `{{date}}` and `{{time}}` are substituted with a neutral string before YAML parsing, so a template's `created: {{date}}` parses as a plain string rather than a nested mapping. Templates must therefore carry complete, valid frontmatter — an empty `confidence: low` default satisfies the required-key check, and `status: seed` keeps the evergreen-sources rule from firing.

- [ ] **Step 1: Create `Templates/Permanent Note.md`**

```markdown
---
type: permanent
created: {{date}}
tags: []
status: seed
confidence: low
sources: []
---

# {{title}}

## Claim

<!-- One claim, in your own words. If this note needs two claims, split it. -->

## Evidence

<!-- Link the immutable sources that support the claim. At least one is required. -->

## Related

<!-- [[Permanent Notes/other-concept]] -->
```

- [ ] **Step 2: Create `Templates/Literature Note.md`**

```markdown
---
type: literature
created: {{date}}
tags: []
status: seed
title:
source:
authors: []
year:
venue:
confidence: low
---

# {{title}}

## Summary

## Findings

## Limitations

## Gaps

## Questions Raised
```

- [ ] **Step 3: Create `Templates/Review Kmutnb.md`**

Preserve the existing Kmutnb headings verbatim, adding only typed frontmatter:

```markdown
---
type: review
created: {{date}}
tags: []
status: seed
course:
due:
confidence: low
sources: []
---

## {{title}}

## Source Information

## Research Objective

## Problem

## Gap Addressed in paper

## Findings and conclusion

## Limitations or Weakness

## Implication or suggestions on future research

## How your search can fill gap
```

- [ ] **Step 4: Create `Templates/Source.md`**

```markdown
---
type: source
created: {{date}}
tags: []
status: seed
source_type: pdf
origin:
author:
published:
retrieved: {{date}}
immutable: true
---

# {{title}}

<!-- Verbatim content only. Never edit the material below this line. -->
```

- [ ] **Step 5: Create `Templates/Fleeting Note.md`**

```markdown
---
type: fleeting
created: {{date}}
tags: []
status: seed
promoted: false
---

# {{title}}

<!-- Raw capture. Triage from [[Fleeting Notes/index]]. -->
```

- [ ] **Step 6: Create `Templates/AI Research.md`**

```markdown
---
type: research
created: {{date}}
tags: []
status: seed
question:
method:
confidence: low
sources: []
---

# {{title}}

## Question

## Method

## Findings

## Gaps and Uncertainty

## Sources
```

- [ ] **Step 7: Create `Templates/AI Log.md`**

```markdown
---
type: log
created: {{date}}
tags: []
status: seed
timestamp: "{{date}} {{time}}"
skills: []
confidence: high
files_touched: []
---

# AI Request Log: {{title}}

- **Timestamp:**
- **Trigger / Request:**
- **Active Skills Utilized:**
- **Confidence Assessment:**
- **Files Created / Modified:**
- **Actions Taken:**
```

- [ ] **Step 8: Delete the superseded template**

Run: `git rm "Templates/Review Kmutnb templates.md"`

Its headings are preserved in `Review Kmutnb.md` (Step 3), so nothing is lost.

- [ ] **Step 9: Run the validator**

Run: `python Files/tools/validate_notes.py`

Expected: still exactly 1 error, the pre-existing `[[Tech Folk Insights]]`. No error line may
name a file under `Templates/` — all seven templates must validate against the same schema as
real notes.

- [ ] **Step 10: Commit**

```powershell
git add Templates/
git commit -m "feat: add seven typed note templates replacing the single legacy template"
```

---

### Task 4: Navigation

Six `index.md` files. A reviewer can reject the information architecture independently of the templates.

**Files:**
- Create: `index.md`
- Create: `Sources/index.md`
- Create: `Literatures Notes/index.md`
- Create: `Permanent Notes/index.md`
- Create: `Fleeting Notes/index.md`
- Create: `AI/AI research/index.md`

**Interfaces:**
- Consumes: templates from Task 3; existing source filenames
- Produces: `index.md` and `log.md` (Task 6) as the root navigation pair. `AGENTS.md` (Task 5) links `[[index|Home]]`.

- [ ] **Step 1: Create the root hub `index.md`**

```markdown
---
type: index
created: 2026-09-26
tags: []
status: evergreen
---

# ECMWF_ML — Second Brain

An Obsidian vault used as a research second brain. Current domain: ECMWF machine-learning
weather forecasting (AIFS). Operating contract for agents: [[AGENTS]].

## Sections

- [[Sources/index|Source Catalogue]] — immutable source dumps
- [[Literatures Notes/index|Literature Notes]] — one per source, summarised and evaluated
- [[Permanent Notes/index|Permanent Notes]] — atomic evergreen concepts
- [[Fleeting Notes/index|Fleeting Inbox]] — raw captures awaiting triage
- [[AI/AI research/index|Research Outputs]] — reports, syntheses, diagrams

## Activity

- [[log]] — chronological task log

## Current Focus

Establishing the vault conventions layer. Five sources are ingested but not yet
distilled into literature or permanent notes.
```

`type: index` is intentionally outside `REQUIRED_KEYS` in the validator, so hubs and MOCs
validate for links only and are not forced to carry claim-bearing fields.

- [ ] **Step 2: Create `Sources/index.md`**

```markdown
---
type: index
created: 2026-09-26
tags: []
status: evergreen
---

# Source Catalogue

Immutable. Never edit these files; critique belongs in a literature note.

## Research Papers

- `Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf` — AIFS, ECMWF data-driven forecasting system (arXiv 2406.01465)
- `Sources/Research Paper/arxiv.org/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf` — AIFS Single, update to the ML weather forecast model (arXiv 2509.18994)
- `Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf` — AIFS-CRPS, ensemble forecasting with a CRPS-based loss

## Report Papers

- `Sources/Report Paper/AS2025_Lang.pdf` — Annual Science 2025, Lang et al.

## Web

- [[Sources/URL/Paper page - AIFS-CRPS Ensemble forecasting using a model trained with a loss  function based on the Continuous Ranked Probability Score]] — Hugging Face paper page, arXiv 2412.15832

## Video

- [[Sources/Youtube/ECMWF AIFS How Europe’s AI Weather Model Is Changing Forecasting]] — transcript note

## Gaps

No source carries a `Source.md` metadata header yet, and none has a literature note.
```

Note: PDFs are listed as inline code, not wiki-links, because they have no markdown file
for the validator to resolve.

- [ ] **Step 3: Create `Literatures Notes/index.md`**

```markdown
---
type: index
created: 2026-09-26
tags: []
status: evergreen
---

# Literature Notes

One note per source, holding summary, findings, limitations, and gaps.

## Gaps

No literature notes exist yet. Five sources await processing:

- AIFS (arXiv 2406.01465)
- AIFS Single (arXiv 2509.18994)
- AIFS-CRPS (Nature, s44387-026-00073-7)
- AS2025 Lang report paper
- ECMWF AIFS YouTube transcript
```

- [ ] **Step 4: Create `Permanent Notes/index.md`**

```markdown
---
type: index
created: 2026-09-26
tags: []
status: evergreen
---

# Permanent Notes

Atomic, evergreen, one claim each. Every permanent note requires at least one
`sources` link.

## Gaps

Empty. Candidate concepts from the ingested sources, not yet extracted:

- CRPS as a proper scoring rule for ensemble training
- Distributional / stochastic ensemble generation
- Medium-range forecast skill metrics (RMSE, ACC, CRPS)
- Data-driven vs physics-based model trade-offs
- Early-exit and inference-cost considerations for diffusion models
```

- [ ] **Step 5: Create `Fleeting Notes/index.md`**

```markdown
---
type: index
created: 2026-09-26
tags: []
status: evergreen
---

# Fleeting Inbox

Raw, unpolished captures. Triage each into a permanent note, a literature note,
or delete.

## Gaps

Empty.
```

- [ ] **Step 6: Create `AI/AI research/index.md`**

```markdown
---
type: index
created: 2026-09-26
tags: []
status: evergreen
---

# Research Outputs

Reports, syntheses, and architecture artifacts produced by deep-research and
diagram workflows.

## Design

- [[AI/AI research/2026-09-26-second-brain-scaffold-design]] — vault conventions design spec
- [[AI/AI research/2026-09-26-second-brain-scaffold-plan]] — implementation plan for the above

## Gaps

No research reports yet. No Archify HTML diagrams generated.
```

- [ ] **Step 7: Run the validator**

Run: `python Files/tools/validate_notes.py`

Expected: **2 errors** — the pre-existing `[[Tech Folk Insights]]`, plus one new
`unresolved link [[AGENTS]]` from the root `index.md`, because `AGENTS.md` is created in
Task 5. Every wiki-link among the six index files that points at an existing note resolves.

- [ ] **Step 8: Commit**

```powershell
git add index.md "Sources/index.md" "Literatures Notes/index.md" "Permanent Notes/index.md" "Fleeting Notes/index.md" "AI/AI research/index.md"
git commit -m "feat: add root hub and five section MOCs"
```

---

### Task 5: AGENTS.md Operating Contract

**Files:**
- Create: `AGENTS.md`

**Interfaces:**
- Consumes: exact template filenames from Task 3; hub filename `index.md` from Task 4
- Produces: the persistent contract every future session loads

- [ ] **Step 1: Create `AGENTS.md`**

```markdown
---
type: agent
created: 2026-09-26
---

# AGENTS.md — Operating Contract

## What this is

An Obsidian vault used as a research second brain. Currently focused on ECMWF
machine-learning weather forecasting (AIFS). Acting here means maintaining a
rigorous, interconnected knowledge graph with evidence-backed claims.

Start at [[index|Home]].

## Vault map

| Folder | Holds |
|---|---|
| `Sources/` | Immutable source dumps. `Report Paper/`, `Research Paper/`, `URL/`, `Youtube/`. **Never edit.** |
| `Sources/Markdown/` | Extracted text of each `Research Paper/` PDF, as immutable source notes. Written only by `Files/tools/pdf_to_markdown.py`. |
| `Literatures Notes/` | One note per source: summary, findings, limitations, gaps. `Reviews Kmutnb/` for assignments. |
| `Permanent Notes/` | Atomic evergreen concepts. One claim per note, with evidence. |
| `Fleeting Notes/` | Raw unprocessed captures. |
| `AI/AI research/` | Research reports, syntheses, architecture diagrams. |
| `AI/logs/` | Per-task execution logs. |
| `Templates/` | Note templates. |
| `Files/` | Attachments. |
| `Files/tools/` | Python tooling: `validate_notes.py`, `pdf_to_markdown.py`, `wiki_doctor.py` and their tests. Run, never hand-edit outputs. |
| `skills/` | Agent skill contracts. One folder per skill, each with a `SKILL.md`. |

## Hard rules

1. **Wiki-links only**, always full-path from the vault root: `[[Permanent Notes/foo]]`.
   Never write `[text](../path/foo.md)`.
2. **`Sources/**` is immutable.** Never edit a source file. Corrections and critique
   go in a literature note.
3. **`confidence` is required** on any note that makes a claim. `high` means verified
   against an immutable source or peer-reviewed literature.
4. **Every completed task produces a log** — see Logging below.

Field values are constrained: `status` is `seed` | `draft` | `evergreen` | `archived`;
`confidence` is `high` | `medium` | `low`. See `Templates/` for the full contract.

## Note types

| Type | Folder | Template |
|---|---|---|
| `permanent` | `Permanent Notes/` | `Templates/Permanent Note.md` |
| `literature` | `Literatures Notes/` | `Templates/Literature Note.md` |
| `review` | `Literatures Notes/Reviews Kmutnb/` | `Templates/Review Kmutnb.md` |
| `source` | `Sources/` | `Templates/Source.md` |
| `fleeting` | `Fleeting Notes/` | `Templates/Fleeting Note.md` |
| `research` | `AI/AI research/` | `Templates/AI Research.md` |
| `log` | `AI/logs/` | `Templates/AI Log.md` |

`type: index` is used by MOCs and is not claim-bearing.

## Workflow: ingest a source

1. Drop the raw file in the correct `Sources/` subfolder.
2. Add a `Templates/Source.md` header with `origin`, `author`, `published`, `retrieved`.
3. Create a literature note from `Templates/Literature Note.md`, linking back to the source.
4. Distil atomic insights into permanent notes, each citing the source.
5. Add both to the relevant MOC. Log the task.

## Workflow: run research

1. Define the question. State it in an `AI Research` note before searching.
2. Gather across multiple source types. Prefer primary literature.
3. Cross-verify each data point. Cite immutably.
4. Record findings, then explicitly record gaps and uncertainty.
5. Set `confidence` honestly. Link the output from `[[AI/AI research/index]]`. Log the task.

## Workflow: log a task

1. Create `AI/logs/YYYY-MM-DD-HHmm-topic.md` from `Templates/AI Log.md`.
2. Record trigger, skills used, confidence, files touched, actions taken.
3. Append a one-line entry to `[[log]]`, newest first.

## Never

- Edit a file in `Sources/`.
- Write a markdown link where a wiki-link belongs.
- Promote a permanent note to `status: evergreen` without at least one `sources` link.
- Promote a note to `status: evergreen` while its `confidence` is `low`.
- Link to a note that does not exist yet — describe it under **Gaps** instead.
- Leave a dangling wiki-link. Every `[[...]]` must resolve to a real file.
- Finish a task without logging it.

## Verify before claiming done

Run `python Files/tools/validate_notes.py`. Exit 0 means the frontmatter schema and
every wiki-link in the vault are valid. Do not report success without it.
```

- [ ] **Step 2: Verify every path referenced in AGENTS.md exists**

Run:

```powershell
rg -o "\`(Templates|Permanent Notes|Literatures Notes|Fleeting Notes|AI|Sources)/[^\` ]+\`" AGENTS.md
```

Expected: the `Templates/` filenames listed in the note-types table are exactly the seven
files created in Task 3, with matching spelling. Manually confirm the folder names against
the vault root — note `Permanets Notes` must not appear.

- [ ] **Step 3: Run the validator**

Run: `python Files/tools/validate_notes.py`

Expected: exactly **2 errors**, both known and expected:

1. `unresolved link [[log]]` — `log.md` is created in Task 6. This is the knowingly-red
   intermediate state; do not treat it as a regression.
2. `unresolved link [[Tech Folk Insights]]` — pre-existing, fixed in Task 6 Step 4.

The `[[AGENTS]]` error introduced by Task 4 is now gone, since this task creates that file.

- [ ] **Step 4: Commit**

```powershell
git add AGENTS.md
git commit -m "docs: add AGENTS.md operating contract for the vault"
```

---

### Task 6: Logging Convention and Existing-Note Frontmatter

Brings the vault to a fully green validator state and demonstrates the logging convention.

**Files:**
- Create: `log.md`
- Create: `AI/logs/2026-09-26-<HHmm>-second-brain-scaffold.md`
- Modify: `Sources/URL/Paper page - AIFS-CRPS...md` (add frontmatter only)
- Modify: `Sources/Youtube/ECMWF AIFS How Europe’s AI Weather Model Is Changing Forecasting.md` (add frontmatter only)

**Interfaces:**
- Consumes: `Templates/AI Log.md` from Task 3; `[[index|Home]]` hub from Task 4
- Produces: `[[log]]` target referenced by `AGENTS.md`

> **On "modify" for sources.** The immutability rule protects *content*. The two markdown
> files in `Sources/` are clippings/transcripts with no metadata header at all. Adding a
> `Source.md` frontmatter block is the Ingest workflow's step 2, not an edit to the source
> material. Do not alter a single character of the body text. PDFs are untouched.

- [ ] **Step 1: Create `log.md`**

```markdown
---
type: index
created: 2026-09-26
tags: []
status: evergreen
---

# Task Log

Append-only, newest first. One line per completed task; detail lives in the linked
`AI/logs/` entry.

| Date | Task | Skills | Confidence | Log |
|---|---|---|---|---|
| 2026-09-26 | Second brain scaffold: validator, templates, navigation, AGENTS.md, logging | superpowers:brainstorming, superpowers:writing-plans | high | [[AI/logs/2026-09-26-<HHmm>-second-brain-scaffold]] |
```

Replace `<HHmm>` with the actual 24-hour time this task started, in both this file and the
filename in Step 2.

- [ ] **Step 2: Create the execution log**

Create `AI/logs/2026-09-26-<HHmm>-second-brain-scaffold.md` using the same `<HHmm>`:

```markdown
---
type: log
created: 2026-09-26
tags: []
status: evergreen
timestamp: "2026-09-26 <HHmm>"
skills:
  - superpowers:brainstorming
  - superpowers:writing-plans
confidence: high
files_touched:
  - "[[AGENTS]]"
  - "[[index]]"
  - "[[log]]"
  - "[[Files/tools/validate_notes.py]]"
---

# AI Request Log: Second Brain Scaffold

- **Timestamp:** 2026-09-26 <HHmm>
- **Trigger / Request:** Create the vault's conventions layer so it functions as a second
  brain, and formalise the operating instructions as `AGENTS.md`.
- **Active Skills Utilized:** superpowers:brainstorming (architectural path — 5 clarifying
  questions, 3 approaches, 4-section design), superpowers:writing-plans.
- **Confidence Assessment:** Pass. Design verified against the vault's actual state on
  2026-09-26. Scope deliberately excludes distilling the five existing sources.
- **Files Created / Modified:** see `files_touched` in frontmatter.
- **Actions Taken:**
  - Surveyed the vault: 5 sources, 2 templates, no index, no log, no agent config.
  - Corrected the schema typo `Permanets Notes` → `Permanent Notes`.
  - Wrote a Python validator with unit tests to enforce frontmatter and link integrity.
  - Set Obsidian to emit absolute wiki-links so the linking rule is mechanical.
  - Authored seven typed templates and six navigation files.
  - Authored `AGENTS.md` as the persistent operating contract.
  - Initialised git, gitignored 64 MB of PDFs and workspace state.
```

- [ ] **Step 3: Add a `Source.md` header to the Hugging Face clipping**

Prepend this block to `Sources/URL/Paper page - AIFS-CRPS Ensemble forecasting using a model trained with a loss  function based on the Continuous Ranked Probability Score.md`, above the existing `---` block, and delete the old `---` block. Leave every line of body text exactly as-is:

```yaml
---
type: source
created: 2026-09-26
tags: []
status: seed
source_type: url
origin: https://huggingface.co/papers/2412.15832
author: ECMWF
published: 2024-12-21
retrieved: 2026-09-26
immutable: true
---
```

- [ ] **Step 4: Replace the header on the YouTube transcript note**

This file already carries a Web Clipper frontmatter block (`title`, `source`, `author`,
`published`). Replace that entire block with the one below. Leave every line of body text
byte-identical — read and write as UTF-8, since the title contains a U+2019 apostrophe.

Its `author` value is currently the wiki-link `[[Tech Folk Insights]]`, and **no note by that
name exists**, so the link dangles and the validator will reject it. The replacement records
the channel as a plain string, which honours the "no links to notes that do not exist" rule
without inventing a note. `origin` is carried over from the clipper's `source` field;
`published` is left empty because the clipper recorded a clip date, not a publication date.

```yaml
---
type: source
created: 2026-09-26
tags: []
status: seed
source_type: youtube
origin: https://www.youtube.com/watch?v=6Dvrly5Vu6w
author: Tech Folk Insights
published:
retrieved: 2026-09-26
immutable: true
---
```

- [ ] **Step 5: Run the validator**

Run: `python Files/tools/validate_notes.py`

Expected: `OK - vault clean.`, zero errors, exit code 0. This is the first fully green state
and the point of the whole plan. If the YouTube file still reports an unresolved link, the
U+2019 apostrophe was likely mangled by a non-UTF-8 write — re-read it and confirm the filename
is unchanged.

- [ ] **Step 6: Commit**

```powershell
git add -A
git commit -m "feat: add task log convention, scaffold execution log, and source metadata headers"
```

---

### Task 7: Template Cleanup and Final Verification

Contains the one step gated on user confirmation, and the final acceptance run.

**Files:**
- Possibly delete: `Templates/Paper page - AIFS-CRPS Ensemble forecasting...md`

**Interfaces:**
- Consumes: green validator state from Task 6
- Produces: nothing downstream; this is the acceptance gate

- [ ] **Step 1: Diff the duplicate clipping against its source**

Run:

```powershell
git diff --no-index --stat "Templates/Paper page - AIFS-CRPS Ensemble forecasting using a model trained with a loss  function based on the Continuous Ranked Probability Score.md" "Sources/URL/Paper page - AIFS-CRPS Ensemble forecasting using a model trained with a loss  function based on the Continuous Ranked Probability Score.md"
```

Then run the same command without `--stat` to see the actual differing lines. Note the
`Sources/URL/` copy gained a `type: source` header in Task 6 Step 3; that accounts for
part of the difference. Report the remaining substantive differences to the user.

- [ ] **Step 2: STOP — get user confirmation before deleting**

Present the diff and ask the user to confirm that the `Sources/URL/` copy is canonical.
**Do not delete anything until they confirm.** The file may hold content the source copy
lacks.

- [ ] **Step 3: Delete the template copy, if confirmed**

Run: `git rm "Templates/Paper page - AIFS-CRPS Ensemble forecasting using a model trained with a loss  function based on the Continuous Ranked Probability Score.md"`

Skip this step if the user declined.

- [ ] **Step 4: Run the full acceptance check**

Run all of these and confirm each result:

```powershell
python Files/tools/validate_notes.py
python -m unittest discover -s "Files/tools" -p "test_*.py"
rg -n "Permanets" --glob "!.obsidian/**" .
git status --short
```

Expected, mapping to the spec's verification section:

| Check | Expected |
|---|---|
| `validate_notes.py` | `OK - vault clean.` |
| `unittest` | `OK`, 23 tests |
| `rg "Permanets"` | 15 hits, all in the plan and spec, which name the old folder only to document the rename; zero elsewhere |
| `git status --short` | empty (clean tree) |

Additionally confirm by opening Obsidian that `Templates/Permanent Note.md` and
`Templates/AI Log.md` insert cleanly via the core Templates plugin, and that no unresolved
links appear in any of the six index files. These two are the only spec verification items
that cannot be automated.

- [ ] **Step 5: Commit**

```powershell
git commit -m "chore: remove duplicate Web Clipper capture from Templates"
```

Skip if Step 3 was skipped.

---

## Spec Coverage

| Spec section | Task |
|---|---|
| 1. Folder rename | Task 2, Step 1 |
| 2. `AGENTS.md` | Task 5 |
| 3. Seven templates + enum legend | Task 3 |
| 4. Navigation, six files | Task 4 |
| 5. `.obsidian/app.json` | Task 2, Step 2 |
| 6. Logging, both files | Task 6, Steps 1–2 |
| 7. Clipping cleanup (gated) | Task 7, Steps 1–3 |
| 8. git + `.gitignore` | Already committed (`a051b3d`); verified in Task 7 Step 4 |
| Verification 1–6 | Task 7, Step 4 |

## Self-Review Notes

Review was performed against the spec and against the real vault, not from memory. Findings
and their resolutions:

1. **Two of my own tests were wrong.** `test_strips_alias` asserted that
   `[[Permanent Notes/index|Concept Map]]` resolves, but with two `index` entries in the stem
   index the function correctly returns `None` — the test contradicted the implementation.
   Rewritten to alias-strip a uniquely-stemmed target. `test_bare_index_is_ambiguous` used
   `Path(".")` as the root, making it pass or fail depending on the working directory: once
   Task 4 creates a root `index.md`, filesystem existence would resolve the bare link and the
   test would fail. Both now use a root that contains no real files, and a new
   `test_existing_file_beats_stem_index` documents the real-vault behaviour deterministically.
2. **Test count was wrong.** I asserted 18 tests in two places; the suite as first written had
   15. The suite now has exactly 18, and the count is derived in a comment beside it.
3. **The sources rule contradicted the template.** Requiring `sources` on *every* permanent
   note meant a freshly inserted template (`sources: []`, `status: seed`) failed validation on
   creation. The rule now fires only on `status: evergreen`, which matches the
   seed → draft → evergreen lifecycle and keeps new notes born valid. `test_seed_permanent_note_may_be_unsourced`
   and `test_evergreen_permanent_note_requires_sources` pin both sides of that boundary.
4. **`AGENTS.md` would have failed its own validator.** The validator walks every `*.md`, and
   my drafted `AGENTS.md` had no frontmatter. It now carries `type: agent`, an unmanaged type,
   so it is link-checked but not forced to carry claim-bearing fields.
5. **This plan file would also have failed.** It was written without frontmatter. Now typed
   `plan`.
6. **A dangling link already exists in the vault.** The YouTube clipping's Web Clipper header
   contains `author: "[[Tech Folk Insights]]"`, and no such note exists. Task 6 Step 4 replaces
   it with the plain string `Tech Folk Insights` and explains why.
7. **`{{date}}` is not a YAML scalar.** `created: {{date}}` parses as the nested mapping
   `{'date': None}` rather than erroring, which would have produced a dict where a date belongs.
   `parse_frontmatter` now substitutes placeholders before parsing; `test_placeholders_do_not_break_parsing`
   pins it.

8. **The validator failed its own documentation.** Run against the real vault it reported
   **41 errors**, of which 30 were illustrative `[[...]]` examples inside backticks and fenced
   code blocks in the spec and this plan. Obsidian does not create links inside code, so the
   validator was wrong, not the docs — and as written the vault could never have reached a
   green state. `strip_code()` now removes fenced blocks and inline spans before link
   scanning. Measured effect against the real vault: **41 errors → 1**, and the single
   remaining error is the genuine `[[Tech Folk Insights]]` defect handled in Task 6.
9. **A `.py` file was wiki-linked.** `files_touched` in the execution log pointed at
   `[[Files/tools/validate_notes.py]]`, which can never resolve — the stem index covers `*.md`
   only. Now recorded as a plain path string.

10. **Two code blocks contained a literal ` ``` `, corrupting this document.** The
    `TestStripCode` fixture embedded a raw triple-backtick, and `FENCE_RE` was written as
    `re.compile(r"^```.*?^```")`. Either one terminates the enclosing markdown fence early, so
    the plan rendered as broken code from that point on — discovered by diffing the plan's
    extracted code against the code actually executed. Both now build the fence from
    `"`" * 3`. The same class of bug applies to any future code added to this plan: never
    write a literal triple-backtick inside a fenced block.

11. **The validator flagged its own tooling as vault defects.** The SDD harness workspace is
    written to `<repo-root>/.superpowers/sdd/<plan>/`, because `.git/` is a protected path for
    agent writes. That places the progress ledger, the per-task briefs and the implementer
    reports *inside the vault root*, where `rglob("*.md")` finds them: they carry no
    frontmatter, so each was reported as a defect and the measured baseline was 3 errors
    instead of the 1 this plan predicts. `.superpowers` is a tooling directory semantically
    identical to the `.obsidian` and `.trash` entries already skipped, so it is now in
    `SKIP_DIRS`, pinned by `test_skips_tooling_directories`. The fix is permanent rather than
    session-specific, and restores the documented baseline: **1 error**, the genuine
    `[[Tech Folk Insights]]` defect from finding 6. Suite is now 23 tests.

**The validator and its tests were executed, not just written.** Both were materialised in a
scratch directory and run: 23 tests pass, and the vault baseline of 1 error was measured, not
predicted. A diff confirms that both `validate_notes.py` and `test_validate_notes.py` in this
plan are byte-identical to the code that ran, so the blocks above can be trusted as the code
that produced these numbers. Every expected count in the task steps above traces to that run.

**Placeholder scan:** the only `<HHmm>` tokens are runtime values the executor substitutes with
the real start time, called out explicitly in Task 6. No `TBD`, no "similar to Task N".

**Type consistency:** `REQUIRED_KEYS`, `ENUMS`, `parse_frontmatter`, `resolve_link`,
`build_stem_index`, `validate`, and `main` are defined once in Task 1 and consumed by name in
Tasks 1, 3, 6, and 7. The seven template filenames are fixed in Task 3 and referenced verbatim
in Task 5's note-types table.

**Known ordering constraint:** `AGENTS.md` (Task 5) links `[[log]]`, which does not exist until
Task 6. That is the only knowingly-red intermediate state, and Task 5 Step 3 says so explicitly
so the executor does not treat it as a regression.

**Scope:** single coherent deliverable; no decomposition needed.
