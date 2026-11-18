# Issue

**Title:** Fix multiref mapping

## Description

This should fix the failure of `test_multiref` with most mappers (e.g. `bwamem`).
(Sharded) read input channels were `combine`d with references, but for most mappers they were combined a second time later, resulting in duplicates. I hope this changes are valid and I'm not missing anything!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5beb9329f68`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.