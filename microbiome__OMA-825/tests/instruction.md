# Issue

**Title:** docs: Add comprehensive Rarefaction section to transformation chapter

## Description

Added new section 12.3 Rarefaction to address issue #823.

Changes include:
- Introduction to rarefaction with rarefyAssay() and niter parameter
- Subsection on using rarefaction with alpha diversity (addAlpha)
- Subsection on using rarefaction with beta diversity (addMDS)
- Function comparison explaining differences between:
  * addAlpha() vs getAlpha()
  * runMDS() vs addMDS()

Includes practical code examples demonstrating iterative rarefaction with niter=100.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a65548fafa7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.