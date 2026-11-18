# Issue

**Title:** Fix space after backslash [sh: command not found]

## Description

The script `kraken.sh` contained spaces after the backslash. This resulted in _command not found_ errors, that prevented the step `metawrap kraken` to finish.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c9fe757a9ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.