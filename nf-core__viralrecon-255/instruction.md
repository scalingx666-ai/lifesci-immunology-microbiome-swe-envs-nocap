# Issue

**Title:** Bcftools consensus mask fix

## Description

Bcftools consensus masking was not working and the resulting consensus were corresponding to the reference genome. This should fix the bug.


## PR checklist

- [X] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
    - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
    - [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [X] Usage Documentation in `docs/usage.md` is updated.
- [X] Output Documentation in `docs/output.md` is updated.
- [X] `CHANGELOG.md` is updated.
- [X] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e582db9c7072`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.