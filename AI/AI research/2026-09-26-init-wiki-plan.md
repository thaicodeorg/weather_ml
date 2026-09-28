---
type: plan
created: 2026-09-26
tags:
  - meta
  - vault-design
  - tooling
---

# Init Wiki Implementation Plan (Task 8 of the Second Brain Scaffold)

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** A new device that clones this vault can prove it is ready to work in it by running one command, and an agent that lands there is told what to check instead of re-deriving it.

**Architecture:** Deterministic checks live in tested Python (`Files/tools/wiki_doctor.py`), matching the existing `validate_notes.py` pattern. The judgment layer is a thin skill (`skills/init-wiki/SKILL.md`) that runs the doctor and acts on its report. The doctor holds the only machine-readable copy of the vault's expected shape, and a test fails if `AGENTS.md` stops documenting it — so the doctor, the skill, and the operating contract cannot drift apart.

**Tech Stack:** Python 3.10+ (vault runs 3.14), `unittest` from the standard library, `pdfplumber` and `PyYAML` for the package probe, `git` via `subprocess` for read-only state.

**Spec:** `AI/AI research/2026-09-26-second-brain-scaffold-design.md` defines the vault shape this doctor checks (its Deliverables 3 and 5 fix the 7 templates and the 7 `app.json` keys). The `init-wiki` design itself was approved in chat and is recorded in "Approved Design" below; it is not in the scaffold spec, which predates it.

**Predecessor plan:** `AI/AI research/2026-09-26-second-brain-scaffold-plan.md` — this is its Task 8, executed after its Tasks 4–7 land. Its ledger is `.superpowers/sdd/2026-09-26-second-brain-scaffold-plan/progress.md`.

## Approved Design

Decided with the user before planning:

| Question | Decision |
|---|---|
| GitHub's role | Out of scope. The user commits and pushes personally. The doctor **reports** git state read-only and never fails on it. |
| Doctor scope | Runtime, structure, templates, tooling, config, integrity, agent wiring, plus read-only git. |
| Repair behavior | Report by default. `--fix` applies only repairs marked safe. |
| Split | Python doctor + tests; markdown skill on top. No logic in the skill. |
| Single source of truth | `wiki_doctor.VAULT_FOLDERS`; a test asserts `AGENTS.md` mentions every entry. |

Repair split, because some failures are safe to repair and some need a human:

- **Auto-fix under `--fix`:** create a missing folder listed in `VAULT_FOLDERS`; delete stray `__pycache__` directories.
- **Report only, never auto:** missing Python packages, missing templates, missing tools, `app.json` drift, validator errors, missing `AGENTS.md`. These need a decision, not a `mkdir`.

## Global Constraints

- PowerShell 5.1 on Windows. No `&&`. Use `;` or `if ($?) { }`.
- Tests use `unittest` and import the module under test with `sys.path.insert(0, str(Path(__file__).parent))`, matching `Files/tools/test_validate_notes.py:1-7`.
- Every check is pure with respect to the filesystem except `fix_safe`, which is the only function allowed to write.
- `check_git` must never produce a non-`ok` finding. The user manages git; a dirty tree is information, not a readiness failure.
- `Sources/**` is immutable. The doctor reads it and never writes to it.
- Never add a check whose failure mode cannot be fixed by the person reading the report. A check that always fails is noise.
- The skill at `skills/init-wiki/SKILL.md` holds no logic. If a rule needs code, it goes in the doctor and gets a test.

---

## File Structure

**Created:**

| Path | Responsibility |
|---|---|
| `Files/tools/wiki_doctor.py` | All readiness checks, safe repairs, CLI. Exit 0 clean / 1 on any failure |
| `Files/tools/test_wiki_doctor.py` | Unit tests for the doctor |
| `skills/init-wiki/SKILL.md` | Trigger contract: run the doctor, act on the report |

**Modified:** none. The doctor is additive.

**Reads but never writes:** `.obsidian/app.json`, `AGENTS.md`, `Templates/`, `Files/tools/`, git metadata.

---

### Task 8.1: Doctor skeleton, runtime and structure checks

**Files:**
- Create: `Files/tools/wiki_doctor.py`
- Create: `Files/tools/test_wiki_doctor.py`

