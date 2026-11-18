# Issue

**Title:** Fix GPU clustering

## Description

Commit #6554009 messed up clustering on the GPU, which requires that for all array ops, both arrays are on the same device. Fix this.

NOTE: Marking as draft because currently, the `.cpu()` calls before `torch.histogram` destroys performance, so this will have to be fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee04ad64defa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.