# Issue

**Title:** Release vdjtools 5.2.2 with seqtree 1.3.1 minimum

## Description

Raise the base seqtree requirement to >=1.3.1,<2 and prepare vdjtools 5.2.2. This guarantees the released input-length gap-prior preparation fix. Algorithms, native scoring and bundled models are unchanged. Focused version/native/dependency smoke checks pass with public seqtree1.3.1. Author authorized merge/release after green CI with admin bypass; no VDJmatch release or scoring-default promotion.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbc9608208c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.