**Interfaces:**
- Consumes: nothing. This is the first task.
- Produces:
  - `Finding` — frozen dataclass, fields `group: str`, `ok: bool`, `message: str`, `fixable: bool = False`, `hint: str = ""`.
  - `VAULT_FOLDERS: tuple[str, ...]` — 17 relative folder paths.
  - `check_runtime() -> list[Finding]`
  - `check_structure(vault_root: Path) -> list[Finding]`
  - `main() -> int` — prints grouped results, returns 1 if any finding is not `ok`.
  - Every later task adds a `check_*(vault_root) -> list[Finding]` and appends it inside `check_all`.

- [ ] **Step 1: Write the failing tests**

Create `Files/tools/test_wiki_doctor.py`:

```python
import sys
import unittest
from pathlib import Path

sys.path.insert(0, str(Path(__file__).parent))

import wiki_doctor as wd


class TestRuntime(unittest.TestCase):
    def test_reports_a_python_version(self):
        findings = wd.check_runtime()
        self.assertTrue(any(f.ok and "python" in f.message for f in findings))

    def test_reports_each_required_package(self):
        messages = " ".join(f.message for f in wd.check_runtime())
        for name in wd.REQUIRED_PACKAGES:
            self.assertIn(name, messages)

    def test_missing_package_names_its_pip_target(self):
        findings = [wd.Finding("runtime", False, "x is not importable", hint="pip install PyYAML")]
        self.assertEqual(findings[0].hint, "pip install PyYAML")


class TestStructure(unittest.TestCase):
    def test_present_folder_passes(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "Templates").mkdir()
            found = [f for f in wd.check_structure(root) if "Templates" in f.message]
            self.assertEqual(len(found), 1)
            self.assertTrue(found[0].ok)

    def test_missing_folder_fails_and_is_marked_fixable(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            found = [f for f in wd.check_structure(Path(d)) if "Templates" in f.message]
            self.assertFalse(found[0].ok)
            self.assertTrue(found[0].fixable)

    def test_every_declared_folder_is_checked(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            messages = [f.message for f in wd.check_structure(Path(d))]
            self.assertEqual(len(messages), len(wd.VAULT_FOLDERS))


class TestExitCode(unittest.TestCase):
    def _run(self, argv):
        import io
        from contextlib import redirect_stdout

        saved = sys.argv
        sys.argv = ["wiki_doctor.py"] + argv
        try:
            with redirect_stdout(io.StringIO()):
                return wd.main()
        finally:
            sys.argv = saved

    def test_returns_one_when_folders_are_missing(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            self.assertEqual(self._run(["--vault-root", d]), 1)
```

- [ ] **Step 2: Run the tests and confirm they fail**

Run: `python -m unittest test_wiki_doctor -v` from `Files/tools`
Expected: `ModuleNotFoundError: No module named 'wiki_doctor'`

- [ ] **Step 3: Write the implementation**

Create `Files/tools/wiki_doctor.py`:

