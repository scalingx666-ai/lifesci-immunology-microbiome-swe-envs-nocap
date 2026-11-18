# Issue

**Title:** CI: turn on the covr coverage report

## Description

Turns on `enable_coverage_report` (Bioconductor/workflows#37): an HTML coverage report as a run artifact and per-file percentages on the run summary. The Codecov upload was already on through `CODECOV_TOKEN`; this PR's CI run tests both.

Drafted with Claude Code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8894f1a45b97`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.