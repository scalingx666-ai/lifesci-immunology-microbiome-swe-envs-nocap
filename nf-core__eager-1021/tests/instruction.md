# Issue

**Title:** Dsl1 2.5.0

## Description

- Added option to use MapDamage instead of DamageProfiler for damage estimation. Also added options to downsample to a specified number of reads for damage calculation with mapDamage. 
- Fixed a niche error causing file name collisons.

.
.
Clsoes #1031. 

<!-- markdownlint-disable ul-indent -->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
    - [x] If you've added a new tool - add to the software_versions process and a regex to `scrape_software_versions.py`
    - [x] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/>nf-core/eager/tree/master/.github/CONTRIBUTING.md)
    - [x] If necessary, also make a PR on the nf-core/eager _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `870d2ca8cacc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.