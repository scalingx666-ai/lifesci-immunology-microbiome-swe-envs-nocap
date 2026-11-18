# Issue

**Title:** fix: do not display None in LCA_Database repr

## Description

When `LCA_Database` is created without loading from a file, `self.filename` is `None`, causing `repr()` to show `LCA_Database('None')` instead of something sensible.

**Before:** `LCA_Database('None')`
**After:** `LCA_Database()`

One-line change in `src/sourmash/lca/lca_db.py`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `017e51437d19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.