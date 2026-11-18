# Issue

**Title:** Remove expected `.txt` suffix for snp coverage

## Description

The most recent version of pileupcaller removes the `.txt` suffix that previous versions added to the genotype files.

`eigenstrat_snp_coverage.py` could not find the input files because it expected these suffixes to be present. With these changes, the script will no longer expect a `.txt` suffix to its input files.
<!-- markdownlint-disable ul-indent -->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `452821122435`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.