# Issue

**Title:** Correctly call MULTIQC_TSV_FROM_LIST

## Description

This PR addresses 2 issues

1. The MULTIQC_TSV_FROM_LIST process takes a `val header` which should be a list as shown on https://github.com/nf-core/viralrecon/blob/dev/modules/local/multiqc_tsv_from_list.nf#L8
This PR corrects the workflows that were passing in a tab-separated string.

2. Allows the nanopore pipeline to accept fastq.gz files


- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
    - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
    - [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f0841ffd5ced`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.