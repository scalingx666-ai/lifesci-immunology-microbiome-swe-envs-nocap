# Issue

**Title:** Rework skip-binners

## Description

Rework skip-binners to use optional inputs in dastool rule. Avoids complex file/folder generation.
Could be extended to make refinement optional for each binner.

Also includes some logic-testing of the snakemake pipeline. Costly tests since they run a shell, but at least they don't run the actually commands.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e32f6389d834`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.