```python
"""Readiness checks for the ECMWF_ML research vault.

Run `python Files/tools/wiki_doctor.py` to report whether this machine can
work in the vault. Add --fix to apply only the repairs marked safe.
"""

import argparse
import json
import shutil
import subprocess
import sys
from dataclasses import dataclass
from pathlib import Path

VAULT_ROOT = Path(__file__).resolve().parents[2]

VAULT_FOLDERS = (
    "AI",
    "AI/AI research",
    "AI/logs",
    "Files",
    "Files/tools",
    "Fleeting Notes",
    "Literatures Notes",
    "Literatures Notes/Reviews Kmutnb",
    "Permanent Notes",
    "skills",
    "Sources",
    "Sources/Markdown",
    "Sources/Report Paper",
    "Sources/Research Paper",
    "Sources/URL",
    "Sources/Youtube",
    "Templates",
)

REQUIRED_PACKAGES = ("pdfplumber", "yaml")

PIP_TARGETS = {"pdfplumber": "pdfplumber", "yaml": "PyYAML"}

MIN_PYTHON = (3, 10)

SKIP_DIRS = {".obsidian", ".git", ".trash", "node_modules", ".superpowers"}


@dataclass(frozen=True)
class Finding:
    group: str
    ok: bool
    message: str
    fixable: bool = False
    hint: str = ""


def check_runtime():
    findings = []
    version = "{}.{}".format(sys.version_info[0], sys.version_info[1])
    if sys.version_info[:2] < MIN_PYTHON:
        findings.append(Finding("runtime", False, "python " + version + " is older than 3.10"))
    else:
        findings.append(Finding("runtime", True, "python " + version))
    for name in REQUIRED_PACKAGES:
        try:
            __import__(name)
        except ImportError:
            findings.append(
                Finding("runtime", False, name + " is not importable", hint="pip install " + PIP_TARGETS[name])
            )
        else:
            findings.append(Finding("runtime", True, name + " is importable"))
    return findings


def check_structure(vault_root):
    findings = []
    for rel in VAULT_FOLDERS:
        if (vault_root / rel).is_dir():
            findings.append(Finding("structure", True, rel))
        else:
            findings.append(
                Finding("structure", False, "missing folder: " + rel, fixable=True, hint="created by --fix")
            )
    return findings


def check_all(vault_root):
    findings = []
    findings += check_runtime()
    findings += check_structure(vault_root)
    return findings


def fix_safe(vault_root, findings):
    fixed = 0
    for finding in findings:
        if finding.ok or not finding.fixable or finding.group != "structure":
            continue
        rel = finding.message.split("missing folder: ", 1)[1]
        (vault_root / rel).mkdir(parents=True, exist_ok=True)
        fixed += 1
    for cache in vault_root.rglob("__pycache__"):
        if cache.is_dir() and not (SKIP_DIRS & set(cache.relative_to(vault_root).parts)):
            shutil.rmtree(cache, ignore_errors=True)
            fixed += 1
    return fixed


def main():
    if hasattr(sys.stdout, "reconfigure"):
        sys.stdout.reconfigure(encoding="utf-8", errors="replace")

    parser = argparse.ArgumentParser(description=__doc__)
    parser.add_argument("--fix", action="store_true", help="apply safe repairs only")
    parser.add_argument("--vault-root", default=str(VAULT_ROOT))
    args = parser.parse_args()

    vault_root = Path(args.vault_root).resolve()
    findings = check_all(vault_root)

    if args.fix:
        applied = fix_safe(vault_root, findings)
        if applied:
            print("applied {} safe repair(s)\n".format(applied))
            findings = check_all(vault_root)

    current = None
    for finding in findings:
        if finding.group != current:
            current = finding.group
            print("\n[{}]".format(current))
        print("  {} {}{}".format(
            "PASS" if finding.ok else "FAIL",
            finding.message,
            "" if finding.ok else "  -> " + finding.hint if finding.hint else "",
        ))

    failures = [f for f in findings if not f.ok]
    print("\n{} check(s), {} failure(s).".format(len(findings), len(failures)))
    return 1 if failures else 0


if __name__ == "__main__":
    sys.exit(main())
```

- [ ] **Step 4: Run the tests and confirm they pass**

Run: `python -m unittest test_wiki_doctor -v` from `Files/tools`
Expected: 7 tests OK

- [ ] **Step 5: Run the doctor against the real vault**

Run: `python Files/tools/wiki_doctor.py`
Expected: exits 0 if every folder in `VAULT_FOLDERS` exists, else exits 1 listing exactly which are missing. Record the actual output; if it exits 1 the folders really are absent and Task 8.1 is not done.

- [ ] **Step 6: Commit**

```bash
git add Files/tools/wiki_doctor.py Files/tools/test_wiki_doctor.py
git commit -m "feat: add vault readiness doctor with runtime and structure checks"
```

---

### Task 8.2: Templates, tools, config and integrity checks

**Files:**
- Modify: `Files/tools/wiki_doctor.py`
- Modify: `Files/tools/test_wiki_doctor.py`

**Interfaces:**
- Consumes: `Finding`, `check_all`, `VAULT_FOLDERS` from Task 8.1.
- Produces: `REQUIRED_TEMPLATES: tuple[str, ...]`, `REQUIRED_TOOLS: tuple[str, ...]`, `APP_JSON_REQUIRED: dict[str, object]`, `KNOWN_PREEXISTING: tuple[str, ...]`, and `check_templates`, `check_tools`, `check_config`, `check_integrity`, all `(vault_root: Path) -> list[Finding]`. `check_all` grows to call all four.

- [ ] **Step 1: Write the failing tests**

Append to `Files/tools/test_wiki_doctor.py`:

