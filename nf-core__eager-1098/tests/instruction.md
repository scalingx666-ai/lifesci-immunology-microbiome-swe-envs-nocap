# Issue

**Title:** dsl2: metagenomics uncollapsed paired end

## Description

PR for metagenomics paired-end merging off, retaining that info for metagenomic tools that have PE modes.

This is a QOL improvement for tools that can use paired end information (kraken2, krakenuniq), and now allows for variable inputs into these tools (by splitting inputs into either PE or SE data and running separate instances).

Main issues resolved:
- input parsing for paired-end compatible tools (kraken2, krakenuniq, metaphlan) added when `--preprocessing_skippairmerging` used.
- Mixed paired end/single end data parses OK and outputs are properly saved
- Warning for users that singletons are not assessed when skipping pairmerging. and metaphlan, which does not use paired end information should likely not be used with this parameter.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
    - [ ] If you've added a new tool - add to the software_versions process and a regex to `scrape_software_versions.py`
    - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](<https://github.com/>nf-core/eager/tree/master/.github/CONTRIBUTING.md)
    - [ ] If necessary, also make a PR on the nf-core/eager _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `059c33a611b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.