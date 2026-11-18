# Issue

**Title:** Unpin numpy in run_notebooks workflow

## Description

## Unpin numpy in the `run_notebooks` workflow

Removes the temporary `'numpy>=2.3.2,<2.4'` pin (and its trailing comment) from the notebook-execution step in `.github/workflows/run_notebooks.yml`.

The pin was added as a workaround for a CellRank incompatibility with numpy >= 2.4 (upstream: scverse/cellrank#1365). CellRank has since released a compatible version, so the constraint is no longer needed.

Follow-up to the review note in  ("Pin can be removed. Cellrank got a release.").

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01VAw5BNXMpa4xRmPq47A165

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f2c521565b9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.