```python
class TestTemplates(unittest.TestCase):
    def _root(self, d, names):
        (Path(d) / "Templates").mkdir(exist_ok=True)
        for name in names:
            (Path(d) / "Templates" / name).write_text("---\ntype: review\n---\n", encoding="utf-8")
        return Path(d)

    def test_all_present_passes(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            root = self._root(d, wd.REQUIRED_TEMPLATES)
            failures = [f for f in wd.check_templates(root) if not f.ok]
            self.assertEqual(failures, [])

    def test_missing_template_fails_and_is_not_fixable(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            root = self._root(d, wd.REQUIRED_TEMPLATES[:-1])
            found = [f for f in wd.check_templates(root) if not f.ok]
            self.assertEqual(len(found), 1)
            self.assertIn(wd.REQUIRED_TEMPLATES[-1], found[0].message)
            self.assertFalse(found[0].fixable)

    def test_template_count_matches_the_spec(self):
        self.assertEqual(len(wd.REQUIRED_TEMPLATES), 7)


class TestTools(unittest.TestCase):
    def test_missing_tool_fails(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            found = [f for f in wd.check_tools(Path(d)) if not f.ok]
            self.assertEqual(len(found), len(wd.REQUIRED_TOOLS))


class TestConfig(unittest.TestCase):
    def _write(self, d, payload):
        obs = Path(d) / ".obsidian"
        obs.mkdir(exist_ok=True)
        (obs / "app.json").write_text(payload, encoding="utf-8")
        return Path(d)

    def test_matching_config_passes(self):
        import json
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            root = self._write(d, json.dumps(wd.APP_JSON_REQUIRED))
            self.assertEqual([f for f in wd.check_config(root) if not f.ok], [])

    def test_wrong_value_names_key_and_both_values(self):
        import json
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            payload = dict(wd.APP_JSON_REQUIRED, useMarkdownLinks=True)
            root = self._write(d, json.dumps(payload))
            found = [f for f in wd.check_config(root) if not f.ok]
            self.assertEqual(len(found), 1)
            self.assertIn("useMarkdownLinks", found[0].message)
            self.assertIn("True", found[0].message)
            self.assertIn("False", found[0].message)

    def test_invalid_json_fails_without_raising(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            root = self._write(d, "{not json")
            found = wd.check_config(root)
            self.assertEqual(len(found), 1)
            self.assertFalse(found[0].ok)

    def test_app_json_required_has_seven_keys(self):
        self.assertEqual(len(wd.APP_JSON_REQUIRED), 7)


class TestIntegrity(unittest.TestCase):
    def test_known_preexisting_errors_do_not_fail_the_check(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "Tech Folk Insights.md").write_text("no frontmatter here\n", encoding="utf-8")
            found = [f for f in wd.check_integrity(root) if not f.ok]
            self.assertEqual(found, [])
```

- [ ] **Step 2: Run the tests and confirm they fail**

Run: `python -m unittest test_wiki_doctor -v` from `Files/tools`
Expected: `AttributeError: module 'wiki_doctor' has no attribute 'REQUIRED_TEMPLATES'`

- [ ] **Step 3: Write the implementation**

Insert after `VAULT_FOLDERS` in `wiki_doctor.py`:

```python
REQUIRED_TEMPLATES = (
    "AI Log.md",
    "AI Research.md",
    "Fleeting Note.md",
    "Literature Note.md",
    "Permanent Note.md",
    "Review Kmutnb.md",
    "Source.md",
)

REQUIRED_TOOLS = (
    "pdf_to_markdown.py",
    "test_pdf_to_markdown.py",
    "test_validate_notes.py",
    "test_wiki_doctor.py",
    "validate_notes.py",
)

APP_JSON_REQUIRED = {
    "promptDelete": False,
    "templatesFolder": "Templates",
    "attachmentFolderPath": "Files",
    "alwaysUpdateLinks": True,
    "useMarkdownLinks": False,
    "newLinkFormat": "absolute",
    "showUnsupportedFiles": True,
}

KNOWN_PREEXISTING = (
    "Tech Folk Insights.md",
    "AI & Weather Prediction - UK Weather",
)
```

Insert before `check_all`:

