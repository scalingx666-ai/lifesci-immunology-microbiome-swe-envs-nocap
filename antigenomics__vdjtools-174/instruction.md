# Issue

**Title:** Release v2.4.0 — arda becomes a base dependency (ships the germline reference)

## Description

## v2.4.0 — arda becomes a base dependency (vdjtools now ships the germline reference)

Minor release off `dev`.

### The fix: arda is no longer optional
arda sat in the `[model]` extra, so a plain `pip install vdjtools` shipped the bundled models but **not the germline reference** — `model.reference.load_germline()` raised `ImportError`.

That broke the contract downstream libraries depend on. **mirpy** declares `vdjtools>=2.3.0` as a *base* dep explicitly for *"AIRR schema + IO, **germline reference**, Pgen"*, and had to work around the gap by **baking its own copies** at build time (`region_annotations.txt` via arda → BLOSUM62 germline distance matrices via BioPython) rather than just reading the reference from vdjtools.

vdjtools' own pyproject already stated the intent — parents are *"promoted from the extras to base deps as the phases that import them land (model → arda)"*. Phase 1 landed long ago; the promotion never happened.

### Why this is cheap
- arda-mapper ships **the same wheel matrix as vdjtools** (cp310–313 × macOS arm64 / manylinux / win_amd64).
- Its only runtime deps are `polars` + `typer` (already ours) + `requests`.
- It's imported **lazily** inside the functions that use it, so `import vdjtools` stays light.
- **MMseqs2 is only needed for arda's annotate path** — never for germline lookup, Pgen, generation, or the analytics.

### Changes
- `pyproject`: `arda-mapper>=2.5.3` → `[project].dependencies`. `[model]` kept as an **empty no-op alias** so existing `vdjtools[model]` pins (mirpy's build extra) still resolve. Dropped from `all`.
- Reworded everything that called arda optional (`reference` / `io` / `stitch` / `infer`, README, CLAUDE.md).
- **Two regression tests pin the contract** so it can't silently revert: arda-mapper must appear as an *unconditional* requirement (no `extra ==` marker), and `load_germline("TRB")` must return V/D/J + anchors from a plain install.

### Also in this release (was the held v2.3.1)
- arda floor bumped `>=2.5` → **`>=2.5.3`** (latest on PyPI); validated — no vdjtools code change needed.
- Fixed a **pre-existing** stale test (`test_vdj_estep_accumulates` dropped the `n_d` soft-count bucket the E-step legitimately harvests). The library was correct; only the test was stale. It shipped broken in v2.3.0 because the slow tier is deselected by default.

### Verification
- Fast suite: **393 passed** (incl. the 2 new contract tests)
- Full slow tier (excl. HF-network test): **17 passed**, incl. the stitch → arda-annotate round-trip
- C++ `ctest`: green

### Note for CI
`pip install -e ".[test]"` now pulls arda, so the germline tests **run** instead of skipping; arda fetches its IMGT reference once on first use.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54186e852c7e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.