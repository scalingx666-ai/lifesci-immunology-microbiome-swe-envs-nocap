# Issue

**Title:** chore: remove unused imports, debug prints, and stale TODOs

## Description

## Summary
- Drop unused imports (`sys`, `datetime` in `core/meta_information.py`; `matplotlib.gridspec`/`pyplot`/`ticker` in `plot/_survival_analysis.py`).
- Remove leftover debug `print()` calls in `plot/_sankey.py::sankey_diagram_time`.
- Delete stale TODO + commented-out `_warn_imputation_threshold` call in `preprocessing/_imputation.py::simple_impute`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc9859a094c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.