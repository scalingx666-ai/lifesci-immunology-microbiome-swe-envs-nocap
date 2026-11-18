# Issue

**Title:** Rename error_on to rcmdcheck_error_on for bioconductor/workflows

## Description

bioconductor/workflows renamed the `error_on` input to `rcmdcheck_error_on` and added a separate `bioccheck_error_on` (Bioconductor/workflows#38). The old name now fails workflow validation, so this is the one-line rename.

This also sets `bioccheck_error_on: 'never'` so the known BiocCheck ERROR for the `Remotes:` dependency no longer hides R CMD check results. Remove that line once the dependency is in Bioconductor.

Drafted with Claude Code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc52825fbb4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.