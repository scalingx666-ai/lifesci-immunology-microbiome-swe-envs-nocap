# Issue

**Title:** Adjusted EBI - LSF configuration.

## Description

Limit job submission and queue size, to avoid flooding LSF.
Retry tasks at least twice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc2698f46e12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.