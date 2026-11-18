# Issue

**Title:** Remove the dataloader mask

## Description

Previously, when creating the dataloader, Vamb would create a mask, signifying which contigs were unsuitable for encoding due to having no TNFs or a depth of zeros.
However, with the recent changes in commit 5c1dc3e, sequences with zero depth can be encoded just fine. And it was always unrealistic that a sequence would have zero TNFs - if it did, it was probably due to a serious user mistake. Now, do not mask sequences at all, and throw an error if a sequence has no TNFs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b782b7ae70a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.