# Issue

**Title:** Release vdjtools 5.2.2

## Description

Promote the metadata-only 5.2.2 update from #205: require seqtree>=1.3.1,<2. The six feature CI checks, including the full Linux reference/EM suite, pass; strict local docs and native/Python version/dependency smoke checks pass. Algorithms, native scoring kernels and bundled models are unchanged. Author authorized admin merge/release after green promotion CI. No VDJmatch release or default promotion.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a295ea649d48`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.