```python
def check_templates(vault_root):
    findings = []
    for name in REQUIRED_TEMPLATES:
        if (vault_root / "Templates" / name).is_file():
            findings.append(Finding("templates", True, name))
        else:
            findings.append(
                Finding("templates", False, "missing template: " + name, hint="restore it from git")
            )
    return findings


def check_tools(vault_root):
    findings = []
    for name in REQUIRED_TOOLS:
        if (vault_root / "Files" / "tools" / name).is_file():
            findings.append(Finding("tools", True, name))
        else:
            findings.append(Finding("tools", False, "missing tool: " + name, hint="restore it from git"))
    return findings


def check_config(vault_root):
    path = vault_root / ".obsidian" / "app.json"
    if not path.is_file():
        return [Finding("config", False, "missing .obsidian/app.json", hint="restore it from git")]
    try:
        data = json.loads(path.read_text(encoding="utf-8"))
    except json.JSONDecodeError as exc:
        return [Finding("config", False, "app.json is not valid JSON: " + str(exc))]
    findings = []
    for key in sorted(APP_JSON_REQUIRED):
        want = APP_JSON_REQUIRED[key]
        if key not in data:
            findings.append(Finding("config", False, "app.json missing key: " + key))
        elif data[key] != want:
            findings.append(Finding(
                "config", False,
                "app.json {} is {!r}, expected {!r}".format(key, data[key], want),
            ))
        else:
            findings.append(Finding("config", True, "app.json " + key + " ok"))
    return findings


def check_integrity(vault_root):
    import validate_notes as vn

    errors = vn.validate(vault_root)
    known = [e for e in errors if any(k in e for k in KNOWN_PREEXISTING)]
    unknown = [e for e in errors if e not in known]
    if unknown:
        return [Finding("integrity", False, "validator: " + e) for e in unknown]
    return [Finding(
        "integrity", True,
        "validate_notes.py: 0 new error(s), {} known pre-existing".format(len(known)),
    )]
```

Replace the body of `check_all` with:

```python
def check_all(vault_root):
    findings = []
    findings += check_runtime()
    findings += check_structure(vault_root)
    findings += check_templates(vault_root)
    findings += check_tools(vault_root)
    findings += check_config(vault_root)
    findings += check_integrity(vault_root)
    return findings
```

- [ ] **Step 4: Run the tests and confirm they pass**

Run: `python -m unittest test_wiki_doctor -v` from `Files/tools`
Expected: 16 tests OK

- [ ] **Step 5: Run the whole tool test suite**

Run: `python -m unittest discover -s Files/tools -p "test_*.py" -v`
Expected: every test OK. `validate_notes.py` contributes its 28, `pdf_to_markdown.py` its own, and no test regresses.

- [ ] **Step 6: Commit**

```bash
git add Files/tools/wiki_doctor.py Files/tools/test_wiki_doctor.py
git commit -m "feat: check templates, tools, app.json and validator integrity in the doctor"
```

---

### Task 8.3: Agent wiring, read-only git, and the drift guard

**Files:**
- Modify: `Files/tools/wiki_doctor.py`
- Modify: `Files/tools/test_wiki_doctor.py`

**Interfaces:**
- Consumes: everything from Tasks 8.1 and 8.2, plus `AGENTS.md` at the vault root, which Task 5 of the scaffold plan creates.
- Produces: `check_agent_wiring(vault_root) -> list[Finding]`, `check_git(vault_root) -> list[Finding]`, and `check_all` calls both. `check_all` is now final.

- [ ] **Step 1: Write the failing tests**

Append to `Files/tools/test_wiki_doctor.py`:

