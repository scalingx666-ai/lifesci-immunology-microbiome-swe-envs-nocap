# Issue

**Title:** Release corpus archive handles on failures

## Description

Corpus.load left its NPZ archive open when read or validation failures were retained in exception tracebacks. Read the arrays inside the existing NumPy context-manager pattern used by TablePCA.load, then validate after closing the archive. This prevents retained file handles from blocking later pipeline file operations.

Validation: all 57 signature tests pass. The new regression failed on both error paths before the fix and checks success, read failure and validation failure with retained exceptions. A direct file-descriptor probe changes from open to closed. No model parameters, array values, native code or dependencies change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55f81005b86b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.