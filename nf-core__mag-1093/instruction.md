# Issue

**Title:** Ignore CheckM storage subdirectories in nf-test snapshots

## Description

## Why

`tests/.nftignore` had:

```
GenomeBinning/QC/CheckM/*/storage/*
```

So CheckM intermediates were not actually excluded from the snapshot. Checksuming these files doesn't add much value, the important file in CheckM is the summary. And that is covered.

In the v5.5.0 release PR, I got a checksum drift in one of those files, only in conda. And I wasn't able to reproduce that locally, even trying on different machines. That's the main reason why I digged into this and figured out  that this could be solved leaving the exclusion pattern as intended in the first place.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98082c4d21c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.