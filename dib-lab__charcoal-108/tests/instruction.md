# Issue

**Title:** don't run contamination analysis on lineages that are "pure"

## Description

adds a short circuit so that if f_major and f_ident are both 100%, the analysis exits early.

adds `GCA_001593925` as a test case in the demo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c71a9526c8ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.