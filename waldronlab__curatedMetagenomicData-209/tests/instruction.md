# Issue

**Title:** Restore check bioc

## Description

Restores .github/workflows/check-bioc.yml and removes [.github/workflows/pkgdown.yaml](https://github.com/waldronlab/curatedMetagenomicData/blob/master/.github/workflows/pkgdown.yaml) since check-bioc.yml can also generate the pkgdown site.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3316055a7c53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.