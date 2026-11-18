# Issue

**Title:** Upgrading to version 0.1.5

## Description

See change log for details. Most importantly, the `collapse` command has been upgraded to support taxonomic/functional stratification of ORF tables (i.e., the "per-gene" tables generated in Qiita), without the need of running classification twice. @droush @wasade @antgonza

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c017f4f3328`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.