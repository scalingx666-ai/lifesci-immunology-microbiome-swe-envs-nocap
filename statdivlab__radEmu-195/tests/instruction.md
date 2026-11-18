# Issue

**Title:** Update readme & vignettes

## Description

- Replace preprint link with peer-reviewed manuscript link
- Update installation instructions
    - `devtools::install_github()` was deprecated in devtools 2.5.0, and it recommends switching to `pak::pak` instead. The install instructions in the vignettes were changed to match the install instructions in the README as well.
    - I could update the patch to use `remotes::install_github` instead of `pak::pak` if you prefer that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb2d6c596358`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.