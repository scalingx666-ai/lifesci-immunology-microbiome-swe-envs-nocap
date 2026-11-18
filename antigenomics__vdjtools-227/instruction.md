# Issue

**Title:** Release 5.6.0: public Pgen and matched-subset discovery APIs

## Description

Expose the existing amino-acid Pgen single/batch APIs and add matched-subset richness rarefaction at whole-library read depths using the existing native iNEXT engine. Source clonotypes remain separate and unmatched reads are accounted for; no model parameters or native algorithms change.

Prepare version 5.6.0 and document the API. Validation: 1,854 tests passed in the full non-heavy tier; 14 dependency-cache permission failures passed in the access-enabled 37-test interop rerun. Seven focused subset tests and 30 related rarefaction tests pass. Strict Sphinx passes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b1501cf8f79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.