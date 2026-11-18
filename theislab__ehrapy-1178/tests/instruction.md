# Issue

**Title:** Stop warning for variables left out of an explicit_impute mapping

## Description

`ep.pp.explicit_impute` with a `replacement` mapping no longer logs a warning for every variable the mapping leaves out, so imputing only some variables, the intended use of a mapping, is silent.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0655a5b94b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.