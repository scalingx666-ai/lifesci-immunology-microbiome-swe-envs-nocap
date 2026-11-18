# Issue

**Title:** Fix: increase log_filesize_limit in MultiQC config for high-coverage samples

## Description

Fixes the issue where high-coverage samples are silently missing from the 
Samtools Stats section in the MultiQC report when using long-read host removal.

The root cause is MultiQC's default `log_filesize_limit` of 50MB. Samtools stats 
files from high-coverage Nanopore samples mapped to a large reference genome can 
exceed this, causing them to be silently skipped with no warning.

Fix: added  log_filesize_limit: 500000000 to assets/multiqc_config.yml 


## PR checklist

- [X] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/taxprofiler/tree/main/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/taxprofiler _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ X] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2e313e7f56b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.