```python
class TestAgentWiring(unittest.TestCase):
    def test_missing_agents_md_fails_with_a_pointer(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            found = wd.check_agent_wiring(Path(d))
            self.assertEqual(len(found), 1)
            self.assertFalse(found[0].ok)
            self.assertIn("AGENTS.md", found[0].message)

    def test_folder_absent_from_agents_md_fails(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "AGENTS.md").write_text("only mentions Templates\n", encoding="utf-8")
            found = [f for f in wd.check_agent_wiring(root) if not f.ok]
            self.assertTrue(found)
            self.assertTrue(any("Permanent Notes" in f.message for f in found))

    def test_matching_is_by_leaf_name_not_contiguous_path(self):
        """The scaffold's vault map puts `Sources/` and `Report Paper/` in
        separate table cells, so "Sources/Report Paper" is never a contiguous
        substring. Matching leaves is what "documents the vault" means."""
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            root = Path(d)
            (root / "AGENTS.md").write_text(
                "| `Sources/` | `Report Paper/`, `Research Paper/` |", encoding="utf-8"
            )
            found = [f for f in wd.check_agent_wiring(root) if "Report Paper" in f.message]
            self.assertEqual(found, [], "leaf name present in prose must satisfy the check")

    def test_real_agents_md_names_every_folder(self):
        if not (wd.VAULT_ROOT / "AGENTS.md").is_file():
            self.skipTest("AGENTS.md not created yet; scaffold plan Task 5 is a precondition")
        found = [f for f in wd.check_agent_wiring(wd.VAULT_ROOT) if not f.ok]
        self.assertEqual(found, [])


class TestGitIsInformational(unittest.TestCase):
    def test_non_repo_still_reports_ok(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            found = wd.check_git(Path(d))
            self.assertTrue(all(f.ok for f in found))

    def test_findings_are_always_ok(self):
        found = wd.check_git(wd.VAULT_ROOT)
        self.assertTrue(found)
        self.assertTrue(all(f.ok for f in found), "git state must never fail the doctor")


class TestCompleteVaultExitsZero(unittest.TestCase):
    """End-to-end: a vault built to spec must exit 0, so exit 1 means a real defect."""

    def _build(self, root):
        import json

        for rel in wd.VAULT_FOLDERS:
            (root / rel).mkdir(parents=True, exist_ok=True)
        # Schema-valid, because check_integrity runs the real validator over this
        # vault: a bare "---\ntype: review\n---" template is itself a defect.
        for name in wd.REQUIRED_TEMPLATES:
            (root / "Templates" / name).write_text(
                "---\ntype: review\ncreated: 2026-09-26\ntags: []\nstatus: seed\n"
                "course: Kmutnb seminar\ndue:\nconfidence: medium\nsources: []\n---\n",
                encoding="utf-8",
            )
        for name in wd.REQUIRED_TOOLS:
            (root / "Files" / "tools" / name).write_text("", encoding="utf-8")
        obs = root / ".obsidian"
        obs.mkdir(exist_ok=True)
        (obs / "app.json").write_text(json.dumps(wd.APP_JSON_REQUIRED), encoding="utf-8")
        # type: agent is deliberately outside REQUIRED_KEYS, per the scaffold
        # ledger, so AGENTS.md is link-checked but not forced to carry claims.
        # Leaf names, because that is what check_agent_wiring matches on.
        leaves = sorted({rel.rsplit("/", 1)[-1] for rel in wd.VAULT_FOLDERS})
        (root / "AGENTS.md").write_text(
            "---\ntype: agent\n---\n\n" + "\n".join(leaves) + "\n",
            encoding="utf-8",
        )
        return root

    def _run(self, root):
        import io
        from contextlib import redirect_stdout

        saved = sys.argv
        sys.argv = ["wiki_doctor.py", "--vault-root", str(root)]
        try:
            with redirect_stdout(io.StringIO()):
                return wd.main()
        finally:
            sys.argv = saved

    def test_a_vault_built_to_spec_exits_zero(self):
        import tempfile

        with tempfile.TemporaryDirectory() as d:
            root = self._build(Path(d))
            self.assertEqual(self._run(root), 0, "a spec-complete vault must not report failures")
```

- [ ] **Step 2: Run the tests and confirm they fail**

Run: `python -m unittest test_wiki_doctor -v` from `Files/tools`
Expected: `AttributeError: module 'wiki_doctor' has no attribute 'check_agent_wiring'`

- [ ] **Step 3: Write the implementation**

Insert before `check_all` in `wiki_doctor.py`:

```python
def check_agent_wiring(vault_root):
    agents = vault_root / "AGENTS.md"
    if not agents.is_file():
        return [Finding(
            "agent", False, "missing AGENTS.md",
            hint="agents have no operating contract; run Task 5 of the scaffold plan",
        )]
    text = agents.read_text(encoding="utf-8")
    # Match on leaf folder names, never on the full relative path: the vault map
    # is prose and a table, so `Sources/` and `Report Paper/` sit in separate
    # cells and "Sources/Report Paper" never appears as a contiguous substring.
    leaves = sorted({rel.rsplit("/", 1)[-1] for rel in VAULT_FOLDERS})
    findings = [
        Finding("agent", False, "AGENTS.md never mentions " + leaf)
        for leaf in leaves
        if leaf not in text
    ]
    if findings:
        return findings
    return [Finding("agent", True, "AGENTS.md names all {} folders".format(len(leaves)))]


def _git(vault_root, *args):
    try:
        proc = subprocess.run(
            ["git"] + list(args),
            cwd=str(vault_root),
            capture_output=True,
            text=True,
            timeout=20,
        )
    except (OSError, subprocess.SubprocessError):
        return None
    return proc.stdout.strip() if proc.returncode == 0 else None


def check_git(vault_root):
    if _git(vault_root, "rev-parse", "--is-inside-work-tree") != "true":
        return [Finding("git", True, "not a git repository; commits are managed by hand")]
    branch = _git(vault_root, "rev-parse", "--abbrev-ref", "HEAD") or "unknown"
    status = _git(vault_root, "status", "--porcelain") or ""
    dirty = len([line for line in status.splitlines() if line.strip()])
    remotes = (_git(vault_root, "remote") or "").split()
    return [
        Finding("git", True, "branch " + branch),
        Finding("git", True, "{} uncommitted change(s)".format(dirty)),
        Finding("git", True, "remotes: " + (", ".join(remotes) if remotes else "none configured")),
    ]
```

