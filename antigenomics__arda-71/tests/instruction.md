# Issue

**Title:** docs CI: install seqtree (fixes the failing docs build on master)

## Description

Making `seqtree` a core dependency (2.5.5) moved its import to the top of `rnaseq.correct`, so
autodoc now needs it importable. The docs workflow installed only `sphinx pydata-sphinx-theme
nbsphinx polars`, and the build failed on master:

```
WARNING: autodoc: failed to import 'correct' from module 'arda.rnaseq';
ModuleNotFoundError: No module named 'seqtree'
```

(`sphinx-build -W` turns that warning into a failure, which is the point of the gate.)

**Installed, not mocked** — for the same reason `polars` is: both are imported at *module* level by
the rnaseq API, and autodoc cannot document a mock.

Verified: `sphinx-build -W --keep-going` builds clean locally with seqtree present.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c048c2e572b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.