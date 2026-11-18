# Issue

**Title:** Bump MultiQC so we get proper AR2 plots

## Description

This uses the sneaky 13a veriosn of MultiQC on bioconda which includes the awesome fixes to AR2 plots from @NiemannJ!!

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
    - [ ] If you've added a new tool - add to the software_versions process and a regex to `scrape_software_versions.py`
    - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](<https://github.com/>nf-core/eager/tree/master/.github/CONTRIBUTING.md)
    - [ ] If necessary, also make a PR on the nf-core/eager _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint .`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8271378a3d43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.