Replace the body of `check_all` with:

```python
def check_all(vault_root):
    findings = []
    findings += check_runtime()
    findings += check_structure(vault_root)
    findings += check_templates(vault_root)
    findings += check_tools(vault_root)
    findings += check_config(vault_root)
    findings += check_integrity(vault_root)
    findings += check_agent_wiring(vault_root)
    findings += check_git(vault_root)
    return findings
```

- [ ] **Step 4: Run the tests and confirm they pass**

Run: `python -m unittest test_wiki_doctor -v` from `Files/tools`
Expected: 23 tests OK. `test_real_agents_md_names_every_folder` reports `skipped` until scaffold Task 5 lands; that is the intended precondition, not a failure. `test_a_vault_built_to_spec_exits_zero` is the one that proves the whole doctor is satisfiable — if it fails, a check is demanding something no correct vault can provide.

- [ ] **Step 5: Verify `--fix` creates a missing folder and is idempotent**

Run: `python Files/tools/wiki_doctor.py --fix` twice
Expected: the first run reports the applied repairs, the second reports `applied 0 safe repair(s)`, and the vault ends with no missing folders.

- [ ] **Step 6: Commit**

```bash
git add Files/tools/wiki_doctor.py Files/tools/test_wiki_doctor.py
git commit -m "feat: check AGENTS.md coverage and report git state read-only"
```

---

### Task 8.4: The `init-wiki` skill

**Files:**
- Create: `skills/init-wiki/SKILL.md`

**Interfaces:**
- Consumes: `python Files/tools/wiki_doctor.py` and its `--fix` flag from Tasks 8.1–8.3.
- Produces: the skill contract. No code.

- [ ] **Step 1: Run the baseline before writing the skill**

Dispatch a fresh subagent with the vault path and this request, and nothing else:

> "You are setting up on a new machine with a clone of this vault. Check that it is ready to work in, and report anything broken."

Record what it inspects, what it invents, and what it misses. Do not tell it a doctor exists. Keep the output; the skill is written against the gaps it exposes.

- [ ] **Step 2: Write the skill**

Create `skills/init-wiki/SKILL.md`:

```markdown
---
name: init-wiki
description: Use when setting up on a new machine or a fresh clone of this vault, when asked whether the vault is ready to work in, when an agent session starts and the environment is unverified, or when a tool, template, dependency, or folder appears to be missing.
---

# Initialising the wiki

## Overview

One command decides whether this machine can work in the vault. Run it before
any other work and believe its output over your own assumptions about the setup.

## When to Use

- First session on a new device, or immediately after cloning
- "Is this ready?", "is the vault set up?", "why is this tool missing?"
- Any `ModuleNotFoundError`, missing template, or missing-folder error
- Before claiming a task is done, to confirm the environment is still sound

Not for: judging research content, or repairing notes. Use
`validate_notes.py` for note defects.

## The command

```bash
python Files/tools/wiki_doctor.py
```

Exit 0 means every check passed. Exit 1 means at least one failed, and the
report names each one. Add `--fix` to create missing folders and clear stale
`__pycache__`; nothing else is ever repaired automatically.

## Reading the report

The report is grouped. Groups that can fail on a fresh clone:

| Group | Fails when | Do this |
|---|---|---|
| `runtime` | Python older than 3.10, or `pdfplumber`/`PyYAML` missing | Run the `pip install` in the hint, then re-run |
| `structure` | A vault folder is absent | `--fix` creates it; re-run to confirm |
| `templates` | One of the 7 templates is gone | Restore from git; do not hand-write a template |
| `tools` | A script or its test is gone | Restore from git |
| `config` | `.obsidian/app.json` drifted from the 7 required keys | Restore from git; the keys enforce the wiki-link rule |
| `integrity` | `validate_notes.py` found a new error | Fix the note; the hint names the file |
| `agent` | `AGENTS.md` is missing or no longer documents every folder | Restore or update `AGENTS.md` |

The `git` group is **informational and never fails**. The user manages commits
and pushes personally. Report the branch, dirty count and remotes; change
nothing.

A `validator` error that mentions `Tech Folk Insights.md` or
`AI & Weather Prediction - UK Weather` is pre-existing and not yours to fix
unless asked. Say so rather than silently absorbing it.

## After a clean report

Read `AGENTS.md` before your first edit. It is the operating contract: vault map,
hard rules, note types, workflows. It outranks anything inferred from the folder
tree, and this skill does not restate it.

## Never

- Hand-write a missing template, tool, or `AGENTS.md`; restore from git
- Run `--fix` expecting it to install packages or repair notes
- Treat a passing doctor as evidence that the notes are correct; it checks the
  environment, and `validate_notes.py` checks the notes
- Commit, push, or change git state
```

