# Issue

**Title:** Alignment mode changes

## Description

-switch back to global alignment in snps module; makes program consistent with versions <= 1.2.2
-genes module has always used local alignment, so no changes here
-added option `-m` in run_midas.py snps|genes to choose between global/local read alignment
-updated help text and examples to reflect these changes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ab56ecceccf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.