- [ ] **Step 3: Verify the skill end to end**

Re-run the Step 1 request as a fresh subagent, this time instructing it to read
`skills/init-wiki/SKILL.md` first. Confirm it runs the doctor, reports the real
group, and does not attempt to fix `integrity` or `agent` findings by hand.

- [ ] **Step 4: Confirm the skill describes the real groups**

Run: `python Files/tools/wiki_doctor.py --vault-root .` and compare the group
names printed against the table in the skill. Every group in the output must
appear in the table and vice versa. Fix any mismatch before committing.

- [ ] **Step 5: Commit**

```bash
git add skills/init-wiki/SKILL.md
git commit -m "feat: add init-wiki readiness skill"
```

---

### Task 8.5: Whole-branch verification

**Files:** none created.

- [ ] **Step 1: Full test suite**

Run: `python -m unittest discover -s Files/tools -p "test_*.py" -v`
Expected: all OK, zero failures, zero errors.

- [ ] **Step 2: Validator**

Run: `python Files/tools/validate_notes.py`
Expected: exactly the 2 known pre-existing failures, nothing new.

- [ ] **Step 3: Doctor**

Run: `python Files/tools/wiki_doctor.py`
Expected: exit 0, zero failures.

- [ ] **Step 4: Idempotence**

Run: `python Files/tools/wiki_doctor.py --fix` twice
Expected: second run reports `applied 0 safe repair(s)`.

- [ ] **Step 5: Fresh-clone simulation**

Copy the vault to a temporary directory excluding `.git`, run the doctor there
with `--vault-root`, and confirm it reports the missing `.git` as informational
rather than failing.

- [ ] **Step 6: Record the outcome in the ledger**

Append a Task 8 section to
`.superpowers/sdd/2026-09-26-second-brain-scaffold-plan/progress.md` following
the existing format: rulings, findings, deferred items, and the completion line.

## Self-Review Notes

- **Spec coverage:** the scaffold spec's Deliverables 3 (7 templates) and 5
  (7 `app.json` keys) are checked verbatim against `REQUIRED_TEMPLATES` and
  `APP_JSON_REQUIRED`; its Deliverables 1, 2, 4 and 6 are covered by
  `check_structure` and `check_agent_wiring`. No spec requirement is left
  unverified.
- **Ordering:** Task 8.3's real-vault drift test skips until scaffold Task 5
  creates `AGENTS.md`. That is a stated precondition, not a silent skip.
- **Type consistency:** `check_*` all take `vault_root: Path` except
  `check_runtime()`, which touches no filesystem. `check_all` is the only
  aggregator and is rewritten in each task; its final form is Task 8.3's.
- **No placeholders:** every check, test, and constant is spelled out. The one
  judgement call left to the implementer is Step 1 of Task 8.4, which requires
  *running* a baseline and recording it, not inventing content.
- **Defect found by self-review and fixed:** the Task 8.3 end-to-end test first
  built its synthetic vault with bare `---\ntype: review\n---` templates and a
  frontmatter-less `AGENTS.md`. Both are themselves `validate_notes.py` errors,
  so `check_integrity` would have failed and the test would have demanded the
  impossible. The fixture now writes schema-valid frontmatter, using
  `type: agent` for `AGENTS.md` per the scaffold ledger's ruling that it sits
  outside `REQUIRED_KEYS`. This is the class of bug that test exists to catch,
  which is why it is written as a spec-complete vault rather than a mock.
